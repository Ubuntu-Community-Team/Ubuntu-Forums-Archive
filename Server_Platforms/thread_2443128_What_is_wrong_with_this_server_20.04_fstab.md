---
title: "What is wrong with this server 20.04 fstab?"
date: 2020-05-11
forum: Server Platforms
---

### Post by trash1464 on 2020-05-11
I installed a fresh Ubuntu 20.04 server with a 120GB SSD for the OS and a 1TB standard HDD for data storage. The 1TB drive will not mount. Here is my fstab:

                         
 
 [SIZE=2]fstab:[/SIZE]
 [SIZE=2]/dev/disk/by-uuid/ac525950-9913-4dfb-80a9-c8733766d56b / ext4 defaults 0 0[/SIZE]
 [SIZE=2]/swap.img       none    swap    sw      0       0[/SIZE]
 [SIZE=2]/dev/disk/by-uuid/1969F149-6110-4854-900D-6B77FBF9A254 / ext4 defaults 0 0[/SIZE]
 [SIZE=2]/dev/disk/by-uuid/d26c67ba-ca26-4720-85bc-1f4465d23a1e / ext4 defaults 0 2[/SIZE]
  
The last line is for the 1TB drive, it does not mount on reboot nor on the command "mount -a"
Yes it is partitioned and formatted as ext4. One whole disk partition labeled ZMevents. Defined as /dev/sda/ and /dev/sda1/
What am I doing wrong?

---

### Post by volkswagner on 2020-05-11
You can't have two partitions mount to the same location.

The last two entries are trying to mount to the root filesystem (AKA /)

edit: Actually I see you have three mount points pointing to /

Can you print the output of:
```
sudo blkid
```

---

### Post by trash1464 on 2020-05-11
sudo blkid

```

/dev/sda1: LABEL="ZMevents" UUID="d26c67ba-ca26-4720-85bc-1f4465d23a1e" TYPE="ext4" PARTLABEL="ZMevents" PARTUUID="c599d0d4-b2dc-4bfb-aae2-7cebab5383d1"
/dev/sdb2: UUID="ac525950-9913-4dfb-80a9-c8733766d56b" TYPE="ext4" PARTUUID="f16f73ef-2027-4c16-b3d9-317cbd56403c"
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/sdb1: PARTUUID="b35d55b7-d859-461a-89f3-cc06aa1c9b0a"

```

I think I see what you mean with / after the UUID being the mount point? That is interesting because the only line  I added is the third one.

---

### Post by trash1464 on 2020-05-11
It might help if I posted the entire fstab:

```

cat /etc/fstab
 /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb2 during curtin installation
/dev/disk/by-uuid/ac525950-9913-4dfb-80a9-c8733766d56b / ext4 defaults 0 0
/swap.img    none    swap    sw    0    0
/dev/disk/by-uuid/1969F149-6110-4854-900D-6B77FBF9A254 / ext4 defaults 0 0
/dev/disk/by-uuid/d26c67ba-ca26-4720-85bc-1f4465d23a1e / ext4 defaults 0 2
/dev/disk/by-uuid/c599d0d4-b2dc-4bfb-aae2-7cebab5383d1 / ext4 defaults 0 2

```

---

### Post by TheFu on 2020-05-11
Telling 3 devices to mount onto the same place won't work.
Also, when using UUiDs, there's a shorter way:
```
UUID=ac525950-9913-4dfb-80a9-c8733766d56b    /     ext4      defaults 0 0
```

**You still can't have more than 1 mount on /**

---

### Post by LHammonds on 2020-05-12
Disclaimer: I am NOT an expert troubleshooter on fstab...just trying to throw some ideas out for you to chew on.

@TheFu, the "/dev/disk/by-id/...." is something that the "live"  installer does automatically.  The legacy installer does not do this so I  suppose it can be used as a fingerprint of sorts which can let you know  what installer was used.

@trash1464, when testing if a device can be mounted, just use "mount <device> <destination>" to see if it can be mounted.

If you have issues with something in fstab, doing "mount -a" will do nothing different because the -a says to mount all known partitions (which it goes by fstab).

If you mount it directly and it works, then that proves the issue is not with the device but just with fstab configuration.

In order to fix the fstab, we need to know is which device is the actual root you are mounting.  If fstab is read in order, then that means the actual root device is "ac525950-9913-4dfb-80a9-c8733766d56b" but that is a HUGE assumption.  If your system is running, use the "df" command to show what is mounted where.  Other useful command are "lsblk" and "sfdisk -l" which reveal the boot disk and partition types.

