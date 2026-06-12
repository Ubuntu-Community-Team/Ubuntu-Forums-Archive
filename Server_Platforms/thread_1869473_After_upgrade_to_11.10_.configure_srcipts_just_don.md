---
title: "After upgrade to 11.10 ./configure srcipts just don't work any more..."
date: 2011-10-25
forum: Server Platforms
---

### Post by andros144 on 2011-10-25
I use to have a V Server which i upgraded to the newest Ubuntu version, since then i CAN use cc or g++ to make simple bin's, but if i would like to build some app from souce with a configure script like nginx or with pecl it didn't find it's dependency's.


```

pecl install memcache-betadownloading memcache-3.0.6.tgz ... Starting to download memcache-3.0.6.tgz (54,717 bytes) .............done: 54,717 bytes 15 source files, building running: phpize Configuring for: PHP Api Version:         20090626 Zend Module Api No:      20090626 Zend Extension Api No:   220090626 Enable memcache session handler support? [yes] :  building in /tmp/pear/temp/pear-build-rootJYIDty/memcache-3.0.6 running: /tmp/pear/temp/memcache/configure --enable-memcache-session=yes checking for grep that handles long lines and -e... /bin/grep checking for egrep... /bin/grep -E checking for a sed that does not truncate output... /bin/sed checking for cc... cc checking whether the C compiler works... no configure: error: in `/tmp/pear/temp/pear-build-rootJYIDty/memcache-3.0.6': configure: error: C compiler cannot create executables See `config.log' for more details ERROR: `/tmp/pear/temp/memcache/configure --enable-memcache-session=yes' failed
``````
./configure --sbin-path=/usr/local/sbin --with-http_ssl_module --with-http_stub_status_module --add-module=/root/build/masterzen-nginx-upload-progress-module-3d8e105 --http-log-path=/var/log/nginx/access_log --error-log-path=/var/log/nginx/error_log --pid-path=/var/run/nginx.pid --http-client-body-temp-path=/var/tmp/nginx/client --http-proxy-temp-path=/var/tmp/nginx/proxy --http-fastcgi-temp-path=/var/tmp/nginx/fastcgi --with-md5-asm --with-md5=/usr/include --with-sha1-asm --with-sha1=/usr/include --with-http_ssl_module --with-http_perl_module --with-http_flv_module --without-mail_imap_module --without-mail_smtp_module --without-mail_pop3_module checking for OS  + Linux 3.0.0-12-server x86_64 checking for C compiler ... found  + using GNU C compiler checking for gcc builtin atomic operations ... not found checking for C99 variadic macros ... not found checking for gcc variadic macros ... not found checking for unistd.h ... found checking for inttypes.h ... found checking for limits.h ... found checking for sys/filio.h ... not found checking for sys/param.h ... found checking for sys/mount.h ... found checking for sys/statvfs.h ... found checking for crypt.h ... found checking for Linux specific features checking for epoll ... not found checking for sendfile() ... not found checking for sendfile64() ... not found checking for sys/prctl.h ... found checking for prctl(PR_SET_DUMPABLE) ... not found checking for sched_setaffinity() ... not found checking for crypt_r() ... not found checking for sys/vfs.h ... found checking for nobody group ... not found checking for nogroup group ... found checking for poll() ... not found checking for /dev/poll ... not found checking for kqueue ... not found checking for crypt() ... not found checking for crypt() in libcrypt ... not found checking for F_READAHEAD ... not found checking for posix_fadvise() ... not found checking for O_DIRECT ... not found checking for F_NOCACHE ... not found checking for directio() ... not found checking for statfs() ... not found checking for statvfs() ... not found checking for dlopen() ... not found checking for dlopen() in libdl ... not found checking for sched_yield() ... not found checking for sched_yield() in librt ... not found checking for SO_SETFIB ... not found checking for SO_ACCEPTFILTER ... not found checking for TCP_DEFER_ACCEPT ... not found checking for accept4() ... not found checking for int size ... ./configure: error: can not detect int size
```This is really strange to me because i have tested the upgrade process before on my test Server in VirtualBox. On the test Server all works fine and i can build  nginx, memcache or any other app from source wihtout any problems. 

My test server has nearly the same configuration like the production server, newest kernel, all upgrades installed. aptitude -f install or upgrade brings nothing new on both machines. Both run on amd64 arch. 

I have tested to purge and reinstall all what i can find related to package compiling like g++ gcc build-essential etc.
But nothing has changed...

Any help would be appreciated.

---

