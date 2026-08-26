# CPS 535: Environment Setup Instructions

Follow these steps once, at the start of the semester. You will reuse this same environment for every week of the course.

## Prerequisites

Before starting, make sure you have:
- **Python 3.10 or newer**: check with `python --version` (or `python3 --version` on Mac/Linux). If you don't have it, download from [python.org](https://www.python.org/downloads/).
- **VS Code**: download from [code.visualstudio.com](https://code.visualstudio.com/).
- **VS Code extensions:**: open VS Code, go to the Extensions panel (left sidebar), and install:
  - **Python** (by Microsoft)
  - **Jupyter** (by Microsoft)

---

## Step 1: Create your course folder

Create one main folder for this entire course. This is where everything will live all semester.

```
CPS535/
```

Create it wherever you keep coursework (Desktop, Documents, etc.), then open it in VS Code: **File → Open Folder → select `CPS535`**.

---

## Step 2: Create a Python virtual environment

A virtual environment keeps this course's libraries separate from other Python projects on your machine. Open a terminal **inside VS Code** (Terminal → New Terminal). Make sure you are in your `CPS535` folder and run:

```bash
python -m venv cps535-env
```

This creates a folder called `cps535-env` inside `CPS535` containing an isolated Python installation. You only do this once.

---

## Step 3: Activate the environment

Every time you work on course material in a new terminal, activate the environment first.

**Windows (PowerShell):**
```bash
cps535-env\Scripts\Activate.ps1
```
>Note: if you get an error, you might have to run this command in powershell : `Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser`

**Mac/Linux:**
```bash
source cps535-env/bin/activate
```

You'll know it worked when you see `(cps535-env)` at the start of your terminal prompt.

---

## Step 4: Install the course libraries

With the environment activated, download `requirements.txt` (provided alongside this file) into your `CPS535` folder, then run:

```bash
pip install -r requirements.txt
```

This installs everything we'll use this semester: Jupyter, numpy, pandas, matplotlib, scikit-learn, PyTorch, Hugging Face Transformers, Gensim, and Sentence-Transformers. Some weeks may ask you to `pip install` one or two extra packages as new topics come up (e.g., a vector database library for the RAG week). I'll let you know exactly when.

This step may take several minutes and needs an internet connection. Do it somewhere with reliable Wi-Fi before class, not during.

---

## Step 5: Create your weekly folders

Inside `CPS535`, create a new folder for each week as we go, matching that week's notebook(s):

```
CPS535/
├── cps535-env/
├── requirements.txt
├── Week1/
│   └── Week1_Code.ipynb (or any name you wanna give it)
├── Week2/
│   └── ...
├── Week3/
│   └── ...
```

You'll be provided lecture notes, plus any lab/exercise work you do and it is recommended to put them inside that week's folder. Keeping everything under one `CPS535` folder means your environment (`cps535-env`) is always just one level up, no matter which week you're working in.

---

## Step 6: Select the kernel in VS Code

Open any `.ipynb` notebook file in VS Code:
1. Click **Select Kernel** in the top-right corner of the notebook.
2. Choose **Python Environments…**, then select `cps535-env` from the list.

If you don't see `cps535-env` listed, make sure you opened VS Code from inside the `CPS535` folder (Step 1) and that Step 2 completed without errors.

You only need to select the kernel once per notebook as VS Code remembers your choice when you reopen it.

---

## Step 7: Verify everything works

Open a new notebook (or use the first cell of Week 1's notebook) and run:

```python
import torch
import transformers
import sklearn
import gensim

print("Torch:", torch.__version__)
print("Transformers:", transformers.__version__)
print("CUDA available:", torch.cuda.is_available())
```

If this runs without errors, your environment is ready. `CUDA available: False` is expected and fine if you don't have an NVIDIA GPU, everything in this course also works on CPU, just a bit slower for some exercises.

---

## Troubleshooting

- **"python: command not found"**: try `python3` instead of `python` (common on Mac/Linux).
- **Kernel not showing up in VS Code**: restart VS Code after Step 4 finishes installing.
- **A `pip install` fails partway through**: re-run `pip install -r requirements.txt`; it skips packages already installed and retries the rest.
- **Started fresh terminal and commands aren't found**: you forgot to activate the environment (Step 3). Do this every time you open a new terminal.
- **gensim error**: If you get `gensim` error, install a specific version `pip install gensim==4.3.3`
- In case of any other install errors, try and install them again.
- **Still stuck**: bring your error message to office hours.
