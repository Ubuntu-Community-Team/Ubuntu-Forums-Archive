---
title: "How can i draw on frames of videos?"
date: 2009-02-07
forum: Ubuntu Studio
---

### Post by higashi on 2009-02-07
Hi, i wanna add some animation into live action videos.  i dont know what to use or how.. pleez help.

---

### Post by cotcot on 2009-02-08
Depends on what editor you use.
Look for an editor that is able to mix images with video. 

In case of Blender VSE you can do it as follow :

1. Make your animation on a transparent underground with gimp and save it as png (png save transparency). 

2. Open blender VSE and import the video an the png above each other (so in different tracks). Use the effect "alpha over" to overlay the png on the video. (use "premul" in the filter buttons for better png quality). 

3. Render

This might be cryptic if you are not use to blender VSE. In that case please use the blender [[COLOR="Red"]VSE wiki[/COLOR]]("http://wiki.blender.org/index.php/Manual/Using_VSE").

An alternative way to do is to decompose the video in frame and to add your animations on the frames individually with gimp. But that is less convenient because you will need to open and save many files.

---

### Post by rylleman on 2009-02-08
Do you have any examples of what you want to achieve?
It would be a lot easier to help if you narrow it down a little.
Basically you would import the live footage (most likely as a series of still images) into an animation software where you do your animation. Then export this animation and comp it together with the live action material.

---

### Post by higashi on 2009-02-08
I just want to do simple animation (using a simple paintbrush tool) .. i dont want to use any 3D programs cuz im completely useless when it comes to blender and stuff.

......Yeah so all i rly want is a simple paintbrush tool for my videos?
(my preffered editor is LiVEs, but im open to others.. as long as they're as simple as possible.)

I've tried using GimpGAP a long time ago, i went thru hell to get it to work and never succeeded. so id rather not go thru that again.

---

### Post by higashi on 2009-04-04
BUMP

need another example of what i want to do?  I want something simple like..

Example: me fighting a stickman.

---

### Post by rylleman on 2009-04-05
Try Synfig.

---

### Post by higashi on 2009-04-05
Thanks. But are there any other , more simple, programs?

---

