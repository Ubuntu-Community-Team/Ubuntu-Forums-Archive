---
title: "Cant update Raspbian"
date: 2016-04-10
forum: Ubuntu/Debian BASED
---

### Post by linuxyogi on 2016-04-10
When I try to update my Raspbian I get this 

```
 $ sudo apt-get upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  pypy-upstream raspberrypi-ui-mods
The following packages will be upgraded:
  apt apt-utils bind9-host bluej git git-core git-man gnupg gpgv
  gtk2-engines-clearlookspix gtk2-engines-pixbuf initramfs-tools
  libapt-inst1.5 libapt-pkg4.12 libav-tools libavcodec56 libavdevice55
  libavfilter5 libavformat56 libavresample2 libavutil54 libbind9-90 libc-bin
  libc-dev-bin libc6 libc6-dbg libc6-dev libcairo-gobject2 libcairo2
  libdns-export100 libdns100 libfftw3-double3 libfftw3-single3 libgif4
  libgraphite2-3 libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libgudev-1.0-0
  libhogweed2 libimlib2 libirs-export91 libisc-export95 libisc95 libisccc90
  libisccfg-export90 libisccfg90 libjasper1 liblwres90 libnettle4
  libpam-systemd libpcre3 libraspberrypi-bin libraspberrypi-dev
  libraspberrypi-doc libraspberrypi0 librsvg2-2 librsvg2-common
  libservlet2.5-java libsmbclient libsndfile1 libsrtp0 libssl1.0.0 libswscale3
  libsystemd0 libudev1 libvpx1 libwbclient0 libx264-142 locales lxpanel
  lxpanel-data multiarch-support nodered openssl perl perl-base perl-modules
  python-pil python-rpi.gpio python3-pil python3-rpi.gpio
  raspberrypi-bootloader raspberrypi-net-mods raspberrypi-sys-mods
  raspi-config rc-gui ruby samba-common samba-libs systemd systemd-sysv tzdata
  udev wiringpi
95 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 36.9 MB/139 MB of archives.
After this operation, 12.8 MB of additional disk space will be used.
Do you want to continue? [Y/n] 
Err http://mirrordirector.raspbian.org/raspbian/ jessie/main libc6-dev armhf 2.19-18+deb8u4
  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]
Err http://mirrordirector.raspbian.org/raspbian/ jessie/main libc-dev-bin armhf 2.19-18+deb8u4
  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]
Err http://mirrordirector.raspbian.org/raspbian/ jessie/main libc-bin armhf 2.19-18+deb8u4
  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]
Err http://mirrordirector.raspbian.org/raspbian/ jessie/main libc6-dbg armhf 2.19-18+deb8u4
  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]
Err http://mirrordirector.raspbian.org/raspbian/ jessie/main libc6 armhf 2.19-18+deb8u4
  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]
Err http://mirrordirector.raspbian.org/raspbian/ jessie/main libapt-pkg4.12 armhf 1.0.9.8.3
  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]
Err http://mirrordirector.raspbian.org/raspbian/ jessie/main gpgv armhf 1.4.18-7+deb8u1
  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]
Err http://mirrordirector.raspbian.org/raspbian/ jessie/main gnupg armhf 1.4.18-7+deb8u1
  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]
Err http://mirrordirector.raspbian.org/raspbian/ jessie/main apt armhf 1.0.9.8.3
  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]
Err http://mirrordirector.raspbian.org/raspbian/ jessie/main libpcre3 armhf 2:8.35-3.3+deb8u4
  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]
Err http://mirrordirector.raspbian.org/raspbian/ jessie/main libudev1 armhf 215-17+deb8u4
  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]
Err http://mirrordirector.raspbian.org/raspbian/ jessie/main udev armhf 215-17+deb8u4
  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]
Err http://mirrordirector.raspbian.org/raspbian/ jessie/main initramfs-tools all 0.120+deb8u1
  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]
Err http://mirrordirector.raspbian.org/raspbian/ jessie/main libsystemd0 armhf 215-17+deb8u4
  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]
Err http://mirrordirector.raspbian.org/raspbian/ jessie/main libpam-systemd armhf 215-17+deb8u4
  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]
Err http://mirrordirector.raspbian.org/raspbian/ jessie/main systemd armhf 215-17+deb8u4
  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]
Err http://mirrordirector.raspbian.org/raspbian/ jessie/main systemd-sysv armhf 215-17+deb8u4
  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]
Err http://mirrordirector.raspbian.org/raspbian/ jessie/main libapt-inst1.5 armhf 1.0.9.8.3
  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]
Err http://mirrordirector.raspbian.org/raspbian/ jessie/main libvpx1 armhf 1.3.0-3+rvt
  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]
Err http://mirrordirector.raspbian.org/raspbian/ jessie/main libx264-142 armhf 2:0.142.2431+gita5831aa-1+rpi2
  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]
Err http://mirrordirector.raspbian.org/raspbian/ jessie/main libcairo2 armhf 1.14.0-2.1+deb8u1
  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]
Err http://mirrordirector.raspbian.org/raspbian/ jessie/main libcairo-gobject2 armhf 1.14.0-2.1+deb8u1
  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]
Err http://mirrordirector.raspbian.org/raspbian/ jessie/main libfftw3-double3 armhf 3.3.4-2+rvt
  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]
Err http://mirrordirector.raspbian.org/raspbian/ jessie/main libfftw3-single3 armhf 3.3.4-2+rvt
  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]
Err http://mirrordirector.raspbian.org/raspbian/ jessie/main libgif4 armhf 4.1.6-11+deb8u1
  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]
Err http://mirrordirector.raspbian.org/raspbian/ jessie/main libgtk2.0-common all 2.24.25-3+deb8u1
  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]
Err http://mirrordirector.raspbian.org/raspbian/ jessie/main gtk2-engines-pixbuf armhf 2.24.25-3+deb8u1
  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]
Err http://mirrordirector.raspbian.org/raspbian/ jessie/main librsvg2-common armhf 2.40.5-1+deb8u1
  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]
Err http://mirrordirector.raspbian.org/raspbian/ jessie/main librsvg2-2 armhf 2.40.5-1+deb8u1
  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]
Err http://mirrordirector.raspbian.org/raspbian/ jessie/main libgtk2.0-bin armhf 2.24.25-3+deb8u1
  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]
Err http://mirrordirector.raspbian.org/raspbian/ jessie/main libgtk2.0-0 armhf 2.24.25-3+deb8u1
  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]
Err http://mirrordirector.raspbian.org/raspbian/ jessie/main libgudev-1.0-0 armhf 215-17+deb8u4
  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]
Err http://mirrordirector.raspbian.org/raspbian/ jessie/main libhogweed2 armhf 2.7.1-5+deb8u1
  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]
Err http://mirrordirector.raspbian.org/raspbian/ jessie/main libnettle4 armhf 2.7.1-5+deb8u1
  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]
Err http://mirrordirector.raspbian.org/raspbian/ jessie/main samba-libs armhf 2:4.1.17+dfsg-2+deb8u2
  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]
Err http://mirrordirector.raspbian.org/raspbian/ jessie/main libsndfile1 armhf 1.0.25-9.1+deb8u1
  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]
Err http://mirrordirector.raspbian.org/raspbian/ jessie/main multiarch-support armhf 2.19-18+deb8u4
  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]
Err http://mirrordirector.raspbian.org/raspbian/ jessie/main tzdata all 2016c-0+deb8u1
  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]
Err http://mirrordirector.raspbian.org/raspbian/ jessie/main apt-utils armhf 1.0.9.8.3
  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]
Err http://mirrordirector.raspbian.org/raspbian/ jessie/main locales all 2.19-18+deb8u4
  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]
Err http://mirrordirector.raspbian.org/raspbian/ jessie/main libimlib2 armhf 1.4.6-2+deb8u1
  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]
Err http://mirrordirector.raspbian.org/raspbian/ jessie/main libservlet2.5-java all 6.0.45+dfsg-1~deb8u1
  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]
Err http://mirrordirector.raspbian.org/raspbian/ jessie/main libsrtp0 armhf 1.4.5~20130609~dfsg-1.1+deb8u1
  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]
Err http://mirrordirector.raspbian.org/raspbian/ jessie/main ruby all 1:2.1.5+deb8u2
  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]
E: Failed to fetch http://mirrordirector.raspbian.org/raspbian/pool/main/g/glibc/libc6-dev_2.19-18+deb8u4_armhf.deb  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]

E: Failed to fetch http://mirrordirector.raspbian.org/raspbian/pool/main/g/glibc/libc-dev-bin_2.19-18+deb8u4_armhf.deb  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]

E: Failed to fetch http://mirrordirector.raspbian.org/raspbian/pool/main/g/glibc/libc-bin_2.19-18+deb8u4_armhf.deb  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]

E: Failed to fetch http://mirrordirector.raspbian.org/raspbian/pool/main/g/glibc/libc6-dbg_2.19-18+deb8u4_armhf.deb  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]

E: Failed to fetch http://mirrordirector.raspbian.org/raspbian/pool/main/g/glibc/libc6_2.19-18+deb8u4_armhf.deb  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]

E: Failed to fetch http://mirrordirector.raspbian.org/raspbian/pool/main/a/apt/libapt-pkg4.12_1.0.9.8.3_armhf.deb  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]

E: Failed to fetch http://mirrordirector.raspbian.org/raspbian/pool/main/g/gnupg/gpgv_1.4.18-7+deb8u1_armhf.deb  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]

E: Failed to fetch http://mirrordirector.raspbian.org/raspbian/pool/main/g/gnupg/gnupg_1.4.18-7+deb8u1_armhf.deb  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]

E: Failed to fetch http://mirrordirector.raspbian.org/raspbian/pool/main/a/apt/apt_1.0.9.8.3_armhf.deb  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]

E: Failed to fetch http://mirrordirector.raspbian.org/raspbian/pool/main/p/pcre3/libpcre3_8.35-3.3+deb8u4_armhf.deb  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]

E: Failed to fetch http://mirrordirector.raspbian.org/raspbian/pool/main/s/systemd/libudev1_215-17+deb8u4_armhf.deb  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]

E: Failed to fetch http://mirrordirector.raspbian.org/raspbian/pool/main/s/systemd/udev_215-17+deb8u4_armhf.deb  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]

E: Failed to fetch http://mirrordirector.raspbian.org/raspbian/pool/main/i/initramfs-tools/initramfs-tools_0.120+deb8u1_all.deb  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]

E: Failed to fetch http://mirrordirector.raspbian.org/raspbian/pool/main/s/systemd/libsystemd0_215-17+deb8u4_armhf.deb  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]

E: Failed to fetch http://mirrordirector.raspbian.org/raspbian/pool/main/s/systemd/libpam-systemd_215-17+deb8u4_armhf.deb  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]

E: Failed to fetch http://mirrordirector.raspbian.org/raspbian/pool/main/s/systemd/systemd_215-17+deb8u4_armhf.deb  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]

E: Failed to fetch http://mirrordirector.raspbian.org/raspbian/pool/main/s/systemd/systemd-sysv_215-17+deb8u4_armhf.deb  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]

E: Failed to fetch http://mirrordirector.raspbian.org/raspbian/pool/main/a/apt/libapt-inst1.5_1.0.9.8.3_armhf.deb  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]

E: Failed to fetch http://mirrordirector.raspbian.org/raspbian/pool/main/libv/libvpx/libvpx1_1.3.0-3+rvt_armhf.deb  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]

E: Failed to fetch http://mirrordirector.raspbian.org/raspbian/pool/main/x/x264/libx264-142_0.142.2431+gita5831aa-1+rpi2_armhf.deb  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]

E: Failed to fetch http://mirrordirector.raspbian.org/raspbian/pool/main/c/cairo/libcairo2_1.14.0-2.1+deb8u1_armhf.deb  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]

E: Failed to fetch http://mirrordirector.raspbian.org/raspbian/pool/main/c/cairo/libcairo-gobject2_1.14.0-2.1+deb8u1_armhf.deb  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]

E: Failed to fetch http://mirrordirector.raspbian.org/raspbian/pool/main/f/fftw3/libfftw3-double3_3.3.4-2+rvt_armhf.deb  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]

E: Failed to fetch http://mirrordirector.raspbian.org/raspbian/pool/main/f/fftw3/libfftw3-single3_3.3.4-2+rvt_armhf.deb  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]

E: Failed to fetch http://mirrordirector.raspbian.org/raspbian/pool/main/g/giflib/libgif4_4.1.6-11+deb8u1_armhf.deb  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]

E: Failed to fetch http://mirrordirector.raspbian.org/raspbian/pool/main/g/gtk+2.0/libgtk2.0-common_2.24.25-3+deb8u1_all.deb  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]

E: Failed to fetch http://mirrordirector.raspbian.org/raspbian/pool/main/g/gtk+2.0/gtk2-engines-pixbuf_2.24.25-3+deb8u1_armhf.deb  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]

E: Failed to fetch http://mirrordirector.raspbian.org/raspbian/pool/main/libr/librsvg/librsvg2-common_2.40.5-1+deb8u1_armhf.deb  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]

E: Failed to fetch http://mirrordirector.raspbian.org/raspbian/pool/main/libr/librsvg/librsvg2-2_2.40.5-1+deb8u1_armhf.deb  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]

E: Failed to fetch http://mirrordirector.raspbian.org/raspbian/pool/main/g/gtk+2.0/libgtk2.0-bin_2.24.25-3+deb8u1_armhf.deb  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]

E: Failed to fetch http://mirrordirector.raspbian.org/raspbian/pool/main/g/gtk+2.0/libgtk2.0-0_2.24.25-3+deb8u1_armhf.deb  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]

E: Failed to fetch http://mirrordirector.raspbian.org/raspbian/pool/main/s/systemd/libgudev-1.0-0_215-17+deb8u4_armhf.deb  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]

E: Failed to fetch http://mirrordirector.raspbian.org/raspbian/pool/main/n/nettle/libhogweed2_2.7.1-5+deb8u1_armhf.deb  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]

E: Failed to fetch http://mirrordirector.raspbian.org/raspbian/pool/main/n/nettle/libnettle4_2.7.1-5+deb8u1_armhf.deb  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]

E: Failed to fetch http://mirrordirector.raspbian.org/raspbian/pool/main/s/samba/samba-libs_4.1.17+dfsg-2+deb8u2_armhf.deb  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]

E: Failed to fetch http://mirrordirector.raspbian.org/raspbian/pool/main/libs/libsndfile/libsndfile1_1.0.25-9.1+deb8u1_armhf.deb  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]

E: Failed to fetch http://mirrordirector.raspbian.org/raspbian/pool/main/g/glibc/multiarch-support_2.19-18+deb8u4_armhf.deb  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]

E: Failed to fetch http://mirrordirector.raspbian.org/raspbian/pool/main/t/tzdata/tzdata_2016c-0+deb8u1_all.deb  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]

E: Failed to fetch http://mirrordirector.raspbian.org/raspbian/pool/main/a/apt/apt-utils_1.0.9.8.3_armhf.deb  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]

E: Failed to fetch http://mirrordirector.raspbian.org/raspbian/pool/main/g/glibc/locales_2.19-18+deb8u4_all.deb  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]

E: Failed to fetch http://mirrordirector.raspbian.org/raspbian/pool/main/i/imlib2/libimlib2_1.4.6-2+deb8u1_armhf.deb  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]

E: Failed to fetch http://mirrordirector.raspbian.org/raspbian/pool/main/t/tomcat6/libservlet2.5-java_6.0.45+dfsg-1~deb8u1_all.deb  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]

E: Failed to fetch http://mirrordirector.raspbian.org/raspbian/pool/main/s/srtp/libsrtp0_1.4.5~20130609~dfsg-1.1+deb8u1_armhf.deb  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]

E: Failed to fetch http://mirrordirector.raspbian.org/raspbian/pool/main/r/ruby-defaults/ruby_2.1.5+deb8u2_all.deb  Cannot initiate the connection to ftp.tsukuba.wide.ad.jp:80 (2001:200:0:7c06::9393). - connect (101: Network is unreachable) [IP: 2001:200:0:7c06::9393 80]

E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


```

I have done apt-get update but same thing.

---

