---
title: "mkinitrd: Cannot determine SCSI module"
date: 2008-05-14
forum: Server Platforms
---

### Post by TruckStuff on 2008-05-14
I've compiled custom kernels for my Ubuntu servers and everything has been happy for a while.  I go to do a few upgrades today and find that mkinitrd won't build me a new initrd image: ```
$ sudo mkinitrd -o /boot/initrd.img-2.6.25.3 2.6.25.3
/usr/sbin/mkinitrd: Cannot determine SCSI module
``` So I start looking at mkinitrd and find it complains about this because it can't find /proc/scsi.  Fair enough, it doesn't exist on my system because I'm already running 2.6.24.2.  The kicker is about 100 lines later you see this: ```
# New kernels don't list the scsi drivers in /proc/scsi
``` No kidding!  So why does mkinitrd error out if it has a work around a few lines later?  Any thoughts on a work around so I can get to the work around?

---

