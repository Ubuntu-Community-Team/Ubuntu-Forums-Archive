---
title: "Help?"
date: 2010-05-12
forum: Ubuntu Moblin Remix
---

### Post by utjbart on 2010-05-12
I'm pretty new to linux in general.  I recently purchased an Acer Aspire One Netbook and tried to install the Ubuntu OS on it with absolutely no success at all.  I first tried making a bootable flash drive.  I'm able to boot from the flash drive and load the OS but I'm unable to actually install the OS onto my hdd.  I tried to do the install before booting the OS from the flash drive and received a screen that had an error that looked like a missing file and went to the terminal with I believe it said transinit or something like that.  I then just waited instead of trying to install and I was able to boot from the flash drive.  I tried to install ubuntu from the GUI in which I thought it was going to install because I went through the process of creating the partition with a swap partition and the rest dedicated to Ubuntu but it still does not boot after I remove the flash drive.  
 
I then burned the ISO onto a DVD and tried that way with a external cd/dvd drive but I just kept getting an IO error and could not read this disc.  So far my experience with trying to put netbook remix 9.10 onto a netbook has been very very frustrating.  I'm to the point of giving up but now I no longer have Windows 7 on it anymore.  So I need an OS on my netbook.  Does anyone have any suggestion?:confused:

---

### Post by utjbart on 2010-05-12
When I try to install from the flash drive I get:

Gave up waiting for root device.  Common Problems:
- Boot args (cat /proc/cmdline)
-Check rootdelay = (did the system wait long enough)
- Check root = (did the system wait for the right device?)
-Missing modules ( cat /proc/modules; ls /dev)
Alert! does not exist dropping to a shell!

---

### Post by cariboo on 2010-05-12
What program are using to create your flash drive image. I have had great success with [unetbootin]("http://unetbootin.sourceforge.net/"). If you have Ubuntu installed on an other system, unetbootin is in the repositories.

---

### Post by utjbart on 2010-05-12
> **cariboo907 said:**
> What program are using to create your flash drive image. I have had great success with [unetbootin]("http://unetbootin.sourceforge.net/"). If you have Ubuntu installed on an other system, unetbootin is in the repositories.
 
I used unetbootin to create the flash drive image.

---

