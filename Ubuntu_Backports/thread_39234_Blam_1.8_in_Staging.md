---
title: "Blam 1.8 in Staging"
date: 2005-06-03
forum: Ubuntu Backports
---

### Post by Majlo on 2005-06-03
Hi .
I try Blam 1.8 from Staging and give me this error

[HTML]mario@ubuntu:~$ blam

Unhandled Exception: System.DllNotFoundException: libblam.so
in (wrapper managed-to-native) Imendio.Blam.MessageConnection:bacon_message_conn ection_new (string)
in <0x00016> Imendio.Blam.MessageConnection:.ctor (System.String appName)
in <0x00075> Imendio.Blam.Application:.ctor (System.String[] args, System.Object [] props)
in <0x0002c> Imendio.Blam.Application:Main (System.String[] args)[/HTML] 

When i compile blam from source works great.
Any suggestion ?

---

### Post by Slo Mo Snail on 2005-06-04
Is libblam.so located in /usr/lib/blam?

For me it's installed with the package and blam also finds it while running... weird

---

### Post by Majlo on 2005-06-04
[QUOTE=Slo Mo Snail]Is libblam.so located in /usr/lib/blam?

For me it's installed with the package and blam also finds it while running... weird[/QUOTE]

Yes libblam.so is in /usr/lib/blam

```
mario@ubuntu:/usr/lib/blam$ ls -la
total 428
drwxr-xr-x    2 root root   4096 2005-06-04 04:04 .
drwxr-xr-x  130 root root  28672 2005-06-04 04:03 ..
-rw-r--r--    1 root root 117760 2005-06-03 22:45 atom.dll
-rwxr-xr-x    1 root root 193536 2005-06-03 22:45 blam.exe
-rw-r--r--    1 root root    136 2005-06-03 22:45 blam.exe.config
lrwxrwxrwx    1 root root     16 2005-06-04 04:04 libblam.so -> libblam.so.0.0.0
lrwxrwxrwx    1 root root     16 2005-06-04 04:04 libblam.so.0 -> libblam.so.0.0 .0
-rw-r--r--    1 root root  28596 2005-06-03 22:45 libblam.so.0.0.0
-rw-r--r--    1 root root  45568 2005-06-03 22:45 rss.dll
``` 

Hm interesting

---

### Post by jdong on 2005-06-04
I've been having this problem with Blam, too... looking for a solution also.

---

### Post by Slo Mo Snail on 2005-06-04
Hm, what exactly does change when you compile blam by yourself? Especially what changes in /usr/lib/blam?

---

### Post by Majlo on 2005-06-04
[QUOTE=Slo Mo Snail]Hm, what exactly does change when you compile blam by yourself? Especially what changes in /usr/lib/blam?[/QUOTE]

OK
First i uninstall blam 1.8 from staging

*sudo apt-get remove --purge blam* 

Then 
./configure --with-firefox
make
sudo make install

```
mario@ubuntu:~/Software/blam-1.8.0$ ls -la /usr/local/lib/blam/
total 2428
drwxr-xr-x  2 root root    4096 2005-06-05 02:45 .
drwxr-xr-x  5 root root    4096 2005-06-05 02:45 ..
-rw-r--r--  1 root root  117760 2005-06-05 02:45 atom.dll
-rw-r--r--  1 root root  193536 2005-06-05 02:45 blam.exe
-rw-r--r--  1 root root 1330576 2005-06-05 02:45 libblam.a
-rwxr-xr-x  1 root root    2389 2005-06-05 02:45 libblam.la
lrwxrwxrwx  1 root root      16 2005-06-05 02:45 libblam.so -> libblam.so.0.0.0
lrwxrwxrwx  1 root root      16 2005-06-05 02:45 libblam.so.0 -> libblam.so.0.0.0
-rwxr-xr-x  1 root root  759977 2005-06-05 02:45 libblam.so.0.0.0
-rw-r--r--  1 root root   45568 2005-06-05 02:45 rss.dll
``` 

Work perfect

---

### Post by Slo Mo Snail on 2005-06-05
Interesting... the libblam.so.0.0.0 is many times bigger than in the package... and there are statically linked libblam* but that shouldn't be the problem

hmm... try strip --strip-all on /usr/lib/libblam.so.0.0.0 and look at the size it has after that... afaik dpkg-buildpackage strips everything

also ldd /usr/lib/libblam.so.0.0.0 for the one in the package and the one you compiled yourself would be interesting

---

### Post by Majlo on 2005-06-05
OK i compile Blam and then :

