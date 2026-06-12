---
title: "Can a hard drive partition be expanded after install?"
date: 2021-10-25
forum: Server Platforms
---

### Post by mw4jet on 2021-10-25
I installed my Ubuntu server 20.04 on a 4TB drive and chose to use entire disk, now after I spent all dat setting it up I see it only shows its using a couple hundred gigs.

Can I expand the partition or must I re-install and manually choose directory sizes on install?

---

### Post by CharlesA on 2021-10-25
That depends - did you select LVM during install?

Run this and post the output:

```
sudo fdisk -l
```

---

### Post by mw4jet on 2021-10-25
I have not tried to post "code" before so I hope it works right. I think is 

```
mark123@4jetserver:~$ sudo fdisk -l[sudo] password for mark123:
Disk /dev/loop0: 54.98 MiB, 57626624 bytes, 112552 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop1: 55.45 MiB, 58130432 bytes, 113536 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop2: 32.45 MiB, 34017280 bytes, 66440 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop3: 71.28 MiB, 74735616 bytes, 145968 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop4: 29.9 MiB, 31334400 bytes, 61200 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop5: 67.26 MiB, 70516736 bytes, 137728 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop6: 61.85 MiB, 64835584 bytes, 126632 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/sda: 3.65 TiB, 4000787030016 bytes, 7814037168 sectors
Disk model: WDC WD40EFAX-68J
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 144D53EA-9AEE-43B7-AEEA-B98BF8D74DA1


Device       Start        End    Sectors  Size Type
/dev/sda1     2048       4095       2048    1M BIOS boot
/dev/sda2     4096    2101247    2097152    1G Linux filesystem
/dev/sda3  2101248 7814033407 7811932160  3.7T Linux filesystem




Disk /dev/sdb: 2.75 TiB, 3000592982016 bytes, 5860533168 sectors
Disk model: ST3000DM001-1ER1
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: A20644A7-20F4-11EB-B63E-D48564A46205


Device     Start        End    Sectors  Size Type
/dev/sdb1     40 5860528064 5860528025  2.7T Microsoft basic data




Disk /dev/sdc: 931.53 GiB, 1000204886016 bytes, 1953525168 sectors
Disk model: ST1000DM003-9YN1
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x0000433d


Device     Boot Start        End    Sectors   Size Id Type
/dev/sdc1          63 1953520064 1953520002 931.5G 83 Linux


Partition 1 does not start on physical sector boundary.












Disk /dev/sde: 931.53 GiB, 1000204886016 bytes, 1953525168 sectors
Disk model: ST1000DM003-1ER1
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 05F2103B-1FC9-11EB-B1B0-D48564A46205


Device     Start        End    Sectors   Size Type
/dev/sde1     40 1953520064 1953520025 931.5G Microsoft basic data




Disk /dev/mapper/ubuntu--vg-ubuntu--lv: 200 GiB, 214748364800 bytes, 419430400 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
mark123@4jetserver:~$



```

and this from lsblk

```
mark123@4jetserver:~$ lsblkNAME                      MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
loop0                       7:0    0    55M  1 loop /snap/core18/1880
loop1                       7:1    0  55.4M  1 loop /snap/core18/2128
loop2                       7:2    0  32.5M  1 loop /snap/snapd/13640
loop3                       7:3    0  71.3M  1 loop /snap/lxd/16099
loop4                       7:4    0  29.9M  1 loop /snap/snapd/8542
loop5                       7:5    0  67.3M  1 loop /snap/lxd/21545
loop6                       7:6    0  61.9M  1 loop /snap/core20/1169
sda                         8:0    0   3.7T  0 disk
&#9500;&#9472;sda1                      8:1    0     1M  0 part
&#9500;&#9472;sda2                      8:2    0     1G  0 part /boot
&#9492;&#9472;sda3                      8:3    0   3.7T  0 part
  &#9492;&#9472;ubuntu--vg-ubuntu--lv 253:0    0   200G  0 lvm  /
sdb                         8:16   0   2.7T  0 disk
&#9492;&#9472;sdb1                      8:17   0   2.7T  0 part /shares/d2p1
sdc                         8:32   0 931.5G  0 disk
&#9492;&#9472;sdc1                      8:33   0 931.5G  0 part /shares/d3p1
sdd                         8:48   0 931.5G  0 disk
&#9492;&#9472;sdd1                      8:49   0 931.5G  0 part /shares/d4p1
sde                         8:64   0 931.5G  0 disk
&#9492;&#9472;sde1                      8:65   0 931.5G  0 part /shares/d5p1
sr0                        11:0    1  1024M  0 rom



```

---

### Post by CharlesA on 2021-10-25
Good news. You are using LVM.

Run the following:

```
sudo pvdisplay
sudo vgdisplay
sudo lvdisplay

```

---

### Post by mw4jet on 2021-10-25
Thanks for any advice you can give, I just installed Nexcloud, got my security certificates working on NC and webmin, I put a lot of time into it and its working well now, except for this mistake.

pvdisplay
```
  --- Physical volume ---  PV Name               /dev/sda3
  VG Name               ubuntu-vg
  PV Size               <3.64 TiB / not usable 3.00 MiB
  Allocatable           yes
  PE Size               4.00 MiB
  Total PE              953604
  Free PE               902404
  Allocated PE          51200
  PV UUID               qzrfCJ-CFuT-pzFV-hurx-Wiic-v1ew-21L9Sz

```

