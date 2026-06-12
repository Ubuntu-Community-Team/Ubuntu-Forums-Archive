---
title: "Unique display/screen issue lemu1|9.10"
date: 2010-04-07
forum: System76 Support
---

### Post by chromatic.lotus on 2010-04-07
So I've delved the forums and can't find a suitable solution.

Initial Description of Issue:
My issue is quite unique, and hard to explain, so bear with me.
Definitions:
    Screen: the physical screen on my computer
    Display: what my computer is outputting
OK, simply put, my screen has 2 displays and unused space.
There is a horizontal 'split' on my screen in which each half (top and bottom) contain duplicate copies of the display (2 desktops, 2 cursors, 2 everything).  In addition to that, the right 1/4 of the screen (split vertically) is blank
A visualization:
    my screen```

_________________________________
|display copy 1********|*blank**|
|**********************|********|
|**********************|********|
|----------------------|********|
|display copy 2********|********|
|**********************|********|
|**********************|********|
|----------------------|--------|

```My laptop:
Lemur Ultrathin (lemu1)
Ubuntu 9.10 (2.6.31-20-generic)

More Description:
I thought that this may have been an issue with my xorg.conf, so I ran 
```
sudo dpkg-reconfigure xserver-xorg
```(before doing so, I had a look through it and saw nothing suspicious)
where is the xorg.conf file that my system uses?  I ran a search and 4 popped up, looked through each.  Some said something about a touchscreen, so I assume I don't use it, but idk.

Also I reinstalled all Sys76 drivers using their preinstalled app (and performed 'restore')

reinstalled grub-pc

Note: this effects my laptop from power button to desktop (BIOS, grub, splash, etc)

So I'm at the end of my rope in the way of knowledge (started using ubuntu this past Oct)  Any ideas?  Need any more info?  Let me know.

~C.Lotus

---

### Post by chromatic.lotus on 2010-04-07
Additional information:

Under display properties, I noticed an interesting thing
The computer has the option of displaying at a lot of low res selections

This leads me to believe the computer thinks that the monitor (in its entirety) is what I described earlier as "display 1".  "display 2" is just a mirror image, so I guess if I can get Ubuntu to recognize the entire active area on my screen, I don't think I'll have any more issues.

---

### Post by Paul Stone on 2010-04-07
"Note: this effects my laptop from power button to desktop (BIOS, grub, splash, etc)"

Sounds like a h/w issue if it affects your BIOS screen.  Are you saying that if you go into BIOS setup, the screen has the same issue?

Did it use to work correctly?

---

### Post by chromatic.lotus on 2010-04-07
Yeah it used to work correctly, and there was a period of time when it jumped back and forth for a while (problem did not persist through reboot, but popped up randomly).  The laptop is brand new (Dec 09) and well taken care of (no drops, hits, etc).

Also yes the issue effects BIOS screen, and everything else.  When the screen is on, the displays are messed up. Period.

I haven't been running anything questionable, as this laptop is used solely for school work (C++ and Java related development) as well as Open Office (using eclipse for java and g++/nasm/gedit/terminals for C++).  Other than that, I run Dropbox, Opera, and Tomboy Notes on a regular basis; nothing that I feel could have produced the issue.

I don't remember having any recent updates when the problem became persistent.

---

### Post by thomasaaron on 2010-04-07
Paul is right. If it affects the BIOS screen, it is a hardware issue. Please contact me at support...at...system76...dot...com for further support.

---

