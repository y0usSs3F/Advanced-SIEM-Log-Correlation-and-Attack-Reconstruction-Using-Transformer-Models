# Advanced-SIEM-Log-Correlation-and-Attack-Reconstruction-Using-Transformer-Models

# Advanced SIEM Dataset — Transformer Correlation & Attack Reconstruction (CSCI590 INS Assignment 2)

This repository implements an end-to-end SIEM analytics pipeline on the **Advanced_SIEM_Dataset**:
1) **Data preparation + preprocessing** (unify multi-source logs, clean, encode, label, build sequences)  
2) **Exploratory Data Analysis (EDA)** (distributions, temporal patterns, correlation heatmap)  
3) **Transformer correlation engine** (two models: baseline Transformer encoder classifier + BERT-style masked modeling)  
4) **Attack reconstruction module** (link anomalous events into multi-stage attack chains using ≥2 methods)  
5) **Final evaluation & reporting artifacts** (metrics tables + plots)

---

## Assignment Summary (What this repo delivers)

### Phase 1 — Data Preparation & Preprocessing
- Loads the dataset and organizes it into a clean **unified events table**.
- Standardizes timestamps, handles missing values, encodes categorical features, scales numeric features.
- Derives **multi-stage attack labels** (0..5) and builds fixed-length **sequence windows** for Transformers.
- Saves processed artifacts under `data/processed/`.

### Phase 2 — Exploratory Data Analysis (EDA)
- Generates required visualizations (at least 3):
  - Log source / event type distributions
  - Attack stage distribution (class imbalance)
  - Temporal patterns
  - Correlation heatmap (numeric features)
- Saves plots under `results/eda/`.

### Phase 3 — Correlation Engine Development (Transformer Models)
Trains and compares **two Transformer models**:
- **Model 1 (Baseline):** Transformer Encoder Classifier (positional encoding + encoder layers + classifier head).
- **Model 2 (BERT-style):** masked event modeling pretraining + fine-tuning for stage classification.

Outputs:
- Saved checkpoints under `results/phase3/`
- Predictions/probabilities for evaluation
- Optional attention matrices for interpretability

### Phase 4 — Attack Reconstruction Module
Goal: use trained Transformer outputs to link anomalies into coherent **multi-stage attack chains**.

Implemented reconstruction methods (≥2):
- **Method B:** Attention-based event linkage
- **Method D:** Graph reconstruction using weighted correlations (attention + time proximity + entity match)

Outputs (required):
- `results/reconstruction/reconstructed_chains.json`
- `results/reconstruction/chain_1_timeline.png`
- `results/reconstruction/chain_1_graph.png`

### Phase 5 — Final Evaluation & Reporting Artifacts
Produces and saves:
- Accuracy, precision, recall, F1-score tables
- Confusion matrix heatmaps
- ROC/AUC plots (OvR) if probabilities are saved
- Reconstruction summary and example chain views

All saved under `results/phase5/`.

---

## Dataset Source
Dataset name: **Advanced_SIEM_Dataset**  
Source (Hugging Face):  
https://huggingface.co/datasets/darkknight25/Advanced_SIEM_Dataset/

The dataset is provided as JSONL. In Phase 1 we also derive multi-source CSV files (IDS / Firewall / System-like logs) to match the assignment’s “multiple log files” description.

---

## Repository Structure

