---
title: "Starcraft 2 with Intel i3 GMA HD in Ubuntu 10.10 with Wine 1.3"
date: 2011-04-12
forum: Wine
---

### Post by rablanken on 2011-04-12
I know, wordy title, but hopefully if this gets resolved others will be able to easily find it.

I'm trying to run Starcraft 2 in wine on my Toshiba R705 laptop.

So far I have:

1. Installed the latest Wine (when 1.2 didn't work).
2. Installed the digital download version of SC2.
3. Tried to edit the registry

What does work:

I can start the game, and use all menus and battle.net functions. The opening video also works.

What does NOT:

During matches, everything that is 3D is pitch-black, except for the unit portraits. Also, in the start-up screen, there is supposed to be a 3D image which doesn't work. Basically, the game is unplayable because all you see is black.



I THINK the problem is with the drivers for my graphics chip, specifically with DirectDraw3D in Wine. However I don't really have the know-how to fix this. On my other machine (with an Nvidia 7600 GT card, running 10.10 w/ Wine 1.3) SC2 works like a charm. I also know that SC2 runs on Windows 7 on this laptop.

Here's the info about this machine:
i3 processor
GMA HD
1366*768 rez
Ubuntu 10.10, updated
Most recent Wine (1.3..17)
Misbehaving program: Starcraft 2.


I've been looking around for a while, and I'd really appreciate some help.


EDIT: Here's the reg-key edits I tried:

(in "HKEY_CURRENT_USER/Software/Wine/Direct3D")

DirectDrawRenderer	opengl 
Multisampling		disabled 
OffScreenRenderingMode	backbuffer 
UseGLSL			enabled 
VertexShaderMode	hardware 
VideoMemorySize		(Set this value to the RAM on your video card) 

Enable limited ARB_fragment_shader support on 915/945: yes
S3TC compression: yes 

Those edits did nothing. I heard somewhere that SC2 doesn't even use -opengl, I'm not sure if that is true or not...
Also, I'm using the XP compatibility option, "run in a virtual desktop" 1366*768, lowest settings, etc.

---

### Post by cogadh on 2011-04-12
The problem is that Intel graphics solution. The Linux drivers for the Intel graphics chips aren't that great and most people have some kind of problems running non-native games on them. You're much better off sticking with that Nvidia machine for Wine gaming.

---

### Post by emlyn on 2011-04-29
I have the same issue; same symptoms, same hardware, running Natty and using wine installed via Ubuntu Software Centre.

Little more info: My machine dual boots, and sc II works perfectly well under win 7.

---

### Post by cogadh on 2011-04-29
It should work perfectly well under Win 7, its a Windows game running on a Windows system with Windows drivers. Running a Windows game on a Linux system using Wine with Linux drivers is going to produce very different results.

---

### Post by rasmus91 on 2011-05-01
So far i've heard that the Graphics has gotten better, but still, the intel onboard accelerator really sucks. [This is a thread]("http://ubuntuforums.org/showthread.php?t=963386") i did about my old laptop. I couldn't even run neverwinter nights on it, and thats a native Linux game though... If you want to play games on Linux nVidia is your way around it.

and im really sorry, but it seems thats just the way it is :(

---

