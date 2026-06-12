---
title: "Precise trashed my hdd?"
date: 2012-01-18
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by mrkofee on 2012-01-18
Hi,

sorry for the headline, but I'm having a very strange problem with one of my HDDs.

I have an external 1.5TB hdd which was connected via e-sata to an Ubuntu 10.04 LTS Server for the last years. Now I bought a new Server to upgrade from an old AMD X2 platform to an Intel i3 with Ubuntu Precise (Alpha Version).

The Problem is, that the filesystems on 2 out of 4 HDDs weren't recognized in the new server!
Not a that big deal... I have a backup of that data!

Now comes the external HDD. WHICH IS MY BACKUP! I connected it to the Precise Server to restore from backup... also no filesystem found!

Shouldn't be a that big deal... except that now my old server also doesn't find a valid filesystem on it!

gparted doesn't find anything. xfs_repair/xfs_check doesn't find anything:
Phase 1 - find and verify superblock...
xfs_repair: error - read only 0 of 512 bytes

What can cause this? I checked the hdd for errors using my vendors tools, but they are ok!


Any help is appreciated.

Thanks!
Chris

---

### Post by sudodus on 2012-01-18
Maybe you can try gpart (not gparted) and testdisk. Browse the internet to find them. Sometimes the partition table can be repaired.

---

### Post by mrkofee on 2012-01-18
Thanks!

I'm just running testdisk, but this seems to take a couple of hours. At least it discovered my XFS 4 Filesystem :)

Still... I really don't get how this could happen.

---

### Post by xyzzyman on 2012-01-18
Hence why it's still in alpha and not in beta.

---

### Post by nothingspecial on 2012-01-18
Moved to Ubuntu +1

---

### Post by xyzzyman on 2012-01-18
If it was the OS's fault (As opposed to them not being properly dismounted or previous error's in the FS), it may be due to all the changes in XFS through kernel 3.2's devel cycle.

---

### Post by ronacc on 2012-01-18
you could also try 10.04 on a live CD or usb stick and see if it finds them , you can mount them from nautilus in the live session .

---

### Post by mrkofee on 2012-01-18
Well, I did try to mount the HDD with an 10.04 system. But the filesystem isn't detected either. Also testdisk doesn't find a anything useful... some XFS here some HFS there, somthing unknown in between...

---

### Post by sudodus on 2012-01-18
Try also ***gpart*** before resorting to ***photorec*** or similar tools!

---

### Post by ronacc on 2012-01-18
If your external drive was not connected during the installation of precise (alpha) It couldn't have done anything to the drive so perhaps it is the way the new motherboard handles e-sata . If you still have the old system available try connecting the external to it , then if that works back it up to dvd's before you potentially do lose your data . If the external was connected during install it is possible that the installer did something nasty like formatting the wrong drive . Your data can still probably be recovered as long as it was not overwritten .

---

### Post by cariboo on 2012-01-18
Have you got xfsprogs installed?

---

### Post by mrkofee on 2012-01-18
In reply to the last two replies: please read my initial post

I do have xfsprogs installed, hence I have xfs_heck and xfs_repair.
I also tried to connect the drive to the old server and the parition is also gone over there.

Btw. the drive wasn't connected during installation!

I'm currently running gpart... takes ages.

---

### Post by mrkofee on 2012-01-19
Well... gpart didn't find anythingn useful.

But testdisk does see my partition:
$ sudo testdisk /dev/sdd /list
[sudo] password for mrkofee:
TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)
Please wait...
Disk /dev/sdd - 1500 GB / 1397 GiB - CHS 182401 255 63, sector size=512

Disk /dev/sdd - 1500 GB / 1397 GiB - CHS 182401 255 63
     Partition                  Start        End    Size in sectors
   P XFS 4                    0   0  1 182401  47 29 2930275055

But again if I try to mount it:
$ sudo mount /dev/sdd /mnt
mount: /dev/sdd: can't read superblock
(dmesg)
[64970.503735] sdd: rw=32, want=2930277168, limit=2930275055
[64970.503739] XFS (sdd): last sector read failed

$ sudo xfs_repair /dev/sdd
Phase 1 - find and verify superblock...
xfs_repair: error - read only 0 of 512 bytes

Any ideas left??


And yes, I know I'm running xfs_repair on the hdd itself, not on any partition, but I didn't partition the hdd in the first place, but instead created the fs on the entire hdd.

---

### Post by whoop on 2012-01-19
> **mrkofee said:**
> Well... gpart didn't find anythingn useful.

But testdisk does see my partition:
$ sudo testdisk /dev/sdd /list
[sudo] password for mrkofee:
TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)
Please wait...
Disk /dev/sdd - 1500 GB / 1397 GiB - CHS 182401 255 63, sector size=512

Disk /dev/sdd - 1500 GB / 1397 GiB - CHS 182401 255 63
     Partition                  Start        End    Size in sectors
   P XFS 4                    0   0  1 182401  47 29 2930275055

But again if I try to mount it:
$ sudo mount /dev/sdd /mnt
mount: /dev/sdd: can't read superblock
(dmesg)
[64970.503735] sdd: rw=32, want=2930277168, limit=2930275055
[64970.503739] XFS (sdd): last sector read failed

$ sudo xfs_repair /dev/sdd
Phase 1 - find and verify superblock...
xfs_repair: error - read only 0 of 512 bytes

Any ideas left??


And yes, I know I'm running xfs_repair on the hdd itself, not on any partition, but I didn't partition the hdd in the first place, but instead created the fs on the entire hdd.

Not talking about personal experience here, just thinking out loud (so it could be total crap) but shouldn't you run that xfs repair tool against a specific partition? Like /dev/sdd1 or something...

Hope you solve this problem cause xfs is scaring me now!!!

---

### Post by mrkofee on 2012-01-19
> and yes, i know i'm running xfs_repair on the hdd itself, not on any partition, but i didn't partition the hdd in the first place, but instead created the fs on the entire hdd.
                                                                              ^^^^^^^^^^^^^
;)

---

### Post by whoop on 2012-01-19
ooops....

---

### Post by mrkofee on 2012-01-24
It turned out, that mount wants to access about 1Mb above the end of the device!

[http://ubuntuforums.org/showthread.php?t=1755429](http://ubuntuforums.org/showthread.php?t=1755429)

This thread looks exactly like my issue - just with another filesystem?!

So there must really something weird going on!

Unfortunately I can't shrink an XFS filesystem, so there must be another way to fix this!

Any ideas?

---

