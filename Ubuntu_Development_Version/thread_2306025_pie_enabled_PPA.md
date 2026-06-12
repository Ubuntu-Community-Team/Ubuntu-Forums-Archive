---
title: "pie enabled PPA"
date: 2015-12-11
forum: Ubuntu Development Version
---

### Post by zika on 2015-12-11
```
sudo apt-add-repository ppa:sbeattie/gcc-pie-amd64
sudo apt-get update
sudo apt-get upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following package was automatically installed and is no longer required:
  libhunspell-1.3-0v5
Use 'sudo apt autoremove' to remove it.
The following packages will be upgraded:
  account-plugin-aim account-plugin-facebook account-plugin-flickr account-plugin-google account-plugin-jabber account-plugin-salut account-plugin-twitter account-plugin-yahoo acl acpi-support activity-log-manager activity-log-manager-control-center adduser aisleriot alsa-utils anacron apg apparmor appmenu-qt
  apturl apturl-common aspell at at-spi2-core auditd avahi-autoipd avahi-daemon avahi-utils bamfdaemon baobab base-passwd bash bc bind9 bind9-host bind9utils blt bluez bluez-cups bluez-obexd brasero brasero-cdrkit brasero-common brltty bsdmainutils bsdutils build-essential busybox-initramfs busybox-static bzip2
  cgmanager cheese cheese-common colord colord-data command-not-found command-not-found-data compiz compiz-core compiz-gnome compiz-plugins compiz-plugins-default compiz-plugins-main compizconfig-settings-manager console-setup console-setup-linux coreutils cpio cpu-checker cracklib-runtime crda cron cups-pk-helper
  dash dc dconf-cli dconf-gsettings-backend dconf-service debianutils debugedit deja-dup deja-dup-backend-gvfs desktop-file-utils dialog diffstat diffutils dnsmasq dnsmasq-base dnsutils dosfstools dpkg dpkg-dev duplicity dvd+rw-tools ed eject empathy empathy-common enchant eog espeak-data ethtool evince
  evince-common fakeroot fcitx fcitx-bin fcitx-data fcitx-frontend-all fcitx-frontend-gtk2 fcitx-frontend-gtk3 fcitx-frontend-qt4 fcitx-module-dbus fcitx-module-kimpanel fcitx-module-lua fcitx-module-x11 fcitx-modules fcitx-ui-classic file file-roller fontconfig fontconfig-config ftp gawk gcr gdb gdbserver gdisk
  gedit gedit-common genisoimage geoclue geoclue-ubuntu-geoip gettext gettext-base ghostscript ghostscript-x gir1.2-accounts-1.0 gir1.2-appindicator3-0.1 gir1.2-atk-1.0 gir1.2-atspi-2.0 gir1.2-dee-1.0 gir1.2-gck-1 gir1.2-gcr-3 gir1.2-gdata-0.0 gir1.2-gkbd-3.0 gir1.2-gmenu-3.0 gir1.2-gnomebluetooth-1.0
  gir1.2-gnomekeyring-1.0 gir1.2-gst-plugins-base-1.0 gir1.2-gstreamer-1.0 gir1.2-gtksource-3.0 gir1.2-gucharmap-2.90 gir1.2-gweather-3.0 gir1.2-javascriptcoregtk-3.0 gir1.2-json-1.0 gir1.2-messagingmenu-1.0 gir1.2-notify-0.7 gir1.2-peas-1.0 gir1.2-polkit-1.0 gir1.2-rb-3.0 gir1.2-secret-1 gir1.2-signon-1.0
  gir1.2-telepathyglib-0.12 gir1.2-telepathylogger-0.2 gir1.2-totem-1.0 gir1.2-totem-plparser-1.0 gir1.2-udisks-2.0 gir1.2-unity-5.0 gir1.2-upowerglib-1.0 gir1.2-webkit-3.0 gir1.2-wnck-3.0 gir1.2-xkl-1.0 gir1.2-zeitgeist-2.0 gkbd-capplet glib-networking glib-networking-common glib-networking-services
  gnome-accessibility-themes gnome-bluetooth gnome-calculator gnome-disk-utility gnome-font-viewer gnome-keyring gnome-mahjongg gnome-menus gnome-mines gnome-power-manager gnome-screenshot gnome-session-canberra gnome-sudoku gnome-system-log gnome-system-monitor gnome-themes-standard gnome-themes-standard-data
  gnome-user-share gnomine gnupg gnupg-agent gnupg2 gpgv grep grilo-plugins-0.2 grilo-plugins-0.2-base grilo-plugins-0.2-extra groff-base growisofs grub-common grub-pc grub-pc-bin grub2-common gstreamer0.10-alsa gstreamer0.10-gconf gstreamer0.10-nice gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps
  gstreamer0.10-plugins-good gstreamer0.10-pulseaudio gstreamer0.10-tools gstreamer0.10-x gstreamer1.0-alsa gstreamer1.0-clutter gstreamer1.0-clutter-3.0 gstreamer1.0-nice gstreamer1.0-plugins-base gstreamer1.0-plugins-base-apps gstreamer1.0-plugins-good gstreamer1.0-pulseaudio gstreamer1.0-tools gstreamer1.0-x
  gtk2-engines-murrine gtk2-engines-pixbuf gucharmap guile-2.0-libs gvfs gvfs-backends gvfs-bin gvfs-common gvfs-daemons gvfs-fuse gvfs-libs gzip hdparm hostname hplip hplip-data hud hyphen-en-us ifupdown indicator-application indicator-appmenu indicator-bluetooth indicator-datetime indicator-keyboard
  indicator-messages indicator-power indicator-printers indicator-session indicator-sound info init init-system-helpers initramfs-tools initramfs-tools-bin initscripts inputattach insserv install-info intel-gpu-tools ippusbxd iptables iputils-arping iputils-ping iputils-tracepath irqbalance isc-dhcp-client
  isc-dhcp-common java-common jayatana kbd kerneloops-daemon keyboard-configuration klibc-utils kmod krb5-locales landscape-client-ui-install laptop-detect less lib32z1 libaa1 libabw-0.1-1v5 libaccount-plugin-1.0-0 libaccount-plugin-generic-oauth libaccount-plugin-google libaccounts-glib0 libaccounts-qt5-1 libacl1
  libalgorithm-diff-xs-perl libao-common libao4 libapparmor-perl libapparmor1 libappindicator1 libappindicator3-1 libarchive13 libart-2.0-2 libasn1-8-heimdal libasound2 libasound2-data libasound2-plugins libaspell15 libasprintf-dev libasprintf0v5 libassuan0 libasyncns0 libatasmart4 libatk-adaptor
  libatk-bridge2.0-0 libatk-wrapper-java libatk-wrapper-java-jni libatk1.0-0 libatk1.0-data libatkmm-1.6-1v5 libatspi2.0-0 libattr1 libaudio2 libaudit-common libaudit1 libauparse0 libavahi-client3 libavahi-common-data libavahi-common3 libavahi-core7 libavahi-glib1 libavahi-gobject0 libavahi-ui-gtk3-0 libavc1394-0
  libb-hooks-op-check-perl libbabeltrace-ctf1 libbabeltrace1 libbamf3-2 libbareword-filehandles-perl libbind9-90 libblas-common libblas3 libblkid1 libbluetooth3 libbonobo2-0 libbonobo2-common libbonoboui2-0 libbonoboui2-common libbrasero-media3-1 libbrlapi0.6 libbsd0 libburn4 libbz2-1.0 libcaca0 libcairomm-1.0-1v5
  libcanberra-gtk-module libcanberra-gtk0 libcanberra-gtk3-0 libcanberra-gtk3-module libcanberra-pulse libcanberra0 libcap-ng0 libcap2 libcap2-bin libcdio-cdda1 libcdio-paranoia1 libcdio13 libcdparanoia0 libcdr-0.1-1v5 libcgmanager0 libchamplain-0.12-0 libcheese-gtk25 libcheese8 libclass-c3-xs-perl
  libclass-xsaccessor-perl libclone-perl libcloog-isl4 libclucene-contribs1v5 libclucene-core1v5 libclutter-gst-2.0-0 libclutter-gst-3.0-0 libcolord-gtk1 libcolord2 libcolorhug2 libcolumbus1-common libcolumbus1v5 libcompizconfig0 libconfig9 libcrack2 libcroco3 libcryptsetup4 libcurl3 libcurl3-gnutls libcwidget3v5
  libdaemon0 libdatrie1 libdb5.3 libdbus-glib-1-2 libdbusmenu-qt2 libdbusmenu-qt5 libdconf1 libdebconfclient0 libdecoration0 libdee-1.0-4 libdevel-caller-perl libdevel-lexalias-perl libdiscid0 libdjvulibre-text libdjvulibre21 libdmapsharing-3.0-2 libdns-export100 libdns100 libdotconf0 libdouble-conversion1v5
  libdpkg-perl libdv4 libe-book-0.1-1 libedit2 libelf1 libenchant1c2a libeot0 libepoxy0 libespeak1 libestr0 libetonyek-0.1-1 libevdocument3-4 libevent-2.0-5 libevent-core-2.0-5 libevent-pthreads-2.0-5 libevview3-3 libexempi3 libexif12 libexiv2-14 libexpat1 libexttextcat-2.0-0 libexttextcat-data libfakeroot
  libfarstream-0.1-0 libfarstream-0.2-5 libfcgi-perl libfcitx-config4 libfcitx-core0 libfcitx-gclient0 libfcitx-qt0 libfcitx-utils0 libfdisk1 libfdt1 libffi6 libfftw3-double3 libfftw3-single3 libfile-fcntllock-perl libflac8 libflite1 libfontconfig1 libfontenc1 libframe6 libfreehand-0.1-1 libfreerdp-cache1.1
  libfreerdp-client1.1 libfreerdp-codec1.1 libfreerdp-common1.1.0 libfreerdp-core1.1 libfreerdp-crypto1.1 libfreerdp-gdi1.1 libfreerdp-locale1.1 libfreerdp-plugins-standard libfreerdp-primitives1.1 libfreerdp-utils1.1 libfreetype6 libfribidi0 libfs6 libgail-common libgail18 libgc1c2 libgck-1-0 libgcr-3-common
  libgcr-base-3-1 libgcr-ui-3-1 libgcrypt20 libgd3 libgdata-common libgdata22 libgdbm3 libgee-0.8-2 libgee2 libgeis1 libgeoclue-2-0 libgeoclue0 libgeocode-glib0 libgeoip1 libgettextpo-dev libgettextpo0 libgexiv2-2 libgif7 libglade2-0 libglew1.13 libglewmx1.13 libglibmm-2.4-1v5 libglu1-mesa libgmime-2.6-0 libgmp10
  libgnome-bluetooth13 libgnome-keyring-common libgnome-keyring0 libgnome-menu-3-0 libgnome2-0 libgnome2-bin libgnome2-common libgnomecanvas2-0 libgnomecanvas2-common libgnomekbd-common libgnomekbd8 libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnomevfs2-common libgnutls-deb0-28 libgnutls-openssl27 libgom-1.0-0
  libgom-1.0-common libgpg-error0 libgpgme11 libgpm2 libgpod-common libgpod4 libgrail6 libgraphite2-3 libgrilo-0.2-1 libgrip0 libgs9 libgs9-common libgssapi-krb5-2 libgssapi3-heimdal libgssdp-1.0-3 libgstreamer-plugins-base0.10-0 libgstreamer-plugins-base1.0-0 libgstreamer-plugins-good1.0-0 libgstreamer0.10-0
  libgstreamer1.0-0 libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libgtkmm-3.0-1v5 libgtksourceview-3.0-1 libgtksourceview-3.0-common libgtop-2.0-10 libgtop2-common libgucharmap-2-90-7 libgupnp-1.0-4 libgupnp-igd-1.0-4 libgusb2 libgutenprint2 libgweather-3-6 libgweather-common libgxps2 libharfbuzz-icu0 libharfbuzz0b
  libhcrypto4-heimdal libheimbase1-heimdal libheimntlm0-heimdal libhogweed4 libhpmud0 libhtml-parser-perl libhud2 libhunspell-1.3-0 libhunspell-1.3-0v5 libhx509-5-heimdal libhyphen0 libical1a libice6 libicu55 libid3tag0 libidn11 libido3-0.1-0 libiec61883-0 libieee1284-3 libijs-0.35 libilmbase12 libimlib2
  libimobiledevice4 libimobiledevice6 libindirect-perl libirs-export91 libisc-export95 libisc95 libisccc90 libisccfg-export90 libisccfg90 libisl15 libiso9660-8 libisofs6 libiw30 libjack-jackd2-0 libjasper1 libjavascriptcoregtk-1.0-0 libjavascriptcoregtk-3.0-0 libjbig0 libjbig2dec0 libjpeg-turbo-progs
  libjpeg-turbo8 libjpeg62 libjpeg8 libjson-c2 libjson-glib-1.0-0 libjson-glib-1.0-common libjson0 libjte1 libk5crypto3 libklibc libkmod2 libkrb5-26-heimdal libkrb5-3 libkrb5support0 libksba8 liblangtag-common liblangtag1 liblapack3 liblcms2-2 liblcms2-utils libldap-2.4-2 libldb1 liblexical-sealrequirehints-perl
  liblightdm-gobject-1-0 liblircclient0 liblist-moreutils-perl libllvm3.6v5 liblocale-gettext-perl liblockfile-bin liblockfile1 liblouis2 libltdl7 liblua5.2-0 liblwres90 liblzma5 liblzo2-2 libmagic1 libmeanwhile1 libmediaart-2.0-0 libmessaging-menu0 libmetacity-private3a libmhash2 libmirclient9 libmircommon5
  libmirprotobuf3 libmission-control-plugins0 libmm-glib0 libmng2 libmnl0 libmount1 libmpc3 libmpdec2 libmpfr4 libmspub-0.1-1 libmtp-common libmtp-runtime libmtp9 libmultidimensional-perl libmysqlclient18 libmythes-1.2-0 libnatpmp1 libncurses5 libncursesw5 libneon27-gnutls libnet-dbus-perl libnet-dns-perl
  libnet-libidn-perl libnet-ssleay-perl libnetaddr-ip-perl libnetfilter-conntrack3 libnettle6 libnewt0.52 libnfnetlink0 libnice10 libnih-dbus1 libnih1 libnotify-bin libnotify4 libnspr4 libnspr4-0d libnss-mdns libnss3 libnss3-1d libnss3-nssdb libnuma1 libnux-4.0-0 libnux-4.0-common liboauth0 libodfgen-0.1-1 libogg0
  libopencc1 libopenexr22 libopenobex1 libopts25 libopus0 liborbit-2-0 liborc-0.4-0 liborcus-0.10-0v5 libp11-kit-gnome-keyring libp11-kit0 libpackage-stash-xs-perl libpadwalker-perl libpagemaker-0.0-0 libpam-cap libpam-gnome-keyring libpam-modules libpam-modules-bin libpam-runtime libpam0g libpangomm-1.4-1v5
  libpangox-1.0-0 libpaper-utils libpaper1 libparams-classify-perl libparams-util-perl libparams-validate-perl libparted2 libpcap0.8 libpci3 libpciaccess0 libpcre16-3 libpcre3 libpcsclite1 libpeas-1.0-0 libpeas-common libperl5.20 libperlio-gzip-perl libphonon4qt5-4 libpipeline1 libpixman-1-0 libpkcs11-helper1
  libplist3 libpng12-0 libpolkit-agent-1-0 libpolkit-backend-1-0 libpolkit-gobject-1-0 libpoppler-glib8 libpoppler56 libpoppler57 libpopt0 libportaudio2 libpresage-data libpresage1v5 libprocps4 libproxy-tools libproxy1-plugin-gsettings libproxy1-plugin-networkmanager libproxy1v5 libpst4 libpth20
  libpulse-mainloop-glib0 libpulse0 libpulsedsp libpurple-bin libpurple0 libpwquality-common libpwquality1 libpython3-stdlib libqpdf17 libqqwing2v5 libqt4-dbus libqt4-declarative libqt4-designer libqt4-help libqt4-network libqt4-opengl libqt4-script libqt4-scripttools libqt4-sql libqt4-sql-sqlite libqt4-svg
  libqt4-test libqt4-xml libqt4-xmlpatterns libqtassistantclient4 libqtcore4 libqtdbus4 libqtgui4 libqtwebkit4 libquvi7 libraptor2-0 librarian0 librasqal3 libraw15 librdf0 libreadline5 libreadline6 librest-0.7-0 librevenge-0.0-0 librhythmbox-core9 libroken18-heimdal librpm3 librpmbuild3 librpmio3 librpmsign3
  librsvg2-2 librsvg2-common librsync1 librtmp1 libruby2.1 libruby2.2 libsamplerate0 libsane libsane-common libsane-hpaio libsasl2-2 libsasl2-modules libsasl2-modules-db libsbc1 libsdl1.2debian libseccomp2 libsecret-1-0 libsecret-common libsensors4 libsgutils2-2 libshout3 libsigc++-2.0-0v5 libsignon-extension1
  libsignon-glib1 libsignon-plugins-common1 libsignon-qt5-1 libsigsegv2 libslang2 libsm6 libsmartcols1 libsmbclient libsnappy1v5 libsndfile1 libsnmp-base libsnmp30 libsocket6-perl libsonic0 libspectre1 libspeechd2 libspeex1 libspeexdsp1 libspice-server1 libsqlite3-0 libssh-4 libssh-gcrypt-4 libssl1.0.0
  libstartup-notification0 libsub-identify-perl libsub-name-perl libtalloc2 libtasn1-6 libtcl8.6 libtelepathy-farstream3 libtelepathy-glib0 libtelepathy-logger3 libtevent0 libtext-charwidth-perl libtext-iconv-perl libtext-soundex-perl libthai-data libthai0 libtheora0 libtiff5 libtimezonemap-data libtimezonemap1
  libtinfo5 libtinyxml2.6.2v5 libtk8.6 libtotem-plparser-common libtotem-plparser18 libtotem0 libtracker-sparql-1.0-0 libtxc-dxtn-s2tc0 libtype-tiny-xs-perl libudisks2-0 libunicode-utf8-perl libunistring0 libunity-action-qt1 libunity-control-center1 libunity-core-6.0-9 libunity-gtk2-parser0 libunity-gtk3-parser0
  libunity-misc4 libunity-protocol-private0 libunity-scopes-json-def-desktop libunity-settings-daemon1 libunity-webapps0 libunity9 libunwind8 libupower-glib3 libupstart1 libusb-0.1-4 libusbmuxd2 libustr-1.0-1 libutempter0 libuuid-perl libuuid1 libvariable-magic-perl libvdpau1 libvisio-0.1-1 libvisual-0.4-0
  libvncclient1 libvorbis0a libvorbisenc2 libvorbisfile3 libvpx2 libvte-common libvte9 libwacom-bin libwacom-common libwacom2 libwavpack1 libwbclient0 libwebkitgtk-1.0-0 libwebkitgtk-1.0-common libwebkitgtk-3.0-0 libwebkitgtk-3.0-common libwebp5 libwebpmux1 libwebrtc-audio-processing-0 libwhoopsie-preferences0
  libwhoopsie0 libwind0-heimdal libwinpr-crt0.1 libwinpr-dsparse0.1 libwinpr-environment0.1 libwinpr-file0.1 libwinpr-handle0.1 libwinpr-heap0.1 libwinpr-input0.1 libwinpr-interlocked0.1 libwinpr-library0.1 libwinpr-path0.1 libwinpr-pool0.1 libwinpr-registry0.1 libwinpr-rpc0.1 libwinpr-sspi0.1 libwinpr-synch0.1
  libwinpr-sysinfo0.1 libwinpr-thread0.1 libwinpr-utils0.1 libwmf0.2-7 libwmf0.2-7-gtk libwnck-3-0 libwnck-3-common libwnck-common libwnck22 libwrap0 libx11-6 libx11-data libx11-xcb1 libxapian22v5 libxau6 libxaw7 libxcb-composite0 libxcb-dri2-0 libxcb-dri3-0 libxcb-glx0 libxcb-icccm4 libxcb-image0 libxcb-keysyms1
  libxcb-present0 libxcb-randr0 libxcb-render-util0 libxcb-render0 libxcb-screensaver0 libxcb-shape0 libxcb-shm0 libxcb-sync1 libxcb-util1 libxcb-xf86dri0 libxcb-xfixes0 libxcb-xkb1 libxcb-xtest0 libxcb-xv0 libxcb1 libxcomposite1 libxcursor1 libxdamage1 libxdmcp6 libxext6 libxfixes3 libxft2 libxinerama1
  libxkbcommon-x11-0 libxkbcommon0 libxkbfile1 libxklavier16 libxml-parser-perl libxpm4 libxrandr2 libxrender1 libxres1 libxslt1.1 libxss1 libxt6 libxtables10 libxtst6 libxv1 libxvmc1 libxxf86dga1 libxxf86vm1 libyajl2 libyaml-0-2 libyelp0 libzeitgeist-1.0-1 libzeitgeist-2.0-0 libzephyr4 libzzip-0-13 lightdm
  lm-sensors lockfile-progs login logrotate lsb lsb-core lsb-cxx lsb-desktop lsb-graphics lsb-invalid-mta lsb-languages lsb-multimedia lsb-printing lsb-security lshw lsof ltrace m4 make man-db mawk mcp-account-manager-uoa memtest86+ metacity metacity-common mlocate module-init-tools mount mountall mousetweaks
  mscompress msr-tools mtools mysql-common nautilus-sendto ncurses-base ncurses-bin ncurses-term ndisc6 net-tools netcat-openbsd notification-daemon notify-osd ntp ntpdate nux-tools obex-data-server ocl-icd-libopencl1 onboard onboard-data openssl openvpn os-prober overlay-scrollbar overlay-scrollbar-gtk2 p11-kit
  p11-kit-modules parted passwd patch patchutils pax pciutils pcmciautils perl perl-base perl-modules phonon4qt5 pinentry-gnome3 pkg-config plainbox-provider-checkbox plainbox-provider-resource-generic policykit-1 policykit-1-gnome poppler-utils ppp pptp-linux presage printer-driver-brlaser printer-driver-c2esp
  printer-driver-foo2zjs printer-driver-foo2zjs-common printer-driver-gutenprint printer-driver-hpcups printer-driver-min12xxw printer-driver-pnm2ppa printer-driver-postscript-hp printer-driver-ptouch printer-driver-pxljr printer-driver-splix procps ps2eps psmisc pulseaudio pulseaudio-module-bluetooth
  pulseaudio-module-x11 pulseaudio-utils python-appindicator python-cairo python-commandnotfound python-compizconfig python-crypto python-cryptography python-cups python-dbus python-dbus-dev python-gconf python-glade2 python-gnomekeyring python-gobject-2 python-gtk2 python-imaging python-ldb python-numpy
  python-pam python-pil python-pycurl python-qt4 python-qt4-dbus python-renderpm python-reportlab python-reportlab-accel python-samba python-simplejson python-sip python-smbc python-talloc python-twisted-bin python-twisted-core python-twisted-web python-vte python-xapian python-zeitgeist python-zope.interface
  python3 python3-brlapi python3-cairo python3-commandnotfound python3-crypto python3-cryptography python3-cups python3-dbus python3-gdbm python3-markupsafe python3-minimal python3-pil python3-pycurl python3-renderpm python3-reportlab python3-reportlab-accel python3-smbc python3-speechd qdbus
  qml-module-ubuntu-onlineaccounts qpdf qt-at-spi qt4-dev-tools qtcore4-l10n qtdeclarative5-accounts-plugin qtdeclarative5-unity-action-plugin rarian-compat re2c readline-common remmina remmina-common remmina-plugin-rdp remmina-plugin-vnc rfkill rhythmbox rhythmbox-data rhythmbox-mozilla
  rhythmbox-plugin-cdrecorder rhythmbox-plugin-magnatune rhythmbox-plugin-zeitgeist rhythmbox-plugins rpm rpm-common rpm2cpio rsync rsyslog rtmpdump ruby2.1 ruby2.2 sa-compile samba-common samba-common-bin samba-libs sane-utils seahorse sed session-migration shared-mime-info sharutils signon-keyring-extension
  signon-plugin-oauth2 signon-plugin-password signon-ui signon-ui-service signon-ui-x11 signond smbclient spamassassin spamc speech-dispatcher speech-dispatcher-audio-plugins strace sudo syslinux-legacy sysv-rc sysvinit-utils t1utils tar tcl tcl8.6 tcpd tcpdump telepathy-gabble telepathy-haze telepathy-idle
  telepathy-indicator telepathy-logger telepathy-mission-control-5 telepathy-salut telnet thermald time tk tk8.6 tk8.6-blt2.5 toshset totem totem-common totem-plugins transmission-common transmission-gtk udisks2 unity unity-control-center unity-control-center-faces unity-control-center-signon unity-greeter
  unity-gtk-module-common unity-gtk2-module unity-gtk3-module unity-lens-applications unity-lens-files unity-lens-music unity-lens-video unity-schemas unity-scope-home unity-scope-musicstores unity-scope-video-remote unity-scopes-master-default unity-scopes-runner unity-services unity-settings-daemon
  unity-webapps-qml unity-webapps-service unrar unzip update-notifier update-notifier-common upower upstart upstart-bin upstart-dconf-bridge ureadahead usb-creator-common usb-creator-gtk usb-modeswitch usbmuxd usbutils util-linux uuid-runtime vbetool vim-common vim-tiny wget whiptail whoopsie whoopsie-preferences
  wireless-tools wodim wpasupplicant x11-apps x11-common x11-session-utils x11-utils x11-xkb-utils x11-xserver-utils xauth xbrlapi xclip xdg-user-dirs xdg-user-dirs-gtk xfonts-utils xinit xinput xorg xserver-common xserver-xephyr xserver-xorg xserver-xorg-core xserver-xorg-input-all xserver-xorg-input-mouse
  xserver-xorg-input-synaptics xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-all xserver-xorg-video-cirrus xserver-xorg-video-fbdev xserver-xorg-video-mach64 xserver-xorg-video-mga xserver-xorg-video-neomagic xserver-xorg-video-openchrome xserver-xorg-video-qxl xserver-xorg-video-r128
  xserver-xorg-video-savage xserver-xorg-video-siliconmotion xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident xserver-xorg-video-vesa xserver-xorg-video-vmware xterm xwayland xz-utils yelp zeitgeist zeitgeist-core zeitgeist-datahub zenity zenity-common zip zlib1g zsh zsh-common
1344 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 429 MB of archives.
After this operation, 267 MB of additional disk space will be used.
Do you want to continue? [Y/n] n
Abort.
```Tempting... ;)

