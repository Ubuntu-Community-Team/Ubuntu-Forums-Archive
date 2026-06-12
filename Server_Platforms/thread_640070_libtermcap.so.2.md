---
title: "libtermcap.so.2"
date: 2007-12-13
forum: Server Platforms
---

### Post by jvain2005@gmail.com on 2007-12-13
I need libtermcap.so.2 for ubuntu server ed 7.10. I am not able to find it. doing little google i found that it should be part of termcap-compat. so when i do 

sudo apt-get install termcap-compat it should install. but it is not finding that package in repository.

jvain2005@ubuntu:~$ ldd ./setup
        linux-gate.so.1 =>  (0xffffe000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7f2c000)
        libresolv.so.2 => /lib/tls/i686/cmov/libresolv.so.2 (0xb7f19000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7f14000)
        libncurses.so.5 => /lib/libncurses.so.5 (0xb7ed0000)
        libtermcap.so.2 => not found
        libstdc++-libc6.2-2.so.3 => /usr/lib/libstdc++-libc6.2-2.so.3 (0xb7e88000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7e63000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7d18000)
        /lib/ld-linux.so.2 (0xb7f49000)
jvain2005@ubuntu:~$ sudo apt-get install termcap-compat
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package termcap-compat is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package termcap-compat has no installation candidate
jvain2005@ubuntu:~$ 


any idea where can I get it? 
If this package is obsolute, how can i fool my app to use new version?

---

