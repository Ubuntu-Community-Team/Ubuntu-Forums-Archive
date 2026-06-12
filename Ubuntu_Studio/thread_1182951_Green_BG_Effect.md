---
title: "Green BG Effect"
date: 2009-06-09
forum: Ubuntu Studio
---

### Post by B4RR13N705 on 2009-06-09
Hi, ive heard a lot about that effect of the green background, used in movies.
I want to do that for a high school "homework".
I tried editing a few images with green bg in GIMP. It works, but the other color dye a litle. Anyway, is there a way to do this on a video? what program should i use? 
what program should i use to this with some pictures?

---

### Post by lukeiamyourfather on 2009-06-09
Any compositing or motion graphics application should be able to handle the task. To reduce the bleeding color from the green/blue screen selectively desaturate colors within that range, which also means that the subjects can't be similar in color to the green/blue screen.

There are dozens of video compositing applications out there like After Effects, Nuke, Fusion, Combustion, Smoke, etc. Most of them are commercial software and/or for Windows with a few exceptions. I think Blender has compositing tools, and there's also Jahshaka (might be defunct). There might be other open source compisiting applications but those are what I know of off the top of my head. Cheers!

EDIT: A free but not open source option would be to use the compositing tools in Houdini Apprentice.

---

### Post by B4RR13N705 on 2009-06-09
ill try Houdini :)

---

### Post by Stochastic on 2009-07-27
You might want to give this program a try: [http://effectv.sourceforge.net/](http://effectv.sourceforge.net/)

Blender will also do it, here's a tutorial: [http://wiki.blender.org/index.php/Doc:Tutorials/Composite_Nodes/Types/Matte/ChromaKeying](http://wiki.blender.org/index.php/Doc:Tutorials/Composite_Nodes/Types/Matte/ChromaKeying)

---

### Post by Aphorism on 2009-07-31
The term you are looking for is keying - deriving an alpha channel matte from a uniform hue.

The two most common forms of this are green screen and blue screen.  Ideally they are lit uniformly at a level that delivers the best results from your keyer.

The bulk of keying is usually done in an application known as a compositor.  See Nuke or Shake for example.

In Free Software, we have Blender.  

If you are able to get uniformly lit background colour, you might be able to perform it as a high school project.  It isn't the easiest thing in the world to accomplish however, so be ready to spend many hours learning and experimenting.

The best keying can probably be achieved using math nodes in Blender.  See [http://www.blendedplanet.com/?SFX_Tutorials:The_Ultimate_Keyer](http://www.blendedplanet.com/?SFX_Tutorials:The_Ultimate_Keyer).

Hope this helps...

---

