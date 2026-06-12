---
title: "Unable to install CUPS on server 12.04"
date: 2013-05-24
forum: Server Platforms
---

### Post by bryan.sailer on 2013-05-24
I used the command apt-get install cups. There were packages without authentication. When asked to install I chose [y]. Then the following output came out and CUPS was not installed. What should I do next.

```
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main libcolord1 i386 0.1.16-2ubuntu0.1
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main libgudev-1.0-0 i386 1:175-0ubuntu9.2
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main liblcms2-2 i386 2.2+git20110628-2ubuntu3
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main libsane-common i386 1.0.22-7ubuntu1
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main acl i386 2.2.51-5ubuntu1
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main libexif12 i386 0.6.20-2ubuntu0.1
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main libjpeg-turbo8 i386 1.1.90+svn733-0ubuntu4.1
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main libexif12 i386 0.6.20-2ubuntu0.1
  Temporary failure resolving 'security.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main libjpeg8 i386 8c-2ubuntu7
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main libxpm4 i386 1:3.5.9-4
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main libgd2-xpm i386 2.0.36~rc1~dfsg-6ubuntu2
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main libgphoto2-port0 i386 2.4.13-1ubuntu1.2
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main libgphoto2-2 i386 2.4.13-1ubuntu1.2
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main libieee1284-3 i386 0.2.11-10build1
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main libtiff4 i386 3.9.5-2ubuntu1.3
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main libv4lconvert0 i386 0.8.6-1ubuntu2
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main libtiff4 i386 3.9.5-2ubuntu1.3
  Temporary failure resolving 'security.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main libv4l-0 i386 0.8.6-1ubuntu2
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main libsane i386 1.0.22-7ubuntu1
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main libpolkit-agent-1-0 i386 0.104-1ubuntu1
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main libpolkit-backend-1-0 i386 0.104-1ubuntu1
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main libck-connector0 i386 0.4.5-2
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main consolekit i386 0.4.5-2
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main policykit-1 i386 0.104-1ubuntu1
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main colord i386 0.1.16-2ubuntu0.1
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main libcupscgi1 i386 1.5.3-0ubuntu4
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main libcupsimage2 i386 1.5.3-0ubuntu4
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main libcupsmime1 i386 1.5.3-0ubuntu4
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main libcupsppdc1 i386 1.5.3-0ubuntu4
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main libpaper1 i386 1.1.24+nmu1build1
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main libslp1 i386 1.2.1-7.8ubuntu1
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main libpoppler19 i386 0.18.4-1ubuntu2
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main poppler-utils i386 0.18.4-1ubuntu2
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main libijs-0.35 i386 0.35-8
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main libjasper1 i386 1.900.1-13
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main libjbig2dec0 i386 0.11-1ubuntu1
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main gs-cjk-resource all 1.20100103-3
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main libgs9-common all 9.05~dfsg-0ubuntu4.2
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main libgs9 i386 9.05~dfsg-0ubuntu4.2
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main gsfonts all 1:8.11+urwcyr1.0.7~pre44-4.2ubuntu1
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main ghostscript i386 9.05~dfsg-0ubuntu4.2
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main cups-common all 1.5.3-0ubuntu4
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main cups-client i386 1.5.3-0ubuntu4
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main cups-ppdc i386 1.5.3-0ubuntu4
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main libcupsfilters1 i386 1.0.18-0ubuntu0.1
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main ttf-freefont all 20100919-1
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main cups-filters i386 1.0.18-0ubuntu0.1
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main cups i386 1.5.3-0ubuntu4
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main foomatic-filters i386 4.0.16-0ubuntu0.2
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main libgutenprint2 i386 5.2.8~pre1-0ubuntu2.1
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main libsensors4 i386 1:3.3.1-2ubuntu1
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main foomatic-db-engine i386 4.0.8-2ubuntu1
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main cmap-adobe-japan1 all 0+20090930-2
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main foomatic-db-compressed-ppds all 20120322-0ubuntu1
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main ghostscript-cups i386 9.05~dfsg-0ubuntu4.2
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main libgphoto2-l10n all 2.4.13-1ubuntu1.2
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main libsnmp-base all 5.4.3~dfsg-2.4ubuntu1.1
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main libsnmp-base all 5.4.3~dfsg-2.4ubuntu1.1
  Temporary failure resolving 'security.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main libperl5.14 i386 5.14.2-6ubuntu2.1
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main libsnmp15 i386 5.4.3~dfsg-2.4ubuntu1.1
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main libhpmud0 i386 3.12.2-1ubuntu3.1
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main libsnmp15 i386 5.4.3~dfsg-2.4ubuntu1.1
  Temporary failure resolving 'security.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main libpam-ck-connector i386 0.4.5-2
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main libpaper-utils i386 1.1.24+nmu1build1
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main printer-driver-gutenprint i386 5.2.8~pre1-0ubuntu2.1
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main printer-driver-hpijs i386 3.12.2-1ubuntu3.1
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main printer-driver-min12xxw i386 0.0.9-6ubuntu1
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main printer-driver-pnm2ppa i386 1.13+nondbs-0ubuntu1
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main smbclient i386 2:3.6.3-2ubuntu2.3
  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/colord/libcolord1_0.1.16-2ubuntu0.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/colord/libcolord1_0.1.16-2ubuntu0.1_i386.deb)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/u/udev/libgudev-1.0-0_175-0ubuntu9.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/u/udev/libgudev-1.0-0_175-0ubuntu9.2_i386.deb)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/lcms2/liblcms2-2_2.2+git20110628-2ubuntu3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/lcms2/liblcms2-2_2.2+git20110628-2ubuntu3_i386.deb)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/s/sane-backends/libsane-common_1.0.22-7ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/s/sane-backends/libsane-common_1.0.22-7ubuntu1_i386.deb)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/acl/acl_2.2.51-5ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/acl/acl_2.2.51-5ubuntu1_i386.deb)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libe/libexif/libexif12_0.6.20-2ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/libe/libexif/libexif12_0.6.20-2ubuntu0.1_i386.deb)  Temporary failure resolving 'security.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libj/libjpeg-turbo/libjpeg-turbo8_1.1.90+svn733-0ubuntu4.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libj/libjpeg-turbo/libjpeg-turbo8_1.1.90+svn733-0ubuntu4.1_i386.deb)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libj/libjpeg8-empty/libjpeg8_8c-2ubuntu7_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libj/libjpeg8-empty/libjpeg8_8c-2ubuntu7_i386.deb)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libxpm/libxpm4_3.5.9-4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libxpm/libxpm4_3.5.9-4_i386.deb)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libgd2/libgd2-xpm_2.0.36~rc1~dfsg-6ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libgd2/libgd2-xpm_2.0.36~rc1~dfsg-6ubuntu2_i386.deb)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libgphoto2/libgphoto2-port0_2.4.13-1ubuntu1.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libgphoto2/libgphoto2-port0_2.4.13-1ubuntu1.2_i386.deb)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libgphoto2/libgphoto2-2_2.4.13-1ubuntu1.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libgphoto2/libgphoto2-2_2.4.13-1ubuntu1.2_i386.deb)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libi/libieee1284/libieee1284-3_0.2.11-10build1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libi/libieee1284/libieee1284-3_0.2.11-10build1_i386.deb)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/t/tiff/libtiff4_3.9.5-2ubuntu1.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/t/tiff/libtiff4_3.9.5-2ubuntu1.3_i386.deb)  Temporary failure resolving 'security.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/v/v4l-utils/libv4lconvert0_0.8.6-1ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/v/v4l-utils/libv4lconvert0_0.8.6-1ubuntu2_i386.deb)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/v/v4l-utils/libv4l-0_0.8.6-1ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/v/v4l-utils/libv4l-0_0.8.6-1ubuntu2_i386.deb)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/s/sane-backends/libsane_1.0.22-7ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/s/sane-backends/libsane_1.0.22-7ubuntu1_i386.deb)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/policykit-1/libpolkit-agent-1-0_0.104-1ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/policykit-1/libpolkit-agent-1-0_0.104-1ubuntu1_i386.deb)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/policykit-1/libpolkit-backend-1-0_0.104-1ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/policykit-1/libpolkit-backend-1-0_0.104-1ubuntu1_i386.deb)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/consolekit/libck-connector0_0.4.5-2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/consolekit/libck-connector0_0.4.5-2_i386.deb)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/consolekit/consolekit_0.4.5-2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/consolekit/consolekit_0.4.5-2_i386.deb)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/policykit-1/policykit-1_0.104-1ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/policykit-1/policykit-1_0.104-1ubuntu1_i386.deb)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/colord/colord_0.1.16-2ubuntu0.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/colord/colord_0.1.16-2ubuntu0.1_i386.deb)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupscgi1_1.5.3-0ubuntu4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupscgi1_1.5.3-0ubuntu4_i386.deb)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupsimage2_1.5.3-0ubuntu4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupsimage2_1.5.3-0ubuntu4_i386.deb)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupsmime1_1.5.3-0ubuntu4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupsmime1_1.5.3-0ubuntu4_i386.deb)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupsppdc1_1.5.3-0ubuntu4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupsppdc1_1.5.3-0ubuntu4_i386.deb)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libp/libpaper/libpaper1_1.1.24+nmu1build1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libp/libpaper/libpaper1_1.1.24+nmu1build1_i386.deb)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/o/openslp-dfsg/libslp1_1.2.1-7.8ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/o/openslp-dfsg/libslp1_1.2.1-7.8ubuntu1_i386.deb)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/poppler/libpoppler19_0.18.4-1ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/poppler/libpoppler19_0.18.4-1ubuntu2_i386.deb)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/poppler/poppler-utils_0.18.4-1ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/poppler/poppler-utils_0.18.4-1ubuntu2_i386.deb)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/i/ijs/libijs-0.35_0.35-8_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/i/ijs/libijs-0.35_0.35-8_i386.deb)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/j/jasper/libjasper1_1.900.1-13_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/j/jasper/libjasper1_1.900.1-13_i386.deb)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/j/jbig2dec/libjbig2dec0_0.11-1ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/j/jbig2dec/libjbig2dec0_0.11-1ubuntu1_i386.deb)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gs-cjk-resource/gs-cjk-resource_1.20100103-3_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gs-cjk-resource/gs-cjk-resource_1.20100103-3_all.deb)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/libgs9-common_9.05~dfsg-0ubuntu4.2_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/libgs9-common_9.05~dfsg-0ubuntu4.2_all.deb)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/libgs9_9.05~dfsg-0ubuntu4.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/libgs9_9.05~dfsg-0ubuntu4.2_i386.deb)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gsfonts/gsfonts_8.11+urwcyr1.0.7~pre44-4.2ubuntu1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gsfonts/gsfonts_8.11+urwcyr1.0.7~pre44-4.2ubuntu1_all.deb)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/ghostscript_9.05~dfsg-0ubuntu4.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/ghostscript_9.05~dfsg-0ubuntu4.2_i386.deb)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-common_1.5.3-0ubuntu4_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-common_1.5.3-0ubuntu4_all.deb)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-client_1.5.3-0ubuntu4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-client_1.5.3-0ubuntu4_i386.deb)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-ppdc_1.5.3-0ubuntu4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-ppdc_1.5.3-0ubuntu4_i386.deb)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups-filters/libcupsfilters1_1.0.18-0ubuntu0.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups-filters/libcupsfilters1_1.0.18-0ubuntu0.1_i386.deb)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/t/ttf-freefont/ttf-freefont_20100919-1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/t/ttf-freefont/ttf-freefont_20100919-1_all.deb)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups-filters/cups-filters_1.0.18-0ubuntu0.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups-filters/cups-filters_1.0.18-0ubuntu0.1_i386.deb)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups_1.5.3-0ubuntu4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups_1.5.3-0ubuntu4_i386.deb)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/f/foomatic-filters/foomatic-filters_4.0.16-0ubuntu0.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/f/foomatic-filters/foomatic-filters_4.0.16-0ubuntu0.2_i386.deb)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gutenprint/libgutenprint2_5.2.8~pre1-0ubuntu2.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gutenprint/libgutenprint2_5.2.8~pre1-0ubuntu2.1_i386.deb)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/lm-sensors/libsensors4_3.3.1-2ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/lm-sensors/libsensors4_3.3.1-2ubuntu1_i386.deb)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/f/foomatic-db-engine/foomatic-db-engine_4.0.8-2ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/f/foomatic-db-engine/foomatic-db-engine_4.0.8-2ubuntu1_i386.deb)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/cmap-adobe-japan1/cmap-adobe-japan1_0+20090930-2_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/cmap-adobe-japan1/cmap-adobe-japan1_0+20090930-2_all.deb)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/f/foomatic-db/foomatic-db-compressed-ppds_20120322-0ubuntu1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/f/foomatic-db/foomatic-db-compressed-ppds_20120322-0ubuntu1_all.deb)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/ghostscript-cups_9.05~dfsg-0ubuntu4.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/ghostscript-cups_9.05~dfsg-0ubuntu4.2_i386.deb)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libgphoto2/libgphoto2-l10n_2.4.13-1ubuntu1.2_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libgphoto2/libgphoto2-l10n_2.4.13-1ubuntu1.2_all.deb)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/n/net-snmp/libsnmp-base_5.4.3~dfsg-2.4ubuntu1.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/n/net-snmp/libsnmp-base_5.4.3~dfsg-2.4ubuntu1.1_all.deb)  Temporary failure resolving 'security.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/perl/libperl5.14_5.14.2-6ubuntu2.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/perl/libperl5.14_5.14.2-6ubuntu2.1_i386.deb)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/n/net-snmp/libsnmp15_5.4.3~dfsg-2.4ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/n/net-snmp/libsnmp15_5.4.3~dfsg-2.4ubuntu1.1_i386.deb)  Temporary failure resolving 'security.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/h/hplip/libhpmud0_3.12.2-1ubuntu3.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/h/hplip/libhpmud0_3.12.2-1ubuntu3.1_i386.deb)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/consolekit/libpam-ck-connector_0.4.5-2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/consolekit/libpam-ck-connector_0.4.5-2_i386.deb)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libp/libpaper/libpaper-utils_1.1.24+nmu1build1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libp/libpaper/libpaper-utils_1.1.24+nmu1build1_i386.deb)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gutenprint/printer-driver-gutenprint_5.2.8~pre1-0ubuntu2.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gutenprint/printer-driver-gutenprint_5.2.8~pre1-0ubuntu2.1_i386.deb)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/h/hplip/printer-driver-hpijs_3.12.2-1ubuntu3.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/h/hplip/printer-driver-hpijs_3.12.2-1ubuntu3.1_i386.deb)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/m/min12xxw/printer-driver-min12xxw_0.0.9-6ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/m/min12xxw/printer-driver-min12xxw_0.0.9-6ubuntu1_i386.deb)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/pnm2ppa/printer-driver-pnm2ppa_1.13+nondbs-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/pnm2ppa/printer-driver-pnm2ppa_1.13+nondbs-0ubuntu1_i386.deb)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.6.3-2ubuntu2.3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.6.3-2ubuntu2.3_i386.deb)  Temporary failure resolving 'us.archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

Also, in /var/log, there is no cup directory.

---

### Post by 2F4U on 2013-05-25
It seems as if the mirror us.archive.ubuntu.com is not reachable. Wait some time and retry or choose another mirror.

---

### Post by bryan.sailer on 2013-05-25
That makes since after I reread the screen output this morning. How do I change the mirror that I am using to download CUPS? 

Ubuntu 12.04 server

---

### Post by 2F4U on 2013-05-25
It depends on whether you have a GUI or do it through the command line:

[http://askubuntu.com/questions/104695/how-do-i-change-mirrors-in-ubuntu-server-from-regional-to-main](http://askubuntu.com/questions/104695/how-do-i-change-mirrors-in-ubuntu-server-from-regional-to-main)

If you can't do it through the GUI, be careful when editing /etc/apt/sources.list.

---

### Post by bryan.sailer on 2013-05-25
I just checked my /etc/apt/sources.list and it was empty. When I went to add to the list I received this error.

Error writing etc/apt/sources.list: No such file or directory

---

### Post by 2F4U on 2013-05-25
Is the missing "/" in front of etc in the error message > Error writing etc/apt/sources.list: No such file or directory a typo? Else it would explain why the system is unable to find the file.

---

### Post by bryan.sailer on 2013-05-25
Yes it was a typo on the message.

---

### Post by bryan.sailer on 2013-05-25
And I was doing the same thing in terminal. Thanks for pointing that out, just goes to show how much the little things matter. I have now changes the mirror from  us.archive.ubuntu.com to archive.ubuntu.com. I will now see if that works. Thank you again for your assistance I cannot believe that it was one / that has messed me up. 

That did not help now I am getting the following error: 

Package cups is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source.

---

### Post by bryan.sailer on 2013-05-25
After looking at everything I think there was an issue when I upgraded from 11.10 to 12.04. I did not use a CD/DVD but instead I used the apt-get upgrade command. My server was running fine but I was not receiving any updates like I normally should. Also, looking at /etc/apt/sources.list it still refered to the 11.10 platform. So I am going to reload that server with 12.04 and go from there. Thank you for all of your help.

---

