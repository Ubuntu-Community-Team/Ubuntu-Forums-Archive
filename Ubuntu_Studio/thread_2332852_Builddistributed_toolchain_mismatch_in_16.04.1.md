---
title: "Build/distributed toolchain mismatch in 16.04.1"
date: 2016-08-04
forum: Ubuntu Studio
---

### Post by perheldal on 2016-08-04
I just upgraded from 14.04 to 16.04.1 as suggested by the software update-tools and got problems with a couple custom kernel modules I need to build on this host. Compilation and/or linking of kernel modules should be performed with the same toolchain used to compile the kernel.

/proc/version:
```
Linux version 4.4.0-34-lowlatency (buildd@lgw01-20) (gcc version [COLOR=#ff0000]**5.3.1**[/COLOR] 20160413 (Ubuntu 5.3.1-14ubuntu2.1) ) #53-Ubuntu SMP PREEMPT Wed Jul 27 19:23:26 UTC 2016
```

The "compatibility-packages" with symlinks are tagged with a version matching the compiler used to build the kernel:
```
ii  gcc                          4:[COLOR=#ff0000]**5.3.1**[/COLOR]-1ubuntu1    amd64               GNU C compiler
```
but the symlink within points to gcc-5
```
lrwxrwxrwx 1 root root 5 feb.  11 10:47 /usr/bin/gcc -> gcc-5
```
which turns out to be gcc version 5.4.0
```
gcc-5 (Ubuntu [COLOR=#ff0000]**5.4.0**[/COLOR]-6ubuntu1~16.04.1) 5.4.0 20160609
```
The corresponding binary package installed is version 5.4.0
```
ii  gcc-5                        [COLOR=#ff0000]**5.4.0**[/COLOR]-6ubuntu1~16.0 amd64               GNU C compiler
```
There is no gcc-5.3.1 binary available in the repos so there is no simple workaround

The same issue applies to other packages in the build toolchain (cpp, g++, gcc and lots of other tools/libraries)

It's surprising that there aren't more complaints in the forum as this issue breaks the widely used Nvidia graphics-drivers as well as any other custom kernel module that has to be compiled and linked on a running system. Is there a kernel somewhere in the repos that is built with the gcc 5.4.0 toolchain? To force older versions of the compiler and all related tools/libraries creates a mess of dependencies that is very hard to resolve. The bump of compiler-toolchain-versions that have happened in the xenial-updates repo seem to be a mistake unless the kernel (4.4.0-34-lowlatency) also gets an upgrade.

---

