---
title: "Can't boot Debian. No init found"
date: 2018-10-18
forum: Ubuntu/Debian BASED
---

### Post by obake2 on 2018-10-18
Two days ago I did a forced shutdown when I was doing an update. The laptop computer hanged completely as I couldn't kill the X. When I rebooted, it showed that error. I am attaching a photo with the full-message. I'm sorry for any spelling mistake as I am typing very awkwardly on a tablet. 

The OS: Debian Linux
FileSystem: Btrfs
Busybox: 1.27.2

I don't have a raid system. just a single SSD. 

EDIT 2:  When trying to access the local SSD drive with Nautilus from  Ubuntu Mate LiveUSB , it showed an error that says "can't read  superblock"  Screenshot is attached.


EDIT: I have wifi connection in my laptop now so I will add the following info:

```
ubuntu-mate@ubuntu-mate:~$ sudo fdisk -l
Disk /dev/loop0: 1.8 GiB, 1917960192 bytes, 3746016 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 86.9 MiB, 91099136 bytes, 177928 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 7.9 MiB, 8294400 bytes, 16200 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 71.7 MiB, 75120640 bytes, 146720 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 86.7 MiB, 90923008 bytes, 177584 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 87.9 MiB, 92123136 bytes, 179928 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 87.1 MiB, 91308032 bytes, 178336 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 223.6 GiB, 240057409536 bytes, 468862128 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xbc74177d

Device     Boot Start       End   Sectors   Size Id Type
/dev/sda1        2048 468860927 468858880 223.6G 83 Linux


Disk /dev/sdb: 28.8 GiB, 30943995904 bytes, 60437492 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x4ad90688

Device     Boot   Start     End Sectors  Size Id Type
/dev/sdb1  *          0 3920639 3920640  1.9G  0 Empty
/dev/sdb2       3841944 3846615    4672  2.3M ef EFI (FAT-12/16/32)


Disk /dev/mapper/luks-277f3ea3-9750-401f-849d-df29fc26cf26: 223.6 GiB, 240053649408 bytes, 468854784 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mapper/matrix-rootvol: 221.7 GiB, 238001586176 bytes, 464846848 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mapper/matrix-swap: 1.9 GiB, 2051014656 bytes, 4005888 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
ubuntu-mate@ubuntu-mate:~$ 


```

```
ubuntu-mate@ubuntu-mate:~$ df
Filesystem     1K-blocks    Used Available Use% Mounted on
udev             4044156       0   4044156   0% /dev
tmpfs             813068    1356    811712   1% /run
/dev/sdb         1960320 1960320         0 100% /cdrom
/dev/loop0       1873024 1873024         0 100% /rofs
/cow             4065340  293116   3772224   8% /
tmpfs            4065340       0   4065340   0% /dev/shm
tmpfs               5120       4      5116   1% /run/lock
tmpfs            4065340       0   4065340   0% /sys/fs/cgroup
tmpfs            4065340       4   4065336   1% /tmp
tmpfs             813068      56    813012   1% /run/user/999
/dev/loop1         89088   89088         0 100% /snap/core/4917
/dev/loop2          8192    8192         0 100% /snap/pulsemixer/23
/dev/loop3         73472   73472         0 100% /snap/software-boutique/31
/dev/loop4         88832   88832         0 100% /snap/ubuntu-mate-welcome/169


```

```
ubuntu-mate@ubuntu-mate:~$ lsblk
NAME                                          MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
loop0                                           7:0    0   1.8G  1 loop  /rofs
loop1                                           7:1    0  86.9M  1 loop  /snap/core/4917
loop2                                           7:2    0   7.9M  1 loop  /snap/pulsemixer/23
loop3                                           7:3    0  71.7M  1 loop  /snap/software-boutique/31
loop4                                           7:4    0  86.7M  1 loop  /snap/ubuntu-mate-welcome/169
sda                                             8:0    0 223.6G  0 disk  
&#9492;&#9472;sda1                                          8:1    0 223.6G  0 part  
  &#9492;&#9472;luks-277f3ea3-9750-401f-849d-df29fc26cf26 253:0    0 223.6G  0 crypt 
    &#9500;&#9472;matrix-rootvol                          253:1    0 221.7G  0 lvm   
    &#9492;&#9472;matrix-swap                             253:2    0   1.9G  0 lvm   
sdb                                             8:16   1  28.8G  0 disk  /cdrom
&#9500;&#9472;sdb1                                          8:17   1   1.9G  0 part  
&#9492;&#9472;sdb2                                          8:18   1   2.3M  0 part  
ubuntu-mate@ubuntu-mate:~$ 


```

---

