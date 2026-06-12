---
title: "Mount synology linux raid"
date: 2019-04-27
forum: Server Platforms
---

### Post by osharko on 2019-04-27
Hi,
i made a linux raid with 2HDD on my Synology 6.x version, a lot of mounts ago (it should be a brtfs raid).
I tried to mount the raid but without success. Here some examples:

> mdadm --assemble --run /dev/md0 /dev/sde1
mdadm --add /dev/md0 /dev/sdd1
mdadm --assemble md0
                   or
> mdadm --assemble --scan --verbose

or other version of these mount founded on the web, but the raid was never mounted.
What is the correct way to mount these Hdds? 
Thank you

---

### Post by darkod on 2019-04-27
I don't think btrfs is mdadm raid. Anyway, you can check first if the disks have mdadm superblock on them. If the partition are sdd1 and sde1 you can check that with:
```
sudo mdadm -E /dev/sd[de]1
```

That will show you mdadm superblock info if there is any, or will show you a message that no mdadm superblock exists.

---

### Post by osharko on 2019-04-27
Hi, thank you for quick replying and sorry for the late.
I ran the command for bot the hdd, and this is the result:

> root@ubuntu:/dev# mdadm -E /dev/sd[bc]1
/dev/sdb1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0xa
     Array UUID : 74706b4c:45abb1c1:5c98ecb2:4539eaf0
           Name : ubuntu:0  (local to host ubuntu)
  Creation Time : Sat Apr 27 16:43:56 2019
     Raid Level : raid1
   Raid Devices : 2

 Avail Dev Size : 4974336 (2.37 GiB 2.55 GB)
     Array Size : 2487168 (2.37 GiB 2.55 GB)
    Data Offset : 6144 sectors
   Super Offset : 8 sectors
Recovery Offset : 175744 sectors
   Unused Space : before=6064 sectors, after=0 sectors
          State : clean
    Device UUID : c679ce69:b50a3ce5:878fe06e:c9b2dfea

    Update Time : Sat Apr 27 20:58:58 2019
  Bad Block Log : 512 entries available at offset 16 sectors - bad blocks present.
       Checksum : 5cc6b9d7 - correct
         Events : 64


   Device Role : Active device 0
   Array State : AA ('A' == active, '.' == missing, 'R' == replacing)
mdadm: No md superblock detected on /dev/sdc1.


I not remember very well, but even if they are a linux raid, the was not  in raid 1, so it was a single hdd raid (I made this to ensure that on  one hdd fail, i will lose everything, and it was a suggested way from  synology)

---

### Post by osharko on 2019-04-27
I not remember very well, but even if they are a linux raid, the was not in raid 1, so it was a single hdd raid (I made this to ensure that on one hdd fail, i will lose everything, and it was a suggested way from synology)

---

### Post by darkod on 2019-04-27
I don't think sdb1 was part of any big data raid. The size is only 2.5GB. Looks more like small linux OS partition size.

And sdc1 has no mdadm superblock.

Are you sure you are working with the correct partitions? You can use blkid to see all partitions and UUID on them.
```
sudo blkid
```

---

### Post by osharko on 2019-04-27
The very big partition is on sd[bc]3, should I use that partition?

---

### Post by osharko on 2019-04-27
Here is the response on the partition 3:

> root@ubuntu:~# sudo mdadm -E /dev/sd[ac]3
/dev/sda3:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x9
     Array UUID : dc554429:61f95817:00b1c8e8:550ac45a
           Name : ubuntu:3  (local to host ubuntu)
  Creation Time : Sat Apr 27 16:48:49 2019
     Raid Level : raid1
   Raid Devices : 2

 Avail Dev Size : 5850626976 (2789.80 GiB 2995.52 GB)
     Array Size : 2925313472 (2789.80 GiB 2995.52 GB)
  Used Dev Size : 5850626944 (2789.80 GiB 2995.52 GB)
    Data Offset : 264192 sectors
   Super Offset : 8 sectors
   Unused Space : before=264112 sectors, after=32 sectors
          State : clean
    Device UUID : 7806d334:28fd5555:e8db742d:643de050

