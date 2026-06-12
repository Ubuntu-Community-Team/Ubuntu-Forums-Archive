---
title: "Adding 'ubuntu-gnome-desktop' to tasksel"
date: 2014-04-02
forum: Ubuntu Development Version
---

### Post by kansasnoob on 2014-04-02
I need to steal some space to parse info for adding 'ubuntu-gnome-desktop' to tasksel:

[https://bugs.launchpad.net/ubuntu/+source/tasksel/+bug/1299953](https://bugs.launchpad.net/ubuntu/+source/tasksel/+bug/1299953)

Adding just 'ubuntu-gnome-desktop' to a CLI install in a chroot adds some unwanted packages (the important part is highlighted):

```
root@lance-desktop:/# apt-get install ubuntu-gnome-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  account-plugin-aim account-plugin-facebook account-plugin-google account-plugin-jabber account-plugin-salut account-plugin-windows-live
  account-plugin-yahoo acl acpi-support acpid aisleriot alsa-base alsa-utils anacron apg app-install-data app-install-data-partner apport apport-gtk
  apport-symptoms aptdaemon aptdaemon-data apturl apturl-common argyll aspell aspell-en at-spi2-core avahi-autoipd avahi-daemon avahi-utils baobab
  bc binutils bluez bluez-alsa bluez-cups bluez-gstreamer brasero brasero-cdrkit brasero-common brltty cheese cheese-common colord cpp cpp-4.8
  cracklib-runtime cups cups-browsed cups-bsd cups-client cups-common cups-core-drivers cups-daemon cups-filters cups-filters-core-drivers
  cups-pk-helper cups-ppdc cups-server-common dbus-x11 dc dconf-cli dconf-editor dconf-gsettings-backend dconf-service deja-dup
  deja-dup-backend-cloudfiles deja-dup-backend-gvfs deja-dup-backend-s3 deja-dup-backend-ubuntuone desktop-file-utils dialog dictionaries-common
  diffstat dnsmasq-base duplicity dvd+rw-tools empathy empathy-common enchant eog espeak-data evince evince-common evolution evolution-common
  evolution-data-server evolution-data-server-common evolution-data-server-online-accounts evolution-indicator evolution-plugins file-roller firefox
  folks-common fontconfig fontconfig-config fonts-cantarell fonts-dejavu-core fonts-droid fonts-freefont-ttf fonts-kacst fonts-kacst-one
  fonts-khmeros-core fonts-lao fonts-liberation fonts-lklug-sinhala fonts-nanum fonts-opensymbol fonts-sil-abyssinica fonts-sil-padauk
  fonts-takao-pgothic fonts-thai-tlwg fonts-tibetan-machine fonts-tlwg-garuda fonts-tlwg-kinnari fonts-tlwg-loma fonts-tlwg-mono fonts-tlwg-norasi
  fonts-tlwg-purisa fonts-tlwg-sawasdee fonts-tlwg-typewriter fonts-tlwg-typist fonts-tlwg-typo fonts-tlwg-umpush fonts-tlwg-waree
  foomatic-db-compressed-ppds gcc gcc-4.8 gconf-service gconf-service-backend gconf2 gconf2-common gcr gdb gdisk gdm gedit gedit-common genisoimage
  geoclue gettext ghostscript ghostscript-x gir1.2-accountsservice-1.0 gir1.2-atk-1.0 gir1.2-atspi-2.0 gir1.2-caribou-1.0 gir1.2-clutter-1.0
  gir1.2-clutter-gst-2.0 gir1.2-cogl-1.0 gir1.2-coglpango-1.0 gir1.2-dbusmenu-glib-0.4 gir1.2-dee-1.0 gir1.2-evince-3.0 gir1.2-freedesktop
  gir1.2-gck-1 gir1.2-gcr-3 gir1.2-gdata-0.0 gir1.2-gdesktopenums-3.0 gir1.2-gdkpixbuf-2.0 gir1.2-gdm-1.0 gir1.2-gkbd-3.0 gir1.2-gmenu-3.0
  gir1.2-gnomebluetooth-1.0 gir1.2-gnomedesktop-3.0 gir1.2-gnomekeyring-1.0 gir1.2-goa-1.0 gir1.2-gst-plugins-base-1.0 gir1.2-gstreamer-1.0
  gir1.2-gtk-3.0 gir1.2-gtkclutter-1.0 gir1.2-gtksource-3.0 gir1.2-gtop-2.0 gir1.2-gudev-1.0 gir1.2-ibus-1.0 gir1.2-javascriptcoregtk-3.0
  gir1.2-json-1.0 gir1.2-mutter-3.0 gir1.2-networkmanager-1.0 gir1.2-nmgtk-1.0 gir1.2-notify-0.7 gir1.2-packagekitglib-1.0 gir1.2-pango-1.0
  gir1.2-peas-1.0 gir1.2-polkit-1.0 gir1.2-rb-3.0 gir1.2-rest-0.7 gir1.2-secret-1 gir1.2-soup-2.4 gir1.2-syncmenu-0.1 gir1.2-telepathyglib-0.12
  gir1.2-telepathylogger-0.2 gir1.2-totem-1.0 gir1.2-totem-plparser-1.0 gir1.2-tracker-0.16 gir1.2-udisks-2.0 gir1.2-unity-5.0 gir1.2-upowerglib-1.0
  gir1.2-vte-2.90 gir1.2-webkit-3.0 gir1.2-wnck-3.0 gir1.2-xkl-1.0 gir1.2-zpj-0.0 gjs gkbd-capplet glib-networking glib-networking-common
  glib-networking-services gnome-accessibility-themes gnome-backgrounds gnome-bluetooth gnome-calculator gnome-color-manager gnome-contacts
  gnome-control-center gnome-control-center-data gnome-control-center-shared-data gnome-desktop3-data gnome-disk-utility gnome-documents
  gnome-font-viewer gnome-icon-theme gnome-icon-theme-extras gnome-icon-theme-full gnome-icon-theme-symbolic gnome-keyring gnome-mahjongg
  gnome-menus gnome-mines gnome-online-accounts gnome-online-miners gnome-orca gnome-screenshot gnome-session gnome-session-bin
  gnome-session-canberra gnome-session-common gnome-settings-daemon gnome-settings-daemon-schemas gnome-shell gnome-shell-common
  gnome-shell-extensions gnome-sudoku gnome-sushi gnome-system-log gnome-system-monitor gnome-terminal gnome-terminal-data gnome-themes-standard
  gnome-themes-standard-data gnome-tweak-tool gnome-user-guide gnome-user-share gnome-video-effects growisofs gsettings-desktop-schemas
  gsettings-ubuntu-schemas gsfonts gstreamer0.10-alsa gstreamer0.10-nice gstreamer0.10-plugins-base gstreamer0.10-plugins-good
  gstreamer0.10-pulseaudio gstreamer0.10-x gstreamer1.0-alsa gstreamer1.0-clutter gstreamer1.0-nice gstreamer1.0-plugins-base
  gstreamer1.0-plugins-good gstreamer1.0-pulseaudio gstreamer1.0-x gtk2-engines-pixbuf gucharmap guile-2.0-libs gvfs gvfs-backends gvfs-backends-goa
  gvfs-bin gvfs-common gvfs-daemons gvfs-fuse gvfs-libs hardening-includes hicolor-icon-theme hplip hplip-data humanity-icon-theme hunspell-en-us
  hwdata ibus ibus-gtk ibus-gtk3 ibus-pinyin ibus-table im-config indicator-application indicator-sync inputattach intel-gpu-tools intltool-debian
  iproute iputils-arping itstool kerneloops-daemon libaa1 libaccount-plugin-1.0-0 libaccount-plugin-generic-oauth libaccount-plugin-google
  libaccounts-glib0 libaccounts-qt5-1 libappindicator3-1 libapt-pkg-perl libarchive-zip-perl libarchive13 libart-2.0-2 libasan0 libasound2
  libasound2-data libasound2-plugins libaspell15 libasprintf-dev libassuan0 libasyncns0 libatasmart4 libatk-adaptor libatk-bridge2.0-0 libatk1.0-0
  libatk1.0-data libatkmm-1.6-1 libatomic1 libatspi2.0-0 libauthen-sasl-perl libautodie-perl libavahi-client3 libavahi-common-data libavahi-common3
  libavahi-core7 libavahi-glib1 libavahi-gobject0 libavc1394-0 libbluetooth3 libboost-date-time1.54.0 libboost-system1.54.0 libbrasero-media3-1
  libbrlapi0.6 libburn4 libc-dev-bin libc6-dbg libc6-dev libcaca0 libcairo-gobject2 libcairo2 libcairomm-1.0-1 libcamel-1.2-45
  libcanberra-gtk-module libcanberra-gtk0 libcanberra-gtk3-0 libcanberra-gtk3-module libcanberra-pulse libcanberra0 libcaribou-common libcaribou0
  libcdio-cdda1 libcdio-paranoia1 libcdio13 libcdparanoia0 libcdr-0.0-0 libcgmanager0 libcheese-gtk23 libcheese7 libclone-perl libcloog-isl4
  libclucene-contribs1 libclucene-core1 libclutter-1.0-0 libclutter-1.0-common libclutter-gst-2.0-0 libclutter-gtk-1.0-0 libcmis-0.4-4
  libcogl-common libcogl-pango15 libcogl15 libcolamd2.8.0 libcolord-gtk1 libcolord1 libcolorhug1 libcrack2 libcroco3 libcrypt-passwdmd5-perl
  libcups2 libcupscgi1 libcupsfilters1 libcupsimage2 libcupsmime1 libcupsppdc1 libcurl3 libdaemon0 libdatrie1 libdbusmenu-glib4 libdbusmenu-gtk3-4
  libdbusmenu-gtk4 libdconf1 libdee-1.0-4 libdigest-hmac-perl libdjvulibre-text libdjvulibre21 libdmapsharing-3.0-2 libdotconf0 libdpkg-perl
  libdrm-intel1 libdrm-nouveau2 libdrm-radeon1 libdv4 libebackend-1.2-7 libebook-1.2-14 libebook-contacts-1.2-0 libecal-1.2-16 libedata-book-1.2-20
  libedata-cal-1.2-23 libedataserver-1.2-18 libegl1-mesa libegl1-mesa-drivers libelfg0 libemail-valid-perl libenca0 libenchant1c2a
  libencode-locale-perl liberror-perl libespeak1 libevdocument3-4 libevent-2.0-5 libevolution libevview3-3 libexempi3 libexif12 libexiv2-12
  libexttextcat-2.0-0 libexttextcat-data libfarstream-0.1-0 libfarstream-0.2-2 libfftw3-single3 libfile-basedir-perl libfile-copy-recursive-perl
  libfile-desktopentry-perl libfile-fcntllock-perl libfile-listing-perl libfile-mimeinfo-perl libflac8 libfolks-eds25 libfolks-telepathy25
  libfolks25 libfont-afm-perl libfontconfig1 libfontembed1 libfontenc1 libframe6 libfs6 libgail-3-0 libgail-common libgail18 libgbm1 libgc1c2
  libgcc-4.8-dev libgconf-2-4 libgcr-ui-3-1 libgd3 libgdata-common libgdata13 libgdk-pixbuf2.0-0 libgdk-pixbuf2.0-common libgdm1 libgee-0.8-2
  libgeis1 libgeoclue0 libgettextpo-dev libgettextpo0 libgexiv2-2 libgif4 libgjs0e libgl1-mesa-dri libgl1-mesa-glx libglamor0 libglapi-mesa
  libgles2-mesa libglib2.0-bin libglibmm-2.4-1c2a libglu1-mesa libgmime-2.6-0 libgmp10 libgnome-bluetooth11 libgnome-control-center1
  libgnome-desktop-3-7 libgnome-keyring-common libgnome-keyring0 libgnome-menu-3-0 libgnomekbd-common libgnomekbd8 libgoa-1.0-0b libgoa-1.0-common
  libgoa-backend-1.0-1 libgomp1 libgpgme11 libgphoto2-6 libgphoto2-l10n libgphoto2-port10 libgpm2 libgpod-common libgpod4 libgrail6 libgraphite2-3
  libgrilo-0.2-1 libgrip0 libgs9 libgs9-common libgsf-1-114 libgsf-1-common libgssdp-1.0-3 libgstreamer-plugins-base0.10-0
  libgstreamer-plugins-base1.0-0 libgstreamer-plugins-good1.0-0 libgstreamer0.10-0 libgstreamer1.0-0 libgtk-3-0 libgtk-3-bin libgtk-3-common
  libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libgtkhtml-4.0-0 libgtkhtml-4.0-common libgtkhtml-editor-4.0-0 libgtkmm-3.0-1 libgtksourceview-3.0-1
  libgtksourceview-3.0-common libgtop2-7 libgtop2-common libgucharmap-2-90-7 libgudev-1.0-0 libgupnp-1.0-4 libgupnp-igd-1.0-4 libgusb2
  libgutenprint2 libgweather-3-6 libgweather-common libgxps2 libharfbuzz-icu0 libharfbuzz0b libhdb9-heimdal libhpmud0 libhtml-form-perl
  libhtml-format-perl libhtml-parser-perl libhtml-tagset-perl libhtml-tree-perl libhttp-cookies-perl libhttp-daemon-perl libhttp-date-perl
  libhttp-message-perl libhttp-negotiate-perl libhunspell-1.3-0 libhyphen0 libibus-1.0-5 libical1 libicc2 libice6 libicu52 libido3-0.1-0
  libiec61883-0 libieee1284-3 libijs-0.35 libimdi0 libimobiledevice4 libindicator3-7 libio-html-perl libio-pty-perl libio-socket-inet6-perl
  libio-socket-ssl-perl libipc-run-perl libipc-system-simple-perl libiptcdata0 libisl10 libisofs6 libitm1 libiw30 libjack-jackd2-0 libjasper1
  libjavascriptcoregtk-3.0-0 libjbig0 libjbig2dec0 libjpeg-turbo8 libjpeg8 libjson-glib-1.0-0 libjson-glib-1.0-common libjte1 libkpathsea6
  liblangtag-common liblangtag1 liblcms2-2 libldb1 liblircclient0 liblist-moreutils-perl libllvm3.4 liblouis-data liblouis2 libltdl7 liblua5.2-0
  liblwp-mediatypes-perl liblwp-protocol-https-perl liblzo2-2 libmail-spf-perl libmailtools-perl libmbim-glib0 libmeanwhile1 libmessaging-menu0
  libmhash2 libminiupnpc8 libmission-control-plugins0 libmm-glib0 libmnl0 libmozjs-24-0 libmpc3 libmpfr4 libmspub-0.0-0 libmtdev1 libmtp-common
  libmtp-runtime libmtp9 libmusicbrainz5-0 libmutter0c libmythes-1.2-0 libnatpmp1 libnautilus-extension1a libneon27-gnutls libnet-dns-perl
  libnet-domain-tld-perl libnet-http-perl libnet-ip-perl libnet-libidn-perl libnet-smtp-ssl-perl libnet-ssleay-perl libnetaddr-ip-perl
  libnetfilter-conntrack3 libnettle4 libnice10 libnl-route-3-200 libnm-glib-vpn1 libnm-glib4 libnm-gtk-common libnm-gtk0 libnm-util2 libnotify-bin
  libnotify4 libnspr4 libnss-mdns libnss-myhostname libnss3 libnss3-nssdb libntdb1 liboauth0 libogg0 libopencc1 libopenobex1 libopenvg1-mesa
  liborc-0.4-0 liborcus-0.6-0 libp11-kit-gnome-keyring libpackagekit-glib2-16 libpam-gnome-keyring libpango-1.0-0 libpango1.0-0 libpangocairo-1.0-0
  libpangoft2-1.0-0 libpangomm-1.4-1 libpangox-1.0-0 libpangoxft-1.0-0 libpaper-utils libpaper1 libpciaccess0 libpcsclite1 libpeas-1.0-0
  libpeas-common libperl5.18 libperlio-gzip-perl libpixman-1-0 libplist1 libpolkit-agent-1-0 libpolkit-backend-1-0 libpoppler-glib8 libpoppler44
  libportaudio2 libproxy1 libproxy1-plugin-gsettings libproxy1-plugin-networkmanager libpst4 libpulse-mainloop-glib0 libpulse0 libpulsedsp
  libpurple-bin libpurple0 libpwquality-common libpwquality1 libpython2.7 libpython3.4 libpyzy-1.0-0 libqmi-glib0 libqpdf13 libqt5core5a libqt5dbus5
  libqt5gui5 libqt5network5 libqt5opengl5 libqt5positioning5 libqt5printsupport5 libqt5qml5 libqt5quick5 libqt5sensors5 libqt5sql5 libqt5sql5-sqlite
  libqt5test5 libqt5webkit5 libqt5widgets5 libqt5xml5 libquadmath0 libraptor2-0 librasqal3 libraw1394-11 libraw9 librdf0 libreadline5
  libreoffice-avmedia-backend-gstreamer libreoffice-base-core libreoffice-calc libreoffice-common libreoffice-core libreoffice-draw
  libreoffice-gnome libreoffice-gtk libreoffice-impress libreoffice-math libreoffice-ogltrans libreoffice-pdfimport
  libreoffice-presentation-minimizer libreoffice-style-galaxy libreoffice-style-human libreoffice-style-tango libreoffice-writer librest-0.7-0
  librhythmbox-core8 librsvg2-2 librsvg2-common librsync1 libsamplerate0 libsane libsane-common libsane-hpaio libsbc1 libsecret-1-0 libsecret-common
  libsensors4 libsgutils2-2 libshout3 libsignon-extension1 libsignon-glib1 libsignon-plugins-common1 libsignon-qt5-1 libsm6 libsmbclient libsndfile1
  libsnmp-base libsnmp30 libsocket6-perl libsonic0 libsoup-gnome2.4-1 libsoup2.4-1 libspectre1 libspeechd2 libspeex1 libspeexdsp1
  libstartup-notification0 libsub-identify-perl libsync-menu1 libsys-hostname-long-perl libsystemd-journal0 libt1-5 libtag1-vanilla libtag1c2a
  libtalloc2 libtcl8.6 libtdb1 libtelepathy-farstream3 libtelepathy-glib0 libtelepathy-logger3 libtevent0 libtext-levenshtein-perl libthai-data
  libthai0 libtheora0 libtiff5 libtimezonemap1 libtk8.6 libtotem-plparser18 libtotem0 libtracker-extract-0.16-0 libtracker-miner-0.16-0
  libtracker-sparql-0.16-0 libtxc-dxtn-s2tc0 libudisks2-0 libunistring0 libunity-control-center1 libunity-protocol-private0
  libunity-scopes-json-def-desktop libunity9 libupower-glib1 liburi-perl libusbmuxd2 libutempter0 libv4l-0 libv4lconvert0 libvisio-0.0-0
  libvisual-0.4-0 libvisual-0.4-plugins libvorbis0a libvorbisenc2 libvorbisfile3 libvpx1 libvte-2.90-9 libvte-2.90-common libwacom-common libwacom2
  libwavpack1 libwayland-client0 libwayland-cursor0 libwayland-egl1-mesa libwayland-server0 libwbclient0 libwebkitgtk-3.0-0 libwebkitgtk-3.0-common
  libwebp5 libwebpmux1 libwhoopsie0 libwmf0.2-7 libwmf0.2-7-gtk libwnck-3-0 libwnck-3-common libwpd-0.9-9 libwpg-0.2-2 libwps-0.2-2 libwrap0
  libwww-perl libwww-robotrules-perl libx11-xcb1 libxatracker2 libxaw7 libxcb-dri2-0 libxcb-dri3-0 libxcb-glx0 libxcb-icccm4 libxcb-image0
  libxcb-keysyms1 libxcb-present0 libxcb-randr0 libxcb-render-util0 libxcb-render0 libxcb-shape0 libxcb-shm0 libxcb-sync1 libxcb-util0
  libxcb-xf86dri0 libxcb-xfixes0 libxcb-xkb1 libxcb-xv0 libxcomposite1 libxcursor1 libxdamage1 libxfixes3 libxfont1 libxft2 libxi6 libxinerama1
  libxkbcommon0 libxkbfile1 libxklavier16 libxml2-utils libxmu6 libxp6 libxpm4 libxrandr2 libxrender1 libxres1 libxshmfence1 libxslt1.1 libxss1
  libxt6 libxtst6 libxv1 libxvmc1 libxxf86dga1 libxxf86vm1 libyajl2 libyelp0 libytnef0 libzapojit-0.0-0 libzeitgeist-1.0-1 libzeitgeist-2.0-0
  libzephyr4 lintian linux-libc-dev linux-sound-base lp-solve make manpages-dev mcp-account-manager-goa mcp-account-manager-uoa media-player-info
  memtest86+ mobile-broadband-provider-info modemmanager mousetweaks mscompress mtools mutter mutter-common nautilus nautilus-data nautilus-sendto
  nautilus-sendto-empathy nautilus-share network-manager network-manager-gnome network-manager-pptp network-manager-pptp-gnome notification-daemon
  obex-data-server obexd-client oneconf oneconf-common openprinting-ppds p11-kit p11-kit-modules patch patchutils pcmciautils plymouth-label
  plymouth-theme-ubuntu-gnome-logo plymouth-theme-ubuntu-gnome-text policykit-1 policykit-1-gnome policykit-desktop-privileges poppler-data
  poppler-utils pptp-linux printer-driver-c2esp printer-driver-foo2zjs printer-driver-foo2zjs-common printer-driver-gutenprint printer-driver-hpcups
  printer-driver-min12xxw printer-driver-pnm2ppa printer-driver-postscript-hp printer-driver-ptouch printer-driver-pxljr printer-driver-sag-gdi
  printer-driver-splix pulseaudio pulseaudio-module-bluetooth pulseaudio-module-x11 pulseaudio-utils python-aptdaemon python-aptdaemon.gtk3widgets
  python-boto python-cairo python-cloudfiles python-commandnotfound python-configglue python-crypto python-cups python-cupshelpers python-dbus
  python-dbus-dev python-debtagshw python-defer python-dirspec python-gdbm python-gi python-gi-cairo python-gnomekeyring python-gobject
  python-gobject-2 python-gtk2 python-httplib2 python-ibus python-imaging python-ldb python-libxml2 python-lockfile python-lxml python-notify
  python-ntdb python-oauthlib python-oneconf python-openssl python-pam python-pexpect python-pil python-piston-mini-client python-pkg-resources
  python-protobuf python-pycurl python-pyinotify python-renderpm python-reportlab python-reportlab-accel python-requests python-samba python-serial
  python-smbc python-talloc python-tdb python-twisted-bin python-twisted-core python-twisted-names python-twisted-web python-ubuntu-sso-client
  python-ubuntuone-client python-ubuntuone-control-panel python-ubuntuone-storageprotocol python-urllib3 python-xdg python-zeitgeist
  python-zope.interface python3-apport python3-aptdaemon python3-aptdaemon.gtk3widgets python3-aptdaemon.pkcompat python3-brlapi python3-cairo
  python3-chardet python3-crypto python3-debian python3-defer python3-dirspec python3-gi-cairo python3-httplib2 python3-louis python3-mako
  python3-markupsafe python3-oauthlib python3-oneconf python3-piston-mini-client python3-pkg-resources python3-problem-report python3-pyatspi
  python3-pycurl python3-six python3-software-properties python3-speechd python3-uno python3-xdg python3-xkit qpdf re2c rfkill rhythmbox
  rhythmbox-data rhythmbox-mozilla rhythmbox-plugin-cdrecorder rhythmbox-plugin-magnatune rhythmbox-plugin-zeitgeist rhythmbox-plugins
  rhythmbox-ubuntuone rtkit sa-compile samba-common samba-common-bin samba-libs sane-utils seahorse session-migration sessioninstaller shotwell
  shotwell-common signon-keyring-extension signon-plugin-oauth2 signon-plugin-password signon-ui signond simple-scan smbclient software-center
  software-center-aptdaemon-plugins software-properties-common software-properties-gtk sound-theme-freedesktop spamassassin spamc speech-dispatcher
  speech-dispatcher-audio-plugins ssh-askpass-gnome ssl-cert syslinux syslinux-common syslinux-legacy system-config-printer-common
  system-config-printer-gnome system-config-printer-udev t1utils tcl tcl8.6 tcpd telepathy-gabble telepathy-haze telepathy-idle telepathy-logger
  telepathy-mission-control-5 telepathy-salut tk tk8.6 toshset totem totem-common totem-plugins tracker tracker-extract tracker-miner-fs
  tracker-utils transmission-common transmission-gtk ttf-indic-fonts-core ttf-punjabi-fonts ttf-ubuntu-font-family ubuntu-drivers-common
  ubuntu-extras-keyring ubuntu-gnome-default-settings ubuntu-release-upgrader-gtk ubuntu-sso-client ubuntu-system-service ubuntuone-client
  ubuntuone-client-data ubuntuone-control-panel udisks2 unattended-upgrades unity-asset-pool unity-control-center unity-control-center-signon
  unity-settings-daemon uno-libs3 unoconv unzip update-inetd update-manager update-notifier update-notifier-common upower ure usb-creator-common
  usb-creator-gtk usb-modeswitch usb-modeswitch-data usbmuxd vino wamerican whoopsie wireless-tools wodim wpasupplicant x11-apps x11-common
  x11-session-utils x11-utils x11-xfs-utils x11-xkb-utils x11-xserver-utils xbitmaps xdg-user-dirs xdg-user-dirs-gtk xdg-utils xdiagnose xfonts-base
  xfonts-encodings xfonts-mathml xfonts-scalable xfonts-utils xinit xinput xorg xorg-docs-core xserver-common xserver-xephyr xserver-xorg
  xserver-xorg-core xserver-xorg-input-all xserver-xorg-input-evdev xserver-xorg-input-mouse xserver-xorg-input-synaptics xserver-xorg-input-vmmouse
  xserver-xorg-input-wacom xserver-xorg-video-all xserver-xorg-video-ati xserver-xorg-video-cirrus xserver-xorg-video-fbdev
  xserver-xorg-video-glamoregl xserver-xorg-video-intel xserver-xorg-video-mach64 xserver-xorg-video-mga xserver-xorg-video-modesetting
  xserver-xorg-video-neomagic xserver-xorg-video-nouveau xserver-xorg-video-openchrome xserver-xorg-video-qxl xserver-xorg-video-r128
  xserver-xorg-video-radeon xserver-xorg-video-s3 xserver-xorg-video-savage xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident xserver-xorg-video-vesa xserver-xorg-video-vmware xsltproc xterm
  xul-ext-ubufox yelp yelp-tools yelp-xsl zeitgeist zeitgeist-core zeitgeist-datahub zenity zenity-common zip zsync
Suggested packages:
  gnome-cards-data apmd alsa-oss oss-compat default-mta mail-transport-agent libgtk2-perl gir1.2-colordgtk-1.0 aspell-doc spellutils binutils-doc
  bluez-hcidump vcdimager libdvdcss2 dvdauthor readom brltty-speechd brltty-x11 console-braille gnome-video-effects-frei0r gnome-video-effects-extra
  cpp-doc gcc-4.8-locales cups-pdf xpp wordlist emacsen-common jed-extra python-paramiko ncftp lftp python-gdata tahoe-lafs python-swiftclient
  cdrskin unrar evolution-ews evolution-plugins-experimental evolution-data-server-dbg arj lha lzip lzop ncompress p7zip-full rpm2cpio rzip
  sharutils unace unalz unar zoo ttf-lyx libgraphite3 pango-graphite hplip-cups printer-driver-all gcc-multilib autoconf automake1.9 libtool flex
  bison gcc-doc gcc-4.8-multilib gcc-4.8-doc libgcc1-dbg libgomp1-dbg libitm1-dbg libatomic1-dbg libasan0-dbg libtsan0-dbg libbacktrace1-dbg
  libquadmath0-dbg binutils-gold gconf-defaults-service gdb-doc gdbserver gedit-plugins cdrkit-doc gettext-doc hpijs gnome-screensaver xscreensaver
  desktop-base metacity x-window-manager gstreamer1.0-libav apache2.2-bin libapache2-mod-dnssd hplip-gui hplip-doc system-config-printer hunspell
  openoffice.org-hunspell openoffice.org-core ibus-clutter ibus-doc ibus-qt4 lrzip libgssapi-perl gstreamer1.0-plugins-ugly cdrdao
  gstreamer1.0-fluendo-mp3 gstreamer1.0-plugins-bad glibc-doc debian-keyring libdv-bin libenchant-voikko exiv2 libfftw3-bin libfftw3-dev libgd-tools
  libglide3 gpgsm gphoto2 gtkam gpm grilo-plugins-0.2 gstreamer-codec-install gnome-codec-install gstreamer0.10-tools gstreamer1.0-tools
  gutenprint-locales libdata-dump-perl jackd2 libjasper-runtime liblcms2-utils lirc libcrypt-ssleay-perl minissdpd natpmp-utils ttf-baekmuk
  ttf-arphic-gbsn00lp ttf-arphic-bsmi00lp ttf-arphic-gkai00mp ttf-arphic-bkai00mp pcscd raptor2-utils rasqal-utils libraw1394-doc
  librdf-storage-postgresql librdf-storage-mysql librdf-storage-sqlite librdf-storage-virtuoso redland-utils libreoffice-base libopencl1
  libreoffice-style-crystal libreoffice-style-hicontrast libreoffice-style-oxygen libreoffice-style-sifr libreoffice-evolution crystalcursors
  kde-icons-crystal tango-icon-theme libreoffice-gcj libreoffice-java-common default-jre gcj-jre openjdk-7-jre openjdk-6-jre sun-java5-jre
  sun-java6-jre java5-runtime jre librsvg2-bin hpoj libsane-extras lm-sensors sg3-utils snmp-mibs-downloader libspectre1-dbg speex unity-common
  libauthen-ntlm-perl binutils-multiarch dpkg-dev libtext-template-perl libyaml-perl make-doc account-plugin-gadugadu account-plugin-groupwise
  account-plugin-icq account-plugin-irc account-plugin-mxit account-plugin-myspace account-plugin-sametime account-plugin-sip account-plugin-yahoojp
  account-plugin-zephyr hwtools memtester kernel-patch-badram memtest86 floppyd pidgin gajim samba network-manager-openconnect-gnome
  network-manager-openvpn-gnome network-manager-vpnc-gnome hpijs-ppds diffutils-doc fonts-japanese-mincho fonts-ipafont-mincho fonts-japanese-gothic
  fonts-ipafont-gothic fonts-arphic-ukai fonts-arphic-uming fonts-unfonts-core psutils hannah-foo2zjs tix gutenprint-doc magicfilter apsfilter
  pavumeter paman pavucontrol paprefs pulseaudio-module-raop pulseaudio-esound-compat python-crypto-dbg python-crypto-doc python-dbus-doc
  python-dbus-dbg python-gdbm-dbg python-gobject-2-dbg python-gtk2-doc python-lxml-dbg python-openssl-doc python-openssl-dbg python-pam-dbg
  python-pexpect-doc python-pil-doc python-pil-dbg python-distribute python-distribute-doc libcurl4-gnutls-dev python-pycurl-dbg
  python-pyinotify-doc python-renderpm-dbg pdf-viewer python-egenix-mxtexttools python-reportlab-doc python-wxgtk2.8 python-wxgtk
  python-twisted-bin-dbg python-tk python-glade2 python-qt3 python3-launchpadlib python3-crypto-dbg python3-beaker python-mako-doc
  python3-setuptools python3-pycurl-dbg heimdal-clients unpaper account-plugin-flickr cifs-utils razor libdbi-perl pyzor libmail-dkim-perl
  libttspico-utils speech-dispatcher-doc-cs speech-dispatcher-festival speech-dispatcher-flite openssl-blacklist tcl-tclreadline totem-mozilla
  gromit tracker-gui ubuntu-sso-client-gui ubuntuone-client-proxy ubuntuone-control-panel-gui xfsprogs reiserfsprogs exfat-utils btrfs-tools mdadm
  cryptsetup-bin bsd-mailx comgt wvdial vinagre wpagui libengine-pkcs11-openssl mesa-utils nickle cairo-5c xfs xserver fonts-lyx fonts-stix
  xorg-docs xfonts-100dpi xfonts-75dpi gpointing-device-settings touchfreeze firmware-linux xfonts-cyrillic
Recommended packages:
  libc-dbg ubuntu-control-center-signon
[B]The following NEW packages will be installed:
  account-plugin-aim account-plugin-facebook account-plugin-google account-plugin-jabber account-plugin-salut account-plugin-windows-live
  account-plugin-yahoo acl acpi-support acpid aisleriot alsa-base alsa-utils anacron apg app-install-data app-install-data-partner apport apport-gtk
  apport-symptoms aptdaemon aptdaemon-data apturl apturl-common argyll aspell aspell-en at-spi2-core avahi-autoipd avahi-daemon avahi-utils baobab
  bc binutils bluez bluez-alsa bluez-cups bluez-gstreamer brasero brasero-cdrkit brasero-common brltty cheese cheese-common colord cpp cpp-4.8
  cracklib-runtime cups cups-browsed cups-bsd cups-client cups-common cups-core-drivers cups-daemon cups-filters cups-filters-core-drivers
  cups-pk-helper cups-ppdc cups-server-common dbus-x11 dc dconf-cli dconf-editor dconf-gsettings-backend dconf-service deja-dup
  deja-dup-backend-cloudfiles deja-dup-backend-gvfs deja-dup-backend-s3 deja-dup-backend-ubuntuone desktop-file-utils dialog dictionaries-common
  diffstat dnsmasq-base duplicity dvd+rw-tools empathy empathy-common enchant eog espeak-data evince evince-common evolution evolution-common
  evolution-data-server evolution-data-server-common evolution-data-server-online-accounts evolution-indicator evolution-plugins file-roller firefox
  folks-common fontconfig fontconfig-config fonts-cantarell fonts-dejavu-core fonts-droid fonts-freefont-ttf fonts-kacst fonts-kacst-one
  fonts-khmeros-core fonts-lao fonts-liberation fonts-lklug-sinhala fonts-nanum fonts-opensymbol fonts-sil-abyssinica fonts-sil-padauk
  fonts-takao-pgothic fonts-thai-tlwg fonts-tibetan-machine fonts-tlwg-garuda fonts-tlwg-kinnari fonts-tlwg-loma fonts-tlwg-mono fonts-tlwg-norasi
  fonts-tlwg-purisa fonts-tlwg-sawasdee fonts-tlwg-typewriter fonts-tlwg-typist fonts-tlwg-typo fonts-tlwg-umpush fonts-tlwg-waree
  foomatic-db-compressed-ppds gcc gcc-4.8 gconf-service gconf-service-backend gconf2 gconf2-common gcr gdb gdisk gdm gedit gedit-common genisoimage
  geoclue gettext ghostscript ghostscript-x gir1.2-accountsservice-1.0 gir1.2-atk-1.0 gir1.2-atspi-2.0 gir1.2-caribou-1.0 gir1.2-clutter-1.0
  gir1.2-clutter-gst-2.0 gir1.2-cogl-1.0 gir1.2-coglpango-1.0 gir1.2-dbusmenu-glib-0.4 gir1.2-dee-1.0 gir1.2-evince-3.0 gir1.2-freedesktop
  gir1.2-gck-1 gir1.2-gcr-3 gir1.2-gdata-0.0 gir1.2-gdesktopenums-3.0 gir1.2-gdkpixbuf-2.0 gir1.2-gdm-1.0 gir1.2-gkbd-3.0 gir1.2-gmenu-3.0
  gir1.2-gnomebluetooth-1.0 gir1.2-gnomedesktop-3.0 gir1.2-gnomekeyring-1.0 gir1.2-goa-1.0 gir1.2-gst-plugins-base-1.0 gir1.2-gstreamer-1.0
  gir1.2-gtk-3.0 gir1.2-gtkclutter-1.0 gir1.2-gtksource-3.0 gir1.2-gtop-2.0 gir1.2-gudev-1.0 gir1.2-ibus-1.0 gir1.2-javascriptcoregtk-3.0
  gir1.2-json-1.0 gir1.2-mutter-3.0 gir1.2-networkmanager-1.0 gir1.2-nmgtk-1.0 gir1.2-notify-0.7 gir1.2-packagekitglib-1.0 gir1.2-pango-1.0
  gir1.2-peas-1.0 gir1.2-polkit-1.0 gir1.2-rb-3.0 gir1.2-rest-0.7 gir1.2-secret-1 gir1.2-soup-2.4 gir1.2-syncmenu-0.1 gir1.2-telepathyglib-0.12
  gir1.2-telepathylogger-0.2 gir1.2-totem-1.0 gir1.2-totem-plparser-1.0 gir1.2-tracker-0.16 gir1.2-udisks-2.0 gir1.2-unity-5.0 gir1.2-upowerglib-1.0
  gir1.2-vte-2.90 gir1.2-webkit-3.0 gir1.2-wnck-3.0 gir1.2-xkl-1.0 gir1.2-zpj-0.0 gjs gkbd-capplet glib-networking glib-networking-common
  glib-networking-services gnome-accessibility-themes gnome-backgrounds gnome-bluetooth gnome-calculator gnome-color-manager gnome-contacts
  gnome-control-center gnome-control-center-data gnome-control-center-shared-data gnome-desktop3-data gnome-disk-utility gnome-documents
  gnome-font-viewer gnome-icon-theme gnome-icon-theme-extras gnome-icon-theme-full gnome-icon-theme-symbolic gnome-keyring gnome-mahjongg
  gnome-menus gnome-mines gnome-online-accounts gnome-online-miners gnome-orca gnome-screenshot gnome-session gnome-session-bin
  gnome-session-canberra gnome-session-common gnome-settings-daemon gnome-settings-daemon-schemas gnome-shell gnome-shell-common
  gnome-shell-extensions gnome-sudoku gnome-sushi gnome-system-log gnome-system-monitor gnome-terminal gnome-terminal-data gnome-themes-standard
  gnome-themes-standard-data gnome-tweak-tool gnome-user-guide gnome-user-share gnome-video-effects growisofs gsettings-desktop-schemas
  gsettings-ubuntu-schemas gsfonts gstreamer0.10-alsa gstreamer0.10-nice gstreamer0.10-plugins-base gstreamer0.10-plugins-good
  gstreamer0.10-pulseaudio gstreamer0.10-x gstreamer1.0-alsa gstreamer1.0-clutter gstreamer1.0-nice gstreamer1.0-plugins-base
  gstreamer1.0-plugins-good gstreamer1.0-pulseaudio gstreamer1.0-x gtk2-engines-pixbuf gucharmap guile-2.0-libs gvfs gvfs-backends gvfs-backends-goa
  gvfs-bin gvfs-common gvfs-daemons gvfs-fuse gvfs-libs hardening-includes hicolor-icon-theme hplip hplip-data humanity-icon-theme hunspell-en-us
  hwdata ibus ibus-gtk ibus-gtk3 ibus-pinyin ibus-table im-config indicator-application indicator-sync inputattach intel-gpu-tools intltool-debian
  iproute iputils-arping itstool kerneloops-daemon libaa1 libaccount-plugin-1.0-0 libaccount-plugin-generic-oauth libaccount-plugin-google
  libaccounts-glib0 libaccounts-qt5-1 libappindicator3-1 libapt-pkg-perl libarchive-zip-perl libarchive13 libart-2.0-2 libasan0 libasound2
  libasound2-data libasound2-plugins libaspell15 libasprintf-dev libassuan0 libasyncns0 libatasmart4 libatk-adaptor libatk-bridge2.0-0 libatk1.0-0
  libatk1.0-data libatkmm-1.6-1 libatomic1 libatspi2.0-0 libauthen-sasl-perl libautodie-perl libavahi-client3 libavahi-common-data libavahi-common3
  libavahi-core7 libavahi-glib1 libavahi-gobject0 libavc1394-0 libbluetooth3 libboost-date-time1.54.0 libboost-system1.54.0 libbrasero-media3-1
  libbrlapi0.6 libburn4 libc-dev-bin libc6-dbg libc6-dev libcaca0 libcairo-gobject2 libcairo2 libcairomm-1.0-1 libcamel-1.2-45
  libcanberra-gtk-module libcanberra-gtk0 libcanberra-gtk3-0 libcanberra-gtk3-module libcanberra-pulse libcanberra0 libcaribou-common libcaribou0
  libcdio-cdda1 libcdio-paranoia1 libcdio13 libcdparanoia0 libcdr-0.0-0 libcgmanager0 libcheese-gtk23 libcheese7 libclone-perl libcloog-isl4
  libclucene-contribs1 libclucene-core1 libclutter-1.0-0 libclutter-1.0-common libclutter-gst-2.0-0 libclutter-gtk-1.0-0 libcmis-0.4-4
  libcogl-common libcogl-pango15 libcogl15 libcolamd2.8.0 libcolord-gtk1 libcolord1 libcolorhug1 libcrack2 libcroco3 libcrypt-passwdmd5-perl
  libcups2 libcupscgi1 libcupsfilters1 libcupsimage2 libcupsmime1 libcupsppdc1 libcurl3 libdaemon0 libdatrie1 libdbusmenu-glib4 libdbusmenu-gtk3-4
  libdbusmenu-gtk4 libdconf1 libdee-1.0-4 libdigest-hmac-perl libdjvulibre-text libdjvulibre21 libdmapsharing-3.0-2 libdotconf0 libdpkg-perl
  libdrm-intel1 libdrm-nouveau2 libdrm-radeon1 libdv4 libebackend-1.2-7 libebook-1.2-14 libebook-contacts-1.2-0 libecal-1.2-16 libedata-book-1.2-20
  libedata-cal-1.2-23 libedataserver-1.2-18 libegl1-mesa libegl1-mesa-drivers libelfg0 libemail-valid-perl libenca0 libenchant1c2a
  libencode-locale-perl liberror-perl libespeak1 libevdocument3-4 libevent-2.0-5 libevolution libevview3-3 libexempi3 libexif12 libexiv2-12
  libexttextcat-2.0-0 libexttextcat-data libfarstream-0.1-0 libfarstream-0.2-2 libfftw3-single3 libfile-basedir-perl libfile-copy-recursive-perl
  libfile-desktopentry-perl libfile-fcntllock-perl libfile-listing-perl libfile-mimeinfo-perl libflac8 libfolks-eds25 libfolks-telepathy25
  libfolks25 libfont-afm-perl libfontconfig1 libfontembed1 libfontenc1 libframe6 libfs6 libgail-3-0 libgail-common libgail18 libgbm1 libgc1c2
  libgcc-4.8-dev libgconf-2-4 libgcr-ui-3-1 libgd3 libgdata-common libgdata13 libgdk-pixbuf2.0-0 libgdk-pixbuf2.0-common libgdm1 libgee-0.8-2
  libgeis1 libgeoclue0 libgettextpo-dev libgettextpo0 libgexiv2-2 libgif4 libgjs0e libgl1-mesa-dri libgl1-mesa-glx libglamor0 libglapi-mesa
  libgles2-mesa libglib2.0-bin libglibmm-2.4-1c2a libglu1-mesa libgmime-2.6-0 libgmp10 libgnome-bluetooth11 libgnome-control-center1
  libgnome-desktop-3-7 libgnome-keyring-common libgnome-keyring0 libgnome-menu-3-0 libgnomekbd-common libgnomekbd8 libgoa-1.0-0b libgoa-1.0-common
  libgoa-backend-1.0-1 libgomp1 libgpgme11 libgphoto2-6 libgphoto2-l10n libgphoto2-port10 libgpm2 libgpod-common libgpod4 libgrail6 libgraphite2-3
  libgrilo-0.2-1 libgrip0 libgs9 libgs9-common libgsf-1-114 libgsf-1-common libgssdp-1.0-3 libgstreamer-plugins-base0.10-0
  libgstreamer-plugins-base1.0-0 libgstreamer-plugins-good1.0-0 libgstreamer0.10-0 libgstreamer1.0-0 libgtk-3-0 libgtk-3-bin libgtk-3-common
  libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libgtkhtml-4.0-0 libgtkhtml-4.0-common libgtkhtml-editor-4.0-0 libgtkmm-3.0-1 libgtksourceview-3.0-1
  libgtksourceview-3.0-common libgtop2-7 libgtop2-common libgucharmap-2-90-7 libgudev-1.0-0 libgupnp-1.0-4 libgupnp-igd-1.0-4 libgusb2
  libgutenprint2 libgweather-3-6 libgweather-common libgxps2 libharfbuzz-icu0 libharfbuzz0b libhdb9-heimdal libhpmud0 libhtml-form-perl
  libhtml-format-perl libhtml-parser-perl libhtml-tagset-perl libhtml-tree-perl libhttp-cookies-perl libhttp-daemon-perl libhttp-date-perl
  libhttp-message-perl libhttp-negotiate-perl libhunspell-1.3-0 libhyphen0 libibus-1.0-5 libical1 libicc2 libice6 libicu52 libido3-0.1-0
  libiec61883-0 libieee1284-3 libijs-0.35 libimdi0 libimobiledevice4 libindicator3-7 libio-html-perl libio-pty-perl libio-socket-inet6-perl
  libio-socket-ssl-perl libipc-run-perl libipc-system-simple-perl libiptcdata0 libisl10 libisofs6 libitm1 libiw30 libjack-jackd2-0 libjasper1
  libjavascriptcoregtk-3.0-0 libjbig0 libjbig2dec0 libjpeg-turbo8 libjpeg8 libjson-glib-1.0-0 libjson-glib-1.0-common libjte1 libkpathsea6
  liblangtag-common liblangtag1 liblcms2-2 libldb1 liblircclient0 liblist-moreutils-perl libllvm3.4 liblouis-data liblouis2 libltdl7 liblua5.2-0
  liblwp-mediatypes-perl liblwp-protocol-https-perl liblzo2-2 libmail-spf-perl libmailtools-perl libmbim-glib0 libmeanwhile1 libmessaging-menu0
  libmhash2 libminiupnpc8 libmission-control-plugins0 libmm-glib0 libmnl0 libmozjs-24-0 libmpc3 libmpfr4 libmspub-0.0-0 libmtdev1 libmtp-common
  libmtp-runtime libmtp9 libmusicbrainz5-0 libmutter0c libmythes-1.2-0 libnatpmp1 libnautilus-extension1a libneon27-gnutls libnet-dns-perl
  libnet-domain-tld-perl libnet-http-perl libnet-ip-perl libnet-libidn-perl libnet-smtp-ssl-perl libnet-ssleay-perl libnetaddr-ip-perl
  libnetfilter-conntrack3 libnettle4 libnice10 libnl-route-3-200 libnm-glib-vpn1 libnm-glib4 libnm-gtk-common libnm-gtk0 libnm-util2 libnotify-bin
  libnotify4 libnspr4 libnss-mdns libnss-myhostname libnss3 libnss3-nssdb libntdb1 liboauth0 libogg0 libopencc1 libopenobex1 libopenvg1-mesa
  liborc-0.4-0 liborcus-0.6-0 libp11-kit-gnome-keyring libpackagekit-glib2-16 libpam-gnome-keyring libpango-1.0-0 libpango1.0-0 libpangocairo-1.0-0
  libpangoft2-1.0-0 libpangomm-1.4-1 libpangox-1.0-0 libpangoxft-1.0-0 libpaper-utils libpaper1 libpciaccess0 libpcsclite1 libpeas-1.0-0
  libpeas-common libperl5.18 libperlio-gzip-perl libpixman-1-0 libplist1 libpolkit-agent-1-0 libpolkit-backend-1-0 libpoppler-glib8 libpoppler44
  libportaudio2 libproxy1 libproxy1-plugin-gsettings libproxy1-plugin-networkmanager libpst4 libpulse-mainloop-glib0 libpulse0 libpulsedsp
  libpurple-bin libpurple0 libpwquality-common libpwquality1 libpython2.7 libpython3.4 libpyzy-1.0-0 libqmi-glib0 libqpdf13 libqt5core5a libqt5dbus5
  libqt5gui5 libqt5network5 libqt5opengl5 libqt5positioning5 libqt5printsupport5 libqt5qml5 libqt5quick5 libqt5sensors5 libqt5sql5 libqt5sql5-sqlite
  libqt5test5 libqt5webkit5 libqt5widgets5 libqt5xml5 libquadmath0 libraptor2-0 librasqal3 libraw1394-11 libraw9 librdf0 libreadline5
  libreoffice-avmedia-backend-gstreamer libreoffice-base-core libreoffice-calc libreoffice-common libreoffice-core libreoffice-draw
  libreoffice-gnome libreoffice-gtk libreoffice-impress libreoffice-math libreoffice-ogltrans libreoffice-pdfimport
  libreoffice-presentation-minimizer libreoffice-style-galaxy libreoffice-style-human libreoffice-style-tango libreoffice-writer librest-0.7-0
  librhythmbox-core8 librsvg2-2 librsvg2-common librsync1 libsamplerate0 libsane libsane-common libsane-hpaio libsbc1 libsecret-1-0 libsecret-common
  libsensors4 libsgutils2-2 libshout3 libsignon-extension1 libsignon-glib1 libsignon-plugins-common1 libsignon-qt5-1 libsm6 libsmbclient libsndfile1
  libsnmp-base libsnmp30 libsocket6-perl libsonic0 libsoup-gnome2.4-1 libsoup2.4-1 libspectre1 libspeechd2 libspeex1 libspeexdsp1
  libstartup-notification0 libsub-identify-perl libsync-menu1 libsys-hostname-long-perl libsystemd-journal0 libt1-5 libtag1-vanilla libtag1c2a
  libtalloc2 libtcl8.6 libtdb1 libtelepathy-farstream3 libtelepathy-glib0 libtelepathy-logger3 libtevent0 libtext-levenshtein-perl libthai-data
  libthai0 libtheora0 libtiff5 libtimezonemap1 libtk8.6 libtotem-plparser18 libtotem0 libtracker-extract-0.16-0 libtracker-miner-0.16-0
  libtracker-sparql-0.16-0 libtxc-dxtn-s2tc0 libudisks2-0 libunistring0 libunity-control-center1 libunity-protocol-private0
  libunity-scopes-json-def-desktop libunity9 libupower-glib1 liburi-perl libusbmuxd2 libutempter0 libv4l-0 libv4lconvert0 libvisio-0.0-0
  libvisual-0.4-0 libvisual-0.4-plugins libvorbis0a libvorbisenc2 libvorbisfile3 libvpx1 libvte-2.90-9 libvte-2.90-common libwacom-common libwacom2
  libwavpack1 libwayland-client0 libwayland-cursor0 libwayland-egl1-mesa libwayland-server0 libwbclient0 libwebkitgtk-3.0-0 libwebkitgtk-3.0-common
  libwebp5 libwebpmux1 libwhoopsie0 libwmf0.2-7 libwmf0.2-7-gtk libwnck-3-0 libwnck-3-common libwpd-0.9-9 libwpg-0.2-2 libwps-0.2-2 libwrap0
  libwww-perl libwww-robotrules-perl libx11-xcb1 libxatracker2 libxaw7 libxcb-dri2-0 libxcb-dri3-0 libxcb-glx0 libxcb-icccm4 libxcb-image0
  libxcb-keysyms1 libxcb-present0 libxcb-randr0 libxcb-render-util0 libxcb-render0 libxcb-shape0 libxcb-shm0 libxcb-sync1 libxcb-util0
  libxcb-xf86dri0 libxcb-xfixes0 libxcb-xkb1 libxcb-xv0 libxcomposite1 libxcursor1 libxdamage1 libxfixes3 libxfont1 libxft2 libxi6 libxinerama1
  libxkbcommon0 libxkbfile1 libxklavier16 libxml2-utils libxmu6 libxp6 libxpm4 libxrandr2 libxrender1 libxres1 libxshmfence1 libxslt1.1 libxss1
  libxt6 libxtst6 libxv1 libxvmc1 libxxf86dga1 libxxf86vm1 libyajl2 libyelp0 libytnef0 libzapojit-0.0-0 libzeitgeist-1.0-1 libzeitgeist-2.0-0
  libzephyr4 lintian linux-libc-dev linux-sound-base lp-solve make manpages-dev mcp-account-manager-goa mcp-account-manager-uoa media-player-info
  memtest86+ mobile-broadband-provider-info modemmanager mousetweaks mscompress mtools mutter mutter-common nautilus nautilus-data nautilus-sendto
  nautilus-sendto-empathy nautilus-share network-manager network-manager-gnome network-manager-pptp network-manager-pptp-gnome notification-daemon
  obex-data-server obexd-client oneconf oneconf-common openprinting-ppds p11-kit p11-kit-modules patch patchutils pcmciautils plymouth-label
  plymouth-theme-ubuntu-gnome-logo plymouth-theme-ubuntu-gnome-text policykit-1 policykit-1-gnome policykit-desktop-privileges poppler-data
  poppler-utils pptp-linux printer-driver-c2esp printer-driver-foo2zjs printer-driver-foo2zjs-common printer-driver-gutenprint printer-driver-hpcups
  printer-driver-min12xxw printer-driver-pnm2ppa printer-driver-postscript-hp printer-driver-ptouch printer-driver-pxljr printer-driver-sag-gdi
  printer-driver-splix pulseaudio pulseaudio-module-bluetooth pulseaudio-module-x11 pulseaudio-utils python-aptdaemon python-aptdaemon.gtk3widgets
  python-boto python-cairo python-cloudfiles python-commandnotfound python-configglue python-crypto python-cups python-cupshelpers python-dbus
  python-dbus-dev python-debtagshw python-defer python-dirspec python-gdbm python-gi python-gi-cairo python-gnomekeyring python-gobject
  python-gobject-2 python-gtk2 python-httplib2 python-ibus python-imaging python-ldb python-libxml2 python-lockfile python-lxml python-notify
  python-ntdb python-oauthlib python-oneconf python-openssl python-pam python-pexpect python-pil python-piston-mini-client python-pkg-resources
  python-protobuf python-pycurl python-pyinotify python-renderpm python-reportlab python-reportlab-accel python-requests python-samba python-serial
  python-smbc python-talloc python-tdb python-twisted-bin python-twisted-core python-twisted-names python-twisted-web python-ubuntu-sso-client
  python-ubuntuone-client python-ubuntuone-control-panel python-ubuntuone-storageprotocol python-urllib3 python-xdg python-zeitgeist
  python-zope.interface python3-apport python3-aptdaemon python3-aptdaemon.gtk3widgets python3-aptdaemon.pkcompat python3-brlapi python3-cairo
  python3-chardet python3-crypto python3-debian python3-defer python3-dirspec python3-gi-cairo python3-httplib2 python3-louis python3-mako
  python3-markupsafe python3-oauthlib python3-oneconf python3-piston-mini-client python3-pkg-resources python3-problem-report python3-pyatspi
  python3-pycurl python3-six python3-software-properties python3-speechd python3-uno python3-xdg python3-xkit qpdf re2c rfkill rhythmbox
  rhythmbox-data rhythmbox-mozilla rhythmbox-plugin-cdrecorder rhythmbox-plugin-magnatune rhythmbox-plugin-zeitgeist rhythmbox-plugins
  rhythmbox-ubuntuone rtkit sa-compile samba-common samba-common-bin samba-libs sane-utils seahorse session-migration sessioninstaller shotwell
  shotwell-common signon-keyring-extension signon-plugin-oauth2 signon-plugin-password signon-ui signond simple-scan smbclient software-center
  software-center-aptdaemon-plugins software-properties-common software-properties-gtk sound-theme-freedesktop spamassassin spamc speech-dispatcher
  speech-dispatcher-audio-plugins ssh-askpass-gnome ssl-cert syslinux syslinux-common syslinux-legacy system-config-printer-common
  system-config-printer-gnome system-config-printer-udev t1utils tcl tcl8.6 tcpd telepathy-gabble telepathy-haze telepathy-idle telepathy-logger
  telepathy-mission-control-5 telepathy-salut tk tk8.6 toshset totem totem-common totem-plugins tracker tracker-extract tracker-miner-fs
  tracker-utils transmission-common transmission-gtk ttf-indic-fonts-core ttf-punjabi-fonts ttf-ubuntu-font-family ubuntu-drivers-common
  ubuntu-extras-keyring ubuntu-gnome-default-settings ubuntu-gnome-desktop ubuntu-release-upgrader-gtk ubuntu-sso-client ubuntu-system-service
  ubuntuone-client ubuntuone-client-data ubuntuone-control-panel udisks2 unattended-upgrades unity-asset-pool unity-control-center
  unity-control-center-signon unity-settings-daemon uno-libs3 unoconv unzip update-inetd update-manager update-notifier update-notifier-common
  upower ure usb-creator-common usb-creator-gtk usb-modeswitch usb-modeswitch-data usbmuxd vino wamerican whoopsie wireless-tools wodim
  wpasupplicant x11-apps x11-common x11-session-utils x11-utils x11-xfs-utils x11-xkb-utils x11-xserver-utils xbitmaps xdg-user-dirs
  xdg-user-dirs-gtk xdg-utils xdiagnose xfonts-base xfonts-encodings xfonts-mathml xfonts-scalable xfonts-utils xinit xinput xorg xorg-docs-core
  xserver-common xserver-xephyr xserver-xorg xserver-xorg-core xserver-xorg-input-all xserver-xorg-input-evdev xserver-xorg-input-mouse
  xserver-xorg-input-synaptics xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-all xserver-xorg-video-ati
  xserver-xorg-video-cirrus xserver-xorg-video-fbdev xserver-xorg-video-glamoregl xserver-xorg-video-intel xserver-xorg-video-mach64
  xserver-xorg-video-mga xserver-xorg-video-modesetting xserver-xorg-video-neomagic xserver-xorg-video-nouveau xserver-xorg-video-openchrome
  xserver-xorg-video-qxl xserver-xorg-video-r128 xserver-xorg-video-radeon xserver-xorg-video-s3 xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident
  xserver-xorg-video-vesa xserver-xorg-video-vmware xsltproc xterm xul-ext-ubufox yelp yelp-tools yelp-xsl zeitgeist zeitgeist-core
  zeitgeist-datahub zenity zenity-common zip zsync
0 upgraded, 1235 newly installed, 0 to remove and 11 not upgraded.
Need to get 444 MB of archives.
After this operation, 1,690 MB of additional disk space will be used.[/B]
Do you want to continue? [Y/n] n
Abort.

```

---

### Post by kansasnoob on 2014-04-02
BTW the packages available for upgrade are:

```
root@lance-desktop:/# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  libcgmanager0 linux-headers-3.13.0-21 linux-headers-3.13.0-21-generic linux-image-3.13.0-21-generic linux-image-extra-3.13.0-21-generic
The following packages will be upgraded:
  dbus libdbus-1-3 libpam-systemd libsystemd-daemon0 libsystemd-login0 libudev1 linux-generic linux-headers-generic linux-image-generic
  systemd-services udev
11 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 62.7 MB of archives.
After this operation, 222 MB of additional disk space will be used.
Do you want to continue? [Y/n] n
Abort.

```

I just don't want to upgrade the kernel in a chroot ;)

---

### Post by kansasnoob on 2014-04-02
Lets see what effect just installing 'gnome-session-common' has on things:

```
root@lance-desktop:/# apt-get install gnome-session-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  gnome-session-common
0 upgraded, 1 newly installed, 0 to remove and 11 not upgraded.
Need to get 42.2 kB of archives.
After this operation, 352 kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ trusty/main gnome-session-common all 3.9.90-0ubuntu12 [42.2 kB]
Fetched 42.2 kB in 0s (113 kB/s)              
E: Can not write log (Is /dev/pts mounted?) - openpty (2: No such file or directory)
Selecting previously unselected package gnome-session-common.
(Reading database ... 49544 files and directories currently installed.)
Preparing to unpack .../gnome-session-common_3.9.90-0ubuntu12_all.deb ...
Unpacking gnome-session-common (3.9.90-0ubuntu12) ...
Processing triggers for mime-support (3.54ubuntu1) ...
Setting up gnome-session-common (3.9.90-0ubuntu12) ...

```

No apparent change:

```
0 upgraded, 1234 newly installed, 0 to remove and 11 not upgraded.
Need to get 444 MB of archives.
After this operation, 1,690 MB of additional disk space will be used.
Do you want to continue? [Y/n] n
Abort.

```

---

### Post by kansasnoob on 2014-04-02
Purged 'gnome-session-common' and going to try 'gnome-session':

```
root@lance-desktop:/# apt-get purge gnome-session-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  gnome-session-common*
0 upgraded, 0 newly installed, 1 to remove and 11 not upgraded.
After this operation, 352 kB disk space will be freed.
Do you want to continue? [Y/n] y
E: Can not write log (Is /dev/pts mounted?) - openpty (2: No such file or directory)
(Reading database ... 49575 files and directories currently installed.)
Removing gnome-session-common (3.9.90-0ubuntu12) ...
Purging configuration files for gnome-session-common (3.9.90-0ubuntu12) ...
Processing triggers for mime-support (3.54ubuntu1) ...
root@lance-desktop:/# apt-get install gnome-session
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  acl aspell aspell-en at-spi2-core colord dbus-x11 dconf-cli dconf-gsettings-backend dconf-service dialog dictionaries-common enchant fontconfig
  fontconfig-config fonts-dejavu-core gir1.2-atk-1.0 gir1.2-freedesktop gir1.2-gdkpixbuf-2.0 gir1.2-gtk-3.0 gir1.2-ibus-1.0 gir1.2-pango-1.0
  glib-networking glib-networking-common glib-networking-services gnome-desktop3-data gnome-icon-theme gnome-session-bin gnome-session-common
  gnome-settings-daemon gnome-settings-daemon-schemas gsettings-desktop-schemas gstreamer0.10-pulseaudio gstreamer1.0-plugins-base
  gstreamer1.0-plugins-good gstreamer1.0-x hicolor-icon-theme humanity-icon-theme hunspell-en-us hwdata ibus ibus-gtk ibus-gtk3 im-config libaa1
  libasound2 libasound2-data libasound2-plugins libaspell15 libasyncns0 libatk-bridge2.0-0 libatk1.0-0 libatk1.0-data libatspi2.0-0 libavahi-client3
  libavahi-common-data libavahi-common3 libavc1394-0 libcaca0 libcairo-gobject2 libcairo2 libcanberra-gtk3-0 libcanberra-gtk3-module libcanberra0
  libcdparanoia0 libcgmanager0 libcolord1 libcolorhug1 libcroco3 libcups2 libdatrie1 libdconf1 libdrm-intel1 libdrm-nouveau2 libdrm-radeon1 libdv4
  libenchant1c2a libexif12 libfftw3-single3 libflac8 libfontconfig1 libgd3 libgdk-pixbuf2.0-0 libgdk-pixbuf2.0-common libgeoclue0 libgl1-mesa-dri
  libgl1-mesa-glx libglapi-mesa libglu1-mesa libgnome-desktop-3-7 libgomp1 libgphoto2-6 libgphoto2-l10n libgphoto2-port10 libgpm2 libgraphite2-3
  libgstreamer-plugins-base0.10-0 libgstreamer-plugins-base1.0-0 libgstreamer-plugins-good1.0-0 libgstreamer0.10-0 libgstreamer1.0-0 libgtk-3-0
  libgtk-3-bin libgtk-3-common libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libgudev-1.0-0 libgusb2 libharfbuzz-icu0 libharfbuzz0b libhunspell-1.3-0
  libibus-1.0-5 libice6 libicu52 libiec61883-0 libieee1284-3 libimobiledevice4 libjack-jackd2-0 libjasper1 libjavascriptcoregtk-3.0-0 libjbig0
  libjpeg-turbo8 libjpeg8 libjson-glib-1.0-0 libjson-glib-1.0-common liblcms2-2 libllvm3.4 libltdl7 libnotify4 libogg0 liborc-0.4-0 libpango-1.0-0
  libpangocairo-1.0-0 libpangoft2-1.0-0 libpangoxft-1.0-0 libpciaccess0 libpixman-1-0 libplist1 libpolkit-agent-1-0 libpolkit-backend-1-0 libproxy1
  libpulse-mainloop-glib0 libpulse0 libpulsedsp libraw1394-11 librsvg2-2 librsvg2-common libsamplerate0 libsane libsane-common libsecret-1-0
  libsecret-common libshout3 libsm6 libsndfile1 libsoup2.4-1 libspeex1 libspeexdsp1 libsystemd-journal0 libtag1-vanilla libtag1c2a libtdb1
  libthai-data libthai0 libtheora0 libtiff5 libtxc-dxtn-s2tc0 libupower-glib1 libusbmuxd2 libv4l-0 libv4lconvert0 libvisual-0.4-0
  libvisual-0.4-plugins libvorbis0a libvorbisenc2 libvorbisfile3 libvpx1 libwacom-common libwacom2 libwavpack1 libwayland-client0 libwayland-cursor0
  libwebkitgtk-3.0-0 libwebkitgtk-3.0-common libwebp5 libwrap0 libx11-xcb1 libxcb-dri2-0 libxcb-dri3-0 libxcb-glx0 libxcb-present0 libxcb-render0
  libxcb-shm0 libxcb-sync1 libxcomposite1 libxcursor1 libxdamage1 libxfixes3 libxft2 libxi6 libxinerama1 libxkbcommon0 libxkbfile1 libxpm4
  libxrandr2 libxrender1 libxshmfence1 libxslt1.1 libxt6 libxtst6 libxv1 libxxf86vm1 nautilus-data notification-daemon policykit-1 pulseaudio
  pulseaudio-module-x11 pulseaudio-utils python-cairo python-gi python-gobject-2 python-gtk2 python-notify rtkit session-migration
  sound-theme-freedesktop tcpd upower usbmuxd x11-common zenity zenity-common
Suggested packages:
  aspell-doc spellutils wordlist emacsen-common jed-extra gnome-user-guide desktop-base gnome-keyring x11-xserver-utils gnome-screensaver metacity
  x-window-manager gvfs hunspell openoffice.org-hunspell openoffice.org-core ibus-clutter ibus-doc ibus-qt4 alsa-utils libcanberra-gtk0
  libcanberra-pulse cups-common libdv-bin oss-compat libenchant-voikko libfftw3-bin libfftw3-dev libgd-tools geoclue libglide3 gphoto2 gtkam gpm
  gstreamer-codec-install gnome-codec-install gstreamer0.10-tools gstreamer0.10-plugins-base gstreamer1.0-tools jackd2 libjasper-runtime
  liblcms2-utils ttf-baekmuk ttf-arphic-gbsn00lp ttf-arphic-bsmi00lp ttf-arphic-gkai00mp ttf-arphic-bkai00mp libraw1394-doc librsvg2-bin
  avahi-daemon hplip hpoj libsane-extras sane-utils speex nautilus pavumeter paman pavucontrol paprefs pulseaudio-module-raop
  pulseaudio-esound-compat python-gi-cairo python-gobject-2-dbg python-gtk2-doc
The following NEW packages will be installed:
  acl aspell aspell-en at-spi2-core colord dbus-x11 dconf-cli dconf-gsettings-backend dconf-service dialog dictionaries-common enchant fontconfig
  fontconfig-config fonts-dejavu-core gir1.2-atk-1.0 gir1.2-freedesktop gir1.2-gdkpixbuf-2.0 gir1.2-gtk-3.0 gir1.2-ibus-1.0 gir1.2-pango-1.0
  glib-networking glib-networking-common glib-networking-services gnome-desktop3-data gnome-icon-theme gnome-session gnome-session-bin
  gnome-session-common gnome-settings-daemon gnome-settings-daemon-schemas gsettings-desktop-schemas gstreamer0.10-pulseaudio
  gstreamer1.0-plugins-base gstreamer1.0-plugins-good gstreamer1.0-x hicolor-icon-theme humanity-icon-theme hunspell-en-us hwdata ibus ibus-gtk
  ibus-gtk3 im-config libaa1 libasound2 libasound2-data libasound2-plugins libaspell15 libasyncns0 libatk-bridge2.0-0 libatk1.0-0 libatk1.0-data
  libatspi2.0-0 libavahi-client3 libavahi-common-data libavahi-common3 libavc1394-0 libcaca0 libcairo-gobject2 libcairo2 libcanberra-gtk3-0
  libcanberra-gtk3-module libcanberra0 libcdparanoia0 libcgmanager0 libcolord1 libcolorhug1 libcroco3 libcups2 libdatrie1 libdconf1 libdrm-intel1
  libdrm-nouveau2 libdrm-radeon1 libdv4 libenchant1c2a libexif12 libfftw3-single3 libflac8 libfontconfig1 libgd3 libgdk-pixbuf2.0-0
  libgdk-pixbuf2.0-common libgeoclue0 libgl1-mesa-dri libgl1-mesa-glx libglapi-mesa libglu1-mesa libgnome-desktop-3-7 libgomp1 libgphoto2-6
  libgphoto2-l10n libgphoto2-port10 libgpm2 libgraphite2-3 libgstreamer-plugins-base0.10-0 libgstreamer-plugins-base1.0-0
  libgstreamer-plugins-good1.0-0 libgstreamer0.10-0 libgstreamer1.0-0 libgtk-3-0 libgtk-3-bin libgtk-3-common libgtk2.0-0 libgtk2.0-bin
  libgtk2.0-common libgudev-1.0-0 libgusb2 libharfbuzz-icu0 libharfbuzz0b libhunspell-1.3-0 libibus-1.0-5 libice6 libicu52 libiec61883-0
  libieee1284-3 libimobiledevice4 libjack-jackd2-0 libjasper1 libjavascriptcoregtk-3.0-0 libjbig0 libjpeg-turbo8 libjpeg8 libjson-glib-1.0-0
  libjson-glib-1.0-common liblcms2-2 libllvm3.4 libltdl7 libnotify4 libogg0 liborc-0.4-0 libpango-1.0-0 libpangocairo-1.0-0 libpangoft2-1.0-0
  libpangoxft-1.0-0 libpciaccess0 libpixman-1-0 libplist1 libpolkit-agent-1-0 libpolkit-backend-1-0 libproxy1 libpulse-mainloop-glib0 libpulse0
  libpulsedsp libraw1394-11 librsvg2-2 librsvg2-common libsamplerate0 libsane libsane-common libsecret-1-0 libsecret-common libshout3 libsm6
  libsndfile1 libsoup2.4-1 libspeex1 libspeexdsp1 libsystemd-journal0 libtag1-vanilla libtag1c2a libtdb1 libthai-data libthai0 libtheora0 libtiff5
  libtxc-dxtn-s2tc0 libupower-glib1 libusbmuxd2 libv4l-0 libv4lconvert0 libvisual-0.4-0 libvisual-0.4-plugins libvorbis0a libvorbisenc2
  libvorbisfile3 libvpx1 libwacom-common libwacom2 libwavpack1 libwayland-client0 libwayland-cursor0 libwebkitgtk-3.0-0 libwebkitgtk-3.0-common
  libwebp5 libwrap0 libx11-xcb1 libxcb-dri2-0 libxcb-dri3-0 libxcb-glx0 libxcb-present0 libxcb-render0 libxcb-shm0 libxcb-sync1 libxcomposite1
  libxcursor1 libxdamage1 libxfixes3 libxft2 libxi6 libxinerama1 libxkbcommon0 libxkbfile1 libxpm4 libxrandr2 libxrender1 libxshmfence1 libxslt1.1
  libxt6 libxtst6 libxv1 libxxf86vm1 nautilus-data notification-daemon policykit-1 pulseaudio pulseaudio-module-x11 pulseaudio-utils python-cairo
  python-gi python-gobject-2 python-gtk2 python-notify rtkit session-migration sound-theme-freedesktop tcpd upower usbmuxd x11-common zenity
  zenity-common
0 upgraded, 233 newly installed, 0 to remove and 11 not upgraded.
Need to get 58.3 MB/58.3 MB of archives.
After this operation, 269 MB of additional disk space will be used.
Do you want to continue? [Y/n] 

```

And what would happen if I added 'ubuntu-gnome-desktop' after that:

```
root@lance-desktop:/# apt-get install ubuntu-gnome-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  account-plugin-aim account-plugin-facebook account-plugin-google account-plugin-jabber account-plugin-salut account-plugin-windows-live
  account-plugin-yahoo acpi-support acpid aisleriot alsa-base alsa-utils anacron apg app-install-data app-install-data-partner apport apport-gtk
  apport-symptoms aptdaemon aptdaemon-data apturl apturl-common argyll avahi-autoipd avahi-daemon avahi-utils baobab bc binutils bluez bluez-alsa
  bluez-cups bluez-gstreamer brasero brasero-cdrkit brasero-common brltty cheese cheese-common cpp cpp-4.8 cracklib-runtime cups cups-browsed
  cups-bsd cups-client cups-common cups-core-drivers cups-daemon cups-filters cups-filters-core-drivers cups-pk-helper cups-ppdc cups-server-common
  dc dconf-editor deja-dup deja-dup-backend-cloudfiles deja-dup-backend-gvfs deja-dup-backend-s3 deja-dup-backend-ubuntuone desktop-file-utils
  diffstat dnsmasq-base duplicity dvd+rw-tools empathy empathy-common eog espeak-data evince evince-common evolution evolution-common
  evolution-data-server evolution-data-server-common evolution-data-server-online-accounts evolution-indicator evolution-plugins file-roller firefox
  folks-common fonts-cantarell fonts-droid fonts-freefont-ttf fonts-kacst fonts-kacst-one fonts-khmeros-core fonts-lao fonts-liberation
  fonts-lklug-sinhala fonts-nanum fonts-opensymbol fonts-sil-abyssinica fonts-sil-padauk fonts-takao-pgothic fonts-thai-tlwg fonts-tibetan-machine
  fonts-tlwg-garuda fonts-tlwg-kinnari fonts-tlwg-loma fonts-tlwg-mono fonts-tlwg-norasi fonts-tlwg-purisa fonts-tlwg-sawasdee fonts-tlwg-typewriter
  fonts-tlwg-typist fonts-tlwg-typo fonts-tlwg-umpush fonts-tlwg-waree foomatic-db-compressed-ppds gcc gcc-4.8 gconf-service gconf-service-backend
  gconf2 gconf2-common gcr gdb gdisk gdm gedit gedit-common genisoimage geoclue gettext ghostscript ghostscript-x gir1.2-accountsservice-1.0
  gir1.2-atspi-2.0 gir1.2-caribou-1.0 gir1.2-clutter-1.0 gir1.2-clutter-gst-2.0 gir1.2-cogl-1.0 gir1.2-coglpango-1.0 gir1.2-dbusmenu-glib-0.4
  gir1.2-dee-1.0 gir1.2-evince-3.0 gir1.2-gck-1 gir1.2-gcr-3 gir1.2-gdata-0.0 gir1.2-gdesktopenums-3.0 gir1.2-gdm-1.0 gir1.2-gkbd-3.0
  gir1.2-gmenu-3.0 gir1.2-gnomebluetooth-1.0 gir1.2-gnomedesktop-3.0 gir1.2-gnomekeyring-1.0 gir1.2-goa-1.0 gir1.2-gst-plugins-base-1.0
  gir1.2-gstreamer-1.0 gir1.2-gtkclutter-1.0 gir1.2-gtksource-3.0 gir1.2-gtop-2.0 gir1.2-gudev-1.0 gir1.2-javascriptcoregtk-3.0 gir1.2-json-1.0
  gir1.2-mutter-3.0 gir1.2-networkmanager-1.0 gir1.2-nmgtk-1.0 gir1.2-notify-0.7 gir1.2-packagekitglib-1.0 gir1.2-peas-1.0 gir1.2-polkit-1.0
  gir1.2-rb-3.0 gir1.2-rest-0.7 gir1.2-secret-1 gir1.2-soup-2.4 gir1.2-syncmenu-0.1 gir1.2-telepathyglib-0.12 gir1.2-telepathylogger-0.2
  gir1.2-totem-1.0 gir1.2-totem-plparser-1.0 gir1.2-tracker-0.16 gir1.2-udisks-2.0 gir1.2-unity-5.0 gir1.2-upowerglib-1.0 gir1.2-vte-2.90
  gir1.2-webkit-3.0 gir1.2-wnck-3.0 gir1.2-xkl-1.0 gir1.2-zpj-0.0 gjs gkbd-capplet gnome-accessibility-themes gnome-backgrounds gnome-bluetooth
  gnome-calculator gnome-color-manager gnome-contacts gnome-control-center gnome-control-center-data gnome-control-center-shared-data
  gnome-disk-utility gnome-documents gnome-font-viewer gnome-icon-theme-extras gnome-icon-theme-full gnome-icon-theme-symbolic gnome-keyring
  gnome-mahjongg gnome-menus gnome-mines gnome-online-accounts gnome-online-miners gnome-orca gnome-screenshot gnome-session-canberra gnome-shell
  gnome-shell-common gnome-shell-extensions gnome-sudoku gnome-sushi gnome-system-log gnome-system-monitor gnome-terminal gnome-terminal-data
  gnome-themes-standard gnome-themes-standard-data gnome-tweak-tool gnome-user-guide gnome-user-share gnome-video-effects growisofs
  gsettings-ubuntu-schemas gsfonts gstreamer0.10-alsa gstreamer0.10-nice gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-x
  gstreamer1.0-alsa gstreamer1.0-clutter gstreamer1.0-nice gstreamer1.0-pulseaudio gtk2-engines-pixbuf gucharmap guile-2.0-libs gvfs gvfs-backends
  gvfs-backends-goa gvfs-bin gvfs-common gvfs-daemons gvfs-fuse gvfs-libs hardening-includes hplip hplip-data ibus-pinyin ibus-table
  indicator-application indicator-sync inputattach intel-gpu-tools intltool-debian iproute iputils-arping itstool kerneloops-daemon
  libaccount-plugin-1.0-0 libaccount-plugin-generic-oauth libaccount-plugin-google libaccounts-glib0 libaccounts-qt5-1 libappindicator3-1
  libapt-pkg-perl libarchive-zip-perl libarchive13 libart-2.0-2 libasan0 libasprintf-dev libassuan0 libatasmart4 libatk-adaptor libatkmm-1.6-1
  libatomic1 libauthen-sasl-perl libautodie-perl libavahi-core7 libavahi-glib1 libavahi-gobject0 libbluetooth3 libboost-date-time1.54.0
  libboost-system1.54.0 libbrasero-media3-1 libbrlapi0.6 libburn4 libc-dev-bin libc6-dbg libc6-dev libcairomm-1.0-1 libcamel-1.2-45
  libcanberra-gtk-module libcanberra-gtk0 libcanberra-pulse libcaribou-common libcaribou0 libcdio-cdda1 libcdio-paranoia1 libcdio13 libcdr-0.0-0
  libcheese-gtk23 libcheese7 libclone-perl libcloog-isl4 libclucene-contribs1 libclucene-core1 libclutter-1.0-0 libclutter-1.0-common
  libclutter-gst-2.0-0 libclutter-gtk-1.0-0 libcmis-0.4-4 libcogl-common libcogl-pango15 libcogl15 libcolamd2.8.0 libcolord-gtk1 libcrack2
  libcrypt-passwdmd5-perl libcupscgi1 libcupsfilters1 libcupsimage2 libcupsmime1 libcupsppdc1 libcurl3 libdaemon0 libdbusmenu-glib4
  libdbusmenu-gtk3-4 libdbusmenu-gtk4 libdee-1.0-4 libdigest-hmac-perl libdjvulibre-text libdjvulibre21 libdmapsharing-3.0-2 libdotconf0
  libdpkg-perl libebackend-1.2-7 libebook-1.2-14 libebook-contacts-1.2-0 libecal-1.2-16 libedata-book-1.2-20 libedata-cal-1.2-23
  libedataserver-1.2-18 libegl1-mesa libegl1-mesa-drivers libelfg0 libemail-valid-perl libenca0 libencode-locale-perl liberror-perl libespeak1
  libevdocument3-4 libevent-2.0-5 libevolution libevview3-3 libexempi3 libexiv2-12 libexttextcat-2.0-0 libexttextcat-data libfarstream-0.1-0
  libfarstream-0.2-2 libfile-basedir-perl libfile-copy-recursive-perl libfile-desktopentry-perl libfile-fcntllock-perl libfile-listing-perl
  libfile-mimeinfo-perl libfolks-eds25 libfolks-telepathy25 libfolks25 libfont-afm-perl libfontembed1 libfontenc1 libframe6 libfs6 libgail-3-0
  libgail-common libgail18 libgbm1 libgc1c2 libgcc-4.8-dev libgconf-2-4 libgcr-ui-3-1 libgdata-common libgdata13 libgdm1 libgee-0.8-2 libgeis1
  libgettextpo-dev libgettextpo0 libgexiv2-2 libgif4 libgjs0e libglamor0 libgles2-mesa libglib2.0-bin libglibmm-2.4-1c2a libgmime-2.6-0 libgmp10
  libgnome-bluetooth11 libgnome-control-center1 libgnome-keyring-common libgnome-keyring0 libgnome-menu-3-0 libgnomekbd-common libgnomekbd8
  libgoa-1.0-0b libgoa-1.0-common libgoa-backend-1.0-1 libgpgme11 libgpod-common libgpod4 libgrail6 libgrilo-0.2-1 libgrip0 libgs9 libgs9-common
  libgsf-1-114 libgsf-1-common libgssdp-1.0-3 libgtkhtml-4.0-0 libgtkhtml-4.0-common libgtkhtml-editor-4.0-0 libgtkmm-3.0-1 libgtksourceview-3.0-1
  libgtksourceview-3.0-common libgtop2-7 libgtop2-common libgucharmap-2-90-7 libgupnp-1.0-4 libgupnp-igd-1.0-4 libgutenprint2 libgweather-3-6
  libgweather-common libgxps2 libhdb9-heimdal libhpmud0 libhtml-form-perl libhtml-format-perl libhtml-parser-perl libhtml-tagset-perl
  libhtml-tree-perl libhttp-cookies-perl libhttp-daemon-perl libhttp-date-perl libhttp-message-perl libhttp-negotiate-perl libhyphen0 libical1
  libicc2 libido3-0.1-0 libijs-0.35 libimdi0 libindicator3-7 libio-html-perl libio-pty-perl libio-socket-inet6-perl libio-socket-ssl-perl
  libipc-run-perl libipc-system-simple-perl libiptcdata0 libisl10 libisofs6 libitm1 libiw30 libjbig2dec0 libjte1 libkpathsea6 liblangtag-common
  liblangtag1 libldb1 liblircclient0 liblist-moreutils-perl liblouis-data liblouis2 liblua5.2-0 liblwp-mediatypes-perl liblwp-protocol-https-perl
  liblzo2-2 libmail-spf-perl libmailtools-perl libmbim-glib0 libmeanwhile1 libmessaging-menu0 libmhash2 libminiupnpc8 libmission-control-plugins0
  libmm-glib0 libmnl0 libmozjs-24-0 libmpc3 libmpfr4 libmspub-0.0-0 libmtdev1 libmtp-common libmtp-runtime libmtp9 libmusicbrainz5-0 libmutter0c
  libmythes-1.2-0 libnatpmp1 libnautilus-extension1a libneon27-gnutls libnet-dns-perl libnet-domain-tld-perl libnet-http-perl libnet-ip-perl
  libnet-libidn-perl libnet-smtp-ssl-perl libnet-ssleay-perl libnetaddr-ip-perl libnetfilter-conntrack3 libnettle4 libnice10 libnl-route-3-200
  libnm-glib-vpn1 libnm-glib4 libnm-gtk-common libnm-gtk0 libnm-util2 libnotify-bin libnspr4 libnss-mdns libnss-myhostname libnss3 libnss3-nssdb
  libntdb1 liboauth0 libopencc1 libopenobex1 libopenvg1-mesa liborcus-0.6-0 libp11-kit-gnome-keyring libpackagekit-glib2-16 libpam-gnome-keyring
  libpango1.0-0 libpangomm-1.4-1 libpangox-1.0-0 libpaper-utils libpaper1 libpcsclite1 libpeas-1.0-0 libpeas-common libperl5.18 libperlio-gzip-perl
  libpoppler-glib8 libpoppler44 libportaudio2 libproxy1-plugin-gsettings libproxy1-plugin-networkmanager libpst4 libpurple-bin libpurple0
  libpwquality-common libpwquality1 libpython2.7 libpython3.4 libpyzy-1.0-0 libqmi-glib0 libqpdf13 libqt5core5a libqt5dbus5 libqt5gui5
  libqt5network5 libqt5opengl5 libqt5positioning5 libqt5printsupport5 libqt5qml5 libqt5quick5 libqt5sensors5 libqt5sql5 libqt5sql5-sqlite
  libqt5test5 libqt5webkit5 libqt5widgets5 libqt5xml5 libquadmath0 libraptor2-0 librasqal3 libraw9 librdf0 libreadline5
  libreoffice-avmedia-backend-gstreamer libreoffice-base-core libreoffice-calc libreoffice-common libreoffice-core libreoffice-draw
  libreoffice-gnome libreoffice-gtk libreoffice-impress libreoffice-math libreoffice-ogltrans libreoffice-pdfimport
  libreoffice-presentation-minimizer libreoffice-style-galaxy libreoffice-style-human libreoffice-style-tango libreoffice-writer librest-0.7-0
  librhythmbox-core8 librsync1 libsane-hpaio libsbc1 libsensors4 libsgutils2-2 libsignon-extension1 libsignon-glib1 libsignon-plugins-common1
  libsignon-qt5-1 libsmbclient libsnmp-base libsnmp30 libsocket6-perl libsonic0 libsoup-gnome2.4-1 libspectre1 libspeechd2 libstartup-notification0
  libsub-identify-perl libsync-menu1 libsys-hostname-long-perl libt1-5 libtalloc2 libtcl8.6 libtelepathy-farstream3 libtelepathy-glib0
  libtelepathy-logger3 libtevent0 libtext-levenshtein-perl libtimezonemap1 libtk8.6 libtotem-plparser18 libtotem0 libtracker-extract-0.16-0
  libtracker-miner-0.16-0 libtracker-sparql-0.16-0 libudisks2-0 libunistring0 libunity-control-center1 libunity-protocol-private0
  libunity-scopes-json-def-desktop libunity9 liburi-perl libutempter0 libvisio-0.0-0 libvte-2.90-9 libvte-2.90-common libwayland-egl1-mesa
  libwayland-server0 libwbclient0 libwebpmux1 libwhoopsie0 libwmf0.2-7 libwmf0.2-7-gtk libwnck-3-0 libwnck-3-common libwpd-0.9-9 libwpg-0.2-2
  libwps-0.2-2 libwww-perl libwww-robotrules-perl libxatracker2 libxaw7 libxcb-icccm4 libxcb-image0 libxcb-keysyms1 libxcb-randr0
  libxcb-render-util0 libxcb-shape0 libxcb-util0 libxcb-xf86dri0 libxcb-xfixes0 libxcb-xkb1 libxcb-xv0 libxfont1 libxklavier16 libxml2-utils libxmu6
  libxp6 libxres1 libxss1 libxvmc1 libxxf86dga1 libyajl2 libyelp0 libytnef0 libzapojit-0.0-0 libzeitgeist-1.0-1 libzeitgeist-2.0-0 libzephyr4
  lintian linux-libc-dev linux-sound-base lp-solve make manpages-dev mcp-account-manager-goa mcp-account-manager-uoa media-player-info memtest86+
  mobile-broadband-provider-info modemmanager mousetweaks mscompress mtools mutter mutter-common nautilus nautilus-sendto nautilus-sendto-empathy
  nautilus-share network-manager network-manager-gnome network-manager-pptp network-manager-pptp-gnome obex-data-server obexd-client oneconf
  oneconf-common openprinting-ppds p11-kit p11-kit-modules patch patchutils pcmciautils plymouth-label plymouth-theme-ubuntu-gnome-logo
  plymouth-theme-ubuntu-gnome-text policykit-1-gnome policykit-desktop-privileges poppler-data poppler-utils pptp-linux printer-driver-c2esp
  printer-driver-foo2zjs printer-driver-foo2zjs-common printer-driver-gutenprint printer-driver-hpcups printer-driver-min12xxw
  printer-driver-pnm2ppa printer-driver-postscript-hp printer-driver-ptouch printer-driver-pxljr printer-driver-sag-gdi printer-driver-splix
  pulseaudio-module-bluetooth python-aptdaemon python-aptdaemon.gtk3widgets python-boto python-cloudfiles python-commandnotfound python-configglue
  python-crypto python-cups python-cupshelpers python-dbus python-dbus-dev python-debtagshw python-defer python-dirspec python-gdbm python-gi-cairo
  python-gnomekeyring python-gobject python-httplib2 python-ibus python-imaging python-ldb python-libxml2 python-lockfile python-lxml python-ntdb
  python-oauthlib python-oneconf python-openssl python-pam python-pexpect python-pil python-piston-mini-client python-pkg-resources python-protobuf
  python-pycurl python-pyinotify python-renderpm python-reportlab python-reportlab-accel python-requests python-samba python-serial python-smbc
  python-talloc python-tdb python-twisted-bin python-twisted-core python-twisted-names python-twisted-web python-ubuntu-sso-client
  python-ubuntuone-client python-ubuntuone-control-panel python-ubuntuone-storageprotocol python-urllib3 python-xdg python-zeitgeist
  python-zope.interface python3-apport python3-aptdaemon python3-aptdaemon.gtk3widgets python3-aptdaemon.pkcompat python3-brlapi python3-cairo
  python3-chardet python3-crypto python3-debian python3-defer python3-dirspec python3-gi-cairo python3-httplib2 python3-louis python3-mako
  python3-markupsafe python3-oauthlib python3-oneconf python3-piston-mini-client python3-pkg-resources python3-problem-report python3-pyatspi
  python3-pycurl python3-six python3-software-properties python3-speechd python3-uno python3-xdg python3-xkit qpdf re2c rfkill rhythmbox
  rhythmbox-data rhythmbox-mozilla rhythmbox-plugin-cdrecorder rhythmbox-plugin-magnatune rhythmbox-plugin-zeitgeist rhythmbox-plugins
  rhythmbox-ubuntuone sa-compile samba-common samba-common-bin samba-libs sane-utils seahorse sessioninstaller shotwell shotwell-common
  signon-keyring-extension signon-plugin-oauth2 signon-plugin-password signon-ui signond simple-scan smbclient software-center
  software-center-aptdaemon-plugins software-properties-common software-properties-gtk spamassassin spamc speech-dispatcher
  speech-dispatcher-audio-plugins ssh-askpass-gnome ssl-cert syslinux syslinux-common syslinux-legacy system-config-printer-common
  system-config-printer-gnome system-config-printer-udev t1utils tcl tcl8.6 telepathy-gabble telepathy-haze telepathy-idle telepathy-logger
  telepathy-mission-control-5 telepathy-salut tk tk8.6 toshset totem totem-common totem-plugins tracker tracker-extract tracker-miner-fs
  tracker-utils transmission-common transmission-gtk ttf-indic-fonts-core ttf-punjabi-fonts ttf-ubuntu-font-family ubuntu-drivers-common
  ubuntu-extras-keyring ubuntu-gnome-default-settings ubuntu-release-upgrader-gtk ubuntu-sso-client ubuntu-system-service ubuntuone-client
  ubuntuone-client-data ubuntuone-control-panel udisks2 unattended-upgrades unity-asset-pool unity-control-center unity-control-center-signon
  unity-settings-daemon uno-libs3 unoconv unzip update-inetd update-manager update-notifier update-notifier-common ure usb-creator-common
  usb-creator-gtk usb-modeswitch usb-modeswitch-data vino wamerican whoopsie wireless-tools wodim wpasupplicant x11-apps x11-session-utils x11-utils
  x11-xfs-utils x11-xkb-utils x11-xserver-utils xbitmaps xdg-user-dirs xdg-user-dirs-gtk xdg-utils xdiagnose xfonts-base xfonts-encodings
  xfonts-mathml xfonts-scalable xfonts-utils xinit xinput xorg xorg-docs-core xserver-common xserver-xephyr xserver-xorg xserver-xorg-core
  xserver-xorg-input-all xserver-xorg-input-evdev xserver-xorg-input-mouse xserver-xorg-input-synaptics xserver-xorg-input-vmmouse
  xserver-xorg-input-wacom xserver-xorg-video-all xserver-xorg-video-ati xserver-xorg-video-cirrus xserver-xorg-video-fbdev
  xserver-xorg-video-glamoregl xserver-xorg-video-intel xserver-xorg-video-mach64 xserver-xorg-video-mga xserver-xorg-video-modesetting
  xserver-xorg-video-neomagic xserver-xorg-video-nouveau xserver-xorg-video-openchrome xserver-xorg-video-qxl xserver-xorg-video-r128
  xserver-xorg-video-radeon xserver-xorg-video-s3 xserver-xorg-video-savage xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident xserver-xorg-video-vesa xserver-xorg-video-vmware xsltproc xterm
  xul-ext-ubufox yelp yelp-tools yelp-xsl zeitgeist zeitgeist-core zeitgeist-datahub zip zsync
Suggested packages:
  gnome-cards-data apmd alsa-oss oss-compat default-mta mail-transport-agent libgtk2-perl gir1.2-colordgtk-1.0 binutils-doc bluez-hcidump vcdimager
  libdvdcss2 dvdauthor readom brltty-speechd brltty-x11 console-braille gnome-video-effects-frei0r gnome-video-effects-extra cpp-doc gcc-4.8-locales
  cups-pdf xpp python-paramiko ncftp lftp python-gdata tahoe-lafs python-swiftclient cdrskin unrar evolution-ews evolution-plugins-experimental
  evolution-data-server-dbg arj lha lzip lzop ncompress p7zip-full rpm2cpio rzip sharutils unace unalz unar zoo ttf-lyx libgraphite3 pango-graphite
  hplip-cups printer-driver-all gcc-multilib autoconf automake1.9 libtool flex bison gcc-doc gcc-4.8-multilib gcc-4.8-doc libgcc1-dbg libgomp1-dbg
  libitm1-dbg libatomic1-dbg libasan0-dbg libtsan0-dbg libbacktrace1-dbg libquadmath0-dbg binutils-gold gconf-defaults-service gdb-doc gdbserver
  gedit-plugins cdrkit-doc gettext-doc hpijs gnome-screensaver xscreensaver gstreamer1.0-libav apache2.2-bin libapache2-mod-dnssd hplip-gui
  hplip-doc system-config-printer lrzip libgssapi-perl gstreamer1.0-plugins-ugly cdrdao gstreamer1.0-fluendo-mp3 gstreamer1.0-plugins-bad glibc-doc
  debian-keyring exiv2 gpgsm grilo-plugins-0.2 gutenprint-locales libdata-dump-perl lirc libcrypt-ssleay-perl minissdpd natpmp-utils pcscd
  raptor2-utils rasqal-utils librdf-storage-postgresql librdf-storage-mysql librdf-storage-sqlite librdf-storage-virtuoso redland-utils
  libreoffice-base libopencl1 libreoffice-style-crystal libreoffice-style-hicontrast libreoffice-style-oxygen libreoffice-style-sifr
  libreoffice-evolution crystalcursors kde-icons-crystal tango-icon-theme libreoffice-gcj libreoffice-java-common default-jre gcj-jre openjdk-7-jre
  openjdk-6-jre sun-java5-jre sun-java6-jre java5-runtime jre lm-sensors sg3-utils snmp-mibs-downloader libspectre1-dbg unity-common
  libauthen-ntlm-perl binutils-multiarch dpkg-dev libtext-template-perl libyaml-perl make-doc account-plugin-gadugadu account-plugin-groupwise
  account-plugin-icq account-plugin-irc account-plugin-mxit account-plugin-myspace account-plugin-sametime account-plugin-sip account-plugin-yahoojp
  account-plugin-zephyr hwtools memtester kernel-patch-badram memtest86 floppyd pidgin gajim samba network-manager-openconnect-gnome
  network-manager-openvpn-gnome network-manager-vpnc-gnome hpijs-ppds diffutils-doc fonts-japanese-mincho fonts-ipafont-mincho fonts-japanese-gothic
  fonts-ipafont-gothic fonts-arphic-ukai fonts-arphic-uming fonts-unfonts-core psutils hannah-foo2zjs tix gutenprint-doc magicfilter apsfilter
  python-crypto-dbg python-crypto-doc python-dbus-doc python-dbus-dbg python-gdbm-dbg python-lxml-dbg python-openssl-doc python-openssl-dbg
  python-pam-dbg python-pexpect-doc python-pil-doc python-pil-dbg python-distribute python-distribute-doc libcurl4-gnutls-dev python-pycurl-dbg
  python-pyinotify-doc python-renderpm-dbg pdf-viewer python-egenix-mxtexttools python-reportlab-doc python-wxgtk2.8 python-wxgtk
  python-twisted-bin-dbg python-tk python-glade2 python-qt3 python3-launchpadlib python3-crypto-dbg python3-beaker python-mako-doc
  python3-setuptools python3-pycurl-dbg gnome-codec-install heimdal-clients unpaper account-plugin-flickr cifs-utils razor libdbi-perl pyzor
  libmail-dkim-perl libttspico-utils speech-dispatcher-doc-cs speech-dispatcher-festival speech-dispatcher-flite openssl-blacklist tcl-tclreadline
  totem-mozilla gromit tracker-gui ubuntu-sso-client-gui ubuntuone-client-proxy ubuntuone-control-panel-gui xfsprogs reiserfsprogs exfat-utils
  btrfs-tools mdadm cryptsetup-bin bsd-mailx metacity x-window-manager comgt wvdial vinagre wpagui libengine-pkcs11-openssl mesa-utils nickle
  cairo-5c xfs xserver fonts-lyx fonts-stix xorg-docs xfonts-100dpi xfonts-75dpi gpointing-device-settings touchfreeze firmware-linux
  xfonts-cyrillic
Recommended packages:
  libc-dbg ubuntu-control-center-signon
The following NEW packages will be installed:
  account-plugin-aim account-plugin-facebook account-plugin-google account-plugin-jabber account-plugin-salut account-plugin-windows-live
  account-plugin-yahoo acpi-support acpid aisleriot alsa-base alsa-utils anacron apg app-install-data app-install-data-partner apport apport-gtk
  apport-symptoms aptdaemon aptdaemon-data apturl apturl-common argyll avahi-autoipd avahi-daemon avahi-utils baobab bc binutils bluez bluez-alsa
  bluez-cups bluez-gstreamer brasero brasero-cdrkit brasero-common brltty cheese cheese-common cpp cpp-4.8 cracklib-runtime cups cups-browsed
  cups-bsd cups-client cups-common cups-core-drivers cups-daemon cups-filters cups-filters-core-drivers cups-pk-helper cups-ppdc cups-server-common
  dc dconf-editor deja-dup deja-dup-backend-cloudfiles deja-dup-backend-gvfs deja-dup-backend-s3 deja-dup-backend-ubuntuone desktop-file-utils
  diffstat dnsmasq-base duplicity dvd+rw-tools empathy empathy-common eog espeak-data evince evince-common evolution evolution-common
  evolution-data-server evolution-data-server-common evolution-data-server-online-accounts evolution-indicator evolution-plugins file-roller firefox
  folks-common fonts-cantarell fonts-droid fonts-freefont-ttf fonts-kacst fonts-kacst-one fonts-khmeros-core fonts-lao fonts-liberation
  fonts-lklug-sinhala fonts-nanum fonts-opensymbol fonts-sil-abyssinica fonts-sil-padauk fonts-takao-pgothic fonts-thai-tlwg fonts-tibetan-machine
  fonts-tlwg-garuda fonts-tlwg-kinnari fonts-tlwg-loma fonts-tlwg-mono fonts-tlwg-norasi fonts-tlwg-purisa fonts-tlwg-sawasdee fonts-tlwg-typewriter
  fonts-tlwg-typist fonts-tlwg-typo fonts-tlwg-umpush fonts-tlwg-waree foomatic-db-compressed-ppds gcc gcc-4.8 gconf-service gconf-service-backend
  gconf2 gconf2-common gcr gdb gdisk gdm gedit gedit-common genisoimage geoclue gettext ghostscript ghostscript-x gir1.2-accountsservice-1.0
  gir1.2-atspi-2.0 gir1.2-caribou-1.0 gir1.2-clutter-1.0 gir1.2-clutter-gst-2.0 gir1.2-cogl-1.0 gir1.2-coglpango-1.0 gir1.2-dbusmenu-glib-0.4
  gir1.2-dee-1.0 gir1.2-evince-3.0 gir1.2-gck-1 gir1.2-gcr-3 gir1.2-gdata-0.0 gir1.2-gdesktopenums-3.0 gir1.2-gdm-1.0 gir1.2-gkbd-3.0
  gir1.2-gmenu-3.0 gir1.2-gnomebluetooth-1.0 gir1.2-gnomedesktop-3.0 gir1.2-gnomekeyring-1.0 gir1.2-goa-1.0 gir1.2-gst-plugins-base-1.0
  gir1.2-gstreamer-1.0 gir1.2-gtkclutter-1.0 gir1.2-gtksource-3.0 gir1.2-gtop-2.0 gir1.2-gudev-1.0 gir1.2-javascriptcoregtk-3.0 gir1.2-json-1.0
  gir1.2-mutter-3.0 gir1.2-networkmanager-1.0 gir1.2-nmgtk-1.0 gir1.2-notify-0.7 gir1.2-packagekitglib-1.0 gir1.2-peas-1.0 gir1.2-polkit-1.0
  gir1.2-rb-3.0 gir1.2-rest-0.7 gir1.2-secret-1 gir1.2-soup-2.4 gir1.2-syncmenu-0.1 gir1.2-telepathyglib-0.12 gir1.2-telepathylogger-0.2
  gir1.2-totem-1.0 gir1.2-totem-plparser-1.0 gir1.2-tracker-0.16 gir1.2-udisks-2.0 gir1.2-unity-5.0 gir1.2-upowerglib-1.0 gir1.2-vte-2.90
  gir1.2-webkit-3.0 gir1.2-wnck-3.0 gir1.2-xkl-1.0 gir1.2-zpj-0.0 gjs gkbd-capplet gnome-accessibility-themes gnome-backgrounds gnome-bluetooth
  gnome-calculator gnome-color-manager gnome-contacts gnome-control-center gnome-control-center-data gnome-control-center-shared-data
  gnome-disk-utility gnome-documents gnome-font-viewer gnome-icon-theme-extras gnome-icon-theme-full gnome-icon-theme-symbolic gnome-keyring
  gnome-mahjongg gnome-menus gnome-mines gnome-online-accounts gnome-online-miners gnome-orca gnome-screenshot gnome-session-canberra gnome-shell
  gnome-shell-common gnome-shell-extensions gnome-sudoku gnome-sushi gnome-system-log gnome-system-monitor gnome-terminal gnome-terminal-data
  gnome-themes-standard gnome-themes-standard-data gnome-tweak-tool gnome-user-guide gnome-user-share gnome-video-effects growisofs
  gsettings-ubuntu-schemas gsfonts gstreamer0.10-alsa gstreamer0.10-nice gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-x
  gstreamer1.0-alsa gstreamer1.0-clutter gstreamer1.0-nice gstreamer1.0-pulseaudio gtk2-engines-pixbuf gucharmap guile-2.0-libs gvfs gvfs-backends
  gvfs-backends-goa gvfs-bin gvfs-common gvfs-daemons gvfs-fuse gvfs-libs hardening-includes hplip hplip-data ibus-pinyin ibus-table
  indicator-application indicator-sync inputattach intel-gpu-tools intltool-debian iproute iputils-arping itstool kerneloops-daemon
  libaccount-plugin-1.0-0 libaccount-plugin-generic-oauth libaccount-plugin-google libaccounts-glib0 libaccounts-qt5-1 libappindicator3-1
  libapt-pkg-perl libarchive-zip-perl libarchive13 libart-2.0-2 libasan0 libasprintf-dev libassuan0 libatasmart4 libatk-adaptor libatkmm-1.6-1
  libatomic1 libauthen-sasl-perl libautodie-perl libavahi-core7 libavahi-glib1 libavahi-gobject0 libbluetooth3 libboost-date-time1.54.0
  libboost-system1.54.0 libbrasero-media3-1 libbrlapi0.6 libburn4 libc-dev-bin libc6-dbg libc6-dev libcairomm-1.0-1 libcamel-1.2-45
  libcanberra-gtk-module libcanberra-gtk0 libcanberra-pulse libcaribou-common libcaribou0 libcdio-cdda1 libcdio-paranoia1 libcdio13 libcdr-0.0-0
  libcheese-gtk23 libcheese7 libclone-perl libcloog-isl4 libclucene-contribs1 libclucene-core1 libclutter-1.0-0 libclutter-1.0-common
  libclutter-gst-2.0-0 libclutter-gtk-1.0-0 libcmis-0.4-4 libcogl-common libcogl-pango15 libcogl15 libcolamd2.8.0 libcolord-gtk1 libcrack2
  libcrypt-passwdmd5-perl libcupscgi1 libcupsfilters1 libcupsimage2 libcupsmime1 libcupsppdc1 libcurl3 libdaemon0 libdbusmenu-glib4
  libdbusmenu-gtk3-4 libdbusmenu-gtk4 libdee-1.0-4 libdigest-hmac-perl libdjvulibre-text libdjvulibre21 libdmapsharing-3.0-2 libdotconf0
  libdpkg-perl libebackend-1.2-7 libebook-1.2-14 libebook-contacts-1.2-0 libecal-1.2-16 libedata-book-1.2-20 libedata-cal-1.2-23
  libedataserver-1.2-18 libegl1-mesa libegl1-mesa-drivers libelfg0 libemail-valid-perl libenca0 libencode-locale-perl liberror-perl libespeak1
  libevdocument3-4 libevent-2.0-5 libevolution libevview3-3 libexempi3 libexiv2-12 libexttextcat-2.0-0 libexttextcat-data libfarstream-0.1-0
  libfarstream-0.2-2 libfile-basedir-perl libfile-copy-recursive-perl libfile-desktopentry-perl libfile-fcntllock-perl libfile-listing-perl
  libfile-mimeinfo-perl libfolks-eds25 libfolks-telepathy25 libfolks25 libfont-afm-perl libfontembed1 libfontenc1 libframe6 libfs6 libgail-3-0
  libgail-common libgail18 libgbm1 libgc1c2 libgcc-4.8-dev libgconf-2-4 libgcr-ui-3-1 libgdata-common libgdata13 libgdm1 libgee-0.8-2 libgeis1
  libgettextpo-dev libgettextpo0 libgexiv2-2 libgif4 libgjs0e libglamor0 libgles2-mesa libglib2.0-bin libglibmm-2.4-1c2a libgmime-2.6-0 libgmp10
  libgnome-bluetooth11 libgnome-control-center1 libgnome-keyring-common libgnome-keyring0 libgnome-menu-3-0 libgnomekbd-common libgnomekbd8
  libgoa-1.0-0b libgoa-1.0-common libgoa-backend-1.0-1 libgpgme11 libgpod-common libgpod4 libgrail6 libgrilo-0.2-1 libgrip0 libgs9 libgs9-common
  libgsf-1-114 libgsf-1-common libgssdp-1.0-3 libgtkhtml-4.0-0 libgtkhtml-4.0-common libgtkhtml-editor-4.0-0 libgtkmm-3.0-1 libgtksourceview-3.0-1
  libgtksourceview-3.0-common libgtop2-7 libgtop2-common libgucharmap-2-90-7 libgupnp-1.0-4 libgupnp-igd-1.0-4 libgutenprint2 libgweather-3-6
  libgweather-common libgxps2 libhdb9-heimdal libhpmud0 libhtml-form-perl libhtml-format-perl libhtml-parser-perl libhtml-tagset-perl
  libhtml-tree-perl libhttp-cookies-perl libhttp-daemon-perl libhttp-date-perl libhttp-message-perl libhttp-negotiate-perl libhyphen0 libical1
  libicc2 libido3-0.1-0 libijs-0.35 libimdi0 libindicator3-7 libio-html-perl libio-pty-perl libio-socket-inet6-perl libio-socket-ssl-perl
  libipc-run-perl libipc-system-simple-perl libiptcdata0 libisl10 libisofs6 libitm1 libiw30 libjbig2dec0 libjte1 libkpathsea6 liblangtag-common
  liblangtag1 libldb1 liblircclient0 liblist-moreutils-perl liblouis-data liblouis2 liblua5.2-0 liblwp-mediatypes-perl liblwp-protocol-https-perl
  liblzo2-2 libmail-spf-perl libmailtools-perl libmbim-glib0 libmeanwhile1 libmessaging-menu0 libmhash2 libminiupnpc8 libmission-control-plugins0
  libmm-glib0 libmnl0 libmozjs-24-0 libmpc3 libmpfr4 libmspub-0.0-0 libmtdev1 libmtp-common libmtp-runtime libmtp9 libmusicbrainz5-0 libmutter0c
  libmythes-1.2-0 libnatpmp1 libnautilus-extension1a libneon27-gnutls libnet-dns-perl libnet-domain-tld-perl libnet-http-perl libnet-ip-perl
  libnet-libidn-perl libnet-smtp-ssl-perl libnet-ssleay-perl libnetaddr-ip-perl libnetfilter-conntrack3 libnettle4 libnice10 libnl-route-3-200
  libnm-glib-vpn1 libnm-glib4 libnm-gtk-common libnm-gtk0 libnm-util2 libnotify-bin libnspr4 libnss-mdns libnss-myhostname libnss3 libnss3-nssdb
  libntdb1 liboauth0 libopencc1 libopenobex1 libopenvg1-mesa liborcus-0.6-0 libp11-kit-gnome-keyring libpackagekit-glib2-16 libpam-gnome-keyring
  libpango1.0-0 libpangomm-1.4-1 libpangox-1.0-0 libpaper-utils libpaper1 libpcsclite1 libpeas-1.0-0 libpeas-common libperl5.18 libperlio-gzip-perl
  libpoppler-glib8 libpoppler44 libportaudio2 libproxy1-plugin-gsettings libproxy1-plugin-networkmanager libpst4 libpurple-bin libpurple0
  libpwquality-common libpwquality1 libpython2.7 libpython3.4 libpyzy-1.0-0 libqmi-glib0 libqpdf13 libqt5core5a libqt5dbus5 libqt5gui5
  libqt5network5 libqt5opengl5 libqt5positioning5 libqt5printsupport5 libqt5qml5 libqt5quick5 libqt5sensors5 libqt5sql5 libqt5sql5-sqlite
  libqt5test5 libqt5webkit5 libqt5widgets5 libqt5xml5 libquadmath0 libraptor2-0 librasqal3 libraw9 librdf0 libreadline5
  libreoffice-avmedia-backend-gstreamer libreoffice-base-core libreoffice-calc libreoffice-common libreoffice-core libreoffice-draw
  libreoffice-gnome libreoffice-gtk libreoffice-impress libreoffice-math libreoffice-ogltrans libreoffice-pdfimport
  libreoffice-presentation-minimizer libreoffice-style-galaxy libreoffice-style-human libreoffice-style-tango libreoffice-writer librest-0.7-0
  librhythmbox-core8 librsync1 libsane-hpaio libsbc1 libsensors4 libsgutils2-2 libsignon-extension1 libsignon-glib1 libsignon-plugins-common1
  libsignon-qt5-1 libsmbclient libsnmp-base libsnmp30 libsocket6-perl libsonic0 libsoup-gnome2.4-1 libspectre1 libspeechd2 libstartup-notification0
  libsub-identify-perl libsync-menu1 libsys-hostname-long-perl libt1-5 libtalloc2 libtcl8.6 libtelepathy-farstream3 libtelepathy-glib0
  libtelepathy-logger3 libtevent0 libtext-levenshtein-perl libtimezonemap1 libtk8.6 libtotem-plparser18 libtotem0 libtracker-extract-0.16-0
  libtracker-miner-0.16-0 libtracker-sparql-0.16-0 libudisks2-0 libunistring0 libunity-control-center1 libunity-protocol-private0
  libunity-scopes-json-def-desktop libunity9 liburi-perl libutempter0 libvisio-0.0-0 libvte-2.90-9 libvte-2.90-common libwayland-egl1-mesa
  libwayland-server0 libwbclient0 libwebpmux1 libwhoopsie0 libwmf0.2-7 libwmf0.2-7-gtk libwnck-3-0 libwnck-3-common libwpd-0.9-9 libwpg-0.2-2
  libwps-0.2-2 libwww-perl libwww-robotrules-perl libxatracker2 libxaw7 libxcb-icccm4 libxcb-image0 libxcb-keysyms1 libxcb-randr0
  libxcb-render-util0 libxcb-shape0 libxcb-util0 libxcb-xf86dri0 libxcb-xfixes0 libxcb-xkb1 libxcb-xv0 libxfont1 libxklavier16 libxml2-utils libxmu6
  libxp6 libxres1 libxss1 libxvmc1 libxxf86dga1 libyajl2 libyelp0 libytnef0 libzapojit-0.0-0 libzeitgeist-1.0-1 libzeitgeist-2.0-0 libzephyr4
  lintian linux-libc-dev linux-sound-base lp-solve make manpages-dev mcp-account-manager-goa mcp-account-manager-uoa media-player-info memtest86+
  mobile-broadband-provider-info modemmanager mousetweaks mscompress mtools mutter mutter-common nautilus nautilus-sendto nautilus-sendto-empathy
  nautilus-share network-manager network-manager-gnome network-manager-pptp network-manager-pptp-gnome obex-data-server obexd-client oneconf
  oneconf-common openprinting-ppds p11-kit p11-kit-modules patch patchutils pcmciautils plymouth-label plymouth-theme-ubuntu-gnome-logo
  plymouth-theme-ubuntu-gnome-text policykit-1-gnome policykit-desktop-privileges poppler-data poppler-utils pptp-linux printer-driver-c2esp
  printer-driver-foo2zjs printer-driver-foo2zjs-common printer-driver-gutenprint printer-driver-hpcups printer-driver-min12xxw
  printer-driver-pnm2ppa printer-driver-postscript-hp printer-driver-ptouch printer-driver-pxljr printer-driver-sag-gdi printer-driver-splix
  pulseaudio-module-bluetooth python-aptdaemon python-aptdaemon.gtk3widgets python-boto python-cloudfiles python-commandnotfound python-configglue
  python-crypto python-cups python-cupshelpers python-dbus python-dbus-dev python-debtagshw python-defer python-dirspec python-gdbm python-gi-cairo
  python-gnomekeyring python-gobject python-httplib2 python-ibus python-imaging python-ldb python-libxml2 python-lockfile python-lxml python-ntdb
  python-oauthlib python-oneconf python-openssl python-pam python-pexpect python-pil python-piston-mini-client python-pkg-resources python-protobuf
  python-pycurl python-pyinotify python-renderpm python-reportlab python-reportlab-accel python-requests python-samba python-serial python-smbc
  python-talloc python-tdb python-twisted-bin python-twisted-core python-twisted-names python-twisted-web python-ubuntu-sso-client
  python-ubuntuone-client python-ubuntuone-control-panel python-ubuntuone-storageprotocol python-urllib3 python-xdg python-zeitgeist
  python-zope.interface python3-apport python3-aptdaemon python3-aptdaemon.gtk3widgets python3-aptdaemon.pkcompat python3-brlapi python3-cairo
  python3-chardet python3-crypto python3-debian python3-defer python3-dirspec python3-gi-cairo python3-httplib2 python3-louis python3-mako
  python3-markupsafe python3-oauthlib python3-oneconf python3-piston-mini-client python3-pkg-resources python3-problem-report python3-pyatspi
  python3-pycurl python3-six python3-software-properties python3-speechd python3-uno python3-xdg python3-xkit qpdf re2c rfkill rhythmbox
  rhythmbox-data rhythmbox-mozilla rhythmbox-plugin-cdrecorder rhythmbox-plugin-magnatune rhythmbox-plugin-zeitgeist rhythmbox-plugins
  rhythmbox-ubuntuone sa-compile samba-common samba-common-bin samba-libs sane-utils seahorse sessioninstaller shotwell shotwell-common
  signon-keyring-extension signon-plugin-oauth2 signon-plugin-password signon-ui signond simple-scan smbclient software-center
  software-center-aptdaemon-plugins software-properties-common software-properties-gtk spamassassin spamc speech-dispatcher
  speech-dispatcher-audio-plugins ssh-askpass-gnome ssl-cert syslinux syslinux-common syslinux-legacy system-config-printer-common
  system-config-printer-gnome system-config-printer-udev t1utils tcl tcl8.6 telepathy-gabble telepathy-haze telepathy-idle telepathy-logger
  telepathy-mission-control-5 telepathy-salut tk tk8.6 toshset totem totem-common totem-plugins tracker tracker-extract tracker-miner-fs
  tracker-utils transmission-common transmission-gtk ttf-indic-fonts-core ttf-punjabi-fonts ttf-ubuntu-font-family ubuntu-drivers-common
  ubuntu-extras-keyring ubuntu-gnome-default-settings ubuntu-gnome-desktop ubuntu-release-upgrader-gtk ubuntu-sso-client ubuntu-system-service
  ubuntuone-client ubuntuone-client-data ubuntuone-control-panel udisks2 unattended-upgrades unity-asset-pool unity-control-center
  unity-control-center-signon unity-settings-daemon uno-libs3 unoconv unzip update-inetd update-manager update-notifier update-notifier-common ure
  usb-creator-common usb-creator-gtk usb-modeswitch usb-modeswitch-data vino wamerican whoopsie wireless-tools wodim wpasupplicant x11-apps
  x11-session-utils x11-utils x11-xfs-utils x11-xkb-utils x11-xserver-utils xbitmaps xdg-user-dirs xdg-user-dirs-gtk xdg-utils xdiagnose xfonts-base
  xfonts-encodings xfonts-mathml xfonts-scalable xfonts-utils xinit xinput xorg xorg-docs-core xserver-common xserver-xephyr xserver-xorg
  xserver-xorg-core xserver-xorg-input-all xserver-xorg-input-evdev xserver-xorg-input-mouse xserver-xorg-input-synaptics xserver-xorg-input-vmmouse
  xserver-xorg-input-wacom xserver-xorg-video-all xserver-xorg-video-ati xserver-xorg-video-cirrus xserver-xorg-video-fbdev
  xserver-xorg-video-glamoregl xserver-xorg-video-intel xserver-xorg-video-mach64 xserver-xorg-video-mga xserver-xorg-video-modesetting
  xserver-xorg-video-neomagic xserver-xorg-video-nouveau xserver-xorg-video-openchrome xserver-xorg-video-qxl xserver-xorg-video-r128
  xserver-xorg-video-radeon xserver-xorg-video-s3 xserver-xorg-video-savage xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident xserver-xorg-video-vesa xserver-xorg-video-vmware xsltproc xterm
  xul-ext-ubufox yelp yelp-tools yelp-xsl zeitgeist zeitgeist-core zeitgeist-datahub zip zsync
0 upgraded, 1002 newly installed, 0 to remove and 11 not upgraded.
Need to get 385 MB of archives.
After this operation, 1,421 MB of additional disk space will be used.
Do you want to continue? [Y/n] n
Abort.

```

Time to do some math and parsing :)

Still the same 1235 packages so time to purge 'gnome-session'.

---

### Post by kansasnoob on 2014-04-02
Here we go:

```
root@lance-desktop:/# apt-get purge acl aspell aspell-en at-spi2-core colord dbus-x11 dconf-cli dconf-gsettings-backend dconf-service dialog dictionaries-common enchant fontconfig fontconfig-config fonts-dejavu-core gir1.2-atk-1.0 gir1.2-freedesktop gir1.2-gdkpixbuf-2.0 gir1.2-gtk-3.0 gir1.2-ibus-1.0 gir1.2-pango-1.0 glib-networking glib-networking-common glib-networking-services gnome-desktop3-data gnome-icon-theme gnome-session gnome-session-bin gnome-session-common gnome-settings-daemon gnome-settings-daemon-schemas gsettings-desktop-schemas gstreamer0.10-pulseaudio gstreamer1.0-plugins-base gstreamer1.0-plugins-good gstreamer1.0-x hicolor-icon-theme humanity-icon-theme hunspell-en-us hwdata ibus ibus-gtk ibus-gtk3 im-config libaa1 libasound2 libasound2-data libasound2-plugins libaspell15 libasyncns0 libatk-bridge2.0-0 libatk1.0-0 libatk1.0-data libatspi2.0-0 libavahi-client3 libavahi-common-data libavahi-common3 libavc1394-0 libcaca0 libcairo-gobject2 libcairo2 libcanberra-gtk3-0 libcanberra-gtk3-module libcanberra0 libcdparanoia0 libcgmanager0 libcolord1 libcolorhug1 libcroco3 libcups2 libdatrie1 libdconf1 libdrm-intel1 libdrm-nouveau2 libdrm-radeon1 libdv4 libenchant1c2a libexif12 libfftw3-single3 libflac8 libfontconfig1 libgd3 libgdk-pixbuf2.0-0 libgdk-pixbuf2.0-common libgeoclue0 libgl1-mesa-dri libgl1-mesa-glx libglapi-mesa libglu1-mesa libgnome-desktop-3-7 libgomp1 libgphoto2-6 libgphoto2-l10n libgphoto2-port10 libgpm2 libgraphite2-3 libgstreamer-plugins-base0.10-0 libgstreamer-plugins-base1.0-0 libgstreamer-plugins-good1.0-0 libgstreamer0.10-0 libgstreamer1.0-0 libgtk-3-0 libgtk-3-bin libgtk-3-common libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libgudev-1.0-0 libgusb2 libharfbuzz-icu0 libharfbuzz0b libhunspell-1.3-0 libibus-1.0-5 libice6 libicu52 libiec61883-0 libieee1284-3 libimobiledevice4 libjack-jackd2-0 libjasper1 libjavascriptcoregtk-3.0-0 libjbig0 libjpeg-turbo8 libjpeg8 libjson-glib-1.0-0 libjson-glib-1.0-common liblcms2-2 libllvm3.4 libltdl7 libnotify4 libogg0 liborc-0.4-0 libpango-1.0-0 libpangocairo-1.0-0 libpangoft2-1.0-0 libpangoxft-1.0-0 libpciaccess0 libpixman-1-0 libplist1 libpolkit-agent-1-0 libpolkit-backend-1-0 libproxy1 libpulse-mainloop-glib0 libpulse0 libpulsedsp libraw1394-11 librsvg2-2 librsvg2-common libsamplerate0 libsane libsane-common libsecret-1-0 libsecret-common libshout3 libsm6 libsndfile1 libsoup2.4-1 libspeex1 libspeexdsp1 libsystemd-journal0 libtag1-vanilla libtag1c2a libtdb1 libthai-data libthai0 libtheora0 libtiff5 libtxc-dxtn-s2tc0 libupower-glib1 libusbmuxd2 libv4l-0 libv4lconvert0 libvisual-0.4-0 libvisual-0.4-plugins libvorbis0a libvorbisenc2 libvorbisfile3 libvpx1 libwacom-common libwacom2 libwavpack1 libwayland-client0 libwayland-cursor0 libwebkitgtk-3.0-0 libwebkitgtk-3.0-common libwebp5 libwrap0 libx11-xcb1 libxcb-dri2-0 libxcb-dri3-0 libxcb-glx0 libxcb-present0 libxcb-render0 libxcb-shm0 libxcb-sync1 libxcomposite1 libxcursor1 libxdamage1 libxfixes3 libxft2 libxi6 libxinerama1 libxkbcommon0 libxkbfile1 libxpm4 libxrandr2 libxrender1 libxshmfence1 libxslt1.1 libxt6 libxtst6 libxv1 libxxf86vm1 nautilus-data notification-daemon policykit-1 pulseaudio pulseaudio-module-x11 pulseaudio-utils python-cairo python-gi python-gobject-2 python-gtk2 python-notify rtkit session-migration sound-theme-freedesktop tcpd upower usbmuxd x11-common zenity zenity-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  acl* aspell* aspell-en* at-spi2-core* colord* dbus-x11* dconf-cli* dconf-gsettings-backend* dconf-service* dialog* dictionaries-common* enchant*
  fontconfig* fontconfig-config* fonts-dejavu-core* gir1.2-atk-1.0* gir1.2-freedesktop* gir1.2-gdkpixbuf-2.0* gir1.2-gtk-3.0* gir1.2-ibus-1.0*
  gir1.2-pango-1.0* glib-networking* glib-networking-common* glib-networking-services* gnome-desktop3-data* gnome-icon-theme* gnome-session*
  gnome-session-bin* gnome-session-common* gnome-settings-daemon* gnome-settings-daemon-schemas* gsettings-desktop-schemas*
  gstreamer0.10-pulseaudio* gstreamer1.0-plugins-base* gstreamer1.0-plugins-good* gstreamer1.0-x* hicolor-icon-theme* humanity-icon-theme*
  hunspell-en-us* hwdata* ibus* ibus-gtk* ibus-gtk3* im-config* libaa1* libasound2* libasound2-data* libasound2-plugins* libaspell15* libasyncns0*
  libatk-bridge2.0-0* libatk1.0-0* libatk1.0-data* libatspi2.0-0* libavahi-client3* libavahi-common-data* libavahi-common3* libavc1394-0* libcaca0*
  libcairo-gobject2* libcairo2* libcanberra-gtk3-0* libcanberra-gtk3-module* libcanberra0* libcdparanoia0* libcgmanager0* libcolord1* libcolorhug1*
  libcroco3* libcups2* libdatrie1* libdconf1* libdrm-intel1* libdrm-nouveau2* libdrm-radeon1* libdv4* libenchant1c2a* libexif12* libfftw3-single3*
  libflac8* libfontconfig1* libgd3* libgdk-pixbuf2.0-0* libgdk-pixbuf2.0-common* libgeoclue0* libgl1-mesa-dri* libgl1-mesa-glx* libglapi-mesa*
  libglu1-mesa* libgnome-desktop-3-7* libgomp1* libgphoto2-6* libgphoto2-l10n* libgphoto2-port10* libgpm2* libgraphite2-3*
  libgstreamer-plugins-base0.10-0* libgstreamer-plugins-base1.0-0* libgstreamer-plugins-good1.0-0* libgstreamer0.10-0* libgstreamer1.0-0*
  libgtk-3-0* libgtk-3-bin* libgtk-3-common* libgtk2.0-0* libgtk2.0-bin* libgtk2.0-common* libgudev-1.0-0* libgusb2* libharfbuzz-icu0*
  libharfbuzz0b* libhunspell-1.3-0* libibus-1.0-5* libice6* libicu52* libiec61883-0* libieee1284-3* libimobiledevice4* libjack-jackd2-0* libjasper1*
  libjavascriptcoregtk-3.0-0* libjbig0* libjpeg-turbo8* libjpeg8* libjson-glib-1.0-0* libjson-glib-1.0-common* liblcms2-2* libllvm3.4* libltdl7*
  libnotify4* libogg0* liborc-0.4-0* libpango-1.0-0* libpangocairo-1.0-0* libpangoft2-1.0-0* libpangoxft-1.0-0* libpciaccess0* libpixman-1-0*
  libplist1* libpolkit-agent-1-0* libpolkit-backend-1-0* libproxy1* libpulse-mainloop-glib0* libpulse0* libpulsedsp* libraw1394-11* librsvg2-2*
  librsvg2-common* libsamplerate0* libsane* libsane-common* libsecret-1-0* libsecret-common* libshout3* libsm6* libsndfile1* libsoup2.4-1*
  libspeex1* libspeexdsp1* libsystemd-journal0* libtag1-vanilla* libtag1c2a* libtdb1* libthai-data* libthai0* libtheora0* libtiff5*
  libtxc-dxtn-s2tc0* libupower-glib1* libusbmuxd2* libv4l-0* libv4lconvert0* libvisual-0.4-0* libvisual-0.4-plugins* libvorbis0a* libvorbisenc2*
  libvorbisfile3* libvpx1* libwacom-common* libwacom2* libwavpack1* libwayland-client0* libwayland-cursor0* libwebkitgtk-3.0-0*
  libwebkitgtk-3.0-common* libwebp5* libwrap0* libx11-xcb1* libxcb-dri2-0* libxcb-dri3-0* libxcb-glx0* libxcb-present0* libxcb-render0* libxcb-shm0*
  libxcb-sync1* libxcomposite1* libxcursor1* libxdamage1* libxfixes3* libxft2* libxi6* libxinerama1* libxkbcommon0* libxkbfile1* libxpm4*
  libxrandr2* libxrender1* libxshmfence1* libxslt1.1* libxt6* libxtst6* libxv1* libxxf86vm1* nautilus-data* notification-daemon* policykit-1*
  pulseaudio* pulseaudio-module-x11* pulseaudio-utils* python-cairo* python-gi* python-gobject-2* python-gtk2* python-notify* rtkit*
  session-migration* sound-theme-freedesktop* tcpd* upower* usbmuxd* x11-common* zenity* zenity-common*
0 upgraded, 0 newly installed, 233 to remove and 11 not upgraded.
After this operation, 269 MB disk space will be freed.
Do you want to continue? [Y/n] 

```

---

### Post by kansasnoob on 2014-04-02
OK purge successful so what if I begin by installing 'gnome-shell':

```
root@lance-desktop:/# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.
root@lance-desktop:/# apt-get install gnome-shell
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  acl apg aptdaemon aspell aspell-en at-spi2-core avahi-daemon avahi-utils binutils bluez cheese-common colord cpp cpp-4.8 cracklib-runtime
  cups-pk-helper dbus-x11 dconf-cli dconf-gsettings-backend dconf-service desktop-file-utils dialog dictionaries-common diffstat dnsmasq-base
  enchant evolution-data-server evolution-data-server-common evolution-data-server-online-accounts folks-common fontconfig fontconfig-config
  fonts-dejavu-core gconf-service gconf-service-backend gconf2 gconf2-common gcr gdisk gdm gettext gir1.2-accountsservice-1.0 gir1.2-atk-1.0
  gir1.2-atspi-2.0 gir1.2-caribou-1.0 gir1.2-clutter-1.0 gir1.2-cogl-1.0 gir1.2-coglpango-1.0 gir1.2-freedesktop gir1.2-gck-1 gir1.2-gcr-3
  gir1.2-gdesktopenums-3.0 gir1.2-gdkpixbuf-2.0 gir1.2-gdm-1.0 gir1.2-gkbd-3.0 gir1.2-gmenu-3.0 gir1.2-gnomebluetooth-1.0 gir1.2-gnomedesktop-3.0
  gir1.2-gtk-3.0 gir1.2-ibus-1.0 gir1.2-json-1.0 gir1.2-mutter-3.0 gir1.2-networkmanager-1.0 gir1.2-nmgtk-1.0 gir1.2-notify-0.7
  gir1.2-packagekitglib-1.0 gir1.2-pango-1.0 gir1.2-polkit-1.0 gir1.2-soup-2.4 gir1.2-telepathyglib-0.12 gir1.2-telepathylogger-0.2
  gir1.2-upowerglib-1.0 gir1.2-xkl-1.0 gjs gkbd-capplet glib-networking glib-networking-common glib-networking-services gnome-accessibility-themes
  gnome-bluetooth gnome-contacts gnome-control-center gnome-control-center-data gnome-control-center-shared-data gnome-desktop3-data
  gnome-icon-theme gnome-icon-theme-full gnome-icon-theme-symbolic gnome-keyring gnome-menus gnome-session gnome-session-bin gnome-session-common
  gnome-settings-daemon gnome-settings-daemon-schemas gnome-shell-common gnome-themes-standard gnome-themes-standard-data gnome-user-guide
  gnome-user-share gsettings-desktop-schemas gsettings-ubuntu-schemas gstreamer0.10-pulseaudio gstreamer1.0-clutter gstreamer1.0-plugins-base
  gstreamer1.0-plugins-good gstreamer1.0-x gtk2-engines-pixbuf gvfs gvfs-backends gvfs-common gvfs-daemons gvfs-libs hardening-includes
  hicolor-icon-theme hunspell-en-us hwdata ibus ibus-gtk ibus-gtk3 im-config indicator-application intltool-debian iputils-arping libaa1
  libaccounts-glib0 libappindicator3-1 libapt-pkg-perl libarchive-zip-perl libarchive13 libasound2 libasound2-data libasound2-plugins libaspell15
  libasprintf-dev libasyncns0 libatasmart4 libatk-bridge2.0-0 libatk1.0-0 libatk1.0-data libatspi2.0-0 libauthen-sasl-perl libautodie-perl
  libavahi-client3 libavahi-common-data libavahi-common3 libavahi-core7 libavahi-glib1 libavc1394-0 libbluetooth3 libcaca0 libcairo-gobject2
  libcairo2 libcamel-1.2-45 libcanberra-gtk3-0 libcanberra-gtk3-module libcanberra-pulse libcanberra0 libcaribou-common libcaribou0 libcdio-cdda1
  libcdio-paranoia1 libcdio13 libcdparanoia0 libcgmanager0 libcheese-gtk23 libcheese7 libclone-perl libcloog-isl4 libclutter-1.0-0
  libclutter-1.0-common libclutter-gst-2.0-0 libclutter-gtk-1.0-0 libcogl-common libcogl-pango15 libcogl15 libcolord1 libcolorhug1 libcrack2
  libcroco3 libcups2 libdaemon0 libdatrie1 libdbusmenu-glib4 libdbusmenu-gtk3-4 libdconf1 libdee-1.0-4 libdigest-hmac-perl libdpkg-perl
  libdrm-intel1 libdrm-nouveau2 libdrm-radeon1 libdv4 libebackend-1.2-7 libebook-1.2-14 libebook-contacts-1.2-0 libecal-1.2-16 libedata-book-1.2-20
  libedata-cal-1.2-23 libedataserver-1.2-18 libegl1-mesa libegl1-mesa-drivers libelfg0 libemail-valid-perl libenchant1c2a libexif12 libfftw3-single3
  libfile-basedir-perl libfile-fcntllock-perl libflac8 libfolks-eds25 libfolks-telepathy25 libfolks25 libfontconfig1 libfontenc1 libgbm1
  libgconf-2-4 libgcr-ui-3-1 libgd3 libgdata-common libgdata13 libgdk-pixbuf2.0-0 libgdk-pixbuf2.0-common libgdm1 libgee-0.8-2 libgeoclue0
  libgettextpo-dev libgettextpo0 libgjs0e libgl1-mesa-dri libgl1-mesa-glx libglamor0 libglapi-mesa libglib2.0-bin libglu1-mesa libgmp10
  libgnome-bluetooth11 libgnome-control-center1 libgnome-desktop-3-7 libgnome-keyring-common libgnome-keyring0 libgnome-menu-3-0 libgnomekbd-common
  libgnomekbd8 libgoa-1.0-0b libgoa-1.0-common libgoa-backend-1.0-1 libgomp1 libgphoto2-6 libgphoto2-l10n libgphoto2-port10 libgpm2 libgraphite2-3
  libgstreamer-plugins-base0.10-0 libgstreamer-plugins-base1.0-0 libgstreamer-plugins-good1.0-0 libgstreamer0.10-0 libgstreamer1.0-0 libgtk-3-0
  libgtk-3-bin libgtk-3-common libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libgtop2-7 libgtop2-common libgudev-1.0-0 libgusb2 libgweather-3-6
  libgweather-common libharfbuzz-icu0 libharfbuzz0b libhdb9-heimdal libhunspell-1.3-0 libibus-1.0-5 libical1 libice6 libicu52 libiec61883-0
  libieee1284-3 libimobiledevice4 libindicator3-7 libio-pty-perl libio-socket-inet6-perl libio-socket-ssl-perl libipc-run-perl
  libipc-system-simple-perl libisl10 libjack-jackd2-0 libjasper1 libjavascriptcoregtk-3.0-0 libjbig0 libjpeg-turbo8 libjpeg8 libjson-glib-1.0-0
  libjson-glib-1.0-common liblcms2-2 libldb1 liblist-moreutils-perl libllvm3.4 libltdl7 liblzo2-2 libmailtools-perl libmbim-glib0
  libmission-control-plugins0 libmm-glib0 libmnl0 libmozjs-24-0 libmpc3 libmpfr4 libmtdev1 libmtp-common libmtp-runtime libmtp9 libmutter0c
  libnet-dns-perl libnet-domain-tld-perl libnet-ip-perl libnet-libidn-perl libnet-smtp-ssl-perl libnet-ssleay-perl libnetfilter-conntrack3
  libnettle4 libnl-route-3-200 libnm-glib-vpn1 libnm-glib4 libnm-gtk-common libnm-gtk0 libnm-util2 libnotify4 libnspr4 libnss-mdns libnss3
  libnss3-nssdb libntdb1 liboauth0 libogg0 libopenobex1 libopenvg1-mesa liborc-0.4-0 libp11-kit-gnome-keyring libpackagekit-glib2-16
  libpam-gnome-keyring libpango-1.0-0 libpango1.0-0 libpangocairo-1.0-0 libpangoft2-1.0-0 libpangox-1.0-0 libpangoxft-1.0-0 libpciaccess0
  libpcsclite1 libperlio-gzip-perl libpixman-1-0 libplist1 libpolkit-agent-1-0 libpolkit-backend-1-0 libproxy1 libpulse-mainloop-glib0 libpulse0
  libpulsedsp libpwquality-common libpwquality1 libpython2.7 libqmi-glib0 libraw1394-11 libreadline5 librest-0.7-0 librsvg2-2 librsvg2-common
  libsamplerate0 libsane libsane-common libsecret-1-0 libsecret-common libshout3 libsignon-glib1 libsm6 libsmbclient libsndfile1 libsocket6-perl
  libsoup-gnome2.4-1 libsoup2.4-1 libspeex1 libspeexdsp1 libstartup-notification0 libsub-identify-perl libsystemd-journal0 libtag1-vanilla
  libtag1c2a libtalloc2 libtdb1 libtelepathy-glib0 libtelepathy-logger3 libtevent0 libtext-levenshtein-perl libthai-data libthai0 libtheora0
  libtiff5 libtimezonemap1 libtxc-dxtn-s2tc0 libudisks2-0 libunistring0 libunity-control-center1 libupower-glib1 liburi-perl libusbmuxd2 libv4l-0
  libv4lconvert0 libvisual-0.4-0 libvisual-0.4-plugins libvorbis0a libvorbisenc2 libvorbisfile3 libvpx1 libwacom-common libwacom2 libwavpack1
  libwayland-client0 libwayland-cursor0 libwayland-egl1-mesa libwayland-server0 libwbclient0 libwebkitgtk-3.0-0 libwebkitgtk-3.0-common libwebp5
  libwrap0 libx11-xcb1 libxatracker2 libxaw7 libxcb-dri2-0 libxcb-dri3-0 libxcb-glx0 libxcb-icccm4 libxcb-image0 libxcb-keysyms1 libxcb-present0
  libxcb-render0 libxcb-shape0 libxcb-shm0 libxcb-sync1 libxcb-util0 libxcb-xf86dri0 libxcb-xfixes0 libxcb-xv0 libxcomposite1 libxcursor1
  libxdamage1 libxfixes3 libxfont1 libxft2 libxi6 libxinerama1 libxkbcommon0 libxkbfile1 libxklavier16 libxmu6 libxpm4 libxrandr2 libxrender1
  libxshmfence1 libxslt1.1 libxt6 libxtst6 libxv1 libxvmc1 libxxf86dga1 libxxf86vm1 libyelp0 libzeitgeist-2.0-0 lintian make
  mobile-broadband-provider-info modemmanager mousetweaks mutter-common nautilus-data network-manager network-manager-gnome network-manager-pptp
  network-manager-pptp-gnome notification-daemon obex-data-server obexd-client p11-kit p11-kit-modules patch patchutils policykit-1
  policykit-1-gnome pptp-linux pulseaudio pulseaudio-module-x11 pulseaudio-utils python-cairo python-cups python-cupshelpers python-dbus
  python-dbus-dev python-gi python-gnomekeyring python-gobject python-gobject-2 python-gtk2 python-libxml2 python-notify python-pycurl python-smbc
  python-talloc python-xdg python-zeitgeist python3-aptdaemon python3-aptdaemon.pkcompat python3-defer python3-pkg-resources rtkit samba-libs
  session-migration sound-theme-freedesktop system-config-printer-common system-config-printer-gnome system-config-printer-udev t1utils tcpd
  telepathy-mission-control-5 ubuntu-system-service udisks2 unity-control-center unity-settings-daemon unzip upower usb-modeswitch
  usb-modeswitch-data usbmuxd wamerican wpasupplicant x11-common x11-utils x11-xkb-utils x11-xserver-utils xfonts-base xfonts-encodings xfonts-utils
  xserver-common xserver-xephyr xserver-xorg xserver-xorg-core xserver-xorg-input-all xserver-xorg-input-evdev xserver-xorg-input-mouse
  xserver-xorg-input-synaptics xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-all xserver-xorg-video-ati
  xserver-xorg-video-cirrus xserver-xorg-video-fbdev xserver-xorg-video-glamoregl xserver-xorg-video-intel xserver-xorg-video-mach64
  xserver-xorg-video-mga xserver-xorg-video-modesetting xserver-xorg-video-neomagic xserver-xorg-video-nouveau xserver-xorg-video-openchrome
  xserver-xorg-video-qxl xserver-xorg-video-r128 xserver-xorg-video-radeon xserver-xorg-video-s3 xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident
  xserver-xorg-video-vesa xserver-xorg-video-vmware yelp yelp-xsl zeitgeist zeitgeist-core zeitgeist-datahub zenity zenity-common
Suggested packages:
  aspell-doc spellutils avahi-autoipd binutils-doc bluez-hcidump cpp-doc gcc-4.8-locales wordlist emacsen-common jed-extra evolution
  evolution-data-server-dbg gconf-defaults-service gnome-orca gettext-doc gnome-screensaver xscreensaver libcanberra-gtk-module desktop-base
  metacity x-window-manager apache2.2-bin libapache2-mod-dnssd gvfs-backends-goa samba-common hunspell openoffice.org-hunspell openoffice.org-core
  ibus-clutter ibus-doc ibus-qt4 lrzip alsa-utils libgssapi-perl libcanberra-gtk0 libgles2-mesa libgles2 cups-common debian-keyring gcc c-compiler
  libdv-bin oss-compat libenchant-voikko libfftw3-bin libfftw3-dev libgd-tools geoclue libglide3 gphoto2 gtkam gpm gstreamer-codec-install
  gnome-codec-install gstreamer0.10-tools gstreamer0.10-plugins-base gstreamer1.0-tools jackd2 libjasper-runtime liblcms2-utils ttf-baekmuk
  ttf-arphic-gbsn00lp ttf-arphic-bsmi00lp ttf-arphic-gkai00mp ttf-arphic-bkai00mp pcscd libraw1394-doc librsvg2-bin hplip hpoj libsane-extras
  sane-utils speex libwww-perl binutils-multiarch dpkg-dev libhtml-parser-perl libtext-template-perl libyaml-perl make-doc nautilus
  network-manager-openconnect-gnome network-manager-openvpn-gnome network-manager-vpnc-gnome diffutils-doc pavumeter paman pavucontrol paprefs
  pulseaudio-module-raop pulseaudio-esound-compat python-dbus-doc python-dbus-dbg python-gi-cairo python-gobject-2-dbg python-gtk2-doc
  libcurl4-gnutls-dev python-pycurl-dbg python3-setuptools telepathy-haze xfsprogs reiserfsprogs exfat-utils btrfs-tools mdadm cryptsetup-bin comgt
  wvdial wpagui libengine-pkcs11-openssl mesa-utils nickle cairo-5c xorg-docs-core xfs xserver xfonts-100dpi xfonts-75dpi xfonts-scalable
  gpointing-device-settings touchfreeze xinput firmware-linux
The following NEW packages will be installed:
  acl apg aptdaemon aspell aspell-en at-spi2-core avahi-daemon avahi-utils binutils bluez cheese-common colord cpp cpp-4.8 cracklib-runtime
  cups-pk-helper dbus-x11 dconf-cli dconf-gsettings-backend dconf-service desktop-file-utils dialog dictionaries-common diffstat dnsmasq-base
  enchant evolution-data-server evolution-data-server-common evolution-data-server-online-accounts folks-common fontconfig fontconfig-config
  fonts-dejavu-core gconf-service gconf-service-backend gconf2 gconf2-common gcr gdisk gdm gettext gir1.2-accountsservice-1.0 gir1.2-atk-1.0
  gir1.2-atspi-2.0 gir1.2-caribou-1.0 gir1.2-clutter-1.0 gir1.2-cogl-1.0 gir1.2-coglpango-1.0 gir1.2-freedesktop gir1.2-gck-1 gir1.2-gcr-3
  gir1.2-gdesktopenums-3.0 gir1.2-gdkpixbuf-2.0 gir1.2-gdm-1.0 gir1.2-gkbd-3.0 gir1.2-gmenu-3.0 gir1.2-gnomebluetooth-1.0 gir1.2-gnomedesktop-3.0
  gir1.2-gtk-3.0 gir1.2-ibus-1.0 gir1.2-json-1.0 gir1.2-mutter-3.0 gir1.2-networkmanager-1.0 gir1.2-nmgtk-1.0 gir1.2-notify-0.7
  gir1.2-packagekitglib-1.0 gir1.2-pango-1.0 gir1.2-polkit-1.0 gir1.2-soup-2.4 gir1.2-telepathyglib-0.12 gir1.2-telepathylogger-0.2
  gir1.2-upowerglib-1.0 gir1.2-xkl-1.0 gjs gkbd-capplet glib-networking glib-networking-common glib-networking-services gnome-accessibility-themes
  gnome-bluetooth gnome-contacts gnome-control-center gnome-control-center-data gnome-control-center-shared-data gnome-desktop3-data
  gnome-icon-theme gnome-icon-theme-full gnome-icon-theme-symbolic gnome-keyring gnome-menus gnome-session gnome-session-bin gnome-session-common
  gnome-settings-daemon gnome-settings-daemon-schemas gnome-shell gnome-shell-common gnome-themes-standard gnome-themes-standard-data
  gnome-user-guide gnome-user-share gsettings-desktop-schemas gsettings-ubuntu-schemas gstreamer0.10-pulseaudio gstreamer1.0-clutter
  gstreamer1.0-plugins-base gstreamer1.0-plugins-good gstreamer1.0-x gtk2-engines-pixbuf gvfs gvfs-backends gvfs-common gvfs-daemons gvfs-libs
  hardening-includes hicolor-icon-theme hunspell-en-us hwdata ibus ibus-gtk ibus-gtk3 im-config indicator-application intltool-debian iputils-arping
  libaa1 libaccounts-glib0 libappindicator3-1 libapt-pkg-perl libarchive-zip-perl libarchive13 libasound2 libasound2-data libasound2-plugins
  libaspell15 libasprintf-dev libasyncns0 libatasmart4 libatk-bridge2.0-0 libatk1.0-0 libatk1.0-data libatspi2.0-0 libauthen-sasl-perl
  libautodie-perl libavahi-client3 libavahi-common-data libavahi-common3 libavahi-core7 libavahi-glib1 libavc1394-0 libbluetooth3 libcaca0
  libcairo-gobject2 libcairo2 libcamel-1.2-45 libcanberra-gtk3-0 libcanberra-gtk3-module libcanberra-pulse libcanberra0 libcaribou-common
  libcaribou0 libcdio-cdda1 libcdio-paranoia1 libcdio13 libcdparanoia0 libcgmanager0 libcheese-gtk23 libcheese7 libclone-perl libcloog-isl4
  libclutter-1.0-0 libclutter-1.0-common libclutter-gst-2.0-0 libclutter-gtk-1.0-0 libcogl-common libcogl-pango15 libcogl15 libcolord1 libcolorhug1
  libcrack2 libcroco3 libcups2 libdaemon0 libdatrie1 libdbusmenu-glib4 libdbusmenu-gtk3-4 libdconf1 libdee-1.0-4 libdigest-hmac-perl libdpkg-perl
  libdrm-intel1 libdrm-nouveau2 libdrm-radeon1 libdv4 libebackend-1.2-7 libebook-1.2-14 libebook-contacts-1.2-0 libecal-1.2-16 libedata-book-1.2-20
  libedata-cal-1.2-23 libedataserver-1.2-18 libegl1-mesa libegl1-mesa-drivers libelfg0 libemail-valid-perl libenchant1c2a libexif12 libfftw3-single3
  libfile-basedir-perl libfile-fcntllock-perl libflac8 libfolks-eds25 libfolks-telepathy25 libfolks25 libfontconfig1 libfontenc1 libgbm1
  libgconf-2-4 libgcr-ui-3-1 libgd3 libgdata-common libgdata13 libgdk-pixbuf2.0-0 libgdk-pixbuf2.0-common libgdm1 libgee-0.8-2 libgeoclue0
  libgettextpo-dev libgettextpo0 libgjs0e libgl1-mesa-dri libgl1-mesa-glx libglamor0 libglapi-mesa libglib2.0-bin libglu1-mesa libgmp10
  libgnome-bluetooth11 libgnome-control-center1 libgnome-desktop-3-7 libgnome-keyring-common libgnome-keyring0 libgnome-menu-3-0 libgnomekbd-common
  libgnomekbd8 libgoa-1.0-0b libgoa-1.0-common libgoa-backend-1.0-1 libgomp1 libgphoto2-6 libgphoto2-l10n libgphoto2-port10 libgpm2 libgraphite2-3
  libgstreamer-plugins-base0.10-0 libgstreamer-plugins-base1.0-0 libgstreamer-plugins-good1.0-0 libgstreamer0.10-0 libgstreamer1.0-0 libgtk-3-0
  libgtk-3-bin libgtk-3-common libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libgtop2-7 libgtop2-common libgudev-1.0-0 libgusb2 libgweather-3-6
  libgweather-common libharfbuzz-icu0 libharfbuzz0b libhdb9-heimdal libhunspell-1.3-0 libibus-1.0-5 libical1 libice6 libicu52 libiec61883-0
  libieee1284-3 libimobiledevice4 libindicator3-7 libio-pty-perl libio-socket-inet6-perl libio-socket-ssl-perl libipc-run-perl
  libipc-system-simple-perl libisl10 libjack-jackd2-0 libjasper1 libjavascriptcoregtk-3.0-0 libjbig0 libjpeg-turbo8 libjpeg8 libjson-glib-1.0-0
  libjson-glib-1.0-common liblcms2-2 libldb1 liblist-moreutils-perl libllvm3.4 libltdl7 liblzo2-2 libmailtools-perl libmbim-glib0
  libmission-control-plugins0 libmm-glib0 libmnl0 libmozjs-24-0 libmpc3 libmpfr4 libmtdev1 libmtp-common libmtp-runtime libmtp9 libmutter0c
  libnet-dns-perl libnet-domain-tld-perl libnet-ip-perl libnet-libidn-perl libnet-smtp-ssl-perl libnet-ssleay-perl libnetfilter-conntrack3
  libnettle4 libnl-route-3-200 libnm-glib-vpn1 libnm-glib4 libnm-gtk-common libnm-gtk0 libnm-util2 libnotify4 libnspr4 libnss-mdns libnss3
  libnss3-nssdb libntdb1 liboauth0 libogg0 libopenobex1 libopenvg1-mesa liborc-0.4-0 libp11-kit-gnome-keyring libpackagekit-glib2-16
  libpam-gnome-keyring libpango-1.0-0 libpango1.0-0 libpangocairo-1.0-0 libpangoft2-1.0-0 libpangox-1.0-0 libpangoxft-1.0-0 libpciaccess0
  libpcsclite1 libperlio-gzip-perl libpixman-1-0 libplist1 libpolkit-agent-1-0 libpolkit-backend-1-0 libproxy1 libpulse-mainloop-glib0 libpulse0
  libpulsedsp libpwquality-common libpwquality1 libpython2.7 libqmi-glib0 libraw1394-11 libreadline5 librest-0.7-0 librsvg2-2 librsvg2-common
  libsamplerate0 libsane libsane-common libsecret-1-0 libsecret-common libshout3 libsignon-glib1 libsm6 libsmbclient libsndfile1 libsocket6-perl
  libsoup-gnome2.4-1 libsoup2.4-1 libspeex1 libspeexdsp1 libstartup-notification0 libsub-identify-perl libsystemd-journal0 libtag1-vanilla
  libtag1c2a libtalloc2 libtdb1 libtelepathy-glib0 libtelepathy-logger3 libtevent0 libtext-levenshtein-perl libthai-data libthai0 libtheora0
  libtiff5 libtimezonemap1 libtxc-dxtn-s2tc0 libudisks2-0 libunistring0 libunity-control-center1 libupower-glib1 liburi-perl libusbmuxd2 libv4l-0
  libv4lconvert0 libvisual-0.4-0 libvisual-0.4-plugins libvorbis0a libvorbisenc2 libvorbisfile3 libvpx1 libwacom-common libwacom2 libwavpack1
  libwayland-client0 libwayland-cursor0 libwayland-egl1-mesa libwayland-server0 libwbclient0 libwebkitgtk-3.0-0 libwebkitgtk-3.0-common libwebp5
  libwrap0 libx11-xcb1 libxatracker2 libxaw7 libxcb-dri2-0 libxcb-dri3-0 libxcb-glx0 libxcb-icccm4 libxcb-image0 libxcb-keysyms1 libxcb-present0
  libxcb-render0 libxcb-shape0 libxcb-shm0 libxcb-sync1 libxcb-util0 libxcb-xf86dri0 libxcb-xfixes0 libxcb-xv0 libxcomposite1 libxcursor1
  libxdamage1 libxfixes3 libxfont1 libxft2 libxi6 libxinerama1 libxkbcommon0 libxkbfile1 libxklavier16 libxmu6 libxpm4 libxrandr2 libxrender1
  libxshmfence1 libxslt1.1 libxt6 libxtst6 libxv1 libxvmc1 libxxf86dga1 libxxf86vm1 libyelp0 libzeitgeist-2.0-0 lintian make
  mobile-broadband-provider-info modemmanager mousetweaks mutter-common nautilus-data network-manager network-manager-gnome network-manager-pptp
  network-manager-pptp-gnome notification-daemon obex-data-server obexd-client p11-kit p11-kit-modules patch patchutils policykit-1
  policykit-1-gnome pptp-linux pulseaudio pulseaudio-module-x11 pulseaudio-utils python-cairo python-cups python-cupshelpers python-dbus
  python-dbus-dev python-gi python-gnomekeyring python-gobject python-gobject-2 python-gtk2 python-libxml2 python-notify python-pycurl python-smbc
  python-talloc python-xdg python-zeitgeist python3-aptdaemon python3-aptdaemon.pkcompat python3-defer python3-pkg-resources rtkit samba-libs
  session-migration sound-theme-freedesktop system-config-printer-common system-config-printer-gnome system-config-printer-udev t1utils tcpd
  telepathy-mission-control-5 ubuntu-system-service udisks2 unity-control-center unity-settings-daemon unzip upower usb-modeswitch
  usb-modeswitch-data usbmuxd wamerican wpasupplicant x11-common x11-utils x11-xkb-utils x11-xserver-utils xfonts-base xfonts-encodings xfonts-utils
  xserver-common xserver-xephyr xserver-xorg xserver-xorg-core xserver-xorg-input-all xserver-xorg-input-evdev xserver-xorg-input-mouse
  xserver-xorg-input-synaptics xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-all xserver-xorg-video-ati
  xserver-xorg-video-cirrus xserver-xorg-video-fbdev xserver-xorg-video-glamoregl xserver-xorg-video-intel xserver-xorg-video-mach64
  xserver-xorg-video-mga xserver-xorg-video-modesetting xserver-xorg-video-neomagic xserver-xorg-video-nouveau xserver-xorg-video-openchrome
  xserver-xorg-video-qxl xserver-xorg-video-r128 xserver-xorg-video-radeon xserver-xorg-video-s3 xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident
  xserver-xorg-video-vesa xserver-xorg-video-vmware yelp yelp-xsl zeitgeist zeitgeist-core zeitgeist-datahub zenity zenity-common
0 upgraded, 585 newly installed, 0 to remove and 11 not upgraded.
Need to get 78.1 MB/135 MB of archives.
After this operation, 560 MB of additional disk space will be used.
Do you want to continue? [Y/n] 

```

---

### Post by kansasnoob on 2014-04-02
Next step:

```
root@lance-desktop:/# [B][COLOR="#FF0000"]apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.[/COLOR][/B]
root@lance-desktop:/# apt-get install ubuntu-gnome-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  account-plugin-aim account-plugin-facebook account-plugin-google account-plugin-jabber account-plugin-salut account-plugin-windows-live
  account-plugin-yahoo acpi-support acpid aisleriot alsa-base alsa-utils anacron app-install-data app-install-data-partner apport apport-gtk
  apport-symptoms aptdaemon-data apturl apturl-common argyll avahi-autoipd baobab bc bluez-alsa bluez-cups bluez-gstreamer brasero brasero-cdrkit
  brasero-common brltty cheese cups cups-browsed cups-bsd cups-client cups-common cups-core-drivers cups-daemon cups-filters
  cups-filters-core-drivers cups-ppdc cups-server-common dc dconf-editor deja-dup deja-dup-backend-cloudfiles deja-dup-backend-gvfs
  deja-dup-backend-s3 deja-dup-backend-ubuntuone duplicity dvd+rw-tools empathy empathy-common eog espeak-data evince evince-common evolution
  evolution-common evolution-indicator evolution-plugins file-roller firefox fonts-cantarell fonts-droid fonts-freefont-ttf fonts-kacst
  fonts-kacst-one fonts-khmeros-core fonts-lao fonts-liberation fonts-lklug-sinhala fonts-nanum fonts-opensymbol fonts-sil-abyssinica
  fonts-sil-padauk fonts-takao-pgothic fonts-thai-tlwg fonts-tibetan-machine fonts-tlwg-garuda fonts-tlwg-kinnari fonts-tlwg-loma fonts-tlwg-mono
  fonts-tlwg-norasi fonts-tlwg-purisa fonts-tlwg-sawasdee fonts-tlwg-typewriter fonts-tlwg-typist fonts-tlwg-typo fonts-tlwg-umpush fonts-tlwg-waree
  foomatic-db-compressed-ppds gcc gcc-4.8 gdb gedit gedit-common genisoimage geoclue ghostscript ghostscript-x gir1.2-clutter-gst-2.0
  gir1.2-dbusmenu-glib-0.4 gir1.2-dee-1.0 gir1.2-evince-3.0 gir1.2-gdata-0.0 gir1.2-gnomekeyring-1.0 gir1.2-goa-1.0 gir1.2-gst-plugins-base-1.0
  gir1.2-gstreamer-1.0 gir1.2-gtkclutter-1.0 gir1.2-gtksource-3.0 gir1.2-gtop-2.0 gir1.2-gudev-1.0 gir1.2-javascriptcoregtk-3.0 gir1.2-peas-1.0
  gir1.2-rb-3.0 gir1.2-rest-0.7 gir1.2-secret-1 gir1.2-syncmenu-0.1 gir1.2-totem-1.0 gir1.2-totem-plparser-1.0 gir1.2-tracker-0.16 gir1.2-udisks-2.0
  gir1.2-unity-5.0 gir1.2-vte-2.90 gir1.2-webkit-3.0 gir1.2-wnck-3.0 gir1.2-zpj-0.0 gnome-backgrounds gnome-calculator gnome-color-manager
  gnome-disk-utility gnome-documents gnome-font-viewer gnome-icon-theme-extras gnome-mahjongg gnome-mines gnome-online-accounts gnome-online-miners
  gnome-orca gnome-screenshot gnome-session-canberra gnome-shell-extensions gnome-sudoku gnome-sushi gnome-system-log gnome-system-monitor
  gnome-terminal gnome-terminal-data gnome-tweak-tool gnome-video-effects growisofs gsfonts gstreamer0.10-alsa gstreamer0.10-nice
  gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-x gstreamer1.0-alsa gstreamer1.0-nice gstreamer1.0-pulseaudio gucharmap
  guile-2.0-libs gvfs-backends-goa gvfs-bin gvfs-fuse hplip hplip-data humanity-icon-theme ibus-pinyin ibus-table indicator-sync inputattach
  intel-gpu-tools iproute itstool kerneloops-daemon libaccount-plugin-1.0-0 libaccount-plugin-generic-oauth libaccount-plugin-google
  libaccounts-qt5-1 libart-2.0-2 libasan0 libassuan0 libatk-adaptor libatkmm-1.6-1 libatomic1 libavahi-gobject0 libboost-date-time1.54.0
  libboost-system1.54.0 libbrasero-media3-1 libbrlapi0.6 libburn4 libc-dev-bin libc6-dbg libc6-dev libcairomm-1.0-1 libcanberra-gtk-module
  libcanberra-gtk0 libcdr-0.0-0 libclucene-contribs1 libclucene-core1 libcmis-0.4-4 libcolamd2.8.0 libcolord-gtk1 libcrypt-passwdmd5-perl
  libcupscgi1 libcupsfilters1 libcupsimage2 libcupsmime1 libcupsppdc1 libcurl3 libdbusmenu-gtk4 libdjvulibre-text libdjvulibre21
  libdmapsharing-3.0-2 libdotconf0 libenca0 libencode-locale-perl liberror-perl libespeak1 libevdocument3-4 libevent-2.0-5 libevolution libevview3-3
  libexempi3 libexiv2-12 libexttextcat-2.0-0 libexttextcat-data libfarstream-0.1-0 libfarstream-0.2-2 libfile-copy-recursive-perl
  libfile-desktopentry-perl libfile-listing-perl libfile-mimeinfo-perl libfont-afm-perl libfontembed1 libframe6 libfs6 libgail-3-0 libgail-common
  libgail18 libgc1c2 libgcc-4.8-dev libgeis1 libgexiv2-2 libgif4 libgles2-mesa libglibmm-2.4-1c2a libgmime-2.6-0 libgpgme11 libgpod-common libgpod4
  libgrail6 libgrilo-0.2-1 libgrip0 libgs9 libgs9-common libgsf-1-114 libgsf-1-common libgssdp-1.0-3 libgtkhtml-4.0-0 libgtkhtml-4.0-common
  libgtkhtml-editor-4.0-0 libgtkmm-3.0-1 libgtksourceview-3.0-1 libgtksourceview-3.0-common libgucharmap-2-90-7 libgupnp-1.0-4 libgupnp-igd-1.0-4
  libgutenprint2 libgxps2 libhpmud0 libhtml-form-perl libhtml-format-perl libhtml-parser-perl libhtml-tagset-perl libhtml-tree-perl
  libhttp-cookies-perl libhttp-daemon-perl libhttp-date-perl libhttp-message-perl libhttp-negotiate-perl libhyphen0 libicc2 libido3-0.1-0
  libijs-0.35 libimdi0 libio-html-perl libiptcdata0 libisofs6 libitm1 libiw30 libjbig2dec0 libjte1 libkpathsea6 liblangtag-common liblangtag1
  liblircclient0 liblouis-data liblouis2 liblua5.2-0 liblwp-mediatypes-perl liblwp-protocol-https-perl libmail-spf-perl libmeanwhile1
  libmessaging-menu0 libmhash2 libminiupnpc8 libmspub-0.0-0 libmusicbrainz5-0 libmythes-1.2-0 libnatpmp1 libnautilus-extension1a libneon27-gnutls
  libnet-http-perl libnetaddr-ip-perl libnice10 libnotify-bin libnss-myhostname libopencc1 liborcus-0.6-0 libpangomm-1.4-1 libpaper-utils libpaper1
  libpeas-1.0-0 libpeas-common libperl5.18 libpoppler-glib8 libpoppler44 libportaudio2 libproxy1-plugin-gsettings libproxy1-plugin-networkmanager
  libpst4 libpurple-bin libpurple0 libpython3.4 libpyzy-1.0-0 libqpdf13 libqt5core5a libqt5dbus5 libqt5gui5 libqt5network5 libqt5opengl5
  libqt5positioning5 libqt5printsupport5 libqt5qml5 libqt5quick5 libqt5sensors5 libqt5sql5 libqt5sql5-sqlite libqt5test5 libqt5webkit5
  libqt5widgets5 libqt5xml5 libquadmath0 libraptor2-0 librasqal3 libraw9 librdf0 libreoffice-avmedia-backend-gstreamer libreoffice-base-core
  libreoffice-calc libreoffice-common libreoffice-core libreoffice-draw libreoffice-gnome libreoffice-gtk libreoffice-impress libreoffice-math
  libreoffice-ogltrans libreoffice-pdfimport libreoffice-presentation-minimizer libreoffice-style-galaxy libreoffice-style-human
  libreoffice-style-tango libreoffice-writer librhythmbox-core8 librsync1 libsane-hpaio libsbc1 libsensors4 libsgutils2-2 libsignon-extension1
  libsignon-plugins-common1 libsignon-qt5-1 libsnmp-base libsnmp30 libsonic0 libspectre1 libspeechd2 libsync-menu1 libsys-hostname-long-perl libt1-5
  libtcl8.6 libtelepathy-farstream3 libtk8.6 libtotem-plparser18 libtotem0 libtracker-extract-0.16-0 libtracker-miner-0.16-0
  libtracker-sparql-0.16-0 libunity-protocol-private0 libunity-scopes-json-def-desktop libunity9 libutempter0 libvisio-0.0-0 libvte-2.90-9
  libvte-2.90-common libwebpmux1 libwhoopsie0 libwmf0.2-7 libwmf0.2-7-gtk libwnck-3-0 libwnck-3-common libwpd-0.9-9 libwpg-0.2-2 libwps-0.2-2
  libwww-perl libwww-robotrules-perl libxcb-randr0 libxcb-render-util0 libxcb-xkb1 libxml2-utils libxp6 libxres1 libxss1 libyajl2 libytnef0
  libzapojit-0.0-0 libzeitgeist-1.0-1 libzephyr4 linux-libc-dev linux-sound-base lp-solve manpages-dev mcp-account-manager-goa
  mcp-account-manager-uoa media-player-info memtest86+ mscompress mtools mutter nautilus nautilus-sendto nautilus-sendto-empathy nautilus-share
  oneconf oneconf-common openprinting-ppds pcmciautils plymouth-label plymouth-theme-ubuntu-gnome-logo plymouth-theme-ubuntu-gnome-text
  policykit-desktop-privileges poppler-data poppler-utils printer-driver-c2esp printer-driver-foo2zjs printer-driver-foo2zjs-common
  printer-driver-gutenprint printer-driver-hpcups printer-driver-min12xxw printer-driver-pnm2ppa printer-driver-postscript-hp printer-driver-ptouch
  printer-driver-pxljr printer-driver-sag-gdi printer-driver-splix pulseaudio-module-bluetooth python-aptdaemon python-aptdaemon.gtk3widgets
  python-boto python-cloudfiles python-commandnotfound python-configglue python-crypto python-debtagshw python-defer python-dirspec python-gdbm
  python-gi-cairo python-httplib2 python-ibus python-imaging python-ldb python-lockfile python-lxml python-ntdb python-oauthlib python-oneconf
  python-openssl python-pam python-pexpect python-pil python-piston-mini-client python-pkg-resources python-protobuf python-pyinotify
  python-renderpm python-reportlab python-reportlab-accel python-requests python-samba python-serial python-tdb python-twisted-bin
  python-twisted-core python-twisted-names python-twisted-web python-ubuntu-sso-client python-ubuntuone-client python-ubuntuone-control-panel
  python-ubuntuone-storageprotocol python-urllib3 python-zope.interface python3-apport python3-aptdaemon.gtk3widgets python3-brlapi python3-cairo
  python3-chardet python3-crypto python3-debian python3-dirspec python3-gi-cairo python3-httplib2 python3-louis python3-mako python3-markupsafe
  python3-oauthlib python3-oneconf python3-piston-mini-client python3-problem-report python3-pyatspi python3-pycurl python3-six
  python3-software-properties python3-speechd python3-uno python3-xdg python3-xkit qpdf re2c rfkill rhythmbox rhythmbox-data rhythmbox-mozilla
  rhythmbox-plugin-cdrecorder rhythmbox-plugin-magnatune rhythmbox-plugin-zeitgeist rhythmbox-plugins rhythmbox-ubuntuone sa-compile samba-common
  samba-common-bin sane-utils seahorse sessioninstaller shotwell shotwell-common signon-keyring-extension signon-plugin-oauth2
  signon-plugin-password signon-ui signond simple-scan smbclient software-center software-center-aptdaemon-plugins software-properties-common
  software-properties-gtk spamassassin spamc speech-dispatcher speech-dispatcher-audio-plugins ssh-askpass-gnome ssl-cert syslinux syslinux-common
  syslinux-legacy tcl tcl8.6 telepathy-gabble telepathy-haze telepathy-idle telepathy-logger telepathy-salut tk tk8.6 toshset totem totem-common
  totem-plugins tracker tracker-extract tracker-miner-fs tracker-utils transmission-common transmission-gtk ttf-indic-fonts-core ttf-punjabi-fonts
  ttf-ubuntu-font-family ubuntu-drivers-common ubuntu-extras-keyring ubuntu-gnome-default-settings ubuntu-release-upgrader-gtk ubuntu-sso-client
  ubuntuone-client ubuntuone-client-data ubuntuone-control-panel unattended-upgrades unity-asset-pool unity-control-center-signon uno-libs3 unoconv
  update-inetd update-manager update-notifier update-notifier-common ure usb-creator-common usb-creator-gtk vino whoopsie wireless-tools wodim
  x11-apps x11-session-utils x11-xfs-utils xbitmaps xdg-user-dirs xdg-user-dirs-gtk xdg-utils xdiagnose xfonts-mathml xfonts-scalable xinit xinput
  xorg xorg-docs-core xsltproc xterm xul-ext-ubufox yelp-tools zip zsync
Suggested packages:
  gnome-cards-data apmd alsa-oss oss-compat default-mta mail-transport-agent libgtk2-perl gir1.2-colordgtk-1.0 vcdimager libdvdcss2 dvdauthor readom
  brltty-speechd brltty-x11 console-braille gnome-video-effects-frei0r gnome-video-effects-extra cups-pdf xpp python-paramiko ncftp lftp
  python-gdata tahoe-lafs python-swiftclient cdrskin unrar evolution-ews evolution-plugins-experimental arj lha lzip lzop ncompress p7zip-full
  rpm2cpio rzip sharutils unace unalz unar zoo ttf-lyx libgraphite3 pango-graphite hplip-cups printer-driver-all gcc-multilib autoconf automake1.9
  libtool flex bison gcc-doc gcc-4.8-multilib gcc-4.8-doc gcc-4.8-locales libgcc1-dbg libgomp1-dbg libitm1-dbg libatomic1-dbg libasan0-dbg
  libtsan0-dbg libbacktrace1-dbg libquadmath0-dbg gdb-doc gdbserver gedit-plugins cdrkit-doc hpijs gstreamer1.0-libav hplip-gui hplip-doc
  system-config-printer gstreamer1.0-plugins-ugly cdrdao gstreamer1.0-fluendo-mp3 gstreamer1.0-plugins-bad glibc-doc exiv2 gpgsm grilo-plugins-0.2
  gutenprint-locales libdata-dump-perl lirc libcrypt-ssleay-perl minissdpd natpmp-utils raptor2-utils rasqal-utils librdf-storage-postgresql
  librdf-storage-mysql librdf-storage-sqlite librdf-storage-virtuoso redland-utils libreoffice-base libopencl1 libreoffice-style-crystal
  libreoffice-style-hicontrast libreoffice-style-oxygen libreoffice-style-sifr libreoffice-evolution crystalcursors kde-icons-crystal
  tango-icon-theme libreoffice-gcj libreoffice-java-common default-jre gcj-jre openjdk-7-jre openjdk-6-jre sun-java5-jre sun-java6-jre java5-runtime
  jre lm-sensors sg3-utils snmp-mibs-downloader libspectre1-dbg unity-common libauthen-ntlm-perl account-plugin-gadugadu account-plugin-groupwise
  account-plugin-icq account-plugin-irc account-plugin-mxit account-plugin-myspace account-plugin-sametime account-plugin-sip account-plugin-yahoojp
  account-plugin-zephyr hwtools memtester kernel-patch-badram memtest86 floppyd pidgin gajim samba hpijs-ppds fonts-japanese-mincho
  fonts-ipafont-mincho fonts-japanese-gothic fonts-ipafont-gothic fonts-arphic-ukai fonts-arphic-uming fonts-unfonts-core psutils hannah-foo2zjs tix
  gutenprint-doc magicfilter apsfilter python-crypto-dbg python-crypto-doc python-gdbm-dbg python-lxml-dbg python-openssl-doc python-openssl-dbg
  python-pam-dbg python-pexpect-doc python-pil-doc python-pil-dbg python-distribute python-distribute-doc python-pyinotify-doc python-renderpm-dbg
  pdf-viewer python-egenix-mxtexttools python-reportlab-doc python-wxgtk2.8 python-wxgtk python-twisted-bin-dbg python-tk python-glade2 python-qt3
  python3-launchpadlib python3-crypto-dbg python3-beaker python-mako-doc libcurl4-gnutls-dev python3-pycurl-dbg gnome-codec-install heimdal-clients
  unpaper account-plugin-flickr cifs-utils razor libdbi-perl pyzor libmail-dkim-perl libttspico-utils speech-dispatcher-doc-cs
  speech-dispatcher-festival speech-dispatcher-flite openssl-blacklist tcl-tclreadline totem-mozilla gromit tracker-gui ubuntu-sso-client-gui
  ubuntuone-client-proxy ubuntuone-control-panel-gui bsd-mailx vinagre mesa-utils fonts-lyx fonts-stix xorg-docs xfonts-100dpi xfonts-75dpi
  xfonts-cyrillic
Recommended packages:
  libc-dbg ubuntu-control-center-signon
The following NEW packages will be installed:
  account-plugin-aim account-plugin-facebook account-plugin-google account-plugin-jabber account-plugin-salut account-plugin-windows-live
  account-plugin-yahoo acpi-support acpid aisleriot alsa-base alsa-utils anacron app-install-data app-install-data-partner apport apport-gtk
  apport-symptoms aptdaemon-data apturl apturl-common argyll avahi-autoipd baobab bc bluez-alsa bluez-cups bluez-gstreamer brasero brasero-cdrkit
  brasero-common brltty cheese cups cups-browsed cups-bsd cups-client cups-common cups-core-drivers cups-daemon cups-filters
  cups-filters-core-drivers cups-ppdc cups-server-common dc dconf-editor deja-dup deja-dup-backend-cloudfiles deja-dup-backend-gvfs
  deja-dup-backend-s3 deja-dup-backend-ubuntuone duplicity dvd+rw-tools empathy empathy-common eog espeak-data evince evince-common evolution
  evolution-common evolution-indicator evolution-plugins file-roller firefox fonts-cantarell fonts-droid fonts-freefont-ttf fonts-kacst
  fonts-kacst-one fonts-khmeros-core fonts-lao fonts-liberation fonts-lklug-sinhala fonts-nanum fonts-opensymbol fonts-sil-abyssinica
  fonts-sil-padauk fonts-takao-pgothic fonts-thai-tlwg fonts-tibetan-machine fonts-tlwg-garuda fonts-tlwg-kinnari fonts-tlwg-loma fonts-tlwg-mono
  fonts-tlwg-norasi fonts-tlwg-purisa fonts-tlwg-sawasdee fonts-tlwg-typewriter fonts-tlwg-typist fonts-tlwg-typo fonts-tlwg-umpush fonts-tlwg-waree
  foomatic-db-compressed-ppds gcc gcc-4.8 gdb gedit gedit-common genisoimage geoclue ghostscript ghostscript-x gir1.2-clutter-gst-2.0
  gir1.2-dbusmenu-glib-0.4 gir1.2-dee-1.0 gir1.2-evince-3.0 gir1.2-gdata-0.0 gir1.2-gnomekeyring-1.0 gir1.2-goa-1.0 gir1.2-gst-plugins-base-1.0
  gir1.2-gstreamer-1.0 gir1.2-gtkclutter-1.0 gir1.2-gtksource-3.0 gir1.2-gtop-2.0 gir1.2-gudev-1.0 gir1.2-javascriptcoregtk-3.0 gir1.2-peas-1.0
  gir1.2-rb-3.0 gir1.2-rest-0.7 gir1.2-secret-1 gir1.2-syncmenu-0.1 gir1.2-totem-1.0 gir1.2-totem-plparser-1.0 gir1.2-tracker-0.16 gir1.2-udisks-2.0
  gir1.2-unity-5.0 gir1.2-vte-2.90 gir1.2-webkit-3.0 gir1.2-wnck-3.0 gir1.2-zpj-0.0 gnome-backgrounds gnome-calculator gnome-color-manager
  gnome-disk-utility gnome-documents gnome-font-viewer gnome-icon-theme-extras gnome-mahjongg gnome-mines gnome-online-accounts gnome-online-miners
  gnome-orca gnome-screenshot gnome-session-canberra gnome-shell-extensions gnome-sudoku gnome-sushi gnome-system-log gnome-system-monitor
  gnome-terminal gnome-terminal-data gnome-tweak-tool gnome-video-effects growisofs gsfonts gstreamer0.10-alsa gstreamer0.10-nice
  gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-x gstreamer1.0-alsa gstreamer1.0-nice gstreamer1.0-pulseaudio gucharmap
  guile-2.0-libs gvfs-backends-goa gvfs-bin gvfs-fuse hplip hplip-data humanity-icon-theme ibus-pinyin ibus-table indicator-sync inputattach
  intel-gpu-tools iproute itstool kerneloops-daemon libaccount-plugin-1.0-0 libaccount-plugin-generic-oauth libaccount-plugin-google
  libaccounts-qt5-1 libart-2.0-2 libasan0 libassuan0 libatk-adaptor libatkmm-1.6-1 libatomic1 libavahi-gobject0 libboost-date-time1.54.0
  libboost-system1.54.0 libbrasero-media3-1 libbrlapi0.6 libburn4 libc-dev-bin libc6-dbg libc6-dev libcairomm-1.0-1 libcanberra-gtk-module
  libcanberra-gtk0 libcdr-0.0-0 libclucene-contribs1 libclucene-core1 libcmis-0.4-4 libcolamd2.8.0 libcolord-gtk1 libcrypt-passwdmd5-perl
  libcupscgi1 libcupsfilters1 libcupsimage2 libcupsmime1 libcupsppdc1 libcurl3 libdbusmenu-gtk4 libdjvulibre-text libdjvulibre21
  libdmapsharing-3.0-2 libdotconf0 libenca0 libencode-locale-perl liberror-perl libespeak1 libevdocument3-4 libevent-2.0-5 libevolution libevview3-3
  libexempi3 libexiv2-12 libexttextcat-2.0-0 libexttextcat-data libfarstream-0.1-0 libfarstream-0.2-2 libfile-copy-recursive-perl
  libfile-desktopentry-perl libfile-listing-perl libfile-mimeinfo-perl libfont-afm-perl libfontembed1 libframe6 libfs6 libgail-3-0 libgail-common
  libgail18 libgc1c2 libgcc-4.8-dev libgeis1 libgexiv2-2 libgif4 libgles2-mesa libglibmm-2.4-1c2a libgmime-2.6-0 libgpgme11 libgpod-common libgpod4
  libgrail6 libgrilo-0.2-1 libgrip0 libgs9 libgs9-common libgsf-1-114 libgsf-1-common libgssdp-1.0-3 libgtkhtml-4.0-0 libgtkhtml-4.0-common
  libgtkhtml-editor-4.0-0 libgtkmm-3.0-1 libgtksourceview-3.0-1 libgtksourceview-3.0-common libgucharmap-2-90-7 libgupnp-1.0-4 libgupnp-igd-1.0-4
  libgutenprint2 libgxps2 libhpmud0 libhtml-form-perl libhtml-format-perl libhtml-parser-perl libhtml-tagset-perl libhtml-tree-perl
  libhttp-cookies-perl libhttp-daemon-perl libhttp-date-perl libhttp-message-perl libhttp-negotiate-perl libhyphen0 libicc2 libido3-0.1-0
  libijs-0.35 libimdi0 libio-html-perl libiptcdata0 libisofs6 libitm1 libiw30 libjbig2dec0 libjte1 libkpathsea6 liblangtag-common liblangtag1
  liblircclient0 liblouis-data liblouis2 liblua5.2-0 liblwp-mediatypes-perl liblwp-protocol-https-perl libmail-spf-perl libmeanwhile1
  libmessaging-menu0 libmhash2 libminiupnpc8 libmspub-0.0-0 libmusicbrainz5-0 libmythes-1.2-0 libnatpmp1 libnautilus-extension1a libneon27-gnutls
  libnet-http-perl libnetaddr-ip-perl libnice10 libnotify-bin libnss-myhostname libopencc1 liborcus-0.6-0 libpangomm-1.4-1 libpaper-utils libpaper1
  libpeas-1.0-0 libpeas-common libperl5.18 libpoppler-glib8 libpoppler44 libportaudio2 libproxy1-plugin-gsettings libproxy1-plugin-networkmanager
  libpst4 libpurple-bin libpurple0 libpython3.4 libpyzy-1.0-0 libqpdf13 libqt5core5a libqt5dbus5 libqt5gui5 libqt5network5 libqt5opengl5
  libqt5positioning5 libqt5printsupport5 libqt5qml5 libqt5quick5 libqt5sensors5 libqt5sql5 libqt5sql5-sqlite libqt5test5 libqt5webkit5
  libqt5widgets5 libqt5xml5 libquadmath0 libraptor2-0 librasqal3 libraw9 librdf0 libreoffice-avmedia-backend-gstreamer libreoffice-base-core
  libreoffice-calc libreoffice-common libreoffice-core libreoffice-draw libreoffice-gnome libreoffice-gtk libreoffice-impress libreoffice-math
  libreoffice-ogltrans libreoffice-pdfimport libreoffice-presentation-minimizer libreoffice-style-galaxy libreoffice-style-human
  libreoffice-style-tango libreoffice-writer librhythmbox-core8 librsync1 libsane-hpaio libsbc1 libsensors4 libsgutils2-2 libsignon-extension1
  libsignon-plugins-common1 libsignon-qt5-1 libsnmp-base libsnmp30 libsonic0 libspectre1 libspeechd2 libsync-menu1 libsys-hostname-long-perl libt1-5
  libtcl8.6 libtelepathy-farstream3 libtk8.6 libtotem-plparser18 libtotem0 libtracker-extract-0.16-0 libtracker-miner-0.16-0
  libtracker-sparql-0.16-0 libunity-protocol-private0 libunity-scopes-json-def-desktop libunity9 libutempter0 libvisio-0.0-0 libvte-2.90-9
  libvte-2.90-common libwebpmux1 libwhoopsie0 libwmf0.2-7 libwmf0.2-7-gtk libwnck-3-0 libwnck-3-common libwpd-0.9-9 libwpg-0.2-2 libwps-0.2-2
  libwww-perl libwww-robotrules-perl libxcb-randr0 libxcb-render-util0 libxcb-xkb1 libxml2-utils libxp6 libxres1 libxss1 libyajl2 libytnef0
  libzapojit-0.0-0 libzeitgeist-1.0-1 libzephyr4 linux-libc-dev linux-sound-base lp-solve manpages-dev mcp-account-manager-goa
  mcp-account-manager-uoa media-player-info memtest86+ mscompress mtools mutter nautilus nautilus-sendto nautilus-sendto-empathy nautilus-share
  oneconf oneconf-common openprinting-ppds pcmciautils plymouth-label plymouth-theme-ubuntu-gnome-logo plymouth-theme-ubuntu-gnome-text
  policykit-desktop-privileges poppler-data poppler-utils printer-driver-c2esp printer-driver-foo2zjs printer-driver-foo2zjs-common
  printer-driver-gutenprint printer-driver-hpcups printer-driver-min12xxw printer-driver-pnm2ppa printer-driver-postscript-hp printer-driver-ptouch
  printer-driver-pxljr printer-driver-sag-gdi printer-driver-splix pulseaudio-module-bluetooth python-aptdaemon python-aptdaemon.gtk3widgets
  python-boto python-cloudfiles python-commandnotfound python-configglue python-crypto python-debtagshw python-defer python-dirspec python-gdbm
  python-gi-cairo python-httplib2 python-ibus python-imaging python-ldb python-lockfile python-lxml python-ntdb python-oauthlib python-oneconf
  python-openssl python-pam python-pexpect python-pil python-piston-mini-client python-pkg-resources python-protobuf python-pyinotify
  python-renderpm python-reportlab python-reportlab-accel python-requests python-samba python-serial python-tdb python-twisted-bin
  python-twisted-core python-twisted-names python-twisted-web python-ubuntu-sso-client python-ubuntuone-client python-ubuntuone-control-panel
  python-ubuntuone-storageprotocol python-urllib3 python-zope.interface python3-apport python3-aptdaemon.gtk3widgets python3-brlapi python3-cairo
  python3-chardet python3-crypto python3-debian python3-dirspec python3-gi-cairo python3-httplib2 python3-louis python3-mako python3-markupsafe
  python3-oauthlib python3-oneconf python3-piston-mini-client python3-problem-report python3-pyatspi python3-pycurl python3-six
  python3-software-properties python3-speechd python3-uno python3-xdg python3-xkit qpdf re2c rfkill rhythmbox rhythmbox-data rhythmbox-mozilla
  rhythmbox-plugin-cdrecorder rhythmbox-plugin-magnatune rhythmbox-plugin-zeitgeist rhythmbox-plugins rhythmbox-ubuntuone sa-compile samba-common
  samba-common-bin sane-utils seahorse sessioninstaller shotwell shotwell-common signon-keyring-extension signon-plugin-oauth2
  signon-plugin-password signon-ui signond simple-scan smbclient software-center software-center-aptdaemon-plugins software-properties-common
  software-properties-gtk spamassassin spamc speech-dispatcher speech-dispatcher-audio-plugins ssh-askpass-gnome ssl-cert syslinux syslinux-common
  syslinux-legacy tcl tcl8.6 telepathy-gabble telepathy-haze telepathy-idle telepathy-logger telepathy-salut tk tk8.6 toshset totem totem-common
  totem-plugins tracker tracker-extract tracker-miner-fs tracker-utils transmission-common transmission-gtk ttf-indic-fonts-core ttf-punjabi-fonts
  ttf-ubuntu-font-family ubuntu-drivers-common ubuntu-extras-keyring ubuntu-gnome-default-settings ubuntu-gnome-desktop ubuntu-release-upgrader-gtk
  ubuntu-sso-client ubuntuone-client ubuntuone-client-data ubuntuone-control-panel unattended-upgrades unity-asset-pool unity-control-center-signon
  uno-libs3 unoconv update-inetd update-manager update-notifier update-notifier-common ure usb-creator-common usb-creator-gtk vino whoopsie
  wireless-tools wodim x11-apps x11-session-utils x11-xfs-utils xbitmaps xdg-user-dirs xdg-user-dirs-gtk xdg-utils xdiagnose xfonts-mathml
  xfonts-scalable xinit xinput xorg xorg-docs-core xsltproc xterm xul-ext-ubufox yelp-tools zip zsync
0 upgraded, 650 newly installed, 0 to remove and 11 not upgraded.
Need to get 307 MB/309 MB of archives.
After this operation, 1,131 MB of additional disk space will be used.
Do you want to continue? [Y/n] n
Abort.
root@lance-desktop:/# 

```

Time for more math and parsing :)

Nope, still 1235 packages :(

---

### Post by kansasnoob on 2014-04-03
Repeating some tests with the latest netboot image. I'm excluding theses updates:

```
root@lance-desktop:/# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  file libglib2.0-0 libglib2.0-data libmagic1 libpam-systemd libplymouth2
  libsystemd-daemon0 libsystemd-login0 libudev1 plymouth
  plymouth-theme-ubuntu-text systemd-services udev
13 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 2,564 kB of archives.
After this operation, 2,048 B of additional disk space will be used.
Do you want to continue? [Y/n] n
Abort.

```

---

### Post by kansasnoob on 2014-04-03
Package count is going down:

```
root@lance-desktop:/# apt-get install ubuntu-gnome-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  account-plugin-aim account-plugin-facebook account-plugin-google account-plugin-jabber account-plugin-salut account-plugin-windows-live
  account-plugin-yahoo acl acpi-support acpid aisleriot alsa-base alsa-utils anacron apg app-install-data app-install-data-partner apport apport-gtk
  apport-symptoms aptdaemon aptdaemon-data apturl apturl-common argyll aspell aspell-en at-spi2-core avahi-autoipd avahi-daemon avahi-utils baobab
  bc binutils bluez bluez-alsa bluez-cups brasero brasero-cdrkit brasero-common brltty cheese cheese-common colord cpp cpp-4.8 cracklib-runtime cups
  cups-browsed cups-bsd cups-client cups-common cups-core-drivers cups-daemon cups-filters cups-filters-core-drivers cups-pk-helper cups-ppdc
  cups-server-common dbus-x11 dc dconf-cli dconf-editor dconf-gsettings-backend dconf-service deja-dup deja-dup-backend-cloudfiles
  deja-dup-backend-gvfs deja-dup-backend-s3 desktop-file-utils dialog dictionaries-common diffstat dnsmasq-base duplicity dvd+rw-tools empathy
  empathy-common enchant eog espeak-data evince evince-common evolution evolution-common evolution-data-server evolution-data-server-common
  evolution-data-server-online-accounts evolution-indicator evolution-plugins file-roller firefox folks-common fontconfig fontconfig-config
  fonts-cantarell fonts-dejavu-core fonts-droid fonts-freefont-ttf fonts-kacst fonts-kacst-one fonts-khmeros-core fonts-lao fonts-liberation
  fonts-lklug-sinhala fonts-nanum fonts-opensymbol fonts-sil-abyssinica fonts-sil-padauk fonts-takao-pgothic fonts-thai-tlwg fonts-tibetan-machine
  fonts-tlwg-garuda fonts-tlwg-kinnari fonts-tlwg-loma fonts-tlwg-mono fonts-tlwg-norasi fonts-tlwg-purisa fonts-tlwg-sawasdee fonts-tlwg-typewriter
  fonts-tlwg-typist fonts-tlwg-typo fonts-tlwg-umpush fonts-tlwg-waree foomatic-db-compressed-ppds gcc gcc-4.8 gconf-service gconf-service-backend
  gconf2 gconf2-common gcr gdb gdisk gdm gedit gedit-common genisoimage geoclue gettext ghostscript ghostscript-x gir1.2-accountsservice-1.0
  gir1.2-atk-1.0 gir1.2-atspi-2.0 gir1.2-caribou-1.0 gir1.2-clutter-1.0 gir1.2-clutter-gst-2.0 gir1.2-cogl-1.0 gir1.2-coglpango-1.0
  gir1.2-dbusmenu-glib-0.4 gir1.2-dee-1.0 gir1.2-evince-3.0 gir1.2-freedesktop gir1.2-gck-1 gir1.2-gcr-3 gir1.2-gdata-0.0 gir1.2-gdesktopenums-3.0
  gir1.2-gdkpixbuf-2.0 gir1.2-gdm-1.0 gir1.2-gkbd-3.0 gir1.2-gmenu-3.0 gir1.2-gnomebluetooth-1.0 gir1.2-gnomedesktop-3.0 gir1.2-gnomekeyring-1.0
  gir1.2-goa-1.0 gir1.2-gst-plugins-base-1.0 gir1.2-gstreamer-1.0 gir1.2-gtk-3.0 gir1.2-gtkclutter-1.0 gir1.2-gtksource-3.0 gir1.2-gtop-2.0
  gir1.2-gudev-1.0 gir1.2-ibus-1.0 gir1.2-javascriptcoregtk-3.0 gir1.2-json-1.0 gir1.2-mutter-3.0 gir1.2-networkmanager-1.0 gir1.2-nmgtk-1.0
  gir1.2-notify-0.7 gir1.2-packagekitglib-1.0 gir1.2-pango-1.0 gir1.2-peas-1.0 gir1.2-polkit-1.0 gir1.2-rb-3.0 gir1.2-rest-0.7 gir1.2-secret-1
  gir1.2-soup-2.4 gir1.2-telepathyglib-0.12 gir1.2-telepathylogger-0.2 gir1.2-totem-1.0 gir1.2-totem-plparser-1.0 gir1.2-tracker-0.16
  gir1.2-udisks-2.0 gir1.2-unity-5.0 gir1.2-upowerglib-1.0 gir1.2-vte-2.90 gir1.2-webkit-3.0 gir1.2-wnck-3.0 gir1.2-xkl-1.0 gir1.2-zpj-0.0 gjs
  gkbd-capplet glib-networking glib-networking-common glib-networking-services gnome-accessibility-themes gnome-backgrounds gnome-bluetooth
  gnome-calculator gnome-color-manager gnome-contacts gnome-control-center gnome-control-center-data gnome-control-center-shared-data
  gnome-desktop3-data gnome-disk-utility gnome-documents gnome-font-viewer gnome-icon-theme gnome-icon-theme-extras gnome-icon-theme-full
  gnome-icon-theme-symbolic gnome-keyring gnome-mahjongg gnome-menus gnome-mines gnome-online-accounts gnome-online-miners gnome-orca
  gnome-screenshot gnome-session gnome-session-bin gnome-session-canberra gnome-session-common gnome-settings-daemon gnome-settings-daemon-schemas
  gnome-shell gnome-shell-common gnome-shell-extensions gnome-sudoku gnome-sushi gnome-system-log gnome-system-monitor gnome-terminal
  gnome-terminal-data gnome-themes-standard gnome-themes-standard-data gnome-tweak-tool gnome-user-guide gnome-user-share gnome-video-effects
  growisofs gsettings-desktop-schemas gsettings-ubuntu-schemas gsfonts gstreamer0.10-alsa gstreamer0.10-nice gstreamer0.10-plugins-base
  gstreamer0.10-plugins-good gstreamer0.10-pulseaudio gstreamer0.10-x gstreamer1.0-alsa gstreamer1.0-clutter gstreamer1.0-nice
  gstreamer1.0-plugins-base gstreamer1.0-plugins-good gstreamer1.0-pulseaudio gstreamer1.0-x gtk2-engines-pixbuf gucharmap guile-2.0-libs gvfs
  gvfs-backends gvfs-backends-goa gvfs-bin gvfs-common gvfs-daemons gvfs-fuse gvfs-libs hardening-includes hicolor-icon-theme hplip hplip-data
  humanity-icon-theme hunspell-en-us hwdata ibus ibus-gtk ibus-gtk3 ibus-pinyin ibus-table im-config indicator-application inputattach
  intel-gpu-tools intltool-debian iproute iputils-arping itstool kerneloops-daemon libaa1 libaccount-plugin-1.0-0 libaccount-plugin-generic-oauth
  libaccount-plugin-google libaccounts-glib0 libaccounts-qt5-1 libappindicator3-1 libapt-pkg-perl libarchive-zip-perl libarchive13 libart-2.0-2
  libasan0 libasound2 libasound2-data libasound2-plugins libaspell15 libasprintf-dev libassuan0 libasyncns0 libatasmart4 libatk-adaptor
  libatk-bridge2.0-0 libatk1.0-0 libatk1.0-data libatkmm-1.6-1 libatomic1 libatspi2.0-0 libauthen-sasl-perl libautodie-perl libavahi-client3
  libavahi-common-data libavahi-common3 libavahi-core7 libavahi-glib1 libavahi-gobject0 libavc1394-0 libbluetooth3 libboost-date-time1.54.0
  libboost-system1.54.0 libbrasero-media3-1 libbrlapi0.6 libburn4 libc-dev-bin libc6-dbg libc6-dev libcaca0 libcairo-gobject2 libcairo2
  libcairomm-1.0-1 libcamel-1.2-45 libcanberra-gtk-module libcanberra-gtk0 libcanberra-gtk3-0 libcanberra-gtk3-module libcanberra-pulse libcanberra0
  libcaribou-common libcaribou0 libcdio-cdda1 libcdio-paranoia1 libcdio13 libcdparanoia0 libcdr-0.0-0 libcheese-gtk23 libcheese7 libclone-perl
  libcloog-isl4 libclucene-contribs1 libclucene-core1 libclutter-1.0-0 libclutter-1.0-common libclutter-gst-2.0-0 libclutter-gtk-1.0-0 libcmis-0.4-4
  libcogl-common libcogl-pango15 libcogl15 libcolamd2.8.0 libcolord-gtk1 libcolord1 libcolorhug1 libcrack2 libcroco3 libcrypt-passwdmd5-perl
  libcups2 libcupscgi1 libcupsfilters1 libcupsimage2 libcupsmime1 libcupsppdc1 libcurl3 libdaemon0 libdatrie1 libdbusmenu-glib4 libdbusmenu-gtk3-4
  libdbusmenu-gtk4 libdconf1 libdee-1.0-4 libdigest-hmac-perl libdjvulibre-text libdjvulibre21 libdmapsharing-3.0-2 libdotconf0 libdpkg-perl
  libdrm-intel1 libdrm-nouveau2 libdrm-radeon1 libdv4 libebackend-1.2-7 libebook-1.2-14 libebook-contacts-1.2-0 libecal-1.2-16 libedata-book-1.2-20
  libedata-cal-1.2-23 libedataserver-1.2-18 libegl1-mesa libegl1-mesa-drivers libelfg0 libemail-valid-perl libenca0 libenchant1c2a
  libencode-locale-perl liberror-perl libespeak1 libevdocument3-4 libevent-2.0-5 libevolution libevview3-3 libexempi3 libexif12 libexiv2-12
  libexttextcat-2.0-0 libexttextcat-data libfarstream-0.1-0 libfarstream-0.2-2 libfftw3-single3 libfile-basedir-perl libfile-copy-recursive-perl
  libfile-desktopentry-perl libfile-fcntllock-perl libfile-listing-perl libfile-mimeinfo-perl libflac8 libfolks-eds25 libfolks-telepathy25
  libfolks25 libfont-afm-perl libfontconfig1 libfontembed1 libfontenc1 libframe6 libfs6 libgail-3-0 libgail-common libgail18 libgbm1 libgc1c2
  libgcc-4.8-dev libgconf-2-4 libgcr-ui-3-1 libgd3 libgdata-common libgdata13 libgdk-pixbuf2.0-0 libgdk-pixbuf2.0-common libgdm1 libgee-0.8-2
  libgeis1 libgeoclue0 libgettextpo-dev libgettextpo0 libgexiv2-2 libgif4 libgjs0e libgl1-mesa-dri libgl1-mesa-glx libglamor0 libglapi-mesa
  libgles2-mesa libglib2.0-0 libglib2.0-bin libglibmm-2.4-1c2a libglu1-mesa libgmime-2.6-0 libgmp10 libgnome-bluetooth11 libgnome-control-center1
  libgnome-desktop-3-7 libgnome-keyring-common libgnome-keyring0 libgnome-menu-3-0 libgnomekbd-common libgnomekbd8 libgoa-1.0-0b libgoa-1.0-common
  libgoa-backend-1.0-1 libgomp1 libgpgme11 libgphoto2-6 libgphoto2-l10n libgphoto2-port10 libgpm2 libgpod-common libgpod4 libgrail6 libgraphite2-3
  libgrilo-0.2-1 libgrip0 libgs9 libgs9-common libgsf-1-114 libgsf-1-common libgssdp-1.0-3 libgstreamer-plugins-base0.10-0
  libgstreamer-plugins-base1.0-0 libgstreamer-plugins-good1.0-0 libgstreamer0.10-0 libgstreamer1.0-0 libgtk-3-0 libgtk-3-bin libgtk-3-common
  libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libgtkhtml-4.0-0 libgtkhtml-4.0-common libgtkhtml-editor-4.0-0 libgtkmm-3.0-1 libgtksourceview-3.0-1
  libgtksourceview-3.0-common libgtop2-7 libgtop2-common libgucharmap-2-90-7 libgudev-1.0-0 libgupnp-1.0-4 libgupnp-igd-1.0-4 libgusb2
  libgutenprint2 libgweather-3-6 libgweather-common libgxps2 libharfbuzz-icu0 libharfbuzz0b libhpmud0 libhtml-form-perl libhtml-format-perl
  libhtml-parser-perl libhtml-tagset-perl libhtml-tree-perl libhttp-cookies-perl libhttp-daemon-perl libhttp-date-perl libhttp-message-perl
  libhttp-negotiate-perl libhunspell-1.3-0 libhyphen0 libibus-1.0-5 libical1 libicc2 libice6 libicu52 libido3-0.1-0 libiec61883-0 libieee1284-3
  libijs-0.35 libimdi0 libimobiledevice4 libindicator3-7 libio-html-perl libio-pty-perl libio-socket-inet6-perl libio-socket-ssl-perl
  libipc-run-perl libipc-system-simple-perl libiptcdata0 libisl10 libisofs6 libitm1 libiw30 libjack-jackd2-0 libjasper1 libjavascriptcoregtk-3.0-0
  libjbig0 libjbig2dec0 libjpeg-turbo8 libjpeg8 libjson-glib-1.0-0 libjson-glib-1.0-common libjte1 libkpathsea6 liblangtag-common liblangtag1
  liblcms2-2 libldb1 liblircclient0 liblist-moreutils-perl libllvm3.4 liblouis-data liblouis2 libltdl7 liblua5.2-0 liblwp-mediatypes-perl
  liblwp-protocol-https-perl liblzo2-2 libmail-spf-perl libmailtools-perl libmbim-glib0 libmeanwhile1 libmessaging-menu0 libmhash2 libminiupnpc8
  libmission-control-plugins0 libmm-glib0 libmnl0 libmozjs-24-0 libmpc3 libmpfr4 libmspub-0.0-0 libmtdev1 libmtp-common libmtp-runtime libmtp9
  libmusicbrainz5-0 libmutter0c libmythes-1.2-0 libnatpmp1 libnautilus-extension1a libneon27-gnutls libnet-dns-perl libnet-domain-tld-perl
  libnet-http-perl libnet-ip-perl libnet-libidn-perl libnet-smtp-ssl-perl libnet-ssleay-perl libnetaddr-ip-perl libnetfilter-conntrack3 libnettle4
  libnice10 libnl-route-3-200 libnm-glib-vpn1 libnm-glib4 libnm-gtk-common libnm-gtk0 libnm-util2 libnotify-bin libnotify4 libnspr4 libnss-mdns
  libnss-myhostname libnss3 libnss3-nssdb libntdb1 liboauth0 libogg0 libopencc1 libopenobex1 libopenvg1-mesa liborc-0.4-0 liborcus-0.6-0
  libp11-kit-gnome-keyring libpackagekit-glib2-16 libpam-gnome-keyring libpango-1.0-0 libpango1.0-0 libpangocairo-1.0-0 libpangoft2-1.0-0
  libpangomm-1.4-1 libpangox-1.0-0 libpangoxft-1.0-0 libpaper-utils libpaper1 libpciaccess0 libpcsclite1 libpeas-1.0-0 libpeas-common libperl5.18
  libperlio-gzip-perl libpixman-1-0 libplist1 libplymouth2 libpolkit-agent-1-0 libpolkit-backend-1-0 libpoppler-glib8 libpoppler44 libportaudio2
  libproxy1 libproxy1-plugin-gsettings libproxy1-plugin-networkmanager libpst4 libpulse-mainloop-glib0 libpulse0 libpulsedsp libpurple-bin
  libpurple0 libpwquality-common libpwquality1 libpython2.7 libpython3.4 libpyzy-1.0-0 libqmi-glib0 libqpdf13 libqt5core5a libqt5dbus5 libqt5gui5
  libqt5network5 libqt5opengl5 libqt5positioning5 libqt5printsupport5 libqt5qml5 libqt5quick5 libqt5sensors5 libqt5sql5 libqt5sql5-sqlite
  libqt5test5 libqt5webkit5 libqt5widgets5 libqt5xml5 libquadmath0 libraptor2-0 librasqal3 libraw1394-11 libraw9 librdf0 libreadline5
  libreoffice-avmedia-backend-gstreamer libreoffice-base-core libreoffice-calc libreoffice-common libreoffice-core libreoffice-draw
  libreoffice-gnome libreoffice-gtk libreoffice-impress libreoffice-math libreoffice-ogltrans libreoffice-pdfimport
  libreoffice-presentation-minimizer libreoffice-style-galaxy libreoffice-style-human libreoffice-style-tango libreoffice-writer librest-0.7-0
  librhythmbox-core8 librsvg2-2 librsvg2-common librsync1 libsamplerate0 libsane libsane-common libsane-hpaio libsbc1 libsecret-1-0 libsecret-common
  libsensors4 libsgutils2-2 libshout3 libsignon-extension1 libsignon-glib1 libsignon-plugins-common1 libsignon-qt5-1 libsm6 libsmbclient libsndfile1
  libsnmp-base libsnmp30 libsocket6-perl libsonic0 libsoup-gnome2.4-1 libsoup2.4-1 libspectre1 libspeechd2 libspeex1 libspeexdsp1
  libstartup-notification0 libsub-identify-perl libsys-hostname-long-perl libsystemd-journal0 libt1-5 libtag1-vanilla libtag1c2a libtalloc2
  libtcl8.6 libtdb1 libtelepathy-farstream3 libtelepathy-glib0 libtelepathy-logger3 libtevent0 libtext-levenshtein-perl libthai-data libthai0
  libtheora0 libtiff5 libtimezonemap1 libtk8.6 libtotem-plparser18 libtotem0 libtracker-extract-0.16-0 libtracker-miner-0.16-0
  libtracker-sparql-0.16-0 libtxc-dxtn-s2tc0 libudisks2-0 libunistring0 libunity-control-center1 libunity-protocol-private0
  libunity-scopes-json-def-desktop libunity9 libupower-glib1 liburi-perl libusbmuxd2 libutempter0 libv4l-0 libv4lconvert0 libvisio-0.0-0
  libvisual-0.4-0 libvisual-0.4-plugins libvorbis0a libvorbisenc2 libvorbisfile3 libvpx1 libvte-2.90-9 libvte-2.90-common libwacom-common libwacom2
  libwavpack1 libwayland-client0 libwayland-cursor0 libwayland-egl1-mesa libwayland-server0 libwbclient0 libwebkitgtk-3.0-0 libwebkitgtk-3.0-common
  libwebp5 libwebpmux1 libwhoopsie0 libwmf0.2-7 libwmf0.2-7-gtk libwnck-3-0 libwnck-3-common libwpd-0.9-9 libwpg-0.2-2 libwps-0.2-2 libwrap0
  libwww-perl libwww-robotrules-perl libx11-xcb1 libxatracker2 libxaw7 libxcb-dri2-0 libxcb-dri3-0 libxcb-glx0 libxcb-icccm4 libxcb-image0
  libxcb-keysyms1 libxcb-present0 libxcb-randr0 libxcb-render-util0 libxcb-render0 libxcb-shape0 libxcb-shm0 libxcb-sync1 libxcb-util0
  libxcb-xf86dri0 libxcb-xfixes0 libxcb-xkb1 libxcb-xv0 libxcomposite1 libxcursor1 libxdamage1 libxfixes3 libxfont1 libxft2 libxi6 libxinerama1
  libxkbcommon0 libxkbfile1 libxklavier16 libxml2-utils libxmu6 libxp6 libxpm4 libxrandr2 libxrender1 libxres1 libxshmfence1 libxslt1.1 libxss1
  libxt6 libxtst6 libxv1 libxvmc1 libxxf86dga1 libxxf86vm1 libyajl2 libyelp0 libytnef0 libzapojit-0.0-0 libzeitgeist-1.0-1 libzeitgeist-2.0-0
  libzephyr4 lintian linux-libc-dev linux-sound-base lp-solve make manpages-dev mcp-account-manager-goa mcp-account-manager-uoa media-player-info
  memtest86+ mobile-broadband-provider-info modemmanager mousetweaks mscompress mtools mutter mutter-common nautilus nautilus-data nautilus-sendto
  nautilus-sendto-empathy nautilus-share network-manager network-manager-gnome network-manager-pptp network-manager-pptp-gnome notification-daemon
  obex-data-server obexd-client oneconf oneconf-common openprinting-ppds p11-kit p11-kit-modules patch patchutils pcmciautils plymouth
  plymouth-label plymouth-theme-ubuntu-gnome-logo plymouth-theme-ubuntu-gnome-text policykit-1 policykit-1-gnome policykit-desktop-privileges
  poppler-data poppler-utils pptp-linux printer-driver-c2esp printer-driver-foo2zjs printer-driver-foo2zjs-common printer-driver-gutenprint
  printer-driver-hpcups printer-driver-min12xxw printer-driver-pnm2ppa printer-driver-postscript-hp printer-driver-ptouch printer-driver-pxljr
  printer-driver-sag-gdi printer-driver-splix pulseaudio pulseaudio-module-bluetooth pulseaudio-module-x11 pulseaudio-utils python-aptdaemon
  python-aptdaemon.gtk3widgets python-boto python-cairo python-cloudfiles python-commandnotfound python-crypto python-cups python-cupshelpers
  python-dbus python-dbus-dev python-debtagshw python-defer python-dirspec python-gdbm python-gi python-gi-cairo python-gnomekeyring python-gobject
  python-gobject-2 python-gtk2 python-httplib2 python-ibus python-imaging python-ldb python-libxml2 python-lockfile python-lxml python-notify
  python-ntdb python-oauthlib python-oneconf python-openssl python-pam python-pexpect python-pil python-piston-mini-client python-pkg-resources
  python-pycurl python-renderpm python-reportlab python-reportlab-accel python-requests python-samba python-serial python-smbc python-talloc
  python-tdb python-twisted-bin python-twisted-core python-twisted-web python-ubuntu-sso-client python-urllib3 python-xdg python-zeitgeist
  python-zope.interface python3-apport python3-aptdaemon python3-aptdaemon.gtk3widgets python3-aptdaemon.pkcompat python3-brlapi python3-cairo
  python3-chardet python3-crypto python3-debian python3-defer python3-gi-cairo python3-httplib2 python3-louis python3-mako python3-markupsafe
  python3-oauthlib python3-oneconf python3-piston-mini-client python3-pkg-resources python3-problem-report python3-pyatspi python3-pycurl
  python3-six python3-software-properties python3-speechd python3-uno python3-xdg python3-xkit qpdf re2c rfkill rhythmbox rhythmbox-data
  rhythmbox-mozilla rhythmbox-plugin-cdrecorder rhythmbox-plugin-magnatune rhythmbox-plugin-zeitgeist rhythmbox-plugins rtkit sa-compile
  samba-common samba-common-bin samba-libs sane-utils seahorse session-migration sessioninstaller shotwell shotwell-common signon-keyring-extension
  signon-plugin-oauth2 signon-plugin-password signon-ui signond simple-scan smbclient software-center software-center-aptdaemon-plugins
  software-properties-common software-properties-gtk sound-theme-freedesktop spamassassin spamc speech-dispatcher speech-dispatcher-audio-plugins
  ssh-askpass-gnome ssl-cert syslinux syslinux-common syslinux-legacy system-config-printer-common system-config-printer-gnome
  system-config-printer-udev t1utils tcl tcl8.6 tcpd telepathy-gabble telepathy-haze telepathy-idle telepathy-logger telepathy-mission-control-5
  telepathy-salut tk tk8.6 toshset totem totem-common totem-plugins tracker tracker-extract tracker-miner-fs tracker-utils transmission-common
  transmission-gtk ttf-indic-fonts-core ttf-punjabi-fonts ttf-ubuntu-font-family ubuntu-drivers-common ubuntu-extras-keyring
  ubuntu-gnome-default-settings ubuntu-release-upgrader-gtk ubuntu-sso-client ubuntu-system-service udisks2 unattended-upgrades unity-asset-pool
  unity-control-center unity-control-center-signon unity-settings-daemon uno-libs3 unoconv unzip update-inetd update-manager update-notifier
  update-notifier-common upower ure usb-creator-common usb-creator-gtk usb-modeswitch usb-modeswitch-data usbmuxd vino wamerican whoopsie
  wireless-tools wodim wpasupplicant x11-apps x11-common x11-session-utils x11-utils x11-xfs-utils x11-xkb-utils x11-xserver-utils xbitmaps
  xdg-user-dirs xdg-user-dirs-gtk xdg-utils xdiagnose xfonts-base xfonts-encodings xfonts-mathml xfonts-scalable xfonts-utils xinit xinput xorg
  xorg-docs-core xserver-common xserver-xephyr xserver-xorg xserver-xorg-core xserver-xorg-input-all xserver-xorg-input-evdev
  xserver-xorg-input-mouse xserver-xorg-input-synaptics xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-all
  xserver-xorg-video-ati xserver-xorg-video-cirrus xserver-xorg-video-fbdev xserver-xorg-video-glamoregl xserver-xorg-video-intel
  xserver-xorg-video-mach64 xserver-xorg-video-mga xserver-xorg-video-modesetting xserver-xorg-video-neomagic xserver-xorg-video-nouveau
  xserver-xorg-video-openchrome xserver-xorg-video-qxl xserver-xorg-video-r128 xserver-xorg-video-radeon xserver-xorg-video-s3
  xserver-xorg-video-savage xserver-xorg-video-siliconmotion xserver-xorg-video-sis xserver-xorg-video-sisusb xserver-xorg-video-tdfx
  xserver-xorg-video-trident xserver-xorg-video-vesa xserver-xorg-video-vmware xsltproc xterm xul-ext-ubufox yelp yelp-tools yelp-xsl zeitgeist
  zeitgeist-core zeitgeist-datahub zenity zenity-common zip zsync
Suggested packages:
  gnome-cards-data apmd alsa-oss oss-compat default-mta mail-transport-agent libgtk2-perl gir1.2-colordgtk-1.0 aspell-doc spellutils binutils-doc
  bluez-hcidump vcdimager libdvdcss2 dvdauthor readom brltty-speechd brltty-x11 console-braille gnome-video-effects-frei0r gnome-video-effects-extra
  cpp-doc gcc-4.8-locales cups-pdf xpp wordlist emacsen-common jed-extra python-paramiko ncftp lftp python-gdata tahoe-lafs python-swiftclient
  cdrskin unrar evolution-ews evolution-plugins-experimental evolution-data-server-dbg arj lha lzip lzop ncompress p7zip-full rpm2cpio rzip
  sharutils unace unalz unar zoo ttf-lyx libgraphite3 pango-graphite hplip-cups printer-driver-all gcc-multilib autoconf automake1.9 libtool flex
  bison gcc-doc gcc-4.8-multilib gcc-4.8-doc libgcc1-dbg libgomp1-dbg libitm1-dbg libatomic1-dbg libasan0-dbg libtsan0-dbg libbacktrace1-dbg
  libquadmath0-dbg binutils-gold gconf-defaults-service gdb-doc gdbserver gedit-plugins cdrkit-doc gettext-doc hpijs gnome-screensaver xscreensaver
  desktop-base metacity x-window-manager gstreamer1.0-libav apache2.2-bin libapache2-mod-dnssd hplip-gui hplip-doc system-config-printer hunspell
  openoffice.org-hunspell openoffice.org-core ibus-clutter ibus-doc ibus-qt4 lrzip libgssapi-perl gstreamer1.0-plugins-ugly cdrdao
  gstreamer1.0-fluendo-mp3 gstreamer1.0-plugins-bad glibc-doc debian-keyring libdv-bin libenchant-voikko exiv2 libfftw3-bin libfftw3-dev libgd-tools
  libglide3 gpgsm gphoto2 gtkam gpm grilo-plugins-0.2 gstreamer-codec-install gnome-codec-install gstreamer0.10-tools gstreamer1.0-tools
  gutenprint-locales libdata-dump-perl jackd2 libjasper-runtime liblcms2-utils lirc libcrypt-ssleay-perl minissdpd natpmp-utils ttf-baekmuk
  ttf-arphic-gbsn00lp ttf-arphic-bsmi00lp ttf-arphic-gkai00mp ttf-arphic-bkai00mp pcscd raptor2-utils rasqal-utils libraw1394-doc
  librdf-storage-postgresql librdf-storage-mysql librdf-storage-sqlite librdf-storage-virtuoso redland-utils libreoffice-base libopencl1
  libreoffice-style-crystal libreoffice-style-hicontrast libreoffice-style-oxygen libreoffice-style-sifr libreoffice-evolution crystalcursors
  kde-icons-crystal tango-icon-theme libreoffice-gcj libreoffice-java-common default-jre gcj-jre openjdk-7-jre openjdk-6-jre sun-java5-jre
  sun-java6-jre java5-runtime jre librsvg2-bin hpoj libsane-extras lm-sensors sg3-utils snmp-mibs-downloader libspectre1-dbg speex unity-common
  libauthen-ntlm-perl binutils-multiarch dpkg-dev libtext-template-perl libyaml-perl make-doc account-plugin-gadugadu account-plugin-groupwise
  account-plugin-icq account-plugin-irc account-plugin-mxit account-plugin-myspace account-plugin-sametime account-plugin-sip account-plugin-yahoojp
  account-plugin-zephyr hwtools memtester kernel-patch-badram memtest86 floppyd pidgin gajim samba network-manager-openconnect-gnome
  network-manager-openvpn-gnome network-manager-vpnc-gnome hpijs-ppds diffutils-doc fonts-japanese-mincho fonts-ipafont-mincho fonts-japanese-gothic
  fonts-ipafont-gothic fonts-arphic-ukai fonts-arphic-uming fonts-unfonts-core psutils hannah-foo2zjs tix gutenprint-doc magicfilter apsfilter
  pavumeter paman pavucontrol paprefs pulseaudio-module-raop pulseaudio-esound-compat python-crypto-dbg python-crypto-doc python-dbus-doc
  python-dbus-dbg python-gdbm-dbg python-gobject-2-dbg python-gtk2-doc python-lxml-dbg python-openssl-doc python-openssl-dbg python-pam-dbg
  python-pexpect-doc python-pil-doc python-pil-dbg python-distribute python-distribute-doc libcurl4-gnutls-dev python-pycurl-dbg python-renderpm-dbg
  pdf-viewer python-egenix-mxtexttools python-reportlab-doc python-wxgtk2.8 python-wxgtk python-twisted-bin-dbg python-tk python-glade2 python-qt3
  python3-launchpadlib python3-crypto-dbg python3-beaker python-mako-doc python3-setuptools python3-pycurl-dbg heimdal-clients unpaper
  account-plugin-flickr cifs-utils razor libdbi-perl pyzor libmail-dkim-perl libttspico-utils speech-dispatcher-doc-cs speech-dispatcher-festival
  speech-dispatcher-flite openssl-blacklist tcl-tclreadline totem-mozilla gromit tracker-gui ubuntu-sso-client-gui xfsprogs reiserfsprogs
  exfat-utils btrfs-tools mdadm cryptsetup-bin bsd-mailx comgt wvdial vinagre wpagui libengine-pkcs11-openssl mesa-utils nickle cairo-5c xfs xserver
  fonts-lyx fonts-stix xorg-docs xfonts-100dpi xfonts-75dpi gpointing-device-settings touchfreeze firmware-linux xfonts-cyrillic
Recommended packages:
  libc-dbg ubuntu-control-center-signon
**The following NEW packages will be installed:**
  account-plugin-aim account-plugin-facebook account-plugin-google account-plugin-jabber account-plugin-salut account-plugin-windows-live
  account-plugin-yahoo acl acpi-support acpid aisleriot alsa-base alsa-utils anacron apg app-install-data app-install-data-partner apport apport-gtk
  apport-symptoms aptdaemon aptdaemon-data apturl apturl-common argyll aspell aspell-en at-spi2-core avahi-autoipd avahi-daemon avahi-utils baobab
  bc binutils bluez bluez-alsa bluez-cups brasero brasero-cdrkit brasero-common brltty cheese cheese-common colord cpp cpp-4.8 cracklib-runtime cups
  cups-browsed cups-bsd cups-client cups-common cups-core-drivers cups-daemon cups-filters cups-filters-core-drivers cups-pk-helper cups-ppdc
  cups-server-common dbus-x11 dc dconf-cli dconf-editor dconf-gsettings-backend dconf-service deja-dup deja-dup-backend-cloudfiles
  deja-dup-backend-gvfs deja-dup-backend-s3 desktop-file-utils dialog dictionaries-common diffstat dnsmasq-base duplicity dvd+rw-tools empathy
  empathy-common enchant eog espeak-data evince evince-common evolution evolution-common evolution-data-server evolution-data-server-common
  evolution-data-server-online-accounts evolution-indicator evolution-plugins file-roller firefox folks-common fontconfig fontconfig-config
  fonts-cantarell fonts-dejavu-core fonts-droid fonts-freefont-ttf fonts-kacst fonts-kacst-one fonts-khmeros-core fonts-lao fonts-liberation
  fonts-lklug-sinhala fonts-nanum fonts-opensymbol fonts-sil-abyssinica fonts-sil-padauk fonts-takao-pgothic fonts-thai-tlwg fonts-tibetan-machine
  fonts-tlwg-garuda fonts-tlwg-kinnari fonts-tlwg-loma fonts-tlwg-mono fonts-tlwg-norasi fonts-tlwg-purisa fonts-tlwg-sawasdee fonts-tlwg-typewriter
  fonts-tlwg-typist fonts-tlwg-typo fonts-tlwg-umpush fonts-tlwg-waree foomatic-db-compressed-ppds gcc gcc-4.8 gconf-service gconf-service-backend
  gconf2 gconf2-common gcr gdb gdisk gdm gedit gedit-common genisoimage geoclue gettext ghostscript ghostscript-x gir1.2-accountsservice-1.0
  gir1.2-atk-1.0 gir1.2-atspi-2.0 gir1.2-caribou-1.0 gir1.2-clutter-1.0 gir1.2-clutter-gst-2.0 gir1.2-cogl-1.0 gir1.2-coglpango-1.0
  gir1.2-dbusmenu-glib-0.4 gir1.2-dee-1.0 gir1.2-evince-3.0 gir1.2-freedesktop gir1.2-gck-1 gir1.2-gcr-3 gir1.2-gdata-0.0 gir1.2-gdesktopenums-3.0
  gir1.2-gdkpixbuf-2.0 gir1.2-gdm-1.0 gir1.2-gkbd-3.0 gir1.2-gmenu-3.0 gir1.2-gnomebluetooth-1.0 gir1.2-gnomedesktop-3.0 gir1.2-gnomekeyring-1.0
  gir1.2-goa-1.0 gir1.2-gst-plugins-base-1.0 gir1.2-gstreamer-1.0 gir1.2-gtk-3.0 gir1.2-gtkclutter-1.0 gir1.2-gtksource-3.0 gir1.2-gtop-2.0
  gir1.2-gudev-1.0 gir1.2-ibus-1.0 gir1.2-javascriptcoregtk-3.0 gir1.2-json-1.0 gir1.2-mutter-3.0 gir1.2-networkmanager-1.0 gir1.2-nmgtk-1.0
  gir1.2-notify-0.7 gir1.2-packagekitglib-1.0 gir1.2-pango-1.0 gir1.2-peas-1.0 gir1.2-polkit-1.0 gir1.2-rb-3.0 gir1.2-rest-0.7 gir1.2-secret-1
  gir1.2-soup-2.4 gir1.2-telepathyglib-0.12 gir1.2-telepathylogger-0.2 gir1.2-totem-1.0 gir1.2-totem-plparser-1.0 gir1.2-tracker-0.16
  gir1.2-udisks-2.0 gir1.2-unity-5.0 gir1.2-upowerglib-1.0 gir1.2-vte-2.90 gir1.2-webkit-3.0 gir1.2-wnck-3.0 gir1.2-xkl-1.0 gir1.2-zpj-0.0 gjs
  gkbd-capplet glib-networking glib-networking-common glib-networking-services gnome-accessibility-themes gnome-backgrounds gnome-bluetooth
  gnome-calculator gnome-color-manager gnome-contacts gnome-control-center gnome-control-center-data gnome-control-center-shared-data
  gnome-desktop3-data gnome-disk-utility gnome-documents gnome-font-viewer gnome-icon-theme gnome-icon-theme-extras gnome-icon-theme-full
  gnome-icon-theme-symbolic gnome-keyring gnome-mahjongg gnome-menus gnome-mines gnome-online-accounts gnome-online-miners gnome-orca
  gnome-screenshot gnome-session gnome-session-bin gnome-session-canberra gnome-session-common gnome-settings-daemon gnome-settings-daemon-schemas
  gnome-shell gnome-shell-common gnome-shell-extensions gnome-sudoku gnome-sushi gnome-system-log gnome-system-monitor gnome-terminal
  gnome-terminal-data gnome-themes-standard gnome-themes-standard-data gnome-tweak-tool gnome-user-guide gnome-user-share gnome-video-effects
  growisofs gsettings-desktop-schemas gsettings-ubuntu-schemas gsfonts gstreamer0.10-alsa gstreamer0.10-nice gstreamer0.10-plugins-base
  gstreamer0.10-plugins-good gstreamer0.10-pulseaudio gstreamer0.10-x gstreamer1.0-alsa gstreamer1.0-clutter gstreamer1.0-nice
  gstreamer1.0-plugins-base gstreamer1.0-plugins-good gstreamer1.0-pulseaudio gstreamer1.0-x gtk2-engines-pixbuf gucharmap guile-2.0-libs gvfs
  gvfs-backends gvfs-backends-goa gvfs-bin gvfs-common gvfs-daemons gvfs-fuse gvfs-libs hardening-includes hicolor-icon-theme hplip hplip-data
  humanity-icon-theme hunspell-en-us hwdata ibus ibus-gtk ibus-gtk3 ibus-pinyin ibus-table im-config indicator-application inputattach
  intel-gpu-tools intltool-debian iproute iputils-arping itstool kerneloops-daemon libaa1 libaccount-plugin-1.0-0 libaccount-plugin-generic-oauth
  libaccount-plugin-google libaccounts-glib0 libaccounts-qt5-1 libappindicator3-1 libapt-pkg-perl libarchive-zip-perl libarchive13 libart-2.0-2
  libasan0 libasound2 libasound2-data libasound2-plugins libaspell15 libasprintf-dev libassuan0 libasyncns0 libatasmart4 libatk-adaptor
  libatk-bridge2.0-0 libatk1.0-0 libatk1.0-data libatkmm-1.6-1 libatomic1 libatspi2.0-0 libauthen-sasl-perl libautodie-perl libavahi-client3
  libavahi-common-data libavahi-common3 libavahi-core7 libavahi-glib1 libavahi-gobject0 libavc1394-0 libbluetooth3 libboost-date-time1.54.0
  libboost-system1.54.0 libbrasero-media3-1 libbrlapi0.6 libburn4 libc-dev-bin libc6-dbg libc6-dev libcaca0 libcairo-gobject2 libcairo2
  libcairomm-1.0-1 libcamel-1.2-45 libcanberra-gtk-module libcanberra-gtk0 libcanberra-gtk3-0 libcanberra-gtk3-module libcanberra-pulse libcanberra0
  libcaribou-common libcaribou0 libcdio-cdda1 libcdio-paranoia1 libcdio13 libcdparanoia0 libcdr-0.0-0 libcheese-gtk23 libcheese7 libclone-perl
  libcloog-isl4 libclucene-contribs1 libclucene-core1 libclutter-1.0-0 libclutter-1.0-common libclutter-gst-2.0-0 libclutter-gtk-1.0-0 libcmis-0.4-4
  libcogl-common libcogl-pango15 libcogl15 libcolamd2.8.0 libcolord-gtk1 libcolord1 libcolorhug1 libcrack2 libcroco3 libcrypt-passwdmd5-perl
  libcups2 libcupscgi1 libcupsfilters1 libcupsimage2 libcupsmime1 libcupsppdc1 libcurl3 libdaemon0 libdatrie1 libdbusmenu-glib4 libdbusmenu-gtk3-4
  libdbusmenu-gtk4 libdconf1 libdee-1.0-4 libdigest-hmac-perl libdjvulibre-text libdjvulibre21 libdmapsharing-3.0-2 libdotconf0 libdpkg-perl
  libdrm-intel1 libdrm-nouveau2 libdrm-radeon1 libdv4 libebackend-1.2-7 libebook-1.2-14 libebook-contacts-1.2-0 libecal-1.2-16 libedata-book-1.2-20
  libedata-cal-1.2-23 libedataserver-1.2-18 libegl1-mesa libegl1-mesa-drivers libelfg0 libemail-valid-perl libenca0 libenchant1c2a
  libencode-locale-perl liberror-perl libespeak1 libevdocument3-4 libevent-2.0-5 libevolution libevview3-3 libexempi3 libexif12 libexiv2-12
  libexttextcat-2.0-0 libexttextcat-data libfarstream-0.1-0 libfarstream-0.2-2 libfftw3-single3 libfile-basedir-perl libfile-copy-recursive-perl
  libfile-desktopentry-perl libfile-fcntllock-perl libfile-listing-perl libfile-mimeinfo-perl libflac8 libfolks-eds25 libfolks-telepathy25
  libfolks25 libfont-afm-perl libfontconfig1 libfontembed1 libfontenc1 libframe6 libfs6 libgail-3-0 libgail-common libgail18 libgbm1 libgc1c2
  libgcc-4.8-dev libgconf-2-4 libgcr-ui-3-1 libgd3 libgdata-common libgdata13 libgdk-pixbuf2.0-0 libgdk-pixbuf2.0-common libgdm1 libgee-0.8-2
  libgeis1 libgeoclue0 libgettextpo-dev libgettextpo0 libgexiv2-2 libgif4 libgjs0e libgl1-mesa-dri libgl1-mesa-glx libglamor0 libglapi-mesa
  libgles2-mesa libglib2.0-bin libglibmm-2.4-1c2a libglu1-mesa libgmime-2.6-0 libgmp10 libgnome-bluetooth11 libgnome-control-center1
  libgnome-desktop-3-7 libgnome-keyring-common libgnome-keyring0 libgnome-menu-3-0 libgnomekbd-common libgnomekbd8 libgoa-1.0-0b libgoa-1.0-common
  libgoa-backend-1.0-1 libgomp1 libgpgme11 libgphoto2-6 libgphoto2-l10n libgphoto2-port10 libgpm2 libgpod-common libgpod4 libgrail6 libgraphite2-3
  libgrilo-0.2-1 libgrip0 libgs9 libgs9-common libgsf-1-114 libgsf-1-common libgssdp-1.0-3 libgstreamer-plugins-base0.10-0
  libgstreamer-plugins-base1.0-0 libgstreamer-plugins-good1.0-0 libgstreamer0.10-0 libgstreamer1.0-0 libgtk-3-0 libgtk-3-bin libgtk-3-common
  libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libgtkhtml-4.0-0 libgtkhtml-4.0-common libgtkhtml-editor-4.0-0 libgtkmm-3.0-1 libgtksourceview-3.0-1
  libgtksourceview-3.0-common libgtop2-7 libgtop2-common libgucharmap-2-90-7 libgudev-1.0-0 libgupnp-1.0-4 libgupnp-igd-1.0-4 libgusb2
  libgutenprint2 libgweather-3-6 libgweather-common libgxps2 libharfbuzz-icu0 libharfbuzz0b libhpmud0 libhtml-form-perl libhtml-format-perl
  libhtml-parser-perl libhtml-tagset-perl libhtml-tree-perl libhttp-cookies-perl libhttp-daemon-perl libhttp-date-perl libhttp-message-perl
  libhttp-negotiate-perl libhunspell-1.3-0 libhyphen0 libibus-1.0-5 libical1 libicc2 libice6 libicu52 libido3-0.1-0 libiec61883-0 libieee1284-3
  libijs-0.35 libimdi0 libimobiledevice4 libindicator3-7 libio-html-perl libio-pty-perl libio-socket-inet6-perl libio-socket-ssl-perl
  libipc-run-perl libipc-system-simple-perl libiptcdata0 libisl10 libisofs6 libitm1 libiw30 libjack-jackd2-0 libjasper1 libjavascriptcoregtk-3.0-0
  libjbig0 libjbig2dec0 libjpeg-turbo8 libjpeg8 libjson-glib-1.0-0 libjson-glib-1.0-common libjte1 libkpathsea6 liblangtag-common liblangtag1
  liblcms2-2 libldb1 liblircclient0 liblist-moreutils-perl libllvm3.4 liblouis-data liblouis2 libltdl7 liblua5.2-0 liblwp-mediatypes-perl
  liblwp-protocol-https-perl liblzo2-2 libmail-spf-perl libmailtools-perl libmbim-glib0 libmeanwhile1 libmessaging-menu0 libmhash2 libminiupnpc8
  libmission-control-plugins0 libmm-glib0 libmnl0 libmozjs-24-0 libmpc3 libmpfr4 libmspub-0.0-0 libmtdev1 libmtp-common libmtp-runtime libmtp9
  libmusicbrainz5-0 libmutter0c libmythes-1.2-0 libnatpmp1 libnautilus-extension1a libneon27-gnutls libnet-dns-perl libnet-domain-tld-perl
  libnet-http-perl libnet-ip-perl libnet-libidn-perl libnet-smtp-ssl-perl libnet-ssleay-perl libnetaddr-ip-perl libnetfilter-conntrack3 libnettle4
  libnice10 libnl-route-3-200 libnm-glib-vpn1 libnm-glib4 libnm-gtk-common libnm-gtk0 libnm-util2 libnotify-bin libnotify4 libnspr4 libnss-mdns
  libnss-myhostname libnss3 libnss3-nssdb libntdb1 liboauth0 libogg0 libopencc1 libopenobex1 libopenvg1-mesa liborc-0.4-0 liborcus-0.6-0
  libp11-kit-gnome-keyring libpackagekit-glib2-16 libpam-gnome-keyring libpango-1.0-0 libpango1.0-0 libpangocairo-1.0-0 libpangoft2-1.0-0
  libpangomm-1.4-1 libpangox-1.0-0 libpangoxft-1.0-0 libpaper-utils libpaper1 libpciaccess0 libpcsclite1 libpeas-1.0-0 libpeas-common libperl5.18
  libperlio-gzip-perl libpixman-1-0 libplist1 libpolkit-agent-1-0 libpolkit-backend-1-0 libpoppler-glib8 libpoppler44 libportaudio2 libproxy1
  libproxy1-plugin-gsettings libproxy1-plugin-networkmanager libpst4 libpulse-mainloop-glib0 libpulse0 libpulsedsp libpurple-bin libpurple0
  libpwquality-common libpwquality1 libpython2.7 libpython3.4 libpyzy-1.0-0 libqmi-glib0 libqpdf13 libqt5core5a libqt5dbus5 libqt5gui5
  libqt5network5 libqt5opengl5 libqt5positioning5 libqt5printsupport5 libqt5qml5 libqt5quick5 libqt5sensors5 libqt5sql5 libqt5sql5-sqlite
  libqt5test5 libqt5webkit5 libqt5widgets5 libqt5xml5 libquadmath0 libraptor2-0 librasqal3 libraw1394-11 libraw9 librdf0 libreadline5
  libreoffice-avmedia-backend-gstreamer libreoffice-base-core libreoffice-calc libreoffice-common libreoffice-core libreoffice-draw
  libreoffice-gnome libreoffice-gtk libreoffice-impress libreoffice-math libreoffice-ogltrans libreoffice-pdfimport
  libreoffice-presentation-minimizer libreoffice-style-galaxy libreoffice-style-human libreoffice-style-tango libreoffice-writer librest-0.7-0
  librhythmbox-core8 librsvg2-2 librsvg2-common librsync1 libsamplerate0 libsane libsane-common libsane-hpaio libsbc1 libsecret-1-0 libsecret-common
  libsensors4 libsgutils2-2 libshout3 libsignon-extension1 libsignon-glib1 libsignon-plugins-common1 libsignon-qt5-1 libsm6 libsmbclient libsndfile1
  libsnmp-base libsnmp30 libsocket6-perl libsonic0 libsoup-gnome2.4-1 libsoup2.4-1 libspectre1 libspeechd2 libspeex1 libspeexdsp1
  libstartup-notification0 libsub-identify-perl libsys-hostname-long-perl libsystemd-journal0 libt1-5 libtag1-vanilla libtag1c2a libtalloc2
  libtcl8.6 libtdb1 libtelepathy-farstream3 libtelepathy-glib0 libtelepathy-logger3 libtevent0 libtext-levenshtein-perl libthai-data libthai0
  libtheora0 libtiff5 libtimezonemap1 libtk8.6 libtotem-plparser18 libtotem0 libtracker-extract-0.16-0 libtracker-miner-0.16-0
  libtracker-sparql-0.16-0 libtxc-dxtn-s2tc0 libudisks2-0 libunistring0 libunity-control-center1 libunity-protocol-private0
  libunity-scopes-json-def-desktop libunity9 libupower-glib1 liburi-perl libusbmuxd2 libutempter0 libv4l-0 libv4lconvert0 libvisio-0.0-0
  libvisual-0.4-0 libvisual-0.4-plugins libvorbis0a libvorbisenc2 libvorbisfile3 libvpx1 libvte-2.90-9 libvte-2.90-common libwacom-common libwacom2
  libwavpack1 libwayland-client0 libwayland-cursor0 libwayland-egl1-mesa libwayland-server0 libwbclient0 libwebkitgtk-3.0-0 libwebkitgtk-3.0-common
  libwebp5 libwebpmux1 libwhoopsie0 libwmf0.2-7 libwmf0.2-7-gtk libwnck-3-0 libwnck-3-common libwpd-0.9-9 libwpg-0.2-2 libwps-0.2-2 libwrap0
  libwww-perl libwww-robotrules-perl libx11-xcb1 libxatracker2 libxaw7 libxcb-dri2-0 libxcb-dri3-0 libxcb-glx0 libxcb-icccm4 libxcb-image0
  libxcb-keysyms1 libxcb-present0 libxcb-randr0 libxcb-render-util0 libxcb-render0 libxcb-shape0 libxcb-shm0 libxcb-sync1 libxcb-util0
  libxcb-xf86dri0 libxcb-xfixes0 libxcb-xkb1 libxcb-xv0 libxcomposite1 libxcursor1 libxdamage1 libxfixes3 libxfont1 libxft2 libxi6 libxinerama1
  libxkbcommon0 libxkbfile1 libxklavier16 libxml2-utils libxmu6 libxp6 libxpm4 libxrandr2 libxrender1 libxres1 libxshmfence1 libxslt1.1 libxss1
  libxt6 libxtst6 libxv1 libxvmc1 libxxf86dga1 libxxf86vm1 libyajl2 libyelp0 libytnef0 libzapojit-0.0-0 libzeitgeist-1.0-1 libzeitgeist-2.0-0
  libzephyr4 lintian linux-libc-dev linux-sound-base lp-solve make manpages-dev mcp-account-manager-goa mcp-account-manager-uoa media-player-info
  memtest86+ mobile-broadband-provider-info modemmanager mousetweaks mscompress mtools mutter mutter-common nautilus nautilus-data nautilus-sendto
  nautilus-sendto-empathy nautilus-share network-manager network-manager-gnome network-manager-pptp network-manager-pptp-gnome notification-daemon
  obex-data-server obexd-client oneconf oneconf-common openprinting-ppds p11-kit p11-kit-modules patch patchutils pcmciautils plymouth-label
  plymouth-theme-ubuntu-gnome-logo plymouth-theme-ubuntu-gnome-text policykit-1 policykit-1-gnome policykit-desktop-privileges poppler-data
  poppler-utils pptp-linux printer-driver-c2esp printer-driver-foo2zjs printer-driver-foo2zjs-common printer-driver-gutenprint printer-driver-hpcups
  printer-driver-min12xxw printer-driver-pnm2ppa printer-driver-postscript-hp printer-driver-ptouch printer-driver-pxljr printer-driver-sag-gdi
  printer-driver-splix pulseaudio pulseaudio-module-bluetooth pulseaudio-module-x11 pulseaudio-utils python-aptdaemon python-aptdaemon.gtk3widgets
  python-boto python-cairo python-cloudfiles python-commandnotfound python-crypto python-cups python-cupshelpers python-dbus python-dbus-dev
  python-debtagshw python-defer python-dirspec python-gdbm python-gi python-gi-cairo python-gnomekeyring python-gobject python-gobject-2 python-gtk2
  python-httplib2 python-ibus python-imaging python-ldb python-libxml2 python-lockfile python-lxml python-notify python-ntdb python-oauthlib
  python-oneconf python-openssl python-pam python-pexpect python-pil python-piston-mini-client python-pkg-resources python-pycurl python-renderpm
  python-reportlab python-reportlab-accel python-requests python-samba python-serial python-smbc python-talloc python-tdb python-twisted-bin
  python-twisted-core python-twisted-web python-ubuntu-sso-client python-urllib3 python-xdg python-zeitgeist python-zope.interface python3-apport
  python3-aptdaemon python3-aptdaemon.gtk3widgets python3-aptdaemon.pkcompat python3-brlapi python3-cairo python3-chardet python3-crypto
  python3-debian python3-defer python3-gi-cairo python3-httplib2 python3-louis python3-mako python3-markupsafe python3-oauthlib python3-oneconf
  python3-piston-mini-client python3-pkg-resources python3-problem-report python3-pyatspi python3-pycurl python3-six python3-software-properties
  python3-speechd python3-uno python3-xdg python3-xkit qpdf re2c rfkill rhythmbox rhythmbox-data rhythmbox-mozilla rhythmbox-plugin-cdrecorder
  rhythmbox-plugin-magnatune rhythmbox-plugin-zeitgeist rhythmbox-plugins rtkit sa-compile samba-common samba-common-bin samba-libs sane-utils
  seahorse session-migration sessioninstaller shotwell shotwell-common signon-keyring-extension signon-plugin-oauth2 signon-plugin-password
  signon-ui signond simple-scan smbclient software-center software-center-aptdaemon-plugins software-properties-common software-properties-gtk
  sound-theme-freedesktop spamassassin spamc speech-dispatcher speech-dispatcher-audio-plugins ssh-askpass-gnome ssl-cert syslinux syslinux-common
  syslinux-legacy system-config-printer-common system-config-printer-gnome system-config-printer-udev t1utils tcl tcl8.6 tcpd telepathy-gabble
  telepathy-haze telepathy-idle telepathy-logger telepathy-mission-control-5 telepathy-salut tk tk8.6 toshset totem totem-common totem-plugins
  tracker tracker-extract tracker-miner-fs tracker-utils transmission-common transmission-gtk ttf-indic-fonts-core ttf-punjabi-fonts
  ttf-ubuntu-font-family ubuntu-drivers-common ubuntu-extras-keyring ubuntu-gnome-default-settings ubuntu-gnome-desktop ubuntu-release-upgrader-gtk
  ubuntu-sso-client ubuntu-system-service udisks2 unattended-upgrades unity-asset-pool unity-control-center unity-control-center-signon
  unity-settings-daemon uno-libs3 unoconv unzip update-inetd update-manager update-notifier update-notifier-common upower ure usb-creator-common
  usb-creator-gtk usb-modeswitch usb-modeswitch-data usbmuxd vino wamerican whoopsie wireless-tools wodim wpasupplicant x11-apps x11-common
  x11-session-utils x11-utils x11-xfs-utils x11-xkb-utils x11-xserver-utils xbitmaps xdg-user-dirs xdg-user-dirs-gtk xdg-utils xdiagnose xfonts-base
  xfonts-encodings xfonts-mathml xfonts-scalable xfonts-utils xinit xinput xorg xorg-docs-core xserver-common xserver-xephyr xserver-xorg
  xserver-xorg-core xserver-xorg-input-all xserver-xorg-input-evdev xserver-xorg-input-mouse xserver-xorg-input-synaptics xserver-xorg-input-vmmouse
  xserver-xorg-input-wacom xserver-xorg-video-all xserver-xorg-video-ati xserver-xorg-video-cirrus xserver-xorg-video-fbdev
  xserver-xorg-video-glamoregl xserver-xorg-video-intel xserver-xorg-video-mach64 xserver-xorg-video-mga xserver-xorg-video-modesetting
  xserver-xorg-video-neomagic xserver-xorg-video-nouveau xserver-xorg-video-openchrome xserver-xorg-video-qxl xserver-xorg-video-r128
  xserver-xorg-video-radeon xserver-xorg-video-s3 xserver-xorg-video-savage xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident xserver-xorg-video-vesa xserver-xorg-video-vmware xsltproc xterm
  xul-ext-ubufox yelp yelp-tools yelp-xsl zeitgeist zeitgeist-core zeitgeist-datahub zenity zenity-common zip zsync
The following packages will be upgraded:
  libglib2.0-0 libplymouth2 plymouth
3 upgraded, **[COLOR="#FF0000"]1216 newly installed[/COLOR]**, 0 to remove and 10 not upgraded.
Need to get 444 MB of archives.
After this operation, 1,685 MB of additional disk space will be used.
Do you want to continue? [Y/n] n
Abort.

```

Was 1235 > now 1216.

---

### Post by kansasnoob on 2014-04-03
Without 'shotwell' takes the package count to 1212:

```
root@lance-desktop:/# apt-get install ubuntu-gnome-desktop shotwell-
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'shotwell' is not installed, so not removed
The following extra packages will be installed:
  account-plugin-aim account-plugin-facebook account-plugin-google account-plugin-jabber account-plugin-salut account-plugin-windows-live
  account-plugin-yahoo acl acpi-support acpid aisleriot alsa-base alsa-utils anacron apg app-install-data app-install-data-partner apport apport-gtk
  apport-symptoms aptdaemon aptdaemon-data apturl apturl-common argyll aspell aspell-en at-spi2-core avahi-autoipd avahi-daemon avahi-utils baobab
  bc binutils bluez bluez-alsa bluez-cups brasero brasero-cdrkit brasero-common brltty cheese cheese-common colord cpp cpp-4.8 cracklib-runtime cups
  cups-browsed cups-bsd cups-client cups-common cups-core-drivers cups-daemon cups-filters cups-filters-core-drivers cups-pk-helper cups-ppdc
  cups-server-common dbus-x11 dc dconf-cli dconf-editor dconf-gsettings-backend dconf-service deja-dup deja-dup-backend-cloudfiles
  deja-dup-backend-gvfs deja-dup-backend-s3 desktop-file-utils dialog dictionaries-common diffstat dnsmasq-base duplicity dvd+rw-tools empathy
  empathy-common enchant eog espeak-data evince evince-common evolution evolution-common evolution-data-server evolution-data-server-common
  evolution-data-server-online-accounts evolution-indicator evolution-plugins file-roller firefox folks-common fontconfig fontconfig-config
  fonts-cantarell fonts-dejavu-core fonts-droid fonts-freefont-ttf fonts-kacst fonts-kacst-one fonts-khmeros-core fonts-lao fonts-liberation
  fonts-lklug-sinhala fonts-nanum fonts-opensymbol fonts-sil-abyssinica fonts-sil-padauk fonts-takao-pgothic fonts-thai-tlwg fonts-tibetan-machine
  fonts-tlwg-garuda fonts-tlwg-kinnari fonts-tlwg-loma fonts-tlwg-mono fonts-tlwg-norasi fonts-tlwg-purisa fonts-tlwg-sawasdee fonts-tlwg-typewriter
  fonts-tlwg-typist fonts-tlwg-typo fonts-tlwg-umpush fonts-tlwg-waree foomatic-db-compressed-ppds gcc gcc-4.8 gconf-service gconf-service-backend
  gconf2 gconf2-common gcr gdb gdisk gdm gedit gedit-common genisoimage geoclue gettext ghostscript ghostscript-x gir1.2-accountsservice-1.0
  gir1.2-atk-1.0 gir1.2-atspi-2.0 gir1.2-caribou-1.0 gir1.2-clutter-1.0 gir1.2-clutter-gst-2.0 gir1.2-cogl-1.0 gir1.2-coglpango-1.0
  gir1.2-dbusmenu-glib-0.4 gir1.2-dee-1.0 gir1.2-evince-3.0 gir1.2-freedesktop gir1.2-gck-1 gir1.2-gcr-3 gir1.2-gdata-0.0 gir1.2-gdesktopenums-3.0
  gir1.2-gdkpixbuf-2.0 gir1.2-gdm-1.0 gir1.2-gkbd-3.0 gir1.2-gmenu-3.0 gir1.2-gnomebluetooth-1.0 gir1.2-gnomedesktop-3.0 gir1.2-gnomekeyring-1.0
  gir1.2-goa-1.0 gir1.2-gst-plugins-base-1.0 gir1.2-gstreamer-1.0 gir1.2-gtk-3.0 gir1.2-gtkclutter-1.0 gir1.2-gtksource-3.0 gir1.2-gtop-2.0
  gir1.2-gudev-1.0 gir1.2-ibus-1.0 gir1.2-javascriptcoregtk-3.0 gir1.2-json-1.0 gir1.2-mutter-3.0 gir1.2-networkmanager-1.0 gir1.2-nmgtk-1.0
  gir1.2-notify-0.7 gir1.2-packagekitglib-1.0 gir1.2-pango-1.0 gir1.2-peas-1.0 gir1.2-polkit-1.0 gir1.2-rb-3.0 gir1.2-rest-0.7 gir1.2-secret-1
  gir1.2-soup-2.4 gir1.2-telepathyglib-0.12 gir1.2-telepathylogger-0.2 gir1.2-totem-1.0 gir1.2-totem-plparser-1.0 gir1.2-tracker-0.16
  gir1.2-udisks-2.0 gir1.2-unity-5.0 gir1.2-upowerglib-1.0 gir1.2-vte-2.90 gir1.2-webkit-3.0 gir1.2-wnck-3.0 gir1.2-xkl-1.0 gir1.2-zpj-0.0 gjs
  gkbd-capplet glib-networking glib-networking-common glib-networking-services gnome-accessibility-themes gnome-backgrounds gnome-bluetooth
  gnome-calculator gnome-color-manager gnome-contacts gnome-control-center gnome-control-center-data gnome-control-center-shared-data
  gnome-desktop3-data gnome-disk-utility gnome-documents gnome-font-viewer gnome-icon-theme gnome-icon-theme-extras gnome-icon-theme-full
  gnome-icon-theme-symbolic gnome-keyring gnome-mahjongg gnome-menus gnome-mines gnome-online-accounts gnome-online-miners gnome-orca
  gnome-screenshot gnome-session gnome-session-bin gnome-session-canberra gnome-session-common gnome-settings-daemon gnome-settings-daemon-schemas
  gnome-shell gnome-shell-common gnome-shell-extensions gnome-sudoku gnome-sushi gnome-system-log gnome-system-monitor gnome-terminal
  gnome-terminal-data gnome-themes-standard gnome-themes-standard-data gnome-tweak-tool gnome-user-guide gnome-user-share gnome-video-effects
  growisofs gsettings-desktop-schemas gsettings-ubuntu-schemas gsfonts gstreamer0.10-alsa gstreamer0.10-nice gstreamer0.10-plugins-base
  gstreamer0.10-plugins-good gstreamer0.10-pulseaudio gstreamer0.10-x gstreamer1.0-alsa gstreamer1.0-clutter gstreamer1.0-nice
  gstreamer1.0-plugins-base gstreamer1.0-plugins-good gstreamer1.0-pulseaudio gstreamer1.0-x gtk2-engines-pixbuf gucharmap guile-2.0-libs gvfs
  gvfs-backends gvfs-backends-goa gvfs-bin gvfs-common gvfs-daemons gvfs-fuse gvfs-libs hardening-includes hicolor-icon-theme hplip hplip-data
  humanity-icon-theme hunspell-en-us hwdata ibus ibus-gtk ibus-gtk3 ibus-pinyin ibus-table im-config indicator-application inputattach
  intel-gpu-tools intltool-debian iproute iputils-arping itstool kerneloops-daemon libaa1 libaccount-plugin-1.0-0 libaccount-plugin-generic-oauth
  libaccount-plugin-google libaccounts-glib0 libaccounts-qt5-1 libappindicator3-1 libapt-pkg-perl libarchive-zip-perl libarchive13 libart-2.0-2
  libasan0 libasound2 libasound2-data libasound2-plugins libaspell15 libasprintf-dev libassuan0 libasyncns0 libatasmart4 libatk-adaptor
  libatk-bridge2.0-0 libatk1.0-0 libatk1.0-data libatkmm-1.6-1 libatomic1 libatspi2.0-0 libauthen-sasl-perl libautodie-perl libavahi-client3
  libavahi-common-data libavahi-common3 libavahi-core7 libavahi-glib1 libavahi-gobject0 libavc1394-0 libbluetooth3 libboost-date-time1.54.0
  libboost-system1.54.0 libbrasero-media3-1 libbrlapi0.6 libburn4 libc-dev-bin libc6-dbg libc6-dev libcaca0 libcairo-gobject2 libcairo2
  libcairomm-1.0-1 libcamel-1.2-45 libcanberra-gtk-module libcanberra-gtk0 libcanberra-gtk3-0 libcanberra-gtk3-module libcanberra-pulse libcanberra0
  libcaribou-common libcaribou0 libcdio-cdda1 libcdio-paranoia1 libcdio13 libcdparanoia0 libcdr-0.0-0 libcheese-gtk23 libcheese7 libclone-perl
  libcloog-isl4 libclucene-contribs1 libclucene-core1 libclutter-1.0-0 libclutter-1.0-common libclutter-gst-2.0-0 libclutter-gtk-1.0-0 libcmis-0.4-4
  libcogl-common libcogl-pango15 libcogl15 libcolamd2.8.0 libcolord-gtk1 libcolord1 libcolorhug1 libcrack2 libcroco3 libcrypt-passwdmd5-perl
  libcups2 libcupscgi1 libcupsfilters1 libcupsimage2 libcupsmime1 libcupsppdc1 libcurl3 libdaemon0 libdatrie1 libdbusmenu-glib4 libdbusmenu-gtk3-4
  libdbusmenu-gtk4 libdconf1 libdee-1.0-4 libdigest-hmac-perl libdjvulibre-text libdjvulibre21 libdmapsharing-3.0-2 libdotconf0 libdpkg-perl
  libdrm-intel1 libdrm-nouveau2 libdrm-radeon1 libdv4 libebackend-1.2-7 libebook-1.2-14 libebook-contacts-1.2-0 libecal-1.2-16 libedata-book-1.2-20
  libedata-cal-1.2-23 libedataserver-1.2-18 libegl1-mesa libegl1-mesa-drivers libelfg0 libemail-valid-perl libenca0 libenchant1c2a
  libencode-locale-perl liberror-perl libespeak1 libevdocument3-4 libevent-2.0-5 libevolution libevview3-3 libexempi3 libexif12 libexiv2-12
  libexttextcat-2.0-0 libexttextcat-data libfarstream-0.1-0 libfarstream-0.2-2 libfftw3-single3 libfile-basedir-perl libfile-copy-recursive-perl
  libfile-desktopentry-perl libfile-fcntllock-perl libfile-listing-perl libfile-mimeinfo-perl libflac8 libfolks-eds25 libfolks-telepathy25
  libfolks25 libfont-afm-perl libfontconfig1 libfontembed1 libfontenc1 libframe6 libfs6 libgail-3-0 libgail-common libgail18 libgbm1 libgc1c2
  libgcc-4.8-dev libgconf-2-4 libgcr-ui-3-1 libgd3 libgdata-common libgdata13 libgdk-pixbuf2.0-0 libgdk-pixbuf2.0-common libgdm1 libgee-0.8-2
  libgeis1 libgeoclue0 libgettextpo-dev libgettextpo0 libgif4 libgjs0e libgl1-mesa-dri libgl1-mesa-glx libglamor0 libglapi-mesa libgles2-mesa
  libglib2.0-0 libglib2.0-bin libglibmm-2.4-1c2a libglu1-mesa libgmime-2.6-0 libgmp10 libgnome-bluetooth11 libgnome-control-center1
  libgnome-desktop-3-7 libgnome-keyring-common libgnome-keyring0 libgnome-menu-3-0 libgnomekbd-common libgnomekbd8 libgoa-1.0-0b libgoa-1.0-common
  libgoa-backend-1.0-1 libgomp1 libgpgme11 libgphoto2-6 libgphoto2-l10n libgphoto2-port10 libgpm2 libgpod-common libgpod4 libgrail6 libgraphite2-3
  libgrilo-0.2-1 libgrip0 libgs9 libgs9-common libgsf-1-114 libgsf-1-common libgssdp-1.0-3 libgstreamer-plugins-base0.10-0
  libgstreamer-plugins-base1.0-0 libgstreamer-plugins-good1.0-0 libgstreamer0.10-0 libgstreamer1.0-0 libgtk-3-0 libgtk-3-bin libgtk-3-common
  libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libgtkhtml-4.0-0 libgtkhtml-4.0-common libgtkhtml-editor-4.0-0 libgtkmm-3.0-1 libgtksourceview-3.0-1
  libgtksourceview-3.0-common libgtop2-7 libgtop2-common libgucharmap-2-90-7 libgudev-1.0-0 libgupnp-1.0-4 libgupnp-igd-1.0-4 libgusb2
  libgutenprint2 libgweather-3-6 libgweather-common libgxps2 libharfbuzz-icu0 libharfbuzz0b libhpmud0 libhtml-form-perl libhtml-format-perl
  libhtml-parser-perl libhtml-tagset-perl libhtml-tree-perl libhttp-cookies-perl libhttp-daemon-perl libhttp-date-perl libhttp-message-perl
  libhttp-negotiate-perl libhunspell-1.3-0 libhyphen0 libibus-1.0-5 libical1 libicc2 libice6 libicu52 libido3-0.1-0 libiec61883-0 libieee1284-3
  libijs-0.35 libimdi0 libimobiledevice4 libindicator3-7 libio-html-perl libio-pty-perl libio-socket-inet6-perl libio-socket-ssl-perl
  libipc-run-perl libipc-system-simple-perl libiptcdata0 libisl10 libisofs6 libitm1 libiw30 libjack-jackd2-0 libjasper1 libjavascriptcoregtk-3.0-0
  libjbig0 libjbig2dec0 libjpeg-turbo8 libjpeg8 libjson-glib-1.0-0 libjson-glib-1.0-common libjte1 libkpathsea6 liblangtag-common liblangtag1
  liblcms2-2 libldb1 liblircclient0 liblist-moreutils-perl libllvm3.4 liblouis-data liblouis2 libltdl7 liblua5.2-0 liblwp-mediatypes-perl
  liblwp-protocol-https-perl liblzo2-2 libmail-spf-perl libmailtools-perl libmbim-glib0 libmeanwhile1 libmessaging-menu0 libmhash2 libminiupnpc8
  libmission-control-plugins0 libmm-glib0 libmnl0 libmozjs-24-0 libmpc3 libmpfr4 libmspub-0.0-0 libmtdev1 libmtp-common libmtp-runtime libmtp9
  libmusicbrainz5-0 libmutter0c libmythes-1.2-0 libnatpmp1 libnautilus-extension1a libneon27-gnutls libnet-dns-perl libnet-domain-tld-perl
  libnet-http-perl libnet-ip-perl libnet-libidn-perl libnet-smtp-ssl-perl libnet-ssleay-perl libnetaddr-ip-perl libnetfilter-conntrack3 libnettle4
  libnice10 libnl-route-3-200 libnm-glib-vpn1 libnm-glib4 libnm-gtk-common libnm-gtk0 libnm-util2 libnotify-bin libnotify4 libnspr4 libnss-mdns
  libnss-myhostname libnss3 libnss3-nssdb libntdb1 liboauth0 libogg0 libopencc1 libopenobex1 libopenvg1-mesa liborc-0.4-0 liborcus-0.6-0
  libp11-kit-gnome-keyring libpackagekit-glib2-16 libpam-gnome-keyring libpango-1.0-0 libpango1.0-0 libpangocairo-1.0-0 libpangoft2-1.0-0
  libpangomm-1.4-1 libpangox-1.0-0 libpangoxft-1.0-0 libpaper-utils libpaper1 libpciaccess0 libpcsclite1 libpeas-1.0-0 libpeas-common libperl5.18
  libperlio-gzip-perl libpixman-1-0 libplist1 libplymouth2 libpolkit-agent-1-0 libpolkit-backend-1-0 libpoppler-glib8 libpoppler44 libportaudio2
  libproxy1 libproxy1-plugin-gsettings libproxy1-plugin-networkmanager libpst4 libpulse-mainloop-glib0 libpulse0 libpulsedsp libpurple-bin
  libpurple0 libpwquality-common libpwquality1 libpython2.7 libpython3.4 libpyzy-1.0-0 libqmi-glib0 libqpdf13 libqt5core5a libqt5dbus5 libqt5gui5
  libqt5network5 libqt5opengl5 libqt5positioning5 libqt5printsupport5 libqt5qml5 libqt5quick5 libqt5sensors5 libqt5sql5 libqt5sql5-sqlite
  libqt5test5 libqt5webkit5 libqt5widgets5 libqt5xml5 libquadmath0 libraptor2-0 librasqal3 libraw1394-11 librdf0 libreadline5
  libreoffice-avmedia-backend-gstreamer libreoffice-base-core libreoffice-calc libreoffice-common libreoffice-core libreoffice-draw
  libreoffice-gnome libreoffice-gtk libreoffice-impress libreoffice-math libreoffice-ogltrans libreoffice-pdfimport
  libreoffice-presentation-minimizer libreoffice-style-galaxy libreoffice-style-human libreoffice-style-tango libreoffice-writer librest-0.7-0
  librhythmbox-core8 librsvg2-2 librsvg2-common librsync1 libsamplerate0 libsane libsane-common libsane-hpaio libsbc1 libsecret-1-0 libsecret-common
  libsensors4 libsgutils2-2 libshout3 libsignon-extension1 libsignon-glib1 libsignon-plugins-common1 libsignon-qt5-1 libsm6 libsmbclient libsndfile1
  libsnmp-base libsnmp30 libsocket6-perl libsonic0 libsoup-gnome2.4-1 libsoup2.4-1 libspectre1 libspeechd2 libspeex1 libspeexdsp1
  libstartup-notification0 libsub-identify-perl libsys-hostname-long-perl libsystemd-journal0 libt1-5 libtag1-vanilla libtag1c2a libtalloc2
  libtcl8.6 libtdb1 libtelepathy-farstream3 libtelepathy-glib0 libtelepathy-logger3 libtevent0 libtext-levenshtein-perl libthai-data libthai0
  libtheora0 libtiff5 libtimezonemap1 libtk8.6 libtotem-plparser18 libtotem0 libtracker-extract-0.16-0 libtracker-miner-0.16-0
  libtracker-sparql-0.16-0 libtxc-dxtn-s2tc0 libudisks2-0 libunistring0 libunity-control-center1 libunity-protocol-private0
  libunity-scopes-json-def-desktop libunity9 libupower-glib1 liburi-perl libusbmuxd2 libutempter0 libv4l-0 libv4lconvert0 libvisio-0.0-0
  libvisual-0.4-0 libvisual-0.4-plugins libvorbis0a libvorbisenc2 libvorbisfile3 libvpx1 libvte-2.90-9 libvte-2.90-common libwacom-common libwacom2
  libwavpack1 libwayland-client0 libwayland-cursor0 libwayland-egl1-mesa libwayland-server0 libwbclient0 libwebkitgtk-3.0-0 libwebkitgtk-3.0-common
  libwebp5 libwebpmux1 libwhoopsie0 libwmf0.2-7 libwmf0.2-7-gtk libwnck-3-0 libwnck-3-common libwpd-0.9-9 libwpg-0.2-2 libwps-0.2-2 libwrap0
  libwww-perl libwww-robotrules-perl libx11-xcb1 libxatracker2 libxaw7 libxcb-dri2-0 libxcb-dri3-0 libxcb-glx0 libxcb-icccm4 libxcb-image0
  libxcb-keysyms1 libxcb-present0 libxcb-randr0 libxcb-render-util0 libxcb-render0 libxcb-shape0 libxcb-shm0 libxcb-sync1 libxcb-util0
  libxcb-xf86dri0 libxcb-xfixes0 libxcb-xkb1 libxcb-xv0 libxcomposite1 libxcursor1 libxdamage1 libxfixes3 libxfont1 libxft2 libxi6 libxinerama1
  libxkbcommon0 libxkbfile1 libxklavier16 libxml2-utils libxmu6 libxp6 libxpm4 libxrandr2 libxrender1 libxres1 libxshmfence1 libxslt1.1 libxss1
  libxt6 libxtst6 libxv1 libxvmc1 libxxf86dga1 libxxf86vm1 libyajl2 libyelp0 libytnef0 libzapojit-0.0-0 libzeitgeist-1.0-1 libzeitgeist-2.0-0
  libzephyr4 lintian linux-libc-dev linux-sound-base lp-solve make manpages-dev mcp-account-manager-goa mcp-account-manager-uoa media-player-info
  memtest86+ mobile-broadband-provider-info modemmanager mousetweaks mscompress mtools mutter mutter-common nautilus nautilus-data nautilus-sendto
  nautilus-sendto-empathy nautilus-share network-manager network-manager-gnome network-manager-pptp network-manager-pptp-gnome notification-daemon
  obex-data-server obexd-client oneconf oneconf-common openprinting-ppds p11-kit p11-kit-modules patch patchutils pcmciautils plymouth
  plymouth-label plymouth-theme-ubuntu-gnome-logo plymouth-theme-ubuntu-gnome-text policykit-1 policykit-1-gnome policykit-desktop-privileges
  poppler-data poppler-utils pptp-linux printer-driver-c2esp printer-driver-foo2zjs printer-driver-foo2zjs-common printer-driver-gutenprint
  printer-driver-hpcups printer-driver-min12xxw printer-driver-pnm2ppa printer-driver-postscript-hp printer-driver-ptouch printer-driver-pxljr
  printer-driver-sag-gdi printer-driver-splix pulseaudio pulseaudio-module-bluetooth pulseaudio-module-x11 pulseaudio-utils python-aptdaemon
  python-aptdaemon.gtk3widgets python-boto python-cairo python-cloudfiles python-commandnotfound python-crypto python-cups python-cupshelpers
  python-dbus python-dbus-dev python-debtagshw python-defer python-dirspec python-gdbm python-gi python-gi-cairo python-gnomekeyring python-gobject
  python-gobject-2 python-gtk2 python-httplib2 python-ibus python-imaging python-ldb python-libxml2 python-lockfile python-lxml python-notify
  python-ntdb python-oauthlib python-oneconf python-openssl python-pam python-pexpect python-pil python-piston-mini-client python-pkg-resources
  python-pycurl python-renderpm python-reportlab python-reportlab-accel python-requests python-samba python-serial python-smbc python-talloc
  python-tdb python-twisted-bin python-twisted-core python-twisted-web python-ubuntu-sso-client python-urllib3 python-xdg python-zeitgeist
  python-zope.interface python3-apport python3-aptdaemon python3-aptdaemon.gtk3widgets python3-aptdaemon.pkcompat python3-brlapi python3-cairo
  python3-chardet python3-crypto python3-debian python3-defer python3-gi-cairo python3-httplib2 python3-louis python3-mako python3-markupsafe
  python3-oauthlib python3-oneconf python3-piston-mini-client python3-pkg-resources python3-problem-report python3-pyatspi python3-pycurl
  python3-six python3-software-properties python3-speechd python3-uno python3-xdg python3-xkit qpdf re2c rfkill rhythmbox rhythmbox-data
  rhythmbox-mozilla rhythmbox-plugin-cdrecorder rhythmbox-plugin-magnatune rhythmbox-plugin-zeitgeist rhythmbox-plugins rtkit sa-compile
  samba-common samba-common-bin samba-libs sane-utils seahorse session-migration sessioninstaller signon-keyring-extension signon-plugin-oauth2
  signon-plugin-password signon-ui signond simple-scan smbclient software-center software-center-aptdaemon-plugins software-properties-common
  software-properties-gtk sound-theme-freedesktop spamassassin spamc speech-dispatcher speech-dispatcher-audio-plugins ssh-askpass-gnome ssl-cert
  syslinux syslinux-common syslinux-legacy system-config-printer-common system-config-printer-gnome system-config-printer-udev t1utils tcl tcl8.6
  tcpd telepathy-gabble telepathy-haze telepathy-idle telepathy-logger telepathy-mission-control-5 telepathy-salut tk tk8.6 toshset totem
  totem-common totem-plugins tracker tracker-extract tracker-miner-fs tracker-utils transmission-common transmission-gtk ttf-indic-fonts-core
  ttf-punjabi-fonts ttf-ubuntu-font-family ubuntu-drivers-common ubuntu-extras-keyring ubuntu-gnome-default-settings ubuntu-release-upgrader-gtk
  ubuntu-sso-client ubuntu-system-service udisks2 unattended-upgrades unity-asset-pool unity-control-center unity-control-center-signon
  unity-settings-daemon uno-libs3 unoconv unzip update-inetd update-manager update-notifier update-notifier-common upower ure usb-creator-common
  usb-creator-gtk usb-modeswitch usb-modeswitch-data usbmuxd vino wamerican whoopsie wireless-tools wodim wpasupplicant x11-apps x11-common
  x11-session-utils x11-utils x11-xfs-utils x11-xkb-utils x11-xserver-utils xbitmaps xdg-user-dirs xdg-user-dirs-gtk xdg-utils xdiagnose xfonts-base
  xfonts-encodings xfonts-mathml xfonts-scalable xfonts-utils xinit xinput xorg xorg-docs-core xserver-common xserver-xephyr xserver-xorg
  xserver-xorg-core xserver-xorg-input-all xserver-xorg-input-evdev xserver-xorg-input-mouse xserver-xorg-input-synaptics xserver-xorg-input-vmmouse
  xserver-xorg-input-wacom xserver-xorg-video-all xserver-xorg-video-ati xserver-xorg-video-cirrus xserver-xorg-video-fbdev
  xserver-xorg-video-glamoregl xserver-xorg-video-intel xserver-xorg-video-mach64 xserver-xorg-video-mga xserver-xorg-video-modesetting
  xserver-xorg-video-neomagic xserver-xorg-video-nouveau xserver-xorg-video-openchrome xserver-xorg-video-qxl xserver-xorg-video-r128
  xserver-xorg-video-radeon xserver-xorg-video-s3 xserver-xorg-video-savage xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident xserver-xorg-video-vesa xserver-xorg-video-vmware xsltproc xterm
  xul-ext-ubufox yelp yelp-tools yelp-xsl zeitgeist zeitgeist-core zeitgeist-datahub zenity zenity-common zip zsync
Suggested packages:
  gnome-cards-data apmd alsa-oss oss-compat default-mta mail-transport-agent libgtk2-perl gir1.2-colordgtk-1.0 aspell-doc spellutils binutils-doc
  bluez-hcidump vcdimager libdvdcss2 dvdauthor readom brltty-speechd brltty-x11 console-braille gnome-video-effects-frei0r gnome-video-effects-extra
  cpp-doc gcc-4.8-locales cups-pdf xpp wordlist emacsen-common jed-extra python-paramiko ncftp lftp python-gdata tahoe-lafs python-swiftclient
  cdrskin unrar evolution-ews evolution-plugins-experimental evolution-data-server-dbg arj lha lzip lzop ncompress p7zip-full rpm2cpio rzip
  sharutils unace unalz unar zoo ttf-lyx libgraphite3 pango-graphite hplip-cups printer-driver-all gcc-multilib autoconf automake1.9 libtool flex
  bison gcc-doc gcc-4.8-multilib gcc-4.8-doc libgcc1-dbg libgomp1-dbg libitm1-dbg libatomic1-dbg libasan0-dbg libtsan0-dbg libbacktrace1-dbg
  libquadmath0-dbg binutils-gold gconf-defaults-service gdb-doc gdbserver gedit-plugins cdrkit-doc gettext-doc hpijs gnome-screensaver xscreensaver
  desktop-base metacity x-window-manager gstreamer1.0-libav apache2.2-bin libapache2-mod-dnssd hplip-gui hplip-doc system-config-printer hunspell
  openoffice.org-hunspell openoffice.org-core ibus-clutter ibus-doc ibus-qt4 lrzip libgssapi-perl gstreamer1.0-plugins-ugly cdrdao
  gstreamer1.0-fluendo-mp3 gstreamer1.0-plugins-bad glibc-doc debian-keyring libdv-bin libenchant-voikko exiv2 libfftw3-bin libfftw3-dev libgd-tools
  libglide3 gpgsm gphoto2 gtkam gpm grilo-plugins-0.2 gstreamer-codec-install gnome-codec-install gstreamer0.10-tools gstreamer1.0-tools
  gutenprint-locales libdata-dump-perl jackd2 libjasper-runtime liblcms2-utils lirc libcrypt-ssleay-perl minissdpd natpmp-utils ttf-baekmuk
  ttf-arphic-gbsn00lp ttf-arphic-bsmi00lp ttf-arphic-gkai00mp ttf-arphic-bkai00mp pcscd raptor2-utils rasqal-utils libraw1394-doc
  librdf-storage-postgresql librdf-storage-mysql librdf-storage-sqlite librdf-storage-virtuoso redland-utils libreoffice-base libopencl1
  libreoffice-style-crystal libreoffice-style-hicontrast libreoffice-style-oxygen libreoffice-style-sifr libreoffice-evolution crystalcursors
  kde-icons-crystal tango-icon-theme libreoffice-gcj libreoffice-java-common default-jre gcj-jre openjdk-7-jre openjdk-6-jre sun-java5-jre
  sun-java6-jre java5-runtime jre librsvg2-bin hpoj libsane-extras lm-sensors sg3-utils snmp-mibs-downloader libspectre1-dbg speex unity-common
  libauthen-ntlm-perl binutils-multiarch dpkg-dev libtext-template-perl libyaml-perl make-doc account-plugin-gadugadu account-plugin-groupwise
  account-plugin-icq account-plugin-irc account-plugin-mxit account-plugin-myspace account-plugin-sametime account-plugin-sip account-plugin-yahoojp
  account-plugin-zephyr hwtools memtester kernel-patch-badram memtest86 floppyd pidgin gajim samba network-manager-openconnect-gnome
  network-manager-openvpn-gnome network-manager-vpnc-gnome hpijs-ppds diffutils-doc fonts-japanese-mincho fonts-ipafont-mincho fonts-japanese-gothic
  fonts-ipafont-gothic fonts-arphic-ukai fonts-arphic-uming fonts-unfonts-core psutils hannah-foo2zjs tix gutenprint-doc magicfilter apsfilter
  pavumeter paman pavucontrol paprefs pulseaudio-module-raop pulseaudio-esound-compat python-crypto-dbg python-crypto-doc python-dbus-doc
  python-dbus-dbg python-gdbm-dbg python-gobject-2-dbg python-gtk2-doc python-lxml-dbg python-openssl-doc python-openssl-dbg python-pam-dbg
  python-pexpect-doc python-pil-doc python-pil-dbg python-distribute python-distribute-doc libcurl4-gnutls-dev python-pycurl-dbg python-renderpm-dbg
  pdf-viewer python-egenix-mxtexttools python-reportlab-doc python-wxgtk2.8 python-wxgtk python-twisted-bin-dbg python-tk python-glade2 python-qt3
  python3-launchpadlib python3-crypto-dbg python3-beaker python-mako-doc python3-setuptools python3-pycurl-dbg heimdal-clients unpaper cifs-utils
  razor libdbi-perl pyzor libmail-dkim-perl libttspico-utils speech-dispatcher-doc-cs speech-dispatcher-festival speech-dispatcher-flite
  openssl-blacklist tcl-tclreadline totem-mozilla gromit tracker-gui ubuntu-sso-client-gui xfsprogs reiserfsprogs exfat-utils btrfs-tools mdadm
  cryptsetup-bin bsd-mailx comgt wvdial vinagre wpagui libengine-pkcs11-openssl mesa-utils nickle cairo-5c xfs xserver fonts-lyx fonts-stix
  xorg-docs xfonts-100dpi xfonts-75dpi gpointing-device-settings touchfreeze firmware-linux xfonts-cyrillic
Recommended packages:
  libc-dbg ubuntu-control-center-signon
The following NEW packages will be installed:
  account-plugin-aim account-plugin-facebook account-plugin-google account-plugin-jabber account-plugin-salut account-plugin-windows-live
  account-plugin-yahoo acl acpi-support acpid aisleriot alsa-base alsa-utils anacron apg app-install-data app-install-data-partner apport apport-gtk
  apport-symptoms aptdaemon aptdaemon-data apturl apturl-common argyll aspell aspell-en at-spi2-core avahi-autoipd avahi-daemon avahi-utils baobab
  bc binutils bluez bluez-alsa bluez-cups brasero brasero-cdrkit brasero-common brltty cheese cheese-common colord cpp cpp-4.8 cracklib-runtime cups
  cups-browsed cups-bsd cups-client cups-common cups-core-drivers cups-daemon cups-filters cups-filters-core-drivers cups-pk-helper cups-ppdc
  cups-server-common dbus-x11 dc dconf-cli dconf-editor dconf-gsettings-backend dconf-service deja-dup deja-dup-backend-cloudfiles
  deja-dup-backend-gvfs deja-dup-backend-s3 desktop-file-utils dialog dictionaries-common diffstat dnsmasq-base duplicity dvd+rw-tools empathy
  empathy-common enchant eog espeak-data evince evince-common evolution evolution-common evolution-data-server evolution-data-server-common
  evolution-data-server-online-accounts evolution-indicator evolution-plugins file-roller firefox folks-common fontconfig fontconfig-config
  fonts-cantarell fonts-dejavu-core fonts-droid fonts-freefont-ttf fonts-kacst fonts-kacst-one fonts-khmeros-core fonts-lao fonts-liberation
  fonts-lklug-sinhala fonts-nanum fonts-opensymbol fonts-sil-abyssinica fonts-sil-padauk fonts-takao-pgothic fonts-thai-tlwg fonts-tibetan-machine
  fonts-tlwg-garuda fonts-tlwg-kinnari fonts-tlwg-loma fonts-tlwg-mono fonts-tlwg-norasi fonts-tlwg-purisa fonts-tlwg-sawasdee fonts-tlwg-typewriter
  fonts-tlwg-typist fonts-tlwg-typo fonts-tlwg-umpush fonts-tlwg-waree foomatic-db-compressed-ppds gcc gcc-4.8 gconf-service gconf-service-backend
  gconf2 gconf2-common gcr gdb gdisk gdm gedit gedit-common genisoimage geoclue gettext ghostscript ghostscript-x gir1.2-accountsservice-1.0
  gir1.2-atk-1.0 gir1.2-atspi-2.0 gir1.2-caribou-1.0 gir1.2-clutter-1.0 gir1.2-clutter-gst-2.0 gir1.2-cogl-1.0 gir1.2-coglpango-1.0
  gir1.2-dbusmenu-glib-0.4 gir1.2-dee-1.0 gir1.2-evince-3.0 gir1.2-freedesktop gir1.2-gck-1 gir1.2-gcr-3 gir1.2-gdata-0.0 gir1.2-gdesktopenums-3.0
  gir1.2-gdkpixbuf-2.0 gir1.2-gdm-1.0 gir1.2-gkbd-3.0 gir1.2-gmenu-3.0 gir1.2-gnomebluetooth-1.0 gir1.2-gnomedesktop-3.0 gir1.2-gnomekeyring-1.0
  gir1.2-goa-1.0 gir1.2-gst-plugins-base-1.0 gir1.2-gstreamer-1.0 gir1.2-gtk-3.0 gir1.2-gtkclutter-1.0 gir1.2-gtksource-3.0 gir1.2-gtop-2.0
  gir1.2-gudev-1.0 gir1.2-ibus-1.0 gir1.2-javascriptcoregtk-3.0 gir1.2-json-1.0 gir1.2-mutter-3.0 gir1.2-networkmanager-1.0 gir1.2-nmgtk-1.0
  gir1.2-notify-0.7 gir1.2-packagekitglib-1.0 gir1.2-pango-1.0 gir1.2-peas-1.0 gir1.2-polkit-1.0 gir1.2-rb-3.0 gir1.2-rest-0.7 gir1.2-secret-1
  gir1.2-soup-2.4 gir1.2-telepathyglib-0.12 gir1.2-telepathylogger-0.2 gir1.2-totem-1.0 gir1.2-totem-plparser-1.0 gir1.2-tracker-0.16
  gir1.2-udisks-2.0 gir1.2-unity-5.0 gir1.2-upowerglib-1.0 gir1.2-vte-2.90 gir1.2-webkit-3.0 gir1.2-wnck-3.0 gir1.2-xkl-1.0 gir1.2-zpj-0.0 gjs
  gkbd-capplet glib-networking glib-networking-common glib-networking-services gnome-accessibility-themes gnome-backgrounds gnome-bluetooth
  gnome-calculator gnome-color-manager gnome-contacts gnome-control-center gnome-control-center-data gnome-control-center-shared-data
  gnome-desktop3-data gnome-disk-utility gnome-documents gnome-font-viewer gnome-icon-theme gnome-icon-theme-extras gnome-icon-theme-full
  gnome-icon-theme-symbolic gnome-keyring gnome-mahjongg gnome-menus gnome-mines gnome-online-accounts gnome-online-miners gnome-orca
  gnome-screenshot gnome-session gnome-session-bin gnome-session-canberra gnome-session-common gnome-settings-daemon gnome-settings-daemon-schemas
  gnome-shell gnome-shell-common gnome-shell-extensions gnome-sudoku gnome-sushi gnome-system-log gnome-system-monitor gnome-terminal
  gnome-terminal-data gnome-themes-standard gnome-themes-standard-data gnome-tweak-tool gnome-user-guide gnome-user-share gnome-video-effects
  growisofs gsettings-desktop-schemas gsettings-ubuntu-schemas gsfonts gstreamer0.10-alsa gstreamer0.10-nice gstreamer0.10-plugins-base
  gstreamer0.10-plugins-good gstreamer0.10-pulseaudio gstreamer0.10-x gstreamer1.0-alsa gstreamer1.0-clutter gstreamer1.0-nice
  gstreamer1.0-plugins-base gstreamer1.0-plugins-good gstreamer1.0-pulseaudio gstreamer1.0-x gtk2-engines-pixbuf gucharmap guile-2.0-libs gvfs
  gvfs-backends gvfs-backends-goa gvfs-bin gvfs-common gvfs-daemons gvfs-fuse gvfs-libs hardening-includes hicolor-icon-theme hplip hplip-data
  humanity-icon-theme hunspell-en-us hwdata ibus ibus-gtk ibus-gtk3 ibus-pinyin ibus-table im-config indicator-application inputattach
  intel-gpu-tools intltool-debian iproute iputils-arping itstool kerneloops-daemon libaa1 libaccount-plugin-1.0-0 libaccount-plugin-generic-oauth
  libaccount-plugin-google libaccounts-glib0 libaccounts-qt5-1 libappindicator3-1 libapt-pkg-perl libarchive-zip-perl libarchive13 libart-2.0-2
  libasan0 libasound2 libasound2-data libasound2-plugins libaspell15 libasprintf-dev libassuan0 libasyncns0 libatasmart4 libatk-adaptor
  libatk-bridge2.0-0 libatk1.0-0 libatk1.0-data libatkmm-1.6-1 libatomic1 libatspi2.0-0 libauthen-sasl-perl libautodie-perl libavahi-client3
  libavahi-common-data libavahi-common3 libavahi-core7 libavahi-glib1 libavahi-gobject0 libavc1394-0 libbluetooth3 libboost-date-time1.54.0
  libboost-system1.54.0 libbrasero-media3-1 libbrlapi0.6 libburn4 libc-dev-bin libc6-dbg libc6-dev libcaca0 libcairo-gobject2 libcairo2
  libcairomm-1.0-1 libcamel-1.2-45 libcanberra-gtk-module libcanberra-gtk0 libcanberra-gtk3-0 libcanberra-gtk3-module libcanberra-pulse libcanberra0
  libcaribou-common libcaribou0 libcdio-cdda1 libcdio-paranoia1 libcdio13 libcdparanoia0 libcdr-0.0-0 libcheese-gtk23 libcheese7 libclone-perl
  libcloog-isl4 libclucene-contribs1 libclucene-core1 libclutter-1.0-0 libclutter-1.0-common libclutter-gst-2.0-0 libclutter-gtk-1.0-0 libcmis-0.4-4
  libcogl-common libcogl-pango15 libcogl15 libcolamd2.8.0 libcolord-gtk1 libcolord1 libcolorhug1 libcrack2 libcroco3 libcrypt-passwdmd5-perl
  libcups2 libcupscgi1 libcupsfilters1 libcupsimage2 libcupsmime1 libcupsppdc1 libcurl3 libdaemon0 libdatrie1 libdbusmenu-glib4 libdbusmenu-gtk3-4
  libdbusmenu-gtk4 libdconf1 libdee-1.0-4 libdigest-hmac-perl libdjvulibre-text libdjvulibre21 libdmapsharing-3.0-2 libdotconf0 libdpkg-perl
  libdrm-intel1 libdrm-nouveau2 libdrm-radeon1 libdv4 libebackend-1.2-7 libebook-1.2-14 libebook-contacts-1.2-0 libecal-1.2-16 libedata-book-1.2-20
  libedata-cal-1.2-23 libedataserver-1.2-18 libegl1-mesa libegl1-mesa-drivers libelfg0 libemail-valid-perl libenca0 libenchant1c2a
  libencode-locale-perl liberror-perl libespeak1 libevdocument3-4 libevent-2.0-5 libevolution libevview3-3 libexempi3 libexif12 libexiv2-12
  libexttextcat-2.0-0 libexttextcat-data libfarstream-0.1-0 libfarstream-0.2-2 libfftw3-single3 libfile-basedir-perl libfile-copy-recursive-perl
  libfile-desktopentry-perl libfile-fcntllock-perl libfile-listing-perl libfile-mimeinfo-perl libflac8 libfolks-eds25 libfolks-telepathy25
  libfolks25 libfont-afm-perl libfontconfig1 libfontembed1 libfontenc1 libframe6 libfs6 libgail-3-0 libgail-common libgail18 libgbm1 libgc1c2
  libgcc-4.8-dev libgconf-2-4 libgcr-ui-3-1 libgd3 libgdata-common libgdata13 libgdk-pixbuf2.0-0 libgdk-pixbuf2.0-common libgdm1 libgee-0.8-2
  libgeis1 libgeoclue0 libgettextpo-dev libgettextpo0 libgif4 libgjs0e libgl1-mesa-dri libgl1-mesa-glx libglamor0 libglapi-mesa libgles2-mesa
  libglib2.0-bin libglibmm-2.4-1c2a libglu1-mesa libgmime-2.6-0 libgmp10 libgnome-bluetooth11 libgnome-control-center1 libgnome-desktop-3-7
  libgnome-keyring-common libgnome-keyring0 libgnome-menu-3-0 libgnomekbd-common libgnomekbd8 libgoa-1.0-0b libgoa-1.0-common libgoa-backend-1.0-1
  libgomp1 libgpgme11 libgphoto2-6 libgphoto2-l10n libgphoto2-port10 libgpm2 libgpod-common libgpod4 libgrail6 libgraphite2-3 libgrilo-0.2-1
  libgrip0 libgs9 libgs9-common libgsf-1-114 libgsf-1-common libgssdp-1.0-3 libgstreamer-plugins-base0.10-0 libgstreamer-plugins-base1.0-0
  libgstreamer-plugins-good1.0-0 libgstreamer0.10-0 libgstreamer1.0-0 libgtk-3-0 libgtk-3-bin libgtk-3-common libgtk2.0-0 libgtk2.0-bin
  libgtk2.0-common libgtkhtml-4.0-0 libgtkhtml-4.0-common libgtkhtml-editor-4.0-0 libgtkmm-3.0-1 libgtksourceview-3.0-1 libgtksourceview-3.0-common
  libgtop2-7 libgtop2-common libgucharmap-2-90-7 libgudev-1.0-0 libgupnp-1.0-4 libgupnp-igd-1.0-4 libgusb2 libgutenprint2 libgweather-3-6
  libgweather-common libgxps2 libharfbuzz-icu0 libharfbuzz0b libhpmud0 libhtml-form-perl libhtml-format-perl libhtml-parser-perl libhtml-tagset-perl
  libhtml-tree-perl libhttp-cookies-perl libhttp-daemon-perl libhttp-date-perl libhttp-message-perl libhttp-negotiate-perl libhunspell-1.3-0
  libhyphen0 libibus-1.0-5 libical1 libicc2 libice6 libicu52 libido3-0.1-0 libiec61883-0 libieee1284-3 libijs-0.35 libimdi0 libimobiledevice4
  libindicator3-7 libio-html-perl libio-pty-perl libio-socket-inet6-perl libio-socket-ssl-perl libipc-run-perl libipc-system-simple-perl
  libiptcdata0 libisl10 libisofs6 libitm1 libiw30 libjack-jackd2-0 libjasper1 libjavascriptcoregtk-3.0-0 libjbig0 libjbig2dec0 libjpeg-turbo8
  libjpeg8 libjson-glib-1.0-0 libjson-glib-1.0-common libjte1 libkpathsea6 liblangtag-common liblangtag1 liblcms2-2 libldb1 liblircclient0
  liblist-moreutils-perl libllvm3.4 liblouis-data liblouis2 libltdl7 liblua5.2-0 liblwp-mediatypes-perl liblwp-protocol-https-perl liblzo2-2
  libmail-spf-perl libmailtools-perl libmbim-glib0 libmeanwhile1 libmessaging-menu0 libmhash2 libminiupnpc8 libmission-control-plugins0 libmm-glib0
  libmnl0 libmozjs-24-0 libmpc3 libmpfr4 libmspub-0.0-0 libmtdev1 libmtp-common libmtp-runtime libmtp9 libmusicbrainz5-0 libmutter0c libmythes-1.2-0
  libnatpmp1 libnautilus-extension1a libneon27-gnutls libnet-dns-perl libnet-domain-tld-perl libnet-http-perl libnet-ip-perl libnet-libidn-perl
  libnet-smtp-ssl-perl libnet-ssleay-perl libnetaddr-ip-perl libnetfilter-conntrack3 libnettle4 libnice10 libnl-route-3-200 libnm-glib-vpn1
  libnm-glib4 libnm-gtk-common libnm-gtk0 libnm-util2 libnotify-bin libnotify4 libnspr4 libnss-mdns libnss-myhostname libnss3 libnss3-nssdb libntdb1
  liboauth0 libogg0 libopencc1 libopenobex1 libopenvg1-mesa liborc-0.4-0 liborcus-0.6-0 libp11-kit-gnome-keyring libpackagekit-glib2-16
  libpam-gnome-keyring libpango-1.0-0 libpango1.0-0 libpangocairo-1.0-0 libpangoft2-1.0-0 libpangomm-1.4-1 libpangox-1.0-0 libpangoxft-1.0-0
  libpaper-utils libpaper1 libpciaccess0 libpcsclite1 libpeas-1.0-0 libpeas-common libperl5.18 libperlio-gzip-perl libpixman-1-0 libplist1
  libpolkit-agent-1-0 libpolkit-backend-1-0 libpoppler-glib8 libpoppler44 libportaudio2 libproxy1 libproxy1-plugin-gsettings
  libproxy1-plugin-networkmanager libpst4 libpulse-mainloop-glib0 libpulse0 libpulsedsp libpurple-bin libpurple0 libpwquality-common libpwquality1
  libpython2.7 libpython3.4 libpyzy-1.0-0 libqmi-glib0 libqpdf13 libqt5core5a libqt5dbus5 libqt5gui5 libqt5network5 libqt5opengl5 libqt5positioning5
  libqt5printsupport5 libqt5qml5 libqt5quick5 libqt5sensors5 libqt5sql5 libqt5sql5-sqlite libqt5test5 libqt5webkit5 libqt5widgets5 libqt5xml5
  libquadmath0 libraptor2-0 librasqal3 libraw1394-11 librdf0 libreadline5 libreoffice-avmedia-backend-gstreamer libreoffice-base-core
  libreoffice-calc libreoffice-common libreoffice-core libreoffice-draw libreoffice-gnome libreoffice-gtk libreoffice-impress libreoffice-math
  libreoffice-ogltrans libreoffice-pdfimport libreoffice-presentation-minimizer libreoffice-style-galaxy libreoffice-style-human
  libreoffice-style-tango libreoffice-writer librest-0.7-0 librhythmbox-core8 librsvg2-2 librsvg2-common librsync1 libsamplerate0 libsane
  libsane-common libsane-hpaio libsbc1 libsecret-1-0 libsecret-common libsensors4 libsgutils2-2 libshout3 libsignon-extension1 libsignon-glib1
  libsignon-plugins-common1 libsignon-qt5-1 libsm6 libsmbclient libsndfile1 libsnmp-base libsnmp30 libsocket6-perl libsonic0 libsoup-gnome2.4-1
  libsoup2.4-1 libspectre1 libspeechd2 libspeex1 libspeexdsp1 libstartup-notification0 libsub-identify-perl libsys-hostname-long-perl
  libsystemd-journal0 libt1-5 libtag1-vanilla libtag1c2a libtalloc2 libtcl8.6 libtdb1 libtelepathy-farstream3 libtelepathy-glib0
  libtelepathy-logger3 libtevent0 libtext-levenshtein-perl libthai-data libthai0 libtheora0 libtiff5 libtimezonemap1 libtk8.6 libtotem-plparser18
  libtotem0 libtracker-extract-0.16-0 libtracker-miner-0.16-0 libtracker-sparql-0.16-0 libtxc-dxtn-s2tc0 libudisks2-0 libunistring0
  libunity-control-center1 libunity-protocol-private0 libunity-scopes-json-def-desktop libunity9 libupower-glib1 liburi-perl libusbmuxd2
  libutempter0 libv4l-0 libv4lconvert0 libvisio-0.0-0 libvisual-0.4-0 libvisual-0.4-plugins libvorbis0a libvorbisenc2 libvorbisfile3 libvpx1
  libvte-2.90-9 libvte-2.90-common libwacom-common libwacom2 libwavpack1 libwayland-client0 libwayland-cursor0 libwayland-egl1-mesa
  libwayland-server0 libwbclient0 libwebkitgtk-3.0-0 libwebkitgtk-3.0-common libwebp5 libwebpmux1 libwhoopsie0 libwmf0.2-7 libwmf0.2-7-gtk
  libwnck-3-0 libwnck-3-common libwpd-0.9-9 libwpg-0.2-2 libwps-0.2-2 libwrap0 libwww-perl libwww-robotrules-perl libx11-xcb1 libxatracker2 libxaw7
  libxcb-dri2-0 libxcb-dri3-0 libxcb-glx0 libxcb-icccm4 libxcb-image0 libxcb-keysyms1 libxcb-present0 libxcb-randr0 libxcb-render-util0
  libxcb-render0 libxcb-shape0 libxcb-shm0 libxcb-sync1 libxcb-util0 libxcb-xf86dri0 libxcb-xfixes0 libxcb-xkb1 libxcb-xv0 libxcomposite1
  libxcursor1 libxdamage1 libxfixes3 libxfont1 libxft2 libxi6 libxinerama1 libxkbcommon0 libxkbfile1 libxklavier16 libxml2-utils libxmu6 libxp6
  libxpm4 libxrandr2 libxrender1 libxres1 libxshmfence1 libxslt1.1 libxss1 libxt6 libxtst6 libxv1 libxvmc1 libxxf86dga1 libxxf86vm1 libyajl2
  libyelp0 libytnef0 libzapojit-0.0-0 libzeitgeist-1.0-1 libzeitgeist-2.0-0 libzephyr4 lintian linux-libc-dev linux-sound-base lp-solve make
  manpages-dev mcp-account-manager-goa mcp-account-manager-uoa media-player-info memtest86+ mobile-broadband-provider-info modemmanager mousetweaks
  mscompress mtools mutter mutter-common nautilus nautilus-data nautilus-sendto nautilus-sendto-empathy nautilus-share network-manager
  network-manager-gnome network-manager-pptp network-manager-pptp-gnome notification-daemon obex-data-server obexd-client oneconf oneconf-common
  openprinting-ppds p11-kit p11-kit-modules patch patchutils pcmciautils plymouth-label plymouth-theme-ubuntu-gnome-logo
  plymouth-theme-ubuntu-gnome-text policykit-1 policykit-1-gnome policykit-desktop-privileges poppler-data poppler-utils pptp-linux
  printer-driver-c2esp printer-driver-foo2zjs printer-driver-foo2zjs-common printer-driver-gutenprint printer-driver-hpcups printer-driver-min12xxw
  printer-driver-pnm2ppa printer-driver-postscript-hp printer-driver-ptouch printer-driver-pxljr printer-driver-sag-gdi printer-driver-splix
  pulseaudio pulseaudio-module-bluetooth pulseaudio-module-x11 pulseaudio-utils python-aptdaemon python-aptdaemon.gtk3widgets python-boto
  python-cairo python-cloudfiles python-commandnotfound python-crypto python-cups python-cupshelpers python-dbus python-dbus-dev python-debtagshw
  python-defer python-dirspec python-gdbm python-gi python-gi-cairo python-gnomekeyring python-gobject python-gobject-2 python-gtk2 python-httplib2
  python-ibus python-imaging python-ldb python-libxml2 python-lockfile python-lxml python-notify python-ntdb python-oauthlib python-oneconf
  python-openssl python-pam python-pexpect python-pil python-piston-mini-client python-pkg-resources python-pycurl python-renderpm python-reportlab
  python-reportlab-accel python-requests python-samba python-serial python-smbc python-talloc python-tdb python-twisted-bin python-twisted-core
  python-twisted-web python-ubuntu-sso-client python-urllib3 python-xdg python-zeitgeist python-zope.interface python3-apport python3-aptdaemon
  python3-aptdaemon.gtk3widgets python3-aptdaemon.pkcompat python3-brlapi python3-cairo python3-chardet python3-crypto python3-debian python3-defer
  python3-gi-cairo python3-httplib2 python3-louis python3-mako python3-markupsafe python3-oauthlib python3-oneconf python3-piston-mini-client
  python3-pkg-resources python3-problem-report python3-pyatspi python3-pycurl python3-six python3-software-properties python3-speechd python3-uno
  python3-xdg python3-xkit qpdf re2c rfkill rhythmbox rhythmbox-data rhythmbox-mozilla rhythmbox-plugin-cdrecorder rhythmbox-plugin-magnatune
  rhythmbox-plugin-zeitgeist rhythmbox-plugins rtkit sa-compile samba-common samba-common-bin samba-libs sane-utils seahorse session-migration
  sessioninstaller signon-keyring-extension signon-plugin-oauth2 signon-plugin-password signon-ui signond simple-scan smbclient software-center
  software-center-aptdaemon-plugins software-properties-common software-properties-gtk sound-theme-freedesktop spamassassin spamc speech-dispatcher
  speech-dispatcher-audio-plugins ssh-askpass-gnome ssl-cert syslinux syslinux-common syslinux-legacy system-config-printer-common
  system-config-printer-gnome system-config-printer-udev t1utils tcl tcl8.6 tcpd telepathy-gabble telepathy-haze telepathy-idle telepathy-logger
  telepathy-mission-control-5 telepathy-salut tk tk8.6 toshset totem totem-common totem-plugins tracker tracker-extract tracker-miner-fs
  tracker-utils transmission-common transmission-gtk ttf-indic-fonts-core ttf-punjabi-fonts ttf-ubuntu-font-family ubuntu-drivers-common
  ubuntu-extras-keyring ubuntu-gnome-default-settings ubuntu-gnome-desktop ubuntu-release-upgrader-gtk ubuntu-sso-client ubuntu-system-service
  udisks2 unattended-upgrades unity-asset-pool unity-control-center unity-control-center-signon unity-settings-daemon uno-libs3 unoconv unzip
  update-inetd update-manager update-notifier update-notifier-common upower ure usb-creator-common usb-creator-gtk usb-modeswitch
  usb-modeswitch-data usbmuxd vino wamerican whoopsie wireless-tools wodim wpasupplicant x11-apps x11-common x11-session-utils x11-utils
  x11-xfs-utils x11-xkb-utils x11-xserver-utils xbitmaps xdg-user-dirs xdg-user-dirs-gtk xdg-utils xdiagnose xfonts-base xfonts-encodings
  xfonts-mathml xfonts-scalable xfonts-utils xinit xinput xorg xorg-docs-core xserver-common xserver-xephyr xserver-xorg xserver-xorg-core
  xserver-xorg-input-all xserver-xorg-input-evdev xserver-xorg-input-mouse xserver-xorg-input-synaptics xserver-xorg-input-vmmouse
  xserver-xorg-input-wacom xserver-xorg-video-all xserver-xorg-video-ati xserver-xorg-video-cirrus xserver-xorg-video-fbdev
  xserver-xorg-video-glamoregl xserver-xorg-video-intel xserver-xorg-video-mach64 xserver-xorg-video-mga xserver-xorg-video-modesetting
  xserver-xorg-video-neomagic xserver-xorg-video-nouveau xserver-xorg-video-openchrome xserver-xorg-video-qxl xserver-xorg-video-r128
  xserver-xorg-video-radeon xserver-xorg-video-s3 xserver-xorg-video-savage xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident xserver-xorg-video-vesa xserver-xorg-video-vmware xsltproc xterm
  xul-ext-ubufox yelp yelp-tools yelp-xsl zeitgeist zeitgeist-core zeitgeist-datahub zenity zenity-common zip zsync
The following packages will be upgraded:
  libglib2.0-0 libplymouth2 plymouth
3 upgraded, 1212 newly installed, 0 to remove and 10 not upgraded.
Need to get 442 MB of archives.
After this operation, 1,676 MB of additional disk space will be used.
Do you want to continue? [Y/n] n
Abort.

```

---

### Post by kansasnoob on 2014-04-03
Things puke if I exclude 'gnome-bluetooth':

```
root@lance-desktop:/# apt-get install ubuntu-gnome-desktop gnome-bluetooth-
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'gnome-bluetooth' is not installed, so not removed
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 ubuntu-gnome-desktop : Depends: gdm but it is not going to be installed
                        Depends: gnome-shell but it is not going to be installed
                        Depends: gnome-shell-extensions but it is not going to be installed
                        Depends: gnome-user-share but it is not going to be installed
                        Recommends: gnome-bluetooth but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

---

### Post by kansasnoob on 2014-04-03
Excluding 'empathy' dramatically reduces the package count to 1149:

```
root@lance-desktop:/# apt-get install ubuntu-gnome-desktop empathy-
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'empathy' is not installed, so not removed
The following extra packages will be installed:
  acl acpi-support acpid aisleriot alsa-base alsa-utils anacron apg app-install-data app-install-data-partner apport apport-gtk apport-symptoms
  aptdaemon aptdaemon-data apturl apturl-common argyll aspell aspell-en at-spi2-core avahi-autoipd avahi-daemon avahi-utils baobab bc binutils bluez
  bluez-alsa bluez-cups brasero brasero-cdrkit brasero-common brltty cheese cheese-common colord cpp cpp-4.8 cracklib-runtime cups cups-browsed
  cups-bsd cups-client cups-common cups-core-drivers cups-daemon cups-filters cups-filters-core-drivers cups-pk-helper cups-ppdc cups-server-common
  dbus-x11 dc dconf-cli dconf-editor dconf-gsettings-backend dconf-service deja-dup deja-dup-backend-cloudfiles deja-dup-backend-gvfs
  deja-dup-backend-s3 desktop-file-utils dialog dictionaries-common diffstat dnsmasq-base duplicity dvd+rw-tools enchant eog espeak-data evince
  evince-common evolution evolution-common evolution-data-server evolution-data-server-common evolution-data-server-online-accounts
  evolution-indicator evolution-plugins file-roller firefox folks-common fontconfig fontconfig-config fonts-cantarell fonts-dejavu-core fonts-droid
  fonts-freefont-ttf fonts-kacst fonts-kacst-one fonts-khmeros-core fonts-lao fonts-liberation fonts-lklug-sinhala fonts-nanum fonts-opensymbol
  fonts-sil-abyssinica fonts-sil-padauk fonts-takao-pgothic fonts-thai-tlwg fonts-tibetan-machine fonts-tlwg-garuda fonts-tlwg-kinnari
  fonts-tlwg-loma fonts-tlwg-mono fonts-tlwg-norasi fonts-tlwg-purisa fonts-tlwg-sawasdee fonts-tlwg-typewriter fonts-tlwg-typist fonts-tlwg-typo
  fonts-tlwg-umpush fonts-tlwg-waree foomatic-db-compressed-ppds gcc gcc-4.8 gconf-service gconf-service-backend gconf2 gconf2-common gcr gdb gdisk
  gdm gedit gedit-common genisoimage gettext ghostscript ghostscript-x gir1.2-accountsservice-1.0 gir1.2-atk-1.0 gir1.2-atspi-2.0 gir1.2-caribou-1.0
  gir1.2-clutter-1.0 gir1.2-clutter-gst-2.0 gir1.2-cogl-1.0 gir1.2-coglpango-1.0 gir1.2-dbusmenu-glib-0.4 gir1.2-dee-1.0 gir1.2-evince-3.0
  gir1.2-freedesktop gir1.2-gck-1 gir1.2-gcr-3 gir1.2-gdata-0.0 gir1.2-gdesktopenums-3.0 gir1.2-gdkpixbuf-2.0 gir1.2-gdm-1.0 gir1.2-gkbd-3.0
  gir1.2-gmenu-3.0 gir1.2-gnomebluetooth-1.0 gir1.2-gnomedesktop-3.0 gir1.2-gnomekeyring-1.0 gir1.2-goa-1.0 gir1.2-gst-plugins-base-1.0
  gir1.2-gstreamer-1.0 gir1.2-gtk-3.0 gir1.2-gtkclutter-1.0 gir1.2-gtksource-3.0 gir1.2-gtop-2.0 gir1.2-gudev-1.0 gir1.2-ibus-1.0
  gir1.2-javascriptcoregtk-3.0 gir1.2-json-1.0 gir1.2-mutter-3.0 gir1.2-networkmanager-1.0 gir1.2-nmgtk-1.0 gir1.2-notify-0.7
  gir1.2-packagekitglib-1.0 gir1.2-pango-1.0 gir1.2-peas-1.0 gir1.2-polkit-1.0 gir1.2-rb-3.0 gir1.2-rest-0.7 gir1.2-secret-1 gir1.2-soup-2.4
  gir1.2-telepathyglib-0.12 gir1.2-telepathylogger-0.2 gir1.2-totem-1.0 gir1.2-totem-plparser-1.0 gir1.2-tracker-0.16 gir1.2-udisks-2.0
  gir1.2-unity-5.0 gir1.2-upowerglib-1.0 gir1.2-vte-2.90 gir1.2-webkit-3.0 gir1.2-wnck-3.0 gir1.2-xkl-1.0 gir1.2-zpj-0.0 gjs gkbd-capplet
  glib-networking glib-networking-common glib-networking-services gnome-accessibility-themes gnome-backgrounds gnome-bluetooth gnome-calculator
  gnome-color-manager gnome-contacts gnome-control-center gnome-control-center-data gnome-control-center-shared-data gnome-desktop3-data
  gnome-disk-utility gnome-documents gnome-font-viewer gnome-icon-theme gnome-icon-theme-extras gnome-icon-theme-full gnome-icon-theme-symbolic
  gnome-keyring gnome-mahjongg gnome-menus gnome-mines gnome-online-accounts gnome-online-miners gnome-orca gnome-screenshot gnome-session
  gnome-session-bin gnome-session-canberra gnome-session-common gnome-settings-daemon gnome-settings-daemon-schemas gnome-shell gnome-shell-common
  gnome-shell-extensions gnome-sudoku gnome-sushi gnome-system-log gnome-system-monitor gnome-terminal gnome-terminal-data gnome-themes-standard
  gnome-themes-standard-data gnome-tweak-tool gnome-user-guide gnome-user-share gnome-video-effects growisofs gsettings-desktop-schemas
  gsettings-ubuntu-schemas gsfonts gstreamer0.10-alsa gstreamer0.10-pulseaudio gstreamer1.0-alsa gstreamer1.0-clutter gstreamer1.0-plugins-base
  gstreamer1.0-plugins-good gstreamer1.0-pulseaudio gstreamer1.0-x gtk2-engines-pixbuf gucharmap guile-2.0-libs gvfs gvfs-backends gvfs-backends-goa
  gvfs-bin gvfs-common gvfs-daemons gvfs-fuse gvfs-libs hardening-includes hicolor-icon-theme hplip hplip-data humanity-icon-theme hunspell-en-us
  hwdata ibus ibus-gtk ibus-gtk3 ibus-pinyin ibus-table im-config indicator-application inputattach intel-gpu-tools intltool-debian iproute
  iputils-arping itstool kerneloops-daemon libaa1 libaccounts-glib0 libappindicator3-1 libapt-pkg-perl libarchive-zip-perl libarchive13 libart-2.0-2
  libasan0 libasound2 libasound2-data libasound2-plugins libaspell15 libasprintf-dev libassuan0 libasyncns0 libatasmart4 libatk-adaptor
  libatk-bridge2.0-0 libatk1.0-0 libatk1.0-data libatkmm-1.6-1 libatomic1 libatspi2.0-0 libauthen-sasl-perl libautodie-perl libavahi-client3
  libavahi-common-data libavahi-common3 libavahi-core7 libavahi-glib1 libavc1394-0 libbluetooth3 libboost-date-time1.54.0 libboost-system1.54.0
  libbrasero-media3-1 libbrlapi0.6 libburn4 libc-dev-bin libc6-dbg libc6-dev libcaca0 libcairo-gobject2 libcairo2 libcairomm-1.0-1 libcamel-1.2-45
  libcanberra-gtk-module libcanberra-gtk0 libcanberra-gtk3-0 libcanberra-gtk3-module libcanberra-pulse libcanberra0 libcaribou-common libcaribou0
  libcdio-cdda1 libcdio-paranoia1 libcdio13 libcdparanoia0 libcdr-0.0-0 libcheese-gtk23 libcheese7 libclone-perl libcloog-isl4 libclucene-contribs1
  libclucene-core1 libclutter-1.0-0 libclutter-1.0-common libclutter-gst-2.0-0 libclutter-gtk-1.0-0 libcmis-0.4-4 libcogl-common libcogl-pango15
  libcogl15 libcolamd2.8.0 libcolord-gtk1 libcolord1 libcolorhug1 libcrack2 libcroco3 libcrypt-passwdmd5-perl libcups2 libcupscgi1 libcupsfilters1
  libcupsimage2 libcupsmime1 libcupsppdc1 libcurl3 libdaemon0 libdatrie1 libdbusmenu-glib4 libdbusmenu-gtk3-4 libdbusmenu-gtk4 libdconf1
  libdee-1.0-4 libdigest-hmac-perl libdjvulibre-text libdjvulibre21 libdmapsharing-3.0-2 libdotconf0 libdpkg-perl libdrm-intel1 libdrm-nouveau2
  libdrm-radeon1 libdv4 libebackend-1.2-7 libebook-1.2-14 libebook-contacts-1.2-0 libecal-1.2-16 libedata-book-1.2-20 libedata-cal-1.2-23
  libedataserver-1.2-18 libegl1-mesa libegl1-mesa-drivers libelfg0 libemail-valid-perl libenca0 libenchant1c2a libencode-locale-perl liberror-perl
  libespeak1 libevdocument3-4 libevent-2.0-5 libevolution libevview3-3 libexempi3 libexif12 libexiv2-12 libexttextcat-2.0-0 libexttextcat-data
  libfftw3-single3 libfile-basedir-perl libfile-copy-recursive-perl libfile-desktopentry-perl libfile-fcntllock-perl libfile-listing-perl
  libfile-mimeinfo-perl libflac8 libfolks-eds25 libfolks-telepathy25 libfolks25 libfont-afm-perl libfontconfig1 libfontembed1 libfontenc1 libframe6
  libfs6 libgail-3-0 libgail-common libgail18 libgbm1 libgc1c2 libgcc-4.8-dev libgconf-2-4 libgcr-ui-3-1 libgd3 libgdata-common libgdata13
  libgdk-pixbuf2.0-0 libgdk-pixbuf2.0-common libgdm1 libgee-0.8-2 libgeis1 libgeoclue0 libgettextpo-dev libgettextpo0 libgexiv2-2 libgif4 libgjs0e
  libgl1-mesa-dri libgl1-mesa-glx libglamor0 libglapi-mesa libglib2.0-0 libglib2.0-bin libglibmm-2.4-1c2a libglu1-mesa libgmime-2.6-0 libgmp10
  libgnome-bluetooth11 libgnome-control-center1 libgnome-desktop-3-7 libgnome-keyring-common libgnome-keyring0 libgnome-menu-3-0 libgnomekbd-common
  libgnomekbd8 libgoa-1.0-0b libgoa-1.0-common libgoa-backend-1.0-1 libgomp1 libgpgme11 libgphoto2-6 libgphoto2-l10n libgphoto2-port10 libgpm2
  libgpod-common libgpod4 libgrail6 libgraphite2-3 libgrilo-0.2-1 libgrip0 libgs9 libgs9-common libgsf-1-114 libgsf-1-common libgssdp-1.0-3
  libgstreamer-plugins-base0.10-0 libgstreamer-plugins-base1.0-0 libgstreamer-plugins-good1.0-0 libgstreamer0.10-0 libgstreamer1.0-0 libgtk-3-0
  libgtk-3-bin libgtk-3-common libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libgtkhtml-4.0-0 libgtkhtml-4.0-common libgtkhtml-editor-4.0-0
  libgtkmm-3.0-1 libgtksourceview-3.0-1 libgtksourceview-3.0-common libgtop2-7 libgtop2-common libgucharmap-2-90-7 libgudev-1.0-0 libgupnp-1.0-4
  libgusb2 libgutenprint2 libgweather-3-6 libgweather-common libgxps2 libharfbuzz-icu0 libharfbuzz0b libhpmud0 libhtml-form-perl libhtml-format-perl
  libhtml-parser-perl libhtml-tagset-perl libhtml-tree-perl libhttp-cookies-perl libhttp-daemon-perl libhttp-date-perl libhttp-message-perl
  libhttp-negotiate-perl libhunspell-1.3-0 libhyphen0 libibus-1.0-5 libical1 libicc2 libice6 libicu52 libiec61883-0 libieee1284-3 libijs-0.35
  libimdi0 libimobiledevice4 libindicator3-7 libio-html-perl libio-pty-perl libio-socket-inet6-perl libio-socket-ssl-perl libipc-run-perl
  libipc-system-simple-perl libiptcdata0 libisl10 libisofs6 libitm1 libiw30 libjack-jackd2-0 libjasper1 libjavascriptcoregtk-3.0-0 libjbig0
  libjbig2dec0 libjpeg-turbo8 libjpeg8 libjson-glib-1.0-0 libjson-glib-1.0-common libjte1 libkpathsea6 liblangtag-common liblangtag1 liblcms2-2
  libldb1 liblircclient0 liblist-moreutils-perl libllvm3.4 liblouis-data liblouis2 libltdl7 liblua5.2-0 liblwp-mediatypes-perl
  liblwp-protocol-https-perl liblzo2-2 libmail-spf-perl libmailtools-perl libmbim-glib0 libmessaging-menu0 libmhash2 libminiupnpc8
  libmission-control-plugins0 libmm-glib0 libmnl0 libmozjs-24-0 libmpc3 libmpfr4 libmspub-0.0-0 libmtdev1 libmtp-common libmtp-runtime libmtp9
  libmusicbrainz5-0 libmutter0c libmythes-1.2-0 libnatpmp1 libnautilus-extension1a libneon27-gnutls libnet-dns-perl libnet-domain-tld-perl
  libnet-http-perl libnet-ip-perl libnet-libidn-perl libnet-smtp-ssl-perl libnet-ssleay-perl libnetaddr-ip-perl libnetfilter-conntrack3 libnettle4
  libnl-route-3-200 libnm-glib-vpn1 libnm-glib4 libnm-gtk-common libnm-gtk0 libnm-util2 libnotify-bin libnotify4 libnspr4 libnss-mdns
  libnss-myhostname libnss3 libnss3-nssdb libntdb1 liboauth0 libogg0 libopencc1 libopenobex1 libopenvg1-mesa liborc-0.4-0 liborcus-0.6-0
  libp11-kit-gnome-keyring libpackagekit-glib2-16 libpam-gnome-keyring libpango-1.0-0 libpango1.0-0 libpangocairo-1.0-0 libpangoft2-1.0-0
  libpangomm-1.4-1 libpangox-1.0-0 libpangoxft-1.0-0 libpaper-utils libpaper1 libpciaccess0 libpcsclite1 libpeas-1.0-0 libpeas-common libperl5.18
  libperlio-gzip-perl libpixman-1-0 libplist1 libplymouth2 libpolkit-agent-1-0 libpolkit-backend-1-0 libpoppler-glib8 libpoppler44 libportaudio2
  libproxy1 libproxy1-plugin-gsettings libproxy1-plugin-networkmanager libpst4 libpulse-mainloop-glib0 libpulse0 libpulsedsp libpwquality-common
  libpwquality1 libpython2.7 libpython3.4 libpyzy-1.0-0 libqmi-glib0 libqpdf13 libquadmath0 libraptor2-0 librasqal3 libraw1394-11 libraw9 librdf0
  libreadline5 libreoffice-avmedia-backend-gstreamer libreoffice-base-core libreoffice-calc libreoffice-common libreoffice-core libreoffice-draw
  libreoffice-gnome libreoffice-gtk libreoffice-impress libreoffice-math libreoffice-ogltrans libreoffice-pdfimport
  libreoffice-presentation-minimizer libreoffice-style-galaxy libreoffice-style-human libreoffice-style-tango libreoffice-writer librest-0.7-0
  librhythmbox-core8 librsvg2-2 librsvg2-common librsync1 libsamplerate0 libsane libsane-common libsane-hpaio libsbc1 libsecret-1-0 libsecret-common
  libsensors4 libsgutils2-2 libshout3 libsignon-glib1 libsm6 libsmbclient libsndfile1 libsnmp-base libsnmp30 libsocket6-perl libsonic0
  libsoup-gnome2.4-1 libsoup2.4-1 libspectre1 libspeechd2 libspeex1 libspeexdsp1 libstartup-notification0 libsub-identify-perl
  libsys-hostname-long-perl libsystemd-journal0 libt1-5 libtag1-vanilla libtag1c2a libtalloc2 libtcl8.6 libtdb1 libtelepathy-glib0
  libtelepathy-logger3 libtevent0 libtext-levenshtein-perl libthai-data libthai0 libtheora0 libtiff5 libtimezonemap1 libtk8.6 libtotem-plparser18
  libtotem0 libtracker-extract-0.16-0 libtracker-miner-0.16-0 libtracker-sparql-0.16-0 libtxc-dxtn-s2tc0 libudisks2-0 libunistring0
  libunity-control-center1 libunity-protocol-private0 libunity-scopes-json-def-desktop libunity9 libupower-glib1 liburi-perl libusbmuxd2
  libutempter0 libv4l-0 libv4lconvert0 libvisio-0.0-0 libvisual-0.4-0 libvisual-0.4-plugins libvorbis0a libvorbisenc2 libvorbisfile3 libvpx1
  libvte-2.90-9 libvte-2.90-common libwacom-common libwacom2 libwavpack1 libwayland-client0 libwayland-cursor0 libwayland-egl1-mesa
  libwayland-server0 libwbclient0 libwebkitgtk-3.0-0 libwebkitgtk-3.0-common libwebp5 libwebpmux1 libwhoopsie0 libwmf0.2-7 libwmf0.2-7-gtk
  libwnck-3-0 libwnck-3-common libwpd-0.9-9 libwpg-0.2-2 libwps-0.2-2 libwrap0 libwww-perl libwww-robotrules-perl libx11-xcb1 libxatracker2 libxaw7
  libxcb-dri2-0 libxcb-dri3-0 libxcb-glx0 libxcb-icccm4 libxcb-image0 libxcb-keysyms1 libxcb-present0 libxcb-render0 libxcb-shape0 libxcb-shm0
  libxcb-sync1 libxcb-util0 libxcb-xf86dri0 libxcb-xfixes0 libxcb-xv0 libxcomposite1 libxcursor1 libxdamage1 libxfixes3 libxfont1 libxft2 libxi6
  libxinerama1 libxkbcommon0 libxkbfile1 libxklavier16 libxml2-utils libxmu6 libxp6 libxpm4 libxrandr2 libxrender1 libxres1 libxshmfence1 libxslt1.1
  libxss1 libxt6 libxtst6 libxv1 libxvmc1 libxxf86dga1 libxxf86vm1 libyajl2 libyelp0 libytnef0 libzapojit-0.0-0 libzeitgeist-1.0-1
  libzeitgeist-2.0-0 lintian linux-libc-dev linux-sound-base lp-solve make manpages-dev media-player-info memtest86+ mobile-broadband-provider-info
  modemmanager mousetweaks mscompress mtools mutter mutter-common nautilus nautilus-data nautilus-sendto nautilus-share network-manager
  network-manager-gnome network-manager-pptp network-manager-pptp-gnome notification-daemon obex-data-server obexd-client oneconf oneconf-common
  openprinting-ppds p11-kit p11-kit-modules patch patchutils pcmciautils plymouth plymouth-label plymouth-theme-ubuntu-gnome-logo
  plymouth-theme-ubuntu-gnome-text policykit-1 policykit-1-gnome policykit-desktop-privileges poppler-data poppler-utils pptp-linux
  printer-driver-c2esp printer-driver-foo2zjs printer-driver-foo2zjs-common printer-driver-gutenprint printer-driver-hpcups printer-driver-min12xxw
  printer-driver-pnm2ppa printer-driver-postscript-hp printer-driver-ptouch printer-driver-pxljr printer-driver-sag-gdi printer-driver-splix
  pulseaudio pulseaudio-module-bluetooth pulseaudio-module-x11 pulseaudio-utils python-aptdaemon python-aptdaemon.gtk3widgets python-boto
  python-cairo python-cloudfiles python-commandnotfound python-crypto python-cups python-cupshelpers python-dbus python-dbus-dev python-debtagshw
  python-defer python-dirspec python-gdbm python-gi python-gi-cairo python-gnomekeyring python-gobject python-gobject-2 python-gtk2 python-httplib2
  python-ibus python-imaging python-ldb python-libxml2 python-lockfile python-lxml python-notify python-ntdb python-oauthlib python-oneconf
  python-openssl python-pam python-pexpect python-pil python-piston-mini-client python-pkg-resources python-pycurl python-renderpm python-reportlab
  python-reportlab-accel python-requests python-samba python-serial python-smbc python-talloc python-tdb python-twisted-bin python-twisted-core
  python-twisted-web python-ubuntu-sso-client python-urllib3 python-xdg python-zeitgeist python-zope.interface python3-apport python3-aptdaemon
  python3-aptdaemon.gtk3widgets python3-aptdaemon.pkcompat python3-brlapi python3-cairo python3-chardet python3-crypto python3-debian python3-defer
  python3-gi-cairo python3-httplib2 python3-louis python3-mako python3-markupsafe python3-oauthlib python3-oneconf python3-piston-mini-client
  python3-pkg-resources python3-problem-report python3-pyatspi python3-pycurl python3-six python3-software-properties python3-speechd python3-uno
  python3-xdg python3-xkit qpdf re2c rfkill rhythmbox rhythmbox-data rhythmbox-mozilla rhythmbox-plugin-cdrecorder rhythmbox-plugin-magnatune
  rhythmbox-plugin-zeitgeist rhythmbox-plugins rtkit sa-compile samba-common samba-common-bin samba-libs sane-utils seahorse session-migration
  sessioninstaller shotwell shotwell-common simple-scan smbclient software-center software-center-aptdaemon-plugins software-properties-common
  software-properties-gtk sound-theme-freedesktop spamassassin spamc speech-dispatcher speech-dispatcher-audio-plugins ssh-askpass-gnome ssl-cert
  syslinux syslinux-common syslinux-legacy system-config-printer-common system-config-printer-gnome system-config-printer-udev t1utils tcl tcl8.6
  tcpd telepathy-idle telepathy-mission-control-5 tk tk8.6 toshset totem totem-common totem-plugins tracker tracker-extract tracker-miner-fs
  tracker-utils transmission-common transmission-gtk ttf-indic-fonts-core ttf-punjabi-fonts ttf-ubuntu-font-family ubuntu-drivers-common
  ubuntu-extras-keyring ubuntu-gnome-default-settings ubuntu-release-upgrader-gtk ubuntu-sso-client ubuntu-system-service udisks2
  unattended-upgrades unity-control-center unity-settings-daemon uno-libs3 unoconv unzip update-inetd update-manager update-notifier
  update-notifier-common upower ure usb-creator-common usb-creator-gtk usb-modeswitch usb-modeswitch-data usbmuxd vino wamerican whoopsie
  wireless-tools wodim wpasupplicant x11-apps x11-common x11-session-utils x11-utils x11-xfs-utils x11-xkb-utils x11-xserver-utils xbitmaps
  xdg-user-dirs xdg-user-dirs-gtk xdg-utils xdiagnose xfonts-base xfonts-encodings xfonts-mathml xfonts-scalable xfonts-utils xinit xinput xorg
  xorg-docs-core xserver-common xserver-xephyr xserver-xorg xserver-xorg-core xserver-xorg-input-all xserver-xorg-input-evdev
  xserver-xorg-input-mouse xserver-xorg-input-synaptics xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-all
  xserver-xorg-video-ati xserver-xorg-video-cirrus xserver-xorg-video-fbdev xserver-xorg-video-glamoregl xserver-xorg-video-intel
  xserver-xorg-video-mach64 xserver-xorg-video-mga xserver-xorg-video-modesetting xserver-xorg-video-neomagic xserver-xorg-video-nouveau
  xserver-xorg-video-openchrome xserver-xorg-video-qxl xserver-xorg-video-r128 xserver-xorg-video-radeon xserver-xorg-video-s3
  xserver-xorg-video-savage xserver-xorg-video-siliconmotion xserver-xorg-video-sis xserver-xorg-video-sisusb xserver-xorg-video-tdfx
  xserver-xorg-video-trident xserver-xorg-video-vesa xserver-xorg-video-vmware xsltproc xterm xul-ext-ubufox yelp yelp-tools yelp-xsl zeitgeist
  zeitgeist-core zeitgeist-datahub zenity zenity-common zip zsync
Suggested packages:
  gnome-cards-data apmd alsa-oss oss-compat default-mta mail-transport-agent libgtk2-perl gir1.2-colordgtk-1.0 aspell-doc spellutils binutils-doc
  bluez-hcidump vcdimager libdvdcss2 dvdauthor readom brltty-speechd brltty-x11 console-braille gnome-video-effects-frei0r gnome-video-effects-extra
  cpp-doc gcc-4.8-locales cups-pdf xpp wordlist emacsen-common jed-extra python-paramiko ncftp lftp python-gdata tahoe-lafs python-swiftclient
  cdrskin unrar evolution-ews evolution-plugins-experimental evolution-data-server-dbg arj lha lzip lzop ncompress p7zip-full rpm2cpio rzip
  sharutils unace unalz unar zoo ttf-lyx libgraphite3 pango-graphite hplip-cups printer-driver-all gcc-multilib autoconf automake1.9 libtool flex
  bison gcc-doc gcc-4.8-multilib gcc-4.8-doc libgcc1-dbg libgomp1-dbg libitm1-dbg libatomic1-dbg libasan0-dbg libtsan0-dbg libbacktrace1-dbg
  libquadmath0-dbg binutils-gold gconf-defaults-service gdb-doc gdbserver gedit-plugins cdrkit-doc gettext-doc hpijs gnome-screensaver xscreensaver
  desktop-base metacity x-window-manager gstreamer1.0-libav apache2.2-bin libapache2-mod-dnssd hplip-gui hplip-doc system-config-printer hunspell
  openoffice.org-hunspell openoffice.org-core ibus-clutter ibus-doc ibus-qt4 lrzip libgssapi-perl gstreamer1.0-plugins-ugly cdrdao
  gstreamer1.0-fluendo-mp3 gstreamer1.0-plugins-bad glibc-doc libgles2-mesa libgles2 debian-keyring libdv-bin libenchant-voikko exiv2 libfftw3-bin
  libfftw3-dev libgd-tools geoclue libglide3 gpgsm gphoto2 gtkam gpm grilo-plugins-0.2 gstreamer-codec-install gnome-codec-install
  gstreamer0.10-tools gstreamer0.10-plugins-base gstreamer1.0-tools gutenprint-locales libdata-dump-perl jackd2 libjasper-runtime liblcms2-utils
  lirc libcrypt-ssleay-perl minissdpd natpmp-utils ttf-baekmuk ttf-arphic-gbsn00lp ttf-arphic-bsmi00lp ttf-arphic-gkai00mp ttf-arphic-bkai00mp pcscd
  raptor2-utils rasqal-utils libraw1394-doc librdf-storage-postgresql librdf-storage-mysql librdf-storage-sqlite librdf-storage-virtuoso
  redland-utils libreoffice-base libopencl1 libreoffice-style-crystal libreoffice-style-hicontrast libreoffice-style-oxygen libreoffice-style-sifr
  libreoffice-evolution crystalcursors kde-icons-crystal tango-icon-theme libreoffice-gcj libreoffice-java-common default-jre gcj-jre openjdk-7-jre
  openjdk-6-jre sun-java5-jre sun-java6-jre java5-runtime jre librsvg2-bin hpoj libsane-extras lm-sensors sg3-utils snmp-mibs-downloader
  libspectre1-dbg speex unity-common libauthen-ntlm-perl binutils-multiarch dpkg-dev libtext-template-perl libyaml-perl make-doc hwtools memtester
  kernel-patch-badram memtest86 floppyd pidgin gajim samba network-manager-openconnect-gnome network-manager-openvpn-gnome
  network-manager-vpnc-gnome hpijs-ppds diffutils-doc fonts-japanese-mincho fonts-ipafont-mincho fonts-japanese-gothic fonts-ipafont-gothic
  fonts-arphic-ukai fonts-arphic-uming fonts-unfonts-core psutils hannah-foo2zjs tix gutenprint-doc magicfilter apsfilter pavumeter paman
  pavucontrol paprefs pulseaudio-module-raop pulseaudio-esound-compat python-crypto-dbg python-crypto-doc python-dbus-doc python-dbus-dbg
  python-gdbm-dbg python-gobject-2-dbg python-gtk2-doc python-lxml-dbg python-openssl-doc python-openssl-dbg python-pam-dbg python-pexpect-doc
  python-pil-doc python-pil-dbg python-distribute python-distribute-doc libcurl4-gnutls-dev python-pycurl-dbg python-renderpm-dbg pdf-viewer
  python-egenix-mxtexttools python-reportlab-doc python-wxgtk2.8 python-wxgtk python-twisted-bin-dbg python-tk python-glade2 python-qt3
  python3-launchpadlib python3-crypto-dbg python3-beaker python-mako-doc python3-setuptools python3-pycurl-dbg heimdal-clients unpaper
  account-plugin-facebook account-plugin-google account-plugin-flickr unity-control-center-signon cifs-utils razor libdbi-perl pyzor
  libmail-dkim-perl libttspico-utils speech-dispatcher-doc-cs speech-dispatcher-festival speech-dispatcher-flite openssl-blacklist tcl-tclreadline
  telepathy-haze totem-mozilla gromit tracker-gui ubuntu-sso-client-gui xfsprogs reiserfsprogs exfat-utils btrfs-tools mdadm cryptsetup-bin
  bsd-mailx comgt wvdial vinagre wpagui libengine-pkcs11-openssl mesa-utils nickle cairo-5c xfs xserver fonts-lyx fonts-stix xorg-docs xfonts-100dpi
  xfonts-75dpi gpointing-device-settings touchfreeze firmware-linux xfonts-cyrillic
Recommended packages:
  libc-dbg mcp-account-manager-goa
The following NEW packages will be installed:
  acl acpi-support acpid aisleriot alsa-base alsa-utils anacron apg app-install-data app-install-data-partner apport apport-gtk apport-symptoms
  aptdaemon aptdaemon-data apturl apturl-common argyll aspell aspell-en at-spi2-core avahi-autoipd avahi-daemon avahi-utils baobab bc binutils bluez
  bluez-alsa bluez-cups brasero brasero-cdrkit brasero-common brltty cheese cheese-common colord cpp cpp-4.8 cracklib-runtime cups cups-browsed
  cups-bsd cups-client cups-common cups-core-drivers cups-daemon cups-filters cups-filters-core-drivers cups-pk-helper cups-ppdc cups-server-common
  dbus-x11 dc dconf-cli dconf-editor dconf-gsettings-backend dconf-service deja-dup deja-dup-backend-cloudfiles deja-dup-backend-gvfs
  deja-dup-backend-s3 desktop-file-utils dialog dictionaries-common diffstat dnsmasq-base duplicity dvd+rw-tools enchant eog espeak-data evince
  evince-common evolution evolution-common evolution-data-server evolution-data-server-common evolution-data-server-online-accounts
  evolution-indicator evolution-plugins file-roller firefox folks-common fontconfig fontconfig-config fonts-cantarell fonts-dejavu-core fonts-droid
  fonts-freefont-ttf fonts-kacst fonts-kacst-one fonts-khmeros-core fonts-lao fonts-liberation fonts-lklug-sinhala fonts-nanum fonts-opensymbol
  fonts-sil-abyssinica fonts-sil-padauk fonts-takao-pgothic fonts-thai-tlwg fonts-tibetan-machine fonts-tlwg-garuda fonts-tlwg-kinnari
  fonts-tlwg-loma fonts-tlwg-mono fonts-tlwg-norasi fonts-tlwg-purisa fonts-tlwg-sawasdee fonts-tlwg-typewriter fonts-tlwg-typist fonts-tlwg-typo
  fonts-tlwg-umpush fonts-tlwg-waree foomatic-db-compressed-ppds gcc gcc-4.8 gconf-service gconf-service-backend gconf2 gconf2-common gcr gdb gdisk
  gdm gedit gedit-common genisoimage gettext ghostscript ghostscript-x gir1.2-accountsservice-1.0 gir1.2-atk-1.0 gir1.2-atspi-2.0 gir1.2-caribou-1.0
  gir1.2-clutter-1.0 gir1.2-clutter-gst-2.0 gir1.2-cogl-1.0 gir1.2-coglpango-1.0 gir1.2-dbusmenu-glib-0.4 gir1.2-dee-1.0 gir1.2-evince-3.0
  gir1.2-freedesktop gir1.2-gck-1 gir1.2-gcr-3 gir1.2-gdata-0.0 gir1.2-gdesktopenums-3.0 gir1.2-gdkpixbuf-2.0 gir1.2-gdm-1.0 gir1.2-gkbd-3.0
  gir1.2-gmenu-3.0 gir1.2-gnomebluetooth-1.0 gir1.2-gnomedesktop-3.0 gir1.2-gnomekeyring-1.0 gir1.2-goa-1.0 gir1.2-gst-plugins-base-1.0
  gir1.2-gstreamer-1.0 gir1.2-gtk-3.0 gir1.2-gtkclutter-1.0 gir1.2-gtksource-3.0 gir1.2-gtop-2.0 gir1.2-gudev-1.0 gir1.2-ibus-1.0
  gir1.2-javascriptcoregtk-3.0 gir1.2-json-1.0 gir1.2-mutter-3.0 gir1.2-networkmanager-1.0 gir1.2-nmgtk-1.0 gir1.2-notify-0.7
  gir1.2-packagekitglib-1.0 gir1.2-pango-1.0 gir1.2-peas-1.0 gir1.2-polkit-1.0 gir1.2-rb-3.0 gir1.2-rest-0.7 gir1.2-secret-1 gir1.2-soup-2.4
  gir1.2-telepathyglib-0.12 gir1.2-telepathylogger-0.2 gir1.2-totem-1.0 gir1.2-totem-plparser-1.0 gir1.2-tracker-0.16 gir1.2-udisks-2.0
  gir1.2-unity-5.0 gir1.2-upowerglib-1.0 gir1.2-vte-2.90 gir1.2-webkit-3.0 gir1.2-wnck-3.0 gir1.2-xkl-1.0 gir1.2-zpj-0.0 gjs gkbd-capplet
  glib-networking glib-networking-common glib-networking-services gnome-accessibility-themes gnome-backgrounds gnome-bluetooth gnome-calculator
  gnome-color-manager gnome-contacts gnome-control-center gnome-control-center-data gnome-control-center-shared-data gnome-desktop3-data
  gnome-disk-utility gnome-documents gnome-font-viewer gnome-icon-theme gnome-icon-theme-extras gnome-icon-theme-full gnome-icon-theme-symbolic
  gnome-keyring gnome-mahjongg gnome-menus gnome-mines gnome-online-accounts gnome-online-miners gnome-orca gnome-screenshot gnome-session
  gnome-session-bin gnome-session-canberra gnome-session-common gnome-settings-daemon gnome-settings-daemon-schemas gnome-shell gnome-shell-common
  gnome-shell-extensions gnome-sudoku gnome-sushi gnome-system-log gnome-system-monitor gnome-terminal gnome-terminal-data gnome-themes-standard
  gnome-themes-standard-data gnome-tweak-tool gnome-user-guide gnome-user-share gnome-video-effects growisofs gsettings-desktop-schemas
  gsettings-ubuntu-schemas gsfonts gstreamer0.10-alsa gstreamer0.10-pulseaudio gstreamer1.0-alsa gstreamer1.0-clutter gstreamer1.0-plugins-base
  gstreamer1.0-plugins-good gstreamer1.0-pulseaudio gstreamer1.0-x gtk2-engines-pixbuf gucharmap guile-2.0-libs gvfs gvfs-backends gvfs-backends-goa
  gvfs-bin gvfs-common gvfs-daemons gvfs-fuse gvfs-libs hardening-includes hicolor-icon-theme hplip hplip-data humanity-icon-theme hunspell-en-us
  hwdata ibus ibus-gtk ibus-gtk3 ibus-pinyin ibus-table im-config indicator-application inputattach intel-gpu-tools intltool-debian iproute
  iputils-arping itstool kerneloops-daemon libaa1 libaccounts-glib0 libappindicator3-1 libapt-pkg-perl libarchive-zip-perl libarchive13 libart-2.0-2
  libasan0 libasound2 libasound2-data libasound2-plugins libaspell15 libasprintf-dev libassuan0 libasyncns0 libatasmart4 libatk-adaptor
  libatk-bridge2.0-0 libatk1.0-0 libatk1.0-data libatkmm-1.6-1 libatomic1 libatspi2.0-0 libauthen-sasl-perl libautodie-perl libavahi-client3
  libavahi-common-data libavahi-common3 libavahi-core7 libavahi-glib1 libavc1394-0 libbluetooth3 libboost-date-time1.54.0 libboost-system1.54.0
  libbrasero-media3-1 libbrlapi0.6 libburn4 libc-dev-bin libc6-dbg libc6-dev libcaca0 libcairo-gobject2 libcairo2 libcairomm-1.0-1 libcamel-1.2-45
  libcanberra-gtk-module libcanberra-gtk0 libcanberra-gtk3-0 libcanberra-gtk3-module libcanberra-pulse libcanberra0 libcaribou-common libcaribou0
  libcdio-cdda1 libcdio-paranoia1 libcdio13 libcdparanoia0 libcdr-0.0-0 libcheese-gtk23 libcheese7 libclone-perl libcloog-isl4 libclucene-contribs1
  libclucene-core1 libclutter-1.0-0 libclutter-1.0-common libclutter-gst-2.0-0 libclutter-gtk-1.0-0 libcmis-0.4-4 libcogl-common libcogl-pango15
  libcogl15 libcolamd2.8.0 libcolord-gtk1 libcolord1 libcolorhug1 libcrack2 libcroco3 libcrypt-passwdmd5-perl libcups2 libcupscgi1 libcupsfilters1
  libcupsimage2 libcupsmime1 libcupsppdc1 libcurl3 libdaemon0 libdatrie1 libdbusmenu-glib4 libdbusmenu-gtk3-4 libdbusmenu-gtk4 libdconf1
  libdee-1.0-4 libdigest-hmac-perl libdjvulibre-text libdjvulibre21 libdmapsharing-3.0-2 libdotconf0 libdpkg-perl libdrm-intel1 libdrm-nouveau2
  libdrm-radeon1 libdv4 libebackend-1.2-7 libebook-1.2-14 libebook-contacts-1.2-0 libecal-1.2-16 libedata-book-1.2-20 libedata-cal-1.2-23
  libedataserver-1.2-18 libegl1-mesa libegl1-mesa-drivers libelfg0 libemail-valid-perl libenca0 libenchant1c2a libencode-locale-perl liberror-perl
  libespeak1 libevdocument3-4 libevent-2.0-5 libevolution libevview3-3 libexempi3 libexif12 libexiv2-12 libexttextcat-2.0-0 libexttextcat-data
  libfftw3-single3 libfile-basedir-perl libfile-copy-recursive-perl libfile-desktopentry-perl libfile-fcntllock-perl libfile-listing-perl
  libfile-mimeinfo-perl libflac8 libfolks-eds25 libfolks-telepathy25 libfolks25 libfont-afm-perl libfontconfig1 libfontembed1 libfontenc1 libframe6
  libfs6 libgail-3-0 libgail-common libgail18 libgbm1 libgc1c2 libgcc-4.8-dev libgconf-2-4 libgcr-ui-3-1 libgd3 libgdata-common libgdata13
  libgdk-pixbuf2.0-0 libgdk-pixbuf2.0-common libgdm1 libgee-0.8-2 libgeis1 libgeoclue0 libgettextpo-dev libgettextpo0 libgexiv2-2 libgif4 libgjs0e
  libgl1-mesa-dri libgl1-mesa-glx libglamor0 libglapi-mesa libglib2.0-bin libglibmm-2.4-1c2a libglu1-mesa libgmime-2.6-0 libgmp10
  libgnome-bluetooth11 libgnome-control-center1 libgnome-desktop-3-7 libgnome-keyring-common libgnome-keyring0 libgnome-menu-3-0 libgnomekbd-common
  libgnomekbd8 libgoa-1.0-0b libgoa-1.0-common libgoa-backend-1.0-1 libgomp1 libgpgme11 libgphoto2-6 libgphoto2-l10n libgphoto2-port10 libgpm2
  libgpod-common libgpod4 libgrail6 libgraphite2-3 libgrilo-0.2-1 libgrip0 libgs9 libgs9-common libgsf-1-114 libgsf-1-common libgssdp-1.0-3
  libgstreamer-plugins-base0.10-0 libgstreamer-plugins-base1.0-0 libgstreamer-plugins-good1.0-0 libgstreamer0.10-0 libgstreamer1.0-0 libgtk-3-0
  libgtk-3-bin libgtk-3-common libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libgtkhtml-4.0-0 libgtkhtml-4.0-common libgtkhtml-editor-4.0-0
  libgtkmm-3.0-1 libgtksourceview-3.0-1 libgtksourceview-3.0-common libgtop2-7 libgtop2-common libgucharmap-2-90-7 libgudev-1.0-0 libgupnp-1.0-4
  libgusb2 libgutenprint2 libgweather-3-6 libgweather-common libgxps2 libharfbuzz-icu0 libharfbuzz0b libhpmud0 libhtml-form-perl libhtml-format-perl
  libhtml-parser-perl libhtml-tagset-perl libhtml-tree-perl libhttp-cookies-perl libhttp-daemon-perl libhttp-date-perl libhttp-message-perl
  libhttp-negotiate-perl libhunspell-1.3-0 libhyphen0 libibus-1.0-5 libical1 libicc2 libice6 libicu52 libiec61883-0 libieee1284-3 libijs-0.35
  libimdi0 libimobiledevice4 libindicator3-7 libio-html-perl libio-pty-perl libio-socket-inet6-perl libio-socket-ssl-perl libipc-run-perl
  libipc-system-simple-perl libiptcdata0 libisl10 libisofs6 libitm1 libiw30 libjack-jackd2-0 libjasper1 libjavascriptcoregtk-3.0-0 libjbig0
  libjbig2dec0 libjpeg-turbo8 libjpeg8 libjson-glib-1.0-0 libjson-glib-1.0-common libjte1 libkpathsea6 liblangtag-common liblangtag1 liblcms2-2
  libldb1 liblircclient0 liblist-moreutils-perl libllvm3.4 liblouis-data liblouis2 libltdl7 liblua5.2-0 liblwp-mediatypes-perl
  liblwp-protocol-https-perl liblzo2-2 libmail-spf-perl libmailtools-perl libmbim-glib0 libmessaging-menu0 libmhash2 libminiupnpc8
  libmission-control-plugins0 libmm-glib0 libmnl0 libmozjs-24-0 libmpc3 libmpfr4 libmspub-0.0-0 libmtdev1 libmtp-common libmtp-runtime libmtp9
  libmusicbrainz5-0 libmutter0c libmythes-1.2-0 libnatpmp1 libnautilus-extension1a libneon27-gnutls libnet-dns-perl libnet-domain-tld-perl
  libnet-http-perl libnet-ip-perl libnet-libidn-perl libnet-smtp-ssl-perl libnet-ssleay-perl libnetaddr-ip-perl libnetfilter-conntrack3 libnettle4
  libnl-route-3-200 libnm-glib-vpn1 libnm-glib4 libnm-gtk-common libnm-gtk0 libnm-util2 libnotify-bin libnotify4 libnspr4 libnss-mdns
  libnss-myhostname libnss3 libnss3-nssdb libntdb1 liboauth0 libogg0 libopencc1 libopenobex1 libopenvg1-mesa liborc-0.4-0 liborcus-0.6-0
  libp11-kit-gnome-keyring libpackagekit-glib2-16 libpam-gnome-keyring libpango-1.0-0 libpango1.0-0 libpangocairo-1.0-0 libpangoft2-1.0-0
  libpangomm-1.4-1 libpangox-1.0-0 libpangoxft-1.0-0 libpaper-utils libpaper1 libpciaccess0 libpcsclite1 libpeas-1.0-0 libpeas-common libperl5.18
  libperlio-gzip-perl libpixman-1-0 libplist1 libpolkit-agent-1-0 libpolkit-backend-1-0 libpoppler-glib8 libpoppler44 libportaudio2 libproxy1
  libproxy1-plugin-gsettings libproxy1-plugin-networkmanager libpst4 libpulse-mainloop-glib0 libpulse0 libpulsedsp libpwquality-common libpwquality1
  libpython2.7 libpython3.4 libpyzy-1.0-0 libqmi-glib0 libqpdf13 libquadmath0 libraptor2-0 librasqal3 libraw1394-11 libraw9 librdf0 libreadline5
  libreoffice-avmedia-backend-gstreamer libreoffice-base-core libreoffice-calc libreoffice-common libreoffice-core libreoffice-draw
  libreoffice-gnome libreoffice-gtk libreoffice-impress libreoffice-math libreoffice-ogltrans libreoffice-pdfimport
  libreoffice-presentation-minimizer libreoffice-style-galaxy libreoffice-style-human libreoffice-style-tango libreoffice-writer librest-0.7-0
  librhythmbox-core8 librsvg2-2 librsvg2-common librsync1 libsamplerate0 libsane libsane-common libsane-hpaio libsbc1 libsecret-1-0 libsecret-common
  libsensors4 libsgutils2-2 libshout3 libsignon-glib1 libsm6 libsmbclient libsndfile1 libsnmp-base libsnmp30 libsocket6-perl libsonic0
  libsoup-gnome2.4-1 libsoup2.4-1 libspectre1 libspeechd2 libspeex1 libspeexdsp1 libstartup-notification0 libsub-identify-perl
  libsys-hostname-long-perl libsystemd-journal0 libt1-5 libtag1-vanilla libtag1c2a libtalloc2 libtcl8.6 libtdb1 libtelepathy-glib0
  libtelepathy-logger3 libtevent0 libtext-levenshtein-perl libthai-data libthai0 libtheora0 libtiff5 libtimezonemap1 libtk8.6 libtotem-plparser18
  libtotem0 libtracker-extract-0.16-0 libtracker-miner-0.16-0 libtracker-sparql-0.16-0 libtxc-dxtn-s2tc0 libudisks2-0 libunistring0
  libunity-control-center1 libunity-protocol-private0 libunity-scopes-json-def-desktop libunity9 libupower-glib1 liburi-perl libusbmuxd2
  libutempter0 libv4l-0 libv4lconvert0 libvisio-0.0-0 libvisual-0.4-0 libvisual-0.4-plugins libvorbis0a libvorbisenc2 libvorbisfile3 libvpx1
  libvte-2.90-9 libvte-2.90-common libwacom-common libwacom2 libwavpack1 libwayland-client0 libwayland-cursor0 libwayland-egl1-mesa
  libwayland-server0 libwbclient0 libwebkitgtk-3.0-0 libwebkitgtk-3.0-common libwebp5 libwebpmux1 libwhoopsie0 libwmf0.2-7 libwmf0.2-7-gtk
  libwnck-3-0 libwnck-3-common libwpd-0.9-9 libwpg-0.2-2 libwps-0.2-2 libwrap0 libwww-perl libwww-robotrules-perl libx11-xcb1 libxatracker2 libxaw7
  libxcb-dri2-0 libxcb-dri3-0 libxcb-glx0 libxcb-icccm4 libxcb-image0 libxcb-keysyms1 libxcb-present0 libxcb-render0 libxcb-shape0 libxcb-shm0
  libxcb-sync1 libxcb-util0 libxcb-xf86dri0 libxcb-xfixes0 libxcb-xv0 libxcomposite1 libxcursor1 libxdamage1 libxfixes3 libxfont1 libxft2 libxi6
  libxinerama1 libxkbcommon0 libxkbfile1 libxklavier16 libxml2-utils libxmu6 libxp6 libxpm4 libxrandr2 libxrender1 libxres1 libxshmfence1 libxslt1.1
  libxss1 libxt6 libxtst6 libxv1 libxvmc1 libxxf86dga1 libxxf86vm1 libyajl2 libyelp0 libytnef0 libzapojit-0.0-0 libzeitgeist-1.0-1
  libzeitgeist-2.0-0 lintian linux-libc-dev linux-sound-base lp-solve make manpages-dev media-player-info memtest86+ mobile-broadband-provider-info
  modemmanager mousetweaks mscompress mtools mutter mutter-common nautilus nautilus-data nautilus-sendto nautilus-share network-manager
  network-manager-gnome network-manager-pptp network-manager-pptp-gnome notification-daemon obex-data-server obexd-client oneconf oneconf-common
  openprinting-ppds p11-kit p11-kit-modules patch patchutils pcmciautils plymouth-label plymouth-theme-ubuntu-gnome-logo
  plymouth-theme-ubuntu-gnome-text policykit-1 policykit-1-gnome policykit-desktop-privileges poppler-data poppler-utils pptp-linux
  printer-driver-c2esp printer-driver-foo2zjs printer-driver-foo2zjs-common printer-driver-gutenprint printer-driver-hpcups printer-driver-min12xxw
  printer-driver-pnm2ppa printer-driver-postscript-hp printer-driver-ptouch printer-driver-pxljr printer-driver-sag-gdi printer-driver-splix
  pulseaudio pulseaudio-module-bluetooth pulseaudio-module-x11 pulseaudio-utils python-aptdaemon python-aptdaemon.gtk3widgets python-boto
  python-cairo python-cloudfiles python-commandnotfound python-crypto python-cups python-cupshelpers python-dbus python-dbus-dev python-debtagshw
  python-defer python-dirspec python-gdbm python-gi python-gi-cairo python-gnomekeyring python-gobject python-gobject-2 python-gtk2 python-httplib2
  python-ibus python-imaging python-ldb python-libxml2 python-lockfile python-lxml python-notify python-ntdb python-oauthlib python-oneconf
  python-openssl python-pam python-pexpect python-pil python-piston-mini-client python-pkg-resources python-pycurl python-renderpm python-reportlab
  python-reportlab-accel python-requests python-samba python-serial python-smbc python-talloc python-tdb python-twisted-bin python-twisted-core
  python-twisted-web python-ubuntu-sso-client python-urllib3 python-xdg python-zeitgeist python-zope.interface python3-apport python3-aptdaemon
  python3-aptdaemon.gtk3widgets python3-aptdaemon.pkcompat python3-brlapi python3-cairo python3-chardet python3-crypto python3-debian python3-defer
  python3-gi-cairo python3-httplib2 python3-louis python3-mako python3-markupsafe python3-oauthlib python3-oneconf python3-piston-mini-client
  python3-pkg-resources python3-problem-report python3-pyatspi python3-pycurl python3-six python3-software-properties python3-speechd python3-uno
  python3-xdg python3-xkit qpdf re2c rfkill rhythmbox rhythmbox-data rhythmbox-mozilla rhythmbox-plugin-cdrecorder rhythmbox-plugin-magnatune
  rhythmbox-plugin-zeitgeist rhythmbox-plugins rtkit sa-compile samba-common samba-common-bin samba-libs sane-utils seahorse session-migration
  sessioninstaller shotwell shotwell-common simple-scan smbclient software-center software-center-aptdaemon-plugins software-properties-common
  software-properties-gtk sound-theme-freedesktop spamassassin spamc speech-dispatcher speech-dispatcher-audio-plugins ssh-askpass-gnome ssl-cert
  syslinux syslinux-common syslinux-legacy system-config-printer-common system-config-printer-gnome system-config-printer-udev t1utils tcl tcl8.6
  tcpd telepathy-idle telepathy-mission-control-5 tk tk8.6 toshset totem totem-common totem-plugins tracker tracker-extract tracker-miner-fs
  tracker-utils transmission-common transmission-gtk ttf-indic-fonts-core ttf-punjabi-fonts ttf-ubuntu-font-family ubuntu-drivers-common
  ubuntu-extras-keyring ubuntu-gnome-default-settings ubuntu-gnome-desktop ubuntu-release-upgrader-gtk ubuntu-sso-client ubuntu-system-service
  udisks2 unattended-upgrades unity-control-center unity-settings-daemon uno-libs3 unoconv unzip update-inetd update-manager update-notifier
  update-notifier-common upower ure usb-creator-common usb-creator-gtk usb-modeswitch usb-modeswitch-data usbmuxd vino wamerican whoopsie
  wireless-tools wodim wpasupplicant x11-apps x11-common x11-session-utils x11-utils x11-xfs-utils x11-xkb-utils x11-xserver-utils xbitmaps
  xdg-user-dirs xdg-user-dirs-gtk xdg-utils xdiagnose xfonts-base xfonts-encodings xfonts-mathml xfonts-scalable xfonts-utils xinit xinput xorg
  xorg-docs-core xserver-common xserver-xephyr xserver-xorg xserver-xorg-core xserver-xorg-input-all xserver-xorg-input-evdev
  xserver-xorg-input-mouse xserver-xorg-input-synaptics xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-all
  xserver-xorg-video-ati xserver-xorg-video-cirrus xserver-xorg-video-fbdev xserver-xorg-video-glamoregl xserver-xorg-video-intel
  xserver-xorg-video-mach64 xserver-xorg-video-mga xserver-xorg-video-modesetting xserver-xorg-video-neomagic xserver-xorg-video-nouveau
  xserver-xorg-video-openchrome xserver-xorg-video-qxl xserver-xorg-video-r128 xserver-xorg-video-radeon xserver-xorg-video-s3
  xserver-xorg-video-savage xserver-xorg-video-siliconmotion xserver-xorg-video-sis xserver-xorg-video-sisusb xserver-xorg-video-tdfx
  xserver-xorg-video-trident xserver-xorg-video-vesa xserver-xorg-video-vmware xsltproc xterm xul-ext-ubufox yelp yelp-tools yelp-xsl zeitgeist
  zeitgeist-core zeitgeist-datahub zenity zenity-common zip zsync
The following packages will be upgraded:
  libglib2.0-0 libplymouth2 plymouth
3 upgraded, **[COLOR="#FF0000"]1149 newly installed[/COLOR]**, 0 to remove and 10 not upgraded.
Need to get 418 MB of archives.
After this operation, 1,580 MB of additional disk space will be used.
Do you want to continue? [Y/n] n
Abort.

```

---

### Post by kansasnoob on 2014-04-04
Trying something new:

```
root@lance-desktop:/# add-apt-repository ppa:darkxst/ppa
The program 'add-apt-repository' is currently not installed. You can install it by typing:
apt-get install software-properties-common

```

Probably not a big deal but I want to record ALL results :)

---

### Post by kansasnoob on 2014-04-04
OK added 'software-properties-common':

```
root@lance-desktop:/# apt-get install software-properties-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  python3-pycurl python3-software-properties unattended-upgrades
Suggested packages:
  libcurl4-gnutls-dev python3-pycurl-dbg bsd-mailx mail-transport-agent
The following NEW packages will be installed:
  python3-pycurl python3-software-properties software-properties-common unattended-upgrades
0 upgraded, 4 newly installed, 0 to remove and 13 not upgraded.
Need to get 101 kB of archives.
After this operation, 793 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://us.archive.ubuntu.com/ubuntu/ trusty/main python3-pycurl i386 7.19.3-0ubuntu3 [46.3 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ trusty/main unattended-upgrades all 0.82.1ubuntu1 [25.7 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ trusty/main python3-software-properties all 0.92.34 [19.5 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ trusty/main software-properties-common all 0.92.34 [9,284 B]
Fetched 101 kB in 0s (130 kB/s)                       
Preconfiguring packages ...
Selecting previously unselected package python3-pycurl.
(Reading database ... 49492 files and directories currently installed.)
Preparing to unpack .../python3-pycurl_7.19.3-0ubuntu3_i386.deb ...
Unpacking python3-pycurl (7.19.3-0ubuntu3) ...
Selecting previously unselected package unattended-upgrades.
Preparing to unpack .../unattended-upgrades_0.82.1ubuntu1_all.deb ...
Unpacking unattended-upgrades (0.82.1ubuntu1) ...
Selecting previously unselected package python3-software-properties.
Preparing to unpack .../python3-software-properties_0.92.34_all.deb ...
Unpacking python3-software-properties (0.92.34) ...
Selecting previously unselected package software-properties-common.
Preparing to unpack .../software-properties-common_0.92.34_all.deb ...
Unpacking software-properties-common (0.92.34) ...
Processing triggers for man-db (2.6.6-1) ...
Processing triggers for ureadahead (0.100.0-16) ...
Setting up python3-pycurl (7.19.3-0ubuntu3) ...
Setting up unattended-upgrades (0.82.1ubuntu1) ...
Processing triggers for ureadahead (0.100.0-16) ...
Setting up python3-software-properties (0.92.34) ...
Setting up software-properties-common (0.92.34) ...

```

And then:

```
root@lance-desktop:/# add-apt-repository ppa:darkxst/ppa
 
 More info: https://launchpad.net/~darkxst/+archive/ppa
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmphic0dxgu/secring.gpg' created
gpg: keyring `/tmp/tmphic0dxgu/pubring.gpg' created
gpg: requesting key 31945C87 from hkp server keyserver.ubuntu.com
gpg: /tmp/tmphic0dxgu/trustdb.gpg: trustdb created
gpg: key 31945C87: public key "Launchpad PPA for Tim" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK

```

Stay tuned :)

---

### Post by kansasnoob on 2014-04-04
So far so good:

```
root@lance-desktop:/# apt-get update
Ign http://us.archive.ubuntu.com trusty InRelease
Ign http://security.ubuntu.com trusty-security InRelease
Ign http://us.archive.ubuntu.com trusty-updates InRelease
Ign http://ppa.launchpad.net trusty InRelease  
Hit http://security.ubuntu.com trusty-security Release.gpg
Ign http://us.archive.ubuntu.com trusty-backports InRelease
Hit http://security.ubuntu.com trusty-security Release
Get:1 http://us.archive.ubuntu.com trusty Release.gpg [933 B]
Get:2 http://ppa.launchpad.net trusty Release.gpg [316 B]
Hit http://us.archive.ubuntu.com trusty-updates Release.gpg            
Hit http://us.archive.ubuntu.com trusty-backports Release.gpg          
Get:3 http://ppa.launchpad.net trusty Release [14.0 kB]
Hit http://security.ubuntu.com trusty-security/main Sources                   
Get:4 http://us.archive.ubuntu.com trusty Release [58.5 kB]
Hit http://security.ubuntu.com trusty-security/restricted Sources             
Get:5 http://ppa.launchpad.net trusty/main i386 Packages [5,937 B]            
Hit http://security.ubuntu.com trusty-security/universe Sources                           
Hit http://security.ubuntu.com trusty-security/multiverse Sources                                     
Hit http://us.archive.ubuntu.com trusty-updates Release               
Hit http://security.ubuntu.com trusty-security/main i386 Packages                            
Hit http://us.archive.ubuntu.com trusty-backports Release                                    
Hit http://security.ubuntu.com trusty-security/restricted i386 Packages                      
Get:6 http://us.archive.ubuntu.com trusty/main Sources [1,077 kB]                            
Hit http://security.ubuntu.com trusty-security/universe i386 Packages         
Hit http://security.ubuntu.com trusty-security/multiverse i386 Packages       
Hit http://security.ubuntu.com trusty-security/main Translation-en
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en       
Hit http://security.ubuntu.com trusty-security/restricted Translation-en       
Get:7 http://us.archive.ubuntu.com trusty/restricted Sources [5,386 B]                      
Hit http://security.ubuntu.com trusty-security/universe Translation-en                           
Ign http://ppa.launchpad.net trusty/main Translation-en_US                                  
Get:8 http://us.archive.ubuntu.com trusty/universe Sources [6,405 kB]                       
Ign http://ppa.launchpad.net trusty/main Translation-en                                          
Ign http://security.ubuntu.com trusty-security/main Translation-en_US                            
Ign http://security.ubuntu.com trusty-security/multiverse Translation-en_US      
Ign http://security.ubuntu.com trusty-security/restricted Translation-en_US
Ign http://security.ubuntu.com trusty-security/universe Translation-en_US
Get:9 http://us.archive.ubuntu.com trusty/multiverse Sources [175 kB]                                                                                
Get:10 http://us.archive.ubuntu.com trusty/main i386 Packages [1,366 kB]                                                                             
Get:11 http://us.archive.ubuntu.com trusty/restricted i386 Packages [13.4 kB]                                                                        
Get:12 http://us.archive.ubuntu.com trusty/universe i386 Packages [5,876 kB]                                                                         
Get:13 http://us.archive.ubuntu.com trusty/multiverse i386 Packages [134 kB]                                                                         
Hit http://us.archive.ubuntu.com trusty/main Translation-en                                                                                          
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en                                                                                    
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en                                                                                    
Get:14 http://us.archive.ubuntu.com trusty/universe Translation-en [4,047 kB]                                                                        
Hit http://us.archive.ubuntu.com trusty-updates/main Sources                                                                                         
Hit http://us.archive.ubuntu.com trusty-updates/restricted Sources                                                                                   
Hit http://us.archive.ubuntu.com trusty-updates/universe Sources                                                                                     
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Sources                                                                                   
Hit http://us.archive.ubuntu.com trusty-updates/main i386 Packages                                                                                   
Hit http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages                                                                             
Hit http://us.archive.ubuntu.com trusty-updates/universe i386 Packages                                                                               
Hit http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages                                                                             
Hit http://us.archive.ubuntu.com trusty-updates/main Translation-en                                                                                  
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en                                                                            
Hit http://us.archive.ubuntu.com trusty-updates/restricted Translation-en                                                                            
Hit http://us.archive.ubuntu.com trusty-updates/universe Translation-en                                                                              
Hit http://us.archive.ubuntu.com trusty-backports/main Sources                                                                                       
Hit http://us.archive.ubuntu.com trusty-backports/restricted Sources                                                                                 
Hit http://us.archive.ubuntu.com trusty-backports/universe Sources                                                                                   
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Sources                                                                                 
Hit http://us.archive.ubuntu.com trusty-backports/main i386 Packages                                                                                 
Hit http://us.archive.ubuntu.com trusty-backports/restricted i386 Packages                                                                           
Hit http://us.archive.ubuntu.com trusty-backports/universe i386 Packages                                                                             
Hit http://us.archive.ubuntu.com trusty-backports/multiverse i386 Packages                                                                           
Hit http://us.archive.ubuntu.com trusty-backports/main Translation-en                                                                                
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Translation-en                                                                          
Hit http://us.archive.ubuntu.com trusty-backports/restricted Translation-en                                                                          
Hit http://us.archive.ubuntu.com trusty-backports/universe Translation-en                                                                            
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US                                                                                       
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US                                                                                 
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US                                                                                 
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US                                                                                   
Ign http://us.archive.ubuntu.com trusty-updates/main Translation-en_US                                                                               
Ign http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en_US                                                                         
Ign http://us.archive.ubuntu.com trusty-updates/restricted Translation-en_US                                                                         
Ign http://us.archive.ubuntu.com trusty-updates/universe Translation-en_US                                                                           
Ign http://us.archive.ubuntu.com trusty-backports/main Translation-en_US                                                                             
Ign http://us.archive.ubuntu.com trusty-backports/multiverse Translation-en_US                                                                       
Ign http://us.archive.ubuntu.com trusty-backports/restricted Translation-en_US                                                                       
Ign http://us.archive.ubuntu.com trusty-backports/universe Translation-en_US                                                                         
Fetched 19.2 MB in 40s (474 kB/s)                                                                                                                    
Reading package lists... Done

```

```
root@lance-desktop:/# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 16 not upgraded.

```

BTW I did NOT upgrade.

---

### Post by kansasnoob on 2014-04-04
Tim will need to parse this:

```
root@lance-desktop:/# apt-get install ubuntu-gnome-desktop mcp-account-manager-uoa-
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'mcp-account-manager-uoa' is not installed, so not removed
The following extra packages will be installed:
  acl acpi-support acpid aisleriot alsa-base alsa-utils anacron apg app-install-data app-install-data-partner apport apport-gtk apport-symptoms
  aptdaemon aptdaemon-data apturl apturl-common argyll aspell aspell-en at-spi2-core avahi-autoipd avahi-daemon avahi-utils baobab bc binutils bluez
  bluez-alsa bluez-cups brasero brasero-cdrkit brasero-common brltty cheese cheese-common colord cpp cpp-4.8 cracklib-runtime cups cups-browsed
  cups-bsd cups-client cups-common cups-core-drivers cups-daemon cups-filters cups-filters-core-drivers cups-pk-helper cups-ppdc cups-server-common
  dbus-x11 dc dconf-cli dconf-editor dconf-gsettings-backend dconf-service deja-dup deja-dup-backend-cloudfiles deja-dup-backend-gvfs
  deja-dup-backend-s3 desktop-file-utils dialog dictionaries-common diffstat dnsmasq-base duplicity dvd+rw-tools empathy empathy-common enchant eog
  espeak-data evince evince-common evolution evolution-common evolution-data-server evolution-data-server-common
  evolution-data-server-online-accounts evolution-indicator evolution-plugins file-roller firefox folks-common fontconfig fontconfig-config
  fonts-cantarell fonts-dejavu-core fonts-droid fonts-freefont-ttf fonts-kacst fonts-kacst-one fonts-khmeros-core fonts-lao fonts-liberation
  fonts-lklug-sinhala fonts-nanum fonts-opensymbol fonts-sil-abyssinica fonts-sil-padauk fonts-takao-pgothic fonts-thai-tlwg fonts-tibetan-machine
  fonts-tlwg-garuda fonts-tlwg-kinnari fonts-tlwg-loma fonts-tlwg-mono fonts-tlwg-norasi fonts-tlwg-purisa fonts-tlwg-sawasdee fonts-tlwg-typewriter
  fonts-tlwg-typist fonts-tlwg-typo fonts-tlwg-umpush fonts-tlwg-waree foomatic-db-compressed-ppds gcc gcc-4.8 gconf-service gconf-service-backend
  gconf2 gconf2-common gcr gdb gdisk gdm gedit gedit-common genisoimage geoclue gettext ghostscript ghostscript-x gir1.2-accountsservice-1.0
  gir1.2-atk-1.0 gir1.2-atspi-2.0 gir1.2-caribou-1.0 gir1.2-clutter-1.0 gir1.2-clutter-gst-2.0 gir1.2-cogl-1.0 gir1.2-coglpango-1.0
  gir1.2-dbusmenu-glib-0.4 gir1.2-dee-1.0 gir1.2-evince-3.0 gir1.2-freedesktop gir1.2-gck-1 gir1.2-gcr-3 gir1.2-gdata-0.0 gir1.2-gdesktopenums-3.0
  gir1.2-gdkpixbuf-2.0 gir1.2-gdm-1.0 gir1.2-gkbd-3.0 gir1.2-gmenu-3.0 gir1.2-gnomebluetooth-1.0 gir1.2-gnomedesktop-3.0 gir1.2-gnomekeyring-1.0
  gir1.2-goa-1.0 gir1.2-gst-plugins-base-1.0 gir1.2-gstreamer-1.0 gir1.2-gtk-3.0 gir1.2-gtkclutter-1.0 gir1.2-gtksource-3.0 gir1.2-gtop-2.0
  gir1.2-gudev-1.0 gir1.2-ibus-1.0 gir1.2-javascriptcoregtk-3.0 gir1.2-json-1.0 gir1.2-mutter-3.0 gir1.2-networkmanager-1.0 gir1.2-nmgtk-1.0
  gir1.2-notify-0.7 gir1.2-packagekitglib-1.0 gir1.2-pango-1.0 gir1.2-peas-1.0 gir1.2-polkit-1.0 gir1.2-rb-3.0 gir1.2-rest-0.7 gir1.2-secret-1
  gir1.2-soup-2.4 gir1.2-telepathyglib-0.12 gir1.2-telepathylogger-0.2 gir1.2-totem-1.0 gir1.2-totem-plparser-1.0 gir1.2-tracker-0.16
  gir1.2-udisks-2.0 gir1.2-unity-5.0 gir1.2-upowerglib-1.0 gir1.2-vte-2.90 gir1.2-webkit-3.0 gir1.2-wnck-3.0 gir1.2-xkl-1.0 gir1.2-zpj-0.0 gjs
  gkbd-capplet glib-networking glib-networking-common glib-networking-services gnome-accessibility-themes gnome-backgrounds gnome-bluetooth
  gnome-calculator gnome-color-manager gnome-contacts gnome-control-center gnome-control-center-data gnome-control-center-shared-data
  gnome-desktop3-data gnome-disk-utility gnome-documents gnome-font-viewer gnome-icon-theme gnome-icon-theme-extras gnome-icon-theme-full
  gnome-icon-theme-symbolic gnome-keyring gnome-mahjongg gnome-menus gnome-mines gnome-online-accounts gnome-online-miners gnome-orca
  gnome-screenshot gnome-session gnome-session-bin gnome-session-canberra gnome-session-common gnome-settings-daemon gnome-settings-daemon-schemas
  gnome-shell gnome-shell-common gnome-shell-extensions gnome-sudoku gnome-sushi gnome-system-log gnome-system-monitor gnome-terminal
  gnome-terminal-data gnome-themes-standard gnome-themes-standard-data gnome-tweak-tool gnome-user-guide gnome-user-share gnome-video-effects
  growisofs gsettings-desktop-schemas gsfonts gstreamer0.10-alsa gstreamer0.10-nice gstreamer0.10-plugins-base gstreamer0.10-plugins-good
  gstreamer0.10-pulseaudio gstreamer0.10-x gstreamer1.0-alsa gstreamer1.0-clutter gstreamer1.0-nice gstreamer1.0-plugins-base
  gstreamer1.0-plugins-good gstreamer1.0-pulseaudio gstreamer1.0-x gtk2-engines-pixbuf gucharmap guile-2.0-libs gvfs gvfs-backends gvfs-backends-goa
  gvfs-bin gvfs-common gvfs-daemons gvfs-fuse gvfs-libs hardening-includes hicolor-icon-theme hplip hplip-data humanity-icon-theme hunspell-en-us
  hwdata ibus ibus-gtk ibus-gtk3 ibus-pinyin ibus-table im-config indicator-application inputattach intel-gpu-tools intltool-debian iproute
  iputils-arping itstool kerneloops-daemon libaa1 libaccounts-glib0 libappindicator3-1 libapt-pkg-perl libarchive-zip-perl libarchive13 libart-2.0-2
  libasan0 libasound2 libasound2-data libasound2-plugins libaspell15 libasprintf-dev libassuan0 libasyncns0 libatasmart4 libatk-adaptor
  libatk-bridge2.0-0 libatk1.0-0 libatk1.0-data libatkmm-1.6-1 libatomic1 libatspi2.0-0 libauthen-sasl-perl libautodie-perl libavahi-client3
  libavahi-common-data libavahi-common3 libavahi-core7 libavahi-glib1 libavahi-gobject0 libavc1394-0 libbluetooth3 libboost-date-time1.54.0
  libboost-system1.54.0 libbrasero-media3-1 libbrlapi0.6 libburn4 libc-dev-bin libc6-dbg libc6-dev libcaca0 libcairo-gobject2 libcairo2
  libcairomm-1.0-1 libcamel-1.2-45 libcanberra-gtk-module libcanberra-gtk0 libcanberra-gtk3-0 libcanberra-gtk3-module libcanberra-pulse libcanberra0
  libcaribou-common libcaribou0 libcdio-cdda1 libcdio-paranoia1 libcdio13 libcdparanoia0 libcdr-0.0-0 libcheese-gtk23 libcheese7 libclone-perl
  libcloog-isl4 libclucene-contribs1 libclucene-core1 libclutter-1.0-0 libclutter-1.0-common libclutter-gst-2.0-0 libclutter-gtk-1.0-0 libcmis-0.4-4
  libcogl-common libcogl-pango15 libcogl15 libcolamd2.8.0 libcolord-gtk1 libcolord1 libcolorhug1 libcrack2 libcroco3 libcrypt-passwdmd5-perl
  libcups2 libcupscgi1 libcupsfilters1 libcupsimage2 libcupsmime1 libcupsppdc1 libcurl3 libdaemon0 libdatrie1 libdbusmenu-glib4 libdbusmenu-gtk3-4
  libdbusmenu-gtk4 libdconf1 libdee-1.0-4 libdigest-hmac-perl libdjvulibre-text libdjvulibre21 libdmapsharing-3.0-2 libdotconf0 libdpkg-perl
  libdrm-intel1 libdrm-nouveau2 libdrm-radeon1 libdv4 libebackend-1.2-7 libebook-1.2-14 libebook-contacts-1.2-0 libecal-1.2-16 libedata-book-1.2-20
  libedata-cal-1.2-23 libedataserver-1.2-18 libegl1-mesa libegl1-mesa-drivers libelfg0 libemail-valid-perl libenca0 libenchant1c2a
  libencode-locale-perl liberror-perl libespeak1 libevdocument3-4 libevent-2.0-5 libevolution libevview3-3 libexempi3 libexif12 libexiv2-12
  libexttextcat-2.0-0 libexttextcat-data libfarstream-0.1-0 libfarstream-0.2-2 libfftw3-single3 libfile-basedir-perl libfile-copy-recursive-perl
  libfile-desktopentry-perl libfile-fcntllock-perl libfile-listing-perl libfile-mimeinfo-perl libflac8 libfolks-eds25 libfolks-telepathy25
  libfolks25 libfont-afm-perl libfontconfig1 libfontembed1 libfontenc1 libframe6 libfs6 libgail-3-0 libgail-common libgail18 libgbm1 libgc1c2
  libgcc-4.8-dev libgconf-2-4 libgcr-ui-3-1 libgd3 libgdata-common libgdata13 libgdk-pixbuf2.0-0 libgdk-pixbuf2.0-common libgdm1 libgee-0.8-2
  libgeis1 libgeoclue0 libgettextpo-dev libgettextpo0 libgexiv2-2 libgif4 libgjs0e libgl1-mesa-dri libgl1-mesa-glx libglamor0 libglapi-mesa
  libglib2.0-0 libglib2.0-bin libglibmm-2.4-1c2a libglu1-mesa libgmime-2.6-0 libgmp10 libgnome-bluetooth11 libgnome-control-center1
  libgnome-desktop-3-7 libgnome-keyring-common libgnome-keyring0 libgnome-menu-3-0 libgnomekbd-common libgnomekbd8 libgoa-1.0-0b libgoa-1.0-common
  libgoa-backend-1.0-1 libgomp1 libgpgme11 libgphoto2-6 libgphoto2-l10n libgphoto2-port10 libgpm2 libgpod-common libgpod4 libgrail6 libgraphite2-3
  libgrilo-0.2-1 libgrip0 libgs9 libgs9-common libgsf-1-114 libgsf-1-common libgssdp-1.0-3 libgstreamer-plugins-base0.10-0
  libgstreamer-plugins-base1.0-0 libgstreamer-plugins-good1.0-0 libgstreamer0.10-0 libgstreamer1.0-0 libgtk-3-0 libgtk-3-bin libgtk-3-common
  libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libgtkhtml-4.0-0 libgtkhtml-4.0-common libgtkhtml-editor-4.0-0 libgtkmm-3.0-1 libgtksourceview-3.0-1
  libgtksourceview-3.0-common libgtop2-7 libgtop2-common libgucharmap-2-90-7 libgudev-1.0-0 libgupnp-1.0-4 libgupnp-igd-1.0-4 libgusb2
  libgutenprint2 libgweather-3-6 libgweather-common libgxps2 libharfbuzz-icu0 libharfbuzz0b libhpmud0 libhtml-form-perl libhtml-format-perl
  libhtml-parser-perl libhtml-tagset-perl libhtml-tree-perl libhttp-cookies-perl libhttp-daemon-perl libhttp-date-perl libhttp-message-perl
  libhttp-negotiate-perl libhunspell-1.3-0 libhyphen0 libibus-1.0-5 libical1 libicc2 libice6 libicu52 libido3-0.1-0 libiec61883-0 libieee1284-3
  libijs-0.35 libimdi0 libimobiledevice4 libindicator3-7 libio-html-perl libio-pty-perl libio-socket-inet6-perl libio-socket-ssl-perl
  libipc-run-perl libipc-system-simple-perl libiptcdata0 libisl10 libisofs6 libitm1 libiw30 libjack-jackd2-0 libjasper1 libjavascriptcoregtk-3.0-0
  libjbig0 libjbig2dec0 libjpeg-turbo8 libjpeg8 libjson-glib-1.0-0 libjson-glib-1.0-common libjte1 libkpathsea6 liblangtag-common liblangtag1
  liblcms2-2 libldb1 liblircclient0 liblist-moreutils-perl libllvm3.4 liblouis-data liblouis2 libltdl7 liblua5.2-0 liblwp-mediatypes-perl
  liblwp-protocol-https-perl liblzo2-2 libmail-spf-perl libmailtools-perl libmbim-glib0 libmeanwhile1 libmessaging-menu0 libmhash2 libminiupnpc8
  libmission-control-plugins0 libmm-glib0 libmnl0 libmozjs-24-0 libmpc3 libmpfr4 libmspub-0.0-0 libmtdev1 libmtp-common libmtp-runtime libmtp9
  libmusicbrainz5-0 libmutter0c libmythes-1.2-0 libnatpmp1 libnautilus-extension1a libneon27-gnutls libnet-dns-perl libnet-domain-tld-perl
  libnet-http-perl libnet-ip-perl libnet-libidn-perl libnet-smtp-ssl-perl libnet-ssleay-perl libnetaddr-ip-perl libnetfilter-conntrack3 libnettle4
  libnice10 libnl-route-3-200 libnm-glib-vpn1 libnm-glib4 libnm-gtk-common libnm-gtk0 libnm-util2 libnotify-bin libnotify4 libnspr4 libnss-mdns
  libnss-myhostname libnss3 libnss3-nssdb libntdb1 liboauth0 libogg0 libopencc1 libopenobex1 libopenvg1-mesa liborc-0.4-0 liborcus-0.6-0
  libp11-kit-gnome-keyring libpackagekit-glib2-16 libpam-gnome-keyring libpango-1.0-0 libpango1.0-0 libpangocairo-1.0-0 libpangoft2-1.0-0
  libpangomm-1.4-1 libpangox-1.0-0 libpangoxft-1.0-0 libpaper-utils libpaper1 libpciaccess0 libpcsclite1 libpeas-1.0-0 libpeas-common libperl5.18
  libperlio-gzip-perl libpixman-1-0 libplist1 libplymouth2 libpolkit-agent-1-0 libpolkit-backend-1-0 libpoppler-glib8 libpoppler44 libportaudio2
  libproxy1 libproxy1-plugin-gsettings libproxy1-plugin-networkmanager libpst4 libpulse-mainloop-glib0 libpulse0 libpulsedsp libpurple-bin
  libpurple0 libpwquality-common libpwquality1 libpython2.7 libpython3.4 libpyzy-1.0-0 libqmi-glib0 libqpdf13 libquadmath0 libraptor2-0 librasqal3
  libraw1394-11 libraw9 librdf0 libreadline5 libreoffice-avmedia-backend-gstreamer libreoffice-base-core libreoffice-calc libreoffice-common
  libreoffice-core libreoffice-draw libreoffice-gnome libreoffice-gtk libreoffice-impress libreoffice-math libreoffice-ogltrans
  libreoffice-pdfimport libreoffice-presentation-minimizer libreoffice-style-galaxy libreoffice-style-human libreoffice-style-tango
  libreoffice-writer librest-0.7-0 librhythmbox-core8 librsvg2-2 librsvg2-common librsync1 libsamplerate0 libsane libsane-common libsane-hpaio
  libsbc1 libsecret-1-0 libsecret-common libsensors4 libsgutils2-2 libshout3 libsignon-glib1 libsm6 libsmbclient libsndfile1 libsnmp-base libsnmp30
  libsocket6-perl libsonic0 libsoup-gnome2.4-1 libsoup2.4-1 libspectre1 libspeechd2 libspeex1 libspeexdsp1 libstartup-notification0
  libsub-identify-perl libsys-hostname-long-perl libsystemd-journal0 libt1-5 libtag1-vanilla libtag1c2a libtalloc2 libtcl8.6 libtdb1
  libtelepathy-farstream3 libtelepathy-glib0 libtelepathy-logger3 libtevent0 libtext-levenshtein-perl libthai-data libthai0 libtheora0 libtiff5
  libtk8.6 libtotem-plparser18 libtotem0 libtracker-extract-0.16-0 libtracker-miner-0.16-0 libtracker-sparql-0.16-0 libtxc-dxtn-s2tc0 libudisks2-0
  libunistring0 libunity-control-center1 libunity-protocol-private0 libunity-scopes-json-def-desktop libunity9 libupower-glib1 liburi-perl
  libusbmuxd2 libutempter0 libv4l-0 libv4lconvert0 libvisio-0.0-0 libvisual-0.4-0 libvisual-0.4-plugins libvorbis0a libvorbisenc2 libvorbisfile3
  libvpx1 libvte-2.90-9 libvte-2.90-common libwacom-common libwacom2 libwavpack1 libwayland-client0 libwayland-cursor0 libwayland-egl1-mesa
  libwayland-server0 libwbclient0 libwebkitgtk-3.0-0 libwebkitgtk-3.0-common libwebp5 libwebpmux1 libwhoopsie0 libwmf0.2-7 libwmf0.2-7-gtk
  libwnck-3-0 libwnck-3-common libwpd-0.9-9 libwpg-0.2-2 libwps-0.2-2 libwrap0 libwww-perl libwww-robotrules-perl libx11-xcb1 libxatracker2 libxaw7
  libxcb-dri2-0 libxcb-dri3-0 libxcb-glx0 libxcb-icccm4 libxcb-image0 libxcb-keysyms1 libxcb-present0 libxcb-render0 libxcb-shape0 libxcb-shm0
  libxcb-sync1 libxcb-util0 libxcb-xf86dri0 libxcb-xfixes0 libxcb-xv0 libxcomposite1 libxcursor1 libxdamage1 libxfixes3 libxfont1 libxft2 libxi6
  libxinerama1 libxkbcommon0 libxkbfile1 libxklavier16 libxml2-utils libxmu6 libxp6 libxpm4 libxrandr2 libxrender1 libxres1 libxshmfence1 libxslt1.1
  libxss1 libxt6 libxtst6 libxv1 libxvmc1 libxxf86dga1 libxxf86vm1 libyajl2 libyelp0 libytnef0 libzapojit-0.0-0 libzeitgeist-1.0-1
  libzeitgeist-2.0-0 libzephyr4 lintian linux-libc-dev linux-sound-base lp-solve make manpages-dev mcp-account-manager-goa media-player-info
  memtest86+ mobile-broadband-provider-info modemmanager mousetweaks mscompress mtools mutter mutter-common nautilus nautilus-data nautilus-sendto
  nautilus-sendto-empathy nautilus-share network-manager network-manager-gnome network-manager-pptp network-manager-pptp-gnome notification-daemon
  obex-data-server obexd-client oneconf oneconf-common openprinting-ppds p11-kit p11-kit-modules patch patchutils pcmciautils plymouth
  plymouth-label plymouth-theme-ubuntu-gnome-logo plymouth-theme-ubuntu-gnome-text policykit-1 policykit-1-gnome policykit-desktop-privileges
  poppler-data poppler-utils pptp-linux printer-driver-c2esp printer-driver-foo2zjs printer-driver-foo2zjs-common printer-driver-gutenprint
  printer-driver-hpcups printer-driver-min12xxw printer-driver-pnm2ppa printer-driver-postscript-hp printer-driver-ptouch printer-driver-pxljr
  printer-driver-sag-gdi printer-driver-splix pulseaudio pulseaudio-module-bluetooth pulseaudio-module-x11 pulseaudio-utils python-aptdaemon
  python-aptdaemon.gtk3widgets python-boto python-cairo python-cloudfiles python-commandnotfound python-crypto python-cups python-cupshelpers
  python-dbus python-dbus-dev python-debtagshw python-defer python-dirspec python-gdbm python-gi python-gi-cairo python-gnomekeyring python-gobject
  python-gobject-2 python-gtk2 python-httplib2 python-ibus python-imaging python-ldb python-libxml2 python-lockfile python-lxml python-notify
  python-ntdb python-oauthlib python-oneconf python-openssl python-pam python-pexpect python-pil python-piston-mini-client python-pkg-resources
  python-pycurl python-renderpm python-reportlab python-reportlab-accel python-requests python-samba python-serial python-smbc python-talloc
  python-tdb python-twisted-bin python-twisted-core python-twisted-web python-ubuntu-sso-client python-urllib3 python-xdg python-zeitgeist
  python-zope.interface python3-apport python3-aptdaemon python3-aptdaemon.gtk3widgets python3-aptdaemon.pkcompat python3-brlapi python3-cairo
  python3-chardet python3-crypto python3-debian python3-defer python3-gi-cairo python3-httplib2 python3-louis python3-mako python3-markupsafe
  python3-oauthlib python3-oneconf python3-piston-mini-client python3-pkg-resources python3-problem-report python3-pyatspi python3-six
  python3-speechd python3-uno python3-xdg python3-xkit qpdf re2c rfkill rhythmbox rhythmbox-data rhythmbox-mozilla rhythmbox-plugin-cdrecorder
  rhythmbox-plugin-magnatune rhythmbox-plugin-zeitgeist rhythmbox-plugins rtkit sa-compile samba-common samba-common-bin samba-libs sane-utils
  seahorse session-migration sessioninstaller shotwell shotwell-common simple-scan smbclient software-center software-center-aptdaemon-plugins
  software-properties-gtk sound-theme-freedesktop spamassassin spamc speech-dispatcher speech-dispatcher-audio-plugins ssh-askpass-gnome ssl-cert
  syslinux syslinux-common syslinux-legacy system-config-printer-common system-config-printer-gnome system-config-printer-udev t1utils tcl tcl8.6
  tcpd telepathy-gabble telepathy-haze telepathy-idle telepathy-logger telepathy-mission-control-5 telepathy-salut tk tk8.6 toshset totem
  totem-common totem-plugins tracker tracker-extract tracker-miner-fs tracker-utils transmission-common transmission-gtk ttf-indic-fonts-core
  ttf-punjabi-fonts ttf-ubuntu-font-family ubuntu-drivers-common ubuntu-extras-keyring ubuntu-gnome-default-settings ubuntu-release-upgrader-gtk
  ubuntu-sso-client ubuntu-system-service udisks2 uno-libs3 unoconv unzip update-inetd update-manager update-notifier update-notifier-common upower
  ure usb-creator-common usb-creator-gtk usb-modeswitch usb-modeswitch-data usbmuxd vino wamerican whoopsie wireless-tools wodim wpasupplicant
  x11-apps x11-common x11-session-utils x11-utils x11-xfs-utils x11-xkb-utils x11-xserver-utils xbitmaps xdg-user-dirs xdg-user-dirs-gtk xdg-utils
  xdiagnose xfonts-base xfonts-encodings xfonts-mathml xfonts-scalable xfonts-utils xinit xinput xorg xorg-docs-core xserver-common xserver-xephyr
  xserver-xorg xserver-xorg-core xserver-xorg-input-all xserver-xorg-input-evdev xserver-xorg-input-mouse xserver-xorg-input-synaptics
  xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-all xserver-xorg-video-ati xserver-xorg-video-cirrus
  xserver-xorg-video-fbdev xserver-xorg-video-glamoregl xserver-xorg-video-intel xserver-xorg-video-mach64 xserver-xorg-video-mga
  xserver-xorg-video-modesetting xserver-xorg-video-neomagic xserver-xorg-video-nouveau xserver-xorg-video-openchrome xserver-xorg-video-qxl
  xserver-xorg-video-r128 xserver-xorg-video-radeon xserver-xorg-video-s3 xserver-xorg-video-savage xserver-xorg-video-siliconmotion
  xserver-xorg-video-sis xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident xserver-xorg-video-vesa
  xserver-xorg-video-vmware xsltproc xterm xul-ext-ubufox yelp yelp-tools yelp-xsl zeitgeist zeitgeist-core zeitgeist-datahub zenity zenity-common
  zip zsync
Suggested packages:
  gnome-cards-data apmd alsa-oss oss-compat default-mta mail-transport-agent libgtk2-perl gir1.2-colordgtk-1.0 aspell-doc spellutils binutils-doc
  bluez-hcidump vcdimager libdvdcss2 dvdauthor readom brltty-speechd brltty-x11 console-braille gnome-video-effects-frei0r gnome-video-effects-extra
  cpp-doc gcc-4.8-locales cups-pdf xpp wordlist emacsen-common jed-extra python-paramiko ncftp lftp python-gdata tahoe-lafs python-swiftclient
  cdrskin unrar evolution-ews evolution-plugins-experimental evolution-data-server-dbg arj lha lzip lzop ncompress p7zip-full rpm2cpio rzip
  sharutils unace unalz unar zoo ttf-lyx libgraphite3 pango-graphite hplip-cups printer-driver-all gcc-multilib autoconf automake1.9 libtool flex
  bison gcc-doc gcc-4.8-multilib gcc-4.8-doc libgcc1-dbg libgomp1-dbg libitm1-dbg libatomic1-dbg libasan0-dbg libtsan0-dbg libbacktrace1-dbg
  libquadmath0-dbg binutils-gold gconf-defaults-service gdb-doc gdbserver gedit-plugins cdrkit-doc gettext-doc hpijs gnome-screensaver xscreensaver
  desktop-base metacity x-window-manager gstreamer1.0-libav apache2.2-bin libapache2-mod-dnssd hplip-gui hplip-doc system-config-printer hunspell
  openoffice.org-hunspell openoffice.org-core ibus-clutter ibus-doc ibus-qt4 lrzip libgssapi-perl gstreamer1.0-plugins-ugly cdrdao
  gstreamer1.0-fluendo-mp3 gstreamer1.0-plugins-bad glibc-doc libgles2-mesa libgles2 debian-keyring libdv-bin libenchant-voikko exiv2 libfftw3-bin
  libfftw3-dev libgd-tools libglide3 gpgsm gphoto2 gtkam gpm grilo-plugins-0.2 gstreamer-codec-install gnome-codec-install gstreamer0.10-tools
  gstreamer1.0-tools gutenprint-locales libdata-dump-perl jackd2 libjasper-runtime liblcms2-utils lirc libcrypt-ssleay-perl minissdpd natpmp-utils
  ttf-baekmuk ttf-arphic-gbsn00lp ttf-arphic-bsmi00lp ttf-arphic-gkai00mp ttf-arphic-bkai00mp pcscd raptor2-utils rasqal-utils libraw1394-doc
  librdf-storage-postgresql librdf-storage-mysql librdf-storage-sqlite librdf-storage-virtuoso redland-utils libreoffice-base libopencl1
  libreoffice-style-crystal libreoffice-style-hicontrast libreoffice-style-oxygen libreoffice-style-sifr libreoffice-evolution crystalcursors
  kde-icons-crystal tango-icon-theme libreoffice-gcj libreoffice-java-common default-jre gcj-jre openjdk-7-jre openjdk-6-jre sun-java5-jre
  sun-java6-jre java5-runtime jre librsvg2-bin hpoj libsane-extras lm-sensors sg3-utils snmp-mibs-downloader libspectre1-dbg speex unity-common
  libauthen-ntlm-perl binutils-multiarch dpkg-dev libtext-template-perl libyaml-perl make-doc hwtools memtester kernel-patch-badram memtest86
  floppyd pidgin gajim samba network-manager-openconnect-gnome network-manager-openvpn-gnome network-manager-vpnc-gnome hpijs-ppds diffutils-doc
  fonts-japanese-mincho fonts-ipafont-mincho fonts-japanese-gothic fonts-ipafont-gothic fonts-arphic-ukai fonts-arphic-uming fonts-unfonts-core
  psutils hannah-foo2zjs tix gutenprint-doc magicfilter apsfilter pavumeter paman pavucontrol paprefs pulseaudio-module-raop
  pulseaudio-esound-compat python-crypto-dbg python-crypto-doc python-dbus-doc python-dbus-dbg python-gdbm-dbg python-gobject-2-dbg python-gtk2-doc
  python-lxml-dbg python-openssl-doc python-openssl-dbg python-pam-dbg python-pexpect-doc python-pil-doc python-pil-dbg python-distribute
  python-distribute-doc libcurl4-gnutls-dev python-pycurl-dbg python-renderpm-dbg pdf-viewer python-egenix-mxtexttools python-reportlab-doc
  python-wxgtk2.8 python-wxgtk python-twisted-bin-dbg python-tk python-glade2 python-qt3 python3-launchpadlib python3-crypto-dbg python3-beaker
  python-mako-doc python3-setuptools heimdal-clients unpaper account-plugin-facebook account-plugin-google account-plugin-flickr
  unity-control-center-signon cifs-utils razor libdbi-perl pyzor libmail-dkim-perl libttspico-utils speech-dispatcher-doc-cs
  speech-dispatcher-festival speech-dispatcher-flite openssl-blacklist tcl-tclreadline totem-mozilla gromit tracker-gui ubuntu-sso-client-gui
  xfsprogs reiserfsprogs exfat-utils btrfs-tools mdadm cryptsetup-bin comgt wvdial vinagre wpagui libengine-pkcs11-openssl mesa-utils nickle
  cairo-5c xfs xserver fonts-lyx fonts-stix xorg-docs xfonts-100dpi xfonts-75dpi gpointing-device-settings touchfreeze firmware-linux
  xfonts-cyrillic
Recommended packages:
  libc-dbg
The following NEW packages will be installed:
  acl acpi-support acpid aisleriot alsa-base alsa-utils anacron apg app-install-data app-install-data-partner apport apport-gtk apport-symptoms
  aptdaemon aptdaemon-data apturl apturl-common argyll aspell aspell-en at-spi2-core avahi-autoipd avahi-daemon avahi-utils baobab bc binutils bluez
  bluez-alsa bluez-cups brasero brasero-cdrkit brasero-common brltty cheese cheese-common colord cpp cpp-4.8 cracklib-runtime cups cups-browsed
  cups-bsd cups-client cups-common cups-core-drivers cups-daemon cups-filters cups-filters-core-drivers cups-pk-helper cups-ppdc cups-server-common
  dbus-x11 dc dconf-cli dconf-editor dconf-gsettings-backend dconf-service deja-dup deja-dup-backend-cloudfiles deja-dup-backend-gvfs
  deja-dup-backend-s3 desktop-file-utils dialog dictionaries-common diffstat dnsmasq-base duplicity dvd+rw-tools empathy empathy-common enchant eog
  espeak-data evince evince-common evolution evolution-common evolution-data-server evolution-data-server-common
  evolution-data-server-online-accounts evolution-indicator evolution-plugins file-roller firefox folks-common fontconfig fontconfig-config
  fonts-cantarell fonts-dejavu-core fonts-droid fonts-freefont-ttf fonts-kacst fonts-kacst-one fonts-khmeros-core fonts-lao fonts-liberation
  fonts-lklug-sinhala fonts-nanum fonts-opensymbol fonts-sil-abyssinica fonts-sil-padauk fonts-takao-pgothic fonts-thai-tlwg fonts-tibetan-machine
  fonts-tlwg-garuda fonts-tlwg-kinnari fonts-tlwg-loma fonts-tlwg-mono fonts-tlwg-norasi fonts-tlwg-purisa fonts-tlwg-sawasdee fonts-tlwg-typewriter
  fonts-tlwg-typist fonts-tlwg-typo fonts-tlwg-umpush fonts-tlwg-waree foomatic-db-compressed-ppds gcc gcc-4.8 gconf-service gconf-service-backend
  gconf2 gconf2-common gcr gdb gdisk gdm gedit gedit-common genisoimage geoclue gettext ghostscript ghostscript-x gir1.2-accountsservice-1.0
  gir1.2-atk-1.0 gir1.2-atspi-2.0 gir1.2-caribou-1.0 gir1.2-clutter-1.0 gir1.2-clutter-gst-2.0 gir1.2-cogl-1.0 gir1.2-coglpango-1.0
  gir1.2-dbusmenu-glib-0.4 gir1.2-dee-1.0 gir1.2-evince-3.0 gir1.2-freedesktop gir1.2-gck-1 gir1.2-gcr-3 gir1.2-gdata-0.0 gir1.2-gdesktopenums-3.0
  gir1.2-gdkpixbuf-2.0 gir1.2-gdm-1.0 gir1.2-gkbd-3.0 gir1.2-gmenu-3.0 gir1.2-gnomebluetooth-1.0 gir1.2-gnomedesktop-3.0 gir1.2-gnomekeyring-1.0
  gir1.2-goa-1.0 gir1.2-gst-plugins-base-1.0 gir1.2-gstreamer-1.0 gir1.2-gtk-3.0 gir1.2-gtkclutter-1.0 gir1.2-gtksource-3.0 gir1.2-gtop-2.0
  gir1.2-gudev-1.0 gir1.2-ibus-1.0 gir1.2-javascriptcoregtk-3.0 gir1.2-json-1.0 gir1.2-mutter-3.0 gir1.2-networkmanager-1.0 gir1.2-nmgtk-1.0
  gir1.2-notify-0.7 gir1.2-packagekitglib-1.0 gir1.2-pango-1.0 gir1.2-peas-1.0 gir1.2-polkit-1.0 gir1.2-rb-3.0 gir1.2-rest-0.7 gir1.2-secret-1
  gir1.2-soup-2.4 gir1.2-telepathyglib-0.12 gir1.2-telepathylogger-0.2 gir1.2-totem-1.0 gir1.2-totem-plparser-1.0 gir1.2-tracker-0.16
  gir1.2-udisks-2.0 gir1.2-unity-5.0 gir1.2-upowerglib-1.0 gir1.2-vte-2.90 gir1.2-webkit-3.0 gir1.2-wnck-3.0 gir1.2-xkl-1.0 gir1.2-zpj-0.0 gjs
  gkbd-capplet glib-networking glib-networking-common glib-networking-services gnome-accessibility-themes gnome-backgrounds gnome-bluetooth
  gnome-calculator gnome-color-manager gnome-contacts gnome-control-center gnome-control-center-data gnome-control-center-shared-data
  gnome-desktop3-data gnome-disk-utility gnome-documents gnome-font-viewer gnome-icon-theme gnome-icon-theme-extras gnome-icon-theme-full
  gnome-icon-theme-symbolic gnome-keyring gnome-mahjongg gnome-menus gnome-mines gnome-online-accounts gnome-online-miners gnome-orca
  gnome-screenshot gnome-session gnome-session-bin gnome-session-canberra gnome-session-common gnome-settings-daemon gnome-settings-daemon-schemas
  gnome-shell gnome-shell-common gnome-shell-extensions gnome-sudoku gnome-sushi gnome-system-log gnome-system-monitor gnome-terminal
  gnome-terminal-data gnome-themes-standard gnome-themes-standard-data gnome-tweak-tool gnome-user-guide gnome-user-share gnome-video-effects
  growisofs gsettings-desktop-schemas gsfonts gstreamer0.10-alsa gstreamer0.10-nice gstreamer0.10-plugins-base gstreamer0.10-plugins-good
  gstreamer0.10-pulseaudio gstreamer0.10-x gstreamer1.0-alsa gstreamer1.0-clutter gstreamer1.0-nice gstreamer1.0-plugins-base
  gstreamer1.0-plugins-good gstreamer1.0-pulseaudio gstreamer1.0-x gtk2-engines-pixbuf gucharmap guile-2.0-libs gvfs gvfs-backends gvfs-backends-goa
  gvfs-bin gvfs-common gvfs-daemons gvfs-fuse gvfs-libs hardening-includes hicolor-icon-theme hplip hplip-data humanity-icon-theme hunspell-en-us
  hwdata ibus ibus-gtk ibus-gtk3 ibus-pinyin ibus-table im-config indicator-application inputattach intel-gpu-tools intltool-debian iproute
  iputils-arping itstool kerneloops-daemon libaa1 libaccounts-glib0 libappindicator3-1 libapt-pkg-perl libarchive-zip-perl libarchive13 libart-2.0-2
  libasan0 libasound2 libasound2-data libasound2-plugins libaspell15 libasprintf-dev libassuan0 libasyncns0 libatasmart4 libatk-adaptor
  libatk-bridge2.0-0 libatk1.0-0 libatk1.0-data libatkmm-1.6-1 libatomic1 libatspi2.0-0 libauthen-sasl-perl libautodie-perl libavahi-client3
  libavahi-common-data libavahi-common3 libavahi-core7 libavahi-glib1 libavahi-gobject0 libavc1394-0 libbluetooth3 libboost-date-time1.54.0
  libboost-system1.54.0 libbrasero-media3-1 libbrlapi0.6 libburn4 libc-dev-bin libc6-dbg libc6-dev libcaca0 libcairo-gobject2 libcairo2
  libcairomm-1.0-1 libcamel-1.2-45 libcanberra-gtk-module libcanberra-gtk0 libcanberra-gtk3-0 libcanberra-gtk3-module libcanberra-pulse libcanberra0
  libcaribou-common libcaribou0 libcdio-cdda1 libcdio-paranoia1 libcdio13 libcdparanoia0 libcdr-0.0-0 libcheese-gtk23 libcheese7 libclone-perl
  libcloog-isl4 libclucene-contribs1 libclucene-core1 libclutter-1.0-0 libclutter-1.0-common libclutter-gst-2.0-0 libclutter-gtk-1.0-0 libcmis-0.4-4
  libcogl-common libcogl-pango15 libcogl15 libcolamd2.8.0 libcolord-gtk1 libcolord1 libcolorhug1 libcrack2 libcroco3 libcrypt-passwdmd5-perl
  libcups2 libcupscgi1 libcupsfilters1 libcupsimage2 libcupsmime1 libcupsppdc1 libcurl3 libdaemon0 libdatrie1 libdbusmenu-glib4 libdbusmenu-gtk3-4
  libdbusmenu-gtk4 libdconf1 libdee-1.0-4 libdigest-hmac-perl libdjvulibre-text libdjvulibre21 libdmapsharing-3.0-2 libdotconf0 libdpkg-perl
  libdrm-intel1 libdrm-nouveau2 libdrm-radeon1 libdv4 libebackend-1.2-7 libebook-1.2-14 libebook-contacts-1.2-0 libecal-1.2-16 libedata-book-1.2-20
  libedata-cal-1.2-23 libedataserver-1.2-18 libegl1-mesa libegl1-mesa-drivers libelfg0 libemail-valid-perl libenca0 libenchant1c2a
  libencode-locale-perl liberror-perl libespeak1 libevdocument3-4 libevent-2.0-5 libevolution libevview3-3 libexempi3 libexif12 libexiv2-12
  libexttextcat-2.0-0 libexttextcat-data libfarstream-0.1-0 libfarstream-0.2-2 libfftw3-single3 libfile-basedir-perl libfile-copy-recursive-perl
  libfile-desktopentry-perl libfile-fcntllock-perl libfile-listing-perl libfile-mimeinfo-perl libflac8 libfolks-eds25 libfolks-telepathy25
  libfolks25 libfont-afm-perl libfontconfig1 libfontembed1 libfontenc1 libframe6 libfs6 libgail-3-0 libgail-common libgail18 libgbm1 libgc1c2
  libgcc-4.8-dev libgconf-2-4 libgcr-ui-3-1 libgd3 libgdata-common libgdata13 libgdk-pixbuf2.0-0 libgdk-pixbuf2.0-common libgdm1 libgee-0.8-2
  libgeis1 libgeoclue0 libgettextpo-dev libgettextpo0 libgexiv2-2 libgif4 libgjs0e libgl1-mesa-dri libgl1-mesa-glx libglamor0 libglapi-mesa
  libglib2.0-bin libglibmm-2.4-1c2a libglu1-mesa libgmime-2.6-0 libgmp10 libgnome-bluetooth11 libgnome-control-center1 libgnome-desktop-3-7
  libgnome-keyring-common libgnome-keyring0 libgnome-menu-3-0 libgnomekbd-common libgnomekbd8 libgoa-1.0-0b libgoa-1.0-common libgoa-backend-1.0-1
  libgomp1 libgpgme11 libgphoto2-6 libgphoto2-l10n libgphoto2-port10 libgpm2 libgpod-common libgpod4 libgrail6 libgraphite2-3 libgrilo-0.2-1
  libgrip0 libgs9 libgs9-common libgsf-1-114 libgsf-1-common libgssdp-1.0-3 libgstreamer-plugins-base0.10-0 libgstreamer-plugins-base1.0-0
  libgstreamer-plugins-good1.0-0 libgstreamer0.10-0 libgstreamer1.0-0 libgtk-3-0 libgtk-3-bin libgtk-3-common libgtk2.0-0 libgtk2.0-bin
  libgtk2.0-common libgtkhtml-4.0-0 libgtkhtml-4.0-common libgtkhtml-editor-4.0-0 libgtkmm-3.0-1 libgtksourceview-3.0-1 libgtksourceview-3.0-common
  libgtop2-7 libgtop2-common libgucharmap-2-90-7 libgudev-1.0-0 libgupnp-1.0-4 libgupnp-igd-1.0-4 libgusb2 libgutenprint2 libgweather-3-6
  libgweather-common libgxps2 libharfbuzz-icu0 libharfbuzz0b libhpmud0 libhtml-form-perl libhtml-format-perl libhtml-parser-perl libhtml-tagset-perl
  libhtml-tree-perl libhttp-cookies-perl libhttp-daemon-perl libhttp-date-perl libhttp-message-perl libhttp-negotiate-perl libhunspell-1.3-0
  libhyphen0 libibus-1.0-5 libical1 libicc2 libice6 libicu52 libido3-0.1-0 libiec61883-0 libieee1284-3 libijs-0.35 libimdi0 libimobiledevice4
  libindicator3-7 libio-html-perl libio-pty-perl libio-socket-inet6-perl libio-socket-ssl-perl libipc-run-perl libipc-system-simple-perl
  libiptcdata0 libisl10 libisofs6 libitm1 libiw30 libjack-jackd2-0 libjasper1 libjavascriptcoregtk-3.0-0 libjbig0 libjbig2dec0 libjpeg-turbo8
  libjpeg8 libjson-glib-1.0-0 libjson-glib-1.0-common libjte1 libkpathsea6 liblangtag-common liblangtag1 liblcms2-2 libldb1 liblircclient0
  liblist-moreutils-perl libllvm3.4 liblouis-data liblouis2 libltdl7 liblua5.2-0 liblwp-mediatypes-perl liblwp-protocol-https-perl liblzo2-2
  libmail-spf-perl libmailtools-perl libmbim-glib0 libmeanwhile1 libmessaging-menu0 libmhash2 libminiupnpc8 libmission-control-plugins0 libmm-glib0
  libmnl0 libmozjs-24-0 libmpc3 libmpfr4 libmspub-0.0-0 libmtdev1 libmtp-common libmtp-runtime libmtp9 libmusicbrainz5-0 libmutter0c libmythes-1.2-0
  libnatpmp1 libnautilus-extension1a libneon27-gnutls libnet-dns-perl libnet-domain-tld-perl libnet-http-perl libnet-ip-perl libnet-libidn-perl
  libnet-smtp-ssl-perl libnet-ssleay-perl libnetaddr-ip-perl libnetfilter-conntrack3 libnettle4 libnice10 libnl-route-3-200 libnm-glib-vpn1
  libnm-glib4 libnm-gtk-common libnm-gtk0 libnm-util2 libnotify-bin libnotify4 libnspr4 libnss-mdns libnss-myhostname libnss3 libnss3-nssdb libntdb1
  liboauth0 libogg0 libopencc1 libopenobex1 libopenvg1-mesa liborc-0.4-0 liborcus-0.6-0 libp11-kit-gnome-keyring libpackagekit-glib2-16
  libpam-gnome-keyring libpango-1.0-0 libpango1.0-0 libpangocairo-1.0-0 libpangoft2-1.0-0 libpangomm-1.4-1 libpangox-1.0-0 libpangoxft-1.0-0
  libpaper-utils libpaper1 libpciaccess0 libpcsclite1 libpeas-1.0-0 libpeas-common libperl5.18 libperlio-gzip-perl libpixman-1-0 libplist1
  libpolkit-agent-1-0 libpolkit-backend-1-0 libpoppler-glib8 libpoppler44 libportaudio2 libproxy1 libproxy1-plugin-gsettings
  libproxy1-plugin-networkmanager libpst4 libpulse-mainloop-glib0 libpulse0 libpulsedsp libpurple-bin libpurple0 libpwquality-common libpwquality1
  libpython2.7 libpython3.4 libpyzy-1.0-0 libqmi-glib0 libqpdf13 libquadmath0 libraptor2-0 librasqal3 libraw1394-11 libraw9 librdf0 libreadline5
  libreoffice-avmedia-backend-gstreamer libreoffice-base-core libreoffice-calc libreoffice-common libreoffice-core libreoffice-draw
  libreoffice-gnome libreoffice-gtk libreoffice-impress libreoffice-math libreoffice-ogltrans libreoffice-pdfimport
  libreoffice-presentation-minimizer libreoffice-style-galaxy libreoffice-style-human libreoffice-style-tango libreoffice-writer librest-0.7-0
  librhythmbox-core8 librsvg2-2 librsvg2-common librsync1 libsamplerate0 libsane libsane-common libsane-hpaio libsbc1 libsecret-1-0 libsecret-common
  libsensors4 libsgutils2-2 libshout3 libsignon-glib1 libsm6 libsmbclient libsndfile1 libsnmp-base libsnmp30 libsocket6-perl libsonic0
  libsoup-gnome2.4-1 libsoup2.4-1 libspectre1 libspeechd2 libspeex1 libspeexdsp1 libstartup-notification0 libsub-identify-perl
  libsys-hostname-long-perl libsystemd-journal0 libt1-5 libtag1-vanilla libtag1c2a libtalloc2 libtcl8.6 libtdb1 libtelepathy-farstream3
  libtelepathy-glib0 libtelepathy-logger3 libtevent0 libtext-levenshtein-perl libthai-data libthai0 libtheora0 libtiff5 libtk8.6 libtotem-plparser18
  libtotem0 libtracker-extract-0.16-0 libtracker-miner-0.16-0 libtracker-sparql-0.16-0 libtxc-dxtn-s2tc0 libudisks2-0 libunistring0
  libunity-control-center1 libunity-protocol-private0 libunity-scopes-json-def-desktop libunity9 libupower-glib1 liburi-perl libusbmuxd2
  libutempter0 libv4l-0 libv4lconvert0 libvisio-0.0-0 libvisual-0.4-0 libvisual-0.4-plugins libvorbis0a libvorbisenc2 libvorbisfile3 libvpx1
  libvte-2.90-9 libvte-2.90-common libwacom-common libwacom2 libwavpack1 libwayland-client0 libwayland-cursor0 libwayland-egl1-mesa
  libwayland-server0 libwbclient0 libwebkitgtk-3.0-0 libwebkitgtk-3.0-common libwebp5 libwebpmux1 libwhoopsie0 libwmf0.2-7 libwmf0.2-7-gtk
  libwnck-3-0 libwnck-3-common libwpd-0.9-9 libwpg-0.2-2 libwps-0.2-2 libwrap0 libwww-perl libwww-robotrules-perl libx11-xcb1 libxatracker2 libxaw7
  libxcb-dri2-0 libxcb-dri3-0 libxcb-glx0 libxcb-icccm4 libxcb-image0 libxcb-keysyms1 libxcb-present0 libxcb-render0 libxcb-shape0 libxcb-shm0
  libxcb-sync1 libxcb-util0 libxcb-xf86dri0 libxcb-xfixes0 libxcb-xv0 libxcomposite1 libxcursor1 libxdamage1 libxfixes3 libxfont1 libxft2 libxi6
  libxinerama1 libxkbcommon0 libxkbfile1 libxklavier16 libxml2-utils libxmu6 libxp6 libxpm4 libxrandr2 libxrender1 libxres1 libxshmfence1 libxslt1.1
  libxss1 libxt6 libxtst6 libxv1 libxvmc1 libxxf86dga1 libxxf86vm1 libyajl2 libyelp0 libytnef0 libzapojit-0.0-0 libzeitgeist-1.0-1
  libzeitgeist-2.0-0 libzephyr4 lintian linux-libc-dev linux-sound-base lp-solve make manpages-dev mcp-account-manager-goa media-player-info
  memtest86+ mobile-broadband-provider-info modemmanager mousetweaks mscompress mtools mutter mutter-common nautilus nautilus-data nautilus-sendto
  nautilus-sendto-empathy nautilus-share network-manager network-manager-gnome network-manager-pptp network-manager-pptp-gnome notification-daemon
  obex-data-server obexd-client oneconf oneconf-common openprinting-ppds p11-kit p11-kit-modules patch patchutils pcmciautils plymouth-label
  plymouth-theme-ubuntu-gnome-logo plymouth-theme-ubuntu-gnome-text policykit-1 policykit-1-gnome policykit-desktop-privileges poppler-data
  poppler-utils pptp-linux printer-driver-c2esp printer-driver-foo2zjs printer-driver-foo2zjs-common printer-driver-gutenprint printer-driver-hpcups
  printer-driver-min12xxw printer-driver-pnm2ppa printer-driver-postscript-hp printer-driver-ptouch printer-driver-pxljr printer-driver-sag-gdi
  printer-driver-splix pulseaudio pulseaudio-module-bluetooth pulseaudio-module-x11 pulseaudio-utils python-aptdaemon python-aptdaemon.gtk3widgets
  python-boto python-cairo python-cloudfiles python-commandnotfound python-crypto python-cups python-cupshelpers python-dbus python-dbus-dev
  python-debtagshw python-defer python-dirspec python-gdbm python-gi python-gi-cairo python-gnomekeyring python-gobject python-gobject-2 python-gtk2
  python-httplib2 python-ibus python-imaging python-ldb python-libxml2 python-lockfile python-lxml python-notify python-ntdb python-oauthlib
  python-oneconf python-openssl python-pam python-pexpect python-pil python-piston-mini-client python-pkg-resources python-pycurl python-renderpm
  python-reportlab python-reportlab-accel python-requests python-samba python-serial python-smbc python-talloc python-tdb python-twisted-bin
  python-twisted-core python-twisted-web python-ubuntu-sso-client python-urllib3 python-xdg python-zeitgeist python-zope.interface python3-apport
  python3-aptdaemon python3-aptdaemon.gtk3widgets python3-aptdaemon.pkcompat python3-brlapi python3-cairo python3-chardet python3-crypto
  python3-debian python3-defer python3-gi-cairo python3-httplib2 python3-louis python3-mako python3-markupsafe python3-oauthlib python3-oneconf
  python3-piston-mini-client python3-pkg-resources python3-problem-report python3-pyatspi python3-six python3-speechd python3-uno python3-xdg
  python3-xkit qpdf re2c rfkill rhythmbox rhythmbox-data rhythmbox-mozilla rhythmbox-plugin-cdrecorder rhythmbox-plugin-magnatune
  rhythmbox-plugin-zeitgeist rhythmbox-plugins rtkit sa-compile samba-common samba-common-bin samba-libs sane-utils seahorse session-migration
  sessioninstaller shotwell shotwell-common simple-scan smbclient software-center software-center-aptdaemon-plugins software-properties-gtk
  sound-theme-freedesktop spamassassin spamc speech-dispatcher speech-dispatcher-audio-plugins ssh-askpass-gnome ssl-cert syslinux syslinux-common
  syslinux-legacy system-config-printer-common system-config-printer-gnome system-config-printer-udev t1utils tcl tcl8.6 tcpd telepathy-gabble
  telepathy-haze telepathy-idle telepathy-logger telepathy-mission-control-5 telepathy-salut tk tk8.6 toshset totem totem-common totem-plugins
  tracker tracker-extract tracker-miner-fs tracker-utils transmission-common transmission-gtk ttf-indic-fonts-core ttf-punjabi-fonts
  ttf-ubuntu-font-family ubuntu-drivers-common ubuntu-extras-keyring ubuntu-gnome-default-settings ubuntu-gnome-desktop ubuntu-release-upgrader-gtk
  ubuntu-sso-client ubuntu-system-service udisks2 uno-libs3 unoconv unzip update-inetd update-manager update-notifier update-notifier-common upower
  ure usb-creator-common usb-creator-gtk usb-modeswitch usb-modeswitch-data usbmuxd vino wamerican whoopsie wireless-tools wodim wpasupplicant
  x11-apps x11-common x11-session-utils x11-utils x11-xfs-utils x11-xkb-utils x11-xserver-utils xbitmaps xdg-user-dirs xdg-user-dirs-gtk xdg-utils
  xdiagnose xfonts-base xfonts-encodings xfonts-mathml xfonts-scalable xfonts-utils xinit xinput xorg xorg-docs-core xserver-common xserver-xephyr
  xserver-xorg xserver-xorg-core xserver-xorg-input-all xserver-xorg-input-evdev xserver-xorg-input-mouse xserver-xorg-input-synaptics
  xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-all xserver-xorg-video-ati xserver-xorg-video-cirrus
  xserver-xorg-video-fbdev xserver-xorg-video-glamoregl xserver-xorg-video-intel xserver-xorg-video-mach64 xserver-xorg-video-mga
  xserver-xorg-video-modesetting xserver-xorg-video-neomagic xserver-xorg-video-nouveau xserver-xorg-video-openchrome xserver-xorg-video-qxl
  xserver-xorg-video-r128 xserver-xorg-video-radeon xserver-xorg-video-s3 xserver-xorg-video-savage xserver-xorg-video-siliconmotion
  xserver-xorg-video-sis xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident xserver-xorg-video-vesa
  xserver-xorg-video-vmware xsltproc xterm xul-ext-ubufox yelp yelp-tools yelp-xsl zeitgeist zeitgeist-core zeitgeist-datahub zenity zenity-common
  zip zsync
The following packages will be upgraded:
  libglib2.0-0 libplymouth2 plymouth
3 upgraded, 1166 newly installed, 0 to remove and 13 not upgraded.
Need to get 424 MB of archives.
After this operation, 1,599 MB of additional disk space will be used.
Do you want to continue? [Y/n] n
Abort.

```

---

### Post by kansasnoob on 2014-04-04
The work paid off:

[https://bugs.launchpad.net/ubuntu/+source/tasksel/+bug/1299953/comments/7](https://bugs.launchpad.net/ubuntu/+source/tasksel/+bug/1299953/comments/7)

> 

This bug was fixed in the package tasksel - 2.88ubuntu15

---------------
tasksel (2.88ubuntu15) trusty; urgency=medium

  [ Jackson Doak ]
  * Add seeds for ubuntu-gnome (LP: #1299953).

  [ Colin Watson ]
  * Point Ubuntu task update script at trusty.
  * Update Ubuntu tasks from seeds, removing ubuntu-touch (which doesn't
    have Task fields in the archive any more anyway).
 -- Colin Watson <cjwatson@ubuntu.com> Fri, 04 Apr 2014 12:49:20 +0100


---

