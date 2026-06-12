---
title: "Fix Bad Sector on HDD/Partitions Not Mounting"
date: 2018-11-14
forum: Virtualisation
---

### Post by chaun-a on 2018-11-14
Hi,

I would like some help with recovering data / fixing bad sector from my Seagate HDD originally formatted on a Mac in HFS+. The device (2TB, 2 partitions) isn't recognized nor able to mount on either platform (mac, pc, linux) after it was disconnected without being properly ejected. Note that I'm running ubuntu on a mac using VM Ware, not sure how this can affect the results. 
Here is the output I get with command 'sudo fdisk -l':

thch@ubuntu:~$ sudo fdisk -l
[sudo] password for thch: 
```
Disk /dev/loop0: 87.9 MiB, 92123136 bytes, 179928 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop1: 140.9 MiB, 147722240 bytes, 288520 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop2: 2.3 MiB, 2355200 bytes, 4600 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop3: 13 MiB, 13619200 bytes, 26600 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop4: 14.5 MiB, 15208448 bytes, 29704 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop5: 3.7 MiB, 3878912 bytes, 7576 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop6: 42.1 MiB, 44183552 bytes, 86296 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop7: 87.9 MiB, 92114944 bytes, 179912 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes








Disk /dev/sda: 20 GiB, 21474836480 bytes, 41943040 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xc954e4e2


Device     Boot Start      End  Sectors Size Id Type
/dev/sda1  *     2048 41940991 41938944  20G 83 Linux




Disk /dev/loop8: 2.3 MiB, 2355200 bytes, 4600 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop9: 13 MiB, 13619200 bytes, 26600 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop10: 34.2 MiB, 35827712 bytes, 69976 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop11: 140.7 MiB, 147496960 bytes, 288080 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
```

Here is a snap of the output I get with command 'dmesg':
[ATTACH=CONFIG]281629[/ATTACH]

I really hope this can be fixed, any help would be much appreciated.
Thanks.

---

### Post by Autodave on 2018-11-14
Hopefully someone else will have better info for you, but whenever I see that Block 0 is bad, there is not usually much that you can do with it.

---

### Post by chaun-a on 2018-11-14
I believe Block 0 was from the floppy disk that wasn't deactivated. Here is a snap of the output I get with command '[COLOR=#000000]dmesg[/COLOR]' with fd 0 blacklisted:
[ATTACH=CONFIG]281637[/ATTACH]
Nothing new with command 
[COLOR=#000000]'sudo fdisk -l'[/COLOR]

Anyone know what can be done at this point?
Thanks

---

### Post by deadflowr on 2018-11-14
You're running a virtual machine? (VMWare?)

---

### Post by chaun-a on 2018-11-14
correct, VM Ware, does it affect in anyway?

---

### Post by deadflowr on 2018-11-15
*Thread moved to **Virtualization***

---

