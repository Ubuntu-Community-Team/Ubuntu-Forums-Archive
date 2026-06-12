---
title: "Unity easy install on 17.10"
date: 2017-06-26
forum: Ubuntu Development Version
---

### Post by OHD2wdc on 2017-06-26
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install unity-session

---

### Post by howefield on 2017-06-26
Thread moved to the "*Ubuntu Development Version*" forum.

Is this a question or a statement of fact ?

---

### Post by OHD2wdc on 2017-06-26
> **Qwerty Dragon said:**
> sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install unity-session

> **howefield said:**
> Thread moved to the "*Ubuntu Development Version*" forum.

Is this a question or a statement of fact ?

Took me awhile to find out how to do it best way, so I shared it here for others.

---

### Post by deadflowr on 2017-06-27
I see that unity-session is now a recommended package for unity,
so you should only need to install unity and it should automatically install the session package.
(unless you've changed your apt settings to excludes recommends.)

---

### Post by Chanath on 2017-06-27
Once Unity is reinstalled, should (or could) Gnome shell be uninstalled to get the only-Unity experience?

---

### Post by jbicha on 2017-06-27
You could but I think it's very useful to have a metapackage like ubuntu-desktop installed (especially for upgrades). No one has made a -desktop metapackage for Unity yet.

---

### Post by ventrical on 2017-06-27
Here is what I get when I install unity-session on top of Kubuntu-17.10.

```

ventrical@ventrical-Precision-WorkStation-T3400:~$ sudo apt-get install unity-session
[sudo] password for ventrical: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  apg appmenu-qt bamfdaemon cheese-common compiz compiz-core compiz-gnome
  compiz-plugins-default dbus-user-session dconf-cli desktop-file-utils
  evolution-data-server gcr geoclue geoclue-ubuntu-geoip gir1.2-accounts-1.0
  gir1.2-dbusmenu-glib-0.4 gir1.2-dee-1.0 gir1.2-gdata-0.0 gir1.2-goa-1.0
  gir1.2-ibus-1.0 gir1.2-json-1.0 gir1.2-signon-1.0 gir1.2-soup-2.4 gir1.2-unity-5.0
  gkbd-capplet gnome-bluetooth gnome-calculator gnome-desktop3-data gnome-disk-utility
  gnome-keyring gnome-menus gnome-power-manager gnome-screensaver gnome-session-bin
  gnome-session-common gnome-settings-daemon-schemas gnome-system-monitor
  gnome-user-share gsettings-ubuntu-schemas gstreamer1.0-clutter-3.0 gvfs
  gvfs-backends gvfs-common gvfs-daemons gvfs-libs hud ibus indicator-application
  indicator-appmenu indicator-bluetooth indicator-common indicator-datetime
  indicator-keyboard indicator-messages indicator-power indicator-printers
  indicator-session indicator-sound jayatana libappindicator3-1 libatkmm-1.6-1v5
  libbamf3-2 libboost-log1.62.0 libboost-regex1.62.0 libcairomm-1.0-1v5
  libcanberra-gtk3-0 libcanberra-gtk3-module libcdio-cdda1 libcdio-paranoia1
  libcheese-gtk25 libcheese8 libclutter-1.0-0 libclutter-1.0-common
  libclutter-gst-3.0-0 libclutter-gtk-1.0-0 libcogl-common libcogl-pango20
  libcogl-path20 libcogl20 libcolumbus1-common libcolumbus1v5 libcompizconfig0
  libcontent-hub0 libdbusmenu-gtk3-4 libdecoration0 libdee-1.0-4 libecal-1.2-19
  libedata-cal-1.2-28 libertine-xmir-tools libertined libexempi3 libfcitx-config4
  libfcitx-gclient0 libfcitx-utils0 libframe6 libgail-3-0 libgck-1-0 libgcr-3-common
  libgcr-base-3-1 libgcr-ui-3-1 libgdata-common libgdata22 libgee-0.8-2 libgeis1
  libgeoclue0 libgeocode-glib0 libgeonames-common libgeonames0 libgexiv2-2
  libgflags2v5 libgles2-mesa libglewmx1.13 libglibmm-2.4-1v5 libgnome-autoar-0-0
  libgnome-bluetooth13 libgnome-desktop-3-12 libgnome-menu-3-0 libgnomekbd-common
  libgnomekbd8 libgoa-1.0-0b libgoa-1.0-common libgoogle-glog0v5 libgrail6
  libgsettings-qt1 libgtkmm-3.0-1v5 libgtksourceview-3.0-1 libgtksourceview-3.0-common
  libgtop-2.0-10 libgtop2-common libgweather-3-6 libgweather-common libido3-0.1-0
  libindicator3-7 libjavascriptcoregtk-4.0-18 liblibertine1 liblightdm-gobject-1-0
  liblttng-ust-ctl2 liblttng-ust0 libmessaging-menu0 libmetacity1
  libnautilus-extension1a libnih-dbus1 libnm-gtk-common libnm-gtk0 libnma-common
  libnma0 libnux-4.0-0 libnux-4.0-common liboauth0 libp11-kit-gnome-keyring
  libpam-gnome-keyring libpangomm-1.4-1v5 libsigc++-2.0-0v5 libtimezonemap-data
  libtimezonemap1 libtracker-sparql-1.0-0 libubuntu-app-launch4
  libubuntu-download-manager-client1 libubuntu-download-manager-common1 libudm-common1
  libunity-control-center1 libunity-core-6.0-9 libunity-gtk2-parser0
  libunity-gtk3-parser0 libunity-misc4 libunity-protocol-private0
  libunity-scopes-json-def-desktop libunity-settings-daemon1 libunity9 libunwind8
  liburcu4 liburl-dispatcher1 libwebkit2gtk-4.0-37 libwnck-3-0 libwnck-3-common
  libxklavier16 libxres1 libyelp0 libzeitgeist-1.0-1 libzeitgeist-2.0-0
  metacity-common mousetweaks nautilus nautilus-data network-manager-gnome nux-tools
  p11-kit p11-kit-modules pinentry-gnome3 python3-blinker python3-bs4
  python3-cffi-backend python3-cryptography python3-feedparser python3-html5lib
  python3-httplib2 python3-idna python3-jwt python3-libertine python3-lxml
  python3-oauthlib python3-psutil python3-pyasn1 python3-setuptools
  python3-webencodings python3-xdg session-shortcuts shotwell shotwell-common
  ubuntu-app-launch ubuntu-system-service ubuntu-touch-sounds unity unity-asset-pool
  unity-control-center unity-control-center-faces unity-greeter
  unity-gtk-module-common unity-gtk2-module unity-gtk3-module unity-lens-applications
  unity-lens-files unity-lens-music unity-lens-photos unity-lens-video unity-schemas
  unity-scope-calculator unity-scope-chromiumbookmarks unity-scope-colourlovers
  unity-scope-devhelp unity-scope-firefoxbookmarks unity-scope-home
  unity-scope-manpages unity-scope-openclipart unity-scope-texdoc unity-scope-tomboy
  unity-scope-video-remote unity-scope-virtualbox unity-scope-yelp unity-scope-zotero
  unity-scopes-master-default unity-scopes-runner unity-services unity-settings-daemon
  xmir yelp yelp-xsl zeitgeist-core
Suggested packages:
  evolution apache2-bin libapache2-mod-dnssd samba-common ibus-clutter ibus-doc
  lightdm zenity unity-greeter-session-broadcast content-hub fcitx unity-common
  url-dispatcher libwebkit2gtk-4.0-37-gtk2 brasero eog gnome-sushi totem | mp3-decoder
  nautilus-sendto tracker network-manager-openconnect-gnome
  network-manager-openvpn-gnome network-manager-vpnc-gnome network-manager-pptp-gnome
  pinentry-doc python-blinker-doc python-cryptography-doc python3-cryptography-vectors
  python3-genshi python3-crypto python3-libertine-chroot python3-libertine-lxc
  python3-libertine-lxd python3-lxml-dbg python-lxml-doc python-psutil-doc doc-base
  python-setuptools-doc account-plugin-facebook account-plugin-google
  account-plugin-flickr unity-control-center-signon gnome-user-guide | ubuntu-docs
  libcanberra-gtk-module lightdm-remote-session-freerdp
  lightdm-remote-session-uccsconfigure remote-login-service tomboy gnome-user-guide
  zeitgeist-datahub
Recommended packages:
  systemd-services
The following NEW packages will be installed:
  apg appmenu-qt bamfdaemon cheese-common compiz compiz-core compiz-gnome
  compiz-plugins-default dbus-user-session dconf-cli desktop-file-utils
  evolution-data-server gcr geoclue geoclue-ubuntu-geoip gir1.2-accounts-1.0
  gir1.2-dbusmenu-glib-0.4 gir1.2-dee-1.0 gir1.2-gdata-0.0 gir1.2-goa-1.0
  gir1.2-ibus-1.0 gir1.2-json-1.0 gir1.2-signon-1.0 gir1.2-soup-2.4 gir1.2-unity-5.0
  gkbd-capplet gnome-bluetooth gnome-calculator gnome-desktop3-data gnome-disk-utility
  gnome-keyring gnome-menus gnome-power-manager gnome-screensaver gnome-session-bin
  gnome-session-common gnome-settings-daemon-schemas gnome-system-monitor
  gnome-user-share gsettings-ubuntu-schemas gstreamer1.0-clutter-3.0 gvfs
  gvfs-backends gvfs-common gvfs-daemons gvfs-libs hud ibus indicator-application
  indicator-appmenu indicator-bluetooth indicator-common indicator-datetime
  indicator-keyboard indicator-messages indicator-power indicator-printers
  indicator-session indicator-sound jayatana libappindicator3-1 libatkmm-1.6-1v5
  libbamf3-2 libboost-log1.62.0 libboost-regex1.62.0 libcairomm-1.0-1v5
  libcanberra-gtk3-0 libcanberra-gtk3-module libcdio-cdda1 libcdio-paranoia1
  libcheese-gtk25 libcheese8 libclutter-1.0-0 libclutter-1.0-common
  libclutter-gst-3.0-0 libclutter-gtk-1.0-0 libcogl-common libcogl-pango20
  libcogl-path20 libcogl20 libcolumbus1-common libcolumbus1v5 libcompizconfig0
  libcontent-hub0 libdbusmenu-gtk3-4 libdecoration0 libdee-1.0-4 libecal-1.2-19
  libedata-cal-1.2-28 libertine-xmir-tools libertined libexempi3 libfcitx-config4
  libfcitx-gclient0 libfcitx-utils0 libframe6 libgail-3-0 libgck-1-0 libgcr-3-common
  libgcr-base-3-1 libgcr-ui-3-1 libgdata-common libgdata22 libgee-0.8-2 libgeis1
  libgeoclue0 libgeocode-glib0 libgeonames-common libgeonames0 libgexiv2-2
  libgflags2v5 libgles2-mesa libglewmx1.13 libglibmm-2.4-1v5 libgnome-autoar-0-0
  libgnome-bluetooth13 libgnome-desktop-3-12 libgnome-menu-3-0 libgnomekbd-common
  libgnomekbd8 libgoa-1.0-0b libgoa-1.0-common libgoogle-glog0v5 libgrail6
  libgsettings-qt1 libgtkmm-3.0-1v5 libgtksourceview-3.0-1 libgtksourceview-3.0-common
  libgtop-2.0-10 libgtop2-common libgweather-3-6 libgweather-common libido3-0.1-0
  libindicator3-7 libjavascriptcoregtk-4.0-18 liblibertine1 liblightdm-gobject-1-0
  liblttng-ust-ctl2 liblttng-ust0 libmessaging-menu0 libmetacity1
  libnautilus-extension1a libnih-dbus1 libnm-gtk-common libnm-gtk0 libnma-common
  libnma0 libnux-4.0-0 libnux-4.0-common liboauth0 libp11-kit-gnome-keyring
  libpam-gnome-keyring libpangomm-1.4-1v5 libsigc++-2.0-0v5 libtimezonemap-data
  libtimezonemap1 libtracker-sparql-1.0-0 libubuntu-app-launch4
  libubuntu-download-manager-client1 libubuntu-download-manager-common1 libudm-common1
  libunity-control-center1 libunity-core-6.0-9 libunity-gtk2-parser0
  libunity-gtk3-parser0 libunity-misc4 libunity-protocol-private0
  libunity-scopes-json-def-desktop libunity-settings-daemon1 libunity9 libunwind8
  liburcu4 liburl-dispatcher1 libwebkit2gtk-4.0-37 libwnck-3-0 libwnck-3-common
  libxklavier16 libxres1 libyelp0 libzeitgeist-1.0-1 libzeitgeist-2.0-0
  metacity-common mousetweaks nautilus nautilus-data network-manager-gnome nux-tools
  p11-kit p11-kit-modules pinentry-gnome3 python3-blinker python3-bs4
  python3-cffi-backend python3-cryptography python3-feedparser python3-html5lib
  python3-httplib2 python3-idna python3-jwt python3-libertine python3-lxml
  python3-oauthlib python3-psutil python3-pyasn1 python3-setuptools
  python3-webencodings python3-xdg session-shortcuts shotwell shotwell-common
  ubuntu-app-launch ubuntu-system-service ubuntu-touch-sounds unity unity-asset-pool
  unity-control-center unity-control-center-faces unity-greeter
  unity-gtk-module-common unity-gtk2-module unity-gtk3-module unity-lens-applications
  unity-lens-files unity-lens-music unity-lens-photos unity-lens-video unity-schemas
  unity-scope-calculator unity-scope-chromiumbookmarks unity-scope-colourlovers
  unity-scope-devhelp unity-scope-firefoxbookmarks unity-scope-home
  unity-scope-manpages unity-scope-openclipart unity-scope-texdoc unity-scope-tomboy
  unity-scope-video-remote unity-scope-virtualbox unity-scope-yelp unity-scope-zotero
  unity-scopes-master-default unity-scopes-runner unity-services unity-session
  unity-settings-daemon xmir yelp yelp-xsl zeitgeist-core
0 upgraded, 250 newly installed, 0 to remove and 0 not upgraded.
Need to get 58.9 MB of archives.
After this operation, 216 MB of additional disk space will be used.
Do you want to continue? [Y/n] 

```

---

### Post by ventrical on 2017-06-27
Which was a complete fail. Unity looks like a dogs-breakfast :)

Regards..

---

### Post by ventrical on 2017-06-27
> **jbicha said:**
> You could but I think it's very useful to have a metapackage like ubuntu-desktop installed (especially for upgrades). No one has made a -desktop metapackage for Unity yet.

Without maintainers and patches it will surely break, or it will break GNOME. But there might be another way.

Regards..

---

### Post by Frogs Hair on 2017-06-28
I have Budgie installation with a unity-session running . The file's menu is duplicated in the global menu , but other than that it works.

---