---

### Post by QDR06VV9 on 2015-12-11
I'll be back with the results in about an hour..
She's a slow DL
Regards

---

### Post by zika on 2015-12-11
Caveat is that we do not know how often new versions of packages are compiled so that mix of pie and pde is almost inevitable... ;)
I'll keep my eye(s) open both on PPA and on You(r progress)... ;)

---

### Post by QDR06VV9 on 2015-12-11
Hehehaha! Well here she blows

```
MaxReports is reached already                              No apport report written because MaxReports is reached already
            No apport report written because MaxReports is reached already
                                                                          No apport report written because MaxReports is reached already
                                                        No apport report written because MaxReports is reached already
                                      No apport report written because MaxReports is reached already
                    No apport report written because MaxReports is reached already
  sing triggers for gconf2:
 gconf2 depends on psmisc; however:
  Package psmisc is not configured yet.
 gconf2 depends on python3:any; however:
  Package python3 is not configured yet.


dpkg: error processing package gconf2 (--configure):
 dependency problems - leaving triggers unprocessed
dpkg: dependency problems prevent processing triggers for gconf2:
 gconf2 depends on psmisc; however:
  Package psmisc is not configured yet.
 gconf2 depends on python3:any; however:
  Package python3 is not configured yet.


dpkg: error processing package gconf2 (--configure):
 dependency problems - leaving triggers unprocessed
dpkg: dependency problems prevent processing triggers for gconf2:
 gconf2 depends on psmisc; however:
  Package psmisc is not configured yet.
 gconf2 depends on python3:any; however:
  Package python3 is not configured yet.


dpkg: error processing package gconf2 (--configure):
 dependency problems - leaving triggers unprocessed
dpkg: dependency problems prevent processing triggers for gconf2:
 gconf2 depends on psmisc; however:
  Package psmisc is not configured yet.
 gconf2 depends on python3:any; however:
  Package python3 is not configured yet.


dpkg: error processing package gconf2 (--configure):
 dependency problems - leaving triggers unprocessed
dpkg: dependency problems prevent processing triggers for gconf2:
 gconf2 depends on psmisc; however:
  Package psmisc is not configured yet.
 gconf2 depends on python3:any; however:
  Package python3 is not configured yet.


dpkg: error processing package gconf2 (--configure):
 dependency problems - leaving triggers unprocessed
dpkg: dependency problems prevent processing triggers for gconf2:
 gconf2 depends on psmisc; however:
  Package psmisc is not configured yet.
 gconf2 depends on python3:any; however:
  Package python3 is not configured yet.


dpkg: error processing package gconf2 (--configure):
 dependency problems - leaving triggers unprocessed
dpkg: dependency problems prevent processing triggers for gconf2:
 gconf2 depends on psmisc; however:
  Package psmisc is not configured yet.
 gconf2 depends on python3:any; however:
  Package python3 is not configured yet.


dpkg: error processing package gconf2 (--configure):
 dependency problems - leaving triggers unprocessed
dpkg: dependency problems prevent processing triggers for gconf2:
 gconf2 depends on psmisc; however:
  Package psmisc is not configured yet.
 gconf2 depends on python3:any; however:
  Package python3 is not configured yet.


dpkg: error processing package gconf2 (--configure):
 dependency problems - leaving triggers unprocessed
dpkg: dependency problems prevent processing triggers for gconf2:
 gconf2 depends on psmisc; however:
  Package psmisc is not configured yet.
 gconf2 depends on python3:any; however:
  Package python3 is not configured yet.


dpkg: error processing package gconf2 (--configure):
 dependency problems - leaving triggers unprocessed
dpkg: dependency problems prevent processing triggers for gconf2:
 gconf2 depends on psmisc; however:
  Package psmisc is not configured yet.
 gconf2 depends on python3:any; however:
  Package python3 is not configured yet.


dpkg: error processing package gconf2 (--configure):
 dependency problems - leaving triggers unprocessed
dpkg: dependency problems prevent processing triggers for gconf2:
 gconf2 depends on psmisc; however:
  Package psmisc is not configured yet.
 gconf2 depends on python3:any; however:
  Package python3 is not configured yet.


dpkg: error processing package gconf2 (--configure):
 dependency problems - leaving triggers unprocessed
dpkg: dependency problems prevent processing triggers for gconf2:
 gconf2 depends on psmisc; however:
  Package psmisc is not configured yet.
 gconf2 depends on python3:any; however:
  Package python3 is not configured yet.


dpkg: error processing package gconf2 (--configure):
 dependency problems - leaving triggers unprocessed
dpkg: dependency problems prevent processing triggers for gconf2:
 gconf2 depends on psmisc; however:
  Package psmisc is not configured yet.
 gconf2 depends on python3:any; however:
  Package python3 is not configured yet.


dpkg: error processing package gconf2 (--configure):
 dependency problems - leaving triggers unprocessed
dpkg: dependency problems prevent processing triggers for gconf2:
 gconf2 depends on psmisc; however:
  Package psmisc is not configured yet.
 gconf2 depends on python3:any; however:
  Package python3 is not configured yet.


dpkg: error processing package gconf2 (--configure):
 dependency problems - leaving triggers unprocessed
dpkg: dependency problems prevent processing triggers for gconf2:
 gconf2 depends on psmisc; however:
  Package psmisc is not configured yet.
 gconf2 depends on python3:any; however:
  Package python3 is not configured yet.


dpkg: error processing package gconf2 (--configure):
 dependency problems - leaving triggers unprocessed
dpkg: dependency problems prevent processing triggers for gconf2:
 gconf2 depends on psmisc; however:
  Package psmisc is not configured yet.
 gconf2 depends on python3:any; however:
  Package python3 is not configured yet.


dpkg: error processing package gconf2 (--configure):
 dependency problems - leaving triggers unprocessed
dpkg: dependency problems prevent processing triggers for gconf2:
 gconf2 depends on psmisc; however:
  Package psmisc is not configured yet.
 gconf2 depends on python3:any; however:
  Package python3 is not configured yet.


dpkg: error processing package gconf2 (--configure):
 dependency problems - leaving triggers unprocessed
dpkg: dependency problems prevent processing triggers for gconf2:
 gconf2 depends on psmisc; however:
  Package psmisc is not configured yet.
 gconf2 depends on python3:any; however:
  Package python3 is not configured yet.


dpkg: error processing package gconf2 (--configure):
 dependency problems - leaving triggers unprocessed
dpkg: dependency problems prevent processing triggers for gconf2:
 gconf2 depends on psmisc; however:
  Package psmisc is not configured yet.
 gconf2 depends on python3:any; however:
  Package python3 is not configured yet.


dpkg: error processing package gconf2 (--configure):
 dependency problems - leaving triggers unprocessed
dpkg: dependency problems prevent processing triggers for gconf2:
 gconf2 depends on psmisc; however:
  Package psmisc is not configured yet.
 gconf2 depends on python3:any; however:
  Package python3 is not configured yet.


dpkg: error processing package gconf2 (--configure):
 dependency problems - leaving triggers unprocessed
dpkg: dependency problems prevent processing triggers for gconf2:
 gconf2 depends on psmisc; however:
  Package psmisc is not configured yet.
 gconf2 depends on python3:any; however:
  Package python3 is not configured yet.


dpkg: error processing package gconf2 (--configure):
 dependency problems - leaving triggers unprocessed
dpkg: dependency problems prevent processing triggers for gconf2:
 gconf2 depends on psmisc; however:
  Package psmisc is not configured yet.
 gconf2 depends on python3:any; however:
  Package python3 is not configured yet.


dpkg: error processing package gconf2 (--configure):
 dependency problems - leaving triggers unprocessed
dpkg: dependency problems prevent processing triggers for gconf2:
 gconf2 depends on psmisc; however:
  Package psmisc is not configured yet.
 gconf2 depends on python3:any; however:
  Package python3 is not configured yet.


dpkg: error processing package gconf2 (--configure):
 dependency problems - leaving triggers unprocessed
dpkg: dependency problems prevent processing triggers for gconf2:
 gconf2 depends on psmisc; however:
  Package psmisc is not configured yet.
 gconf2 depends on python3:any; however:
  Package python3 is not configured yet.


dpkg: error processing package gconf2 (--configure):
 dependency problems - leaving triggers unprocessed
dpkg: dependency problems prevent processing triggers for gconf2:
 gconf2 depends on psmisc; however:
  Package psmisc is not configured yet.
 gconf2 depends on python3:any; however:
  Package python3 is not configured yet.


dpkg: error processing package gconf2 (--configure):
 dependency problems - leaving triggers unprocessed
dpkg: dependency problems prevent processing triggers for gconf2:
 gconf2 depends on psmisc; however:
  Package psmisc is not configured yet.
 gconf2 depends on python3:any; however:
  Package python3 is not configured yet.


dpkg: error processing package gconf2 (--configure):
 dependency problems - leaving triggers unprocessed
dpkg: dependency problems prevent processing triggers for gconf2:
 gconf2 depends on psmisc; however:
  Package psmisc is not configured yet.
 gconf2 depends on python3:any; however:
  Package python3 is not configured yet.


dpkg: error processing package gconf2 (--configure):
 dependency problems - leaving triggers unprocessed
dpkg: dependency problems prevent processing triggers for gconf2:
 gconf2 depends on psmisc; however:
  Package psmisc is not configured yet.
 gconf2 depends on python3:any; however:
  Package python3 is not configured yet.


dpkg: error processing package gconf2 (--configure):
 dependency problems - leaving triggers unprocessed
dpkg: dependency problems prevent processing triggers for gconf2:
 gconf2 depends on psmisc; however:
  Package psmisc is not configured yet.
 gconf2 depends on python3:any; however:
  Package python3 is not configured yet.


dpkg: error processing package gconf2 (--configure):
 dependency problems - leaving triggers unprocessed
dpkg: dependency problems prevent processing triggers for gconf2:
 gconf2 depends on psmisc; however:
  Package psmisc is not configured yet.
 gconf2 depends on python3:any; however:
  Package python3 is not configured yet.


dpkg: error processing package gconf2 (--configure):
 dependency problems - leaving triggers unprocessed
dpkg: dependency problems prevent processing triggers for gconf2:
 gconf2 depends on psmisc; however:
  Package psmisc is not configured yet.
 gconf2 depends on python3:any; however:
  Package python3 is not configured yet.


dpkg: error processing package gconf2 (--configure):
 dependency problems - leaving triggers unprocessed
dpkg: dependency problems prevent processing triggers for gconf2:
 gconf2 depends on psmisc; however:
  Package psmisc is not configured yet.
 gconf2 depends on python3:any; however:
  Package python3 is not configured yet.


dpkg: error processing package gconf2 (--configure):
 dependency problems - leaving triggers unprocessed
dpkg: dependency problems prevent processing triggers for gconf2:
 gconf2 depends on psmisc; however:
  Package psmisc is not configured yet.
 gconf2 depends on python3:any; however:
  Package python3 is not configured yet.


dpkg: error processing package gconf2 (--configure):
 dependency problems - leaving triggers unprocessed
dpkg: dependency problems prevent processing triggers for gconf2:
 gconf2 depends on psmisc; however:
  Package psmisc is not configured yet.
 gconf2 depends on python3:any; however:
  Package python3 is not configured yet.


dpkg: error processing package gconf2 (--configure):
 dependency problems - leaving triggers unprocessed
dpkg: dependency problems prevent processing triggers for gconf2:
 gconf2 depends on psmisc; however:
  Package psmisc is not configured yet.
 gconf2 depends on python3:any; however:
  Package python3 is not configured yet.


dpkg: error processing package gconf2 (--configure):
 dependency problems - leaving triggers unprocessed
dpkg: dependency problems prevent processing triggers for gconf2:
 gconf2 depends on psmisc; however:
  Package psmisc is not configured yet.
 gconf2 depends on python3:any; however:
  Package python3 is not configured yet.


dpkg: error processing package gconf2 (--configure):
 dependency problems - leaving triggers unprocessed
dpkg: dependency problems prevent processing triggers for gconf2:
 gconf2 depends on psmisc; however:
  Package psmisc is not configured yet.
 gconf2 depends on python3:any; however:
  Package python3 is not configured yet.


dpkg: error processing package gconf2 (--configure):
 dependency problems - leaving triggers unprocessed
dpkg: dependency problems prevent processing triggers for gconf2:
 gconf2 depends on psmisc; however:
  Package psmisc is not configured yet.
 gconf2 depends on python3:any; however:
  Package python3 is not configured yet.


dpkg: error processing package gconf2 (--configure):
 dependency problems - leaving triggers unprocessed
dpkg: too many errors, stopping
Processing triggers for libc-bin (2.21-0ubuntu5) ...
Errors were encountered while processing:
 gconf2
 gconf2
 gconf2
 gconf2
 gconf2
 gconf2
 gconf2
 gconf2
 gconf2
 gconf2
 gconf2
 gconf2
 gconf2
 gconf2
 gconf2
 gconf2
 gconf2
 gconf2
 gconf2
 gconf2
 gconf2
 gconf2
 gconf2
 gconf2
 gconf2
 gconf2
 gconf2
 gconf2
 gconf2
 gconf2
 gconf2
 gconf2
 gconf2
 gconf2
 gconf2
 gconf2
 gconf2
 gconf2
 gconf2
 gconf2
 gconf2
 gconf2
 gconf2
 gconf2
 gconf2
 gconf2
 gconf2
 gconf2
 gconf2
 gconf2
 gconf2
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)



```
Ok time for PPA purge
Kind regards

