# Mask-RCNN-Nuclei-Detection


Mask RCNN: Is an approach to instance segmentation.


Instance Segmentation is a combination of two operations:
Object Detection + Semantic Segmentation


Used mask rcnn on python3, keras and tensorflow. Mask R-CNN is an updated version of faster r cnn. It is a 3 stage parallel procedure. Model predict the class, generate bounding box and mask segmentation for each instance of an object in the image.


1. Training data has been divided into 2 part ‘train’ and ‘val’.
2. COCO pretrained weights used for new model training.
3. Mrcnn configuration file contains class name, number of classes, bach size, epochs, learning rate, number of gpu and image per gpu for parallel processing,backbone model, image dimensions, anchor length etc inherited parent Config class in NucleiConfig sub-class.
4. Used ResNet 50 as backbone model because of resources constraint, ResNet101 can be used.
5. In the code 2 different config sub class one for training(NucleiConfig) and one for Inference(NucleiInferenceConfig).
6. For dataset preprocessing NucleiDataset is the sun class. It will load the dataset split and arrange it according to train, test, val input, it will also generate the mask for  an image and will return image path accordingly.
7. Training function contain image augmentation, and model definition operation.
8. After training the model next step in interfacing for the we use test data.


Detection:
Mask to RLE conversion:  RLE is an efficient way of storing mask. This is a lossless data        compression technique to increase speed and processing in less storage. Many mask operations can be computed directly using the RLE with decoding.


Evaluation and map(Mean Average Precision):
Average precision matrix is used to measure the accuracy of an object detected .Its a measurement of precision value for recall value over 0 to 1. We compute AP over range of IoU thresholds.
IoU is intersection over union. It's basically a measurement of overlap between two boundaries, (original and predicted boundary). In this program IoU default threshold is 0.5.


There are some parent class like compute_iou, compute_ap etc used for map computation.
