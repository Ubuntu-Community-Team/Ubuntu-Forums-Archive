---
title: "Ubuntu 9.10 Boots in 10 Seconds"
date: 2009-12-12
forum: The Cafe
---

### Post by Regeneration on 2009-12-12
Thanks to Intel's X25-M SSD, the latest version of Ubuntu 64-bit boots up in ten seconds. Well done! ;)

[**Here is the link to the video**]("http://www.ngohq.com/news/16945-ubuntu-9-10-boots-in-10-seconds.html").

---

### Post by NCLI on 2009-12-13
That's great, but you should post stuff like this in the [Community Café]("http://ubuntuforums.org/forumdisplay.php?f=11") ;)

---

### Post by overdrank on 2009-12-13
Moved to The Community Cafe

---

### Post by earthpigg on 2009-12-13
indeed, <3 my ssd.

---

### Post by Giant Speck on 2009-12-13
Boot speed is *the most important* feature of Ubuntu.

---

### Post by earthpigg on 2009-12-13
> **Giant Speck said:**
> Boot speed is *the most important* feature of Ubuntu.

i'm glad we have that settled, then. :lolflag:

---

### Post by earthpigg on 2009-12-13
also, the most important feature of Giant Speck is the nifty looking ubuntu/windows logo for his avatar.

he has recently experienced a regression in this area.

---

### Post by macmaster on 2009-12-13
Ubuntu shuts down faster than boots. Ubuntu shuts down in about 3 seconds with a computer with 2GB RAM. Startup is a lot faster if you do not multi boot.

---

### Post by Xbehave on 2009-12-13
dammit with my HDD it takes 15seconds just to get to xorg (kde hangs for an extra 10 seconds too so all in all boot time is ~50s including amarok & kmail)

---

### Post by chriswyatt on 2009-12-13
If boot time is the most important feature then DOS should be right down your street.

---

### Post by Xbehave on 2009-12-13
> **chriswyatt said:**
> If boot time is the most important feature then DOS should be right down your street.
Dos can't boot to a gui in 15 seconds on a HDD (If you don't want a GUI linux can boot in <10s to cli again without an ssd) to beet linux on boot time you have to look at something like qnx and even then its hard

---

### Post by pveurshout on 2009-12-28
Does someone know what the difference in boot speed is if you install Ubuntu on either the beginning or the end of the disk? Currently I have Karmic installed at the very end of my disk (except for swap and a 10 GB HP recovery partition that's still there) and am considering to completely repartition my drive to move Ubuntu to a faster place, but as one can imagine I'm not going through this hell of a process if it hardly makes any difference :)

---

### Post by Bölvaður on 2009-12-28
> **pveurshout said:**
> Does someone know what the difference in boot speed is if you install Ubuntu on either the beginning or the end of the disk? Currently I have Karmic installed at the very end of my disk (except for swap and a 10 GB HP recovery partition that's still there) and am considering to completely repartition my drive to move Ubuntu to a faster place, but as one can imagine I'm not going through this hell of a process if it hardly makes any difference :)

For boot speed you can do something different than speeding how quickly you seek the data.
Rather minimize the data you are fetching.

If you are on a desktop computer disable all the laptop features and hardware testing. I managed to get ubuntu 9.10 down to 15 - 20 seconds on a normal hdd. Even 20 seconds is not bad for fully fletched GNOME desktop.

System &#8594; Preferences &#8594; Startup Applications
And disable pretty much everything except:

Keyring Daemon
Settings Daemon
PolicyKit Aythentication Agent
Seahorse Daemon

you might want to keep also some of the others.. like Network Manager and Print Queue Applet. Make sure you are ok with disabling what is on the list, because even though I dont use it... it is probable that you do.


Moving Ubuntu at front will be peanuts compared to what you can lose by cutting off fat.

---

