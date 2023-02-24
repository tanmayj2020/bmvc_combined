# How to Train Vision Transformer on Small-scale Datasets? (BMVC'22)

[Hanan Gani](https://scholar.google.co.in/citations?user=XFugeQ4AAAAJ&hl=en), [Muzammal Naseer](https://muzammal-naseer.netlify.app/), and [Mohammad Yaqub](https://scholar.google.co.uk/citations?hl=en&user=9dfn5GkAAAAJ&view_op=list_works&sortby=pubdate)

[![paper](https://img.shields.io/badge/arXiv-Paper-<COLOR>.svg)](https://arxiv.org/abs/2210.07240v1)
[![Poster](https://img.shields.io/badge/Poster-PDF-8333FF)](https://drive.google.com/file/d/1eywuOkHPbH3bJhC7_kwBvyfI29jxfAkv/view?usp=sharing)
[![Slides](https://img.shields.io/badge/Slides-PDF-87CEEB)](https://docs.google.com/presentation/d/1Hlw9TdiuiPWmuwf0lJGF0mNEGqp60n-U/edit?usp=sharing&ouid=105985073683824470966&rtpof=true&sd=true) 
[![Video](https://img.shields.io/badge/Video-Presentation-F9D371)](https://drive.google.com/file/d/1oA0C_AAeGzwQogvsJHyWPE8CGOCQYkFG/view?usp=sharing)
#


> **Abstract:** *Vision Transformer (ViT), a radically different architecture than convolutional neural networks offers multiple advantages including design simplicity, robustness and state-of-the-art performance on many vision tasks. However, in contrast to convolutional neural networks, Vision Transformer lacks inherent inductive biases. Therefore, successful training of such models is mainly attributed to pre-training on large-scale datasets such as ImageNet with 1.2M or JFT with 300M images. This hinders the direct adaption of Vision Transformer for small-scale datasets. In this work, we show that self-supervised inductive biases can be learned directly from small-scale datasets and serve as an effective weight initialization scheme for fine tuning. This allows to train these models without large scale pre-training, changes to model architecture or loss functions. We present thorough experiments to successfully train monolithic and non-monolithic Vision Transformers on five small datasets including CIFAR10/100, CINIC-10, SVHN, Tiny-ImageNet and two fine-grained datasets: Aircarft and Cars. Our approach consistently improves the performance while retaining their properties such as attention to salient regions and higher robustness.*
>



#
<hr>

## Contents

1. [What's New?](#What's-New?)
2. [Highlights](#Highlights)
3. [Model Zoo](#Model-Zoo)
4. [Requirements](#Requirements)
5. [Self-Supervised Training](#Self-supervised-Training)
6. [Supervised Training](#Supervised-Training)
7. [Results](#Results)
8. [Citation](#Citation)
9. [Contact](#Contact)
10. [References](#References)


<hr>

## What's New?

### (September 30, 2022)
* Our paper is accepted as a conference paper at [BMVC 2022](https://bmvc2022.org)

### (September 06, 2022)
* **Finegrained Datasets:** Our approach gives 66.04 @ 224 top-1 accuracy on fine-grained Aircraft dataset and 43.89 @ 224 top-1 accuracy on fine-grained Cars dataset 

### (August 09, 2022)
* Pretrained weights released.
  * CIFAR10
    * ```vit_cifar10_patch4_input32``` - 96.41 @ 32
    * ```swin_cifar10_patch2_input32``` - 96.18 @ 32
    * ```cait_cifar10_patch4_input32``` - 96.42 @ 32
  * CIFAR100
    * ```vit_cifar100_patch4_input32``` - 79.15 @ 32
    * ```swin_cifar100_patch2_input32``` - 80.95 @ 32
    * ```cait_cifar100_patch4_input32``` - 80.79 @ 32
  * SVHN
    * ```vit_svhn_patch4_input32``` - 98.08 @ 32
    * ```swin_svhn_patch2_input32``` - 98.01 @ 32
    * ```cait_svhn_patch4_input32``` - 98.18 @ 32
  * CINIC10
    * ```vit_cinic_patch4_input32``` - 86.91 @ 32
    * ```swin_cinic_patch2_input32``` - 87.84 @ 32
    * ```cait_cinic_patch4_input32``` - 88.27 @ 32
  * Tiny-Imagenet
    * ```vit_timnet_patch8_input32``` - 63.36 @ 64
    * ```swin_timnet_patch4_input32``` - 65.13 @ 64
    * ```cait_timnet_patch8_input32``` - 67.46 @ 64
### (August 08, 2022)
* Self-supervised training and finetuning codes released.
   
<hr>

## Highlights
1. Vision Transformers, whether monolithic or non-monolithic, both suffer when trained from scratch on small datasets. This is primarily due to the lack of locality, inductive biases and hierarchical structure of the representations which is commonly observed in the Convolutional Neural Networks. As a result, ViTs require large-scale pre-training to learn such properties from the data for better transfer learning to downstream tasks. We show that inductive biases can be learned directly from the small dataset through self-supervision, thus serving as an effective weight initialization for finetuning on the same dataset.


<!-- <img src="assets/final_main_figure.png" height="500" width="700"> -->
<!-- ![main_figure](assets/final_main_figure.png) -->


2. Our proposed self-supervised inductive biases improve the performance of ViTs on small datasets without modifying the network architecture or loss functions.

<hr>

## Model Zoo

| Dataset       | Input Size | Model |                                                                                                       Pretrained Weights   |
|:--------------|:----------:|:-----:|:--------------------------------------------------------------------------------------------------------------------------:|
|    CIFAR10    |   32x32    |  ViT  | [Link](https://github.com/hananshafi/vits-for-small-scale-datasets/releases/download/v1.0/vit_cifar10_patch4_input32.pth)  |
|    CIFAR10    |   32x32    |  Swin | [Link](https://github.com/hananshafi/vits-for-small-scale-datasets/releases/download/v1.0/swin_cifar10_patch2_input32.pth) |
|    CIFAR10    |   32x32    |  CaiT | [Link](https://github.com/hananshafi/vits-for-small-scale-datasets/releases/download/v1.0/cait_cifar10_patch4_input32.pth) |
|    CIFAR100   |   32x32    |  ViT  | [Link](https://github.com/hananshafi/vits-for-small-scale-datasets/releases/download/v1.0/vit_cifar10_patch4_input32.pth)  |
|    CIFAR100   |   32x32    |  Swin | [Link](https://github.com/hananshafi/vits-for-small-scale-datasets/releases/download/v1.0/swin_cifar100_patch2_input32.pth)|
|    CIFAR100   |   32x32    |  CaiT | [Link](https://github.com/hananshafi/vits-for-small-scale-datasets/releases/download/v1.0/cait_cifar100_patch4_input32.pth)|
|    CINIC10    |   32x32    |  ViT  | [Link](https://github.com/hananshafi/vits-for-small-scale-datasets/releases/download/v1.0/vit_cinic_patch4_input32.pth)    |
|    CINIC10    |   32x32    |  Swin | [Link](https://github.com/hananshafi/vits-for-small-scale-datasets/releases/download/v1.0/swin_cinic_patch2_input32.pth)   |
|    CINIC10    |   32x32    |  CaiT | [Link](https://github.com/hananshafi/vits-for-small-scale-datasets/releases/download/v1.0/cait_cinic_patch4_input32.pth)   |
|     SVHN      |   32x32    |  ViT  | [Link](https://github.com/hananshafi/vits-for-small-scale-datasets/releases/download/v1.0/vit_svhn_patch4_input32.pth)     |
|     SVHN      |   32x32    |  Swin | [Link](https://github.com/hananshafi/vits-for-small-scale-datasets/releases/download/v1.0/swin_svhn_patch2_input32.pth)    |
|     SVHN      |   32x32    |  CaiT | [Link](https://github.com/hananshafi/vits-for-small-scale-datasets/releases/download/v1.0/cait_svhn_patch4_input32.pth)    |
| Tiny-Imagenet |   64x64    |  ViT  | [Link](https://github.com/hananshafi/vits-for-small-scale-datasets/releases/download/v1.0/vit_timnet_patch8_input64.pth)   |
| Tiny-Imagenet |   64x64    |  Swin | [Link](https://github.com/hananshafi/vits-for-small-scale-datasets/releases/download/v1.0/swin_timnet_patch4_input64.pth)  |
| Tiny-Imagenet |   64x64    |  CaiT | [Link](https://github.com/hananshafi/vits-for-small-scale-datasets/releases/download/v1.0/cait_timnet_patch8_input64.pth)  |

<hr>

## Requirements
```shell
pip install -r requirements.txt
```

<hr>

## Self-supervised Training 

#### For Tiny-Imagenet:
With ViT architecture

```shell
python -m torch.distributed.launch --nproc_per_node=2 train_ssl.py --arch vit \
                                   --dataset Tiny_Imagenet --image_size 64 \
                                   --datapath "/path/to/tiny-imagenet/train/folder" \
                                   --patch_size 8  \
                                   --mlp_head_in 192 \
                                   --local_crops_number 8 \
                                   --local_crops_scale 0.2 0.4 \
                                   --global_crops_scale 0.5 1. 
                                   --out_dim 1024 \
                                   --batch_size_per_gpu 256  \
                                   --output_dir "/path/for/saving/checkpoints"
```
With Swin architecture

```shell
python -m torch.distributed.launch --nproc_per_node=2 train_ssl.py --arch swin \
                                   --dataset Tiny_Imagenet --image_size 64 \
                                   --datapath "/path/to/tiny-imagenet/train/folder" \
                                   --patch_size 4  \
                                   --mlp_head_in 384 \
                                   --local_crops_number 8 \
                                   --local_crops_scale 0.2 0.4 \
                                   --global_crops_scale 0.5 1. 
                                   --out_dim 1024 \
                                   --batch_size_per_gpu 256  \
                                   --output_dir "/path/for/saving/checkpoints"
```

#


#### For CIFAR based datasets:

With ViT architecture
```shell
python -m torch.distributed.launch --nproc_per_node=2 train_ssl.py --arch vit \
                                   --dataset CIFAR10 --image_size 32 \
                                   --patch_size 4  \
                                   --mlp_head_in 192  \
                                   --local_crops_number 8 \
                                   --local_crops_scale 0.2 0.5 \
                                   --global_crops_scale 0.7 1. 
                                   --out_dim 1024 \
                                   --batch_size_per_gpu 256  \
                                   --output_dir "/path/for/saving/checkpoints"
```

With Swin architecture

```shell
python -m torch.distributed.launch --nproc_per_node=2 train_ssl.py --arch swin \
                                   --dataset Tiny_Imagenet --image_size 32 \
                                   --datapath "/path/to/tiny-imagenet/train/folder" \
                                   --patch_size 2  \
                                   --mlp_head_in 384  \
                                   --local_crops_number 8 \
                                   --local_crops_scale 0.2 0.5 \
                                   --global_crops_scale 0.7 1. 
                                   --out_dim 1024 \
                                   --batch_size_per_gpu 256  \
                                   --output_dir "/path/for/saving/checkpoints"
```

``` --dataset ``` can be ``` Tiny_Imagenet/CIFAR10/CIFAR100/CINIC/SVHN ```.

``` --arch ``` can be ``` vit/swin/cait ```.

``` --local_crops_scale ``` and ``` --global_crops_scale ``` vary based on the dataset used.

``` --mlp_head_in ``` is dimension of the Vision transformer output going into Projection MLP head and varies based on the model used. For ViT/CaiT, keep ``` --mlp_head_in=192```. For Swin, keep``` --mlp_head_in=384```


<hr>

## Supervised Training
```shell
python finetune.py --arch vit  \
                   --dataset Tiny-Imagenet \
                   --datapath "/path/to/data/folder" \
                   --batch_size 256 \
                   --epochs 100 \
                   --pretrained_weights "/path/to/saved/checkpoint"
``` 
``` --arch ``` can be ```vit/swin/cait ```.
``` --datasets ``` can be ```Tiny-Imagenet/CIFAR10/CIFAR100/CINIC/SVHN ```.
Load the corresponding weights for finetuning.

<hr>

## Results
We test our approach on 5 small low resolution datasets: Tiny-Imagenet, CIFAR10, CIFAR100, CINIC10 and SVHN. We compare the results of our approach with 4 baselines: ConvNets, Scratch ViT training, [Efficient Training of Visual Transformers with Small Datasets (NIPS'21)](https://openreview.net/forum?id=SCN8UaetXx), [Vision Transformer for Small-Size Datasets (arXiv'21)](https://arxiv.org/abs/2112.13492)
#### 1. Quantitative results :
![main_results](assets/results_quantitative.PNG)

#

#### 2. Results on high resolution inputs as compared to baseline - [Efficient Training of Visual Transformers with Small Datasets (NIPS'21)](https://openreview.net/forum?id=SCN8UaetXx)
![results_nips](assets/results_nips.PNG)

#

####  3. Qualitative results - Attention to salient regions
Our proposed self-supervised training is able to capture
the shape of the salient objects efficiently with minimal or no attention to the background on unseen test-set
samples without any supervision.

<!-- <img src="assets/atten_maps_paper.png" height="250" width="275"> -->
![arxiv_heatmaps_figure](assets/arxiv_heatmaps_final.png)


<hr>

## Citation
If you use our work, please consider citing:
```bibtex 
@inproceedings{Gani_2022_BMVC,
author    = {Hanan Gani and Muzammal Naseer and Mohammad Yaqub},
title     = {How to Train Vision Transformer on Small-scale Datasets?},
booktitle = {33rd British Machine Vision Conference 2022, {BMVC} 2022, London, UK, November 21-24, 2022},
publisher = {{BMVA} Press},
year      = {2022},
url       = {https://bmvc2022.mpi-inf.mpg.de/0731.pdf}
}
```

<hr>

## Contact
Should you have any questions, please create an issue in this repository or contact at hanan.ghani@mbzuai.ac.ae
<hr>

## References
Our code is build on the repositories of [DINO](https://github.com/facebookresearch/dino) and [Vision Transformer for Small-Size Datasets](https://github.com/aanna0701/SPT_LSA_ViT). We thank them for releasing their code.

<hr>

  
