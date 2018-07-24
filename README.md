# Mask-RCNN
A PyTorch implementation of the architecture of Mask RCNN, serves as an introduction to working with PyTorch

## Decription of folders 
1) model.py includes the models of ResNet and FPN which were already implemented by the authors of the papers and reproduced in this       implementation
2) nms and RoiAlign are taken from Robb Girshick's implementation of faster RCNN
3) Focal loss has been added to this implementtaion on lieu of better results as evidenced by the paper on RetinaNets 

## Mask-RCNN model:

![alt text](https://lilianweng.github.io/lil-log/assets/images/mask-rcnn.png)

### Features:
1) The part of the network responsible for bounding box detection derives it's inspiration from the faster RCNN model having a RPN working in tandem with a ConvNet
2) The pooling layers present in the ConvNet round down or round up to the nearest integer when the stride is not a divisor of the
receptive field, which tends to either lose or assume "information" from the image respectively at the non integral points.
3) ROI align was proposed to deal with this, wherein bilinear interpolation is used to detect the values at the non integral values of the pixels
4) Using a more complex interpolation scheme( cubic interpolation -> 16 additional features) offers a slightly better result when this model was tested, however not enough to justify the additional complexity
5) Cross entropy loss when summed over a huge number of proposals tends to take a huge value for proposals that have a high confidence metric thereby dwarfing the contribution from the proposals of interest. Focal Loss was proposed to do away with this problem
6) However Focal loss gives much better results with single stage networks. This is because a two stage network has some discriminative policy to deal with this class imbalance something which the single stage networks don't enjoy.

If you find any issue in this repsoritory, feel free to fork this repository and submit a PR with the necessary changes 

