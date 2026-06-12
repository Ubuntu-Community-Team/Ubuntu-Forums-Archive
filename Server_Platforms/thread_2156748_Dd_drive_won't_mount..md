---
title: "Dd drive won't mount."
date: 2013-06-22
forum: Server Platforms
---

### Post by wlraider70 on 2013-06-22
I have two drives in my machine. They are the same SSD 64gb
They have the same partition setup.

Sdb is the primary sdb1 is boot sdb2 is /
So I dd sdb2 to sda2
However when I try to mount sda2 i get a journal error and a super block error.
It won't mount.

---

### Post by Vitsliputsli on 2013-06-26
Have you changed UUID for sda2 after dd?

---

### Post by wlraider70 on 2013-06-26
No, I'm assuming that the DD made them the same...

Can I change it to anything?

---

### Post by oldfred on 2013-06-26
You cannot have duplicate UUID, so if both drives as still mounted you have to change one or the other. 
But then if you want it to work you have to edit fstab and reinstall grub as they have UUIDs. 

 Change UUID see also man pages:
uuidgen
sudo tune2fs /dev/sdaX -U numbergeneratedbyuuidgen
or:
sudo tune2fs -U random /dev/sdaX
if you recreate a swap partition don't forget to update /etc/initramfs-tools/conf.d/resume with the new uuid

---

