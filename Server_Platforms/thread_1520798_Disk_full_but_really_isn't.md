---
title: "Disk full but really isn't?"
date: 2010-06-30
forum: Server Platforms
---

### Post by SamAdam on 2010-06-30
So i just installed ubuntu server 8.04.  Got everything set up and started putting my files on it.  6 Hours of copying later I get a message saying that my Disk is full.  This is a 1.5TB HD and it stopped copying at 269GB.  fdisk shows the drive as 1.5TB, and ls -sh shows that only 269GB have been used.  Yet I cannot add any more files.  The other weird thing is that df doesn't show the hard drive, yet I know it is mounted and accessible. If it makes a difference I have it formatted to ext3.  Any ideas?

---

### Post by windependence on 2010-06-30
What is the output of:

```
fdisk -l
```

and

```
du -h
```

-Tim

---

### Post by benderisgreat on 2010-06-30
c

---

