---
title: "SPARC Ultra5 &amp; X"
date: 2007-05-28
forum: Sun Sparc Users
---

### Post by ecarvalho on 2007-05-28
Guys
I installed the server version SPARC64 on my ultra 5.
I would like to install X. It says X is not installed.
So I did **sudo apt-get install x11-common**
Then I did **sudo apt-get install xorg**

All went well except I can't get X started. The following error message appears:

[B]Fatal server error:
xf86MapPciMem: Could not mmap pci memory [base=0xe2000000,hostbase=0xe2000000,size=2000] (Inappropriate ioctl for device)[/B]

Thanks for any advice!

---

### Post by ecarvalho on 2007-05-28
I've also installed xubuntu desktop
sudo apt-get install xubuntu-desktop

All goes well except I get the same error above when the system attempts to start X
I believe the video card is an ATI

---

### Post by reidms on 2007-06-06
Have you tried configuring X?

```
X -configure
``` should do it

---

### Post by ecarvalho on 2007-06-21
I'm running Solaris 10 with KDE for now but I will try Ubuntu again soon and attempt the X config - Thanks!

---

### Post by jdeisenberg on 2007-06-24
This post: [http://ubuntuforums.org/showthread.php?t=430611](http://ubuntuforums.org/showthread.php?t=430611) may have further information that will be useful to you.

---

