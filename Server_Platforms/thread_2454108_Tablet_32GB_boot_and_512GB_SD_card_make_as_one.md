---
title: "Tablet 32GB boot and 512GB SD card make as one?"
date: 2020-11-23
forum: Server Platforms
---

### Post by Raymond Day on 2020-11-23
Got Ubuntu server on a tablet that has 32GB built in and I have a 512GB SD card plug in it. I wanted to use LVM to make the boot or partition 3 the full size of the 512GB SD card.

Not sure how to do it. Here is some commands I did.

```
root@rayday-tablet:~# fdisk -l
Disk /dev/loop0: 55.33 MiB, 58007552 bytes, 113296 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 55.37 MiB, 58052608 bytes, 113384 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 70.58 MiB, 73990144 bytes, 144512 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 67.77 MiB, 71041024 bytes, 138752 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 30.95 MiB, 32432128 bytes, 63344 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 30.96 MiB, 32440320 bytes, 63360 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mmcblk0: 28.93 GiB, 31037849600 bytes, 60620800 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: FE8F2415-AE2E-4C88-8357-18CD1E0539A3

Device           Start      End  Sectors  Size Type
/dev/mmcblk0p1    2048  1050623  1048576  512M EFI System
/dev/mmcblk0p2 1050624  3147775  2097152    1G Linux filesystem
/dev/mmcblk0p3 3147776 60618751 57470976 27.4G Linux filesystem


Disk /dev/mapper/ubuntu--vg-ubuntu--lv: 20 GiB, 21474836480 bytes, 41943040 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 931.53 GiB, 1000204886016 bytes, 1953525168 sectors
Disk model: 2115
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 33553920 bytes
Disklabel type: dos
Disk identifier: 0xa8ad6ad4

Device     Boot Start        End    Sectors   Size Id Type
/dev/sda1           1 1953524910 1953524910 931.5G 83 Linux


Disk /dev/mmcblk2: 476.73 GiB, 511868665856 bytes, 999743488 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: ADECBC6D-31EB-4586-ACBB-4C2C9AFD4012

Device         Start       End   Sectors   Size Type
/dev/mmcblk2p1    34 999743454 999743421 476.7G Linux filesystem
root@rayday-tablet:~# lvscan
^C  Interrupted...
  Giving up waiting for lock.
root@rayday-tablet:~# df -h
Filesystem                         Size  Used Avail Use% Mounted on
udev                               1.8G     0  1.8G   0% /dev
tmpfs                              376M  3.2M  373M   1% /run
/dev/mapper/ubuntu--vg-ubuntu--lv   20G   15G  3.7G  81% /
tmpfs                              1.9G     0  1.9G   0% /dev/shm
tmpfs                              5.0M     0  5.0M   0% /run/lock
tmpfs                              1.9G     0  1.9G   0% /sys/fs/cgroup
/dev/mmcblk0p2                     976M  199M  711M  22% /boot
/dev/sda1                          916G  468G  402G  54% /mnt/1TB_SSD
/dev/loop0                          56M   56M     0 100% /snap/core18/1885
/dev/loop1                          56M   56M     0 100% /snap/core18/1932
/dev/loop2                          71M   71M     0 100% /snap/lxd/16922
/dev/loop3                          68M   68M     0 100% /snap/lxd/18150
/dev/loop4                          31M   31M     0 100% /snap/snapd/9607
/dev/loop5                          31M   31M     0 100% /snap/snapd/9721
/dev/mmcblk0p1                     511M  7.8M  504M   2% /boot/efi
tmpfs                              376M     0  376M   0% /run/user/0
root@rayday-tablet:~# fdisk -l
Disk /dev/loop0: 55.33 MiB, 58007552 bytes, 113296 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 55.37 MiB, 58052608 bytes, 113384 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 70.58 MiB, 73990144 bytes, 144512 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 67.77 MiB, 71041024 bytes, 138752 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 30.95 MiB, 32432128 bytes, 63344 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 30.96 MiB, 32440320 bytes, 63360 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mmcblk0: 28.93 GiB, 31037849600 bytes, 60620800 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: FE8F2415-AE2E-4C88-8357-18CD1E0539A3

Device           Start      End  Sectors  Size Type
/dev/mmcblk0p1    2048  1050623  1048576  512M EFI System
/dev/mmcblk0p2 1050624  3147775  2097152    1G Linux filesystem
/dev/mmcblk0p3 3147776 60618751 57470976 27.4G Linux filesystem


Disk /dev/mapper/ubuntu--vg-ubuntu--lv: 20 GiB, 21474836480 bytes, 41943040 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 931.53 GiB, 1000204886016 bytes, 1953525168 sectors
Disk model: 2115
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 33553920 bytes
Disklabel type: dos
Disk identifier: 0xa8ad6ad4

Device     Boot Start        End    Sectors   Size Id Type
/dev/sda1           1 1953524910 1953524910 931.5G 83 Linux


Disk /dev/mmcblk2: 476.73 GiB, 511868665856 bytes, 999743488 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: ADECBC6D-31EB-4586-ACBB-4C2C9AFD4012

Device         Start       End   Sectors   Size Type
/dev/mmcblk2p1    34 999743454 999743421 476.7G Linux filesystem
root@rayday-tablet:~# parted /dev/mmcblk2
GNU Parted 3.3
Using /dev/mmcblk2
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print
Model: SD SC512 (sd/mmc)
Disk /dev/mmcblk2: 512GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags:

Number  Start   End    Size   File system  Name      Flags
 1      17.4kB  512GB  512GB  ext4         512GB-SD

(parted) quit
root@rayday-tablet:~# parted /dev/mmcblk0
GNU Parted 3.3
Using /dev/mmcblk0
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) resizepart
Partition number? 3
End?  [31.0GB]?
free(): invalid pointer
Aborted (core dumped)
root@rayday-tablet:~# lvextend
  No command with matching syntax recognised.  Run 'lvextend --help' for more information.
root@rayday-tablet:~# lvextend --size 512G /dev/mapper/ubuntu--vg-ubuntu--lv
  Insufficient free space: 125952 extents needed, but only 1895 available
root@rayday-tablet:~#
```

