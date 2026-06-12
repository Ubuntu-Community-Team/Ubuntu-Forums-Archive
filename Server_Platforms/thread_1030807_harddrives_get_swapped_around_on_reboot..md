---
title: "harddrives get swapped around on reboot."
date: 2009-01-04
forum: Server Platforms
---

### Post by eldaria on 2009-01-04
Hello I have an odd trouble since I installed Ubuntu Server 8.10.
I was previously running Ubuntu server 6.06.

My System has 5 Drives, and 3 of them are in a raid 5.
1 is Swap and / , and a 128MB USB flash drive for /boot

I noticed the problem after I experienced slow performance, and after some investigations I found that my Raid was degraded.
The reason was that one of the harddrives had changed from beeing sdb to sdf, and sdb did not exist.
I figured it was a fluke, and rebooted, now sdb was back but a different drive was there, and my Raid was still degraded.

After some reboots, I noticed that the drives get swapped around on each reboot.

See below:

Short Version:
```

Before reboot:
sudo fdisk -l

Disk /dev/sda: 251.0 GB, 251000193024 bytes
Disk identifier: 0x000262be

Disk /dev/sdb: 128 MB, 128974848 bytes
Disk identifier: 0x000e6d4e

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
Disk identifier: 0x0005f493

Disk /dev/sdd: 160.0 GB, 160041885696 bytes
Disk identifier: 0x00027558

Disk /dev/sde: 251.0 GB, 251000193024 bytes
Disk identifier: 0x000a2fca


Reboot 1:
sudo fdisk -l

Disk /dev/sda: 128 MB, 128974848 bytes
Disk identifier: 0x000e6d4e

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
Disk identifier: 0x0005f493

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
Disk identifier: 0x00027558

Disk /dev/sdd: 251.0 GB, 251000193024 bytes
Disk identifier: 0x000a2fca

Disk /dev/sde: 251.0 GB, 251000193024 bytes
Disk identifier: 0x000262be


Reboot 2:
sudo fdisk -l

Disk /dev/sda: 251.0 GB, 251000193024 bytes
Disk identifier: 0x000262be

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
Disk identifier: 0x00027558

Disk /dev/sdc: 251.0 GB, 251000193024 bytes
Disk identifier: 0x000a2fca

Disk /dev/sdd: 128 MB, 128974848 bytes
Disk identifier: 0x000e6d4e

Disk /dev/sde: 250.0 GB, 250059350016 bytes
Disk identifier: 0x0005f493

```


Complete version:
Before reboot:
```
sudo fdisk -l

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000262be

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30394   244139773+  fd  Linux raid autodetect

Disk /dev/sdb: 128 MB, 128974848 bytes
255 heads, 63 sectors/track, 15 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e6d4e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          16      125905+  83  Linux
Partition 1 has different physical/logical endings:
     phys=(1023, 254, 63) logical=(15, 172, 63)

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005f493

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30394   244139773+  fd  Linux raid autodetect

Disk /dev/sdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00027558

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1         486     3903763+  82  Linux swap / Solaris
/dev/sdd2             487       19457   152384557+   5  Extended
/dev/sdd5             487       19457   152384526   83  Linux

Disk /dev/sde: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a2fca

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       30394   244139773+  fd  Linux raid autodetect

```

Reboot 1:
```
sudo fdisk -l

Disk /dev/sda: 128 MB, 128974848 bytes
255 heads, 63 sectors/track, 15 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e6d4e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          16      125905+  83  Linux
Partition 1 has different physical/logical endings:
     phys=(1023, 254, 63) logical=(15, 172, 63)

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005f493

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30394   244139773+  fd  Linux raid autodetect

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00027558

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         486     3903763+  82  Linux swap / Solaris
/dev/sdc2             487       19457   152384557+   5  Extended
/dev/sdc5             487       19457   152384526   83  Linux

Disk /dev/sdd: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a2fca

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       30394   244139773+  fd  Linux raid autodetect

Disk /dev/sde: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000262be

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       30394   244139773+  fd  Linux raid autodetect

```

Reboot 2:
```
sudo fdisk -l

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000262be

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30394   244139773+  fd  Linux raid autodetect

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00027558

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         486     3903763+  82  Linux swap / Solaris
/dev/sdb2             487       19457   152384557+   5  Extended
/dev/sdb5             487       19457   152384526   83  Linux

Disk /dev/sdc: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a2fca

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30394   244139773+  fd  Linux raid autodetect

Disk /dev/sdd: 128 MB, 128974848 bytes
255 heads, 63 sectors/track, 15 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e6d4e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1          16      125905+  83  Linux
Partition 1 has different physical/logical endings:
     phys=(1023, 254, 63) logical=(15, 172, 63)

Disk /dev/sde: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005f493

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       30394   244139773+  fd  Linux raid autodetect

```

What is going on here, it makes Raid unusable, since I can't build the raid, if it is going to get re-arranged on each reboot.

How can I fix this?
Is it a bug?

---

### Post by eldaria on 2009-01-05
I have not been able to find a solution for this.
But I had an idea, not sure if it is possible.

