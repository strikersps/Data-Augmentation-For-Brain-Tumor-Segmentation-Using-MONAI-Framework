# Data Augmentation For Brain Tumor Segmentation Using MONAI Framework  

## 1. Introduction
In 2020, worldwide 308,102 brain and nervous system cancer cases were reported out of which 251,329 deaths were registered i.e. ≈ 82.0% fatality rate and glioma was found to be one of most occurring brain tumors in the world and it can be both benign or metastatic. According to WHO, glioma can be categorised into 4 types which are Grade-I, Grade-II, Grade-III, and Grade-IV where Grade-I and Grade-II collectively represent Low Grade Glioma (LGG) and Grade-III and Grade-IV collectively represent High Grade Glioma (HGG).

For this work we have used BraTS-2020 dataset which consists of images and segmentation masks (`nii.gz` format) for both low and high grade glioma's and the goal was to develop an efficient data augmentation pipeline using [MONAI](https://monai.io/) opensource domain specialised framework to artificially generate valid and sensible variances of structural brain MRI sequences i.e. T1, T1-Gd (Gadolinium), T2, FLAIR of high and low grade glioma's which will boost the generalisation capabilities of the deep learning model. The need for having a efficient data augmentation pipeline for the development of an automatic segmentation system raised because of the following reasons:
  - In healthcare we always deal with the problem of imbalanced datasets and limitation of expert annotated datasets which in itself is a challenge for applications of deep learning in healthcare.
  - Glioma lesion has a high level of heterogeneity present due to the location, size and histology and an inherent heterogeneity present because of different sources with different conventions from where the multi-modal MRI scans of BraTS-2020 dataset were collected and because of this detection and segmentation of glioma's is a challenging task in medical image processing and analysis.

## 2. About Dataset
- The BraTS-2020 dataset used in this work was open-sourced as part of an annual competition organized by the University of Pennsylvania, Perelman School of Medicine with
support from MICCAI and the aim of the BraTS challenge is to build and evaluate state of the art supervised learners for the segmentation of brain tumors and survival prediction of patients.  
- The dataset is multi-modal and all the Brain-MRI scans and segmentation masks are available in `NifTI` format (`nii.gz` or `nii`) and were obtained with different clinical
protocols from various institutions/organisations with different MRI scanners which inherently makes the dataset heterogeneous in nature and is pre-processed i.e. co-registered to the same anatomical template, interpolated to the same resolution (`1mm^3`) and skull-stripped.

<img src="https://github.com/strikersps/Data-Augmentation-For-Brain-Tumor-Segmentation-Using-MONAI-Framework/blob/main/images/Brain-MRI-Different-Representation.png" alt="Image" style="display: block; margin: 0 auto" />

- Multi-modal brain MRI scans consists of maily four different representations as shown in the above exhibit:
  - Native T1-Weighted Scan (T1) `[D]`
  - Post-Contrast T1-Weighted Scan (T1-Gd) `[C]`
  - Native T2-Weighted Scan (T2) `[A]`
  - T2 Fluid Attenuated Inversion Recovery (FLAIR) `[B]`  
 which plays a pivotal role because it provide different set of information through those four representations which is crucial to understand different tissue intrinsic properties, area of tumor spread and growth like in T1-Gd (Gadolinium) the enhancing tumor (ET) part shows hyper-intensity as compared to its T1 counterpart and when compared to white matter in T1-Gd (Gadolinium).

- The BraTS-2020 dataset is divided into training, validation and testing dataset. The training dataset consists a total of 369 combined cases of low and high grade glioma's and dataset is in-balanced as `79.40%` of the observations belongs to high grade glioma (HGG) and the rest `20.6%` belongs to low grade glioma (LGG).

 <p align="center">
    <img src="https://github.com/strikersps/Data-Augmentation-For-Brain-Tumor-Segmentation-Using-MONAI-Framework/blob/main/images/Training-Data-Distrubution.png" alt="Training Data Distribution">
 </p>

- The validation dataset consits a total of 125 combined cases of low and high grade glioma's but we are not provided with the information about to which grade an observation belongs to and no segmentation masks are provided.
- The testing dataset is only available to contestants of the annual BraTS competition once the training and validation phase is over.

 <p align="center">
    <img src="https://github.com/strikersps/Data-Augmentation-For-Brain-Tumor-Segmentation-Using-MONAI-Framework/blob/main/images/Glioma-Subregions.jpeg" alt="Glioma Subregions">
 </p>

> Glioma sub-regions (manual annotation through experts). The image patches shown from left to right: the whole tumor (yellow) visible in T2-FLAIR (A), the tumor core (red) visible in T2 (B), the active tumor/enhancing tumor (light blue) visible in T1-Gd (Gadolinium), surrounding the cystic/necrotic components of the core (green) (C). The segmentations are then merged to produce the final labels (D): ED (yellow), NET (red), NCR cores (green), AT (blue).

- For only training data we are provided with expert annotated segmentation masks which represent different tumor sub-regions and are labeled numerically as defined in the following table and shown in the above exhibit:

  |Sr. No| Tumor Sub-Region/Mask Name | Mask Label|
  |:----:|:--------------------------:|:---------:|
  | 1 | Necrotic and Non-Enhancing Part (NER) | 1 |
  | 2 | Enhancing Tumor (ET) | 2|
  | 3 | Peritumoral Edematous Tissue (ED) | 4 |
  | 4 | Background or White Matter | 0 |

- As the dataset is large ≈ 4.17 GB, you can access the dataset from
    Google Drive Link: https://drive.google.com/drive/folders/1hd8S54t9XJTwlg1o_2sDi2LhZOx4gUby?usp=sharing

## 3. Publications Based on the Work
1. [**S. P. Sharma and N. Sampath, "Data Augmentation for Brain Tumor Segmentation using MONAI Framework," 2022 2nd International Conference on Intelligent Technologies (CONIT), 2022, pp. 1-8, doi: 10.1109/CONIT55038.2022.9847822.**](https://ieeexplore.ieee.org/document/9847822)

```bibtex
@inproceedings{9847822,
	title        = {Data Augmentation for Brain Tumor Segmentation using MONAI Framework},
	author       = {Sharma, Suraj Prakash and Sampath, Nalini},
	year         = 2022,
	booktitle    = {2022 2nd International Conference on Intelligent Technologies (CONIT)},
	pages        = {1--8},
	doi          = {10.1109/CONIT55038.2022.9847822}
}
```
##### NOTE: To cite our work, please add the above block of code into your *.bib file in the latex environment and if you want to cite this repository, then please copy the respective style information (APA or BibTex) provided under `cite this repository` option as shown in the tutorial: https://github.blog/wp-content/uploads/2021/08/GitHub-citation-demo.gif

###### GNU General Public License v3.0
[![License Badge](https://img.shields.io/github/license/strikersps/Data-Augmentation-For-Brain-Tumor-Segmentation-Using-MONAI-Framework?color=red&style=for-the-badge)](https://github.com/strikersps/Data-Augmentation-For-Brain-Tumor-Segmentation-Using-MONAI-Framework/blob/main/LICENSE)
