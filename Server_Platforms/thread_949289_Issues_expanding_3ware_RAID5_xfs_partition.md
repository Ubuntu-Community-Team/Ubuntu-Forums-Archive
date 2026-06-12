---
title: "Issues expanding 3ware RAID5 xfs partition"
date: 2008-10-16
forum: Server Platforms
---

### Post by hughjay on 2008-10-16
Hello,

I currently have a 3ware 9560se running 3 500gb drives in RAID5 making it a 1TB RAID, I just added 2 more 500gb drives to the controler.  I migrated the 2 new drives into the array without an issue but it seems like parted/gparted refuses to expand the partition to the new size of 2TB.
When i try to expand the partition, gparted give me the error of:
"Partition size can not have -1 sector lengths"

Any ideas?

Hugh

---

### Post by windependence on 2008-10-16
The error message you posted is not the exact error message. Can you post the exact error message you get when you try to expand, complete with spaces, punctuation, etc? 

-Tim

---

### Post by hughjay on 2008-10-16
Heres the exact error msg I get:
"A partition cannot have a length of -1 sectors"

Heres a cfdisk output:
                         cfdisk (util-linux-ng 2.13.1)

                              Disk Drive: /dev/sda
                      Size: 1999957393408 bytes, 1999.9 GB
             Heads: 255   Sectors per Track: 63   Cylinders: 243147

    Name        Flags      Part Type  FS Type          [Label]        Size (MB)
 ------------------------------------------------------------------------------
    sda1        NC          Primary   Linux XFS                       999971.97
                            Pri/Log   Free Space                      999980.20

The other issue is that i will be crossing the 2TB barrier soon, so how would i give the partition a gpt label so i can keep it as one partition instead of carving it up?

---

### Post by tonyh6243 on 2008-10-16
I was receiving the same error message from GParted when I was initially installing my raid on the same raid card. It turn out GParted would not work. I had to use fdisk from within Ubuntu. I am  not sure how to go about merging the new space into your existing partition but it may lead you to the next step.

---

### Post by hughjay on 2008-10-16
Well, it seems like i have to delete the partition through fdisk and then recreate it with the same start sector and the new end sector according to several tutorials out there for resizing ext3 partition but would i be following the same procedure for a XFS file system? and how would i make it a "GPT" partition that can have over 2TB of space?

---

### Post by hughjay on 2008-10-21
Bump

---

### Post by hughjay on 2008-10-22
bump

---

### Post by hughjay on 2008-10-23
bump

---

### Post by hughjay on 2008-10-24
Bump

---

### Post by hughjay on 2008-10-27
bump

---

### Post by silvein on 2008-11-14
I have no idea why you're having trouble expanding the partition.  But, switching to GPT based partition map might help.  Or using parted might help.  I just tested what I'm about to tell you on one of my home machines with no ill effects, but its still kind of risky.  Make sure you have that data backed up.  Also, keep the output of the command from step 2 in a text file or something in case you need that information in an emergency.

[LIST=1]
[*] You need to unmount any filesystems on the device.  For my example, the device is */dev/sdn*.  This way when we modify the partition table, we don't have to reboot to see the changes.

```

root@salusa:~# mount */dev/sdn*1 /mnt/temp
root@salusa:~# df -h */dev/sdn*1
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdn1             187G  175M  187G   1% /mnt/temp
root@salusa:~# umount */dev/sdn1*

```

[*] We need to get the information about the current state of the partition table.  Specifically, we want the start and end sectors of the existing partition, which we will duplicate in the GPT partition table.  I did this with the following command:

```
root@salusa:~# parted */dev/sdn* unit s print
Model: ATA WDC WD2500JD-00G (scsi)
Disk /dev/sdn: 488397168s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End         Size        Type     File system  Flags
 1      **63s**    **390620474s**  390620412s  primary  xfs
```

[*] Now we need to have parted create a new partition table using GPT, and then create a new partition with the same geometry as the previous partition table, using the start and end positions from the previous command.  The -s option to parted makes it not ask for any input, so be sure you're doing this on the right device, because it will erase everything.

```
root@salusa:~# parted -s */dev/sdn* unit s mklabel gpt mkpart primary **63s** **390620474s** print
Model: ATA WDC WD2500JD-00G (scsi)
Disk /dev/sdn: 488397168s
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start  End         Size        File system  Name     Flags
 1      **63s**    **390620474s**  390620412s  xfs          primary
```

[*] Optionally, we can resize the partition to take up the rest of the free space (I specifically made the partition 200G on a 250G drive, so now we're going to make it take up the rest).  If you can still mount and read from the partition with the same geometry, its probably safe to recreate the partition to take up the rest of the space.

```
root@salusa:~# parted -s */dev/sdn* unit s rm 1 mkpart primary **63s** 100% print
Model: ATA WDC WD2500JD-00G (scsi)
Disk /dev/sdn: 488397168s
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start  End         Size        File system  Name     Flags
 1      **63s**    488397134s  488397072s  xfs          primary
```

[*] Now all thats left is to resize the filesystem, and you're set.  I'm using XFS, which has to be resized online.  If you are using ext3/2 you may have to do it offline (but I've done ext3 online, so I know its possible), using resize2fs.

```
root@salusa:~# mount */dev/sdn*1 /mnt/temp
root@salusa:~# xfs_growfs */dev/sdn*1
meta-data=/dev/sdn1              isize=256    agcount=4, agsize=12206888 blks
         =                       sectsz=512   attr=2
data     =                       bsize=4096   blocks=48827551, imaxpct=25
         =                       sunit=0      swidth=0 blks
naming   =version 2              bsize=4096  
log      =internal               bsize=4096   blocks=23841, version=2
         =                       sectsz=512   sunit=0 blks, lazy-count=0
realtime =none                   extsz=4096   blocks=0, rtextents=0
data blocks changed from 48827551 to 61049634
root@salusa:~# df -h */dev/sdn*1
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdn1             233G  175M  233G   1% /mnt/temp
root@salusa:~# umount */dev/sdn*1
```
[/LIST]

So thats it.  Nice, easy, and capable of destroying all of your data.  Aren't low level disk functions grand?

---

