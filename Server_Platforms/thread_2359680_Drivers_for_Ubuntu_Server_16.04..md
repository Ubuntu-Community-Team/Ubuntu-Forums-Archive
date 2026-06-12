---
title: "Drivers for Ubuntu Server 16.04."
date: 2017-04-26
forum: Server Platforms
---

### Post by sethanath2 on 2017-04-26
Hi,

I would like to be able to install most of the drivers for Ubuntu Server 16.04. I have done the following.

$ sudo apt update
$ sudo apt upgrade
$ sudo apt dist-upgrade
$ sudo apt-get install amd64-microcode

However, when I executed the command below, I keep getting desktops along with Nvidia driver.

```
$ sudo apt install nvidia-340
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  adwaita-icon-theme apg aptdaemon aspell aspell-en at-spi2-core avahi-daemon
  avahi-utils bbswitch-dkms binutils bluez bluez-obexd build-essential
  cheese-common colord colord-data cpp cpp-5 cracklib-runtime cups-pk-helper
  dbus-x11 dconf-cli dconf-gsettings-backend dconf-service desktop-file-utils
  dictionaries-common diffstat dkms dpkg-dev emacsen-common enchant
  evolution-data-server evolution-data-server-common
  evolution-data-server-online-accounts fakeroot fontconfig fontconfig-config
  fonts-dejavu-core g++ g++-5 gcc gcc-5 gcr gdisk geoclue geoclue-ubuntu-geoip
  gettext gir1.2-atk-1.0 gir1.2-freedesktop gir1.2-gdkpixbuf-2.0
  gir1.2-gnomekeyring-1.0 gir1.2-gtk-3.0 gir1.2-ibus-1.0 gir1.2-notify-0.7
  gir1.2-packagekitglib-1.0 gir1.2-pango-1.0 gkbd-capplet glib-networking
  glib-networking-common glib-networking-services gnome-bluetooth
  gnome-desktop3-data gnome-keyring gnome-menus gnome-power-manager
  gnome-screensaver gnome-session-bin gnome-settings-daemon-schemas
  gnome-user-guide gnome-user-share gsettings-desktop-schemas
  gsettings-ubuntu-schemas gstreamer1.0-clutter-3.0 gstreamer1.0-plugins-base
  gstreamer1.0-plugins-good gstreamer1.0-x gvfs gvfs-backends gvfs-common
  gvfs-daemons gvfs-libs hardening-includes hicolor-icon-theme
  humanity-icon-theme hunspell-en-us hwdata ibus ibus-gtk ibus-gtk3 im-config
  indicator-applet indicator-application indicator-bluetooth
  indicator-datetime indicator-keyboard indicator-messages indicator-power
  indicator-session indicator-sound intltool-debian ippusbxd iputils-arping
  lib32gcc1 libaa1 libaccount-plugin-1.0-0 libaccount-plugin-generic-oauth
  libaccount-plugin-google libaccounts-glib0 libaccounts-qt5-1
  libalgorithm-diff-perl libalgorithm-diff-xs-perl libalgorithm-merge-perl
  libappindicator3-1 libapt-pkg-perl libarchive-zip-perl libarchive13 libasan2
  libasound2-plugins libaspell15 libasprintf-dev libassuan0 libasyncns0
  libatasmart4 libatk-bridge2.0-0 libatk1.0-0 libatk1.0-data libatomic1
  libatspi2.0-0 libauthen-sasl-perl libavahi-client3 libavahi-common-data
  libavahi-common3 libavahi-core7 libavahi-glib1 libavc1394-0 libbluetooth3
  libboost-filesystem1.58.0 libboost-system1.58.0 libc-dev-bin libc6-dev
  libc6-i386 libcaca0 libcairo-gobject2 libcairo2 libcamel-1.2-54
  libcanberra-gtk3-0 libcanberra-gtk3-module libcanberra-pulse libcanberra0
  libcc1-0 libcdio-cdda1 libcdio-paranoia1 libcdio13 libcdparanoia0
  libcgi-fast-perl libcgi-pm-perl libcgmanager0 libcheese-gtk25 libcheese8
  libcilkrts5 libclass-accessor-perl libclone-perl libclutter-1.0-0
  libclutter-1.0-common libclutter-gst-3.0-0 libclutter-gtk-1.0-0
  libcogl-common libcogl-pango20 libcogl-path20 libcogl20 libcolord2
  libcolorhug2 libcrack2 libcroco3 libcuda1-340 libcups2 libdaemon0
  libdata-alias-perl libdatrie1 libdbusmenu-glib4 libdbusmenu-gtk3-4 libdconf1
  libdigest-hmac-perl libdouble-conversion1v5 libdpkg-perl libdrm-amdgpu1
  libdrm-intel1 libdrm-nouveau2 libdrm-radeon1 libdv4 libebackend-1.2-10
  libebook-1.2-16 libebook-contacts-1.2-2 libecal-1.2-19 libedata-book-1.2-25
  libedata-cal-1.2-28 libedataserver-1.2-21 libegl1-mesa libemail-valid-perl
  libenchant1c2a libencode-locale-perl libepoxy0 libevdev2 libexif12
  libexporter-tiny-perl libfakeroot libfcgi-perl libfcitx-config4
  libfcitx-gclient0 libfcitx-utils0 libfftw3-single3 libfile-basedir-perl
  libfile-fcntllock-perl libflac8 libfontconfig1 libfontenc1 libgbm1
  libgcc-5-dev libgck-1-0 libgcr-3-common libgcr-base-3-1 libgcr-ui-3-1 libgd3
  libgdata-common libgdata22 libgdk-pixbuf2.0-0 libgdk-pixbuf2.0-common
  libgee-0.8-2 libgeoclue0 libgeocode-glib0 libgeonames0 libgettextpo-dev
  libgettextpo0 libgl1-mesa-dri libgl1-mesa-glx libglapi-mesa libglib2.0-bin
  libgnome-bluetooth13 libgnome-desktop-3-12 libgnome-keyring-common
  libgnome-keyring0 libgnome-menu-3-0 libgnomekbd-common libgnomekbd8
  libgoa-1.0-0b libgoa-1.0-common libgphoto2-6 libgphoto2-l10n
  libgphoto2-port12 libgraphite2-3 libgstreamer-plugins-base1.0-0
  libgstreamer-plugins-good1.0-0 libgstreamer1.0-0 libgtk-3-0 libgtk-3-bin
  libgtk-3-common libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libgtop-2.0-10
  libgtop2-common libgudev-1.0-0 libgusb2 libgweather-3-6 libgweather-common
  libharfbuzz-icu0 libharfbuzz0b libhtml-parser-perl libhtml-tagset-perl
  libhttp-date-perl libhttp-message-perl libhunspell-1.3-0 libhyphen0
  libibus-1.0-5 libical1a libice6 libido3-0.1-0 libiec61883-0 libieee1284-3
  libimobiledevice6 libindicator3-7 libinput10 libio-html-perl libio-pty-perl
  libio-socket-inet6-perl libio-socket-ssl-perl libio-string-perl
  libipc-run-perl libipc-system-simple-perl libisl15 libitm1 libjack-jackd2-0
  libjansson4 libjavascriptcoregtk-4.0-18 libjbig0 libjpeg-turbo8 libjpeg8
  libjson-glib-1.0-0 libjson-glib-1.0-common liblcms2-2 libldb1
  liblightdm-gobject-1-0 liblist-moreutils-perl libllvm3.8 liblsan0 libltdl7
  liblwp-mediatypes-perl libmailtools-perl libmbim-glib4 libmbim-proxy
  libmirclient9 libmircommon5 libmirprotobuf3 libmm-glib0 libmpc3 libmpx0
  libmtdev1 libmtp-common libmtp-runtime libmtp9 libnautilus-extension1a
  libndp0 libnet-dns-perl libnet-domain-tld-perl libnet-ip-perl
  libnet-libidn-perl libnet-smtp-ssl-perl libnet-ssleay-perl libnih-dbus1
  libnm-glib4 libnm-gtk-common libnm-gtk0 libnm-util2 libnm0 libnma-common
  libnma0 libnotify4 libnspr4 libnss-mdns libnss3 libnss3-nssdb liboauth0
  libogg0 libopus0 liborc-0.4-0 libp11-kit-gnome-keyring
  libpackagekit-glib2-16 libpam-gnome-keyring libpanel-applet0 libpango-1.0-0
  libpangocairo-1.0-0 libpangoft2-1.0-0 libpangoxft-1.0-0
  libparse-debianchangelog-perl libpcre16-3 libpcsclite1 libperlio-gzip-perl
  libpixman-1-0 libplist3 libprotobuf-lite9v5 libproxy1v5
  libpulse-mainloop-glib0 libpulse0 libpulsedsp libpwquality-common
  libpwquality1 libpython2.7 libqmi-glib1 libqmi-proxy libqt5core5a
  libqt5dbus5 libqt5gui5 libqt5network5 libqt5opengl5 libqt5printsupport5
  libqt5qml5 libqt5quick5 libqt5sql5 libqt5sql5-sqlite libqt5svg5
  libqt5webkit5 libqt5widgets5 libqt5xml5 libquadmath0 libraw1394-11
  librest-0.7-0 librsvg2-2 librsvg2-common libsane libsane-common
  libsecret-1-0 libsecret-common libshout3 libsignon-extension1
  libsignon-glib1 libsignon-plugins-common1 libsignon-qt5-1 libsm6
  libsmbclient libsndfile1 libsocket6-perl libsoup-gnome2.4-1 libsoup2.4-1
  libspeex1 libspeexdsp1 libstdc++-5-dev libsub-name-perl libtag1v5
  libtag1v5-vanilla libtalloc2 libtdb1 libtevent0 libtext-levenshtein-perl
  libthai-data libthai0 libtheora0 libtiff5 libtimedate-perl
  libtimezonemap-data libtimezonemap1 libtsan0 libtxc-dxtn-s2tc0 libubsan0
  libudisks2-0 libunistring0 libunity-control-center1
  libunity-settings-daemon1 libupower-glib3 liburi-perl liburl-dispatcher1
  libusbmuxd4 libv4l-0 libv4lconvert0 libvdpau1 libvisual-0.4-0 libvorbis0a
  libvorbisenc2 libvorbisfile3 libvpx3 libwacom-bin libwacom-common libwacom2
  libwavpack1 libwayland-client0 libwayland-cursor0 libwayland-egl1-mesa
  libwayland-server0 libwbclient0 libwebkit2gtk-4.0-37
  libwebkit2gtk-4.0-37-gtk2 libwebp5 libwebrtc-audio-processing-0 libx11-xcb1
  libxaw7 libxcb-dri2-0 libxcb-dri3-0 libxcb-glx0 libxcb-icccm4 libxcb-image0
  libxcb-keysyms1 libxcb-present0 libxcb-randr0 libxcb-render-util0
  libxcb-render0 libxcb-shape0 libxcb-shm0 libxcb-sync1 libxcb-util1
  libxcb-xfixes0 libxcb-xkb1 libxcomposite1 libxcursor1 libxdamage1 libxfixes3
  libxfont1 libxft2 libxi6 libxinerama1 libxkbcommon-x11-0 libxkbcommon0
  libxkbfile1 libxklavier16 libxmu6 libxnvctrl0 libxpm4 libxrandr2 libxrender1
  libxshmfence1 libxslt1.1 libxt6 libxtst6 libxv1 libxxf86dga1 libxxf86vm1
  libyaml-libyaml-perl libyelp0 lightdm lintian linux-libc-dev make
  manpages-dev mesa-vdpau-drivers mobile-broadband-provider-info modemmanager
  mountall mousetweaks nautilus-data network-manager network-manager-gnome
  network-manager-pptp notification-daemon nvidia-opencl-icd-340 nvidia-prime
  nvidia-settings ocl-icd-libopencl1 p11-kit p11-kit-modules patchutils
  pinentry-gnome3 pkg-config policykit-1-gnome ppp pptp-linux pulseaudio
  pulseaudio-module-x11 pulseaudio-utils python-talloc python3-aptdaemon
  python3-aptdaemon.pkcompat python3-bs4 python3-cairo python3-cups
  python3-cupshelpers python3-defer python3-html5lib python3-lxml python3-xdg
  qttranslations5-l10n rtkit samba-libs screen-resolution-extra
  session-migration signon-keyring-extension signon-plugin-oauth2
  signon-plugin-password signon-ui signon-ui-service signon-ui-x11 signond
  sound-theme-freedesktop system-config-printer-common
  system-config-printer-gnome system-config-printer-udev t1utils ubuntu-mono
  ubuntu-system-service ubuntu-touch-sounds udisks2 unity-control-center
  unity-control-center-faces unity-control-center-signon unity-greeter
  unity-settings-daemon upower upstart usb-modeswitch usb-modeswitch-data
  usbmuxd vdpau-driver-all wamerican wpasupplicant x11-common x11-utils
  x11-xkb-utils xfonts-base xfonts-encodings xfonts-utils xserver-common
  xserver-xorg xserver-xorg-core xserver-xorg-input-all
  xserver-xorg-input-evdev xserver-xorg-input-synaptics
  xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-legacy yelp
  yelp-xsl
Suggested packages:
  aspell-doc spellutils avahi-autoipd bumblebee binutils-doc
  colord-sensor-argyll cpp-doc gcc-5-locales debian-keyring evolution
  evolution-data-server-dbg g++-multilib g++-5-multilib gcc-5-doc
  libstdc++6-5-dbg gcc-multilib autoconf automake libtool flex bison gdb
  gcc-doc gcc-5-multilib libgcc1-dbg libgomp1-dbg libitm1-dbg libatomic1-dbg
  libasan2-dbg liblsan0-dbg libtsan0-dbg libubsan0-dbg libcilkrts5-dbg
  libmpx0-dbg libquadmath0-dbg gettext-doc autopoint apache2-bin
  libapache2-mod-dnssd samba-common hunspell openoffice.org-hunspell
  | openoffice.org-core ibus-clutter ibus-doc ibus-qt4 click powerd
  unity-system-compositor zenity unity-greeter-session-broadcast lrzip
  libgssapi-perl glibc-doc libcanberra-gtk0 libgles2-mesa | libgles2
  cups-common libdv-bin oss-compat libenchant-voikko fcitx libfftw3-bin
  libfftw3-dev libgd-tools gphoto2 libvisual-0.4-plugins gstreamer1.0-tools
  libdata-dump-perl libusbmuxd-tools jackd2 liblcms2-utils avahi-autoipd
  | zeroconf opus-tools libhtml-template-perl libxml-simple-perl pcscd
  libqt5libqgtk2 qt5-image-formats-plugins qtwayland5 libraw1394-doc
  librsvg2-bin hplip libsane-extras sane-utils speex libstdc++-5-doc
  libwww-perl url-dispatcher bindfs binutils-multiarch libtext-template-perl
  make-doc nautilus network-manager-openconnect-gnome
  network-manager-openvpn-gnome network-manager-vpnc-gnome
  network-manager-pptp-gnome pinentry-doc pavumeter pavucontrol paman paprefs
  python3-genshi python3-lxml-dbg python-lxml-doc python3-smbc reiserfsprogs
  exfat-utils libcanberra-gtk-module x11-xserver-utils
  lightdm-remote-session-freerdp lightdm-remote-session-uccsconfigure
  remote-login-service metacity | x-window-manager graphviz upstart-monitor
  comgt wvdial libvdpau-va-gl1 nvidia-vdpau-driver
  nvidia-legacy-340xx-vdpau-driver wpagui libengine-pkcs11-openssl mesa-utils
  xfonts-100dpi | xfonts-75dpi xfonts-scalable gpointing-device-settings
  touchfreeze xinput
The following NEW packages will be installed:
  adwaita-icon-theme apg aptdaemon aspell aspell-en at-spi2-core avahi-daemon
  avahi-utils bbswitch-dkms binutils bluez bluez-obexd build-essential
  cheese-common colord colord-data cpp cpp-5 cracklib-runtime cups-pk-helper
  dbus-x11 dconf-cli dconf-gsettings-backend dconf-service desktop-file-utils
  dictionaries-common diffstat dkms dpkg-dev emacsen-common enchant
  evolution-data-server evolution-data-server-common
  evolution-data-server-online-accounts fakeroot fontconfig fontconfig-config
  fonts-dejavu-core g++ g++-5 gcc gcc-5 gcr gdisk geoclue geoclue-ubuntu-geoip
  gettext gir1.2-atk-1.0 gir1.2-freedesktop gir1.2-gdkpixbuf-2.0
  gir1.2-gnomekeyring-1.0 gir1.2-gtk-3.0 gir1.2-ibus-1.0 gir1.2-notify-0.7
  gir1.2-packagekitglib-1.0 gir1.2-pango-1.0 gkbd-capplet glib-networking
  glib-networking-common glib-networking-services gnome-bluetooth
  gnome-desktop3-data gnome-keyring gnome-menus gnome-power-manager
  gnome-screensaver gnome-session-bin gnome-settings-daemon-schemas
  gnome-user-guide gnome-user-share gsettings-desktop-schemas
  gsettings-ubuntu-schemas gstreamer1.0-clutter-3.0 gstreamer1.0-plugins-base
  gstreamer1.0-plugins-good gstreamer1.0-x gvfs gvfs-backends gvfs-common
  gvfs-daemons gvfs-libs hardening-includes hicolor-icon-theme
  humanity-icon-theme hunspell-en-us hwdata ibus ibus-gtk ibus-gtk3 im-config
  indicator-applet indicator-application indicator-bluetooth
  indicator-datetime indicator-keyboard indicator-messages indicator-power
  indicator-session indicator-sound intltool-debian ippusbxd iputils-arping
  lib32gcc1 libaa1 libaccount-plugin-1.0-0 libaccount-plugin-generic-oauth
  libaccount-plugin-google libaccounts-glib0 libaccounts-qt5-1
  libalgorithm-diff-perl libalgorithm-diff-xs-perl libalgorithm-merge-perl
  libappindicator3-1 libapt-pkg-perl libarchive-zip-perl libarchive13 libasan2
  libasound2-plugins libaspell15 libasprintf-dev libassuan0 libasyncns0
  libatasmart4 libatk-bridge2.0-0 libatk1.0-0 libatk1.0-data libatomic1
  libatspi2.0-0 libauthen-sasl-perl libavahi-client3 libavahi-common-data
  libavahi-common3 libavahi-core7 libavahi-glib1 libavc1394-0 libbluetooth3
  libboost-filesystem1.58.0 libboost-system1.58.0 libc-dev-bin libc6-dev
  libc6-i386 libcaca0 libcairo-gobject2 libcairo2 libcamel-1.2-54
  libcanberra-gtk3-0 libcanberra-gtk3-module libcanberra-pulse libcanberra0
  libcc1-0 libcdio-cdda1 libcdio-paranoia1 libcdio13 libcdparanoia0
  libcgi-fast-perl libcgi-pm-perl libcgmanager0 libcheese-gtk25 libcheese8
  libcilkrts5 libclass-accessor-perl libclone-perl libclutter-1.0-0
  libclutter-1.0-common libclutter-gst-3.0-0 libclutter-gtk-1.0-0
  libcogl-common libcogl-pango20 libcogl-path20 libcogl20 libcolord2
  libcolorhug2 libcrack2 libcroco3 libcuda1-340 libcups2 libdaemon0
  libdata-alias-perl libdatrie1 libdbusmenu-glib4 libdbusmenu-gtk3-4 libdconf1
  libdigest-hmac-perl libdouble-conversion1v5 libdpkg-perl libdrm-amdgpu1
  libdrm-intel1 libdrm-nouveau2 libdrm-radeon1 libdv4 libebackend-1.2-10
  libebook-1.2-16 libebook-contacts-1.2-2 libecal-1.2-19 libedata-book-1.2-25
  libedata-cal-1.2-28 libedataserver-1.2-21 libegl1-mesa libemail-valid-perl
  libenchant1c2a libencode-locale-perl libepoxy0 libevdev2 libexif12
  libexporter-tiny-perl libfakeroot libfcgi-perl libfcitx-config4
  libfcitx-gclient0 libfcitx-utils0 libfftw3-single3 libfile-basedir-perl
  libfile-fcntllock-perl libflac8 libfontconfig1 libfontenc1 libgbm1
  libgcc-5-dev libgck-1-0 libgcr-3-common libgcr-base-3-1 libgcr-ui-3-1 libgd3
  libgdata-common libgdata22 libgdk-pixbuf2.0-0 libgdk-pixbuf2.0-common
  libgee-0.8-2 libgeoclue0 libgeocode-glib0 libgeonames0 libgettextpo-dev
  libgettextpo0 libgl1-mesa-dri libgl1-mesa-glx libglapi-mesa libglib2.0-bin
  libgnome-bluetooth13 libgnome-desktop-3-12 libgnome-keyring-common
  libgnome-keyring0 libgnome-menu-3-0 libgnomekbd-common libgnomekbd8
  libgoa-1.0-0b libgoa-1.0-common libgphoto2-6 libgphoto2-l10n
  libgphoto2-port12 libgraphite2-3 libgstreamer-plugins-base1.0-0
  libgstreamer-plugins-good1.0-0 libgstreamer1.0-0 libgtk-3-0 libgtk-3-bin
  libgtk-3-common libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libgtop-2.0-10
  libgtop2-common libgudev-1.0-0 libgusb2 libgweather-3-6 libgweather-common
  libharfbuzz-icu0 libharfbuzz0b libhtml-parser-perl libhtml-tagset-perl
  libhttp-date-perl libhttp-message-perl libhunspell-1.3-0 libhyphen0
  libibus-1.0-5 libical1a libice6 libido3-0.1-0 libiec61883-0 libieee1284-3
  libimobiledevice6 libindicator3-7 libinput10 libio-html-perl libio-pty-perl
  libio-socket-inet6-perl libio-socket-ssl-perl libio-string-perl
  libipc-run-perl libipc-system-simple-perl libisl15 libitm1 libjack-jackd2-0
  libjansson4 libjavascriptcoregtk-4.0-18 libjbig0 libjpeg-turbo8 libjpeg8
  libjson-glib-1.0-0 libjson-glib-1.0-common liblcms2-2 libldb1
  liblightdm-gobject-1-0 liblist-moreutils-perl libllvm3.8 liblsan0 libltdl7
  liblwp-mediatypes-perl libmailtools-perl libmbim-glib4 libmbim-proxy
  libmirclient9 libmircommon5 libmirprotobuf3 libmm-glib0 libmpc3 libmpx0
  libmtdev1 libmtp-common libmtp-runtime libmtp9 libnautilus-extension1a
  libndp0 libnet-dns-perl libnet-domain-tld-perl libnet-ip-perl
  libnet-libidn-perl libnet-smtp-ssl-perl libnet-ssleay-perl libnih-dbus1
  libnm-glib4 libnm-gtk-common libnm-gtk0 libnm-util2 libnm0 libnma-common
  libnma0 libnotify4 libnspr4 libnss-mdns libnss3 libnss3-nssdb liboauth0
  libogg0 libopus0 liborc-0.4-0 libp11-kit-gnome-keyring
  libpackagekit-glib2-16 libpam-gnome-keyring libpanel-applet0 libpango-1.0-0
  libpangocairo-1.0-0 libpangoft2-1.0-0 libpangoxft-1.0-0
  libparse-debianchangelog-perl libpcre16-3 libpcsclite1 libperlio-gzip-perl
  libpixman-1-0 libplist3 libprotobuf-lite9v5 libproxy1v5
  libpulse-mainloop-glib0 libpulse0 libpulsedsp libpwquality-common
  libpwquality1 libpython2.7 libqmi-glib1 libqmi-proxy libqt5core5a
  libqt5dbus5 libqt5gui5 libqt5network5 libqt5opengl5 libqt5printsupport5
  libqt5qml5 libqt5quick5 libqt5sql5 libqt5sql5-sqlite libqt5svg5
  libqt5webkit5 libqt5widgets5 libqt5xml5 libquadmath0 libraw1394-11
  librest-0.7-0 librsvg2-2 librsvg2-common libsane libsane-common
  libsecret-1-0 libsecret-common libshout3 libsignon-extension1
  libsignon-glib1 libsignon-plugins-common1 libsignon-qt5-1 libsm6
  libsmbclient libsndfile1 libsocket6-perl libsoup-gnome2.4-1 libsoup2.4-1
  libspeex1 libspeexdsp1 libstdc++-5-dev libsub-name-perl libtag1v5
  libtag1v5-vanilla libtalloc2 libtdb1 libtevent0 libtext-levenshtein-perl
  libthai-data libthai0 libtheora0 libtiff5 libtimedate-perl
  libtimezonemap-data libtimezonemap1 libtsan0 libtxc-dxtn-s2tc0 libubsan0
  libudisks2-0 libunistring0 libunity-control-center1
  libunity-settings-daemon1 libupower-glib3 liburi-perl liburl-dispatcher1
  libusbmuxd4 libv4l-0 libv4lconvert0 libvdpau1 libvisual-0.4-0 libvorbis0a
  libvorbisenc2 libvorbisfile3 libvpx3 libwacom-bin libwacom-common libwacom2
  libwavpack1 libwayland-client0 libwayland-cursor0 libwayland-egl1-mesa
  libwayland-server0 libwbclient0 libwebkit2gtk-4.0-37
  libwebkit2gtk-4.0-37-gtk2 libwebp5 libwebrtc-audio-processing-0 libx11-xcb1
  libxaw7 libxcb-dri2-0 libxcb-dri3-0 libxcb-glx0 libxcb-icccm4 libxcb-image0
  libxcb-keysyms1 libxcb-present0 libxcb-randr0 libxcb-render-util0
  libxcb-render0 libxcb-shape0 libxcb-shm0 libxcb-sync1 libxcb-util1
  libxcb-xfixes0 libxcb-xkb1 libxcomposite1 libxcursor1 libxdamage1 libxfixes3
  libxfont1 libxft2 libxi6 libxinerama1 libxkbcommon-x11-0 libxkbcommon0
  libxkbfile1 libxklavier16 libxmu6 libxnvctrl0 libxpm4 libxrandr2 libxrender1
  libxshmfence1 libxslt1.1 libxt6 libxtst6 libxv1 libxxf86dga1 libxxf86vm1
  libyaml-libyaml-perl libyelp0 lightdm lintian linux-libc-dev make
  manpages-dev mesa-vdpau-drivers mobile-broadband-provider-info modemmanager
  mountall mousetweaks nautilus-data network-manager network-manager-gnome
  network-manager-pptp notification-daemon nvidia-340 nvidia-opencl-icd-340
  nvidia-prime nvidia-settings ocl-icd-libopencl1 p11-kit p11-kit-modules
  patchutils pinentry-gnome3 pkg-config policykit-1-gnome ppp pptp-linux
  pulseaudio pulseaudio-module-x11 pulseaudio-utils python-talloc
  python3-aptdaemon python3-aptdaemon.pkcompat python3-bs4 python3-cairo
  python3-cups python3-cupshelpers python3-defer python3-html5lib python3-lxml
  python3-xdg qttranslations5-l10n rtkit samba-libs screen-resolution-extra
  session-migration signon-keyring-extension signon-plugin-oauth2
  signon-plugin-password signon-ui signon-ui-service signon-ui-x11 signond
  sound-theme-freedesktop system-config-printer-common
  system-config-printer-gnome system-config-printer-udev t1utils ubuntu-mono
  ubuntu-system-service ubuntu-touch-sounds udisks2 unity-control-center
  unity-control-center-faces unity-control-center-signon unity-greeter
  unity-settings-daemon upower upstart usb-modeswitch usb-modeswitch-data
  usbmuxd vdpau-driver-all wamerican wpasupplicant x11-common x11-utils
  x11-xkb-utils xfonts-base xfonts-encodings xfonts-utils xserver-common
  xserver-xorg xserver-xorg-core xserver-xorg-input-all
  xserver-xorg-input-evdev xserver-xorg-input-synaptics
  xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-legacy yelp
  yelp-xsl
0 upgraded, 589 newly installed, 0 to remove and 0 not upgraded.
Need to get 266 MB of archives.
After this operation, 1,240 MB of additional disk space will be used.
Do you want to continue? [Y/n] 
```

