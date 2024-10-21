# sophia880919-Occupational-Injury-Prevention_RT-DETR
This homework focuses on object detection for occupational injury prevention in NTU-CVPDL, aiming to optimize detection accuracy and efficiency in workplace safety scenarios.

## Model Architecture and Description 

![image](https://github.com/user-attachments/assets/ef878ead-14da-4ab6-9372-20b5193c6e91)
Figure 1: Model Architecture 

The model selected for this assignment is RT-DETR. The architecture of RT-DETR uses ResNet
50 as the backbone and employs the Efficient Hybrid Encoder as the neck. The Efficient Hybrid 
Encoder consists of two components: Attention-based Intra-scale Feature Interaction (AIFI) and the 
CNN-based Cross-scale Feature-fusion Module (CCFF). AIFI utilizes an attention mechanism to 
enhance feature interactions within the same scale, while CCFF, similar to FPN/PAN, is composed of 
two 1x1 convolutions and several RepBlocks, enabling multi-scale fusion to improve feature 
representation across different scales.  
To address the issue in the original DETR model, where selecting Top-K features solely based on 
classification scores could result in low IoU scores for predicted bounding boxes, RT-DETR introduces 
the Uncertainty Minimal Query Selection mechanism. This mechanism optimizes cognitive 
uncertainty to select higher-quality queries from the encoder features and feeds them to the decoder, 
ultimately improving the accuracy of both classification and bounding box predictions. This 
architecture effectively resolves the inconsistency between classification and IoU scores, enhancing 
the model's detection performance. 

## Implement Details 
For this project, I applied several image augmentations during the data export process in 
Roboflow, such as rotation, color jitter, and blurring, to enhance the robustness of the model. Before 
training, the images were resized to 640 x 640 to reduce computational costs. The loss functions used 
in training include VFL Loss for classification prediction and Bounding Box Regression Loss for 
bounding box prediction, which typically uses L1 or Generalized Intersection over Union (GIoU) loss. 
GIoU Loss was used to measure the overlap between the predicted and ground truth bounding boxes. 
The learning rate was set to 9.999999999999748e-06 for training. and the batch size was set to 4 to 
further reduce memory usage and processing time.

![image](https://github.com/user-attachments/assets/36873a20-de5d-4536-89b7-eac6ec7c9ed8)
Figure 2: Image Augmentation Examples


## Performance
area=all	mAP 70.99
area=small	mAP 50.2
area=medium	mAP 71.66
area=large	AP50	90.57


## Visualization: Comparison of Ground Truth and Predicted Results
The left image displays the ground truth bounding boxes, while the right image shows the predicted results. The comparison reveals that the model struggles with identifying objects in blurry areas or small objects, often failing to detect them accurately. This highlights a common challenge in object detection, where models perform well on larger and clearer objects but tend to miss or misclassify smaller, less distinct features.

![image](https://github.com/user-attachments/assets/e187c428-90ed-4517-a4c5-7df54fa94ad3)  ![image](https://github.com/user-attachments/assets/92e1fdf7-71dc-4b51-92f9-960a1e403323)

![image](https://github.com/user-attachments/assets/e08c1846-274b-4a59-bf7b-fd06a4a4d33f)  ![image](https://github.com/user-attachments/assets/743f39d5-aa70-42fd-9bd7-29b1fd17e736)


## Reference
https://henry870603.medium.com/machine-learning-paper-reading-detrs-beat-yolos-on-real-time-object-detection-2992783c0415
https://github.com/lyuwenyu/RT-DETR


   


