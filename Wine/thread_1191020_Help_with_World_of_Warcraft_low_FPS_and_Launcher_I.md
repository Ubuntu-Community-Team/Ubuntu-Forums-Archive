---
title: "Help with World of Warcraft low FPS and Launcher Issue"
date: 2009-06-18
forum: Wine
---

### Post by Dead_$partan on 2009-06-18
Hi,

I recently installed Ubuntu 9.04 and decided to give WoW a try, decided to download the web based installed and get it on the system that way, took hours but installed and patched all the way up to 3.1.2 but I have an issue with the video performance.

My FPS never goes above 25 but mostly sits around 18.  I followed some instructions from some websites to help improve this but nothing seems to help.  I have tried the following.

Added the following to config.wtf
```

SET gxApi "opengl" 
SET ffxDeath "0"
SET ffxGlow "0"

```

Also tried creat5ing the registry value ```
GL_ARB_vertex_buffer_object

```
Have lowered the resolution to 800x600 and have tried vsync on and off(was on by default).

Refresh options only give me 69 and 70Hz which seems like an odd value and have also tried running the game with the -opengl switch from a terminal.

Oh and I am using nvidia drivers 180.44

Can anyone advise what else I can change?  Oh and latency has been 50ms so doesnt seem to be an issue.

Cheers

---

### Post by donkyhotay on 2009-06-18
This should really be posted in the [ ubuntu wine forum](http://ubuntuforums.org/forumdisplay.php?f=313), you will get more relevant responses there.

---