```
mario@ubuntu:~/Software/blam-1.8.0$ cd /usr/lib/blam/
mario@ubuntu:/usr/lib/blam$ ls -la
total 2452
drwxr-xr-x    2 root root    4096 2005-06-05 15:59 .
drwxr-xr-x  130 root root   28672 2005-06-05 15:59 ..
-rw-r--r--    1 root root  117760 2005-06-05 15:59 atom.dll
-rw-r--r--    1 root root  193536 2005-06-05 15:59 blam.exe
-rw-r--r--    1 root root 1330576 2005-06-05 15:59 libblam.a
-rwxr-xr-x    1 root root    2384 2005-06-05 15:59 libblam.la
lrwxrwxrwx    1 root root      16 2005-06-05 15:59 libblam.so -> libblam.so.0.0.0
lrwxrwxrwx    1 root root      16 2005-06-05 15:59 libblam.so.0 -> libblam.so.0.0.0
-rwxr-xr-x    1 root root  759977 2005-06-05 15:59 libblam.so.0.0.0
-rw-r--r--    1 root root   45568 2005-06-05 15:59 rss.dll
mario@ubuntu:/usr/lib/blam$ sudo strip --strip-all libblam.so.0.0.0
mario@ubuntu:/usr/lib/blam$ ls -la
total 1732
drwxr-xr-x    2 root root    4096 2005-06-05 16:02 .
drwxr-xr-x  130 root root   28672 2005-06-05 15:59 ..
-rw-r--r--    1 root root  117760 2005-06-05 15:59 atom.dll
-rw-r--r--    1 root root  193536 2005-06-05 15:59 blam.exe
-rw-r--r--    1 root root 1330576 2005-06-05 15:59 libblam.a
-rwxr-xr-x    1 root root    2384 2005-06-05 15:59 libblam.la
lrwxrwxrwx    1 root root      16 2005-06-05 15:59 libblam.so -> libblam.so.0.0.0
lrwxrwxrwx    1 root root      16 2005-06-05 15:59 libblam.so.0 -> libblam.so.0.0.0
-rwxr-xr-x    1 root root   27900 2005-06-05 16:02 libblam.so.0.0.0
-rw-r--r--    1 root root   45568 2005-06-05 15:59 rss.dll
``` 

Then i try ldd :
When i compile Blam :

