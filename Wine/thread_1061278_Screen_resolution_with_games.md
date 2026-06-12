---
title: "Screen resolution with games"
date: 2009-02-05
forum: Wine
---

### Post by Acradon on 2009-02-05
Hi there, 

I have two windows based games on my Ubuntu machine (8.10). oth of them have the problem, that the screen resolutionis not optimised. Especially problematic is CSI 3. this game run perfectly under WINE, but the bottom of the screen is cut off, which is problematic, as all the text is in subtitles, that got cut of. 
ANy idea on how to solve this?

Acradon

---

### Post by Dizzle7677 on 2009-02-05
The [Wine wiki]("http://wiki.winehq.org/UsefulRegistryKeys") has all the info about screen resolutions/Xvid mode registry settings. Your best bet is to use the X11 Driver->UseXVidMode or DirectDraw->ForceRefreshRate keys unless you can change the refresh rate in the game's config file(if it has one).

---

