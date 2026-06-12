---
title: "bootable usb flash"
date: 2012-08-30
forum: Server Platforms
---

### Post by nikibg on 2012-08-30
Hi,

I am novice in linux and 
I have to make bootable flash drive to boot linux distro from it.
It will make ram disk so  I'll need somewhere to save data.
What i must do 2 partition one for boot and one for storage and how to make them 
Pls help me

---

### Post by kurt18947 on 2012-08-30
Both Unetbootin and Startup Disk will do this.  They install the O.S. then create an ext2 partition for persistence.  A limitation of the 'liveUSB' is that the O.S. cannot be reliably updated.  Here is one discussion of live USB  compared to full install:

[http://ubuntuforums.org/showthread.php?t=1480144](http://ubuntuforums.org/showthread.php?t=1480144)

Here is another though it's Fedora so terms are different:

[http://forums.fedoraforum.org/showthread.php?t=221719](http://forums.fedoraforum.org/showthread.php?t=221719)

---

### Post by nikibg on 2012-08-30
10x for fast answer but i work with server platform and i dont know comands  for Startup disc creator

---

### Post by kurt18947 on 2012-09-01
> **nikibg said:**
> 10x for fast answer but i work with server platform and i dont know comands  for Startup disc creator

I don't know what's installed with on a server install.  I can launch USB creator from a terminal with this command:

```
usb-creator-gtk
```I doubt this would work if gtk is not installed.  Unetbootin is available for both Linux and Windows if that is a better option.

---

### Post by cortman on 2012-09-01
You can use dd if you're on a headless server. Info [here]("http://askubuntu.com/questions/21303/create-usb-installer-from-the-command-line/142587#142587").

Or use LiLi if you have Windows access (my favorite program for burning bootable media).

---

