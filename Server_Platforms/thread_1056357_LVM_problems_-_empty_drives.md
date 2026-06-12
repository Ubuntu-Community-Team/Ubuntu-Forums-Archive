---
title: "LVM problems - empty drives???"
date: 2009-01-31
forum: Server Platforms
---

### Post by bluepowder7 on 2009-01-31
on my file server (running 7.10), i had 3 hard drives with LVM putting them together to make one large drive.  now, when i do "ls", i get no files.  i'm not sure if the lvm package got hosed during some updates, or if i need to rebuild something, but i've got over 1TB of files that i need to get access to (spanning 3 hard drives, a 750G, a 250G, and a 120G)

what's the SAFE way to reassemble the lvm stuff and get my files to show up again?

---

### Post by RealPSL on 2009-02-01
Concatenations like you have do not provide data redundancy so if one drive goes bad you could potentially loose all the data. The first think to try is unmounting the file system and running a file system check. You do this with the following commands from the terminal:
```
sudo umount /file_system_name
```
Make sure that this command is successful before continuing to the next. If you get an error message that the file system is busy make sure you are not in that directory.
```
sudo fsck /file_system_name
```
Bring the file system back online with 
```
mount /file_system_name
```

---

