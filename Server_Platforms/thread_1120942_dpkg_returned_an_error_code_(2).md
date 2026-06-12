---
title: "dpkg returned an error code (2)"
date: 2009-04-09
forum: Server Platforms
---

### Post by mallox on 2009-04-09
hi guys..
I've following problem..can't install anything via apt-get install..
its ubuntu 8.04 running on server
after typing gcc
```

The program 'gcc' can be found in the following packages:
 * gcc
 * pentium-builder
Try: sudo apt-get install <selected package>
-bash: gcc: command not found

```
sudo apt-get install gcc
```


Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  binutils gcc-4.2 libgomp1
Suggested packages:
  binutils-doc autoconf automake1.9 bison flex gcc-doc gcc-multilib gdb libtool make manpages-dev gcc-4.2-doc gcc-4.2-locales gcc-4.2-multilib
  libgcc1-dbg libgomp1-dbg libmudflap0-4.2-dev libmudflap0-dbg
Recommended packages:
  libc6-dev libc-dev
The following NEW packages will be installed:
  binutils gcc gcc-4.2 libgomp1
0 upgraded, 4 newly installed, 0 to remove and 28 not upgraded.
Need to get 0B/2076kB of archives.
After this operation, 9150kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
E: Sub-process /usr/bin/dpkg returned an error code (2)

```
sudo dpkg --purge gcc
```

dpkg - warning: ignoring request to remove gcc which isn't installed.

```
sudo apt-get check
```

Reading package lists... Done
Building dependency tree
Reading state information... Done

```
dpkg --reconfigure -a doesnt help, restart done
var/lib/dpkg/available was removed, nothing :(
apt-get build-dep dpkg - the same error

could anybody help fix this?
is there any way to display more information during installation to find which package crash?
thanks a lot

---

