---
title: "compile curl, static executable"
date: 2015-09-22
forum: Ubuntu Dev Link Forum
---

### Post by Beer_Town on 2015-09-22
Hi all.

I'm trying to compile curl to a fully static executable.
I'm using curl-7.44.0 sources, the current stable version. I googled a lot but I still haven't figured out how to get my stand-alone executable. I've found a lot of very old mailing list discussions that didn't help me.

My best result is compiling with:

```
./configure --disable-shared --enable-static
```

that produces a curl executable that does not depend on libcurl, but still depends on libssl and others:
```
$ ldd src/curl
    linux-gate.so.1 =>  (0xb77ca000)
    libssl.so.1.0.0 => /lib/i386-linux-gnu/libssl.so.1.0.0 (0xb7759000)
    libcrypto.so.1.0.0 => /lib/i386-linux-gnu/libcrypto.so.1.0.0 (0xb75ac000)
    libz.so.1 => /lib/i386-linux-gnu/libz.so.1 (0xb7591000)
    libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0xb73e3000)
    libdl.so.2 => /lib/i386-linux-gnu/libdl.so.2 (0xb73de000)
    /lib/ld-linux.so.2 (0xb77cc000)
```

I hope somebody here could help me!

thanks in advance.

---

