---
title: "Auto mounting a Window RAID at boot"
date: 2011-06-09
forum: Server Platforms
---

### Post by rchille on 2011-06-09
Hello all!

Thanks to this [post]("http://ubuntuforums.org/showthread.php?t=833653&highlight=dynamic+disk"), I've configured Ubuntu to be able to read my Winodws RAID when I run the following commands:

```

sudo mdadm --build /dev/md0 --chunk=64 --level=0 --raid-devices=2 /dev/sda1 /dev/sdc1
sudo mount -t ntfs-3g /dev/md0 /media/raid0

```

I'd really like to take it one step further and have this setup at boot. I could script up a solution, but it seems that fstab and mdadm.conf really should be the way to go.

There are several examples I've found of setting this up for native Lunix RAIDs, I've just not seen anything for setup with a Windows RAID. The complication, I THINK, is that all the examples I've seen use "mdadm --detail" with I think pulls the superblock data, which I don't have:

```
rob@kitt:~$ sudo mdadm --detail --scan
ARRAY /dev/md0 metadata=

```

That's all I get :(

I tried to create the entires in fstab and mdadm.conf, but no luck (maybe because I can't find a way to specify the chunk size???)

```
rob@kitt:~$ cat /etc/fstab 
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=2820b11d-fae8-44fc-8483-984d9a8a3949 /               ext4    errors=remount-ro 0       1
/dev/md0	/media/raid0	ntfs-3g		rw,user,auto,exec	0	0

```

```

rob@kitt:~$ cat /etc/mdadm/mdadm.conf 
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays

# This file was auto-generated on Sat, 04 Jun 2011 08:37:57 -0400
# by mkconf $Id$

DEVICE /dev/sda1 /dev/sdc1
ARRAY /dev/md0 level=0 devices=/dev/sda1,/dev/sdc1

```

I did try /usr/share/mdadm/mkconf again, but it seems to be missing info:
```
rob@kitt:/usr/share/mdadm$ ./mkconf 
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions
/dev/sda1 /dev/sdc1

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays

```

Thanks for any suggestions!=

---

