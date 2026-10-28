# Image Smoothing and Sharpening Using OpenCV


## Aim

To write a Python program using OpenCV to apply different smoothing filters (Averaging, Weighted Averaging, Gaussian, Median) and sharpening filters (Laplacian Kernel and Laplacian Operator) for image enhancement, and display each result separately along with the original image for comparison.

---

## The program performs the following operations:

- Read and display an input image  
- Apply Averaging filter  
- Apply Weighted Averaging filter  
- Apply Gaussian filter  
- Apply Median filter  
- Apply Laplacian sharpening using kernel  
- Apply Laplacian operator  
- Display all outputs for comparison  

---

##  Software Used

- Anaconda – Python 3.7  
- Jupyter Notebook / VS Code  
- OpenCV (cv2)  
- NumPy  
- Matplotlib  

---

##  Algorithm

### Step 1:
Import the required libraries: OpenCV, NumPy, and Matplotlib.

### Step 2:
Read the input image (e.g., `image.jpg`).

### Step 3:
Convert the image from BGR to RGB format for display.

### Step 4:
Apply Averaging Filter using `cv2.blur()`.

### Step 5:
Apply Weighted Averaging Filter using a custom kernel with `cv2.filter2D()`.

### Step 6:
Apply Gaussian Filter using `cv2.GaussianBlur()`.

### Step 7:
Apply Median Filter using `cv2.medianBlur()`.

### Step 8:
Apply Laplacian Sharpening using Kernel with `cv2.filter2D()`.

### Step 9:
Convert image to grayscale and apply Laplacian Operator using `cv2.Laplacian()`.

### Step 10:
Display all filtered images using a grid layout for comparison.

---
## Program
```
import cv2
import numpy as np
import matplotlib.pyplot as plt

image_path = r"C:\Users\acer\OneDrive\Pictures\Camera Roll\Virat Kohli.jpg"

image = cv2.imread(image_path)

if image is None:
    raise FileNotFoundError("Image not found. Check the image path.")

print("Image loaded successfully!")
print("Image dimensions:", image.shape)

rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

plt.figure(figsize=(6, 6))
plt.imshow(rgb)
plt.title("Original Virat Kohli Image")
plt.axis("off")
plt.show()

averaging = cv2.blur(image, (5, 5))

plt.figure(figsize=(6, 6))
plt.imshow(cv2.cvtColor(averaging, cv2.COLOR_BGR2RGB))
plt.title("Averaging Filter")
plt.axis("off")
plt.show()

kernel = np.array([
    [1, 2, 1],
    [2, 4, 2],
    [1, 2, 1]
], dtype=np.float32) / 16

weighted = cv2.filter2D(image, -1, kernel)

plt.figure(figsize=(6, 6))
plt.imshow(cv2.cvtColor(weighted, cv2.COLOR_BGR2RGB))
plt.title("Weighted Averaging Filter")
plt.axis("off")
plt.show()

gaussian = cv2.GaussianBlur(image, (5, 5), 0)

plt.figure(figsize=(6, 6))
plt.imshow(cv2.cvtColor(gaussian, cv2.COLOR_BGR2RGB))
plt.title("Gaussian Filter")
plt.axis("off")
plt.show()

median = cv2.medianBlur(image, 5)

plt.figure(figsize=(6, 6))
plt.imshow(cv2.cvtColor(median, cv2.COLOR_BGR2RGB))
plt.title("Median Filter")
plt.axis("off")
plt.show()

laplacian_kernel = np.array([
    [0, -1, 0],
    [-1, 5, -1],
    [0, -1, 0]
], dtype=np.float32)

sharpened = cv2.filter2D(image, -1, laplacian_kernel)

plt.figure(figsize=(6, 6))
plt.imshow(cv2.cvtColor(sharpened, cv2.COLOR_BGR2RGB))
plt.title("Laplacian Sharpening")
plt.axis("off")
plt.show()

gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

laplacian = cv2.Laplacian(
    gray,
    cv2.CV_64F
)

laplacian_abs = cv2.convertScaleAbs(laplacian)

plt.figure(figsize=(6, 6))
plt.imshow(laplacian_abs, cmap="gray")
plt.title("Laplacian Operator - Grayscale")
plt.axis("off")
plt.show()


```

##  Developed By

- **Name:** PON SARAVANA PANDIAN B
- **Register No:**212225230207

---

##  Output
<img width="607" height="380" alt="image" src="https://github.com/user-attachments/assets/8665412d-0506-4ff0-9044-538ac5d5d3f2" />

<img width="612" height="388" alt="image" src="https://github.com/user-attachments/assets/77c2da5f-3d78-4b8c-afea-9a23cd15f3ee" />

<img width="602" height="380" alt="image" src="https://github.com/user-attachments/assets/3ddfdbe2-f860-4338-8d01-81bd8c852ebb" />

<img width="607" height="382" alt="image" src="https://github.com/user-attachments/assets/4405ba58-24f7-43a5-9018-364351bed4cf" />

<img width="605" height="386" alt="image" src="https://github.com/user-attachments/assets/916dff61-fbcd-45a1-aedc-6f1b4b0e40da" />

<img width="607" height="378" alt="image" src="https://github.com/user-attachments/assets/eef0f64b-2d3c-438c-b1be-2cab5a366ac4" />

<img width="611" height="386" alt="image" src="https://github.com/user-attachments/assets/4570a30c-b722-4835-a042-f800aedaa8ec" />

<img width="1716" height="786" alt="image" src="https://github.com/user-attachments/assets/2f7be4fd-9555-4d05-ae6f-6c10032bd022" />


### Smoothing Filters

- Averaging filter produces blurred image  
- Weighted averaging provides smoother result with less distortion  
- Gaussian filter preserves edges better while reducing noise  
- Median filter removes salt-and-pepper noise effectively  

###  Sharpening Filters

- Laplacian kernel enhances edges and fine details  
- Laplacian operator detects edges clearly in grayscale  

---

##  Result

Thus, smoothing filters and sharpening filters are successfully implemented using OpenCV.

The smoothing filters reduce noise and improve image quality, while sharpening filters enhance edges and details for better feature extraction.
