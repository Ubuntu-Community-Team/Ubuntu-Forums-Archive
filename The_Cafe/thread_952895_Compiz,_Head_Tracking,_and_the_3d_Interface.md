---
title: "Compiz, Head Tracking, and the 3d Interface"
date: 2008-10-19
forum: The Cafe
---

### Post by klange on 2008-10-19
Watch the video [on YouTube](http://www.youtube.com/watch?v=N5ODz3MNd6s).

**What it is**: The Compiz `headtracking` plugin uses OpenCV to track the three-dimensional location of your head relative to your screen and puts that data into some OpenGL transformations in Compiz to create the illusion that your display has depth.

**What you need**: You will need a reasonable webcam that is V4L compatible (or in some other way works with OpenCV). You will also need to obtain OpenCV [from CVS](http://forum.compiz-fusion.org/showpost.php?p=66126&postcount=33), as the Ubuntu package (even in Intrepid) lacks many important features the plugin makes use of (note: the libtool script was broken for me, [its $echo wasn't set properly](http://forum.compiz-fusion.org/showthread.php?t=9746&page=4)). Then you can get the [plugin itself](http://gitweb.compiz-fusion.org/?p=users/klange/headtracking;a=summary). You'll need a recent version of Compiz, preferably from git, but it should compile with Intrepid (I think).

**Who made this**: The original distortion code is mine and was made for use with a Wiimote. The OpenCV tracking code was added by [pingouinfarceur](http://forum.compiz-fusion.org/member.php?u=16585), who it would appear joined the C-F forums solely to post the patches.

**How it works**: OpenCV is a video processing library that can track objects based on a definition file (which you'll probably want to make for your own face, unless you look like pingouinfarceur). This data is then used with some fancy trig and the OpenGL glFrustrum() function to distort the viewport in which Compiz renders. In order to make the effect visible, windows are also offset based on their z-depth (stacking order).

**Looking forward**: If we work out the minor glitches, we may get `headtracking` merged into plugins-extra, and it may come standard with 9.04 - we'll see. Personally, I don't even have a camera that works with OpenCV, so working bugs out and extended testing isn't something I can do myself. At the very least, I'll try and get it packaged for Intrepid and put up a PPA later on.

Discuss.

---

### Post by cardinals_fan on 2008-10-19
I think that's very cool, but how would you actually use it in your day-to-day life?

---

### Post by klange on 2008-10-19
> **cardinals_fan said:**
> I think that's very cool, but how would you actually use it in your day-to-day life?

To bring something over from the window-style GUI thread, you can use head tracking to literally look behind windows (though not full screen windows in the current set up). The other possibility has already been demonstrated outside of the realm of Compiz (and a long time ago): viewing 3d models (which we can do in Compiz with the `cubemodel` plugin).

---

### Post by smoker on 2008-10-19
anything new is a bonus, look forward to it's further development :-)

---

### Post by cardinals_fan on 2008-10-19
> **WindowsSucks said:**
> To bring something over from the window-style GUI thread, you can use head tracking to literally look behind windows (though not full screen windows in the current set up). The other possibility has already been demonstrated outside of the realm of Compiz (and a long time ago): viewing 3d models (which we can do in Compiz with the `cubemodel` plugin).
I see.  I prefer the tiling approach, but that could be quite useful with a floating window manager.

---

### Post by dracule on 2008-10-19
i think i am going to pick up a webcam for this. i been meaning to get one.

---

### Post by razerbug on 2008-10-19
This just makes you sea sick - faux 3D on a 2D screen looks like a bad "hologram" you used to get in 90's comics.

---

### Post by dracule on 2008-10-19
what happens if two people are sitting side by side? or if someone walks in behind you?

---

### Post by klange on 2008-10-19
> **dracule said:**
> what happens if two people are sitting side by side? or if someone walks in behind you?
I'm not sure how much leeway OpenCV will give, but assuming they look nothing like you it shouldn't cause problems for you - they'll see a slightly distorted screen, though. If your twin walks into view, that may screw with things.

---

### Post by dracule on 2008-10-19
> **WindowsSucks said:**
> I'm not sure how much leeway OpenCV will give, but assuming they look nothing like you it shouldn't cause problems for you - they'll see a slightly distorted screen, though. If your twin walks into view, that may screw with things.

Sounds pretty cool. is there a way to see a list of supported cams?

---

### Post by eragon100 on 2008-10-20
Does this work with games? I would love to play ET:QW and savage and all the others in 3d!

---

### Post by MaxIBoy on 2008-10-20
I doubt it would be. Culling, man, culling! Hidden face removal! It would look really weird.

There are very good reasons why the only FPS that works well with such techniques is Quake 1. You can safely eliminate hidden face removal and backface culling in the Quake 1 engine, compile it, and still get a semi-decent framerate. (And by the way, when I say semi-decent, I mean semi-decent.)

---

### Post by eragon100 on 2008-10-20
> **MaxIBoy said:**
> I doubt it would be. Culling, man, culling! Hidden face removal! It would look really weird.

There are very good reasons why the only FPS that works well with such techniques is Quake 1. You can safely eliminate hidden face removal and backface culling in the Quake 1 engine, compile it, and still get a semi-decent framerate. (And by the way, when I say semi-decent, I mean semi-decent.)

Nexuiz is based on a modified quake 1 engine :wink:

---

### Post by MaxIBoy on 2008-10-20
Emphasize "modified." If you tried to do this with DarkPlaces (which is the engine Nexuiz uses) and holograph it, you'd probably have to disable all the graphical effects and take everything back as close to the quality of the original Quake as you possibly can. 

Think of it this way. Have you ever used Blender 3D on something of that detail (i.e. an entire map,) viewing everything with textures, bump maps, parallax maps, shaders, GLSL distortion effects, light bloom, and so on? 3d modeling software can't do any culling for fairly obvious reasons, so it's noticeably laggy. Now scale that lagginess up considerably. 

It's not *that* bad, because some things *can* be thrown away safely (rooms that aren't visible from the current room, for example.) However, you can just about forget the possibility of having an outdoor map.

---

### Post by eragon100 on 2008-10-20
> **MaxIBoy said:**
> Emphasize "modified." If you tried to do this with DarkPlaces (which is the engine Nexuiz uses) and holograph it, you'd probably have to disable all the graphical effects and take everything back as close to the quality of the original Quake as you possibly can. 

Think of it this way. Have you ever used Blender 3D on something of that detail (i.e. an entire map,) viewing everything with textures, bump maps, parallax maps, shaders, GLSL distortion effects, light bloom, and so on? 3d modeling software can't do any culling for fairly obvious reasons, so it's noticeably laggy. Now scale that lagginess up considerably. 

It's not *that* bad, because some things *can* be thrown away safely (rooms that aren't visible from the current room, for example.) However, you can just about forget the possibility of having an outdoor map.

:( I like outdoor maps (like the space maps in nexuiz and the like).
Also, this rules out ET:QW since it doesn't have a single indoor map, all the maps have huge outdoor areas (which is basicaly fun :), but in this case, sucks :().

---

### Post by MaxIBoy on 2008-10-20
Don't worry about it. Wait about a year for some more advanced graphics cards to come out, put eight of them in crossfire, optimize the engine for multithreaded processing (not hard to do from a technical standpoint,) and we'll see what we can do.

---

### Post by eragon100 on 2008-10-20
> **MaxIBoy said:**
> Don't worry about it. Wait about a year for some more advanced graphics cards to come out, put eight of them in crossfire, optimize the engine for multithreaded processing (not hard to do from a technical standpoint,) and we'll see what we can do.

I don't have money for 8 600$ GPU's in SLI :cry:

Let's not talk about the new computer I would need as well, since the motherboard in this one doesn't even support dual graphic cards :(

The best solution for me might be to simply buy a 3d monitor, such as this one:

[http://www.quietpcusa.com/Zalman-ZM-M220W-22-inch-Widescreen-Trimon-2D3D-LCD-Monitor-P365C53.aspx](http://www.quietpcusa.com/Zalman-ZM-M220W-22-inch-Widescreen-Trimon-2D3D-LCD-Monitor-P365C53.aspx)

look at the small thumbnail pictures :popcorn:

---

### Post by MaxIBoy on 2008-10-20
Same principle.

I think the performance problem isn't as bad as I thought, but you'd still need a monster rig to power the thing.

Custom NVIDIA drivers, eh? I bet it's Windows-only.

---

### Post by eragon100 on 2008-10-20
> **MaxIBoy said:**
> Same principle.

I think the performance problem isn't as bad as I thought, but you'd still need a monster rig to power the thing.

Custom NVIDIA drivers, eh? I bet it's Windows-only.

For the regular GeForce series it is windows-only, but for the quadro cards the linux driver supports 3d as well.

---

### Post by blakjesus on 2008-10-20
Thats pretty cool, but does that mean that eventually we can move windows around the desktop and to different desktops by waving your hand in front of the screen jedi style? :mrgreen:

---

### Post by MaxIBoy on 2008-10-20
I dread the day I have to play Alien Arena that way.

---

### Post by klange on 2008-10-20
> **dracule said:**
> Sounds pretty cool. is there a way to see a list of supported cams?

Find a list of v4l-compatible cameras? I'm sure it's quite lengthy.

> **blakjesus said:**
> Thats pretty cool, but does that mean that eventually we can move windows around the desktop and to different desktops by waving your hand in front of the screen jedi style? :mrgreen:

We're working on this. It's a bit tricky to get the details worked out, what with actually determining what you're trying to drag.

---

### Post by eragon100 on 2008-10-20
> **WindowsSucks said:**
> Find a list of v4l-compatible cameras? I'm sure it's quite lengthy.



We're working on this. It's a bit tricky to get the details worked out, what with actually determining what your trying to drag.

I would say just point to the correct window with your finger.

---

### Post by quanumphaze on 2008-10-20
> **WindowsSucks said:**
> You will need a *reasonable* webcam that is V4L compatible

What would you consider reasonable? My camera is very low quality being something like 352x288 with a frame rate of around 7 Hz.

---

### Post by funky_munky on 2008-10-20
> **WindowsSucks said:**
> Find a list of v4l-compatible cameras? I'm sure it's quite lengthy.



We're working on this. It's a bit tricky to get the details worked out, what with actually determining what you're trying to drag.

How about just allowing you to move the focussed window to a new View space with the jedi move.  Once moved next window comes into focus.  This would make sorting programs very fast.

When I do web design I have browsers in viewspace 1 gimp and related stuff in 2 bluefish editor and file browser in 3 and inkscape and virtual box running windows with several browsers open in 4.  Being able to open a new program and shove it to the other desktops in relation to the wall view (2x2 fashion) would be slick.

---

### Post by klange on 2008-10-20
> **funky_munky said:**
> How about just allowing you to move the focussed window to a new View space with the jedi move.  Once moved next window comes into focus.  This would make sorting programs very fast.

When I do web design I have browsers in viewspace 1 gimp and related stuff in 2 bluefish editor and file browser in 3 and inkscape and virtual box running windows with several browsers open in 4.  Being able to open a new program and shove it to the other desktops in relation to the wall view (2x2 fashion) would be slick.
Definitely a possibility, the motion tracking would be fairly simple.
For larger workspace grids (say, a 4x1 cube), the speed of the "toss" could determine how far it goes. Use `Move` to do the moving and combined with `wobbly`, it would make for a fairly cool effect.

@eragon: There's more to it than that. It would require a lot information on the size of the screen, your finger, etc. In my post, I was referring to the difficulty in determining what you're actually grabbing with your hand based on your perspective, given that we have a totally different one - this is possible, but it takes a lot of trig (and a little more knowledge of your eyes, the screen physical size, a reference size of your hand [because with one camera, that's the only way we can do depth], etc.)

@quanumphaze: I'm not sure if that would cut it (and it would be painfully slow even if it worked). At the very least, I'd say 800x600@30fps would be the minimum. (What I'm going to get for myself is [1600x1200@30](http://www.logitech.com/index.cfm/webcam_communications/webcams/devices/3056&cl=US,EN#))

---

### Post by MaxIBoy on 2008-10-21
Blah, it's not working for me. I have a Toshiba Satellite laptop with integrated webcam. It's pretty low-quality, but I should at least get some glitchy horribleness. I'm not getting any movement at all.

How do you make that definition file for your face?

---

### Post by klange on 2008-10-22
> **MaxIBoy said:**
> Blah, it's not working for me. I have a Toshiba Satellite laptop with integrated webcam. It's pretty low-quality, but I should at least get some glitchy horribleness. I'm not getting any movement at all.

How do you make that definition file for your face?
I'm not sure if you even do... I'm not familiar with any of the OpenCV things. I believe I was wrong about that.

Anyway, a number of people have had trouble getting it to start properly, so you should probably ask [here](http://forum.compiz-fusion.org/showthread.php?t=9746&page=6). It's probably an issue with detecting your camera properly.

---

### Post by geoken on 2008-10-22
> **MaxIBoy said:**
> I doubt it would be. Culling, man, culling! Hidden face removal! It would look really weird.

There are very good reasons why the only FPS that works well with such techniques is Quake 1. You can safely eliminate hidden face removal and backface culling in the Quake 1 engine, compile it, and still get a semi-decent framerate. (And by the way, when I say semi-decent, I mean semi-decent.)

I don't see how that would present any issue?

All you need to do is translate the face tracking commands, to keyboard commands then let the game's own engine handle the translation. 

It's no different from what the plugin is doing now. The facetracking software isn't trying to do the 3d translation of your desktop itself, it's sending the commands to compiz and allowing compiz to do the heavy lifting.

---

### Post by unsungboxer on 2008-11-29
can someone write some easy to understand install instructions?  Ive downloaded and extracted the snapshot.  I keep getting an error when i try to run ./configure ... error 127 cant find ...._options.sh.

Tried make, and make install.  No luck.  Using latest compiz and ubuntu ibex.

---

### Post by klange on 2008-11-29
> **unsungboxer said:**
> can someone write some easy to understand install instructions?  Ive downloaded and extracted the snapshot.  I keep getting an error when i try to run ./configure ... error 127 cant find ...._options.sh.

Tried make, and make install.  No luck.  Using latest compiz and ubuntu ibex.

You need the compiz dev packages, beyond which it's just "make && make install". For further support with Compiz, head over to the [the C-F forum](http://forum.compiz-fusion.org).

---

### Post by unsungboxer on 2008-11-29
> **WindowsSucks said:**
> You need the compiz dev packages, beyond which it's just "make && make install". For further support with Compiz, head over to the [the C-F forum](http://forum.compiz-fusion.org).


thanks for the quick response.  I downloaded the dev pkgs from synaptic.  opened terminal and:

> unsung@ubuntu:~/Desktop/headtracking$ make
bcop'ing  : build/headtracking.xml -> build/headtracking_options.h/bin/sh: --header=build/headtracking_options.h: not found
make: *** [build/headtracking_options.h] Error 127
unsung@ubuntu:~/Desktop/headtracking$ make install
bcop'ing  : build/headtracking.xml -> build/headtracking_options.h/bin/sh: --header=build/headtracking_options.h: not found
make: *** [build/headtracking_options.h] Error 127


sorry, noobish question, normally I don't have these issues.  I am really excited to get this working.

---

### Post by diablo75 on 2008-11-29
Something about that video looks completely backwards.  Shouldn't the window in the background have little movement, and the windows in the foreground move a lot more (because they're "closer" to the user)?

---

### Post by klange on 2008-11-29
> **diablo75 said:**
> Something about that video looks completely backwards.  Shouldn't the window in the background have little movement, and the windows in the foreground move a lot more (because they're "closer" to the user)?
The desktop isn't included in the 3d stacking process as it's a pain to deal with. The window directly in front is at screen level, so as compared to the rest of the screen (ie, the bezel) it shouldn't move at all. Everything behind it, except for the spacetime-defying wallpaper moves as if it were behind it.

If anything is wrong, don't blame me, blame OpenGL, as nothing is actually moving except windows on the Z axis and the camera point.

Regardless, the effect you described is possible with the keybindings I included for manually moving windows, but without input redirection having the top window move would make the entire system completely unusable.

---

### Post by mirhciulica on 2008-11-30
Hi! I can't compile the plugin :( I installed opencv, the dependencies I saw here and from C-F forums, but still I can't compile. :confused:
I'm very excited with this plugin. Please, does anybody know what to do to get rid of these errors?
Here is my output:

```
mirhciulica@ubuntu:~/Desktop/headtracking$ make
compiling : facedetect.c -> build/facedetect.lofacedetect.c:15:23: error: opencv/cv.h: No such file or directory
facedetect.c:16:28: error: opencv/highgui.h: No such file or directory
facedetect.c:28: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
facedetect.c:29: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
facedetect.c:30: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
facedetect.c:31: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
facedetect.c:37: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
facedetect.c:40: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
facedetect.c:41: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
facedetect.c: In function ‘init’:
facedetect.c:128: error: ‘cascade’ undeclared (first use in this function)
facedetect.c:128: error: (Each undeclared identifier is reported only once
facedetect.c:128: error: for each function it appears in.)
facedetect.c:128: error: ‘CvHaarClassifierCascade’ undeclared (first use in this function)
facedetect.c:128: error: expected expression before ‘)’ token
facedetect.c:130: error: ‘storage’ undeclared (first use in this function)
facedetect.c:130: warning: implicit declaration of function ‘cvCreateMemStorage’
facedetect.c:130: warning: nested extern declaration of ‘cvCreateMemStorage’
facedetect.c:131: error: ‘capture’ undeclared (first use in this function)
facedetect.c:131: warning: implicit declaration of function ‘cvCaptureFromCAM’
facedetect.c:131: warning: nested extern declaration of ‘cvCaptureFromCAM’
facedetect.c:138: error: ‘frame_copy’ undeclared (first use in this function)
facedetect.c:139: error: ‘trackingPoint’ undeclared (first use in this function)
facedetect.c:139: error: ‘CvPoint2D32f’ undeclared (first use in this function)
facedetect.c:139: error: expected expression before ‘)’ token
facedetect.c:140: error: expected expression before ‘)’ token
facedetect.c:143: error: ‘prevGray’ undeclared (first use in this function)
facedetect.c:143: error: ‘gray’ undeclared (first use in this function)
facedetect.c:144: error: ‘prevPyramid’ undeclared (first use in this function)
facedetect.c:144: error: ‘pyramid’ undeclared (first use in this function)
facedetect.c: In function ‘end’:
facedetect.c:164: warning: implicit declaration of function ‘cvReleaseImage’
facedetect.c:164: warning: nested extern declaration of ‘cvReleaseImage’
facedetect.c:164: error: ‘frame_copy’ undeclared (first use in this function)
facedetect.c:165: warning: implicit declaration of function ‘cvReleaseCapture’
facedetect.c:165: warning: nested extern declaration of ‘cvReleaseCapture’
facedetect.c:165: error: ‘capture’ undeclared (first use in this function)
facedetect.c: In function ‘headtrack’:
facedetect.c:241: warning: implicit declaration of function ‘cvRound’
facedetect.c:241: warning: nested extern declaration of ‘cvRound’
facedetect.c: In function ‘headtrackThread’:
facedetect.c:289: error: ‘IplImage’ undeclared (first use in this function)
facedetect.c:289: error: ‘frame’ undeclared (first use in this function)
facedetect.c:292: error: ‘capture’ undeclared (first use in this function)
facedetect.c:296: warning: implicit declaration of function ‘cvGrabFrame’
facedetect.c:296: warning: nested extern declaration of ‘cvGrabFrame’
facedetect.c:297: warning: implicit declaration of function ‘cvRetrieveFrame’
facedetect.c:297: warning: nested extern declaration of ‘cvRetrieveFrame’
facedetect.c:299: error: ‘frame_copy’ undeclared (first use in this function)
facedetect.c:300: warning: implicit declaration of function ‘cvCreateImage’
facedetect.c:300: warning: nested extern declaration of ‘cvCreateImage’
facedetect.c:300: warning: implicit declaration of function ‘cvSize’
facedetect.c:300: warning: nested extern declaration of ‘cvSize’
facedetect.c:300: error: ‘IPL_DEPTH_8U’ undeclared (first use in this function)
facedetect.c:301: error: ‘IPL_ORIGIN_TL’ undeclared (first use in this function)
facedetect.c:302: warning: implicit declaration of function ‘cvCopy’
facedetect.c:302: warning: nested extern declaration of ‘cvCopy’
facedetect.c:304: warning: implicit declaration of function ‘cvFlip’
facedetect.c:304: warning: nested extern declaration of ‘cvFlip’
facedetect.c: In function ‘detect’:
facedetect.c:315: error: ‘IplImage’ undeclared (first use in this function)
facedetect.c:315: error: ‘small_img’ undeclared (first use in this function)
facedetect.c:322: error: ‘subimg’ undeclared (first use in this function)
facedetect.c:322: error: ‘eig’ undeclared (first use in this function)
facedetect.c:322: warning: left-hand operand of comma expression has no effect
facedetect.c:322: error: ‘temp’ undeclared (first use in this function)
facedetect.c:322: warning: left-hand operand of comma expression has no effect
facedetect.c:323: error: ‘CvPoint2D32f’ undeclared (first use in this function)
facedetect.c:323: error: ‘swapPoint’ undeclared (first use in this function)
facedetect.c:326: error: ‘CvPoint’ undeclared (first use in this function)
facedetect.c:326: error: expected ‘;’ before ‘pt’
facedetect.c:334: error: ‘gray’ undeclared (first use in this function)
facedetect.c:335: error: ‘frame_copy’ undeclared (first use in this function)
facedetect.c:336: warning: implicit declaration of function ‘cvAlloc’
facedetect.c:336: warning: nested extern declaration of ‘cvAlloc’
facedetect.c:337: error: ‘prevGray’ undeclared (first use in this function)
facedetect.c:337: warning: implicit declaration of function ‘cvGetSize’
facedetect.c:337: warning: nested extern declaration of ‘cvGetSize’
facedetect.c:338: error: ‘prevPyramid’ undeclared (first use in this function)
facedetect.c:339: error: ‘pyramid’ undeclared (first use in this function)
facedetect.c:345: error: ‘cascade’ undeclared (first use in this function)
facedetect.c:346: warning: implicit declaration of function ‘cvCvtColor’
facedetect.c:346: warning: nested extern declaration of ‘cvCvtColor’
facedetect.c:346: error: ‘CV_BGR2GRAY’ undeclared (first use in this function)
facedetect.c:358: warning: implicit declaration of function ‘cvResize’
facedetect.c:358: warning: nested extern declaration of ‘cvResize’
facedetect.c:358: error: ‘CV_INTER_LINEAR’ undeclared (first use in this function)
facedetect.c:359: warning: implicit declaration of function ‘cvEqualizeHist’
facedetect.c:359: warning: nested extern declaration of ‘cvEqualizeHist’
facedetect.c:360: warning: implicit declaration of function ‘cvClearMemStorage’
facedetect.c:360: warning: nested extern declaration of ‘cvClearMemStorage’
facedetect.c:360: error: ‘storage’ undeclared (first use in this function)
facedetect.c:361: error: ‘CvSeq’ undeclared (first use in this function)
facedetect.c:361: error: ‘faces’ undeclared (first use in this function)
facedetect.c:361: warning: implicit declaration of function ‘cvHaarDetectObjects’
facedetect.c:361: warning: nested extern declaration of ‘cvHaarDetectObjects’
facedetect.c:363: error: ‘CV_HAAR_FIND_BIGGEST_OBJECT’ undeclared (first use in this function)
facedetect.c:370: error: ‘CvRect’ undeclared (first use in this function)
facedetect.c:370: error: ‘r’ undeclared (first use in this function)
facedetect.c:370: error: expected expression before ‘)’ token
facedetect.c:377: warning: implicit declaration of function ‘cvSetImageROI’
facedetect.c:377: warning: nested extern declaration of ‘cvSetImageROI’
facedetect.c:377: warning: implicit declaration of function ‘cvRect’
facedetect.c:377: warning: nested extern declaration of ‘cvRect’
facedetect.c:380: warning: implicit declaration of function ‘cvResetImageROI’
facedetect.c:380: warning: nested extern declaration of ‘cvResetImageROI’
facedetect.c:384: warning: implicit declaration of function ‘cvGoodFeaturesToTrack’
facedetect.c:384: warning: nested extern declaration of ‘cvGoodFeaturesToTrack’
facedetect.c:384: error: ‘trackingPoint’ undeclared (first use in this function)
facedetect.c:389: error: ‘pt’ undeclared (first use in this function)
facedetect.c:389: warning: implicit declaration of function ‘cvPointFrom32f’
facedetect.c:389: warning: nested extern declaration of ‘cvPointFrom32f’
facedetect.c:390: warning: implicit declaration of function ‘cvPoint2D32f’
facedetect.c:390: warning: nested extern declaration of ‘cvPoint2D32f’
facedetect.c:416: warning: implicit declaration of function ‘cvCalcOpticalFlowPyrLK’
facedetect.c:416: warning: nested extern declaration of ‘cvCalcOpticalFlowPyrLK’
facedetect.c:416: warning: implicit declaration of function ‘cvTermCriteria’
facedetect.c:416: warning: nested extern declaration of ‘cvTermCriteria’
facedetect.c:416: error: ‘CV_TERMCRIT_ITER’ undeclared (first use in this function)
facedetect.c:416: error: ‘CV_TERMCRIT_EPS’ undeclared (first use in this function)
facedetect.c:417: error: ‘CV_LKFLOW_PYR_A_READY’ undeclared (first use in this function)
facedetect.c:444: error: request for member ‘x’ in something not a structure or union
facedetect.c:444: error: request for member ‘x’ in something not a structure or union
facedetect.c:445: error: request for member ‘y’ in something not a structure or union
facedetect.c:445: error: request for member ‘y’ in something not a structure or union
facedetect.c:446: error: request for member ‘x’ in something not a structure or union
facedetect.c:446: error: request for member ‘x’ in something not a structure or union
facedetect.c:447: error: request for member ‘y’ in something not a structure or union
facedetect.c:447: error: request for member ‘y’ in something not a structure or union
facedetect.c:457: warning: implicit declaration of function ‘CV_SWAP’
facedetect.c:457: warning: nested extern declaration of ‘CV_SWAP’
make: *** [build/facedetect.lo] Error 1

```

Thanks!

---

### Post by mirhciulica on 2008-11-30
What dumb I am:mad: I forgot to compile opencv.
Sorry for that useless post.

---

### Post by Daveski on 2008-11-30
> **geoken said:**
> 
All you need to do is translate the face tracking commands, to keyboard commands then let the game's own engine handle the translation. 


Yes indeed - I cannot understand why this technique would need huge processing power. I thought that 3D scene rendering (in real-time) was already done by calculating what would be seen from the current viewpoint. Sure translating the player or observer viewpoint taking into account the head position AND the relative screen position to the 3D scene would add a little to the calcs, but I can't see how it is dramatically different. Perhaps the head tracking / face tracking needs some major processor time, but hey, we have multi-core and possibly multi-processor in all new machines these days. Give it a couple of years and the tracking will be calculated by software embedded in the webcam anyway.

Why would an outdoor scene cause any more problems than it already does? (I realize that there has to be a distance cut-off point to keep the processing down and the framerate up - hence mist/haze and the dreaded pop-ups).

---

### Post by psd lover on 2008-11-30
> **unsungboxer said:**
> thanks for the quick response.  I downloaded the dev pkgs from synaptic.  opened terminal and:

sorry, noobish question, normally I don't have these issues.  I am really excited to get this working.

i installed those packages as well and get the exact same error, ive tried compiling a few different ways and still no luck, i searched all over the web but i guess i was looking in all the wrong places

---

### Post by psd lover on 2008-11-30
> **unsungboxer said:**
> thanks for the quick response.  I downloaded the dev pkgs from synaptic.  opened terminal and:

sorry, noobish question, normally I don't have these issues.  I am really excited to get this working.

i installed those packages as well and get the exact same error, ive tried compiling a few different ways and still no luck, i searched all over the web but i guess i was looking in all the wrong places, thanks ahead of time for anyone who has a solution

---

### Post by psd lover on 2008-11-30
sorry for the double post, my internet was flipping out and im new to the forums and couldnt figure out how to delete the second one lol

---

### Post by psd lover on 2008-12-01
i finally figured out what i was doing wrong, i found [this link in the compiz forums]("http://forum.compiz-fusion.org/showthread.php?t=5303") and found out i had to run

```
sudo apt-get install compiz-bcop compiz-dev compizconfig-settings-manager build-essential libxcomposite-dev libpng12-dev libsm-dev libxrandr-dev libxdamage-dev libxinerama-dev libstartup-notification0-dev libgconf2-dev librsvg2-dev libdbus-1-dev libdbus-glib-1-dev libgnome-desktop-dev x11proto-scrnsaver-dev libxss-dev libxslt1-dev libtool
```

then i tried compiling the plugin again and got the same error as mirhciulica and realized i had to move my opencv folder where that comiled into and moved it to all the right spots in /usr/local/

i also moved an opencv folder (i forget which one because im not on the computer i installed everything on) into the headtracking folder, i dont think this effected anything but when i ran make i got no errors

after installing the plugin it worked fine when set to follow my mouse but i couldnt get it to work with my webcam, i also screwed up my entire gui when changing other settings, ill get it once i do some more configuring, thanks everyone for all your help, especially WindowsSucks for showing me this awesome plugin

---

### Post by R2D2! on 2009-01-25
H&#305;, I wanted to &#305;nstall th&#305;s plug&#305;n, but when I make, I get the follow&#305;ng:

```
ilhuitemoc@ilhuitemoc-laptop:~/Aplicaciones/headtracking$ make
convert   : headtracking.xml.in -> build/headtracking.xml
bcop'ing  : build/headtracking.xml -> build/headtracking_options.h
bcop'ing  : build/headtracking.xml -> build/headtracking_options.c
schema    : build/headtracking.xml -> build/compiz-headtracking.schema
compiling : headtracking.c -> build/headtracking.lo
compiling : facedetect.c -> build/facedetect.lofacedetect.c: In function ‘headtrackThread’:
facedetect.c:297: error: too few arguments to function ‘cvRetrieveFrame’
make: *** [build/facedetect.lo] Error 1
ilhuitemoc@ilhuitemoc-laptop:~/Aplicaciones/headtracking$ 

```

What's the problem??

—Ilhu&#305;temoc &#948;

---

### Post by R2D2! on 2009-02-03
*bump*

---

### Post by R2D2! on 2009-02-03
Never m&#305;nd; &#305; &#305;nstalled the latest vers&#305;on of the plug&#305;n, and now it works

---

### Post by klange on 2009-02-03
> **R2D2! said:**
> Never m&#305;nd; &#305; &#305;nstalled the latest vers&#305;on of the plug&#305;n, and now it works

Good time to bump, though, seeing as quite a few updates have been made in the past week (and I'm still working).

If anyone's interest has been spurred, enjoy [the new video](http://www.youtube.com/watch?v=XIT4MhZZCMs). I'll be getting another, better one up later today.

Funny, you posted about that bug before I got back into things. I had the same issue, of course, and went straight to the CV headers to see what had changed, [fixed it right up](http://gitweb.compiz-fusion.org/?p=users/klange/headtracking;a=blobdiff;f=facedetect.c;h=b6bb096f084fe1beaca74e42320e3313192829da;hp=cb32af3b3c7ed08494f2cf9c59c7848b7c350107;hb=7378f418a8707e5f455eab815caee95e8850bf00;hpb=4f7ef890b0d70aaf61eb57ce54b747ce528f2e66).

I'll be getting a guide up that should apply to Hardy and Intrepid for installing OpenCV the right way (which is full of pain and suffering), but not for another few days (maybe this weekend?).

---

### Post by Islington on 2009-02-03
> **WindowsSucks said:**
> Good time to bump, though, seeing as quite a few updates have been made in the past week (and I'm still working).

If anyone's interest has been spurred, enjoy [the new video](http://www.youtube.com/watch?v=XIT4MhZZCMs). I'll be getting another, better one up later today.

Funny, you posted about that bug before I got back into things. I had the same issue, of course, and went straight to the CV headers to see what had changed, [fixed it right up](http://gitweb.compiz-fusion.org/?p=users/klange/headtracking;a=blobdiff;f=facedetect.c;h=b6bb096f084fe1beaca74e42320e3313192829da;hp=cb32af3b3c7ed08494f2cf9c59c7848b7c350107;hb=7378f418a8707e5f455eab815caee95e8850bf00;hpb=4f7ef890b0d70aaf61eb57ce54b747ce528f2e66).

I'll be getting a guide up that should apply to Hardy and Intrepid for installing OpenCV the right way (which is full of pain and suffering), but not for another few days (maybe this weekend?).

awesome. looks like I am going to have to buy a webcam.

---

### Post by BDNiner on 2009-02-03
I am unable to open the video. I guess I will wait until i get home to watch this.

---

### Post by klange on 2009-02-03
Speaking of videos, I got my [new one up](http://www.youtube.com/watch?v=askKFSe3aLk). It's a bit more complete and has more than 7 seconds of reliable tracking footage.

---

### Post by polko on 2009-02-09
Hi, 

First of all i have to admit this is realy impressive stuff ! :cool:

I have installed this plugin with no problems. I have similar logitech camera as yours (same box only my led is blue not red) 2Mpix or something.. anyway it seems that everything is installed ok, but it doesn't work... 

I've also installed this stuff: [http://code.google.com/p/ehci/wiki/HeadTracking](http://code.google.com/p/ehci/wiki/HeadTracking), and it works flawlessly. I can see 3D box and "look around it". This means that my opencv and camera works fine.

But when I enable compiz plugin nothing happens, I can move windows by pressing debugging keys. Sometimes windows on desktop move or rather jump is the better word and I don't see 3D desktop (inside cube) like yours seen in video... Most of the times screen freezes and I have to kill X session not to mention my CPU load reaches almost 100%. 

I have AMD turion X2 64bit (dual core), 2G ram on DELL latitude D531 notebook (intrepid)

What can be wrong? Any ideas? How can i see inside 3D cube...
What should i expect after enabling plugin? maybe i'm missing something...

---

### Post by klange on 2009-02-09
> **polko said:**
> Hi, 

First of all i have to admit this is realy impressive stuff ! :cool:

I have installed this plugin with no problems. I have similar logitech camera as yours (same box only my led is blue not red) 2Mpix or something.. anyway it seems that everything is installed ok, but it doesn't work... 

I've also installed this stuff: [http://code.google.com/p/ehci/wiki/HeadTracking](http://code.google.com/p/ehci/wiki/HeadTracking), and it works flawlessly. I can see 3D box and "look around it". This means that my opencv and camera works fine.

But when I enable compiz plugin nothing happens, I can move windows by pressing debugging keys. Sometimes windows on desktop move or rather jump is the better word and I don't see 3D desktop (inside cube) like yours seen in video... Most of the times screen freezes and I have to kill X session not to mention my CPU load reaches almost 100%. 

I have AMD turion X2 64bit (dual core), 2G ram on DELL latitude D531 notebook (intrepid)

What can be wrong? Any ideas? How can i see inside 3D cube...
What should i expect after enabling plugin? maybe i'm missing something...
Did you check "Enable Webcam Tracking" in the options? (Note that the default values may not be sane for your camera, causing some rather interesting effects, I suggest increasing Width Adjustment and FoV Adjustment /before/ enabling the plugin)

To see inside the cube, you need to change its opacity - that's not part of this plugin. (Cube -> Transparent Cube)

---

### Post by polko on 2009-02-10
> **WindowsSucks said:**
> Did you check "Enable Webcam Tracking" in the options? (Note that the default values may not be sane for your camera, causing some rather interesting effects, I suggest increasing Width Adjustment and FoV Adjustment /before/ enabling the plugin)

To see inside the cube, you need to change its opacity - that's not part of this plugin. (Cube -> Transparent Cube)

Thank's for answer and advice :)

Of course i checked "enable webcam tracking" - I've tried increasing FoV Adjustments (as You suggested) from 100 to 500 and changed cube opacity to 30% and something happened ! :) I saw for few seconds how inside cube moves rather quickly, but most of the time my screen was all dark... It took me an effort to turn off this plugin without killing X (it's really hard to click checkbox when window constantly disappears) Next I've changed FoV from 500 to 250... after enabling plugin again my whole system stopped responding :( anyway it would be nice if there was key binding enabling/disabling headtracking...

Maybe later I'll try some other adjustments - it's not easy because I don't understand what these sliders do... ie: 
adjust head height - but what is the starting value? in fact head height is relative to distance from camera, right?

How does "width adjustment" relates to actual screen resolution? Mine is: 1440x900, it's value can be from 0 to 10000...


And one another thing: like I wrote in my earlier post, i've also installed "ehci". It has sample included called "boxView3D". After I start it, small window with my image appears (actually what camera sees)  and another window with boxes. Looking around boxes works nice without any adjustments... 


So maybe You could write more about these adjustments ?

Can You write what are your exact values that work for your camera?


[COLOR="DarkSlateBlue"][EDIT:] I've changed "tracker width adjustment" to 350 and FoV to default value of 100 -> it works better (it works at all) - but still very unstable :( 
i can see "inside cube" but i loose front wall of the cube with active windows like i would step inside..

and another thing: when i move my head to the right the back-side of the cube moves to the left - that's not very real, i don't know yet where can i change this behavior

also I can switch on/off headtracking feature with no harm, but disabling and enabling whole plugin again freezes my system :(
[/COLOR]

---

### Post by jo282 on 2009-02-25
Hi everyone, when i try to install the plugin i get an error and i dont know how to fix that. I passed 4 hours searching everywhere on the web and i cant find a solution. This is wath i got 

> jo@jo-desktop:~$ cd '/home/jo/Desktop/headtracking' 
jo@jo-desktop:~/Desktop/headtracking$ make
bcop'ing  : build/headtracking.xml -> build/headtracking_options.h/bin/sh: --header=build/headtracking_options.h: not found
make: *** [build/headtracking_options.h] Error 127
jo@jo-desktop:~/Desktop/headtracking$ make install
bcop'ing  : build/headtracking.xml -> build/headtracking_options.h/bin/sh: --header=build/headtracking_options.h: not found
make: *** [build/headtracking_options.h] Error 127
jo@jo-desktop:~/Desktop/headtracking$ 


Please help me !
Thanks!

---

### Post by klange on 2009-02-25
post redacted

---

### Post by jo282 on 2009-02-25
Thanks for your answer but.. i am new to ubuntu so can you tell me the command to enter in the terminal. Please dont tell me im a "noob" and giveup. Also i am french so please make it simple.

EDIT : I did this tutorial : [http://forum.compiz-fusion.org/showthread.php?t=1985](http://forum.compiz-fusion.org/showthread.php?t=1985)

And now i got > jo@jo-desktop:~/compiz/compiz/headtracking$ make && sudo make install
compiling : facedetect.c -> build/facedetect.lofacedetect.c: In function &#8216;detect&#8217;:
facedetect.c:360: error: &#8216;CV_HAAR_FIND_BIGGEST_OBJECT&#8217; undeclared (first use in this function)
facedetect.c:360: error: (Each undeclared identifier is reported only once
facedetect.c:360: error: for each function it appears in.)
make: *** [build/facedetect.lo] Error 1
jo@jo-desktop:~/compiz/compiz/headtracking$ 


PLEASE Help ME !!!

---

### Post by klange on 2009-02-25
post redacted

---

### Post by jo282 on 2009-02-25
Again im sorry but like i said im new to ubuntu so can you give me some help installing OpenCV ? Like a tutorial, link or just command. Please 	:confused:

Thank you so much for helping me and im sure im not the only one having trouble.

---

### Post by klange on 2009-02-25
post redacted

---

### Post by jo282 on 2009-02-25
I installed OpenCV like that :

1) sudo apt-get install build-essential

2) sudo apt-get install libgtk2.0-dev libavcodec-dev libavformat-dev libjpeg62-dev libtiff4-dev

3) Downloaded and untar version 1.1.0 of OpenCV from [http://sourceforge.net/project/showfiles.php?group_id=22870&package_id=16948](http://sourceforge.net/project/showfiles.php?group_id=22870&package_id=16948)

4) ./configure --prefix=/opt/opencv --enable-apps --enable-shared --with-ffmpeg --with-gnu-ld --with-x --without-quicktime CXXFLAGS=-fno-strict-aliasing

5) make

6)sudo make install

No errors, 
Then i downloaded the plugin headtracking and untar in the opencv-1.1.0 folder on my desktop (don`t know if that correct or if i need to place it to a specific location). 

Then i cd to the headtracking folder and typed make in the console and im getting this again

> jo@jo-desktop:~/compiz/compiz/headtracking$ make
compiling : facedetect.c -> build/facedetect.lofacedetect.c: In function &#8216;detect&#8217;:
facedetect.c:360: error: &#8216;CV_HAAR_FIND_BIGGEST_OBJECT&#8217; undeclared (first use in this function)
facedetect.c:360: error: (Each undeclared identifier is reported only once
facedetect.c:360: error: for each function it appears in.)
make: *** [build/facedetect.lo] Error 1


Please tell me wath im doing wrong and wath i need to do and please dont send me to a thread with 12 page and tell me is in that (no offense).

Thank you very much for trying to help me !

P.S : A complete step by step guide would be nice to be made to make this work from a fresh ubuntu installation

---

### Post by hanzomon4 on 2009-02-25
Wow dude (WindowsSucks) you got one crappy atitutde...

I think you have the wrong opencv version. You need the one from svn, svn is just a tool projects use to to share source code for software in development. You will need to install svn from the repos. Sorry I can't be more helpful but writing howtos on an iPhone hurts

---

### Post by klange on 2009-02-25
post redacted

---

### Post by jo282 on 2009-02-25
Im searching for 1 hours and still dont get it :@, How to hell does i download OpenCV from SVN 

I write this in terminal > cvs -z3 -d:pserver:anonymous@opencvlibrary.cvs.sourceforge. net:/cvsroot/opencvlibrary co -P opencv

And i get sometight like 

> jo@jo-desktop:~$ cvs -z3 -d:pserver:anonymous@opencvlibrary.cvs.sourceforge. net:/cvsroot/opencvlibrary co -P opencv
Unknown command: `net:/cvsroot/opencvlibrary'

CVS commands are:
        add          Add a new file/directory to the repository
        admin        Administration front end for rcs
        annotate     Show last revision where each line was modified
        checkout     Checkout sources for editin...
     
...version      Show current CVS version(s)
        watch        Set watches
        watchers     See who is watching a file
(Specify the --help option for a list of other help options)
jo@jo-desktop:~$ 
 

So then i tried installing SmartCVS and added "cvs -z3 -d:pserver:anonymous@opencvlibrary.cvs.sourceforge. net:/cvsroot/opencvlibrary co -P opencv" and it tell me to enter a login so i enter "anonymous" and then it ask me for a pasword, so i tried anonymous but it dont work.

Please help me !

---

### Post by klange on 2009-02-25
> **jo282 said:**
> Im searching for 1 hours and still dont get it :@, How to hell does i download OpenCV from SVN 

I write this in terminal 

And i get sometight like 



So then i tried installing SmartCVS and added "cvs -z3 -d:pserver:anonymous@opencvlibrary.cvs.sourceforge. net:/cvsroot/opencvlibrary co -P opencv" and it tell me to enter a login so i enter "anonymous" and then it ask me for a pasword, so i tried anonymous but it dont work.

Please help me !

The link is broken (there's a random space in it...)
Try this:
```
cvs -z3 -d:pserver:anonymous@opencvlibrary.cvs.sourceforge.net:/cvsroot/opencvlibrary co -P opencv
```

I'm requesting this topic be locked because it served its purpose a number of months ago.

If you have any more questions, please ask them [here](http://forum.compiz-fusion.org/showthread.php?t=9746&page=12).

---

### Post by phaed on 2009-02-25
> **cardinals_fan said:**
> I think that's very cool, but how would you actually use it in your day-to-day life?

They said that about the computer in the 1960s.  These things develop and uses are found.

---

### Post by jo282 on 2009-02-25
Umm dude... the link you tell me to try is the same exactly thing when i copy and paste it even in terminal or the other program it tell me the same thing

Edit : ok now it work i remove the space between the . and net entered it in terminal and it updated a bunch of file in like 2 sec

It created a directory opencv so i cd on it then do ./configure and it tell me that it does not exist

Please help me

---

### Post by jo282 on 2009-02-25
I finally installed OpenCV succesfuly (i think :confused:) with this [http://opencvlibrary.svn.sourceforge.net/svnroot/opencvlibrary/trunk/opencv/INSTALL]("http://opencvlibrary.svn.sourceforge.net/svnroot/opencvlibrary/trunk/opencv/INSTALL")

Now when i try to compile headtracking i got a new error :

> build/headtracking_options.c:859: warning: implicit declaration of function &#8216;compFiniDisplayOptions&#8217;
build/headtracking_options.c:859: warning: nested extern declaration of &#8216;compFiniDisplayOptions&#8217;
build/headtracking_options.c: At top level:
build/headtracking_options.c:864: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;headtrackingOptionsInit&#8217;
build/headtracking_options.c: In function &#8216;headtrackingOptionsFini&#8217;:
build/headtracking_options.c:881: error: &#8216;headtrackingPluginVTable&#8217; undeclared (first use in this function)
build/headtracking_options.c:882: warning: &#8216;return&#8217; with a value, in function returning void
build/headtracking_options.c:885: warning: implicit declaration of function &#8216;freeDisplayPrivateIndex&#8217;
build/headtracking_options.c:885: warning: nested extern declaration of &#8216;freeDisplayPrivateIndex&#8217;
build/headtracking_options.c: At top level:
build/headtracking_options.c:896: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
make: *** [build/headtracking_options.lo] Error 1


Please tell me wath is wrong

---

### Post by jo282 on 2009-02-26
Please, i`m so desperate, im sure im almost there please help me !!!!

---

### Post by overdrank on 2009-02-26
> **WindowsSucks said:**
> 
I'm requesting this topic be locked because it served its purpose a number of months ago.

If you have any more questions, please ask them [here](http://forum.compiz-fusion.org/showthread.php?t=9746&page=12).

Thread closed at the request of the op (original post).

---

