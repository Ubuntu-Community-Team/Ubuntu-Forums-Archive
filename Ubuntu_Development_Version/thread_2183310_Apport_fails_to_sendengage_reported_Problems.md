---
title: "Apport fails to send/engage reported Problems"
date: 2013-10-24
forum: Ubuntu Development Version
---

### Post by ventrical on 2013-10-24
On booting my Intel  Core 2 Duo  Box thismorning I recieved  two pop-ups of internal errors. After clicking <continue> to send, the pop-up warnings would crash into airspace.

[https://bugs.launchpad.net/ubuntu/+source/apport/+bug/1244264](https://bugs.launchpad.net/ubuntu/+source/apport/+bug/1244264)

---

### Post by QDR06VV9 on 2013-10-25
> **ventrical said:**
> On booting my Intel  Core 2 Duo  Box thismorning I recieved  two pop-ups of internal errors. After clicking <continue> to send, the pop-up warnings would crash into airspace.

[https://bugs.launchpad.net/ubuntu/+source/apport/+bug/1244264](https://bugs.launchpad.net/ubuntu/+source/apport/+bug/1244264)

Been showing here also since I started the switch to trusty, was also showing in raring testing.

---

### Post by grahammechanical on 2013-10-25
There is a work around to this. It is called hitting the Cancel button. :) I did not get the usual Internal Error message this morning.

---

### Post by mc4man on 2013-10-25
Doesn't seem to indicate apport is crashing, more like the 2 crashes have been uploaded to some crash db or whatever one wants to call.
What were you expecting to happen?

---

### Post by slickymaster on 2013-10-25
> **grahammechanical said:**
> There is a work around to this. It is called hitting the Cancel button. :) I did not get the usual Internal Error message this morning.

Me neither. Preformed the updates through TTLY1 as usual, received approximately 35 MB of updates, among which apport:i386 (2.12.5-0ubuntu2, 2.12.6-0ubuntu1), and everything went smoothly.

