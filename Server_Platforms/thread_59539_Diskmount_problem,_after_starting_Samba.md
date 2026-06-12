---
title: "Diskmount problem, after starting Samba"
date: 2005-08-24
forum: Server Platforms
---

### Post by AntonioT on 2005-08-24
I've installed Samba, but when attempting to share a (mounted) datadisk, something went wrong and I could no longer access the datadisk. 

I have commented out my last changes in smb.conf and restarted Samba, but can not remount the originals.

# mount -a
mount: can't open /etc/mtab for writing: Input/output error

Also a reboot gave an errormessage that the initialization of mtab failed.

Any suggestions, please?
Tony

---

### Post by LordHunter317 on 2005-08-24
Sounds like your root filesystem is being mounted read only or something, which is odd.

What does /proc/mounts say?

---

### Post by AntonioT on 2005-08-24
[QUOTE=LordHunter317]Sounds like your root filesystem is being mounted read only or something, which is odd.

What does /proc/mounts say?[/QUOTE]

from a root terminal:
root@Linuxbox:/ # /proc/mounts
bash: /proc/mounts: Permission denied

Thank you for your support & question. A forced fsck deleted the inode of mtab, and now everything is fine again. Thanks again.

Tony

---

### Post by LordHunter317 on 2005-08-24
/proc/mounts is a text file, you'd have to cat it.

---