Internal Bitmap : 8 sectors from superblock
    Update Time : Sat Apr 27 21:02:25 2019
  Bad Block Log : 512 entries available at offset 24 sectors - bad blocks present.
       Checksum : 4a8d999e - correct
         Events : 14


   Device Role : Active device 1
   Array State : .A ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdc3:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0xb
     Array UUID : dc554429:61f95817:00b1c8e8:550ac45a
           Name : ubuntu:3  (local to host ubuntu)
  Creation Time : Sat Apr 27 16:48:49 2019
     Raid Level : raid1
   Raid Devices : 2

 Avail Dev Size : 5850626976 (2789.80 GiB 2995.52 GB)
     Array Size : 2925313472 (2789.80 GiB 2995.52 GB)
  Used Dev Size : 5850626944 (2789.80 GiB 2995.52 GB)
    Data Offset : 264192 sectors
   Super Offset : 8 sectors
Recovery Offset : 30848 sectors
   Unused Space : before=264112 sectors, after=32 sectors
          State : clean
    Device UUID : 64bb8974:2723dc51:e4a178cf:5488d957

Internal Bitmap : 8 sectors from superblock
    Update Time : Sat Apr 27 21:00:11 2019
  Bad Block Log : 512 entries available at offset 24 sectors - bad blocks present.
       Checksum : 2fc6fd77 - correct
         Events : 8


   Device Role : Active device 0
   Array State : AA ('A' == active, '.' == missing, 'R' == replacing)


---

### Post by osharko on 2019-04-28
This is the output:
> 
root@ubuntu:~# blkid
/dev/nvme0n1p1: LABEL="Ripristino" UUID="D0D6360AD635F178" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="6e2be379-9516-4efa-9104-4a4297410d2b"
/dev/nvme0n1p2: UUID="3C38-83DB" TYPE="vfat" PARTLABEL="EFI system partition" PARTUUID="b8333973-35fc-4274-964f-0018a0017fcb"
/dev/nvme0n1p4: LABEL="Windows10" UUID="54FA4311FA42EEB4" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="91e9bd7c-45be-47dc-815c-6d3b70f918d4"
/dev/sda1: LABEL="ESD-USB" UUID="E63B-C7C2" TYPE="vfat" PARTUUID="706b518a-01"
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/loop6: TYPE="squashfs"
/dev/loop7: TYPE="squashfs"
[B]/dev/sdb1: UUID="50f0847d-7c85-2b91-3017-a5a8c86610be" TYPE="linux_raid_member" PARTUUID="d8a44077-a81b-4122-962c-c50967b10f44"
/dev/sdb2: UUID="264b9bee-8692-c1f7-3017-a5a8c86610be" TYPE="linux_raid_member" PARTUUID="7404715f-355d-4e0b-9c0d-a74ac23d08e4"
/dev/sdb3: UUID="dc554429-61f9-5817-00b1-c8e8550ac45a" UUID_SUB="7806d334-28fd-5555-e8db-742d643de050" LABEL="ubuntu:3" TYPE="linux_raid_member" PARTUUID="e75413c3-c0f9-4a0d-b49d-3f82f8d528bf"
/dev/sdc1: UUID="7312ae57-c799-d75c-3017-a5a8c86610be" TYPE="linux_raid_member" PARTUUID="a9e08f31-faea-48b0-b901-4023136f88e9"
/dev/sdc2: UUID="e02c0d49-db61-ee43-da6e-9d2068bac86e" TYPE="linux_raid_member" PARTUUID="2f49f4cb-f308-4cc1-9881-d02a777a0089"
/dev/sdc3: UUID="2cc834ef-7c91-db5a-0b99-38d23dda92a8" UUID_SUB="977c5ddf-a372-57fb-8508-23fa7043303f" LABEL="ubuntu:3" TYPE="linux_raid_member" PARTUUID="9ccec435-2443-4229-b431-2d14b3328b67"[/B]
/dev/nvme0n1: PTUUID="af5ff68c-2b3a-417d-b0b8-53d5e7ce5e21" PTTYPE="gpt"
/dev/nvme0n1p3: PARTLABEL="Microsoft reserved partition" PARTUUID="57041858-112d-44b2-8030-6f0822ba8f7b"



