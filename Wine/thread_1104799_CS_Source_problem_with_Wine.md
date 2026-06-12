---
title: "CS: Source problem with Wine"
date: 2009-03-24
forum: Wine
---

### Post by humphreybc on 2009-03-24
Hi there,

So I installed Steam, logged in and downloaded CS: Source and ran it. The menus and everything ran fine, but once I got into a game the graphics were completely screwed up and it was unplayable. It froze, then crashed and I was going to disable compiz and try it again but now when I try to start it, it gives me this error: ( see attached also.)

> 
Error!

MountAppFilesystem() failed:
SteamMountAppFilesystem(240,0,0x5dae7c4) failed with error 1: The registry is in use by another process, timeout expired


I am using Wine 1.1.17 and Ubuntu 8.10 Intrepid Ibex.


Thanks for your help :)

---

### Post by cogadh on 2009-03-24
That sometimes happens when Steam fails to exit cleanly. In order to correct it, you just need to start and exit out of Steam a few times without launching any games. If that doesn't correct the issue, sometimes right-clicking on the offending game and selecting "Verify integrity of game cache..." will correct the issue.

BTW - In the future, disable Compiz/Desktop Effects before you run anything with Wine. Compiz essentially "breaks" OpenGL functionality as far as Wine is concerned, so most, if not all games run through Wine will not work properly with the flashy effects turned on.

---

### Post by humphreybc on 2009-03-24
Okay I got it running, but even on low settings the graphics are screwed up. I get this odd sort of glitchy thing where there are jagged lines and crap all over the screen. I disabled compiz.

---

