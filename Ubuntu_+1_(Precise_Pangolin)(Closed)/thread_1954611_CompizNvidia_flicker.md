---
title: "Compiz/Nvidia flicker"
date: 2012-04-08
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ray field on 2012-04-08
I'm using the Nvidia driver version 295.33 according to the Nvidia X Server settings tool with a GeForce 8400GS and consistently get a flicker when I spin the Compiz cube -- it sort of looks like a refresh of the previous screen. any fix for this in either CCSM or Nvidia settings?

---

### Post by dino99 on 2012-04-08
have you used the available tools to look at your Graphics settings ? the mesa-utils package has a tool called glxinfo that will pull up info about your 3D.. ( run as non-root user on the PC in question, in a shell while X is running )

glxinfo | grep rendering

Direct Rendering should be YES

[http://wiki.linuxquestions.org/wiki/OpenGL](http://wiki.linuxquestions.org/wiki/OpenGL)

run: compiz-check

---

### Post by mc4man on 2012-04-08
That is a 6+ month old issue that now has been lumped into an expo flicker bug & finally shows _some_ signs of progress
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/862430](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/862430)

There is nothing you can do other than wait unless you want to rebuild the cube plugin using a hack posted in this subforum
[http://ubuntuforums.org/showthread.php?t=1938942](http://ubuntuforums.org/showthread.php?t=1938942)

---

### Post by ray field on 2012-04-08
I can wait. glad it isn't just me.

---

