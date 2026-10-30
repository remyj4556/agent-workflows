# <GAME NAME>

<!-- Placeholders in <angle brackets> get filled during the kickoff session. Keep this file under ~150 lines. -->

@docs/INDEX.md

## Project
- Engine: Godot <4.x exact version>. Language: GDScript (statically typed).
- Platforms: <PC / web / ...>. Multiplayer: <none / local / online, players>.
- Vision and scope: see `docs/vision.md`. Architecture: see `docs/architecture.md`.

## How we work (Elephant-Goldfish)
Design is the source of truth; code implements an approved doc.

- **No code without a doc.** Feature work starts from a doc in `docs/features/` with `Status: approved`. Exception: when I say "quick fix", make the smallest change and note it in the relevant doc's Decisions Log.
- **Design mode** (when I say "design mode" or we're in plan mode): do not write or edit code. Ask clarifying questions, challenge my assumptions, and propose designs yourself before reacting to mine. Agreeing with me is not helpful; finding gaps is.
- **Implementation mode:** follow the doc's Detailed Implementation exactly. If you need to touch a file the doc doesn't list, or the plan turns out wrong, stop and tell me. We update the doc first, then continue.
- **Write docs one section at a time**, in this order: Problem, Technical Plan, Alternatives Considered, Detailed Implementation (every file + why), Acceptance Criteria, Decisions Log. Template: `docs/features/_TEMPLATE.md`.
- **After a feature lands:** set the doc's Status to `implemented`, update the Decisions Log with anything that changed, and add the doc to `docs/INDEX.md`.
- **If you're unsure how something works in this codebase,** read the relevant doc or file instead of guessing. If unsure about a Godot API, say so — do not invent methods, signals, or properties.

## Git workflow (PRs only)
- **Never work on `main`.** Before editing anything, check the current branch. If it's `main`, create a branch first: `feat/<feature-name>`, `fix/<short-name>`, or `docs/<short-name>`.
- One feature doc = one branch = one PR. Commit in small steps that match the doc's implementation steps.
- When the work is done and tests pass: push the branch and open a PR with `gh pr create`. The PR body links the design doc, lists each Acceptance Criterion with pass/fail, and notes anything that diverged from the doc.
- **Never merge, rebase, force-push, or push to `main`.** I review and merge every PR myself.
- Never use `--no-verify` or disable hooks to get a commit through. If a check fails, stop and tell me.

## Godot rules
- Godot 4 API only. No Godot 3 patterns (`yield`, `KinematicBody`, `export var`, `onready var` without `@`, etc.).
- Static types on every variable, parameter, and return. Use float literals (`1.0`, not `1`) where a float is meant; watch int truncation in timers and division.
- **Scenes and resources (`.tscn`, `.tres`):** prefer telling me the node tree change to make in the editor. If you must edit one by hand, change the minimum, never fabricate `uid://` values or `ext_resource` ids, and tell me to reopen the scene in the editor to verify.
- Commit `*.uid` and `*.import` files; `.godot/` stays gitignored.
- Prefer signals and exported references over `get_node` with long paths. Autoloads are listed below; don't add one without a doc.
- Collision layers are named in Project Settings and listed below. Never use a raw layer number that isn't in this table.

### Autoloads
| Name | Script | Purpose |
|------|--------|---------|
| <...> | <...> | <...> |

### Collision layers
| # | Name | Used by |
|---|------|---------|
| 1 | <...> | <...> |

## Commands
- Run: `<godot --path . >`
- Tests: `<test command, e.g. GUT or gdUnit4 headless>`
- Before saying a task is done: run the tests and report the result.

## Layout
<filled in by kickoff: top-level folders and what lives in each>

## Pitfalls
<!-- Add a line here whenever Claude makes the same mistake twice. -->
- <...>
