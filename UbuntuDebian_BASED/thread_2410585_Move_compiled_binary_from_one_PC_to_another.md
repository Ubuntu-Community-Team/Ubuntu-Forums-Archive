---
title: "Move compiled binary from one PC to another"
date: 2019-01-17
forum: Ubuntu/Debian BASED
---

### Post by mmessiah on 2019-01-17
Hello,

I've compiled "MARC-FS" project at one Debian 9 virtual server and need to copy the binaries to another one (same Debian 9). There are no official binaries and this project is not available from repos.
It requires libjsoncpp.so.1, libjemalloc.so.2 and libfuse3.so.3 - all of them were located at the old machine and copied to new one to the current folder.
The same thing done with libstdc++.so.6. Now I have this error:
> ./marcfs: /lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.28' not found (required by libfuse3.so.3)
I have /lib/x86_64-linux-gnu/libc.so.6, it's a symlink to libc-2.19.so. If I'm replacing libc.so.6 system crashes. How to copy binaries properly?

The question is not about the marcfs, but about the generic problem of compiling at one machine and distributing to few other machines. Usually I did not got such troubles, a binary usually starts at new machine without any problems.

P.S. I don't want to compile it at each machine individually, 1) it's stupid 2) there should not be any unnecessary software installed

---

### Post by ajgreeny on 2019-01-17
When using source code to configure, make, and install software, [checkinstall]("https://help.ubuntu.com/community/CheckInstall") is your friend when you want to do what you're asking about.

Having configured and compiled you use command **sudo checkinstall** instead of **sudo makeinstall** and an ***application*.deb** archive will be created in the source folder.  You can then copy that .deb package to other machines and so long as the hardware is at least similar, it should install normally like any other .deb archive.

Worth trying!

---

### Post by mmessiah on 2019-01-17
Thank you for reply.
I generated a .deb package and installed it on the second machine, but it technically only copied the binary to /usr/local/bin/.
All .so are still missing. I'm putting it to the same directories manually, but now found there is the same problem with libc.so.6. I can't replace this file in the system because it will crash the system.

---

### Post by sisco311 on 2019-01-17
Try to build it statically. [https://en.wikipedia.org/wiki/Static_build](https://en.wikipedia.org/wiki/Static_build)

---

