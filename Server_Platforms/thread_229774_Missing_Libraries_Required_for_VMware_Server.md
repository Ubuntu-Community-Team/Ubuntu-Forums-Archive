---
title: "Missing Libraries Required for VMware Server"
date: 2006-08-04
forum: Server Platforms
---

### Post by jonc101 on 2006-08-04
I'm trying to install vmware server 1.0.0 build 28343, the installation script told me that a version of libc was outdated and suggested that I might have to upgrade to glibc.  I've installed 'build-essential'.  What other libraries should be installed so that vmware can run without a problem?

I need to fix this because I can't enter in a license key to register vmware server and according to a few people on the vmware forums they say that its due to a library problem so I just put two and two together.  

Any help will be appreciated!

---

### Post by jonc101 on 2006-08-05
I un-installed vmware and re-installed it and this is the exact error message it's giving me:

```
The correct version of one or more libraries needed to run VMware Server may be
missing.  This is the output of ldd /usr/bin/vmware:
        linux-gate.so.1 =>  (0xffffe000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7f5a000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7f57000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7f45000)
        libX11.so.6 => not found
        libXtst.so.6 => not found
        libXext.so.6 => not found
        libXt.so.6 => not found
        libICE.so.6 => not found
        libSM.so.6 => not found
        libXrender.so.1 => not found
        libz.so.1 => /usr/lib/libz.so.1 (0xb7f2f000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7e00000)
        /lib/ld-linux.so.2 (0xb7f83000)

This program cannot tell for sure, but you may need to upgrade libc5 to glibc
before you can run VMware Server.

Hit enter to continue.
```

How do I install these files?

---

### Post by lamego on 2006-08-05
```
lamego@lamego-desktop:/$ dpkg-query -S libX11.so.6
libx11-6: /usr/lib/libX11.so.6.2.0
libx11-6: /usr/lib/libX11.so.6
```
You will need to install package libx11-6

---

