---
title: "ubuntu server raid share"
date: 2015-04-13
forum: Server Platforms
---

### Post by amerinde on 2015-04-13
I need a bit of help. when i ran ubuntu desktop 14, i made a raid5, set it to /storage for network access, it worked, i changed over to ubuntu server 14, made the same setup, but have no access. I can see /storage, but wont let me access it... can anyone help? BTW.. i have changed the file permissions, but on reboot, it always goes back to the default- only root...

---

### Post by nerdtron on 2015-04-15
What type of share is this? samba? nfs? what is your config on the desktop? is it the same on the config of the server?

---

### Post by darkod on 2015-04-16
What are the current permissions of storage?

---

### Post by amerinde on 2015-04-17
> **darkod said:**
> What are the current permissions of storage?

> ls -l /storage
total 24
drwx------ 2 ME adm 16384 Apr 13 13:30 lost+found
drwxr-xr-x 2 ME adm  4096 Apr 14 22:46 private
drwxr-xr-x 2 ME adm  4096 Apr 14 22:46 public

---

### Post by amerinde on 2015-04-17
> **nerdtron said:**
> What type of share is this? samba? nfs? what is your config on the desktop? is it the same on the config of the server?

It is a Samba share, i set up the server the same as i did the desktop. I dont have the desktop anymore, i loaded the server in its place. So, i cant be 100% sure, but i am 98% sure i set it up all the same.

---

### Post by amerinde on 2015-04-17
funny thing, i just did "ls -l /". It is showing two files called storage. 

drwxrwxr--   2 root    root  4096 Apr 13 23:10 STORAGE
drwxr-xr-x   5 ME adm   4096 Apr 14 22:46 storage

---

### Post by amerinde on 2015-04-17
i did df -h and fdisk -l... i dont know what /dev/mapper/ubuntu+ is... can someone help out.. sd[a-d] is my raid storage, sde is my windows7 SSD and sdf is my ubuntu server SSD.


> df -h /storage
Filesystem      Size  Used Avail Use% Mounted on
/dev/md0         11T   61M   11T   1% /storage
> df -h /STORAGE
Filesystem                   Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--vg-root  102G  1.9G   95G   2% /
> fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.

Disk /dev/sdb doesn't contain a valid partition table

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.

Disk /dev/sdc doesn't contain a valid partition table

WARNING: GPT (GUID Partition Table) detected on '/dev/sdd'! The util fdisk doesn't support GPT. Use GNU Parted.

Disk /dev/sdd doesn't contain a valid partition table
Disk /dev/md0 doesn't contain a valid partition table
Disk /dev/mapper/ubuntu--vg-root doesn't contain a valid partition table
Disk /dev/mapper/ubuntu--vg-swap_1 doesn't contain a valid partition table

Disk /dev/sda: 4000.8 GB, 4000787030016 bytes
255 heads, 63 sectors/track, 486401 cylinders, total 7814037168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdb: 4000.8 GB, 4000787030016 bytes
255 heads, 63 sectors/track, 486401 cylinders, total 7814037168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000


Disk /dev/sdc: 4000.8 GB, 4000787030016 bytes
255 heads, 63 sectors/track, 486401 cylinders, total 7814037168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000


Disk /dev/sdd: 4000.8 GB, 4000787030016 bytes
255 heads, 63 sectors/track, 486401 cylinders, total 7814037168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000


Disk /dev/sde: 240.1 GB, 240057409536 bytes
255 heads, 63 sectors/track, 29185 cylinders, total 468862128 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002bb7c

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sde2          206848   468858879   234326016    7  HPFS/NTFS/exFAT

Disk /dev/sdf: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001241d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *        2048      499711      248832   83  Linux
/dev/sdf2          501758   234440703   116969473    5  Extended
/dev/sdf5          501760   234440703   116969472   8e  Linux LVM

Disk /dev/md0: 12002.0 GB, 12001957380096 bytes
2 heads, 4 sectors/track, -1364801920 cylinders, total 23441323008 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 524288 bytes / 1572864 bytes
Disk identifier: 0x00000000