So what would be the right way to do this if can?

-Raymond Day

---

### Post by LHammonds on 2020-11-23
You could set it up so that the boot and root are on the 32GB and all others are on the 512GB such as /var, /usr, /home, /opt and /tmp

I have [documented how to slice up partitions](https://hammondslegacy.com/forum/viewtopic.php?f=40&t=273) using the "legacy" installer but have not yet integrated the [new method](https://ubuntuforums.org/showthread.php?t=2441984&page=2&p=13955557#post13955557) to do it with the new "live" installer which is a bit tricky but it is possible to get the exact same result during initial setup.

LHammonds

---

### Post by Raymond Day on 2020-11-26
Booted a live USB on it. Wanted to see if can just install fresh using the 512GB SD card inside it. Sees it as /dev/mmcblk2 and the built in 32GB flash as /dev/mmcblk1

Not sure how I did it but got it so it did not error saying could not format the 512GB SD card. I had to click on some how were the box was checked on it. But I could not click on the box to set it like that.

Any way it's been at the like thinking cereal icon going around for all most a hour now. So I don't think it's going to install.

Is there away to set it for LVM to use both the 32GB and 512GB as one drive?

Not sure how to set this up to install it. I am using the desktop Ubuntu 20.04 on a USB key.

It be neat to use it like that. Had it running on the 32GB and it fills it up.

-Raymond Day

---

### Post by CelticWarrior on 2020-11-26
> **Raymond Day said:**
> 
Is there away to set it for LVM to use both the 32GB and 512GB as one drive?

Not sure how to set this up to install it. I am using the desktop Ubuntu 20.04 on a USB key.


Yes, there's a way but you don't want to do that.
With or without LVM what makes sense here is having the root in the 32GB drive and a separated /home is the bigger one.

---

### Post by TheFu on 2020-11-26
> **CelticWarrior said:**
> Yes, there's a way but you don't want to do that.
With or without LVM what makes sense here is having the root in the 32GB drive and a separated /home is the bigger one.

^^^^^
exactly this.
Just because something is possible, that doesn't make it a good idea.

But if you insist and accept this very,very, risky setup, just do a normal install w/ LVM on 1 of the drives, then add the other drive into the same VG as the first AFTER the INSTALL is complete.  Then you can create and expand LVs as you like. Any of the LVM tutorials should provide sufficient guidance for this.

Did I mention how bad an idea this was?  I lost 80% of my data doing exactly this about 20 years ago. Are you prepared to lose all your data?  That's what will happen if either drive fails. Of course, if you have great backups, go for it.

---

### Post by Raymond Day on 2020-11-26
Booted a live Ubuntu and did commands like this:

root@ubuntu:/media# vgextend vgubuntu /dev/mmcblk2p1
root@ubuntu:/media# lvextend -l +29818 /dev/vgubuntu/root

It seemed like it made the LVM 32GB and 128GB SD card in side it.

Then went to install Ubuntu 20.04 server and it auto sees the LVM and looks like it's the big size. I say to install on it.

Reboot and it just goes to the GRUB menu now. I installed the server again but same just boots to GRUB.

How can I fix this. Did I make the LVM wrong? Can I install it as LVM and then add the 128GB later to it?

-Raymond Day

---

### Post by TheFu on 2020-11-26
Please re-read post #5 above.

---

### Post by LHammonds on 2020-11-27
Like TheFu and others said, we do not recommend the combination like this...but...to do it, follow what TheFu said.  To make this easier to understand....TAKE OUT THE 512GB card.

Install onto the 32 GB using LVM.  You can use the atomic method of letting it do everything for you or you can slice-n-dice the partitions how you want manually...just make sure /boot is outside LVM.

Once you have the OS working, then install the 512 GB card and boot it up.

You can then use fdisk to format the card for Linux LVM, then add it to the LVG and use lvextend and resize2fs as noted in the "Add More Drives" section of [my tutorial]("https://hammondslegacy.com/forum/viewtopic.php?p=814#p814").

Taking out the 512GB card is not required but should give you clarity on what you should be doing since it seems you missed the point.

When I install my servers, I always start off on a 25 GB disk and for the most-part, that is sufficient unless it will be a repository of some kind.

LHammonds

---

### Post by Raymond Day on 2020-11-30
Looks like that 512GB SD card is bad now. I put a new 128GB SD card in it and works good.

Took the SD card out and installed Ubuntu server 20.04.1 as LVM. If I left it it in seen the 32GB and 128GB as one drive but would just boot to grub menu then.

Put the SD card in and just don't know how to add it.

I guess do some "lvm lvextend" command.

A command that my help.

```
root@rayday-tablet:~# lvmdiskscan -l
  WARNING: only considering LVM devices
  /dev/mmcblk0p3    [      27.40 GiB] LVM physical volume
  /dev/mmcblk2      [     116.48 GiB] LVM physical volume
  0 LVM physical volume whole disks
  2 LVM physical volumes
root@rayday-tablet:~#
```

This is what it looks like but they are not linked as one drive.

```
root@rayday-tablet:~# df -h
Filesystem                         Size  Used Avail Use% Mounted on
udev                               1.8G     0  1.8G   0% /dev
tmpfs                              376M  1.8M  374M   1% /run
/dev/mapper/ubuntu--vg-ubuntu--lv   27G  6.2G   20G  25% /
tmpfs                              1.9G     0  1.9G   0% /dev/shm
tmpfs                              5.0M     0  5.0M   0% /run/lock
tmpfs                              1.9G     0  1.9G   0% /sys/fs/cgroup
/dev/mmcblk0p2                     976M  105M  805M  12% /boot
/dev/loop1                          72M   72M     0 100% /snap/lxd/16099
/dev/loop0                          55M   55M     0 100% /snap/core18/1880
/dev/mmcblk0p1                     511M  7.8M  504M   2% /boot/efi
/dev/loop2                          30M   30M     0 100% /snap/snapd/8542
tmpfs                              376M     0  376M   0% /run/user/0
/dev/loop3                          56M   56M     0 100% /snap/core18/1932
/dev/loop4                          31M   31M     0 100% /snap/snapd/9721
/dev/loop5                          68M   68M     0 100% /snap/lxd/18150
root@rayday-tablet:~#
```

```
root@rayday-tablet:~# parted -l
Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-ubuntu--lv: 29.4GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags:

Number  Start  End     Size    File system  Flags
 1      0.00B  29.4GB  29.4GB  ext4


Error: /dev/mmcblk2: unrecognised disk label
Model: SD SD128 (sd/mmc)
Disk /dev/mmcblk2: 125GB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags:

Model: MMC SLD32G (sd/mmc)
Disk /dev/mmcblk0: 31.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags:

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  538MB   537MB   fat32              boot, esp
 2      538MB   1612MB  1074MB  ext4
 3      1612MB  31.0GB  29.4GB


Error: /dev/mmcblk0boot0: unrecognised disk label
Model: Generic SD/MMC Storage Card (sd/mmc)
Disk /dev/mmcblk0boot0: 4194kB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags:

Error: /dev/mmcblk0boot1: unrecognised disk label
Model: Generic SD/MMC Storage Card (sd/mmc)
Disk /dev/mmcblk0boot1: 4194kB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags:

root@rayday-tablet:~#
```

So how do I get it to to see the 32GB and 128GB as one drive?

Thank you.

-Raymond Day

---

### Post by LHammonds on 2020-11-30
I already gave you a link that shows every command you need.

You just need to substitute the device/drive paths in the tutorial for your devices....e.g. /dev/sd* ---> /dev/mmc*

---

### Post by TheFu on 2020-11-30
> **TheFu said:**
> ... then add the other drive into the same VG as the first AFTER the INSTALL is complete.  Then you can create and expand LVs as you like. Any of the LVM tutorials should provide sufficient guidance for this.


Let me see the commands. You can look up the options.

**pvcreate** - to take the partition from the new drive and add it to the existing VG.
**vgextend** - to take the PV and include it in the VG. The VG is where the physical storage gets put into a single bin to be requested.
**lvcreate** and **lvextend**  - to create any new LVs you like and/or use lvextend to make existing LVs bigger. 
**mkfs** - to put a file system (say ext4) onto any new LV.  If you use lvextend on an existing LV with ext4 as the file system, you can use the **--resizefs** _option_ to automatically increase the file system in the same command.  If you forget that, then you'll need to use **resize2fs** (a separate command).

LVs are basically partitions that can be modified, made larger, as needed, while still being used.  The best practice is to only size LVs to what is needed a few months at a time, then increase them.  Increasing an LV while it is in use is trivial, 5 seconds. Reducing an LV is a huge hassle, has to be done off line (not booted, not in-use) and should be avoided.

Making separate LVs for different parts of the system is a "best practice". While we can go crazy, it really makes sense to keep /home and everything else separate. This way the OS is inside a different LV than your personal files. Later, that will be very helpful.  I like to keep swap in a separate LV too.

When asking for specific help with LVM layouts, please post the command and output from these commands:
```
sudo pvs
sudo vgs
sudo lvs
df -hT -x squashfs -x tmpfs -x devtmpfs

```
Wrap that all in code-tags.  [https://ubuntuforums.org/misc.php?do=bbcode#code](https://ubuntuforums.org/misc.php?do=bbcode#code) explains how.
The output from those commands tells a clear story.

IF you want to show a higher level overview, use 
```
lsblk -e 7 -o name,size,type,fstype,mountpoint
```
The code tags are really important since these are all tables and columns matter.

---

### Post by Raymond Day on 2020-11-30
I been trying commands but nothing is working. I don't know maybe need to format the 128GB to be used not sure.

Did the commands you said here is how it came back.

```
root@rayday-tablet:~# pvs
  PV             VG         Fmt  Attr PSize    PFree
  /dev/mmcblk0p3 ubuntu-vg  lvm2 a--    27.40g       0
  /dev/mmcblk2   ubuntu--vg lvm2 a--  <116.48g <116.48g
root@rayday-tablet:~# vgs
  VG         #PV #LV #SN Attr   VSize    VFree
  ubuntu--vg   1   0   0 wz--n- <116.48g <116.48g
  ubuntu-vg    1   1   0 wz--n-   27.40g       0
root@rayday-tablet:~# lvs
  LV        VG        Attr       LSize  Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  ubuntu-lv ubuntu-vg -wi-ao---- 27.40g                                         
root@rayday-tablet:~# df -hT -x squashfs -x tmpfs -x devtmpfs
Filesystem                        Type  Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--vg-ubuntu--lv ext4   27G  6.2G   20G  25% /
/dev/mmcblk0p2                    ext4  976M  105M  805M  12% /boot
/dev/mmcblk0p1                    vfat  511M  7.8M  504M   2% /boot/efi
root@rayday-tablet:~# lsblk -e 7 -o name,size,type,fstype,mountpoint
NAME                        SIZE TYPE FSTYPE      MOUNTPOINT
mmcblk0                    28.9G disk
&#9500;&#9472;mmcblk0p1                 512M part vfat        /boot/efi
&#9500;&#9472;mmcblk0p2                   1G part ext4        /boot
&#9492;&#9472;mmcblk0p3                27.4G part LVM2_member
  &#9492;&#9472;ubuntu--vg-ubuntu--lv  27.4G lvm  ext4        /
mmcblk0boot0                  4M disk
mmcblk0boot1                  4M disk
mmcblk2                   116.5G disk LVM2_member
root@rayday-tablet:~#
```

The the groups have to be named the same? Because they are

  ubuntu--vg   1   0   0 wz--n- <116.48g <116.48g
  ubuntu-vg    1   1   0 wz--n-   27.40g       0

One has 2 -- and the other don't.

Thank you.

-Raymond Day

---

### Post by TheFu on 2020-11-30
If the VG isn't using the exact same name, then it isn't 1 VG. You'll need to fix that.

Only LV need to be formatted. If you extend an existing LV, then the file system must be resized to match the total LV size. Post #11 above has the option to do that. for the lvextend command.

But 1st thing to fix is the PV needs to be added to the correct VG. Until that happens, forgetaboutit.
You'll need to delete the wrong VG.  **sudo vgremove ubuntu--vg**

---

### Post by Raymond Day on 2020-12-01
Guess I have to add one now I did delete it like you said and it worked with no errors.

Went to add it like this:

```
root@rayday-tablet:~# vgremove ubuntu--vg
  Volume group "ubuntu--vg" successfully removed
root@rayday-tablet:~# vgs
  VG        #PV #LV #SN Attr   VSize  VFree
  ubuntu-vg   1   1   0 wz--n- 27.40g    0
root@rayday-tablet:~# vgcreate ubuntu-vg /dev/mmcblk2
  /dev/ubuntu-vg: already exists in filesystem
  Run `vgcreate --help' for more information.
root@rayday-tablet:~# vgs
  VG        #PV #LV #SN Attr   VSize  VFree
  ubuntu-vg   1   1   0 wz--n- 27.40g    0
root@rayday-tablet:~# vgcreate ubuntu-vg /dev/mmcblk0p3 /dev/mmcblk2
  /dev/ubuntu-vg: already exists in filesystem
  Run `vgcreate --help' for more information.
root@rayday-tablet:~#
```

Guess I have to make it now with the same name.

To bad gparted can add one easy. I guess they need to make this easier to do. Not even a install would make it boot when it seen it as one drive.

Thank you.

-Raymond Day

---

### Post by Raymond Day on 2020-12-01
Thanks for all your help. Looks like it worked. I did commands and had to reboot it.

It shows it like this now.

```
root@rayday-tablet:~# vgs
  VG        #PV #LV #SN Attr   VSize    VFree
  ubuntu-vg   2   1   0 wz--n- <143.88g <116.48g
root@rayday-tablet:~# df -h
Filesystem                         Size  Used Avail Use% Mounted on
udev                               1.8G     0  1.8G   0% /dev
tmpfs                              376M  1.7M  375M   1% /run
/dev/mapper/ubuntu--vg-ubuntu--lv   27G  6.8G   19G  27% /
tmpfs                              1.9G     0  1.9G   0% /dev/shm
tmpfs                              5.0M     0  5.0M   0% /run/lock
tmpfs                              1.9G     0  1.9G   0% /sys/fs/cgroup
/dev/mmcblk0p2                     976M  199M  711M  22% /boot
/dev/loop0                          55M   55M     0 100% /snap/core18/1880
/dev/loop1                          72M   72M     0 100% /snap/lxd/16099
/dev/loop2                          56M   56M     0 100% /snap/core18/1932
/dev/loop3                          32M   32M     0 100% /snap/snapd/10238
/dev/mmcblk0p1                     511M  7.8M  504M   2% /boot/efi
/dev/loop4                          68M   68M     0 100% /snap/lxd/18150
/dev/loop5                          31M   31M     0 100% /snap/snapd/9721
tmpfs                              376M     0  376M   0% /run/user/0
root@rayday-tablet:~#
```

It did not save my last commands in /root/.bash_history and I typed exit before I rebooted with Webmin.

But it worked. Not I hope it don't use up all that space.

O I just seen I don't think it sees all the space the df -l shows it still the same size.

-Raymond Day

---

### Post by TheFu on 2020-12-01
An existing VG can't be created again.  You need to add a PV to the existing VG.  Perhaps the **vgextend** command is what you want? Probably should review the vgchange, vgck, and vgconvert commands too.  Any chance vgmerge was looked at too? I've not noticed that command before. Could have been what you wanted yesterday. Sorry.

To see the different commands (the names are good hints for what they do), use tab-completion.
```
pv{tab}{tab}
vg{tab}{tab}
lv{tab}{tab}
```
Lots of helpful commands there.  The only ones I'd STRONGLY advise against using is vgresize and lvresize. It is too easy to screw up the options and do exactly the opposite of what you intend.  Instead, use vgreduce or vgextend or lvreduce or lvextend.

Don't forget the --resizefs option whenever changing LV sizes.

If you want to use advanced options for how the storage devices are merged, then you'll need to carefully read the manpages. LVM isn't something you can just throw commands into hoping for the best. There are many caveats. If you want to stripe or concatenate or use RAID0 or use RAID1 or use RAID10 ... there are specific options to control most details. These options can drastically impact the result and performance. 

Whenever and however different storage devices are merged into a VG, if any of those devices fails, all the data on all the devices will be lost. Never forget that. Expect a device to fail.

---

### Post by Raymond Day on 2020-12-01
Did commands to make it the full size but it don't look like it worked.

```
root@rayday-tablet:~# vgdisplay ubuntu-vg
  --- Volume group ---
  VG Name               ubuntu-vg
  System ID
  Format                lvm2
  Metadata Areas        2
  Metadata Sequence No  12
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                1
  Open LV               1
  Max PV                0
  Cur PV                2
  Act PV                2
  VG Size               <143.88 GiB
  PE Size               4.00 MiB
  Total PE              36833
  Alloc PE / Size       7015 / 27.40 GiB
  Free  PE / Size       29818 / <116.48 GiB
  VG UUID               JCWbYt-W1V2-W1Op-z77J-29Tl-7C71-X0o8Uz

root@rayday-tablet:~# lvextend -L +116.48GB /dev/mapper/ubuntu--vg-ubuntu--lv
  Rounding size to boundary between physical extents: 116.48 GiB.
  Insufficient free space: 29819 extents needed, but only 29818 available
root@rayday-tablet:~# lvextend -L +29819 /dev/mapper/ubuntu--vg-ubuntu--lv
  Rounding size to boundary between physical extents: 29.12 GiB.
  Size of logical volume ubuntu-vg/ubuntu-lv changed from 27.40 GiB (7015 extents) to 56.52 GiB (14470 extents).
  Logical volume ubuntu-vg/ubuntu-lv successfully resized.
root@rayday-tablet:~# df -h
Filesystem                         Size  Used Avail Use% Mounted on
udev                               1.8G     0  1.8G   0% /dev
tmpfs                              376M  1.7M  375M   1% /run
/dev/mapper/ubuntu--vg-ubuntu--lv   27G  6.8G   19G  27% /
tmpfs                              1.9G     0  1.9G   0% /dev/shm
tmpfs                              5.0M     0  5.0M   0% /run/lock
tmpfs                              1.9G     0  1.9G   0% /sys/fs/cgroup
/dev/mmcblk0p2                     976M  199M  711M  22% /boot
/dev/loop0                          55M   55M     0 100% /snap/core18/1880
/dev/loop1                          72M   72M     0 100% /snap/lxd/16099
/dev/loop2                          56M   56M     0 100% /snap/core18/1932
/dev/loop3                          32M   32M     0 100% /snap/snapd/10238
/dev/mmcblk0p1                     511M  7.8M  504M   2% /boot/efi
/dev/loop4                          68M   68M     0 100% /snap/lxd/18150
/dev/loop5                          31M   31M     0 100% /snap/snapd/9721
tmpfs                              376M     0  376M   0% /run/user/0
root@rayday-tablet:~#
```

-Raymond Day

---

### Post by Raymond Day on 2020-12-01
How can I get it to be the full size. I did this command and looks like it is 56G in size now. should be 32+128 in size.

```
root@rayday-tablet:~# resize2fs /dev/mapper/ubuntu--vg-ubuntu--lv
resize2fs 1.45.5 (07-Jan-2020)
Filesystem at /dev/mapper/ubuntu--vg-ubuntu--lv is mounted on /; on-line resizing required
old_desc_blocks = 4, new_desc_blocks = 8
The filesystem on /dev/mapper/ubuntu--vg-ubuntu--lv is now 14817280 (4k) blocks long.

root@rayday-tablet:~# df -h
Filesystem                         Size  Used Avail Use% Mounted on
udev                               1.8G     0  1.8G   0% /dev
tmpfs                              376M  1.7M  375M   1% /run
/dev/mapper/ubuntu--vg-ubuntu--lv   56G  6.8G   47G  13% /
tmpfs                              1.9G     0  1.9G   0% /dev/shm
tmpfs                              5.0M     0  5.0M   0% /run/lock
tmpfs                              1.9G     0  1.9G   0% /sys/fs/cgroup
/dev/mmcblk0p2                     976M  199M  711M  22% /boot
/dev/loop0                          55M   55M     0 100% /snap/core18/1880
/dev/loop1                          72M   72M     0 100% /snap/lxd/16099
/dev/loop2                          56M   56M     0 100% /snap/core18/1932
/dev/loop3                          32M   32M     0 100% /snap/snapd/10238
/dev/mmcblk0p1                     511M  7.8M  504M   2% /boot/efi
/dev/loop4                          68M   68M     0 100% /snap/lxd/18150
/dev/loop5                          31M   31M     0 100% /snap/snapd/9721
tmpfs                              376M     0  376M   0% /run/user/0
root@rayday-tablet:~#
```

-Raymond Day

---

### Post by Raymond Day on 2020-12-01
Looked in Webmin and it was easy it had a "Use all Free VG space" I clicked it on and said save. It like on sec. it came back and I did a df -h.

```
root@rayday-tablet:~# df -h
Filesystem                         Size  Used Avail Use% Mounted on
udev                               1.8G     0  1.8G   0% /dev
tmpfs                              376M  1.7M  375M   1% /run
/dev/mapper/ubuntu--vg-ubuntu--lv  142G  6.8G  129G   5% /
tmpfs                              1.9G     0  1.9G   0% /dev/shm
tmpfs                              5.0M     0  5.0M   0% /run/lock
tmpfs                              1.9G     0  1.9G   0% /sys/fs/cgroup
/dev/mmcblk0p2                     976M  199M  711M  22% /boot
/dev/loop0                          55M   55M     0 100% /snap/core18/1880
/dev/loop1                          72M   72M     0 100% /snap/lxd/16099
/dev/loop2                          56M   56M     0 100% /snap/core18/1932
/dev/loop3                          32M   32M     0 100% /snap/snapd/10238
/dev/mmcblk0p1                     511M  7.8M  504M   2% /boot/efi
/dev/loop4                          68M   68M     0 100% /snap/lxd/18150
/dev/loop5                          31M   31M     0 100% /snap/snapd/9721
tmpfs                              376M     0  376M   0% /run/user/0
root@rayday-tablet:~#
```

Thanks to Webmin it made it easy.

-Raymond Day

---

### Post by TheFu on 2020-12-01
Did you read my post #16? 

Webmin is something to be avoided, especially when you don't know what you are doing, unless you have an experienced mentor there who specifically setup webmin and said for which 4 things it should be used.  Webmin is a security nightmare.  Please be 100% it can only be accessed from the same host, never remotely.

The df output seems to show storage. Would be good to see what webmin did - vgs, lvs, pvs.

---

### Post by Raymond Day on 2020-12-01
The 3 commands look like this now.

```
root@rayday-tablet:~# vgs
  VG        #PV #LV #SN Attr   VSize    VFree
  ubuntu-vg   2   1   0 wz--n- <143.88g    0
root@rayday-tablet:~# lvs
  LV        VG        Attr       LSize    Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  ubuntu-lv ubuntu-vg -wi-ao---- <143.88g                                       
root@rayday-tablet:~# pvs
  PV             VG        Fmt  Attr PSize    PFree
  /dev/mmcblk0p3 ubuntu-vg lvm2 a--    27.40g    0
  /dev/mmcblk2   ubuntu-vg lvm2 a--  <116.48g    0
root@rayday-tablet:~#
```

Seems to be working good now.

This is nice. The tablet only came with a 32GB built in like SSD. But it has a SD card slot and can add a SD card in it and with Ubuntu can make it see it as one big SSD then.

On a cellphone can do that but not all apps can run on the SD card.

-Raymond Day

---

### Post by TheFu on 2020-12-01
> **Raymond Day said:**
> The 3 commands look like this now.
 
Seems to be working good now.


Yep. That looks like what you wanted.

But it is still a really bad idea.  The 32G SSD was perfect for the OS and the other storage would be perfect for all other stuff like /home/ and any extra data.  This could have been done in a way that reduces the chances of data loss from a failure by a little over 50%.

Oh well. Think we've beating that to death. Good bye. I hope when either storage device fails that you aren't using the machine anymore or have excellent backups so it is an inconvenience, not a terrible day.

---

### Post by DuckHook on 2020-12-01
> **TheFu said:**
> &#8230;But it is still a really bad idea.
To others who might read this thread:

While the purely technical aspects of this thread are valid enough, the problem with it is that the OP's implementation leads to a highly fragile and brittle system. TheFu estimates increased chances of failure loss at a little over 50%. In truth, it is **much** higher. This is because:

[list=1]
[*]SD cards are far more likely to fail than main tablet system storage.
[*]Even brand new SD cards vary massively in quality.
[*]Even better quality SD cards are not designed with very high write cycles.
[*]SD cards are a removable media that introduce further failure points in their buses and physical contacts.
[*]People forgetfully eject their SD cards on running tablets all the time.
[/list]
To say this is a "really bad idea" is a "really vast understatement". #-o

---

