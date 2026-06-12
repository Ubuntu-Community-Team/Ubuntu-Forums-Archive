---
title: "Install Ubuntu on existing software raid 1"
date: 2019-07-29
forum: Server Platforms
---

### Post by pmaff on 2019-07-29
Another old SuSE is installed on a software RAID1 which was installed via UEFI.
Also two SSDs,
all together running dual boot with a Windows 7.
And I want to put Ubuntu 18.04 instead of the SuSE onto it.

```
parted - l 
```
shows
"Error: Can't have overlapping partitions.                                 
Model: ATA M4-CT128M4SSD2 (scsi)
Disk /dev/sda: 128GB
Sector size (logical/physical): 512B/512B
Partition Table: unknown"
which is as far as I can see because of /boot and swap being quite close.

and according to df :
with /dev/sda1 the Windows 7 specific 100MB partition.
/dev/sda2 as /var as ext4
/dev/sda3 as /boot as ext4
/dev/sda4 according to yast2 is swap.

System is running ok since 2014 now.

Model: ATA M4-CT256M4SSD2 (scsi)
Disk /dev/sdb: 256GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  256GB  256GB  primary  ntfs         boot, type=07
which is C: of my Windows 7 system.


Model: ATA Hitachi HUA72302 (scsi)
Disk /dev/sdc: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  839GB   839GB   primary  ntfs         boot, type=07 
 2      839GB   2000GB  1162GB  primary  ext4         type=83


Model: ATA Hitachi HUA72302 (scsi)
Disk /dev/sdd: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  839GB   839GB   primary  ntfs         boot, type=07
 2      839GB   2000GB  1162GB  primary  ext4         type=83

Both Hitachis are together in a software RAID1:
Model: Linux Software RAID Array (md)
Disk /dev/md126: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  839GB   839GB   primary  ntfs         boot, type=07  which is the D: on Windows 7 and /dev/md126p1 mounted as /windows/D on Linux
 2      839GB   2000GB  1162GB  primary  ext4         type=83 which is / for Linux
[B]
Can I simply take this software RAID1 and put Ubuntu 18.04 LTS on the 1162GB ext4 partition?
Or is there something which I have to consider before doing so?
Is there some good description for software raids and Ubuntu (did not find one)?[/B]

As far as I remember I was able to put the old SuSE on this partition /dev/md126p2 quite simple.


Thanks in advance

---

### Post by oldfred on 2019-07-29
Moved to server sub-forum where those who know RAID may be able to help.

Do not know RAID, but this is not correct for sda. It should be msdos or gpt. And normally MBR(msdos) is used for BIOS/Legacy boot and gpt is used for UEFI boot.
       Partition Table: unknown" 

Gpt also has backup partition table so easier to recover. MBR does not. If not showing a gpt backup then drive probably was MBR unless you used dd to write the ISO to it and then it is unknown as that is a hybrid DVD/flash drive without any partition table.

---

### Post by darkod on 2019-07-30
I don't know if suse does it another way but in ubuntu usually you do not partition the md arrays. Which means there should be no p1 or p2 after the /dev/md126.

In general, yes, you can easily install ubuntu server on md raid1. If it was raid5 it is little different but on raid1 is rather simple.

I would make sure sda is good and no partitions overlap.

And I would make sure you do not use partitioned md arrays. Each array should be separate device. But not sure if you can make it windows readable in such case. You say /dev/md126p1 is windows D:.

---

### Post by pmaff on 2019-07-30
> **darkod said:**
> I don't know if suse does it another way but in ubuntu usually you do not partition the md arrays. Which means there should be no p1 or p2 after the /dev/md126.

In general, yes, you can easily install ubuntu server on md raid1. If it was raid5 it is little different but on raid1 is rather simple.

I would make sure sda is good and no partitions overlap.

And I would make sure you do not use partitioned md arrays. Each array should be separate device. But not sure if you can make it windows readable in such case. You say /dev/md126p1 is windows D:.

Is there some good documentation how to handle such a software RAID1 for Ubuntu?
Similar to
[https://doc.opensuse.org/documentation/leap/archive/42.2/reference/html/book.opensuse.reference/cha.advdisk.html](https://doc.opensuse.org/documentation/leap/archive/42.2/reference/html/book.opensuse.reference/cha.advdisk.html)
?

---

### Post by darkod on 2019-07-30
This is the official help page for Advanced (softraid) installation of Ubuntu Server 18.04: [https://help.ubuntu.com/lts/serverguide/advanced-installation.html](https://help.ubuntu.com/lts/serverguide/advanced-installation.html)

It might be little less detailed than the suse one but it should help you. Plus there are tons of other manuals online, just make sure it is what you need before you start following it.

If you get stuck with more specific problem/step, ask and someone will help you.

In general, it is quite simple. The high level plan is:
1. Make sure you have identical partitions on both disks. Do not format them with any filesystem or mount them. (you might already have the partitions you want to reuse).
2. During installation I always use manual partitioning step, and it will allow you to create software raid device using your partitions.
3. You specify the md device to be ext4 and its mount point (in this case probably /).

FYI, I still use the standard server installation ISO, not the newer so called live-install. So, I use the ISO that has -server- in the name as opposed to -live-server-. You have it here: [http://cdimage.ubuntu.com/releases/18.04.2/release/](http://cdimage.ubuntu.com/releases/18.04.2/release/)

The newer -live-server- is here: [http://releases.ubuntu.com/bionic/](http://releases.ubuntu.com/bionic/)

---