---

### Post by darkod on 2019-04-28
Are you posting the results from the same boot? If not, please do so, otherwise drive letters might change after reboot.

In your mdadm -E output it is sda3 with the big raid partition, but in your blkid output sda is a usb stick, not a HDD. Also, in blkid sdc3 does not seem to have the correct array UUID. It should be the same as sdb3.

Looking at mdadm -E both sda3 and sdc3 show same array UUID value, but blkid doesn't support that.

Anyway you should be able to force assemble the raid1 but I can't give you precise commands because your drive letters keep changing around.

---

### Post by osharko on 2019-04-28
Hi, yes they are from different boot.
Here the command executed on the same boot:

> ubuntu@ubuntu:~$ sudo mdadm -E /dev/sd[bc]3
/dev/sdb3:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 2cc834ef:7c91db5a:0b9938d2:3dda92a8
           Name : ubuntu:3  (local to host ubuntu)
  Creation Time : Sun Apr 28 00:03:57 2019
     Raid Level : raid1
   Raid Devices : 2

 Avail Dev Size : 5850626976 (2789.80 GiB 2995.52 GB)
     Array Size : 2925313472 (2789.80 GiB 2995.52 GB)
  Used Dev Size : 5850626944 (2789.80 GiB 2995.52 GB)
    Data Offset : 264192 sectors
   Super Offset : 8 sectors
   Unused Space : before=264112 sectors, after=32 sectors
          State : clean
    Device UUID : 977c5ddf:a37257fb:850823fa:7043303f

Internal Bitmap : 8 sectors from superblock
    Update Time : Sun Apr 28 00:03:57 2019
  Bad Block Log : 512 entries available at offset 24 sectors
       Checksum : 96ca0ab5 - correct
         Events : 0


   Device Role : Active device 1
   Array State : .A ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdc3:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x9
     Array UUID : dc554429:61f95817:00b1c8e8:550ac45a
           Name : ubuntu:3  (local to host ubuntu)
  Creation Time : Sat Apr 27 16:48:49 2019
     Raid Level : raid1
   Raid Devices : 2

 Avail Dev Size : 5850626976 (2789.80 GiB 2995.52 GB)
     Array Size : 2925313472 (2789.80 GiB 2995.52 GB)
  Used Dev Size : 5850626944 (2789.80 GiB 2995.52 GB)
    Data Offset : 264192 sectors
   Super Offset : 8 sectors
   Unused Space : before=264112 sectors, after=32 sectors
          State : clean
    Device UUID : 7806d334:28fd5555:e8db742d:643de050

Internal Bitmap : 8 sectors from superblock
    Update Time : Sat Apr 27 23:52:57 2019
  Bad Block Log : 512 entries available at offset 24 sectors - bad blocks present.
       Checksum : 4a8dc1b0 - correct
         Events : 40


   Device Role : Active device 1
   Array State : .A ('A' == active, '.' == missing, 'R' == replacing)
