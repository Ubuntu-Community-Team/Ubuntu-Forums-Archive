---
title: "Size of a mounted partition is smaller than the partition itself"
date: 2010-03-23
forum: Server Platforms
---

### Post by SmartP on 2010-03-23
I have Ubuntu server 8.04.
I have 4 hard drives of 149Go each. Size of a mounted partition is smaller thant the partition itself :
 - first drive is the system
** - I mounted the 2nd drive (ext3) on a folder, but the Size is 941.89 MB instead of 149Go**
 - same for drive 3 monted on another folder, but the Size is 941.89 MB instead of 149Go

Do you have any idea how to solve that ?

---

### Post by Bachstelze on 2010-03-23
Please paste the output of

```
sudo fdisk -l
```

and

```
df -h
```

---

### Post by SmartP on 2010-03-23
Ok problem solved :-)
The **issue is coming from WEBmin** as I did the formating wiht it
I finally did it directly with command line : mkfs and then all worked nice ;-)

Sorry for bothering

---

