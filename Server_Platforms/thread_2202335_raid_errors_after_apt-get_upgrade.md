---
title: "raid errors after apt-get upgrade"
date: 2014-01-28
forum: Server Platforms
---

### Post by astarmathsandphysics on 2014-01-28
I have two 500gb disks in RAID 1 array

After updating I got the following message

```
update-initramfs: Generating /boot/initrd.img-3.2.0-23-generic
W: mdadm: the array /dev/md/13_0 with UUID cd600f4e:8d48320b:258dd0b2:06e7faa4
W: mdadm: is currently active, but it is not listed in mdadm.conf. if
W: mdadm: it is needed for boot, then YOUR SYSTEM IS NOW UNBOOTABLE!
W: mdadm: please inspect the output of /usr/share/mdadm/mkconf, compare
W: mdadm: it to /etc/mdadm/mdadm.conf, and make the necessary changes.
```

mkconf returns

```
# definitions of existing MD arrays
ARRAY /dev/md/0 metadata=1.2 UUID=d4039aa4:18485485:1a47f60a:8a824861 name=server11362:0
ARRAY /dev/md/1 metadata=1.2 UUID=b3410ef6:efc6c593:62dae4d4:579cbabf name=server11362:1
ARRAY /dev/md/2 metadata=1.2 UUID=39816305:28ed0721:a67b18e7:3798f650 name=server11362:2
ARRAY /dev/md125 UUID=00000000:00000000:00000000:00000000
   spares=1
ARRAY /dev/md127 UUID=00000000:00000000:00000000:00000000
   spares=1
ARRAY /dev/md13 UUID=cd600f4e:8d48320b:258dd0b2:06e7faa4
```

and here is mdadm.conf

```
# definitions of existing MD arrays
ARRAY /dev/md/0 metadata=1.2 UUID=d4039aa4:18485485:1a47f60a:8a824861 name=server11362:0
ARRAY /dev/md/1 metadata=1.2 UUID=b3410ef6:efc6c593:62dae4d4:579cbabf name=server11362:1
ARRAY /dev/md/2 metadata=1.2 UUID=39816305:28ed0721:a67b18e7:3798f650 name=server11362:2
```

 md/0 md/1 md/2 match ok
I don't recognise md125 md127 or md13

