---
title: "Help i cant do any thing (dpkg error)"
date: 2017-05-01
forum: Ubuntu/Debian BASED
---

### Post by syrianlegend on 2017-05-01
hello all ...
this is my first thread at all in Linux world but this problem was following me every time i use KaliLinux .
i am very new to this beautiful world , so please be helpful and help me to fix this problem ..

every time i install kali linux and make an update&&upgrade i got initramfs at first of booting and  i can not access to my desktop ..
i did search many threads i have a knowledge says that is happening because of bad update .. 
when i formated my laptop and reinstalled the system many times and 2 days looking for a way to solve this in the end i decided to write this thread right here , when a new error appeared .

when i type ```
apt-get update && apt-get upgrade
```

this is what happening ```
root@kali:~# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  aapt afflib-tools axel bluez cadaver clang commix crda curl dirmngr dradis
  dsniff erlang-asn1 erlang-base erlang-crypto erlang-eunit erlang-inets
  erlang-mnesia erlang-os-mon erlang-public-key erlang-runtime-tools
  erlang-snmp erlang-ssl erlang-syntax-tools erlang-tools erlang-xmerl
  ettercap-common ettercap-graphical evolution-data-server
  evolution-data-server-common ewf-tools firefox-esr folks-common ftp gdb
  gir1.2-gnomedesktop-3.0 gir1.2-mutter-3.0 gir1.2-networkmanager-1.0
  gir1.2-totem-1.0 gir1.2-vte-2.91 gjs gnome-contacts gnome-control-center
  gnome-control-center-data gnome-core gnome-online-accounts gnome-packagekit
  gnome-session gnome-session-bin gnome-session-common gnome-shell
  gnome-shell-common gnome-shell-extension-workspacestodock
  gnome-shell-extensions gnome-sushi gnome-terminal gnome-terminal-data gnupg
  gnupg-agent gnupg2 gnuplot-data gnuplot-qt graphviz gstreamer1.0-libav
  gstreamer1.0-plugins-bad gstreamer1.0-plugins-good guile-2.0-libs gvfs
  gvfs-backends gvfs-bin gvfs-common gvfs-daemons gvfs-fuse gvfs-libs httrack
  hydra hydra-gtk ike-scan imagemagick imagemagick-6.q16 imagemagick-common
  iptables ipython kali-linux king-phisher ldap-utils libafflib0v5
  libalgorithm-diff-xs-perl libapache2-mod-php7.0 libaprutil1
  libaprutil1-dbd-sqlite3 libaprutil1-ldap libavcodec57 libavfilter6
  libavformat57 libcairo-perl libclass-c3-xs-perl libclass-load-xs-perl
  libclc-amdgcn libclc-dev libclc-r600 libcrypt-ssleay-perl libcurl3
  libcurl3-gnutls libdbd-mysql-perl libdbd-sqlite3-perl libdbi-perl
  libdevel-caller-perl libdevel-lexalias-perl libdigest-crc-perl
  libdigest-md4-perl libebackend-1.2-10 libebook-1.2-16
  libebook-contacts-1.2-2 libecal-1.2-19 libedata-book-1.2-25
  libedata-cal-1.2-28 libedataserverui-1.2-1 libevent-core-2.0-5
  libevent-openssl-2.0-5 libevent-pthreads-2.0-5 libewf2 libfbclient2
  libfcgi-perl libfile-fcntllock-perl libfluidsynth1 libfolks-eds25
  libfolks-telepathy25 libfolks25 libfreefare-bin libfreefare0 libgeos-c1v5
  libgjs0e libgl1-mesa-dri libglib-perl libgnome-desktop-3-12 libgoa-1.0-0b
  libgoa-1.0-common libgoa-backend-1.0-1 libgspell-1-1
  libgstreamer-plugins-bad1.0-0 libgtk2-perl libhivex-bin libhtml-parser-perl
  libhttrack2 libip4tc0 libip6tc0 libiptc0 libkpathsea6 libldap-2.4-2 libldb1
  liblircclient0 liblocale-gettext-perl libmath-random-isaac-xs-perl
  libmoose-perl libnet-dbus-perl libnet-pcap-perl libnet-rawip-perl
  libnet-ssh2-perl libnet-ssleay-perl libnm0 libnma0 libopenal-data libopenal1
  libopencv-calib3d2.4v5 libopencv-contrib2.4v5 libopencv-core2.4v5
  libopencv-features2d2.4v5 libopencv-flann2.4v5 libopencv-highgui2.4-deb0
  libopencv-imgproc2.4v5 libopencv-legacy2.4v5 libopencv-ml2.4v5
  libopencv-objdetect2.4v5 libopencv-video2.4v5 libosinfo-1.0-0
  libpackage-stash-xs-perl libpadwalker-perl libpam-systemd libpango-perl
  libparams-classify-perl libparams-util-perl libparted-fs-resize0 libparted2
  libpcsc-perl libphonenumber7 libpoppler-glib8 libpq5 libpsl5 libptexenc1
  libpurple0 libpython-all-dev libpython-dev libpython-stdlib libpython2.7
  libpython2.7-dev libpython2.7-minimal libpython2.7-stdlib libpython3-stdlib
  libpython3.5 libpython3.5-minimal libpython3.5-stdlib libqgsttools-p1
  libqt4-dbus libqt4-declarative libqt4-designer libqt4-help libqt4-network
  libqt4-script libqt4-scripttools libqt4-sql libqt4-sql-mysql libqt4-svg
  libqt4-test libqt4-xml libqt4-xmlpatterns libqt5core5a libqt5dbus5
  libqt5gui5 libqt5multimedia5 libqt5multimedia5-plugins
  libqt5multimediawidgets5 libqt5network5 libqt5opengl5 libqt5printsupport5
  libqt5qml5 libqt5quick5 libqt5scintilla2-12v5 libqt5sql5 libqt5sql5-sqlite
  libqt5svg5 libqt5test5 libqt5webkit5 libqt5widgets5 libqtcore4 libqtdbus4
  libqtgui4 libradare2-dev libruby2.3 libsasl2-2 libsasl2-modules
  libscalar-list-utils-perl libserf-1-1 libsmbclient libsnmp-perl libsnmp30
  libsocket6-perl libsqlite3-0 libsub-identify-perl libsub-name-perl
  libsynctex1 libsystemd0 libterm-readkey-perl libterm-readline-gnu-perl
  libtexlua52 libtexluajit2 libtext-charwidth-perl libtext-iconv-perl
  libtotem0 libudev1 libvariable-magic-perl libvte-2.91-0 libvte-2.91-common
  libwbclient0 libxatracker2 libxml-libxml-perl libxml-parser-perl libzmq5
  linux-image-amd64 mailutils mailutils-common mdbtools medusa mesa-opencl-icd
  mesa-utils mesa-va-drivers mesa-vdpau-drivers mfterm mitmproxy mpg123 mutter
  mutter-common nautilus nautilus-data ndiff network-manager
  network-manager-gnome nmap ntp opensc opensc-pkcs11 openssl ophcrack
  ophcrack-cli parted perl perl-base perl-tk php7.0-cli php7.0-common
  php7.0-json php7.0-mysql php7.0-opcache php7.0-readline pidgin-data
  poppler-utils postgresql postgresql-client-common postgresql-common
  proxytunnel pyrit python python-all python-all-dev python-cryptography
  python-dev python-html5lib python-ldb python-matplotlib python-minimal
  python-mysqldb python-pycurl python-samba python-twisted python-twisted-core
  python-twisted-web python-wheel python-yara python2.7 python2.7-dev
  python2.7-minimal python3 python3-louis python3-minimal python3.5
  python3.5-minimal qdbus radare2 rdesktop recon-ng reportbug rsyslog
  ruby-dataobjects-mysql ruby-eventmachine ruby2.3-dev samba samba-common
  samba-common-bin samba-dsdb-modules samba-libs samba-vfs-modules samdump2
  siege sipcrack smbclient snmp snmpd socat sparta speech-dispatcher
  speech-dispatcher-audio-plugins sqlite3 sqlitebrowser sqsh sslsniff sslsplit
  stunnel4 systemd tcpflow texlive-base texlive-binaries texlive-latex-base
  texlive-latex-base-doc thc-ipv6 totem totem-common totem-plugins tshark udev
  udisks2 vim vim-common vim-gtk vim-gui-common vim-runtime vim-tiny winexe
  wireshark-common wireshark-qt wpasupplicant xpdf xserver-xephyr
  xserver-xorg-core xserver-xorg-input-libinput xserver-xorg-input-wacom
  xserver-xorg-video-amdgpu xserver-xorg-video-ati xserver-xorg-video-fbdev
  xserver-xorg-video-intel xserver-xorg-video-nouveau xserver-xorg-video-qxl
  xserver-xorg-video-radeon xserver-xorg-video-vesa xserver-xorg-video-vmware
  xwayland zeitgeist-core
0 upgraded, 0 newly installed, 0 to remove and 406 not upgraded.
6 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up metasploit-framework (4.14.14-0kali1) ...
dpkg (subprocess): unable to execute installed post-installation script (/var/lib/dpkg/info/metasploit-framework.postinst): Input/output error
dpkg: error processing package metasploit-framework (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up gnome-orca (3.22.2-2) ...
[Errno 5] Input/output error
dpkg: error processing package gnome-orca (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of kali-desktop-gnome:
 kali-desktop-gnome depends on gnome-orca; however:
  Package gnome-orca is not configured yet.

dpkg: error processing package kali-desktop-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kali-linux-full:
 kali-linux-full depends on metasploit-framework; however:
  Package metasploit-framework is not configured yet.

dpkg: error processing package kali-linux-full (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of set:
 set depends on metasploit-framework; however:
  Package metasploit-framework is not configured yet.

dpkg: error processing package set (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ghost-phisher:
 ghost-phisher depends on metasploit-framework; however:
  Package metasploit-framework is not configured yet.

dpkg: error processing package ghost-phisher (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 metasploit-framework
 gnome-orca
 kali-desktop-gnome
 kali-linux-full
 set
 ghost-phisher
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@kali:~# 

```

