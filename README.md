# zuzubox

`zuzubox` is the authoring companion to `zuzuzoo`. It helps distribution
authors mint a clean working tree, verify it against the ZDF-1 packaging
rules, run package tests, build a `tar.gz` archive, and upload that archive
to Zuzulang.org with an upload token.

```sh
zuzubox verify
zuzubox test
zuzubox build
zuzubox upload zuzubox-0.0.1.tar.gz
```

The command is designed for a polished terminal workflow. Human output uses
aligned status markers and a short final summary; `--json` switches the
commands that produce reports to machine-readable JSON.

## Commands

- `zuzubox mint [DIR]` creates a new distribution skeleton. Use `--licence`
  to choose a suggested licence or enter any SPDX expression.
- `zuzubox verify [DIR]` checks metadata, package membership, reserved module
  names, documentation, changelog, licence, and package size.
- `zuzubox test [DIR]` runs every `tests/**/*.zzs` test with the package's own
  `modules` and `inc` directories on the library path.
- `zuzubox build [DIR]` verifies, tests, and writes a ZDF-1 `tar.gz` archive.
- `zuzubox upload [ARCHIVE]` prechecks and uploads an archive using
  `ZUZUBOX_UPLOAD_TOKEN`.

Run `zuzubox help` or `zuzubox help COMMAND` for command-specific options.

## Upload Tokens

Uploads never use account passwords. Create a token on the website, then set:

```sh
export ZUZUBOX_UPLOAD_TOKEN=zubox_...
```

For local development, `--base-url` can point to another server. The tool
refuses to send tokens to non-HTTPS URLs unless `--insecure` is explicitly
given.