### Post by Demented ZA on 2011-10-26
I'm still young in the world of Linux, but if I look at the code snip you gave:
```

using GNU C compiler checking for gcc builtin atomic operations ... not found 
checking for C99 variadic macros ...                 not found 
checking for gcc variadic macros ...                 not found 
checking for unistd.h ...                     found 
checking for inttypes.h ...                     found 
checking for limits.h ...                     found 
checking for sys/filio.h ...                     not found 
checking for sys/param.h ...                     found 
checking for sys/mount.h ...                     found 
checking for sys/statvfs.h ...                     found 
checking for crypt.h ...                     found 
checking for Linux specific features checking for epoll ...     not found 
checking for sendfile() ...                    not found 
checking for sendfile64() ...                     not found 
checking for sys/prctl.h ...                     found 
checking for prctl(PR_SET_DUMPABLE) ...                not found 
checking for sched_setaffinity() ...                 not found 
checking for crypt_r() ...                     not found 
checking for sys/vfs.h ...                     found 
checking for nobody group ...                     not found 
checking for nogroup group ...                     found 
checking for poll() ...                     not found 
checking for /dev/poll ...                     not found 
checking for kqueue ...                     not found 
checking for crypt() ...                     not found 
checking for crypt() in libcrypt ...                 not found 
checking for F_READAHEAD ...                     not found 
checking for posix_fadvise() ...                 not found 
checking for O_DIRECT ...                     not found 
checking for F_NOCACHE ...                     not found 
checking for directio() ...                     not found 
checking for statfs() ...                     not found 
checking for statvfs() ...                     not found 
checking for dlopen() ...                     not found 
checking for dlopen() in libdl ...                not found 
checking for sched_yield() ...                     not found 
checking for sched_yield() in librt ...             not found 
checking for SO_SETFIB ...                     not found 
checking for SO_ACCEPTFILTER ...                 not found 
checking for TCP_DEFER_ACCEPT ...                not found 
checking for accept4() ...                     not found 
checking for int size ... ./configure: error: can not detect int size
```

Just broke the lines a bit. I'd say there's a lot more missing than the gcc related stuff. The problem seems to be a more fundemental one. You say that the upgrade in your VM worked fine? I'd say the upgrade on the live system didn't. Either that, or the hardware made a difference. Are your mount points exactly the same? Could just be that its looking in the wrong place.

---

