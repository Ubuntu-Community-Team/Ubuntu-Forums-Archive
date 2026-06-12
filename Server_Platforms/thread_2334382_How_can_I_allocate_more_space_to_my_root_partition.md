---
title: "How can I allocate more space to my root partition?"
date: 2016-08-19
forum: Server Platforms
---

### Post by sazzadhussein on 2016-08-19
My Ubuntu machine's root partition is above 80% full.
```
xxxx@dberc-repo:~$ df -h
Filesystem                          Size  Used Avail Use% Mounted on
udev                                 79G   12K   79G   1% /dev
tmpfs                                16G  1.3M   16G   1% /run
/dev/mapper/dell--dev--02--vg-root  117G   88G   24G  80% /
none                                4.0K     0  4.0K   0% /sys/fs/cgroup
none                                5.0M     0  5.0M   0% /run/lock
none                                 79G  7.0M   79G   1% /run/shm
none                                100M     0  100M   0% /run/user /dev/sda1                           236M  100M  124M  45% /boot
```

But I can still see that, there are some other partitions (/run/shm or /run), which have space to spare.
Can anyone suggest how I can allocate some of the free space to my root partition?

---

### Post by darkod on 2016-08-19
Those do not seem like partitions. The /run/shm is the mount point, the partition name would be the first column and that says 'none'.

How big is your hdd?

Please post the output of:
```
sudo parted /dev/sda unit MiB print
sudo vgdisplay
sudo lvdisplay
```

---

### Post by ajgreeny on 2016-08-19
I wonder if you are using LVM partitioning for your system?

Please show the output of command **mount** in code tags.
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by sazzadhussein on 2016-08-19
Hi Darko,
Please find the output here in bellow:
> xxx@dberc-repo:~$ sudo parted /dev/sda unit MiB print[sudo] password for xxx: 
Model: DELL PERC H730 Mini (scsi)
Disk /dev/sda: 285568MiB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start    End        Size       Type      File system  Flags
 1      1.00MiB  244MiB     243MiB     primary   ext2         boot
 2      245MiB   285567MiB  285322MiB  extended
 5      245MiB   285567MiB  285322MiB  logical                lvm


 
 
 xxx@dberc-repo:~$ sudo vgdisplay
  --- Volume group ---
  VG Name               dell-dev-02-vg
  System ID             
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  3
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                2
  Open LV               2
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               278.63 GiB
  PE Size               4.00 MiB
  Total PE              71330
  Alloc PE / Size       71330 / 278.63 GiB
  Free  PE / Size       0 / 0   
  VG UUID               QKd7dj-o2Y4-d3Cg-zZds-ro5A-kkaV-CJkTo1
  
  
  xxx@dberc-repo:~$ sudo lvdisplay
  --- Logical volume ---
  LV Path                /dev/dell-dev-02-vg/root
  LV Name                root
  VG Name                dell-dev-02-vg
  LV UUID                9aaEVd-0RDp-9PFB-gubx-4zwa-0Me0-CdCYo7
  LV Write Access        read/write
  LV Creation host, time dell-dev-02, 2015-08-31 18:51:27 +0200
  LV Status              available
  # open                 1
  LV Size                118.73 GiB
  Current LE             30394
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:0
   
  --- Logical volume ---
  LV Path                /dev/dell-dev-02-vg/swap_1
  LV Name                swap_1
  VG Name                dell-dev-02-vg
  LV UUID                f10YZd-QrB6-71RY-WL5y-gbAz-G0Mx-L7cNXi
  LV Write Access        read/write
  LV Creation host, time dell-dev-02, 2015-08-31 18:51:27 +0200
  LV Status              available
  # open                 2
  LV Size                159.91 GiB
  Current LE             40936
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:1

---

### Post by sazzadhussein on 2016-08-19
Hi ajgreeny,
It's a LVM partitioning system.
> xxx@dberc-repo:~$ sudo fdisk -l

Disk /dev/sda: 299.4 GB, 299439751168 bytes
255 heads, 63 sectors/track, 36404 cylinders, total 584843264 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e9776


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758   584841215   292169729    5  Extended
/dev/sda5          501760   584841215   292169728   8e  Linux LVM


Disk /dev/mapper/dell--dev--02--vg-root: 127.5 GB, 127481675776 bytes
255 heads, 63 sectors/track, 15498 cylinders, total 248987648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/mapper/dell--dev--02--vg-root doesn't contain a valid partition table


Disk /dev/mapper/dell--dev--02--vg-swap_1: 171.7 GB, 171698028544 bytes
255 heads, 63 sectors/track, 20874 cylinders, total 335347712 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/mapper/dell--dev--02--vg-swap_1 doesn't contain a valid partition table

---

### Post by darkod on 2016-08-19
As it is, you can't expand the root LV. If you check the vgdisplay "Free PE" value, it says 0 free extents.

This is because you made swap LV too big. Check the lvdisplay output. You assigned 118GB for root LV and 160GB for swap LV.

That is way too much for swap. Usually for swap you need around 1.5 x the amount of memory, and sometimes even that is too much.

You need to unmount swap temporarily (swapoff) and reduce the swap LV. That will give you free extents in the VG and you can expand the root LV.

If you need exact commands for all that, ask, but google has enough tutorials of LVM procedures.

---

### Post by sazzadhussein on 2016-08-19
Thank you for your quick reply!
I'm going to drill down from google first & prepare a procedure first.
Then i will upload the document & may be you will have a short overview on that?
Just need to make sure everything goes well.
I'll get back to you very soon!

---

### Post by sazzadhussein on 2016-08-19
Worth to be mention, i just have checked that the machine is having 157GB of RAM:

```
sysadm@dberc-repo:~$ free -g             total       used       free     shared    buffers     cached
Mem:           157         96         60          0          0         80
-/+ buffers/cache:         15        141
Swap:          159          0        159
```

So, do you think it's ok get space from the swap partition?
As swap is allocated almost same space as the RAM on that machine!

---

### Post by darkod on 2016-08-19
The rule about swap and RAM is approximate and the more RAM you have the less probability swap to be used at all. That's why in your case with 157GB of RAM it doesn't mean you need 160GB of swap.

In fact, the beauty of LVM is that you don't need to extend any LV unless it is really necessary. Your root LV still has 20% free which is not little. So what you can do is this:
1. Shrink the swap LV to 32GB for example.
2. Leave the free space as free in the VG, no need to extend the root LV.
3. If in the future you see that you need more swap, you can assign part of the free space to it. And another part to the root.

But don't assign everything right away. In LVM you assign as much as you need and keep the rest available. That avoids situations like the one you have now. root which is 80% full and big swap that is not even being used at all.

---