The UUID:
In the /etc/mdadm/mdadm.conf
There is the DEVICE optiotn and the ARRAY option.
Would it be possible that I hardcode the UUID's there?
When I look at the man page it does not seem that I can use it for the DEVICE option, mbut I might have missed something.

---

### Post by fjgaude on 2009-01-05
Well, a correctly setup **mdadm** array uses the UUID it creates to know how to assemble an array at startup.

I can't say how you got into the situation you are in. Your **/etc/fstab** file should use UUIDs to mount drives, but not an md array. It should use the /dev/md[n] for that.

A simple way out of your problem is to show us your fstab file, then using **blkid** to find the UUIDs of drives. Notice that these UUIDs have nothing to do with the UUID created by mdadm for the arrays.

I wouldn't edit the mdadm.conf file. I'll let you know how to re-create a valid one after you do the above.

---

### Post by eldaria on 2009-01-05
I did not change my mdadm.conf yet, I only had a look in it. ;-)

This is my fstab I have not changed anything here eitehr, this one is created by the installation, I also created the array through the installation.

```

cat /etc/fstab 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=8cd9305e-973f-415a-a0a3-36cfcd3d12a2 /               ext3    noatime,relatime,errors=remount-ro 0       1
# /dev/sdd1
UUID=27f1e3e9-b3fb-4576-a9b0-237f4aed4a24 /boot           ext3    relatime        0       2
# /dev/md0
UUID=74cf0e48-7853-4041-bd2e-d0d43bb7622c /raid           ext3    noatime,relatime 0       2
# /dev/sda1
UUID=4e70ed07-5af9-4ce8-b2e8-8df99cf0c358 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

I succeeded in re-adding the missing drive and the Raid repaired, but after reboot, the drives are again swapped around and I loose one drive in the raid5.

---

### Post by fjgaude on 2009-01-05
Is this the UUID you get when using **blkid** on the /dev/md0 array?

UUID=74cf0e48-7853-4041-bd2e-d0d43bb7622c

What does mdadm.conf show for the UUID for the md0 array?

---

### Post by eldaria on 2009-01-05
Hmm it seems they are different?

```


blevinse@lnx1:~$ blkid /dev/md0 
/dev/md0: UUID="74cf0e48-7853-4041-bd2e-d0d43bb7622c" TYPE="ext3" SEC_TYPE="ext2" 

blevinse@lnx1:~$ cat /etc/mdadm/mdadm.conf | grep UUID
ARRAY /dev/md0 level=raid5 num-devices=3 UUID=2b487464:074515dd:08736ec8:a831aa8d


```

---

### Post by eldaria on 2009-01-05
**** Removed Duplicate post ****

---

### Post by fjgaude on 2009-01-05
> **eldaria said:**
> Hmm it seems they are different?

```


blevinse@lnx1:~$ blkid /dev/md0 
/dev/md0: UUID="74cf0e48-7853-4041-bd2e-d0d43bb7622c" TYPE="ext3" SEC_TYPE="ext2" 

blevinse@lnx1:~$ cat /etc/mdadm/mdadm.conf | grep UUID
ARRAY /dev/md0 level=raid5 num-devices=3 UUID=2b487464:074515dd:08736ec8:a831aa8d


```

Well, now we are coming to come conclusion: we have an issue, but we don't know yet what it is. <smile>

You mount the array with either /dev/md0 or UUID=74cf0e48-7853-4041-bd2e-d0d43bb7622c which is what blkid says.

The other UUID, found in mdadm.conf, is what you should get when you do this:

```
sudo mdadm -E /dev/sda1
```

You should see the UUID=2b487464:074515dd:08736ec8:a831aa8d there, and it be the same for each of the three drives you have as part of your raid5. If it isn't then we will have to work through it.

While you are at it please show this:

```
sudo mdadm -D /dev/md0
```

---

### Post by eldaria on 2009-01-05
Ok, since I posted the original fdisk print, I have rebooted so sda1 is no longer a raid disk. :-)

Anyway, here is the latest, including diags for the drives that are in the raid, I have also sunced the raid, and all 3 disks are part of the raid. I know though that if I reboot I will again have a degraded raid. :-S

Btw, thanks a lot for looking into this...

```

blevinse@lnx1:~$ sudo fdisk -l
[sudo] password for blevinse: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00027558

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         486     3903763+  82  Linux swap / Solaris
/dev/sda2             487       19457   152384557+   5  Extended
/dev/sda5             487       19457   152384526   83  Linux

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a2fca

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30394   244139773+  fd  Linux raid autodetect

Disk /dev/sdc: 128 MB, 128974848 bytes
255 heads, 63 sectors/track, 15 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e6d4e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1          16      125905+  83  Linux
Partition 1 has different physical/logical endings:
     phys=(1023, 254, 63) logical=(15, 172, 63)

Disk /dev/sde: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000262be

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       30394   244139773+  fd  Linux raid autodetect

Disk /dev/sdf: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005f493

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1       30394   244139773+  fd  Linux raid autodetect

