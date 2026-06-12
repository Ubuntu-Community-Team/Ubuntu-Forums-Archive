---
title: "How to expand main partition after RAID expension ?"
date: 2012-11-21
forum: Server Platforms
---

### Post by Andre-D on 2012-11-21
I tried using gparted, - expanded a partition there, but apparaently without any effect. forced fsck - thinkgs are fine, but the partition is still small.

Please help me use all the space..
posting output of
sudo fdisk -l
df-h



ndre@ODIN2:~$ sudo fdisk -l
[sudo] password for andre: 

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 7999.4 GB, 7999376588800 bytes
255 heads, 63 sectors/track, 972535 cylinders, total 15623782400 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  4294967295  2147483647+  ee  GPT

Disk /dev/mapper/ODIN2-root: 5990.6 GB, 5990552436736 bytes
255 heads, 63 sectors/track, 728309 cylinders, total 11700297728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ODIN2-root doesn't contain a valid partition table

Disk /dev/mapper/ODIN2-swap_1: 8518 MB, 8518631424 bytes
255 heads, 63 sectors/track, 1035 cylinders, total 16637952 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ODIN2-swap_1 doesn't contain a valid partition table

Disk /dev/sdb: 1019 MB, 1019215872 bytes
32 heads, 61 sectors/track, 1019 cylinders, total 1990656 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table
andre@ODIN2:~$ df
Filesystem              1K-blocks       Used  Available Use% Mounted on
/dev/mapper/ODIN2-root 5804055776 3517075240 1994473096  64% /
udev                      4045896          4    4045892   1% /dev
tmpfs                     1622164       1424    1620740   1% /run
none                         5120          0       5120   0% /run/lock
none                      4055404          0    4055404   0% /run/shm
none                       102400          0     102400   0% /run/user
cgroup                    4055404          0    4055404   0% /sys/fs/cgroup
/dev/sda2                  234153      54123     167538  25% /boot
/dev/sda1          


andre@ODIN2:~$ df -h
Filesystem              Size  Used Avail Use% Mounted on
/dev/mapper/ODIN2-root  5.5T  3.3T  1.9T  64% /
udev                    3.9G  4.0K  3.9G   1% /dev
tmpfs                   1.6G  1.4M  1.6G   1% /run
none                    5.0M     0  5.0M   0% /run/lock
none                    3.9G     0  3.9G   0% /run/shm
none                    100M     0  100M   0% /run/user
cgroup                  3.9G     0  3.9G   0% /sys/fs/cgroup
/dev/sda2               229M   53M  164M  25% /boot
/dev/sda1               190M  132K  190M   1% /boot/efi

---

### Post by darkod on 2012-11-21
First, you see that gpt warning about fdisk? Don't use fdisk with gpt disks, use parted instead.

sudo parted -l

Second, what is /dev/sda and what is /dev/mapper/ODIN2-root?

Is that some type of LVM?

/dev/sda does seem to be shown as 8TB but I can't see how that's related to ODIN2-root?

Maybe parted will show more understandable results.

---

### Post by spynappels on 2012-11-21
Also, when you resize a partition, you will also need to resize the filesystem on that partition.

For example, if you had a 100GB partition with an ext3 file system on it, and you used Gparted to grow the partition to 200GB, the ext3 filesystem would still only be 100GB unless it was grown to fill the entire partition.

You should look at resize2fs for normal setups, but if you are dealing with LVM, you should look at vgextend and lvresize.

---

### Post by Andre-D on 2012-11-21
thanks, you are right.
And yes, Server installation suggested LVM



andre@ODIN2:~$ sudo parted -l
Model: DELL PERC H710 (scsi)
Disk /dev/sda: 7999GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name                  Flags
 1      1049kB  200MB   199MB   fat32        EFI System Partition  boot
 2      200MB   456MB   256MB   ext2
 3      456MB   7999GB  7999GB                                     lvm


Error: /dev/sdb: unrecognised disk label                                  

Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ODIN2-swap_1: 8519MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system     Flags
 1      0.00B  8519MB  8519MB  linux-swap(v1)


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ODIN2-root: 5991GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  5991GB  5991GB  ext4


Warning: Unable to open /dev/sr1 read-write (Read-only file system).  /dev/sr1
has been opened read-only.
Error: Invalid partition table - recursive partition on /dev/sr1.         
Ignore/Cancel? i                                                          
Model: Unknown (unknown)
Disk /dev/sr1: 247MB
Sector size (logical/physical): 2048B/2048B
Partition Table: msdos

Number  Start  End  Size  Type  File system  Flags


andre@ODIN2:~$

---

### Post by spynappels on 2012-11-21
In this case I'd look at using lvresize to extend lv /dev/mapper/ODIN2-root and then resize2fs to grow the ext4 filesystem.

You might need to extend the volume group too before doing this using vgextend.

---

### Post by Andre-D on 2012-11-21
thank you, once you helped me by telling that I needed lvresize, I found:

[http://www.tcpdump.com/kb/os/linux/lvm-resizing-guide/all-pages.html](http://www.tcpdump.com/kb/os/linux/lvm-resizing-guide/all-pages.html)
- it worked perfectly fine.

Thank you.

---

### Post by darkod on 2012-11-21
Look here for more details about LVM:
[http://www.howtogeek.com/howto/40702/how-to-manage-and-use-lvm-logical-volume-management-in-ubuntu/](http://www.howtogeek.com/howto/40702/how-to-manage-and-use-lvm-logical-volume-management-in-ubuntu/)

The section about extending a LV is approx in the middle of the page.

It should be something like:
1. Run
sudo vgdisplay

to show you the size of the VG.

2. You can extend the LV to a size little smaller than the size of the VG with something like:
sudo lvextend -LXXXXG /dev/ODIN2/root

replacing the XXXX with the size you want it to have after the extend. Note this is not the size you are adding, it's the final size it will have, for example 7999G.

3. After that you will have to expand the filesystem too:
sudo resize2fs /dev/ODIN2/root

That should do it for extending. Shrinking is a little bit more complicated.

---

