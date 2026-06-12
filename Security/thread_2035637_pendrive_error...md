---
title: "pendrive error.."
date: 2012-07-31
forum: Security
---

### Post by Priyank Kaushal on 2012-07-31
hi,

while downloading any file directly to my pendrive...its showing the error mentioned below ....please help me ..how to resolve this error...in pendrive,files show some lock sign...what is it ..it doesnot copying any file neither its deleting from pendrive....

"/media/PENDRIVE/lesson6.html could not be saved, because the disk, folder, or file is write-protected."

need urgent help..
thank u..

---

### Post by 2F4U on 2012-07-31
What is the filesystem on the drive? Is it a filesystem that carries over privileges, such as ext?

---

### Post by Priyank Kaushal on 2012-07-31
it is msdos............

---

### Post by Ms. Daisy on 2012-07-31
Do you mean the pen drive is formatted with NTFS?

---

### Post by Priyank Kaushal on 2012-07-31
it is FAT32 actually....

---

### Post by cariboo on 2012-07-31
If you setup your pen drive without persistence, it thinks it is a cd-rom, which is read only.

Using the System Startup Disk Creator allows you to create a pen drive with an area that is read/writable.

---

