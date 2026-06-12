---
title: "USB Live Install Doesnt Recognize my SSD. One OS Installer Does."
date: 2016-09-09
forum: Ubuntu Development Version
---

### Post by Chazall1 on 2016-09-09
I have the same problems as everyone here on the daily Ubuntu-Gnome 16.10, Ubuntu daily 16.10 as well as many of the past daily releases for the past week. The installer will see my non ssd drives both of them 2. I have 3 other linux installs on my ssd. I have bios set up correctly I have no boot issues to any OS including WIN on one drive. This is the first time in many years that I have had this issue (very frustrating) that I can NOT install another OS to test. I have tried both 32 and 64 .iso's . While on Trying before install I have run parted -l and my ssd is not listed, same from my USB installer, I select Something else to choose where I want to install, NO SSD listed.
NOTE: I tried UBUNTU_MATE 09.08.16 daily, THIS installer RECOGNIZED  My SSD as it should have and no issues with OS Install

Any way to get Ubuntu or Ubuntu-Gnome installer to recognize my SSD ?

Thanks

---

### Post by sudodus on 2016-09-09
- Please describe the hardware - brand and model of the SSD.

- How do you want to install - via ***Something else*** at the partitioning page?

- How is the SSD partitioned - which file systems?

Please post the output of the following commands within [noparse]```
tags
```[/noparse]

```
df -h
sudo parted -ls
sudo lsblk -fm
```

when the SSD is connected.

- How is the SSD connected - via SATA, eSATA or USB3?

- Are things working well with the released versions of Ubuntu, for example 16.04.1 LTS?

- Do I understand correctly, that Ubuntu MATE recognizes the SSD, but ***the same daily built version*** of Ubuntu and Ubuntu Gnome do not? Or are they from different days (different daily builds)?

---

### Post by Chazall1 on 2016-09-09
Here is my information: Yes I was going to the Something else page.  I am currently running U-Mate 16.04, U-Mate testing 16.10. I was going to update my older Ubuntu Gnome to testing from 16.04. /dev/sdc8 and /dev/sdc9 for this install. I was using the daily build for each of my OS.

```
Filesystem      Size  Used Avail Use% Mounted on
udev            3.9G     0  3.9G   0% /dev
tmpfs           799M  9.8M  789M   2% /run
/dev/sdc6        20G  7.4G   12G  40% /
tmpfs           3.9G  472M  3.5G  12% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           3.9G     0  3.9G   0% /sys/fs/cgroup
/dev/sdc5        30G   17G   12G  59% /home
tmpfs           799M   40K  799M   1% /run/user/1000
```



