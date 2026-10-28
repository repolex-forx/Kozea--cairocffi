# Repolex Knowledge Graph of Kozea/cairocffi

RDF knowledge graph data for [Kozea/cairocffi](https://github.com/Kozea/cairocffi), parsed by [repolex](https://repolex.ai).

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
rlex download Kozea/cairocffi
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 9cea02daaf15a41172f6e27788506a8328d2ef16
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 9cea02daaf15a41172f6e27788506a8328d2ef16
│           └── chunk-001.nq.gz
├── blob
│   ├── 009d8e936de6fd2faec5612ec344296b6ba0c53c.nq.gz
│   ├── 0183c358e20b9604b9add6b4413a5cb11c5c2765.nq.gz
│   ├── 06ff6a09e13599961f12d382c3360668ed63d86c.nq.gz
│   ├── 1241ac0d4b4d532645f9c6357ffbc278ac5aea00.nq.gz
│   ├── 156ca6a2c14d43b53990e57d5da611eba14092a4.nq.gz
│   ├── 1b4b8afc1eb5e21169e2141dde59937f531333dc.nq.gz
│   ├── 1b92c7e3ab7f2a324f88e5622d1b9700cee530c0.nq.gz
│   ├── 2ea10e51cb6ee9e9ff79450c7f26296d029c8b3a.nq.gz
│   ├── 304ea70732b1230215ce2662faa3c540cf559214.nq.gz
│   ├── 311b181a2f869582ddb7406eff9bac65962ddd95.nq.gz
│   ├── 323e6bf5b9321157696c5328c04e12f71e10cff7.nq.gz
│   ├── 3f5a26afc93a0e3bdf5621a48ad98239554b3d6c.nq.gz
│   ├── 4772a10c517f27034c513cf1d0caa8c87671d359.nq.gz
│   ├── 49519677dcf19eeaf784030b266587c3d408be2c.nq.gz
│   ├── 513e1833178138eb10ce14e1150d8955d32d528b.nq.gz
│   ├── 5960c98dd48acd9c984913a203a12975f7f41ab8.nq.gz
│   ├── 5bafa4bb6f4f77f8dcef9f6a275aa432cde9e32c.nq.gz
│   ├── 5dc79c4575c28645b1f46fd28f3133c07b23246c.nq.gz
│   ├── 5e7380efb90325b44eadf4cccf3542b7290c1577.nq.gz
│   ├── 61953cfed60623f065b76dc4f03725e7cd2e1520.nq.gz
│   ├── 6390936c7599e605a6c00100d52826ad24bad80b.nq.gz
│   ├── 7593d26bbc33777a816516200b7dfce16899c2ec.nq.gz
│   ├── 8f685adbc925533da676ee5af9d2a8c80fb1f85e.nq.gz
│   ├── 9142ae9cb80731ae6b87f69d40e497616f0569d0.nq.gz
│   ├── 964e3cd5050a1a95aa52fcfa0cb513fcbf5e794b.nq.gz
│   ├── a8cd8e1e1c61b6e1725184d9744d8ed227f157a3.nq.gz
│   ├── afe5a5e0db7229324707c3a8dea4c08f7d9d32e9.nq.gz
│   ├── b5f1fd80ec810772a42286fb5e04846ec976bc3d.nq.gz
│   ├── b706a46f64658c49f65be595118b378a05ebf361.nq.gz
│   ├── b8a8eef09fec4f33a46b0736219c6b70b57efda0.nq.gz
│   ├── b970abe315a73fe8795156a32f8baab15ccb8865.nq.gz
│   ├── ba86d46a77efe4c5a9143ae7ac52b50d74d46362.nq.gz
│   ├── bc417e79ff621d9688194d5c5af16a33cb1a94e1.nq.gz
│   ├── bc5e4c0e1943baba586904999f3cd6532f839e75.nq.gz
│   ├── c42213ba4de3e55e50ac5eea43df9672aa73416b.nq.gz
│   ├── d1106d665e35b485dbb25b977e98618fa947e36d.nq.gz
│   ├── f727050957b22bb955156ef49ad3879f573aa404.nq.gz
│   └── fd5c01f5069051da5eb81ec1ff3f32ac71219dfa.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 9cea02daaf15a41172f6e27788506a8328d2ef16.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 46 files
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

[Kozea/cairocffi](https://github.com/Kozea/cairocffi)

---
*Parsed on 2026-10-28 by [repolex](https://repolex.ai)*
