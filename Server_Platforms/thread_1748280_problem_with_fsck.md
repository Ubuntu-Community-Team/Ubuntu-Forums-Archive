---
title: "problem with fsck"
date: 2011-05-03
forum: Server Platforms
---

### Post by mkdigital on 2011-05-03
hi!

i got a problem when mounting a ext3 partition on a software raid:

```

mount /dev/mapper/RAID5_2TB /media/RAID5_2TB/ 
mount: wrong fs type, bad option, bad superblock on /dev/mapper/RAID5_2TB,        
missing codepage or helper program, or other error

```

i tried fsck, but it seems the superblock is corrupted:

```

e2fsck /dev/mapper/RAID5_2TB
e2fsck 1.40.8 (13-Mar-2008)
e2fsck: Group descriptors look bad... trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open /dev/mapper/RAID5_2TB

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>


```



i tried with superblock backups (mine is at 32768) but now it complains about another program opened the device

```
e2fsck -b 32768 /dev/mapper/RAID5_2TB
e2fsck 1.40.8 (13-Mar-2008)
e2fsck: Device or resource busy while trying to open /dev/mapper/RAID5_2TB
Filesystem mounted or opened exclusively by another program?


```


lsof shows no trace of another proc opeining that dev. any ideas?

---

