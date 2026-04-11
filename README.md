# Prior Prejudice: LLM-as-Judge is Biased by Its Own Beliefs
### ACL 2026 Findings

[![ACL 2026 Findings](https://img.shields.io/badge/Venue-ACL%202026%20Findings-green?style=flat-square)](https://aclanthology.org)
[![Dataset](https://img.shields.io/badge/Dataset-ConvinceQA%2027k-blue?style=flat-square)](#)
[![License](https://img.shields.io/badge/License-CC%20BY%204.0-orange?style=flat-square)](#)

**Pardis Sadat Zahraei · Xiaoning Wang · Nimet Beyza Bozdag · Gokhan Tur · Dilek Hakkani-Tür**  
University of Illinois Urbana-Champaign

> *"A bare assertion the model agrees with scores higher than a well-crafted argument it opposes — even when explicitly told to judge rhetoric alone."*

---

## TL;DR

LLMs used as judges conflate their trained beliefs with rhetorical quality. We demonstrate this across 15 models and 27,756 arguments, establish causality via a fictional character fine-tuning experiment, show it replicates across fact-checking / essay scoring / debate judging, and trace the root cause to asymmetries in safety alignment training data.

---

## Repository Structure

```
prior-prejudice/
│
├── index.html              ← GitHub Pages website
├── README.md
│
├── img/                    ← Drop your paper figures here
│   ├── fig3_prior_prejudice_bars.png
│   ├── fig4_delta_analysis.png
│   ├── fig8_sex_positive_heatmap.png
│   ├── fig9_sex_negative_heatmap.png
│   ├── fig10_race_positive_heatmap.png
│   ├── fig11_race_negative_heatmap.png
│   ├── fig12_political_positive.png
│   ├── fig13_political_negative.png
│   ├── fig14_leaders_positive.png
│   ├── fig20_country_positive.png
│   └── fig30_subjective_control.png
│
├── data/
│   └── convince_qa_sample.json    ← Small public sample
│
└── src/
    ├── evaluate_persuasion.py
    ├── probe_reveal_qa.py
    └── compute_cwa.py
```

---

## How to Launch GitHub Pages (Step-by-Step)

### Step 1: Create the repository
1. Go to [github.com/new](https://github.com/new)
2. Name it `prior-prejudice` (or any name you like)
3. Set it to **Public**
4. Click **Create repository**

### Step 2: Upload files
Option A — GitHub web interface (easiest):
1. Click **"uploading an existing file"** on the new repo page
2. Drag and drop `index.html` and `README.md`
3. Click **Commit changes**

Option B — Git command line:
```bash
git clone https://github.com/YOUR_USERNAME/prior-prejudice.git
cd prior-prejudice
cp /path/to/index.html .
cp /path/to/README.md .
git add .
git commit -m "Add GitHub Pages site"
git push origin main
```

### Step 3: Enable GitHub Pages
1. Go to your repo on GitHub
2. Click **Settings** (top right tab)
3. Scroll down to **Pages** in the left sidebar
4. Under **Source**, select **"Deploy from a branch"**
5. Choose **main** branch and **/ (root)** folder
6. Click **Save**

### Step 4: Your site is live
After ~2 minutes, your site will be at:
```
https://YOUR_USERNAME.github.io/prior-prejudice/
```

---

## Adding Your Actual Paper Figures

Replace the placeholder `<div class="chart-placeholder">` blocks in `index.html` with real images. Example:

```html
<!-- Find this -->
<div class="chart-placeholder" style="margin-top:36px;">
  <div class="ph-label">Figure 3 · Replace with actual figure</div>
  ...
</div>

<!-- Replace with this -->
<img src="img/fig3_prior_prejudice_bars.png"
     alt="Prior prejudice across all 15 models and claim categories"
     style="width:100%;border-radius:4px;border:1px solid #2a2a35;margin-top:36px;"/>
```

Make sure to create the `img/` folder in your repo and upload all figures there.

---

## Updating Links

In `index.html`, search for `href="#"` and replace with your actual URLs:

| Placeholder | Replace with |
|---|---|
| `📄 ACL 2026 Paper` button | ACL Anthology URL |
| `📦 ConvinceQA Dataset` button | Your dataset URL / form |
| `💻 Code & Pipeline` button | This GitHub repo URL |

---

## Key Results Summary

| Stage | Harm Δ (T1) | Misinfo Δ (T1) |
|---|---|---|
| Tulu-3 SFT | +1.97 | +2.44 |
| **Tulu-3 DPO ▲** | **+2.44** | **+3.29** |
| Tulu-3 RLVR | +2.38 | +3.14 |

| Task | Max Effect Size |
|---|---|
| Persuasion evaluation | +3.4 pts on 6-pt scale |
| Fact-checking (RAG override) | 39–90% document override rate |
| Essay quality assessment | −3.40 pts for false-claim essays |
| Debate judging | +2.22 pts for true-side debater |

---

## Citation

```bibtex
@inproceedings{zahraei2026prior,
  title     = {Prior Beliefs Prejudice {LLM}-as-Judge: Evidence from Persuasion Evaluation},
  author    = {Zahraei, Pardis Sadat and Wang, Xiaoning and Bozdag, Nimet Beyza
               and Tur, Gokhan and Hakkani-T{"{u}}r, Dilek},
  booktitle = {Findings of the Association for Computational Linguistics: ACL 2026},
  year      = {2026},
  publisher = {Association for Computational Linguistics}
}
```

---

## Ethical Statement

ConvinceQA contains persuasive arguments supporting harmful stereotypes and misinformation claims, generated solely for research on LLM evaluation behavior. Full dataset access requires institutional affiliation and signed responsible-use agreement prohibiting misuse.