```
Model: ATA WDC WD5001AALS-0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  98.7MB  98.7MB  primary  ntfs         boot
 2      98.7MB  128GB   128GB   primary  ntfs
 3      128GB   160GB   32.2GB  primary  fat32


Model: ATA WDC WD2500AAKS-0 (scsi)
Disk /dev/sdb: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system     Flags
 1      2096kB  196GB   196GB   extended
 5      2097kB  32.2GB  32.2GB  logical   ext4
 6      32.2GB  48.3GB  16.1GB  logical   ext4
 7      48.3GB  50.5GB  2143MB  logical   linux-swap(v1)
 8      50.5GB  82.7GB  32.2GB  logical   ext4
 9      82.7GB  98.8GB  16.1GB  logical   ext4
10      98.8GB  99.3GB  537MB   logical   ext4            boot
11      99.3GB  132GB   32.2GB  logical   ext4
12      132GB   148GB   16.1GB  logical   ext4
13      148GB   180GB   32.2GB  logical   ext4
14      180GB   196GB   16.1GB  logical   ext4
 2      196GB   223GB   26.8GB  primary   ext4


Model: ATA SanDisk SDSSDXP2 (scsi)
Disk /dev/sdc: 240GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  32.2GB  32.2GB  primary   ext4
 2      32.2GB  53.7GB  21.5GB  primary   ext4
 3      53.7GB  55.3GB  1610MB  primary   linux-swap(v1)
 4      55.3GB  189GB   134GB   extended
 5      55.3GB  87.5GB  32.2GB  logical   ext4
 6      87.5GB  109GB   21.5GB  logical   ext4            boot
 7      109GB   110GB   537MB   logical   ext4
 8      110GB   142GB   32.2GB  logical   ext4
 9      142GB   163GB   21.5GB  logical   ext4
10      163GB   189GB   25.8GB  logical   ext4
11      189GB   189GB   418MB   logical   fat32





```
```
NAME    FSTYPE LABEL          UUID                                 MOUNTPOINT NAME      SIZE OWNER GROUP MODE
sda                                                                           sda     465.8G root  disk  brw-rw----
&#9500;&#9472;sda1  ntfs   Win7 MBR       C09CD6E99CD6D8CC                                &#9500;&#9472;sda1   94.1M root  disk  brw-rw----
&#9500;&#9472;sda2  ntfs   Windows 7      5A88E46C88E44859                                &#9500;&#9472;sda2  119.4G root  disk  brw-rw----
&#9492;&#9472;sda3  vfat   JERI STORAG    8D4A-3CD6                                       &#9492;&#9472;sda3     30G root  disk  brw-rw----
sdb                                                                           sdb     232.9G root  disk  brw-rw----
&#9500;&#9472;sdb1                                                                        &#9500;&#9472;sdb1      1K root  disk  brw-rw----
&#9500;&#9472;sdb2  ext4   BU Area        8bfedd09-3494-4633-bcdb-04fd1c55fc7e            &#9500;&#9472;sdb2     25G root  disk  brw-rw----
&#9500;&#9472;sdb5  ext4                  9362de22-b798-42a5-9281-7efe26a02ede            &#9500;&#9472;sdb5     30G root  disk  brw-rw----
&#9500;&#9472;sdb6  ext4                  cf786d1c-3fd7-44c9-9475-5dee2ed0c15f            &#9500;&#9472;sdb6     15G root  disk  brw-rw----
&#9500;&#9472;sdb7  swap                  b1e04c79-25fd-4ae3-9546-bd9e7126d642 [SWAP]     &#9500;&#9472;sdb7      2G root  disk  brw-rw----
&#9500;&#9472;sdb8  ext4   open home      9a9784c7-5fe4-4a8f-ac60-7dc3f601fd32            &#9500;&#9472;sdb8     30G root  disk  brw-rw----
&#9500;&#9472;sdb9  ext4   open root      00330c58-9131-4df1-b37c-fc108f84f605            &#9500;&#9472;sdb9     15G root  disk  brw-rw----
&#9500;&#9472;sdb10 ext4   grub2          54a9fbb0-2162-4977-ad73-fe0638942391            &#9500;&#9472;sdb10   512M root  disk  brw-rw----
&#9500;&#9472;sdb11 ext4                  3936294c-6d8b-409f-a3e1-0ab4f0af0e93            &#9500;&#9472;sdb11    30G root  disk  brw-rw----
&#9500;&#9472;sdb12 ext4                  65398735-4a39-4538-a6b3-f46cbc4960fe            &#9500;&#9472;sdb12    15G root  disk  brw-rw----
&#9500;&#9472;sdb13 ext4   not used home  bb726300-ebe8-4b6a-a482-20a7ba32e769            &#9500;&#9472;sdb13    30G root  disk  brw-rw----
&#9492;&#9472;sdb14 ext4   not used root  06156748-bf63-49e7-b865-4cab4483fda9            &#9492;&#9472;sdb14    15G root  disk  brw-rw----
sdc                                                                           sdc     223.6G root  disk  brw-rw----
&#9500;&#9472;sdc1  ext4   Mate 1604 Home 2cf203cf-6ca7-4988-93ef-63f6a5cee58a            &#9500;&#9472;sdc1     30G root  disk  brw-rw----
&#9500;&#9472;sdc2  ext4   Mate 1604 Root 9ccfdf40-a980-4c77-93d9-35d1ebadd57e            &#9500;&#9472;sdc2     20G root  disk  brw-rw----
&#9500;&#9472;sdc3  swap                  5a85c7d1-c0eb-415e-be5c-11842ff9a577 [SWAP]     &#9500;&#9472;sdc3    1.5G root  disk  brw-rw----
&#9500;&#9472;sdc4                                                                        &#9500;&#9472;sdc4      1K root  disk  brw-rw----
&#9500;&#9472;sdc5  ext4   Mate YY Home   9cd7630f-9c7c-4eba-8bf7-fb13e9c77ec5 /home      &#9500;&#9472;sdc5     30G root  disk  brw-rw----
&#9500;&#9472;sdc6  ext4   Mate YY Root   38a95276-9607-4570-9580-3fae0c608803 /          &#9500;&#9472;sdc6     20G root  disk  brw-rw----
&#9500;&#9472;sdc7  ext4   ssdgrub        123ee278-b2cc-4b46-bbcc-56da30461f6a            &#9500;&#9472;sdc7    512M root  disk  brw-rw----
&#9500;&#9472;sdc8  ext4                  074fc5ae-7b71-4a37-8d9d-e61db8e45d89            &#9500;&#9472;sdc8     30G root  disk  brw-rw----
&#9500;&#9472;sdc9  ext4                  f6fc08e8-1854-4b46-a778-38304314b826            &#9500;&#9472;sdc9     20G root  disk  brw-rw----
&#9500;&#9472;sdc10 ext4                  089cb436-0f15-4de3-99fb-5f4c0349e0df            &#9500;&#9472;sdc10    24G root  disk  brw-rw----
&#9492;&#9472;sdc11 vfat                  5C00-388A                                       &#9492;&#9472;sdc11   399M root  disk  brw-rw----
sr0                                                                           sr0      1024M root  cdrom brw-rw----
```