```
Start-Date: 2013-10-25  09:56:12
Commandline: apt-get dist-upgrade
Install: libterm-ui-perl:i386 (0.38-1, automatic), liblog-message-simple-perl:i386 (0.10-1, automatic), libqpdf13:i386 (5.0.1-1, automatic), libpod-latex-perl:i386 (0.61-1, automatic), libtext-soundex-perl:i386 (3.4-1build1, automatic), libperl5.18:i386 (5.18.1-4, automatic), libarchive-extract-perl:i386 (0.68-1, automatic), libmodule-pluggable-perl:i386 (4.8-1, automatic)
Upgrade: cracklib-runtime:i386 (2.8.22-1, 2.9.0-1ubuntu1), vim-tiny:i386 (7.4.000-1ubuntu2, 7.4.052-1ubuntu1), vim-runtime:i386 (7.4.000-1ubuntu2, 7.4.052-1ubuntu1), libx264-123:i386 (0.123.2189+git35cf912-1ubuntu1, 0.123.2189+git35cf912-1ubuntu2), libapparmor1:i386 (2.8.0-0ubuntu31, 2.8.0-0ubuntu32), libfontembed1:i386 (1.0.40-0ubuntu1, 1.0.40-0ubuntu2), libx11-xcb1:i386 (1.6.1-1ubuntu1, 1.6.1-1ubuntu2), dh-apparmor:i386 (2.8.0-0ubuntu31, 2.8.0-0ubuntu32), kmod:i386 (9-3ubuntu1, 15-0ubuntu2), perl-modules:i386 (5.14.2-21build1, 5.18.1-4), libpurple0:i386 (2.10.7-0ubuntu4.1, 2.10.7-0ubuntu4.2), libgstreamer-perl:i386 (0.17-1, 0.19-1), libxml-parser-perl:i386 (2.41-1build2, 2.41-1build3), python-aptdaemon.gtk3widgets:i386 (1.1.1-0ubuntu3, 1.1.1-1ubuntu1), libfile-fcntllock-perl:i386 (0.14-2, 0.14-2build1), dconf-service:i386 (0.16.1-1, 0.18.0-1), libsub-name-perl:i386 (0.05-1build3, 0.05-1build4), perl:i386 (5.14.2-21build1, 5.18.1-4), upstart:i386 (1.10-0ubuntu7, 1.10-0ubuntu8), libsnmp-base:i386 (5.7.2~dfsg-8ubuntu1, 5.7.2~dfsg-8ubuntu2), libtext-charwidth-perl:i386 (0.04-7build2, 0.04-7build3), libpurple-bin:i386 (2.10.7-0ubuntu4.1, 2.10.7-0ubuntu4.2), libdconf1:i386 (0.16.1-1, 0.18.0-1), aptdaemon-data:i386 (1.1.1-0ubuntu3, 1.1.1-1ubuntu1), libzvbi0:i386 (0.2.33-7, 0.2.35-2), libnet-dbus-perl:i386 (1.0.0-2, 1.0.0-2build1), pidgin:i386 (2.10.7-0ubuntu4.1, 2.10.7-0ubuntu4.2), libzvbi-common:i386 (0.2.33-7, 0.2.35-2), libintl-perl:i386 (1.23-1, 1.23-1build1), initramfs-tools:i386 (0.103ubuntu1, 0.103ubuntu2), libx11-data:i386 (1.6.1-1ubuntu1, 1.6.1-1ubuntu2), python-ubuntu-sso-client:i386 (13.10-0ubuntu1, 13.10-0ubuntu2), libsub-identify-perl:i386 (0.04-1build2, 0.04-1build3), libcupsfilters1:i386 (1.0.40-0ubuntu1, 1.0.40-0ubuntu2), xfce4-taskmanager:i386 (1.0.0-3, 1.0.0-4), init-system-helpers:i386 (1.7, 1.11), [COLOR=#ff0000]apport-gtk:i386 (2.12.5-0ubuntu2, 2.12.6-0ubuntu1)[/COLOR], grub-common:i386 (2.00-19ubuntu2, 2.00-19ubuntu3), gir1.2-atspi-2.0:i386 (2.10.0-0ubuntu2, 2.10.1-0ubuntu1), dconf-cli:i386 (0.16.1-1, 0.18.0-1), libgtk2-perl:i386 (1.247-2, 1.248-1), apparmor-easyprof:i386 (2.8.0-0ubuntu31, 2.8.0-0ubuntu32), fonts-opensymbol:i386 (102.3+LibO4.1.2~rc3-0ubuntu1, 102.3+LibO4.1.2~rc3-0ubuntu2), xchat-common:i386 (2.8.8-7.1ubuntu2, 2.8.8-7.1ubuntu3), python-aptdaemon:i386 (1.1.1-0ubuntu3, 1.1.1-1ubuntu1), fonts-lyx:i386 (2.0.6-1, 2.0.6-1build1), grub-pc:i386 (2.00-19ubuntu2, 2.00-19ubuntu3), libtext-iconv-perl:i386 (1.7-5build1, 1.7-5build2), aptdaemon:i386 (1.1.1-0ubuntu3, 1.1.1-1ubuntu1), libgtk2-trayicon-perl:i386 (0.06-1build2, 0.06-1build3), system-config-printer-udev:i386 (1.4.2+20130920-0ubuntu1, 1.4.2+20130920-0ubuntu2), libcairo-perl:i386 (1.103-2, 1.104-1), libx11-6:i386 (1.6.1-1ubuntu1, 1.6.1-1ubuntu2), python3-aptdaemon.pkcompat:i386 (1.1.1-0ubuntu3, 1.1.1-1ubuntu1), libsocket6-perl:i386 (0.23-1build3, 0.23+ds-0+nmu1), cups-filters:i386 (1.0.40-0ubuntu1, 1.0.40-0ubuntu2), perl-base:i386 (5.14.2-21build1, 5.18.1-4), libvo-aacenc0:i386 (0.1.2-1, 0.1.3-1), qpdf:i386 (4.2.0-2, 5.0.1-1), [COLOR=#ff0000]apport:i386 (2.12.5-0ubuntu2, 2.12.6-0ubuntu1)[/COLOR], libldap-2.4-2:i386 (2.4.31-1+nmu2ubuntu3, 2.4.31-1+nmu2ubuntu4), libhtml-parser-perl:i386 (3.71-1, 3.71-1build1), libpango-perl:i386 (1.224-1, 1.224-2), dconf-tools:i386 (0.16.1-1, 0.18.0-1), libio-pty-perl:i386 (1.08-1build3, 1.08-1build4), libuuid-perl:i386 (0.02-5, 0.05-1), libapparmor-perl:i386 (2.8.0-0ubuntu31, 2.8.0-0ubuntu32), libmad0:i386 (0.15.1b-7ubuntu2, 0.15.1b-8ubuntu1), python3-aptdaemon.gtk3widgets:i386 (1.1.1-0ubuntu3, 1.1.1-1ubuntu1), grub2-common:i386 (2.00-19ubuntu2, 2.00-19ubuntu3), grub-pc-bin:i386 (2.00-19ubuntu2, 2.00-19ubuntu3), libcrack2:i386 (2.8.22-1, 2.9.0-1ubuntu1), system-config-printer-common:i386 (1.4.2+20130920-0ubuntu1, 1.4.2+20130920-0ubuntu2), libapt-pkg-perl:i386 (0.1.29, 0.1.29build1), [COLOR=#ff0000]python3-apport:i386 (2.12.5-0ubuntu2, 2.12.6-0ubuntu1)[/COLOR], libperlio-gzip-perl:i386 (0.18-1build2, 0.18-1build3), libatspi2.0-0:i386 (2.10.0-0ubuntu2, 2.10.1-0ubuntu1), dconf-editor:i386 (0.16.1-1, 0.18.0-1), libsqlite3-0:i386 (3.7.17-1ubuntu1, 3.8.0.2-1ubuntu1), libgtk2-notify-perl:i386 (0.05-3build1, 0.05-3build2), ubuntu-sso-client:i386 (13.10-0ubuntu1, 13.10-0ubuntu2), liblist-moreutils-perl:i386 (0.33-1build2, 0.33-1build3), vim-common:i386 (7.4.000-1ubuntu2, 7.4.052-1ubuntu1), vim:i386 (7.4.000-1ubuntu2, 7.4.052-1ubuntu1), python-cupshelpers:i386 (1.4.2+20130920-0ubuntu1, 1.4.2+20130920-0ubuntu2), libsnmp30:i386 (5.7.2~dfsg-8ubuntu1, 5.7.2~dfsg-8ubuntu2), initramfs-tools-bin:i386 (0.103ubuntu1, 0.103ubuntu2), liblocale-gettext-perl:i386 (1.05-7build2, 1.05-7build3), libglib-perl:i386 (1.301-1, 1.302-1), system-config-printer-gnome:i386 (1.4.2+20130920-0ubuntu1, 1.4.2+20130920-0ubuntu2), cups-browsed:i386 (1.0.40-0ubuntu1, 1.0.40-0ubuntu2), python3-problem-report:i386 (2.12.5-0ubuntu2, 2.12.6-0ubuntu1), libzbar0:i386 (0.10+doc-9, 0.10+doc-9build1), libnet-dns-perl:i386 (0.68-1.2, 0.68-1.2build1), pidgin-data:i386 (2.10.7-0ubuntu4.1, 2.10.7-0ubuntu4.2), dconf-gsettings-backend:i386 (0.16.1-1, 0.18.0-1), libvo-amrwbenc0:i386 (0.1.2-1, 0.1.3-1), xchat:i386 (2.8.8-7.1ubuntu2, 2.8.8-7.1ubuntu3), libclone-perl:i386 (0.34-1, 0.35-1), libdigest-crc-perl:i386 (0.18-1, 0.18-1build1), apparmor:i386 (2.8.0-0ubuntu31, 2.8.0-0ubuntu32), libnet-ssleay-perl:i386 (1.55-1, 1.55-1build1), libsoundtouch0:i386 (1.7.1-2, 1.7.1-4), libkmod2:i386 (9-3ubuntu1, 15-0ubuntu2), at-spi2-core:i386 (2.10.0-0ubuntu2, 2.10.1-0ubuntu1), python3-aptdaemon:i386 (1.1.1-0ubuntu3, 1.1.1-1ubuntu1), module-init-tools:i386 (9-3ubuntu1, 15-0ubuntu2)
Remove: libperl5.14:i386 (5.14.2-21build1)
End-Date: 2013-10-25  10:02:22
```

