---
title: "Folder Lock-Up on SD_Card"
date: 2016-10-05
forum: Server Platforms
---

### Post by Nikalex on 2016-10-05
Hi everyone

I have a bit of a problem and was hoping for some help. 
I am running a Baikal Server on a Raspberry - unfortunately the latter crashed due to a power outage and I am about to newly set up the SD-Card with a new rPI system on it. 

HOWEVER, before doing that, I wanted to recover the calendar data.
So I plugged the SD card into the cardreader of my laptop, located the calendar folder, only to find it marked with an "x" locked icon. Clicking on it yields a msg saying I dont have the necessary permissions. 

I am a complete Linux noob and did not find the answer to this problem in the forums. 

Any help unlocking the folder is highly appreciated. 

Thanks
n

---

### Post by howefield on 2016-10-05
Thread moved to the "*Server Platforms*" forum, possibly a better fit.

---

### Post by Nikalex on 2016-10-05
Im guessing its a simple permission issue?

---

### Post by Nikalex on 2016-10-10
Giving this a gentle bump

---

### Post by howefield on 2016-10-11
Who owns the file ?

Navigate to the file on the SD card in terminal and post the output of ls -al.

---

### Post by sudodus on 2016-10-11
Welcome to the Ubuntu Forums :-)

We need to know more about the partition table and file systems on the card in order to help. Please post also the output of the following commands (and use code tags around the output text

[noparse]```

output text
(can be several lines)

```[/noparse]

```
df -h
sudo lsblk -f
sudo lsblk -m
sudo parted -ls
```

---

### Post by Nikalex on 2016-10-23
> **howefield said:**
> Who owns the file ?

Navigate to the file on the SD card in terminal and post the output of ls -al.

Sorry guys, I was travelling for work for a few days so did not have the chance to monitor this thread. Back now..

```

nick@nick-P15FV2:/media/nick/13d368bf-6dbf-4751-8ba1-88bed06bef77/var/www$ ls -al
total 3540
drwxr-xr-x  3 root     root        4096 Sep 11  2015 .
drwxr-xr-x 12 root     root        4096 Sep 11  2015 ..
-rw-r--r--  1 root     root     3606142 Feb  5  2014 baikal-flat-0.2.7.zip
-rw-r--r--  1 root     root        3585 Sep 11  2015 index.lighttpd.html
drwx------  8 www-data www-data    4096 Sep 11  2015 kalender
nick@nick-P15FV2:/media/nick/13d368bf-6dbf-4751-8ba1-88bed06bef77/var/www$ 

```

Its the "Kalender" Folder

---

### Post by Nikalex on 2016-10-23
> **sudodus said:**
> Welcome to the Ubuntu Forums :-)

We need to know more about the partition table and file systems on the card in order to help. Please post also the output of the following commands (and use code tags around the output text

[noparse]```

output text
(can be several lines)

```[/noparse]

```
df -h
sudo lsblk -f
sudo lsblk -m
sudo parted -ls
```

df -h
```

Filesystem      Size  Used Avail Use% Mounted on
udev            3.9G     0  3.9G   0% /dev
tmpfs           787M  9.7M  777M   2% /run
/dev/sda4        28G   15G   13G  54% /
tmpfs           3.9G   32M  3.9G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           3.9G     0  3.9G   0% /sys/fs/cgroup
/dev/sda1       511M  3.6M  508M   1% /boot/efi
cgmfs           100K     0  100K   0% /run/cgmanager/fs
tmpfs           787M   88K  787M   1% /run/user/1000
/dev/mmcblk0p2   15G   11G  2.6G  82% /media/nick/13d368bf-6dbf-4751-8ba1-88bed06bef77
/dev/mmcblk0p1   56M   22M   35M  38% /media/nick/boot

```

sudo lsblk -f

```

NAME        FSTYPE LABEL UUID                                 MOUNTPOINT
sda                                                           
&#9500;&#9472;sda1      vfat         8045-A6E8                            /boot/efi
&#9500;&#9472;sda2      swap         d2b9eabf-fa1d-4505-8089-315c91294626 [SWAP]
&#9500;&#9472;sda3      ext4         fc6ba7f7-f6ac-4257-84be-4218bd3d8eca 
&#9492;&#9472;sda4      ext4         e3c8999d-c31a-4864-acb9-7d1d8278ed43 /
sdb                                                           
&#9500;&#9472;sdb1      vfat         02A3-A00E                            
&#9500;&#9472;sdb2      ntfs         57CAA0CB19D78A9C                     
&#9492;&#9472;sdb3      ntfs         9E403D7D403D5D69                     
sr0                                                           
mmcblk0                                                       
&#9500;&#9472;mmcblk0p1 vfat   boot  15CD-3B79                            /media/nick/boot
&#9492;&#9472;mmcblk0p2 ext4         13d368bf-6dbf-4751-8ba1-88bed06bef77 /media/nick/13d368bf-6dbf-4751-8ba1-88bed06bef77

```

sudo lsblk -m
```

NAME          SIZE OWNER GROUP MODE
sda         111.8G root  disk  brw-rw----
&#9500;&#9472;sda1        512M root  disk  brw-rw----
&#9500;&#9472;sda2        7.5G root  disk  brw-rw----
&#9500;&#9472;sda3       75.5G root  disk  brw-rw----
&#9492;&#9472;sda4       28.4G root  disk  brw-rw----
sdb         931.5G root  disk  brw-rw----
&#9500;&#9472;sdb1        512M root  disk  brw-rw----
&#9500;&#9472;sdb2      926.6G root  disk  brw-rw----
&#9492;&#9472;sdb3        508M root  disk  brw-rw----
sr0          1024M root  cdrom brw-rw----
mmcblk0      14.5G root  disk  brw-rw----
&#9500;&#9472;mmcblk0p1    56M root  disk  brw-rw----
&#9492;&#9472;mmcblk0p2  14.4G root  disk  brw-rw----

```



sudo parted -ls
```

Model: ATA Samsung SSD 840 (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 


Number  Start   End     Size    File system     Name                  Flags
 1      1049kB  538MB   537MB   fat32           EFI System Partition  boot, esp
 4      538MB   31.0GB  30.5GB  ext4
 2      31.0GB  39.0GB  8002MB  linux-swap(v1)
 3      39.0GB  120GB   81.0GB  ext4




Model: ATA TOSHIBA MQ01ABD1 (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 


Number  Start   End    Size   File system  Name  Flags
 1      1049kB  538MB  537MB  fat32              boot, esp
 2      538MB   996GB  995GB  ntfs               msftdata
 3      996GB   996GB  533MB  ntfs               hidden, diag




Model: SD SL16G (sd/mmc)
Disk /dev/mmcblk0: 15.5GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 


Number  Start   End     Size    Type     File system  Flags
 1      4194kB  62.9MB  58.7MB  primary  fat16        lba
 2      62.9MB  15.5GB  15.5GB  primary  ext4

```

Thanks for the help guys. I suspect its really jsut a simple permission issue that anyone who know their linux101 can solve in 2 minutes.
Unfortunately I am not very proficient yet and just started tingling lately

---

### Post by darkod on 2016-10-23
Yes, as you can see from the ls -al results the folder is owned by www-data. And only that user can RW the folder.
But you can always use your sudo rights and copy the content or change the ownership to another user.

---

