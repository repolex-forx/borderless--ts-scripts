# Repolex Knowledge Graph of borderless/ts-scripts

RDF knowledge graph data for [borderless/ts-scripts](https://github.com/borderless/ts-scripts), parsed by [repolex](https://repolex.ai).

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
rlex download borderless/ts-scripts
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 35dceb729b3fabbc1e4b7bc2f2a2d995c75e7bd7
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 35dceb729b3fabbc1e4b7bc2f2a2d995c75e7bd7
│           └── chunk-001.nq.gz
├── blob
│   ├── 186fea85837966698cae558f39d7a90f4f42e47a.nq.gz
│   ├── 1e3944708655fcfe4638683e9adff100c2d001cb.nq.gz
│   ├── 31354ec1389994b5f6708c7d915fdcc6bb76ba6e.nq.gz
│   ├── 323c222c6a2a85284e32421741a0c8d58089580f.nq.gz
│   ├── 39538ba364553eae32233173150c3f85f3b425cd.nq.gz
│   ├── 4830dedd443a864f7d747feb460e2eebfed3402b.nq.gz
│   ├── 4a35c66f173be4cfe06c12c1fdbf90650291fb3c.nq.gz
│   ├── 4aa608f07acdb08e4864860e0e520317cf1f5008.nq.gz
│   ├── 6ba103e82110f469e1f8e8a52d2919608477e58d.nq.gz
│   ├── 6dfb001be290cf4ad76f888a331118d5ab9a7606.nq.gz
│   ├── 7f20ff867ab19eda5879a610737fe91b8c8b2b06.nq.gz
│   ├── 8e84accdea7314d466d82e9b499ad5975c03e46d.nq.gz
│   ├── 9e5edd685469929d28dd5034094cc96053cd4be8.nq.gz
│   ├── b8e7a2ee89ae706a622c406f9ec2721b6d28c4f7.nq.gz
│   └── dc6a075bc8737938bdfb85c44b95f7288c520c3b.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 35dceb729b3fabbc1e4b7bc2f2a2d995c75e7bd7.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 23 files
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

[borderless/ts-scripts](https://github.com/borderless/ts-scripts)

---
*Parsed on 2026-11-10 by [repolex](https://repolex.ai)*
