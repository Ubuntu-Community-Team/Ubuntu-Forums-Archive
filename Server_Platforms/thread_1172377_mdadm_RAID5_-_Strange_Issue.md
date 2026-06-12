---
title: "mdadm RAID5 - Strange Issue"
date: 2009-05-28
forum: Server Platforms
---

### Post by uberamd on 2009-05-28
I have created a RAID5 array with an LVM on it using mdadm on my Ubuntu Server. It has 3 500GB Hard Drives (sdb, sdc, sdd). The raid contains about 50GB of data that I copied over via samba.

However, when I do a reboot the RAID array goes away. /dev/md0 will just be missing. I will run:
```
root@swiss:/dev# mdadm --detail --scan
mdadm: metadata format 00.90 unknown, ignored.

```
So, I find I need to do this on every reboot to get the RAID back. I must run fdisk /dev/sdb, delete the partition, create a new primary partition, set type as fd (RAID), write the changes, then repeat for /dev/sdc and /dev/sdd. After I do that, I can do a 
```
root@swiss:/dev# mdadm --detail --scan
mdadm: metadata format 00.90 unknown, ignored.
ARRAY /dev/md0 level=raid5 num-devices=3 metadata=00.90 UUID=2dd2df76:ce4500b3:b52fe641:3d362287
root@swiss:/dev# cd /dev/
root@swiss:/dev# ls
...
disk             lvm-raid            ram14   sdd       tty13   tty33  tty53  usbdev2.1_ep00  vcsa1
...
ecryptfs         md0                 ram2    sg0       tty15   tty35  tty55  usbdev3.1_ep00  vcsa3
...

```
See, md0 comes back, then lvm-raid on top of md0 comes back. Data and everything remains as is
```
root@swiss:/var/storage-server/storehouse# mdadm --detail /dev/md0 
mdadm: metadata format 00.90 unknown, ignored.
/dev/md0:
        Version : 00.90
  Creation Time : Wed May 27 11:06:54 2009
     Raid Level : raid5
     Array Size : 976767872 (931.52 GiB 1000.21 GB)
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Thu May 28 11:14:44 2009
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 2dd2df76:ce4500b3:b52fe641:3d362287
         Events : 0.82

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       2       8       49        2      active sync   /dev/sdd1
root@swiss:/var/storage-server/storehouse# 

```

Am I missing a critical step here? Why does md0 disappear every reboot, then I need to use fdisk to delete and recreate the partition to get /dev/sdb1 /dev/sdc1 /dev/sdd1 to show up again and work for the RAID?

Any help is appreciated.

---

### Post by fjgaude on 2009-05-28
After you do all those things do you still have the data you copied over to the array?

---

### Post by uberamd on 2009-05-28
Yes, thats the strange part. All the folders/files are there, etc.

```
root@swiss:/var/storage-server/storehouse# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/swiss-root
                       71G  748M   66G   2% /
tmpfs                 1.6G     0  1.6G   0% /lib/init/rw
varrun                1.6G  476K  1.6G   1% /var/run
varlock               1.6G     0  1.6G   0% /var/lock
udev                  1.6G  184K  1.6G   1% /dev
tmpfs                 1.6G     0  1.6G   0% /dev/shm
lrm                   1.6G  2.4M  1.6G   1% /lib/modules/2.6.28-11-server/volatile
/dev/sda5             228M   14M  202M   7% /boot
/dev/mapper/lvm--raid-lvm0
                      917G  111G  760G  13% /var/storage-server

```

But I don't get why I need to do that. Am I supposed to throw /dev/md0 in the fstab? If so, shouldn't it show up when I restart the system, just not be mounted? /dev/md0 goes away completely on reboot, so I can't even hand mount it.

---

