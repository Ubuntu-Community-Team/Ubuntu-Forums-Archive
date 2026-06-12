---
title: "Any way to scale wine window with low-reoslution game?"
date: 2009-05-04
forum: Wine
---

### Post by yesint on 2009-05-04
Dear All,
I'm running an old game (Heroes of Might and Magic 3) under wine. It has fixed 800x600 resolution. The problem is that it hangs very often in full screen mode. In desktop emulation mode it work fine, but the 800x600 window is too small for my 1600x1200 screen. Is there any way to scale the window (tell wine that the virtual screen is 800x600 but physical window is larger)?

---

### Post by kkkkdddd on 2009-05-04
I am not sure, but try:

-run winecfg
-go to Graphics 
-tick a checkbox "emulate virtual desktop"
-set resolution to 800x600
-press ok

---

### Post by yesint on 2009-05-04
> **kkkkdddd said:**
> I am not sure, but try:

-run winecfg
-go to Graphics 
-tick a checkbox "emulate virtual desktop"
-set resolution to 800x600
-press ok

So what? This will show 800x600 window. I need to **scale** it as I wrote.

---

### Post by Sempfinger on 2010-07-16
Did you manage to solve this problem yet?

I ran into it yesterday as I wanted to play Diablo 2.

How can we scale low-res 4:3 games for hi-res widescreens?

Help is very much appreciated. 

Thanks!

---

### Post by cogadh on 2010-07-16
Short answer: you can't, at least not from within Wine. You'll have to rely on whatever scaling options your monitor or your video card drivers give you.

---

### Post by hikaricore on 2010-07-16
Look into the glide launcher for diablo, it supports higher resolutions and if I'm not mistaken also wide resolutions.

---

### Post by Sempfinger on 2010-07-20
@hikaricore
Thanks for the hint!

The glide wrapper was key.

For anyone who is interested:

I start Diablo 2 on a virtual desktop via the following script:

```
#! /bin/bash
# Run Diablo 2 on other X instance
export LAST_PWD=$PWD # Saves your last working path
cd /media/sda2/Program\ Files/Diablo2/ #Goes to your diablo 2 install path
xinit /usr/bin/wine "Game.exe" -- :1 vt9 # runs diablo 2 on a new X session at screen 1, on virtual terminal 9.
cd $LAST_PWD # On diablo exit, returns to your last working path.
exit 0

```

Glide wrapper is version 1.4b by Sven Labusch.

Settings: Desktop resolution
Renderer: Bilinear filtering

---

### Post by Atagad on 2010-07-25
i dont know if this would help, but i had that problem with diablo 2, all i did was turn off the virtual desk top and load the ALSA drivers for the audio; its works perfectly

---

