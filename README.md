# Extra Practical: Prototyping a 360 Photographic VR Experience

In the this extra practical we’ll be learning how to prototype a basic virtual reality experience that’s based around a 360-degree photograph. We’ll be looking at how we can use a mobile device as a platform. However, the dragging-based interaction you’ll learn can also be used as nice way to allow people to engage with VR experiences in web browsers.

To get started, make a copy of this repository in your personal GitHub account (press the ```Use this template``` button) and check it out onto your local machine.

## Task 1: Dragging to Look Around

In order to create effective VR experiences, we don’t always need to have an expensive headset with 6-DoF tracking. Rather, there are countless examples of really compelling VR experiences that simply allow the user to explore an immersive environment by dragging the camera. In this task we’re going to learn how to implement this first basic interaction.

To get started open the ```BasicVRScene``` in the root of the practical assets folder. This is a basic scene with some objects in, a light source and a standard Unity camera. In this task, we’re going to convert it into a scene where we can look around by dragging the mouse (on a computer) or a finger (on a mobile device).

To help you enable this interaction, I’ve created a script that let’s you look around by dragging called ```VRCameraLook.cs```. You can find this in the Scripts folder of the practical assets.

Add this to the ```MainCamera``` and test if it works. You should test whether it works by both running it in the editor (where you can click on the screen to interact) and on your Android tablet. If you can’t remember how to deploy to Android, have a look back at last week’s guidance on this.

You’ll notice that the interaction is really sluggish, and that the movement of the camera doesn’t keep up with your mouse / finger movement. Can you change the script to fix this issue in both the editor and on your device?

## Task 2: Adding a 360-degree Photograph

One way to create immersive VR experiences is to surround the viewer with 360-degree photographs, which have been taken with special cameras. In this practical, we’re going to learn how to do this in Unity.

As we’re going to now be using a 360-degree photo as our world instead of 3D graphics, the first thing to do is delete all geometry from your scene. You can do this by simply deleting the “BasicWorld” parent game object.

Now we’re going to replace this with our photo. To do this, we of course need a photo that has been taken with a 360-degree panoramic camera. Luckily, the European Southern Observatory has provided some nice ones we can use. Choose and download photo from here. It’ll look better if you download the a higher resolution version, but if your Internet is slow then you can use one of the lower resolution JPEGs for prototyping:

 https://www.eso.org/public/images/?search=360+degree+panorama

Unity offers us some really nice inbuilt support for displaying 360-degree photos, based around a modified Skybox shader. You can find the full details (including how to show 360 videos!) here:

https://docs.unity3d.com/Manual/VideoPanoramic.html

However, to get started, you can create your first panoramic photo display by following these simple steps:

1. Create a new Material (```Assets > Create > Material```)
2. Configure it to be a panoramic skybox by choosing ```Skybox/Panoramic``` from the Shader dropdown menu in the material’s inspector
3. Import the 360 photo you’ve downloaded into Unity
4. Drag/set the photo as the texture in the ```Spherical (HDR)``` box in the inspector
5. Set the material as the current Skybox by dragging it into scene
6. If you get stuck at any point, I’d recommend you refer to the more detailed instructions in section 2 of the link above.

Compile and run your code in both the editor and on your tablet. You should now be able to explore your photo in 360 VR!

## Task 3: Adding Spatial Audio

Our scene looks cool, but doesn’t feel very immersive yet. One way we might address this is to add some of the spatial audio that we learned about in the lecture.

To start this task, find a sound that you feel represents something in your photograph (e.g. a sound of an animal outside or a person speaking) in the Free Sound archive and place it into your scene as an AudioSource:

https://freesound.org/

A key element of creating immersive sound in VR is having audio appear to come from a particular location in the scene. We can achieve this in Unity with a few relatively simple steps.

The first thing we need to do is to place our audio object such that it’s aligned with the position in the scene we want to sound to appear to be coming from. Doing this for a 360 photo isn’t as simple as it would be for a 3D object – for which we’d just attach it to the game object. Rather, we need to work out how we position the sound source so it lies on a ray that passes through the camera position and desired object in the Skybox. A nice trick to achieving this is to:

1. Align the view in the editor to the scene’s camera. This can be achieved by clicking on the ```MainCamera``` game object and choosing (```Game Object > Align View to Selected```) from the menu
2. Positioning the AudioSource so that it appears aligned in the editor

This should position the object in the right place. In order to visually check the alignment is correct, you might consider positioning a simple 3D sphere at the same position as the audio source as a test.

Finally, in order to make the sound appear as if it’s coming from a particular direction, you’ll need to enable 3D sound. This can be done by moving the ```Spatial Blend``` slider in the inspector all the way from 2D to 3D.

Once you’ve done all of this, play your scene in the editor to hear if you sound is coming from the right place. You’ll need to wear stereo headphones to hear the effect (some basic ear buds will be sufficient). You’ll know it’s working if you can hear the sound more loudly in the headphone that’s closest/facing the intended position.


