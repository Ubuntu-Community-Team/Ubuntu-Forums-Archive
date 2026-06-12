---
title: "Avidemux CPU throttle prioritizing"
date: 2008-10-06
forum: Ubuntu Studio
---

### Post by Firestone on 2008-10-06
I use Avidemux(2) to cut and convert raw mpeg2 recordings to x264 avi files. Until recently I used an Intel P4 3Ghz(no auto throttling) for this, on which the program used most of the CPU power and completed it in about an hour. Since two months however, I've upgraded to an Athlon 64 6000+(3Ghz dual core). On idle the CPU throttles back to 1Ghz.
The problem is that, when I start the converting process, the CPU only stays at full throttle for about a minute. After this, it goes back to running at 1Ghz, which causes my completion time to jump up from 30 to 80 minutes. 
I've tried everything I can think of; running with *nice -n0*, giving it high priority in sys monitor, overriding Avidemux setting for CPU and Threading. I even tried running it as root to see if it made a difference.

Does anyone have an idea?

---

### Post by toaste on 2008-11-10
Found this thread after looking for a better solution myself:

There are a few ways of dealing with this.  One is to use the cpufreq applet ("CPU Frequency Scaling Monitor" in the list.  Why Gnome has to have two names for everything I will never understand.)  You'll need to reconfigure it to run as root so it can set the cpu frequency:

sudo dpkg-reconfigure gnome-applets

Full disclosure is that it's a "bad idea" to have suid-root applications or allow ordinary users to change the system cpu frequency.  But on a single user laptop or desktop it's an awfully handy feature.

Now left clicking the applet brings up a menu where you can set the frequency manually.  I just set it to performance until I'm done transcoding.  You might want to add one applet per cpu (and set the core it controls in properties) if you can set the speed of cores individually -- not too up on AMD lately.

EDIT: no, I never did find how to make cpufreq's ondemand governor account for nice'd processes.

You may be able to get the right behavior by running "powernowd -n" (as root) and having it take over cpu scaling from the kernel.

---