My questions to you are below.

1. I believe I only need AMD Microcode right?
2. I don't need any Nvidia driver correct?
3. If I want to try installing Nvidia driver, but without any desktop how I would do that?

Thank you very much for all your help.

---

### Post by sethanath2 on 2017-04-26
Here is an additional information.

$ sudo ubuntu-drivers devices
== cpu-microcode.py ==
driver   : amd64-microcode - distro non-free

== /sys/devices/pci0000:00/0000:00:17.0/0000:06:00.0 ==
model    : GT218 [GeForce 210]
vendor   : NVIDIA Corporation
modalias : pci:v000010DEd00000A65sv00001043sd00008416bc03sc00i00
driver   : xserver-xorg-video-nouveau - distro free builtin
driver   : nvidia-304 - distro non-free
driver   : nvidia-340 - distro non-free recommended

---

### Post by ian-weisser on 2017-04-26
Getting a desktop after installing that package is expected behavior.

To understand the system's response, take a look at the dependencies of the nvidia-340 package.
```
apt depends nvidia-340
```

---

### Post by houstonbofh on 2017-04-26
You have some X11 and gnome installed, even if it is not running.  As far as removing, "apt-get remove" and "apt-get purge" are what you are looking for.  But it looks like you either installed the desktop version or added it later.  If this is not what you want, you may want to reinstall.

---

### Post by sethanath2 on 2017-04-26
Thanks. I will check it out.

---

### Post by Bucky Ball on 2017-04-27
> **sethanath2 said:**
> 
2. I don't need any Nvidia driver correct?

Not sure you mention which video card you have so not sure. Guess my question is, if you don't know, why are you installing that driver? :-k

Run this command in a terminal and post it back, please.

```
sudo lshw -C video
```

---

