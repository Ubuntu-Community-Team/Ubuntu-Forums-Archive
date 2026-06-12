---
title: "Blender crashes immediately when launched"
date: 2012-07-28
forum: Ubuntu Studio
---

### Post by Gecco3 on 2012-07-28
Hi,
Every time I launch Blender, it crashes before completely loading.  All that comes up is a fullscreen gray window titled "Blender."  After a few seconds of this gray window, the program quits.  It does this every time.  Rebooting does not help.
If anyone knows how to fix this problem, please help.
If it would help, I can post the list of hardware I'm using.
I'm running the XFCE desktop in Ubuntu Studio 12.04, if that helps.  I cannot tell what version of Blender because it never loads far enough.
Thanks in advance for your help.
-Gecco3

---

### Post by jejeman on 2012-07-29
Run it from terminal and see if there is some clue whats wrong.
Run
```
blender -h
```
to see the version

---

### Post by Gecco3 on 2012-07-29
Thanks.  It says it's version 2.62.
When I ran it from the command line, I got the following error:
```
blender: swrast/s_span.c:1327: _swrast_write_rgba_span: Assertion `colorType == 0x1401 || colorType == 0x1406' failed.
Aborted (core dumped
```
What does this mean?

---

### Post by Gecco3 on 2012-07-30
Well, I installed a new graphics card (GTX 570) and now Blender works fine.  It must not have been compatible with the (very) old one I was using before.  The old one was an ATI Radion 9250, and was so old that it used a PCI slot instead of a PCI-e.
Thanks for your help, jejeman.

---

### Post by BcRich on 2012-07-31
Hi Gecco3
my post is a couple of hours too late, i read your thread last night and the first thing that occurred to me was to ask you what graphics card you were using. 
Anyway, I'm glad to hear you managed to fix the problem. Happy Blendering :)

---

### Post by Gecco3 on 2012-08-01
Thanks, BcRich.  I didn't immediately suspect the graphics card because I wasn't fully aware of how much the software depended on the card.

---

### Post by BcRich on 2012-08-01
> **Gecco3 said:**
> Thanks, BcRich.  I didn't immediately suspect the graphics card because I wasn't fully aware of how much the software depended on the card.
Hi Gecco3
no problems :) if you are still interested I found this page on blender system requirements [http://www.blender.org/features-gallery/requirements/](http://www.blender.org/features-gallery/requirements/)
Strange thing is that it seems like some 9250's make the grade (amusing they have 64MB+ RAM). I used to run older versions of Blender 2.4x on a 9800 with 128MB RAM and it actually worked pretty well!
Currently I'm using a 6870 with 1GB RAM and no complaints thus far :)
BTW. graphics cards are really important for an application like Blender because it uses OpenGL to render 3D data in the viewport (this is typically handled by your graphics card). 
Your CPU is also really important as faster CPU's with more cores can help to speed up non-realtime render times.
And finally RAM is particularly useful if you plan on doing alot of sculpting (amongst other viewport tasks), as that is where polygonal data is cached and once your system runs out of RAM it has to resort to swap space which can reduce viewport interactivity to a crawl.
hope that's helpful :)
good luck!

---

### Post by Gecco3 on 2012-08-01
Thanks, BcRich.  That's really helpful.  The card I was using had 128 MB, so it should have worked.  Maybe it had some defect in the hardware that diminished its capability enough that Blender couldn't use it, but not so much that less demanding programs couldn't.
Whatever the problem was, though, it's fixed now.  Thanks for your help
-Gecco3

---

