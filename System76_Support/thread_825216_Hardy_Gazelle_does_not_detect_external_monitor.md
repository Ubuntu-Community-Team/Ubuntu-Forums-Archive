---
title: "Hardy Gazelle does not detect external monitor"
date: 2008-06-10
forum: System76 Support
---

### Post by smulloni on 2008-06-10
I have two system76 laptops, a gazelle and a darter, both up-to-date with Hardy.  The darter, when I stick an external monitor into it and reboot, detects the monitor straightaway and goes to town.  The gazelle refuses to see it.  gnome-display-properties doesn't help.  How can I troubleshoot?

Thanks!

---

### Post by smulloni on 2008-06-10
Sorry to respond to myself.  Some more information.  I found that FunctionxF3 does affect the situation.  Pressing it once causes the laptop screen to go blank and the external monitor (an Acer flat screen) to say "Input Not Supported".  Pressing it again causes them both to show up, but the Acer display is somewhat misaligned, evidently not adequately adjustable in the monitor itself, and not the ideal resolution.  Is it possible to do any better?  The Darter doesn't behave this way at all.

j

---

### Post by jeamer on 2008-06-10
If you have a nvidia card for your gazelle, get nvidia-settings from the repositories and set it up that way

I couldn't get mine to work on my pangolin with gnome-display, but nvidia-settings is very straightforward.

[http://ubuntuforums.org/showthread.php?t=784344&page=2](http://ubuntuforums.org/showthread.php?t=784344&page=2)

---

### Post by thomasaaron on 2008-06-11
Please specify which Gazelle model you have.

---

### Post by smulloni on 2008-06-11
> **thomasaaron said:**
> Please specify which Gazelle model you have.

Sorry not to have done that first.  It is a roughly two-year old Gazelle Value with Intel video; I'm not sure what model number.

lspci | grep Graphics
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

---

### Post by thomasaaron on 2008-06-12
Well, two things come to mind:

> Pressing it again causes them both to show up, but the Acer display is somewhat misaligned, evidently not adequately adjustable in the monitor itself, and not the ideal resolution.

1. Once you have a display on the monitor, can you go to System > Preferences > Screen Resolution and adjust the resolution to an acceptable configuration?

2. Got to System > Prefs > Main Menu. In this utility, under Applications > Other, select 'Screen and Graphics." Then close the utility.

Now go to Applications > Other > Screen and Graphics. Try configuring your monitor there.

---

### Post by nhsbgeek2011 on 2008-06-12
[http://s6.gladiatus.us/game/c.php?uid=42772](http://s6.gladiatus.us/game/c.php?uid=42772)

---

### Post by smulloni on 2008-06-12
> **thomasaaron said:**
> Well, two things come to mind:



1. Once you have a display on the monitor, can you go to System > Preferences > Screen Resolution and adjust the resolution to an acceptable configuration? 

Alas, that doesn't work for me.  It doesn't see the second monitor.

> **thomasaaron said:**
> 2. Got to System > Prefs > Main Menu. In this utility, under Applications > Other, select 'Screen and Graphics." Then close the utility.

Now go to Applications > Other > Screen and Graphics. Try configuring your monitor there.

That at least shows two screens, but unfortunately didn't solve the problem.  Although I didn't modify the default screen,  I succeeded in hosing xorg.conf that way so that the gdm login screen was some absurd resolution.  I restored it from a backup.  

My next step will be to edit xorg.conf manually and see where I get.  I'll report back should I get stuck!  Thanks Tom and jeamer.

---

