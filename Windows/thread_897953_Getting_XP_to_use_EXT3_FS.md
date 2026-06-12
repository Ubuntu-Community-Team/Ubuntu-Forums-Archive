---
title: "Getting XP to use EXT3 FS"
date: 2008-08-22
forum: Windows
---

### Post by MechWarrior001 on 2008-08-22
Does anyone know how to get Windows XP (SP-2-3) to use EXT3? Would it be worth it?

---

### Post by omns on 2008-08-22
[http://www.diskinternals.com/linux-reader/](http://www.diskinternals.com/linux-reader/)

---

### Post by mrsteveman1 on 2008-08-22
what you want is ext2ifs or ext2fsd (think thats the right names). You can't boot XP from an ext3 disk because it depends on some NTFS specific behavior now i think, plus the NT bootloader can't read EXT3.

You can use ext3 disks though from windows just like any other drive.

---

