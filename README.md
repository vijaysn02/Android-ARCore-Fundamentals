## Objective:

	• Understand the basics of AR Core
	• Dependencies for AR Environment
	• AR Core Concepts - Plane, Anchors and Poses
	• AR Core Process - Placing a virtual object in real world

Possibilities of Creating AR App - OpenGL, Unity and Unreal

Referred Tutorial Link - https://www.raywenderlich.com/6986535-arcore-with-kotlin-getting-started#toc-anchor-007
My Git hub Link - https://github.com/vijaysn02/Android-ARCore-Fundamentals.git

--------------------------------------------------------------------------------------------------------------------------------

## Introduction:

At WWDC June 2017, Apple announced ARKit, its foray into the world of AR development. Two months later, Google announced ARCore, which it extracted from the Tango indoor mapping project.

--------------------------------------------------------------------------------------------------------------------------------

Key Mechanisms:

-> Motion tracking: determines both the position and the orientation 

-> Environmental understanding: ARCore can detect horizontal or vertical surfaces like tables, floors or walls while processing input from your device’s camera.

-> Light estimation: ARCore understands the lighting of the environment. It can then adjust the average intensity and color of virtual objects to put them under similar conditions as the environment that surrounds them.


--------------------------------------------------------------------------------------------------------------------------------

## Prerequisites / Dependencies:

-> Install Google Play Services for AR in your android phone.

-> Include Dependencies in Build.gradle
```
implementation ′com.google.ar:core:1.14.0′
```

-> Open AndroidManifest.xml and add the following after the manifest tag:

```
<uses−permission android:name="android.permission.CAMERA" />
```

```
<uses−feature
  android:name="android.hardware.camera.ar"
  android:required="true" />
<uses−feature
  android:glEsVersion="0x00020000"
  android:required="true"≯

-> Also, add the following just before the closing application tag:
<meta−data
  android:name="com.google.ar.core"
  android:value="required" />  
```


--------------------------------------------------------------------------------------------------------------------------------

## Planes, Anchors and Poses

	• Plane -  a real-world planar surface - horizontal or vertical.
	• Anchor - fixed coordinates and orientation.
	• Pose - virtual object coordinates to real world coordinates.
	• Plane Attachment - Attach anchor to plan and retrieve the pose.


--------------------------------------------------------------------------------------------------------------------------------


## PROCEDURE / PROCESS:

	• Setup Surface View and Configure EGLContext.
	• Setup Camera Session after obtaining the permission.
	• On Surface Creation, Render Background, Plane, Point Cloud on GLThread and Create the Virtual Objects on GLThread. Set the Intensity accordingly.
	• On Tap Action, Make the PlaneAttachment by creating the plane from hit test and anchor for hit - pose and add the virtual object using the planeattachment.
	• Draw the Surface by taking the camera frame and draw the plane attachment created.
