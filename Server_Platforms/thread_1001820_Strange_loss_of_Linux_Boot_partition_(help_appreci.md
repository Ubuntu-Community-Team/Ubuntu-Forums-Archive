---
title: "Strange loss of Linux Boot partition (help appreciated)"
date: 2008-12-04
forum: Server Platforms
---

### Post by Zero Ballance on 2008-12-04
Recently a severe problem occurred to my ubuntu 7.10 server. The problem started when downloading a file (internal network download) from the server was going really slow. This slow download problem appeared after we had a couple of electricity "breakdowns" that shut down the server abruptly in a very bad way.

Now instead of trying to figure out what process was causing this slow download problem I decided to just reboot the server (I blame MS for the reboot disease) since it's not a critical server. After the server was rebooted I was able to ping the server but I was unable to ssh into the server. After a couple of retries of this rebooting I decided to hoop up the server to a monitor again since I had no idea why ssh would not automatically start while it should normally do so. 

Upon doing so I noticed that GRUB was not loading correctly or better said it was not loading at all, it just gave me the standard GRUB stage 1.5 loading please wait... message. If I waited long enough it would eventually kick me into a DOS/Terminal like environment but not really. It was just a blank screen with a blinking cursor and I was not able to do anything.

So I decided to look on the internet to find a way to fix my GRUB. This brought me to [Super Grub Disk (SGD for short)]("http://www.supergrubdisk.org/index.php") that would magically rescue my GRUB. Obviously it didn't work or else I would not post here ;)

I followed the instructions precisely as I could find on the [SGD]("http://www.supergrubdisk.org/index.php") website, but it just was unable to repair my GRUB because it was unable to find my Linux boot partition for some very strange reason :( (I forgot the exact messages, sorry for that)

At that point I was like screw fixing my GRUB, I just need to recover some data (I mainly need to recover 2 database files, about the rest I don't really care). Doing some more research brought me to the [TestDisk and PhotoRec]("http://www.cgsecurity.org") Software. First I wanted to try and fix the partition tables as described in the step by step wiki of the TestDisk software. This software was able to find my boot partition, but no matter what I tried it was never able to read the partition that was holding my linux boot. It always gave me the message that this partition was damaged. OK fine I already knew that (couple of hours wasted for nothing :s), but I wanted to try and see my files on this partition (it holds my databases) and no matter what I tried to do it was just not possible. 

In the process of trying out some things with TestDisk I was able to find the windows partition back from before I installed Ubuntu server on it. I consider this strange since I formatted this hard drive more than once while I was installing Ubuntu server on it (I installed the server multiple times to try out some tutorials on setting up a domain controller). Btw I was always able to access the other partition that holds most of my data (I always mount home on another partition) and copy everything if I want to, but unfortunately it does not hold my most important files (the 2 db's I want to recover).

Because TestDisk didn't seem to help me out much I decided to try out the PhotoRec software since it was supposed to be able to find back files even when TestDisk would fail and indeed it was able to find back files. Unfortunately it was not able to find the mysql files I was looking for. I played with the file options of PhotoRec, but to no avail :( it can find files that were on the very old multiply overwritten windows partition (I know this because there were never .doc files on the Ubuntu server, neither were there WoW pictures etc...), but not the more recent "never" overwritten files on my Linux boot partition.

So to come to an end, does anyone happen to have an idea what went wrong and what I could possibly try to recover these 2 files. If you need more specifics, feel free to ask and I will try to get more details. I am especially interested in what went wrong so I can prevent it from happening (if possible) in the future.

I would also like to add a 3 point morale to this story.
1) Always make regular backups!
2) Put critical files on another partition!
3) BACKUPS!!!!!!

---

### Post by caljohnsmith on 2008-12-04
Do you have a Ubuntu Live CD that you can boot on that computer to do troubleshooting? If so, how about doing that, open a terminal (Applications > Accessories > Terminal) and please post the output of:
```
sudo fdisk -lu
```
If that happens to show your linux partition, I would first try running an fsck on it:
```
sudo fsck -y /dev/sdXY
```
And replace sdXY with the linux partition. Let me know if you can make it that far.

---

### Post by Zero Ballance on 2008-12-04
I'll try it in the morning.

Edit:

Forgot I was on Ubuntu with the HD connected as a portable HD. 
Here is the info you requested.

```
Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63    39070079    19535008+  83  Linux
/dev/sdc2        39070143   620237519   290583688+   f  W95 Ext'd (LBA)
/dev/sdc3       620253585   625137344     2441880   82  Linux swap / Solaris
/dev/sdc5        39070206   620237519   290583657   83  Linux

```

```
sudo fsck -y /dev/sdc1
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext2: Attempt to read block from filesystem resulted in 
short read while trying to open /dev/sdc1 
Could this be a zero-length partition?

```

I only tried the sdc1 since that is the boot partition. I can access sdc2 
(aka sdc5) just fine. sdc3 is just swap partition.

---

### Post by CrucifiedEgo on 2008-12-04
the fact that there is overlap between /dev/sdc2 and 5 (most of the blocks are the same) is absolutely bizarre...

---

### Post by Zero Ballance on 2008-12-05
> **CrucifiedEgo said:**
> the fact that there is overlap between /dev/sdc2 and 5 (most of the blocks are the same) is absolutely bizarre...

I think this is because sdc2 is an extended partition to sdc1. I choose this in the past so that in case my sdc1 would become full it would use the extended partition to store the rest of the data. Now I know that for my purposes this is utterly useless, but when I installed this server I did not yet know that this was gonna be useless.

I have done some more googling on the "... Could this be a zero-length partition?" error message, but I haven't found anything useful yet.

---

