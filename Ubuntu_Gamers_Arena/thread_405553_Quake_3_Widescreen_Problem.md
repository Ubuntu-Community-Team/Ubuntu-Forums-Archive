---
title: "Quake 3 Widescreen Problem"
date: 2007-04-09
forum: Ubuntu Gamers Arena
---

### Post by deevus on 2007-04-09
Hey there. I finally got my widescreen monitor working (1440x900) as well as my other LCD (1280x1024) in TwinView. 

I installed Quake 3 and am having troubles with the widescreen resolutions. I set them up using the r_ commands as in Windows, but when I boot it up, it is as if the screen is 2 inchs too far down, leaving a huge black bar at the top of my screen. The game is in the right resolution, Its just that the HUD is cut off.

Any ideas?

Thanks.

---

### Post by deevus on 2007-04-13
Any help would be appreciated, thanks! Btw, I am using Feisty Fawn.

---

### Post by Perfect Storm on 2007-04-13
You might try our Ubuntu Game Forum for such support. I don't have twinviews (god I wish I had) or Quake 3.

---

### Post by deevus on 2007-04-13
Oh just to clarify, I don;t want to play Quake 3 with dual monitors. I only want it to use one of them (the widescreen one), lol.

I think I know what the issue is.. Since the height of the 5:4 is 1024, and the widescreen is 900, theres over 100 pixels below where the taskbar is. This is assuming the total resolution would be considered as 2720x1024, which would leave the 124 x 1440 that I can't see blow the taskbar. Lol...confuses myself even to read that. 

Okay, considering that! Quake3 must be aligned bottom left of my screen, causing the problem. Is there a way to make it align to the top left?

---

### Post by Perfect Storm on 2007-04-13
Is it only a Quake 3 problem?

If so you might want to to quake 3 config file (it should be in something like ~/.quake3)

---

### Post by deevus on 2007-04-13
No idea dude. Its the only game I've tried since upgrading to Feisty, and beforehand, I didn't have TwinView working. I doubt there will be an option in the config. It might have something to do with how TwinView deals with fullscreen applications.

---

### Post by Perfect Storm on 2007-04-13
Have been reading a bit up on the twin issue. As I understand it you have to add **Option "TwinViewOrientation" "Clone"** in your xorg.conf to get the thing you wanted.

There should be a readme for nvidia which might be helpful in /usr/share/doc/ on your system.

---

