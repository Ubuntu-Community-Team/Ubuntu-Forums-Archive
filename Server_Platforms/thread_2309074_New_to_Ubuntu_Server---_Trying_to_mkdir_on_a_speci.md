---
title: "New to Ubuntu Server--- Trying to mkdir on a specific hard drive"
date: 2016-01-07
forum: Server Platforms
---

### Post by steve239 on 2016-01-07
Hello,

I am a noob so please forgive my ignorance.

I have three physical Hard Drives (eventually it will be four).  I want specific folders on specific drives and have samba share them all.

i.e.   sdb would have a "Movies" folder
       sdc would have a "TV" folder

and when I open samba from a Windows box it would list Movies & TV.


Is this possible?

```

root@Plex-OldMill:/home/plexadmin# [B]sudo parted -l
Model: ATA SanDisk SDSSDA12 (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
 
Number  Start   End    Size   File system  Name  Flags
 1      1049kB  538MB  537MB  fat32              boot
 2      538MB   794MB  256MB  ext2
 3      794MB   120GB  119GB                     lvm
 
 
Model: ATA WDC WD20EARS-00M (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
 
Number  Start   End     Size    File system  Name     Flags
 1      1049kB  2000GB  2000GB               primary
 
 
Model: ATA TOSHIBA MD04ACA5 (scsi)
Disk /dev/sdc: 5001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
 
Number  Start   End     Size    File system  Name     Flags
 1      1049kB  5001GB  5001GB               primary
 
 
Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/Plex--OldMill--vg-root: 97.9GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
 
Number  Start  End     Size    File system  Flags
 1      0.00B  97.9GB  97.9GB  ext4
 
 
Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/Plex--OldMill--vg-swap_1: 21.3GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
 
Number  Start  End     Size    File system     Flags
 1      0.00B  21.3GB  21.3GB  linux-swap(v1)
```

---

### Post by ian-weisser on 2016-01-07
You seem to have an LVM that stretches across all three drives.
While using LVM, you cannot decide which drive to store a file upon. That's the big feature of LVM - it all looks like one big drive, and you don't care about the details.

You can use LVM tools to shrink that LVM space, partition the freed space as ext (non-LVM), and mount the new partition for storing your files.
Do NOT use any other partitiong tool to shrink the LVM - you will destroy your system. Use only LVM tools to manuipulate LVM partitions.

---

### Post by steve239 on 2016-01-08
Ian....

I have not gotten too far and would rather start with a format and a clean install.  

1. Do you know how to format the disks from the installer?  Remove existing partitions and start clean....

2. What should I choose in the installer to achieve what I am looking for?  Guided?  Manual?  

My brain is used to Windows and I know that Linux/ Ubuntu is different... but I don't know any of the basic details.

Thanks for the help!  Steve

---

### Post by ian-weisser on 2016-01-08
Choose Guided, and let the installer do the default.
Do not choose LLVM or Encrypted.

---

### Post by steve239 on 2016-01-08
Ian.....

Clean install complete... I used "Guided-- Use entire Disk"

here is the output of parted -l

```

root@Plex-OldMill:/home/plexadmin# parted -l

Model: ATA SanDisk SDSSDA12 (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  98.7GB  98.7GB  primary   ext4            boot
 2      98.7GB  120GB   21.3GB  extended
 5      98.7GB  120GB   21.3GB  logical   linux-swap(v1)


Model: ATA WDC WD20EARS-00M (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name     Flags
 1      1049kB  2000GB  2000GB               primary

Model: ATA TOSHIBA MD04ACA5 (scsi)
Disk /dev/sdc: 5001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system  Name     Flags
 1      1049kB  5001GB  5001GB               primary

Now that the LVM is removed how should I proceed?

I have created the folders:

root@Plex-OldMill:/# ls
bin   dev  home        lib    lost+found  mnt  _**plex**_  root  sbin  sys  usr  vmlinuz
boot  etc  initrd.img  lib64  media       opt  proc  run   srv   tmp  var

root@Plex-OldMill:/# cd /plex
root@Plex-OldMill:/plex# ls
Movies  Music  TV

```


What is the command to mount **sdc1 **to **Movies**. etc.?

I also assume that I need to "add this to fstab" so that the drives will "automount" on boot?


Thanks,

Steve

---

### Post by Bashing-om on 2016-01-09
steve239; ian-weisser;

Subscribed to this thread as I am interested in learning the result of mixing msdos and GPT partitioning schemes on alternate hard drives.

As to :
> 
I also assume that I need to "add this to fstab" so that the drives will "automount" on boot?

You are correct, if you want these devices to be available upon booting, one must tell the system so in the /etc/fstab file.
see:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131) <- bodhi.zazen
[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336) <-Manualy edit fstab - why (Morbius1)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.comunity/Mount/](https://help.ubuntu.comunity/Mount/)
These say much better than I can; then we continue this discussion.

[INDENT][INDENT]progress is made
[INDENT][INDENT][INDENT][INDENT]in small steps
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by matt_symes on 2016-01-09
@steve239. Please use code tags around any output you post from the terminal.

You use code tags like this

[noparse]```
Output from terminal
```[/noparse]

to get output like this

```
Output from terminal
```

Code tags preserve formatting and make terminal output much easier to read.

Thank you :)

---

### Post by nerdtron on 2016-01-10
> **steve239 said:**
> 

What is the command to mount **sdc1 **to **Movies**. etc.?

I also assume that I need to "add this to fstab" so that the drives will "automount" on boot?


Thanks,

Steve

To mount a partition:
```
 sudo mount /dev/sdc1 /plex/Movies 
```

To automount the drive on boot, you need to edit the /etc/fstab file and add an entry for the drive details
First make sure that /dev/sdc1 is not in your fstab. You need the UUID of /dev/sdc1 to add an entry to fstab:
```
 sudo blkid
cat /etc/fstab 
```

Then on your fstab file, add the following line (be sure to add the correct UUID), also assuming your hard drive is formatted is ext4:
```
 UUID=6785eb86-c596-4229-85fb-4d30c8          /plex/Movies        ext4      defaults      0      0 
```

To test if the fsab entry is correct, try to mount the drives: 
```
 mount -va 
```

---

