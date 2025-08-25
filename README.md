# Image-Handling-and-Pixel-Transformations-Using-OpenCV 

## AIM:
Write a Python program using OpenCV that performs the following tasks:

1) Read and Display an Image.  
2) Adjust the brightness of an image.  
3) Modify the image contrast.  
4) Generate a third image using bitwise operations.

## Software Required:
- Anaconda - Python 3.7
- Jupyter Notebook (for interactive development and execution)

## Algorithm:
### Step 1:
Load an image from your local directory and display it.
```
img_gray = cv2.imread('Eagle_in_Flight.jpg', cv2.IMREAD_GRAYSCALE)
```

### Step 2:
Create a matrix of ones (with data type float64) to adjust brightness.

### Step 3:
Create brighter and darker images by adding and subtracting the matrix from the original image.  
Display the original, brighter, and darker images.

### Step 4:
Modify the image contrast by creating two higher contrast images using scaling factors of 1.1 and 1.2 (without overflow fix).  
Display the original, lower contrast, and higher contrast images.

### Step 5:
Split the image (boy.jpg) into B, G, R components and display the channels

## Program Developed By:
- **Name:** [Your Name Here]  
- **Register Number:** [Your Register Number Here]

  ### Ex. No. 01

#### 1. Read the image ('Eagle_in_Flight.jpg') using OpenCV imread() as a grayscale image.
```python
img_gray = cv2.imread('Eagle_in_Flight.jpg', cv2.IMREAD_GRAYSCALE)
```

#### 2. Print the image width, height & Channel.
```python
print("Grayscale Image Shape:", img_gray.shape)
```

#### 3. Display the image using matplotlib imshow().
```python
plt.imshow(img_gray, cmap='gray')
plt.title("Grayscale Eagle")
plt.axis("off")
plt.show()
```

#### 4. Save the image as a PNG file using OpenCV imwrite().
```python
cv2.imwrite("Eagle_in_Flight_gray.png", img_gray)
```

#### 5. Read the saved image above as a color image using cv2.cvtColor().
```python
img_color = cv2.imread("Eagle_in_Flight_gray.png")
img_color = cv2.cvtColor(img_color, cv2.COLOR_BGR2RGB)
```

#### 6. Display the Colour image using matplotlib imshow() & Print the image width, height & channel.
```python
plt.imshow(img_color)
plt.title("Color Image")
plt.axis("off")
plt.show()
print("Color Image Shape:", img_color.shape) 
```

#### 7. Crop the image to extract any specific (Eagle alone) object from the image.
```python
cropped = img_color[100:400, 150:500]  
plt.imshow(cropped)
plt.title("Cropped Eagle")
plt.axis("off")
plt.show()
```

#### 8. Resize the image up by a factor of 2x.
```python
resized = cv2.resize(cropped, None, fx=2, fy=2)
plt.imshow(resized)
plt.title("Resized Eagle (2x)")
plt.axis("off")
plt.show()
```

#### 9. Flip the cropped/resized image horizontally.
```python
flipped = cv2.flip(resized, 1)
plt.imshow(flipped)
plt.title("Flipped Image")
plt.axis("off")
plt.show()
```

#### 10. Read in the image ('Apollo-11-launch.jpg').
```python
apollo = cv2.imread('Apollo-11-launch.jpg')
apollo = cv2.cvtColor(apollo, cv2.COLOR_BGR2RGB)
```

#### 11. Add the following text to the dark area at the bottom of the image (centered on the image):
```python
text = "Apollo 11 Saturn V Launch, July 16, 1969"
font_face = cv2.FONT_HERSHEY_PLAIN
cv2.putText(apollo, text, (100, 950), font_face, 2, (255,255,255), 2, cv2.LINE_AA)
```

#### 12. Draw a magenta rectangle that encompasses the launch tower and the rocket.
```python
rect_color = magenta
cv2.rectangle(apollo, (250,200), (600,950), (255,0,255), 3)
```

