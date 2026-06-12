---
title: "Multiple screens in xorg.conf causes gnome-shell segfault"
date: 2012-03-19
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ryley on 2012-03-19
Hey guys, I just got around to installing Precise on my desktop (clean install, was using Lucid) and I can't seem to get gnome-shell to load when my xorg.conf file specifies all all four screens for my two radeon 5970's. This is using gnome-shell 3.3.90, I don't know if 3.2 works. Im using the latest Catalyst driver (12.2) and Unity and Unity 2D have no issues. I use only one monitor and when only one screen is specified in xorg.conf's server layout gnome-shell will load fine, however I really would like X to load on all 4 as OpenCL requires this.

Thanks in advance, I'm willing to try anything.

Ryley

---

### Post by dino99 on 2012-03-19
gnome-shell is only partialy upgrades, still wait for some  3.3.90-0ubuntu2 packages
[http://ubuntuforums.org/showthread.php?t=1940742](http://ubuntuforums.org/showthread.php?t=1940742)

but you should report this issue to get a fix.

---

### Post by ryley on 2012-03-19
Thanks for the reply dino99, I'll wait a bit before reporting the issue. If the next few gnome updates don't fix my problem, where would I report the issue? Sorry for the stupid question, I just wanna be a bit less slack in reporting problems before Precise is finished.

ryley

---

### Post by dino99 on 2012-03-19
into a terminal:

ubuntu-bug gnome-shell

this will report on launchpad, where you'll be asked to open an account if you have not one yet

---

