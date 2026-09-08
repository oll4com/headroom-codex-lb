# Headroom — OLL4 maintained mirror

Based on upstream **Headroom v0.37.0** (`32d7ca4577d599b8a5f811ada74cf31504302c9d`).
This repository is an OLL4 derivative, not the canonical upstream project.

## Upstream Attribution

Headroom is developed by [Headroom Labs](https://github.com/headroomlabs-ai/headroom), formerly `chopratejas/headroom`, and released under Apache-2.0. The upstream license and notices are retained. See [upstream documentation](https://headroom-docs.vercel.app) and the [upstream README](UPSTREAM_README.md) for the library, proxy and MCP interfaces. Contribute general fixes upstream.

## What OLL4 Changed

- Browser favicon and a root redirect to the dashboard.
- A wider responsive breakpoint for historical charts.
- Mirror-specific release notes and validation without publishing to upstream package registries.

## Intentionally Excluded

Private gateway integrations, account/quota endpoints, streaming diagnostics, aggregate-persistence overrides, credentials, deployment topology, runtime state and internal operational reports are excluded. Upstream `.env` example files are omitted from this public export; configure environments using the upstream documentation. Upstream publishing workflows are replaced with mirror validation.

## Install and Use

For the standard package, use `python -m pip install "headroom-ai[proxy]==0.37.0"`.
That installs the upstream package; this repository carries additional UI source changes. Build from this checkout only if you need those changes, following the upstream development instructions. OLL4 does not publish a separate PyPI or npm package from this repository.

Compression depends on the workload and settings. Provider prefix-cache discounts are separate from removed tokens. No fixed savings percentage is guaranteed, and this mirror does not contain production credentials or a ready-made private gateway deployment.

## Mirror Pull Requests

The mirror keeps three required GitHub check names:

- `changes`: compile the Python source, verify attribution files, check the actual change range for whitespace errors, and reject manual edits to the upstream-generated `CHANGELOG.md` on PRs. Use `OLL4_CHANGELOG.md` for mirror release notes.
- `commitlint`: validate PR commits against the existing Conventional Commit configuration.
- `label`: validate the current PR title, template, behavior proof and review readiness with the base branch's governance script. Suggested labels appear in the job summary; the workflow does not modify labels or post comments. The upstream exemption for bot-authored PR templates remains in place.

Checks rerun when PR metadata changes. Workflow permissions are read-only, and no package publishing or model downloads run. These are lightweight mirror checks, not the full upstream runtime test suite. Follow the PR template and include relevant test evidence for source changes. Merging also requires one approving review under the existing branch protection.
