---
title: "folder i/o error"
date: 2012-06-16
forum: Server Platforms
---

### Post by badperson on 2012-06-16
Hi,
I have ubuntu server running on a box I use as a headless system, and I have had some problems with it over the last 6 months or so. I described the problem in a [thread]("http://ubuntuforums.org/showthread.php?t=1905674") awhile back. I had had some trouble after upgrading to 11.10 (think that was the version). I inserted new ram, and the system then worked ok. 

I had a similar problem recently, I noticed it when I was unable to write to my samba share. I pulled out the machine, re-seated the ram, then did an upgrade to 12.04.... 
uname gives me this: 
> Linux ubuntu-server 3.2.0-24-generic #39-Ubuntu SMP Mon May 21 16:52:17 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux



but, the problem I'm having now is that I'm unable to write to one of the folders on the machine. when I try to navigate to that folder with "cd /parent/code", I get: 

> -bash: cd: code: Input/output error



when I do "ls -al" I get the following for that folder: 

> d?????????  ? ?    ?        ?            ? code


I'm unable to edit a file using vim, and Im unable to create a folder, I get an error saying that the file system is read-only. 

Doe that mean the HD is corrupted? Not sure what to do about that, other than replace the HD. On a headless server system, what is the best way to make sure that the HD's and the system in general are reliable? I usually leave the server on all the time. 


thanks, 
bp

---

### Post by bab1 on 2012-06-16
> **badperson said:**
> Hi,
I have ubuntu server running on a box I use as a headless system, and I have had some problems with it over the last 6 months or so. I described the problem in a [thread]("http://ubuntuforums.org/showthread.php?t=1905674") awhile back. I had had some trouble after upgrading to 11.10 (think that was the version). I inserted new ram, and the system then worked ok. 

I had a similar problem recently, I noticed it when I was unable to write to my samba share. I pulled out the machine, re-seated the ram, then did an upgrade to 12.04.... 
uname gives me this: 



but, the problem I'm having now is that I'm unable to write to one of the folders on the machine. when I try to navigate to that folder with "cd /parent/code", I get: 




when I do "ls -al" I get the following for that folder: 



I'm unable to edit a file using vim, and Im unable to create a folder, I get an error saying that the file system is read-only. 

Doe that mean the HD is corrupted? Not sure what to do about that, other than replace the HD. On a headless server system, what is the best way to make sure that the HD's and the system in general are reliable? I usually leave the server on all the time. 


thanks, 
bp

At this point I would check the partition with the command *fsck*,  Before you can do that you need to unmount the partition you wish to *fsck*.  How many partitions are there on the disk?  Is the partiton that holds /parent/code the same as the root (booting) partition.  If so then you will have to bood form LiveCD or some bootable media and fsck the / (boot) partition that is giving you trouble.  All of this can be done from the command line.  The command to check and repair the file system is ```
sudo fsck </dev/sdan>  
# where sdan is the partiton ID such as sda1 or sda2
# If you have a second disk it might be sdb1 or 2 
``` 

This is only to see if you can fix the immediate problem.  After that you might install smartmon tools to monitor the HDD in the future.

---

### Post by volkswagner on 2012-06-17
I'm not sure how this happens, but It may be permissions got messed up.

I do recall seeing a similar problem in the past.  I don't recall the cause though.

Can you issue a chmod to change the permissions?

```
sudo chmod 775 /parent/code
```

---

### Post by badperson on 2012-06-17
hi,
thanks for the replies. chmod did not have an effect, still got the same error. Here is what I get from sudo lshw -C disk:

>  *-disk:0                
       description: ATA Disk
       product: HDS728080PLA380
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: PF2O
       serial: PFDB37SWSUTV7E
       size: 76GiB (82GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=0001c97e
  *-disk:1
       description: ATA Disk
       product: WDC WD10EADS-00M
       vendor: Western Digital
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/sdb
       version: 01.0
       serial: WD-WCAV51010802
       size: 931GiB (1TB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=ca4a77fb
  *-disk:2
       description: SCSI Disk
       physical id: 2
       bus info: scsi@2:0.0.0
       logical name: /dev/sdc
  *-disk:3
       description: ATA Disk
       product: WDC WD10EADS-00M
       vendor: Western Digital
       physical id: 3
       bus info: scsi@3:0.0.0
       logical name: /dev/sdd
       version: 01.0
       serial: WD-WCAV51013798
       size: 931GiB (1TB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=50c621e4
  *-cdrom
       description: DVD-RAM writer
       product: CDDVDW SH-S223C
       vendor: TSSTcorp
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/sr0
       version: SB00
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc


here are the relevant entries in /etc/fstab: 

> /dev/sdb1       /media/share ext3 defaults      0       2
/dev/sdc1       /media/db1      ext3    defaults        0       2
/dev/sdd1       /media/db2      ext3    defaults        0       2
~                                                                         


/dev/sdc is the drive that contains the folder I'm having a problem with. Not sure why it's coming up as a scsi drive there. I'm pretty sure that when I did the upgrade a few weeks ago I tested that I could read/write on all the drives, but maybe I was wroing. 

 I thought I might pull out the machine and physically make sure the drives are all plugged in.  BTW....this machine has one system HD (where i boot from) and three other hd's, /media/share, /media/db1 and /media/db2. 

the folder in question in on /media/db1
bp

---

