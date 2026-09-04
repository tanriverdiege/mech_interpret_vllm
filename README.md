# mech_interpret_vllm

Implementation of ["Linear Mechanisms for Spatiotemporal Reasoning in Vision Language Models"](https://arxiv.org/pdf/2601.12626) (ICLR 2026). See [`linear_mech/README.md`](linear_mech/README.md) for the full list of experiments.

## Conda Setup (if conda is not already installed)

```bash
curl -L -O "https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh"
bash Miniconda3-latest-Linux-x86_64.sh -b -p "$HOME/miniconda3"
"$HOME/miniconda3/bin/conda" init bash
exec bash
```

## Setup Conda Environment

```bash
cd linear_mech
conda env create -f environment.yml
conda activate vlm-bind
```

## Data Download

Several experiments (e.g. [`mirror_attr_swapping`](linear_mech/mirror_attr_swapping)) need the COCO-Spatial dataset. Download it with `gdown`:

```bash
pip install gdown

mkdir -p linear_mech/mirror_attr_swapping/data
cd linear_mech/mirror_attr_swapping/data
gdown 'https://drive.google.com/file/d/1efplEVOBN-Pas2nXkFPaZeLPHJPflyRq/view?usp=drive_link'

tar xf coco.tar
cd coco
rm coco.tar  # optional, frees ~1.65GB
```

This produces the expected layout:

```
linear_mech/mirror_attr_swapping/data/
├── coco/
│   ├── 000000000139.jpg
│   ├── 000000000285.jpg
│   └── ...                # COCO images + annotations/
    └── coco_qa_two_obj.json   # COCO-Spatial annotations
```

Refer to each experiment's own README for any additional data it requires.
