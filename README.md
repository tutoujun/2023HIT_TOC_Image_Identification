# 2023HIT_TOC_Image_Identification
2023HIT计算理论课设，完成不同方法完成图像的识别，并比较图像识别的效果。

## 数据集准备
使用数据集：https://www.kaggle.com/datasets/julichitai/multilabel-small-car-and-color-dataset 数据集中图片以裁切好。数据集中的文件结构如下：
``` 
.
├── matiz black
├── matiz blue
├── matiz red
├── rio black
├── rio blue
├── rio red
├── tiggo black
├── tiggo blue
└── tiggo red
``` 
数据集一共有9个类，使用不同的模型对以上图片进行分类，并对分类结果进行分析。

## 传统方法进行识别
在深度学习出现之前，有很多传统方法完成图像的识别，这些方法有着不错的准确度。使用一些传统方法进行识别，并分析其中识别的原理，比较不同模型的差别。

> 有很多识别图像的传统方法，负责这部分的同学可以在支持向量机、层次聚类、马尔可夫随机场、随机森林、AdaBoost等方法内选择两个方法进行撰写(当然如果有更好的也可以)。模型写完后分析一下模型的优缺点和识别失败的图像的原因。将分析的内容写在readme文件中，画的图和相关的代码直接在仓库中建一个文件夹push上去即可。

## 使用深度学习方法进行识别
在AlexNet出现后，深度学习成为识别图像的一种主要方法。近年来有很多识别图像的深度学习模型。使用多种不同规模、不同原理的模型，对图像进行识别。分析模型的原理，并比较不同模型的准确度差别，以及神经网络模型的优势。

> 大家对完成的模型的效果进行量化分析，并画一些简单的图进行分析。最好提取出识别失败的图像，分析一下失败的原因。分析的内容大家写到readme文件中，画的图和相关模型的代码直接push到相关的文件夹内即可。

### AlexNet模型
AlexNet 是一个深度卷积神经网络，它的结构如下：
1. 输入层：
- 输入图像的尺寸为 227x227x3
2. 第一层（C1）：
- 卷积层：使用 96 个 11x11 的卷积核，步长为 4，用 2 填充。
- 激活函数：ReLU
- 局部相应归一化（LRN）
- 最大池化：使用 3x3 的核，步长为 2
3. 第二层（C2）：
- 卷积层：使用 256 个 5x5 的卷积核，步长为 1，用 2 填充。
- 激活函数：ReLU
- 局部相应归一化（LRN）
- 最大池化：使用 3x3 的核，步长为 2
4. 第三层（C3）：
- 卷积层：使用 384 个 3x3 的卷积核，步长为 1，用 1 填充。
- 激活函数：ReLU
5. 第四层（C4）：
- 卷积层：使用 384 个 3x3 的卷积核，步长为 1，用 1 填充。
- 激活函数：ReLU
6. 第五层（C5）：
- 卷积层：使用 256 个 3x3 的卷积核，步长为 1，用 1 填充。
- 激活函数：ReLU
- 最大池化：使用 3x3 的核，步长为 2
7. 第六层（F6）：
- 全连接层：有 4096 个神经元
- 激活函数：ReLU
- Dropout：为了减少过拟合，训练时随机丢弃一半的神经元
8. 第七层（F7）：
- 全连接层：有 4096 个神经元
- 激活函数：ReLU
- Dropout：为了减少过拟合，训练时随机丢弃一半的神经元
9. 输出层（F8）：
- 全连接层：有 9 个神经元，对应于数据集的 9 个类别
- 激活函数：Softmax，用于分类概率输出

AlexNet 主要特点：
1. 更深的网络结构：AlexNet由 5 个卷积层、3 个全连接层和最后的 Softmax 分类层组成。
2. ReLU 激活函数：AlexNet 是第一个大规模使用 ReLU 作为激活函数的网络，这加速了训练过程。
3. Dropout：为了减少过拟合，AlexNet 在全连接层中使用了 Dropout。
4. 局部响应归一化（LRN）：在某些卷积层后使用了局部响应归一化。
5. 数据增强：为了进一步减少过拟合，AlexNet 使用了图像平移、翻转和颜色变化等数据增强技术。

训练结果如下：
![graph](./AlexNet/AlexNet.png)
在训练过程中，我们将数据集按 7：3 的比例划分为训练集和测试集。采用 AlexNet 进行训练，训练 50 轮后，发现模型对于测试集的预测准确率不断上升，最后趋于稳定，稳定在 55% 左右；损失函数值也在不断下降，最终达到了 0.13。考虑到样本集中的数据量只有 2700 左右，数据量偏少，因此训练效果不是很理想。如果增大样本集规模，模型预测的准确率应该会有进一步提升。
在训练过程中发现，虽然损失函数值在下降，但是预测准确率却并未上升，有时甚至下降，这说明模型可能存在过拟合现象，这也可能是导致模型预测准确率不高的原因之一。

### YOLO模型

### Vision Transformer(ViT)模型