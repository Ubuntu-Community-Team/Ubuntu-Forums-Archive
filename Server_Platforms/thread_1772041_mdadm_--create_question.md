---
title: "mdadm --create question"
date: 2011-05-31
forum: Server Platforms
---

### Post by jmg999 on 2011-05-31
Hi,

I've been having some problems w/ a my RAID 5 array, and after extensive investigation, I'm fairly sure that my last resort is rebuilding the array. I'd tried --assemble, b/c it's a previously created array, but it didn't seem to like that. So, I checked into --create, and it will re-create the array w/out destroying the data, if the superblocks are persistent, which they seem to be. However, here's what I get:

```
sudo fdisk -l
Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5745e6e0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf8844ad1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc6603c74

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x05563535

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdf: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xff2ebb89

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdg: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5be14e4a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdh: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbe4fb07e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdi: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7135fa61

   Device Boot      Start         End      Blocks   Id  System
/dev/sdi1               1      121601   976760001   fd  Linux raid autodetect

```

```
sudo mdadm --create /dev/md0 --level=5 --raid-devices=8 /dev/sd[b-i]1
mdadm: /dev/sdb1 appears to contain an ext2fs file system
    size=-1752615040K  mtime=Wed Jul 22 12:48:10 2009
mdadm: /dev/sdb1 appears to be part of a raid array:
    level=raid5 devices=8 ctime=Tue Jun 16 20:03:13 2009
mdadm: /dev/sdc1 appears to be part of a raid array:
    level=raid5 devices=8 ctime=Tue Jun 16 20:03:13 2009
mdadm: /dev/sdd1 appears to be part of a raid array:
    level=raid5 devices=8 ctime=Tue Jun 16 20:03:13 2009
mdadm: /dev/sde1 appears to be part of a raid array:
    level=raid5 devices=8 ctime=Tue Jun 16 20:03:13 2009
mdadm: /dev/sdf1 appears to be part of a raid array:
    level=raid5 devices=8 ctime=Tue Jun 16 20:03:13 2009
mdadm: /dev/sdg1 appears to be part of a raid array:
    level=raid5 devices=8 ctime=Tue Jun 16 20:03:13 2009
mdadm: /dev/sdh1 appears to be part of a raid array:
    level=raid5 devices=8 ctime=Tue Jun 16 20:03:13 2009
mdadm: /dev/sdi1 appears to contain an ext2fs file system
    size=-2021050496K  mtime=Wed Jul 22 12:48:10 2009
mdadm: /dev/sdi1 appears to be part of a raid array:
    level=raid5 devices=8 ctime=Tue Jun 16 20:03:13 2009
Continue creating array? no
mdadm: create aborted.
```

My question is: why do /dev/sdb1 and /dev/sdi1 show as *both* ext2fs and also as part of a RAID array? Any help would be greatly appreciated. Thank you.


Jeff

---

### Post by jmg999 on 2011-05-31
No one's ever seen this behavior before?

---

### Post by ruffEdgz on 2011-05-31
I have never tried re-creating a software raid so that the information on it will stay put but it does seem it can be done but I would read the man page again for 'mdadm' before moving forward. I found this variable that might interest you with this re-create:
```

--assume-clean
              Tell  mdadm  that  the  array  pre-existed  and  is  known to be clean.  It can be useful when trying to recover from a major failure as you can be sure that no data will be
              affected unless you actually write to the array.  It can also be used when creating a RAID1 or RAID10 if you want to avoid the initial resync, however this practice &#8212;  while
              normally safe &#8212; is not recommended.   Use this only if you really know what you are doing.

```
Just like if you were trying to place ext4 filesystem on a hard drive that already had ext3 configured on it, the tool is just warning you that it found array data on each of the hard drives you want to use in this creation process.

Before attempting this re-creation, I would always advise on trying to make a backup of the array if you can but best of luck with this. Update us if you decide to see if the re-creation helps you fix you problem without deleting the data on it.

---

### Post by jmg999 on 2011-06-01
Hi ruffEdgz,

Thank you for your reply. I'd read elsewhere that the --create command will keep the data intact. The reason I'd not included the --assume-clean switch is b/c, I was worried that the array would try to re-sync after being recreated. If you're interested, I'd posted some other info about this, but no one ever responded, so I did as much research as I could on my own, then re-posted.

Here's my original post...

[http://ubuntuforums.org/showthread.php?p=10838148#post10838148](http://ubuntuforums.org/showthread.php?p=10838148#post10838148)

I don't know if this will give you any other ideas, but in the meantime, I'll take another look at the mdadm man page. Again, thank you for your reply. :)


Jeff

---

