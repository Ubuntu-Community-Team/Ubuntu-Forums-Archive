---
title: "Ubuntu Kernel 3.5.0.999 detects my DVD-ROM Drive incorrectly!"
date: 2012-06-19
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by kevpan815 on 2012-06-19
For some reason or another, Ubuntu Kernel 3.5.0.999 detects my DVD-ROM Drive as a CD-ROM Drive by mistake! This issue does not occur in Ubuntu Kernel 3.4.0.5.

---

### Post by cariboo on 2012-06-19
Both /dev/cdrom and /dev/dvd are symlinks to /dev/sr0:

```
cariboo@alexis:/dev$ ls -l cdrom
lrwxrwxrwx 1 root root 3 Jun 19 07:10 cdrom -> sr0
cariboo@alexis:/dev$ ls -l dvd
lrwxrwxrwx 1 root root 3 Jun 19 07:10 dvd -> sr0
```

Are you saying that the drive doesn't read DVD's? Or is ist just the mount point that says it's a cdrom drive?

---

### Post by kevpan815 on 2012-06-19
Never mind, I was confused why the Home Window said CD Drive Instead of DVD Drive. The Main Screen does correctly display both as DVD's.

---