---

### Post by QDR06VV9 on 2015-12-11
[COLOR=#ff0000]**Warning this edit below did not work!!!**[/COLOR]
Will try this solution to edit these files:


> /usr/lib/python3.3/sre_constants.py
/usr/lib/python3.3/sre_parse.py
/usr/lib/python3.3/sre_compile.py
In sre_constants.py I replace:


from _sre import MAXREPEAT
with:


```
MAXREPEAT = 65535
#from _sre import MAXREPEAT
In sre_parse.py and sre_compile.py 
```



I comment out:from _sre import MAXREPEAT

EDIT: The edits above did not work for me so a purge and clean up, and back to normal..
Oh well had some excitement for a brief moment..:o
@zika I'm going to watch this thread so if you take the plunge later will you keep this thread updated??

---

### Post by zika on 2015-12-11
I do hope You've used```
-s
```or```
--dry-run
```just to simulate all this... ;)

---

### Post by QDR06VV9 on 2015-12-11
Naa! I was in it to Win, Lose, or Draw..
But I knew what I was doing and all is good(Normal):D
I can not grow with out putting myself in harms way:D;)
Kind Regards
Besides I never could resist a "Double Dog Dare"

---

### Post by zika on 2015-12-11
[img]http://38.media.tumblr.com/tumblr_m2yo8haie91qkvm3xo1_400.gif[/img]

---

### Post by flocculant on 2015-12-11
ha ha ha

---

### Post by zika on 2015-12-11
> **flocculant said:**
> ha ha ha
[IMG]http://i.imgur.com/iuQ8vhIl.png[/IMG]
Are You laughing at me?
No, You're laughing with me...
[img]http://assets.nydailynews.com/polopoly_fs/1.1547232!/img/httpImage/image.jpg_gen/derivatives/article_970/175844725.jpg[/img]

---

### Post by QDR06VV9 on 2015-12-11
See this is why this forum is so wonderful...:D

---

