---
title: "bios sees scsi drive, os does not"
date: 2010-01-21
forum: Server Platforms
---

### Post by wynxpert on 2010-01-21
I've been trying to install an external scsi drive onto a Dell PE 4600 server.  The Adaptec bios sees the drive but I can't configure it with fdisk in the OS.  Running ubuntu 9.1 and other drives (sata cd, cd, raid hard drive) are shown in df -h.  I'm rather newbie so be gentle.

---

### Post by steven.jones on 2010-01-21
Which Adaptec? 2940? these should be so generic its not an issue, raid cards however, I have an Adaptec 2100S that ubuntu cant see....It seems its not unusual on older hardware for the raid card not to be seen on new distros, Ive had awful issues...

Try fdisk -l this should list the disks available to partition. if its not there look in dmesg....see if the controller and disks is seen...if not maybe raise a bug with ubuntu, but good louck on that their bug system is awful to use.

Ive had a lot of problems with perc2 and 3dc trying to install new distros on them over the last month. Debian 5.03 and RHEL5.3 wouldnt see the controller, hence no disk...ubuntu9.10 did so now Im on Ubuntu!....Ubuntu wouldnt see my Promise Sx6000 though...at least as a boot device so I had to insert a Perc3DC to boot with....and use the SX6000 as a slave....which isnt so bad.

Another possibility is, is your scsi termination correct? if you can see the controller in dmesg but not the disk, just double check that.

Otherwise something like a PERC 3DC or 4DC could be fitted....or an Adaptec 2940UW or 3940UW if raid isnt needed...all these should be cheap.

regards

---