ubuntu@ubuntu:~$ blkid
/dev/nvme0n1p1: LABEL="Ripristino" UUID="D0D6360AD635F178" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="6e2be379-9516-4efa-9104-4a4297410d2b"
/dev/nvme0n1p2: UUID="3C38-83DB" TYPE="vfat" PARTLABEL="EFI system partition" PARTUUID="b8333973-35fc-4274-964f-0018a0017fcb"
/dev/nvme0n1p4: LABEL="Windows10" UUID="54FA4311FA42EEB4" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="91e9bd7c-45be-47dc-815c-6d3b70f918d4"
/dev/sda1: LABEL="ESD-USB" UUID="E63B-C7C2" TYPE="vfat" PARTUUID="706b518a-01"
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/loop6: TYPE="squashfs"
/dev/loop7: TYPE="squashfs"
/dev/sdb1: UUID="7312ae57-c799-d75c-3017-a5a8c86610be" TYPE="linux_raid_member" PARTUUID="a9e08f31-faea-48b0-b901-4023136f88e9"
/dev/sdb2: UUID="e02c0d49-db61-ee43-da6e-9d2068bac86e" TYPE="linux_raid_member" PARTUUID="2f49f4cb-f308-4cc1-9881-d02a777a0089"
/dev/sdb3: UUID="2cc834ef-7c91-db5a-0b99-38d23dda92a8" UUID_SUB="977c5ddf-a372-57fb-8508-23fa7043303f" LABEL="ubuntu:3" TYPE="linux_raid_member" PARTUUID="9ccec435-2443-4229-b431-2d14b3328b67"
/dev/sdc1: UUID="50f0847d-7c85-2b91-3017-a5a8c86610be" TYPE="linux_raid_member" PARTUUID="d8a44077-a81b-4122-962c-c50967b10f44"
/dev/sdc2: UUID="264b9bee-8692-c1f7-3017-a5a8c86610be" TYPE="linux_raid_member" PARTUUID="7404715f-355d-4e0b-9c0d-a74ac23d08e4"
/dev/sdc3: UUID="dc554429-61f9-5817-00b1-c8e8550ac45a" UUID_SUB="7806d334-28fd-5555-e8db-742d643de050" LABEL="ubuntu:3" TYPE="linux_raid_member" PARTUUID="e75413c3-c0f9-4a0d-b49d-3f82f8d528bf"

