# Top-K Stock Prediction using HGAT and LSTT

![Project Pipeline](images/pipeline.png)

**Full Project Report**: [View the complete technical report online](https://www.overleaf.com/read/rxmfbswgrvfq#61a0c2)
## Table of Contents
1. [Project Overview](#project-overview)
2. [Repository Structure](#repository-structure)
3. [Installation](#installation)
4. [Data Preparation](#data-preparation)
5. [Running the Project](#running-the-project)
6. [Results](#results)
7. [Contributors](#contributors)
8. [License](#license)

## Project Overview
This project predicts top-K profitable stocks from NIFTY 500 using:
- **LSTT (Long Short-Term Transformer)**: Processes 5-day price windows
- **HGAT (Hierarchical Graph Attention Network)**: Models sector relationships
- **Fused Embeddings**: Combines temporal and graph features

Key Features:
- Processes 3 years of historical data (2022-2025)
- Implements 9-stage prediction pipeline
- Evaluates using MRR@K and Precision@K metrics

## Repository Structure
```
stock-prediction/
├── data/
│   ├── filtered_companies.csv         # Stock symbols and sectors
│   └── sector_mapping.csv             # Stock-to-sector mapping
├── notebooks/
│   └── Stock_Prediction_Pipeline.ipynb # Main executable notebook
├── images/                            # Visualization files
│   ├── pipeline.png                   # Architecture diagram
│   └── results.png                    # Performance metrics
└── phase_outputs/                     # Auto-created during execution
    ├── 1_Stock_Data/                  # Raw downloaded data
    ├── 2_Cleaned_Data/                # Processed OHLCV data
    ├── 3_Reference_Data/              # Date-aligned stocks
    ├── 4_Final_Data/                  # Features added
    ├── 5_Split_Data/                  # Train/Test split
    ├── 6_Sliding_Window/              # 5-day sequences
    ├── 7_LSTT_Embeddings/             # Transformer outputs
    ├── 8_HGAT_Embeddings/             # Graph network outputs
    └── 9_Fused_Embeddings/            # Final combined features
```

## Installation

1. **Create a virtual environment (optional but recommended)**
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

2. **Install dependencies**
   ```bash
   pip install pandas numpy matplotlib seaborn scikit-learn torch networkx
   ```

## Data Preparation

1. **Input CSV Files**
   Place the following files in the `data/` directory:
   - `filtered_companies.csv`: Contains stock symbols and sectors
   - `sector_mapping.csv`: Maps stocks to their sectors

2. **Execution Pipeline**
   The entire processing pipeline is defined in the Jupyter notebook:
   - Downloads stock data
   - Maps stocks to sectors
   - Processes OHLCV data
   - Generates LSTT and HGAT embeddings
   - Combines features for prediction

## Running the Project

1. Open the notebook:
   ```
   notebooks/Stock_Prediction_Pipeline.ipynb
   ```

2. Run all cells sequentially to:
   - Generate phase-wise outputs
   - Extract features
   - Output top-K predicted stocks

3. Results are saved in the `phase_outputs/` folder.

## Results

![Results Visualization](images/result.jpg)

- Predicts top-K profitable stocks
- Evaluation metrics:
  - **MRR@K**: Mean Reciprocal Rank at K
  - **Precision@K**: Precision at top-K
- Visual results saved in:
  ```
  images/results.png
  ```

## Contributors

- **Your Name** – Core development, pipeline design, and model integration

## License

This project is licensed under the MIT License.
