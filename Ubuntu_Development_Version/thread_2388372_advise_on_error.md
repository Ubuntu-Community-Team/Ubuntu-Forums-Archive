---
title: "advise on error"
date: 2018-04-01
forum: Ubuntu Development Version
---

### Post by rburkartjo on 2018-04-01
trying to upgrade ubuntu 16.04 to 18.04. had a freeze up and had to do a hard reboot. now i have no gnome enviroment and get this message
```
ray@nightmare:~$ sudo apt-get install update-manager-core
[sudo] password for ray: 
Sorry, try again.
[sudo] password for ray: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
update-manager-core is already the newest version (1:18.04.10).
update-manager-core set to manually installed.
The following packages were automatically installed and are no longer required:
  account-plugin-facebook account-plugin-flickr account-plugin-google
  activity-log-manager breeze-cursor-theme cgmanager compton-conf-l10n
  elementary-icon-theme empathy-common enca esound-common espeak-data
  evolution-data-server-online-accounts exe-thumbnailer flashplugin-installer
  fonts-hack fonts-hack-ttf fonts-horai-umefont fonts-mathjax fonts-stix
  fonts-unfonts-core g++-5 galternatives gcc-5-base:i386 gcc-6-base
  gcc-6-base:i386 gir1.2-gkbd-3.0 gir1.2-networkmanager-1.0 gir1.2-nmgtk-1.0
  gir1.2-panelapplet-5.0 gir1.2-rb-3.0 gnome-exe-thumbnailer gnome-tweak-tool
  gnuplot-tex gtk3-engines-unico gtk3-nocsd gxmessage hardening-includes
  hwdata icoutils imagemagick-common kactivities-bin kate-data katepart
  kde-runtime-data kde-style-qtcurve-qt4 kdegames-mahjongg-data-kf5
  kdelibs-bin kdelibs5-data kdelibs5-plugins kdoctools kdoctools5
  kpackagetool5 kwayland-data lib32z1 libaccount-plugin-1.0-0
  libaccount-plugin-facebook libaccount-plugin-flickr
  libaccount-plugin-generic-oauth libaccount-plugin-google libaccounts-qt5-1
  libamd2.4.1 libandroid-properties1 libapparmor-perl libappstream3
  libaribb24-0 libasn1-8-heimdal:i386 libasound2:i386 libasound2-plugins:i386
  libass5 libasyncns0:i386 libattica0.4 libaudcore3 libaudgui3 libaudiofile1
  libaudtag2 libautodie-perl libavahi-gobject0 libavcodec-ffmpeg-extra56
  libavdevice-ffmpeg56 libavfilter-ffmpeg5 libavformat-ffmpeg56
  libavresample-ffmpeg2 libavutil-ffmpeg54 libbabeltrace-ctf1
  libbasicusageenvironment1 libbfio1 libbind9-140 libbinio1v5 libblas-common
  libbluray1 libboost-date-time1.58.0 libboost-filesystem1.58.0
  libboost-iostreams1.58.0 libboost-python1.58.0 libboost-python1.65.1
  libboost-random1.58.0 libboost-system1.58.0 libboost-thread1.58.0
  libcamd2.4.1 libcamel-1.2-54 libcap2:i386 libcapi20-3:i386 libcapnp-0.5.3
  libcapnp-0.6.1 libccolamd2.9.1 libcdio-cdda1 libcdio-paranoia1 libcdio13
  libcdparanoia0:i386 libchm1 libcholmod3.0.6 libchromaprint0 libcloog-isl4
  libclutter-gst-2.0-0 libcolamd2.9.1 libcrypto++9v5 libcryptui0a
  libdata-alias-perl libde265-0 libdirectfb-1.2-9 libdlrestrictions1
  libdns-export162 libdns162 libdrm-amdgpu1:i386 libdrm-intel1:i386
  libdrm-nouveau2:i386 libdrm-radeon1:i386 libdrm2:i386 libdvbpsi10 libebml4v5
  libebook-1.2-16 libechonest2.3 libedataserver-1.2-21 libedataserverui-1.2-1
  libedit2:i386 libefivar0 libelf1:i386 libesd0 libespeak1 libetpan17
  libevent-2.0-5 libexif12:i386 libextutils-depends-perl
  libextutils-pkgconfig-perl libfam0 libfcitx-gclient0 libfcitx-qt0
  libflac8:i386 libfm-qt-l10n libfolks-telepathy25 libfreerdp-cache1.1
  libfreerdp-client1.1 libfreerdp-codec1.1 libfreerdp-common1.1.0
  libfreerdp-core1.1 libfreerdp-crypto1.1 libfreerdp-gdi1.1
  libfreerdp-locale1.1 libfreerdp-plugins-standard libfreerdp-primitives1.1
  libfreerdp-utils1.1 libfwup0 libfwupd1 libgcr-3-common libgd3:i386
  libgeonames-common libgeonames0 libgfortran3 libgif7:i386
  libgl1-mesa-dri:i386 libgl1-mesa-glx:i386 libglapi-mesa:i386 libglew1.13
  libglu1-mesa:i386 libgmime-2.6-0 libgnome-autoar-gtk-0-0
  libgnome-desktop-3-12 libgom-1.0-common libgoocanvas-common libgoocanvas3
  libgpgme++2v5 libgphoto2-6:i386 libgphoto2-port12:i386
  libgrantlee-templates5 libgrilo-0.2-1 libgroupsock8 libgsettings-qt1
  libgsm1:i386 libgsoap8 libgssapi3-heimdal:i386 libgstreamer-plugins-bad1.0-0
  libgtk3-nocsd0 libgtkspell3-3-0 libgtop-2.0-10 libguess1 libgweather-3-6
  libhardware2 libhcrypto4-heimdal:i386 libheimbase1-heimdal:i386
  libheimntlm0-heimdal:i386 libhfstospell9 libhud2 libhunspell-1.3-0
  libhx509-5-heimdal:i386 libhybris libhybris-common1 libical1a libice6:i386
  libicu55:i386 libicu60:i386 libidn11:i386 libieee1284-3:i386
  libisc-export160 libisc160 libisccc140 libisccfg140 libiscsi2 libiso9660-8
  libjack-jackd2-0:i386 libjasper1 libjs-coffeescript libjs-mathjax
  libjs-sphinxdoc libjs-underscore libjson-c2:i386 libkactivities6 libkate1
  libkatepartinterfaces4 libkcmutils4 libkde3support4 libkdeclarative5
  libkdecore5 libkdesu5 libkdeui5 libkdewebkit5 libkdnssd4 libkemoticons4
  libkf5activities5 libkf5archive5 libkf5attica5 libkf5auth-data
  libkf5bookmarks-data libkf5calendarevents5 libkf5codecs-data libkf5codecs5
  libkf5completion-data libkf5config-bin libkf5config-data libkf5configcore5
  libkf5configwidgets-data libkf5coreaddons-data libkf5coreaddons5
  libkf5dbusaddons-bin libkf5dbusaddons-data libkf5declarative-data
  libkf5doctools5 libkf5globalaccel-data libkf5gpgmepp5 libkf5i18n-data
  libkf5i18n5 libkf5iconthemes-data libkf5itemviews-data libkf5jobwidgets-data
  libkf5js5 libkf5kcmutils-data libkf5kdegames-data libkf5kdelibs4support-data
  libkf5khtml-data libkf5kiontlm5 libkf5kmahjongglib-data libkf5newstuff-data
  libkf5notifications-data libkf5package-data libkf5package5 libkf5parts-data
  libkf5service-data libkf5solid5-data libkf5sonnet5-data libkf5sonnetcore5
  libkf5textwidgets-data libkf5wallet-data libkf5widgetsaddons-data
  libkf5windowsystem-data libkf5xmlgui-bin libkf5xmlgui-data libkfile4
  libkhtml5 libkio5 libkjsapi4 libkjsembed4 libkmediaplayer4 libknewstuff3-4
  libknotifyconfig4 libkntlm4 libkparts4 libkpty4 libkrb5-26-heimdal:i386
  libkrosscore4 libktexteditor4 libkxmlrpcclient4 liblcms2-2:i386
  libldap-2.4-2:i386 liblilv-0-0 liblink-grammar4 liblivemedia50
  liblivemedia62 libllvm3.6v5 libllvm5.0:i386 liblnk-utils liblnk1 liblouis9
  liblouisutdml6 libltdl7:i386 liblwres141 liblxqt-data liblxqt-globalkeys0
  liblxqt-l10n libmatroska6v5 libmedia1 libmicrodns0 libmimic0 libminizip1
  libmirclient9 libmircommon7 libmircore1 libmirprotobuf3
  libmission-control-plugins0 libmjpegutils-2.1-0 libmozjs-24-0v5
  libmpeg2encpp-2.1-0 libmpfr4 libmpg123-0:i386 libmplex2-2.1-0 libmsi0
  libmuparser2v5 libnfs8 libnm-glib-vpn1 libnm-gtk-common libnm-gtk0
  libnma-common libntrack-qt4-1 libntrack0 libodbc1:i386 libofa0 libogg0:i386
  libonig2 libopenal1:i386 libopencc1 libopencv-calib3d2.4v5
  libopencv-contrib2.4v5 libopencv-core2.4v5 libopencv-features2d2.4v5
  libopencv-flann2.4v5 libopencv-highgui2.4v5 libopencv-imgproc2.4v5
  libopencv-legacy2.4v5 libopencv-ml2.4v5 libopencv-objdetect2.4v5
  libopencv-video2.4v5 libopenjpeg5 libopenmpt-modplug1 libopus0:i386
  liborc-0.4-0:i386 liborcus-0.10-0v5 libosmesa6:i386 libp11-kit-gnome-keyring
  libpanel-applet0 libpcap0.8:i386 libpciaccess0:i386 libphonon4 libplacebo4
  libplasma3 libpng12-0:i386 libpodofo0.9.3 libpodofo0.9.5 libpolkit-qt-1-1
  libpoppler58 libpostproc-ffmpeg53 libprocps4 libprotobuf-lite10
  libprotobuf-lite9v5 libprotobuf9v5 libproxy-tools libpst4 libpulse0:i386
  libqca2 libqca2-plugins libqhull7 libqpdf17 libqt4-qt3support libqt5clucene5
  libqt5dbus5 libqt5network5 libqt5organizer5 libqt5positioning5 libqt5qml5
  libqt5scintilla2-l10n libqt5script5 libqt5sensors5 libqt5sql5
  libqt5sql5-sqlite libqt5test5 libqt5texttospeech5 libqt5webchannel5
  libqt5webengine-data libqt5xml5 libqtcurve-utils2 libqtwebkit4
  libquvi-scripts libquvi7 libraw15 libre2-4 librecode0 libreoffice-gtk
  libreoffice-gtk2 libreoffice-style-human libresid-builder0c2a
  libroken18-heimdal:i386 librpm3 librpmbuild3 librpmio3 librpmsign3
  libsamplerate0:i386 libsane1:i386 libsasl2-2:i386 libsasl2-modules:i386
  libsasl2-modules-db:i386 libschroedinger-1.0-0 libsensors4:i386 libserd-0-0
  libsidplay2 libsignon-extension1 libsignon-plugins-common1 libsignon-qt5-1
  libsm6:i386 libsndfile1:i386 libsndio6.1:i386 libsodium18 libsolid4
  libsord-0-0 libsoundtouch1 libspandsp2 libspeexdsp1:i386 libsqlite3-0:i386
  libsratom-0-0 libsrtp0 libsrtp2-1 libssh2-1 libssl1.0.0:i386 libssl1.1:i386
  libstatgrab10 libstdc++6:i386 libstreamanalyzer0v5 libstreams0v5
  libsub-identify-perl libsuitesparseconfig4.4.6 libswresample-ffmpeg1
  libswscale-ffmpeg3 libsysstat-qt5-0 libtbb2 libtelepathy-farstream3
  libtheora0:i386 libthreadweaver4 libtidy-0.99-0 libtorrent-rasterbar8
  libtorrent-rasterbar9 libtracker-control-1.0-0 libtracker-miner-1.0-0
  libtracker-sparql-1.0-0 libumfpack5.7.1 libunistring0 libunity-action-qt1
  libupnp6 libusageenvironment3 libusb-1.0-0:i386 libutf8proc2 libv4l-0:i386
  libv4lconvert0:i386 libva-drm1 libva-egl1 libva-glx1 libva-tpi1
  libva-wayland1 libva-x11-1 libva1 libvisual-0.4-0:i386 libvlc-bin libvlc5
  libvlccore9 libvo-aacenc0 libvoikko1 libvorbis0a:i386 libvorbisenc2:i386
  libvpx3 libvpx3:i386 libvte-common libvte9 libvulkan1 libwebp5 libwebp6:i386
  libwebpmux1 libwebrtc-audio-processing-0 libwildmidi-config libwildmidi1
  libwildmidi2 libwind0-heimdal:i386 libwinpr-crt0.1 libwinpr-dsparse0.1
  libwinpr-environment0.1 libwinpr-file0.1 libwinpr-handle0.1 libwinpr-heap0.1
  libwinpr-input0.1 libwinpr-interlocked0.1 libwinpr-library0.1
  libwinpr-path0.1 libwinpr-pool0.1 libwinpr-registry0.1 libwinpr-rpc0.1
  libwinpr-sspi0.1 libwinpr-synch0.1 libwinpr-sysinfo0.1 libwinpr-thread0.1
  libwinpr-utils0.1 libwrap0:i386 libx11-xcb1:i386 libx264-148 libx265-79
  libxapian-1.3-5 libxapian22v5 libxcb-composite0 libxcb-damage0 libxcb-dpms0
  libxcb-dri2-0:i386 libxcb-dri3-0:i386 libxcb-glx0:i386 libxcb-present0:i386
  libxcb-screensaver0 libxcb-sync1:i386 libxcb-xf86dri0 libxcb-xinerama0
  libxen-4.6 libxfont1 libxml2:i386 libxpm4:i386 libxshmfence1:i386
  libxslt1.1:i386 libxt6:i386 libxtables11 libxxf86vm1:i386 libytnef0 libzbar0
  linux-tools-4.4.0-117 linux-tools-4.4.0-117-generic linux-tools-4.4.0-118
  linux-tools-4.4.0-118-generic lubuntu-artwork-16-04 luckybackup-data
  lximage-qt-l10n lxqt-about-l10n lxqt-admin-l10n lxqt-config-l10n
  lxqt-globalkeys-l10n lxqt-notificationd-l10n lxqt-openssh-askpass-l10n
  lxqt-panel-l10n lxqt-policykit-l10n lxqt-powermanagement-l10n
  lxqt-runner-l10n lxqt-session-l10n lxqt-sudo-l10n lxqt-system-theme
  lxqt-themes mate-tweak msitools nautilus-scripts-manager
  ntrack-module-libnl-0 obconf-qt-l10n ocl-icd-libopencl1:i386 odbcinst
  odbcinst1debian2 oneconf oneconf-common oxygen5-icon-theme
  p11-kit-modules:i386 palapeli-data pcmanfm-qt-l10n perlmagick phonon
  phonon-backend-gstreamer phonon-backend-gstreamer-common
  plainbox-provider-checkbox plainbox-provider-resource-generic
  plainbox-secure-policy plasma-scriptengine-javascript python-apsw
  python-beautifulsoup python-cherrypy3 python-configparser python-cssselect
  python-cssutils python-cups python-dateutil python-debtagshw
  python-dnspython python-feedparser python-future python-gflags
  python-googleapi python-html5-parser python-keybinder python-keyring
  python-keyrings.alt python-libxml2 python-markdown python-mechanize
  python-msgpack python-ndg-httpsclient python-netifaces python-oauth2client
  python-oneconf python-parsedatetime python-piston-mini-client python-pyatspi
  python-pyexiv2 python-pyexiv2-doc python-pygments python-pyparsing
  python-regex python-repoze.lru python-routes python-rsa python-secretstorage
  python-sqlalchemy python-sqlalchemy-ext python-tz python-uritemplate
  python-utidylib python-vobject python-webob python-wnck python-xapian
  python-yaml python3-checkbox-support python3-dbus.mainloop.pyqt5
  python3-guacamole python3-jinja2 python3-libarchive-c python3-libnacl
  python3-magic python3-mako python3-markupsafe python3-oneconf python3-padme
  python3-piston-mini-client python3-plainbox python3-polib python3-psutil
  python3-pycurl python3-pylast python3-pyparsing python3-xlsxwriter qhull-bin
  qml-module-qt-labs-folderlistmodel qml-module-qt-labs-settings
  qml-module-qtqml-models2 qtdeclarative5-unity-action-plugin qterminal-l10n
  qtermwidget5-data rename seahorse-daemon signon-keyring-extension
  signon-plugin-oauth2 signon-plugin-password signon-ui-service signond
  smartmontools snapd-login-service software-center-aptdaemon-plugins
  sonnet-plugins suru-icon-theme tcpd telepathy-gabble telepathy-haze
  telepathy-logger telepathy-mission-control-5 telepathy-salut
  ttf-wqy-microhei ubuntu-mobile-icons ubuntu-ui-toolkit-theme
  unity-scope-gdrive unixodbc variety-slideshow vlc-bin vlc-data vlc-l10n
  vlc-plugin-base vlc-plugin-notify vlc-plugin-samba vlc-plugin-video-splitter
  vlc-plugin-visualization wine-gecko2.21 wine-gecko2.21:i386 wine-mono0.0.8
  wine1.6-amd64 xfwm4-theme-breeze
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 14 not upgraded.
ray@nightmare:~$ 
```
any idea how to fix/tks  dont want to remove

