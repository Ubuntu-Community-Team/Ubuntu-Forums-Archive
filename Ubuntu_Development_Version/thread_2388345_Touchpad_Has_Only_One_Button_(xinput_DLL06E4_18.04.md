---
title: "Touchpad Has Only One Button (xinput DLL06E4 18.04 Beta)"
date: 2018-03-31
forum: Ubuntu Development Version
---

### Post by micahgalizia on 2018-03-31
Hello,

I'm trying the new Bionic Beaver and my XPS 9550 touchpad is acting like it has a single button (eg: all clicks are left clicks). I can two-finger tap for a right click but the right button behaves like a left button.

Xinput shows:

&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; DLL06E4:01 06CB:7A13 Touchpad           	id=12	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=16	[slave  pointer  (2)]

I'm inferring the pointer is DLL06E4 because disabling it disables all mouse events.

Anyway, if anyone knows how to fix it I'd appreciate the tip.

---

### Post by wildmanne39 on 2018-03-31
Thread moved to **Ubuntu Development Version, a more appropriate forum**.

I think this will fix it, it does require a log out.

[https://ubuntuforums.org/showthread.php?t=2388106](https://ubuntuforums.org/showthread.php?t=2388106)

---

### Post by micahgalizia on 2018-04-01
Thanks! That sorted it.

---

