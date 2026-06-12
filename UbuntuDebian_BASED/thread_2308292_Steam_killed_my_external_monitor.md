---
title: "Steam killed my external monitor"
date: 2016-01-01
forum: Ubuntu/Debian BASED
---

### Post by p.callan on 2016-01-01
Got a brand new installation of Freya 3.2 (Ubuntu 14.04) and Steam on an Asus X550LD. Have been using the external monitor (VGA, 1920x1080) for some desktop use just fine. Tried to run a Steam game on this monitor, and it looked all messed up, part of the game outside the edges of the monitor etc. Turned off the external monitor in system settings and decided to play on my laptop's screen. Worked fine. After playing I went back to system settings to re-enable my external monitor but now it doesn't work!

When I click "Use this monitor" the button jumps back to Off, but the resolution field gets filled in correctly (1920x1080). 

How do I re-enable my monitor for desktop use? And how do I toggle this in the future?

---

### Post by p.callan on 2016-01-01
I solved my own problem after some angst:
In terminal:

**xrandr --auto**

This enabled the external monitor but the screens were mirrored. Went into system settings and there was only one monitor shown. After a second or two both screens appeared.
Turned off "mirror display".
Placed the screens as I wanted them.
Apply.

---

