---
title: "SD card read only"
date: 2016-02-23
forum: Ubuntu Phone and Tablet
---

### Post by regis-sarle on 2016-02-23
Hello,

I'm using an Ubuntu phone since about one year (Aquaris E4.5 Ubuntu edition), but I'm facing a new problem with access rights on the SD Card.
Some weeks ago, I could no longer save my pictures on SD card. I thought it was full. I made some space on it from my Ubuntu desktop. Since, I can't have write rights on it.

From the file manager, after getting full access (from proprieties on top right), it is showing permissions : read, execute. I can't create a folder or copy a file.
From Ubuntu Desktop or terminal, I can't copy a file :
```
phablet@ubuntu-phablet:~$ cp Documents/log.html /media/phablet/2E17-4957/
cp: cannot create regular file ‘/media/phablet/2E17-4957/log.html’: Read-only file system

```

I tryed to add the user phablet in the disk group (from another post), but it fails to solve the problem. 

It seems that the card is locked (I checked if there is an hardware protection but it's not).

Flashing a new Ubuntu doesn't solve the problem.

Can you help me ?

FI: I sometimes use tether with : "sudo adb shell android-gadget-service enable rndis" I don't know if it's related.

Thanks.

EDIT : result of fdisk -l :
```
phablet@ubuntu-phablet:~$ sudo fdisk -l

Disk /dev/loop0: 144,4 MiB, 151416832 bytes, 295736 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk /dev/zram0: 512 MiB, 536870912 bytes, 131072 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Ignoring extra data in partition table 5.
Ignoring extra data in partition table 5.

Disk /dev/mmcblk0: 7,3 GiB, 7787773952 bytes, 15210496 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00000000

Device         Boot  Start        End    Sectors  Size Id Type
/dev/mmcblk0p1        1024 4294968318 4294967295    2T  5 Extended
/dev/mmcblk0p2       18432      38911      20480   10M 83 Linux
/dev/mmcblk0p3       38912      59391      20480   10M 83 Linux
/dev/mmcblk0p4      142336     154623      12288    6M 83 Linux
/dev/mmcblk0p5      182272    1615871    1433600  700M 83 Linux

Disk /dev/mmcblk0boot1: 4 MiB, 4194304 bytes, 8192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk /dev/mmcblk0boot0: 4 MiB, 4194304 bytes, 8192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk /dev/mmcblk1: 7,4 GiB, 7969177600 bytes, 15564800 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00000000

Device         Boot Start      End  Sectors  Size Id Type
/dev/mmcblk1p1       8192 15564799 15556608  7,4G  b W95 FAT32


```

---

### Post by regis-sarle on 2016-02-25
Hi,

My SD Card was in fact dying. It was the same case in any other device. After replacing it, no problem.

---

