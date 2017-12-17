# Spatial Adversarial Transformer #
The goal of this project is enhancing image composition using spatial transformer network and adversarial network. 

## Introduction ##
We downloaded input dataset (bad composition images) and target dataset (good composition images) from [Flickr](http://www.flickr.com) then train the network. In our framework, generator get an input image and generates compositionally changed image. Discriminator try to discriminate between generated images and target data. Finally, we can get compositionally enhanced image from generative model. 

## Files ##
  * [train_ad.lua](Spatial%20Adversarial%20Transformer/train_ad.lua): Training code
  * [Adversarial.lua](Spatial%20Adversarial%20Transformer/Adversarial.lua): set parameters for training 
  * [spatial_transformer.lua](Spatial%20Adversarial%20Transformer/spatial_transformer.lua): design a network architecture
  * [ROTSizeCriterion_boundary.lua](Spatial%20Adversarial%20Transformer/ROTSizeCriterion_boundary.lua): add regularization term
  * [ST_test.lua](Spatial%20Adversarial%20Transformer/ST_test.lua): Test code
    
## How to Use ##
* Test Function Usage  
```
th ST_test.lua –net model/adversarial-epoch-9.net –dir <your test_directory_path>
```
## Requirements ##
* Cuda compatible GPU
* Linux OS
* Torch7
  * Installation guide in [English](http://www.jetsonhacks.com/2015/05/20/torch-7-scientific-computer-framework-with-cudnn-nvidia-jetson-tk1/) and [Korean](http://www.whydsp.org/279)
* CUDA <= 7.5

## Neural Network Framework ##
We use generative adversarial network (GAN) [\[1\]](#references) that are trained in an adversarial manner to generate new data which fits the distribution of the training data. GAN consists two neural networks (generator, discriminator) contesting with each other. For more details regarding this network, please refer to [\[1\]](#references).
Spatial transformer network [\[2\]](#references) is a learnable module that explicitly allows the spatial manipulation of data within the network. This module can learn various operations such as translation, scale, rotation and generic warping. 
In this project, we use spatial transformer network as a generator. Generator generates enhanced image by translating and scaling an input image. And we use Residual network [\[3\]](#references) as our discriminator. We use 34 layer residual network which pre-trained on ImageNet dataset.

## License ##
This software is being made available under the terms in the [LICENSE](LICENSE) file.

Any exemptions to these terms requires a license from the Pohang University of Science and Technology.

## Contact ##
Eunbin Hong (hong5827 [at] postech [dot] ac [dot] kr)

## About Coupe Project ##
Project ‘COUPE’ aims to develop software that evaluates and improves the quality of images and videos based on big visual data. To achieve the goal, we extract sharpness, color, composition features from images and develop technologies for restoring and improving by using it. In addition, personalization technology through user preference analysis is under study.  
  
Please checkout out other Coupe repositories in our [Posgraph](https://github.com/posgraph) github organization.

## Useful Links ##

  * [Coupe Library](http://coupe.postech.ac.kr/)
  * [POSTECH CG Lab.](http://cg.postech.ac.kr/)
  
## References ##
1. Goodfellow, I., Pouget-Abadie, J., Mirza, M., Xu, B., Warde-Farley, D., Ozair, S., ... and Bengio, Y. Generative adversarial nets. In Proceedings of NIPS (2014).
2. Jaderberg, M., Simonyan, K., Zisserman, A. and Kavukcuoglu, K. Spatial Transfomer Networks. In Proceedings of NIPS (2015).
3. He, K., Zhang, X., Ren, S. and Sun, J. Deep residual learning for image recognition. In Proceedings of the IEEE CVPR (2016). 
