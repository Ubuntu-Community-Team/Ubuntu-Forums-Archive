---
title: "Automount issue - Ext3-formatted disk in read/ony"
date: 2008-10-21
forum: Security
---

### Post by Gianchi83 on 2008-10-21
Hello everybody... I have an apparently simple question:

I'm producing a LiveCD forensic distribution, and I have modified the /var/lib/gconf/defaults/%gconf-tree.xml to make Ubuntu automount the external storage (mainly fat and ntfs) with ro, noexec and noatime option. 


But, what about ext3 formatted external storage? I mean not internal partition, but external discs formatted ext3 (or ext2).
How I can edit Ubuntu configuration to not mount ext3 partition in read/write?


Please help me...

---

### Post by cariboo on 2008-10-21
You would an Ext3 disk/partiton as read only, the same as anything else by using the **ro** option.

Jim

---

