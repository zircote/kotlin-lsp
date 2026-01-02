# kotlin-lsp

[![Version](https://img.shields.io/badge/version-0.1.0-blue.svg)](CHANGELOG.md)
[![License](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)
[![Claude Plugin](https://img.shields.io/badge/claude-plugin-orange.svg)](https://docs.anthropic.com/en/docs/claude-code/plugins)
[![Marketplace](https://img.shields.io/badge/marketplace-zircote--lsp-purple.svg)](https://github.com/zircote/lsp-marketplace)
[![Kotlin](https://img.shields.io/badge/Kotlin-7F52FF?logo=kotlin&logoColor=white)](https://kotlinlang.org/)

A Claude Code plugin providing comprehensive Kotlin development support through:

- **kotlin-language-server** integration for IDE-like features
- **12 automated hooks** for Gradle builds, linting, formatting, and testing
- **Kotlin tool ecosystem** integration (detekt, ktlint)

## Quick Setup

```bash
# Run the setup command (after installing the plugin)
/setup
```

Or manually:

```bash
# macOS (Homebrew)
brew install kotlin-language-server
brew install ktlint detekt
```

## Features

### LSP Integration

The plugin configures kotlin-language-server for Claude Code via `.lsp.json`:

```json
{
    "kotlin": {
        "command": "kotlin-language-server",
        "args": [],
        "extensionToLanguage": { ".kt": "kotlin", ".kts": "kotlin" },
        "transport": "stdio"
    }
}
```

**Capabilities:**
- Go to definition / references
- Hover documentation
- Code completion with null safety
- Coroutine-aware navigation
- Real-time diagnostics

### Automated Hooks

| Hook | Trigger | Description |
|------|---------|-------------|
| `kotlin-format-on-edit` | `**/*.kt` | Auto-format with ktlint |
| `kotlin-lint-on-edit` | `**/*.kt` | Lint with detekt |
| `kotlin-compile-check` | `**/*.kt` | Compile with Gradle |
| `kotlin-null-check` | `**/*.kt` | Detect !! usage |

## Required Tools

| Tool | Installation | Purpose |
|------|--------------|---------|
| `kotlin-language-server` | `brew install kotlin-language-server` | LSP server |
| `ktlint` | `brew install ktlint` | Linting & formatting |
| `detekt` | `brew install detekt` | Static analysis |

## Project Structure

```
kotlin-lsp/
├── .claude-plugin/
│   └── plugin.json           # Plugin metadata
├── .lsp.json                  # kotlin-language-server configuration
├── commands/
│   └── setup.md              # /setup command
├── hooks/
│   └── scripts/
│       └── kotlin-hooks.sh
├── tests/
│   └── SampleTest.kt         # Test file
├── CLAUDE.md                  # Project instructions
└── README.md                  # This file
```

## License

MIT
