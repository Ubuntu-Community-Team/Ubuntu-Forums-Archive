---
title: "Kernel 5.11"
date: 2020-12-28
forum: Ubuntu Development Version
---

### Post by zika on 2020-12-28
[https://www.phoronix.com/scan.php?page=news_item&px=Linux-5.11-rc1](https://www.phoronix.com/scan.php?page=news_item&px=Linux-5.11-rc1)
[https://www.linuxtoday.com/developer/linux-5.11-rc1.html](https://www.linuxtoday.com/developer/linux-5.11-rc1.html)

---

### Post by Doug S on 2020-12-28
I see the [mainline PPA]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.11-rc1/") builds are broken again:

```
  DEPMOD  5.11.0-051100rc1-generic
Warning: 'make modules_install' requires depmod. Please install it.
This is probably in the kmod package.
```

I used the config file from 5.10, and accepted defaults:

```
doug@s18:~$ uname -a
Linux s18 5.11.0-rc1-stock #845 SMP PREEMPT Mon Dec 28 07:17:42 PST 2020 x86_64 x86_64 x86_64 GNU/Linux
```
that it is running is as far as I have progressed.

---

### Post by xyz-t on 2020-12-28
It breaks too often now, not the place to be on Sunday anymore. Nothing wrong so far. Splash screen shows a message about libbtf without incidence.

```
pacman -Q | grep linux
archlinux-appstream-data 20201223-1
archlinux-keyring 20201210-1
lib32-util-linux 2.36.1-1
linux-api-headers 5.8-1
linux-firmware 20201218.r1803.646f159-1
linux510 5.10.3-1
**linux511 5.11.rc1.d1227.g5c8fe58-1**
util-linux 2.36.1-4
util-linux-libs 2.36.1-4
```

---

### Post by zika on 2021-01-02
```
:~$ uname -r
5.11.0-051100rc1daily20210102-generic
```
It seems it was worth waiting for...

---

### Post by xyz-t on 2021-02-03
Perfect cycle so far, abnormal splash screen for rc-5, but corrected 2-3 days after. The kernel schedule is now back to normal, 2 hours after Linus.

```
5.11.0-051100rc6daily20210203-generic #202102030207 SMP Wed Feb 3 02:10:28 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by Doug S on 2021-02-14
[5.11 has been released]("https://www.theregister.com/2021/02/14/linux_kernel_5_11_released/"), although not yet on [kernel.or]("https://www.kernel.org/")g or [the Ubuntu PPA]("https://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D").

There was a fix for AMD using schedutil governor that barley made it in, but has [ongoing complaints]("https://bugzilla.kernel.org/show_bug.cgi?id=211305").

I had thought there was going to be an -rc8, and was surprised.

```
f40ddce88593 (HEAD -> master, tag: v5.11, origin/master, origin/HEAD) Linux 5.11
```

```
$ uname -a
Linux s18 5.11.0-stock #851 SMP PREEMPT Sun Feb 14 15:03:43 PST 2021 x86_64 x86_64 x86_64 GNU/Linux
```

EDIT: now available via [Ubuntu PPA]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.11/").
Interesting side note: This is the first time I have ever seen the Ubuntu PPA post before kernel.org

---

### Post by corradoventu on 2021-02-27
Both mainline kernels 5.11.1 and 5.11.2 build failed

---

### Post by Doug S on 2021-02-27
> **corradoventu said:**
> Both mainline kernels 5.11.1 and 5.11.2 build failedGee, build fails have been happening all too often this last year.

the log says:
```
make[3]: *** No rule to make target 'debian/canonical-certs.pem', needed by 'certs/x509_certificate_list'.  Stop.
make[3]: *** Waiting for unfinished jobs....
```
but I do observe the daily built O.K. will watch for 5.12-rc1 tomorrow.

EDIT: [Link to IRC]("https://irclogs.ubuntu.com/2021/02/26/%23ubuntu-kernel.html") mentioned by jermey31 in the next post.

---

### Post by jeremy31 on 2021-02-27
I think this issue is being worked on as the kernel team was alerted on #ubuntu-kernel today

---

### Post by zika on 2021-02-28
For the second day in a row "daily" (the only one available) is not booting here. It installs OK, and stalls on graphics enabling... Will follow. Other non-mainline kernels boot perfectly.

---

### Post by Doug S on 2021-02-28
> **zika said:**
> For the second day in a row "daily" (the only one available) is not booting here. It installs OK, and stalls on graphics enabling... Will follow. Other non-mainline kernels boot perfectly.Hi zika,

the mainline as of now:

```
06d5d309a3f1 (HEAD -> master, origin/master, origin/HEAD) Merge tag 'kbuild-fixes-v5.12' of git://git.kernel.org/pub/scm/linux/kernel/git/masahiroy/linux-kbuild
cd278456d4ca Merge tag 'csky-for-linus-5.12-rc1' of git://github.com/c-sky/csky-linux
7d19ea5e9973 Merge tag 'riscv-for-linus-5.12-mw1' of git://git.kernel.org/pub/scm/linux/kernel/git/riscv/linux
```

boots fine on my test computer. However, it is a CLI only server, no desktop GUI. so, proves nothing really.

---

### Post by zika on 2021-03-01
Resolved on my side, also... 
```
:~$ uname -r5.11.0-051100daily20210228-generic
```
DRMTip and 5.12 still in the oven...

---

### Post by tome74 on 2021-03-05
First time posting in Ubuntu Forum, so forgive me if this is the wrong place to post this.

Ubuntu 20.10, with Linux kernel 5.11 (tried 5.11-rc2, 5.11, 5.11.1, 5.11.3). System boots, but display is corrupted. See attached image.

System specs: Ryzen Pro 4750G APU Renoir, 64GB RAM, Integrated Graphics.

Is this is a known issue ? 

Problem doesn't occur with kernel 5.10.20.

Thanks.

-Hock

---

### Post by Doug S on 2021-03-05
> **tome74 said:**
> First time posting in Ubuntu Forum, so forgive me if this is the wrong place to post this.
Hi, and welcome.

> **tome74 said:**
> Ubuntu 20.10, with Linux kernel 5.11 (tried 5.11-rc2, 5.11, 5.11.1, 5.11.3). System boots, but display is corrupted. See attached image.
System specs: Ryzen Pro 4750G APU Renoir, 64GB RAM, Integrated Graphics.
Is this is a known issue ? 
Problem doesn't occur with kernel 5.10.20.That is a very interesting image. I have no idea if it is a known issue or not (I am a server person, with little to no knowledge of display issues.)
The first thing for you to try is kernel 5.12-rc1. This will tell you if the problem has already been fixed. On Monday, try 5.12-rc2.

Also try mainline kernels 5.10 and 5.11-rc1. The purpose being to narrow down the faulty commit as much as possible. the next step would be to do a kernel bisection to isolate the exact commit. It'll take around 18 kernel compiles. Or, just wait long enough for someone else to figure it out.

EDIT: kernels such as 5.10.20 and 5.11.1 and such are deviations from the main mainline tree. My input towards isolating the issue is via the mainline tree only.

EDIT 2: Oh, I see that this was a major change for the 5.11 cycle. [Link]("https://lists.freedesktop.org/archives/dri-devel/2020-November/285936.html").

EDIT 3: See if you can find your issue listed [here]("https://gitlab.freedesktop.org/drm/amd/-/issues").

---

### Post by tome74 on 2021-03-05
Thanks for your reply. I will try out your suggestions for testing & isolating the issue.

---

### Post by tome74 on 2021-03-06
Just tried with kernel 5.12-rc2. Problem with corrupted screen still occurs.

---

### Post by Doug S on 2021-03-06
> **tome74 said:**
> Just tried with kernel 5.12-rc2. Problem with corrupted screen still occurs.ya, this is a lot of new code. Did you look at that list of issues link I gave. The first one listed looked like a contender for your issue to me. (i'll come back and edit in a direct link later).

EDIT: [this new one]("https://gitlab.freedesktop.org/drm/amd/-/issues/1514"), or is that you that entered it? But [this]("https://gitlab.freedesktop.org/drm/amd/-/issues/1513") is the one I thought of yesterday.

---

### Post by tome74 on 2021-03-06
Yes, I entered the new one. Looked thru all the others, but none that has the kind of whole screen corruption that I'm seeing.

---

### Post by corradoventu on 2021-03-16
Kernel 5.11 status in launchpad: [https://bugs.launchpad.net/kernel-sru-workflow/+bug/1917335](https://bugs.launchpad.net/kernel-sru-workflow/+bug/1917335)

---

### Post by Doug S on 2021-03-16
> **tome74 said:**
> Yes, I entered the new one. Looked thru all the others, but none that has the kind of whole screen corruption that I'm seeing.I see in [that bug report]("https://gitlab.freedesktop.org/drm/amd/-/issues/1514") that you bisected the kernel, which led to a patch set to try which you, and someone else, verified as fixing the issue. A huge time commitment, thank you.

---

### Post by corradoventu on 2021-03-19
corrado@corrado-n3-hh-0228:~$ uname -a
Linux corrado-n3-hh-0228 5.11.0-11-generic #12-Ubuntu SMP Mon Mar 1 19:26:56 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux
corrado@corrado-n3-hh-0228:~$

---

### Post by IanW on 2021-03-19
> **corradoventu said:**
> corrado@corrado-n3-hh-0228:~$ uname -a
Linux corrado-n3-hh-0228 5.11.0-11-generic #12-Ubuntu SMP Mon Mar 1 19:26:56 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux
corrado@corrado-n3-hh-0228:~$

I also got 5.11 in my normal daily apt update.

---

