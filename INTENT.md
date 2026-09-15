# INTENT.md

## 1. Purpose of This Project

`commonsense` is not a project that builds software.

**It is a reference-material repository for performing the following two steps, automatically or semi-automatically, every time a new piece of work (project/repo) starts:**

1. Write that work's own `INTENT.md` — defining the problem, goal, and scope it actually needs to solve
2. Assemble a `CLAUDE.md` or `AGENTS.md` that fits the purpose/domain/constraints recorded in that `INTENT.md` — instead of writing from scratch every time, pick and attach only the already-validated modules that are needed

In other words, what this repository holds is not "the instructions themselves," but **the raw material (source of modules) + assembly procedure referenced when composing instructions per project**.

## 2. Background / Why This Is Needed

- Writing a fresh `CLAUDE.md`/`AGENTS.md` from scratch for every project breaks consistency across projects and makes it easy to drop already-validated rules (anti-hallucination, evidence priority, refactoring policy, etc.).
- Conversely, copy-pasting the same giant instruction file into every project injects irrelevant domain rules (e.g., OT/PLC integration rules bleeding into a pure frontend project) as noise, degrading the signal-to-noise ratio.
- Solution: always include the common principles (Common Core), and selectively include domain/work-mode/industry-specific modules **only when they match the purpose stated in that project's own `INTENT.md`**.

## 3. Core Workflow

```
[New work starts]
      │
      ▼
1) Check whether INTENT.md exists
   - If it exists: read the problem, goal, scope (In/Out of Scope),
     domain, and constraints directly from it
   - If it doesn't: infer from the repo/README/code/user request,
     or confirm directly with the user; write a new INTENT.md now
     if practical
      │
      ▼
2) Determine domain/preset from INTENT.md (or the inferred content)
   - See MASTER.md's PART G (Preset → Module Activation Map)
      │
      ▼
3) Select only the modules that are needed
   - PART A (Common Core): always included
   - PART B (work modes) / PART C (technical domains) /
     PART D (industrial & public projects) / PART E (Git/PR):
     only the ones actually relevant to this project
      │
      ▼
4) Identify the target agent, then assemble CLAUDE.md or AGENTS.md
   - Look up the target agent (Claude Code / Codex CLI·AGENTS.md
     convention / other) in MASTER.md section 0.3 "Agent Delta Table"
     to decide the output filename, placement, and any minor rule
     differences
   - Finish assembly by filling in PART F (Project Profile Template)
     with the project overview
      │
      ▼
5) Place the result at the target project's root
   - INTENT.md and CLAUDE.md/AGENTS.md both exist together
```

This repository aims for a **single document** that any agent can fetch and reference identically. There used to be separate master documents for Claude and Codex, but once it was confirmed that the PART A–J body was substantively the same in both, they were merged into one. The parts that differ by agent (output filename, placement, PR header level, co-author attribution, etc.) exist only in the merged document's 0.3 table.

## 4. What This Repository Currently Contains

- `MASTER.md`
  A single, agent-independent modular master. Composed of:
  - Section 0: usage guide — assembly procedure, Agent Delta Table (0.3), facts requiring verification (0.4)
  - PART A (Common Core) through PART J (final check): rule body that is identical no matter which agent assembles it
  - PART F: Project Profile Template (used to map this repository's own `INTENT.md` into a project profile)
  - PART G: Preset (G1–G13) → Module Activation Map
  - PART K: Worked Examples — finished results of assembling the same preset (G1) for Claude Code (`CLAUDE.md`), the Codex/`AGENTS.md` convention (`AGENTS.md`), and Hermes (`AGENTS.md`, plus a subdirectory-placement example since that's the one thing that actually differs from Codex)

There used to be separate Claude/Codex master documents and their assembly examples (`CLAUDE.md`/`AGENTS.md`) split across 4 files. After confirming the PART A–J body was substantively identical, they were merged into one (the example files were absorbed into PART K). This file is this repository's primary raw material. If an assembly procedure or script is ever added, update sections 4 and 6 of this document.

## 5. How to Use This Repository (when applying it to another project)

1. Check whether the target project already has an `INTENT.md`.
   - **If it exists**, use its content (Project Purpose / In·Out of Scope / Domain / constraints) as-is.
   - **If it doesn't**, infer it from the repo/README/code/user request, or confirm directly with the user. Write a new `INTENT.md` now if practical. Do not write inferred content as if it were fact.
2. Based on Domain, pick the closest preset (G1–G13) from `MASTER.md`'s PART G table. If none fits exactly, combine individual modules from PART B/C/D directly.
3. In the same document's 0.3 "Agent Delta Table," look up the target agent to confirm the output filename (`CLAUDE.md`/`AGENTS.md`/other) and placement.
4. Fill PART F (Project Profile Template) with what was obtained in step 1 (from `INTENT.md` if it exists, otherwise the inferred/confirmed content), and append it to the bottom of the assembled file.
5. Commit the result at the target project's root. Do not modify the `commonsense` repository itself (it's a raw-material repository, so per-project outputs don't accumulate here).

## 6. Scope

**In Scope**
- Defining the `INTENT.md` writing guide and its standard fields
- Maintaining the modular raw material used for automatic/semi-automatic `CLAUDE.md`/`AGENTS.md` assembly
- Maintaining the preset (domain) → module mapping table
- Adding modules to PART C/D as new domains recur often enough to justify it

**Out of Scope**
- Permanently storing a specific project's actual `CLAUDE.md`/`AGENTS.md` output in this repository (`MASTER.md`'s PART K is only an assembly example, not the final version of any specific real project)
- Implementing source code/application logic for this repository itself
- Whether to implement an automation script for assembly is a separate decision — currently this assumes a human/agent manually assembles it by referring to the master document (TBD: whether script/CLI automation is actually required)

## 7. Future Work (undecided — not filled in arbitrarily)

- Whether to split the standard `INTENT.md` template into a separate file (e.g., `INTENT_Template.md`) — TBD
- Whether preset selection should be automated by a script/agent instead of a human — TBD
- Hosting `MASTER.md` on a public GitHub repo as a raw URL — check the commit log and remote repo state for progress/completion (this document does not pin a date to it)
- If PART A–J content ever needs to behave differently for a specific agent, whether to extend the 0.3 delta table or branch the body content again — TBD
