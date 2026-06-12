---
title: "Nautilus locks on drag and drop to ZFS pool"
date: 2014-02-04
forum: Server Platforms
---

### Post by Damon_Sisk on 2014-02-04
1) Installed Ubuntu Server 12.04 on 200GB SATA drive.  Machine also has 3x2TB SATA drives, one of which has data
2) Installed Unity (didn't realize Ubuntu Server did not have GUI, yes I'm very new to all this)
3) Installed mdadm and setup RAID1 array on 2 of the drives
4) Learned about ZFS, installed it according to instructions here [http://www.latentexistence.me.uk/zfs-and-ubuntu-home-server-howto/](http://www.latentexistence.me.uk/zfs-and-ubuntu-home-server-howto/) with the following commands:[INDENT]sudo add-apt-repository ppa:zfs-native/stable
 sudo apt-get update
 sudo apt-get install ubuntu-zfs

[/INDENT]
5) Uninstalled mdadm, then discovered I needed it to remove the RAID1 array, so re-installed it and removed the array
6) Created a mirrored zpool via:

zpool create data mirror /dev/disk/by-id/scsi-SATA_(can't remember right now) /dev/disk/by-id/scsi-SATA_(can't remember this one either)

7) Verified that the zpool seemed ok via:
sudo zpool list
(which showed the zpool with appropriate size information, etc.)

8) Verified that the correct two disks made up the mirrored zpool via:
sudo zpool status

9) Tried to copy ~ 800GB of files from the 2TB drive not in the zpool to the zpool at /data via drag and drop in Unity.  A window opened claiming that 65kb (or so) had been copied out of the ~800GB, but the progress bar never moved.  The system monitor utility (can't remember the name) showed one of my 2 CPU's at 100% utilization.
10) I left it on overnight, no progress at all.  Started the process monitor program (sorry again, still new to this so I don't remember the name) and noticed that Nautilus was using %49 of my CPU capacity (thus the pegged CPU).
11) Forced the machine to restart, then experimented dragging and dropping various combinations of file sizes/numbers until I found that it does not seem to matter how many files are in the attempted copy, as long as the total size is less than 2MB or so.  If more, Nautilus displays the window with the progress bar that locks up.
12) found that I could copy ~2MB or so of files all at once to the zpool without any issues

Sorry I'm so new I don't know the proper names/terms for all this.  I guess I'm a baby with a power tool!  However, I have used UNIX back in college, and done a fair bit of programming, so I can follow directions fairly well...

Any ideas?

---

### Post by Damon_Sisk on 2014-02-05
If I asked a dumb question, please point me to resources I can read to help me understand whatever I've missed.  For example, I am confused about the difference between ZFS and ZFS-Fuse, though I'm trying to read more in order to understand.

---

### Post by bab1 on 2014-02-05
> **Damon_Sisk said:**
> If I asked a dumb question, please point me to resources I can read to help me understand whatever I've missed.  For example, I am confused about the difference between ZFS and ZFS-Fuse, though I'm trying to read more in order to understand.

ZFS can be run entirely in the kernel as a module (driver) or in user space (FUSE).  The kernel driver is more efficient. 

Drag and Drop is not the same as Cut and Paste.  Try Cut and Paste on some files and see what you get.  If you look at the logs (at /var/log) such as syslog of auth.log you might see a problem.  A guess is that the user permissions are not valid.  You can view that last lines of a long log file by using this format```
tail -n20 <log file>
```...where <log file> is the name of the log file.

---

### Post by brokenhachi on 2014-02-07
ZFS is a deep, deep filesystem and takes a lot to understand.. (i'm just getting started myself) There are a lot of configurable options that can change the performance of the pools.

consider setting some of the options listed here: [http://askubuntu.com/questions/228386/how-do-you-apply-performance-tuning-settings-for-native-zfs](http://askubuntu.com/questions/228386/how-do-you-apply-performance-tuning-settings-for-native-zfs) 

The above options helped a lot with my I/O especially turning prefetch off.

---

### Post by Damon_Sisk on 2014-03-10
Apparently, ZFS for Linux does not play well with 32-bit Linux OS.  See [http://zfsonlinux.org/faq.html](http://zfsonlinux.org/faq.html)

Question 1.5 states:
[TABLE="width: 80%"]
[TR="bgcolor: #aaaaaa"]
[TH]1.5 Why should I use a 64-bit system? 		
[/TH]
 	[/TR]
 	[TR]
 		[TD] **You are strongly encouraged to use a 64-bit kernel.  At the moment zfs will build in a 32-bit environment but will not run stably.**

[/TD]
[/TR]
[/TABLE]

Thank you to all who responded.  My system crashed and would not boot.  For some reason the boot drive was set as read only.  I discovered I had a 64 bit processor, so nuked the drive and installed Ubuntu 12.04 64 bit, and now ZFS seems quite happy!  Currently listening to music files, courtesy of Ubuntu serving files from mirrored ZFS drives!

---