### Post by andros144 on 2011-10-26
You are right, there's a lot more missing. But i just don't know how to solve it.
But the upgrade process on both system's was essentially the same, on both i had to do **aptitude -f install **in order to install left packages.
Here is a diff from **dpkg --get-sections **
```
]diff test-server live-server 
3d2
< apache2                        install
36d34
< btrfs-tools                    install
40c38
< byobu                        install
---
> byobu                        deinstall
43c41,43
< ca-certificates-java                install
---
> ca-certificates-java                deinstall
> checkinstall                    deinstall
> chkconfig                    install
45a46
> cli-common                    install
54c55
< consolekit                    install
---
> consolekit                    deinstall
64a66
> db5.1-util                    install
72,73d73
< default-jre                    install
< default-jre-headless                install
87a88
> dovecot-managesieved                install
89a91,92
> dovecot-postfix                    install
> dovecot-sieve                    install
104,105d106
< firefox-locale-de                install
< firefox-locale-en                install
122,123c123
< gcj-4.4-base                    install
< gcj-4.4-jre-lib                    install
---
> gcc-4.6-base:i386                install
140a141
> grub                        deinstall
154c155,157
< icedtea-6-jre-cacao                install
---
> ia32-libs                    deinstall
> ice34-translators                install
> icedtea-netx                    deinstall
182,185d184
< language-pack-de                install
< language-pack-de-base                install
< language-pack-en                install
< language-pack-en-base                install
189,190c188,196
< libaccess-bridge-java                install
< libaccess-bridge-java-jni            install
---
> lib32asound2                    deinstall
> lib32ffi6                    deinstall
> lib32gcc1                    deinstall
> lib32ncurses5                    deinstall
> lib32ncursesw5                    deinstall
> lib32tinfo5                    deinstall
> lib32v4l-0                    deinstall
> lib32z1                        deinstall
> libaccess-bridge-java-jni            deinstall
192a199
> libacl1:i386                    deinstall
196a204
> libapache2-mod-wsgi                deinstall
210c218
< libasyncns0                    install
---
> libasyncns0                    deinstall
214a223,224
> libattr1:i386                    deinstall
> libaudio2                    install
215a226
> libavahi-client3:i386                deinstall
216a228
> libavahi-common-data:i386            install
217a230
> libavahi-common3:i386                deinstall
230,232c243,244
< libbcmail-java                    install
< libbcmail-java-gcj                install
< libbcprov-java                    install
---
> libbcmail-java-gcj                deinstall
> libbcprov-java                    deinstall
243a256
> libc6:i386                    deinstall
244a258
> libc6-i386                    deinstall
249c263
< libck-connector0                install
---
> libck-connector0                deinstall
253a268
> libcomerr2:i386                    deinstall
257a273
> libcups2:i386                    deinstall
258a275
> libcupsimage2:i386                deinstall
259a277
> libcurl3:i386                    deinstall
265a284
> libdb4.8-java-gcj                deinstall
266a286,287
> libdb5.1:i386                    deinstall
> libdb5.1++                    deinstall
269a291
> libdbus-1-3:i386                deinstall
274d295
< libdigest-sha1-perl                install
280a302
> libdrm-intel1:i386                deinstall
282a305
> libdrm-nouveau1a:i386                deinstall
283a307
> libdrm-radeon1:i386                deinstall
284a309
> libdrm2:i386                    deinstall
295a321,322
> libexpat1:i386                    deinstall
> libexpat1-dev                    install
297a325
> libffi6:i386                    deinstall
299c327
< libflac8                    install
---
> libflac8                    deinstall
301a330
> libfontconfig1:i386                deinstall
303a333,335
> libfreetype6:i386                deinstall
> libfreeze33                    deinstall
> libfreeze34                    deinstall
308c340
< libgcj-bc                    install
---
> libgcc1:i386                    deinstall
310c342
< libgcj10                    install
---
> libgcj10                    deinstall
313a346
> libgcrypt11:i386                deinstall
316a350
> libgdbm3:i386                    deinstall
320c354
< libgif4                        install
---
> libgif4                        deinstall
324a359,361
> libgl1-mesa-glx:i386                deinstall
> libglacier2-33                    deinstall
> libglacier2-34                    deinstall
325a363
> libglapi-mesa:i386                deinstall
326a365,366
> libglib2.0-0:i386                deinstall
> libglib2.0-data                    install
330,332d369
< libgnuinet-java                    install
< libgnujaf-java                    install
< libgnumail-java                    install
334a372
> libgnutls26:i386                deinstall
338a377
> libgpg-error0:i386                deinstall
346a386
> libgssapi-krb5-2:i386                deinstall
364a405,415
> libice6:i386                    deinstall
> libicebox33                    deinstall
> libicebox34                    deinstall
> libicedb34                    deinstall
> libicegrid33                    deinstall
> libicegrid34                    deinstall
> libicepatch2-33                    deinstall
> libicepatch2-34                    deinstall
> libicessl33                    deinstall
> libicestorm33                    deinstall
> libicestorm34                    deinstall
366a418,419
> libicexml33                    deinstall
> libicexml34                    deinstall
369a423
> libidn11:i386                    deinstall
380,381c434
< libitext-java                    install
< libitext-java-gcj                install
---
> libitext-java-gcj                deinstall
383a437
> libjaxp1.3-java                    install
387d440
< libjpeg8                    install
390c443
< libjson0                    install
---
> libjson0                    deinstall
391a445
> libk5crypto3:i386                deinstall
399a454
> libkeyutils1:i386                deinstall
401a457
> libkrb5-3:i386                    deinstall
403a460
> libkrb5support0:i386                deinstall
405a463
> liblcms1:i386                    deinstall
406a465
> libldap-2.4-2:i386                deinstall
409a469
> libllvm2.9:i386                    deinstall
430a491
> libmemcache0                    install
431a493
> libmemcached5                    deinstall
433a496
> libmemcachedutil0                deinstall
436a500,501
> libmng1                        install
> libmng1:i386                    deinstall
455c520
< libnspr4-0d                    install
---
> libnspr4:i386                    deinstall
457a523
> libnss3:i386                    deinstall
465,466d530
< libossp-uuid16                    install
< libpam-ck-connector                install
481a546
> libpciaccess0:i386                deinstall
483a549
> libpcre3:i386                    deinstall
487a554
> libphp-jpgraph                    install
489a557
> libpkcs11-helper1                deinstall
492a561
> libpng12-0:i386                    deinstall
503c572
< libpq5                        install
---
> libpq5                        deinstall
507c576
< libpulse0                    install
---
> libpulse0                    deinstall
509c578
< libpython2.6                    install
---
> libpython2.6                    deinstall
512a582,586
> libqt4-dbus:i386                deinstall
> libqt4-declarative                deinstall
> libqt4-declarative:i386                deinstall
> libqt4-designer                    deinstall
> libqt4-designer:i386                deinstall
513a588,596
> libqt4-network:i386                deinstall
> libqt4-opengl                    deinstall
> libqt4-opengl:i386                deinstall
> libqt4-qt3support                deinstall
> libqt4-qt3support:i386                deinstall
> libqt4-script                    deinstall
> libqt4-script:i386                deinstall
> libqt4-scripttools                deinstall
> libqt4-scripttools:i386                deinstall
514a598
> libqt4-sql:i386                    deinstall
516a601,604
> libqt4-svg                    deinstall
> libqt4-svg:i386                    deinstall
> libqt4-test                    install
> libqt4-test:i386                deinstall
517a606,608
> libqt4-xml:i386                    deinstall
> libqt4-xmlpatterns                deinstall
> libqt4-xmlpatterns:i386                deinstall
518a610,612
> libqtcore4:i386                    deinstall
> libqtgui4                    deinstall
> libqtgui4:i386                    deinstall
527a622
> librtmp0:i386                    deinstall
529a625
> libsasl2-2:i386                    deinstall
534a631
> libselinux1:i386                deinstall
539a637
> libslp1                        deinstall
541c639,640
< libsndfile1                    install
---
> libsm6:i386                    deinstall
> libsndfile1                    deinstall
543c642
< libsqlite0                    install
---
> libsqlite0                    deinstall
544a644
> libsqlite3-0:i386                deinstall
549a650
> libssl1.0.0:i386                deinstall
550a652
> libstdc++6:i386                    deinstall
559c661
< libtalloc2                    install
---
> libtalloc2                    deinstall
560a663
> libtasn1-3:i386                    deinstall
569a673
> libtiff4:i386                    deinstall
580c684,685
< libv4l-0                    install
---
> libuuid1:i386                    deinstall
> libv4l-0                    deinstall
589a695
> libx11-6:i386                    deinstall
591c697
< libx11-xcb1                    install
---
> libx11-xcb1                    deinstall
594a701
> libxau6:i386                    deinstall
600a708
> libxcb1:i386                    deinstall
603a712
> libxdamage1:i386                deinstall
605c714,715
< libxdot4                    install
---
> libxdmcp6:i386                    deinstall
> libxdot4                    deinstall
606a717
> libxext6:i386                    deinstall
607a719
> libxfixes3:i386                    deinstall
610a723
> libxi6:i386                    deinstall
623a737
> libxrender1:i386                deinstall
625a740,741
> libxss1                        install
> libxss1:i386                    deinstall
626a743
> libxt6:i386                    deinstall
630a748
> libxxf86vm1:i386                deinstall
633a752
> lilo                        install
638a758,762
> linux-image-2.6.35-23-server            deinstall
> linux-image-2.6.35-24-server            deinstall
> linux-image-2.6.35-25-server            deinstall
> linux-image-2.6.35-27-server            deinstall
> linux-image-2.6.35-28-server            deinstall
644d767
< linux-server                    install
656a780
> mail-stack-delivery                install
663d786
< mbr                        install
672a796
> mono-runtime                    deinstall
692a817
> nginx                        deinstall
697,699c822,823
< openjdk-6-jre                    install
< openjdk-6-jre-headless                install
< openjdk-6-jre-lib                install
---
> openjdk-6-jre                    deinstall
> openjdk-6-jre-headless                deinstall
712a837,838
> php-mail-mime                    install
> php-mail-mimedecode                install
714a841
> php5                        install
726c853
< php5-memcache                    deinstall
---
> php5-memcached                    install
737a865
> portmap                        deinstall
740,742d867
< postgresql-client-8.4                install
< postgresql-client-9.1                install
< postgresql-client-common            install
758c883,884
< python-django                    deinstall
---
> python-dev                    install
> python-django                    install
766d891
< python-newt                    install
775d899
< python2.6-dev                    install
777a902
> python2.7-dev                    install
792a918
> sasl2-bin                    deinstall
801d926
< sqlite                        install
868a994
> zlib1g:i386                    deinstall

```mtab Test-Server
```
cat /etc/mtab 
/dev/sda6 / ext4 rw 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev devtmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0
none /run/lock tmpfs rw,noexec,nosuid,nodev,size=5242880 0 0
none /run/shm tmpfs rw,nosuid,nodev 0 0
/dev/sda1 /boot ext2 rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0

```Live Server:
```

 cat /etc/mtab
/dev/sda3 / ext3 rw 0 0
proc /proc proc rw 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev devtmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0
none /run/lock tmpfs rw,noexec,nosuid,nodev,size=5242880 0 0
none /run/shm tmpfs rw,nosuid,nodev 0 0
/dev/sda2 /boot ext3 rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0

```I have even build a nginx version on the Test System and copied it to the Live System and i runs without any problem.

---

### Post by Demented ZA on 2011-10-26
Of the mount points you listed, there are four differences, two of which shouldn't cause a problem. The other two, might also not be a problem, but I don't know what impact the differences will have:
```
proc /proc proc rw 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0

devpts /dev/pts devpts rw,gid=5,mode=620 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0

```

To recap, if we could verify that the components that are "not found" are infact there, I think we could really shed some light on the problem. With the information you have given, I have a hunch they are (because you even re-installed them).

I still think the answer to your question will lie in the answer as to why does it work virtually, but not on the physical machine.

With the above in mind, assuming that the packages are there, tho only thing I can think of is that mounts differ, because thats the only difference that can have this effect as far as I can think.

Or is my logic wrong?

---

