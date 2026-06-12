---
title: "Why is bluez tied to the hip of gdm?"
date: 2013-09-18
forum: Ubuntu Development Version
---

### Post by VMC on 2013-09-18
I was hoping that it only removed meta files...it didn't. The first time I did this, I didn't realize gdm was gone, and I booted to a terminal and noticed that gdm failed to launch.

Here's my question, aside from compiling my own gdm, how come "gdm gets the bluez". Is there another display manager that can carry the load without bluez; lightdm perhaps?

```
sudo apt-get purge bluez

The following packages will be REMOVED:
  bluez* bluez-alsa* bluez-gstreamer* **gdm*** gnome-bluetooth* **gnome-shell***
  gnome-shell-extensions* gnome-user-share* ubuntu-gnome-desktop*


Removing ubuntu-gnome-desktop ...
Removing gnome-shell-extensions ...
Removing gnome-user-share ...
Purging configuration files for gnome-user-share ...
Removing bluez-gstreamer ...
Removing bluez-alsa:amd64 ...
Removing gdm ...
Purging configuration files for gdm ...
Removing user `gdm' ...
Warning: group `gdm' has no more members.


Removing gnome-shell ...
Removing gnome-bluetooth ...
Purging configuration files for gnome-bluetooth ...
Removing bluez ...
bluetooth stop/waiting
Purging configuration files for bluez ...
cat: /etc/init/bluetooth.override: No such file or directory
Processing triggers for libglib2.0-0:amd64 ...
Processing triggers for gnome-menus ...
Processing triggers for desktop-file-utils ...
Processing triggers for mime-support ...
Processing triggers for gconf2 ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for man-db ...
Wed Sep 18 
$ gdm
The program 'gdm' is currently not installed. You can install it by typing:
sudo apt-get install gdm
Wed Sep 18 
$ **sudo apt-get install gdm**


The following extra packages will be installed:
  bluez gnome-bluetooth gnome-shell gnome-user-share
Suggested packages:
  bluez-hcidump gnome-orca apache2.2-bin libapache2-mod-dnssd
The following NEW packages will be installed:
  bluez gdm gnome-bluetooth gnome-shell gnome-user-share
```

---

