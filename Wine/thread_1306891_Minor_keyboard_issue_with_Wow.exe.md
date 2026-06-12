---
title: "Minor keyboard issue with Wow.exe"
date: 2009-10-30
forum: Wine
---

### Post by the_darkside_986 on 2009-10-30
World of Warcraft runs amazingly well in Wine and Ubuntu 9.04 (I'm using the default Wine version) but when I run it in fullscreen mode, the keyboard doesn't work at all; I have to run it in windowed mode. Anyone have this issue and know what to set in winecfg or config.wtf to fix it? Or should I upgrade to the latest Wine on their official website?

---

### Post by Dark_Stang on 2009-10-30
I had a lot of odd quirks with WoW on my laptop until I did some tweaking in the graphics settings. Here is what I tweaked...
Reduce input lag - Checked
Tripple Buffering - Checked
Windowed Mode - Checked
Maximized - Checked
Also, to launch wow I am using the opengl flag as follows...
```
env WINEPREFIX="/home/darkstang/.wine" wine "C:\Program Files\World of Warcraft\Launcher.exe" -opengl
```
Doing those last 3 things seem to have helped my simple onboard video card handle WoW so much better.

---

