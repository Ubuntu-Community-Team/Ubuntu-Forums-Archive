---
title: "G Parted refuses to format and partition slave HDD"
date: 2014-08-29
forum: Ubuntu Studio
---

### Post by Ramlee on 2014-08-29
Hi everyone,

My Ubuntu Studio desktop has an additional 160Gb HDD which is recognised by G Parted as /dev/sdb; so far so good.  Any attempt however to to format the drive to ext4 or even ntfs results in G Parted shutting down and refusing to complete the format.  Other times G Parted will not even open without a reboot.  Has anyone else experienced this kind of problem with G Parted?  Can anyone suggest a course of action?  All suggestions welcome.

Regards Ramlee.

---

### Post by jejeman on 2014-08-30
Give
```
sudo parted -l
```

---

### Post by uRock on 2014-09-03
For questions like this you may be better off asking in the General Help section of the forums.

---

