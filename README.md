# DSC212 – Modularity on the Karate Club Graph

Research assignment for **DSC212: Graph Theory** (IISER Thiruvananthapuram, Dr. Saptarshi Bej).

**Author:** Vaibhav Sawroop · **Roll No.:** IMS25227

This repository contains a from-scratch implementation of **Newman's spectral modularity method** (recursive bisection using the leading eigenvector of the modularity matrix `B = A − kkᵀ/2m`) applied to Zachary's Karate Club network.

## Contents

| File / folder | Description |
|---|---|
| `Modularity_Karate_Club.ipynb` | The full notebook (code, outputs, visualisations, discussion). Already executed – GitHub shows all results. |
| `figures/` | PNG copies of every figure produced by the notebook. |
| `requirements.txt` | Python dependencies. |

## How to run

```bash
pip install -r requirements.txt
jupyter notebook Modularity_Karate_Club.ipynb     # then: Kernel → Restart & Run All
```

The notebook runs top-to-bottom without manual edits (only `numpy`, `networkx`, `matplotlib`).

## What the notebook does

1. Builds the modularity matrix and checks `B = Bᵀ`, `B·1 = 0`.
2. Recursively bisects communities with the sign of the leading eigenvector of the restricted matrix `B^(C)`.
3. Draws the graph after every split (fixed layout, stable community colours, node IDs).
4. After every split computes degree, betweenness, closeness centrality and clustering coefficient for every node (inside each node's current community) and plots their evolution (line plots + heat-maps).
5. Compares the result with the real split: the first bipartition recovers **33/34** memberships (only node 8 differs); final partition has **5 communities, Q = 0.4094** (real 2-faction split: Q = 0.3582).
6. Discussion of which nodes stay central (nodes 0 and 33) and how community structure shapes each metric.
7. Optional extension: Newman's generalised matrix `B^(g)` and a numerical check of the ΔQ identity.

## Reference

Newman, M. E. J. (2006). *Modularity and community structure in networks.* PNAS 103(23), 8577–8582. https://doi.org/10.1073/pnas.0601602103
