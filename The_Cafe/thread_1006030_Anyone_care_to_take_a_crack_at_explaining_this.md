---
title: "Anyone care to take a crack at explaining this?"
date: 2008-12-08
forum: The Cafe
---

### Post by etnlIcarus on 2008-12-08
This is the second time this has happened over the years:

- Installed Ubuntu and used xorg-video-ati driver for my Radeon 9550:
-- Have 3D Acceleration for most applications.
-- No acceleration in WINE (OpenGL/Direct3D < 1fps).

- Installed fglrx video driver:
-- Have 3D Acceleration for most applications.
-- Have decent, comparable 3D acceleration in WINE.

- For one reason or another, removed fglrx driver and went back to xorg-video-ati:
-- Have 3D Acceleration for most applications.
-- 3D Acceleration in WINE remains stable.

Any clue why this happens? I usually only install fglrx when I want to fire up something like Tribes in WINE. First time this happened, I just figured it was a fluke but if there's some reason WINE isn't enabling 3D acceleration until it detects fglrx, at which point I can remove fglrx and not be negatively impacted by it's absence, is there a way of getting around having to install the binary-only fglrx driver in the first place?

FTR, I restored the xorg.conf I used previously to fglrx so there's no changes there. And glxinfo is telling me my glx vendor is SGI, my OpenGL vendor is DRI R300 Project and my OpenGL renderer is Mesa DRI R300 so fglrx hasn't left anything behind.

---

### Post by Trail on 2008-12-09
(sudo) lsmod | grep fglrx?

---

### Post by etnlIcarus on 2008-12-09
> **Trail said:**
> (sudo) lsmod | grep fglrx?

Nothing.

---

### Post by Trail on 2008-12-10
No idea :| And I assume you are getting a normal 3D acceleration performance in wine.

Try removing stuff with --purge if you haven't? Scan xorg/syslog/dmesg messages for remnants of fglrx or something. Or try asking upstream?

---

### Post by etnlIcarus on 2008-12-10
> **Trail said:**
> No idea :| And I assume you are getting a normal 3D acceleration performance in wine.

Try removing stuff with --purge if you haven't? Scan xorg/syslog/dmesg messages for remnants of fglrx or something. Or try asking upstream?

The --purge argument in apt is the same as "completely removing (including config files)", in synaptic, right?

If so, way ahead of you.

---

### Post by stephenchant@hotmail.com on 2009-05-25
> **etnlIcarus said:**
> This is the second time this has happened over the years:

- Installed Ubuntu and used xorg-video-ati driver for my Radeon 9550:
-- Have 3D Acceleration for most applications.
-- No acceleration in WINE (OpenGL/Direct3D < 1fps).

- Installed fglrx video driver:
-- Have 3D Acceleration for most applications.
-- Have decent, comparable 3D acceleration in WINE.

- For one reason or another, removed fglrx driver and went back to xorg-video-ati:
-- Have 3D Acceleration for most applications.
-- 3D Acceleration in WINE remains stable.

Any clue why this happens? I usually only install fglrx when I want to fire up something like Tribes in WINE. First time this happened, I just figured it was a fluke but if there's some reason WINE isn't enabling 3D acceleration until it detects fglrx, at which point I can remove fglrx and not be negatively impacted by it's absence, is there a way of getting around having to install the binary-only fglrx driver in the first place?

FTR, I restored the xorg.conf I used previously to fglrx so there's no changes there. And glxinfo is telling me my glx vendor is SGI, my OpenGL vendor is DRI R300 Project and my OpenGL renderer is Mesa DRI R300 so fglrx hasn't left anything behind.


Personally I would try hunting down a new driver and or video card.
Try going to the manufacturers web site see if they have released a linux driver, I have a msi nx8600gt oc and it works nicely with linux on my machine

---

### Post by CharmyBee on 2009-05-25
> **stephenchant@hotmail.com said:**
> I have a msi nx8600gt oc and it works nicely

Radeons aren't Geforces.

---

### Post by zekopeko on 2009-05-25
ok this might be long shot but...

what if when you install the ati driver wine doesn't register 3d?

purge wine and fglrx. install the ati driver and then install wine. dump wines registry in a file.
purge wine again, install fglrx, install wine, dump wine's registry.
look at the diff between wine-ati and wine-fglrx. probably along the lines of direct3d or 3d or something similar.

---

### Post by etnlIcarus on 2009-05-25
As I'm now using Jaunty and ATi no longer provide a working FGLRX driver for my card, I can't actually do that.

---

### Post by CharmyBee on 2009-05-25
I think Jaunty should have had an alternate 9.3 catalyst metapackage for fglrx for the older Radeon cards that just dropped support for every version after that. It's a shame that it doesn't.

---

### Post by etnlIcarus on 2009-05-25
> **CharmyBee said:**
> I think Jaunty should have had an alternate 9.3 catalyst metapackage for fglrx for the older Radeon cards that just dropped support for every version after that. It's a shame that it doesn't.

It doesn't matter if they had included the last working FGLRX driver for those cards; the current xserver isn't supported by those drivers.

---

