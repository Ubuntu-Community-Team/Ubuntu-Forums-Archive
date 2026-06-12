---
title: "Low FPS on CSS even with good specs"
date: 2009-04-01
forum: Wine
---

### Post by QuickNinja on 2009-04-01
Hey everyone, 

I'm using the latest version of WINE, have the 177.something Nvidia driver,3.2 GHz Celeron D processor, 533 MHz FSB, 1.5 GBs of DDR RAM, Nvidia XLR8 9800 GT with 1 GB of DDR3 RAM.  

I'm only able to get less than 30 fps in CSS with all the graphic options set to low!  In game it has even lower fps.  Is my cpu not good enough or something because I feel like I should be able to run the game smoothly with no problems?  Oh and I have fiddled with WINE to try to find the best configuration but less than 30 fps is about as much as I can get.

---

### Post by Brynster on 2009-04-02
what resolution are you running at?

The reason i ask is on my install i have terrible frame rate issues when i run on any other that 1024*768 or 1152*854. Changing detail options also helps a little but no as much as the resolution.

---

### Post by QuickNinja on 2009-04-02
The resolution that I use is the default resolution 1024*768

---

### Post by asdfoo on 2009-04-04
> **QuickNinja said:**
> The resolution that I use is the default resolution 1024*768

177.x is really old.

Upgrade to 180.44, make sure you're using Wine 1.1.18, in regedit, goto HKLM, Software, Wine

make a new Key called Direct3D, under which put an entry OffscreenRenderingMode, set the value to fbo

You should get in excess of 70fps.

---

### Post by QuickNinja on 2009-04-06
thanks for the info about adding in the key to the regedit file.  It does seem to make a difference in-game but when I do the video stress test I can only get about 29.xx fps.  That's still kind of pissing me off.

---

### Post by asdfoo on 2009-04-06
> **QuickNinja said:**
> thanks for the info about adding in the key to the regedit file.  It does seem to make a difference in-game but when I do the video stress test I can only get about 29.xx fps.  That's still kind of pissing me off.

did you upgrade to 180.44 and 1.1.18?

---

### Post by QuickNinja on 2009-04-06
That's what I did the test on with 180.xx, 1.1.18 WINE, OpenGL settings to high performance, and overwrite app setings with all setings turned to the minimum.

---

### Post by asdfoo on 2009-04-06
> **QuickNinja said:**
> That's what I did the test on with 180.xx, 1.1.18 WINE, OpenGL settings to high performance, and overwrite app setings with all setings turned to the minimum.

yeah ok, the video stress test is lower than the ingame perf.

I believe the issue is being investigated by people in the know.  Hopefully they can come up with a good fix to improve performance further.

---

### Post by QuickNinja on 2009-04-06
> **asdfoo said:**
> yeah ok, the video stress test is lower than the ingame perf.

I believe the issue is being investigated by people in the know.  Hopefully they can come up with a good fix to improve performance further.

Oh alright then, I'll see what else I can find to further improve CSS performance.  Thanks for the help.

---

### Post by Brynster on 2009-04-07
another option is to force directx into an older version it currently defaults to to 9.0c i think
to do this add one od these to the launcher options (only use 1 )

-dxlevel 80 (for directx 8.0)
-dxlevel 81 (for directx 8.1)
-dxlevel 70 (for directx 7.0)

Dxlevel 70 will give you a huge perfomance boost but it look the ugliest as directx 7.0 simply doesn't support some of the high level rendering features and lighting effects used in source based games.

I generally use -dxlevel 81

---

### Post by QuickNinja on 2009-04-10
> **Brynster said:**
> another option is to force directx into an older version it currently defaults to to 9.0c i think
to do this add one od these to the launcher options (only use 1 )

-dxlevel 80 (for directx 8.0)
-dxlevel 81 (for directx 8.1)
-dxlevel 70 (for directx 7.0)

Dxlevel 70 will give you a huge perfomance boost but it look the ugliest as directx 7.0 simply doesn't support some of the high level rendering features and lighting effects used in source based games.

I generally use -dxlevel 81


Yeah I started using the -dxlevel70 settings just to see how much I can get squeezed out.  I still get some pretty crappy fps though slightly below 30 fps :x  What the hell am I doing wrong now?  Is my system too crappy or something?

---

