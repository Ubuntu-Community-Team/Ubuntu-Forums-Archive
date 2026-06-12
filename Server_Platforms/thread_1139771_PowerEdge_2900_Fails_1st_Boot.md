---
title: "PowerEdge 2900 Fails 1st Boot"
date: 2009-04-27
forum: Server Platforms
---

### Post by jverge on 2009-04-27
I have a new Dell PowerEdge 2900 server with an integrated SAS6iR SAS RAID controller with two 750GB Near-Line SAS hard drives.  The hard drives are not set up with any sort of RAID, just a bunch of disks. 

I have tried to install either 9.04-server (64bit) or 8.10-server (64bit).  The installation goes fine but when I reboot the system, I get the following error during boot...

Gave up waiting for device. Common problems:
- Boot args (cat /proc/cmdline)
  - Check rootdelay= (did the system wait long enough?)
  - Check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/xxxxxx-xxx-xxxx-xxx... does not exist. Dropping to shell!

and then .. BusyBox terminal

I have seen posts describing possible fixes in earlier versions of ubuntu, the most promising being that the kernel fails to compile the megaraid_sas driver into the initrd.img file.  I haven't had a chance to try that yet but I have tried:
   1) replacing /dev/disk/by-uuid/... with /dev/sda2 (my / partition) in menu.lst
   2) disabling the SAS card for both BIOS and OS. This still installed fine but then the drive wasn't seen by the BIOS
   3) enable SAS card for BIOS only.  The drive was seen this time but I got the same ALERT! error.

Any help would be appreciated.
James

---

### Post by ikonia on 2009-04-27
first thing to do is make sure the controller is actually set to jbod mode, if it's set to raid mode, but the disks are not in any raid configuration as you suggest, the disks are still "raid" even though they are not in a raid set.

Setting the disks to jbod would be my first port of call.

---

### Post by jverge on 2009-04-27
Yes, I should have mentioned that it is setup as jbod.

---

### Post by carbm1 on 2009-04-27
I have two PowerEdge 2900 with the same RAID card running 8.04 Server without any issues. Have you tried it?

---

### Post by jverge on 2009-04-27
No I haven't tried 8.04, I will download it now and give that a try.  

By the way, do you have RAID or jbod?

---

### Post by carbm1 on 2009-04-27
I am running RAID 5 on both. I would still try 8.04 just in case.

Thanks,

Craig

---

### Post by jverge on 2009-04-27
Thanks to those who replied.  

For all those interested in the very simple solution, all that was needed was to give grub more time with the rootdelay=180 option in /boot/grub/menu.lst (which was suggested in the error output initially but who would have thought).  I inserted this by 1st booting with a Knoppix DVD and making the changes.

I found this solution in this post [http://ubuntuforums.org/showthread.php?t=1063456](http://ubuntuforums.org/showthread.php?t=1063456) (gotta give the credit to [beatgr]("http://ubuntuforums.org/member.php?u=765098")).

---

