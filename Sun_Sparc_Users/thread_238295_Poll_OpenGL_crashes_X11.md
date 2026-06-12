---
title: "Poll: OpenGL crashes X11"
date: 2006-08-17
forum: Sun Sparc Users
---

### Post by netztier on 2006-08-17
Hi all

This morning i did a successful install of xubuntu-desktop on a fresh install of ubuntu-server my low-spec Ultra2 (2x 167Mhz UltraSPARC I, 128MByte RAM, 2x9Gig disks).

It has an UPA Creator video card that runs with the **sunffb** driver.

Whenever I run an OpenGL app (such as a xscreensaver hack), X.org crashes instantly. The same thing happens on my Ultra60s with Creator3D cards (also with sunffb), but with ubuntu-desktop instead of xubuntu.

I had observed this before during the beta times of Dapper Drake and had hoped it would go away.

Can anyone share these observations?

kind regards

Marc

---

### Post by recupero on 2006-09-06
this happens to me, when the random screensaver starts...
Some screensavers work good, other make X crash, just go back to login, so I chose a screensaver which is good (I guess that's flipflop).
But the same problem I also have with my AMD which can just run almost the same subset of screensavers as the ultra60.
I should disable the 12cm-wide fan in the ultra to make it sound friendly...

Another thing: I recently learned how to make X modular, and switching to xorg from xfree86, but still I should learn more about OpenGL.
Where to start and where to end this journey?

Thanks to all.

---

### Post by netztier on 2007-04-01
> **netztier said:**
> Hi all

This morning i did a successful install of xubuntu-desktop on a fresh install of ubuntu-server my low-spec Ultra2 (2x 167Mhz UltraSPARC I, 128MByte RAM, 2x9Gig disks).

It has an UPA Creator video card that runs with the **sunffb** driver.

Whenever I run an OpenGL app (such as a xscreensaver hack), X.org crashes instantly. The same thing happens on my Ultra60s with Creator3D cards (also with sunffb), but with ubuntu-desktop instead of xubuntu.

I had observed this before during the beta times of Dapper Drake and had hoped it would go away.




As it turned out, I had to wait a little longer. I Installed [Herd 5]("http://cdimages.ubuntu.com/releases/7.04/herd-5/") of Ubuntu 7.04 Feisty Fawn yesterday on my Ultra 60 (the one with the 2x Creator3D) and added ubuntu-desktop to it. I didn't even need to edit **/etc/X11/xorg.conf** manually (!).

All OpenGL apps from the screensaver collection seem to work. Same goes for Blender, the rendering application. :-)

This is great. Other problems are there (HAL is not running properly), but hey, this is still beta...

best regards

Marc

---