blevinse@lnx1:~$ sudo mdadm -E /dev/sdb1
/dev/sdb1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 2b487464:074515dd:08736ec8:a831aa8d
  Creation Time : Thu Jan  1 13:11:12 2009
     Raid Level : raid5
  Used Dev Size : 244139648 (232.83 GiB 250.00 GB)
     Array Size : 488279296 (465.66 GiB 500.00 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0

    Update Time : Mon Jan  5 21:12:38 2009
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 2dab579a - correct
         Events : 70

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     2       8       17        2      active sync   /dev/sdb1

   0     0       8       81        0      active sync   /dev/sdf1
   1     1       8       65        1      active sync   /dev/sde1
   2     2       8       17        2      active sync   /dev/sdb1

blevinse@lnx1:~$ sudo mdadm -E /dev/sde1
/dev/sde1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 2b487464:074515dd:08736ec8:a831aa8d
  Creation Time : Thu Jan  1 13:11:12 2009
     Raid Level : raid5
  Used Dev Size : 244139648 (232.83 GiB 250.00 GB)
     Array Size : 488279296 (465.66 GiB 500.00 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0

    Update Time : Mon Jan  5 21:12:38 2009
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 2dab57c8 - correct
         Events : 70

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       65        1      active sync   /dev/sde1

   0     0       8       81        0      active sync   /dev/sdf1
   1     1       8       65        1      active sync   /dev/sde1
   2     2       8       17        2      active sync   /dev/sdb1

blevinse@lnx1:~$ sudo mdadm -E /dev/sdf1
/dev/sdf1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 2b487464:074515dd:08736ec8:a831aa8d
  Creation Time : Thu Jan  1 13:11:12 2009
     Raid Level : raid5
  Used Dev Size : 244139648 (232.83 GiB 250.00 GB)
     Array Size : 488279296 (465.66 GiB 500.00 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0

    Update Time : Mon Jan  5 21:12:38 2009
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 2dab57d6 - correct
         Events : 70

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8       81        0      active sync   /dev/sdf1

   0     0       8       81        0      active sync   /dev/sdf1
   1     1       8       65        1      active sync   /dev/sde1
   2     2       8       17        2      active sync   /dev/sdb1

blevinse@lnx1:~$ sudo mdadm -D /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Thu Jan  1 13:11:12 2009
     Raid Level : raid5
     Array Size : 488279296 (465.66 GiB 500.00 GB)
  Used Dev Size : 244139648 (232.83 GiB 250.00 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Mon Jan  5 21:12:38 2009
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 2b487464:074515dd:08736ec8:a831aa8d
         Events : 0.70

    Number   Major   Minor   RaidDevice State
       0       8       81        0      active sync   /dev/sdf1
       1       8       65        1      active sync   /dev/sde1
       2       8       17        2      active sync   /dev/sdb1


```

---

### Post by fjgaude on 2009-01-05
All that looks just fine... do you have your BIOS pointing to the /sda or /sdc? The /sda doesn't show that it is bootable in fdisk listing. The /sda is your boot drive, eh?

I notice that the "*" in fdisk has shifted from sda, sdc to sdd. Strange!

You have taken the /sda1 out of the raid array?

Let me say that an mdadm raid array doesn't depend on the drive names, but only on the UUID it has given to the array at --create time.

Think about what is going on and you likely will figure it all out.

---

### Post by eldaria on 2009-01-05
I did not change anything.

The boot drive is a 128Mb USB stick I use, only for booting.
That one also changes "position" on every reboot.
But it is always the one it is booting from, there is no boot files on any other drive.

In the last listing, it is listed as sdc.

I did not take any drives out of the array, But on each reboot I loose 1 drive, and have to manually add it again, and resync.
I'm just happy I went for a Raid5, instead of Raid 0, as I was first planning.

But what casues the drive to be thrown out all the time?
Or that the drives get swapped around all the time?

---

### Post by fjgaude on 2009-01-05
Drives get renamed by Linux when anything is added or substracted from the last time a boot was made.

Since all but the arrays use UUIDs to mount it doesn't matter if names change.

Is the BIOS pointing to the correct boot partition, drive? It seems that the array doesn't like one or more of the drives... could be a flakey drive, but I can't say.

From what I know the kernel **md** thinks something is wrong with at least one of the drives in the array as it tries to assemble from the UUID.

After a re-sync is fully complete, **umount** the array and see what a **fsck** has to say about the array.

**Do not run such a check on a busy or mounted array.**

Something is strange here and can't say what it is with what you give me.

---

### Post by cariboo on 2009-01-06
Use uuid in grub too, so that it doesn't matter what the device_label is eg:

```
title		Ubuntu jaunty (development branch), kernel 2.6.28-4-generic
uuid		c6afffda-4b72-454e-8bfb-29d122e3cc3e
kernel		/boot/vmlinuz-2.6.28-4-generic root=UUID=c6afffda-4b72-454e-8bfb-29d122e3cc3e ro quiet splash 
initrd		/boot/initrd.img-2.6.28-4-generic
quiet
```

It seems once I started using uuid the device order doesn't change any more.

Jim

---

