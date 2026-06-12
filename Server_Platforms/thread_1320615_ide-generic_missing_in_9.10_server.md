---
title: "ide-generic missing in 9.10 server"
date: 2009-11-09
forum: Server Platforms
---

### Post by ifoo on 2009-11-09
I tried to install ubuntu 9.10 amd64 server edition on my intel ss4200 nas. The disk for the operating system is an IDE DOM module.
The problem is that the ubuntu installer (in text mode -> NAS has no graphics card) doesn't find the IDE drive. But it detects all the other drives (which are in a bios-raid 1) as sata drives. Now i wanted to load the ide-generic module for IDE support, but it was not found on the installer cd (nor was ata_piix). When i boot a different distribution (like gentoo) the ide-generic module is included and the disk is correctly mounted. Is this a bug or was the module removed ?

---

### Post by Lil' Kim on 2010-03-18
I have run into the exact same problem on the Karmic server on the Intel SS4200 w/ 2GB DOM. Did you ever discover a workaround?

---

### Post by ifoo on 2010-03-19
no, i ended up installing debian.

---

