---
title: "Disk /dev/mapper/ubuntu-root doesn't contain a valid partition table"
date: 2012-05-28
forum: Server Platforms
---

### Post by Kainwolf on 2012-05-28
I am having a server installed at a remote data centre; running 12.04.  I'm getting the following when I do an fdisk -l:

```
kain@kyuurem:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00094083

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758   976771071   488134657    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5          501760   976771071   488134656   8e  Linux LVM

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001c522

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   612853759   306425856   83  Linux
/dev/sdb2       612855806   625141759     6142977    5  Extended
/dev/sdb5       612855808   625141759     6142976   82  Linux swap / Solaris

Disk /dev/mapper/ubuntu-root: 497.7 GB, 497662558208 bytes
255 heads, 63 sectors/track, 60504 cylinders, total 971997184 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu-root doesn't contain a valid partition table

Disk /dev/mapper/ubuntu-swap_1: 2134 MB, 2134900736 bytes
255 heads, 63 sectors/track, 259 cylinders, total 4169728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu-swap_1 doesn't contain a valid partition table
```

The following is the contents of /dev/mapper:
```
kain@kyuurem:~$ ls -l /dev/mapper
total 0
crw------- 1 root root 10, 236 May 26 02:39 control
lrwxrwxrwx 1 root root       7 May 26 02:39 ubuntu-root -> ../dm-0
lrwxrwxrwx 1 root root       7 May 26 02:39 ubuntu-swap_1 -> ../dm-1
```

And mount:
```
kain@ubuntu:~$ sudo mount
/dev/mapper/ubuntu-root on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sda1 on /boot type ext2 (rw)
/dev/sdb1 on /home/old type ext4 (rw)
```

I'm particularly concerned that / maps to /dev/mapper/ubuntu-root which is listed as not containing a partition table.

Right now, everything seems to be working correctly.  Is this ok, or something that will cause OS corruption at some point in the future?

---

### Post by theluli on 2012-05-29
Hi

For this one 

  Device Boot      Start         End      Blocks   Id  System 
/dev/sda1   *        2048      499711      248832   83  Linux
 /dev/sda2          501758   976771071   488134657    5  Extended 
Partition 2 does not start on physical sector boundary. /dev/sda5          501760   976771071   488134656   8e  Linux LVM

l think that you did not make a good partition as Linux require 

and for other things you don need to worry much , most of times when you try to LVM , you will get this kind of messages

---

### Post by darkod on 2012-05-29
I don't think fdisk can understand the LVM content so it reports no valid partition table. It does the same with software raid even though your array works just fine.

Try parted for example.
sudo parted /dev/sda print all

See what that prints for the LVM.

As for the message that a partition doesn't start on a cylinder boundary, it's not a problem at all. Just a report. There is no requirement to start each partition at cylinder boundary.

---

### Post by SAngeli on 2013-02-13
Hi,
I also noticed, when I run fdisk -l , that I have the following outputs:
```
Disk /dev/mapper/ubuntu-root: 76.3 GB, 76332138496 bytes
The disk  /dev/mapper/ubuntu-root doesn't contain a valid partition table

Disk /dev/mapper/ubuntu-swap_1: 5364 MB, 5364514816 byte
The disk  /dev/mapper/ubuntu-swap_1 doesn't contain a valid partition table
```

I did not understand the answers posted.
I wish to know if I do have to be concerned about fdisk messages or I can just ignore them.

Here is what I have in fstab file:
```
/dev/mapper/ubuntu-root /       ext4    errors=remount-ro                       0       1

UUID=5be45eae-b83c-4ff8-8a29-a3d322cba241 /boot           ext2    defaults      0       2
/dev/mapper/ubuntu-swap_1 none  swap            sw                              0       0

```

Please if possible comment what are the three lines in the fstab I posted. I know the third is for swap file. What about the first two lines?

Thank you,
Spiro

---

### Post by darkod on 2013-02-13
I just answered it above in post #3. fdisk can't understand LVM fully, so you can ignire the messages about missing partition table.

As for your fstab question, look at the mount points. The first line is for root, mount point /.
The second is for /boot.

---

