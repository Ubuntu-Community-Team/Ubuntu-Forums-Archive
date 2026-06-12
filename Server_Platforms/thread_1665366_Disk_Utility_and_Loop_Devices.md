---
title: "Disk Utility and Loop Devices"
date: 2011-01-12
forum: Server Platforms
---

### Post by Dropbear67 on 2011-01-12
Hi all.

Bit of a linux noob but im experimenting with mdadm and lvm with loop devices... have successfully played with it usuing manual commands, but wanted to try disk utility.

I created some loop devices using 

```

dd if=/dev/zero of=raid-0 bs=10240 count=10240 
cp raid-0 raid-1 
cp raid-0 raid-2 
losetup /dev/loop0 raid-0 
losetup /dev/loop1 raid-1 
losetup /dev/loop2 raid-2  

```i could successfully use mdm to create an array with

```

mdadm --create --verbose /dev/md0 -l5 -n3 /dev/loop0 /dev/loop1 /dev/loop2 

```however when I went to create an array in disk util (after wiping those loop devices and starting from scratch, repeating the creation etc) I got

```

Error creating partition: helper exited with exit code 1: In part_add_partition: device_file=/dev/loop2, start=0, size=104857600, type=0xfd
Entering MS-DOS parser (offset=0, size=104857600)
MSDOS_MAGIC found
looking at part 0 (offset 0, size 0, type 0x00)
new part entry
looking at part 1 (offset 0, size 0, type 0x00)
new part entry
looking at part 2 (offset 0, size 0, type 0x00)
new part entry
looking at part 3 (offset 0, size 0, type 0x00)
new part entry
Exiting MS-DOS parser
MSDOS partition table detected
containing partition table scheme = 0
got it
got disk
new partition
added partition start=16384 size=104841216
committed to disk
Error doing BLKPG ioctl with BLKPG_ADD_PARTITION for partition 1 of size 16384 at offset 104841216 on /dev/loop2: Invalid argument

```anything I tried in regards to partitions etc I keep getting "invalid argument" type errors with the loop devices.

Is there a problem using them with disk util?

What do I need to do after creating the loop device before I can create a raid array with them, and why do I need to do that when the madm --create command worked fine?

---