---

### Post by ventrical on 2013-10-25
> **mc4man said:**
> Doesn't seem to indicate apport is crashing, more like the 2 crashes have been uploaded to some crash db or whatever one wants to call.
What were you expecting to happen?


  Ahhhh .. yes .. I recall now mac4man. Thanks for the reminder. I was actually expecting to file a full bug report as in being taken to launchpad... but I remember now that this has all been turned around..

---

### Post by mc4man on 2013-10-25
LP reports for crashers are turned off near end of dev & not re-enabled in next dev for awhile, you'll see it in an apport* update at some point down the road

---

### Post by ventrical on 2013-10-25
> **mc4man said:**
> LP reports for crashers are turned off near end of dev & not re-enabled in next dev for awhile, you'll see it in an apport* update at some point down the road


Thats right .. I just cheked /var/crash/ and all those reports are going there. They are actually benign reports unless you use ubuntu-bug or launchpad directly.

---

### Post by QDR06VV9 on 2013-10-25
> **mc4man said:**
> LP reports for crashers are turned off near end of dev & not re-enabled in next dev for awhile, you'll see it in an apport* update at some point down the road

Yep that has been case for as long as I been testing.:D

---

### Post by Cavsfan on 2013-10-27
Good to know. I haven't seen a webpage popup after something crashed yet either.

---

