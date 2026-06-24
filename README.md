# Interpretable Cardiovascular Disease Prediction Using a Physiologically Grounded Non-Invasive RISK SCORE

[![Python Version](https://img.shields.io/badge/python-3.13-blue.svg)](https://www.python.org/)
[![Framework](https://img.shields.io/badge/framework-PyTorch-orange.svg)](https://pytorch.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

This repository contains the official code pipeline, engineered datasets, and statistical validation suite for the paper **"Interpretable Cardiovascular Disease Prediction Using a Physiologically Grounded Non-Invasive RISK SCORE"**. 

The core thesis of this work is that utilizing pathophysiological domain knowledge into data captures disease variance more effectively than relying on "black-box" neural networks to infer relationships from isolated variables, while strictly preserving transparency in primary care settings.

## Project Overview

* **Objective:** Bridge the gap between predictive performance and clinical transparency by eliminating invasive biomarkers (e.g., Thallium stress testing, coronary angiography) and introducing a non-invasive, interpretable **RISK SCORE**.
* **Core Innovation:** A 0–5 point composite score derived from raw constituent parameters that quantifies cumulative mechanical and chemical strain on the cardiovascular system.
* **Key Findings:** Integrating the RISK SCORE into a transparent Logistic Regression model elevated stratified accuracy to **80.42%** and achieved a **87.07 stratified AUC**, outperforming literature-standard and custom Deep Multilayer Perceptrons (MLPs) under identical non-invasive constraints.

---

## The RISK SCORE Formulation

The RISK SCORE aggregates multiple independent biological pathways into a singular metric:

$$\text{RISK SCORE} = \sum_{i=1}^{5} 1(C_i)$$

Where the conditions $C_i$ are defined as:
* **$C_1$ (Age & Sex Thresholds):** $(\text{Age} > 40 \cap \text{Male}) \cup (\text{Age} > 55 \cap \text{Female})$
* **$C_2$ (Smoking History):** $\text{Cigarettes Daily} > 0$
* **$C_3$ (Blood Sugar):** $\text{Fasting Blood Sugar} = 1 \ (\ge 120 \text{ mg/dL})$
* **$C_4$ (Cholesterol Burden):** $\text{Serum Cholesterol} > 250 \text{ mg/dL}$
* **$C_5$ (Mechanical Strain):** $\text{Resting Blood Pressure} > 120 \text{ mmHg}$

---

## Statistical Validation

Univariate analysis confirms that the consolidated RISK SCORE functions as a superior standalone biomarker compared to raw constituent features:
* **Independent T-Test:** Absolute $t$-statistic of **5.43** ($p = 1.26 \times 10^{-7}$).
* **Univariate Logistic Regression:** Odds Ratio of **1.84** ($95\%$ CI: $[1.45, 2.34]$).
* **Cohen's $d$ Effect Size:** **0.65** (indicates medium-to-large standardized mean separation).
* **Point-Biserial Correlation:** Absolute coefficient of **0.31**, directly rivaling the dataset's strongest standalone clinical features (*Oldpeak* and *Thalach*).

---

## In this repository, there is the complete Jupyter notebook with all of the outputs to show data reproducibility and the custom merged data frame with the new cigarette variable taken from the unprocessed original Cleveland dataset
