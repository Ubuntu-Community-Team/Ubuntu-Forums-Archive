---
title: "Issues with scroll wheel..."
date: 2012-02-07
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by dnewkirk on 2012-02-07
Hi everyone,
     I was curious if others are having issues using the scroll wheel on their mouse in Precise. I currently have a fair bit of issues with scrolling, where the webpage, document, etc. bounces back up partway through scrolling. It is getting pretty annoying. I looked for bug reports that match this, and haven't found any. I had also tried to file one a few days back, but had such problems getting a connection to launchpad that I wasn't able to go all the way through the process. Any thoughts? I've not had this issue on windows or 10.04 on the same machine, so I'm guessing it's not a hardware issue...

---

### Post by MacUntu on 2012-02-08
I'm experiencing the same, whenever I use the middle-click (using the Trackpoint key, simulated on the Trackpad, or simply using a mouse). Guess this should be reported against X?

---

### Post by dino99 on 2012-02-08
Nothing broken here with nvidia + gnome-classic on i386

---

### Post by dnewkirk on 2012-02-08
Bug Filed: [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/928930](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/928930)

---

### Post by ronacc on 2012-02-08
just for info I am not seeing this on my precise amd64 sys with G-S and the nvidia-current driver .

---

### Post by Sworddragon on 2012-02-08
I have posted something on the bug report:

> I can reproduce this bug on Virtual Box with a 32 bit and 64 bit installation. If I'm scrolling in lxterminal while the mouse is moving the scrollbar is jumping randomly. If the mouse is not moving while scrolling all is working fine. My host system is not affected from this bug (all 3 systems have the same configuration so this seems to trigger only on some hardware).

---

### Post by xyzzyman on 2012-02-08
Similiar to sworddragon, this has been happening on my Linux, XP & Win7 guests for about a month now. Even on 11.10 host, even after a fresh install.

---

### Post by kyleabaker on 2012-02-08
I'm seeing the same behavior. Added my +1 to the bug report.

---

### Post by xyzzyman on 2012-02-08
Why is this filed against xorg? It only seems to be happening inside virtualbox so it sounds like virtualbox isn't emulating properly.

---

### Post by MacUntu on 2012-02-09
Don't worry, triagers will figure it out. ;) I originally suggested X because it's happening for me on a real system, but my bug seems to be something different, because I need to click to make it jump upwards (though it started around the same time as for the bug reporter).

---

### Post by ubername on 2012-02-11
Same here, added +1 to bug report

---

