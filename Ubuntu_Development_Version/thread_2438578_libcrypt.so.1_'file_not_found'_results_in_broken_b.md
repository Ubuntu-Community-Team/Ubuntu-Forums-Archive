---
title: "libcrypt.so.1 'file not found' results in broken boot"
date: 2020-03-14
forum: Ubuntu Development Version
---

### Post by jkwiatkoski on 2020-03-14
After latest updates from the last day or two my 20.04 will no longer boot. I am debugging below using a liveCD chrooted to my broken install. It looks like an issue with libcrypt.so.1? I cannot drop to a root shell via recovery with an error message saying that libcrypt.so.1 file not found. This also prevents any tty's from prompting for passwords at login.yesterday


```
root@ubuntu:/# apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 libc-bin : Depends: libc6 (< 2.31) but 2.31-0ubuntu5 is installed
 libc6:i386 : Depends: libcrypt1:i386 but it is not installed
 libcrypt-dev : Depends: libcrypt1 (= 1:4.4.10-10ubuntu4) but 1:4.4.10-10ubuntu1 is installed
 locales : Depends: libc-bin (> 2.31)
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
root@ubuntu:/# apt --fix-broken install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following additional packages will be installed:
  libc-bin libcrypt1 libcrypt1:i386
The following NEW packages will be installed:
  libcrypt1:i386
The following packages will be upgraded:
  libc-bin libcrypt1
2 upgraded, 1 newly installed, 0 to remove and 104 not upgraded.
7 not fully installed or removed.
Need to get 0 B/804 kB of archives.
After this operation, 267 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
/usr/bin/perl: error while loading shared libraries: libcrypt.so.1: cannot open shared object file: No such file or directory
E: Can not write log (Is /dev/pts mounted?) - posix_openpt (19: No such device)
Setting up libc6:amd64 (2.31-0ubuntu5) ...
/usr/bin/perl: error while loading shared libraries: libcrypt.so.1: cannot open shared object file: No such file or directory
dpkg: error processing package libc6:amd64 (--configure):
 installed libc6:amd64 package post-installation script subprocess returned error exit status 127
Errors were encountered while processing:
 libc6:amd64
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ubuntu:/# 

```


Any thoughts on how this could be resolved?

---

### Post by jkwiatkoski on 2020-03-14
This was the bug i was hitting: [https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/1866844](https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/1866844)

These steps resolved my issue: [https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/1866844/comments/12](https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/1866844/comments/12)

---

### Post by paulycalvinmiller on 2020-03-14
This issue has bricked my computer. Can't enter bios, can't enter grub, won't boot to Bootable USB. No CD Drive on laptop. Yoga 920 bricked unless someone has any ideas. $1200 laptop. Should have stayed away from the developmental version.

---

### Post by paulycalvinmiller on 2020-03-14
I have pressed esc and now I am seeing grub>
Minimal Bash Like Line editing

Can anyone help me here?

---

