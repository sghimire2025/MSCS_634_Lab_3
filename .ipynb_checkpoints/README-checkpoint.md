# MSCS 634 Lab 3 — Clustering (Wine Dataset)

**Name:** Suresh Ghimire  
**Course:** Advanced Big Data and Data Mining (MSCS-634-M20)  
**Lab:** Clustering Using K-Means and K-Medoids (Wine Dataset)

---

## Overview / Purpose
In this lab, I explored clustering techniques using the Wine dataset from `sklearn`. I implemented **K-Means** and **K-Medoids** (k = 3) and compared their clustering quality using:

- **Silhouette Score** (how well-separated and compact the clusters are)
- **Adjusted Rand Index (ARI)** (how closely the clustering matches the true class labels)

This helped me understand the full clustering workflow (preprocessing → clustering → evaluation → visualization) and when each algorithm is a better fit.

---

## Repository Contents
- `MSCS_634_Lab_3.ipynb` — Jupyter notebook covering Steps 1–4
- `screenshots/` — screenshots captured for each step
- `pyproject.toml`, `uv.lock` — dependency + lock files (uv-based)

---

## How to Run

### Option A — Using `uv` (recommended)
If your repo includes `pyproject.toml` + `uv.lock`, you can run:

```bash
uv sync
uv run jupyter lab
```

> If Jupyter isn’t included in your project dependencies, install it once:
```bash
uv add --dev notebook jupyterlab
uv sync
uv run jupyter lab
```

### Option B — Using pip (simple)
```bash
python -m venv .venv
# Windows:
.venv\Scripts\activate
# macOS/Linux:
# source .venv/bin/activate

pip install -r requirements.txt  # if you have one
pip install notebook jupyterlab scikit-learn pandas matplotlib
jupyter lab
```

---

## Step-by-Step Summary (with Screenshot Placeholders)

### Step 1 — Load and Prepare the Dataset
- Loaded the Wine dataset using `sklearn.datasets.load_wine`
- Performed basic exploration (head, missing values, stats, class distribution)
- Standardized the dataset using **z-score normalization** (`StandardScaler`)

**Screenshot (Data Collection and Scaled Data):**  
![Data Collection](screenshots/data_collection.png)
![Scaled Data](screenshots/scaled_data.png)


---

### Step 2 — Implement K-Means Clustering (k = 3)
- Trained K-Means with **k = 3**
- Generated cluster labels
- Calculated:
  - Silhouette Score
  - Adjusted Rand Index (ARI)

**Screenshot (K Means Clustering):**  
![K Means Clustering](screenshots/k_means_clustering.png)

---

### Step 3 — Implement K-Medoids Clustering (k = 3)
- Trained K-Medoids with **k = 3**
- Generated cluster labels
- Calculated:
  - Silhouette Score
  - Adjusted Rand Index (ARI)

**Screenshot (K-Medoids Clustering):**  
![K-Medoids Clustering](screenshots/k-medoids.png)

---

### Step 4 — Visualize and Compare Results
- Created side-by-side scatter plots using **PCA (2D projection)**
- Marked cluster **centroids** (K-Means) and **medoids** (K-Medoids)
- Compared cluster shapes and separation visually

**Screenshot (Comparing Result):**  
![Compare Result](screenshots/visual_comparison.png)

---

## Results Summary (Key Insights)
> Replace the placeholders below with the values from your notebook output.

- **K-Means**
  - Silhouette Score: **0.2849**
  - ARI: **0.8975**
- **K-Medoids**
  - Silhouette Score: **0.2660**
  - ARI: **0.7263**

**What I noticed:**
- The method with the **higher Silhouette Score** produced more clearly separated clusters.
- ARI helped confirm how closely the clusters align with the actual wine classes.
- From the PCA plots, I could see small differences in how each method positions clusters and handles borderline points.

---

## When Each Method is Preferable
- **K-Means is preferable** when:
  - you want faster performance (especially on larger datasets)
  - clusters are roughly round/spherical in feature space
- **K-Medoids is preferable** when:
  - you want more robustness to outliers/noise
  - you prefer real data points as cluster centers (medoids)

---

## Challenges / Decisions
- **Decision:** Standardized all features so no single feature dominates the distance calculation.
- **Challenge:** K-Medoids sometimes requires an extra library and may show harmless warnings depending on environment.
- **Note:** PCA plots are a 2D projection used for visualization; clustering is performed in the full feature space.

---

## Submission Notes
- Include in the GitHub repo:
  - `MSCS_634_Lab_3.ipynb`
  - `README.md`
  - `screenshots/` folder with step screenshots