### Post by VMC on 2013-09-18
Edit: So much for Lightdm being "lighter" than gdm:
```
 sudo apt-get install lightdmReading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  account-plugin-facebook account-plugin-flickr account-plugin-google
  account-plugin-twitter appmenu-qt appmenu-qt5 bamfdaemon bluez compiz
  compiz-core compiz-gnome compiz-plugins-default firefox freerdp-x11 friends
  friends-dispatcher friends-facebook friends-twitter geoclue-ubuntu-geoip
  gir1.2-accounts-1.0 gir1.2-ebook-1.2 gir1.2-ebookcontacts-1.2
  gir1.2-edataserver-1.2 gir1.2-messagingmenu-1.0 gir1.2-signon-1.0
  gnome-control-center-datetime gnome-control-center-signon
  gnome-control-center-unity gnome-power-manager gnome-screensaver
  gsettings-ubuntu-touch-schemas hud indicator-applet indicator-appmenu
  indicator-bluetooth indicator-datetime indicator-keyboard indicator-messages
  indicator-power indicator-printers indicator-session indicator-sound
  libaccount-plugin-1.0-0 libaccount-plugin-generic-oauth
  libaccount-plugin-google libaccounts-qt5-1 libandroid-properties1 libaudio2
  libbamf3-2 libcolumbus1 libcolumbus1-common libcompizconfig0 libcontent-hub0
  libdbusmenu-qt2 libdbusmenu-qt5 libdecoration0 libfreerdp-plugins-standard
  libfreerdp1 libfriends0 libglew1.8 libglewmx1.8 libgsettings-qt1
  libhud-client2 libhud2 liblightdm-gobject-1-0 libmessaging-menu0
  libmetacity-private0a libmng1 libmysqlclient18 libnux-4.0-0
  libnux-4.0-common libofono-qt1 libpam-freerdp libpanel-applet-4-0
  libpocketsphinx1 libqt4-dbus libqt4-declarative libqt4-network libqt4-script
  libqt4-sql libqt4-sql-mysql libqt4-xml libqt4-xmlpatterns libqt53d5
  libqt5core5 libqt5dbus5 libqt5gui5 libqt5location5 libqt5multimedia5
  libqt5multimediaquick-p5 libqt5network5 libqt5opengl5 libqt5organizer5
  libqt5printsupport5 libqt5qml-graphicaleffects libqt5qml5 libqt5quick5
  libqt5sensors5 libqt5sql5 libqt5sql5-sqlite libqt5svg5 libqt5systeminfo5
  libqt5test5 libqt5v8-5 libqt5webkit5 libqt5widgets5 libqt5xml5 libqtcore4
  libqtgui4 libsignon-extension1 libsignon-plugins-common1 libsignon-qt5-1
  libsphinxbase1 libsystemsettings1 libtimezonemap1 libunity-action-qt1
  libunity-core-6.0-7 libunity-gtk2-parser0 libunity-gtk3-parser0
  libunity-misc4 libunity-protocol-private0 libunity-webapps0
  libupstart-app-launch1 libupstart1 libwhoopsie-preferences0 libwnck-common
  libwnck22 libxcb-icccm4 libxcb-image0 libxcb-keysyms1 libxcb-randr0
  libxcb-render-util0 libxcb-sync0 lightdm-remote-session-freerdp
  lightdm-remote-session-uccsconfigure metacity-common mysql-common nux-tools
  python-gconf python3-feedparser python3-gnupg python3-lxml qdbus qtchooser
  qtdeclarative5-accounts-plugin qtdeclarative5-folderlistmodel-plugin
  qtdeclarative5-gsettings1.0 qtdeclarative5-qtmultimedia-plugin
  qtdeclarative5-qtquick2-plugin qtdeclarative5-systeminfo-plugin
  qtdeclarative5-ubuntu-content0.1 qtdeclarative5-ubuntu-ui-toolkit-plugin
  qtdeclarative5-unity-action-plugin qtdeclarative5-window-plugin
  remote-login-service signon-keyring-extension signon-plugin-oauth2 signon-ui
  signond sphinx-voxforge-hmm-en sphinx-voxforge-lm-en system-image-common
  system-image-dbus thin-client-config-agent ubuntu-mobile-icons
  ubuntu-system-settings ubuntu-system-settings-online-accounts
  ubuntu-ui-toolkit-theme unity unity-asset-pool unity-greeter
  unity-gtk-module-common unity-gtk2-module unity-gtk3-module
  unity-lens-applications unity-lens-files unity-lens-friends unity-lens-music
  unity-lens-photos unity-lens-video unity-scope-audacious
  unity-scope-calculator unity-scope-chromiumbookmarks unity-scope-clementine
  unity-scope-colourlovers unity-scope-devhelp unity-scope-firefoxbookmarks
  unity-scope-gdrive unity-scope-gmusicbrowser unity-scope-gourmet
  unity-scope-guayadeque unity-scope-home unity-scope-manpages
  unity-scope-musicstores unity-scope-musique unity-scope-openclipart
  unity-scope-texdoc unity-scope-tomboy unity-scope-video-remote
  unity-scope-virtualbox unity-scope-yelp unity-scope-zotero
  unity-scopes-master-default unity-scopes-runner unity-services
  unity-webapps-service whoopsie-preferences
Suggested packages:
  bluez-hcidump ttf-lyx nas glew-utils libqt4-declarative-folderlistmodel
  libqt4-declarative-gestures libqt4-declarative-particles
  libqt4-declarative-shaders qt4-qmlviewer libqt4-dev qt4-qtconfig
  python-gnome2-doc python3-lxml-dbg qt4-default qt5-default audacious
  clementine gmusicbrowser guayadeque musique tomboy webbrowser-app
The following NEW packages will be installed:
  account-plugin-facebook account-plugin-flickr account-plugin-google
  account-plugin-twitter appmenu-qt appmenu-qt5 bamfdaemon bluez compiz
  compiz-core compiz-gnome compiz-plugins-default firefox freerdp-x11 friends
  friends-dispatcher friends-facebook friends-twitter geoclue-ubuntu-geoip
  gir1.2-accounts-1.0 gir1.2-ebook-1.2 gir1.2-ebookcontacts-1.2
  gir1.2-edataserver-1.2 gir1.2-messagingmenu-1.0 gir1.2-signon-1.0
  gnome-control-center-datetime gnome-control-center-signon
  gnome-control-center-unity gnome-power-manager gnome-screensaver
  gsettings-ubuntu-touch-schemas hud indicator-applet indicator-appmenu
  indicator-bluetooth indicator-datetime indicator-keyboard indicator-messages
  indicator-power indicator-printers indicator-session indicator-sound
  libaccount-plugin-1.0-0 libaccount-plugin-generic-oauth
  libaccount-plugin-google libaccounts-qt5-1 libandroid-properties1 libaudio2
  libbamf3-2 libcolumbus1 libcolumbus1-common libcompizconfig0 libcontent-hub0
  libdbusmenu-qt2 libdbusmenu-qt5 libdecoration0 libfreerdp-plugins-standard
  libfreerdp1 libfriends0 libglew1.8 libglewmx1.8 libgsettings-qt1
  libhud-client2 libhud2 liblightdm-gobject-1-0 libmessaging-menu0
  libmetacity-private0a libmng1 libmysqlclient18 libnux-4.0-0
  libnux-4.0-common libofono-qt1 libpam-freerdp libpanel-applet-4-0
  libpocketsphinx1 libqt4-dbus libqt4-declarative libqt4-network libqt4-script
  libqt4-sql libqt4-sql-mysql libqt4-xml libqt4-xmlpatterns libqt53d5
  libqt5core5 libqt5dbus5 libqt5gui5 libqt5location5 libqt5multimedia5
  libqt5multimediaquick-p5 libqt5network5 libqt5opengl5 libqt5organizer5
  libqt5printsupport5 libqt5qml-graphicaleffects libqt5qml5 libqt5quick5
  libqt5sensors5 libqt5sql5 libqt5sql5-sqlite libqt5svg5 libqt5systeminfo5
  libqt5test5 libqt5v8-5 libqt5webkit5 libqt5widgets5 libqt5xml5 libqtcore4
  libqtgui4 libsignon-extension1 libsignon-plugins-common1 libsignon-qt5-1
  libsphinxbase1 libsystemsettings1 libtimezonemap1 libunity-action-qt1
  libunity-core-6.0-7 libunity-gtk2-parser0 libunity-gtk3-parser0
  libunity-misc4 libunity-webapps0 libupstart-app-launch1 libupstart1
  libwhoopsie-preferences0 libwnck-common libwnck22 libxcb-icccm4
  libxcb-image0 libxcb-keysyms1 libxcb-randr0 libxcb-render-util0 libxcb-sync0
  lightdm lightdm-remote-session-freerdp lightdm-remote-session-uccsconfigure
  metacity-common mysql-common nux-tools python-gconf python3-feedparser
  python3-gnupg python3-lxml qdbus qtchooser qtdeclarative5-accounts-plugin
  qtdeclarative5-folderlistmodel-plugin qtdeclarative5-gsettings1.0
  qtdeclarative5-qtmultimedia-plugin qtdeclarative5-qtquick2-plugin
  qtdeclarative5-systeminfo-plugin qtdeclarative5-ubuntu-content0.1
  qtdeclarative5-ubuntu-ui-toolkit-plugin qtdeclarative5-unity-action-plugin
  qtdeclarative5-window-plugin remote-login-service signon-keyring-extension
  signon-plugin-oauth2 signon-ui signond sphinx-voxforge-hmm-en
  sphinx-voxforge-lm-en system-image-common system-image-dbus
  thin-client-config-agent ubuntu-mobile-icons ubuntu-system-settings
  ubuntu-system-settings-online-accounts ubuntu-ui-toolkit-theme unity
  unity-asset-pool unity-greeter unity-gtk-module-common unity-gtk2-module
  unity-gtk3-module unity-lens-applications unity-lens-files
  unity-lens-friends unity-lens-music unity-lens-photos unity-lens-video
  unity-scope-audacious unity-scope-calculator unity-scope-chromiumbookmarks
  unity-scope-clementine unity-scope-colourlovers unity-scope-devhelp
  unity-scope-firefoxbookmarks unity-scope-gdrive unity-scope-gmusicbrowser
  unity-scope-gourmet unity-scope-guayadeque unity-scope-home
  unity-scope-manpages unity-scope-musicstores unity-scope-musique
  unity-scope-openclipart unity-scope-texdoc unity-scope-tomboy
  unity-scope-video-remote unity-scope-virtualbox unity-scope-yelp
  unity-scope-zotero unity-scopes-master-default unity-scopes-runner
  unity-services unity-webapps-service whoopsie-preferences
The following packages will be upgraded:
  libunity-protocol-private0
1 upgraded, 207 newly installed, 0 to remove and 3 not upgraded.
**Need to get 105 MB/106 MB of archives**.
After this operation, _**288 MB of additional disk space will be used**_.
```

