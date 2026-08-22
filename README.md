# Applied AI for Information Security

[![Python 3.10+](https://img.shields.io/badge/python-3.10+-blue.svg)](https://www.python.org/downloads/)
[![Jupyter Notebook](https://img.shields.io/badge/Jupyter-Notebook-orange.svg)](https://jupyter.org/)
[![PyTorch](https://img.shields.io/badge/PyTorch-Deep%20Learning-EE4C2C.svg)](https://pytorch.org/)
[![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-Machine%20Learning-F7931E.svg)](https://scikit-learn.org/)
[![Hack The Box](https://img.shields.io/badge/Hack%20The%20Box-AI%20Red%20Teamer-success.svg)](https://academy.hackthebox.com/)

**Author:** Sean Kilfoy  
**Companion to:** Hack The Box Academy — *Applications of AI in InfoSec*

---

## 📑 Quick Links

- 📄 **[Read the Full Technical PDF Report](./Applied%20AI%20for%20Information%20Security.pdf)**
- 📓 **[Open Interactive Notebook](./Applied%20AI%20for%20Information%20Security.ipynb)**
- 🔗 **[GitHub Gist Version](https://gist.github.com/skilfoy/9405902f61061c0110000538c57e984e)**
- 🤖 **[Introduction to Red Teaming AI Notebook](./Introduction%20to%20Red%20Teaming%20AI.ipynb)**
- 📘 **[Introduction to Red Teaming AI PDF Report](./Introduction%20to%20Red%20Teaming%20AI.pdf)**
- 🔗 **[Introduction to Red Teaming AI Gist](https://gist.github.com/skilfoy/800ddaff92e0f7c01001300bcbe48118)**

---

## 🤖 Module: Introduction to Red Teaming AI

**Companion to:** [Hack The Box Academy — Introduction to Red Teaming AI](https://academy.hackthebox.com/app/module/294)

This portfolio artifact documents an end-to-end red-team assessment of machine-learning and generative-AI systems. The accompanying notebook develops a reproducible narrative around model exposure, training-data manipulation, text-generation attacks, data poisoning, and component-level attack surfaces.

The implementation preserves the supplied HTB lab workflow while adding analytical commentary, explicit provenance, reproducibility notes, result interpretation, and a final triggered-poisoning assessment. The compiled PDF provides a reviewable technical report, while the notebook preserves the executable evidence and recorded outputs.

### Assessment Coverage

1. ML-based system architecture and red-team assessment scope
2. Model manipulation and inference-time behavior
3. LLM OWASP Top 10 and text-generation attack surfaces
4. Secure AI architecture through Google’s SAIF
5. Model, data, application, and system component attacks
6. Triggered data poisoning and validation of the resulting model behavior

### Portfolio Artifacts

- [Interactive notebook](./Introduction%20to%20Red%20Teaming%20AI.ipynb)
- [Compiled technical report](./Introduction%20to%20Red%20Teaming%20AI.pdf)
- [GitHub Gist](https://gist.github.com/skilfoy/800ddaff92e0f7c01001300bcbe48118)

---

## 🔍 Executive Overview

This repository houses a comprehensive, portfolio-oriented applied machine learning project spanning several core security data modalities. Rather than treating machine learning as a black box that outputs single aggregate accuracy metrics, the workflow adheres to strict security-engineering principles:

1. **Explicit Data Contracts:** Establishing data provenance, identifying sentinel values, and formalizing validation checks before ingestion.
2. **Leakage-Free Partitioning:** Ensuring zero train-validation-test leakage across structured, NLP, image, and tabular pipelines.
3. **Operationally Meaningful Metrics:** Measuring class-balanced accuracy, precision/recall trade-offs, false positive rates, and macro/weighted F1 scores.
4. **Error & Subgroup Diagnostics:** Inspecting confusion matrices and confidence distributions on rare and critical attack classes.
5. **Reproducible Artifact Packaging:** Serializing, reloading, and smoke-testing deployable inference pipelines (`joblib` and `torch` models).

---

## 🛡️ Modalities & Case Studies

```
Applied AI for Information Security
│
├── 1. Network Event Logs ────────► Data contract, sentinel handling, KNN imputation, Bayes posteriors
├── 2. SMS Spam Detection ────────► NLP normalization, N-grams, tuned Multinomial Naive Bayes
├── 3. Network Anomaly Detection ─► NSL-KDD taxonomy, stratified partitions, Random Forest classifier
├── 4. Malware Image Triage ──────► PE byteplot representations, ResNet-50 transfer learning, early stopping
└── 5. Sentiment Skills Capstone ─► Rerun-safe acquisition, hash leakage audit, exportable text pipeline
```

### 1. Network Event Logs: Establish a Data Contract
- **Problem:** Ingesting and auditing noisy network telemetry with missing values and malformed sentinels (`STRING_PORT`, `NEGATIVE`, `MISSING_IP`).
- **Methods:** Formal regex IP/port validators, median and KNN imputation comparison, log1p byte transformations, and worked Bayesian probability inference.

### 2. SMS Spam Detection: Turn Language into Evidence
- **Problem:** Classifying short, unstructured text communications with severe class imbalance (`ham` vs. `spam`).
- **Methods:** Transparent NLP pipeline (NLTK tokenization, punctuation filtering, Porter stemming, stopword removal), Count/TF-IDF feature representations, and hyperparameter-tuned Multinomial Naive Bayes.

### 3. Network Anomaly Detection: Model Structured Traffic
- **Problem:** Multi-class intrusion detection on the 148k-record NSL-KDD benchmark.
- **Methods:** Mapping raw connection logs to a 5-class attack taxonomy (Normal, DoS, Probe, R2L, U2R), one-hot encoding, stratified cross-validation, and Random Forest feature-importance analysis.

### 4. Malware Image Classification: Learn from Byteplot Structure
- **Problem:** Static PE binary family classification across 9,339 grayscale byteplots (Malimg dataset, 25 malware families).
- **Methods:** Pretrained ResNet-50 transfer learning in PyTorch, class-weighted Cross-Entropy loss, validation loss monitoring with early stopping, and normalized confusion matrix inspection.

### 5. IMDB Sentiment Classification: Skills Assessment Capstone
- **Problem:** End-to-end deployment capstone evaluating pipeline generalization on a large textual corpus.
- **Methods:** SHA-256 hash-based cross-split leakage audit, stratified validation protocol, TF-IDF + Classifier selection, and Joblib artifact smoke testing.

---

## 📊 Repository Structure

```bash
.
├── Applied AI for Information Security.ipynb  # Applications of AI in InfoSec notebook
├── Applied AI for Information Security.pdf    # Applications of AI in InfoSec report
├── Introduction to Red Teaming AI.ipynb       # AI red-teaming assessment notebook
├── Introduction to Red Teaming AI.pdf         # AI red-teaming technical report
├── README.md                                  # Portfolio overview and navigation
├── demo_dataset.csv                           # Sample network log validation data
└── .gitignore                                 # Dataset and artifact exclusion rules
```

---

## 🚀 Reproduction & Setup

1. **Clone the repository:**
   ```bash
   git clone https://github.com/skilfoy/Applied-AI-for-Information-Security.git
   cd Applied-AI-for-Information-Security
   ```

2. **Create and activate a virtual environment:**
   ```bash
   python3 -m venv venv
   source venv/bin/activate
   ```

3. **Install dependencies:**
   ```bash
   pip install pandas numpy scikit-learn matplotlib seaborn torch torchvision nltk joblib
   ```

4. **Launch the notebook:**
   ```bash
   jupyter lab "Applied AI for Information Security.ipynb"
   ```

---

## 📜 License & Acknowledgments

- Built as an analytical extension of the **Hack The Box Academy** module *Applications of AI in InfoSec*.
- Built as a portfolio companion to the **Hack The Box Academy** module *Introduction to Red Teaming AI*.
- Research datasets: NSL-KDD (UNB), SMS Spam Collection (UCI), Malimg (Nataraj et al.), and IMDB Large Movie Review Dataset (Maas et al.).