---

### Post by rburkartjo on 2018-04-01
still get the same message if run
sudo apt-get install ubuntu-gnome-desktop
sudo apt-get install gnome-shell

in terminal

---

### Post by westie457 on 2018-04-01
Hi, there is two ways I know of to fix this.

1, Boot the system to Grub and select 'recovery mode' then 'drop to a root shell' then 'Enter for maintenance'.
    In the root shell run ```
dpkg --configure -a
#followed by 
apt install -f
reboot
```
Repeat until the terminal returns a clear line

2, Boot the system and at the log in screen press Ctrl+Alt+F1 for a tty terminal and run the above commands using 'Sudo'

Reboot one more time to the normal system open a terminal ```
sudo apt update
sudo apt dist-upgrade
```
Hopefully you should now have cleared all errors and have a working system.

For completeness you can run the commands you tried previously.

---

### Post by westie457 on 2018-04-01
The dist-upgrade command might need changing to full-upgrade.

---

### Post by dino99 on 2018-04-02
Instead of trying to install/upgrade metapackage/app, choose the soft way step by step:

First step: upgrade the language: cpp g++  python-minimal  python3-minimal curl  perl ...
also continue with the tools: apt dpkg bash dash bc ...
then followed by the default config: ubuntu-minimal/standard, unattended-upgrades ubuntu-restricted*

