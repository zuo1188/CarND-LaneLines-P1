# **Finding Lane Lines on the Road** 


### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 6 steps. 

step1:

    result = grayscale(image)
    
step2:

    result = gaussian_blur(result,3)
    
step3:

    result = canny(result, 100, 200)
    
step4：

    vertices = np.array([[[100, 539],[900, 539],[480, 310]]])
    result = region_of_interest(result, vertices)
    
step5:

    result = hough_lines(result, 1, np.pi/180, 1, 5, 1)
    5.1 classify the slopes between 0.5~0.8 or -0.8~-0.5 to get two line groups
    5.2 compute average slopes of the two groups
    5.3 assume that start point as Y=539 and end point as Y=339,
        then caculate start and end point of the left lane and right lane
     
     
    
step6:

    mix the result with initial image
    result = weighted_img(result, image, α=0.8, β=1., λ=0.)


### 2. Identify potential shortcomings with your current pipeline


 1.the algorithm is not robust,may consider some other lines as line feature
 
 2.hough transform can not detect curve lines


### 3. Suggest possible improvements to your pipeline

1.use deep learning to detected lines

2.use splines polynomials to represent line result
