---
title: "iso bug or parted bug?"
date: 2014-09-04
forum: Ubuntu Development Version
---

### Post by kansasnoob on 2014-09-04
I recently encountered this in Trusty:

[http://ubuntuforums.org/showthread.php?t=2242245&page=2&p=13114225#post13114225](http://ubuntuforums.org/showthread.php?t=2242245&page=2&p=13114225#post13114225)

So I decided to have a look at Utopic using the Ubuntu GNOME Beta 1 image:

```
ubuntu-gnome@ubuntu-gnome:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu Utopic Unicorn (development branch)
Release:	14.10
Codename:	utopic
```

You'll see some error code at the end of "sudo parted -l":

```
ubuntu-gnome@ubuntu-gnome:~$ sudo parted -l
Model: ATA WDC WD5000AAKS-0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size    Type      File system     Flags
 1      32.3kB  157GB  157GB   primary   ext4            boot
 2      157GB   210GB  52.4GB  primary   ext4
 3      210GB   232GB  21.8GB  primary   ext4
 4      232GB   500GB  268GB   extended
 6      232GB   252GB  20.5GB  logical   ext4
 7      252GB   273GB  20.4GB  logical   ext4
 8      273GB   293GB  20.4GB  logical   ext4
 9      293GB   313GB  20.4GB  logical   ext4
10      313GB   334GB  20.4GB  logical   ext4
11      334GB   354GB  20.4GB  logical   ext4
12      354GB   374GB  20.0GB  logical   ext4
13      374GB   395GB  20.4GB  logical   ext4
14      395GB   415GB  20.1GB  logical   ext4
15      415GB   435GB  20.1GB  logical   ext4
16      435GB   455GB  20.4GB  logical   ext4
17      455GB   476GB  20.4GB  logical   ext4
18      476GB   498GB  21.9GB  logical   ext4
 5      498GB   500GB  2517MB  logical   linux-swap(v1)


Model: ATA WDC WD800BB-63JK (scsi)
Disk /dev/sdb: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  29.4GB  29.4GB  primary   ntfs
 2      29.4GB  75.6GB  46.3GB  primary   ext4
 3      75.6GB  80.0GB  4404MB  extended
 5      75.6GB  80.0GB  4403MB  logical   linux-swap(v1)


Model: ATA WDC WD1600AABB-5 (scsi)
Disk /dev/sdc: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  158GB  158GB   primary   ext4            boot
 2      158GB   160GB  2136MB  extended
 5      158GB   160GB  2136MB  logical   linux-swap(v1)


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
**[COLOR="#FF0000"]Error: Can't have a partition outside the disk![/COLOR]**
Ignore/Cancel? c                                                          
Model: ASUS DRW-24B1ST i (scsi)
Disk /dev/sr0: 1049MB
Sector size (logical/physical): 2048B/2048B
Partition Table: unknown
Disk Flags: 

```

Then I booted into an Ubuntu Utopic installed on the same hardware and you can see there is no such error:

```
lance@lance-desktop:~$ sudo parted -l
[sudo] password for lance: 
Model: ATA WDC WD5000AAKS-0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size    Type      File system     Flags
 1      32.3kB  157GB  157GB   primary   ext4            boot
 2      157GB   210GB  52.4GB  primary   ext4
 3      210GB   232GB  21.8GB  primary   ext4
 4      232GB   500GB  268GB   extended
 6      232GB   252GB  20.5GB  logical   ext4
 7      252GB   273GB  20.4GB  logical   ext4
 8      273GB   293GB  20.4GB  logical   ext4
 9      293GB   313GB  20.4GB  logical   ext4
10      313GB   334GB  20.4GB  logical   ext4
11      334GB   354GB  20.4GB  logical   ext4
12      354GB   374GB  20.0GB  logical   ext4
13      374GB   395GB  20.4GB  logical   ext4
14      395GB   415GB  20.1GB  logical   ext4
15      415GB   435GB  20.1GB  logical   ext4
16      435GB   455GB  20.4GB  logical   ext4
17      455GB   476GB  20.4GB  logical   ext4
18      476GB   498GB  21.9GB  logical   ext4
 5      498GB   500GB  2517MB  logical   linux-swap(v1)


Model: ATA WDC WD800BB-63JK (scsi)
Disk /dev/sdb: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  29.4GB  29.4GB  primary   ntfs
 2      29.4GB  75.6GB  46.3GB  primary   ext4
 3      75.6GB  80.0GB  4404MB  extended
 5      75.6GB  80.0GB  4403MB  logical   linux-swap(v1)


Model: ATA WDC WD1600AABB-5 (scsi)
Disk /dev/sdc: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  158GB  158GB   primary   ext4            boot
 2      158GB   160GB  2136MB  extended
 5      158GB   160GB  2136MB  logical   linux-swap(v1)


Model: Kingston DataTraveler 2.0 (scsi)
Disk /dev/sdd: 15.6GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  15.6GB  15.6GB  primary  fat32

```

Any thoughts regarding that ***Error: Can't have a partition outside the disk!*** displayed in only a live session?

I searched for a bug report and found none :)

