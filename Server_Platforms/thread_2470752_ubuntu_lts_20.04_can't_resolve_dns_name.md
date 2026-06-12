---
title: "ubuntu lts 20.04 can't resolve dns name"
date: 2022-01-10
forum: Server Platforms
---

### Post by decehakan on 2022-01-10
Dear Ubuntu-Team and Community
 
i purge reinstall the package bind9-dnsutils and if i want to resolve dns name google.com like host or nslookup i get the following error:
 
$ host google.com
host: symbol lookup error: /lib/x86_64-linux-gnu/libisc.so.1601: undefined symbol: deflate
 
$ nslookup google.com
nslookup: symbol lookup error: /lib/x86_64-linux-gnu/libisc.so.1601: undefined symbol: deflate
 

checking ldd, is looking fine
 
$ ldd /usr/bin/host
        linux-vdso.so.1 (0x00007ffd621da000)
        libdns.so.1601 => /lib/x86_64-linux-gnu/libdns.so.1601 (0x00007fece36d4000)
        libirs.so.1600 => /lib/x86_64-linux-gnu/libirs.so.1600 (0x00007fece36c7000)
        libbind9.so.1600 => /lib/x86_64-linux-gnu/libbind9.so.1600 (0x00007fece36b2000)
        libisccfg.so.1600 => /lib/x86_64-linux-gnu/libisccfg.so.1600 (0x00007fece367c000)
        libisc.so.1601 => /lib/x86_64-linux-gnu/libisc.so.1601 (0x00007fece3607000)
        libcrypto.so.1.1 => /lib/x86_64-linux-gnu/libcrypto.so.1.1 (0x00007fece3331000)
        libidn2.so.0 => /lib/x86_64-linux-gnu/libidn2.so.0 (0x00007fece330e000)
        libpthread.so.0 => /lib/x86_64-linux-gnu/libpthread.so.0 (0x00007fece32eb000)
        libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007fece30f9000)
        libjson-c.so.4 => /lib/x86_64-linux-gnu/libjson-c.so.4 (0x00007fece30e7000)
        libxml2.so.2 => /opt/lib7/program/libxml2.so.2 (0x00007fece2d2e000)
        libgssapi_krb5.so.2 => /lib/x86_64-linux-gnu/libgssapi_krb5.so.2 (0x00007fece2ce1000)
        libkrb5.so.3 => /lib/x86_64-linux-gnu/libkrb5.so.3 (0x00007fece2c02000)
        libmaxminddb.so.0 => /lib/x86_64-linux-gnu/libmaxminddb.so.0 (0x00007fece2bfb000)
        liblmdb.so.0 => /lib/x86_64-linux-gnu/liblmdb.so.0 (0x00007fece2be3000)
        libdl.so.2 => /lib/x86_64-linux-gnu/libdl.so.2 (0x00007fece2bdd000)
        /lib64/ld-linux-x86-64.so.2 (0x00007fece3917000)
        libns.so.1601 => /lib/x86_64-linux-gnu/libns.so.1601 (0x00007fece2b93000)
        libuv.so.1 => /lib/x86_64-linux-gnu/libuv.so.1 (0x00007fece2b60000)
        libunistring.so.2 => /lib/x86_64-linux-gnu/libunistring.so.2 (0x00007fece29de000)
        libm.so.6 => /lib/x86_64-linux-gnu/libm.so.6 (0x00007fece288f000)
        libk5crypto.so.3 => /lib/x86_64-linux-gnu/libk5crypto.so.3 (0x00007fece285e000)
        libcom_err.so.2 => /lib/x86_64-linux-gnu/libcom_err.so.2 (0x00007fece2857000)
        libkrb5support.so.0 => /lib/x86_64-linux-gnu/libkrb5support.so.0 (0x00007fece2848000)
        libkeyutils.so.1 => /lib/x86_64-linux-gnu/libkeyutils.so.1 (0x00007fece283f000)
        libresolv.so.2 => /lib/x86_64-linux-gnu/libresolv.so.2 (0x00007fece2823000)
 
What should i do ?

Of another server ubuntu lts. 20.04  the DNS name can be resolved. 

kind regards decehakan

---

### Post by TheFu on 2022-01-10
[https://ubuntu.com/server/docs/service-domain-name-service-dns](https://ubuntu.com/server/docs/service-domain-name-service-dns) has instructions for setting up bind9 correctly.

---

