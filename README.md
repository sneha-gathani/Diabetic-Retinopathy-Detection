# DiabeticRetinopathyDetection
Automatic detection of Diabetic Retinopathy using Deep Learning.

The architecture is trained similar the net2net technique proposed by Goodfellow et al. This technique enables rapid transferring of information stored in one neural net into another neural net. The main purpose is to accelerate the training of a significantly larger neural net.

In this implementation, I have used the teacher model as VGG16 by OxfordNet and tranferred the learned features to a self constructed dilated convolution block. These two modules are further concatenated and the feature maps are globally average pooled to give final predictions.

Preprocessing was done using the LAB format of images which spilt the images into three channels and applied Adaptive Histogram Equlisation to the L-channel. After this the channel was recombined with other channels and converted to the original RGB format.

Hyperparameters:

Optimiser           : Stochastic gradient descent with momentum 0.9
Loss Function       : Categorical Crossentropy 
Learning Rate       : 0.0001 which was reduced by a factor of 0.125 after 10 epochs
Activation Function : ReLU for Conv layers and Softmax for output layer.
Epochs              : 20
Batch size          : 32
Class Weight        : Since the data visualisation showed us the imbalance in the dataset, we provide appropriate                                     weightage to each class while training
