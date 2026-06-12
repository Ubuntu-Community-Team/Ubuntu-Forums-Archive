---
title: "Ubuntu Studio 13.04-beta2, yet another fail :("
date: 2013-04-15
forum: Ubuntu Studio
---

### Post by wkulecz on 2013-04-15
I've yet to have a Ubuntu Studio installation produce a usable system.  Yet another fail with 13.04-beta2, I've tried every LTS release and a few others.

I don't get it, same as always the installer gives me a nice 1920x1200 display but when it finishes and I boot the system its stuck is some crappy low-res mode.  Trying to install "better" drivers or reconfigure the X server quickly ends in a system that only boots to busybox :(

How can the installer get things right with my Nvidia card and the installation end up not even close?  Same system had no problems with Xubuntu 13.04-beta2, and then later installing the low-latency kernel.

---

### Post by wkulecz on 2013-04-15
I'm happy to say it looks like one of the 289 updates since Thursday seems to have fixed the issue.

I was reinstalling from the CD while posting my complaint.  When it finished, there it was in ugly 1280x1024 mode again.   I then let it install all the updates, and when rebooted I had glorious 1920x1200 display.

Nouveau still has visible glitches, so I'm not sure how useful it'll really be, but finally I can play with it a bit.  Oops, UbuntuStudio seems to be running Nvidia drivers now, version 304.88,  Maybe what I'm seeing as glitches are "effects" :) 

I'm sure Xubuntu installed Nouveau and it has coloured "mouse droppings" on background fills that disappear with a redraw. I'll have to try the Nvidia 304 drivers on it.

Still doesn't answer how the installer gets it right initially but was wrong on the installation!  Can make the "try before installing" deceptive, but I find telling someone to try a "live CD" to test out Linux is sure to leave a bad taste as live CD are painfully slow and unresponsive.  What does impress the yokels is when I boot a live CD and recover their data from a dead windows system.

---

### Post by wkulecz on 2013-04-27
Well after installing a ton of automatic updates I'm back to fail.  Just wasted a whole lot more time to get there with this version :(

System crashes back to login screen if I do much of anything :(

xfce4-session is in the crash reports I'm sending.

---

### Post by wkulecz on 2013-04-29
Going into "Settings"->"Session and Startup" choosing "Advanced" tab and unchecking "Launch GNOME services on startup  so far seems to have stopped the crashing back to the login screen.

Why are these GNOME and KDE service options there?  What is the installer's default?  Would installing other software change it?  I know I didn't mess with it until I stumbled on to it while trying to permute options in an attempt to get back to the working system I had before Friday's "updates" broke it.  Right now, neither is checked and the system seems to be working fine -- at least its not crashing.


I did manage to do a couple of short video clips of last Saturday's hail storm in Openshot after I stumbled on to this settings change.

---

### Post by linucksrox on 2013-04-29
&#3232;__&#3232;
Is this a blogging website now?

---

