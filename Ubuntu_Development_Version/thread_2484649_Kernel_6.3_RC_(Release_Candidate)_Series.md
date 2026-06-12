---
title: "Kernel 6.3 RC (Release Candidate) Series"
date: 2023-03-05
forum: Ubuntu Development Version
---

### Post by Doug S on 2023-03-05
[Kernel 6.3-RC1 is available]("https://kernel.org/"), although not yet from [the Ubuntu mainline PPA]("https://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D").

There are 125 default kernel configuration changes between 6.2 and 6.3-rc1.

```
doug@s19:~$ uname -a
Linux s19 6.3.0-rc1-stock #1112 SMP PREEMPT_DYNAMIC Sun Mar  5 15:38:45 PST 2023 x86_64 x86_64 x86_64 GNU/Linux
```

EDIT: All the [Ubuntu Mainline PPA]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v6.3-rc1/") Compiles failed (AMD64 log example):

```
check-config: FAIL: (- != y): CONFIG_PAHOLE_HAS_LANG_EXCLUDE policy<{'amd64': 'y', 'arm64': 'y', 'armhf': 'y', 'ppc64el': 'y', 'riscv64': 'y', 's390x': 'y'}>)
```

---

### Post by zika on 2023-03-07
```
uname -r
6.3.0-060300rc1daily20230307-generic
```
Nice and fast. Very promising.

---

### Post by deadflowr on 2023-03-10
Hopefully the build failures will stop: [https://discourse.ubuntu.com/t/whats-up-with-ubuntu-mainline-builds/34438]("https://discourse.ubuntu.com/t/whats-up-with-ubuntu-mainline-builds/34438")

---

### Post by xyz-t on 2023-03-11
An update was made on the 9th for RC-1, using daily ones all week with no issue.
```

6.3.0-060300rc1daily20230312-generic
```

---

### Post by zika on 2023-03-13
```
uname -r
6.3.0-060300rc2daily20230313-generic
```
Working nice.

---

### Post by Doug S on 2023-03-19
Kernel 6.3-rc3 is available.

It has been quite awhile since I have synchronized my own compile with the Ubutnu kernel configuration. There are 88 differences between the defaults since whenever I last used the Ubuntu kernel configuration and todays -rc3, mostly additional modules.

```
doug@s19:~$ uname -a
Linux s19 6.3.0-rc3-stock #1115 SMP PREEMPT_DYNAMIC Sun Mar 19 15:49:40 PDT 2023 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by xyz-t on 2023-03-21
This one (kerneldotorg) boots in a Kernel panic, meaning that one of the patches submitted on the 20 cause this fatal error (cold shutdown). Rc-3 boots normally.

```
6.3.0-rc3-next-20230321-1-next-git-05298-gf3594f0204b7
```

---

### Post by xyz-t on 2023-03-22
> **xyz-t said:**
> This one (kerneldotorg) boots in a Kernel panic, meaning that one of the patches submitted on the 20 cause this fatal error (cold shutdown). Rc-3 boots normally.

```
6.3.0-rc3-next-20230321-1-next-git-05298-gf3594f0204b7
```

Today's Kernel overwrites the bug, but a new one was introduced. No battery available all over, and the icon (gnome instead of kde) on the taskbar has no charging indicator. Only brightness is displayed. Other Kernels are ok.

---

### Post by zika on 2023-03-27
```
$ uname -r
6.3.0-060300rc4daily20230327-generic
```

---

### Post by IanW on 2023-04-03
RC5 is up on mainline.

---

### Post by xyz-t on 2023-04-16
```
ls /lib/modules
6.2.0-20-generic  6.2.0-21-generic  6.3.0-060300rc7-generic
```


Got that unknown label this week:
```
6.3.0-060300rc6drmtip20230414-generic
```

Noise free and Ku 23.04 runs very well.

---

### Post by zika on 2023-04-17
```
 uname -r
6.3.0-060300rc7drmtip20230417-generic
```
```
 uname -r
6.3.0-060300rc7daily20230417-generic
```
```
 uname -r
6.3.0-060300rc7-generic
```
[https://lore.kernel.org/lkml/CAHk-=wjwK59PegTZb9r=EVuCPwbigcbbby5AwEboMBgykhL-KA@mail.gmail.com/](https://lore.kernel.org/lkml/CAHk-=wjwK59PegTZb9r=EVuCPwbigcbbby5AwEboMBgykhL-KA@mail.gmail.com/)

---