---

### Post by sudodus on 2016-09-09
Please put the text output within CODE tags, as I described in the previous post and here. Otherwise it will be very difficult to read. You can click on the big red button 'Advanced' below the editing window, mark the text and click on the # icon above the editing window, or you can type in the code tags manually [within square parentheses] like this

[noparse]```

copy and paste
the output from
the commands
like this

```[/noparse]

```
$ df -h
Filesystem Size Used Avail Use% Mounted on
...
/dev/sdc6  20G  7.4G 12G   40%  /      # root partition
...
/dev/sdc5  30G  17G  12G   59%  /home  # home partition
...

```


```
$ parted -ls
Model: ATA SanDisk SDSSDXP2 (scsi)
Disk /dev/sdc: 240GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags:

Number   Start  End    Size   Type    File system    Flags
1        1049kB 32.2GB 32.2GB primary ext4
2        32.2GB 53.7GB 21.5GB primary ext4
3        53.7GB 55.3GB 1610MB primary linux-swap(v1)
4        55.3GB 189GB  134GB  extended
5        55.3GB 87.5GB 32.2GB logical ext4
6        87.5GB 109GB  21.5GB logical ext4           boot
7        109GB  110GB  537MB  logical ext4
8        110GB  142GB  32.2GB logical ext4
9        142GB  163GB  21.5GB logical ext4
10       163GB  189GB  25.8GB logical ext4
11       189GB  189GB  418MB  logical fat32

```

I see nothing wrong or unusual here. Your problem could be a mismatch with the SSD itself, or maybe with the hardware connecting to it, and the linux drivers.

-o-