```
mario@ubuntu:~$ ldd /usr/lib/blam/libblam.so.0.0.0
                libgnomeui-2.so.0 => /usr/lib/libgnomeui-2.so.0 (0xb7f50000)
        libSM.so.6 => /usr/X11R6/lib/libSM.so.6 (0xb7f47000)
        libICE.so.6 => /usr/X11R6/lib/libICE.so.6 (0xb7f2e000)
        libbonoboui-2.so.0 => /usr/lib/libbonoboui-2.so.0 (0xb7ed2000)
        libxml2.so.2 => /usr/lib/libxml2.so.2 (0xb7dd3000)
        libz.so.1 => /usr/lib/libz.so.1 (0xb7dc2000)
        libgnomecanvas-2.so.0 => /usr/lib/libgnomecanvas-2.so.0 (0xb7d99000)
        libgnome-2.so.0 => /usr/lib/libgnome-2.so.0 (0xb7d84000)
        libpopt.so.0 => /lib/libpopt.so.0 (0xb7d7b000)
        libart_lgpl_2.so.2 => /usr/lib/libart_lgpl_2.so.2 (0xb7d66000)
        libpangoft2-1.0.so.0 => /usr/lib/libpangoft2-1.0.so.0 (0xb7d41000)
        libgtk-x11-2.0.so.0 => /usr/lib/libgtk-x11-2.0.so.0 (0xb7a7c000)
        libgdk-x11-2.0.so.0 => /usr/lib/libgdk-x11-2.0.so.0 (0xb7a02000)
        libatk-1.0.so.0 => /usr/lib/libatk-1.0.so.0 (0xb79e6000)
        libgdk_pixbuf-2.0.so.0 => /usr/lib/libgdk_pixbuf-2.0.so.0 (0xb79d0000)
        libpangoxft-1.0.so.0 => /usr/lib/libpangoxft-1.0.so.0 (0xb79c9000)
        libpangox-1.0.so.0 => /usr/lib/libpangox-1.0.so.0 (0xb79be000)
        libpango-1.0.so.0 => /usr/lib/libpango-1.0.so.0 (0xb7987000)
        libgobject-2.0.so.0 => /usr/lib/libgobject-2.0.so.0 (0xb7956000)
        libgnomevfs-2.so.0 => /usr/lib/libgnomevfs-2.so.0 (0xb78fa000)
        libbonobo-2.so.0 => /usr/lib/libbonobo-2.so.0 (0xb78a2000)
        libgconf-2.so.4 => /usr/lib/libgconf-2.so.4 (0xb7871000)
        libbonobo-activation.so.4 => /usr/lib/libbonobo-activation.so.4 (0xb785c 000)
        libORBit-2.so.0 => /usr/lib/libORBit-2.so.0 (0xb7809000)
        libgmodule-2.0.so.0 => /usr/lib/libgmodule-2.0.so.0 (0xb7805000)
        libgthread-2.0.so.0 => /usr/lib/libgthread-2.0.so.0 (0xb7800000)
        libglib-2.0.so.0 => /usr/lib/libglib-2.0.so.0 (0xb7783000)
        libgtkembedmoz.so => not found
        libxpcom.so => not found
        libplds4.so => /usr/lib/libplds4.so (0xb7780000)
        libplc4.so => /usr/lib/libplc4.so (0xb777b000)
        libnspr4.so => /usr/lib/libnspr4.so (0xb7747000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7736000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7733000)
        libstdc++.so.5 => /usr/lib/libstdc++.so.5 (0xb7679000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7658000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb752b000)
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb7520000)
        libgnome-keyring.so.0 => /usr/lib/libgnome-keyring.so.0 (0xb7515000)
        libjpeg.so.62 => /usr/lib/libjpeg.so.62 (0xb74f8000)
        libX11.so.6 => /usr/X11R6/lib/libX11.so.6 (0xb7433000)
        libesd.so.0 => /usr/lib/libesd.so.0 (0xb7429000)
        libaudiofile.so.0 => /usr/lib/libaudiofile.so.0 (0xb7405000)
        libfontconfig.so.1 => /usr/lib/libfontconfig.so.1 (0xb73dd000)
        libfreetype.so.6 => /usr/lib/libfreetype.so.6 (0xb7370000)
        libXrandr.so.2 => /usr/X11R6/lib/libXrandr.so.2 (0xb736c000)
        libXi.so.6 => /usr/X11R6/lib/libXi.so.6 (0xb7364000)
        libXinerama.so.1 => /usr/X11R6/lib/libXinerama.so.1 (0xb7361000)
        libXext.so.6 => /usr/X11R6/lib/libXext.so.6 (0xb7353000)
        libXft.so.2 => /usr/lib/libXft.so.2 (0xb7341000)
        libXcursor.so.1 => /usr/lib/libXcursor.so.1 (0xb7338000)
        libXrender.so.1 => /usr/lib/libXrender.so.1 (0xb7330000)
        libgnutls.so.11 => /usr/lib/libgnutls.so.11 (0xb72cc000)
        libresolv.so.2 => /lib/tls/i686/cmov/libresolv.so.2 (0xb72ba000)
        librt.so.1 => /lib/tls/i686/cmov/librt.so.1 (0xb72b3000)
        libORBitCosNaming-2.so.0 => /usr/lib/libORBitCosNaming-2.so.0 (0xb72ae00 0)
        /lib/ld-linux.so.2 => /lib/ld-linux.so.2 (0x80000000)
        libasound.so.2 => /usr/lib/libasound.so.2 (0xb7204000)
        libexpat.so.1 => /usr/lib/libexpat.so.1 (0xb71e3000)
        libtasn1.so.2 => /usr/lib/libtasn1.so.2 (0xb71d3000)
        libgcrypt.so.11 => /usr/lib/libgcrypt.so.11 (0xb7189000)
        libgpg-error.so.0 => /usr/lib/libgpg-error.so.0 (0xb7185000)
        libnsl.so.1 => /lib/tls/i686/cmov/libnsl.so.1 (0xb7171000)
``` 

When i install Blam from Backport Staging

