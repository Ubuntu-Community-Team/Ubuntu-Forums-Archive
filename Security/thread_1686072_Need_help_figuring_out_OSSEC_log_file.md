---
title: "Need help figuring out OSSEC log file"
date: 2011-02-11
forum: Security
---

### Post by Notable on 2011-02-11
Here is the odd portion of the log I dont understand. The whole log file is listed below as well to help with context.

```

** Alert 1297452000.35246: mail  - ossec,syscheck,
2011 Feb 11 14:20:00 rosemary-122-CK-NF68->syscheck
Rule: 550 (level 7) -> 'Integrity checksum changed.'
Src IP: (none)
User: (none)
Integrity checksum changed for: '/etc/mailcap'
Size changed from '20341' to '23547'
Old md5sum was: '7375633acc830f0e2c0f77cdf7f86726'
New md5sum is : 'bf11ec43b2065fc878e68e4d66557bf7'
Old sha1sum was: '87db09bd11a1cccc97ab8f2d7c3989e366155b0e'
New sha1sum is : 'c701bb9041c2c327cf9a11c2544865b4c0d682f5'


** Alert 1297452006.35738: mail  - ossec,syscheck,
2011 Feb 11 14:20:06 rosemary-122-CK-NF68->syscheck
Rule: 552 (level 7) -> 'Integrity checksum changed again (3rd time).'
Src IP: (none)
User: (none)
Integrity checksum changed for: '/etc/ld.so.cache'
Size changed from '96045' to '99902'
Old md5sum was: '764d42ddfdae000831ffa7a3815cb68a'
New md5sum is : '9d9b12e1130282f7243d8150369668ad'
Old sha1sum was: '4e00f2d66c787e256588a57708a8c8e90add1c35'
New sha1sum is : '200eabf186cc5141ee63da2c763db9be059f6e66'
``````
** Alert 1297406857.0: mail  - syslog,errors,
2011 Feb 11 01:47:37 rosemary-122-CK-NF68->/var/log/messages
Rule: 1002 (level 2) -> 'Unknown problem somewhere in the system.'
Src IP: (none)
User: (none)
Feb 11 01:47:36 rosemary-122-CK-NF68 kernel: [ 9916.558179] npviewer.bin[3951]: segfault at 418 ip 00000000f60d8d16 sp 00000000ffe08918 error 6 in libflashplayer.so[f5e6b000+b5f000]

** Alert 1297407584.385: mail  - syslog,errors,
2011 Feb 11 01:59:44 rosemary-122-CK-NF68->/var/log/messages
Rule: 1002 (level 2) -> 'Unknown problem somewhere in the system.'
Src IP: (none)
User: (none)
Feb 11 01:59:43 rosemary-122-CK-NF68 kernel: [10643.034026] npviewer.bin[4113]: segfault at 418 ip 00000000f603dd16 sp 00000000ff9a3de8 error 6 in libflashplayer.so[f5dd0000+b5f000]

** Alert 1297408970.772: mail  - syslog,errors,
2011 Feb 11 02:22:50 rosemary-122-CK-NF68->/var/log/messages
Rule: 1002 (level 2) -> 'Unknown problem somewhere in the system.'
Src IP: (none)
User: (none)
Feb 11 02:22:49 rosemary-122-CK-NF68 kernel: [12029.524164] npviewer.bin[4210]: segfault at 418 ip 00000000f6066d16 sp 00000000fff30668 error 6 in libflashplayer.so[f5df9000+b5f000]

** Alert 1297410129.1159: - syslog,sudo
2011 Feb 11 02:42:09 rosemary-122-CK-NF68->/var/log/auth.log
Rule: 5402 (level 3) -> 'Successful sudo to ROOT executed'
Src IP: (none)
User: (none)
Feb 11 02:42:07 rosemary-122-CK-NF68 sudo: rosemary : TTY=pts/0 ; PWD=/home/rosemary ; USER=root ; COMMAND=/usr/bin/apt-get install vlc

** Alert 1297410175.1484: - syslog,dpkg,
2011 Feb 11 02:42:55 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2901 (level 3) -> 'New dpkg (Debian Package) requested to install.'
Src IP: (none)
User: (none)
2011-02-11 02:42:54 install liba52-0.7.4 <none> 0.7.4-14ubuntu1

** Alert 1297410177.1753: - syslog,dpkg,
2011 Feb 11 02:42:57 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2901 (level 3) -> 'New dpkg (Debian Package) requested to install.'
Src IP: (none)
User: (none)
2011-02-11 02:42:56 install libaudio2 <none> 1.9.2-3

** Alert 1297410179.2011: - syslog,dpkg,
2011 Feb 11 02:42:59 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2901 (level 3) -> 'New dpkg (Debian Package) requested to install.'
Src IP: (none)
User: (none)
2011-02-11 02:42:58 install libavutil50 <none> 4:0.6-2ubuntu6

** Alert 1297410179.2278: - syslog,dpkg,
2011 Feb 11 02:42:59 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2901 (level 3) -> 'New dpkg (Debian Package) requested to install.'
Src IP: (none)
User: (none)
2011-02-11 02:42:59 install libgsm1 <none> 1.0.13-3

** Alert 1297410181.2535: - syslog,dpkg,
2011 Feb 11 02:43:01 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2901 (level 3) -> 'New dpkg (Debian Package) requested to install.'
Src IP: (none)
User: (none)
2011-02-11 02:43:00 install libschroedinger-1.0-0 <none> 1.0.9.really-1build1

** Alert 1297410181.2818: - syslog,dpkg,
2011 Feb 11 02:43:01 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2901 (level 3) -> 'New dpkg (Debian Package) requested to install.'
Src IP: (none)
User: (none)
2011-02-11 02:43:01 install libva1 <none> 1.0.1-3

** Alert 1297410183.3073: - syslog,dpkg,
2011 Feb 11 02:43:03 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2901 (level 3) -> 'New dpkg (Debian Package) requested to install.'
Src IP: (none)
User: (none)
2011-02-11 02:43:02 install libvpx0 <none> 0.9.2-1ubuntu0.1

** Alert 1297410183.3338: - syslog,dpkg,
2011 Feb 11 02:43:03 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2901 (level 3) -> 'New dpkg (Debian Package) requested to install.'
Src IP: (none)
User: (none)
2011-02-11 02:43:03 install libavcodec52 <none> 4:0.6-2ubuntu6

** Alert 1297410185.3606: - syslog,dpkg,
2011 Feb 11 02:43:05 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2901 (level 3) -> 'New dpkg (Debian Package) requested to install.'
Src IP: (none)
User: (none)
2011-02-11 02:43:04 install libavformat52 <none> 4:0.6-2ubuntu6

** Alert 1297410187.3875: - syslog,dpkg,
2011 Feb 11 02:43:07 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2901 (level 3) -> 'New dpkg (Debian Package) requested to install.'
Src IP: (none)
User: (none)
2011-02-11 02:43:05 install libcddb2 <none> 1.3.2-2fakesync1

** Alert 1297410187.4141: - syslog,dpkg,
2011 Feb 11 02:43:07 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2901 (level 3) -> 'New dpkg (Debian Package) requested to install.'
Src IP: (none)
User: (none)
2011-02-11 02:43:06 install libdirac-encoder0 <none> 1.0.2-3

** Alert 1297410189.4407: - syslog,dpkg,
2011 Feb 11 02:43:09 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2901 (level 3) -> 'New dpkg (Debian Package) requested to install.'
Src IP: (none)
User: (none)
2011-02-11 02:43:07 install libdvbpsi6 <none> 0.1.7-1

** Alert 1297410189.4666: - syslog,dpkg,
2011 Feb 11 02:43:09 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2901 (level 3) -> 'New dpkg (Debian Package) requested to install.'
Src IP: (none)
User: (none)
2011-02-11 02:43:08 install libdvdread4 <none> 4.1.3-10ubuntu2

** Alert 1297410191.4934: - syslog,dpkg,
2011 Feb 11 02:43:11 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2901 (level 3) -> 'New dpkg (Debian Package) requested to install.'
Src IP: (none)
User: (none)
2011-02-11 02:43:09 install libdvdnav4 <none> 4.1.3-7

** Alert 1297410191.5193: - syslog,dpkg,
2011 Feb 11 02:43:11 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2901 (level 3) -> 'New dpkg (Debian Package) requested to install.'
Src IP: (none)
User: (none)
2011-02-11 02:43:11 install libebml2 <none> 1.0.0+dfsg-0ubuntu1

** Alert 1297410193.5462: - syslog,dpkg,
2011 Feb 11 02:43:13 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2901 (level 3) -> 'New dpkg (Debian Package) requested to install.'
Src IP: (none)
User: (none)
2011-02-11 02:43:12 install libenca0 <none> 1.13-2

** Alert 1297410193.5718: - syslog,dpkg,
2011 Feb 11 02:43:13 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2901 (level 3) -> 'New dpkg (Debian Package) requested to install.'
Src IP: (none)
User: (none)
2011-02-11 02:43:13 install libfaad2 <none> 2.7-4

** Alert 1297410195.5973: - syslog,dpkg,
2011 Feb 11 02:43:15 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2901 (level 3) -> 'New dpkg (Debian Package) requested to install.'
Src IP: (none)
User: (none)
2011-02-11 02:43:14 install libiso9660-7 <none> 0.81-4

** Alert 1297410195.6233: - syslog,dpkg,
2011 Feb 11 02:43:15 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2901 (level 3) -> 'New dpkg (Debian Package) requested to install.'
Src IP: (none)
User: (none)
2011-02-11 02:43:15 install libkate1 <none> 0.3.7-3

** Alert 1297410197.6490: - syslog,dpkg,
2011 Feb 11 02:43:17 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2901 (level 3) -> 'New dpkg (Debian Package) requested to install.'
Src IP: (none)
User: (none)
2011-02-11 02:43:16 install libmad0 <none> 0.15.1b-4ubuntu2

** Alert 1297410197.6755: - syslog,dpkg,
2011 Feb 11 02:43:17 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2901 (level 3) -> 'New dpkg (Debian Package) requested to install.'
Src IP: (none)
User: (none)
2011-02-11 02:43:17 install libmatroska2 <none> 1.0.0+repack-0ubuntu1

** Alert 1297410199.7030: - syslog,dpkg,
2011 Feb 11 02:43:19 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2901 (level 3) -> 'New dpkg (Debian Package) requested to install.'
Src IP: (none)
User: (none)
2011-02-11 02:43:18 install libmng1 <none> 1.0.10-1

** Alert 1297410201.7287: - syslog,dpkg,
2011 Feb 11 02:43:21 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2901 (level 3) -> 'New dpkg (Debian Package) requested to install.'
Src IP: (none)
User: (none)
2011-02-11 02:43:19 install libmodplug1 <none> 1:0.8.8.1-1ubuntu1

** Alert 1297410201.7558: - syslog,dpkg,
2011 Feb 11 02:43:21 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2901 (level 3) -> 'New dpkg (Debian Package) requested to install.'
Src IP: (none)
User: (none)
2011-02-11 02:43:20 install libmpcdec6 <none> 2:0.1~r459-1

** Alert 1297410201.7822: - syslog,dpkg,
2011 Feb 11 02:43:21 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2901 (level 3) -> 'New dpkg (Debian Package) requested to install.'
Src IP: (none)
User: (none)
2011-02-11 02:43:21 install libmpeg2-4 <none> 0.4.1-3

** Alert 1297410203.8081: - syslog,dpkg,
2011 Feb 11 02:43:23 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2901 (level 3) -> 'New dpkg (Debian Package) requested to install.'
Src IP: (none)
User: (none)
2011-02-11 02:43:22 install libpostproc51 <none> 4:0.6-2ubuntu6

** Alert 1297410205.8350: - syslog,dpkg,
2011 Feb 11 02:43:25 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2901 (level 3) -> 'New dpkg (Debian Package) requested to install.'
Src IP: (none)
User: (none)
2011-02-11 02:43:23 install libqtcore4 <none> 4:4.7.0-0ubuntu4.2

** Alert 1297410205.8620: - syslog,dpkg,
2011 Feb 11 02:43:25 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2901 (level 3) -> 'New dpkg (Debian Package) requested to install.'
Src IP: (none)
User: (none)
2011-02-11 02:43:25 install libqt4-xml <none> 4:4.7.0-0ubuntu4.2

** Alert 1297410207.8890: - syslog,dpkg,
2011 Feb 11 02:43:27 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2901 (level 3) -> 'New dpkg (Debian Package) requested to install.'
Src IP: (none)
User: (none)
2011-02-11 02:43:26 install libqt4-dbus <none> 4:4.7.0-0ubuntu4.2

** Alert 1297410207.9161: - syslog,dpkg,
2011 Feb 11 02:43:27 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2901 (level 3) -> 'New dpkg (Debian Package) requested to install.'
Src IP: (none)
User: (none)
2011-02-11 02:43:27 install libqtgui4 <none> 4:4.7.0-0ubuntu4.2

** Alert 1297410209.9430: - syslog,dpkg,
2011 Feb 11 02:43:29 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2901 (level 3) -> 'New dpkg (Debian Package) requested to install.'
Src IP: (none)
User: (none)
2011-02-11 02:43:29 install libsdl-image1.2 <none> 1.2.10-2

** Alert 1297410211.9695: - syslog,dpkg,
2011 Feb 11 02:43:31 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2901 (level 3) -> 'New dpkg (Debian Package) requested to install.'
Src IP: (none)
User: (none)
2011-02-11 02:43:30 install libswscale0 <none> 4:0.6-2ubuntu6

** Alert 1297410211.9962: - syslog,dpkg,
2011 Feb 11 02:43:31 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2901 (level 3) -> 'New dpkg (Debian Package) requested to install.'
Src IP: (none)
User: (none)
2011-02-11 02:43:31 install libtar <none> 1.2.11-6

** Alert 1297410213.10218: - syslog,dpkg,
2011 Feb 11 02:43:33 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2901 (level 3) -> 'New dpkg (Debian Package) requested to install.'
Src IP: (none)
User: (none)
2011-02-11 02:43:32 install libtwolame0 <none> 0.3.12-1

** Alert 1297410213.10480: - syslog,dpkg,
2011 Feb 11 02:43:33 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2901 (level 3) -> 'New dpkg (Debian Package) requested to install.'
Src IP: (none)
User: (none)
2011-02-11 02:43:33 install libva-x11-1 <none> 1.0.1-3

** Alert 1297410215.10741: - syslog,dpkg,
2011 Feb 11 02:43:35 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2901 (level 3) -> 'New dpkg (Debian Package) requested to install.'
Src IP: (none)
User: (none)
2011-02-11 02:43:34 install libvcdinfo0 <none> 0.7.23-4ubuntu2

** Alert 1297410215.11010: - syslog,dpkg,
2011 Feb 11 02:43:35 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2901 (level 3) -> 'New dpkg (Debian Package) requested to install.'
Src IP: (none)
User: (none)
2011-02-11 02:43:35 install vlc-data <none> 1.1.4-1ubuntu1.3

** Alert 1297410219.11277: - syslog,dpkg,
2011 Feb 11 02:43:39 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2901 (level 3) -> 'New dpkg (Debian Package) requested to install.'
Src IP: (none)
User: (none)
2011-02-11 02:43:37 install libvlccore4 <none> 1.1.4-1ubuntu1.3

** Alert 1297410219.11547: - syslog,dpkg,
2011 Feb 11 02:43:39 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2901 (level 3) -> 'New dpkg (Debian Package) requested to install.'
Src IP: (none)
User: (none)
2011-02-11 02:43:39 install libvlc5 <none> 1.1.4-1ubuntu1.3

** Alert 1297410221.11813: - syslog,dpkg,
2011 Feb 11 02:43:41 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2901 (level 3) -> 'New dpkg (Debian Package) requested to install.'
Src IP: (none)
User: (none)
2011-02-11 02:43:40 install libxcb-randr0 <none> 1.6-1

** Alert 1297410221.12074: - syslog,dpkg,
2011 Feb 11 02:43:41 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2901 (level 3) -> 'New dpkg (Debian Package) requested to install.'
Src IP: (none)
User: (none)
2011-02-11 02:43:41 install libxcb-xv0 <none> 1.6-1

** Alert 1297410223.12332: - syslog,dpkg,
2011 Feb 11 02:43:43 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2901 (level 3) -> 'New dpkg (Debian Package) requested to install.'
Src IP: (none)
User: (none)
2011-02-11 02:43:42 install libass4 <none> 0.9.9-1fakesync1

** Alert 1297410223.12598: - syslog,dpkg,
2011 Feb 11 02:43:43 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2901 (level 3) -> 'New dpkg (Debian Package) requested to install.'
Src IP: (none)
User: (none)
2011-02-11 02:43:43 install libdc1394-22 <none> 2.1.2-3

** Alert 1297410225.12860: - syslog,dpkg,
2011 Feb 11 02:43:45 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2901 (level 3) -> 'New dpkg (Debian Package) requested to install.'
Src IP: (none)
User: (none)
2011-02-11 02:43:44 install libdca0 <none> 0.0.5-3

** Alert 1297410225.13117: - syslog,dpkg,
2011 Feb 11 02:43:45 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2901 (level 3) -> 'New dpkg (Debian Package) requested to install.'
Src IP: (none)
User: (none)
2011-02-11 02:43:45 install libupnp3 <none> 1:1.6.6-5

** Alert 1297410227.13377: - syslog,dpkg,
2011 Feb 11 02:43:47 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2901 (level 3) -> 'New dpkg (Debian Package) requested to install.'
Src IP: (none)
User: (none)
2011-02-11 02:43:46 install libx264-98 <none> 2:0.98.1653+git88b90d9-3ubuntu2

** Alert 1297410227.13661: - syslog,dpkg,
2011 Feb 11 02:43:47 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2901 (level 3) -> 'New dpkg (Debian Package) requested to install.'
Src IP: (none)
User: (none)
2011-02-11 02:43:47 install vlc-nox <none> 1.1.4-1ubuntu1.3

** Alert 1297410229.13927: - syslog,dpkg,
2011 Feb 11 02:43:49 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2901 (level 3) -> 'New dpkg (Debian Package) requested to install.'
Src IP: (none)
User: (none)
2011-02-11 02:43:49 install libxcb-keysyms1 <none> 0.3.6-1build1

** Alert 1297410231.14198: - syslog,dpkg,
2011 Feb 11 02:43:51 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2901 (level 3) -> 'New dpkg (Debian Package) requested to install.'
Src IP: (none)
User: (none)
2011-02-11 02:43:50 install vlc <none> 1.1.4-1ubuntu1.3

** Alert 1297410233.14460: - syslog,dpkg,
2011 Feb 11 02:43:53 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2901 (level 3) -> 'New dpkg (Debian Package) requested to install.'
Src IP: (none)
User: (none)
2011-02-11 02:43:52 install vlc-plugin-notify <none> 1.1.4-1ubuntu1.3

** Alert 1297410233.14736: - syslog,dpkg,
2011 Feb 11 02:43:53 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2901 (level 3) -> 'New dpkg (Debian Package) requested to install.'
Src IP: (none)
User: (none)
2011-02-11 02:43:53 install vlc-plugin-pulse <none> 1.1.4-1ubuntu1.3

** Alert 1297410235.15011: mail  - syslog,dpkg,config_changed,
2011 Feb 11 02:43:55 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 02:43:55 status installed hicolor-icon-theme 0.11-1

** Alert 1297410237.15290: mail  - syslog,dpkg,config_changed,
2011 Feb 11 02:43:57 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 02:43:56 status installed man-db 2.5.7-4

** Alert 1297410237.15558: mail  - syslog,dpkg,config_changed,
2011 Feb 11 02:43:57 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 02:43:56 status installed desktop-file-utils 0.16-0ubuntu4

** Alert 1297410237.15844: mail  - syslog,dpkg,config_changed,
2011 Feb 11 02:43:57 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 02:43:57 status installed python-gmenu 2.30.4-0ubuntu1

** Alert 1297410239.16126: mail  - syslog,dpkg,config_changed,
2011 Feb 11 02:43:59 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 02:43:58 status installed menu 2.1.44ubuntu1

** Alert 1297410241.16398: mail  - syslog,dpkg,config_changed,
2011 Feb 11 02:44:01 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 02:44:00 status installed python-support 1.0.9ubuntu1

** Alert 1297410241.16679: mail  - syslog,dpkg,config_changed,
2011 Feb 11 02:44:01 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 02:44:01 status installed liba52-0.7.4 0.7.4-14ubuntu1

** Alert 1297410241.16961: mail  - syslog,dpkg,config_changed,
2011 Feb 11 02:44:01 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 02:44:01 status installed libaudio2 1.9.2-3

** Alert 1297410243.17232: mail  - syslog,dpkg,config_changed,
2011 Feb 11 02:44:03 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 02:44:02 status installed libavutil50 4:0.6-2ubuntu6

** Alert 1297410243.17512: mail  - syslog,dpkg,config_changed,
2011 Feb 11 02:44:03 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 02:44:02 status installed libgsm1 1.0.13-3

** Alert 1297410243.17782: mail  - syslog,dpkg,config_changed,
2011 Feb 11 02:44:03 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 02:44:02 status installed libschroedinger-1.0-0 1.0.9.really-1build1

** Alert 1297410243.18078: mail  - syslog,dpkg,config_changed,
2011 Feb 11 02:44:03 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 02:44:02 status installed libva1 1.0.1-3

** Alert 1297410243.18346: mail  - syslog,dpkg,config_changed,
2011 Feb 11 02:44:03 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 02:44:03 status installed libvpx0 0.9.2-1ubuntu0.1

** Alert 1297410243.18624: mail  - syslog,dpkg,config_changed,
2011 Feb 11 02:44:03 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 02:44:03 status installed libavcodec52 4:0.6-2ubuntu6

** Alert 1297410243.18905: mail  - syslog,dpkg,config_changed,
2011 Feb 11 02:44:03 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 02:44:03 status installed libavformat52 4:0.6-2ubuntu6

** Alert 1297410245.19187: mail  - syslog,dpkg,config_changed,
2011 Feb 11 02:44:05 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 02:44:03 status installed libcddb2 1.3.2-2fakesync1

** Alert 1297410245.19466: mail  - syslog,dpkg,config_changed,
2011 Feb 11 02:44:05 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 02:44:04 status installed libdirac-encoder0 1.0.2-3

** Alert 1297410245.19745: mail  - syslog,dpkg,config_changed,
2011 Feb 11 02:44:05 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 02:44:04 status installed libdvbpsi6 0.1.7-1

** Alert 1297410245.20017: mail  - syslog,dpkg,config_changed,
2011 Feb 11 02:44:05 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 02:44:04 status installed libdvdread4 4.1.3-10ubuntu2

** Alert 1297410245.20298: mail  - syslog,dpkg,config_changed,
2011 Feb 11 02:44:05 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 02:44:04 status installed libdvdnav4 4.1.3-7

** Alert 1297410245.20570: mail  - syslog,dpkg,config_changed,
2011 Feb 11 02:44:05 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 02:44:05 status installed libebml2 1.0.0+dfsg-0ubuntu1

** Alert 1297410245.20852: mail  - syslog,dpkg,config_changed,
2011 Feb 11 02:44:05 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 02:44:05 status installed libenca0 1.13-2

** Alert 1297410245.21121: mail  - syslog,dpkg,config_changed,
2011 Feb 11 02:44:05 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 02:44:05 status installed libfaad2 2.7-4

** Alert 1297410247.21389: mail  - syslog,dpkg,config_changed,
2011 Feb 11 02:44:07 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 02:44:05 status installed libiso9660-7 0.81-4

** Alert 1297410247.21662: mail  - syslog,dpkg,config_changed,
2011 Feb 11 02:44:07 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 02:44:06 status installed libkate1 0.3.7-3

** Alert 1297410247.21932: mail  - syslog,dpkg,config_changed,
2011 Feb 11 02:44:07 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 02:44:06 status installed libmad0 0.15.1b-4ubuntu2

** Alert 1297410247.22210: mail  - syslog,dpkg,config_changed,
2011 Feb 11 02:44:07 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 02:44:06 status installed libmatroska2 1.0.0+repack-0ubuntu1

** Alert 1297410247.22498: mail  - syslog,dpkg,config_changed,
2011 Feb 11 02:44:07 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 02:44:06 status installed libmng1 1.0.10-1

** Alert 1297410247.22768: mail  - syslog,dpkg,config_changed,
2011 Feb 11 02:44:07 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 02:44:07 status installed libmodplug1 1:0.8.8.1-1ubuntu1

** Alert 1297410247.23052: mail  - syslog,dpkg,config_changed,
2011 Feb 11 02:44:07 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 02:44:07 status installed libmpcdec6 2:0.1~r459-1

** Alert 1297410247.23329: mail  - syslog,dpkg,config_changed,
2011 Feb 11 02:44:07 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 02:44:07 status installed libmpeg2-4 0.4.1-3

** Alert 1297410249.23601: mail  - syslog,dpkg,config_changed,
2011 Feb 11 02:44:09 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 02:44:07 status installed libpostproc51 4:0.6-2ubuntu6

** Alert 1297410249.23883: mail  - syslog,dpkg,config_changed,
2011 Feb 11 02:44:09 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 02:44:08 status installed libqtcore4 4:4.7.0-0ubuntu4.2

** Alert 1297410249.24166: mail  - syslog,dpkg,config_changed,
2011 Feb 11 02:44:09 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 02:44:08 status installed libqt4-xml 4:4.7.0-0ubuntu4.2

** Alert 1297410249.24449: mail  - syslog,dpkg,config_changed,
2011 Feb 11 02:44:09 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 02:44:08 status installed libqt4-dbus 4:4.7.0-0ubuntu4.2

** Alert 1297410249.24733: mail  - syslog,dpkg,config_changed,
2011 Feb 11 02:44:09 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 02:44:09 status installed libqtgui4 4:4.7.0-0ubuntu4.2

** Alert 1297410249.25015: mail  - syslog,dpkg,config_changed,
2011 Feb 11 02:44:09 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 02:44:09 status installed libsdl-image1.2 1.2.10-2

** Alert 1297410249.25293: mail  - syslog,dpkg,config_changed,
2011 Feb 11 02:44:09 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 02:44:09 status installed libswscale0 4:0.6-2ubuntu6

** Alert 1297410251.25573: mail  - syslog,dpkg,config_changed,
2011 Feb 11 02:44:11 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 02:44:09 status installed libtar 1.2.11-6

** Alert 1297410251.25842: mail  - syslog,dpkg,config_changed,
2011 Feb 11 02:44:11 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 02:44:10 status installed libtwolame0 0.3.12-1

** Alert 1297410251.26116: mail  - syslog,dpkg,config_changed,
2011 Feb 11 02:44:11 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 02:44:10 status installed libva-x11-1 1.0.1-3

** Alert 1297410251.26389: mail  - syslog,dpkg,config_changed,
2011 Feb 11 02:44:11 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 02:44:10 status installed libvcdinfo0 0.7.23-4ubuntu2

** Alert 1297410251.26670: mail  - syslog,dpkg,config_changed,
2011 Feb 11 02:44:11 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 02:44:11 status installed vlc-data 1.1.4-1ubuntu1.3

** Alert 1297410251.26949: mail  - syslog,dpkg,config_changed,
2011 Feb 11 02:44:11 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 02:44:11 status installed libvlccore4 1.1.4-1ubuntu1.3

** Alert 1297410251.27231: mail  - syslog,dpkg,config_changed,
2011 Feb 11 02:44:11 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 02:44:11 status installed libvlc5 1.1.4-1ubuntu1.3

** Alert 1297410251.27509: mail  - syslog,dpkg,config_changed,
2011 Feb 11 02:44:11 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 02:44:11 status installed libxcb-randr0 1.6-1

** Alert 1297410253.27782: mail  - syslog,dpkg,config_changed,
2011 Feb 11 02:44:13 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 02:44:11 status installed libxcb-xv0 1.6-1

** Alert 1297410253.28052: mail  - syslog,dpkg,config_changed,
2011 Feb 11 02:44:13 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 02:44:12 status installed libass4 0.9.9-1fakesync1

** Alert 1297410253.28330: mail  - syslog,dpkg,config_changed,
2011 Feb 11 02:44:13 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 02:44:12 status installed libdc1394-22 2.1.2-3

** Alert 1297410253.28604: mail  - syslog,dpkg,config_changed,
2011 Feb 11 02:44:13 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 02:44:12 status installed libdca0 0.0.5-3

** Alert 1297410253.28873: mail  - syslog,dpkg,config_changed,
2011 Feb 11 02:44:13 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 02:44:12 status installed libupnp3 1:1.6.6-5

** Alert 1297410253.29145: mail  - syslog,dpkg,config_changed,
2011 Feb 11 02:44:13 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 02:44:13 status installed libx264-98 2:0.98.1653+git88b90d9-3ubuntu2

** Alert 1297410257.29441: mail  - syslog,dpkg,config_changed,
2011 Feb 11 02:44:17 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 02:44:16 status installed vlc-nox 1.1.4-1ubuntu1.3

** Alert 1297410257.29719: mail  - syslog,dpkg,config_changed,
2011 Feb 11 02:44:17 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 02:44:16 status installed libxcb-keysyms1 0.3.6-1build1

** Alert 1297410257.30002: mail  - syslog,dpkg,config_changed,
2011 Feb 11 02:44:17 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 02:44:17 status installed vlc 1.1.4-1ubuntu1.3

** Alert 1297410259.30276: mail  - syslog,dpkg,config_changed,
2011 Feb 11 02:44:19 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 02:44:17 status installed vlc-plugin-notify 1.1.4-1ubuntu1.3

** Alert 1297410259.30564: mail  - syslog,dpkg,config_changed,
2011 Feb 11 02:44:19 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 02:44:17 status installed vlc-plugin-pulse 1.1.4-1ubuntu1.3

** Alert 1297410259.30851: mail  - syslog,dpkg,config_changed,
2011 Feb 11 02:44:19 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 02:44:18 status installed libc-bin 2.12.1-0ubuntu10.2

** Alert 1297410259.31132: mail  - syslog,dpkg,config_changed,
2011 Feb 11 02:44:19 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 02:44:18 status installed menu 2.1.44ubuntu1

** Alert 1297412178.31404: mail  - syslog,errors,
2011 Feb 11 03:16:18 rosemary-122-CK-NF68->/var/log/messages
Rule: 1002 (level 2) -> 'Unknown problem somewhere in the system.'
Src IP: (none)
User: (none)
Feb 11 03:16:17 rosemary-122-CK-NF68 kernel: [15237.362702] npviewer.bin[5905]: segfault at f381a0ac ip 00000000f620c8d7 sp 00000000ffceb8a0 error 4 in libflashplayer.so[f5e44000+b5f000]

** Alert 1297416744.31798: - syslog,sudo
2011 Feb 11 04:32:24 rosemary-122-CK-NF68->/var/log/auth.log
Rule: 5402 (level 3) -> 'Successful sudo to ROOT executed'
Src IP: (none)
User: (none)
Feb 11 04:32:24 rosemary-122-CK-NF68 sudo: rosemary : no tty present and no askpass program specified ; TTY=unknown ; PWD=/home/rosemary ; USER=root ; COMMAND=/var/ossec

** Alert 1297416780.32158: - syslog,sudo
2011 Feb 11 04:33:00 rosemary-122-CK-NF68->/var/log/auth.log
Rule: 5402 (level 3) -> 'Successful sudo to ROOT executed'
Src IP: (none)
User: (none)
Feb 11 04:33:00 rosemary-122-CK-NF68 sudo: rosemary : TTY=pts/0 ; PWD=/home/rosemary ; USER=root ; COMMAND=/usr/bin/gedit /var/ossec/logs/alerts/alerts.log

** Alert 1297417101.32504: mail  - syslog,errors,
2011 Feb 11 04:38:21 rosemary-122-CK-NF68->/var/log/messages
Rule: 1002 (level 2) -> 'Unknown problem somewhere in the system.'
Src IP: (none)
User: (none)
Feb 11 04:38:20 rosemary-122-CK-NF68 kernel: [20160.060322] npviewer.bin[6127]: segfault at 0 ip 00000000f625a8c1 sp 00000000ff937e00 error 4 in libflashplayer.so[f5e92000+b5f000]

** Alert 1297451861.32891: mail  - ossec,
2011 Feb 11 14:17:41 rosemary-122-CK-NF68->ossec-monitord
Rule: 502 (level 3) -> 'Ossec server started.'
Src IP: (none)
User: (none)
ossec: Ossec started.

** Alert 1297451880.33089: mail  - syslog,errors,
2011 Feb 11 14:18:00 rosemary-122-CK-NF68->/var/log/syslog
Rule: 1002 (level 2) -> 'Unknown problem somewhere in the system.'
Src IP: (none)
User: (none)
Feb 11 14:17:58 rosemary-122-CK-NF68 gdm-session-worker[1736]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed

** Alert 1297451888.33450: - pam,syslog,authentication_success,
2011 Feb 11 14:18:08 rosemary-122-CK-NF68->/var/log/auth.log
Rule: 5501 (level 3) -> 'Login session opened.'
Src IP: (none)
User: (none)
Feb 11 14:18:07 rosemary-122-CK-NF68 gdm-session-worker[1736]: pam_unix(gdm:session): session opened for user rosemary by (uid=0)

** Alert 1297451888.33782: mail  - syslog,errors,
2011 Feb 11 14:18:08 rosemary-122-CK-NF68->/var/log/syslog
Rule: 1002 (level 2) -> 'Unknown problem somewhere in the system.'
Src IP: (none)
User: (none)
Feb 11 14:18:07 rosemary-122-CK-NF68 NetworkManager[1146]: <error> [1297451887.676873] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name

** Alert 1297451888.34240: mail  - syslog,errors,
2011 Feb 11 14:18:08 rosemary-122-CK-NF68->/var/log/syslog
Rule: 1002 (level 2) -> 'Unknown problem somewhere in the system.'
Src IP: (none)
User: (none)
Feb 11 14:18:07 rosemary-122-CK-NF68 NetworkManager[1146]: <error> [1297451887.692546] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name

** Alert 1297451890.34698: mail  - syslog,errors,
2011 Feb 11 14:18:10 rosemary-122-CK-NF68->/var/log/auth.log
Rule: 1002 (level 2) -> 'Unknown problem somewhere in the system.'
Src IP: (none)
User: (none)
Feb 11 14:18:09 rosemary-122-CK-NF68 dbus-daemon: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.36" (uid=1000 pid=2131 comm="nautilus) interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply=0 destination=":1.10" (uid=0 pid=1573 comm="/usr/sbin/console-kit-daemon))

** Alert 1297452000.35246: mail  - ossec,syscheck,
2011 Feb 11 14:20:00 rosemary-122-CK-NF68->syscheck
Rule: 550 (level 7) -> 'Integrity checksum changed.'
Src IP: (none)
User: (none)
Integrity checksum changed for: '/etc/mailcap'
Size changed from '20341' to '23547'
Old md5sum was: '7375633acc830f0e2c0f77cdf7f86726'
New md5sum is : 'bf11ec43b2065fc878e68e4d66557bf7'
Old sha1sum was: '87db09bd11a1cccc97ab8f2d7c3989e366155b0e'
New sha1sum is : 'c701bb9041c2c327cf9a11c2544865b4c0d682f5'


** Alert 1297452006.35738: mail  - ossec,syscheck,
2011 Feb 11 14:20:06 rosemary-122-CK-NF68->syscheck
Rule: 552 (level 7) -> 'Integrity checksum changed again (3rd time).'
Src IP: (none)
User: (none)
Integrity checksum changed for: '/etc/ld.so.cache'
Size changed from '96045' to '99902'
Old md5sum was: '764d42ddfdae000831ffa7a3815cb68a'
New md5sum is : '9d9b12e1130282f7243d8150369668ad'
Old sha1sum was: '4e00f2d66c787e256588a57708a8c8e90add1c35'
New sha1sum is : '200eabf186cc5141ee63da2c763db9be059f6e66'


** Alert 1297452398.36251: - syslog,sudo
2011 Feb 11 14:26:38 rosemary-122-CK-NF68->/var/log/auth.log
Rule: 5402 (level 3) -> 'Successful sudo to ROOT executed'
Src IP: (none)
User: (none)
Feb 11 14:26:38 rosemary-122-CK-NF68 sudo: rosemary : no tty present and no askpass program specified ; TTY=unknown ; PWD=/home/rosemary ; USER=root ; COMMAND=/home/rosemary/Downloads

** Alert 1297452448.36625: - syslog,sudo
2011 Feb 11 14:27:28 rosemary-122-CK-NF68->/var/log/auth.log
Rule: 5402 (level 3) -> 'Successful sudo to ROOT executed'
Src IP: (none)
User: (none)
Feb 11 14:26:44 rosemary-122-CK-NF68 sudo: rosemary : no tty present and no askpass program specified ; TTY=unknown ; PWD=/home/rosemary ; USER=root ; COMMAND=/home/rosemary/Downloads

** Alert 1297453157.36999: - ossec,
2011 Feb 11 14:39:17 rosemary-122-CK-NF68->ossec-logcollector
Rule: 591 (level 3) -> 'Log file rotated.'
Src IP: (none)
User: (none)
ossec: File rotated (inode changed): '/var/log/syslog'.

** Alert 1297453177.37225: mail  - syslog,dpkg,config_changed,
2011 Feb 11 14:39:37 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 14:39:35 status installed man-db 2.5.7-4

** Alert 1297453177.37493: mail  - syslog,dpkg,config_changed,
2011 Feb 11 14:39:37 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 14:39:36 status installed mount 2.17.2-0ubuntu1.10.10.2

** Alert 1297453181.37776: mail  - syslog,dpkg,config_changed,
2011 Feb 11 14:39:41 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 14:39:41 status installed ureadahead 0.100.0-8

** Alert 1297453183.38050: mail  - syslog,dpkg,config_changed,
2011 Feb 11 14:39:43 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 14:39:42 status installed man-db 2.5.7-4

** Alert 1297453183.38318: mail  - syslog,dpkg,config_changed,
2011 Feb 11 14:39:43 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 14:39:42 status installed install-info 4.13a.dfsg.1-5ubuntu1

** Alert 1297453185.38606: mail  - syslog,dpkg,config_changed,
2011 Feb 11 14:39:45 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 14:39:43 status installed util-linux 2.17.2-0ubuntu1.10.10.2

** Alert 1297453189.38894: mail  - syslog,dpkg,config_changed,
2011 Feb 11 14:39:49 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 14:39:48 status installed man-db 2.5.7-4

** Alert 1297453189.39162: mail  - syslog,dpkg,config_changed,
2011 Feb 11 14:39:49 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 14:39:49 status installed bsdutils 1:2.17.2-0ubuntu1.10.10.2

** Alert 1297453193.39450: mail  - syslog,dpkg,config_changed,
2011 Feb 11 14:39:53 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 14:39:52 status installed libuuid1 2.17.2-0ubuntu1.10.10.2

** Alert 1297453193.39736: mail  - syslog,dpkg,config_changed,
2011 Feb 11 14:39:53 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 14:39:52 status installed libc-bin 2.12.1-0ubuntu10.2

** Alert 1297453197.40017: mail  - syslog,dpkg,config_changed,
2011 Feb 11 14:39:57 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 14:39:56 status installed libblkid1 2.17.2-0ubuntu1.10.10.2

** Alert 1297453197.40304: mail  - syslog,dpkg,config_changed,
2011 Feb 11 14:39:57 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 14:39:56 status installed libc-bin 2.12.1-0ubuntu10.2

** Alert 1297453217.40585: mail  - syslog,dpkg,config_changed,
2011 Feb 11 14:40:17 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 14:40:16 status installed man-db 2.5.7-4

** Alert 1297453217.40853: mail  - syslog,dpkg,config_changed,
2011 Feb 11 14:40:17 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 14:40:16 status installed ureadahead 0.100.0-8

** Alert 1297453219.41127: mail  - syslog,dpkg,config_changed,
2011 Feb 11 14:40:19 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 14:40:17 status installed doc-base 0.9.5

** Alert 1297453221.41395: mail  - syslog,dpkg,config_changed,
2011 Feb 11 14:40:21 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 14:40:20 status installed fontconfig 2.8.0-2ubuntu1

** Alert 1297453227.41674: mail  - syslog,dpkg,config_changed,
2011 Feb 11 14:40:27 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 14:40:25 status installed exim4-config 4.72-1ubuntu1.1

** Alert 1297453227.41956: mail  - syslog,dpkg,config_changed,
2011 Feb 11 14:40:27 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 14:40:26 status installed exim4-base 4.72-1ubuntu1.1

** Alert 1297453227.42236: mail  - syslog,dpkg,config_changed,
2011 Feb 11 14:40:27 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 14:40:27 status installed exim4-daemon-light 4.72-1ubuntu1.1

** Alert 1297453229.42524: mail  - syslog,dpkg,config_changed,
2011 Feb 11 14:40:29 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 14:40:28 status installed exim4 4.72-1ubuntu1.1

** Alert 1297453229.42799: mail  - syslog,dpkg,config_changed,
2011 Feb 11 14:40:29 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 14:40:28 status installed libfuse2 2.8.4-1ubuntu1.2

** Alert 1297453229.43078: mail  - syslog,dpkg,config_changed,
2011 Feb 11 14:40:29 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 14:40:28 status installed fuse-utils 2.8.4-1ubuntu1.2

** Alert 1297453229.43359: mail  - syslog,dpkg,config_changed,
2011 Feb 11 14:40:29 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 14:40:29 status installed uuid-runtime 2.17.2-0ubuntu1.10.10.2

** Alert 1297453229.43649: mail  - syslog,dpkg,config_changed,
2011 Feb 11 14:40:29 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 14:40:29 status installed ttf-ubuntu-font-family 0.70.1-0ubuntu1~maverick2

** Alert 1297453231.43951: mail  - syslog,dpkg,config_changed,
2011 Feb 11 14:40:31 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 14:40:29 status installed xdg-utils 1.0.2+cvs20100307-1ubuntu0.2

** Alert 1297453231.44243: mail  - syslog,dpkg,config_changed,
2011 Feb 11 14:40:31 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 14:40:29 status installed libc-bin 2.12.1-0ubuntu10.2

** Alert 1297453243.44524: mail  - syslog,dpkg,config_changed,
2011 Feb 11 14:40:43 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 14:40:42 status installed initramfs-tools 0.98.1ubuntu6

** Alert 1297453621.44807: mail  - syslog,errors,
2011 Feb 11 14:47:01 rosemary-122-CK-NF68->/var/log/messages
Rule: 1002 (level 2) -> 'Unknown problem somewhere in the system.'
Src IP: (none)
User: (none)
Feb 11 14:47:01 rosemary-122-CK-NF68 kernel: [ 1788.184455] npviewer.bin[2342]: segfault at f37b40ac ip 00000000f61cd8d7 sp 00000000ffd53db0 error 4 in libflashplayer.so[f5e05000+b5f000]

** Alert 1297453653.45201: mail  - syslog,errors,
2011 Feb 11 14:47:33 rosemary-122-CK-NF68->/var/log/messages
Rule: 1002 (level 2) -> 'Unknown problem somewhere in the system.'
Src IP: (none)
User: (none)
Feb 11 14:47:33 rosemary-122-CK-NF68 kernel: [ 1820.294918] npviewer.bin[13589]: segfault at f57eb0b4 ip 00000000f62278b3 sp 00000000ff928680 error 4 in libflashplayer.so[f5e5f000+b5f000]

** Alert 1297453713.45596: mail  - syslog,errors,
2011 Feb 11 14:48:33 rosemary-122-CK-NF68->/var/log/messages
Rule: 1002 (level 2) -> 'Unknown problem somewhere in the system.'
Src IP: (none)
User: (none)
Feb 11 14:48:32 rosemary-122-CK-NF68 kernel: [ 1879.447456] npviewer.bin[13615]: segfault at f2a230ac ip 00000000f61a08d7 sp 00000000ffdf1dd0 error 4 in libflashplayer.so[f5dd8000+b5f000]

** Alert 1297453727.45991: mail  - syslog,errors,
2011 Feb 11 14:48:47 rosemary-122-CK-NF68->/var/log/messages
Rule: 1002 (level 2) -> 'Unknown problem somewhere in the system.'
Src IP: (none)
User: (none)
Feb 11 14:48:46 rosemary-122-CK-NF68 kernel: [ 1893.009504] npviewer.bin[13666]: segfault at 0 ip 00000000f624e8c1 sp 00000000ffac03d0 error 4 in libflashplayer.so[f5e86000+b5f000]

** Alert 1297453727.46379: mail  - syslog,errors,
2011 Feb 11 14:48:47 rosemary-122-CK-NF68->/var/log/syslog
Rule: 1002 (level 2) -> 'Unknown problem somewhere in the system.'
Src IP: (none)
User: (none)
Feb 11 14:48:46 rosemary-122-CK-NF68 kernel: [ 1893.009504] npviewer.bin[13666]: segfault at 0 ip 00000000f624e8c1 sp 00000000ffac03d0 error 4 in libflashplayer.so[f5e86000+b5f000]

** Alert 1297458000.46765: mail  - syslog,errors,
2011 Feb 11 16:00:00 rosemary-122-CK-NF68->/var/log/messages
Rule: 1002 (level 2) -> 'Unknown problem somewhere in the system.'
Src IP: (none)
User: (none)
Feb 11 15:59:58 rosemary-122-CK-NF68 kernel: [ 6165.415734] npviewer.bin[13720]: segfault at 80000000 ip 0000000080000000 sp 00000000ffcec3cc error 14

** Alert 1297458010.47123: mail  - syslog,errors,
2011 Feb 11 16:00:10 rosemary-122-CK-NF68->/var/log/messages
Rule: 1002 (level 2) -> 'Unknown problem somewhere in the system.'
Src IP: (none)
User: (none)
Feb 11 16:00:08 rosemary-122-CK-NF68 kernel: [ 6174.837128] npviewer.bin[14128]: segfault at 0 ip 00000000f61e58c1 sp 00000000ffd4f7c0 error 4 in libflashplayer.so[f5e1d000+b5f000]

** Alert 1297460848.47511: - syslog,sudo
2011 Feb 11 16:47:28 rosemary-122-CK-NF68->/var/log/auth.log
Rule: 5402 (level 3) -> 'Successful sudo to ROOT executed'
Src IP: (none)
User: (none)
Feb 11 16:47:27 rosemary-122-CK-NF68 sudo: rosemary : TTY=unknown ; PWD=/home/rosemary ; USER=root ; COMMAND=/usr/sbin/synaptic

** Alert 1297461060.47829: - syslog,dpkg,
2011 Feb 11 16:51:00 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2901 (level 3) -> 'New dpkg (Debian Package) requested to install.'
Src IP: (none)
User: (none)
2011-02-11 16:50:59 install ttf-symbol-replacement <none> 1.2.2-0ubuntu2~maverick2

** Alert 1297461062.48118: - syslog,dpkg,
2011 Feb 11 16:51:02 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2901 (level 3) -> 'New dpkg (Debian Package) requested to install.'
Src IP: (none)
User: (none)
2011-02-11 16:51:01 install lib32nss-mdns <none> 0.10-3ubuntu4

** Alert 1297461066.48387: - syslog,dpkg,
2011 Feb 11 16:51:06 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2901 (level 3) -> 'New dpkg (Debian Package) requested to install.'
Src IP: (none)
User: (none)
2011-02-11 16:51:05 install wine1.2 <none> 1.2.2-0ubuntu2~maverick2

** Alert 1297461074.48661: - syslog,dpkg,
2011 Feb 11 16:51:14 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2901 (level 3) -> 'New dpkg (Debian Package) requested to install.'
Src IP: (none)
User: (none)
2011-02-11 16:51:13 install wine1.2-gecko <none> 1.0.0-0ubuntu4

** Alert 1297461076.48931: - syslog,dpkg,
2011 Feb 11 16:51:16 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2901 (level 3) -> 'New dpkg (Debian Package) requested to install.'
Src IP: (none)
User: (none)
2011-02-11 16:51:15 install cabextract <none> 1.3-1

** Alert 1297461078.49189: - syslog,dpkg,
2011 Feb 11 16:51:18 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2901 (level 3) -> 'New dpkg (Debian Package) requested to install.'
Src IP: (none)
User: (none)
2011-02-11 16:51:17 install icoutils <none> 0.29.1-0ubuntu1

** Alert 1297461078.49455: - syslog,dpkg,
2011 Feb 11 16:51:18 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2901 (level 3) -> 'New dpkg (Debian Package) requested to install.'
Src IP: (none)
User: (none)
2011-02-11 16:51:18 install imagemagick <none> 7:6.6.2.6-1ubuntu1.1

** Alert 1297461080.49729: - syslog,dpkg,
2011 Feb 11 16:51:20 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2901 (level 3) -> 'New dpkg (Debian Package) requested to install.'
Src IP: (none)
User: (none)
2011-02-11 16:51:20 install libcdt4 <none> 2.26.3-4

** Alert 1297461082.49987: - syslog,dpkg,
2011 Feb 11 16:51:22 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2901 (level 3) -> 'New dpkg (Debian Package) requested to install.'
Src IP: (none)
User: (none)
2011-02-11 16:51:22 install libgraph4 <none> 2.26.3-4

** Alert 1297461084.50247: - syslog,dpkg,
2011 Feb 11 16:51:24 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2901 (level 3) -> 'New dpkg (Debian Package) requested to install.'
Src IP: (none)
User: (none)
2011-02-11 16:51:24 install libpathplan4 <none> 2.26.3-4

** Alert 1297461086.50510: - syslog,dpkg,
2011 Feb 11 16:51:26 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2901 (level 3) -> 'New dpkg (Debian Package) requested to install.'
Src IP: (none)
User: (none)
2011-02-11 16:51:26 install libxdot4 <none> 2.26.3-4

** Alert 1297461088.50769: - syslog,dpkg,
2011 Feb 11 16:51:28 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2901 (level 3) -> 'New dpkg (Debian Package) requested to install.'
Src IP: (none)
User: (none)
2011-02-11 16:51:28 install libgvc5 <none> 2.26.3-4

** Alert 1297461090.51027: - syslog,dpkg,
2011 Feb 11 16:51:30 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2901 (level 3) -> 'New dpkg (Debian Package) requested to install.'
Src IP: (none)
User: (none)
2011-02-11 16:51:29 install libilmbase6 <none> 1.0.1-3build2

** Alert 1297461092.51294: - syslog,dpkg,
2011 Feb 11 16:51:32 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2901 (level 3) -> 'New dpkg (Debian Package) requested to install.'
Src IP: (none)
User: (none)
2011-02-11 16:51:31 install libopenexr6 <none> 1.6.1-4.1

** Alert 1297461092.51557: - syslog,dpkg,
2011 Feb 11 16:51:32 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2901 (level 3) -> 'New dpkg (Debian Package) requested to install.'
Src IP: (none)
User: (none)
2011-02-11 16:51:32 install libmagickcore3-extra <none> 7:6.6.2.6-1ubuntu1.1

** Alert 1297461094.51840: - syslog,dpkg,
2011 Feb 11 16:51:34 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2901 (level 3) -> 'New dpkg (Debian Package) requested to install.'
Src IP: (none)
User: (none)
2011-02-11 16:51:34 install libnetpbm10 <none> 2:10.0-12.2

** Alert 1297461096.52105: - syslog,dpkg,
2011 Feb 11 16:51:36 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2901 (level 3) -> 'New dpkg (Debian Package) requested to install.'
Src IP: (none)
User: (none)
2011-02-11 16:51:35 install netpbm <none> 2:10.0-12.2

** Alert 1297461098.52365: - syslog,dpkg,
2011 Feb 11 16:51:38 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2901 (level 3) -> 'New dpkg (Debian Package) requested to install.'
Src IP: (none)
User: (none)
2011-02-11 16:51:37 install ttf-droid <none> 1.00~b112+dfsg+1-0ubuntu1

** Alert 1297461100.52642: - syslog,dpkg,
2011 Feb 11 16:51:40 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2901 (level 3) -> 'New dpkg (Debian Package) requested to install.'
Src IP: (none)
User: (none)
2011-02-11 16:51:39 install ttf-mscorefonts-installer <none> 3.2ubuntu2

** Alert 1297461114.52920: - syslog,dpkg,
2011 Feb 11 16:51:54 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2901 (level 3) -> 'New dpkg (Debian Package) requested to install.'
Src IP: (none)
User: (none)
2011-02-11 16:51:54 install ttf-umefont <none> 416-2

** Alert 1297461125.53179: - syslog,dpkg,
2011 Feb 11 16:52:05 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2901 (level 3) -> 'New dpkg (Debian Package) requested to install.'
Src IP: (none)
User: (none)
2011-02-11 16:52:03 install winbind <none> 2:3.5.4~dfsg-1ubuntu8.2

** Alert 1297461127.53452: - syslog,dpkg,
2011 Feb 11 16:52:07 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2901 (level 3) -> 'New dpkg (Debian Package) requested to install.'
Src IP: (none)
User: (none)
2011-02-11 16:52:06 install wine <none> 1.2.2-0ubuntu2~maverick2

** Alert 1297461129.53723: - syslog,dpkg,
2011 Feb 11 16:52:09 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2901 (level 3) -> 'New dpkg (Debian Package) requested to install.'
Src IP: (none)
User: (none)
2011-02-11 16:52:08 install gnome-exe-thumbnailer <none> 0.7-0ubuntu1

** Alert 1297461133.53999: mail  - syslog,dpkg,config_changed,
2011 Feb 11 16:52:13 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 16:52:12 status installed fontconfig 2.8.0-2ubuntu1

** Alert 1297461137.54278: mail  - syslog,dpkg,config_changed,
2011 Feb 11 16:52:17 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 16:52:15 status installed man-db 2.5.7-4

** Alert 1297461139.54546: mail  - syslog,dpkg,config_changed,
2011 Feb 11 16:52:19 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 16:52:17 status installed hicolor-icon-theme 0.11-1

** Alert 1297461139.54825: mail  - syslog,dpkg,config_changed,
2011 Feb 11 16:52:19 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 16:52:18 status installed desktop-file-utils 0.16-0ubuntu4

** Alert 1297461141.55111: mail  - syslog,dpkg,config_changed,
2011 Feb 11 16:52:21 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 16:52:19 status installed python-gmenu 2.30.4-0ubuntu1

** Alert 1297461141.55393: mail  - syslog,dpkg,config_changed,
2011 Feb 11 16:52:21 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 16:52:20 status installed menu 2.1.44ubuntu1

** Alert 1297461141.55665: mail  - syslog,dpkg,config_changed,
2011 Feb 11 16:52:21 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 16:52:20 status installed ureadahead 0.100.0-8

** Alert 1297461145.55939: mail  - syslog,dpkg,config_changed,
2011 Feb 11 16:52:25 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 16:52:24 status installed gconf2 2.31.91-0ubuntu3.1

** Alert 1297461147.56218: mail  - syslog,dpkg,config_changed,
2011 Feb 11 16:52:27 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 16:52:26 status installed python-support 1.0.9ubuntu1

** Alert 1297461149.56499: mail  - syslog,dpkg,config_changed,
2011 Feb 11 16:52:29 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 16:52:27 status installed ttf-symbol-replacement 1.2.2-0ubuntu2~maverick2

** Alert 1297461149.56800: mail  - syslog,dpkg,config_changed,
2011 Feb 11 16:52:29 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 16:52:27 status installed lib32nss-mdns 0.10-3ubuntu4

** Alert 1297461151.57081: mail  - syslog,dpkg,config_changed,
2011 Feb 11 16:52:31 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 16:52:30 status installed wine1.2 1.2.2-0ubuntu2~maverick2

** Alert 1297461151.57367: mail  - syslog,dpkg,config_changed,
2011 Feb 11 16:52:31 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 16:52:30 status installed wine1.2-gecko 1.0.0-0ubuntu4

** Alert 1297461151.57649: mail  - syslog,dpkg,config_changed,
2011 Feb 11 16:52:31 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 16:52:30 status installed cabextract 1.3-1

** Alert 1297461151.57919: mail  - syslog,dpkg,config_changed,
2011 Feb 11 16:52:31 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 16:52:30 status installed icoutils 0.29.1-0ubuntu1

** Alert 1297461151.58197: mail  - syslog,dpkg,config_changed,
2011 Feb 11 16:52:31 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 16:52:30 status installed imagemagick 7:6.6.2.6-1ubuntu1.1

** Alert 1297461153.58483: mail  - syslog,dpkg,config_changed,
2011 Feb 11 16:52:33 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 16:52:31 status installed libcdt4 2.26.3-4

** Alert 1297461153.58753: mail  - syslog,dpkg,config_changed,
2011 Feb 11 16:52:33 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 16:52:31 status installed libgraph4 2.26.3-4

** Alert 1297461153.59025: mail  - syslog,dpkg,config_changed,
2011 Feb 11 16:52:33 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 16:52:32 status installed libpathplan4 2.26.3-4

** Alert 1297461153.59300: mail  - syslog,dpkg,config_changed,
2011 Feb 11 16:52:33 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 16:52:32 status installed libxdot4 2.26.3-4

** Alert 1297461153.59571: mail  - syslog,dpkg,config_changed,
2011 Feb 11 16:52:33 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 16:52:32 status installed libgvc5 2.26.3-4

** Alert 1297461153.59841: mail  - syslog,dpkg,config_changed,
2011 Feb 11 16:52:33 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 16:52:32 status installed libilmbase6 1.0.1-3build2

** Alert 1297461155.60120: mail  - syslog,dpkg,config_changed,
2011 Feb 11 16:52:35 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 16:52:33 status installed libopenexr6 1.6.1-4.1

** Alert 1297461155.60395: mail  - syslog,dpkg,config_changed,
2011 Feb 11 16:52:35 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 16:52:33 status installed libmagickcore3-extra 7:6.6.2.6-1ubuntu1.1

** Alert 1297461155.60690: mail  - syslog,dpkg,config_changed,
2011 Feb 11 16:52:35 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 16:52:33 status installed libnetpbm10 2:10.0-12.2

** Alert 1297461155.60967: mail  - syslog,dpkg,config_changed,
2011 Feb 11 16:52:35 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 16:52:33 status installed netpbm 2:10.0-12.2

** Alert 1297461165.61239: mail  - syslog,dpkg,config_changed,
2011 Feb 11 16:52:45 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 16:52:43 status installed ttf-droid 1.00~b112+dfsg+1-0ubuntu1

** Alert 1297461309.61528: mail  - syslog,adduser
2011 Feb 11 16:55:09 rosemary-122-CK-NF68->/var/log/auth.log
Rule: 5901 (level 8) -> 'New group added to the system'
Src IP: (none)
User: (none)
Feb 11 16:55:08 rosemary-122-CK-NF68 groupadd[16685]: new group: name=winbindd_priv, GID=124

** Alert 1297461309.61817: mail  - syslog,dpkg,config_changed,
2011 Feb 11 16:55:09 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 16:55:07 status installed ttf-mscorefonts-installer 3.2ubuntu2

** Alert 1297461309.62107: mail  - syslog,dpkg,config_changed,
2011 Feb 11 16:55:09 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 16:55:07 status installed ttf-umefont 416-2

** Alert 1297461311.62378: mail  - syslog,dpkg,config_changed,
2011 Feb 11 16:55:11 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 16:55:10 status installed winbind 2:3.5.4~dfsg-1ubuntu8.2

** Alert 1297461311.62663: mail  - syslog,dpkg,config_changed,
2011 Feb 11 16:55:11 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 16:55:11 status installed wine 1.2.2-0ubuntu2~maverick2

** Alert 1297461313.62946: mail  - syslog,dpkg,config_changed,
2011 Feb 11 16:55:13 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 16:55:11 status installed gnome-exe-thumbnailer 0.7-0ubuntu1

** Alert 1297461313.63234: mail  - syslog,dpkg,config_changed,
2011 Feb 11 16:55:13 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 16:55:12 status installed libc-bin 2.12.1-0ubuntu10.2

** Alert 1297461313.63515: mail  - syslog,dpkg,config_changed,
2011 Feb 11 16:55:13 rosemary-122-CK-NF68->/var/log/dpkg.log
Rule: 2902 (level 7) -> 'New dpkg (Debian Package) installed.'
Src IP: (none)
User: (none)
2011-02-11 16:55:12 status installed menu 2.1.44ubuntu1

** Alert 1297461889.63787: - syslog,sudo
2011 Feb 11 17:04:49 rosemary-122-CK-NF68->/var/log/auth.log
Rule: 5402 (level 3) -> 'Successful sudo to ROOT executed'
Src IP: (none)
User: (none)
Feb 11 17:04:49 rosemary-122-CK-NF68 sudo: rosemary : no tty present and no askpass program specified ; TTY=unknown ; PWD=/home/rosemary ; USER=root ; COMMAND=/home/rosemary/Downloads

** Alert 1297461949.64161: - syslog,sudo
2011 Feb 11 17:05:49 rosemary-122-CK-NF68->/var/log/auth.log
Rule: 5402 (level 3) -> 'Successful sudo to ROOT executed'
Src IP: (none)
User: (none)
Feb 11 17:05:49 rosemary-122-CK-NF68 sudo: rosemary : TTY=pts/0 ; PWD=/home/rosemary ; USER=root ; COMMAND=/usr/bin/gedit /var/ossec/logs/alerts/alerts.log

** Alert 1297464536.64507: - pam,syslog,authentication_failed,
2011 Feb 11 17:48:56 rosemary-122-CK-NF68->/var/log/auth.log
Rule: 5503 (level 5) -> 'User login failed.'
Src IP: rosemary-122-CK-NF68
User: rosemary
Feb 11 17:48:55 rosemary-122-CK-NF68 sudo: pam_unix(sudo:auth): authentication failure; logname=rosemary uid=0 euid=0 tty=/dev/pts/0 ruser=rosemary rhost=rosemary-122-CK-NF68  user=rosemary

** Alert 1297464548.64911: - syslog,sudo
2011 Feb 11 17:49:08 rosemary-122-CK-NF68->/var/log/auth.log
Rule: 5402 (level 3) -> 'Successful sudo to ROOT executed'
Src IP: (none)
User: (none)
Feb 11 17:49:06 rosemary-122-CK-NF68 sudo: rosemary : TTY=pts/0 ; PWD=/home/rosemary ; USER=root ; COMMAND=/usr/bin/gedit /var/ossec/logs/alerts/alerts.log

```If anyone could tell me whats going on with my computer I would be grateful. I am a bit on the paranoid end as my windows computer and my honey pot were both hacked. (Judging from the honey pots log files it was done by someone who knows what they are doing and not a script kiddie.) I am new-ish to running on linux but I am trying to figure out how to harden it and fast.

