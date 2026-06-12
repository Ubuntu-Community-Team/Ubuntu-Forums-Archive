---
title: "Only Low graphics settings available in WoW"
date: 2010-11-11
forum: Wine
---

### Post by pacman43 on 2010-11-11
Hi,
I'm running wow through Wine and the game itself is working fine. The problem is I'm only able to select the lowest graphics settings possible. It wont let me select shadows, enhanced water effects etc.
I have a fairly good rig that should definitely be capable of running the game on Max settings.
All my drivers are up to date.

Anyone have a fix for this?

---

### Post by cwwilson721 on 2010-11-11
If you want the extra "eyecandy", it's only available in D3D, not OpenGL. So if you wish, install that (using winetricks, look elsewhere in this forum), or just be VERY happy with much faster framerates.

Running WoW/wine with Direct 3D is not advised, because D3D is not fully implemented in wine. And it is MUCH slower.

---

### Post by jrave on 2010-11-12
I'm unsure how confident/experienced you are with your linux install, so I hope I'm not teaching you to suck eggs but..
Linux can have problems with some cards which use power scaling/dual card switching for power consumtion vs performance balancing.

I myself am having a currently unresolvable issue with wow graphics as my laptop has an ATI HD 4570 which can switch to a 3200 under windows. Linux only sees the 3200 so I have to have low settings in order to play.

I'm pretty sure ATI also make non-dual cards which scale with power consumtion using windows only software.

Not sure how relevant this is to you, but theres my 50p

---

