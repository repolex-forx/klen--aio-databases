# Repolex Knowledge Graph of klen/aio-databases

RDF knowledge graph data for [klen/aio-databases](https://github.com/klen/aio-databases), parsed by [repolex](https://repolex.ai).

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
rlex download klen/aio-databases
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── a072cd47cbdf3b8f0b84551da645231db4bc9149
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── a072cd47cbdf3b8f0b84551da645231db4bc9149
│           └── chunk-001.nq.gz
├── blob
│   ├── 0a5870f7c9fc32927a0c1fac4246c7a5817bded0.nq.gz
│   ├── 0b76fa3c5e174b36f9a20c04a8cd34ec11c734f4.nq.gz
│   ├── 2997250e89f56d744ea06954e477dbd62fd16e7c.nq.gz
│   ├── 29c0a10e5fc0a12b6b35d21a2aaf812726e7dafd.nq.gz
│   ├── 33db641ae8c223e04ce2808e4e8f52a2b024f41c.nq.gz
│   ├── 5646acbef0eea39bd8c7390909d57777e0a9df5c.nq.gz
│   ├── 602a75f44acd923adc9aa0d54d590b0c5cf37f9d.nq.gz
│   ├── 700bf5efc73f1387b0c8018981f48e4dcb7c6bcc.nq.gz
│   ├── 7e6f55159f97c43fb8cae53b498ae0c8ef92a56a.nq.gz
│   ├── 7f980ec9b4d75bbd3d8f85228d2cf435ec3913bd.nq.gz
│   ├── 8087b699c8cc40f465355630d01c9695c5a6d68c.nq.gz
│   ├── 81dea268475abbb8621f24ca25a6a8e80a559484.nq.gz
│   ├── 87ce3fd4657944edd067fe0bae1d0c29b9d76cf2.nq.gz
│   ├── 88eafa1529293ee005a11adb646b0c3fa4139a05.nq.gz
│   ├── 8fe5c1a8eb515ddee1571ee91649d0bc07a438f2.nq.gz
│   ├── 90b77142922ba70d99f164906489ab578d9424f1.nq.gz
│   ├── 91643bfe5bd16fa43b4ba1f4e62ea1d9e9dea617.nq.gz
│   ├── 931fa306d77915c3735799ffdf48ade037bdb04f.nq.gz
│   ├── a5b90dfcbfe841d65a866e02ee9067a11b69cd80.nq.gz
│   ├── a95ec691189337fb5ee620553ebf5fb6d5fb8bcf.nq.gz
│   ├── abe8d106e63bed86928077748be669739b9cbafb.nq.gz
│   ├── af180fa5a087d3933f510898f3ce68edacd50444.nq.gz
│   ├── b00c7b5760cc9e91e7e44802b6df0875d29bce7e.nq.gz
│   ├── b1750e0fb7c8cc457432b328ccf7a58723323b4e.nq.gz
│   ├── b2fdb6e5c7d8e5cddb5c201dbad65b19b1567661.nq.gz
│   ├── b4cdf0a28d8615fdd9786ff1f921cac2a3c722fd.nq.gz
│   ├── c74224b9675e914dc8d5af125e64d43c6a66634f.nq.gz
│   ├── c9aba1c5f9280c513f8d53f0d6509c358d45f4b4.nq.gz
│   ├── cc3a30ae02872d17bf5d50eaba5ec2498f220b0b.nq.gz
│   ├── d281ac3d3bae5b785dae17f4a15d1648ffb2ed48.nq.gz
│   ├── dd75aa8b824895f3cec11833412c1712b752d831.nq.gz
│   ├── e103580c6522e03e72e873286fe85ebc7a2b8a67.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   ├── eb986edf784028ad2cff0f7ce03c517b8ee496d9.nq.gz
│   ├── f56dafafb2024556fc294ab458686f8139534e9e.nq.gz
│   ├── f84edc40800659a24115b4ab6a6c69c151c57d22.nq.gz
│   ├── f957260e5c170b93b2c56e9925466b7979bde82a.nq.gz
│   └── fa0b923907752fa9c598699d2418f210e14718af.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── a072cd47cbdf3b8f0b84551da645231db4bc9149.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

12 directories, 45 files
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

[klen/aio-databases](https://github.com/klen/aio-databases)

---
*Parsed on 2026-10-20 by [repolex](https://repolex.ai)*
