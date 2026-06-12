---
title: "Update broken multiple monitors"
date: 2014-11-25
forum: Virtualisation
---

### Post by Dr._B on 2014-11-25
I have been running a Win7 guest in virtualbox on a ubuntu host successfully for years. I recently upgraded virtualbox (and on the same day, the most recent linux kernal was also updated) and one and/or the other broke virtualbox.

My setup is a dual-monitor system, running off of an NVIDIA GF108 video card. I have a total of 6 virtual desktops, with my Win7 VM given one of the virtual desktops to itself. Previously I was able to run WIn7 in full-screen mode and it would fill both monitors perfectly (obviously, taking up the entire virtual desktop). After this "upgrade" the VM fills the left monitor properly, but the right monitor incorrectly. Now, the right-side of the VM screen is half on my right monitor, and the other half "spills" onto the next virtual desktop. You can see this in the attached image as the large black gap in the wallpaper.

Previously I was running the proprietary NVIDIA binary drive 304.117; since this error cropped up I've tried the newer NVIDIA driver (331.38) as well as 
X.Org driver; despite reinstalling guest-additions each time, disabling the pop-up menu (which has caused different issues for other people) as well as rebooting both the guest and host after each driver change, this problem remains unchanged.

Does anyone know how I can fix this?

Thank you

[ATTACH=CONFIG]258194[/ATTACH]

Bryan

---

### Post by Dr._B on 2014-11-27
So the solution appears to be downgrading to the older virtualbox - fixed all that ails me, aside from loosing the network connection information. Its always nice when an "upgrade" breaks things..

Bryan

---

