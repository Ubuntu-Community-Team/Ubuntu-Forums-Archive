---
title: "Problem with 4.16 kernel install"
date: 2018-02-28
forum: Ubuntu Development Version
---

### Post by DougieFresh4U on 2018-02-28
Trying to install the 4.16 kernel.
Getting this from terminal:
```
dpkg: error: unable to read filedescriptor flags for <package status and progress file descriptor>: Bad file descriptor
```

---

### Post by zika on 2018-02-28
It would be easier to answer if we knew the origin of .deb file and a way You've tried to use it.```
:~$ uname -a
Linux *...* 4.16.0-994-generic #201802272100 SMP Wed Feb 28 02:02:08 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by Doug S on 2018-02-28
> **zika said:**
> It would be easier to answer if we knew the origin of .deb file and a way You've tried to use it.
+1.

I didn't have a problem installing kernel 4.16-rc1 rc2 or rc3 from the [Ubuntu mainline PPA]("http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D"), or compiled myself.

---

### Post by DougieFresh4U on 2018-02-28
> dougiefresh@Deeswin10:~$ uname -a
Linux Deeswin10 4.16.0-041600rc1-generic #201802120030 SMP Mon Feb 12 00:31:33 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

> **Doug S said:**
> +1.

I didn't have a problem installing kernel 4.16-rc1 rc2 or rc3 from the [Ubuntu mainline PPA]("http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D"), or compiled myself.

I used the link provided and have always installed using gdebi package installer.
I have 4.16rc1 installed(using) but rc2 & rc3 giving error.

---

### Post by zika on 2018-03-01
Did You try installing via command line (dpkg) and if You did give us pertinent text from terminal...
This looks to me as GDebi's trouble, not dpkg... If so, You could always use terminal instead of GDebi...

---

