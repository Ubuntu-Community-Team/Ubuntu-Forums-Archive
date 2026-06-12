---
title: "Firmware update not installing"
date: 2022-03-15
forum: Ubuntu Development Version
---

### Post by exploder on 2022-03-15
An update to the Linux firmware drivers came in last night but refuses to install. Just wondering if anyone else is having this issue?

---

### Post by zebra2 on 2022-03-15
Disable "proposed" if enabled and refresh.
Run ```
 dpkg --configure -a 
``` with sudo.

---

### Post by zika on 2022-03-15
Had this trouble, today, on one of several machines that I work on.
Solved it this way:
1. Download some older version of that package, I did that from xanmod site.
2. Install that package via dpkg from downloade .deb
3. Then do apt upgrade and all should be OK.
Yes I do use latest, on-the-edge, version, and that worked.
```
:~$ apt policy linux-firmwarelinux-firmware:
  &#1048;&#1085;&#1089;&#1090;&#1072;&#1083;&#1080;&#1088;&#1072;&#1085;: 20220314.gitcd01f857-0ubuntu2
  &#1050;&#1072;&#1085;&#1076;&#1080;&#1076;&#1072;&#1090;:   20220314.gitcd01f857-0ubuntu2
  &#1058;&#1072;&#1073;&#1077;&#1083;&#1072; &#1080;&#1079;&#1076;&#1072;&#1114;&#1072;:
 *** 20220314.gitcd01f857-0ubuntu2 500
        500 http://archive.ubuntu.com/ubuntu devel-proposed/main amd64 Packages
        500 http://archive.ubuntu.com/ubuntu devel-proposed/main i386 Packages
        100 /var/lib/dpkg/status
     20220314.gitcd01f857-0ubuntu1 500
        500 http://archive.ubuntu.com/ubuntu devel/main amd64 Packages
        500 http://archive.ubuntu.com/ubuntu devel/main i386 Packages
     1.201.5 500
        500 http://deb.xanmod.org releases/main amd64 Packages
        500 http://deb.xanmod.org releases/main i386 Packages
```
Other is solution is to mark it on hold and wait for a newer version. Simple glitch with one file in package... It could be solved by some editing but, since I was at work, I took easier way out... ;)
Funny, home machine did not report any trouble and upgrade went smoothly.

---

### Post by corradoventu on 2022-03-15
[https://www.mail-archive.com/kernel-packages@lists.launchpad.net/msg473446.html](https://www.mail-archive.com/kernel-packages@lists.launchpad.net/msg473446.html)
[https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/1964814](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/1964814)

---

### Post by Claus7 on 2022-03-15
Hello,

the error I received was the following:
> unable to open '/lib/firmware/ath11k/WCN6855/hw2.0/regdb.bin.dpkg-new': No such file or directory No apport report written because the error message indicates an issue on the local system

In the meantime I had at some time proposed enabled. With proposed disabled, I purged the firmware package. This also removed the following packages:
linux-generic
linux-image-generic

I installed the firmware anew without problems and the linux-image-generic (linux-generic could not be installed).

System is working fine.

Regards!

---

### Post by zebra2 on 2022-03-15
Fix is in "proposed".  Just updated my #2 system with no problem.

---

### Post by lammert-nijhof on 2022-03-16
I had the same issue, after a day it has been solved.

---

### Post by vicshrike on 2022-03-16
Yes, update came through after a while here too. There were some other packages too, about 10 if I recall correctly; that were held back for a day before they upgraded.

---

### Post by exploder on 2022-03-16
I grabbed the package from proposed and later the package made it to the regular repo. The additional drivers app is still broken though.

---