I have a Sandisk Ultra Plus 128 GB drive (a few years old, that I only use once in a great while). It works for me with various operating systems. Here I see it from a live session of Lubuntu Yakkety i386 (not today's daily iso, it is from Sept 4),

```
lubuntu@lubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu Yakkety Yak (development branch)
Release:	16.10
Codename:	yakkety

lubuntu@lubuntu:~$ sudo parted /dev/sda print
Model: SanDisk SDSSDH2128G (scsi)
Disk /dev/sda: 128GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system     Flags
 1      1049kB  64.4GB  64.4GB  primary  ext4            boot
 3      64.4GB  124GB   59.2GB  primary  ext4
 2      124GB   128GB   4403MB  primary  linux-swap(v1)

lubuntu@lubuntu:~$ sudo lsblk -fm /dev/sda
NAME   FSTYPE LABEL            UUID                                 MOUNTPOINT                      NAME     SIZE OWNER GROUP MODE
sda                                                                                                 sda    119.2G root  disk  brw-rw----
&#9500;&#9472;sda1 ext4   saucy64-n-virt-m d31306e0-9e95-4e8d-a271-ffa0a7a02195 /media/lubuntu/saucy64-n-virt-m &#9500;&#9472;sda1    60G root  disk  brw-rw----
&#9500;&#9472;sda2 swap                    24d07dea-2b93-4bac-b962-80c3c18344c0 [SWAP]                          &#9500;&#9472;sda2   4.1G root  disk  brw-rw----
&#9492;&#9472;sda3 ext4   precise-mkiso    65dec8c0-8f82-4b99-add9-4812a32d69de /media/lubuntu/precise-mkiso    &#9492;&#9472;sda3  55.1G root  disk  brw-rw----
lubuntu@lubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu Yakkety Yak (development branch)
Release:	16.10
Codename:	yakkety

```

***Finally, what do these commands see, when you are running standard Ubuntu and Ubuntu Gnome (you can try from a live drive)?***

---

### Post by Chazall1 on 2016-09-09
Here is more info thanks
> bart@ubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu Yakkety Yak (development branch)
Release:	16.10
Codename:	yakkety


bart@ubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu Yakkety Yak (development branch)
Release:	16.10
Codename:	yakkety
bart@ubuntu:~$ sudo parted /dev/sdc print
[sudo] password for bart: 
Model: ATA SanDisk SDSSDXP2 (scsi)
Disk /dev/sdc: 240GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  32.2GB  32.2GB  primary   ext4
 2      32.2GB  53.7GB  21.5GB  primary   ext4
 3      53.7GB  55.3GB  1610MB  primary   linux-swap(v1)
 4      55.3GB  189GB   134GB   extended
 5      55.3GB  87.5GB  32.2GB  logical   ext4
 6      87.5GB  109GB   21.5GB  logical   ext4            boot
 7      109GB   110GB   537MB   logical   ext4
 8      110GB   142GB   32.2GB  logical   ext3
 9      142GB   163GB   21.5GB  logical   ext3
10      163GB   189GB   26.2GB  logical   ext4


bart@ubuntu:~$ sudo lsblk -fm /dev/sdc
NAME    FSTYPE LABEL          UUID                                 MOUNTPOINT NAME      SIZE OWNER GROUP MODE
sdc                                                                           sdc     223.6G root  disk  brw-rw----
&#9500;&#9472;sdc1  ext4   Mate 1604 Home 2cf203cf-6ca7-4988-93ef-63f6a5cee58a            &#9500;&#9472;sdc1     30G root  disk  brw-rw----
&#9500;&#9472;sdc2  ext4   Mate 1604 Root 9ccfdf40-a980-4c77-93d9-35d1ebadd57e            &#9500;&#9472;sdc2     20G root  disk  brw-rw----
&#9500;&#9472;sdc3  swap                  5a85c7d1-c0eb-415e-be5c-11842ff9a577 [SWAP]     &#9500;&#9472;sdc3    1.5G root  disk  brw-rw----
&#9500;&#9472;sdc5  ext4   Mate YY Home   9cd7630f-9c7c-4eba-8bf7-fb13e9c77ec5 /home      &#9500;&#9472;sdc5     30G root  disk  brw-rw----
&#9500;&#9472;sdc6  ext4   Mate YY Root   38a95276-9607-4570-9580-3fae0c608803 /          &#9500;&#9472;sdc6     20G root  disk  brw-rw----
&#9500;&#9472;sdc7  ext4   ssdgrub        123ee278-b2cc-4b46-bbcc-56da30461f6a            &#9500;&#9472;sdc7    512M root  disk  brw-rw----
&#9500;&#9472;sdc8  ext3                  22d33868-c92a-4b7c-ae76-e93f84f407e0            &#9500;&#9472;sdc8     30G root  disk  brw-rw----
&#9500;&#9472;sdc9  ext3                  5d004561-e1a7-494b-8ae0-43c903957400            &#9500;&#9472;sdc9     20G root  disk  brw-rw----
&#9492;&#9472;sdc10 ext4   Open for OS    089cb436-0f15-4de3-99fb-5f4c0349e0df            &#9492;&#9472;sdc10  24.4G root  disk  brw-rw----



---

### Post by sudodus on 2016-09-09
Please edit your latest post and put the output text within CODE tags, not QUOTE tags.

---

### Post by sudodus on 2016-09-09
Anyway, straining my eyes I can see that your Ubuntu Yakkety is recognizing the Sandisk SSD :-)

