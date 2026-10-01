# Drug-Drug Interaction Prediction

Artifacts for the CCS2026 drug-drug interaction prediction study.

## Repository contents

- `Drug_Drug_Interaction_CCS2026.ipynb`: analysis and experiment notebook.
- `data/`: source data, canonicalized drug records, labels, and audit outputs.
- `features/`: molecular fingerprints, transformer embeddings, and feature metadata.
- `splits/`: frozen known-drug and cold-start evaluation partitions.
- `preds/`: saved predictions for the evaluated models and protocols.
- `tables/`: comparison, ablation, similarity, bootstrap, and audit tables.
- `figs/`: generated figures in PNG and PDF formats.
- `frozen.json`: finalized experiment configuration and selection record.

Training checkpoints and intermediate run directories are intentionally excluded from this repository. The `runs/` directory is ignored by Git.

## Evaluation design

The repository includes a known-drug split and three cold-start partitions (`cold0`, `cold1`, and `cold2`). Results cover standard evaluation as well as one-unseen and two-unseen drug settings. The primary selection metric is `macro_f1_all`, with model comparisons and partition-level results available under `tables/`.

The frozen configuration uses:

- A graph neural network as the selected neural model.
- XGBoost as the baseline model.
- 1,024-bit radius-2 molecular fingerprints for the fingerprint features.
- Grouped drug identities to prevent identity leakage across splits.
- Validation-only treatment selection, with a minimum improvement threshold of `0.005` over the unweighted alternative.
- Three cold-start seeds and bootstrap intervals with 1,000 repeats where reported.

## Reproducibility

The committed split files, feature arrays, predictions, tables, figures, and `frozen.json` provide the finalized experiment record. The notebook contains the analysis workflow used to inspect and compare these artifacts.

The raw data files may be subject to the terms of their original source. Verify the applicable data-use requirements before redistributing or reusing them.
