---
title: "Panv3 GRUB fails to load"
date: 2008-10-25
forum: System76 Support
---

### Post by Zxaos on 2008-10-25
There was already a thread on this issue at [http://ubuntuforums.org/showthread.php?t=636664](http://ubuntuforums.org/showthread.php?t=636664) but it has expired and been locked.

Has there been any progress on this issue? It has started happening increasingly frequently for me (I just had to restart four times to get this machine to boot - it kept POSTing and then not loading GRUB). It's starting to get a little worrying.

---

### Post by ctsdownloads on 2008-10-26
No real way to help here as it is not something I can see being fixed without a log file or a grub error code, but you could try this next time it happens.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by thomasaaron on 2008-10-27
I've had this happen a number of times on a number of computers. The problems with fixing this are: a) its occurrence is unpredictable; b) it leaves no errors in the logs, as it is pre-grub.

I've come to think that it is probably just some sort of fluke, or minor data corruption, or hardware inconsistency that causes grub to not be found. On some systems, I've had some luck with re-imaging. With others, changing hard drives worked.

The good news is, I seriously doubt you will corrupt your OS by hard-resetting prior to grub.

---

