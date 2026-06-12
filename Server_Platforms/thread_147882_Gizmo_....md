---
title: "Gizmo ..."
date: 2006-03-21
forum: Server Platforms
---

### Post by dbee on 2006-03-21
gizmo won't work on my server ...
> 
        linux-gate.so.1 =>  (0xffffe000)
        libgtk-x11-2.0.so.0 => /usr/lib/libgtk-x11-2.0.so.0 (0x55572000)
        libgdk-x11-2.0.so.0 => /usr/lib/libgdk-x11-2.0.so.0 (0x55846000)
        libXext.so.6 => /usr/lib/libXext.so.6 (0x558c3000)
        libXft.so.2 => /usr/lib/libXft.so.2 (0x558d0000)
        libfreetype.so.6 => /usr/lib/libfreetype.so.6 (0x558e2000)
        libz.so.1 => /usr/lib/libz.so.1 (0x5594c000)
        libXrender.so.1 => /usr/lib/libXrender.so.1 (0x55960000)
        libfontconfig.so.1 => /usr/lib/libfontconfig.so.1 (0x55969000)
        libX11.so.6 => /usr/lib/libX11.so.6 (0x55997000)
        libatk-1.0.so.0 => /usr/lib/libatk-1.0.so.0 (0x55a57000)
        libgdk_pixbuf-2.0.so.0 => /usr/lib/libgdk_pixbuf-2.0.so.0 (0x55a72000)
        libtiff.so.4 => /usr/lib/libtiff.so.4 (0x55a88000)
        libjpeg.so.62 => /usr/lib/libjpeg.so.62 (0x55ad9000)
        libpng12.so.0 => /usr/lib/libpng12.so.0 (0x55af9000)
        libpangoxft-1.0.so.0 => /usr/lib/libpangoxft-1.0.so.0 (0x55b1d000)
        libpangox-1.0.so.0 => /usr/lib/libpangox-1.0.so.0 (0x55b23000)
        libpangoft2-1.0.so.0 => /usr/lib/libpangoft2-1.0.so.0 (0x55b2e000)
        libpango-1.0.so.0 => /usr/lib/libpango-1.0.so.0 (0x55b51000)
        libgobject-2.0.so.0 => /usr/lib/libgobject-2.0.so.0 (0x55b86000)
        libgmodule-2.0.so.0 => /usr/lib/libgmodule-2.0.so.0 (0x55bbe000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0x55bc1000)
        libglib-2.0.so.0 => /usr/lib/libglib-2.0.so.0 (0x55bc4000)
        libgthread-2.0.so.0 => /usr/lib/libgthread-2.0.so.0 (0x55c45000)
        libgconf-2.so.4 => /usr/lib/libgconf-2.so.4 (0x55c49000)
        libORBit-2.so.0 => /usr/lib/libORBit-2.so.0 (0x55c79000)
        libglade-2.0.so.0 => /usr/lib/libglade-2.0.so.0 (0x55ccb000)
        libxml2.so.2 => /usr/lib/libxml2.so.2 (0x55ce1000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0x55ded000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0x55dff000)
        libsipphoneapi.so => /usr/lib/libsipphoneapi.so (0x55e21000)
        libsipphonesslopsapi.so => /usr/lib/libsipphonesslopsapi.so (0x566ce000)
        libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0x566f1000)
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0x567d7000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0x567e2000)
        libexpat.so.1 => /usr/lib/libexpat.so.1 (0x56910000)
        libpangocairo-1.0.so.0 => /usr/lib/libpangocairo-1.0.so.0 (0x5692f000)
        libcairo.so.2 => /usr/lib/libcairo.so.2 (0x56935000)
        libXinerama.so.1 => /usr/lib/libXinerama.so.1 (0x5697c000)
        libXi.so.6 => /usr/lib/libXi.so.6 (0x5697f000)
        libXrandr.so.2 => /usr/lib/libXrandr.so.2 (0x56987000)
        libXcursor.so.1 => /usr/lib/libXcursor.so.1 (0x5698a000)
        libXfixes.so.3 => /usr/lib/libXfixes.so.3 (0x56993000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0x56998000)
        libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0x5699b000)
        /lib/ld-linux.so.2 (0x55555000)
        libpopt.so.0 => /lib/libpopt.so.0 (0x5699f000)
        libdns_sd.so => /usr/lib/libdns_sd.so (0x569a7000)
        libssl.so.0.9.7 => /usr/lib/i686/cmov/libssl.so.0.9.7 (0x569ad000)
        libcrypto.so.0.9.7 => /usr/lib/i686/cmov/libcrypto.so.0.9.7 (0x569dd000)
        libcurl.so.3 => /usr/lib/libcurl.so.3 (0x56ada000)
        librt.so.1 => /lib/tls/i686/cmov/librt.so.1 (0x56b0b000)
        libasound.so.2 => /usr/lib/libasound.so.2 (0x56b13000)
        libidn.so.11 => /usr/lib/libidn.so.11 (0x56bc7000)


I have it in 32 bit chroot environment ...

> 
root@ubuntu64:/usr/bin# gizmo

(gizmo:19115): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

(gizmo:19115): Gtk-WARNING **: cannot open display:


---

### Post by claes on 2006-03-21
Have you started the X server as root? See that you run gizmo as root. The only user that are alowed to connect to the X server is the user that started it.

Claes

---

### Post by dbee on 2006-03-22
Can my chroot connect and use the X server from my original root then ?

Or does it have to have it's own X server ?

---

### Post by claes on 2006-03-22
Not sure how it works with does bit. But I'm talking about the user not the filesystem.

Claes

---

