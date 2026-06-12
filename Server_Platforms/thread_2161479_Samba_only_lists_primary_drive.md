---
title: "Samba only lists primary drive?"
date: 2013-07-10
forum: Server Platforms
---

### Post by adamtomaino on 2013-07-10
I setup a ubuntu server machine within my home to learn the basics of linux server management. I was able to successfully get samba running on my home network but only have access to the "primary" bootable hdd on my linux server box... I have 3 drives inside :( let me know if you see my problem..... I think my other drives are not mounting properly so here is my f disk and fstab:

sudo fdisk -l


Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d33d7


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   386529279   193263616   83  Linux
/dev/sda2       386531326   390721535     2095105    5  Extended
/dev/sda5       386531328   390721535     2095104   82  Linux swap / Solaris


Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005b699


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   972580863   486289408   83  Linux
/dev/sdb2       972582910   976771071     2094081    5  Extended
/dev/sdb5       972582912   976771071     2094080   82  Linux swap / Solaris


Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00090871


   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048      499711      248832   83  Linux
/dev/sdc2          501758   312580095   156039169    5  Extended
/dev/sdc5          501760   312580095   156039168   8e  Linux LVM


Disk /dev/mapper/tomaino--server--vg-root: 157.6 GB, 157634527232 bytes
255 heads, 63 sectors/track, 19164 cylinders, total 307879936 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/mapper/tomaino--server--vg-root doesn't contain a valid partition table


Disk /dev/mapper/tomaino--server--vg-swap_1: 2147 MB, 2147483648 bytes
255 heads, 63 sectors/track, 261 cylinders, total 4194304 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/mapper/tomaino--server--vg-swap_1 doesn't contain a valid partition table

*****Fstab:
adamtomaino@tomaino-server:~$ sudo  nano /etc/fstab
  GNU nano 2.2.6              File: /etc/fstab


# /etc/fstab: static file system information.
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/tomaino--server--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sdc1 during installation
UUID=a4d8a441-3131-4297-8d2b-5050fb9855c7 /boot           ext2    defaults        0       2
/dev/mapper/tomaino--server--vg-swap_1 none            swap    sw              0      2
# swap was on /dev/sdb5 during installation
UUID=63fe9b6d-792e-41c9-a560-0478f1c3ab09 none            swap    sw              0     2
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
# /etc/fstab: static file system information.



Thanks for any advice you can provide. This is a learning experience and I appreciate any advice or recommended reading/watching material  .-AT

---

### Post by SBJ95 on 2013-07-10
Hmm, it looks to me like you have them all set up to use LVM.  If you run 'df -h' (without the quotes), does the size for your root volume make sense?  Is it the size of all of your disks combined?  

Recommended reading material?  [Beginner's Guide to LVM]("http://www.howtoforge.com/linux_lvm").  LVM is kinda complicated to understand and make work!

---

### Post by volkswagner on 2013-07-11
In addition to the above command, please give the output of:

```
sudo mount
```

```
sudo blkid
```

```
vgdisplay
```

```
pvdisplay
```

When you installed/setup LVM, where did you expect/setup the additional drives to be mounted?

---

### Post by volkswagner on 2013-07-11
In addition to the above command, please give the output of:

```
sudo mount
```

```
sudo blkid
```

```
sudo vgdisplay
```

```
sudo pvdisplay
```

When you installed/setup LVM, where did you expect/setup the additional drives to be mounted?

---

### Post by adamtomaino on 2013-07-12
> **volkswagner said:**
> In addition to the above command, please give the output of:

```
sudo mount
```

```
sudo blkid
```

```
sudo vgdisplay
```

```
sudo pvdisplay
```

When you installed/setup LVM, where did you expect/setup the additional drives to be mounted?
 
df -h
Filesystem                            Size  Used Avail Use% Mounted on
/dev/mapper/tomaino--server--vg-root  145G   15G  123G  11% /
none                                  4.0K     0  4.0K   0% /sys/fs/cgroup
udev                                  992M   12K  992M   1% /dev
tmpfs                                 201M  440K  200M   1% /run
none                                  5.0M     0  5.0M   0% /run/lock
none                                 1002M     0 1002M   0% /run/shm
none                                  100M     0  100M   0% /run/user
/dev/sdc1                             228M   30M  187M  14% /boot
adamtomaino@tomaino-server:~$


-------------------
sudo mount

/dev/mapper/tomaino--server--vg-root on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
/dev/sdc1 on /boot type ext2 (rw)

---------------------------
 sudo blkid
/dev/sdb1: UUID="c2c78d07-24d2-4c7a-b338-2fd32155a87c" TYPE="ext4"
/dev/sdb5: UUID="63fe9b6d-792e-41c9-a560-0478f1c3ab09" TYPE="swap"
/dev/sdc1: UUID="a4d8a441-3131-4297-8d2b-5050fb9855c7" TYPE="ext2"
/dev/sdc5: UUID="UMUjlq-tTxV-9Xld-1kvh-uimw-NlXm-13XuHO" TYPE="LVM2_member"
/dev/mapper/tomaino--server--vg-root: UUID="f0a80bb7-694a-4c97-bae2-97ae608840a5" TYPE="ext4"
/dev/mapper/tomaino--server--vg-swap_1: UUID="d5f6da07-7692-49f3-8c7b-9000705fdae3" TYPE="swap"

----------------------------
sudo vgdisplay
  --- Volume group ---
  VG Name               tomaino-server-vg
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
  VG Size               148.81 GiB
  PE Size               4.00 MiB
  Total PE              38095
  Alloc PE / Size       38095 / 148.81 GiB
  Free  PE / Size       0 / 0
  VG UUID               ic12Cg-uXyG-0kst-Sq2J-K1bh-3U22-Y7ruiu
----------------
sudo pvdisplay
  --- Physical volume ---
  PV Name               /dev/sdc5
  VG Name               tomaino-server-vg
  PV Size               148.81 GiB / not usable 2.00 MiB
  Allocatable           yes (but full)
  PE Size               4.00 MiB
  Total PE              38095
  Free PE               0
  Allocated PE          38095
  PV UUID               UMUjlq-tTxV-9Xld-1kvh-uimw-NlXm-13XuHO


Thanks for the help-AT

---

### Post by adamtomaino on 2013-07-12
I have 3 hdd's but only primary appears... blkid lists all hdds present but nothing else ?/:(

---

### Post by volkswagner on 2013-07-13
> **adamtomaino said:**
> I have 3 hdd's but only primary appears... blkid lists all hdds present but nothing else ?/:(

Correct.

Now would be a good time to describe what your intentions are and/or how you thought things were setup during the install.
How would you like to use/mount the additional drives?

---

### Post by adamtomaino on 2013-07-13
> **volkswagner said:**
> Correct.

Now would be a good time to describe what your intentions are and/or how you thought things were setup during the install.
How would you like to use/mount the additional drives?

I would like to allocate all hdd space to my samba server for storage use. Ext4 is fine. I am not sure how to mount the drives and have smb recognize them.

---

### Post by volkswagner on 2013-07-13
Well, I was hoping for a more descriptive response.

Do you want to use LVM?
Do you want to use a single mount point or multiple mount points.

When you installed the OS, did you assign the disks to a mount point?

Where would you like to mount the additional drives?

Why do you have swap defined twice?

According to your /etc/fstab/ swap is actually on /dev/sdb5 and /dev/mapper/tomaino--server--vg-swap_1 aka "/dev/sdc5" which is part of LVM.
You created swap partitions on all of your disks, which is not typical.

What how-to were you following?

---

### Post by adamtomaino on 2013-07-13
> **volkswagner said:**
> Well, I was hoping for a more descriptive response.

Do you want to use LVM?
Do you want to use a single mount point or multiple mount points.

When you installed the OS, did you assign the disks to a mount point?

Where would you like to mount the additional drives?

Why do you have swap defined twice?

According to your /etc/fstab/ swap is actually on /dev/sdb5 and /dev/mapper/tomaino--server--vg-swap_1 aka "/dev/sdc5" which is part of LVM.
You created swap partitions on all of your disks, which is not typical.

What how-to were you following?

Sorry for the limited description. A more detailed description is beyond my current knowledge level. I do not have any need to setup LVM and would prefer a single mount point. I "think" i assigned a mount point during the ubuntu server install, but I had to reinstall  "few" times (probably where the double swap came from). I wasn't really following any "how to" i am sure you can tell... should to do a fresh reinstall with a real how to? I was hoping i could reformat a few drives and edit the fstab and everything would work, but maybe i am a wishful thinker "-AT

---

### Post by adamtomaino on 2013-07-13
> **adamtomaino said:**
> Sorry for the limited description. A more detailed description is beyond my current knowledge level. I do not have any need to setup LVM and would prefer a single mount point. I "think" i assigned a mount point during the ubuntu server install, but I had to reinstall  "few" times (probably where the double swap came from). I wasn't really following any "how to" i am sure you can tell... should to do a fresh reinstall with a real how to? I was hoping i could reformat a few drives and edit the fstab and everything would work, but maybe i am a wishful thinker "-AT

After trying fdisk partition editing, i've decided to[FONT=monospace][COLOR=#000000] "[/COLOR][/FONT][COLOR=#333333][FONT=verdana]sudo apt-get install ubuntu-desktop" and I am planning on utilizing "gparted" to get me where i need to go. I will keep you guys informed/[/FONT][/COLOR]

---

### Post by volkswagner on 2013-07-13
Well that's too bad.

To get a single mount point using multiple disks you will likely need LVM or RAID (JBOD) setup, or something like Greyhole (disk pooling).

You can easily create multiple mount points with your two large available partitions.

---

### Post by capscrew on 2013-07-14
> **adamtomaino said:**
> I have 3 hdd's but only primary appears... blkid lists all hdds present but nothing else ?/:(

A careful look at the disks shows that you have at least formatted the devices /dev/sda and /dev/sdb with both a ext4 partition and a swap partition.  

Here is sda```
Disk*[COLOR="#FF0000"] /dev/sda:[/COLOR]* 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d33d7


Device Boot Start End Blocks Id System
/dev/sda1 * 2048 386529279 193263616 83 Linux
/dev/sda2 386531326 390721535 2095105 5 Extended
/dev/sda5 386531328 390721535 2095104 82 Linux swap / Solaris
```... and here is sdb

```
Disk [COLOR="#FF0000"]*/dev/sdb*[/COLOR]: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005b699


Device Boot Start End Blocks Id System
/dev/sdb1 2048 972580863 486289408 83 Linux
/dev/sdb2 972582910 976771071 2094081 5 Extended
/dev/sdb5 972582912 976771071 2094080 82 Linux swap / Solaris
```

To my eyes this looks like you tried to install multiple times and chose a different device to install on each time.  You were successful the 3rd time and allowed the installer to use LVM to create a volume to then use as a partition.

As to your initial question.  You do not mount disks (the device) LVM volumes or partitions (Ext4).  You mount the file system created on the partition.  This means you can mount what ever file systems are on the existing partitions as long as you create a mount point in the already running file system which in your case is on the device /dev/sdc using LVM2 to use the space that is created when formating with an EXT4 file system.

The reason you can see the partitions on sda and sdb is that the partitions with file systems are not mounted for the running OS to see them.  In addition, when these devices (sda and sdb) were formatted they were setup to be the booted file system so they have an OS and complete Linux file system tree already.  These should be re-formatted as a single partition (no swap) and formatted as EXT but without an OS installed.  

This will give you the ability to mount them into the running OS file system at a mount point of your choice.  For instance I have a 1TB drive that is mounted to the small 100 GB EXT4 partition at /backup.  I made the mount point (sudo mkdir /backup) and then added the appropriate line to the fstab file.  You can certainly add 2 of these device/partition/file_systems to your existing running OS file system.

Why the LVM you might ask.  The installer defaults to that in later Ubuntu releases and it is not obvious when it does it.  I have seen the spot where you can make a choice, but you also have to select manual configuration to get the choice to NOT use LVM.

Lots to think about here and I know you are new to this.  Now is the time to ask more questions until you understand.

---

### Post by adamtomaino on 2013-07-14
> **capscrew said:**
> A careful look at the disks shows that you have at least formatted the devices /dev/sda and /dev/sdb with both a ext4 partition and a swap partition.  

Here is sda```
Disk*[COLOR=#FF0000] /dev/sda:[/COLOR]* 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d33d7


Device Boot Start End Blocks Id System
/dev/sda1 * 2048 386529279 193263616 83 Linux
/dev/sda2 386531326 390721535 2095105 5 Extended
/dev/sda5 386531328 390721535 2095104 82 Linux swap / Solaris
```... and here is sdb

```
Disk [COLOR=#FF0000]*/dev/sdb*[/COLOR]: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005b699


Device Boot Start End Blocks Id System
/dev/sdb1 2048 972580863 486289408 83 Linux
/dev/sdb2 972582910 976771071 2094081 5 Extended
/dev/sdb5 972582912 976771071 2094080 82 Linux swap / Solaris
```

To my eyes this looks like you tried to install multiple times and chose a different device to install on each time.  You were successful the 3rd time and allowed the installer to use LVM to create a volume to then use as a partition.

As to your initial question.  You do not mount disks (the device) LVM volumes or partitions (Ext4).  You mount the file system created on the partition.  This means you can mount what ever file systems are on the existing partitions as long as you create a mount point in the already running file system which in your case is on the device /dev/sdc using LVM2 to use the space that is created when formating with an EXT4 file system.

The reason you can see the partitions on sda and sdb is that the partitions with file systems are not mounted for the running OS to see them.  In addition, when these devices (sda and sdb) were formatted they were setup to be the booted file system so they have an OS and complete Linux file system tree already.  These should be re-formatted as a single partition (no swap) and formatted as EXT but without an OS installed.  

This will give you the ability to mount them into the running OS file system at a mount point of your choice.  For instance I have a 1TB drive that is mounted to the small 100 GB EXT4 partition at /backup.  I made the mount point (sudo mkdir /backup) and then added the appropriate line to the fstab file.  You can certainly add 2 of these device/partition/file_systems to your existing running OS file system.

Why the LVM you might ask.  The installer defaults to that in later Ubuntu releases and it is not obvious when it does it.  I have seen the spot where you can make a choice, but you also have to select manual configuration to get the choice to NOT use LVM.

Lots to think about here and I know you are new to this.  Now is the time to ask more questions until you understand.

Thanks for the input. You are correct in all of your multiple install assumptions. I decided to try all over again with complete formatting of all drives and setup a 3 hdd logical LVM + 1 primary ext 4 (bootable) + 1 swap partition. Install seemed to go ok, and the LVG looks like it is setup correctly. I used the manual install feature in ubuntu server install to format all drives and create lvm group

sudo blkid
/dev/sda1: UUID="g0tvtP-nhYP-f96p-2j41-NtlJ-XTem-mXTHUb" TYPE="LVM2_member"
/dev/sdb1: UUID="ef448a1a-9d16-4113-ae06-1242bd751ced" TYPE="ext4"
/dev/sdb5: UUID="8mVi2M-S2hO-8eIF-farM-1YJi-2miS-dRLNQY" TYPE="LVM2_member"
/dev/sdb6: UUID="f958e6d7-9ee2-48d5-aaf1-805ef4597933" TYPE="swap"
/dev/sdc1: UUID="G3RiJq-5qrY-9NK7-vcdc-ZsVx-JPzE-M6BlNP" TYPE="LVM2_member"
---------------

here is a my current fdisk -l
adamtomaino@Tomaino-Server:~$ sudo fdisk -l


Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a04fc


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   390721535   195359744   8e  Linux LVM


Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000555cd


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    35352575    17675264   83  Linux
/dev/sdb2        35354622   976771071   470708225    5  Extended
/dev/sdb5        39260160   976771071   468755456   8e  Linux LVM
/dev/sdb6        35354624    39260159     1952768   82  Linux swap / Solaris


Partition table entries are not in disk order


Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00090871


   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048   312580095   156289024   8e  Linux LVM
----------------

Also here is my VGdisplay
sudo vgdisplay
  --- Volume group ---
  VG Name               lvg
  System ID
  Format                lvm2
  Metadata Areas        3
  Metadata Sequence No  3
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                0
  Open LV               0
  Max PV                0
  Cur PV                3
  Act PV                3
  VG Size               782.39 GiB
  PE Size               4.00 MiB
  Total PE              200293
  Alloc PE / Size       0 / 0
  Free  PE / Size       200293 / 782.39 GiB
  VG UUID               9NdRbp-x4dA-ASLK-TKcf-qa2J-3Vse-jomzuh



my issue now seems to be that on bootup my total memory appears to only be what is on the primary drive and not the LVM. I don't want to move forward with setting up samba again until i get this issue resolved. So is my next step editing the fstab to mount the lvm group? I am not sure how this should look. Thank you both so much for your assistance thus far and your detailed and informative responses.-Adam

---

### Post by adamtomaino on 2013-07-14
> **adamtomaino said:**
> Thanks for the input. You are correct in all of your multiple install assumptions. I decided to try all over again with complete formatting of all drives and setup a 3 hdd logical LVM + 1 primary ext 4 (bootable) + 1 swap partition. Install seemed to go ok, and the LVG looks like it is setup correctly. I used the manual install feature in ubuntu server install to format all drives and create lvm group

sudo blkid
/dev/sda1: UUID="g0tvtP-nhYP-f96p-2j41-NtlJ-XTem-mXTHUb" TYPE="LVM2_member"
/dev/sdb1: UUID="ef448a1a-9d16-4113-ae06-1242bd751ced" TYPE="ext4"
/dev/sdb5: UUID="8mVi2M-S2hO-8eIF-farM-1YJi-2miS-dRLNQY" TYPE="LVM2_member"
/dev/sdb6: UUID="f958e6d7-9ee2-48d5-aaf1-805ef4597933" TYPE="swap"
/dev/sdc1: UUID="G3RiJq-5qrY-9NK7-vcdc-ZsVx-JPzE-M6BlNP" TYPE="LVM2_member"
---------------

here is a my current fdisk -l
adamtomaino@Tomaino-Server:~$ sudo fdisk -l


Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a04fc


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   390721535   195359744   8e  Linux LVM


Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000555cd


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    35352575    17675264   83  Linux
/dev/sdb2        35354622   976771071   470708225    5  Extended
/dev/sdb5        39260160   976771071   468755456   8e  Linux LVM
/dev/sdb6        35354624    39260159     1952768   82  Linux swap / Solaris


Partition table entries are not in disk order


Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00090871


   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048   312580095   156289024   8e  Linux LVM
----------------

Also here is my VGdisplay
sudo vgdisplay
  --- Volume group ---
  VG Name               lvg
  System ID
  Format                lvm2
  Metadata Areas        3
  Metadata Sequence No  3
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                0
  Open LV               0
  Max PV                0
  Cur PV                3
  Act PV                3
  VG Size               782.39 GiB
  PE Size               4.00 MiB
  Total PE              200293
  Alloc PE / Size       0 / 0
  Free  PE / Size       200293 / 782.39 GiB
  VG UUID               9NdRbp-x4dA-ASLK-TKcf-qa2J-3Vse-jomzuh



my issue now seems to be that on bootup my total memory appears to only be what is on the primary drive and not the LVM. I don't want to move forward with setting up samba again until i get this issue resolved. So is my next step editing the fstab to mount the lvm group? I am not sure how this should look. Thank you both so much for your assistance thus far and your detailed and informative responses.-Adam

Also my current fstab:
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb1 during installation
UUID=ef448a1a-9d16-4113-ae06-1242bd751ced /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=f958e6d7-9ee2-48d5-aaf1-805ef4597933 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by capscrew on 2013-07-15
> **adamtomaino said:**
> Also my current fstab:
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb1 during installation
UUID=ef448a1a-9d16-4113-ae06-1242bd751ced /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=f958e6d7-9ee2-48d5-aaf1-805ef4597933 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

By memory I assume you mean storage size, since both memory (RAM) and storage size is stated in the same terms (MB, GB and TB).

It seems the LVM voume is not mounted so you can't see it yet.  

What do you get wiith ```
df -h
```

You can see the LVM volume with this command```
sudo lvs
```

You can see the mountable volume with this```
ls -l /dev/mapper/
```

Post these 3 items here for me to see.  Then we can set it up for you.

---

### Post by adamtomaino on 2013-07-15
> **capscrew said:**
> By memory I assume you mean storage size, since both memory (RAM) and storage size is stated in the same terms (MB, GB and TB).

It seems the LVM voume is not mounted so you can't see it yet.  

What do you get wiith ```
df -h
```

You can see the LVM volume with this command```
sudo lvs
```

You can see the mountable volume with this```
ls -l /dev/mapper/
```

Post these 3 items here for me to see.  Then we can set it up for you.

df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdb1        17G  1.2G   15G   8% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            992M  8.0K  992M   1% /dev
tmpfs           201M  432K  200M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none           1002M     0 1002M   0% /run/shm
none            100M     0  100M   0% /run/user
--------------------------------------

adamtomaino@Tomaino-Server:~$ sudo lvs
[sudo] password for adamtomaino:
adamtomaino@Tomaino-Server:~$
-------------------------------------------

ls -l /dev/mapper/
total 0
crw------- 1 root root 10, 236 Jul 14 22:59 control
adamtomaino@Tomaino-Server:~$

---

### Post by capscrew on 2013-07-15
> **adamtomaino said:**
> ```
df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdb1        17G  1.2G   15G   8% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            992M  8.0K  992M   1% /dev
tmpfs           201M  432K  200M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none           1002M     0 1002M   0% /run/shm
none            100M     0  100M   0% /run/user
```

```
adamtomaino@Tomaino-Server:~$ sudo lvs
[sudo] password for adamtomaino:
adamtomaino@Tomaino-Server:~$
```

```
ls -l /dev/mapper/
total 0
crw------- 1 root root 10, 236 Jul 14 22:59 control
adamtomaino@Tomaino-Server:~$
```

This is not good.  No LVM volumes showing.

The command: sudo lvs should return something like this```

sudo lvs
[sudo] password for bruce: 
  LV     VG     Attr   LSize   Origin Snap%  Move Log Copy%  Convert
  backup atlas -wi-a- 511.00g                                      
  music  atlas -wi-a- 200.70g        

```

The command: ls -l /dev/mapper should have returned something like this```

ls -l /dev/mapper
total 0
crw------- 1 root root 10, 236 Jul 15 07:52 control
lrwxrwxrwx 1 root root       7 Jul 15 07:52 atlas-backup -> ../dm-0
lrwxrwxrwx 1 root root       7 Jul 15 07:52 atlas-music -> ../dm-1

```

What do you get from this ```

sudo blkid -c /dev/null -o list

```

---

### Post by adamtomaino on 2013-07-15
> **capscrew said:**
> This is not good.  No LVM volumes showing.

The command: sudo lvs should return something like this```

sudo lvs
[sudo] password for bruce: 
  LV     VG     Attr   LSize   Origin Snap%  Move Log Copy%  Convert
  backup atlas -wi-a- 511.00g                                      
  music  atlas -wi-a- 200.70g        

```

The command: ls -l /dev/mapper should have returned something like this```

ls -l /dev/mapper
total 0
crw------- 1 root root 10, 236 Jul 15 07:52 control
lrwxrwxrwx 1 root root       7 Jul 15 07:52 atlas-backup -> ../dm-0
lrwxrwxrwx 1 root root       7 Jul 15 07:52 atlas-music -> ../dm-1

```

What do you get from this ```

sudo blkid -c /dev/null -o list

```
sudo blkid -c /dev/null -o list
[sudo] password for adamtomaino:
device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  LVM2_member      (not mounted)  g0tvtP-nhYP-f96p-2j41-NtlJ-XTem-mXTHUb
/dev/sdb1  ext4             /              ef448a1a-9d16-4113-ae06-1242bd751ced
/dev/sdb5  LVM2_member      (not mounted)  8mVi2M-S2hO-8eIF-farM-1YJi-2miS-dRLNQY
/dev/sdb6  swap             <swap>         f958e6d7-9ee2-48d5-aaf1-805ef4597933
/dev/sdc1  LVM2_member      (not mounted)  G3RiJq-5qrY-9NK7-vcdc-ZsVx-JPzE-M6BlNP
adamtomaino@Tomaino-Server:~$

---

### Post by adamtomaino on 2013-07-15
> **adamtomaino said:**
> sudo blkid -c /dev/null -o list
[sudo] password for adamtomaino:
device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  LVM2_member      (not mounted)  g0tvtP-nhYP-f96p-2j41-NtlJ-XTem-mXTHUb
/dev/sdb1  ext4             /              ef448a1a-9d16-4113-ae06-1242bd751ced
/dev/sdb5  LVM2_member      (not mounted)  8mVi2M-S2hO-8eIF-farM-1YJi-2miS-dRLNQY
/dev/sdb6  swap             <swap>         f958e6d7-9ee2-48d5-aaf1-805ef4597933
/dev/sdc1  LVM2_member      (not mounted)  G3RiJq-5qrY-9NK7-vcdc-ZsVx-JPzE-M6BlNP
adamtomaino@Tomaino-Server:~$
I think i might have foung the problem, non of my drives seem to actually be in the VG:

~# pvscan
  PV /dev/sda1   VG lvg   lvm2 [186.31 GiB / 186.31 GiB free]
  PV /dev/sdb5   VG lvg   lvm2 [447.04 GiB / 447.04 GiB free]
  PV /dev/sdc1   VG lvg   lvm2 [149.05 GiB / 149.05 GiB free]
  Total: 3 [782.39 GiB] / in use: 3 [782.39 GiB] / in no VG: 0 [0   ]

---

### Post by capscrew on 2013-07-16
> **adamtomaino said:**
> I think i might have foung the problem, non of my drives seem to actually be in the VG:

~# pvscan
  PV /dev/sda1   VG lvg   lvm2 [186.31 GiB / 186.31 GiB free]
  PV /dev/sdb5   VG lvg   lvm2 [447.04 GiB / 447.04 GiB free]
  PV /dev/sdc1   VG lvg   lvm2 [149.05 GiB / 149.05 GiB free]
  Total: 3 [782.39 GiB] / in use: 3 [782.39 GiB] / in no VG: 0 [0   ]

It sure looks that way.  Did you create these manually?  What do you want to do with these PV's?  Create 1 large LV;  or a couple of them to mount at separate mount points?

Have you made a VG for them?  What do you get from this:```
sudo vgdisplay
```...if not you need to make a VG and then you can create the LV's

A good howto to follow can be found here: [**[COLOR="#0000FF"]http://www.davelachapelle.ca/guides/ubuntu-lvm-guide/[/COLOR]**]("http://www.davelachapelle.ca/guides/ubuntu-lvm-guide/").

---

### Post by adamtomaino on 2013-07-16
> **capscrew said:**
> It sure looks that way.  Did you create these manually?  What do you want to do with these PV's?  Create 1 large LV;  or a couple of them to mount at separate mount points?

Have you made a VG for them?  What do you get from this:```
sudo vgdisplay
```...if not you need to make a VG and then you can create the LV's

A good howto to follow can be found here: [**[COLOR=#0000FF]http://www.davelachapelle.ca/guides/ubuntu-lvm-guide/[/COLOR]**]("http://www.davelachapelle.ca/guides/ubuntu-lvm-guide/").



root@Tomaino-Server:~# sudo vgdisplay
  --- Volume group ---
  VG Name               lvg
  System ID
  Format                lvm2
  Metadata Areas        3
  Metadata Sequence No  5
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                0
  Open LV               0
  Max PV                0
  Cur PV                3
  Act PV                3
  VG Size               782.39 GiB
  PE Size               4.00 MiB
  Total PE              200293
  Alloc PE / Size       0 / 0
  Free  PE / Size       200293 / 782.39 GiB
  VG UUID               9NdRbp-x4dA-ASLK-TKcf-qa2J-3Vse-jomzuh

----------------

I formatted the hdds to "free space" and created lv using Ubuntu Server's "manual partition tools" included during installation. My goal is to create 1 large LV. I would like to use this server primarily as a samba file server for my home network. 

Can I add my VG UUID (above) to fstab? or is there still a problem.

---

### Post by capscrew on 2013-07-16
> **adamtomaino said:**
> I formatted the hdds to "free space" and created lv using Ubuntu Server's "manual partition tools" included during installation. My goal is to create 1 large LV. I would like to use this server primarily as a samba file server for my home network. 

Can I add my VG UUID (above) to fstab? or is there still a problem.
Two out of the three tests for validity say that the VG does NOT exist.  I can't say it wont work, but then again I can't say that it will.  Try it and see what happens.  My guess is you will have to redo the LVM setup.  But that does not mean you have to reinstall.  It's pretty simple to recreate a LV from the command line.  Let us know what happens.

---

### Post by adamtomaino on 2013-07-16
> **capscrew said:**
>  It's pretty simple to recreate a LV from the command line. Let us know what happens.

Do you have a recommended tutorial? -AT

---

### Post by capscrew on 2013-07-16
Sure do.  Try this: [_[COLOR="#0000FF"]http://www.davelachapelle.ca/guides/ubuntu-lvm-guide/[/COLOR]_]("http://www.davelachapelle.ca/guides/ubuntu-lvm-guide/")

---

