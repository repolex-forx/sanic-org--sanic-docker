# Repolex Knowledge Graph of sanic-org/sanic-docker

RDF knowledge graph data for [sanic-org/sanic-docker](https://github.com/sanic-org/sanic-docker), parsed by [repolex](https://repolex.ai).

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
rlex download sanic-org/sanic-docker
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 3406c70aeb287193750b281e59d3bd2b1239f8e8
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 3406c70aeb287193750b281e59d3bd2b1239f8e8
│           └── chunk-001.nq.gz
├── blob
│   ├── 6b8d18bad35546c6d92ee472b8c6349d17c148bc.nq.gz
│   ├── 6d95da4461c7a0eab4e4bbf29386d809f9ceda20.nq.gz
│   ├── 7302f570550f283090610b13687217a67dc3eae9.nq.gz
│   ├── 7495b8be3559caae10d2e8ea00ada47405c98f29.nq.gz
│   ├── 812c8419831ccd89ba0351fa94c48ad17cbc8f35.nq.gz
│   ├── b95a46fff1606d824cac3175f2a29d06e9f6b369.nq.gz
│   └── e5d17c1e053b82d5fd6174fed01355e93bd939e9.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 3406c70aeb287193750b281e59d3bd2b1239f8e8.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 15 files
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

[sanic-org/sanic-docker](https://github.com/sanic-org/sanic-docker)

---
*Parsed on 2026-10-21 by [repolex](https://repolex.ai)*
