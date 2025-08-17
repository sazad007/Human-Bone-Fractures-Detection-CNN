# 🦴 Human Bone Fracture Detection & Classification  

This project applies deep learning to detect and classify human bone fractures using the [Human Bone Fractures Image Dataset](https://www.kaggle.com/datasets/jockeroika/human-bone-fractures-image-dataset). The model is designed to not only classify fracture types but also localize the affected regions in X-ray images.  

## 🔍 Features  
- **Raw CNN Implementation**  
  - Built entirely from scratch using a custom Convolutional Neural Network (CNN).  
  - Does not rely on prebuilt architectures such as ResNet, VGG, Ultralytics, or Inception.  
  - Provides flexibility in experimenting with layers, activations, and loss functions.  

- **Custom Dataset Integration**  
  - Trained on **1,344 training images** and tested on **128 images** of bone fractures.  
  - Handles variability in fracture shapes, sizes, and positions.  

- **Data Augmentation**  
  - Resized images with center padding to preserve aspect ratio.
  - Randomly applied augmentation on training images.
  - horizontal/vertical flip, 90/180/270 degree rotations were applied randomly.   

- **Bounding Box Regression**  
  - Detects the exact location of fractures with bounding boxes.  
  - Uses **Huber loss** for robust bounding box regression.  

- **Multi-Task Learning**  
  - Simultaneously optimizes for:  
    - **Classification Loss** → Identifies the type of fracture.  
    - **Bounding Box Loss** → Learns precise fracture localization.  

- **Custom Loss Design**  
  - Weighted combination of box loss and class loss for balanced optimization.  
  - Supports experiments with different loss weighting strategies.  

- **Early Stopping & Model Checkpointing**  
  - Prevents overfitting by restoring the model to the best epoch.  

## 📊 Results  
- Training converged within **20 epochs** with early stopping.  
- **Validation Accuracy** stabilized around **38–42%** for classification.  
- **Bounding Box Regression** achieved low error with validation MSE ~**0.025–0.04**.  
- **Best Model Epoch (11)**:  
  - Validation classification accuracy: ~**40%**  
  - Validation box loss: ~**0.027**  
  - Overall validation loss: **2.53**  
  - Model is biased towards class 8 which needs to be addressed in future versions

These results highlight strong localization performance with room for improvement in classification accuracy, which may benefit from more advanced architectures or augmentation strategies.   

## 📌 Key Takeaways  
- Dataset size too small to classify between 10 classes.
- Built with a **raw CNN implementation** without using prebuilt architectures.  
- Demonstrates that deep learning can detect and localize fractures in medical X-rays.  
- Localization is reliable, while classification remains a challenging task.  
- Provides a strong baseline for further improvements using transfer learning or larger datasets.  
