---
title: "Restore macrium hard disk image in virtualbox"
date: 2010-12-28
forum: Virtualisation
---

### Post by supershin on 2010-12-28
Hi, I have a macrium reflect backup of a hard drive and I want to restore it to the guest hard drive. 

I'm running Ubuntu Lucid Lynx with Virtualbox 3.2.10 and I have Win7 as a guest machine. I have 3 usb ports, 2 are used by the cd/dvd drive to load the macrium reflect boot cd and my external hard drive which has the image file needs 2 usb ports. So i'm short 1 port though I tried it with just one. I also enabled the external USB hard drive.

I tried to boot the cd and then access the image from the external via the boot cd file browser but it gives the guest machine hard drive listing. I also tried some other stuff, like shared folders, but that was awhile back. Anyway, how would you go about restoring the backup to a guest machine?

---

### Post by supershin on 2011-03-17
Did some research and found out I can load an ISO image file that is on the hard drive. So I save the macrium boot CD as a image and set virtualbox to boot from it thus freeing my 2 usb ports. 

The only thing is that the external hard drive has more than 3 partitions and only 3 partitions are listed by macrium. I believe this is an issue with macrium free version.

---

