# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [0.1.1] - 2026-11-26

### Fixed

- resolve katex and js-yaml security alerts in dev dependencies (#57)
- remove unused OutputEvent import (#52)
- use client-id instead of the deprecated app-id for the bot token (#51)
- ignore TypeScript 7 and ESLint 10 updates until the lint tooling supports them (#49)
- ignore TypeScript 7 and ESLint 10 updates until the lint tooling supports them (#49)

### Changed

- fix wrong package references and branch target (#20)
- deps-dev(deps-dev): bump @types/node from 25.3.2 to 26.6.6 (#56)
- bump @winccoa-tools-pack/npm-winccoa-core (#27)
- align .github files and scripts with the template (#55)
- deps-dev(deps-dev): bump the dev-tools group across 1 directory with 2 updates (#15)
- prefer REPO_ADMIN_TOKEN over the bot app token for merges and branch updates (#50)
- bump actions/setup-node from 6 to 7 (#37)
- bump softprops/action-gh-release from 2 to 3 (#17)
- bump actions/checkout from 6 to 7 (#35)
- deps-dev(deps-dev): bump @humanfs/node from 0.16.7 to 0.16.8 (#47)
- deps-dev(deps-dev): bump flatted from 3.3.3 to 3.4.4 (#48)
- use the winccoa-tools-pack-bot app token for automated PR actions (#46)
- deps-dev(deps-dev): bump markdownlint-cli from 0.47.0 to 0.50.1 (#36)
- deps-dev(deps-dev): bump globals from 17.3.0 to 17.14.0 (#38)
- deps-dev(deps-dev): bump markdownlint from 0.40.0 to 0.42.2 (#33)
- deps-dev(deps-dev): bump typescript-eslint from 8.56.1 to 8.73.0 (#34)
- deps-dev(deps-dev): bump tsx from 4.21.0 to 4.23.15 (#39)
- add apply-settings helper scripts and actions policy (#42)

## [Unreleased]

### Documentation

- Align README CLI/API examples with actual tool behavior (required version, argument order).

## [1.0.0] - 2026-03-03

> **Breaking change:** Package transformed from PNL/XML converter to CTRL script runner.

### Added

- `CtrlRunner` class wrapping WinCC OA `WCCOActrl` binary for programmatic script execution.
- TypeScript API convenience functions: `executeScript()`, `createRunner()`, `checkExecutable()`, `getExecutablePath()`.
- CLI command `winccoa-ctrl execute` with full flag support.
- Script parameter support — positional args passed before `-proj` flag per WCCOActrl syntax.
- Timeout handling (default 60 s, configurable via `--timeout`).
- Standalone mode (`-n` flag via `--standalone`).
- Syntax-check-only mode (`-syntax` flag via `--syntax-only`).
- CTRL trace debugging (`-dbg 29` via `--enable-trace`).
- Report file output (`-reportfile` via `--report-file`).
- Custom config path support (`-config` via `--config`).
- Complete stdout/stderr capture and exit code propagation in `CtrlExecutionResult`.
- Execution duration tracking in result.
- JSON output mode for machine-readable CLI results (`--json`).
- Silent mode to suppress console output (`--silent`).
- Dual module format: CommonJS (`dist/cjs/`) and ESM (`dist/esm/`).
- Full TypeScript type definitions (`CtrlExecutionOptions`, `CtrlExecutionResult`, `OutputEvent`, `OutputCallback`).
- `onOutput` callback API for streaming output events.
- Cross-platform support (Windows `WCCOActrl.exe` and Linux `WCCOActrl`).

### Changed

- Package renamed from `@winccoa-tools-pack/npm-winccoa-ui-pnl-xml` to `@winccoa-tools-pack/npm-winccoa-ctrl`.
- CLI binary renamed from `winccoa-pnl-xml` to `winccoa-ctrl`.
- Full API redesign — replaces `PnlXmlConverter` with `CtrlRunner`.

### Fixed

- CLI direct-run detection now uses `require.main === module` and matches the `winccoa-ctrl` symlink name, fixing invocation via `npm link` or globally installed symlinks.
