---
title: "[SOLVED] How to fix invalid mount point name???"
date: 2008-10-26
forum: Security
---

### Post by joemilx on 2008-10-26
I inadvertently included a slash before the name while defining a mount point and now I cannot mount the partition.  How can I correct the problem?

AMD64 8.04.1

---

### Post by cdtech on 2008-10-26
How did you define the mount point?

You could edit your fstab file to include the partition for the correct mount point.

---

### Post by joemilx on 2008-10-26
> **cdtech said:**
> How did you define the mount point?

You could edit your fstab file to include the partition for the correct mount point.

The partition was my home partition from my previous 32 bit install.  After I installed the 64 bit system, I changed the mount point for the old home partition under Properties after mounting the partition.  Now I'm sure that wasn't the right way to do it, but I'm stuck with a partition I cannot mount.  I don't know how to get the UUID of a partition I can't mount to edit the fstab file.  Help, please!

---

### Post by saltire89 on 2008-10-26
hi there, if you can try mounting the partition manually to the correct place ie by using the mount command: it will show up on nautilus - you can then click properties and change the mount point in nautilus after that.

Hope that helps 
:)

---

### Post by joemilx on 2008-10-26
> **saltire89 said:**
> hi there, if you can try mounting the partition manually to the correct place ie by using the mount command: it will show up on nautilus - you can then click properties and change the mount point in nautilus after that.

Hope that helps 
:)

Tried that. Get error not found in fstab or mtab.

---

### Post by cariboo on 2008-10-26
Can you paste your /etc/fstab file in your next post?

This really isn't a security question, but it will probably get solved here.

Jim

---

### Post by joemilx on 2008-10-26
> **cariboo907 said:**
> Can you paste your /etc/fstab file in your next post?

This really isn't a security question, but it will probably get solved here.

Jim

Here's the fstab file.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=15c38daa-f9b8-4761-a7bb-3f589425ee55 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=67f16e62-d565-4cac-b0ed-0a83ee169911 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

/dev/sda1 is a Windows XP partition.

---

### Post by joemilx on 2008-10-26
Thought I needed UUID for fstab, but /dev/sda4 worked fine.  Old home partition is alive and well.

---