vgdisplay
```
  --- Volume group ---  VG Name               ubuntu-vg
  System ID
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  4
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                1
  Open LV               1
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               <3.64 TiB
  PE Size               4.00 MiB
  Total PE              953604
  Alloc PE / Size       51200 / 200.00 GiB
  Free  PE / Size       902404 / 3.44 TiB
  VG UUID               EcBIt8-zy4c-lLoS-ZIEJ-zTCB-Qsey-BtLf1X

```

lvdisplay
```
  --- Logical volume ---  LV Path                /dev/ubuntu-vg/ubuntu-lv
  LV Name                ubuntu-lv
  VG Name                ubuntu-vg
  LV UUID                CBfUpa-TlPH-sYq0-wgdd-OBo6-SMRK-5PLICJ
  LV Write Access        read/write
  LV Creation host, time ubuntu-server, 2021-10-23 16:03:09 -0400
  LV Status              available
  # open                 1
  LV Size                200.00 GiB
  Current LE             51200
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           253:0

```

---

### Post by CharlesA on 2021-10-25
You should only need to extend the logical volume and then resize the file system.

Check this out:
[https://slice2.com/2020/12/05/howto-easily-resize-the-default-lvm-volume-on-ubuntu-18-04/](https://slice2.com/2020/12/05/howto-easily-resize-the-default-lvm-volume-on-ubuntu-18-04/)

---

### Post by mw4jet on 2021-10-25
Thank you, I will run through it tomorrow and let you know.

---

### Post by TheFu on 2021-10-26
Excellent choice in picking LVM. It provides options and flexibility, but it is also easy to make mistakes which can lead to a system that cannot be moved to new storage.  There are lots of LVM commands to make it tremendously flexible.  look at the command that start with pv* vg* and lv* on your system.  Their names are descriptive.  Learn the power of LVM.

While Charles is correct that you can do the lvextend, I'd strongly suggest that isn't a good idea.

LVM helps to keep the different parts of our systems separate. There are a number of reasons why you might want/need to do that.
For example, the OS will likely never need more than 35G total. But if you put a bunch of non-OS junk into the same LV, it will make upgrades and replacement installs riskier.

It is common for servers to have /var in a separate LV, since that is where logs and DB data ends up. Somethings things go sideways and the LV/partition with the logs will have 1G/min added.  It doesn't take too long for even a 4TB disk to be filled.  When the OS disk fills up, bad things happen - keeping logs on a different LV can prevent that. /var in a separate LV has been a best practice for decades, for good reason.
Then there is personal data.  That is usually put into /home - under each user's HOME.  It is be common to have /home in a separate LV for decades. With good reason.

Each LV can have different mount options. That means we can mount these other LVs in a way that is more secure by preventing dangerous ACLs, owners, and permissions.  It is common to block setuid programs from /home and /tmp.  Probably want to do that for /media/ as well.

There are lots and lots of discussions about LVM layouts in these forums.  I'd suggest reading a few of those.  The main thing to understand for the best use of LVM storage is to only extend/create the LVs you want for the next 3 months.  Extending an LV takes 5 seconds and zero downtime.  Reducing an LV almost always requires booting from alternate media and screwing around with vgchange -ay and other commands.  A VG that has all the storage allocated to LVs isn't very flexible.  The real power from using LVM is in the flexibility over time, but that can only happen if there is plenty of unused storage available for that flexibility.  For example, to perform safe backups of the data, you'll want to create a snapshot LV for each of the LVs, then have your backup tool backup that snapshot.  While that snapshot exists, those blocks are frozen and any changes have to go elsewhere.  IF the isn't any free space to hold the new data and the snapshot, then you can't use that method.

In 25 yrs as a Unix/Linux admin, I've never been able to guess how much storage will be needed on any system. With LVM, I don't have to be correct 3 yrs in advance. I only need to be correct for the next 3 months.  It is possible to have LVM automatically extend an LV 10G or 10% when it gets close to filling up.  This can be the best of the flexibility with little hassle factor for the admin.  But some LVs - like the one for /var shouldn't automatically extend - if they run out of storage, there's usually something wrong that needs to be researched and fixed.

Also, while **lvdisplay**, **vgdisplay** and **pvdisplay** show all the information, it is extremely seldom to need all that data.  There are summary commands with cleaner output - **lvs**, **vgs**, **pvs** ... try those out instead. I think you'll agree.

Lastly, loop devices in df and lsblk output are useless. They aren't real storage and just misdirect people from seeing what's important. Here's an alias for lsblk and df that don't show fake storage.
```
alias lsblkt='lsblk -e 7 -o name,size,type,fstype,mountpoint'
alias dft='df -hT -x squashfs -x tmpfs -x devtmpfs'

```
Hope this is helpful in some way. I've never seen any good reason to see loop devices unless I'm specifically troubleshooting the loop mount. Beside that, those just get in the way of the important data.  Delete it before posting here.

Of course, each LV needs a mount line in the /etc/fstab.  Those are pretty easy to setup, so don't be intimidated.

---

### Post by mw4jet on 2021-10-29
> **CharlesA said:**
> You should only need to extend the logical volume and then resize the file system.

Check this out:
[https://slice2.com/2020/12/05/howto-easily-resize-the-default-lvm-volume-on-ubuntu-18-04/](https://slice2.com/2020/12/05/howto-easily-resize-the-default-lvm-volume-on-ubuntu-18-04/)

I thank you for this link, the procedure was a success as far as I can tell. I had already bookmarked the link and performed the procedure before seeing that post from TheFu. If there are any issues I guess I will be re-installing, but again so far so good. My DNS and Nextcloud are working great.

Thanks again CharlesA

---

