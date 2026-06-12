---
title: "[SOLVED] Memorry Exception when opening WoW"
date: 2008-12-08
forum: Wine
---

### Post by Mustardo on 2008-12-08
Hello and thank you to anybody who may be able to help 

Every time I try to open WoW I encounter an error.  

[I]This application has encountered a critical error:

ERROR #132 (0x85100084) Fatal Exception
Program:	C:\Program Files\World of Warcraft\Wow.exe
Exception:	0xC0000005 (ACCESS_VIOLATION) at 0073:004118F0

The instruction at "0x004118F0" referenced memory at "0x00000000".
The memory could not be "read".[/I]


As far as I can gather this is a hardware issue?

Therefore I have run the memtest on the ubuntu live cd with no issues, tried different installs of WoW (direct install on pc, and a copy of the one that used to run on this exact pc).  I have also tried the WoW repair all with no joy.

I am running:

Ubuntu 8.10 
Wine 1.1.10 + (development packages)

nVidia 7600gs
2 Gb Ram 
intel core 2 duo (2Ghz)

If anyone could explain this error to me or better yet suggest a fix I would be greatly appreciative.

It was only after a hard drive failure and replacement that I had to re-install everything and cannot understand why now WoW will not run as it did flawlessly before.

---

### Post by hikaricore on 2008-12-08
1. Are you drivers properly installed?
2. Are you running the game in OpenGL mode?

---

### Post by Eviljim on 2008-12-08
Hi there,

Error #132 is a very generic error message for WoW, and does not indicate a specific problem (like a corrupt file in Error #134 for example).

I know this guide is for Windows, but you may be able to get some hints on other things to try.

[http://eu.blizzard.com/support/article.xml?articleId=24198]("http://eu.blizzard.com/support/article.xml?articleId=24198")

My feeling is that access memory violation refers to the graphics card memory rather than the system memory, so it would be wise to try other versions of your nvidia driver. You may be able to find out which version is the most stable by doing a search through these forums or via google.

Hope you manage to resolve this.

---

### Post by Mustardo on 2008-12-09
Thank you for all your help.

I am almost certain that it is an issue with my graphics card driver now.  
I remember my flat mate using a graphics card "management" GUI that allowed him to select or auto detect the graphics card, I remember that is what I used last time to set it up (successfully).  But now I can't find the application in add/remove or by googling,  from memory it was called something like 'envy'?? could anyone suggest?

I am currently using the 177 accelerated card driver version that was prompted to install after the initial boot (System => Administration => Hardware Drivers) But have a feeling it may be incorrectly detecting my card.

In effort to find another driver to try or the ability to manually select my exact card I have attempted to follow this guide [http://uk.download.nvidia.com/XFree86/Linux-x86/177.82/README/chapter-03.html](http://uk.download.nvidia.com/XFree86/Linux-x86/177.82/README/chapter-03.html)  But are having difficulty exit the X server and terminating all OpenGL applications (dont know how to do that  (Q_Q) )  I can 'cd' directory and sudo run the app but it says X server is still running????  Anyway I may be going down an unnecessary track with this?

Basically I would like help to install graphics card drivers.

Thanks again.  

PS this community ROCKS

---

### Post by Eviljim on 2008-12-09
The program you were probably using was EnvyNG, which was in the Hardy repositories. Im not sure if its in Intrepids, and the website for the developer doesnt mention intrepid.

[http://www.albertomilone.com/envyfaq.html#D]("http://www.albertomilone.com/envyfaq.html#D")

Im using an ATi card at the moment, so I am not entirely sure which nvidia driver version is best for Intrepid. The last version on nvidias site is 177.82, but if you search the beta drivers there is a 180.06.

Check this post on how to install the nvidia drivers on linux.

[http://www.nvnews.net/vbulletin/showthread.php?t=72490]("http://www.nvnews.net/vbulletin/showthread.php?t=72490")

---

### Post by Mustardo on 2008-12-11
Have just done a clean install on Ubuntu 8.04.1 LTS just on the chance something was not supported under version 8.10 (envyNG)

Also installed envyNG ran it installed NVidia drivers have tried different versions,  also a clean install of WOW 

Also I made sure to include** SET gxApi "opengl"** in the wtf.config file in my case after a clean install it was RunOncewtf.config

AND SUCCESS!!!!!!


I would highly recommend envyNG to people using ATI and especially NVidia graphics cards works a treat and is a lot more user friendly than other methods (for us more novice users)

Thanks hikaricor and Eviljim.

FREEWARE FTW!

---

### Post by Eviljim on 2008-12-11
Glad you sorted the problem.

To be honest, I had graphics issues after upgrading from 8.04 to 8.10, with the Ati 8.11 drivers. Having tried all the applicable ATi driver available via their website, and via EnvyNG, I still had issues.

A complete format and install of 8.10 from CD cured the problem, even using the repo driver for Ati.

It seems a bit hit and miss I think.

---

### Post by darkknight045 on 2008-12-11
As a note:

EnvyNG is not available for Intrepid (afaik) because they have built-in a GUI for installing the latest drivers for your video card.  

If you go to System -> Hardware Drivers(?Something like this) you'll be able to access this GUI to enable the nvidia drivers.

---

