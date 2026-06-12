---
title: "Mounting windows software mirror"
date: 2012-01-12
forum: Server Platforms
---

### Post by grezzo on 2012-01-12
I'm switching my windows server to Ubuntu and am trying to get my software RAID1 (mirror) that I created in Windows to show up in Ubuntu. I have read that this is possible using mdadm, but I'm having trouble.

Here is what I'm trying:
```
Script started on Thu 12 Jan 2012 12:22:33 GMT
graeme@MediaCentre:~/Desktop$ cat /proc/partitions                              major minor  #blocks  name

   8        0  120060864 sda
   8        1  117974016 sda1
   8        2          1 sda2
   8        5    2083840 sda5
   8       16 1465138584 sdb
   8       17 1465136128 sdb1
   8       32 1465138584 sdc
   8       33 1465136128 sdc1
graeme@MediaCentre:~/Desktop$ sudo mdadm --build /dev/md0 --chunk=128 --level=1 --raid-devices=2 /dev/sdb1 /dev/sdc1
[sudo] password for graeme:
mdadm: array /dev/md0 built and started.
graeme@MediaCentre:~/Desktop$ sudo mkdir /media/WinMirror/
mkdir: cannot create directory `/media/WinMirror/': File exists
graeme@MediaCentre:~/Desktop$ sudo mount -t ntfs /dev/md0 /media/WinMirror
Failed to read last sector (5860544511): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/md0': Invalid argument
The device '/dev/md0' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
graeme@MediaCentre:~/Desktop$ exit
exit

Script done on Thu 12 Jan 2012 12:23:23 GMT
```I get the same thing when I try 64 chunks, and if I list the disks in the other order.

Does anyone know what I'm doing wrong here?

Thanks

Graeme

---

### Post by rubylaser on 2012-01-12
I assume, you're following [this thread]("http://ubuntuforums.org/showthread.php?t=833653").  Have you tried following all of the suggestions in that thread?  Like was Windows shut down cleanly, have you tried to switch the order of your drives when building the array, etc. ?

---

### Post by grezzo on 2012-01-12
I have tried changing the order of the disks, and windows was shut down cleanly. I do still have my windows image on another disk so I can try booting that, checking that it still mounts, then shutting down cleanly again and see if that makes a difference.

---

### Post by grezzo on 2012-01-12
I think I've just discovered that it's not possible to "build" a RAID1 and "build"ing is the only way to view a Windows software RAID. Can someone confirm that for me?

This is what I managed to get out of mdadm:```
graeme@MediaCentre:~$ sudo mdadm --build --help
Usage:  mdadm --build device -chunk=X --level=Y --raid-devices=Z devices

 This usage is similar to --create.  The difference is that it creates
 a legacy array without a superblock.  With these arrays there is no
 difference between initially creating the array and subsequently
 assembling the array, except that hopefully there is useful data
 there in the second case.

 The level may only be 0, raid0, or linear.
 All devices must be listed and the array will be started once complete.
 Options that are valid with --build (-B) are:
  --bitmap=          : file to store/find bitmap information in.
  --chunk=      -c   : chunk size of kibibytes
  --rounding=        : rounding factor for linear array (==chunk size)
  --level=      -l   : 0, raid0, or linear
  --raid-devices= -n : number of active devices in array
  --bitmap-chunk=    : bitmap chunksize in Kilobytes.
  --delay=      -d   : bitmap update delay in seconds.

```

---

### Post by rubylaser on 2012-01-12
Okay, I'm confused about what you're trying to do now.  If you're trying to just create a software RAID1 mirror, you can set that up during the install with the alternate install disk, or with mdadm --create (you wouldn't use build for this).

If, you're trying to mount your windows array to do something with the data, then you'd need to use the --build option.  The build option should support all of these versions: linear, stripe, raid0, 0, raid1, multipath, mp, and faulty are valid per the [man page]("http://linux.die.net/man/8/mdadm"). I'm very firmiliar with mdadm, but I wouldn't try what you're doing other than to mount and backup my data. Once that's complete, I would create an mdadm array with an ext4 filesystem after the backup.

---

