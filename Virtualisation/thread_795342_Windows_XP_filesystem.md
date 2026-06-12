---
title: "Windows XP filesystem?"
date: 2008-05-15
forum: Virtualisation
---

### Post by vishzilla on 2008-05-15
I am planning to virtualize Windows XP on my system in Virtualbox. Which filesystem is better to choose between NTFS and Fat32? I don't plan to use XP much (only for a share trading website which supports IE only) as IE on Hardy is unusable with the regression in Wine

---

### Post by gsiliceo on 2008-05-15
For the virtual hard disk? NTFS

---

### Post by jen1963 on 2008-05-15
NTFS would be a much better choice. FAT is far more prone to file system fragmentation which can cause system performance degradation,system crashes & data corruption.
NTFS also fragments which causes performance degradation but hasn't had the crash issues or data degradation like FAT\FAT32 has traditionally had.

The EXT 3 in Linux ain't the greatest either....I wish Ubuntu had support for Sun's ZFS. Hopefully ZFS will be of the goodies that Linux can get from Solaris...

---

### Post by vishzilla on 2008-05-15
Then NTFS it is :)
Thanks guys

---

