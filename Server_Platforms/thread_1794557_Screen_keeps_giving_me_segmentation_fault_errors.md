---
title: "Screen keeps giving me segmentation fault errors"
date: 2011-07-01
forum: Server Platforms
---

### Post by DevgruSeal on 2011-07-01
```
u@m:~$ screen
Segmentation fault
```

Running as different or super user returns the same.

I have already tried reinstalling it (*apt-get install --reinstall screen byobo screen-profiles etc*), purging it (*aptitutde remove --purge screen*) and installing it again from scratch, but nothing fixes it.

I think I know *why* it's broken, but not *how* to fix it -- Several weeks ago, I took an image of a customized VM and restored it to a physical hard-drive. Something was funky with the filesystem, so I fsck'd it. That led to a bunch of corrupt files, which I fixed by restoring the corrupt files from backups. Therefore, my guess was going to be that a binary/file used by/for screen is corrupted, but I don't know how to further troubleshoot or debug. 

Any advice?

E: Here's *strace screen*:
```
execve("/usr/bin/screen", ["screen"], [/* 20 vars */]) = 0
brk(0)                                  = 0x152b000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f82a334a000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f82a3349000
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f82a3348000
arch_prctl(ARCH_SET_FS, 0x7f82a3349680) = 0
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
+++ killed by SIGSEGV +++
```

---

