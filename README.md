# Repolex Knowledge Graph of tox-dev/workflow

RDF knowledge graph data for [tox-dev/workflow](https://github.com/tox-dev/workflow), parsed by [repolex](https://repolex.ai).

> **Note**: This data is experimental and subject to change without notice.

## How to use this data

The easiest way to get started is to install the [rlex](https://github.com/repolex-ai/rlex) query tool:

```bash
cargo install --git https://github.com/repolex-ai/rlex
```

Verify the install:

```bash
rlex --help
```

**rlex is designed to be used primarily by LLMs in a terminal.** Start up your favorite AI assistant and ask it to use rlex. It handles the SPARQL — you just ask questions in plain English.

To load this repo's data:

```bash
rlex download tox-dev/workflow
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 1bb961580e20073f66ccb9024f248357f8c8fecb
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 1bb961580e20073f66ccb9024f248357f8c8fecb
│           └── chunk-001.nq.gz
├── blob
│   ├── 180a57ec308669536fd321b7fdc35d2b75c2b9a1.nq.gz
│   ├── 3dde2eaa4cfe6dee0045748b18c8db8a4fb2fca6.nq.gz
│   ├── 52deee148ff5590000d2b9c47a618c1564b88078.nq.gz
│   ├── 689bed022ce6a35279e71123f28e52040a37934c.nq.gz
│   ├── dd64f3d5ee6cdfcf3dc4f5bedef937bff4026dd9.nq.gz
│   └── f84658ab5bd81be05a64d3ca30bf23c285cdf741.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 1bb961580e20073f66ccb9024f248357f8c8fecb.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 14 files
```

| Directory | What it contains |
|-----------|-----------------|
| `blob/` | Per-file AST graphs, content-addressed by git blob SHA. Each file in the source repo gets its own graph. |
| `aggregate/ast/` | Combined AST graph per parsed commit. Merges all blob graphs for a snapshot of the entire codebase at that point. |
| `aggregate/lsp/` | Language Server Protocol enrichment: resolved symbols, definitions, references, and type information. |
| `aggregate/dataflow/` | Interprocedural data flow edges between functions and modules. |
| `aggregate/repolex/` | Combined graph (AST + LSP + dataflow) per commit. |
| `commit/` | Git commit metadata (author, date, message, parent links). |
| `branch/` | Branch metadata. |
| `tag/` | Tag metadata. |
| `filetree/` | File tree snapshots per commit (which files existed and their blob SHAs). |
| `audit/` | Code architecture and graph audit reports per commit. |

## Source repository

[tox-dev/workflow](https://github.com/tox-dev/workflow)

---
*Parsed on 2026-10-11 by [repolex](https://repolex.ai)*
