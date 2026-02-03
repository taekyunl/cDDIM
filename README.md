# cDDIM (Conditional Denoising Diffusion Implicit Model for wireless channel matrix)

This repository contains the implementation for: "Generating High Dimensional User-Specific Wireless Channels Using Diffusion Models," IEEE Transactions on Wireless Communications, vol. 25, pp. 2907–2921, Aug. 26, 2025, doi: 10.1109/TWC.2025.3600286. (Preprint: https://arxiv.org/abs/2409.03924)

![proposed_approach](./proposed_approach.png)

## Generating Initial Channel Dataset from QuaDRiGa

After installing QuaDRiGa ([https://quadriga-channel-model.de/software/](https://quadriga-channel-model.de/software/)), 
place `main_chgen.m` in the `/quadriga_src/` folder.

Then, execute the file in MATLAB. After generation, place the output files into `/data/QuaDRiGa`. Alternatively, you can download the dataset from Google Drive [here](https://drive.google.com/file/d/17ho6jTsPh6HD4IkkYSlB9WM9JXF4xwII/view?usp=drive_link).

## Conda Environment Setup

To create and activate the Conda environment using the provided `environment.yml`, follow these steps:

1. **Create the environment**:

   ```bash
   conda env create -f environment.yml
   ```
   
2. **Activate the environment**:

   ```bash
   conda activate cDDIM
   ```
   
## Training and Inference

First, create `/cDDIM_10000/` folder, and execute `script_channel_ddim.py` to train the model:

```bash
python script_channel_ddim.py
```

For inference, use the following commands:

```bash
python ddim_inference.py generate
```
to generate channel matrices. Then,
```bash
python ddim_inference.py concatenate
```
to concatenate the generated matrices. 
The above description is for the quadriga dataset. A version for the DeepMIMO dataset will be updated.

## References

This repository was inspired by the following codebases:

- The codebase is primarily based on **conditional MNIST**: [https://github.com/cloneofsimo/minDiffusion](https://github.com/cloneofsimo/minDiffusion)
  
Two downstream tasks mentioned in the paper:

- Channel compression - CRNet: [https://github.com/Kylin9511/CRNet](https://github.com/Kylin9511/CRNet)
- Site-specific beamforming - DLGF: [https://github.com/YuqiangHeng/DLGF](https://github.com/YuqiangHeng/DLGF)

Other ideas are referenced in the [paper](https://www.arxiv.org/abs/2409.03924).

If you find this repository helpful, please cite our work!:
```bash
@ARTICLE{lee2025generating,
  author  = {Lee, Taekyun and Park, Juseong and Kim, Hyeji and Andrews, Jeffrey G.},
  title   = {Generating High Dimensional User-Specific Wireless Channels Using Diffusion Models},
  journal = {IEEE Transactions on Wireless Communications},
  year    = {2025},
  volume  = {25},
  pages   = {2907--2921},
  doi     = {10.1109/TWC.2025.3600286}
}
```