#### 13. Display the final annotated image.
```python
plt.imshow(apollo)
plt.title("Apollo 11 Annotated")
plt.axis("off")
plt.show()

```

#### 14. Read the image ('Boy.jpg').
```python
boy = cv2.imread("Boy.jpg")
boy = cv2.cvtColor(boy, cv2.COLOR_BGR2RGB)
```

#### 15. Adjust the brightness of the image.
```python
# Create a matrix of ones (with data type float64)
matrix = np.ones(boy.shape, dtype="uint8") * 50
```

#### 16. Create brighter and darker images.
```python
img_brighter = cv2.add(boy, matrix)
img_darker = cv2.subtract(boy, matrix)
```

#### 17. Display the images (Original Image, Darker Image, Brighter Image).
```python
fig, ax = plt.subplots(1,3, figsize=(12,5))
ax[0].imshow(boy); ax[0].set_title("Original")
ax[1].imshow(img_darker); ax[1].set_title("Darker")
ax[2].imshow(img_brighter); ax[2].set_title("Brighter")
for a in ax: a.axis("off")
plt.show()

```

#### 18. Modify the image contrast.
```python
# Create two higher contrast images using the 'scale' option with factors of 1.1 and 1.2 (without overflow fix)
img_higher1 = cv2.convertScaleAbs(boy, alpha=1.1, beta=0)
img_higher2 = cv2.convertScaleAbs(boy, alpha=1.2, beta=0)
```

#### 19. Display the images (Original, Lower Contrast, Higher Contrast).
```python
fig, ax = plt.subplots(1,3, figsize=(12,5))
ax[0].imshow(boy); ax[0].set_title("Original")
ax[1].imshow(img_higher1); ax[1].set_title("Contrast x1.1")
ax[2].imshow(img_higher2); ax[2].set_title("Contrast x1.2")
for a in ax: a.axis("off")
plt.show()
```

#### 20. Split the image (boy.jpg) into the B,G,R components & Display the channels.
```python
b, g, r = cv2.split(boy)
fig, ax = plt.subplots(1,3, figsize=(12,5))
ax[0].imshow(b, cmap='gray'); ax[0].set_title("Blue Channel")
ax[1].imshow(g, cmap='gray'); ax[1].set_title("Green Channel")
ax[2].imshow(r, cmap='gray'); ax[2].set_title("Red Channel")
for a in ax: a.axis("off")
plt.show()
```

#### 21. Merged the R, G, B , displays along with the original image
```python
merged = cv2.merge([r,g,b])  
plt.imshow(merged)
plt.title("Merged Image (R,G,B)")
plt.axis("off")
plt.show()
```

#### 22. Split the image into the H, S, V components & Display the channels.
```python
hsv = cv2.cvtColor(boy, cv2.COLOR_RGB2HSV)
h, s, v = cv2.split(hsv)
fig, ax = plt.subplots(1,3, figsize=(12,5))
ax[0].imshow(h, cmap='gray'); ax[0].set_title("Hue")
ax[1].imshow(s, cmap='gray'); ax[1].set_title("Saturation")
ax[2].imshow(v, cmap='gray'); ax[2].set_title("Value")
for a in ax: a.axis("off")
plt.show()

```
#### 23. Merged the H, S, V, displays along with original image.
```
pythonmerged_hsv = cv2.merge([h,s,v])
plt.imshow(cv2.cvtColor(merged_hsv, cv2.COLOR_HSV2RGB))
plt.title("Merged HSV -> RGB")
plt.axis("off")
plt.show()
```

## Output:
- **i)** Read and Display an Image.
  
- **ii)** Adjust Image Brightness.  
- **iii)** Modify Image Contrast.  
- **iv)** Generate Third Image Using Bitwise Operations.

## Result:
Thus, the images were read, displayed, brightness and contrast adjustments were made, and bitwise operations were performed successfully using the Python program.

