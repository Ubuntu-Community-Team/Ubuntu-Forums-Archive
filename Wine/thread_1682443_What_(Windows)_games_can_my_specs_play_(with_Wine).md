---
title: "What (Windows) games can my specs play (with Wine)?"
date: 2011-02-05
forum: Wine
---

### Post by 3602 on 2011-02-05
The specs are pretty much there in the sig. The CPU is P540 with 2.4GHz, and while it has an advertised 2MB of L2 cache, *sysinfo* in Ubuntu only shows 1MB (1024KB). I also do not know the RAM speed, but it is 2DIMM, most likely single-channel 1066 or 1333.
Yes the graphics is integrated. I have *fglrx* running correctly, here's what I tested as of now:
* SuperTuxKart, Extreme TuxRacer, TORCS: glorious 40+ FPS at maximum resolution (1600x900).
* WarZone 2100: Unknown FPS but as smooth as it gets. Correct animations, shadows, particles, etc. Correct screen actions (zoom, angle, spin). Played at 1280x720 fullscreen because 1920x1080 "spills out" of the screen.
* AstroMenace: I cannot get it to run fullscreen so it is 1024x768 windowed. Trilinear filtering, 6x anisotropy and 8x anti-aliasing. As smooth as it gets, correct animations and particles.
* Scorched 3D: Fullscreen, everything maxed out, as smooth as it gets. Didn't really get a shot off, will need to figure out the whole 3D ballistics calculations.
* Those Funny Fungaloids: Fullscreen, everything maxed out, as smooth as it gets.
* vDrift: Unplayable at fullscreen. Would severely lag with bloom drawing and shadows and the like, still lags even with them disabled.
Now all the above are either Linux or cross-platform games. The only Windows games I have under Wine as of right now is DemonStar, a 2D vertical scroller.
I have C&C: Generals disk (actually First Decade) but that thing lags on a GMA400 (945GM) under WinXP. I don't really play shooter or fast-action games unless you can control everything with the keyboard, because have you ever tried playing FPS with a touchpad?
So dear fellow users, please suggest some games that I can play with this computer. I'd prefer (modern) strategy or anything that can be majorly controlled with the keyboard. Although if Call on Duty (One, not Two, not Modern Warfare) can run I'd be happy too. Just need to get used to a mouse.
Thank you very much!

---

### Post by 3602 on 2011-02-27
Bump.

---

### Post by dino99 on 2011-02-27
some free ones:

[http://absolutist.com/linux/](http://absolutist.com/linux/)
[http://www.linuxlinks.com/article/20080510052539217/Games.html](http://www.linuxlinks.com/article/20080510052539217/Games.html)

the better test is yours :)

and you can search here:
[http://ubuntuforums.org/forumdisplay.php?f=93](http://ubuntuforums.org/forumdisplay.php?f=93)

---

### Post by cogadh on 2011-02-27
As long as your system exceeds the minimum requirements of the game, it should have little difficulty playing the game on Linux via Wine. You check which games are compatible with Wine here:

[http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by Tweak42 on 2011-03-02
Check out Dan Kegel's latest winetricks alpha.  It does point-click wine install for a good number of demo versions of popular windows games.

[http://code.google.com/p/winetricks/](http://code.google.com/p/winetricks/)

---

