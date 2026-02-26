# 🧠 Data-Efficient CNN–ViT Hybrid for Alzheimer’s Disease Severity Classification

> 📄 Detailed experimental results, ablation studies, and extended analysis are available in the project presentation:  
> **[View Final Presentation (PDF)](docs/Alzheimer_CNN-ViT_Hybrid_Report.pdf)**

A research-oriented exploration of hybrid inductive bias and self-attention mechanisms under data-constrained medical imaging settings.
---

## 1. Problem Definition

Early-stage Alzheimer’s disease diagnosis is particularly challenging due to:

- Subtle visual differences between **NonDemented** and **VeryMildDemented** cases  
- Class imbalance in medical datasets  
- Limited availability of labeled MRI data  

This project investigates whether a **CNN–ViT hybrid architecture** can improve boundary classification under data-constrained settings.

Rather than focusing solely on accuracy, we emphasize:

- Boundary error reduction  
- Model calibration reliability  
- Attention interpretability  

---

## 2. Research Hypothesis

We hypothesize that:

> Combining CNN-based local feature extraction with Transformer-based global self-attention improves classification robustness in limited medical datasets.

Specifically, we expect:

- Reduced confusion between **NonDemented** and **VeryMildDemented** classes  
- More stable confidence calibration  
- Improved attention localization in MRI regions  

---

## 3. Dataset

- **Augmented Alzheimer MRI Dataset**
- 4 classes:
  - NonDemented
  - VeryMildDemented
  - MildDemented
  - ModerateDemented

### Dataset Characteristics

- Class imbalance (especially *ModerateDemented*)
- Medical imaging domain with subtle inter-class variation

---

## 4. Model Development Process

### 4.1 ViT Baseline

- Implemented using `timm`
- Patch-based transformer encoder
- Observed significant confusion at early-stage boundary

**Limitations**

- Data-hungry architecture  
- Weak local inductive bias  

---

### 4.2 DeiT-S (Distilled Vision Transformer)

- Introduced knowledge distillation from CNN teacher
- Improved training stability
- Partial boundary improvement

**Insight**

Distillation improves optimization but does not fully compensate for lack of local feature bias.

---

### 4.3 CNN–ViT Hybrid Architecture (Final Model)

**Architecture Design**

- CNN backbone for local spatial feature extraction  
- Transformer encoder for global contextual reasoning  

**Rationale**

- CNN provides strong inductive bias under limited data  
- Self-attention identifies globally relevant features  

**Results**

- Reduced misclassification at Non vs VeryMild boundary  
- Improved training stability  
- More interpretable attention maps  

---

## 5. Model Evaluation & Analysis

We evaluated models using:

- Accuracy  
- Macro F1-score  
- Confusion matrix analysis  
- Temperature scaling for calibration  
- Attention Rollout visualization  

### Key Findings

- Hybrid model reduced early-stage boundary confusion  
- Calibration improved reliability in high-confidence predictions  
- Attention maps showed meaningful activation patterns in relevant regions  

---

## 6. Discussion

This study suggests that:

- Pure ViT architectures may underperform in small medical datasets  
- Hybrid models better leverage both inductive bias and global reasoning  
- Model reliability (calibration) is crucial in medical AI systems  

---

## 7. Limitations

- Dataset size limitations  
- No external validation dataset  
- MRI preprocessing variability not extensively explored  

---

## 8. Future Research Directions

- Multi-modal fusion (MRI + clinical metadata)  
- Self-supervised pretraining for medical images  
- Uncertainty-aware prediction frameworks  
- Edge deployment feasibility analysis  

---

## 9. Technical Stack

- Python  
- PyTorch  
- timm  
- scikit-learn  
- NumPy  
- Matplotlib  

---