---
title: "DVD Multisession problem - GnomeBaker"
date: 2009-07-12
forum: Ubuntu Studio
---

### Post by prabath_fun on 2009-07-12
Hi all,
  I am using GNOMEBAKER for burning CD/DVD in Ubuntu9.04. I tried Multisession DVD. Very first session was success and while starting next session, I tried to import session from project menu. I got
"The mount point (e.g. /mnt/cdrom) for the writing device could not be obtained. Please check that the writing device has an entry in /etc/fstab and then go to preferences and rescan for devices."
as error.

After search in forums, I added 
/dev/sr0 /media/cdrom fs=cdfss,ro,procuid, nosuid,nodev,exec,iocharset=utf8 0 0

in /dev/fstab and got 

Error mounting /media/cdrom.
mount: only root can mount /dev/sr0 on /media/cdrom

as error.
Please help me. I don't want to use KDE applications..

With Thanks,
Prabath

---

### Post by prabath_fun on 2009-07-14
Any update.....

---

### Post by prabath_fun on 2009-10-20
I started using K3B and it is very good...
Prabath

---

