---
title: "Kudu Pro on 18.04 LTS,upgrade loses wifi"
date: 2020-07-21
forum: System76 Support
---

### Post by Skaperen on 2020-07-21
i am running Xubuntu 18.04 LTS on System76 Kudu Pro.  an upgrade changed initrd.img to 5.4.0-42-generic which fails to drive wifi (but initrd.img-5.3.0-62-generic from 5 days ago worked OK).  the kernel file is dated in June.  only the initrd is dated in July so i looks like something changed in initrd.  on the 5.4.0-42-generic the system comes up without interface wlp4s0.  i had to boot up an older system because wifi is my only internet (apparently both 2.4 and 5 GHz).

i would like to know if i need to install a specific driver (and how, where, to make grub do what it needs to do) to get things working, again.  i am not accustomed to configuring grub or making its images or configs so i will need full details on those steps, as needed.
```

-rw------- 1 root  4490843 2020-06-24 08:07:22.000000000 -0400 /boot/System.map-5.3.0-62-generic
-rw-r--r-- 1 root   235827 2020-06-24 08:07:22.000000000 -0400 /boot/config-5.3.0-62-generic
-rw------- 1 root  9158912 2020-06-24 08:20:32.000000000 -0400 /boot/vmlinuz-5.3.0-62-generic
-rw------- 1 root  4573787 2020-07-10 02:54:33.000000000 -0400 /boot/System.map-5.4.0-42-generic
-rw-r--r-- 1 root   237786 2020-07-10 02:54:33.000000000 -0400 /boot/config-5.4.0-42-generic
-rw------- 1 root  9371904 2020-07-10 02:56:10.000000000 -0400 /boot/vmlinuz-5.4.0-42-generic
-rw-r--r-- 1 root 69003432 2020-07-15 23:06:46.334746128 -0400 /boot/initrd.img-5.3.0-62-generic
-rw-r--r-- 1 root 68720316 2020-07-21 18:06:30.808842335 -0400 /boot/initrd.img-5.4.0-42-generic

```

---

