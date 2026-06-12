---
title: "RAID 6 file system corruption"
date: 2011-01-29
forum: Server Platforms
---

### Post by Garugaga on 2011-01-29
I have an ubuntu 10.10 server install with 5 1.5 tb hard drives in a mdadm software RAID 6 array.

 About a week ago one of my hard drives failed and dropped out of the array. At around the same time I started noticing some corrupted files. I can't pinpoint an exact time frame because the corruption is quite subtle. All of the files are still there and appear to be intact. I only noticed the corruption when I watched some videos off of the array. I rechecked some torrents and they all came back between 97 and 99 % complete. 

I removed the drive from the array so right now I am running a degraded array.

In an attempt to fix the corruption I tried running fsck on the array. But it gives this error:

```
marcel@server:~$ sudo fsck.ext3 /dev/md0
e2fsck 1.41.12 (17-May-2010)
fsck.ext3: Superblock invalid, trying backup blocks...
fsck.ext3: Bad magic number in super-block while trying to open /dev/md0

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```

When I try to find out the location of the backup superblocks with dumpe2fs I get this error:

```
dumpe2fs 1.41.12 (17-May-2010)
dumpe2fs: Bad magic number in super-block while trying to open /dev/md0
Couldn't find valid filesystem superblock.

```

I tried running fsck with the normal locations for the backups (eg 8193,32768,etc) and it just keeps giving the same error. So either I am trying the wrong super blocks or they are all corrupted.

I have no idea what to do now. I read that the journal might be corrupted so I was thinking that I should disable and re-enable the journaling with tune2fs. I just don't know if that will mess things up even more. 

The funny thing with this is that I can still mount the drive and access all the data fine. I'm pretty sure that normally with a corrupted superblock that's not possible. 

Is there anything I can do to rebuild the corrupted data? Could my hard drive have corrupted data on the way out?

---

### Post by |{urse on 2011-01-30
Run badblocks on each drive then try to rebuild.

[http://manpages.ubuntu.com/manpages/intrepid/man8/badblocks.8.html](http://manpages.ubuntu.com/manpages/intrepid/man8/badblocks.8.html)

You should really consider a hardware array if your data is mission critical.

---

