---
title: "Virtualbox 1.5.6 guest addition problem"
date: 2009-07-15
forum: Virtualisation
---

### Post by back2arie on 2009-07-15
I've installed virtualbox and windows XP as guest, but when i want to install the guest addition, the image file(VBoxGuestAdditions_1.5.6.iso) have been downloaded, and already mounted, nothing happen on guest OS, i try to click the CD-ROM drive but windows said that the file corrupted.

I'm finally noticed that the image file is too small (256 Bytes), it's weird...
I'm trying alternative download, [ftp://ftp.dvo.ru/pub/distfiles/VBoxGuestAdditions_1.5.6.iso](ftp://ftp.dvo.ru/pub/distfiles/VBoxGuestAdditions_1.5.6.iso) (5MB), and it works...

Tested on Hardy Heron (8.04.3)
Hope it will help somebody...

---

### Post by bodhi.zazen on 2009-07-15
That is a very old version of Virtualbox you have there. Virtualbox is currently on 3.0.2.

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

The additions are included when you install the PUEL version of VirtualBox, so no need to download a copy.

From your post it sounds as if the problem was with the iso (was the origional corupt somehow ?) and your problem is solved.

If you need assistance let us know.

---

### Post by wlee on 2009-10-04
> **back2arie said:**
> I'm finally noticed that the image file is too small (256 Bytes), it's weird...
I'm trying alternative download, [ftp://ftp.dvo.ru/pub/distfiles/VBoxGuestAdditions_1.5.6.iso](ftp://ftp.dvo.ru/pub/distfiles/VBoxGuestAdditions_1.5.6.iso) (5MB), and it works...

Tested on Hardy Heron (8.04.3)
Hope it will help somebody...

I noticed the same issue. Thanks for the alternate download!

---

