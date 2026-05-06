# SpecOps Skills Directory

A community-maintained directory of AI agent instruction sets (skills) for the [SpecOps methodology](https://spec-ops.ai) — a specification-driven approach to software development and legacy system modernization.

Skills are human-authored Markdown guides that teach AI coding agents how to perform specialized tasks. They encode domain-specific procedural knowledge — patterns, terminology, analysis steps, and output formats — that models don't reliably possess from training data alone. For more on the role of skills in the SpecOps methodology, see [Instruction Set Examples](https://github.com/mheadd/spec-ops/blob/main/public/INSTRUCTION-SETS.md).

This directory links to externally hosted skills shared by the SpecOps community. If you've built a SpecOps skill and want it listed here, open a new issue or submit a PR.

---

## Skills

### Spec-Driven Development Workflow

| Skill | Description | Author |
|-------|-------------|--------|
| [specops](https://github.com/JarvusInnovations/agent-skills/blob/main/skills/specops/SKILL.md) | Spec-driven development workflow where specs are the source of truth. Covers philosophy, spec writing, directory structure, templates, how agents use specs, and project setup. Includes a spec drift auditor. | [Jarvus Innovations](https://github.com/JarvusInnovations/agent-skills) |

### Analysis & Planning

| Skill | Description | Author |
|-------|-------------|--------|
| [specops-initial-plan](https://github.com/ryan-mahoney/ryan-llm-skills/blob/main/skills/specops-initial-plan/SKILL.md) | Create an initial SpecOps plan — extract a comprehensive, implementation-language-agnostic specification from an existing codebase, module, or workflow. | [Ryan Mahoney](https://github.com/ryan-mahoney/ryan-llm-skills) |
| [specops-analysis](https://github.com/ryan-mahoney/ryan-llm-skills/blob/main/skills/specops-analysis/SKILL.md) | Perform a SpecOps analysis to produce a detailed 11-section specification from existing artifacts, including business rules, decision logic, defaults, thresholds, and policies. | [Ryan Mahoney](https://github.com/ryan-mahoney/ryan-llm-skills) |
| [specops-refactor-plan](https://github.com/ryan-mahoney/ryan-llm-skills/blob/main/skills/specops-refactor-plan/SKILL.md) | Create a refactor-focused SpecOps plan for a specific source folder and goal — preserves behavioral contracts while producing a decision-complete refactor strategy. | [Ryan Mahoney](https://github.com/ryan-mahoney/ryan-llm-skills) |

### Specification Generation

| Skill | Description | Author |
|-------|-------------|--------|
| [specops-make-spec](https://github.com/ryan-mahoney/ryan-llm-skills/blob/main/skills/specops-make-spec/SKILL.md) | Convert a verified SpecOps analysis into a deterministic implementation specification with architecture, acceptance criteria, and sequenced implementation steps. | [Ryan Mahoney](https://github.com/ryan-mahoney/ryan-llm-skills) |

### Verification & Auditing

| Skill | Description | Author |
|-------|-------------|--------|
| [specops-ambiguity-audit](https://github.com/ryan-mahoney/ryan-llm-skills/blob/main/skills/specops-ambiguity-audit/SKILL.md) | Audit an analysis spec for ambiguities that would force an implementer to make undocumented judgment calls, then resolve them by researching the legacy source code via parallel subagents. | [Ryan Mahoney](https://github.com/ryan-mahoney/ryan-llm-skills) |
| [specops-spec-coherence](https://github.com/ryan-mahoney/ryan-llm-skills/blob/main/skills/specops-spec-coherence/SKILL.md) | Audit a set of analysis specs for cross-spec coherence — dependency order, pairwise integration contracts, shared data models, side-effect ownership, and terminology — then patch gaps. | [Ryan Mahoney](https://github.com/ryan-mahoney/ryan-llm-skills) |
| [specops-spec-conformance](https://github.com/ryan-mahoney/ryan-llm-skills/blob/main/skills/specops-spec-conformance/SKILL.md) | Audit an implementation spec against its source analysis spec for dropped, weakened, or contradicted requirements, then patch the implementation spec. | [Ryan Mahoney](https://github.com/ryan-mahoney/ryan-llm-skills) |
| [specops-implementation-drift](https://github.com/ryan-mahoney/ryan-llm-skills/blob/main/skills/specops-implementation-drift/SKILL.md) | Re-analyze migrated code, diff against the original analysis spec, and generate corrective specs for each behavioral divergence so the next code-gen iteration converges. | [Ryan Mahoney](https://github.com/ryan-mahoney/ryan-llm-skills) |

### Testing

| Skill | Description | Author |
|-------|-------------|--------|
| [specops-contract-tests](https://github.com/ryan-mahoney/ryan-llm-skills/blob/main/skills/specops-contract-tests/SKILL.md) | Generate framework-agnostic pytest contract tests from a SpecOps analysis file, covering interfaces, data models, policy rules, behavioral scenarios, error handling, and edge cases. | [Ryan Mahoney](https://github.com/ryan-mahoney/ryan-llm-skills) |
| [specops-integration-test](https://github.com/ryan-mahoney/ryan-llm-skills/blob/main/skills/specops-integration-test/SKILL.md) | Generate integration tests for normative cross-module pathways discovered from analysis specs and the migrated call graph, reusing existing unit-test mocks. | [Ryan Mahoney](https://github.com/ryan-mahoney/ryan-llm-skills) |

### Orchestration

| Skill | Description | Author |
|-------|-------------|--------|
| [specops-orchestrate-analysis](https://github.com/ryan-mahoney/ryan-llm-skills/blob/main/skills/specops-orchestrate-analysis/SKILL.md) | Orchestrate sequential subagents to generate one analysis per target from an initial plan, with per-target verification and fix-up loops. | [Ryan Mahoney](https://github.com/ryan-mahoney/ryan-llm-skills) |
| [specops-orchestrate-spec-create](https://github.com/ryan-mahoney/ryan-llm-skills/blob/main/skills/specops-orchestrate-spec-create/SKILL.md) | Orchestrate sequential subagents to generate one implementation spec per analysis file, with per-file verification and fix-up loops. | [Ryan Mahoney](https://github.com/ryan-mahoney/ryan-llm-skills) |

### Plugins

| Plugin | Description | Author |
|--------|-------------|--------|
| [code-modernization](https://github.com/anthropics/claude-plugins-official/tree/morganl/code-modernization-plugin/plugins/code-modernization) | Claude Code plugin providing a structured `assess → map → extract-rules → reimagine → transform → harden` workflow with specialist agents (legacy-analyst, business-rules-extractor, architecture-critic, security-auditor, test-engineer) for modernizing legacy codebases. | [Anthropic](https://github.com/anthropics/claude-plugins-official) |

---

## How Skills Fit the SpecOps Pipeline

The skills above map to specific phases of a SpecOps migration:

```
1. specops-initial-plan          → Discovery & assessment
2. specops-analysis              → Specification generation (per module)
3. specops-ambiguity-audit       → Harden each spec individually
4. specops-spec-coherence        → Cross-spec consistency & implementation order
5. Domain experts verify specs
6. specops-make-spec             → Implementation spec generation
7. specops-spec-conformance      → Verify impl spec derives from analysis
8. Code generation
9. specops-contract-tests        → Generate contract tests from specs
10. specops-integration-test     → Generate cross-module integration tests
11. specops-implementation-drift → Verify migrated code matches analysis
12. Iterate until convergence
```

---

## Adding a Skill to This Directory

To list your skill here, open a PR that adds a row to the appropriate table above. Include:

- **Link** to the `SKILL.md` file in your public repository
- **Description** — one sentence summarizing what the skill does
- **Author** — link to the repository containing the skill

Skills should be human-authored, publicly accessible, and follow the SpecOps methodology.

## Related Projects

- [Code Modernization Plugin](https://github.com/anthropics/claude-plugins-official/tree/morganl/code-modernization-plugin/plugins/code-modernization) — Claude Code plugin with specialist agents and a phased workflow for legacy system modernization
- [SpecOps Methodology](https://spec-ops.ai) — The specification-driven modernization methodology
- [SpecOps AGENTS.md](https://github.com/mheadd/spec-ops-agents-file) — Template AGENTS.md for SpecOps projects
- [SpecOps Action](https://github.com/spec-ops-method/spec-ops-action) — GitHub Action for spec change tracking
- [SpecOps Demo](https://github.com/mheadd/spec-ops-demo) — Example skills and specifications for IRS tax systems
- [Instruction Set Examples](https://github.com/mheadd/spec-ops/blob/main/public/INSTRUCTION-SETS.md) — Detailed guide on building and sharing skills

## License

This project is released under the [MIT License](LICENSE).
