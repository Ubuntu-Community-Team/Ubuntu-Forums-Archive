---
title: "xfs file systems"
date: 2011-10-18
forum: Server Platforms
---

### Post by MakOwner on 2011-10-18
Two questions, really. And this has probably been beat to death, but I can't seem to find the right keywords for search to get to the answers.

First:
Is there a (better) alternative for 10TB+ file systems on servers with limited memory?
I use the filesystems on servers with 4GB - 20GB files, each accompanied by descriptor files of only a few hundred bytes, so I have 50/50 mix of very large and very small files.

Second:

```

UUID={uuid} /media/md0p1 xfs default,errors=remount-ro	0	1 

```

With this in the fstab I get this from mount -a 
```

mount: wrong fs type, bad option, bad superblock on /dev/md0p1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

So long as I mount the filesystem manually, it mounts right up.
It could really be an issue with the filesystem, but I can't get xfs_check to run to completion - even on a 64 bit system with 16 GB of RAM.

Is there a reasonable way to check/repair an xfs filesystem without supercomputer resource requirements?  While I know that 16GB isn't anywhere near the upper limit of open systems these days, that's a pretty hefty chunk of memory for me.



I have two external 8 bay enclosures, one with 1.5TB SATA drives and the other with 8 2TB SATA drives.  Both are configured suing software RAID5. 

Would I be better off just using ext4?
Will it work with filesystems this size?

---

### Post by Hakunka-Matata on 2011-11-01
Hi, no answers from me, but I also have a HDD with a large xfs partition on it.  
The only tools I've used so far that recognize the xfs partition is **sfdisk**.  I'd like to shrink it and free some space but do not know what software tool to use, but I've just started looking too, so that's ok.  The HDD is out of a LaCie NAS box.  500GB drive with an adapter for Ethernet, USB, ESATA connections.  The drive uses **TwonkyVision **software to manage the network interface while it's operating as NAS, it can be FTPed to, or HTTP transfers.

My system is an Ubuntu Desktop 11.10-32-GNOME-SHELL gdm

---

