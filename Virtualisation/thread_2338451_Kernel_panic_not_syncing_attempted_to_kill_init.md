---
title: "Kernel panic not syncing attempted to kill init"
date: 2016-09-28
forum: Virtualisation
---

### Post by hs0774 on 2016-09-28
I keep getting this error with virtual box and ubuntu what do I do to fix it?

[http://imgur.com/a/pQ6k4](http://imgur.com/a/pQ6k4)

here is what it looks like.

here's the attachment of my last log

---

### Post by howefield on 2016-09-28
Thread moved to the "*Virtualisation*" forum.

---

### Post by SeijiSensei on 2016-09-28
That's a "kernel panic."  If that log is from the host machine, then something is wrong with either your hardware or perhaps with the VirtualBox installation.  Did you install VB from the Oracle repositories?  If not, remove virtualbox from your system, then follow the procedure described here: [https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions](https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions)

If that log comes from the virtual machine itself, then try reinstalling the same version of Ubuntu in another virtual machine and see if the problem recurs.

---

