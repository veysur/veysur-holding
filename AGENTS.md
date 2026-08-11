# AGENTS.md

This directory is a git submodule (`veysur-holding`) — the "coming soon" holding page for
veysur.com. It is not a Node.js package; there are no build steps, tests, or dependencies.

## Purpose

Plain static HTML (`index.html`, `favicon.svg`, `image/`) served, unmodified, by the shared
nginx layer in `package/k8s`:

- `holding.veysur.local` in the Tilt dev environment
- `holding.stagevs.com` in staging
- `holding.veysur.com` in production

See `package/k8s/AGENTS.md` for how the nginx config, Dockerfile, and Tiltfile sync this
content into the running nginx pod/image.

The `CNAME` file is a leftover GitHub Pages artifact and is not consumed by nginx — leave it
in place but don't rely on it.

## Editing

- Markdown/HTML only; keep it a plain static site — no build tooling, no `package.json`
- Unlike the other `external/*` submodules, this one has no cspell/commitizen setup —
  commit directly with `git commit`, following the monorepo's conventional-commit style
  (`type(scope): summary`) by hand
- Changes sync via git submodule update in the main repo
