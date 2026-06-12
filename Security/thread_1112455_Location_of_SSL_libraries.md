---
title: "Location of SSL libraries"
date: 2009-03-31
forum: Security
---

### Post by Sebonix on 2009-03-31
I ran into some issues with OpenSSL when running Nmap scans.  So I updated my openssl, libssl, and libssl-dev packages and recompiled Nmap from source.  Out of curiousity I ran `ldd` against my new `nmap` binary and noticed that it's linking to libssl.so.0.9.8 in /usr/lib/i686/cmov/ but the newest version seems to reside in /usr/lib.  Anyone know why Ubuntu would not expose the most recent version?  Granted, I can use the appropriate `configure` directive to specify the path but I'm perplexed, or perhaps just ignorant.

Running a fully updated 8.04 on x86.

/usr/bin$ ldd /usr/local/bin/nmap
        linux-gate.so.1 =>  (0xb7f7f000)
        libpcre.so.3 => /usr/lib/libpcre.so.3 (0xb7f4a000)
        libpcap.so.0.8 => /usr/lib/libpcap.so.0.8 (0xb7f21000)
        libssl.so.0.9.8 => /usr/lib/i686/cmov/libssl.so.0.9.8 (0xb7ede000)
        libcrypto.so.0.9.8 => /usr/lib/i686/cmov/libcrypto.so.0.9.8 (0xb7d9c000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7d98000)
        libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0xb7ca5000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7c80000)
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb7c75000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7b25000)
        libz.so.1 => /usr/lib/libz.so.1 (0xb7b10000)
        /lib/ld-linux.so.2 (0xb7f80000)

/usr/bin$ locate libssl.so | xargs ls -al
-rw-r--r-- 1 root root 253508 2009-03-26 17:49 /usr/lib/i486/libssl.so.0.9.8
-rw-r--r-- 1 root root 248356 2009-03-26 17:49 /usr/lib/i586/libssl.so.0.9.8
-rw-r--r-- 1 root root 264420 2009-03-26 17:49 /usr/lib/i686/cmov/libssl.so.0.9.8
lrwxrwxrwx 1 root root     15 2009-03-31 13:05 /usr/lib/libssl.so -> libssl.so.0.9.8
-rw-r--r-- 1 root root 264548 2009-03-26 17:49 /usr/lib/libssl.so.0.9.8



Thanks,

Seb

---

### Post by hyper_ch on 2009-03-31
you answered your question already... you did not configure it correct according to ubuntu scheme.

---

### Post by Sebonix on 2009-03-31
I can guess at what you mean but, I think you're missing my point.  When I installed Ubuntu OpenSSL was included.  Subsequently I have updated all OpenSSL related files using `apt-get`.  So, Ubuntu decided where to put the OpenSSL libraries, and it seems to be putting things in different directories.  That would be fine if during a `configure` it told software "I keep the OpenSSL libraries over here" and pointed to the most recent version but, this doesn't seem to be the case.  It seems to update /usr/lib with the newer files but, by default, identify those libraries in /usr/lib/i686/cmov/ to software as what should be used during the build process.

---

