# Video Subtitles Detector Program

This program processes video frames to detect subtitles using various image processing techniques. 
It is done on this video https://drive.google.com/file/d/1mUOdZbcvRS_UTIoi4wGdfp9i8pNl3fYM/view

## Image Processing Basics

The program includes the following image processing steps:
1. **Pre-processing**: Adjustments for noise reduction, contrast enhancement.
2. **Image Segmentation**: Dividing an image into meaningful parts.
3. **Feature Extraction**: Identifying and extracting important characteristics.
4. **Image Recognition**: Assigning labels or classifications to objects.

## Pre-Processing

### 1. Converting Image to Grayscale
Convert a 3-channel image into a one-channel grayscale image for faster and easier processing. The grayscale values range between [0:255].

![Grayscale Conversion](https://github.com/user-attachments/assets/224780ef-0d84-4368-82bf-8cde764667ec)

### 2. Noise Removal
Applies a Gaussian blur to the grayscale image (`frame_gray`) using a kernel of size `kernel_size x kernel_size` and a standard deviation of 5. This reduces noise and smooths the image.

![Noise Removal](https://github.com/user-attachments/assets/0d7ee949-f83e-44a2-a047-cc3ddfcbb131)

### 3. Thresholding & Connectivity
`cv2.threshold` is a function that applies a fixed-level threshold to each pixel in the image. `cv2.THRESH_BINARY` converts the image to a binary image (black and white).

![Thresholding & Connectivity](https://github.com/user-attachments/assets/18001cc1-779b-4f74-88a8-7af9a7743137)

## Image Segmentation

### 1. Region of Interest (ROI)
Working on a specific region to apply other processing steps without the need to apply these processes to the whole frame.

![Region of Interest](https://github.com/user-attachments/assets/a961ae38-16fb-47b4-b7c6-92d642495bf5)

### 2. Mask Filtration
The code converts a region of interest (ROI) in a video frame from BGR to HSV color space and then creates a mask that isolates white colors within the specified HSV range. The mask highlights pixels in the ROI that fall within the range defined by `lower_white` and `upper_white`.

![Mask Filtration](https://github.com/user-attachments/assets/b32a76d4-4860-4a4f-a3a1-73baa973f2b0)

### 3. Remove Noise using Morphology
Morphological transformations are applied to remove noise and improve the mask.

![Morphology](https://github.com/user-attachments/assets/f6b9c296-4bd8-4d3e-9b5c-365ac29d6526)

## Results

### Segmentation Results
![Segmentation Results](https://github.com/user-attachments/assets/82bb3f2c-e712-4cba-9c34-d48a9d0e4f08)

### Feature Extraction Results
![Feature Extraction Results](https://github.com/user-attachments/assets/6635116f-ecf8-4f62-9b46-6a4c52879b73)

### Final Result
![Final Result](https://github.com/user-attachments/assets/26228abb-46be-48d7-93ee-3c53488b32af)

