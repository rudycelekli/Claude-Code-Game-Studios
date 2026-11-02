---
paths:
  - "prototypes/**"
---

# Prototype Code Standards (Relaxed)

Prototypes are throwaway code for validating ideas. Standards are intentionally
relaxed to maximize iteration speed. The goal is learning, not production quality.

## What's Allowed in Prototypes
- Hardcoded values (no need for data-driven config)
- Minimal or no doc comments
- Simple architecture (no dependency injection required)
- Singletons and global state
- Copy-pasted code (no need for abstraction)
- Debug output left in place
- Placeholder art and audio
- Quick-and-dirty solutions

## What's Still Required
- Each prototype lives in its own subdirectory: `prototypes/[name]-concept/`
  (`/prototype`), `prototypes/[name]-spike-[date]/` (`/prototype` spike mode) or
  `prototypes/[name]-vertical-slice/` (`/vertical-slice`)
- Every prototype file starts with the `PROTOTYPE - NOT FOR PRODUCTION` (or
  `VERTICAL SLICE - NOT FOR PRODUCTION`) header comment, in the file's own
  comment syntax; files that cannot hold a comment are exempt
- Every prototype MUST end with a `REPORT.md` in its directory, from
  `.claude/docs/templates/prototype-report.md` (concept) or
  `.claude/docs/templates/vertical-slice-report.md` (vertical slice): the
  hypothesis, what was built, the result and the PROCEED / PIVOT / KILL verdict,
  with its row in `prototypes/index.md`. `/gate-check` looks for this file. A
  spike ends with a shorter `SPIKE-NOTE.md` instead
- No production code may reference or import from `prototypes/`
- Prototypes must not modify files outside `prototypes/`
- Prototypes must not be deployed or shipped

## When a Prototype Succeeds
If a prototype validates a concept and the feature moves to production:
1. The prototype code is NOT migrated directly — it is rewritten to production standards
2. The prototype `REPORT.md` findings inform the production design document
3. The prototype directory is preserved for reference but never extended

## Cleanup
A concluded prototype is frozen, not deleted: its `REPORT.md` is the record
`prototypes/index.md` links to and `/gate-check` reads, so keep the directory.
Never let prototype code grow into production code through incremental "cleanup."
