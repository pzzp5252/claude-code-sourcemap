# Security model — claude-code-sourcemap

This is the threat model used by Devin security scans. It is shared across pzzp5252's five repositories (claude-code-sourcemap, dji-remote-c3, hvac-validation-docs, opencode-gmp-skills, web-slide-fps), which are unrelated systems scanned separately. This file covers **claude-code-sourcemap**. Facts marked **(owner)** come from the repository owner; the rest is read from the code. No infrastructure repository exists: these are local tools, firmware and research code, nothing hosted **(owner)**.

## Components

| Component | Code | Trust boundary |
|---|---|---|
| Claude-Code-Research | `restored-src/src` | None in practice (read-only research copy) |

## System overview

TypeScript reconstructed from the public `@anthropic-ai/claude-code` 2.1.88 source map, kept for research.

## Out of scope / accepted risk

- Research/reading only; not shipped or run for others **(owner)**. Vulnerabilities in the reconstructed third-party code do not threaten the owner's systems; only issues that would hurt someone merely cloning or reading the repository matter.
- Scans cover `restored-src/src` only. `restored-src/node_modules`, `restored-src/vendor`, `package/` (bundled `cli.js`) and the tarball are excluded **(owner)**.

## Owner priorities across all repositories

- Integrity of GMP validation records and reports (data integrity, ALCOA+) **(owner, critical)**.
- Camera control and take/journal integrity in the field **(owner, critical)**.
- Developer/QA workstations that run these tools **(owner)**.

## Finding tags

- `Component` (table above), `CVE` for known dependency vulnerabilities, `GMP-relevance` = yes when the finding could affect GMP record/report or data integrity (ALCOA+), otherwise no **(owner)**.
