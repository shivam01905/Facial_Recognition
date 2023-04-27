# Facial_Recognition
Download the lfw(labelled faces in wild) data set.

This is a face verification system that uses a Siamese neural network to compare two images and determine whether they belong to the same person. The system uses OpenCV to capture images from the camera, preprocess them, and pass them through the Siamese network for comparison.

Requirements
The following packages are required to run the system:

TensorFlow 2.5.0 or later
OpenCV 4.5.1 or later
NumPy 1.19.5 or later
Matplotlib 3.4.2 or later
You can install these packages inside the notebook

Usage
To use the system, run the .pynb file:


Preprocessing:
The preprocess function in the .pynb file takes in an image and a scaling factor and performs the following preprocessing steps:

Convert the image to grayscale.
Resize the image by the scaling factor.
Normalize the pixel values to be between 0 and 1.
Expand the dimensions of the image to have a batch size of 1.


Siamese Network:
make_embedding() that creates a CNN-based image embedding model. The embedding model takes an image as input and outputs a 4096-dimensional vector. The function then defines a custom Keras layer L1Dist that computes the L1 distance between two input image embeddings. The L1Dist layer is used to define the Siamese network in the make_siamese_model() function. The Siamese network takes two input images and computes their distance using the L1Dist layer. Finally, the distance is passed to a sigmoid activation function to perform binary classification.
The train() function trains the Siamese network using the Binary Cross-Entropy loss function and the Adam optimizer. The training process is performed over a specified number of epochs. Within each epoch, the training data is looped through in batches, and each batch is used to update the network weights. The function also uses Keras Precision and Recall metrics to evaluate the performance of the Siamese network during training.

The Siamese network is defined in the file. The load_siamese_model function loads a pre-trained model from a HDF5 file. The compare_images function takes in two images and returns a similarity score between 0 and 1.

Verification:
The verify function in the file takes in a Siamese model, a threshold for the similarity score, and a scaling factor for the images. It captures an image from the camera, preprocesses it, and compares it to the input image using the Siamese model. It captures video from the default camera (Webcam) using OpenCV's VideoCapture class, extracts a region of interest from the frame, displays the ROI in a window, and waits for a keypress.

If the 'v' key is pressed, the current frame is saved to the 'Application_data/input_image' folder, and then a verification function called 'verify' is called with the Siamese model, 0.5 as the threshold for cosine similarity, and 0.5 as the threshold for classification. The results and verification status are printed to the console.

If the 'q' key is pressed, the program exits the while loop and the camera is released. If the similarity score is above the threshold, it returns a "verified" message and the similarity score. Otherwise, it returns a "not verified" message and the similarity score. 

License
This project is licensed under the MIT License.
You can find the thesis paper refered here:- https://www.cs.utoronto.ca/~gkoch/files/msc-thesis.pdf
