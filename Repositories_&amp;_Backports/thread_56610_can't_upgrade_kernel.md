---
title: "can't upgrade kernel"
date: 2005-08-13
forum: Repositories &amp; Backports
---

### Post by ke han on 2005-08-13
According to 'uname -r' I have kernel 2.6.10-3-386.
I need to install vmWare 5.  This requires I have linux headers installed.
However, I cannot find a package for linux-headers-2.6.10-3-386.
I do find packages for linux-headers-2.6.10-4-386 and 2.6.10-5-386.
According to all the postings I have read about installing vmware on ubuntu, everyone seems to have kernel 2.5.10-5-386.  How is this so???
I do 'apt-get update' and apt-get dist-upgrade' .  I have nothing left to install and my kernel is stuck on 2.6.10-3-386.

What's UP!!!!  This is seriously weird.
Any thoughts?

thanks, ke han

---

### Post by nad on 2005-08-13
Have you restarted your computer? This is one of the few times that you have to reboot a linux system in order to have the change take effect.

Before you reboot though, doublecheck your /boot/grub/menu.lst file to confirm that everything looks okay.

---

### Post by PeP on 2005-08-13
just apt-get install linux-image-2.6.10-5-386 and reboot :-)

---

