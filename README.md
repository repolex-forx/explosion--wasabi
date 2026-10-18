# Repolex Knowledge Graph of explosion/wasabi

RDF knowledge graph data for [explosion/wasabi](https://github.com/explosion/wasabi), parsed by [repolex](https://repolex.ai).

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
rlex download explosion/wasabi
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── ddcb05ac1e27ca564a46ba9ae55b79aef3d99bbb
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── ddcb05ac1e27ca564a46ba9ae55b79aef3d99bbb
│           └── chunk-001.nq.gz
├── blob
│   ├── 02273e6b8124b3813d73a5a4e78aa01c43ad1cd1.nq.gz
│   ├── 04bd6f6dd17e934d584a8d000b9116af5f9c7b2c.nq.gz
│   ├── 04f50aa304f891a3b0412cba15094c12cad9f6e0.nq.gz
│   ├── 16d8d4a66c09ea08932e93382a18e0fbb51d8949.nq.gz
│   ├── 32c198028ceacaa821cfb9e5f723f0ee17acbbdc.nq.gz
│   ├── 65d06d6197f501fda97deb110861f0f8d4340027.nq.gz
│   ├── 687827a4ad2e1094e9c40000949d4143e42a1619.nq.gz
│   ├── 694166b0db290ce3466315b9b1d1321796cc5eb7.nq.gz
│   ├── 882362d2316b2660cb192f188c1506703332db1b.nq.gz
│   ├── 9dff68e98b53d039f92cac5530b43ba99019a410.nq.gz
│   ├── 9e6b1ff551ca99ef78b8b9cc9241c9fe3a206146.nq.gz
│   ├── 9fe54d3f261707571608d400053e4de28d8c718a.nq.gz
│   ├── a4da55492af024fcc7c25a5f857e595a5cd92345.nq.gz
│   ├── ac46402056a55ae34cd45ef49ac9005d8abd6474.nq.gz
│   ├── b158a8433804a2dd15d0d21d653775180431e3d9.nq.gz
│   ├── bdfb798b3cec59facf10e9925dcb377675154135.nq.gz
│   ├── c2d46c0ecea4db6ae6bb163d625458dde4d1cf4f.nq.gz
│   ├── d0fc488b35dfcbb4bc55be9c0b06d5100833d705.nq.gz
│   ├── d5c75c8553a83b941c6439bc71455c75fe166b53.nq.gz
│   ├── dd5b92db381f4ab9c2f990dc50de5f8113d7bfa1.nq.gz
│   ├── dee27c4ceea340216b1c24a44721c3cc9d13247a.nq.gz
│   ├── e33da3ce72e11bfbe26883f1126d8c6552b5d781.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   └── f07fa62615b6a18e8fae592a08758a4e8bd8083e.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── ddcb05ac1e27ca564a46ba9ae55b79aef3d99bbb.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 32 files
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

[explosion/wasabi](https://github.com/explosion/wasabi)

---
*Parsed on 2026-10-18 by [repolex](https://repolex.ai)*
