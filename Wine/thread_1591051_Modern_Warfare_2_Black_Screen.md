---
title: "Modern Warfare 2 Black Screen??"
date: 2010-10-08
forum: Wine
---

### Post by jazzyjonesy on 2010-10-08
Hi guys, this is my first first post so bare with me please! I've been running Ubuntu 10.04 for a while now and love it, I only use Windows for gaming. I've recently decided to try and get my steam games working in Ubuntu. Easier said than done! I now have steam installed through Wine and also Modern Warfare 2 which is my main game. When I start the game it runs and goes to the main menu (music and sounds from moving mouse prove this) but I am left with a black screen with bits of text showing occasionally. I'm fairly sure it's a resolution problem (but not certain) and I was wondering if anyone could help me get it running? Especially as my xp hard drive has done what windows does best and crashed! I would be very grateful for any help. Thanks in advance!

---

### Post by jazzyjonesy on 2010-10-09
Have now changed started resolution to 1280x768 so i'm not so sure resolution is the problem. And ideas yet? I was really hoping someone could help me out on this!

---

### Post by s.fox on 2010-10-09
Thread moved to Wine forum.

---

### Post by Half-Left on 2010-10-09
You won't be able to play online because of PunkBuster. Try the following for your problem:

> 
string: DirectDrawRenderer          value: opengl
string: Nonpower2Mode              	 value: repack
string: OffscreenRenderingMode  	value: fbo
string: RenderTargetLockMode    	value: auto
string: UseGLSL                           value: readtex

you can use winetricks to set these things without using regedit.

---