---

### Post by VMC on 2013-09-18
Edit3: Strange, but I don't see 'bluez' as a required dependancy of 'gdm':```
apt-cache showpkg gdmPackage: gdm
Versions: 
3.8.4-0ubuntu2 (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_saucy_universe_binary-amd64_Packages) (/var/lib/dpkg/status)
 Description Language: 
                 File: /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_saucy_universe_binary-amd64_Packages
                  MD5: 289fec08e973fa0389c78da5c38f13ba
 Description Language: en
                 File: /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_saucy_universe_i18n_Translation-en
                  MD5: 289fec08e973fa0389c78da5c38f13ba




Reverse Depends: 
  libgdm:i386,gdm 3.8.3-3~
  libgdm:i386,gdm 3.8.3-3~
  gdm:i386,gdm
  plymouth:i386,gdm 3.0.4-0ubuntu11
  xfswitch-plugin,gdm
  ubuntu-mobile-default-settings,gdm
  ubuntu-gnome-desktop,gdm
  libgdm,gdm 3.8.3-3~
  libgdm,gdm 3.8.3-3~
  gnome-shell,gdm
  gnome-core,gdm 3.4
  altos,gdm
  plymouth,gdm 3.0.4-0ubuntu11
  numlockx,gdm
  gnome-control-center-data,gdm 3.0
  gnome-control-center-data,gdm 3.0
