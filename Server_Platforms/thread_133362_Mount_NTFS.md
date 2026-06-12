---
title: "Mount NTFS"
date: 2006-02-20
forum: Server Platforms
---

### Post by soon82 on 2006-02-20
I had install the samba server.. and i would like to mount the ntfs partition and share for other user... but i cant get it done.....

my /etc/fstab configuration script

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       /Public         vfat    defaults        0       0
/dev/hda1       /boot           ext3    defaults        0       2
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdb1       /media/windows  ntfs    iocharset=utf8,umask=0000 0       0
/dev/hdb5       /media/windows2  ntfs    iocharset=utf8,umask=0000 0       0

So anyone can help me....

---

### Post by Sutekh on 2006-02-20
[QUOTE=soon82]
/dev/hdb1       /media/windows  ntfs    iocharset=utf8,umask=0000 0       0
/dev/hdb5       /media/windows2  ntfs    iocharset=utf8,umask=0000 0       0

So anyone can help me....[/QUOTE]
Try
```
/dev/hdb1       /media/windows   ntfs    **nls**=utf8,umask=0**222** 0       0
/dev/hdb5       /media/windows2  ntfs    **nls**=utf8,umask=0**222** 0       0
```
 - **nls** is the new name for **iocharset**, still use that for FAT though.

 - You don't want a umask of 000  - full access - because Linux is not up to writing to NTFS.

 - A umask=0222 allows read and execute access not write.

---

### Post by pgroover on 2006-02-20
Put the following in fstab:
/dev/hdb1 /media/windows ntfs nls=utf8,umask=0222 0 0
/dev/hdb5 /media/windows ntfs nls=utf8,umask=0222 0 0

That should take care of it.

---

### Post by soon82 on 2006-02-20
i had try to put the 

/dev/hdb1 /media/windows ntfs nls=utf8,umask=0222 0 0
/dev/hdb5 /media/windows ntfs nls=utf8,umask=0222 0 0


but i only can read the data but i cannot change it.. in the ntfs partition..

have other solution that can modify the data in the ntfs partition...

---

### Post by maulattu on 2006-02-20
[QUOTE=soon82]have other solution that can modify the data in the ntfs partition...[/QUOTE]

you must have the write support compiled as a module in your kernel (the default one shipped with (k)ubuntu does), but there're some limitations (like the file must exist, it cannot be too much defragmented... and so on...)

---

