---
title: "Format a new disk"
date: 2017-12-12
forum: Server Platforms
---

### Post by sed_faster on 2017-12-12
Hello folks,

I have some problems with a new disk. I have a environment ubuntu server installed on intel machine. I intend add a new sata disk and to this task a use fdisk, to create/configuration a new partition in the disk, and finally use mkfs to format the new partition as ext4.
Here is an example of which commands I followed:
```

$ sudo fdisk -l
$ df -kh
$ sudo fdisk /dev/sdc # here I intend create a new partiton

Command (m for help): n
Partition type
   p   primary (0 primary, 0 extended, 4 free)
   e   extended (container for logical partitions)
Select (default p): p
Partition number (1-4, default 1): 1
First sector (2048-1953525167, default 2048): 
Last sector, +sectors or +size{K,M,G,T,P} (2048-1953525167, default 1953525167): 

Created a new partition 1 of type 'Linux' and of size 931.5 GiB.

Command (m for help): p
Disk /dev/sdc: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: esfrgfdhtht

Device     Boot Start        End    Sectors   Size Id Type
/dev/sdc1        5048 45436654654654 546456765765767 5031.5G 83 Linux

Command (m for help): w
The partition table has been altered.
Calling ioctl() to re-read partition table.
Syncing disks.


$ sudo blkid /dev/sdb1

$ sudo mkfs -c -t ext4 /dev/sdc1 OR $ sudo mkfs -t ext4 /dev/sdc1 (as disk is new I prefer this last method)

```

I did this script on two disk and both were damaged. I was able to initialize the disk but after some days or a third reboot, the system could never see the disks again. I ran the tools seagate and discovery the disk is damaged. Here is an example of the erros: [https://snag.gy/8iGuzA.jpg](https://snag.gy/8iGuzA.jpg)
My question is: Am I doing these tasks well?

Thanks

---

### Post by howefield on 2017-12-12
Thread moved to the "*Server Platforms*" forum.

---

### Post by darkod on 2017-12-12
I stopped using fdisk a while ago. I find parted much better and it serves for what I need.

But fdisk shouldn't damage the disks anyway, it's weird if it is really related to fdisk.

Try using parted, use MiB as a unit and I usually leave 10-15MiB unused at the end. Don't create the partition until last sector like fdisk suggested, even though that shouldn't be a problem...

Then you can use mkfs.ext4 to format it (it's the same as 'mkfs -t ext4').

---

### Post by ian-weisser on 2017-12-12
Looks like a hardware issue that fdisk cannot cause.
Coincidence.
Run a SMART test.

---

### Post by QIII on 2017-12-12
Hello!

What us the model of the Seagate disks, the firmware and the date of manufacture?

Which release of Ubuntu are you using?

---

