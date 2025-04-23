# Cytokine Storm Response Comparison Across Diseases

## Overview
This repository contains an R script for analyzing and comparing differential gene expression profiles associated with cytokine storms across multiple diseases:
- COVID-19 (SARS-CoV-2)
- Influenza (H1N1)
- Sepsis
- ARDS (Acute Respiratory Distress Syndrome)
- Original SARS-CoV (2003)

The analysis focuses on identifying common and unique gene expression patterns that may help understand the molecular mechanisms underlying cytokine storms in different disease contexts.

## Dependencies
This analysis requires the following R packages:
- Bioconductor packages: `BiocManager`, `GEOquery`, `limma`, `affy`, `sva`, `AnnotationDbi`, `org.Hs.eg.db`, `ComplexHeatmap`, `biomaRt`, `hgu133plus2.db`, `clusterProfiler`, `STRINGdb`
- CRAN packages: `ggplot2`, `pheatmap`, `RColorBrewer`, `dplyr`, `VennDiagram`, `UpSetR`, `circlize`

## Data Sources
The analysis uses the following GEO datasets:
- GSE164805: COVID-19 patient samples
- GSE213313: COVID-19 patient samples (Prebenson dataset)
- GSE37571: H1N1 Influenza samples
- GSE13904: Sepsis samples

## Analysis Workflow

### 1. Data Processing
For each disease dataset:
- Download expression data from GEO
- Normalize expression data
- Extract sample information and create comparison groups
- Map probe IDs to gene symbols

### 2. Differential Expression Analysis
For each disease:
- Set up design matrix using limma
- Create contrast matrix for disease vs control comparison
- Fit linear models
- Apply empirical Bayes statistics
- Identify differentially expressed genes (DEGs) with criteria:
  - Adjusted p-value ≤ 0.05
  - |log2 fold change| ≥ 1.5

### 3. Visualization
- Generate volcano plots for each disease condition
- Create Venn diagrams and UpSet plots to visualize overlapping DEGs
- Generate heatmaps of logFC values for genes common across diseases

### 4. Cytokine Storm-Specific Analysis
- Compare DEGs with a curated list of cytokine storm-related genes
- Visualize cytokine storm gene overlaps using UpSet plots
- Create heatmaps of cytokine storm genes across conditions

### 5. Functional Enrichment Analysis
- Perform GO enrichment analysis for DEGs from each disease
- Create dotplots of top GO terms for each disease
- Filter for immune-related GO terms
- Generate heatmaps comparing GO term enrichment across diseases

## Output Files
The script generates multiple visualization outputs:
- Volcano plots for each disease condition
- Venn diagram comparing DEGs across diseases (`venn_diagram_comparison.png`)
- UpSet plot for cytokine storm genes (`cytokine_upset.png`)
- Heatmap of cytokine storm genes (`cytokine_heatmap_logFC.png`)
- GO term enrichment plots and heatmaps in the `GO_Plots` directory

## Usage
1. Ensure all required packages are installed
2. Run the entire script in RStudio or via command line
3. Results will be generated in the working directory and the `GO_Plots` subdirectory

## Notes
- The script includes helper functions for normalization, probe processing, and visualization
- For gene ontology analysis, results are filtered for both all terms and immune-specific terms
- The analysis framework can be extended to include additional diseases by following the same workflow pattern

## Author
Noah Hamilton

## Date
Generated on: April 23, 2025
