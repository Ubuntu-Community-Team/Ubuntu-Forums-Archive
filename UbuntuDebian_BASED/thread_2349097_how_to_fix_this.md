---
title: "how to fix this"
date: 2017-01-11
forum: Ubuntu/Debian BASED
---

### Post by 7mod998 on 2017-01-11
```
apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  caribou-antler castxml creepy dff espeak-data firebird2.5-common
  firebird2.5-common-doc gccxml gdebi-core gir1.2-clutter-gst-2.0
  gir1.2-gkbd-3.0 gir1.2-xkl-1.0 gnome-icon-theme-symbolic gnome-packagekit
  gnome-packagekit-data gnuplot5-qt gtk2-engines gucharmap hwdata iceweasel
  imagemagick-common inguma iproute libapache2-mod-php5 libasn1-8-heimdal
  libavcodec-ffmpeg56 libavdevice-ffmpeg56 libavfilter-ffmpeg5
  libavformat-ffmpeg56 libavresample-ffmpeg2 libavutil-ffmpeg54
  libbasicusageenvironment0 libbind9-90 libboost-filesystem1.58.0
  libboost-python1.58.0 libboost-python1.62.0 libboost-system1.58.0
  libboost-thread1.58.0 libcamel-1.2-54 libchromaprint0 libclutter-gst-2.0-0
  libcrypto++6 libcrypto++9v5 libcurses-perl libcurses-ui-perl libdbus-1-dev
  libdns100 libedataserver-1.2-21 libespeak1 libexporter-tiny-perl
  libfftw3-single3 libgdict-1.0-9 libgeos-3.5.0 libgif4 libglew1.13
  libgrilo-0.2-1 libgroupsock1 libgssapi3-heimdal libgtkglext1
  libgucharmap-2-90-7 libhcrypto4-heimdal libhdb9-heimdal libheimbase1-heimdal
  libheimntlm0-heimdal libhunspell-1.3-0 libhx509-5-heimdal libical1a
  libilmbase6v5 libisc95 libisccc90 libisccfg90 libjasper1 libjpeg9
  libkdc2-heimdal libkrb5-26-heimdal liblist-moreutils-perl liblivemedia23
  libllvm3.7 liblouis9 liblwres90 libmimic0 libnm-glib-vpn1 libntdb1 libonig2
  libopencv-contrib2.4v5 libopencv-legacy2.4v5 libopencv-ml2.4v5 libopenexr6v5
  libopenjpeg5 libpff1 libpgm-5.1-0 libphonon4 libpng12-0 libpoppler57
  libpostproc-ffmpeg53 libpth20 libpython3.4-minimal libpython3.4-stdlib
  libqdbm14 libqmi-glib1 libquvi-scripts libquvi7 libradare2-0.9.9 libregfi0
  libroken18-heimdal libschroedinger-1.0-0 libsodium13 libswresample-ffmpeg1
  libswscale-ffmpeg3 libtask-weaken-perl libtre5 libtrio2 libusageenvironment1
  libusbmuxd2 libvncclient1 libvpx3 libvte-common libvte9 libwebp5
  libwebpdemux1 libwebpmux1 libwebrtc-audio-processing-0 libwildmidi1
  libwind0-heimdal libwireshark6 libwiretap5 libwsutil6 libx265-68
  libxcb-composite0 libzip2 libzmq3 multiforcer phonon phonon-backend-vlc php5
  php5-cli php5-common php5-json php5-mysql php5-readline python-apsw
  python-bluez python-characteristic python-clamd python-ctypeslib
  python-d2to1 python-dbus-dev python-defusedxml python-distlib
  python-dominate python-ecdsa python-flickrapi python-googleapi
  python-instagram python-ipaddr python-jwt python-lzma python-lzo
  python-magic python-ntdb python-oauth2client python-oauthlib python-opengl
  python-pyatspi python-pycryptopp python-pyexiv2 python-pyexiv2-doc
  python-pypdf python-pyqtgraph python-pyregfi python-qt4-gl python-qt4-phonon
  python-requests-oauthlib python-requests-toolbelt python-rsa python-soappy
  python-stopit python-svn python-tidylib python-tweepy python-uritemplate
  python-vte python-wstools python-yapsy python3.4 python3.4-minimal ratproxy
  rcconf reglookup-doc ruby-rainbow ruby-rexec ruby2.2-dev
  system-config-printer sysv-rc-conf vlc-nox
Use 'apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
55 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
Setting up libpam-systemd:amd64 (232-8) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing package libpam-systemd:amd64 (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up clamav-freshclam (0.99.2+dfsg-5) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing package clamav-freshclam (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up tex-common (6.05) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing package tex-common (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up nfs-common (1:1.3.4-2) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing package nfs-common (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of gdm3:
 gdm3 depends on libpam-systemd; however:
  Package libpam-systemd:amd64 is not configured yet.

dpkg: error processing package gdm3 (--configure):
 dependency problems - leaving unconfigured
Setting up wireshark-common (2.2.3+g57531cd-1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing package wireshark-common (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of udisks2:
 udisks2 depends on libpam-systemd; however:
  Package libpam-systemd:amd64 is not configured yet.

dpkg: error processing package udisks2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of network-manager:
 network-manager depends on libpam-systemd; however:
  Package libpam-systemd:amd64 is not configured yet.

dpkg: error processing package network-manager (--configure):
 dependency problems - leaving unconfigured
Setting up cups-bsd (2.2.1-4) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing package cups-bsd (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of clamav:
 clamav depends on clamav-freshclam (>= 0.99.2+dfsg) | clamav-data; however:
  Package clamav-freshclam is not configured yet.
  Package clamav-data is not installed.
  Package clamav-freshclam which provides clamav-data is not configured yet.

dpkg: error processing package clamav (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-core:
 gnome-core depends on gdm3 (>= 3.20); however:
  Package gdm3 is not configured yet.

dpkg: error processing package gnome-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of clamav-daemon:
 clamav-daemon depends on clamav-freshclam (>= 0.99.2+dfsg) | clamav-data; however:
  Package clamav-freshclam is not configured yet.
  Package clamav-data is not installed.
  Package clamav-freshclam which provides clamav-data is not configured yet.

dpkg: error processing package clamav-daemon (--configure):
 dependency problems - leaving unconfigured
Setting up postgresql-common (178) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing package postgresql-common (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up apt-listchanges (3.8) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing package apt-listchanges (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up unattended-upgrades (0.93.1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing package unattended-upgrades (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of texlive-base:
 texlive-base depends on tex-common (>= 6); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-base (--configure):
 dependency problems - leaving unconfigured
Setting up exim4-daemon-light (4.88-2) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing package exim4-daemon-light (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up php7.0-common (7.0.14-2) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing package php7.0-common (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of tshark:
 tshark depends on wireshark-common (= 2.2.3+g57531cd-1); however:
  Package wireshark-common is not configured yet.

dpkg: error processing package tshark (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-base:
 texlive-latex-base depends on tex-common (>= 6); however:
  Package tex-common is not configured yet.
 texlive-latex-base depends on texlive-base (>= 2016); however:
  Package texlive-base is not configured yet.

dpkg: error processing package texlive-latex-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-base-doc:
 texlive-latex-base-doc depends on texlive-base (>= 2016); however:
  Package texlive-base is not configured yet.
 texlive-latex-base-doc depends on tex-common (>= 6); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-latex-base-doc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of php7.0-mysql:
 php7.0-mysql depends on php7.0-common (= 7.0.14-2); however:
  Package php7.0-common is not configured yet.

dpkg: error processing package php7.0-mysql (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-settings-daemon:
 gnome-settings-daemon depends on libpam-systemd; however:
  Package libpam-systemd:amd64 is not configured yet.

dpkg: error processing package gnome-settings-daemon (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of php7.0-readline:
 php7.0-readline depends on php7.0-common (= 7.0.14-2); however:
  Package php7.0-common is not configured yet.

dpkg: error processing package php7.0-readline (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gvfs-daemons:
 gvfs-daemons depends on udisks2; however:
  Package udisks2 is not configured yet.

dpkg: error processing package gvfs-daemons (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of php7.0-opcache:
 php7.0-opcache depends on php7.0-common (= 7.0.14-2); however:
  Package php7.0-common is not configured yet.

dpkg: error processing package php7.0-opcache (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of php7.0:
 php7.0 depends on php7.0-common; however:
  Package php7.0-common is not configured yet.

dpkg: error processing package php7.0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-session:
 gnome-session depends on gnome-settings-daemon (>= 3.0); however:
  Package gnome-settings-daemon is not configured yet.

dpkg: error processing package gnome-session (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of wireshark-qt:
 wireshark-qt depends on wireshark-common (= 2.2.3+g57531cd-1); however:
  Package wireshark-common is not configured yet.

dpkg: error processing package wireshark-qt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libapache2-mod-php7.0:
 libapache2-mod-php7.0 depends on php7.0-common (= 7.0.14-2); however:
  Package php7.0-common is not configured yet.
 libapache2-mod-php7.0 depends on php7.0-opcache; however:
  Package php7.0-opcache is not configured yet.

dpkg: error processing package libapache2-mod-php7.0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of network-manager-gnome:
 network-manager-gnome depends on network-manager (>= 1.4); however:
  Package network-manager is not configured yet.

dpkg: error processing package network-manager-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kali-desktop-gnome:
 kali-desktop-gnome depends on gnome-core; however:
  Package gnome-core is not configured yet.

dpkg: error processing package kali-desktop-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-shell:
 gnome-shell depends on gnome-settings-daemon (>= 3.16.0); however:
  Package gnome-settings-daemon is not configured yet.

dpkg: error processing package gnome-shell (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-shell-extensions:
 gnome-shell-extensions depends on gnome-shell (>= 3.22); however:
  Package gnome-shell is not configured yet.
 gnome-shell-extensions depends on gnome-shell (<< 3.23); however:
  Package gnome-shell is not configured yet.
 gnome-shell-extensions depends on gnome-session (>= 3.8); however:
  Package gnome-session is not configured yet.

dpkg: error processing package gnome-shell-extensions (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of php7.0-cli:
 php7.0-cli depends on php7.0-common (= 7.0.14-2); however:
  Package php7.0-common is not configured yet.
 php7.0-cli depends on php7.0-opcache; however:
  Package php7.0-opcache is not configured yet.
 php7.0-cli depends on php7.0-readline; however:
  Package php7.0-readline is not configured yet.

dpkg: error processing package php7.0-cli (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-control-center:
 gnome-control-center depends on gnome-settings-daemon (>= 3.19.1); however:
  Package gnome-settings-daemon is not configured yet.

dpkg: error processing package gnome-control-center (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-tweak-tool:
 gnome-tweak-tool depends on gnome-settings-daemon; however:
  Package gnome-settings-daemon is not configured yet.

dpkg: error processing package gnome-tweak-tool (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gvfs:amd64:
 gvfs:amd64 depends on gvfs-daemons (>= 1.30.3-1); however:
  Package gvfs-daemons is not configured yet.
 gvfs:amd64 depends on gvfs-daemons (<< 1.30.3-1.1~); however:
  Package gvfs-daemons is not configured yet.

dpkg: error processing package gvfs:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of php:
 php depends on php7.0; however:
  Package php7.0 is not configured yet.

dpkg: error processing package php (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of postgresql-9.6:
 postgresql-9.6 depends on postgresql-common (>= 171~); however:
  Package postgresql-common is not configured yet.

dpkg: error processing package postgresql-9.6 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of postgresql:
 postgresql depends on postgresql-9.6; however:
  Package postgresql-9.6 is not configured yet.

dpkg: error processing package postgresql (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of php7.0-json:
 php7.0-json depends on php7.0-common (= 7.0.14-2); however:
  Package php7.0-common is not configured yet.

dpkg: error processing package php7.0-json (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of metasploit-framework:
 metasploit-framework depends on postgresql; however:
  Package postgresql is not configured yet.

dpkg: error processing package metasploit-framework (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of php-mysql:
 php-mysql depends on php7.0-mysql; however:
  Package php7.0-mysql is not configured yet.

dpkg: error processing package php-mysql (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nautilus:
 nautilus depends on gvfs (>= 1.3.2); however:
  Package gvfs:amd64 is not configured yet.

dpkg: error processing package nautilus (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-shell-extension-workspacestodock:
 gnome-shell-extension-workspacestodock depends on gnome-shell (>= 3.22); however:
  Package gnome-shell is not configured yet.
 gnome-shell-extension-workspacestodock depends on gnome-shell (<< 3.23); however:
  Package gnome-shell is not configured yet.

dpkg: error processing package gnome-shell-extension-workspacestodock (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gvfs-backends:
 gvfs-backends depends on gvfs (= 1.30.3-1); however:
  Package gvfs:amd64 is not configured yet.
 gvfs-backends depends on gvfs-daemons (= 1.30.3-1); however:
  Package gvfs-daemons is not configured yet.

dpkg: error processing package gvfs-backends (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libapache2-mod-php:
 libapache2-mod-php depends on libapache2-mod-php7.0; however:
  Package libapache2-mod-php7.0 is not configured yet.

dpkg: error processing package libapache2-mod-php (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gvfs-fuse:
 gvfs-fuse depends on gvfs (= 1.30.3-1); however:
  Package gvfs:amd64 is not configured yet.

dpkg: error processing package gvfs-fuse (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kali-linux:
 kali-linux depends on php; however:
  Package php is not configured yet.
  Package php7.0 which provides php is not configured yet.
 kali-linux depends on php-mysql; however:
  Package php-mysql is not configured yet.

dpkg: error processing package kali-linux (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of king-phisher:
 king-phisher depends on postgresql; however:
  Package postgresql is not configured yet.

dpkg: error processing package king-phisher (--configure):
 dependency problems - leaving unconfigured
dpkg: too many errors, stopping
Errors were encountered while processing:
 libpam-systemd:amd64
 clamav-freshclam
 tex-common
 nfs-common
 gdm3
 wireshark-common
 udisks2
 network-manager
 cups-bsd
 clamav
 gnome-core
 clamav-daemon
 postgresql-common
 apt-listchanges
 unattended-upgrades
 texlive-base
 exim4-daemon-light
 php7.0-common
 tshark
 texlive-latex-base
 texlive-latex-base-doc
 php7.0-mysql
 gnome-settings-daemon
 php7.0-readline
 gvfs-daemons
 php7.0-opcache
 php7.0
 gnome-session
 wireshark-qt
 libapache2-mod-php7.0
 network-manager-gnome
 kali-desktop-gnome
 gnome-shell
 gnome-shell-extensions
 php7.0-cli
 gnome-control-center
 gnome-tweak-tool
 gvfs:amd64
 php
 postgresql-9.6
 postgresql
 php7.0-json
 metasploit-framework
 php-mysql
 nautilus
 gnome-shell-extension-workspacestodock
 gvfs-backends
 libapache2-mod-php
 gvfs-fuse
 kali-linux
 king-phisher
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by Bucky Ball on 2017-01-11
Welcome. Try 

```
sudo apt-get autoremove
```

... then

```
sudo apt-get update
sudo apt-get dist-upgrade
```

ALWAYS run the update command before dist-upgrade.

For quicker support, use descriptive thread titles rather than asking how to fix 'this'. Be specific. Also use code tags for terminal output. Swathes of it just put people off. See how to use code tags by following the green link in the first line of my signature below.

Good luck. ;)

PS: Your command 'apt-get dist-upgrade' would suggest you are running as root. If so, why and which release of Ubuntu are you using?

---

### Post by howefield on 2017-01-11
Moved to the "*Ubuntu/Debian BASED*" forum.

---

