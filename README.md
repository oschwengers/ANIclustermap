# ANIclustermap: Draw Clustermap of All-vs-All ANI

![Python3](https://img.shields.io/badge/Language-Python3-steelblue)
![OS](https://img.shields.io/badge/OS-Mac_|_Linux-steelblue)
![License](https://img.shields.io/badge/License-MIT-steelblue)
[![Latest PyPI version](https://img.shields.io/pypi/v/aniclustermap.svg)](https://pypi.python.org/pypi/aniclustermap)

## Overview

ANIclustermap is easy-to-use tool for drawing ANI clustermap between all-vs-all microbial genomes.

![ANIclustermap.png](https://raw.githubusercontent.com/moshi4/ANIclustermap/main/images/minimal_dataset/ANIclustermap_annotation.png)  

## Installation

ANIclustermap is implemented in Python3. [fastANI](https://github.com/ParBLiSS/FastANI) is required to calculate ANI.

Install PyPI stable version with pip:

    pip install aniclustermap

Install latest development version with pip:

    pip install git+https://github.com/moshi4/ANIclustermap.git

## Workflow

Description of ANIclustermap's automated workflow.

1. Calculate ANI between all-vs-all microbial genomes by fastANI.  
   If similarity between genomes is low, fastANI output NA. In that case, NA is replaced by 0.0.
2. Clustering ANI matrix by scipy's UPGMA method.  
3. Using clustered matrix, drawing clustermap by seaborn.  

## Usage

### Basic Command

    ANIclustermap -i [Genome fasta directory] -o [output directory]

### Options

    -h, --help           show this help message and exit
    -i I, --indir I      Input genome fasta directory (*.fa|*.fna[.gz]|*.fasta)
    -o O, --outdir O     Output directory
    -t , --thread_num    fastANI thread number parameter (Default: MaxThread - 1)
    --fig_width          Figure width (Default: 10)
    --fig_height         Figure height (Default: 10)
    --dendrogram_ratio   Dendrogram ratio to figsize (Default: 0.15)
    --cmap_colors        cmap interpolation colors parameter (Default: 'lime,yellow,red')
    --cmap_gamma         cmap gamma parameter (Default: 1.0)
    --annotation         Show ANI value annotation (Default: OFF)
    -v, --version        Print version information

### Example Command

    ANIclustermap -i ./example/input/minimal_dataset/ -o ./aniclustermap_result

## Output Contents

ANIclustermap outputs 3 types of files.

- **`ANIclustermap.[png|svg]`**  
  ANI clustermap result figure.
  ![ANIclustermap.png](https://raw.githubusercontent.com/moshi4/ANIclustermap/main/images/minimal_dataset/ANIclustermap.png)  

- **`ANIclustermap_matrix.tsv`** ([example](https://github.com/moshi4/ANIclustermap/blob/main/example/output/minimal_dataset/ANIclustermap_matrix.tsv))  
  Clustered all-vs-all ANI matrix.

- **`ANIclustermap_dendrogram.nwk`** ([example](https://github.com/moshi4/ANIclustermap/blob/main/example/output/minimal_dataset/ANIclustermap_dendrogram.nwk))  
  Newick format clustering dendrogram.