Dependencies: 
3.8.4-0ubuntu2 - libaccountsservice0 (2 0.6.8) libaudit1 (2 1:2.2.1) libc6 (2 2.14) libcairo2 (2 1.10.0) libcanberra-gtk3-0 (2 0.25) libcanberra0 (2 0.2) libgdk-pixbuf2.0-0 (2 2.22.0) libgdm (5 3.8.4-0ubuntu2) libglib2.0-0 (2 2.37.3) libgtk-3-0 (2 3.0.0) libpam0g (2 0.99.7.1) libpango-1.0-0 (2 1.14.0) libselinux1 (2 1.32) libsystemd-daemon0 (2 31) libsystemd-login0 (2 186) libupower-glib1 (2 0.9.0) libwrap0 (2 7.6-4~) libx11-6 (0 (null)) libxau6 (0 (null)) libxdmcp6 (0 (null)) libxrandr2 (2 2:1.2.99.3) dconf-gsettings-backend (2 0.12.1-2) debconf (18 0.5) debconf-2.0 (0 (null)) sysv-rc (18 2.88dsf-24) file-rc (2 0.8.16) adduser (0 (null)) libpam-modules (2 0.72-1) libpam-runtime (2 0.76-13.1) libpam-systemd (0 (null)) gnome-session-bin (2 3.6) gnome-settings-daemon (2 3.2) gnome-shell (0 (null)) plymouth (2 0.8.8-0ubuntu6.1) policykit-1-gnome (0 (null)) upower (0 (null)) gnome-session (16 (null)) x-session-manager (16 (null)) x-window-manager (16 (null)) x-terminal-emulator (0 (null)) lsb-base (2 3.2-14) librsvg2-common (0 (null)) accountsservice (2 0.6.12) gsettings-desktop-schemas (0 (null)) libglib2.0-bin (2 2.35.0) dconf-cli (2 0.12.1-2) x11-common (2 1:7.6+11) x11-xserver-utils (0 (null)) libpam-gnome-keyring (0 (null)) gnome-orca (0 (null)) zenity (0 (null)) xserver-xephyr (0 (null)) x11-xkb-utils (0 (null)) xserver-xorg (0 (null)) at-spi2-core (0 (null)) gnome-icon-theme (0 (null)) gnome-icon-theme-symbolic (0 (null)) gnome-control-center (3 3.0) gnome-control-center:i386 (3 3.0) gnome-orca (3 2.30.0-2) gnome-orca:i386 (3 2.30.0-2) gnome-panel (3 3.0) gnome-panel:i386 (3 3.0) gnome-screensaver (3 2.17.7) gnome-screensaver:i386 (3 2.17.7) gnome-shell (3 3.5) gnome-shell:i386 (3 3.5) gdm:i386 (0 (null)) 
Provides: 
3.8.4-0ubuntu2 - x-display-manager 
Reverse Provides: 
```

Unless they share a common library somewhere...

---

### Post by jbicha on 2013-09-18
Bluetooth support won't actually hurt you, but...

gdm depends on gnome-shell to actually do anything. gnome-shell depends on gnome-bluetooth (which uses bluez)

lightdm by default includes unity-greeter which includes many of the "indicator" status menus which depend on something that can display them. The two choices are unity or indicator-applet (which can be used in GNOME Flashback).

For a simple option, install **lightdm-gtk-greeter**. It's what Lubuntu, Xubuntu, Mythbuntu, and Ubuntu Studio use.

---