That means we need to figure out where to mount the remaining 3 devices.

I would create 3 folders to mount each device and inspect / verify the contents before modifying fstab.

```

sudo mkdir /mnt/1
sudo mkdir /mnt/2
sudo mkdir /mnt/3
mount /dev/disk/by-uuid/1969F149-6110-4854-900D-6B77FBF9A254 /mnt/1
mount /dev/disk/by-uuid/d26c67ba-ca26-4720-85bc-1f4465d23a1e /mnt/2
mount /dev/disk/by-uuid/c599d0d4-b2dc-4bfb-aae2-7cebab5383d1 /mnt/3
ls -la /mnt/1
ls -la /mnt/2
ls -la /mnt/3

```

If these are not part of the system (such as /opt, /home, /var and so on, then you just need to figure out where you want to mount them.  If the folders you made for the inspection works for you, then you'd modify the fstab to look like this:

```

/dev/disk/by-uuid/ac525950-9913-4dfb-80a9-c8733766d56b / ext4 defaults 0 0
/swap.img    none    swap    sw    0    0
/dev/disk/by-uuid/1969F149-6110-4854-900D-6B77FBF9A254 /mnt/1 ext4 defaults 0 0
/dev/disk/by-uuid/d26c67ba-ca26-4720-85bc-1f4465d23a1e /mnt/2 ext4 defaults 0 2
/dev/disk/by-uuid/c599d0d4-b2dc-4bfb-aae2-7cebab5383d1 /mnt/3 ext4 defaults 0 2

```

**EDIT: **Once you get things worked out as to what is what, I would recommend adding descriptive labels to everything in case you need to troubleshoot like this again in the future (or need to choose what to restore from backup)

Example:
```

sudo e2label /dev/disk/by-uuid/1969F149-6110-4854-900D-6B77FBF9A254 games
sudo e2label /dev/disk/by-uuid/d26c67ba-ca26-4720-85bc-1f4465d23a1e movies
sudo e2label /dev/disk/by-uuid/c599d0d4-b2dc-4bfb-aae2-7cebab5383d1 data

```

Here is an example of what someone will see when trying to restore a partition on one of my servers...which are all nicely labeled and makes the selection process EASY rather than just staring blankly at device names:

[color=lime]root@sysresccd[/color] [color=blue]/root[/color] % **fsarchiver probe simple**
```

[======DISK======] [=============NAME==============] [====SIZE====] [MAJ] [MIN]
[sda             ] [VBOX HARDDISK                  ] [    25.00 GB] [  8] [  0]
[sr0             ] [CD-ROM                         ] [   675.00 MB] [ 11] [  0]

[=====DEVICE=====] [==FILESYS==] [======LABEL======] [====SIZE====] [MAJ] [MIN]
[loop0           ] [squashfs   ] [<unknown>        ] [   620.12 MB] [  7] [  0]
[sda1            ] [ext4       ] [boot             ] [   953.00 MB] [  8] [  1]
[sda5            ] [LVM2_member] [<unknown>        ] [    24.87 GB] [  8] [  5]
[dm-0            ] [ext4       ] [root             ] [     6.00 GB] [254] [  0]
[dm-1            ] [ext4       ] [var              ] [     3.00 GB] [254] [  1]
[dm-2            ] [ext4       ] [tmp              ] [     1.00 GB] [254] [  2]
[dm-3            ] [ext4       ] [bak              ] [     4.00 GB] [254] [  3]
[dm-4            ] [ext4       ] [home             ] [     1.00 GB] [254] [  4]

```

---

### Post by trash1464 on 2020-05-12
What if those multiple / mount points are on individual partitions? Does not each partition have its own root?

---

### Post by volkswagner on 2020-05-12
You should do a little research on the Linux filesystem. Devices are mounted to a directory. "/" is the top level or root if the filesystem. You can't mount more than one device to ANY directory (or sub directory).

Basically whichever mount command runs last, will "remount" the mount point with device specified.

---

### Post by TheFu on 2020-05-13
> **trash1464 said:**
> What if those multiple / mount points are on individual partitions? Does not each partition have its own root?

I'm not certain how you mean that.

A running OS can only have 1 root mount point = /

Partitions need to be mounted to specific locations, with 1 mounted to /
another probably mounted to /boot/ 
another probably mounted to /boot/efi/
and another probably mounted to /home/.

On a running system, we can easily see that:
```
$ dft
Filesystem                            Type  Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--mate--vg-root     ext4   25G   20G  3.4G  86% /
/dev/sda2                             ext2  721M  216M  469M  32% /boot
/dev/sda1                             vfat  511M  3.7M  508M   1% /boot/efi
/dev/mapper/ubuntu--mate--vg-home--lv ext4   74G   20G   51G  29% /home
/dev/mapper/ubuntu--mate--vg-stuff    ext4   99G   44G   50G  47% /stuff
```

Everything in the 1st column is a device which can be considered a partition.  The /dev/mapper/.... stuff is because I use LVM2 to manage my storage. 

On the last column in the far right are the "mount points."  These are directories, usually empty, where the file systems get mounted.
Here's the fstab for that outcome:
```
UUID=E7E6-D023  /boot/efi       vfat    umask=0077      0 1
UUID=d62de6a2-5b69-4d3a-8a31-91040d274d9e /boot   ext2 defaults,noatime 0 2
/dev/mapper/ubuntu--mate--vg-root     /      ext4 noatime,errors=remount-ro 0 1
/dev/mapper/ubuntu--mate--vg-home--lv /home  ext4 errors=remount-ro,noatime 0 2
/dev/mapper/ubuntu--mate--vg-stuff /stuff   ext4 errors=remount-ro,noatime 0 2 
/dev/mapper/ubuntu--mate--vg-swap_1 none     swap sw              0       0
```

> You still can't have more than 1 mount on /
still true.

---

### Post by trash1464 on 2020-05-13
OK now I am understanding better and you, of course are correct. This old brain needs to switch from the MS world of disks to the Linux world of mount points. That being said, the question was pretty dumb. Your patient assistance is appreciated! To make a long story longer, what I wound up doing since this was a brand new install was to nuke it and start over from scratch. What now is a installer generated and functioning fstab follows:

```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb1 during curtin installation
/dev/disk/by-uuid/b8fdde54-e29e-44f2-b6a1-794678897136 / ext4 defaults 0 0
# /boot was on /dev/sdb2 during curtin installation
/dev/disk/by-uuid/697161e2-7948-4303-a85b-2a2a373e15fe /boot ext4 defaults 0 0
# /zmdata was on /dev/sda2 during curtin installation
/dev/disk/by-uuid/2b9dc7bd-bee9-4ee7-8b07-d662d47e9ef3 /zmdata ext4 defaults 0 0
/swap.img    none    swap    sw    0    0

```

What is interesting is Ubuntu's current default of using UUIDs which complicates manual mount operations if one should be needed. 
I have run Ubuntu desktop for some years. This is my first go around with server. 

Thanks to contributors of this forum for teaching this old dog some new tricks!

---

### Post by TheFu on 2020-05-13
We've all been there.  I substitute my reality all the time for the true reality. ;)

You don't need to use UUIDs if you don't want. Just don't use the direct /dev/sd.... device names, since those CAN and DO change.  If you look under /dev/disk/by*  there are multiple other options.  

```
by-id/       by-partuuid/ by-path/     by-uuid/
```

I remember by-label/ being available too.  My only 20.04 system is a VM, so it won't ever have direct access to disks. On 16.04 ...
```
by-id/  by-label/  by-partuuid/  by-path/  by-uuid/
```

I mount by label all the time, usually USB storage.  As shown above, I use LVM2, which provides a mapper into the specific LVs. The /dev/dm-xx devices are created during boot as LVM scans storage for LVM storage.  I'd never bothered to see of those /dev/dm-xx devices change order or not.  I use the /dev/{vg}/{lv} symbolic links which do not change.  Find those to be very handy and preferred.

In very large installations, they would probably use by-path/ so the storage device connected to the specific controller on the specific port can be specified at mount time.  With a consistent system, that makes dealing with disk arrays easier.  I have a few arrays at home, it is good to know which disk is where by-path/ so when one fails, it isn't hard to figure out which it is.  Of course, if you spend $5K on an array, it will have a green/red light showing which disk failed.  But if you spend $150 or less, there aren't often LEDs for each disk showing any more than attempted reads.

I've not seen the new /dev/disk/by-uuid/xxxxxx-xxxxx-xxxx-xxxxxxx method used inside a server before.

Anyways, if you got all the data from this thread that you need, please use the THREAD TOOLS at the top and mark it "SOLVED" to help the community out.

---

