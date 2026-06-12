---
title: "Blender locks up on TAB Press"
date: 2009-09-02
forum: Ubuntu Studio
---

### Post by Spaceman9 on 2009-09-02
I'm trying to do the first animation tut in the Blender Manual. It's called "Your First Animation in 30 plus 30 Minutes Part 1".

Everything goes fine until I press TAB to go into Edit Mode and Blender locks up and so do any other apps I have running. I have to press the warm reboot button to get out of the lock up. I tried using Ctrl+Alt+F2 and Ctrl+Alt+Del but they don't do anything.

I'm running Blender on a computer I built in 2001. It has an ATI ALL-IN-WONDER 128 PRO video card with OpenGL, but I'm using the default video driver from Ubuntu Studio 9.04 so I don't know if that has OpenGL or not.

The ATI site says my video card does OpenGL [http://ati.amd.com/products/rage128/aiw128/specs.html](http://ati.amd.com/products/rage128/aiw128/specs.html)

Thanks for any help.

---

### Post by UbuKunubi on 2009-09-03
Hello!

Im also learning blender, and kept getting random program quits while going through the tutorial -
 however I am now using 2.49b, directly from: [http://mirror.cs.umn.edu/blender.org/release/Blender2.49b/blender_2.49b-ubuntu0904_i386.deb](http://mirror.cs.umn.edu/blender.org/release/Blender2.49b/blender_2.49b-ubuntu0904_i386.deb)

I am working from the utter start since i have no clue but want to learn.

Dont forget to remove the original 2.48 before installing mind!

Hope this helps,
Ubu

---

### Post by Spaceman9 on 2009-09-03
Thanks for the help UbuKunubi. I'll try installing Blender from the Blender web site. I wonder if there's a bug in the Ubuntu Blender?

---

### Post by Spaceman9 on 2009-09-03
UbuKunubi as I understand this business of installing a new package one has to first uninstall what's already there. Because I'm using Ubuntu Studio, I have to uninstall the ubuntustidio-graphics package to uninstall Blender. Blender, you see, is part of the ubuntustudio-graphics package in Ubuntu Studio. 

So, the long and short of it is, if I uninstall the ubuntustudio-graphics package to get rid of Blender I'll also be uninstalling about twenty other graphics programs. Hardly seems worth the effort does it!

Still, you can't win it if you're not in it and if I uninstall the ubuntustudio-graphics package I'll be deep in it.

I tried the same tut in PCLOS 2009.2 and the same thing happens when I press TAB. So, perhaps this is more a hardware problem then a software problem. Either way it all seems a right kurfuffle. I thought Linux just works.

---

### Post by UbuKunubi on 2009-09-03
> **Spaceman9 said:**
> I'm trying to do the first animation tut in the Blender Manual. It's called "Your First Animation in 30 plus 30 Minutes Part 1".

Everything goes fine until I press TAB to go into Edit Mode and Blender locks up and so do any other apps I have running. I have to press the warm reboot button to get out of the lock up. I tried using Ctrl+Alt+F2 and Ctrl+Alt+Del but they don't do anything.

I'm running Blender on a computer I built in 2001. It has an ATI ALL-IN-WONDER 128 PRO video card with OpenGL, but I'm using the default video driver from Ubuntu Studio 9.04 so I don't know if that has OpenGL or not.

The ATI site says my video card does OpenGL [http://ati.amd.com/products/rage128/aiw128/specs.html](http://ati.amd.com/products/rage128/aiw128/specs.html)

Thanks for any help.

That was also my first fear - however I'm using Jaunty.... so first I simply used add/remove to uninstall blender 2.48 - when that process was complete I visted the link I posted earlier, and downloaded the .deb file. 
When it completed I simply right clicked, and used 'open' to start the installing the new version. Normally any needed packages are then downloaded and installed before the main dependant package (in our case blender 2.49b).

That was all I did, and it i've managed to get several simple animations done, although there is still a lot to learn.

Can you let me know what happens when you try the same method as me?
For all I know Ubuntu Studio is based on 9.04 (Jaunty) so I would expect them both to behave in a very similar manner....

Ubu

---

### Post by Spaceman9 on 2009-09-03
Ubuntu Studio is Ubuntu with the extra graphics, audio and video programs added.

Right, I uninstalled ubuntustudio-graphics and it didn't uninstall Blender or any other graphics programs. So, I had to uninstall Blender myself. I also uninstalled yafray. Then I installed the Blender .deb package. 

The same thing happens when I press TAB. I also tried changing to Edit with the menu and everything locks up. 

Can your computer run compiz-fusion? Mine can't. Perhaps that's why I can't use Blender. I don't know. 


UPDATE: I installed the windows version of Blender to see if that had the same problem with TAB. It does! So, it must be my ancient ATI video card. I think I need to build a new computer. I've had this one for eight years. I suppose that's good value for money.Ta for your help UbuKunubi.

---

### Post by UbuKunubi on 2009-09-04
> **Spaceman9 said:**
> Ubuntu Studio is Ubuntu with the extra graphics, audio and video programs added.

Right, I uninstalled ubuntustudio-graphics and it didn't uninstall Blender or any other graphics programs. So, I had to uninstall Blender myself. I also uninstalled yafray. Then I installed the Blender .deb package. 

The same thing happens when I press TAB. I also tried changing to Edit with the menu and everything locks up. 

Can your computer run compiz-fusion? Mine can't. Perhaps that's why I can't use Blender. I don't know. 


UPDATE: I installed the windows version of Blender to see if that had the same problem with TAB. It does! So, it must be my ancient ATI video card. I think I need to build a new computer. I've had this one for eight years. I suppose that's good value for money.Ta for your help UbuKunubi.

LOL!
No, my pc can't run compiz-fusion - this machine was found in a skip!
I'm not sure you should have uninstalled the graphics package... could you do a fresh install (or re-install the graphics packages)?? and then try the new .deb for blender?

For what its worth it take this machine 47 mins to render 100 frames with very little in them.

Sorry about the late reply (parental duties)

Ubu.

---

### Post by cotcot on 2009-09-04
No need to install Blender. It is enough to download the 2.49b (or other) tar.bz2 file, extract it, go into the extracted map and just start blender with the binary in the extracted folder. I made a launcher on my desktop  (right mouse click on the desktop; create launcher and put 'home/cotcot/blender-2.48a-linux-glibc236-py25-x86_64/./blender -g noaudio' in the command field). -g noaudio is added to get sound while other sound applications are open.

---

### Post by andrew2276 on 2009-09-04
I am also going to make my first annimation with it. Hope I will make it without any problem. Thanks

---

### Post by Spaceman9 on 2009-09-04
UbuKunubi I had to uninstall the windows version first. Then I uninstalled Blender 2.49b.deb. I reinstalled ubuntustudio-graphics and it only wanted to install Blender 2.49a. Then I installed Blender 2.49b.

So, I booted Blender 2.49b and hit TAB and everything locked up again. I discovered clicking on Sculpt Mode also locks up everything. For some reason clicking on Texture Paint doesn't lock up anything. It's at times like this I wax nostalgic for Autodesk Animator.

I found two other 3D apps in the repos. One is luxrender. I can't get it to run. The other is wings3d. I can't get it to run either. 

GIMP and Inkscape work ok so I can at least use those, and I found a 2D animation app called pencil [http://www.pencil-animation.org/](http://www.pencil-animation.org/) it's in the Ubuntu repos too.

Also in the Ubuntu repo is k3d which is designed from-the-ground-up to generate motion-picture-quality animation with RenderMan-compliant render engines (such as aqsis).

Some of its features are:
 - Record and play back interactive tutorials and macros.
 - Able to create and edit documents in multiple realtime OpenGL
solid, shaded, texture-mapped views. You can even model, animate, and
interact with animations while they play back.
 - Unlimited Undos/Redos.
 - Default output to Pixar Renderman Interface Bytestream (RIB) files.
 - K-3D documents are stored using a simple, flexible, easy-to-understand
 XML markup.
 - Scripting interface supports Python, with open API for other scripting
languages.

If you get k3d also install the Aqsis package first.

The Aqsis Rendering System consists of a set of libraries and
applications for creating high-quality computer imagery using the
Pixar RenderMan Interface.

And also in the repos is synfig.

synfig is a vector based 2D animation renderer. It is designed to be
capable of producing feature-film quality animation. It eliminates the
need for tweening, preventing the need to hand-draw each frame.

This package contains the command-line renderer, for the GUI animation
editor, please install synfigstudio.

So, I'm off to investigate k3d and synfig. Bob's your uncle.

---

### Post by Spaceman9 on 2009-09-04
> **cotcot said:**
> No need to install Blender. It is enough to download the 2.49b (or other) tar.bz2 file, extract it, go into the extracted map and just start blender with the binary in the extracted folder. I made a launcher on my desktop  (right mouse click on the desktop; create launcher and put 'home/cotcot/blender-2.48a-linux-glibc236-py25-x86_64/./blender -g noaudio' in the command field). -g noaudio is added to get sound while other sound applications are open.

That kind of sounds like what I did with Celtx. In the end though I installed the windowz version of Celtx because I just couldn't get the linux version to work.

I think some of these new versions of apps don't like my old hardware. I think my next move is to WalMart for one of those shiny new fangled laptops. May be I'll try Intel this time.

---

### Post by Spaceman9 on 2009-09-04
Good luck andrew2276.

---

### Post by Spaceman9 on 2009-09-05
Ok, I think my computer is cursed! k3d uses OpenGL just like Blender so k3d locked after it booted up. synfig ran it's splash screen and didn't do anymore. It never loaded completely. Pencil works though. One out of three isn't to good thought. A new laptop sounds like a really good idea I think.


UPDATE: I also have PCLOS 2009.2 installed so I installed synfig and it works fine in PCLOS.

---

### Post by Spaceman9 on 2009-09-07
UPDATE: 

I haven't found a way to solve the problem I'm having with Blender 2.49b so I'm using a work around in the mean time. 

I discovered by looking around the Blender site they have all the versions of Blender for down load. I tried one at a time until I found one that doesn't lock up.

It's very important to download a "static" file. The "static" files include everything to satisfy the dependencies. I discovered version 2.48a works on my computer without any problems after I downloaded this file

blender-2.48a-linux-glibc236-py25-i386-static.tar.bz2  2008-Oct-23 08:12:08  14.3M application/x-bzip

I opened the file with Archive Manager and Extracted it to the user folder. Then double clicked on the "blender" icon and it runs perfectly.

---

