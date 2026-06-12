---
title: "libattr.so.1.1.0 error 6"
date: 2010-12-20
forum: Server Platforms
---

### Post by sapremias on 2010-12-20
I am having problems with a production FTP server that periodically runs a script to move files from place to place for processing. The script that runs executes several loops to move files where they are supposed to be based on the file name. The problem that started occurring on this system (Ubuntu 10.04 x64 Server: Linux ftp01 2.6.32-27-server #49-Ubuntu SMP Thu Dec 2 02:05:21 UTC 2010 x86_64 GNU/Linux)is that the 'mv' commands started segfaulting. This is the output that I get on the console:

[ 6158.285492] ---[ end trace 40eac3c3c2ca6c91 ]---
[ 6158.515945] mv[6320]: segfault at 7fffe4ed46f8 ip 00007f9265202305 sp 00007fffe4ed4700 error 6 in libattr.so.1.1.0[7f9265200000+4000]
[ 6158.603525] mv[6328]: segfault at 7fff634c4668 ip 00007f3088c93305 sp 00007fff634c4670 error 6 in libattr.so.1.1.0[7f3088c91000+4000]
[ 6158.733902] mv[6336]: segfault at 7fff02008138 ip 00007f976b4a7305 sp 00007fff02008140 error 6 in libattr.so.1.1.0[7f976b4a5000+4000]
[ 6158.828277] mv[6344]: segfault at 7fff7997ecf8 ip 00007f301a6c7305 sp 00007fff7997ed00 error 6 in libattr.so.1.1.0[7f301a6c5000+4000]
[ 6158.920661] mv[6352]: segfault at 7fff85641308 ip 00007fa7ac50a305 sp 00007fff85641310 error 6 in libattr.so.1.1.0[7fa7ac508000+4000]
[ 6159.054496] mv[6360]: segfault at 7fff77da8cb8 ip 00007f5bfa7b2305 sp 00007fff77da8cc0 error 6 in libattr.so.1.1.0[7f5bfa7b0000+4000]
[ 6159.148489] mv[6368]: segfault at 7fff336d97c8 ip 00007f19f64bc305 sp 00007fff336d97d0 error 6 in libattr.so.1.1.0[7f19f64ba000+4000]
[ 6159.242103] mv[6376]: segfault at 7fff7834a5f8 ip 00007f7ae4743305 sp 00007fff7834a600 error 6 in libattr.so.1.1.0[7f7ae4741000+4000]
[ 6159.335203] mv[6384]: segfault at 7fff9c48b948 ip 00007f33c8f61305 sp 00007fff9c48b950 error 6 in libattr.so.1.1.0[7f33c8f5f000+4000]
[ 6292.840785] __ratelimit: 23 callbacks suppressed
[ 6292.867025] mv[7150]: segfault at 7fffc7b53808 ip 00007fee392ef305 sp 00007fffc7b53810 error 6 in libattr.so.1.1.0[7fee392ed000+4000]
[ 6292.965685] mv[7160]: segfault at 7fffd48321d8 ip 00007ff8f4811305 sp 00007fffd48321e0 error 6 in libattr.so.1.1.0[7ff8f480f000+4000]
[ 6293.064408] mv[7168]: segfault at 7fffa31a4c78 ip 00007f1c24edc305 sp 00007fffa31a4c80 error 6 in libattr.so.1.1.0[7f1c24eda000+4000]
[ 6293.166315] mv[7176]: segfault at 7fffd6907998 ip 00007fd21428b305 sp 00007fffd69079a0 error 6 in libattr.so.1.1.0[7fd214289000+4000]
[ 6293.310463] mv[7184]: segfault at 7ffefe6a30d8 ip 00007fdf815cd305 sp 00007ffefe6a30e0 error 6 in libattr.so.1.1.0[7fdf815cb000+4000]
[ 6293.413979] mv[7192]: segfault at 7fff07a526c8 ip 00007f64e7d61305 sp 00007fff07a526d0 error 6 in libattr.so.1.1.0[7f64e7d5f000+4000]
[ 6293.519434] mv[7200]: segfault at 7fffa57add68 ip 00007fca9f785305 sp 00007fffa57add70 error 6 in libattr.so.1.1.0[7fca9f783000+4000]
[ 6293.663706] mv[7208]: segfault at 7fff35511148 ip 00007fa7752fd305 sp 00007fff35511150 error 6 in libattr.so.1.1.0[7fa7752fb000+4000]
[ 6293.767432] mv[7216]: segfault at 7fff6847c468 ip 00007f11f2105305 sp 00007fff6847c470 error 6 in libattr.so.1.1.0[7f11f2103000+4000]
[ 6293.870930] mv[7224]: segfault at 7fff8d6ae528 ip 00007fbe89c6f305 sp 00007fff8d6ae530 error 6 in libattr.so.1.1.0[7fbe89c6d000+4000]


Any ideas of what I should be looking at to fix this problem?

Ive done a 'apt-get --reinstall install coreutils' and 'apt-get --reinstall install libattr1' but neither seemed to help this problem.

---

