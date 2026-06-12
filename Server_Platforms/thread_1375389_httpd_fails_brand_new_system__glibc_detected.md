---
title: "httpd fails brand new system: *** glibc detected ***"
date: 2010-01-07
forum: Server Platforms
---

### Post by xbaez on 2010-01-07
Thu Jan 07 12:25:29 2010] [error] [client 79.17.5.236] File does not exist: /home/site/public_html/skins/games/1463b.jpg, referer: [http://site/index.php?file_id=45360](http://site/index.php?file_id=45360)
*** glibc detected *** /usr/sbin/apache2: double free or corruption (fasttop): 0x00007f5452ece020 ***

Here is the complete error from error_log:
```
Thu Jan 07 12:25:29 2010] [error] [client 79.17.5.236] File does not exist: /home/site/public_html/skins/games/1463b.jpg, referer: http://site/index.php?file_id=45360
*** glibc detected *** /usr/sbin/apache2: double free or corruption (fasttop): 0x00007f5452ece020 ***
======= Backtrace: =========
/lib/libc.so.6[0x7f544fdbfdd6]
/lib/libc.so.6(cfree+0x6c)[0x7f544fdc470c]
/usr/lib/apache2/modules/libphp5.so[0x7f544cb0cf9b]
/usr/lib/apache2/modules/libphp5.so[0x7f544ca31302]
/usr/lib/apache2/modules/libphp5.so(zend_error_noreturn+0x5dc)[0x7f544cb4fc9c]
/lib/libc.so.6[0x7f544fd7d530]
/lib/libc.so.6(strlen+0x3f)[0x7f544fdc93ef]
/lib/libc.so.6(__strdup+0x16)[0x7f544fdc9116]
/usr/lib/apache2/modules/libphp5.so[0x7f544cb0cd77]
/usr/lib/apache2/modules/libphp5.so[0x7f544ca31302]
/usr/lib/apache2/modules/libphp5.so(zend_error_noreturn+0x5dc)[0x7f544cb4fc9c]
/usr/lib/apache2/modules/libphp5.so(zend_fetch_resource+0x160)[0x7f544cb5d9b0]
/usr/lib/apache2/modules/libphp5.so(zif_fgets+0xaa)[0x7f544ca9d24a]
/usr/lib/apache2/modules/libphp5.so[0x7f544cb778db]
/usr/lib/apache2/modules/libphp5.so(execute+0x18c)[0x7f544cb735fc]
/usr/lib/apache2/modules/libphp5.so(zend_execute_scripts+0x166)[0x7f544cb4f4d6]
/usr/lib/apache2/modules/libphp5.so(php_execute_script+0x193)[0x7f544cb0a563]
/usr/lib/apache2/modules/libphp5.so[0x7f544cbc148d]
/usr/sbin/apache2(ap_run_handler+0x70)[0x7f5450bbf0d0]
/usr/sbin/apache2(ap_invoke_handler+0x98)[0x7f5450bc2a18]
/usr/sbin/apache2(ap_process_request+0x1c8)[0x7f5450bd0578]
/usr/sbin/apache2[0x7f5450bcd458]
/usr/sbin/apache2(ap_run_process_connection+0x68)[0x7f5450bc6c68]
/usr/sbin/apache2[0x7f5450bd4fcb]
/usr/sbin/apache2[0x7f5450bd529a]
/usr/sbin/apache2(ap_mpm_run+0xc24)[0x7f5450bd5f24]
/usr/sbin/apache2(main+0xb40)[0x7f5450bab350]
/lib/libc.so.6(__libc_start_main+0xfd)[0x7f544fd68abd]
/usr/sbin/apache2[0x7f5450baa2e9]
======= Memory map: ========
7f543c000000-7f543c021000 rw-p 00000000 00:00 0
7f543c021000-7f5440000000 ---p 00000000 00:00 0
7f5441c35000-7f5441c4b000 r-xp 00000000 08:05 24199                      /lib/libgcc_s.so.1
7f5441c4b000-7f5441e4a000 ---p 00016000 08:05 24199                      /lib/libgcc_s.so.1
7f5441e4a000-7f5441e4b000 r--p 00015000 08:05 24199                      /lib/libgcc_s.so.1
7f5441e4b000-7f5441e4c000 rw-p 00016000 08:05 24199                      /lib/libgcc_s.so.1
7f5441e4c000-7f5441e4d000 ---p 00000000 00:00 0
7f5441e4d000-7f544264d000 rw-p 00000000 00:00 0
7f544264d000-7f5442685000 r-xp 00000000 08:05 12969                      /usr/lib/libxslt.so.1.1.24
7f5442685000-7f5442884000 ---p 00038000 08:05 12969                      /usr/lib/libxslt.so.1.1.24
7f5442884000-7f5442885000 r--p 00037000 08:05 12969                      /usr/lib/libxslt.so.1.1.24
7f5442885000-7f5442886000 rw-p 00038000 08:05 12969                      /usr/lib/libxslt.so.1.1.24
7f5442886000-7f5442899000 r-xp 00000000 08:05 12968                      /usr/lib/libexslt.so.0.8.13
7f5442899000-7f5442a98000 ---p 00013000 08:05 12968                      /usr/lib/libexslt.so.0.8.13
7f5442a98000-7f5442a99000 r--p 00012000 08:05 12968                      /usr/lib/libexslt.so.0.8.13
7f5442a99000-7f5442a9a000 rw-p 00013000 08:05 12968                      /usr/lib/libexslt.so.0.8.13
7f5442a9a000-7f5442aa1000 r-xp 00000000 08:05 114906                     /usr/lib/php5/20060613/xsl.so
7f5442aa1000-7f5442ca0000 ---p 00007000 08:05 114906                     /usr/lib/php5/20060613/xsl.so
7f5442ca0000-7f5442ca1000 r--p 00006000 08:05 114906                     /usr/lib/php5/20060613/xsl.so
7f5442ca1000-7f5442ca2000 rw-p 00007000 08:05 114906                     /usr/lib/php5/20060613/xsl.so
7f5442ca2000-7f5442ca9000 r-xp 00000000 08:05 114905                     /usr/lib/php5/20060613/pdo_mysql.so
7f5442ca9000-7f5442ea8000 ---p 00007000 08:05 114905                     /usr/lib/php5/20060613/pdo_mysql.so
7f5442ea8000-7f5442ea9000 r--p 00006000 08:05 114905                     /usr/lib/php5/20060613/pdo_mysql.so
7f5442ea9000-7f5442eaa000 rw-p 00007000 08:05 114905                     /usr/lib/php5/20060613/pdo_mysql.so
7f5442eaa000-7f5442ec0000 r-xp 00000000 08:05 114673                     /usr/lib/php5/20060613/pdo.so
7f5442ec0000-7f54430bf000 ---p 00016000 08:05 114673                     /usr/lib/php5/20060613/pdo.so
7f54430bf000-7f54430c0000 r--p 00015000 08:05 114673                     /usr/lib/php5/20060613/pdo.so
7f54430c0000-7f54430c3000 rw-p 00016000 08:05 114673                     /usr/lib/php5/20060613/pdo.so
7f54430c3000-7f54430de000 r-xp 00000000 08:05 114904                     /usr/lib/php5/20060613/mysqli.so
7f54430de000-7f54432dd000 ---p 0001b000 08:05 114904                     /usr/lib/php5/20060613/mysqli.so
7f54432dd000-7f54432de000 r--p 0001a000 08:05 114904                     /usr/lib/php5/20060613/mysqli.so
7f54432de000-7f54432e1000 rw-p 0001b000 08:05 114904                     /usr/lib/php5/20060613/mysqli.so
7f54432e1000-7f54434a7000 r-xp 00000000 08:05 12769                      /usr/lib/libmysqlclient_r.so.16.0.0
7f54434a7000-7f54436a7000 ---p 001c6000 08:05 12769                      /usr/lib/libmysqlclient_r.so.16.0.0
7f54436a7000-7f54436ac000 r--p 001c6000 08:05 12769                      /usr/lib/libmysqlclient_r.so.16.0.0
7f54436ac000-7f54436f6000 rw-p 001cb000 08:05 12769                      /usr/lib/libmysqlclient_r.so.16.0.0
7f54436f6000-7f54436f7000 rw-p 00000000 00:00 0
7f54436f7000-7f5443703000 r-xp 00000000 08:05 114903                     /usr/lib/php5/20060613/mysql.so
7f5443703000-7f5443902000 ---p 0000c000 08:05 114903                     /usr/lib/php5/20060613/mysql.so
7f5443902000-7f5443903000 r--p 0000b000 08:05 114903                     /usr/lib/php5/20060613/mysql.so
7f5443903000-7f5443904000 rw-p 0000c000 08:05 114903                     /usr/lib/php5/20060613/mysql.so
7f5443904000-7f5443905000 rw-p 00000000 00:00 0
7f5443905000-7f544390d000 r-xp 00000000 08:05 13041                      /usr/lib/libltdl.so.7.2.0
7f544390d000-7f5443b0d000 ---p 00008000 08:05 13041                      /usr/lib/libltdl.so.7.2.0
7f5443b0d000-7f5443b0e000 r--p 00008000 08:05 13041                      /usr/lib/libltdl.so.7.2.0
7f5443b0e000-7f5443b0f000 rw-p 00009000 08:05 13041                      /usr/lib/libltdl.so.7.2.0
7f5443b0f000-7f5443b39000 r-xp 00000000 08:05 14201                      /usr/lib/libmcrypt.so.4.4.8
7f5443b39000-7f5443d39000 ---p 0002a000 08:05 14201                      /usr/lib/libmcrypt.so.4.4.8
7f5443d39000-7f5443d3b000 r--p 0002a000 08:05 14201                      /usr/lib/libmcrypt.so.4.4.8
7f5443d3b000-7f5443d3d000 rw-p 0002c000 08:05 14201                      /usr/lib/libmcrypt.so.4.4.8
7f5443d3d000-7f5443d42000 rw-p 00000000 00:00 0
7f5443d42000-7f5443d4b000 r-xp 00000000 08:05 116640                     /usr/lib/php5/20060613/mcrypt.so
7f5443d4b000-7f5443f4a000 ---p 00009000 08:05 116640                     /usr/lib/php5/20060613/mcrypt.so
7f5443f4a000-7f5443f4b000 r--p 00008000 08:05 116640                     /usr/lib/php5/20060613/mcrypt.so
7f5443f4b000-7f5443f4c000 rw-p 00009000 08:05 116640                     /usr/lib/php5/20060613/mcrypt.so
7f5443f4c000-7f5443f50000 r-xp 00000000 08:05 116689                     /usr/lib/php5/20060613/geoip.so
7f5443f50000-7f544414f000 ---p 00004000 08:05 116689                     /usr/lib/php5/20060613/geoip.so
7f544414f000-7f5444150000 r--p 00003000 08:05 116689                     /usr/lib/php5/20060613/geoip.so
7f5444150000-7f5444151000 rw-p 00004000 08:05 116689                     /usr/lib/php5/20060613/geoip.so
7f5444151000-7f5444156000 r-xp 00000000 08:05 11700                      /usr/lib/libXdmcp.so.6.0.0
7f5444156000-7f5444355000 ---p 00005000 08:05 11700                      /usr/lib/libXdmcp.so.6.0.0
7f5444355000-7f5444356000 rw-p 00004000 08:05 11700                      /usr/lib/libXdmcp.so.6.0.0
7f5444356000-7f5444358000 r-xp 00000000 08:05 11698                      /usr/lib/libXau.so.6.0.0
7f5444358000-7f5444557000 ---p 00002000 08:05 11698                      /usr/lib/libXau.so.6.0.0
7f5444557000-7f5444558000 r--p 00001000 08:05 11698                      /usr/lib/libXau.so.6.0.0
7f5444558000-7f5444559000 rw-p 00002000 08:05 11698                      /usr/lib/libXau.so.6.0.0
7f5444559000-7f5444574000 r-xp 00000000 08:05 11702                      /usr/lib/libxcb.so.1.1.0
7f5444574000-7f5444773000 ---p 0001b000 08:05 11702                      /usr/lib/libxcb.so.1.1.0
7f5444773000-7f5444774000 r--p 0001a000 08:05 11702                      /usr/lib/libxcb.so.1.1.0
7f5444774000-7f5444775000 rw-p 0001b000 08:05 11702                      /usr/lib/libxcb.so.1.1.0
7f5444775000-7f54447a5000 r-xp 00000000 08:05 12952                      /usr/lib/libfontconfig.so.1.3.0
7f54447a5000-7f54449a5000 ---p 00030000 08:05 12952                      /usr/lib/libfontconfig.so.1.3.0
7f54449a5000-7f54449a6000 r--p 00030000 08:05 12952                      /usr/lib/libfontconfig.so.1.3.0
7f54449a6000-7f54449a7000 rw-p 00031000 08:05 12952                      /usr/lib/libfontconfig.so.1.3.0
7f54449a7000-7f54449ca000 r-xp 00000000 08:05 12954                      /usr/lib/libjpeg.so.62.0.0
7f54449ca000-7f5444bca000 ---p 00023000 08:05 12954                      /usr/lib/libjpeg.so.62.0.0
7f5444bca000-7f5444bcb000 r--p 00023000 08:05 12954                      /usr/lib/libjpeg.so.62.0.0
7f5444bcb000-7f5444bcc000 rw-p 00024000 08:05 12954                      /usr/lib/libjpeg.so.62.0.0
7f5444bcc000-7f5444bf1000 r-xp 00000000 08:05 12957                      /usr/lib/libpng12.so.0.37.0
7f5444bf1000-7f5444df1000 ---p 00025000 08:05 12957                      /usr/lib/libpng12.so.0.37.0
7f5444df1000-7f5444df2000 r--p 00025000 08:05 12957                      /usr/lib/libpng12.so.0.37.0
7f5444df2000-7f5444df3000 rw-p 00026000 08:05 12957                      /usr/lib/libpng12.so.0.37.0
7f5444df3000-7f5444e03000 r-xp 00000000 08:05 12959                      /usr/lib/libXpm.so.4.11.0
7f5444e03000-7f5445002000 ---p 00010000 08:05 12959                      /usr/lib/libXpm.so.4.11.0
7f5445002000-7f5445003000 r--p 0000f000 08:05 12959                      /usr/lib/libXpm.so.4.11.0
7f5445003000-7f5445004000 rw-p 00010000 08:05 12959                      /usr/lib/libXpm.so.4.11.0
7f5445004000-7f5445135000 r-xp 00000000 08:05 11704                      /usr/lib/libX11.so.6.2.0
7f5445135000-7f5445335000 ---p 00131000 08:05 11704                      /usr/lib/libX11.so.6.2.0
7f5445335000-7f5445336000 r--p 00131000 08:05 11704                      /usr/lib/libX11.so.6.2.0
7f5445336000-7f544533a000 rw-p 00132000 08:05 11704                      /usr/lib/libX11.so.6.2.0
7f544533a000-7f54453b9000 r-xp 00000000 08:05 11288                      /usr/lib/libfreetype.so.6.3.20
7f54453b9000-7f54455b9000 ---p 0007f000 08:05 11288                      /usr/lib/libfreetype.so.6.3.20
7f54455b9000-7f54455be000 r--p 0007f000 08:05 11288                      /usr/lib/libfreetype.so.6.3.20
7f54455be000-7f54455bf000 rw-p 00084000 08:05 11288                      /usr/lib/libfreetype.so.6.3.20
7f54455bf000-7f5445603000 r-xp 00000000 08:05 12964                      /usr/lib/libt1.so.5.1.2
7f5445603000-7f5445803000 ---p 00044000 08:05 12964                      /usr/lib/libt1.so.5.1.2
7f5445803000-7f5445804000 r--p 00044000 08:05 12964                      /usr/lib/libt1.so.5.1.2
7f5445804000-7f5445807000 rw-p 00045000 08:05 12964                      /usr/lib/libt1.so.5.1.2
7f5445807000-7f544581d000 rw-p 00000000 00:00 0
7f544581d000-7f544583f000 r-xp 00000000 08:05 12961                      /usr/lib/libgd.so.2.0.0
7f544583f000-7f5445a3e000 ---p 00022000 08:05 12961                      /usr/lib/libgd.so.2.0.0
7f5445a3e000-7f5445a3f000 r--p 00021000 08:05 12961                      /usr/lib/libgd.so.2.0.0
7f5445a3f000-7f5445a5f000 rw-p 00022000 08:05 12961                      /usr/lib/libgd.so.2.0.0
7f5445a5f000-7f5445a63000 rw-p 00000000 00:00 0
7f5445a63000-7f5445a7d000 r-xp 00000000 08:05 114902                     /usr/lib/php5/20060613/gd.so
7f5445a7d000-7f5445c7c000 ---p 0001a000 08:05 114902                     /usr/lib/php5/20060613/gd.so
7f5445c7c000-7f5445c7d000 r--p 00019000 08:05 114902                     /usr/lib/php5/20060613/gd.so
7f5445c7d000-7f5445c83000 rw-p 0001a000 08:05 114902                     /usr/lib/php5/20060613/gd.so
7f5445c83000-7f5445c88000 r-xp 00000000 08:05 13066                      /usr/lib/libogg.so.0.6.0
7f5445c88000-7f5445e87000 ---p 00005000 08:05 13066                      /usr/lib/libogg.so.0.6.0
7f5445e87000-7f5445e88000 r--p 00004000 08:05 13066                      /usr/lib/libogg.so.0.6.0
7f5445e88000-7f5445e89000 rw-p 00005000 08:05 13066                      /usr/lib/libogg.so.0.6.0
7f5445e89000-7f5445efb000 r-xp 00000000 08:05 13059                      /usr/lib/liboil-0.3.so.0.3.0
7f5445efb000-7f54460fb000 ---p 00072000 08:05 13059                      /usr/lib/liboil-0.3.so.0.3.0
7f54460fb000-7f54460fc000 r--p 00072000 08:05 13059                      /usr/lib/liboil-0.3.so.0.3.0
7f54460fc000-7f5446117000 rw-p 00073000 08:05 13059                      /usr/lib/liboil-0.3.so.0.3.0
7f5446117000-7f5446119000 rw-p 00000000 00:00 0
7f5446119000-7f5446138000 r-xp 00000000 08:05 13081                      /usr/lib/libvorbis.so.0.4.0
7f5446138000-7f5446337000 ---p 0001f000 08:05 13081                      /usr/lib/libvorbis.so.0.4.0
7f5446337000-7f5446338000 r--p 0001e000 08:05 13081                      /usr/lib/libvorbis.so.0.4.0
7f5446338000-7f5446346000 rw-p 0001f000 08:05 13081                      /usr/lib/libvorbis.so.0.4.0
7f5446346000-7f5446360000 r-xp 00000000 08:05 13083                      /usr/lib/libvorbisenc.so.2.0.3
7f5446360000-7f544655f000 ---p 0001a000 08:05 13083                      /usr/lib/libvorbisenc.so.2.0.3
7f544655f000-7f5446560000 r--p 00019000 08:05 13083                      /usr/lib/libvorbisenc.so.2.0.3
7f5446560000-7f5446720000 rw-p 0001a000 08:05 13083                      /usr/lib/libvorbisenc.so.2.0.3
7f5446720000-7f5446770000 r-xp 00000000 08:05 13068                      /usr/lib/libtheora.so.0.3.4
7f5446770000-7f544696f000 ---p 00050000 08:05 13068                      /usr/lib/libtheora.so.0.3.4
7f544696f000-7f5446970000 r--p 0004f000 08:05 13068                      /usr/lib/libtheora.so.0.3.4
7f5446970000-7f5446971000 rw-p 00050000 08:05 13068                      /usr/lib/libtheora.so.0.3.4
7f5446971000-7f5446989000 r-xp 00000000 08:05 13064                      /usr/lib/libspeex.so.1.5.0
7f5446989000-7f5446b89000 ---p 00018000 08:05 13064                      /usr/lib/libspeex.so.1.5.0
7f5446b89000-7f5446b8a000 r--p 00018000 08:05 13064                      /usr/lib/libspeex.so.1.5.0
7f5446b8a000-7f5446b8b000 rw-p 00019000 08:05 13064                      /usr/lib/libspeex.so.1.5.0
7f5446b8b000-7f5446c08000 r-xp 00000000 08:05 13062                      /usr/lib/libschroedinger-1.0.so.0.2.0
7f5446c08000-7f5446e07000 ---p 0007d000 08:05 13062                      /usr/lib/libschroedinger-1.0.so.0.2.0
7f5446e07000-7f5446e09000 r--p 0007c000 08:05 13062                      /usr/lib/libschroedinger-1.0.so.0.2.0
7f5446e09000-7f5446e0a000 rw-p 0007e000 08:05 13062                      /usr/lib/libschroedinger-1.0.so.0.2.0
7f5446e0a000-7f5446e16000 r-xp 00000000 08:05 13057                      /usr/lib/libgsm.so.1.0.12
7f5446e16000-7f5447016000 ---p 0000c000 08:05 13057                      /usr/lib/libgsm.so.1.0.12
7f5447016000-7f5447017000 r--p 0000c000 08:05 13057                      /usr/lib/libgsm.so.1.0.12
7f5447017000-7f5447018000 rw-p 0000d000 08:05 13057                      /usr/lib/libgsm.so.1.0.12
7f5447018000-7f5447023000 r-xp 00000000 08:05 13054                      /usr/lib/libavutil.so.49.15.0
7f5447023000-7f5447222000 ---p 0000b000 08:05 13054                      /usr/lib/libavutil.so.49.15.0
7f5447222000-7f5447223000 r--p 0000a000 08:05 13054                      /usr/lib/libavutil.so.49.15.0
7f5447223000-7f5447224000 rw-p 0000b000 08:05 13054                      /usr/lib/libavutil.so.49.15.0
7f5447224000-7f5447227000 rw-p 00000000 00:00 0
7f5447227000-7f544774c000 r-xp 00000000 08:05 13085                      /usr/lib/libavcodec.so.52.20.0
7f544774c000-7f544794c000 ---p 00525000 08:05 13085                      /usr/lib/libavcodec.so.52.20.0
7f544794c000-7f5447956000 r--p 00525000 08:05 13085                      /usr/lib/libavcodec.so.52.20.0
7f5447956000-7f5447963000 rw-p 0052f000 08:05 13085                      /usr/lib/libavcodec.so.52.20.0
7f5447963000-7f5447c73000 rw-p 00000000 00:00 0
7f5447c73000-7f5447d0f000 r-xp 00000000 08:05 13088                      /usr/lib/libavformat.so.52.31.0
7f5447d0f000-7f5447f0f000 ---p 0009c000 08:05 13088                      /usr/lib/libavformat.so.52.31.0
7f5447f0f000-7f5447f13000 r--p 0009c000 08:05 13088                      /usr/lib/libavformat.so.52.31.0
7f5447f13000-7f5447f1c000 rw-p 000a0000 08:05 13088                      /usr/lib/libavformat.so.52.31.0
7f5447f1c000-7f5447f68000 rw-p 00000000 00:00 0
7f5447f68000-7f5447f9b000 r-xp 00000000 08:05 13091                      /usr/lib/libswscale.so.0.7.1
7f5447f9b000-7f544819a000 ---p 00033000 08:05 13091                      /usr/lib/libswscale.so.0.7.1
7f544819a000-7f544819b000 r--p 00032000 08:05 13091                      /usr/lib/libswscale.so.0.7.1
7f544819b000-7f544819c000 rw-p 00033000 08:05 13091                      /usr/lib/libswscale.so.0.7.1
7f544819c000-7f54481a4000 r-xp 00000000 08:05 116688                     /usr/lib/php5/20060613/ffmpeg.so
7f54481a4000-7f54483a4000 ---p 00008000 08:05 116688                     /usr/lib/php5/20060613/ffmpeg.so
7f54483a4000-7f54483a5000 r--p 00008000 08:05 116688                     /usr/lib/php5/20060613/ffmpeg.so
7f54483a5000-7f54483a6000 rw-p 00009000 08:05 116688                     /usr/lib/php5/20060613/ffmpeg.so
7f54483a6000-7f54483a9000 r-xp 00000000 08:05 26060                      /lib/libgpg-error.so.0.4.0
7f54483a9000-7f54485a8000 ---p 00003000 08:05 26060                      /lib/libgpg-error.so.0.4.0
7f54485a8000-7f54485a9000 r--p 00002000 08:05 26060                      /lib/libgpg-error.so.0.4.0
7f54485a9000-7f54485aa000 rw-p 00003000 08:05 26060                      /lib/libgpg-error.so.0.4.0
7f54485aa000-7f544861f000 r-xp 00000000 08:05 26054                      /lib/libgcrypt.so.11.5.2
7f544861f000-7f544881e000 ---p 00075000 08:05 26054                      /lib/libgcrypt.so.11.5.2
7f544881e000-7f544881f000 r--p 00074000 08:05 26054                      /lib/libgcrypt.so.11.5.2
7f544881f000-7f5448822000 rw-p 00075000 08:05 26054                      /lib/libgcrypt.so.11.5.2
7f5448822000-7f5448832000 r-xp 00000000 08:05 10815                      /usr/lib/libtasn1.so.3.1.5
7f5448832000-7f5448a31000 ---p 00010000 08:05 10815                      /usr/lib/libtasn1.so.3.1.5
7f5448a31000-7f5448a32000 r--p 0000f000 08:05 10815                      /usr/lib/libtasn1.so.3.1.5
7f5448a32000-7f5448a33000 rw-p 00010000 08:05 10815                      /usr/lib/libtasn1.so.3.1.5
7f5448a33000-7f5448ace000 r-xp 00000000 08:05 10624                      /usr/lib/libgnutls.so.26.14.10
7f5448ace000-7f5448cce000 ---p 0009b000 08:05 10624                      /usr/lib/libgnutls.so.26.14.10
7f5448cce000-7f5448cd4000 r--p 0009b000 08:05 10624                      /usr/lib/libgnutls.so.26.14.10
7f5448cd4000-7f5448cd5000 rw-p 000a1000 08:05 10624                      /usr/lib/libgnutls.so.26.14.10
7f5448cd5000-7f5448cee000 r-xp 00000000 08:05 10558                      /usr/lib/libsasl2.so.2.0.23
7f5448cee000-7f5448eed000 ---p 00019000 08:05 10558                      /usr/lib/libsasl2.so.2.0.23
7f5448eed000-7f5448eee000 r--p 00018000 08:05 10558                      /usr/lib/libsasl2.so.2.0.23
7f5448eee000-7f5448eef000 rw-p 00019000 08:05 10558                      /usr/lib/libsasl2.so.2.0.23
7f5448eef000-7f5448f34000 r-xp 00000000 08:05 10788                      /usr/lib/libldap_r-2.4.so.2.5.1
7f5448f34000-7f5449133000 ---p 00045000 08:05 10788                      /usr/lib/libldap_r-2.4.so.2.5.1
7f5449133000-7f5449135000 r--p 00044000 08:05 10788                      /usr/lib/libldap_r-2.4.so.2.5.1
7f5449135000-7f5449136000 rw-p 00046000 08:05 10788                      /usr/lib/libldap_r-2.4.so.2.5.1
7f5449136000-7f5449138000 rw-p 00000000 00:00 0
7f5449138000-7f5449145000 r-xp 00000000 08:05 10787                      /usr/lib/liblber-2.4.so.2.5.1
7f5449145000-7f5449344000 ---p 0000d000 08:05 10787                      /usr/lib/liblber-2.4.so.2.5.1
7f5449344000-7f5449345000 r--p 0000c000 08:05 10787                      /usr/lib/liblber-2.4.so.2.5.1
7f5449345000-7f5449346000 rw-p 0000d000 08:05 10787                      /usr/lib/liblber-2.4.so.2.5.1
7f5449346000-7f5449377000 r-xp 00000000 08:05 10762                      /usr/lib/libidn.so.11.5.44
7f5449377000-7f5449577000 ---p 00031000 08:05 10762                      /usr/lib/libidn.so.11.5.44
7f5449577000-7f5449578000 r--p 00031000 08:05 10762                      /usr/lib/libidn.so.11.5.44
7f5449578000-7f5449579000 rw-p 00032000 08:05 10762                      /usr/lib/libidn.so.11.5.44
7f5449579000-7f54495be000 r-xp 00000000 08:05 13100                      /usr/lib/libcurl.so.4.1.1
7f54495be000-7f54497be000 ---p 00045000 08:05 13100                      /usr/lib/libcurl.so.4.1.1
7f54497be000-7f54497bf000 r--p 00045000 08:05 13100                      /usr/lib/libcurl.so.4.1.1
7f54497bf000-7f54497c0000 rw-p 00046000 08:05 13100                      /usr/lib/libcurl.so.4.1.1
7f54497c0000-7f54497ce000 r-xp 00000000 08:05 116736                     /usr/lib/php5/20060613/curl.so
7f54497ce000-7f54499cd000 ---p 0000e000 08:05 116736                     /usr/lib/php5/20060613/curl.so
7f54499cd000-7f54499ce000 r--p 0000d000 08:05 116736                     /usr/lib/php5/20060613/curl.so
7f54499ce000-7f54499cf000 rw-p 0000e000 08:05 116736                     /usr/lib/php5/20060613/curl.so

7f54499cf000-7f54499db000 r-xp 00000000 08:05 24170                      /lib/libnss_files-2.10.1.so
7f54499db000-7f5449bda000 ---p 0000c000 08:05 24170                      /lib/libnss_files-2.10.1.so
7f5449bda000-7f5449bdb000 r--p 0000b000 08:05 24170                      /lib/libnss_files-2.10.1.so
7f5449bdb000-7f5449bdc000 rw-p 0000c000 08:05 24170                      /lib/libnss_files-2.10.1.so
7f5449bdc000-7f5449be6000 r-xp 00000000 08:05 24172                      /lib/libnss_nis-2.10.1.so
7f5449be6000-7f5449de5000 ---p 0000a000 08:05 24172                      /lib/libnss_nis-2.10.1.so
7f5449de5000-7f5449de6000 r--p 00009000 08:05 24172                      /lib/libnss_nis-2.10.1.so
7f5449de6000-7f5449de7000 rw-p 0000a000 08:05 24172                      /lib/libnss_nis-2.10.1.so
7f5449de7000-7f5449dee000 r-xp 00000000 08:05 24168                      /lib/libnss_compat-2.10.1.so
7f5449dee000-7f5449fee000 ---p 00007000 08:05 24168                      /lib/libnss_compat-2.10.1.so
7f5449fee000-7f5449fef000 r--p 00007000 08:05 24168                      /lib/libnss_compat-2.10.1.so
7f5449fef000-7f5449ff0000 rw-p 00008000 08:05 24168                      /lib/libnss_compat-2.10.1.so
7f5449ff0000-7f5449ff4000 r-xp 00000000 08:05 114336                     /usr/lib/apache2/modules/mod_status.so
7f5449ff4000-7f544a1f4000 ---p 00004000 08:05 114336                     /usr/lib/apache2/modules/mod_status.so
7f544a1f4000-7f544a1f5000 r--p 00004000 08:05 114336                     /usr/lib/apache2/modules/mod_status.so
7f544a1f5000-7f544a1f6000 rw-p 00005000 08:05 114336                     /usr/lib/apache2/modules/mod_status.so
7f544a1f6000-7f544a1f9000 r-xp 00000000 08:05 114325                     /usr/lib/apache2/modules/mod_setenvif.so
7f544a1f9000-7f544a3f8000 ---p 00003000 08:05 114325                     /usr/lib/apache2/modules/mod_setenvif.so
7f544a3f8000-7f544a3f9000 r--p 00002000 08:05 114325                     /usr/lib/apache2/modules/mod_setenvif.so
7f544a3f9000-7f544a3fa000 rw-p 00003000 08:05 114325                     /usr/lib/apache2/modules/mod_setenvif.so
7f544a3fa000-7f544a408000 r-xp 00000000 08:05 114353                     /usr/lib/apache2/modules/mod_rewrite.so
7f544a408000-7f544a608000 ---p 0000e000 08:05 114353                     /usr/lib/apache2/modules/mod_rewrite.so
7f544a608000-7f544a609000 r--p 0000e000 08:05 114353                     /usr/lib/apache2/modules/mod_rewrite.so
7f544a609000-7f544a60a000 rw-p 0000f000 08:05 114353                     /usr/lib/apache2/modules/mod_rewrite.so
7f544a60a000-7f544a60c000 r-xp 00000000 08:05 25938                      /lib/libkeyutils-1.2.so
7f544a60c000-7f544a80b000 ---p 00002000 08:05 25938                      /lib/libkeyutils-1.2.so
7f544a80b000-7f544a80c000 r--p 00001000 08:05 25938                      /lib/libkeyutils-1.2.so
7f544a80c000-7f544a80d000 rw-p 00002000 08:05 25938                      /lib/libkeyutils-1.2.so
7f544a80d000-7f544a814000 r-xp 00000000 08:05 10742                      /usr/lib/libkrb5support.so.0.1
7f544a814000-7f544aa13000 ---p 00007000 08:05 10742                      /usr/lib/libkrb5support.so.0.1
7f544aa13000-7f544aa14000 r--p 00006000 08:05 10742                      /usr/lib/libkrb5support.so.0.1
7f544aa14000-7f544aa15000 rw-p 00007000 08:05 10742                      /usr/lib/libkrb5support.so.0.1
7f544aa15000-7f544ab75000 r-xp 00000000 08:05 24269                      /lib/libcrypto.so.0.9.8
7f544ab75000-7f544ad75000 ---p 00160000 08:05 24269                      /lib/libcrypto.so.0.9.8
7f544ad75000-7f544ad82000 r--p 00160000 08:05 24269                      /lib/libcrypto.so.0.9.8
7f544ad82000-7f544ad98000 rw-p 0016d000 08:05 24269                      /lib/libcrypto.so.0.9.8
7f544ad98000-7f544ad9c000 rw-p 00000000 00:00 0
7f544ad9c000-7f544aee0000 r-xp 00000000 08:05 10818                      /usr/lib/libxml2.so.2.7.5
7f544aee0000-7f544b0df000 ---p 00144000 08:05 10818                      /usr/lib/libxml2.so.2.7.5
7f544b0df000-7f544b0e7000 r--p 00143000 08:05 10818                      /usr/lib/libxml2.so.2.7.5
7f544b0e7000-7f544b0e9000 rw-p 0014b000 08:05 10818                      /usr/lib/libxml2.so.2.7.5
7f544b0e9000-7f544b0ea000 rw-p 00000000 00:00 0
7f544b0ea000-7f544b0ed000 r-xp 00000000 08:05 24152                      /lib/libcom_err.so.2.1
7f544b0ed000-7f544b2ec000 ---p 00003000 08:05 24152                      /lib/libcom_err.so.2.1
7f544b2ec000-7f544b2ed000 r--p 00002000 08:05 24152                      /lib/libcom_err.so.2.1
7f544b2ed000-7f544b2ee000 rw-p 00003000 08:05 24152                      /lib/libcom_err.so.2.1
7f544b2ee000-7f544b317000 r-xp 00000000 08:05 10737                      /usr/lib/libk5crypto.so.3.1
7f544b317000-7f544b516000 ---p 00029000 08:05 10737                      /usr/lib/libk5crypto.so.3.1
7f544b516000-7f544b518000 r--p 00028000 08:05 10737                      /usr/lib/libk5crypto.so.3.1
7f544b518000-7f544b519000 rw-p 0002a000 08:05 10737                      /usr/lib/libk5crypto.so.3.1
7f544b519000-7f544b5c7000 r-xp 00000000 08:05 10739                      /usr/lib/libkrb5.so.3.3
7f544b5c7000-7f544b7c7000 ---p 000ae000 08:05 10739                      /usr/lib/libkrb5.so.3.3
7f544b7c7000-7f544b7cf000 r--p 000ae000 08:05 10739                      /usr/lib/libkrb5.so.3.3
7f544b7cf000-7f544b7d1000 rw-p 000b6000 08:05 10739                      /usr/lib/libkrb5.so.3.3
7f544b7d1000-7f544b7fe000 r-xp 00000000 08:05 10735                      /usr/lib/libgssapi_krb5.so.2.2
7f544b7fe000-7f544b9fd000 ---p 0002d000 08:05 10735                      /usr/lib/libgssapi_krb5.so.2.2
7f544b9fd000-7f544b9fe000 r--p 0002c000 08:05 10735                      /usr/lib/libgssapi_krb5.so.2.2
7f544b9fe000-7f544b9ff000 rw-p 0002d000 08:05 10735                      /usr/lib/libgssapi_krb5.so.2.2
7f544b9ff000-7f544ba15000 r-xp 00000000 08:05 24167                      /lib/libnsl-2.10.1.so
7f544ba15000-7f544bc15000 ---p 00016000 08:05 24167                      /lib/libnsl-2.10.1.so
7f544bc15000-7f544bc16000 r--p 00016000 08:05 24167                      /lib/libnsl-2.10.1.so


7f544bc16000-7f544bc17000 rw-p 00017000 08:05 24167                      /lib/libnsl-2.10.1.so
7f544bc17000-7f544bc19000 rw-p 00000000 00:00 0
7f544bc19000-7f544bc9b000 r-xp 00000000 08:05 24165                      /lib/libm-2.10.1.so
7f544bc9b000-7f544be9b000 ---p 00082000 08:05 24165                      /lib/libm-2.10.1.so
7f544be9b000-7f544be9c000 r--p 00082000 08:05 24165                      /lib/libm-2.10.1.so
7f544be9c000-7f544be9d000 rw-p 00083000 08:05 24165                      /lib/libm-2.10.1.so
7f544be9d000-7f544beb3000 r-xp 00000000 08:05 24176                      /lib/libresolv-2.10.1.so
7f544beb3000-7f544c0b2000 ---p 00016000 08:05 24176                      /lib/libresolv-2.10.1.so
7f544c0b2000-7f544c0b3000 r--p 00015000 08:05 24176                      /lib/libresolv-2.10.1.so
7f544c0b3000-7f544c0b4000 rw-p 00016000 08:05 24176                      /lib/libresolv-2.10.1.so
7f544c0b4000-7f544c0b6000 rw-p 00000000 00:00 0
7f544c0b6000-7f544c0c5000 r-xp 00000000 08:05 24589                      /lib/libbz2.so.1.0.4
7f544c0c5000-7f544c2c5000 ---p 0000f000 08:05 24589                      /lib/libbz2.so.1.0.4
7f544c2c5000-7f544c2c6000 r--p 0000f000 08:05 24589                      /lib/libbz2.so.1.0.4
7f544c2c6000-7f544c2c7000 rw-p 00010000 08:05 24589                      /lib/libbz2.so.1.0.4
7f544c2c7000-7f544c426000 r-xp 00000000 08:05 8155                       /usr/lib/libdb-4.7.so
7f544c426000-7f544c625000 ---p 0015f000 08:05 8155                       /usr/lib/libdb-4.7.so
7f544c625000-7f544c628000 r--p 0015e000 08:05 8155                       /usr/lib/libdb-4.7.so
7f544c628000-7f544c629000 rw-p 00161000 08:05 8155                       /usr/lib/libdb-4.7.so
7f544c629000-7f544c671000 r-xp 00000000 08:05 24271                      /lib/libssl.so.0.9.8
7f544c671000-7f544c871000 ---p 00048000 08:05 24271                      /lib/libssl.so.0.9.8
7f544c871000-7f544c872000 r--p 00048000 08:05 24271                      /lib/libssl.so.0.9.8
7f544c872000-7f544c877000 rw-p 00049000 08:05 24271                      /lib/libssl.so.0.9.8
7f544c877000-7f544cde8000 r-xp 00000000 08:05 114700                     /usr/lib/apache2/modules/libphp5.so
7f544cde8000-7f544cfe8000 ---p 00571000 08:05 114700                     /usr/lib/apache2/modules/libphp5.so
7f544cfe8000-7f544d007000 r--p 00571000 08:05 114700                     /usr/lib/apache2/modules/libphp5.so
7f544d007000-7f544d041000 rw-p 00590000 08:05 114700                     /usr/lib/apache2/modules/libphp5.so
7f544d041000-7f544d049000 rw-p 00000000 00:00 0
7f544d049000-7f544d050000 r-xp 00000000 08:05 114346                     /usr/lib/apache2/modules/mod_negotiation.so
7f544d050000-7f544d250000 ---p 00007000 08:05 114346                     /usr/lib/apache2/modules/mod_negotiation.so
7f544d250000-7f544d251000 r--p 00007000 08:05 114346                     /usr/lib/apache2/modules/mod_negotiation.so
7f544d251000-7f544d252000 rw-p 00008000 08:05 114346                     /usr/lib/apache2/modules/mod_negotiation.so
7f544d252000-7f544d256000 r-xp 00000000 08:05 114334                     /usr/lib/apache2/modules/mod_mime.so
7f544d256000-7f544d455000 ---p 00004000 08:05 114334                     /usr/lib/apache2/modules/mod_mime.so
7f544d455000-7f544d456000 r--p 00003000 08:05 114334                     /usr/lib/apache2/modules/mod_mime.so
7f544d456000-7f544d457000 rw-p 00004000 08:05 114334                     /usr/lib/apache2/modules/mod_mime.so
7f544d457000-7f544d488000 r-xp 00000000 08:05 11904                      /usr/lib/libGeoIP.so.1.4.6
7f544d488000-7f544d688000 ---p 00031000 08:05 11904                      /usr/lib/libGeoIP.so.1.4.6
7f544d688000-7f544d689000 r--p 00031000 08:05 11904                      /usr/lib/libGeoIP.so.1.4.6
7f544d689000-7f544d68a000 rw-p 00032000 08:05 11904                      /usr/lib/libGeoIP.so.1.4.6
7f544d68a000-7f544d68d000 r-xp 00000000 08:05 116687                     /usr/lib/apache2/modules/mod_geoip.so
7f544d68d000-7f544d88c000 ---p 00003000 08:05 116687                     /usr/lib/apache2/modules/mod_geoip.so
7f544d88c000-7f544d88d000 r--p 00002000 08:05 116687                     /usr/lib/apache2/modules/mod_geoip.so
7f544d88d000-7f544d88e000 rw-p 00003000 08:05 116687                     /usr/lib/apache2/modules/mod_geoip.so
7f544d88e000-7f544d890000 r-xp 00000000 08:05 114317                     /usr/lib/apache2/modules/mod_env.so
7f544d890000-7f544da8f000 ---p 00002000 08:05 114317                     /usr/lib/apache2/modules/mod_env.so
7f544da8f000-7f544da90000 r--p 00001000 08:05 114317                     /usr/lib/apache2/modules/mod_env.so
7f544da90000-7f544da91000 rw-p 00002000 08:05 114317                     /usr/lib/apache2/modules/mod_env.so
7f544da91000-7f544da93000 r-xp 00000000 08:05 114347                     /usr/lib/apache2/modules/mod_dir.so
7f544da93000-7f544dc92000 ---p 00002000 08:05 114347                     /usr/lib/apache2/modules/mod_dir.so
7f544dc92000-7f544dc93000 r--p 00001000 08:05 114347                     /usr/lib/apache2/modules/mod_dir.so
7f544dc93000-7f544dc94000 rw-p 00002000 08:05 114347                     /usr/lib/apache2/modules/mod_dir.so
7f544dc94000-7f544dcaa000 r-xp 00000000 08:05 24375                      /lib/libz.so.1.2.3.3
7f544dcaa000-7f544dea9000 ---p 00016000 08:05 24375                      /lib/libz.so.1.2.3.3
7f544dea9000-7f544deaa000 r--p 00015000 08:05 24375                      /lib/libz.so.1.2.3.3
7f544deaa000-7f544deab000 rw-p 00016000 08:05 24375                      /lib/libz.so.1.2.3.3
7f544deab000-7f544deb0000 r-xp 00000000 08:05 114314                     /usr/lib/apache2/modules/mod_deflate.so
7f544deb0000-7f544e0af000 ---p 00005000 08:05 114314                     /usr/lib/apache2/modules/mod_deflate.so
7f544e0af000-7f544e0b0000 r--p 00004000 08:05 114314                     /usr/lib/apache2/modules/mod_deflate.so
7f544e0b0000-7f544e0b1000 rw-p 00005000 08:05 114314                     /usr/lib/apache2/modules/mod_deflate.so
7f544e0b1000-7f544e0b7000 r-xp 00000000 08:05 114342                     /usr/lib/apache2/modules/mod_cgi.so
7f544e0b7000-7f544e2b6000 ---p 00006000 08:05 114342                     /usr/lib/apache2/modules/mod_cgi.so
7f544e2b6000-7f544e2b7000 r--p 00005000 08:05 114342                     /usr/lib/apache2/modules/mod_cgi.so
7f544e2b7000-7f544e2b8000 rw-p 00006000 08:05 114342                     /usr/lib/apache2/modules/mod_cgi.so
7f544e2b8000-7f544e2c0000 r-xp 00000000 08:05 114337                     /usr/lib/apache2/modules/mod_autoindex.so
7f544e2c0000-7f544e4c0000 ---p 00008000 08:05 114337                     /usr/lib/apache2/modules/mod_autoindex.so
7f544e4c0000-7f544e4c1000 r--p 00008000 08:05 114337                     /usr/lib/apache2/modules/mod_autoindex.so
7f544e4c1000-7f544e4c2000 rw-p 00009000 08:05 114337                     /usr/lib/apache2/modules/mod_autoindex.so
7f544e4c2000-7f544e4c3000 r-xp 00000000 08:05 114296                     /usr/lib/apache2/modules/mod_authz_user.so
7f544e4c3000-7f544e6c3000 ---p 00001000 08:05 114296                     /usr/lib/apache2/modules/mod_authz_user.so
7f544e6c3000-7f544e6c4000 r--p 00001000 08:05 114296                     /usr/lib/apache2/modules/mod_authz_user.so
7f544e6c4000-7f544e6c5000 rw-p 00002000 08:05 114296                     /usr/lib/apache2/modules/mod_authz_user.so
7f544e6c5000-7f544e6c7000 r-xp 00000000 08:05 114294                     /usr/lib/apache2/modules/mod_authz_host.so
7f544e6c7000-7f544e8c6000 ---p 00002000 08:05 114294                     /usr/lib/apache2/modules/mod_authz_host.so
7f544e8c6000-7f544e8c7000 r--p 00001000 08:05 114294                     /usr/lib/apache2/modules/mod_authz_host.so
7f544e8c7000-7f544e8c8000 rw-p 00002000 08:05 114294                     /usr/lib/apache2/modules/mod_authz_host.so
7f544e8c8000-7f544e8ca000 r-xp 00000000 08:05 114295                     /usr/lib/apache2/modules/mod_authz_groupfile.so
7f544e8ca000-7f544eac9000 ---p 00002000 08:05 114295                     /usr/lib/apache2/modules/mod_authz_groupfile.so
7f544eac9000-7f544eaca000 r--p 00001000 08:05 114295                     /usr/lib/apache2/modules/mod_authz_groupfile.so
7f544eaca000-7f544eacb000 rw-p 00002000 08:05 114295                     /usr/lib/apache2/modules/mod_authz_groupfile.so
7f544eacb000-7f544eacc000 r-xp 00000000 08:05 114300                     /usr/lib/apache2/modules/mod_authz_default.so
7f544eacc000-7f544eccb000 ---p 00001000 08:05 114300                     /usr/lib/apache2/modules/mod_authz_default.so
7f544eccb000-7f544eccc000 r--p 00000000 08:05 114300                     /usr/lib/apache2/modules/mod_authz_default.so
7f544eccc000-7f544eccd000 rw-p 00001000 08:05 114300                     /usr/lib/apache2/modules/mod_authz_default.so
7f544eccd000-7f544eccf000 r-xp 00000000 08:05 114288                     /usr/lib/apache2/modules/mod_authn_file.so
7f544eccf000-7f544eece000 ---p 00002000 08:05 114288                     /usr/lib/apache2/modules/mod_authn_file.so
7f544eece000-7f544eecf000 r--p 00001000 08:05 114288                     /usr/lib/apache2/modules/mod_authn_file.so
7f544eecf000-7f544eed0000 rw-p 00002000 08:05 114288                     /usr/lib/apache2/modules/mod_authn_file.so
7f544eed0000-7f544eed2000 r-xp 00000000 08:05 114301                     /usr/lib/apache2/modules/mod_auth_basic.so
7f544eed2000-7f544f0d1000 ---p 00002000 08:05 114301                     /usr/lib/apache2/modules/mod_auth_basic.so
7f544f0d1000-7f544f0d2000 r--p 00001000 08:05 114301                     /usr/lib/apache2/modules/mod_auth_basic.so
7f544f0d2000-7f544f0d3000 rw-p 00002000 08:05 114301                     /usr/lib/apache2/modules/mod_auth_basic.so
7f544f0d3000-7f544f0d6000 r-xp 00000000 08:05 114352                     /usr/lib/apache2/modules/mod_alias.so
7f544f0d6000-7f544f2d5000 ---p 00003000 08:05 114352                     /usr/lib/apache2/modules/mod_alias.so
7f544f2d5000-7f544f2d6000 r--p 00002000 08:05 114352                     /usr/lib/apache2/modules/mod_alias.so
7f544f2d6000-7f544f2d7000 rw-p 00003000 08:05 114352                     /usr/lib/apache2/modules/mod_alias.so
7f544f2d7000-7f544f2fd000 r-xp 00000000 08:05 27125                      /lib/libexpat.so.1.5.2
7f544f2fd000-7f544f4fd000 ---p 00026000 08:05 27125                      /lib/libexpat.so.1.5.2
7f544f4fd000-7f544f4ff000 r--p 00026000 08:05 27125                      /lib/libexpat.so.1.5.2
7f544f4ff000-7f544f500000 rw-p 00028000 08:05 27125                      /lib/libexpat.so.1.5.2
7f544f500000-7f544f502000 r-xp 00000000 08:05 24164                      /lib/libdl-2.10.1.so
7f544f502000-7f544f702000 ---p 00002000 08:05 24164                      /lib/libdl-2.10.1.so
7f544f702000-7f544f703000 r--p 00002000 08:05 24164                      /lib/libdl-2.10.1.so
7f544f703000-7f544f704000 rw-p 00003000 08:05 24164                      /lib/libdl-2.10.1.so
7f544f704000-7f544f70d000 r-xp 00000000 08:05 24163                      /lib/libcrypt-2.10.1.so
7f544f70d000-7f544f90d000 ---p 00009000 08:05 24163                      /lib/libcrypt-2.10.1.so
7f544f90d000-7f544f90e000 r--p 00009000 08:05 24163                      /lib/libcrypt-2.10.1.so
7f544f90e000-7f544f90f000 rw-p 0000a000 08:05 24163                      /lib/libcrypt-2.10.1.so
7f544f90f000-7f544f93d000 rw-p 00000000 00:00 0
7f544f93d000-7f544f944000 r-xp 00000000 08:05 24177                      /lib/librt-2.10.1.so
7f544f944000-7f544fb43000 ---p 00007000 08:05 24177                      /lib/librt-2.10.1.so
7f544fb43000-7f544fb44000 r--p 00006000 08:05 24177                      /lib/librt-2.10.1.so
7f544fb44000-7f544fb45000 rw-p 00007000 08:05 24177                      /lib/librt-2.10.1.so
7f544fb45000-7f544fb48000 r-xp 00000000 08:05 24351                      /lib/libuuid.so.1.3.0
7f544fb48000-7f544fd48000 ---p 00003000 08:05 24351                      /lib/libuuid.so.1.3.0
7f544fd48000-7f544fd49000 r--p 00003000 08:05 24351                      /lib/libuuid.so.1.3.0
7f544fd49000-7f544fd4a000 rw-p 00004000 08:05 24351                      /lib/libuuid.so.1.3.0
7f544fd4a000-7f544feb0000 r-xp 00000000 08:05 24161                      /lib/libc-2.10.1.so
7f544feb0000-7f54500af000 ---p 00166000 08:05 24161                      /lib/libc-2.10.1.so
7f54500af000-7f54500b3000 r--p 00165000 08:05 24161                      /lib/libc-2.10.1.so
7f54500b3000-7f54500b4000 rw-p 00169000 08:05 24161                      /lib/libc-2.10.1.so
7f54500b9000-7f54500d0000 r-xp 00000000 08:05 24175                      /lib/libpthread-2.10.1.so
7f54500d0000-7f54502cf000 ---p 00017000 08:05 24175                      /lib/libpthread-2.10.1.so
7f54502cf000-7f54502d0000 r--p 00016000 08:05 24175                      /lib/libpthread-2.10.1.so
7f54502d0000-7f54502d1000 rw-p 00017000 08:05 24175                      /lib/libpthread-2.10.1.so
7f54502d1000-7f54502d5000 rw-p 00000000 00:00 0
7f54502d5000-7f5450309000 r-xp 00000000 08:05 12872                      /usr/lib/libapr-1.so.0.3.8
7f5450309000-7f5450508000 ---p 00034000 08:05 12872                      /usr/lib/libapr-1.so.0.3.8
7f5450508000-7f5450509000 r--p 00033000 08:05 12872                      /usr/lib/libapr-1.so.0.3.8
7f5450509000-7f545050a000 rw-p 00034000 08:05 12872                      /usr/lib/libapr-1.so.0.3.8
7f545050a000-7f545052b000 r-xp 00000000 08:05 12876                      /usr/lib/libaprutil-1.so.0.3.9
7f545052b000-7f545072b000 ---p 00021000 08:05 12876                      /usr/lib/libaprutil-1.so.0.3.9
7f545072b000-7f545072c000 r--p 00021000 08:05 12876                      /usr/lib/libaprutil-1.so.0.3.9
7f545072c000-7f545072d000 rw-p 00022000 08:05 12876                      /usr/lib/libaprutil-1.so.0.3.9
7f545072d000-7f545075a000 r-xp 00000000 08:05 26132                      /lib/libpcre.so.3.12.1
7f545075a000-7f5450959000 ---p 0002d000 08:05 26132                      /lib/libpcre.so.3.12.1
7f5450959000-7f545095a000 r--p 0002c000 08:05 26132                      /lib/libpcre.so.3.12.1
7f545095a000-7f545095b000 rw-p 0002d000 08:05 26132                      /lib/libpcre.so.3.12.1
7f545095b000-7f545097a000 r-xp 00000000 08:05 24155                      /lib/ld-2.10.1.so
7f5450b36000-7f5450b6d000 rw-s 00000000 00:09 23120731                   /dev/zero (deleted)
7f5450b6d000-7f5450b72000 rw-p 00000000 00:00 0
7f5450b75000-7f5450b79000 rw-p 00000000 00:00 0
7f5450b79000-7f5450b7a000 r--p 0001e000 08:05 24155                      /lib/ld-2.10.1.so
7f5450b7a000-7f5450b7b000 rw-p 0001f000 08:05 24155                      /lib/ld-2.10.1.so
7f5450b7b000-7f5450be8000 r-xp 00000000 08:05 114284                     /usr/lib/apache2/mpm-prefork/apache2
7f5450de8000-7f5450deb000 r--p 0006d000 08:05 114284                     /usr/lib/apache2/mpm-prefork/apache2
7f5450deb000-7f5450dee000 rw-p 00070000 08:05 114284                     /usr/lib/apache2/mpm-prefork/apache2
7f5450dee000-7f5450df1000 rw-p 00000000 00:00 0
7f54526b9000-7f5452ef4000 rw-p 00000000 00:00 0                          [heap]
7fffb7067000-7fffb7091000 rw-p 00000000 00:00 0                          [stack]
7fffb711c000-7fffb711d000 r-xp 00000000 00:00 0                          [vdso]
ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vsyscall]
[Thu Jan 07 12:25:32 2010] [notice] child pid 15124 exit signal Aborted (6)
```

---

