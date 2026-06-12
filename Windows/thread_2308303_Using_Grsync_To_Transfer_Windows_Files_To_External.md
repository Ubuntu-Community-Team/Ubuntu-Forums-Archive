---
title: "Using Grsync To Transfer Windows Files To External HDD"
date: 2016-01-01
forum: Windows
---

### Post by quaesitor2 on 2016-01-01
I am wondering if there are any special precautions to take in regards  to backing up 309 GBs of data to a seagate external hdd from a windows 7  os western digital hard drive held in a vantec enclosure. I am using  lubuntu live to facilitate the backup using grsync. The wd hard drive  suffered bsod after I interrupted an update to windows 7. I 've not yet  been able to repair said  hard drive. I want to backup data before I  attempt to repair the disk using hirens boot cd.

---

### Post by oklokl on 2016-01-03
The recommended command
```
mount
```
```
mount ntfs-3g /dev/sdX
```
```
unmount -l /dev/sdX
```
The mounting method.[But (ntfs) is not fully supported in Ubuntu ext4.
 Therefore the error occurs frequently.]
:)
The recommended automatic mounting.(It mounted inside.)
External hard drive is not recommended. (backup date)
ntfs usb hdd(Ubuntu has often failed to bug delicate.)

After the files are synchronized.
 ```
sync
```
 Please turn off completely through.
USB hdd(mouse Click Eject)



However..
 I saw a program with which you have presented.
 [COLOR=#ff0000]There are many bugs.[/COLOR]
 The synchronization is solved.


This partition is not separate.
It leads to partition damage.
 That is why..
 Blue Screen errors occur.

 ntfs is not recommended.
 ext4 and recommendations synchronization.

 It is recommended to copy the file.

Please use only one operating system(Recommended) 
:)

---