```
mario@ubuntu:~/Software/blam-1.8.0$ ldd /usr/lib/blam/libblam.so.0.0.0
                libgnomeui-2.so.0 => /usr/lib/libgnomeui-2.so.0 (0xb7f4f000)
        libSM.so.6 => /usr/X11R6/lib/libSM.so.6 (0xb7f46000)
        libICE.so.6 => /usr/X11R6/lib/libICE.so.6 (0xb7f2d000)
        libbonoboui-2.so.0 => /usr/lib/libbonoboui-2.so.0 (0xb7ed1000)
        libxml2.so.2 => /usr/lib/libxml2.so.2 (0xb7dd2000)
        libz.so.1 => /usr/lib/libz.so.1 (0xb7dc1000)
        libgnomecanvas-2.so.0 => /usr/lib/libgnomecanvas-2.so.0 (0xb7d98000)
        libgnome-2.so.0 => /usr/lib/libgnome-2.so.0 (0xb7d83000)
        libpopt.so.0 => /lib/libpopt.so.0 (0xb7d7a000)
        libart_lgpl_2.so.2 => /usr/lib/libart_lgpl_2.so.2 (0xb7d65000)
        libpangoft2-1.0.so.0 => /usr/lib/libpangoft2-1.0.so.0 (0xb7d40000)
        libgtk-x11-2.0.so.0 => /usr/lib/libgtk-x11-2.0.so.0 (0xb7a7b000)
        libgdk-x11-2.0.so.0 => /usr/lib/libgdk-x11-2.0.so.0 (0xb7a01000)
        libatk-1.0.so.0 => /usr/lib/libatk-1.0.so.0 (0xb79e5000)
        libgdk_pixbuf-2.0.so.0 => /usr/lib/libgdk_pixbuf-2.0.so.0 (0xb79cf000)
        libpangoxft-1.0.so.0 => /usr/lib/libpangoxft-1.0.so.0 (0xb79c8000)
        libpangox-1.0.so.0 => /usr/lib/libpangox-1.0.so.0 (0xb79bd000)
        libpango-1.0.so.0 => /usr/lib/libpango-1.0.so.0 (0xb7986000)
        libgobject-2.0.so.0 => /usr/lib/libgobject-2.0.so.0 (0xb7955000)
        libgnomevfs-2.so.0 => /usr/lib/libgnomevfs-2.so.0 (0xb78f9000)
        libbonobo-2.so.0 => /usr/lib/libbonobo-2.so.0 (0xb78a1000)
        libgconf-2.so.4 => /usr/lib/libgconf-2.so.4 (0xb7870000)
        libbonobo-activation.so.4 => /usr/lib/libbonobo-activation.so.4 (0xb785b000)
        libORBit-2.so.0 => /usr/lib/libORBit-2.so.0 (0xb7808000)
        libgmodule-2.0.so.0 => /usr/lib/libgmodule-2.0.so.0 (0xb7804000)
        libgthread-2.0.so.0 => /usr/lib/libgthread-2.0.so.0 (0xb77ff000)
        libglib-2.0.so.0 => /usr/lib/libglib-2.0.so.0 (0xb7782000)
        libgtkembedmoz.so => not found
        libxpcom.so => not found
        libplds4.so => /usr/lib/libplds4.so (0xb777f000)
        libplc4.so => /usr/lib/libplc4.so (0xb777a000)
        libnspr4.so => /usr/lib/libnspr4.so (0xb7746000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7742000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7732000)
        libstdc++.so.5 => /usr/lib/libstdc++.so.5 (0xb7678000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7657000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb752a000)
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb751f000)
        libgnome-keyring.so.0 => /usr/lib/libgnome-keyring.so.0 (0xb7514000)
        libjpeg.so.62 => /usr/lib/libjpeg.so.62 (0xb74f7000)
        libX11.so.6 => /usr/X11R6/lib/libX11.so.6 (0xb7432000)
        libesd.so.0 => /usr/lib/libesd.so.0 (0xb7428000)
        libaudiofile.so.0 => /usr/lib/libaudiofile.so.0 (0xb7404000)
        libfontconfig.so.1 => /usr/lib/libfontconfig.so.1 (0xb73dc000)
        libfreetype.so.6 => /usr/lib/libfreetype.so.6 (0xb736f000)
        libXrandr.so.2 => /usr/X11R6/lib/libXrandr.so.2 (0xb736b000)
        libXi.so.6 => /usr/X11R6/lib/libXi.so.6 (0xb7363000)
        libXinerama.so.1 => /usr/X11R6/lib/libXinerama.so.1 (0xb7360000)
        libXext.so.6 => /usr/X11R6/lib/libXext.so.6 (0xb7352000)
```

---

### Post by Slo Mo Snail on 2005-06-05
Looks like a missing dependency... either install mozilla (not firefox) or wait until I've created a blam package linked against firefox

---

### Post by Slo Mo Snail on 2005-06-05
Uploaded to staging... please try blam_1.8.0-0ubuntu4~5.04ubp2_i386.deb

When it works as expected I'll upload the ppc version later

---

### Post by Majlo on 2005-06-05
[QUOTE=Slo Mo Snail]Uploaded to staging... please try blam_1.8.0-0ubuntu4~5.04ubp2_i386.deb

When it works as expected I'll upload the ppc version later[/QUOTE]

Great work Slo Mo Snail :-)
Blam working perfect now...
Thank you so much

---

