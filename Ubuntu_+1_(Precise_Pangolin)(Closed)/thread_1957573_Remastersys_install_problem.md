---
title: "Remastersys install problem"
date: 2012-04-12
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by wolf_3d on 2012-04-12
I'm using this repository to install Remastersys: deb [http://www.remastersys.com/ubuntu](http://www.remastersys.com/ubuntu) oneiric main

But it wants to install 179 packages including KDE for some reason;

```
:~$ sudo apt-get install remastersys
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libcogl5 prboom libtelepathy-farstream1 doom-wad-shareware timidity
  gnome-shell-extensions-common timidity-daemon
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  akonadi-backend-mysql akonadi-server apt-clone archdetect-deb btrfs-tools
  casper cryptsetup dialog discover discover-data dmraid docbook-xsl
  dpkg-repack ecryptfs-utils icoutils kate-data katepart kde-runtime
  kde-runtime-data kde-style-oxygen kde-window-manager
  kde-window-manager-common kdelibs-bin kdelibs5-data kdelibs5-plugins
  kdepim-runtime kdepimlibs-kio-plugins kdoctools keyutils kpartx kpartx-boot
  kubuntu-debug-installer libakonadi-calendar4 libakonadi-contact4
  libakonadi-kabc4 libakonadi-kcal4 libakonadi-kde4 libakonadi-kmime4
  libakonadi-notes4 libakonadiprotocolinternals1 libattica0.3
  libboost-program-options1.46.1 libclucene0ldbl libdebconfclient0
  libdebian-installer4 libdiscover2 libdlrestrictions1 libdmraid1.0.0.rc16
  libdmtx0a libecryptfs0 libencode-locale-perl libfile-listing-perl
  libfont-afm-perl libglade2-0 libhtml-form-perl libhtml-format-perl
  libhtml-parser-perl libhtml-tagset-perl libhtml-tree-perl
  libhttp-cookies-perl libhttp-daemon-perl libhttp-date-perl
  libhttp-message-perl libhttp-negotiate-perl libio-socket-inet6-perl
  libio-socket-ssl-perl libkabc4 libkactivities-bin libkactivities6
  libkalarmcal2 libkatepartinterfaces4 libkcal4 libkcalcore4 libkcalutils4
  libkcmutils4 libkde3support4 libkdeclarative5 libkdecorations4 libkdecore5
  libkdesu5 libkdeui5 libkdewebkit5 libkdnssd4 libkemoticons4 libkephal4abi1
  libkfile4 libkholidays4 libkhtml5 libkidletime4 libkimap4 libkio5 libkjsapi4
  libkjsembed4 libkldap4 libkmbox4 libkmediaplayer4 libkmime4 libknewstuff2-4
  libknewstuff3-4 libknotifyconfig4 libkntlm4 libkparts4 libkpimidentities4
  libkpimtextedit4 libkpimutils4 libkprintutils4 libkpty4 libkresources4
  libkrosscore4 libktexteditor4 libkwineffects1abi3 libkwinglutils1
  libkwinnvidiahack4 libkworkspace4abi1 liblwp-mediatypes-perl
  liblwp-protocol-https-perl liblzo2-2 libmailtools-perl libmailtransport4
  libmicroblog4 libnepomuk4 libnepomukdatamanagement4 libnepomukquery4a
  libnepomuksync4 libnepomukutils4 libnet-http-perl libnet-ssleay-perl
  libntrack-qt4-1 libntrack0 libphonon4 libplasma3 libpolkit-qt-1-1 libprison0
  libqapt-runtime libqapt1 libqca2 libqrencode3 libqt4-qt3support
  libsocket6-perl libsolid4 libsoprano4 libstreamanalyzer0 libstreams0
  libthreadweaver4 liburi-perl libvirtodbc0 libwww-perl libwww-robotrules-perl
  libxml2-utils localechooser-data mysql-client-core-5.5 mysql-server-core-5.5
  ntrack-module-libnl-0 odbcinst odbcinst1debian2 oxygen-icon-theme phonon
  phonon-backend-gstreamer plasma-scriptengine-javascript python-glade2
  python-kde4 python-pyicu qapt-batch rdate realpath reiserfsprogs
  shared-desktop-ontologies soprano-daemon squashfs-tools ubiquity
  ubiquity-casper ubiquity-frontend-kde ubiquity-ubuntu-artwork user-setup
  virtuoso-minimal virtuoso-opensource-6.1-bin virtuoso-opensource-6.1-common
  xresprobe
Suggested packages:
  akonadi-backend-sqlite akonadi-backend-postgresql busybox
  docbook-xsl-doc-html docbook-xsl-doc-pdf docbook-xsl-doc-text
  docbook-xsl-doc libsaxon-java libxalan2-java libxslthl-java
  docbook-xsl-saxon fop xalan dbtoepub opencryptoki keyescrow-client
  libterm-readline-gnu-perl libterm-readline-perl-perl djvulibre-bin finger
  libdata-dump-perl hspell libcrypt-ssleay-perl libqca2-plugin-cyrus-sasl
  libqca2-plugin-gnupg libqca2-plugin-ossl libauthen-ntlm-perl
  phonon-backend-vlc phonon-backend-xine phonon-backend-mplayer
  python-gtk2-doc plymouth-x11
The following NEW packages will be installed
  akonadi-backend-mysql akonadi-server apt-clone archdetect-deb btrfs-tools
  casper cryptsetup dialog discover discover-data dmraid docbook-xsl
  dpkg-repack ecryptfs-utils icoutils kate-data katepart kde-runtime
  kde-runtime-data kde-style-oxygen kde-window-manager
  kde-window-manager-common kdelibs-bin kdelibs5-data kdelibs5-plugins
  kdepim-runtime kdepimlibs-kio-plugins kdoctools keyutils kpartx kpartx-boot
  kubuntu-debug-installer libakonadi-calendar4 libakonadi-contact4
  libakonadi-kabc4 libakonadi-kcal4 libakonadi-kde4 libakonadi-kmime4
  libakonadi-notes4 libakonadiprotocolinternals1 libattica0.3
  libboost-program-options1.46.1 libclucene0ldbl libdebconfclient0
  libdebian-installer4 libdiscover2 libdlrestrictions1 libdmraid1.0.0.rc16
  libdmtx0a libecryptfs0 libencode-locale-perl libfile-listing-perl
  libfont-afm-perl libglade2-0 libhtml-form-perl libhtml-format-perl
  libhtml-parser-perl libhtml-tagset-perl libhtml-tree-perl
  libhttp-cookies-perl libhttp-daemon-perl libhttp-date-perl
  libhttp-message-perl libhttp-negotiate-perl libio-socket-inet6-perl
  libio-socket-ssl-perl libkabc4 libkactivities-bin libkactivities6
  libkalarmcal2 libkatepartinterfaces4 libkcal4 libkcalcore4 libkcalutils4
  libkcmutils4 libkde3support4 libkdeclarative5 libkdecorations4 libkdecore5
  libkdesu5 libkdeui5 libkdewebkit5 libkdnssd4 libkemoticons4 libkephal4abi1
  libkfile4 libkholidays4 libkhtml5 libkidletime4 libkimap4 libkio5 libkjsapi4
  libkjsembed4 libkldap4 libkmbox4 libkmediaplayer4 libkmime4 libknewstuff2-4
  libknewstuff3-4 libknotifyconfig4 libkntlm4 libkparts4 libkpimidentities4
  libkpimtextedit4 libkpimutils4 libkprintutils4 libkpty4 libkresources4
  libkrosscore4 libktexteditor4 libkwineffects1abi3 libkwinglutils1
  libkwinnvidiahack4 libkworkspace4abi1 liblwp-mediatypes-perl
  liblwp-protocol-https-perl liblzo2-2 libmailtools-perl libmailtransport4
  libmicroblog4 libnepomuk4 libnepomukdatamanagement4 libnepomukquery4a
  libnepomuksync4 libnepomukutils4 libnet-http-perl libnet-ssleay-perl
  libntrack-qt4-1 libntrack0 libphonon4 libplasma3 libpolkit-qt-1-1 libprison0
  libqapt-runtime libqapt1 libqca2 libqrencode3 libqt4-qt3support
  libsocket6-perl libsolid4 libsoprano4 libstreamanalyzer0 libstreams0
  libthreadweaver4 liburi-perl libvirtodbc0 libwww-perl libwww-robotrules-perl
  libxml2-utils localechooser-data mysql-client-core-5.5 mysql-server-core-5.5
  ntrack-module-libnl-0 odbcinst odbcinst1debian2 oxygen-icon-theme phonon
  phonon-backend-gstreamer plasma-scriptengine-javascript python-glade2
  python-kde4 python-pyicu qapt-batch rdate realpath reiserfsprogs remastersys
  shared-desktop-ontologies soprano-daemon squashfs-tools ubiquity
  ubiquity-casper ubiquity-frontend-kde ubiquity-ubuntu-artwork user-setup
  virtuoso-minimal virtuoso-opensource-6.1-bin virtuoso-opensource-6.1-common
  xresprobe
0 upgraded, 179 newly installed, 0 to remove and 0 not upgraded.
Need to get 83.1 MB of archives.
After this operation, 277 MB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.

```

Assuming that a precise repository is in progress?

---

### Post by bluexrider on 2012-04-12
I got my version from here [http://www.remastersys.com/downloads/](http://www.remastersys.com/downloads/)

---

### Post by cariboo on 2012-04-12
Updates are coming hard and fast, I updated 3 times yesterday, and this morning there were another 150+ packages that needed updating.

---

