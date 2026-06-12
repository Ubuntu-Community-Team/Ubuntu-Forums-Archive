---
title: "Change harddrive from FAT32 to NTFS"
date: 2010-06-12
forum: Server Platforms
---

### Post by imjakes on 2010-06-12
Im usning ubuntu server 10.04 (Command-line)

My second harddrive is FAT32 but i would like to change it to HTFS so i can store large files (larger than 2GB)

How do i do that?

> jakes@jakes-server:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 Gb, 1000204886016 byte
255 heads, 63 sectors/track, 121601 cylinders
Units = cylindre of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b36a6

    Enhed Opstart   Start         ****     Blokke   Id  System
/dev/sda1   *           1      120897   971103232   83  Linux
/dev/sda2          120898      121602     5656577    5  Udvidet
/dev/sda5          120898      121602     5656576   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 Gb, 1000204886016 byte
81 heads, 63 sectors/track, 382818 cylinders
Units = cylindre of 5103 * 512 = 2612736 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd3ae9386

    Enhed Opstart   Start         ****     Blokke   Id  System
/dev/sdb1               1      382819   976761560    b  W95 FAT32


---

### Post by John Bean on 2010-06-12
Without losing data you mean?

Good question. I know how to do it on a Windows box but I have no idea how to do it with Linux tools. Surely it must be possible though...

---

### Post by imjakes on 2010-06-12
> **John Bean said:**
> Without losing data you mean?

Good question. I know how to do it on a Windows box but I have no idea how to do it with Linux tools. Surely it must be possible though...

The hardrive is empty so datalos is not a problem :)

---

### Post by John Bean on 2010-06-12
> **imjakes said:**
> The hardrive is empty so datalos is not a problem :)

Oh, that's easy then. Just reformat it with mkntfs (mkfs.ntfs) :-)

---

### Post by HermanAB on 2010-06-12
To be a little more specific:

See what ismounted:
$ mount

if you recognize the drive, unmount it:
$ sudo umount -l /dev/sdXY

Format it:
$ sudo mkfs.ntfs -L NTFSDISK -Q /dev/sdXY

Mount it:
$ sudo mkdir /mnt/ntfsdisk
$ sudo mount /dev/sdXY /mnt/ntfsdisk

Modify /etc/fstab to suit so it will automount at startup.

---

### Post by imjakes on 2010-06-12
> **HermanAB said:**
> To be a little more specific:

See what ismounted:
$ mount

if you recognize the drive, unmount it:
$ sudo umount -l /dev/sdXY

Format it:
$ sudo mkfs.ntfs -L NTFSDISK -Q /dev/sdXY

Mount it:
$ sudo mkdir /mnt/ntfsdisk
$ sudo mount /dev/sdXY /mnt/ntfsdisk

Modify /etc/fstab to suit so it will automount at startup.

Worked like a charm except im not sure what to put in /etc/fstab.
Now for that drive it says :
/dev/sdb1 /home/fileshare2 vfat iocharset=utf8,umask=000 0 0

---

### Post by oldfred on 2010-06-12
I have two different style entries and I think the one with defaults only works better. The the other does set more permissions.

# Entry for /dev/sdc2 :
UUID=44332FD360AA9657                      /home/fred/shared  ntfs-3g      defaults                             0  0  
# Entry for /dev/sda1 :
UUID=04B05B70B05B6768                      /media/cdrive      ntfs-3g      defaults,locale=en_US.UTF-8,fmask=0111,dmask=0000         0  0  

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

---

### Post by John Bean on 2010-06-12
I agree. Use defaults for the ntfs mount unless you have a convincing reason to do otherwise, in your example:

```
/dev/sdb1 /home/fileshare2 ntfs-3g defaults 0 0 	
```

---

### Post by imjakes on 2010-06-12
Yet again you solved my problem, thanks a lot :)

---

