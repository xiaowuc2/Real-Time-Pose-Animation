# Real-time Pose Animation 






This Real-time Pose Animation takes 2D vector illustration and animates its containing curves in real-time based on the recognition, the result from PoseNet and FaceMesh. It is based on the idea of skeleton-based animation from computer graphics, computer vision and applies it to vector characters.

<img src="/files/gif/boy.gif?raw=true" alt="cameraDemo" style="width: 250px;"/>

<img src="/files/image/blathers.png?raw=true" alt="cameraDemo" style="width: 250px;"/>

In skeletal animation a character is represented in two parts:
1. a surface used to draw the character, and 
1. a hierarchical set of interconnected bones used to animate the surface. 

In Pose Animation, the surface is defined by the 2D vector paths in the input SVG files.
And for the bone structure, Pose Animation provides a predefined rig (bone hierarchy) representation, designed based on the keypoints from PoseNet and FaceMesh. This bone structure’s initial pose is specified in the input SVG file, along with the character illustration, while the real time bone positions are updated by the recognition result from ML models.

<img src="/files/gif/avatar.gif?raw=true" alt="cameraDemo" style="width: 250px;"/>

// TODO: Add blog post link.
For more details on its technical design please check out this blog post.

### Demo 1: [Camera feed](https://pose-animator-demo.firebaseapp.com/camera.html)

The camera demo animates a 2D avatar in real-time from a webcam video stream.


### Demo 2: [Static image](https://pose-animator-demo.firebaseapp.com/static_image.html)

The static image demo shows the avatar positioned from a single image.

## Build And Run

Install dependencies and prepare the build directory:

```sh
yarn
```

To watch files for changes, and launch a dev server:

```sh
yarn watch
```

# Credits
This project is inspired by the work of @yemount. I got very much help from that account and I've used the same website casue I can't buy a domain right now and the I also used .svg from that account.
I don't feel shy to say that I have taken things from others cause I love to work with this things and explore with development.

# Animate your own design

1. Download the [sample skeleton SVG here](/resources/samples/skeleton.svg).
1. Create a new file in your vector graphics editor of choice. Copy the group named ‘skeleton’ from the above file into your working file. Note: 
	* Do not add, remove or rename the joints (circles) in this group. Pose Animator relies on these named paths to read the skeleton’s initial position. Missing joints will cause errors.
	* However you can move the joints around to embed them into your illustration. See step 4.
1. Create a new group and name it ‘illustration’, next to the ‘skeleton’ group. This is the group where you can put all the paths for your illustration.
    * Flatten all subgroups so that ‘illustration’ only contains path elements.
    * Composite paths are not supported at the moment.
    * The working file structure should look like this:
	```
        [Layer 1]
        |---- skeleton
        |---- illustration
              |---- path 1
              |---- path 2
              |---- path 3
	```
1. Embed the sample skeleton in ‘skeleton’ group into your illustration by moving the joints around.
1. Export the file as an SVG file.
1. Open [Pose Animator camera demo](https://pose-animator-demo.firebaseapp.com/camera.html). Once everything loads, drop your SVG file into the browser tab. You should be able to see it come to life 

If you really like my project please give me a star and improve the project by fork :D

