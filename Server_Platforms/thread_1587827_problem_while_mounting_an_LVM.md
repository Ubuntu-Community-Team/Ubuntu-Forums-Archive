---
title: "problem while mounting an LVM"
date: 2010-10-04
forum: Server Platforms
---

### Post by tapas_mishra on 2010-10-04
I am trying to mount an LVM
mount /dev/nintendo/backupos /mnt/backup/
mount: /dev/mapper/nintendo-backupos already mounted or /mnt/backup/ busy

where as if I do umount /mnt/backup 
then 
umount: /mnt/backup/: not mounted

So what might be wrong?

---

### Post by windependence on 2010-10-04
You are in /mnt/backup. You cannot mount it while you  are in the directory. cd to root (cd /) or some other directory and try again.
 
-Tim

---

