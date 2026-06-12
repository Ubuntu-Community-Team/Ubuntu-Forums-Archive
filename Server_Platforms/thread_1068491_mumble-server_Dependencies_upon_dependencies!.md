---
title: "mumble-server: Dependencies upon dependencies!"
date: 2009-02-12
forum: Server Platforms
---

### Post by BorgHunter on 2009-02-12
I just got an Intrepid VPS set up, and hey, I want to do all sorts of fun stuff with it! One of the first things I thought of was a Mumble VoIP server. Ubuntu has Mumble's command line server version, Murmur, in the repo as mumble-server. I go to install it on my VPS, and it comes up with the following list of dependencies:
```
  bsd-mailx consolekit cron dbus dbus-x11 defoma exim4 exim4-base
  exim4-config exim4-daemon-light fontconfig fontconfig-config ghostscript
  gsfonts hicolor-icon-theme ice33-slice ice33-translators libatk1.0-0
  libatk1.0-data libcairo2 libcgi-session-perl libck-connector0
  libcompress-raw-zlib-perl libcompress-zlib-perl libconfig-simple-perl
  libcroco3 libcups2 libcupsimage2 libdatrie0 libdbi-perl libdbus-1-3
  libdbus-glib-1-2 libdigest-hmac-perl libdigest-sha1-perl libdjvulibre21
  libfont-afm-perl libfontconfig1 libfontenc1 libfreetype6 libgd2-noxpm
  libglib2.0-0 libglib2.0-data libgraphviz4 libgs8 libgsf-1-114
  libgsf-1-common libgtk2.0-0 libgtk2.0-bin libgtk2.0-common
  libhtml-format-perl libhtml-parser-perl libhtml-tagset-perl
  libhtml-tree-perl libice6 libiceutil33 libilmbase6
  libio-compress-base-perl libio-compress-zlib-perl libjasper1 libjpeg62
  liblcms1 libltdl7 libmagick10 libmailtools-perl libmcpp0
  libnet-daemon-perl libnet-dbus-perl libnet-dns-perl libnet-ip-perl
  libopenexr6 libpam-ck-connector libpango1.0-0 libpango1.0-common
  libpaper-utils libpaper1 libpixman-1-0 libplrpc-perl libpng12-0 libpolkit2
  libqt4-dbus libqt4-network libqt4-sql libqt4-sql-mysql libqt4-sql-sqlite
  libqt4-xml libqtcore4 librsvg2-2 libslice33 libsm6 libthai-data libthai0
  libtie-ixhash-perl libtiff4 libtimedate-perl liburi-perl libwmf0.2-7
  libwww-perl libx11-6 libx11-data libxau6 libxcb-render-util0
  libxcb-render0 libxcb-xlib0 libxcb1 libxcomposite1 libxcursor1 libxdamage1
  libxdmcp6 libxext6 libxfixes3 libxfont1 libxft2 libxi6 libxinerama1
  libxml-parser-perl libxml-twig-perl libxml-xpath-perl libxrandr2
  libxrender1 libxt6 libzeroc-ice33 mailx mumble-server mumble-server-web
  perlmagick php-zeroc-ice psfontmgr psmisc ttf-dejavu ttf-dejavu-core
  ttf-dejavu-extra x-ttcidfont-conf x11-common xfonts-encodings xfonts-utils
```
xfont? x11? *libcups?!* mumble-server (Murmur) is a command-line program—why is the package trying to make me install 140 MB of cruft?

---

### Post by windependence on 2009-02-13
Some packages may contain libraries that are needed by your install even though it may not be obvious.

I use Linux when necessary, but one of the reasons I like to use FreeBSD is because I can compile everything using the ports system, and it will only bring in the actual dependencies I need. Much more lean and mean.

-Tim

---

### Post by BorgHunter on 2009-02-13
Well yeah, I use Gentoo on my desktop, and its Portage system is very similar to FreeBSD's Ports. But lord, do I really want to go through the hell of installing Gentoo on the server, only to find I've broken something that managed to make the server unreachable? (It's not unlikely—kernel panics were something of a routine for me until I recompiled the kernel.)

---

### Post by downhillgames on 2009-02-13
It's the -web package that's causing you to pull in *so* many deps. Best just to compile it yourself with as few features as you need.

---

### Post by arch_o_median on 2009-03-05
I've hit a similar issue.   I trying to pare down my installed packages and when I sudo apt-get remove --purge libthai0 I get:

The following packages were automatically installed and are no longer required:
  libfreebob0 libofx4 libical0 libjaxp1.3-java libaccess-bridge-java
  libgoffice-0-6-common guile-1.6 fakeroot libgringotts2
  cacao-oj6-jre-headless libxerces2-java python-numpy debhelper libgcj9-0
  libreadline5-dev libgcj-bc gfortran-4.3 libblas-dev libosp5 libxalan2-java
  libfluidsynth1 patchutils libchipcard-data libaqbanking-data bsh-gcj
  libcrypt-ssleay-perl libjack0 libdate-manip-perl libaqofxconnect4
  java-common po-debconf libcddb2 guile-1.6-libs python-uniconvertor
  python-lxml libaqbanking20-plugins-qt g++ liblapack3gf intltool-debian
  libguile-ltdl-1 libpcrecpp0 libxerces2-java-gcj liblapack-dev slib
  libmcrypt4 libbinio1ldbl ttf-telugu-fonts bsh libchipcardc2 aqbanking-tools
  ttf-bengali-fonts libaudclient1 libgconfmm-2.6-1c2 libresid-builder0c2a
  tzdata-java libpulse-mainloop-glib0 gfortran libgsf-gnome-1-114 libgcj9-jar
  gcj-4.3-base libaqhbci13 libgwenhywfar47 build-essential libmowgli1 dpkg-dev
  libfinance-quote-perl libblas3gf cacao-oj6-jre tcl8.4 libsidplay2 rhino
  tk8.4 guile-1.6-slib gnucash-common libmad0 libgfortran3 libid3tag0
  libpcre3-dev ca-certificates-java html2text libxft-dev
  libaqbanking20-plugins ttf-kannada-fonts libmhash2 libqt3-mt libmcs1
  libgcj-common libktoblzcheck1c2a libaqbanking-plugins-libgwenhywfar47
  cacao-oj6-jre-lib ladcca2 libimlib2 libmail-sendmail-perl libxalan2-java-gcj
  libaqbanking20 ttf-oriya-fonts libsys-hostname-long-perl libmpcdec3
  libchipcard-ctapi0 libjline-java dpatch pulseaudio-module-zeroconf
  libhtml-tableextract-perl libbz2-dev libqbanking5 libmms0
  libchipcard-libgwenhywfar47-plugins libjaxp1.3-java-gcj

  This seems like a really silly set of dependencies to me....

---

