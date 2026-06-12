---
title: "Problems with VirtualBox and external hard drive"
date: 2010-10-02
forum: Virtualisation
---

### Post by gabriel.pelmus on 2010-10-02
I have an Asus x51H notebook with 2GB RAM , Intel Pentium dual core 1,86GHz CPU , KUbuntu 10.04 and a 500GB external hard drive . Today I installed Virtual Box 3.2.8 and I'm trying to create a Windows XP image . I want to save the virtual hard disk on my external hard disk formatted as fat32 . I have 490 GB free space on it , but when I'm creating the virtual hard disk , Virtual Box tells me that there is only 4 GB free space . I installed Windows XP but Virtual Box paused my session due to insufficient space for the virtual hard disk . I searched over the Internet but I found no solution . Does anyone know how can I fix this issue? Thanks!

---

### Post by gabriel.pelmus on 2010-10-02
I found out that I have do modify the filesystem because FAT32 has a 4GB file size limit . SOLVED

---