my source,list is

 ```
deb http://http.kali.org/kali kali-rolling main contrib non-free
# For source package access, uncomment the following line
deb-src http://http.kali.org/kali kali-rolling main contrib non-free
deb http://old.kali.org/kali sana main non-free contrib
# For source package access, uncomment the following line
deb-src http://old.kali.org/kali sana main non-free contrib
```
please any fast help what should i do to never initramfs being shown and to fix this error .
thnx a lot

---

### Post by jeremy31 on 2017-05-01
Moved to Ubuntu/Debian based

---

### Post by #&amp;thj^% on 2017-05-01
Please just take this as friendly advice
The single most common causes of a broken Kali Linux installation are following unofficial advice, and particularly arbitrarily populating the system&#8217;s sources.list file with unofficial repositories. The following post aims to clarify what repositories should exist in sources.list, and when they should be used.

Any additional repositories added to the Kali sources.list file will most likely BREAK YOUR KALI LINUX INSTALL.
These are the official factory sources:
```
deb http://http.kali.org/kali kali-rolling main contrib non-free
deb-src http://http.kali.org/kali kali-rolling main contrib non-free

```
Never have I had good luck with:
Retired Kali sana (2.0) Repositories

For access to the retired sana repositories, have the following entries in your sources.list:
```
deb http://old.kali.org/kali sana main non-free contrib
# For source package access, uncomment the following line
# deb-src http://old.kali.org/kali sana main non-free contrib
```

Source: [http://docs.kali.org/general-use/kali-linux-sources-list-repositories](http://docs.kali.org/general-use/kali-linux-sources-list-repositories)

What should my sources.list look like?
[http://docs.kali.org/faq/kali-sources-list-faq](http://docs.kali.org/faq/kali-sources-list-faq)

---

### Post by syrianlegend on 2017-05-01
so dose that mean i should reinstall the system again with no any unofficial repositories . 
but what about the initramfs >>?

---

### Post by ian-weisser on 2017-05-01
> **syrianlegend said:**
> dpkg (subprocess): unable to execute installed post-installation script (/var/lib/dpkg/info/metasploit-framework.postinst): Input/output error

'input/output' error often means a hardware failure.
Run a SMART test on your hard drive.

---