Second step: main libs, like gvfs apparmor policykit ...
Third step: main tools, like systemd* network*  xserver* cups* ...

If you get a conflict/circular dependency error, then ignore it and continue upgrading the other package/app. Also purge the orphaned ones, that will help resolve the conflicts.
At that point, the still not yet upgraded packages should accept a dist-upgrade.

---

### Post by rburkartjo on 2018-04-03
update i got xubuntu to work now i have it and lubuntu to log in. still cant log into any any gnome session. get returned to the log in screen when i try. try removing .Xauthority to no avail.  any suggestions.

---

### Post by dino99 on 2018-04-03
journalctl -b might help you find the reason(s)

---

### Post by rburkartjo on 2018-04-04
what would happen if i used the ubuntu sources list generator  [https://repogen.simplylinux.ch/index.php](https://repogen.simplylinux.ch/index.php) and set it to 18.04 replacing mine

---

### Post by mc4man on 2018-04-04
why not just run autoremove, then install whatever previous apps you still want to use.?

In terms of your first post it seems several apps didn't survive  your upgrade, that why their dependencies or recommends are marked for autoremove.

As far as ubuntu specific gnome packakages - 
```
sudo apt purge ubuntu-desktop
```
followed by
```
sudo apt install ubuntu-desktop
```

---

### Post by rburkartjo on 2018-04-05
mc tks but didnt work still can only log into lubuntu or xubuntu session

---

### Post by rburkartjo on 2018-04-10
do you think i might have a permission problem because i just noticed that i can log into a gnome flashback metacity session
but not a flashback compiz session.

---

### Post by rburkartjo on 2018-04-14
if i open xsessions folder i can launch xubuntu lubuntu or flashback metacity but not any others.it appears all the exes have the same permissons. any ideas?

---

### Post by mc4man on 2018-04-14
while you should probably start a new thread on whatever your new issue is what's this show?
```
ls /usr/share/xsessions
```

Edit; as far as "i can log into a gnome flashback metacity session but not a flashback compiz session. " does that mean the option exists but nothing happens or there is no option?
If the later then install compiz.

---

### Post by rburkartjo on 2018-04-15
mc good idea will start new thread after final 18.04

here is output
ls /usr/share/xsessions
gnome.desktop                     LXLE-OSX.desktop
gnome-flashback-compiz.desktop    LXLE-Unity.desktop
gnome-flashback-metacity.desktop  lxqt.desktop
gnome-xorg.desktop                mate.desktop
kodi.desktop                      openbox.desktop
Lubuntu.desktop                   QLubuntu.desktop
Lubuntu-Netbook.desktop           ubuntu-communitheme-snap.desktop
lubuntu-nexus7.desktop            ubuntu.desktop
LXDE.desktop                      unity.desktop
lxgames.desktop                   xbmc.desktop
LXLE-G2.desktop

---

### Post by mc4man on 2018-04-15
If you've managed to run 20 sessions from a single install without issue in 16.04 & now unable to after a semi broken upgrade to 18.04 maybe try a fresh 18.04 install & see if you can add/run these 20 sessions.
(the 21st session is an added theme testing for 18.04.

---

### Post by rburkartjo on 2018-04-15
mc good advise this install is on my testing partition. just want to figure out for the h--- of it how to fix.  tks just old and stubborn.

---

