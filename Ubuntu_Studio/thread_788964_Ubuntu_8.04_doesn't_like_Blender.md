---
title: "Ubuntu 8.04 doesn't like Blender?"
date: 2008-05-10
forum: Ubuntu Studio
---

### Post by gohatto on 2008-05-10
Hi,

I've run into some serious problems with running Blender on Ubuntu 8.04...

Sometimes when I use tools like extrude, scale, crease, etc. - every option where you have some vertices selected and you try to move the MOUSE (mouse seems to be crucial) Blender hangs for few seconds. In the matter of fact whole system just freezes (no sound, no System monitor running).

After those few seconds everything get back to normal (Blender doesn't quit, no errors reported).

Looking at the past chart of System Monitor the CPU usage was about 100% (2 cores sweating ;) )

No informations in console when I run Blender from there.

It only occurs when I move mouse (ex. when I want to crease the edges typing the value using keyboard the error doesn't occurs).

I tried to reinstall the whole system from the scratch but nothing helped.

My uname -a:
**Linux piotr-desktop 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux**

It's Intel C2D E6750, 2 GB ram with nVidia GeForce 8600 GE.

I'm not running Compiz; the direct rendering is turned on.
The Xorg.conf is created default by the Ubuntu.

Anyone knows what could to be the reason of this strange behavior? :|

Edit: The problem occurs also under KDE.

---

### Post by Gasten on 2008-05-28
I got the exact same problem! I do also have 2 cores (core 2 duo) and that very same graphics-card. I am using effects, and I got gnome running.

Reported a bug here: [https://bugs.launchpad.net/ubuntu/+source/blender/+bug/235521](https://bugs.launchpad.net/ubuntu/+source/blender/+bug/235521)

---

### Post by joegiampaoli on 2008-05-30
Are you using blender from repos? I advise you to download the one directly from blender.org

---

### Post by stinger30au on 2008-05-30
im using Ultimate edition 1.8 

[http://ultimateedition.info/](http://ultimateedition.info/)

it has blender built in to it and works fine

---

### Post by joegiampaoli on 2008-05-30
well it could be an xorg.conf problem with video configuration, a lot of us are having problems with this new xorg but I always download the latest blender from the site and it's working well for me, just give it a shot....

---

### Post by gohatto on 2008-06-24
It was fine for some time but right now it's back again :/

It's really a pain to use Blender in such circumstances.

I tried Blender from official site. Nothing changed.
I am using my own compiled version from Blender SVN.

@Gasten: did you work that out?

---

### Post by Samhain13 on 2008-06-25
I'm using Blender from the repos and it works fine. My uname is:
Linux memphis **2.6.24-19-rt** #1 SMP PREEMPT RT Wed Jun 18 16:35:41 UTC 2008 i686 GNU/Linux

I hope that information is useful.

---

