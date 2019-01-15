# depth_eigen
An implementation of https://arxiv.org/abs/1406.2283 in PyTorch.

The paper firstly proposed a coarse-fine convolutional deep neural network approach to estimate depth from a single image.

## Network structure
<p>
  <img src="https://github.com/shuuchen/depth_eigen/blob/master/images/structure.png" height="250" width="500" />
</p>

## Files
- depth_eigen.ipynb
  - model, preprocessing, train, validation and test
- data_prepare.ipynb
  - data preparation and cleaning

## Training data
[NYU Depth](https://cs.nyu.edu/~silberman/datasets/)
I used 2807 train samples and 694 validation samples for a light train and validation.

## Loss curves 
- Coarse networks per epoch
<p>
  <img src="https://github.com/shuuchen/depth_eigen/blob/master/images/coarse.png" height="250" width="500" />
</p>

- Fine networks per epoch
<p>
  <img src="https://github.com/shuuchen/depth_eigen/blob/master/images/fine.png" height="250" width="500" />
</p>

The validation loss is lower than train loss, mostly because dropout is used in coarse6 layer of coarse network. Dropout is prohibited during validation, which leads to better inference results.

## Test

<p>
  <img src="https://github.com/shuuchen/depth_eigen/blob/master/images/test.png" height="250" width="500" />
</p>

Though not so accurate, the depth can be slightly predicted by fine network. The output of coarse network seems unchanged to different input images, which is a problem. Anyway, the losses of both networks are highly above the losses provided in the paper, which are merely around 0.2. I believe better accuracy can be achieved by using more training data and learning iterations.
