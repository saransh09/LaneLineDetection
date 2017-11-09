# **Finding Lane Lines on the Road** 

## Writeup Template


**Finding Lane Lines on the Road**


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Saransh's Reflection from this project

This task a lot difficult before I went through this section, everything was explained quite well in the course material

It took some time for me to tune the parameters of the Hough Lines, I am still a little unclear with the intiuition of the parameter tuning in Hough Lines

### 1. Pipeline.

Initially, I went for a simple approach and did not really spend much time in the draw_lines() function, 
the initial pipeline consisted of the following steps
  1. Convert the image to Gray fro RGB
  2. Hardcoding the region of interest, for the image
  3. Getting the edges through canny edge detection, after application of Gaussian Blur
  4. Using Hough transform to get the desired line segments
  5. I had modified the draw_lines() function using simple slope > 0 and slope < 0 approach, followed by the averaging   approach
  
However, I realised while this worked for the basic images and the videos, the results were not at all good for the challenge video, so I had to use the HSV approach, where I set the threshold for the white lanes and the yellow lanes, added them and masked the orignal image for only those portions, which had the white lanes and the yellow lanes.
I also, used specific ratios to select the region of interest, instead of plainly hardcoding the ROI
Also, I improved my selection critierion so for the slopes so that I do no get outliers in the draw_lines() function


![alt text][image1]


### 2. Possible shortcomings of my pipeline

From what I have realised is this pipeline will work best for straight roads, with not much of lane changing involved during the drive, if lane changes and sharp turns do occur, this pipeline is likely to fail
Also, the lighting conitions is an important part of the project, the results can be affected during the dark, or during very bright sunlight.
Camera jitters causes the lane lines to deviate sometimes
These can be avoided

### 3. Some possible ways to improve the pipeline

Perhaps there can be a way, to store the previous frame image so that in case of a camera jitter, if there is a very drastic change in the lane lines, it can be avoided
also, this will help smoothen the lane lines