These are photos from gparted:
[[IMG]https://i.ibb.co/nDN0f3F/sdb.png[/IMG]]("https://ibb.co/Jzwd2x9")
[[IMG]https://i.ibb.co/BP09KpB/sdc.png[/IMG]]("https://ibb.co/W3mLphf")




And this is the result of an assemble try:
> root@ubuntu:/dev# mdadm --assemble --run /dev/md0 /dev/sd[bc]3
mdadm: superblock on /dev/sdc3 doesn't match others - assembly aborted
root@ubuntu:/dev# mdadm --assemble --run /dev/md0 /dev/sdb3
mdadm: /dev/md0 has been started with 1 drive (out of 2).
root@ubuntu:/dev# mdadm --add /dev/md0 /dev/sdc3 
mdadm: added /dev/sdc3
root@ubuntu:/dev# mdadm --assemble /dev/md0
mdadm: Fail create md0 when using /sys/module/md_mod/parameters/new_array
mdadm: /dev/md0 is already in use.
root@ubuntu:/dev# sudo mdadm -E /dev/sd[bc]3
/dev/sdb3:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x9
     Array UUID : 2cc834ef:7c91db5a:0b9938d2:3dda92a8
           Name : ubuntu:3  (local to host ubuntu)
  Creation Time : Sun Apr 28 00:03:57 2019
     Raid Level : raid1
   Raid Devices : 2

 Avail Dev Size : 5850626976 (2789.80 GiB 2995.52 GB)
     Array Size : 2925313472 (2789.80 GiB 2995.52 GB)
  Used Dev Size : 5850626944 (2789.80 GiB 2995.52 GB)
    Data Offset : 264192 sectors
   Super Offset : 8 sectors
   Unused Space : before=264112 sectors, after=32 sectors
          State : clean
    Device UUID : 977c5ddf:a37257fb:850823fa:7043303f

Internal Bitmap : 8 sectors from superblock
    Update Time : Sun Apr 28 12:28:41 2019
  Bad Block Log : 512 entries available at offset 24 sectors - bad blocks present.
       Checksum : 96c9b94d - correct
         Events : 3


   Device Role : Active device 1
   Array State : AA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdc3:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0xb
     Array UUID : 2cc834ef:7c91db5a:0b9938d2:3dda92a8
           Name : ubuntu:3  (local to host ubuntu)
  Creation Time : Sun Apr 28 00:03:57 2019
     Raid Level : raid1
   Raid Devices : 2

 Avail Dev Size : 5850626976 (2789.80 GiB 2995.52 GB)
     Array Size : 2925313472 (2789.80 GiB 2995.52 GB)
  Used Dev Size : 5850626944 (2789.80 GiB 2995.52 GB)
    Data Offset : 264192 sectors
   Super Offset : 8 sectors
Recovery Offset : 0 sectors
   Unused Space : before=264112 sectors, after=32 sectors
          State : clean
    Device UUID : 3f5cc0a4:5dda9424:0de380c1:1c48cd5c

Internal Bitmap : 8 sectors from superblock
    Update Time : Sun Apr 28 12:28:41 2019
  Bad Block Log : 512 entries available at offset 24 sectors - bad blocks present.
       Checksum : 6a64dfe5 - correct
         Events : 3


   Device Role : Active device 0
   Array State : AA ('A' == active, '.' == missing, 'R' == replacing)



[[img]https://i.ibb.co/DtqFR69/md0.png[/img]](https://ibb.co/PNSy6bc)
[[img]https://i.ibb.co/HXntvjT/sdb3.png[/img]](https://ibb.co/rv4xPV2)
[[img]https://i.ibb.co/y6GFKgd/sdc3.png[/img]](https://ibb.co/K2RxBVb)

---

### Post by darkod on 2019-04-28
You have md0 started now as raid1 array. When you mount it, does it have the data you expect to find?

sdb3 and sdc3 had different array UUIDs. You chose to assemble the new array with sdb3.

---

### Post by osharko on 2019-04-28
How do i mount? When i try, i fail with this error
> root@ubuntu:/dev# mkdir /mnt/raid
root@ubuntu:/dev# sudo mount /dev/md0 /mnt/raid/
mount: /mnt/raid: wrong fs type, bad option, bad superblock on /dev/md0, missing codepage or helper program, or other error.

Are you sure is mounted with sdb3? from gparted i see that sd[bc]3 are mounted into /dev/md0

---

### Post by darkod on 2019-04-28
/dev/md0 is the array device assembled from sdb3 and sdc3. After that usually the filesystem is on md0 so you need to mount it to read it. How you mount it would depend which filesystem it had, or if you assembled it from the correct device (sdb3). Maybe it was sdc3, don't forget at the start they had different array UUIDs.

And if you are running commands as root you don't need to use sudo in front. Leave it out.

PS. You need to check now if there is recognizable filesystem on md0.

---

### Post by osharko on 2019-04-28
How do i check the fs and eventually mount it?

---

### Post by osharko on 2019-04-28
After a Reboot I made this:

> root@ubuntu:/dev# mdadm --assemble --scan --verbose
mdadm: looking for devices for /dev/md/0
mdadm: /dev/sdc3 has wrong uuid.
mdadm: No super block found on /dev/sdc2 (Expected magic a92b4efc, got 00000000)
mdadm: no RAID superblock on /dev/sdc2
mdadm: No super block found on /dev/sdc (Expected magic a92b4efc, got 00000000)
mdadm: no RAID superblock on /dev/sdc
mdadm: No super block found on /dev/sdb1 (Expected magic a92b4efc, got 00000000)
mdadm: no RAID superblock on /dev/sdb1
mdadm: No super block found on /dev/sdb (Expected magic a92b4efc, got 00000000)
mdadm: no RAID superblock on /dev/sdb
mdadm: /dev/sda3 has wrong uuid.
mdadm: No super block found on /dev/sda2 (Expected magic a92b4efc, got 00000000)
mdadm: no RAID superblock on /dev/sda2
mdadm: Cannot read superblock on /dev/sda1
mdadm: no RAID superblock on /dev/sda1
mdadm: No super block found on /dev/sda (Expected magic a92b4efc, got 00000000)
mdadm: no RAID superblock on /dev/sda
mdadm: No super block found on /dev/nvme0n1p4 (Expected magic a92b4efc, got 0fc02366)
mdadm: no RAID superblock on /dev/nvme0n1p4
mdadm: No super block found on /dev/nvme0n1p3 (Expected magic a92b4efc, got 00000000)
mdadm: no RAID superblock on /dev/nvme0n1p3
mdadm: No super block found on /dev/nvme0n1p2 (Expected magic a92b4efc, got 00000000)
mdadm: no RAID superblock on /dev/nvme0n1p2
mdadm: No super block found on /dev/nvme0n1p1 (Expected magic a92b4efc, got 0fc02366)
mdadm: no RAID superblock on /dev/nvme0n1p1
mdadm: No super block found on /dev/nvme0n1 (Expected magic a92b4efc, got 00000000)
mdadm: no RAID superblock on /dev/nvme0n1
mdadm: No super block found on /dev/loop7 (Expected magic a92b4efc, got d08a0895)
mdadm: no RAID superblock on /dev/loop7
mdadm: No super block found on /dev/loop6 (Expected magic a92b4efc, got de4868bf)
mdadm: no RAID superblock on /dev/loop6
mdadm: No super block found on /dev/loop5 (Expected magic a92b4efc, got f22ae586)
mdadm: no RAID superblock on /dev/loop5
mdadm: No super block found on /dev/loop4 (Expected magic a92b4efc, got de4868bf)
mdadm: no RAID superblock on /dev/loop4
mdadm: No super block found on /dev/loop3 (Expected magic a92b4efc, got de4868bf)
mdadm: no RAID superblock on /dev/loop3
mdadm: No super block found on /dev/loop2 (Expected magic a92b4efc, got 1bd7e597)
mdadm: no RAID superblock on /dev/loop2
mdadm: No super block found on /dev/loop1 (Expected magic a92b4efc, got fd6d4056)
mdadm: no RAID superblock on /dev/loop1
mdadm: No super block found on /dev/loop0 (Expected magic a92b4efc, got e02b1df3)
mdadm: no RAID superblock on /dev/loop0
mdadm: /dev/sdc1 is identified as a member of /dev/md/0, slot 0.
mdadm: no uptodate device for slot 1 of /dev/md/0
mdadm: added /dev/sdc1 to /dev/md/0 as 0
mdadm: /dev/md/0 assembled from 0 drives and 1 rebuilding - not enough to start the array.
mdadm: looking for devices for /dev/md/3
mdadm: No super block found on /dev/sdc2 (Expected magic a92b4efc, got 00000000)
mdadm: no RAID superblock on /dev/sdc2
mdadm: /dev/sdc1 has wrong uuid.
mdadm: No super block found on /dev/sdc (Expected magic a92b4efc, got 00000000)
mdadm: no RAID superblock on /dev/sdc
mdadm: No super block found on /dev/sdb1 (Expected magic a92b4efc, got 00000000)
mdadm: no RAID superblock on /dev/sdb1
mdadm: No super block found on /dev/sdb (Expected magic a92b4efc, got 00000000)
mdadm: no RAID superblock on /dev/sdb
mdadm: No super block found on /dev/sda2 (Expected magic a92b4efc, got 00000000)
mdadm: no RAID superblock on /dev/sda2
mdadm: Cannot read superblock on /dev/sda1
mdadm: no RAID superblock on /dev/sda1
mdadm: No super block found on /dev/sda (Expected magic a92b4efc, got 00000000)
mdadm: no RAID superblock on /dev/sda
mdadm: No super block found on /dev/nvme0n1p4 (Expected magic a92b4efc, got 0fc02366)
mdadm: no RAID superblock on /dev/nvme0n1p4
mdadm: No super block found on /dev/nvme0n1p3 (Expected magic a92b4efc, got 00000000)
mdadm: no RAID superblock on /dev/nvme0n1p3
mdadm: No super block found on /dev/nvme0n1p2 (Expected magic a92b4efc, got 00000000)
mdadm: no RAID superblock on /dev/nvme0n1p2
mdadm: No super block found on /dev/nvme0n1p1 (Expected magic a92b4efc, got 0fc02366)
mdadm: no RAID superblock on /dev/nvme0n1p1
mdadm: No super block found on /dev/nvme0n1 (Expected magic a92b4efc, got 00000000)
mdadm: no RAID superblock on /dev/nvme0n1
mdadm: No super block found on /dev/loop7 (Expected magic a92b4efc, got d08a0895)
mdadm: no RAID superblock on /dev/loop7
mdadm: No super block found on /dev/loop6 (Expected magic a92b4efc, got de4868bf)
mdadm: no RAID superblock on /dev/loop6
mdadm: No super block found on /dev/loop5 (Expected magic a92b4efc, got f22ae586)
mdadm: no RAID superblock on /dev/loop5
mdadm: No super block found on /dev/loop4 (Expected magic a92b4efc, got de4868bf)
mdadm: no RAID superblock on /dev/loop4
mdadm: No super block found on /dev/loop3 (Expected magic a92b4efc, got de4868bf)
mdadm: no RAID superblock on /dev/loop3
mdadm: No super block found on /dev/loop2 (Expected magic a92b4efc, got 1bd7e597)
mdadm: no RAID superblock on /dev/loop2
mdadm: No super block found on /dev/loop1 (Expected magic a92b4efc, got fd6d4056)
mdadm: no RAID superblock on /dev/loop1
mdadm: No super block found on /dev/loop0 (Expected magic a92b4efc, got e02b1df3)
mdadm: no RAID superblock on /dev/loop0
mdadm: /dev/sdc3 is identified as a member of /dev/md/3, slot 0.
mdadm: /dev/sda3 is identified as a member of /dev/md/3, slot 1.
mdadm: added /dev/sda3 to /dev/md/3 as 1
mdadm: added /dev/sdc3 to /dev/md/3 as 0
mdadm: /dev/md/3 has been started with 1 drive (out of 2) and 1 rebuilding.
mdadm: timeout waiting for /dev/md/3
mdadm: looking for devices for /dev/md/0
Segmentation fault (core dumped)
root@ubuntu:/dev# clear

root@ubuntu:/dev# lsblk -f
NAME        FSTYPE            LABEL      UUID                                 MOUNTPOINT
loop0       squashfs                                                          /rofs
loop1       squashfs                                                          /snap/core/5662
loop2       squashfs                                                          /snap/gnome-3-26-1604/70
loop3       squashfs                                                          /snap/gnome-calculator/238
loop4       squashfs                                                          /snap/gnome-characters/124
loop5       squashfs                                                          /snap/gnome-logs/45
loop6       squashfs                                                          /snap/gnome-system-monitor/57
loop7       squashfs                                                          /snap/gtk-common-themes/701
sda                                                                           
&#9500;&#9472;sda1      linux_raid_member            7312ae57-c799-d75c-3017-a5a8c86610be 
&#9500;&#9472;sda2      linux_raid_member            e02c0d49-db61-ee43-da6e-9d2068bac86e [SWAP]
[SIZE=3]&#9492;&#9472;sda3      linux_raid_member ubuntu:3   2cc834ef-7c91-db5a-0b99-38d23dda92a8 [/SIZE]
  &#9492;&#9472;md3                                                                       
sdb                                                                           
&#9492;&#9472;sdb1      vfat              ESD-USB    E63B-C7C2                            /cdrom
sdc                                                                           
&#9500;&#9472;sdc1      linux_raid_member            50f0847d-7c85-2b91-3017-a5a8c86610be 
&#9474; &#9492;&#9472;md0                                                                       
&#9500;&#9472;sdc2      linux_raid_member            264b9bee-8692-c1f7-3017-a5a8c86610be [SWAP]
[SIZE=3]&#9492;&#9472;sdc3      linux_raid_member ubuntu:3   2cc834ef-7c91-db5a-0b99-38d23dda92a8 [/SIZE]
  &#9492;&#9472;md3                                                                       
nvme0n1                                                                       
&#9500;&#9472;nvme0n1p1 ntfs              Ripristino D0D6360AD635F178                     
&#9500;&#9472;nvme0n1p2 vfat                         3C38-83DB                            
&#9500;&#9472;nvme0n1p3                                                                   
&#9492;&#9472;nvme0n1p4 ntfs              Windows10  54FA4311FA42EEB4                




As you can see, the sd[ac]3 that are mounted has the same guid. That means that they are part of the same array, right?

---

### Post by osharko on 2019-04-28
Btw, as I can see there are two disks in the raid with a main and a secondary. I tried to mount them alone, without mount connect the other hard drive too. That is the result:

Disk 0 (Main) ->
> Disk 0:
root@ubuntu:/dev# mdadm --assemble --run /dev/md123 /dev/sde3
mdadm: /dev/md123 has been started with 1 drive (out of 2).
root@ubuntu:/dev# lsblk -f
NAME        FSTYPE            LABEL      UUID                                 MOUNTPOINT
loop0       squashfs                                                          /rofs
loop1       squashfs                                                          /snap/core/5662
loop2       squashfs                                                          /snap/gnome-3-26-1604/70
loop3       squashfs                                                          /snap/gnome-calculator/238
loop4       squashfs                                                          /snap/gnome-characters/124
loop5       squashfs                                                          /snap/gnome-logs/45
loop6       squashfs                                                          /snap/gnome-system-monitor/57
loop7       squashfs                                                          /snap/gtk-common-themes/701
sdb                                                                           
&#9492;&#9472;sdb1      vfat              ESD-USB    E63B-C7C2                            /cdrom
sde                                                                           
&#9500;&#9472;sde1      linux_raid_member            7312ae57-c799-d75c-3017-a5a8c86610be 
&#9500;&#9472;sde2      linux_raid_member            e02c0d49-db61-ee43-da6e-9d2068bac86e 
&#9492;&#9472;sde3      linux_raid_member ubuntu:3   2cc834ef-7c91-db5a-0b99-38d23dda92a8 
  &#9492;&#9472;md123                                                                     
nvme0n1                                                                       
&#9500;&#9472;nvme0n1p1 ntfs              Ripristino D0D6360AD635F178                     
&#9500;&#9472;nvme0n1p2 vfat                         3C38-83DB                            
&#9500;&#9472;nvme0n1p3                                                                   
&#9492;&#9472;nvme0n1p4 ntfs              Windows10  54FA4311FA42EEB4                     
root@ubuntu:/dev# mount /dev/md123 /mnt/raid/
mount: /mnt/raid: wrong fs type, bad option, bad superblock on /dev/md123, missing codepage or helper program, or other error.


Disk 1 (Secondary) ->
> root@ubuntu:/dev# mdadm --assemble --run /dev/md321 /dev/sdd3
mdadm: failed to RUN_ARRAY /dev/md321: Input/output error
mdadm: Not enough devices to start the array.
root@ubuntu:/dev# lsblk -f
NAME        FSTYPE            LABEL      UUID                                 MOUNTPOINT
loop0       squashfs                                                          /rofs
loop1       squashfs                                                          /snap/core/5662
loop2       squashfs                                                          /snap/gnome-3-26-1604/70
loop3       squashfs                                                          /snap/gnome-calculator/238
loop4       squashfs                                                          /snap/gnome-characters/124
loop5       squashfs                                                          /snap/gnome-logs/45
loop6       squashfs                                                          /snap/gnome-system-monitor/57
loop7       squashfs                                                          /snap/gtk-common-themes/701
sdb                                                                           
&#9492;&#9472;sdb1      vfat              ESD-USB    E63B-C7C2                            /cdrom
sdd                                                                           
&#9500;&#9472;sdd1      linux_raid_member            50f0847d-7c85-2b91-3017-a5a8c86610be 
&#9500;&#9472;sdd2      linux_raid_member            264b9bee-8692-c1f7-3017-a5a8c86610be 
&#9492;&#9472;sdd3      linux_raid_member ubuntu:3   2cc834ef-7c91-db5a-0b99-38d23dda92a8 
nvme0n1                                                                       
&#9500;&#9472;nvme0n1p1 ntfs              Ripristino D0D6360AD635F178                     
&#9500;&#9472;nvme0n1p2 vfat                         3C38-83DB                            
&#9500;&#9472;nvme0n1p3                                                                   
&#9492;&#9472;nvme0n1p4 ntfs              Windows10  54FA4311FA42EEB4    


So, the disk 0 maybe has lost the filesystem, right? (is a possible solution to the output _***mount: /mnt/raid: wrong fs type, bad option, bad superblock on /dev/md123, missing codepage or helper program, or other error.***_) 
While the disk 1 seems to need the disk 0 to start...


Solution/Suggestion?

---

### Post by osharko on 2019-04-30
Up

---

