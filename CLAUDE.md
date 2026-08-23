# sterngold-discussions — rules the OS doesn't already give you

@README.md

## What this repo actually is

The git contents are almost incidental: `README.md`, `SECURITY.md`,
`.github/dependabot.yml`, and one workflow, `ci.yml`. The real content —
the comments Giscus renders on sterngold.nl — lives in this repo's GitHub
**Discussions**, a separate GitHub feature not stored in the git tree.
Editing or merging files here never touches a live comment.

## The one rule that matters

`README.md`: "This repo must remain public for Giscus to function." Never
change this repo's visibility to private, archive it, or delete it — any
of those breaks comments on the live site. Nothing else here is that risky.

## `ci.yml` (`.github/workflows/ci.yml`)

Triggers: `pull_request`, `push` to `main`, `workflow_dispatch`. Two jobs
feed a required `ci` aggregator: `gitleaks` (checksum-verified binary, not
the marketplace action) and `hardening` (zizmor, gating unpinned `uses:`,
`${{ }}` injection, over-scoped tokens). Its own comments note `hardening`
runs from the PR's own checkout, so it catches accidental drift here, not
a hostile PR that edits the job out of `needs:`.

## Merging to `main`

No build, no deploy — a merge only updates the tracked docs/CI files and
has no effect on live Discussions or comments.
