---
title: "Issue with disk resize"
date: 2014-12-24
forum: Server Platforms
---

### Post by skalra63 on 2014-12-24
I am a linux novice and have just installed Ubuntu Server 14.04 as a Hyper-v Virtual Machine.
I have 2 dynamic VHD files configured  - one for OS and one for Data.
Webmin is installed.
I have also mounted the data drive 

I then found some extra data I forgot to take into account so needed to expand the Data drive.
I turned off the server and expanded the disk from 50GB to 100GB.
Webmin showed that the drive was bigger but I wasnt able to modify the partiton size (not sure if that is a webmin limitation) so I used parted instead. I hit a few problems.

I was unable to exand the partition (it only gave me a max of 50GB I could set as the "end"). As i hadnt transferred any data yet I deleted the old partition and created a small one (as a test). Again I tried to expand it but it wouldnt allow me to expand it past the point i set as "end". I removed it and created a partition to fill the disk. It had the same partition ID as when I configured the mount, so it mounted ok.

Parted and webmin show this partition to be 100GB however, via samba it is showing the same 50GB and so I am unable to transfer all the data.

Does anyone have any idea why it does this?

---

### Post by volkswagner on 2014-12-24
Post output of the following commands:
```
sudo fdisk -l
```
```
sudo blkid
```
```
cat /etc/fstab
```

---

### Post by skalra63 on 2014-12-24
```
sudo fdisk -l
```


Disk /dev/sda: 32.2 GB, 32212254720 bytes
255 heads, 63 sectors/track, 3916 cylinders, total 62914560 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1    62914559    31457279+  ee  GPT


Disk /dev/sdb: 107.4 GB, 107374182400 bytes
255 heads, 63 sectors/track, 13054 cylinders, total 209715200 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1   209715199   104857599+  ee  GPT


```
sudo blkid
```

/dev/sda1: UUID="C0C1-1333" TYPE="vfat" 
/dev/sda2: UUID="54d7cd56-9b4a-4c94-a1a3-237c25c14481" TYPE="ext4" 
/dev/sda3: UUID="e10f424a-61e9-4009-a26c-1c1505c9af93" TYPE="swap" 
/dev/sdb1: UUID="b4cea237-75d0-4657-8b38-0195a343416a" TYPE="ext4" 


```
cat /etc/fstab
```

# / was on /dev/sda2 during installation
UUID=54d7cd56-9b4a-4c94-a1a3-237c25c14481 / ext4 errors=remount-ro 0 1
# /boot/efi was on /dev/sda1 during installation
UUID=C0C1-1333 /boot/efi vfat defaults 0 1
# swap was on /dev/sda3 during installation
UUID=e10f424a-61e9-4009-a26c-1c1505c9af93 none swap sw 0 0
/dev/sdb1 /mnt/sab ext4 defaults 0 0

---

### Post by skalra63 on 2014-12-24
ive also run

```
sudo df -h
```

Filesystem      Size  Used Avail Use% Mounted on
/dev/sda2        28G  2.0G   25G   8% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            482M   12K  482M   1% /dev
tmpfs            99M  524K   98M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            493M     0  493M   0% /run/shm
none            100M     0  100M   0% /run/user
/dev/sda1       511M  3.4M  508M   1% /boot/efi
/dev/sdb1        50G   47G   35M 100% /mnt/sab


As you can see it seems to think that /mnt/sab only has 50GB total space despite /dev/sdb1 showing 100GB in fdisk

---

### Post by westie457 on 2014-12-24
Could you also post the result of ```
sudo parted -l
```

---

### Post by skalra63 on 2014-12-25
```
sudo parted -l
```

Model: Msft Virtual Disk (scsi)
Disk /dev/sda: 32.2GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt


Number  Start   End     Size    File system     Name  Flags
 1      1049kB  538MB   537MB   fat32                 boot
 2      538MB   31.1GB  30.6GB  ext4
 3      31.1GB  32.2GB  1070MB  linux-swap(v1)




Model: Msft Virtual Disk (scsi)
Disk /dev/sdb: 107GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt


Number  Start   End    Size   File system  Name  Flags
 1      1049kB  102GB  102GB  ext4

---

### Post by westie457 on 2014-12-25
Just re-read the original post, now my understanding of the situation is you have created an Ubuntu Virtual machine that is running under Windows. Is this correct?
My very limited experience of VM's means that I will not be very much help, especially where Hyper-v is concerned (never used it).
AFAIK the only way to increase the size of a virtual drive/partition is to wipe it and create a new one to the required size.
Also you might get better help if this thread is moved to the Virtualzation Forum.

---

### Post by skalra63 on 2014-12-25
I have already removed the partition from the disk and recreated it with the correct, larger size (in the original post). 

The issue is not that I have resized the VHD and it is not showing the new size in Ubuntu, as you can see it is showing the correct size (100GB) in parted but in samba it is only showing the original size partition size (50GB)

---

### Post by skalra63 on 2014-12-25
another update....

i removed /dev/sdb1. Created /dev/sdb1 10GB, created /dev/sdb2 90GB.

Mounted /dev/sdb2 to /mnt/test and ran df -h. It showed the correct size.

I removed /dev/sdb1 & /dev/sdb2 and created /dev/sdb1 100GB

Mounted /dev/sdb1 to /mnt/test and ran df -h. It shows only 50GB again (the original partition size). Curiously it also says that there is 47GB used again.

---

### Post by volkswagner on 2014-12-25
Are you formatting after creating the partitions? Perhaps mounting using the UUID will help? I'm not well schooled on inodes, but it sounds like something is not flushing the partition table. 

Are you using fdisk to create partitions? I'd try using fdisk to create empty msdos partition table, then add 1 partition using 100%. You'll then need to create the Ext4 filesystem.

Perhaps a workaround would be to create a small sdb1 and large sdb2 then mount sdb2 instead.

---

### Post by skalra63 on 2014-12-26
Thanks Volkswagner. Your reply was extremely helpful.

Being a Windows user I assumed that increasing the partition size in linux would make the whole partition usable (as in windows). Turns out that isn't the case. I googled regarding the file system and found i also needed to run e2fsck -f /dev/sdb1 and then resize2fs /dev/sdb1

df -h now shows 99GB of space and hasn't deleted the data.

---

