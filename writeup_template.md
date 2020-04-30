# **Finding Lane Lines on the Road** 

## Writeup Template

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I blurred the images using a gaussian filter of size 5 to remove noise, and soften out the gradients. Then I applied a canny edge detector to get all the edges of the road, however this also included edges that weren't relevant so I masked out the images to contain only the lane markings. With the help of a modified draw lines functions and hough transform, I was able to extract line segments from the edges which was added on top of the original image to produce the outputs. 

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by first, checking the slope of the lines and classifying accordingly if they belong to the left lane or the right lane. Then using np.polyfit function, which uses a linear regressor to make a line segment which fits the points. 


### 2. Identify potential shortcomings with your current pipeline

The outputs are not smooth and are jagged. 

The lanes are being extracted almost perfectly in the frames(especially of the challenge video), but somehow are having an issue when being processed in the video

### 3. Suggest possible improvements to your pipeline

A possible improvement would be to use machine learning approaches to find the lanes which also take into account the position of the lanes in the previous frame, this could help in smoothening out the sudden errors which are coming in the video.