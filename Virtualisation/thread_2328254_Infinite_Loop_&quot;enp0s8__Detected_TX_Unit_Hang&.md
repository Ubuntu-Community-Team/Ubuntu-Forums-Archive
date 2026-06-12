---
title: "Infinite Loop? &quot;enp0s8 : Detected TX Unit Hang&quot; after crash."
date: 2016-06-19
forum: Virtualisation
---

### Post by david528 on 2016-06-19
I run Ubuntu on VirtualBox. Today I was prompted to upgrade to [16.04]("http://ubuntuforums.org/showthread.php?t=2322324") so I started this process.

During the upgrade the host machine hard drive became full and crashed the VM with a disk full error. 

So after cleaning some free space on the host I started the VM up again and all I get it this in an endless loop "enp0s8 : Detected TX Unit Hang". The Jiffies (what ever that is) is increasing so presume that this may end at some point / or will it?

Thinking it may be a network interface issue I stopped the VM and disabled the interface but it does the same thing with Jiffies starting back again at around "FFFF8000". I've also upgraded to the latest VirtualBox 5.0.22

I really wish I had a recent snapshot but I don't, can any one please explain what's going on, will it ever end, and/or how to break out of this.

Thanks

[IMG]http://i.imgur.com/ZAETOOv.png[/IMG]

---

### Post by david528 on 2016-06-19
Hi, so I solved my own problem. 

When I went to mount the vdi it said it was in use even though I had shutdown Virtualbox. So rebooting the host fixed that and stopped all the TX Unit Hang stuff.

Then just followed the instructions here to fix the upgrade. 
[http://askubuntu.com/questions/256241/upgrade-gone-bad-no-ubuntu-no-upgrade-no-windows](http://askubuntu.com/questions/256241/upgrade-gone-bad-no-ubuntu-no-upgrade-no-windows)

---

### Post by MAFoElffen on 2016-06-19
Happy you fixed your problem.

Since now "Solved" and you found resolution to your problem, please revisit this thread and follow the link at the top right of the page, "Thread Tools" > "Mark thread as Solved". That way it will help other users later to help them find solution to there similar problems.

---

