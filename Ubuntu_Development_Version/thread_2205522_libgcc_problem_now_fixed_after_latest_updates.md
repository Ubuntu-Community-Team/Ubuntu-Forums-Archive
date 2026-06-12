---
title: "libgcc problem now fixed after latest updates"
date: 2014-02-14
forum: Ubuntu Development Version
---

### Post by paul_in_london on 2014-02-14
During the breakage used:

```
# dpkg -i /var/cache/apt/archives/libgcc1_1%3a4.8.2-15ubuntu3_amd64.deb
```

to get aptitude/apt-get working again.

Now after the latest updates:

```
paul@trusty:~$ locate libgcc | grep -v var
/lib/x86_64-linux-gnu/libgcc_s.so.1
/usr/lib/gcc/x86_64-linux-gnu/4.8/libgcc.a
/usr/lib/gcc/x86_64-linux-gnu/4.8/libgcc_eh.a
/usr/lib/gcc/x86_64-linux-gnu/4.8/libgcc_s.so
/usr/lib/x86_64-linux-gnu/libgccpp.so.1
/usr/lib/x86_64-linux-gnu/libgccpp.so.1.0.3
/usr/share/doc/libgcc-4.8-dev
/usr/share/doc/libgcc1
/usr/share/lintian/overrides/libgcc1
/usr/src/linux-3.14-rc1/arch/microblaze/lib/libgcc.h
/usr/src/linux-3.14-rc1/arch/mips/lib/libgcc.h
/usr/src/linux-3.14-rc1/arch/score/lib/libgcc.h
/usr/src/linux-3.14-rc1/arch/sh/lib/libgcc.h
/usr/src/linux-3.14-rc1/arch/sparc/lib/libgcc.h
```

```
paul@trusty:~$ locate libgcc_s
/lib/x86_64-linux-gnu/libgcc_s.so.1
/usr/lib/gcc/x86_64-linux-gnu/4.8/libgcc_s.so
paul@trusty:~$ 
```

```
paul@trusty:~$ ls -la /usr/lib/gcc/x86_64-linux-gnu/4.8/libgcc_s.so
lrwxrwxrwx 1 root root 35 Feb 12 02:18 /usr/lib/gcc/x86_64-linux-gnu/4.8/libgcc_s.so -> /lib/x86_64-linux-gnu/libgcc_s.so.1
paul@trusty:~$
```

```
paul@trusty:~$ apt-cache policy  libgcc1
libgcc1:
  Installed: 1:4.9-20140213-0ubuntu2
  Candidate: 1:4.9-20140213-0ubuntu2
  Version table:
 *** 1:4.9-20140213-0ubuntu2 0
        500 http://gb.archive.ubuntu.com/ubuntu/ trusty-proposed/main amd64 Packages
        100 /var/lib/dpkg/status
     1:4.8.2-15ubuntu3 0
        500 http://gb.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
paul@trusty:~$
```

```
paul@trusty:~$ apt-cache policy  gcc-4.9-base
gcc-4.9-base:
  Installed: 4.9-20140213-0ubuntu2
  Candidate: 4.9-20140213-0ubuntu2
  Version table:
 *** 4.9-20140213-0ubuntu2 0
        500 http://gb.archive.ubuntu.com/ubuntu/ trusty-proposed/main amd64 Packages
        100 /var/lib/dpkg/status
paul@trusty:~$
```

---