Edit: Wine is installed as this is my gaming computer, my work computer is staying offline till I can be sure this mess is sorted out.

---

### Post by cariboo on 2011-02-11
the logs are pretty easy to read, the first sections just tells you about the changes in mailcap and /etc/ld.so.cache, /etc/ld.so.cache, changes every time you install or upgrade packages, I'm not familiar with mailcap, but it has something to do with the email messages you are getting from ossec.

The second section is even easier to read, the last line in each paragraph tells you what is happening eg:

```
* Alert 1297406857.0: mail  - syslog,errors,
2011 Feb 11 01:47:37 rosemary-122-CK-NF68->/var/log/messages
Rule: 1002 (level 2) -> 'Unknown problem somewhere in the system.'
Src IP: (none)
User: (none)
Feb 11 01:47:36 rosemary-122-CK-NF68 kernel: [ 9916.558179] **npviewer.bin[3951]: segfault at 418 ip 00000000f60d8d16 sp 00000000ffe08918 error 6 in libflashplayer.so[f5e6b000+b5f000]**
```

If you look at the last line, it tells you that flash crashed

the second paragraph says that you installed vlc from the command line:

```
** Alert 1297410129.1159: - syslog,sudo
2011 Feb 11 02:42:09 rosemary-122-CK-NF68->/var/log/auth.log
Rule: 5402 (level 3) -> 'Successful sudo to ROOT executed'
Src IP: (none)
User: (none)
Feb 11 02:42:07 rosemary-122-CK-NF68 sudo: rosemary : TTY=pts/0 ; PWD=/home/rosemary ; USER=root ; **COMMAND=/usr/bin/apt-get install vlc**
```

the rest of the listing tells you the vlc depends and recommends that were installed.

There is nothing to be worried about. If you are going to use tools that do a lot of logging, I would suggest you learn to read them.

---

