---
title: "gazu1 On battery, &quot;when critically low&quot; action doesn't work"
date: 2009-11-16
forum: System76 Support
---

### Post by jii on 2009-11-16
I have a Gazelle Ultra (gazu1) with Ubuntu 9.10 Karmic Koala 64 bit freshly installed (partitions were formatted to ext4, etc). My "When battery power is critically low" action (to suspend or hibernate) never happens. Instead, my laptop suddenly powers off in the middle of working.
It happens after a reboot, and it happens after several suspend/resume cycles. I booted up off a live disk, and it happens there too.

In Jaunty, the power manager never carried out any of the on battery actions. The power icon didn't even change. Now in Karmic, the icon changes most of the time. (Sometimes it still says "battery fully charged" and shows the power adapter icon even after I've unplugged it.) Some of the on battery options work. The display will go to sleep when inactive, for example. But the action to "don't lose all my work" always fails.

I have an updated system and the latest System76 driver installed 2.4.0.

---

### Post by 3Miro on 2009-11-16
There seems to be a bug affecting system 76 machines. Here is my input:

[http://ubuntuforums.org/showthread.php?t=1328735](http://ubuntuforums.org/showthread.php?t=1328735)

---

### Post by jii on 2009-11-16
Thanks 3Miro, for the info on how you recompiled your kernel. I won't be doing that for obvious and numerous reasons, but the info is helpful to have on this thread.

---

### Post by 3Miro on 2009-11-16
No problem. I am wouldn't do anything anyway until Tomas posts some comment tomorrow anyway. None of us should have to recompile the kernel to circumvent what is obviously a bug.

---

### Post by HotShotDJ on 2009-11-17
> **jii said:**
> I have a Gazelle Ultra (gazu1) with Ubuntu 9.10 Karmic Koala 64 bit freshly installed (partitions were formatted to ext4, etc). My "When battery power is critically low" action (to suspend or hibernate) never happens. Instead, my laptop suddenly powers off in the middle of working.A custom compiled kernel may or may not correct this problem.  On my PanP5, it does not.  There are bug reports filed in Launchpad (see:[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/444881](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/444881)) and I recommend that you create a launchpad account and chime in on that bug.

In the meantime, you can correct this behavior on your system with some simple edits to your gnome-power-management.

Open a terminal and type "gconf-editor" (without the quotes, of course.  You do not need to be root for this, so no sudo).  Now, find apps -> gnome-power-manager --> general.   You'll see keys and their values on the right side of the window.  Uncheck "use_time_for_policy"

Next, find apps --> gnome-power-manager --> thresholds and set "percentage_action", "percentage_critical", and "percentage low" to appropriate values.  I recommend 5, 6, and 10 respectively, but you can set them higher or lower as you see fit (although I certainly advise against using values that are lower than I have recommended.  The default values are way too low and can damage your battery).

After doing this, your system will use percentage of power left rather than time and should perform the actions you set properly. (Commentary: in my opinion, this should be the way that gnome behaves by default.  Even under the best of circumstances, the "time" perimeter is rarely accurate.  Also, since discharge rates become non-linear at some point below 10%, it is vary dangerous to have critical set below the 5% mark.)

---

### Post by 3Miro on 2009-11-17
If the kernel recompilation doesn't help Panp5, then things are really bad. I will whine about this bug.

There are two issues with your solution:
1. While it will make the system operational, the AC adapter state would still be misread. Thus the system with low battery will not hit performance mode even after the adapter is in.
2. This will not work for KDE, however, KDE has the manual setting made pretty easy.

I should also say that your way is still better than downloading a kernel from a random source.

BtW I am not sure if we are talking about the same bug here. The tread talks about measuring time (which KDE doesn't do for me even with the recompiled kernel), my problem was that it wasn't detecting the AC adapter.

---

### Post by thomasaaron on 2009-11-17
I think it is pretty much the same thing as this...

[http://ubuntuforums.org/showthread.php?t=1218639&highlight=gazelle+power+management](http://ubuntuforums.org/showthread.php?t=1218639&highlight=gazelle+power+management)

We had heard reports of it being fixed in Karmic, and it looks like they might have made some progress, but evidently not enough.

Please file a bug report at...

[http://launchpad.net/system76](http://launchpad.net/system76)

This one is going to go beyond an easy fix on the forums.

---

### Post by HotShotDJ on 2009-11-17
> **3Miro said:**
> There are two issues with your solution:
1. While it will make the system operational, the AC adapter state would still be misread. Thus the system with low battery will not hit performance mode even after the adapter is in.
2. This will not work for KDE, however, KDE has the manual setting made pretty easy.The fix I mentioned is not for Kubuntu or KDE, nor is it a fix for problems with AC power detection.  It is an Ubuntu/Gnome fix for the OP's problem.

---

### Post by jii on 2009-12-02
HotShotDJ, I dunno what to say. I love you? You are the awesome? Maybe "u r teh awesome"? I just tested it and it worked perfectly, with the addition that I had to restart for the gconf-editor changes to take effect (probably I only needed to logout/login). You completely solved the problem I reported in this thread, and now over 95% of my power-manager woes are fixed. I often leave my laptop open, whether to play klove (internet radio), or leave it compiling some verilog project, and then I'm always pissed when suddenly without warning it runs out of power and shuts down without suspending. Now with your fix it will actually suspend, and I can't exaggerate on how this benefits me.

It blows my mind that through all the forum posts everywhere that I've participated in and read through, I never saw anyone offer this simple solution. THANK you for posting.

---

### Post by HotShotDJ on 2009-12-02
> **jii said:**
> HotShotDJ, I dunno what to say. I love you?:redface:

---