Disk /dev/mapper/ubuntu--vg-root: 111.2 GB, 111190999040 bytes
255 heads, 63 sectors/track, 13518 cylinders, total 217169920 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/mapper/ubuntu--vg-swap_1: 8581 MB, 8581545984 bytes
255 heads, 63 sectors/track, 1043 cylinders, total 16760832 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

---

### Post by darkod on 2015-04-17
If you told the server installer to use LVM, the device names created by LVM are /dev/mapper/VGname-LVname...

Did you make a manual entry in /etc/fstab to mount /dev/md0 at /storage?

Please post the output of:
```
sudo pvdisplay
sudo vgdisplay
cat /proc/mdstat
cat /etc/fstab
```

---

### Post by darkod on 2015-04-17
If you told the server installer to use LVM, the device names created by LVM are /dev/mapper/VGname-LVname...

Did you make a manual entry in /etc/fstab to mount /dev/md0 at /storage?

Please post the output of:
```

sudo pvdisplay
sudo vgdisplay
cat /proc/mdstat
cat /etc/fstab
```

---

### Post by amerinde on 2015-04-17
> **darkod said:**
> If you told the server installer to use LVM, the device names created by LVM are /dev/mapper/VGname-LVname...

Did you make a manual entry in /etc/fstab to mount /dev/md0 at /storage?

Please post the output of:
```

sudo pvdisplay
sudo vgdisplay
cat /proc/mdstat
cat /etc/fstab
```

yes, i manually add to fstab

> sudo pvdisplay
  --- Physical volume ---
  PV Name               /dev/sdf5
  VG Name               ubuntu-vg
  PV Size               111.55 GiB / not usable 4.00 MiB
  Allocatable           yes (but full)
  PE Size               4.00 MiB
  Total PE              28556
  Free PE               0
  Allocated PE          28556
  PV UUID               qCYG5u-B1j1-s03C-CeVr-ClPx-Ooim-DMga3b
   
> sudo vgdisplay
  --- Volume group ---
  VG Name               ubuntu-vg
  System ID             
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  3
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                2
  Open LV               1
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               111.55 GiB
  PE Size               4.00 MiB
  Total PE              28556
  Alloc PE / Size       28556 / 111.55 GiB
  Free  PE / Size       0 / 0   
  VG UUID               g2CDdo-Hb7H-549p-adfX-BVJb-aPU4-85EPvn
   
> cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sdd[4] sda[0] sdc[2] sdb[1]
      11720661504 blocks super 1.2 level 5, 512k chunk, algorithm 2 [4/4] [UUUU]
      
unused devices: <none>
> cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
#/dev/mapper/ubuntu--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sdf1 during installation
UUID=46cfce91-529f-48a4-b0f9-b1a99c5f59db /boot           ext2    defaults        0       2
#/dev/mapper/ubuntu--vg-swap_1 none            swap    sw              0       0
/dev/md0    /storage    ext4    user,resgid=100    0    0

---

### Post by amerinde on 2015-04-17
is the mapper the reason, everthing goes back to root access only? can I, and how can i remove it

---

### Post by darkod on 2015-04-17
Why do you have the vg-root and vg-swap_1 disabled in fstab? Did you do that manually?

No, the LVM is not the reason. You can't remove it unless you reinstall again. Rather, it looks like your fstab entries are little messed up. I don't even see a root entry since vg-root is commented.

Also, is there a reason you are mounting md0 with those options (user,resgid=100)? Why not the defaults?

---

### Post by amerinde on 2015-04-17
> **amerinde said:**
> yes, i manually add to fstab

> sudo pvdisplay
  --- Physical volume ---
  PV Name               /dev/sdf5
  VG Name               ubuntu-vg
  PV Size               111.55 GiB / not usable 4.00 MiB
  Allocatable           yes (but full)
  PE Size               4.00 MiB
  Total PE              28556
  Free PE               0
  Allocated PE          28556
  PV UUID               qCYG5u-B1j1-s03C-CeVr-ClPx-Ooim-DMga3b
   
