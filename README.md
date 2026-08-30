# Revo for Zed

Zed language support for [Revo](https://revo.lung.fyi/).

This extension provides Revo syntax highlighting through Tree-sitter and integrates Revo's built-in language server, `revolt`.

## Features

- `.rv` file support
- Revo syntax highlighting
- Tree-sitter grammar integration
- Revo language server integration via `revo lsp`
- Documentation comment highlighting

## Requirements

You need to have the Revo compiler installed and available in your `PATH`.

The extension uses Revo's built-in language server:

```text
revo lsp
```

You can verify that Revo is available with:

```powershell
revo --version
```

If `revo` is not recognized, make sure the directory containing the Revo executable is included in your system `PATH`.

## Installation

### Development Extension

Until this extension is available through Zed's extension registry, you can install it as a development extension.

1. Clone this repository.
2. Open Zed.
3. Open the Command Palette with `Ctrl+Shift+P`.
4. Run `zed: install dev extension`.
5. Select the cloned repository.

Zed will build and load the extension.

## Language Server

Revo includes its own language server, `revolt`, bundled into the `revo` executable.

The language server can be started with:

```bash
revo lsp
```

The extension configures Zed to launch the language server automatically for Revo files.

## Tree-sitter

Syntax highlighting is provided by the Revo Tree-sitter grammar:

https://codeberg.org/doomy/tree-sitter-revo

The extension references the upstream grammar so users do not need to manually install Tree-sitter or configure the grammar themselves.

## Comments

Revo supports several comment forms.

Single-line comments:

```revo
# This is a comment
```

Documentation comments:

```revo
#* This is a documentation comment *#
```

The extension highlights documentation comments separately from regular comments.

## Semantic Tokens

Revo's language server supports LSP semantic tokens.

Zed's semantic-token highlighting may be disabled by default. If you want to use semantic tokens together with Tree-sitter highlighting, enable the `combined` mode in your Zed settings:

```json
{
  "languages": {
    "Revo": {
      "semantic_tokens": "combined"
    }
  }
}
```

Tree-sitter highlighting works independently of semantic tokens.

## Contributing

Issues and pull requests are welcome.

If a syntax-highlighting issue is caused by the upstream Tree-sitter grammar, it may need to be addressed in:

https://codeberg.org/doomy/tree-sitter-revo

For Revo language or language-server issues, see:

https://github.com/if-not-nil/revo

## Credits

- [Revo](https://revo.lung.fyi/) by if-not-nil
- [tree-sitter-revo](https://codeberg.org/doomy/tree-sitter-revo) by doomy

## License

See the `LICENSE` file in this repository.
