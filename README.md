# Modularity on the Karate Club Graph

## Overview

This project explores community detection in a social network using **recursive spectral modularity partitioning**.

The analysis uses Zachary's Karate Club graph, a well-known network dataset containing 34 nodes and 78 edges. The objective is to identify communities in the network, visualize the partitioning process, and examine how the structural importance of individual nodes changes as the network is divided.

## Objectives

- Construct the adjacency matrix and modularity matrix of the Karate Club graph.
- Implement spectral community detection using eigenvalues and eigenvectors.
- Apply recursive modularity-based partitioning.
- Visualize the detected communities after each successful split.
- Calculate degree centrality, betweenness centrality, closeness centrality, and clustering coefficient.
- Examine the evolution of these network metrics across successive partitions.

## Methodology

The project begins by constructing the global modularity matrix:

$$
B = A - \frac{kk^T}{2m}
$$

where:

- $A$ is the binary adjacency matrix.
- $k$ is the vector of node degrees.
- $m$ is the total number of edges.

The leading eigenvector is used to determine an initial division of the network.

The notebook also demonstrates an initial recursive approach using restricted modularity matrices and discusses a limitation encountered when the leading eigenvector does not produce two nonempty groups.

A diagonally corrected modularity matrix is then used for the corrected recursive method:

Proposed splits are evaluated using modularity gain. Splits that do not improve modularity are rejected.

## Results

The corrected recursive algorithm identifies **four communities**, containing:

| Community | Number of nodes |
|---|---:|
| 1 | 7 |
| 2 | 9 |
| 3 | 12 |
| 4 | 6 |

The final partition achieves a modularity score of approximately **0.3934**.

The notebook also includes visualizations of the community structure and plots showing the evolution of four network metrics for individual nodes.

## Network Metrics

The following measures are calculated on the induced subgraphs of the detected communities at each partitioning iteration:

1. **Degree Centrality** – Measures the proportion of nodes directly connected to a given node.
2. **Betweenness Centrality** – Measures how frequently a node lies on shortest paths between other nodes.
3. **Closeness Centrality** – Measures how close a node is to the other nodes based on shortest-path distances.
4. **Clustering Coefficient** – Measures how interconnected a node's neighbours are.

## Technologies Used

- Python
- Jupyter Notebook
- NumPy
- NetworkX
- Matplotlib

## Installation and Execution

### 1. Clone the repository

```bash
git clone <https://github.com/xryxnw/graphtheory>
cd <graphtheory>
```

### 2. Install the required libraries

```bash
pip install numpy networkx matplotlib jupyter
```

### 3. Launch Jupyter Notebook

```bash
jupyter notebook
```

### 4. Run the notebook

Open `assignment.ipynb` and select **Kernel → Restart & Run All** to execute the notebook from beginning to end.

## Project Structure

```text
graphtheory/
│
├── assignment.ipynb
└── README.md
```

## References

1. Newman, M. E. J. (2006). Modularity and community structure in networks. *Proceedings of the National Academy of Sciences*, 103(23), 8577–8582.
2. Zachary, W. W. (1977). An information flow model for conflict and fission in small groups. *Journal of Anthropological Research*, 33(4), 452–473.
3. [NetworkX Documentation](https://networkx.org/documentation/stable/)
4. [NumPy Documentation](https://numpy.org/doc/)

---

**Course:** DSC212 – Graph Theory  
**Project:** Modularity on the Karate Club Graph