---
title: "NTFS Mount"
date: 2012-11-23
forum: Server Platforms
---

### Post by Gareth_2007 on 2012-11-23
Good evening,

I'm driving to mount two drives on my server following this guide [http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

the ext4 has mounted fine but the NTFS drive wont mount i get : ```
Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.
```

> fuser -m /dev/sda1
/dev/sda1:            1161


UUID=d9d5e3dd-fa2c-4a96-bd96-78b5af040942 /storage/500GB ntfs defaults 0 0

I have followed this guide before, but now i've reinstalled the os it's not playing ball.

any suggestions?

thanks

---

### Post by oldfred on 2012-11-23
Your UUID does not look like a typical NTFS, but more like a LInux partition?

NTFS does not normally have the dashes, FAT is short. 

Post this in code tags:
sudo blkid -c /dev/null -o list
sudo parted /dev/sda unit s print

---

### Post by Gareth_2007 on 2012-11-30
Sorry i took so long to reply, i've been awol.

Right it spills out -
```
device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  ext4             /              d9d5e3dd-fa2c-4a96-bd96-78b5af040942
/dev/sda2  swap             <swap>         45173a1c-a275-4f35-a088-9fb3e4caf442
/dev/sdb2  ext4             /storage/2TB   534c576a-4ef4-4a46-9131-509bcfb5dc87
/dev/sdc1  ntfs             (not mounted)  4C2C637E2C636246
/dev/sr0   iso9660 Driver   (not mounted) 
```

```
Model: ATA WDC WD5000AAVS-0 (scsi)
Disk /dev/sdc: 976773168s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End         Size        Type     File system  Flags
 1      63s    974599289s  974599227s  primary  ntfs

```

---

### Post by Gareth_2007 on 2012-11-30
Haha oooopppps my bad.... just seen the differences in the uuid. god knows where i got the other one from. all mounted ok now.

Many Thanks

---

### Post by oldfred on 2012-11-30
Sometimes it just takes another pair of eyes. I have had the same issue. :)

---

