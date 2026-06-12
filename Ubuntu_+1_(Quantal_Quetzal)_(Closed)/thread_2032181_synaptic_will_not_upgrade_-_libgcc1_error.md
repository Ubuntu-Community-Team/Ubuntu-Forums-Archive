---
title: "synaptic will not upgrade - libgcc1 error"
date: 2012-07-23
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by ventrical on 2012-07-23
Just updated/upgraded , but now synaptic is blocking upgrade:

---

### Post by ventrical on 2012-07-23
synaptic reports it in the list  and even sudo apt-get update/upgrade is blocked from terminal.

---

### Post by philinux on 2012-07-23
Not seeing this. Just updated via chroot then rebooted. Nothing adrift.

---

### Post by ventrical on 2012-07-23
I'll try a reboot.

Nope!   No such luck.

Need to get 0 B/241 MB of archives.
After this operation, 10.0 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
E: Internal Error, No file name for libgcc1
dale@dale-desktop:~$

---

### Post by ventrical on 2012-07-23
Now synaptic package manager just died. Won't even come up.?

Weird.

Looks like some breakage amidst us! :)

Oh Joy!:)

---

### Post by philinux on 2012-07-23
> **ventrical said:**
> Now synaptic package manager just died. Won't even come up.?

Weird.

Looks like some breakage amidst us! :)

Oh Joy!:)

Any errors from update / upgrade in terminal.

apt-cache policy libgcc1 
libgcc1:
  Installed: 1:4.7.1-5ubuntu1
  Candidate: 1:4.7.1-5ubuntu1

---

### Post by ventrical on 2012-07-23
> **philinux said:**
> Any errors from update / upgrade in terminal.

apt-cache policy libgcc1 
libgcc1:
  Installed: 1:4.7.1-5ubuntu1
  Candidate: 1:4.7.1-5ubuntu1


Posted them in previous:


Need to get 0 B/241 MB of archives.
After this operation, 10.0 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
E: Internal Error, No file name for libgcc1
dale@dale-desktop:~$

-------------------------------
libgcc1:
  Installed: 1:4.7.1-5ubuntu1
  Candidate: 1:4.7.1-5ubuntu1
  Version table:
 *** 1:4.7.1-5ubuntu1 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/main i386 Packages
        100 /var/lib/dpkg/status

---

### Post by philinux on 2012-07-23
$ apt-get update
$ apt-get clean
$ apt-get install -fy
$ dpkg -i /var/cache/apt/archives/*.deb
$ dpkg --configure -a
$ apt-get install -fy
$ apt-get dist-upgrade

From similar.
[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/945722](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/945722)

---

### Post by ventrical on 2012-07-23
dpkg --configure -a

Thanks!

I am just curious as to why apport did not catch this or why apt did not report it because usually apt does, however, on this particular install I am using 'dolphin' file_manager . Perhaps this may have caused  the problem.

Thanks again.

---

