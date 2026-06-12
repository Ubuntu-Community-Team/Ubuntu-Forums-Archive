---
title: "Utopic first updates and first crash"
date: 2014-04-28
forum: Ubuntu Development Version
---

### Post by slickymaster on 2014-04-28
Today, things started rolling.

One update```
~$ cat /var/log/dpkg.log | grep '\ install\ '
2014-04-28 09:58:27 install libhogweed2:i386 <none> 2.7.1-2
```and a massive pile of upgrades```
~$ cat /var/log/dpkg.log | grep '\ upgrade\ '
2014-04-28 09:55:30 upgrade bash:i386 4.3-6ubuntu1 4.3-7ubuntu1
2014-04-28 09:55:43 upgrade dpkg:i386 1.17.5ubuntu5 1.17.7ubuntu1
2014-04-28 09:56:03 upgrade findutils:i386 4.4.2-7 4.4.2-8
2014-04-28 09:56:15 upgrade grep:i386 2.16-1 2.18-2
2014-04-28 09:56:23 upgrade tar:i386 1.27.1-1 1.27.1-2
2014-04-28 09:56:31 upgrade gcc-4.9-base:i386 4.9-20140406-0ubuntu1 4.9.0-1ubuntu3
2014-04-28 09:56:33 upgrade libgcc1:i386 1:4.9-20140406-0ubuntu1 1:4.9.0-1ubuntu3
2014-04-28 09:56:36 upgrade libstdc++6:i386 4.8.2-19ubuntu1 4.9.0-1ubuntu3
2014-04-28 09:56:38 upgrade libapt-pkg4.12:i386 1.0.1ubuntu2 1.0.2ubuntu2
2014-04-28 09:56:41 upgrade apt:i386 1.0.1ubuntu2 1.0.2ubuntu2
2014-04-28 09:56:53 upgrade libapt-inst1.5:i386 1.0.1ubuntu2 1.0.2ubuntu2
2014-04-28 09:56:53 upgrade liblocale-gettext-perl:i386 1.05-7build3 1.05-8
2014-04-28 09:56:54 upgrade init-system-helpers:all 1.14 1.18
2014-04-28 09:56:54 upgrade resolvconf:all 1.69ubuntu1 1.69ubuntu2
2014-04-28 09:56:57 upgrade libjson-c2:i386 0.11-3ubuntu1 0.11-4ubuntu1
2014-04-28 09:56:58 upgrade libkmod2:i386 15-0ubuntu6 16-2ubuntu3
2014-04-28 09:56:58 upgrade kmod:i386 15-0ubuntu6 16-2ubuntu3
2014-04-28 09:56:59 upgrade module-init-tools:all 15-0ubuntu6 16-2ubuntu3
2014-04-28 09:56:59 upgrade libasprintf-dev:i386 0.18.3.1-1ubuntu2 0.18.3.2-1ubuntu1
2014-04-28 09:57:00 upgrade libasprintf0c2:i386 0.18.3.1-1ubuntu2 0.18.3.2-1ubuntu1
2014-04-28 09:57:00 upgrade libdbus-glib-1-2:i386 0.100.2-1 0.102-1
2014-04-28 09:57:01 upgrade libedit2:i386 3.1-20130712-2 3.1-20140213-1
2014-04-28 09:57:01 upgrade libgck-1-0:i386 3.10.1-1 3.12.0-1
2014-04-28 09:57:02 upgrade libgcr-3-common:all 3.10.1-1 3.12.0-1
2014-04-28 09:57:02 upgrade libgcr-base-3-1:i386 3.10.1-1 3.12.0-1
2014-04-28 09:57:03 upgrade libgcr-3-1:i386 3.10.1-1 3.12.0-1
2014-04-28 09:57:03 upgrade libgcr-ui-3-1:i386 3.10.1-1 3.12.0-1
2014-04-28 09:57:04 upgrade libnfnetlink0:i386 1.0.1-2 1.0.1-3
2014-04-28 09:57:05 upgrade libparted0debian1:i386 2.3-19ubuntu1 2.3-20
2014-04-28 09:57:06 upgrade libsasl2-2:i386 2.1.25.dfsg1-17build1 2.1.26.dfsg1-9
2014-04-28 09:57:06 upgrade libsasl2-modules-db:i386 2.1.25.dfsg1-17build1 2.1.26.dfsg1-9
2014-04-28 09:57:07 upgrade flex:i386 2.5.35-10.1ubuntu2 2.5.39-3ubuntu1
2014-04-28 09:57:08 upgrade libfl-dev:i386 2.5.35-10.1ubuntu2 2.5.39-3ubuntu1
2014-04-28 09:57:08 upgrade fonts-nanum:all 20131007-1 20131007-3
2014-04-28 09:57:13 upgrade gawk:i386 1:4.0.1+dfsg-2.1ubuntu2 1:4.1.1+dfsg-1
2014-04-28 09:57:14 upgrade geany:i386 1.23.1+dfsg-1 1.24.1+dfsg-1
2014-04-28 09:57:15 upgrade geany-common:all 1.23.1+dfsg-1 1.24.1+dfsg-1
2014-04-28 09:57:18 upgrade google-chrome-stable:i386 34.0.1847.116-1 34.0.1847.132-1
2014-04-28 09:57:44 upgrade libaa1:i386 1.4p5-41 1.4p5-42
2014-04-28 09:57:44 upgrade libitm1:i386 4.8.2-19ubuntu1 4.9.0-1ubuntu3
2014-04-28 09:57:45 upgrade libgomp1:i386 4.8.2-19ubuntu1 4.9.0-1ubuntu3
2014-04-28 09:57:46 upgrade libquadmath0:i386 4.8.2-19ubuntu1 4.9.0-1ubuntu3
2014-04-28 09:57:46 upgrade libgfortran3:i386 4.8.2-19ubuntu1 4.9.0-1ubuntu3
2014-04-28 09:57:47 upgrade g++-4.8:i386 4.8.2-19ubuntu1 4.8.2-21ubuntu1
2014-04-28 09:57:50 upgrade libstdc++-4.8-dev:i386 4.8.2-19ubuntu1 4.8.2-21ubuntu1
2014-04-28 09:57:59 upgrade gcc-4.8:i386 4.8.2-19ubuntu1 4.8.2-21ubuntu1
2014-04-28 09:58:03 upgrade cpp-4.8:i386 4.8.2-19ubuntu1 4.8.2-21ubuntu1
2014-04-28 09:58:05 upgrade binutils-dev:i386 2.24-5ubuntu3 2.24.51.20140425-0ubuntu2
2014-04-28 09:58:08 upgrade binutils:i386 2.24-5ubuntu3 2.24.51.20140425-0ubuntu2
2014-04-28 09:58:12 upgrade libatomic1:i386 4.8.2-19ubuntu1 4.9.0-1ubuntu3
2014-04-28 09:58:13 upgrade libgcc-4.8-dev:i386 4.8.2-19ubuntu1 4.8.2-21ubuntu1
2014-04-28 09:58:14 upgrade libasan0:i386 4.8.2-19ubuntu1 4.8.2-21ubuntu1
2014-04-28 09:58:15 upgrade gcc-4.8-base:i386 4.8.2-19ubuntu1 4.8.2-21ubuntu1
2014-04-28 09:58:15 upgrade libbluetooth3:i386 4.101-0ubuntu13 4.101-0ubuntu14
2014-04-28 09:58:16 upgrade libpam-ck-connector:i386 0.4.5-3.1ubuntu2 0.4.6-5
2014-04-28 09:58:16 upgrade consolekit:i386 0.4.5-3.1ubuntu2 0.4.6-5
2014-04-28 09:58:17 upgrade libck-connector0:i386 0.4.5-3.1ubuntu2 0.4.6-5
2014-04-28 09:58:18 upgrade libgstreamer1.0-0:i386 1.2.3-1 1.2.4-1
2014-04-28 09:58:19 upgrade libgstreamer-plugins-base1.0-0:i386 1.2.3-1 1.2.4-1
2014-04-28 09:58:21 upgrade libclutter-gst-2.0-0:i386 2.0.8-1build1 2.0.10-1
2014-04-28 09:58:21 upgrade libcolord1:i386 1.0.6-1 1.0.6-1git1
2014-04-28 09:58:22 upgrade libdaemon0:i386 0.14-2ubuntu1 0.14-5ubuntu1
2014-04-28 09:58:22 upgrade dconf-service:i386 0.20.0-1 0.20.0-2
2014-04-28 09:58:23 upgrade libdconf1:i386 0.20.0-1 0.20.0-2
2014-04-28 09:58:24 upgrade dconf-gsettings-backend:i386 0.20.0-1 0.20.0-2
2014-04-28 09:58:24 upgrade libdjvulibre-text:all 3.5.25.4-3 3.5.25.4-4
2014-04-28 09:58:25 upgrade libdjvulibre21:i386 3.5.25.4-3 3.5.25.4-4
2014-04-28 09:58:25 upgrade libgettextpo-dev:i386 0.18.3.1-1ubuntu2 0.18.3.2-1ubuntu1
2014-04-28 09:58:26 upgrade libgettextpo0:i386 0.18.3.1-1ubuntu2 0.18.3.2-1ubuntu1
2014-04-28 09:58:26 upgrade libgupnp-igd-1.0-4:i386 0.2.2-1 0.2.3-1
2014-04-28 09:58:27 upgrade libnettle4:i386 2.7.1-1 2.7.1-2
2014-04-28 09:58:28 upgrade libijs-0.35:i386 0.35-8build1 0.35-10
2014-04-28 09:58:28 upgrade libmbim-glib0:i386 1.6.0-2 1.8.0-1
2014-04-28 09:58:29 upgrade libmhash2:i386 0.9.9.9-4 0.9.9.9-5
2014-04-28 09:58:29 upgrade libnl-route-3-200:i386 3.2.21-1 3.2.24-2
2014-04-28 09:58:30 upgrade libnl-genl-3-200:i386 3.2.21-1 3.2.24-2
2014-04-28 09:58:30 upgrade libnl-3-200:i386 3.2.21-1 3.2.24-2
2014-04-28 09:58:31 upgrade libsdl1.2debian:i386 1.2.15-8ubuntu1 1.2.15-8ubuntu2
2014-04-28 09:58:32 upgrade libtalloc2:i386 2.1.0-1 2.1.0-2
2014-04-28 09:58:32 upgrade python-tdb:i386 1.2.12-1 1.2.13-2
2014-04-28 09:58:33 upgrade libtdb1:i386 1.2.12-1 1.2.13-2
2014-04-28 09:58:33 upgrade libtevent0:i386 0.9.19-1 0.9.21-1
2014-04-28 09:58:34 upgrade libtiff5:i386 4.0.3-7 4.0.3-8
2014-04-28 09:58:35 upgrade libx264-142:i386 2:0.142.2389+git956c8d8-2 2:0.142.2389+git956c8d8-4
2014-04-28 09:58:35 upgrade libxvidcore4:i386 2:1.3.2-9ubuntu1 2:1.3.3-1
2014-04-28 09:58:36 upgrade lightdm:i386 1.10.0-0ubuntu3 1.11.0-0ubuntu1
2014-04-28 09:58:37 upgrade libnm-util2:i386 0.9.8.8-0ubuntu7 0.9.8.8-0ubuntu8
2014-04-28 09:58:38 upgrade libnm-glib4:i386 0.9.8.8-0ubuntu7 0.9.8.8-0ubuntu8
2014-04-28 09:58:38 upgrade iproute2:i386 3.12.0-2 3.14.0-1
2014-04-28 09:58:40 upgrade dnsmasq-base:i386 2.68-1 2.70-1
2014-04-28 09:58:41 upgrade network-manager:i386 0.9.8.8-0ubuntu7 0.9.8.8-0ubuntu8
2014-04-28 09:58:43 upgrade poppler-data:all 0.4.6-4 0.4.6-5
2014-04-28 09:58:53 upgrade python-talloc:i386 2.1.0-1 2.1.0-2
2014-04-28 09:58:53 upgrade gstreamer1.0-plugins-bad-videoparsers:i386 1.2.3-1ubuntu2 1.2.4-1ubuntu1
2014-04-28 09:58:54 upgrade gstreamer1.0-plugins-good:i386 1.2.3-1ubuntu2 1.2.4-1ubuntu1
2014-04-28 09:58:56 upgrade gstreamer1.0-plugins-bad-faad:i386 1.2.3-1ubuntu2 1.2.4-1ubuntu1
2014-04-28 09:58:57 upgrade gstreamer1.0-plugins-bad:i386 1.2.3-1ubuntu2 1.2.4-1ubuntu1
2014-04-28 09:59:00 upgrade gstreamer1.0-plugins-base:i386 1.2.3-1 1.2.4-1
2014-04-28 09:59:02 upgrade libgstreamer-plugins-good1.0-0:i386 1.2.3-1ubuntu2 1.2.4-1ubuntu1
2014-04-28 09:59:02 upgrade libgstreamer-plugins-bad1.0-0:i386 1.2.3-1ubuntu2 1.2.4-1ubuntu1
2014-04-28 09:59:03 upgrade libcolorhug1:i386 1.0.6-1 1.0.6-1git1
2014-04-28 09:59:03 upgrade apt-utils:i386 1.0.1ubuntu2 1.0.2ubuntu2
2014-04-28 09:59:04 upgrade libarchive-extract-perl:all 0.70-1 0.72-1
2014-04-28 09:59:04 upgrade ucf:all 3.0027+nmu1 3.0028
2014-04-28 09:59:05 upgrade vim:i386 2:7.4.052-1ubuntu3 2:7.4.253-1ubuntu1
2014-04-28 09:59:06 upgrade vim-tiny:i386 2:7.4.052-1ubuntu3 2:7.4.253-1ubuntu1
2014-04-28 09:59:07 upgrade vim-runtime:all 2:7.4.052-1ubuntu3 2:7.4.253-1ubuntu1
2014-04-28 09:59:14 upgrade vim-common:i386 2:7.4.052-1ubuntu3 2:7.4.253-1ubuntu1
2014-04-28 09:59:14 upgrade libjson0:i386 0.11-3ubuntu1 0.11-4ubuntu1
2014-04-28 09:59:15 upgrade locales:all 2.13+git20120306-12 2.13+git20120306-13
2014-04-28 09:59:22 upgrade apt-transport-https:i386 1.0.1ubuntu2 1.0.2ubuntu2
2014-04-28 09:59:22 upgrade dosfstools:i386 3.0.26-1 3.0.26-2
2014-04-28 09:59:22 upgrade ed:i386 1.9-2 1.10-2
2014-04-28 09:59:23 upgrade geoip-database:all 20140313-1 20140409-1
2014-04-28 09:59:24 upgrade gettext-base:i386 0.18.3.1-1ubuntu2 0.18.3.2-1ubuntu1
2014-04-28 09:59:25 upgrade gir1.2-freedesktop:i386 1.40.0-1 1.40.0-2
2014-04-28 09:59:25 upgrade libgirepository-1.0-1:i386 1.40.0-1 1.40.0-2
2014-04-28 09:59:26 upgrade gir1.2-glib-2.0:i386 1.40.0-1 1.40.0-2
2014-04-28 09:59:26 upgrade libsasl2-modules:i386 2.1.25.dfsg1-17build1 2.1.26.dfsg1-9
2014-04-28 09:59:27 upgrade nano:i386 2.2.6-1ubuntu1 2.2.6-1.1
2014-04-28 09:59:28 upgrade parted:i386 2.3-19ubuntu1 2.3-20
2014-04-28 09:59:28 upgrade python-apt-common:all 0.9.3.5 0.9.3.6
2014-04-28 09:59:28 upgrade python3-apt:i386 0.9.3.5 0.9.3.6
2014-04-28 09:59:30 upgrade python3-gi-cairo:i386 3.12.0-1 3.12.1-1
2014-04-28 09:59:31 upgrade python3-gi:i386 3.12.0-1 3.12.1-1
2014-04-28 09:59:32 upgrade time:i386 1.7-24 1.7-25
2014-04-28 09:59:33 upgrade bluez:i386 4.101-0ubuntu13 4.101-0ubuntu14
2014-04-28 09:59:36 upgrade bluez-alsa:i386 4.101-0ubuntu13 4.101-0ubuntu14
2014-04-28 09:59:36 upgrade bluez-cups:i386 4.101-0ubuntu13 4.101-0ubuntu14
2014-04-28 09:59:37 upgrade colord:i386 1.0.6-1 1.0.6-1git1
2014-04-28 09:59:38 upgrade dconf-cli:i386 0.20.0-1 0.20.0-2
2014-04-28 09:59:39 upgrade dconf-editor:i386 0.20.0-1 0.20.0-2
2014-04-28 09:59:49 upgrade dialog:i386 1.2-20130928-1 1.2-20140219-1
2014-04-28 09:59:50 upgrade dictionaries-common:all 1.20.5 1.23.2
2014-04-28 09:59:52 upgrade libtimedate-perl:all 2.3000-1 2.3000-2
2014-04-28 09:59:52 upgrade dpkg-dev:all 1.17.5ubuntu5 1.17.7ubuntu1
2014-04-28 09:59:53 upgrade libdpkg-perl:all 1.17.5ubuntu5 1.17.7ubuntu1
2014-04-28 09:59:56 upgrade patch:i386 2.7.1-4 2.7.1-5
2014-04-28 09:59:56 upgrade fonts-tlwg-garuda:all 1:0.5.1-3 1:0.6.0-1
2014-04-28 09:59:57 upgrade fonts-tlwg-kinnari:all 1:0.5.1-3 1:0.6.0-1
2014-04-28 09:59:58 upgrade fonts-tlwg-loma:all 1:0.5.1-3 1:0.6.0-1
2014-04-28 09:59:58 upgrade fonts-tlwg-mono:all 1:0.5.1-3 1:0.6.0-1
2014-04-28 09:59:59 upgrade fonts-tlwg-norasi:all 1:0.5.1-3 1:0.6.0-1
2014-04-28 09:59:59 upgrade fonts-tlwg-purisa:all 1:0.5.1-3 1:0.6.0-1
2014-04-28 10:00:00 upgrade fonts-tlwg-sawasdee:all 1:0.5.1-3 1:0.6.0-1
2014-04-28 10:00:00 upgrade fonts-tlwg-typewriter:all 1:0.5.1-3 1:0.6.0-1
2014-04-28 10:00:01 upgrade fonts-tlwg-typist:all 1:0.5.1-3 1:0.6.0-1
2014-04-28 10:00:01 upgrade fonts-tlwg-typo:all 1:0.5.1-3 1:0.6.0-1
2014-04-28 10:00:02 upgrade fonts-tlwg-umpush:all 1:0.5.1-3 1:0.6.0-1
2014-04-28 10:00:02 upgrade fonts-tlwg-waree:all 1:0.5.1-3 1:0.6.0-1
2014-04-28 10:00:03 upgrade fonts-thai-tlwg:all 1:0.5.1-3 1:0.6.0-1
2014-04-28 10:00:03 upgrade gcr:i386 3.10.1-1 3.12.0-1
2014-04-28 10:00:04 upgrade gettext:i386 0.18.3.1-1ubuntu2 0.18.3.2-1ubuntu1
2014-04-28 10:00:08 upgrade libgnome-bluetooth11:i386 3.8.2.1-0ubuntu4 3.8.2.1-0ubuntu5
2014-04-28 10:00:09 upgrade gir1.2-gnomebluetooth-1.0:i386 3.8.2.1-0ubuntu4 3.8.2.1-0ubuntu5
2014-04-28 10:00:09 upgrade gnome-bluetooth:i386 3.8.2.1-0ubuntu4 3.8.2.1-0ubuntu5
2014-04-28 10:00:10 upgrade gir1.2-gstreamer-1.0:i386 1.2.3-1 1.2.4-1
2014-04-28 10:00:11 upgrade gir1.2-gst-plugins-base-1.0:i386 1.2.3-1 1.2.4-1
2014-04-28 10:00:11 upgrade glib-networking-common:all 2.40.0-1 2.40.1-1
2014-04-28 10:00:12 upgrade glib-networking:i386 2.40.0-1 2.40.1-1
2014-04-28 10:00:12 upgrade glib-networking-services:i386 2.40.0-1 2.40.1-1
2014-04-28 10:00:13 upgrade gstreamer1.0-clutter:i386 2.0.8-1build1 2.0.10-1
2014-04-28 10:00:13 upgrade gstreamer1.0-libav:i386 1.2.3-1 1.2.4-1
2014-04-28 10:00:14 upgrade gstreamer1.0-plugins-ugly:i386 1.2.3-2build1 1.2.4-1
2014-04-28 10:00:15 upgrade pkg-config:i386 0.26-1ubuntu4 0.28-1
2014-04-28 10:00:16 upgrade gstreamer1.0-tools:i386 1.2.3-1 1.2.4-1
2014-04-28 10:00:16 upgrade gstreamer1.0-x:i386 1.2.3-1 1.2.4-1
2014-04-28 10:00:17 upgrade im-config:all 0.24-1ubuntu4 0.24-1ubuntu5
2014-04-28 10:00:18 upgrade iproute:all 1:3.12.0-2 1:3.14.0-1
2014-04-28 10:00:18 upgrade iw:i386 3.4-1 3.14-1
2014-04-28 10:00:19 upgrade libarchive-zip-perl:all 1.30-7 1.37-2
2014-04-28 10:00:19 upgrade libsub-identify-perl:i386 0.04-1build3 0.04-2
2014-04-28 10:00:20 upgrade libautodie-perl:all 2.23-1 2.25-1
2014-04-28 10:00:20 upgrade libcommon-sense-perl:i386 3.72-2build1 3.72-3
2014-04-28 10:00:21 upgrade libdigest-crc-perl:i386 0.18-1build1 0.18-2
2014-04-28 10:00:21 upgrade libexporter-lite-perl:all 0.02-2 0.04-1
2014-04-28 10:00:22 upgrade libfile-mimeinfo-perl:all 0.22-1 0.25-1
2014-04-28 10:00:22 upgrade libgoffice-0.10-10-common:all 0.10.9-1 0.10.14-1
2014-04-28 10:00:25 upgrade libgoffice-0.10-10:i386 0.10.9-1 0.10.14-1
2014-04-28 10:00:27 upgrade libgtk2-notify-perl:i386 0.05-3build2 0.05-4
2014-04-28 10:00:28 upgrade libgtk2-trayicon-perl:i386 0.06-1build3 0.06-2
2014-04-28 10:00:28 upgrade libio-socket-inet6-perl:all 2.71-1 2.72-1
2014-04-28 10:00:28 upgrade libkeybinder0:i386 0.3.0-2 0.3.0-3
2014-04-28 10:00:29 upgrade liblightdm-gobject-1-0:i386 1.10.0-0ubuntu3 1.11.0-0ubuntu1
2014-04-28 10:00:29 upgrade liblist-moreutils-perl:i386 0.33-1build3 0.33-2
2014-04-28 10:00:30 upgrade libnet-domain-tld-perl:all 1.70-1 1.72-1
2014-04-28 10:00:30 upgrade libnm-glib-vpn1:i386 0.9.8.8-0ubuntu7 0.9.8.8-0ubuntu8
2014-04-28 10:00:31 upgrade libpango-perl:i386 1.224-2 1.226-1
2014-04-28 10:00:34 upgrade libperlio-gzip-perl:i386 0.18-1build3 0.18-2
2014-04-28 10:00:34 upgrade libsub-name-perl:i386 0.05-1build4 0.05-2
2014-04-28 10:00:34 upgrade libswitch-perl:all 2.16-2 2.17-1
2014-04-28 10:00:35 upgrade libwww-perl:all 6.05-2 6.06-1
2014-04-28 10:00:35 upgrade patchutils:i386 0.3.2-3 0.3.3-1
2014-04-28 10:00:36 upgrade lintian:all 2.5.22ubuntu1 2.5.22ubuntu2
2014-04-28 10:00:43 upgrade locate:i386 4.4.2-7 4.4.2-8
2014-04-28 10:00:44 upgrade mousetweaks:i386 3.8.0-2 3.12.0-1
2014-04-28 10:00:44 upgrade printer-driver-c2esp:i386 27~rc1-1 27-1
2014-04-28 10:00:45 upgrade printer-driver-pxljr:i386 1.4+repack0-3 1.4+repack0-4
2014-04-28 10:00:45 upgrade printer-driver-sag-gdi:all 0.1-3 0.1-4
2014-04-28 10:00:46 upgrade printer-driver-splix:i386 2.0.0+svn315-2fakesync1 2.0.0+svn315-3fakesync1
2014-04-28 10:00:46 upgrade python-apt:i386 0.9.3.5 0.9.3.6
2014-04-28 10:00:48 upgrade python-chardet:all 2.0.1-2build2 2.2.1-1
2014-04-28 10:00:49 upgrade python-gi-cairo:i386 3.12.0-1 3.12.1-1
2014-04-28 10:00:49 upgrade python-gi:i386 3.12.0-1 3.12.1-1
2014-04-28 10:00:50 upgrade python-gobject:all 3.12.0-1 3.12.1-1
2014-04-28 10:00:51 upgrade python-keyring:all 3.5-1 3.7-1
2014-04-28 10:00:51 upgrade python3-chardet:all 2.0.1-1 2.2.1-1
2014-04-28 10:00:53 upgrade simple-scan:i386 3.12.0-0ubuntu1 3.13.1-0ubuntu1
2014-04-28 10:00:54 upgrade testdisk:i386 6.14-2 6.14-3
2014-04-28 10:00:56 upgrade transfig:i386 1:3.2.5.e-1ubuntu1 1:3.2.5.e-2ubuntu1
2014-04-28 10:00:57 upgrade wdiff:i386 1.2.1-2 1.2.1-3
2014-04-28 10:00:58 upgrade yelp-xsl:all 3.10.1-1 3.12.0-1
2014-04-28 10:00:59 upgrade dconf-tools:all 0.20.0-1 0.20.0-2
2014-04-28 10:00:59 upgrade libauthen-sasl-perl:all 2.1500-1 2.1600-1
2014-04-28 10:01:00 upgrade lynx-cur:i386 2.8.8pre4-1 2.8.8pre5-1
```
And of course, the first crashes. Specifically with gstreamer```
ERROR: apport (pid 14460) Mon Apr 28 10:05:35 2014: executable: /usr/lib/i386-linux-gnu/gstreamer1.0/gstreamer-1.0/gst-plugin-scanner (command line "/usr/lib/i386-linux-gnu/gstreamer1.0/gstreamer-1.0/gst-plugin-scanner -l")
ERROR: apport (pid 14460) Mon Apr 28 10:05:35 2014: gdbus call error: Error: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

ERROR: apport (pid 14460) Mon Apr 28 10:05:35 2014: debug: session gdbus call: 
ERROR: apport (pid 14460) Mon Apr 28 10:05:53 2014: wrote report /var/crash/_usr_lib_i386-linux-gnu_gstreamer1.0_gstreamer-1.0_gst-plugin-scanner.1000.crash
ERROR: apport (pid 2050) Mon Apr 28 10:13:34 2014: called for pid 2017, signal 11, core limit 0
ERROR: apport (pid 2050) Mon Apr 28 10:13:34 2014: executable: /usr/lib/i386-linux-gnu/gstreamer1.0/gstreamer-1.0/gst-plugin-scanner (command line "/usr/lib/i386-linux-gnu/gstreamer1.0/gstreamer-1.0/gst-plugin-scanner -l")
ERROR: apport (pid 2050) Mon Apr 28 10:13:34 2014: gdbus call error: Error: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

ERROR: apport (pid 2050) Mon Apr 28 10:13:34 2014: debug: session gdbus call: 
ERROR: apport (pid 2050) Mon Apr 28 10:13:44 2014: wrote report /var/crash/_usr_lib_i386-linux-gnu_gstreamer1.0_gstreamer-1.0_gst-plugin-scanner.1000.crash
```

---

