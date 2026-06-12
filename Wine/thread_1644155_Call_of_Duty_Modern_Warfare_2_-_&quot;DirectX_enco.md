---
title: "Call of Duty: Modern Warfare 2 - &quot;DirectX encountered an unrecoverable error.&quot;"
date: 2010-12-12
forum: Wine
---

### Post by bob6993 on 2010-12-12
Hi Guys,:?::?::?:
I recently installed Ubuntu 10.10 alongside windows and installed steam.
I copied my steam apps folder from windows and replaced the empty on on Ubuntu.
The game appears in steam as installed but once it gets past the launcher window i get a message:DirectX encountered an unrecoverable error.
              Check the readme for possible solutions.

How do i fix this?
PS:I tried adding string under reg edit but i don't really get what to do

HP Pavilion DV6 3033TX
Graphics Card: ATI Mobility Radeon
Processor: Intel i3
OS: Ubuntu 10.10 (Installed with WUBI)

Any help appreciated!:p:p:p

---

### Post by CharlesA on 2010-12-12
Are you trying to run it in Wine?

---

### Post by bob6993 on 2010-12-16
kind of i am just copying the steamapps folder from windows and replacing the empty one.

---

### Post by CharlesA on 2010-12-17
Well you'd have to be using Wine to run windows apps.

In any case, I've bumped the thread over to the Wine area.

---

### Post by ronnielsen1 on 2010-12-17
You will have to do some tweaks in winecfg (Type winecfg in a terminal
>  **What works**

-Gameplay
   -Sound
   -Videos
 
**What does not**

-shadows on made the game terribly slow
   -depth of field
   -soften smoke edges
 
**What was not tested**
Multiplayer 

**Additional Comments**

Rig: AMD x2 6000+ @3,3 ghz, 4 GB 800mhz ram, Geforce 8800GTS 320MB, kernel 2.6.31-14, video drivers 190.42, ext4 filesystem
Game settings:1280x1024, fullscreen, all detail max (exept shadows off, soften smoke edges off, detp of field off), AA 4x (from Nvidia settings)

had to use tweaks:

on console run “wine regedit” and then:
- in HKEY_CURRENT_USER-Software-Wine create, if it's doesn't already exists, a new key named Direct3D
- in Direct3D create the following strings with the following values:
string: DirectDrawRenderer          value: opengl
string: OffscreenRenderingMode  	value: fbo
string: RenderTargetLockMode    	value: auto
string: UseGLSL                           value: readtex
string: VideoMemorySize	            	value: (memory size of your graphic card)


[http://appdb.winehq.org/objectManager.php?sClass=version&iId=18348&iTestingId=46478](http://appdb.winehq.org/objectManager.php?sClass=version&iId=18348&iTestingId=46478)

---

### Post by bob6993 on 2011-01-02
Yeah i tried to but i don't quite understand what type in what box when it comes to strings.
Can you post some screen shots?
Thank You for the help anyway!

---

### Post by bob6993 on 2011-01-04
Hi guys,
I did what you said to do any it works but there is no text, how do I fix this?

---