> sudo vgdisplay
  --- Volume group ---
  VG Name               ubuntu-vg
  System ID             
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  3
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                2
  Open LV               1
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               111.55 GiB
  PE Size               4.00 MiB
  Total PE              28556
  Alloc PE / Size       28556 / 111.55 GiB
  Free  PE / Size       0 / 0   
  VG UUID               g2CDdo-Hb7H-549p-adfX-BVJb-aPU4-85EPvn
   
> cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sdd[4] sda[0] sdc[2] sdb[1]
      11720661504 blocks super 1.2 level 5, 512k chunk, algorithm 2 [4/4] [UUUU]
      
unused devices: <none>
> cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
#/dev/mapper/ubuntu--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sdf1 during installation
UUID=46cfce91-529f-48a4-b0f9-b1a99c5f59db /boot           ext2    defaults        0       2
#/dev/mapper/ubuntu--vg-swap_1 none            swap    sw              0       0
/dev/md0    /storage    ext4    user,resgid=100    0    0

yes, i manually commented mapper, trying to disable them, actually forgot i did that... didnt notice /dev/md0 comments... thats not whati i entererd.. in the beginning i entered 

/dev/md0        /storage            ext4        defaults        0        0

i followed this ex.  [http://zackreed.me/articles/38-software-raid-5-in-debian-with-mdadm](http://zackreed.me/articles/38-software-raid-5-in-debian-with-mdadm)

---

### Post by darkod on 2015-04-18
I don't even understand how it's booting right now, since you disabled the root in fstab. Here is what you need to try:

1. In fstab enable the vg-root and vg-swap (remove the # sign in front).
2. For /dev/md0 make the entry with 'defaults', like you had it earlier.

Save the changes and reboot. See how it boots and check mounted partitions with:
```
df -h
```

Also check the LVM running LVs with:
```
 sudo lvdisplay
```

That should show two running LVs, the root and swap.

---

### Post by amerinde on 2015-04-18
> df -h
Filesystem                   Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--vg-root  102G  1.9G   95G   2% /
none                         4.0K     0  4.0K   0% /sys/fs/cgroup
udev                         3.9G  4.0K  3.9G   1% /dev
tmpfs                        798M  1.2M  797M   1% /run
none                         5.0M     0  5.0M   0% /run/lock
none                         3.9G     0  3.9G   0% /run/shm
none                         100M     0  100M   0% /run/user
/dev/sdf1                    236M   69M  155M  31% /boot
/dev/md0                      11T   61M   11T   1% /storage
> sudo lvdisplay
  --- Logical volume ---
  LV Path                /dev/ubuntu-vg/root
  LV Name                root
  VG Name                ubuntu-vg
  LV UUID                5rdiBc-pLD3-cedD-MNK5-xYKO-3430-DGUQ7j
  LV Write Access        read/write
  LV Creation host, time ubuntu, 2015-04-11 18:56:51 +0200
  LV Status              available
  # open                 1
  LV Size                103.55 GiB
  Current LE             26510
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:0
   
  --- Logical volume ---
  LV Path                /dev/ubuntu-vg/swap_1
  LV Name                swap_1
  VG Name                ubuntu-vg
  LV UUID                tFSIh6-JYpj-dc8C-k26u-cZsq-63Fl-eZpkgT
  LV Write Access        read/write
  LV Creation host, time ubuntu, 2015-04-11 18:56:51 +0200
  LV Status              available
  # open                 2
  LV Size                7.99 GiB
  Current LE             2046
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:1

---

### Post by darkod on 2015-04-18
That looks much better now. You didn't say is the server working as expected now?

You can check the /storage permissions and ownerwhip again with:
```
ls -l /
```

After that you can change the permissions/ownership as per your needs.

---

### Post by amerinde on 2015-04-18
> **darkod said:**
> That looks much better now. You didn't say is the server working as expected now?

You can check the /storage permissions and ownerwhip again with:
```
ls -l /
```

After that you can change the permissions/ownership as per your needs.

Yes, thank you darkod, i was able to set the permissions and have them after reboot.. But, i also removed the /STORAGE DIR. i think having 2 folders the same, it was messing up my permissions. Now, to access the files from the web.

---