Here are the drives in fstab
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/md2 during installation
UUID=0e1dc6c8-f272-4622-bdb3-119e26458007 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/md0 during installation
UUID=d20ba226-f3c5-434a-859d-5f634c55395f /boot           ext4    defaults        0       2
# swap was on /dev/md1 during installation
UUID=c6c25c2a-4e15-4cd2-a348-2c6b3cfa9f1e none            swap    sw              0       0
```
These dont mathc and I am hopping on one foot.

Boot is on md/0
Can I reboot the server and run fix?

---

### Post by ian-weisser on 2014-01-28
DO NOT REBOOT!
> W: mdadm: it is needed for boot, then YOUR SYSTEM IS NOW UNBOOTABLE!

This is why my boot disk is separate from my array.

Do you understand the error messages?
You have a different array than mdadm is expecting.

---

### Post by CharlesA on 2014-01-28
Do you really have three raid devices?

Run this and post the output.

```
sudo mdadm --examine /dev/mdx
```

---

### Post by astarmathsandphysics on 2014-01-29
I have one rad array with two 500gb hard drives. I think this is md0
This is the output 
mdadm: No md superblock detected on /dev/md0
mdadm: No md superblock detected on /dev/md1
mdadm: No md superblock detected on /dev/md127

In /dev there are only md0,md1,md2 and md127 files
They are all several tens of mb in size
These seem BIG to me

In dev/disk/by-uuid there are 4 directories
0e1dc6c8-f272-4622-bdb3-119e26458007
c6c25c2a-4e15-4cd2-a348-2c6b3cfa9f1e
d19e88d5-286e-430c-8725-aed4d2161a19
d20ba226-f3c5-434a-859d-5f634c55395f

---

### Post by CharlesA on 2014-01-29
> **astarmathsandphysics said:**
> In /dev there are only md0,md1,md2 and md127 files
They are all several mb in size
These seem BIG to me

Lets try that again. Run this please:

```
sudo mdadm --examine /dev/md0
```
```
sudo mdadm --examine /dev/md1
```
```
sudo mdadm --examine /dev/md2
```
```
sudo mdadm --examine /dev/md127
```

---

### Post by astarmathsandphysics on 2014-01-29
I realised that already and edited my post
The output for each one is 
mdadm: No md superblock detected on /dev/md0
mdadm: No md superblock detected on /dev/md1
mdadm: No md superblock detected on /dev/md2
mdadm: No md superblock detected on /dev/md127

I ran sudo mdadm --detail /dev/md0
and got

Raid Level : raid1
     Array Size : 96244 (94.00 MiB 98.55 MB)
  Used Dev Size : 96244 (94.00 MiB 98.55 MB)
   Raid Devices : 2
  Total Devices : 2
    Persistence : Superblock is persistent

    Update Time : Tue Jan 28 08:37:08 2014
          State : clean 
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           Name : server11362:0  (local to host server11362)
           UUID : d4039aa4:18485485:1a47f60a:8a824861
         Events : 25

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1

root@server11362:~# sudo mdadm --examine /dev/sda1
/dev/sda1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : d4039aa4:18485485:1a47f60a:8a824861
           Name : server11362:0  (local to host server11362)
  Creation Time : Fri Nov  8 04:14:33 2013
     Raid Level : raid1
   Raid Devices : 2

 Avail Dev Size : 192488 (94.00 MiB 98.55 MB)
     Array Size : 96244 (94.00 MiB 98.55 MB)
    Data Offset : 24 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 4dfb8b6e:66c38ea0:43843acc:4eb7f746

    Update Time : Wed Jan 29 05:40:03 2014
       Checksum : e828d3da - correct
         Events : 25


   Device Role : Active device 0
   Array State : AA ('A' == active, '.' == missing)
root@server11362:~#

root@server11362:~# sudo mdadm --examine /dev/sdb1
/dev/sdb1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : d4039aa4:18485485:1a47f60a:8a824861
           Name : server11362:0  (local to host server11362)
  Creation Time : Fri Nov  8 04:14:33 2013
     Raid Level : raid1
   Raid Devices : 2

 Avail Dev Size : 192488 (94.00 MiB 98.55 MB)
     Array Size : 96244 (94.00 MiB 98.55 MB)
    Data Offset : 24 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 5cbc30ff:11d13bb2:f36e2d83:bd8ede94

    Update Time : Wed Jan 29 05:40:03 2014
       Checksum : 8f5464b5 - correct
         Events : 25


   Device Role : Active device 1
   Array State : AA ('A' == active, '.' == missing)
root@server11362:~#

As for keeping the raid devices separate from the arrays - at home I have a server also running ubuntu 12.04 with two raid arrays.
One array is raid1 - gives me no problems and has the operating system.
My data is stored on 3 2000gb drives raided 5 I think
I have recovered from several disk disasters with no loss of data.

root@server11362:~# sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000e8d71

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      194559       96256   fd  Linux raid autodetect
/dev/sda2          196606   976771071   488287233    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5          196608    31444991    15624192   fd  Linux raid autodetect
/dev/sda6        31447040   976771071   472662016   fd  Linux raid autodetect

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000446ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048      194559       96256   fd  Linux raid autodetect
/dev/sdb2          196606   976771071   488287233    5  Extended
/dev/sdb5          196608    31444991    15624192   fd  Linux raid autodetect
/dev/sdb6        31447040   976771071   472662016   fd  Linux raid autodetect

Disk /dev/md2: 484.0 GB, 484004716544 bytes
2 heads, 4 sectors/track, 118165214 cylinders, total 945321712 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md2 doesn't contain a valid partition table

Disk /dev/md1: 16.0 GB, 15998050304 bytes
2 heads, 4 sectors/track, 3905774 cylinders, total 31246192 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md1 doesn't contain a valid partition table

Disk /dev/md0: 98 MB, 98553856 bytes
2 heads, 4 sectors/track, 24061 cylinders, total 192488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbe2f4630

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63      192779       96358+  fd  Linux raid autodetect
/dev/sdc2          192780     4192964     2000092+  fd  Linux raid autodetect
/dev/sdc3         4192965   625137344   310472190   fd  Linux raid autodetect

Disk /dev/md127: 317.9 GB, 317923393536 bytes
2 heads, 4 sectors/track, 77618016 cylinders, total 620944128 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md127 doesn't contain a valid partition table
root@server11362:~# sudo fdisk -l

---

### Post by CharlesA on 2014-01-29
How did you set up mdadm in the first place, this seems like a very, very odd way to set up the file system.

---

### Post by speed32219 on 2014-01-29
Maybe your array uuid has changed.  Try sudo mdadm --detail --scan >> mdadm.conf.new which will be located in your home directory and match it against the /etc/mdadm/mdadm.conf that your array uses during boot.

---

### Post by astarmathsandphysics on 2014-01-29
The raid configuration were set up by the webhost

> **speed32219 said:**
> Maybe your array uuid has changed.  Try sudo mdadm --detail --scan >> mdadm.conf.new which will be located in your home directory and match it against the /etc/mdadm/mdadm.conf that your array uses during boot.

here it is

ARRAY /dev/md/2 metadata=1.2 name=server11362:2 UUID=39816305:28ed0721:a67b18e7:3798f650
ARRAY /dev/md/1 metadata=1.2 name=server11362:1 UUID=b3410ef6:efc6c593:62dae4d4:579cbabf
ARRAY /dev/md/0 metadata=1.2 name=server11362:0 UUID=d4039aa4:18485485:1a47f60a:8a824861
ARRAY /dev/md/13_0 metadata=0.90 UUID=cd600f4e:8d48320b:258dd0b2:06e7faa4

they are the same apart from ARRAY /dev/md/13_0 metadata=0.90 UUID=cd600f4e:8d48320b:258dd0b2:06e7faa4

I found something on a forum [https://bbs.archlinux.org/viewtopic.php?id=136766](https://bbs.archlinux.org/viewtopic.php?id=136766)

e2fsck -cc /dev/md127 (takes seVERAL HOURS)
resize2fs /dev/md127
# fsck -f /dev/md127

md127 is not in mdadm.conf but I can run e2fsck
Does that mean anything?
Every time I run e2fsck I get a broken pipe:

root@server11362:~# e2fsck -cc /dev/md127
e2fsck 1.42 (29-Nov-2011)
Checking for bad blocks (non-destructive read-write test)
Testing with random pattern: Write failed: Broken pipeed. (0/0/0 errors)

And can't update grub

root@server11362:~# sudo update-grub
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
Generating grub.cfg ...
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
Found linux image: /boot/vmlinuz-3.2.0-23-generic
Found initrd image: /boot/initrd.img-3.2.0-23-generic
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
Found memtest86+ image: /memtest86+.bin
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
Found Debian GNU/Linux (5.0.10) on /dev/sdc3
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
done

---

### Post by CharlesA on 2014-01-29
> **astarmathsandphysics said:**
> The raid configuration were set up by the webhost

If that is the case, I would backup any data on that machine before messing with it further or you could end up with an unbootable machine.

I don't know what else to check, but it definitely looks.. odd. How were the arrays mounted when they were working?

---

### Post by astarmathsandphysics on 2014-01-30
The data is already backed up.
It is a new install - a week old.
Everything is working now - I just get a disk which shouldn't be there md127/md13_0
Not sure hat you mean by 'How were the arrays mounted when they were working?'
I think I know what you mean. Maybe stupid but I didn't check

---

