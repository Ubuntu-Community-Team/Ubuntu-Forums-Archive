---
title: "RRDTool error on Ubuntu Server 9.04"
date: 2009-07-26
forum: Server Platforms
---

### Post by Hurup on 2009-07-26
Hello :)

I'm having a error when i'm trying to create a image of a rrd file.

The error is:
/usr/bin/rrdtool: symbol lookup error: /usr/lib/libcairo.so.2: undefined symbol: pixman_region32_init
/usr/bin/rrdtool: symbol lookup error: /usr/lib/libcairo.so.2: undefined symbol: pixman_region32_init
/usr/bin/rrdtool: symbol lookup error: /usr/lib/libcairo.so.2: undefined symbol: pixman_region32_init

Do anyone know what that is?

---

### Post by Hurup on 2009-07-26
If this is any help:
ldd /usr/lib/libcairo.so.2
        linux-gate.so.1 =>  (0xb7f65000)
        libpixman-1.so.0 => /usr/local/lib/libpixman-1.so.0 (0xb7eb8000)
        libfreetype.so.6 => /usr/lib/libfreetype.so.6 (0xb7e41000)
        libfontconfig.so.1 => /usr/lib/libfontconfig.so.1 (0xb7e13000)
        libdirectfb-1.0.so.0 => /usr/lib/libdirectfb-1.0.so.0 (0xb7dad000)
        libfusion-1.0.so.0 => /usr/lib/libfusion-1.0.so.0 (0xb7da4000)
        libdirect-1.0.so.0 => /usr/lib/libdirect-1.0.so.0 (0xb7d8f000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7d76000)
        libpng12.so.0 => /usr/lib/libpng12.so.0 (0xb7d4f000)
        libxcb-render-util.so.0 => /usr/lib/libxcb-render-util.so.0 (0xb7d4a000)
        libxcb-render.so.0 => /usr/lib/libxcb-render.so.0 (0xb7d42000)
        libxcb.so.1 => /usr/lib/libxcb.so.1 (0xb7d28000)
        libXrender.so.1 => /usr/lib/libXrender.so.1 (0xb7d1e000)
        libX11.so.6 => /usr/lib/libX11.so.6 (0xb7c2e000)
        libz.so.1 => /lib/libz.so.1 (0xb7c18000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7bf2000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7a8f000)
        libexpat.so.1 => /usr/lib/libexpat.so.1 (0xb7a68000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7a64000)
        /lib/ld-linux.so.2 (0xb7f66000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0xb7a5f000)
        libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb7a5a000)

---

### Post by Hurup on 2009-07-27
Please help - I'm runnig out of ideas...

---

### Post by kenjidnb on 2009-11-23
Hi Hurup,

I am facing the same issue. Have you found a solution to your problem?

---

