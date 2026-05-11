# Markdown AI Claim Graph

![Markdown AI Claim Graph banner](assets/banner.svg)

A graph-native skill for turning Markdown analyst reports into a structured claim graph.

This project replaces the old report-first cross-review workflow with a graph-first workflow. The graph is the primary output. Prose comes last and must be derived from the graph.

## Installation

Install this skill into your Codex skills directory as `markdown-ai-claim-graph`.

### Option 1: Clone into `~/.codex/skills`

```bash
git clone https://github.com/puwarun/markdown-ai-claim-graph.git ~/.codex/skills/markdown-ai-claim-graph
```

### Option 2: Copy this folder into an existing skills directory

Place this repository at:

```text
~/.codex/skills/markdown-ai-claim-graph
```

The final structure should look like:

```text
~/.codex/skills/markdown-ai-claim-graph/
├── SKILL.md
└── agents/openai.yaml
```

### Verify

After installation, invoke it by name:

```text
Use $markdown-ai-claim-graph to convert these analyst Markdown files into a claim graph and recommend the safest next decision.
```

## What It Is

Markdown AI Claim Graph reads one or more Markdown analysis files and converts them into a normalized graph with typed nodes and typed edges.

It is built for tasks such as:

- Code review and architecture review
- Security analysis
- Performance investigations
- Requirement analysis
- Technical decision review
- Incident and postmortem analysis
- Comparing AI-generated reports before acting on them

## Graph-First Output

The default output order is always:

1. Node Table
2. Edge Table
3. Mermaid Graph
4. JSON Graph
5. Decision Summary

This is not a prose report with a graph attached. The graph is the core artifact.

## Node Types

- `Analyst`
- `File`
- `Topic`
- `Claim`
- `Evidence`
- `Risk`
- `Recommendation`
- `Decision`

## Edge Types

- `supports`
- `contradicts`
- `qualifies`
- `based_on`
- `recommends`
- `warns_about`
- `depends_on`
- `mitigates`
- `leads_to`
- `belongs_to`

## Workflow

1. Parse each Markdown analyst file into discrete topics, claims, evidence items, risks, recommendations, and decisions.
2. Normalize each extracted item into a typed node.
3. Connect nodes with typed edges that make support, contradiction, qualification, and decision flow explicit.
4. Render the graph in Markdown table form, Mermaid form, and JSON form.
5. Write a short decision summary derived from the graph.

## Example Prompt

```text
Use $markdown-ai-claim-graph to turn these Markdown analyst reports into a claim graph. Show node and edge tables, Mermaid, JSON, and then give me the decision summary.
```

## Included Examples

This repo includes a minimal example set:

- `examples/codex_review.md`: sample analyst report
- `examples/claude_review.md`: second analyst report with different risk emphasis
- `examples/claim_graph_output.md`: graph-native output example

## Repository Layout

```text
.
├── assets/
│   ├── banner.svg
│   ├── icon-small.svg
│   └── icon.svg
├── examples/
│   ├── claim_graph_output.md
│   ├── claude_review.md
│   └── codex_review.md
├── README.md
├── SKILL.md
└── agents/
    └── openai.yaml
```

## Design Principles

- Graph-first, not report-first
- Typed nodes and typed edges only
- Source attribution must be preserved
- Agreement and disagreement must appear in graph structure, not just prose
- Evidence, risks, recommendations, and decisions must be separate entities

## Main Files

- `SKILL.md`: full skill instructions
- `agents/openai.yaml`: UI metadata and default invocation prompt
- `examples/`: sample inputs and a graph-native output example
