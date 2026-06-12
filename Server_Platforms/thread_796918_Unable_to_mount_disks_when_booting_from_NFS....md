---
title: "Unable to mount disks when booting from NFS..."
date: 2008-05-16
forum: Server Platforms
---

### Post by microchip13 on 2008-05-16
I'm netbooting a computer with 4 hard drives over NFS. The computer boots fine however I cannot mount any of the hard drives.

Here's what it looks like:
#sudo mount /dev/sda1 /mnt/1
mount: /dev/sda1 already mounted or /mnt/1 busy


Naturally, none of this shows up in /proc/mounts or /etc/mtab.

Any suggestions? TiA!

---