When exactly does Ubuntu fail to recognize it?

***Edit:*** Or is it still Ubuntu MATE? Please show what happens when you try with a flavour of Ubuntu, that does not work for you.

---

### Post by Chazall1 on 2016-09-09
```
bart@ubuntu:~$ sudo lsblk -fm /dev/sdc
NAME    FSTYPE LABEL          UUID                                 MOUNTPOINT NAME      SIZE OWNER GROUP MODE
sdc                                                                           sdc     223.6G root  disk  brw-rw----
&#9500;&#9472;sdc1  ext4   Mate 1604 Home 2cf203cf-6ca7-4988-93ef-63f6a5cee58a            &#9500;&#9472;sdc1     30G root  disk  brw-rw----
&#9500;&#9472;sdc2  ext4   Mate 1604 Root 9ccfdf40-a980-4c77-93d9-35d1ebadd57e            &#9500;&#9472;sdc2     20G root  disk  brw-rw----
&#9500;&#9472;sdc3  swap                  5a85c7d1-c0eb-415e-be5c-11842ff9a577 [SWAP]     &#9500;&#9472;sdc3    1.5G root  disk  brw-rw----
&#9500;&#9472;sdc5  ext4   Mate YY Home   9cd7630f-9c7c-4eba-8bf7-fb13e9c77ec5 /home      &#9500;&#9472;sdc5     30G root  disk  brw-rw----
&#9500;&#9472;sdc6  ext4   Mate YY Root   38a95276-9607-4570-9580-3fae0c608803 /          &#9500;&#9472;sdc6     20G root  disk  brw-rw----
&#9500;&#9472;sdc7  ext4   ssdgrub        123ee278-b2cc-4b46-bbcc-56da30461f6a            &#9500;&#9472;sdc7    512M root  disk  brw-rw----
&#9500;&#9472;sdc8  ext3                  22d33868-c92a-4b7c-ae76-e93f84f407e0            &#9500;&#9472;sdc8     30G root  disk  brw-rw----
&#9500;&#9472;sdc9  ext3                  5d004561-e1a7-494b-8ae0-43c903957400            &#9500;&#9472;sdc9     20G root  disk  brw-rw----
&#9492;&#9472;sdc10 ext4   Open for OS    089cb436-0f15-4de3-99fb-5f4c0349e0df            &#9492;&#9472;sdc10  24.4G root  disk  brw-rw----
```

---

### Post by Chazall1 on 2016-09-09
LOL I figured it out how to assist you with the info. Sorry its been a while sense I have been in Ubuntu forums. I spend most of my time on xda-developers. More than likely got to be related to software somehow.

---

### Post by sudodus on 2016-09-09
Thank you, now it is much easier to read :-)

The mounted partitions are telling me quite clearly now, that it is still Ubuntu MATE, that is running.

---

