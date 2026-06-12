---
title: "Blender won't start"
date: 2009-11-07
forum: Ubuntu Studio
---

### Post by 0AintLifeGrand0 on 2009-11-07
I have a problem with starting blender aswell.

I use ubuntu 9.10 and the following blender version: 2.49a+dfsg-0ubuntu2

I get the following message:
[COLOR=DimGray]Compiled with Python version 2.6.4.
Checking for installed Python... got it!
Xlib:  extension "GLX" missing on display ":0.0".
intern/ghost/intern/GHOST_WindowX11.cpp:177: X11 glxChooseVisual() failed for OpenGL, verify working openGL system!
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  18 (X_ChangeProperty)
  Resource id in failed request:  0x9
  Serial number of failed request:  21
  Current serial number in output stream:  22[/COLOR]

Looks like an openGL failure? Any clues?

B.t.w., I'm a linux/ubuntu n00b, so please not to much tech-advise.

Thanx in advance

---

### Post by 0AintLifeGrand0 on 2009-11-07
I figured out the problem.

On some linux-forum I read about n-videa drivers messing up openGL. 
Tip there was to remove them if they we're installed and return to the open source drivers.

So I did, and guess what it worked. Blender is working fine now.

I just hope I don't get display problems now. I installed the Nvidea drivers to get my 1440x900 widescreen mode working. Well it still works so.....

Kind regards

---

### Post by cotcot on 2009-11-07
You could try to download blender from the blender site, extract the blender downloaded file and just start the executable in the extracted folder.

---

### Post by wolfenden on 2009-12-27
I'm having the same problem with Blender on 9.10
It begins to load, the screen flashes grey then it just stops loading.
It certainly sounds like a graphics thing from the bits I've found so far but I can't make any progress.  I've disabled compiz, which definitely seems to have speeded up the computer but has made no difference to Blender.  It all worked fine on 9.04.
I have an aged and infamous Inspiron 5100 with an ATI Mobility Radeon 7500, I am I looking to uninstall all the ATI stuff from Synaptic?
Best
Wolfenden

---

