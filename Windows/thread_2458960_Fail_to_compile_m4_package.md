---
title: "Fail to compile m4 package"
date: 2021-03-07
forum: Windows
---

### Post by gadi01 on 2021-03-07
Hello, please help me solve this problem,
I use Cygwin under Windows Xp and I plan to install packages for compiling and running programs in Fortran and C languages and before, it is necessary to build and compile packages. I tried to configure m4 but when I type "make" in Cygwin console I got this message:
 $ make
C:/cygwin/bin/sh.exe
C:/cygwin/bin/make  all-recursive
C:/cygwin/bin/sh.exe
make[1]: Entering directory `C:/cygwin/tc/m4-1.4.18'
make[1]: Nothing to be done for `all-recursive'.
make[1]: Leaving directory `C:/cygwin/tc/m4-1.4.18'
and when I type "make" and "make -j" in the / lib subdirectory I have these errors:
$ make
make (e=-1): Error -1
make: *** [sys/stat.h] Error -1
$ make -j
make (e=-1): Error -1
make: *** [sys/stat.h] Error -1
make: *** Waiting for unfinished jobs....
make (e=-1): Error -1
make: *** [sys/time.h] Error -1
make (e=-1): Error -1
make: *** [sys/types.h] Error -1
make (e=-1): Error -1
make: *** [sys/wait.h] Error -1


how can I fix these errors to install the package?
please do not hesitate to react with my post.
N.B: I use an offline cygwin version, so I can not add packages from Cygwin  setup Installer

---

### Post by QIII on 2021-03-07
While Cygwin may provide a substantial library of GNU and other open-source APIs and may provide an environment *similar* to Linux, it is not Linux.

Moved to Windows.

---

