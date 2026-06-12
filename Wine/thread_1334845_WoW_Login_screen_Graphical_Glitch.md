---
title: "WoW Login screen Graphical Glitch"
date: 2009-11-22
forum: Wine
---

### Post by psphacker22 on 2009-11-22
when i launch my wow in wine i see the cinematic and i see the EULA come up and the background is all pink and purple. it flashes for a few seconds and then WoW just freezes and i have to alt tab out and end th process. i suspect this may be a shader problem as the chain also glitches. any tips? thanks.

---

### Post by Xog on 2009-11-22
what video card do you have
what driver are you using
is it the latest driver
what version of wine do you have

---

### Post by psphacker22 on 2009-11-22
im using an ibm thinkpad with a ATI Radeon Mobility 9000 / 32 Meg. 
havent installed any drivers for it, just built in. 
wine 1.1.32

---

### Post by joeelmex on 2009-11-23
Video driver issue in my opinion.

---

### Post by psphacker22 on 2009-11-23
how would i go about fixing the issue?

---

### Post by Alatar1 on 2009-11-24
Try running the game in opengl mode..
browse yourself on over to 
/home/yourusername/.wine/drive_c/Program Files/World of Warcraft/WTF

open the config.wtf to edit it (any text editor will do, gedit is the ubuntu default) and add this to it, with its own line EXACTLY as it is here... 
```
SET gxApi "opengl"
```
you should see other SET options in there, and if you know anything about code you should get how to place it in.

If that doesn't work, try looking in to the graphic drivers.
System> administration> hardware drivers. and see if you're using your video cards restricted drivers.

---

### Post by psphacker22 on 2009-12-01
well now it wont launch at all

---

