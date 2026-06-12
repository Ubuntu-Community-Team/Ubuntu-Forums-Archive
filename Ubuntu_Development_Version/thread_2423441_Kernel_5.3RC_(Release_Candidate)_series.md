---
title: "Kernel 5.3RC (Release Candidate) series"
date: 2019-07-23
forum: Ubuntu Development Version
---

### Post by Doug S on 2019-07-23
Kernel 5.3-rc1 is available from the [Ubuntu mainline PPA]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.3-rc1/") or [kernel.org]("https://www.kernel.org/").

I am completing some tests on 5.2 before trying 5.3-rc1.

We have a running thread during each mainline kernel release cycle.

Previous cycle threads:
[5.2]("https://ubuntuforums.org/showthread.php?t=2419363")
[5.1]("https://ubuntuforums.org/showthread.php?t=2414938")
[5.0]("https://ubuntuforums.org/showthread.php?t=2409811")
[4.20]("https://ubuntuforums.org/showthread.php?t=2405365")
4.19 ?
[4.18]("https://ubuntuforums.org/showthread.php?t=2394500")
[4.17]("https://ubuntuforums.org/showthread.php?t=2389561")
[4.16]("https://ubuntuforums.org/showthread.php?t=2384781")
[4.15]("https://ubuntuforums.org/showthread.php?t=2378956")
[4.14]("https://ubuntuforums.org/showthread.php?t=2371638")

---

### Post by Doug S on 2019-09-02
This has been a quiet cycle.

Has anyone tried [5.3-rc7]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.3-rc7/") yet?
I am having difficulty downloading linux-headers-5.3.0-050300rc7_5.3.0-050300rc7.201909021831_all.deb from the Ubuntu PPA, and am wondering if the issue is on my side of things or the file itself is there, but empty.

```
doug@s15:~/test_kernels$ ls -l linux-headers-5.3.0-050300rc*
-rw-rwxr--+ 1 doug doug 10914276 Aug  4 23:32 linux-headers-5.3.0-050300rc3_5.3.0-050300rc3.201908042232_all.deb
-rw-rwxr--+ 1 doug doug  1175776 Aug  4 23:32 linux-headers-5.3.0-050300rc3-lowlatency_5.3.0-050300rc3.201908042232_amd64.deb
-rw-rwxr--+ 1 doug doug 10911284 Sep  2 14:39 linux-headers-5.3.0-050300rc6_5.3.0-050300rc6.201908252033_all.deb
[COLOR="#FF0000"]-rw-r--r--  1 doug doug        0 Sep  2 14:04 linux-headers-5.3.0-050300rc7_5.3.0-050300rc7.201909021831_all.deb[/COLOR]
-rw-rwxr--+ 1 doug doug  1178016 Sep  2 13:57 linux-headers-5.3.0-050300rc7-lowlatency_5.3.0-050300rc7.201909021831_amd64.deb

```
EDIT: I downloaded the [-rc6 ]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.3-rc6/")"all" headers file, just to check that the file issue didn't occur in a previous week, since I never downloaded -rc4, -5, or -6.

---

### Post by IanW on 2019-09-03
I see that file showing a size of 10M as of 18.33 on Sept 2nd.
Guess you were a little early for it?

[https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.3-rc7/linux-headers-5.3.0-050300rc7_5.3.0-050300rc7.201909021831_all.deb](https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.3-rc7/linux-headers-5.3.0-050300rc7_5.3.0-050300rc7.201909021831_all.deb)

---

### Post by Doug S on 2019-09-03
> **IanW said:**
> I see that file showing a size of 10M as of 18.33 on Sept 2nd.
Guess you were a little early for it?

[https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.3-rc7/linux-headers-5.3.0-050300rc7_5.3.0-050300rc7.201909021831_all.deb](https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.3-rc7/linux-headers-5.3.0-050300rc7_5.3.0-050300rc7.201909021831_all.deb)I don't know. When I closed firefox, later in the day, it showed 4 hung download attempts, that I hadn't noticed prior. Anyway, now I got the file fine. Thanks.

---

### Post by Doug S on 2019-09-03
between kernel 5.3-rc3 and 5.3-rc7 (I missed -rc4, -rc5, and -rc6) there were just a small number of kernel configuration changes for the [Ubuntu mainline PPA kernels]("https://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D"):

```
doug@s15:~/temp-k-git/linux$ scripts/diffconfig .config-5.3.0-050300rc3-lowlatency .config-5.3.0-050300rc7-lowlatency
-IXP4XX_NPE m
-IXP4XX_QMGR m
-REGMAP_SOUNDWIRE m
-SOUNDWIRE_BUS m
 GCC_VERSION 90100 -> 90201
[COLOR="#FF0000"] KERNEL_GZIP y -> n
 KERNEL_LZ4 n -> y[/COLOR]
 TEST_BLACKHOLE_DEV n -> m
 VIDEO_VIMC n -> m

```My main kernel testing and compiling computer is still an Ubuntu Server 16.04.5 LTS, for which the lz4 package is not available (I don't think it is available for 18.04 LTS either). So, to be able to compile the kernel I had to do this:

```
doug@s15:~/temp-k-git/linux$ cp .config-5.3.0-050300rc7-lowlatency .config
doug@s15:~/temp-k-git/linux$ scripts/config --disable DEBUG_INFO  [COLOR="#FF0000"]<<< I always do this to reduce compile time and kernel size.[/COLOR]
doug@s15:~/temp-k-git/linux$ scripts/config --disable KERNEL_LZ4
doug@s15:~/temp-k-git/linux$ scripts/config --enable KERNEL_GZIP

```

---

### Post by Doug S on 2019-09-09
[Kernel 5.3-rc8]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.3-rc8/") ([unusual for an -rc8]("https://marc.info/?l=linux-kernel&m=156797640611434&w=2")) is available.

---

### Post by #&amp;thj^% on 2019-09-09
> **Doug S said:**
> [Kernel 5.3-rc8]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.3-rc8/") ([unusual for an -rc8]("https://marc.info/?l=linux-kernel&m=156797640611434&w=2")) is available.

More of a convenience I suppose. [https://lwn.net/Articles/798743/](https://lwn.net/Articles/798743/)

---

### Post by IanW on 2019-09-16
[Linus has signed off on kernel 5.3]("https://www.phoronix.com/scan.php?page=news_item&px=Linux-5.3-Released"). Just waiting for Ubuntu to catch up.

---

### Post by mrfelker on 2019-09-18
Final is released but it appears to be the same level as rc8!

---

### Post by Doug S on 2019-09-19
> **mrfelker said:**
> Final is released but it appears to be the same level as rc8!Could you elaborate? All looks O.K. to me.

---