Could I get some other testers to try that also? First check the output of "sudo parted -l" from a Utopic live session, then repeat with an installed Utopic and see if you get the same results :biggrin:

---

### Post by mc4man on 2014-09-04
Did you have a disk in the CD/DVD drive in your first example? ( and not in 2nd

---

### Post by kansasnoob on 2014-09-04
> **mc4man said:**
> Did you have a disk in the CD/DVD drive in your first example? ( and not in 2nd

I was using a live DVD, so yes - I had the live DVD in the drive. I should see what happens with a live USB. Thanks :D

---

### Post by kansasnoob on 2014-09-05
Discovered a bug I wasn't aware of since I use live DVD's:

[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1325801](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1325801)

So for now I just created a 14.04.1 live USB for testing purposes and the parted -l output is OK with it:

```
ubuntu-gnome@ubuntu-gnome:~$ sudo parted -l
Model: ATA WDC WD5000AAKS-0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      32.3kB  157GB  157GB   primary   ext4            boot
 2      157GB   210GB  52.4GB  primary   ext4
 3      210GB   232GB  21.8GB  primary   ext4
 4      232GB   500GB  268GB   extended
 6      232GB   252GB  20.5GB  logical   ext4
 7      252GB   273GB  20.4GB  logical   ext4
 8      273GB   293GB  20.4GB  logical   ext4
 9      293GB   313GB  20.4GB  logical   ext4
10      313GB   334GB  20.4GB  logical   ext4
11      334GB   354GB  20.4GB  logical   ext4
12      354GB   374GB  20.0GB  logical   ext4
13      374GB   395GB  20.4GB  logical   ext4
14      395GB   415GB  20.1GB  logical   ext4
15      415GB   435GB  20.1GB  logical   ext4
16      435GB   455GB  20.4GB  logical   ext4
17      455GB   476GB  20.4GB  logical   ext4
18      476GB   498GB  21.9GB  logical   ext4
 5      498GB   500GB  2517MB  logical   linux-swap(v1)


Model: ATA WDC WD800BB-63JK (scsi)
Disk /dev/sdb: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  29.4GB  29.4GB  primary   ntfs
 2      29.4GB  75.6GB  46.3GB  primary   ext4
 3      75.6GB  80.0GB  4404MB  extended
 5      75.6GB  80.0GB  4403MB  logical   linux-swap(v1)


Model: ATA WDC WD1600AABB-5 (scsi)
Disk /dev/sdc: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  158GB  158GB   primary   ext4            boot
 2      158GB   160GB  2136MB  extended
 5      158GB   160GB  2136MB  logical   linux-swap(v1)


Model: Crucial Gizmo! (scsi)
Disk /dev/sdd: 4010MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  4010MB  4009MB  primary  fat32        boot, lba

```

---

