---
title: "Updating 12.04 beta..."
date: 2012-03-17
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by hrickh on 2012-03-17
So, I've had Ubuntu 12.04 beta installed for about 3 weeks now, and I generally like it. I'm using Gnome Shell over Unity, as Unity (rather Compiz) has caused me some problems.

The last couple updates have come up as "Partial Update" ad I can't figure out why. My install is fairly vanilla. Whatever 12.04 beta installed by default, and a few additions, such as Audacity, Chromium, etc.

I ran apt-get with the --simulate dist-upgrade option and here is what I got. Again, I don't understand why certain packages are flagged for removal, and libpurple is even held back.

Thanks for any info/help.

R.
==

Output of simulate dist-upgrade: 

```
~$ sudo apt-get --simulate dist-upgrade
[sudo] password for xxxxxx: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  compiz compiz-gnome compiz-plugins-main compiz-plugins-main-default
  compizconfig-backend-gconf compizconfig-settings-manager libcompizconfig0
  python-compizconfig ubuntu-desktop unity
The following NEW packages will be installed:
  cryptsetup-bin cups-pk-helper gettext gir1.2-gdesktopenums-3.0
  gir1.2-gjs-1.0 libcapi20-3 libcogl9 libcryptsetup4 libgoa-1.0-common
  libidl-common libodbc1 unixodbc
The following packages have been kept back:
  libpurple0
The following packages will be upgraded:
  acpi-support anki app-install-data-partner apparmor apt apt-transport-https
  apt-utils aptdaemon aptdaemon-data apturl apturl-common audacity
  audacity-data bamfdaemon baobab bluez bluez-alsa bluez-cups bluez-gstreamer
  cheese cheese-common chromium-browser chromium-browser-l10n
  chromium-codecs-ffmpeg compiz-core compiz-plugins compiz-plugins-default
  console-setup cpp cups cups-bsd cups-client cups-common cups-filters
  cups-ppdc debconf debconf-i18n firefox firefox-globalmenu
  firefox-gnome-support firefox-locale-en flashplugin-installer
  foomatic-filters friendly-recovery gcc gconf-defaults-service gconf-service
  gconf2 gconf2-common gdb gedit gedit-common gir1.2-atk-1.0
  gir1.2-clutter-1.0 gir1.2-cogl-1.0 gir1.2-coglpango-1.0
  gir1.2-dbusmenu-glib-0.4 gir1.2-dbusmenu-gtk-0.4 gir1.2-dee-1.0
  gir1.2-gconf-2.0 gir1.2-gee-1.0 gir1.2-indicate-0.7
  gir1.2-javascriptcoregtk-3.0 gir1.2-mutter-3.0 gir1.2-networkmanager-1.0
  gir1.2-rb-3.0 gir1.2-soup-2.4 gir1.2-totem-1.0 gir1.2-unity-5.0
  gir1.2-webkit-3.0 gjs gnome-contacts gnome-desktop3-data
  gnome-exe-thumbnailer gnome-font-viewer gnome-online-accounts
  gnome-screensaver gnome-screenshot gnome-settings-daemon gnome-shell
  gnome-shell-common gnome-system-log gnome-tweak-tool gnome-utils-common
  gucharmap gwibber gwibber-service gwibber-service-facebook
  gwibber-service-identica gwibber-service-twitter hpijs hplip hplip-data
  ibus-table indicator-applet-complete indicator-application indicator-appmenu
  indicator-power indicator-session keyboard-configuration
  language-selector-common language-selector-gnome libapt-inst1.4
  libapt-pkg4.12 libasound2 libatk1.0-0 libatk1.0-data libbamf0 libbamf3-0
  libbluetooth3 libcheese-gtk21 libcheese3 libclutter-1.0-0
  libclutter-1.0-common libclutter-gst-1.0-0 libclutter-gtk-1.0-0
  libcogl-common libcogl-pango0 libcups2 libcupscgi1 libcupsdriver1
  libcupsfilters1 libcupsimage2 libcupsmime1 libcupsppdc1 libdbusmenu-glib4
  libdbusmenu-gtk3-4 libdbusmenu-gtk4 libdc1394-22 libdconf-qt0 libdecoration0
  libdee-1.0-4 libexpat1 libgconf-2-4 libgconf2-4 libgdata-common libgdata13
  libgee2 libgjs0c libgl1-mesa-dri libgl1-mesa-glx libglapi-mesa libglib2.0-0
  libglib2.0-bin libglib2.0-data libglu1-mesa libgnome-desktop-3-2
  libgoa-1.0-0 libgucharmap-2-90-7 libgweather-3-0 libgweather-common
  libgwibber-gtk2 libgwibber2 libhpmud0 libical0 libidl0 libido3-0.1-0
  libimobiledevice2 libindicate-gtk3 libindicate5 libjavascriptcoregtk-1.0-0
  libjavascriptcoregtk-3.0-0 liblightdm-gobject-1-0 libmetacity-private0
  libmutter0 libmx-1.0-2 libnm-glib-vpn1 libnm-glib4 libnm-gtk-common
  libnm-gtk0 libnm-util2 libnux-2.0-0 libnux-2.0-common libpackagekit-glib2-14
  libqt4-dbus libqt4-declarative libqt4-designer libqt4-help libqt4-network
  libqt4-opengl libqt4-qt3support libqt4-script libqt4-scripttools libqt4-sql
  libqt4-sql-mysql libqt4-sql-sqlite libqt4-svg libqt4-test libqt4-xml
  libqt4-xmlpatterns libqtcore4 libqtgui4 libqtwebkit4 librhythmbox-core5
  libsane-hpaio libsoup-gnome2.4-1 libsoup2.4-1 libtotem0 libunity-2d-private0
  libunity-core-5.0-5 libunity9 libwebkitgtk-1.0-0 libwebkitgtk-1.0-common
  libwebkitgtk-3.0-0 libwebkitgtk-3.0-common libxatracker1 libxfixes3
  light-themes lightdm linux-headers-3.2.0-18
  linux-headers-3.2.0-18-generic-pae linux-image-3.2.0-18-generic-pae
  linux-libc-dev metacity metacity-common modemmanager mutter-common myunity
  network-manager network-manager-gnome nux-tools nvidia-common os-prober
  printer-driver-hpcups printer-driver-hpijs python python-aptdaemon
  python-aptdaemon.gtk3widgets python-aptdaemon.gtkwidgets
  python-aptdaemon.pkcompat python-debtagshw python-gobject-2 python-minimal
  python-packagekit python-pyatspi2 python-software-properties
  python-ubuntuone-control-panel qdbus qt-at-spi rhythmbox rhythmbox-data
  rhythmbox-mozilla rhythmbox-plugin-cdrecorder rhythmbox-plugin-zeitgeist
  rhythmbox-plugins sessioninstaller software-properties-common
  software-properties-gtk synaptic thunderbird thunderbird-globalmenu
  thunderbird-gnome-support totem totem-common totem-mozilla totem-plugins
  ubuntuone-control-panel ubuntuone-control-panel-common
  ubuntuone-control-panel-gtk ubuntuone-control-panel-qt ubuntuone-installer
  udisks ufw unattended-upgrades unity-2d unity-2d-panel unity-2d-shell
  unity-2d-spread unity-common unity-greeter unity-lens-applications
  unity-lens-files unity-services update-manager update-manager-core
  usb-creator-common usb-creator-gtk vim-common vim-tiny whoopsie wine wine1.4
  wine1.4-common wine1.4-i386 winetricks xserver-xorg-input-evdev
  xserver-xorg-input-synaptics
287 upgraded, 12 newly installed, 10 to remove and 1 not upgraded.
Remv ubuntu-desktop [1.264]
Remv unity [5.4.0-r2065-l2064-p654~precise1]
Remv compiz [1:0.9.7.0~bzr3003-0ubuntu3~ppa1]
Remv compiz-gnome [1:0.9.7.0~bzr3003-0ubuntu3~ppa1]
Remv compiz-plugins-main [1:0.9.7.0~bzr20-0ubuntu1~ppa1]
Remv compiz-plugins-main-default [1:0.9.7.0~bzr20-0ubuntu1~ppa1]
Remv compizconfig-backend-gconf [0.9.5.92-0ubuntu2]
Remv compizconfig-settings-manager [0.9.5.92-0ubuntu3]
Remv python-compizconfig [0.9.5.94-0ubuntu4]
Remv libcompizconfig0 [0.9.7.0-0~428~precise1]
Inst python-minimal [2.7.2-9ubuntu2] (2.7.2-9ubuntu4 Ubuntu:12.04/precise [i386]) [python:i386 ]
Conf python-minimal (2.7.2-9ubuntu4 Ubuntu:12.04/precise [i386]) [python:i386 ]
Inst python [2.7.2-9ubuntu2] (2.7.2-9ubuntu4 Ubuntu:12.04/precise [i386])
Inst libapt-pkg4.12 [0.8.16~exp12ubuntu5] (0.8.16~exp12ubuntu6 Ubuntu:12.04/precise [i386])
Conf libapt-pkg4.12 (0.8.16~exp12ubuntu6 Ubuntu:12.04/precise [i386])
Inst debconf [1.5.41ubuntu2] (1.5.42ubuntu1 Ubuntu:12.04/precise [all])
Conf debconf (1.5.42ubuntu1 Ubuntu:12.04/precise [all])
Inst libapt-inst1.4 [0.8.16~exp12ubuntu5] (0.8.16~exp12ubuntu6 Ubuntu:12.04/precise [i386])
Inst libexpat1 [2.0.1-7.2] (2.0.1-7.2ubuntu1 Ubuntu:12.04/precise [i386])
Inst libglib2.0-data [2.31.20-0ubuntu2] (2.31.20-0ubuntu3 Ubuntu:12.04/precise [all])
Inst libglib2.0-bin [2.31.20-0ubuntu2] (2.31.20-0ubuntu3 Ubuntu:12.04/precise [i386]) []
Inst libglib2.0-0 [2.31.20-0ubuntu2] (2.31.20-0ubuntu3 Ubuntu:12.04/precise [i386])
Inst apparmor [2.7.100-0ubuntu1] (2.7.101-0ubuntu1 Ubuntu:12.04/precise [i386])
Inst bluez [4.98-2ubuntu4] (4.98-2ubuntu6 Ubuntu:12.04/precise [i386])
Inst chromium-browser-l10n [17.0.963.78~r125577-0ubuntu1] (17.0.963.79~r125985-0ubuntu1 Ubuntu:12.04/precise [all]) []
Inst gconf-defaults-service [3.2.4-0ubuntu2] (3.2.5-0ubuntu1 Ubuntu:12.04/precise [i386]) []
Inst gconf2-common [3.2.4-0ubuntu2] (3.2.5-0ubuntu1 Ubuntu:12.04/precise [all]) [libgconf-2-4:i386 gconf-service:i386 ]
Inst libgconf2-4 [3.2.4-0ubuntu2] (3.2.5-0ubuntu1 Ubuntu:12.04/precise [i386]) [libgconf-2-4:i386 gconf-service:i386 ]
Inst gconf2 [3.2.4-0ubuntu2] (3.2.5-0ubuntu1 Ubuntu:12.04/precise [i386]) [libgconf-2-4:i386 gconf-service:i386 ]
Inst gconf-service [3.2.4-0ubuntu2] (3.2.5-0ubuntu1 Ubuntu:12.04/precise [i386]) [libgconf-2-4:i386 ]
Inst libgconf-2-4 [3.2.4-0ubuntu2] (3.2.5-0ubuntu1 Ubuntu:12.04/precise [i386]) []
Inst libasound2 [1.0.25-1ubuntu8] (1.0.25-1ubuntu9 Ubuntu:12.04/precise [i386]) []
Inst libcups2 [1.5.2-6] (1.5.2-8 Ubuntu:12.04/precise [i386]) []
Inst libxfixes3 [1:5.0-4ubuntu1] (1:5.0-4ubuntu4 Ubuntu:12.04/precise [i386]) []
Inst chromium-codecs-ffmpeg [17.0.963.78~r125577-0ubuntu1] (17.0.963.79~r125985-0ubuntu1 Ubuntu:12.04/precise [i386]) []
Inst chromium-browser [17.0.963.78~r125577-0ubuntu1] (17.0.963.79~r125985-0ubuntu1 Ubuntu:12.04/precise [i386])
Inst libcupsfilters1 [1.0.4-1] (1.0.5-1 Ubuntu:12.04/precise [i386])
Inst libcupsimage2 [1.5.2-6] (1.5.2-8 Ubuntu:12.04/precise [i386])
Inst cups-filters [1.0.4-1] (1.0.5-1 Ubuntu:12.04/precise [i386])
Inst libcupsmime1 [1.5.2-6] (1.5.2-8 Ubuntu:12.04/precise [i386])
Inst libcupscgi1 [1.5.2-6] (1.5.2-8 Ubuntu:12.04/precise [i386])
Inst libcupsppdc1 [1.5.2-6] (1.5.2-8 Ubuntu:12.04/precise [i386])
Inst cups-common [1.5.2-6] (1.5.2-8 Ubuntu:12.04/precise [all])
Inst cups-bsd [1.5.2-6] (1.5.2-8 Ubuntu:12.04/precise [i386]) []
Inst cups-client [1.5.2-6] (1.5.2-8 Ubuntu:12.04/precise [i386])
Inst cups-ppdc [1.5.2-6] (1.5.2-8 Ubuntu:12.04/precise [i386])
Inst cups [1.5.2-6] (1.5.2-8 Ubuntu:12.04/precise [i386])
Inst foomatic-filters [4.0.13-0ubuntu1] (4.0.14-0ubuntu1 Ubuntu:12.04/precise [i386])
Inst libgl1-mesa-dri [8.0.1-0ubuntu2] (8.0.1-0ubuntu4 Ubuntu:12.04/precise [i386])
Inst libgl1-mesa-glx [8.0.1-0ubuntu2] (8.0.1-0ubuntu4 Ubuntu:12.04/precise [i386]) []
Inst libglapi-mesa [8.0.1-0ubuntu2] (8.0.1-0ubuntu4 Ubuntu:12.04/precise [i386])
Inst libgnome-desktop-3-2 [3.3.91-0ubuntu1] (3.3.91-0ubuntu2 Ubuntu:12.04/precise [i386]) []
Inst gnome-desktop3-data [3.3.91-0ubuntu1] (3.3.91-0ubuntu2 Ubuntu:12.04/precise [all])
Inst gnome-settings-daemon [3.3.91-0ubuntu3] (3.3.91-0ubuntu5 Ubuntu:12.04/precise [i386])
Inst gnome-screensaver [3.2.2-0ubuntu1] (3.2.2-0ubuntu2 Ubuntu:12.04/precise [i386])
Inst libatk1.0-0 [2.3.91-0ubuntu2] (2.3.93-1 Ubuntu:12.04/precise [i386]) []
Inst libatk1.0-data [2.3.91-0ubuntu2] (2.3.93-1 Ubuntu:12.04/precise [all])
Inst libbamf3-0 [0.2.110-0ubuntu1] (0.2.112-0ubuntu1 Ubuntu:12.04/precise [i386]) []
Inst libbamf0 [0.2.110-0ubuntu1] (0.2.112-0ubuntu1 Ubuntu:12.04/precise [i386]) []
Inst bamfdaemon [0.2.110-0ubuntu1] (0.2.112-0ubuntu1 Ubuntu:12.04/precise [i386])
Inst libbluetooth3 [4.98-2ubuntu4] (4.98-2ubuntu6 Ubuntu:12.04/precise [i386])
Inst libcogl9 (1.9.8-0ubuntu3 Ubuntu:12.04/precise [i386])
Inst libcogl-pango0 [1.8.2-1] (1.9.8-0ubuntu3 Ubuntu:12.04/precise [i386])
Inst gir1.2-coglpango-1.0 [1.8.2-1] (1.9.8-0ubuntu3 Ubuntu:12.04/precise [i386]) []
Inst gir1.2-cogl-1.0 [1.8.2-1] (1.9.8-0ubuntu3 Ubuntu:12.04/precise [i386])
Inst gir1.2-atk-1.0 [2.3.91-0ubuntu2] (2.3.93-1 Ubuntu:12.04/precise [i386])
Inst gir1.2-clutter-1.0 [1.8.4-1] (1.9.14-0ubuntu2 Ubuntu:12.04/precise [i386]) []
Inst libclutter-1.0-0 [1.8.4-1] (1.9.14-0ubuntu2 Ubuntu:12.04/precise [i386])
Inst libclutter-gst-1.0-0 [1.4.6-1] (1.5.4-0ubuntu1 Ubuntu:12.04/precise [i386])
Inst libclutter-gtk-1.0-0 [1.0.4-1] (1.1.2-0ubuntu1 Ubuntu:12.04/precise [i386])
Inst libgee2 [0.6.4-0ubuntu1] (0.6.4-1 Ubuntu:12.04/precise [i386])
Inst libcheese3 [3.3.90-0ubuntu1] (3.3.90-0ubuntu2 Ubuntu:12.04/precise [i386]) []
Inst libcheese-gtk21 [3.3.90-0ubuntu1] (3.3.90-0ubuntu2 Ubuntu:12.04/precise [i386]) []
Inst cheese-common [3.3.90-0ubuntu1] (3.3.90-0ubuntu2 Ubuntu:12.04/precise [all]) [cheese:i386 ]
Inst cheese [3.3.90-0ubuntu1] (3.3.90-0ubuntu2 Ubuntu:12.04/precise [i386])
Inst libmx-1.0-2 [1.4.1-1ubuntu1] (1.4.3-0ubuntu1 Ubuntu:12.04/precise [i386])
Inst libcupsdriver1 [1.5.2-6] (1.5.2-8 Ubuntu:12.04/precise [i386])
Inst gir1.2-dbusmenu-gtk-0.4 [0.5.93-0ubuntu2] (0.5.94-0ubuntu1 Ubuntu:12.04/precise [i386]) []
Inst libdbusmenu-gtk4 [0.5.93-0ubuntu2] (0.5.94-0ubuntu1 Ubuntu:12.04/precise [i386]) []
Inst gir1.2-dbusmenu-glib-0.4 [0.5.93-0ubuntu2] (0.5.94-0ubuntu1 Ubuntu:12.04/precise [i386]) []
Inst libdbusmenu-glib4 [0.5.93-0ubuntu2] (0.5.94-0ubuntu1 Ubuntu:12.04/precise [i386])
Inst libdbusmenu-gtk3-4 [0.5.93-0ubuntu2] (0.5.94-0ubuntu1 Ubuntu:12.04/precise [i386])
Inst libsoup2.4-1 [2.37.91-0ubuntu1] (2.37.91-1 Ubuntu:12.04/precise [i386])
Inst gnome-online-accounts [3.3.0-0ubuntu1] (3.3.0-1 Ubuntu:12.04/precise [i386]) []
Inst libsoup-gnome2.4-1 [2.37.91-0ubuntu1] (2.37.91-1 Ubuntu:12.04/precise [i386]) []
Inst libwebkitgtk-3.0-0 [1.7.90-0ubuntu1] (1.7.91-0ubuntu1 Ubuntu:12.04/precise [i386]) []
Inst libjavascriptcoregtk-3.0-0 [1.7.90-0ubuntu1] (1.7.91-0ubuntu1 Ubuntu:12.04/precise [i386]) []
Inst libwebkitgtk-3.0-common [1.7.90-0ubuntu1] (1.7.91-0ubuntu1 Ubuntu:12.04/precise [all]) []
Inst libgoa-1.0-common (3.3.0-1 Ubuntu:12.04/precise [all]) []
Inst libgoa-1.0-0 [3.3.0-0ubuntu1] (3.3.0-1 Ubuntu:12.04/precise [i386])
Inst cpp [4:4.6.2-4ubuntu1] (4:4.6.3-1ubuntu5 Ubuntu:12.04/precise [i386])
Inst libidl-common (0.8.14-0.2ubuntu2 Ubuntu:12.04/precise [all])
Inst libidl0 [0.8.14-0.2ubuntu1] (0.8.14-0.2ubuntu2 Ubuntu:12.04/precise [i386])
Inst libodbc1 (2.2.14p2-5ubuntu3 Ubuntu:12.04/precise [i386])
Inst libqt4-test [4:4.8.0-1ubuntu9] (4:4.8.0-1ubuntu10 Ubuntu:12.04/precise [i386]) []
Inst libqt4-sql-mysql [4:4.8.0-1ubuntu9] (4:4.8.0-1ubuntu10 Ubuntu:12.04/precise [i386]) []
Inst libqt4-sql-sqlite [4:4.8.0-1ubuntu9] (4:4.8.0-1ubuntu10 Ubuntu:12.04/precise [i386]) []
Inst libqt4-qt3support [4:4.8.0-1ubuntu9] (4:4.8.0-1ubuntu10 Ubuntu:12.04/precise [i386]) []
Inst libqt4-help [4:4.8.0-1ubuntu9] (4:4.8.0-1ubuntu10 Ubuntu:12.04/precise [i386]) []
Inst libqt4-scripttools [4:4.8.0-1ubuntu9] (4:4.8.0-1ubuntu10 Ubuntu:12.04/precise [i386]) []
Inst libqt4-designer [4:4.8.0-1ubuntu9] (4:4.8.0-1ubuntu10 Ubuntu:12.04/precise [i386]) []
Inst libqt4-opengl [4:4.8.0-1ubuntu9] (4:4.8.0-1ubuntu10 Ubuntu:12.04/precise [i386]) []
Inst libqt4-svg [4:4.8.0-1ubuntu9] (4:4.8.0-1ubuntu10 Ubuntu:12.04/precise [i386]) []
Inst libqtgui4 [4:4.8.0-1ubuntu9] (4:4.8.0-1ubuntu10 Ubuntu:12.04/precise [i386]) [libqt4-declarative:i386 ]
Inst libqt4-declarative [4:4.8.0-1ubuntu9] (4:4.8.0-1ubuntu10 Ubuntu:12.04/precise [i386]) []
Inst libqt4-sql [4:4.8.0-1ubuntu9] (4:4.8.0-1ubuntu10 Ubuntu:12.04/precise [i386]) []
Inst libqt4-xmlpatterns [4:4.8.0-1ubuntu9] (4:4.8.0-1ubuntu10 Ubuntu:12.04/precise [i386]) []
Inst qdbus [4:4.8.0-1ubuntu9] (4:4.8.0-1ubuntu10 Ubuntu:12.04/precise [i386]) []
Inst libqt4-script [4:4.8.0-1ubuntu9] (4:4.8.0-1ubuntu10 Ubuntu:12.04/precise [i386]) []
Inst libqt4-network [4:4.8.0-1ubuntu9] (4:4.8.0-1ubuntu10 Ubuntu:12.04/precise [i386]) []
Inst libqt4-dbus [4:4.8.0-1ubuntu9] (4:4.8.0-1ubuntu10 Ubuntu:12.04/precise [i386]) []
Inst libqt4-xml [4:4.8.0-1ubuntu9] (4:4.8.0-1ubuntu10 Ubuntu:12.04/precise [i386]) []
Inst libqtcore4 [4:4.8.0-1ubuntu9] (4:4.8.0-1ubuntu10 Ubuntu:12.04/precise [i386])
Inst libqtwebkit4 [2.2.1-1ubuntu3] (2.2.1-1ubuntu4 Ubuntu:12.04/precise [i386])
Inst libxatracker1 [8.0.1-0ubuntu2] (8.0.1-0ubuntu4 Ubuntu:12.04/precise [i386])
Inst lightdm [1.1.7-0ubuntu1] (1.1.8-0ubuntu1 Ubuntu:12.04/precise [i386])
Inst linux-image-3.2.0-18-generic-pae [3.2.0-18.28] (3.2.0-18.29 Ubuntu:12.04/precise [i386])
Inst nvidia-common [1:0.2.40] (1:0.2.41 Ubuntu:12.04/precise [i386])
Inst qt-at-spi [0.1.1+20120306-0ubuntu1] (0.2.0-0ubuntu1 Ubuntu:12.04/precise [i386])
Inst libglu1-mesa [8.0.1-0ubuntu2] (8.0.1-0ubuntu4 Ubuntu:12.04/precise [i386])
Inst wine1.4-common [1.4~rc6-0ubuntu1] (1.4-0ubuntu1 Ubuntu:12.04/precise [all]) [wine1.4-i386:i386 ]
Inst wine1.4 [1.4~rc6-0ubuntu1] (1.4-0ubuntu1 Ubuntu:12.04/precise [i386]) [wine1.4-i386:i386 ]
Inst wine1.4-i386 [1.4~rc6-0ubuntu1] (1.4-0ubuntu1 Ubuntu:12.04/precise [i386])
Inst winetricks [0.0+20111115] (0.0+20120308 Ubuntu:12.04/precise [i386])
Inst libcapi20-3 (1:3.12.20071127-0ubuntu11 Ubuntu:12.04/precise [i386])
Inst libdc1394-22 [2.1.3-4] (2.2.0-2 Ubuntu:12.04/precise [i386])
Inst apt [0.8.16~exp12ubuntu5] (0.8.16~exp12ubuntu6 Ubuntu:12.04/precise [i386])
Conf apt (0.8.16~exp12ubuntu6 Ubuntu:12.04/precise [i386])
Inst apt-utils [0.8.16~exp12ubuntu5] (0.8.16~exp12ubuntu6 Ubuntu:12.04/precise [i386])
Inst keyboard-configuration [1.70ubuntu2] (1.70ubuntu3 Ubuntu:12.04/precise [all])
Inst console-setup [1.70ubuntu2] (1.70ubuntu3 Ubuntu:12.04/precise [all])
Inst debconf-i18n [1.5.41ubuntu2] (1.5.42ubuntu1 Ubuntu:12.04/precise [all])
Inst vim-tiny [2:7.3.429-2ubuntu1] (2:7.3.429-2ubuntu2 Ubuntu:12.04/precise [i386]) []
Inst vim-common [2:7.3.429-2ubuntu1] (2:7.3.429-2ubuntu2 Ubuntu:12.04/precise [i386])
Inst apt-transport-https [0.8.16~exp12ubuntu5] (0.8.16~exp12ubuntu6 Ubuntu:12.04/precise [i386])
Inst friendly-recovery [0.2.24] (0.2.25 Ubuntu:12.04/precise [all])
Inst aptdaemon-data [0.43+bzr778-0ubuntu1] (0.43+bzr784-0ubuntu1 Ubuntu:12.04/precise [all])
Inst python-aptdaemon.gtkwidgets [0.43+bzr778-0ubuntu1] (0.43+bzr784-0ubuntu1 Ubuntu:12.04/precise [all]) []
Inst python-aptdaemon.gtk3widgets [0.43+bzr778-0ubuntu1] (0.43+bzr784-0ubuntu1 Ubuntu:12.04/precise [all]) []
Inst python-packagekit [0.7.2-4ubuntu1] (0.7.2-4ubuntu2 Ubuntu:12.04/precise [all]) []
Inst python-aptdaemon.pkcompat [0.43+bzr778-0ubuntu1] (0.43+bzr784-0ubuntu1 Ubuntu:12.04/precise [all]) []
Inst unattended-upgrades [0.75.1] (0.76 Ubuntu:12.04/precise [all]) []
Inst python-software-properties [0.82.5] (0.82.7 Ubuntu:12.04/precise [all]) []
Inst aptdaemon [0.43+bzr778-0ubuntu1] (0.43+bzr784-0ubuntu1 Ubuntu:12.04/precise [all]) []
Inst python-aptdaemon [0.43+bzr778-0ubuntu1] (0.43+bzr784-0ubuntu1 Ubuntu:12.04/precise [all])
Inst language-selector-gnome [0.72] (0.74 Ubuntu:12.04/precise [all]) []
Inst language-selector-common [0.72] (0.74 Ubuntu:12.04/precise [all])
Inst ufw [0.31-0ubuntu1] (0.31-0ubuntu2 Ubuntu:12.04/precise [all])
Inst synaptic [0.75.5] (0.75.6 Ubuntu:12.04/precise [i386])
Inst update-manager-core [1:0.156.7] (1:0.156.8 Ubuntu:12.04/precise [i386]) [update-manager:i386 ]
Inst update-manager [1:0.156.7] (1:0.156.8 Ubuntu:12.04/precise [all])
Inst acpi-support [0.139] (0.140 Ubuntu:12.04/precise [i386])
Inst anki [1.2.9-1] (1.2.9-2 Ubuntu:12.04/precise [all])
Inst app-install-data-partner [12.12.04] (12.12.04.1 Ubuntu:12.04/precise [all])
Inst apturl [0.5.1ubuntu1] (0.5.1ubuntu2 Ubuntu:12.04/precise [i386]) []
Inst apturl-common [0.5.1ubuntu1] (0.5.1ubuntu2 Ubuntu:12.04/precise [i386])
Inst software-properties-common [0.82.5] (0.82.7 Ubuntu:12.04/precise [all])
Inst software-properties-gtk [0.82.5] (0.82.7 Ubuntu:12.04/precise [all])
Inst gir1.2-webkit-3.0 [1.7.90-0ubuntu1] (1.7.91-0ubuntu1 Ubuntu:12.04/precise [i386]) []
Inst gir1.2-javascriptcoregtk-3.0 [1.7.90-0ubuntu1] (1.7.91-0ubuntu1 Ubuntu:12.04/precise [i386])
Inst gir1.2-soup-2.4 [2.37.91-0ubuntu1] (2.37.91-1 Ubuntu:12.04/precise [i386])
Inst audacity [2.0.0~rc8-1] (2.0.0-1 Ubuntu:12.04/precise [i386]) []
Inst audacity-data [2.0.0~rc8-1] (2.0.0-1 Ubuntu:12.04/precise [all])
Inst baobab [3.2.1-0ubuntu4] (3.3.3-1 Ubuntu:12.04/precise [i386])
Inst bluez-alsa [4.98-2ubuntu4] (4.98-2ubuntu6 Ubuntu:12.04/precise [i386])
Inst bluez-cups [4.98-2ubuntu4] (4.98-2ubuntu6 Ubuntu:12.04/precise [i386])
Inst bluez-gstreamer [4.98-2ubuntu4] (4.98-2ubuntu6 Ubuntu:12.04/precise [i386])
Inst compiz-plugins [1:0.9.7.0~bzr3003-0ubuntu3~ppa1] (1:0.9.7.0+bzr3035-0ubuntu1 Ubuntu:12.04/precise [i386]) []
Inst compiz-plugins-default [1:0.9.7.0~bzr3003-0ubuntu3~ppa1] (1:0.9.7.0+bzr3035-0ubuntu1 Ubuntu:12.04/precise [i386]) []
Inst libdecoration0 [1:0.9.7.0~bzr3003-0ubuntu3~ppa1] (1:0.9.7.0+bzr3035-0ubuntu1 Ubuntu:12.04/precise [i386]) []
Inst compiz-core [1:0.9.7.0~bzr3003-0ubuntu3~ppa1] (1:0.9.7.0+bzr3035-0ubuntu1 Ubuntu:12.04/precise [i386])
Inst libcryptsetup4 (2:1.4.1-2ubuntu2 Ubuntu:12.04/precise [i386])
Inst cryptsetup-bin (2:1.4.1-2ubuntu2 Ubuntu:12.04/precise [i386])
Inst flashplugin-installer [11.1.102.63ubuntu1] (11.1.102.63ubuntu2 Ubuntu:12.04/precise [i386])
Inst firefox-globalmenu [11.0~b7+build1-0ubuntu1] (11.0+build1-0ubuntu1 Ubuntu:12.04/precise [i386]) []
Inst firefox [11.0~b7+build1-0ubuntu1] (11.0+build1-0ubuntu1 Ubuntu:12.04/precise [i386])
Inst firefox-gnome-support [11.0~b7+build1-0ubuntu1] (11.0+build1-0ubuntu1 Ubuntu:12.04/precise [i386])
Inst firefox-locale-en [11.0~b7+build1-0ubuntu1] (11.0+build1-0ubuntu1 Ubuntu:12.04/precise [all])
Inst gcc [4:4.6.2-4ubuntu1] (4:4.6.3-1ubuntu5 Ubuntu:12.04/precise [i386])
Inst gdb [7.4-0ubuntu1] (7.4-2012.02-0ubuntu2 Ubuntu:12.04/precise [i386])
Inst gedit-common [3.3.7-0ubuntu1] (3.3.7-0ubuntu2 Ubuntu:12.04/precise [all])
Inst gedit [3.3.7-0ubuntu1] (3.3.7-0ubuntu2 Ubuntu:12.04/precise [i386])
Inst gettext (0.18.1.1-5ubuntu3 Ubuntu:12.04/precise [i386])
Inst libdee-1.0-4 [1.0.4-0ubuntu1] (1.0.6-0ubuntu1 Ubuntu:12.04/precise [i386])
Inst gir1.2-dee-1.0 [1.0.4-0ubuntu1] (1.0.6-0ubuntu1 Ubuntu:12.04/precise [i386])
Inst gir1.2-gconf-2.0 [3.2.4-0ubuntu2] (3.2.5-0ubuntu1 Ubuntu:12.04/precise [i386])
Inst gir1.2-gdesktopenums-3.0 (3.3.90-0ubuntu2 Ubuntu:12.04/precise [i386])
Inst gir1.2-gee-1.0 [0.6.4-0ubuntu1] (0.6.4-1 Ubuntu:12.04/precise [i386])
Inst libgjs0c [1.30.1-1ubuntu1] (1.31.20-0ubuntu1 Ubuntu:12.04/precise [i386])
Inst gir1.2-gjs-1.0 (1.31.20-0ubuntu1 Ubuntu:12.04/precise [i386])
Inst libindicate5 [0.6.90-0ubuntu1] (0.6.91-0ubuntu1 Ubuntu:12.04/precise [i386])
Inst gir1.2-indicate-0.7 [0.6.90-0ubuntu1] (0.6.91-0ubuntu1 Ubuntu:12.04/precise [i386])
Inst gir1.2-mutter-3.0 [3.2.2-1ubuntu1] (3.3.90-0ubuntu1 Ubuntu:12.04/precise [i386]) []
Inst libmutter0 [3.2.2-1ubuntu1] (3.3.90-0ubuntu1 Ubuntu:12.04/precise [i386]) []
Inst mutter-common [3.2.2-1ubuntu1] (3.3.90-0ubuntu1 Ubuntu:12.04/precise [all])
Inst libnm-util2 [0.9.2.0+git201202161854.8572ecf-0ubuntu7] (0.9.3.995+git201203081848.bba834f-0ubuntu1 Ubuntu:12.04/precise [i386])
Inst libnm-glib4 [0.9.2.0+git201202161854.8572ecf-0ubuntu7] (0.9.3.995+git201203081848.bba834f-0ubuntu1 Ubuntu:12.04/precise [i386])
Inst gir1.2-networkmanager-1.0 [0.9.2.0+git201202161854.8572ecf-0ubuntu7] (0.9.3.995+git201203081848.bba834f-0ubuntu1 Ubuntu:12.04/precise [i386])
Inst rhythmbox-plugin-cdrecorder [2.95.5-0ubuntu1] (2.95.5-0ubuntu2 Ubuntu:12.04/precise [i386]) []
Inst rhythmbox-plugin-zeitgeist [2.95.5-0ubuntu1] (2.95.5-0ubuntu2 Ubuntu:12.04/precise [all]) []
Inst rhythmbox-data [2.95.5-0ubuntu1] (2.95.5-0ubuntu2 Ubuntu:12.04/precise [all]) []
Inst rhythmbox-mozilla [2.95.5-0ubuntu1] (2.95.5-0ubuntu2 Ubuntu:12.04/precise [i386]) []
Inst rhythmbox [2.95.5-0ubuntu1] (2.95.5-0ubuntu2 Ubuntu:12.04/precise [i386]) [rhythmbox-plugins:i386 ]
Inst rhythmbox-plugins [2.95.5-0ubuntu1] (2.95.5-0ubuntu2 Ubuntu:12.04/precise [i386]) []
Inst librhythmbox-core5 [2.95.5-0ubuntu1] (2.95.5-0ubuntu2 Ubuntu:12.04/precise [i386]) []
Inst gir1.2-rb-3.0 [2.95.5-0ubuntu1] (2.95.5-0ubuntu2 Ubuntu:12.04/precise [i386])
Inst totem-mozilla [3.0.1-0ubuntu18] (3.0.1-0ubuntu20 Ubuntu:12.04/precise [i386]) []
Inst libtotem0 [3.0.1-0ubuntu18] (3.0.1-0ubuntu20 Ubuntu:12.04/precise [i386]) []
Inst totem-plugins [3.0.1-0ubuntu18] (3.0.1-0ubuntu20 Ubuntu:12.04/precise [i386]) []
Inst totem [3.0.1-0ubuntu18] (3.0.1-0ubuntu20 Ubuntu:12.04/precise [i386]) []
Inst totem-common [3.0.1-0ubuntu18] (3.0.1-0ubuntu20 Ubuntu:12.04/precise [all]) []
Inst libgdata-common [0.11.0-0ubuntu1] (0.11.1-1 Ubuntu:12.04/precise [all]) []
Inst libgdata13 [0.11.0-0ubuntu1] (0.11.1-1 Ubuntu:12.04/precise [i386]) []
Inst gir1.2-totem-1.0 [3.0.1-0ubuntu18] (3.0.1-0ubuntu20 Ubuntu:12.04/precise [i386])
Inst libunity9 [5.4.0-0ubuntu1] (5.6.0-0ubuntu1 Ubuntu:12.04/precise [i386])
Inst gir1.2-unity-5.0 [5.4.0-0ubuntu1] (5.6.0-0ubuntu1 Ubuntu:12.04/precise [i386])
Inst gnome-contacts [3.3.90-0ubuntu1] (3.3.91-0ubuntu1 Ubuntu:12.04/precise [i386])
Inst gnome-utils-common [3.2.1-0ubuntu4] (3.2.1-0ubuntu5 Ubuntu:12.04/precise [all])
Inst gnome-font-viewer [3.2.1-0ubuntu4] (3.2.1-0ubuntu5 Ubuntu:12.04/precise [i386])
Inst gnome-screenshot [3.3.91-0ubuntu1] (3.3.91-1ubuntu1 Ubuntu:12.04/precise [i386])
Inst gnome-tweak-tool [3.2.2-3] (3.3.4-0ubuntu1 Ubuntu:12.04/precise [all]) []
Inst gnome-shell [3.2.2.1-0ubuntu1] (3.3.90-0ubuntu1 Ubuntu:12.04/precise [i386]) []
Inst gnome-shell-common [3.2.2.1-0ubuntu1] (3.3.90-0ubuntu1 Ubuntu:12.04/precise [all])
Inst libical0 [0.44-3] (0.48-1 Ubuntu:12.04/precise [i386])
Inst gjs [1.30.1-1ubuntu1] (1.31.20-0ubuntu1 Ubuntu:12.04/precise [i386])
Inst gnome-system-log [3.2.1-0ubuntu4] (3.3.1-2ubuntu1 Ubuntu:12.04/precise [i386])
Inst gucharmap [1:3.3.1-0ubuntu1] (1:3.3.1-1ubuntu1 Ubuntu:12.04/precise [i386]) []
Inst libgucharmap-2-90-7 [1:3.3.1-0ubuntu1] (1:3.3.1-1ubuntu1 Ubuntu:12.04/precise [i386])
Inst gwibber [3.3.91-0ubuntu2] (3.3.92-0ubuntu1 Ubuntu:12.04/precise [i386]) []
Inst gwibber-service [3.3.91-0ubuntu2] (3.3.92-0ubuntu1 Ubuntu:12.04/precise [all])
Inst libgwibber2 [3.3.91-0ubuntu2] (3.3.92-0ubuntu1 Ubuntu:12.04/precise [i386])
Inst libgwibber-gtk2 [3.3.91-0ubuntu2] (3.3.92-0ubuntu1 Ubuntu:12.04/precise [i386])
Inst gwibber-service-facebook [3.3.91-0ubuntu2] (3.3.92-0ubuntu1 Ubuntu:12.04/precise [all])
Inst gwibber-service-identica [3.3.91-0ubuntu2] (3.3.92-0ubuntu1 Ubuntu:12.04/precise [all])
Inst gwibber-service-twitter [3.3.91-0ubuntu2] (3.3.92-0ubuntu1 Ubuntu:12.04/precise [all])
Inst printer-driver-hpijs [3.12.2-1ubuntu1] (3.12.2-1ubuntu2 Ubuntu:12.04/precise [i386]) []
Inst libhpmud0 [3.12.2-1ubuntu1] (3.12.2-1ubuntu2 Ubuntu:12.04/precise [i386]) [hplip:i386 ]
Inst hplip [3.12.2-1ubuntu1] (3.12.2-1ubuntu2 Ubuntu:12.04/precise [i386]) []
Inst libsane-hpaio [3.12.2-1ubuntu1] (3.12.2-1ubuntu2 Ubuntu:12.04/precise [i386]) []
Inst hplip-data [3.12.2-1ubuntu1] (3.12.2-1ubuntu2 Ubuntu:12.04/precise [all]) []
Inst printer-driver-hpcups [3.12.2-1ubuntu1] (3.12.2-1ubuntu2 Ubuntu:12.04/precise [i386])
Inst python-gobject-2 [2.28.6-9] (2.28.6-10 Ubuntu:12.04/precise [i386])
Inst hpijs [3.12.2-1ubuntu1] (3.12.2-1ubuntu2 Ubuntu:12.04/precise [all])
Inst ibus-table [1.3.9.20110827-1] (1.3.9.20110827-1ubuntu1 Ubuntu:12.04/precise [all])
Inst indicator-applet-complete [0.4.91-0ubuntu1] (0.4.92-0ubuntu1 Ubuntu:12.04/precise [i386])
Inst indicator-appmenu [0.3.91-0ubuntu3~ppa5~local2] (0.3.94-0ubuntu2 Ubuntu:12.04/precise [i386])
Inst indicator-application [0.4.91-0ubuntu2] (0.4.93-0ubuntu1 Ubuntu:12.04/precise [i386])
Inst indicator-power [1.91-0ubuntu1] (1.92-0ubuntu1 Ubuntu:12.04/precise [i386])
Inst libpackagekit-glib2-14 [0.7.2-4ubuntu1] (0.7.2-4ubuntu2 Ubuntu:12.04/precise [i386])
Inst indicator-session [0.3.92-0ubuntu3] (0.3.94-0ubuntu1 Ubuntu:12.04/precise [i386])
Inst libclutter-1.0-common [1.8.4-1] (1.9.14-0ubuntu2 Ubuntu:12.04/precise [all])
Inst libcogl-common [1.8.2-1] (1.9.8-0ubuntu3 Ubuntu:12.04/precise [all])
Inst libdconf-qt0 [0.0.0.110722-0ubuntu3] (0.0.0.110722-0ubuntu4 Ubuntu:12.04/precise [i386])
Inst libgweather-common [3.4.0-0ubuntu1] (3.4.1-0ubuntu1 Ubuntu:12.04/precise [all])
Inst libgweather-3-0 [3.4.0-0ubuntu1] (3.4.1-0ubuntu1 Ubuntu:12.04/precise [i386])
Inst libido3-0.1-0 [0.3.1-0ubuntu3] (0.3.3-0ubuntu2 Ubuntu:12.04/precise [i386])
Inst libimobiledevice2 [1.1.1-3] (1.1.1-3ubuntu1 Ubuntu:12.04/precise [i386])
Inst libindicate-gtk3 [0.6.90-0ubuntu1] (0.6.91-0ubuntu1 Ubuntu:12.04/precise [i386])
Inst libwebkitgtk-1.0-common [1.7.90-0ubuntu1] (1.7.91-0ubuntu1 Ubuntu:12.04/precise [all])
Inst libwebkitgtk-1.0-0 [1.7.90-0ubuntu1] (1.7.91-0ubuntu1 Ubuntu:12.04/precise [i386]) []
Inst libjavascriptcoregtk-1.0-0 [1.7.90-0ubuntu1] (1.7.91-0ubuntu1 Ubuntu:12.04/precise [i386])
Inst liblightdm-gobject-1-0 [1.1.7-0ubuntu1] (1.1.8-0ubuntu1 Ubuntu:12.04/precise [i386])
Inst metacity-common [1:2.34.1-1ubuntu7] (1:2.34.1-1ubuntu8 Ubuntu:12.04/precise [all])
Inst libmetacity-private0 [1:2.34.1-1ubuntu7] (1:2.34.1-1ubuntu8 Ubuntu:12.04/precise [i386])
Inst libnm-glib-vpn1 [0.9.2.0+git201202161854.8572ecf-0ubuntu7] (0.9.3.995+git201203081848.bba834f-0ubuntu1 Ubuntu:12.04/precise [i386])
Inst libnm-gtk-common [0.9.2.0+git.20120126t000800.5151959-0ubuntu4] (0.9.3.995+git.20120313t141231.c89224f-0ubuntu1 Ubuntu:12.04/precise [all])
Inst libnm-gtk0 [0.9.2.0+git.20120126t000800.5151959-0ubuntu4] (0.9.3.995+git.20120313t141231.c89224f-0ubuntu1 Ubuntu:12.04/precise [i386])
Inst libnux-2.0-0 [2.4.0+bzr590ubuntu0+320] (2.6.0-0ubuntu1 Ubuntu:12.04/precise [i386]) []
Inst libnux-2.0-common [2.4.0+bzr590ubuntu0+320] (2.6.0-0ubuntu1 Ubuntu:12.04/precise [all])
Inst unity-2d-spread [5.6.0-0ubuntu1] (5.6.0-0ubuntu2 Ubuntu:12.04/precise [i386]) []
Inst libunity-core-5.0-5 [5.4.0-r2065-l2064-p654~precise1] (5.6.0-0ubuntu4 Ubuntu:12.04/precise [i386]) []
Inst unity-services [5.4.0-r2065-l2064-p654~precise1] (5.6.0-0ubuntu4 Ubuntu:12.04/precise [i386]) []
Inst unity-2d-panel [5.6.0-0ubuntu1] (5.6.0-0ubuntu2 Ubuntu:12.04/precise [i386]) []
Inst unity-2d-shell [5.6.0-0ubuntu1] (5.6.0-0ubuntu2 Ubuntu:12.04/precise [i386]) []
Inst unity-common [5.4.0-r2065-l2064-p654~precise1] (5.6.0-0ubuntu4 Ubuntu:12.04/precise [all]) []
Inst libunity-2d-private0 [5.6.0-0ubuntu1] (5.6.0-0ubuntu2 Ubuntu:12.04/precise [i386])
Inst light-themes [0.1.8.30-0ubuntu3] (0.1.8.31-0ubuntu1 Ubuntu:12.04/precise [all])
Inst linux-headers-3.2.0-18 [3.2.0-18.28] (3.2.0-18.29 Ubuntu:12.04/precise [all])
Inst linux-headers-3.2.0-18-generic-pae [3.2.0-18.28] (3.2.0-18.29 Ubuntu:12.04/precise [i386])
Inst linux-libc-dev [3.2.0-18.28] (3.2.0-18.29 Ubuntu:12.04/precise [i386])
Inst metacity [1:2.34.1-1ubuntu7] (1:2.34.1-1ubuntu8 Ubuntu:12.04/precise [i386])
Inst modemmanager [0.5.1.97-0ubuntu1] (0.5.2.0-0ubuntu1 Ubuntu:12.04/precise [i386])
Inst myunity [3.0.0-0ubuntu1] (3.1.0-0ubuntu1 Ubuntu:12.04/precise [all])
Inst network-manager [0.9.2.0+git201202161854.8572ecf-0ubuntu7] (0.9.3.995+git201203081848.bba834f-0ubuntu1 Ubuntu:12.04/precise [i386])
Inst network-manager-gnome [0.9.2.0+git.20120126t000800.5151959-0ubuntu4] (0.9.3.995+git.20120313t141231.c89224f-0ubuntu1 Ubuntu:12.04/precise [i386])
Inst nux-tools [2.4.0+bzr590ubuntu0+320] (2.6.0-0ubuntu1 Ubuntu:12.04/precise [i386])
Inst os-prober [1.49ubuntu1] (1.50ubuntu1 Ubuntu:12.04/precise [i386])
Inst python-debtagshw [1.9+git20120302] (1.9+git20120312 Ubuntu:12.04/precise [all])
Inst python-pyatspi2 [2.3.5-0ubuntu1] (2.3.5-0ubuntu2 Ubuntu:12.04/precise [all])
Inst thunderbird-globalmenu [11.0~b5+build2-0ubuntu1] (11.0+build1-0ubuntu1 Ubuntu:12.04/precise [i386]) []
Inst thunderbird [11.0~b5+build2-0ubuntu1] (11.0+build1-0ubuntu1 Ubuntu:12.04/precise [i386]) [thunderbird-gnome-support:i386 ]
Inst thunderbird-gnome-support [11.0~b5+build2-0ubuntu1] (11.0+build1-0ubuntu1 Ubuntu:12.04/precise [i386])
Inst udisks [1.0.4-3] (1.0.4-3ubuntu1 Ubuntu:12.04/precise [i386])
Inst unity-2d [5.6.0-0ubuntu1] (5.6.0-0ubuntu2 Ubuntu:12.04/precise [all])
Inst unity-greeter [0.2.4-0ubuntu2] (0.2.5-0ubuntu1 Ubuntu:12.04/precise [i386])
Inst unity-lens-applications [5.4.0-0ubuntu2] (5.6.0-0ubuntu1 Ubuntu:12.04/precise [i386])
Inst unity-lens-files [5.4.0-0ubuntu1] (5.6.0-0ubuntu1 Ubuntu:12.04/precise [i386])
Inst unixodbc (2.2.14p2-5ubuntu3 Ubuntu:12.04/precise [i386])
Inst usb-creator-gtk [0.2.36] (0.2.37 Ubuntu:12.04/precise [i386]) []
Inst usb-creator-common [0.2.36] (0.2.37 Ubuntu:12.04/precise [i386])
Inst whoopsie [0.1.14] (0.1.16 Ubuntu:12.04/precise [i386])
Inst xserver-xorg-input-evdev [1:2.6.99.901+git20120126-0ubuntu2] (1:2.7.0-0ubuntu1 Ubuntu:12.04/precise [i386])
Inst xserver-xorg-input-synaptics [1.5.99~git20120223-0ubuntu2] (1.5.99.901-0ubuntu1 Ubuntu:12.04/precise [i386])
Inst cups-pk-helper (0.2.1.2-1 Ubuntu:12.04/precise [i386])
Inst gnome-exe-thumbnailer [0.8-0ubuntu1] (0.9-0ubuntu1 Ubuntu:12.04/precise [all])
Inst ubuntuone-installer [2.99.90-0ubuntu1] (2.99.90-0ubuntu2 Ubuntu:12.04/precise [all])
Inst ubuntuone-control-panel-gtk [2.99.90-0ubuntu1] (2.99.90-0ubuntu2 Ubuntu:12.04/precise [all]) []
Inst ubuntuone-control-panel-qt [2.99.90-0ubuntu1] (2.99.90-0ubuntu2 Ubuntu:12.04/precise [all]) []
Inst ubuntuone-control-panel-common [2.99.90-0ubuntu1] (2.99.90-0ubuntu2 Ubuntu:12.04/precise [all]) []
Inst ubuntuone-control-panel [2.99.90-0ubuntu1] (2.99.90-0ubuntu2 Ubuntu:12.04/precise [all]) []
Inst python-ubuntuone-control-panel [2.99.90-0ubuntu1] (2.99.90-0ubuntu2 Ubuntu:12.04/precise [all])
Inst sessioninstaller [0.20+bzr123-0ubuntu1] (0.20+bzr123-0ubuntu2 Ubuntu:12.04/precise [all])
Inst wine [1.4~rc6-0ubuntu1] (1.4-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf python (2.7.2-9ubuntu4 Ubuntu:12.04/precise [i386])
Conf libapt-inst1.4 (0.8.16~exp12ubuntu6 Ubuntu:12.04/precise [i386])
Conf libexpat1 (2.0.1-7.2ubuntu1 Ubuntu:12.04/precise [i386])
Conf libglib2.0-data (2.31.20-0ubuntu3 Ubuntu:12.04/precise [all])
Conf libglib2.0-0 (2.31.20-0ubuntu3 Ubuntu:12.04/precise [i386])
Conf libglib2.0-bin (2.31.20-0ubuntu3 Ubuntu:12.04/precise [i386])
Conf apparmor (2.7.101-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf bluez (4.98-2ubuntu6 Ubuntu:12.04/precise [i386])
Conf gconf2-common (3.2.5-0ubuntu1 Ubuntu:12.04/precise [all])
Conf libgconf-2-4 (3.2.5-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf gconf-service (3.2.5-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf libasound2 (1.0.25-1ubuntu9 Ubuntu:12.04/precise [i386])
Conf libcups2 (1.5.2-8 Ubuntu:12.04/precise [i386])
Conf libxfixes3 (1:5.0-4ubuntu4 Ubuntu:12.04/precise [i386])
Conf chromium-browser (17.0.963.79~r125985-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf chromium-codecs-ffmpeg (17.0.963.79~r125985-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf chromium-browser-l10n (17.0.963.79~r125985-0ubuntu1 Ubuntu:12.04/precise [all])
Conf gconf-defaults-service (3.2.5-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf libgconf2-4 (3.2.5-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf gconf2 (3.2.5-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf libcupsfilters1 (1.0.5-1 Ubuntu:12.04/precise [i386])
Conf libcupsimage2 (1.5.2-8 Ubuntu:12.04/precise [i386])
Conf cups-filters (1.0.5-1 Ubuntu:12.04/precise [i386])
Conf libcupsmime1 (1.5.2-8 Ubuntu:12.04/precise [i386])
Conf libcupscgi1 (1.5.2-8 Ubuntu:12.04/precise [i386])
Conf libcupsppdc1 (1.5.2-8 Ubuntu:12.04/precise [i386])
Conf cups-common (1.5.2-8 Ubuntu:12.04/precise [all])
Conf cups-client (1.5.2-8 Ubuntu:12.04/precise [i386])
Conf cups-bsd (1.5.2-8 Ubuntu:12.04/precise [i386])
Conf cups-ppdc (1.5.2-8 Ubuntu:12.04/precise [i386])
Conf cups (1.5.2-8 Ubuntu:12.04/precise [i386])
Conf foomatic-filters (4.0.14-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf libgl1-mesa-dri (8.0.1-0ubuntu4 Ubuntu:12.04/precise [i386])
Conf libglapi-mesa (8.0.1-0ubuntu4 Ubuntu:12.04/precise [i386])
Conf libgl1-mesa-glx (8.0.1-0ubuntu4 Ubuntu:12.04/precise [i386])
Conf gnome-desktop3-data (3.3.91-0ubuntu2 Ubuntu:12.04/precise [all])
Conf libgnome-desktop-3-2 (3.3.91-0ubuntu2 Ubuntu:12.04/precise [i386])
Conf gnome-settings-daemon (3.3.91-0ubuntu5 Ubuntu:12.04/precise [i386])
Conf gnome-screensaver (3.2.2-0ubuntu2 Ubuntu:12.04/precise [i386])
Conf libatk1.0-data (2.3.93-1 Ubuntu:12.04/precise [all])
Conf libatk1.0-0 (2.3.93-1 Ubuntu:12.04/precise [i386])
Conf bamfdaemon (0.2.112-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf libbamf3-0 (0.2.112-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf libbamf0 (0.2.112-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf libbluetooth3 (4.98-2ubuntu6 Ubuntu:12.04/precise [i386])
Conf libcogl9 (1.9.8-0ubuntu3 Ubuntu:12.04/precise [i386])
Conf libcogl-pango0 (1.9.8-0ubuntu3 Ubuntu:12.04/precise [i386])
Conf gir1.2-cogl-1.0 (1.9.8-0ubuntu3 Ubuntu:12.04/precise [i386])
Conf gir1.2-coglpango-1.0 (1.9.8-0ubuntu3 Ubuntu:12.04/precise [i386])
Conf gir1.2-atk-1.0 (2.3.93-1 Ubuntu:12.04/precise [i386])
Conf libclutter-1.0-0 (1.9.14-0ubuntu2 Ubuntu:12.04/precise [i386])
Conf gir1.2-clutter-1.0 (1.9.14-0ubuntu2 Ubuntu:12.04/precise [i386])
Conf libclutter-gst-1.0-0 (1.5.4-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf libclutter-gtk-1.0-0 (1.1.2-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf libgee2 (0.6.4-1 Ubuntu:12.04/precise [i386])
Conf cheese-common (3.3.90-0ubuntu2 Ubuntu:12.04/precise [all])
Conf libcheese3 (3.3.90-0ubuntu2 Ubuntu:12.04/precise [i386])
Conf libmx-1.0-2 (1.4.3-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf libcheese-gtk21 (3.3.90-0ubuntu2 Ubuntu:12.04/precise [i386])
Conf cheese (3.3.90-0ubuntu2 Ubuntu:12.04/precise [i386])
Conf libcupsdriver1 (1.5.2-8 Ubuntu:12.04/precise [i386])
Conf libdbusmenu-glib4 (0.5.94-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf libdbusmenu-gtk4 (0.5.94-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf gir1.2-dbusmenu-glib-0.4 (0.5.94-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf gir1.2-dbusmenu-gtk-0.4 (0.5.94-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf libdbusmenu-gtk3-4 (0.5.94-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf libsoup2.4-1 (2.37.91-1 Ubuntu:12.04/precise [i386])
Conf libsoup-gnome2.4-1 (2.37.91-1 Ubuntu:12.04/precise [i386])
Conf libjavascriptcoregtk-3.0-0 (1.7.91-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf libwebkitgtk-3.0-common (1.7.91-0ubuntu1 Ubuntu:12.04/precise [all])
Conf libwebkitgtk-3.0-0 (1.7.91-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf libgoa-1.0-common (3.3.0-1 Ubuntu:12.04/precise [all])
Conf libgoa-1.0-0 (3.3.0-1 Ubuntu:12.04/precise [i386])
Conf gnome-online-accounts (3.3.0-1 Ubuntu:12.04/precise [i386])
Conf cpp (4:4.6.3-1ubuntu5 Ubuntu:12.04/precise [i386])
Conf libidl-common (0.8.14-0.2ubuntu2 Ubuntu:12.04/precise [all])
Conf libidl0 (0.8.14-0.2ubuntu2 Ubuntu:12.04/precise [i386])
Conf libodbc1 (2.2.14p2-5ubuntu3 Ubuntu:12.04/precise [i386])
Conf libqtcore4 (4:4.8.0-1ubuntu10 Ubuntu:12.04/precise [i386])
Conf libqt4-test (4:4.8.0-1ubuntu10 Ubuntu:12.04/precise [i386])
Conf libqt4-sql (4:4.8.0-1ubuntu10 Ubuntu:12.04/precise [i386])
Conf libqt4-sql-mysql (4:4.8.0-1ubuntu10 Ubuntu:12.04/precise [i386])
Conf libqt4-sql-sqlite (4:4.8.0-1ubuntu10 Ubuntu:12.04/precise [i386])
Conf libqt4-xml (4:4.8.0-1ubuntu10 Ubuntu:12.04/precise [i386])
Conf libqt4-dbus (4:4.8.0-1ubuntu10 Ubuntu:12.04/precise [i386])
Conf libqt4-script (4:4.8.0-1ubuntu10 Ubuntu:12.04/precise [i386])
Conf libqt4-network (4:4.8.0-1ubuntu10 Ubuntu:12.04/precise [i386])
Conf libqt4-xmlpatterns (4:4.8.0-1ubuntu10 Ubuntu:12.04/precise [i386])
Conf libqtgui4 (4:4.8.0-1ubuntu10 Ubuntu:12.04/precise [i386])
Conf libqt4-declarative (4:4.8.0-1ubuntu10 Ubuntu:12.04/precise [i386])
Conf libqt4-designer (4:4.8.0-1ubuntu10 Ubuntu:12.04/precise [i386])
Conf libqt4-qt3support (4:4.8.0-1ubuntu10 Ubuntu:12.04/precise [i386])
Conf libqt4-help (4:4.8.0-1ubuntu10 Ubuntu:12.04/precise [i386])
Conf libqt4-scripttools (4:4.8.0-1ubuntu10 Ubuntu:12.04/precise [i386])
Conf libqt4-opengl (4:4.8.0-1ubuntu10 Ubuntu:12.04/precise [i386])
Conf libqt4-svg (4:4.8.0-1ubuntu10 Ubuntu:12.04/precise [i386])
Conf qdbus (4:4.8.0-1ubuntu10 Ubuntu:12.04/precise [i386])
Conf libqtwebkit4 (2.2.1-1ubuntu4 Ubuntu:12.04/precise [i386])
Conf libxatracker1 (8.0.1-0ubuntu4 Ubuntu:12.04/precise [i386])
Conf lightdm (1.1.8-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf linux-image-3.2.0-18-generic-pae (3.2.0-18.29 Ubuntu:12.04/precise [i386])
Conf nvidia-common (1:0.2.41 Ubuntu:12.04/precise [i386])
Conf qt-at-spi (0.2.0-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf libglu1-mesa (8.0.1-0ubuntu4 Ubuntu:12.04/precise [i386])
Conf wine1.4 (1.4-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf wine1.4-common (1.4-0ubuntu1 Ubuntu:12.04/precise [all])
Conf wine1.4-i386 (1.4-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf winetricks (0.0+20120308 Ubuntu:12.04/precise [i386])
Conf libcapi20-3 (1:3.12.20071127-0ubuntu11 Ubuntu:12.04/precise [i386])
Conf libdc1394-22 (2.2.0-2 Ubuntu:12.04/precise [i386])
Conf apt-utils (0.8.16~exp12ubuntu6 Ubuntu:12.04/precise [i386])
Conf keyboard-configuration (1.70ubuntu3 Ubuntu:12.04/precise [all])
Conf console-setup (1.70ubuntu3 Ubuntu:12.04/precise [all])
Conf debconf-i18n (1.5.42ubuntu1 Ubuntu:12.04/precise [all])
Conf vim-common (2:7.3.429-2ubuntu2 Ubuntu:12.04/precise [i386])
Conf vim-tiny (2:7.3.429-2ubuntu2 Ubuntu:12.04/precise [i386])
Conf apt-transport-https (0.8.16~exp12ubuntu6 Ubuntu:12.04/precise [i386])
Conf friendly-recovery (0.2.25 Ubuntu:12.04/precise [all])
Conf aptdaemon-data (0.43+bzr784-0ubuntu1 Ubuntu:12.04/precise [all])
Conf unattended-upgrades (0.76 Ubuntu:12.04/precise [all])
Conf python-software-properties (0.82.7 Ubuntu:12.04/precise [all])
Conf python-aptdaemon (0.43+bzr784-0ubuntu1 Ubuntu:12.04/precise [all])
Conf python-aptdaemon.gtkwidgets (0.43+bzr784-0ubuntu1 Ubuntu:12.04/precise [all])
Conf python-aptdaemon.gtk3widgets (0.43+bzr784-0ubuntu1 Ubuntu:12.04/precise [all])
Conf python-packagekit (0.7.2-4ubuntu2 Ubuntu:12.04/precise [all])
Conf python-aptdaemon.pkcompat (0.43+bzr784-0ubuntu1 Ubuntu:12.04/precise [all])
Conf aptdaemon (0.43+bzr784-0ubuntu1 Ubuntu:12.04/precise [all])
Conf language-selector-common (0.74 Ubuntu:12.04/precise [all])
Conf language-selector-gnome (0.74 Ubuntu:12.04/precise [all])
Conf ufw (0.31-0ubuntu2 Ubuntu:12.04/precise [all])
Conf synaptic (0.75.6 Ubuntu:12.04/precise [i386])
Conf update-manager-core (1:0.156.8 Ubuntu:12.04/precise [i386])
Conf update-manager (1:0.156.8 Ubuntu:12.04/precise [all])
Conf acpi-support (0.140 Ubuntu:12.04/precise [i386])
Conf anki (1.2.9-2 Ubuntu:12.04/precise [all])
Conf app-install-data-partner (12.12.04.1 Ubuntu:12.04/precise [all])
Conf apturl-common (0.5.1ubuntu2 Ubuntu:12.04/precise [i386])
Conf software-properties-common (0.82.7 Ubuntu:12.04/precise [all])
Conf software-properties-gtk (0.82.7 Ubuntu:12.04/precise [all])
Conf gir1.2-javascriptcoregtk-3.0 (1.7.91-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf gir1.2-soup-2.4 (2.37.91-1 Ubuntu:12.04/precise [i386])
Conf gir1.2-webkit-3.0 (1.7.91-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf apturl (0.5.1ubuntu2 Ubuntu:12.04/precise [i386])
Conf audacity-data (2.0.0-1 Ubuntu:12.04/precise [all])
Conf audacity (2.0.0-1 Ubuntu:12.04/precise [i386])
Conf baobab (3.3.3-1 Ubuntu:12.04/precise [i386])
Conf bluez-alsa (4.98-2ubuntu6 Ubuntu:12.04/precise [i386])
Conf bluez-cups (4.98-2ubuntu6 Ubuntu:12.04/precise [i386])
Conf bluez-gstreamer (4.98-2ubuntu6 Ubuntu:12.04/precise [i386])
Conf compiz-core (1:0.9.7.0+bzr3035-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf libdecoration0 (1:0.9.7.0+bzr3035-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf compiz-plugins-default (1:0.9.7.0+bzr3035-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf compiz-plugins (1:0.9.7.0+bzr3035-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf libcryptsetup4 (2:1.4.1-2ubuntu2 Ubuntu:12.04/precise [i386])
Conf cryptsetup-bin (2:1.4.1-2ubuntu2 Ubuntu:12.04/precise [i386])
Conf flashplugin-installer (11.1.102.63ubuntu2 Ubuntu:12.04/precise [i386])
Conf firefox (11.0+build1-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf firefox-globalmenu (11.0+build1-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf firefox-gnome-support (11.0+build1-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf firefox-locale-en (11.0+build1-0ubuntu1 Ubuntu:12.04/precise [all])
Conf gcc (4:4.6.3-1ubuntu5 Ubuntu:12.04/precise [i386])
Conf gdb (7.4-2012.02-0ubuntu2 Ubuntu:12.04/precise [i386])
Conf gedit-common (3.3.7-0ubuntu2 Ubuntu:12.04/precise [all])
Conf gedit (3.3.7-0ubuntu2 Ubuntu:12.04/precise [i386])
Conf gettext (0.18.1.1-5ubuntu3 Ubuntu:12.04/precise [i386])
Conf libdee-1.0-4 (1.0.6-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf gir1.2-dee-1.0 (1.0.6-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf gir1.2-gconf-2.0 (3.2.5-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf gir1.2-gdesktopenums-3.0 (3.3.90-0ubuntu2 Ubuntu:12.04/precise [i386])
Conf gir1.2-gee-1.0 (0.6.4-1 Ubuntu:12.04/precise [i386])
Conf libgjs0c (1.31.20-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf gir1.2-gjs-1.0 (1.31.20-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf libindicate5 (0.6.91-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf gir1.2-indicate-0.7 (0.6.91-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf mutter-common (3.3.90-0ubuntu1 Ubuntu:12.04/precise [all])
Conf libmutter0 (3.3.90-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf gir1.2-mutter-3.0 (3.3.90-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf libnm-util2 (0.9.3.995+git201203081848.bba834f-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf libnm-glib4 (0.9.3.995+git201203081848.bba834f-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf gir1.2-networkmanager-1.0 (0.9.3.995+git201203081848.bba834f-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf librhythmbox-core5 (2.95.5-0ubuntu2 Ubuntu:12.04/precise [i386])
Conf rhythmbox-data (2.95.5-0ubuntu2 Ubuntu:12.04/precise [all])
Conf gir1.2-rb-3.0 (2.95.5-0ubuntu2 Ubuntu:12.04/precise [i386])
Conf rhythmbox (2.95.5-0ubuntu2 Ubuntu:12.04/precise [i386])
Conf rhythmbox-plugin-cdrecorder (2.95.5-0ubuntu2 Ubuntu:12.04/precise [i386])
Conf rhythmbox-plugin-zeitgeist (2.95.5-0ubuntu2 Ubuntu:12.04/precise [all])
Conf rhythmbox-mozilla (2.95.5-0ubuntu2 Ubuntu:12.04/precise [i386])
Conf rhythmbox-plugins (2.95.5-0ubuntu2 Ubuntu:12.04/precise [i386])
Conf libtotem0 (3.0.1-0ubuntu20 Ubuntu:12.04/precise [i386])
Conf totem-common (3.0.1-0ubuntu20 Ubuntu:12.04/precise [all])
Conf totem (3.0.1-0ubuntu20 Ubuntu:12.04/precise [i386])
Conf totem-mozilla (3.0.1-0ubuntu20 Ubuntu:12.04/precise [i386])
Conf libgdata-common (0.11.1-1 Ubuntu:12.04/precise [all])
Conf libgdata13 (0.11.1-1 Ubuntu:12.04/precise [i386])
Conf gir1.2-totem-1.0 (3.0.1-0ubuntu20 Ubuntu:12.04/precise [i386])
Conf totem-plugins (3.0.1-0ubuntu20 Ubuntu:12.04/precise [i386])
Conf libunity9 (5.6.0-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf gir1.2-unity-5.0 (5.6.0-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf gnome-contacts (3.3.91-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf gnome-utils-common (3.2.1-0ubuntu5 Ubuntu:12.04/precise [all])
Conf gnome-font-viewer (3.2.1-0ubuntu5 Ubuntu:12.04/precise [i386])
Conf gnome-screenshot (3.3.91-1ubuntu1 Ubuntu:12.04/precise [i386])
Conf libical0 (0.48-1 Ubuntu:12.04/precise [i386])
Conf gnome-shell-common (3.3.90-0ubuntu1 Ubuntu:12.04/precise [all])
Conf gjs (1.31.20-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf gnome-shell (3.3.90-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf gnome-tweak-tool (3.3.4-0ubuntu1 Ubuntu:12.04/precise [all])
Conf gnome-system-log (3.3.1-2ubuntu1 Ubuntu:12.04/precise [i386])
Conf libgucharmap-2-90-7 (1:3.3.1-1ubuntu1 Ubuntu:12.04/precise [i386])
Conf gucharmap (1:3.3.1-1ubuntu1 Ubuntu:12.04/precise [i386])
Conf gwibber-service (3.3.92-0ubuntu1 Ubuntu:12.04/precise [all])
Conf libgwibber2 (3.3.92-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf libgwibber-gtk2 (3.3.92-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf gwibber (3.3.92-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf gwibber-service-facebook (3.3.92-0ubuntu1 Ubuntu:12.04/precise [all])
Conf gwibber-service-identica (3.3.92-0ubuntu1 Ubuntu:12.04/precise [all])
Conf gwibber-service-twitter (3.3.92-0ubuntu1 Ubuntu:12.04/precise [all])
Conf libhpmud0 (3.12.2-1ubuntu2 Ubuntu:12.04/precise [i386])
Conf printer-driver-hpijs (3.12.2-1ubuntu2 Ubuntu:12.04/precise [i386])
Conf libsane-hpaio (3.12.2-1ubuntu2 Ubuntu:12.04/precise [i386])
Conf hplip-data (3.12.2-1ubuntu2 Ubuntu:12.04/precise [all])
Conf printer-driver-hpcups (3.12.2-1ubuntu2 Ubuntu:12.04/precise [i386])
Conf python-gobject-2 (2.28.6-10 Ubuntu:12.04/precise [i386])
Conf hplip (3.12.2-1ubuntu2 Ubuntu:12.04/precise [i386])
Conf hpijs (3.12.2-1ubuntu2 Ubuntu:12.04/precise [all])
Conf ibus-table (1.3.9.20110827-1ubuntu1 Ubuntu:12.04/precise [all])
Conf indicator-applet-complete (0.4.92-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf indicator-appmenu (0.3.94-0ubuntu2 Ubuntu:12.04/precise [i386])
Conf indicator-application (0.4.93-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf indicator-power (1.92-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf libpackagekit-glib2-14 (0.7.2-4ubuntu2 Ubuntu:12.04/precise [i386])
Conf indicator-session (0.3.94-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf libclutter-1.0-common (1.9.14-0ubuntu2 Ubuntu:12.04/precise [all])
Conf libcogl-common (1.9.8-0ubuntu3 Ubuntu:12.04/precise [all])
Conf libdconf-qt0 (0.0.0.110722-0ubuntu4 Ubuntu:12.04/precise [i386])
Conf libgweather-common (3.4.1-0ubuntu1 Ubuntu:12.04/precise [all])
Conf libgweather-3-0 (3.4.1-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf libido3-0.1-0 (0.3.3-0ubuntu2 Ubuntu:12.04/precise [i386])
Conf libimobiledevice2 (1.1.1-3ubuntu1 Ubuntu:12.04/precise [i386])
Conf libindicate-gtk3 (0.6.91-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf libwebkitgtk-1.0-common (1.7.91-0ubuntu1 Ubuntu:12.04/precise [all])
Conf libjavascriptcoregtk-1.0-0 (1.7.91-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf libwebkitgtk-1.0-0 (1.7.91-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf liblightdm-gobject-1-0 (1.1.8-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf metacity-common (1:2.34.1-1ubuntu8 Ubuntu:12.04/precise [all])
Conf libmetacity-private0 (1:2.34.1-1ubuntu8 Ubuntu:12.04/precise [i386])
Conf libnm-glib-vpn1 (0.9.3.995+git201203081848.bba834f-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf libnm-gtk-common (0.9.3.995+git.20120313t141231.c89224f-0ubuntu1 Ubuntu:12.04/precise [all])
Conf libnm-gtk0 (0.9.3.995+git.20120313t141231.c89224f-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf libnux-2.0-common (2.6.0-0ubuntu1 Ubuntu:12.04/precise [all])
Conf libnux-2.0-0 (2.6.0-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf unity-services (5.6.0-0ubuntu4 Ubuntu:12.04/precise [i386])
Conf libunity-core-5.0-5 (5.6.0-0ubuntu4 Ubuntu:12.04/precise [i386])
Conf unity-common (5.6.0-0ubuntu4 Ubuntu:12.04/precise [all])
Conf libunity-2d-private0 (5.6.0-0ubuntu2 Ubuntu:12.04/precise [i386])
Conf unity-2d-spread (5.6.0-0ubuntu2 Ubuntu:12.04/precise [i386])
Conf unity-2d-panel (5.6.0-0ubuntu2 Ubuntu:12.04/precise [i386])
Conf unity-2d-shell (5.6.0-0ubuntu2 Ubuntu:12.04/precise [i386])
Conf light-themes (0.1.8.31-0ubuntu1 Ubuntu:12.04/precise [all])
Conf linux-headers-3.2.0-18 (3.2.0-18.29 Ubuntu:12.04/precise [all])
Conf linux-headers-3.2.0-18-generic-pae (3.2.0-18.29 Ubuntu:12.04/precise [i386])
Conf linux-libc-dev (3.2.0-18.29 Ubuntu:12.04/precise [i386])
Conf metacity (1:2.34.1-1ubuntu8 Ubuntu:12.04/precise [i386])
Conf modemmanager (0.5.2.0-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf myunity (3.1.0-0ubuntu1 Ubuntu:12.04/precise [all])
Conf network-manager (0.9.3.995+git201203081848.bba834f-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf network-manager-gnome (0.9.3.995+git.20120313t141231.c89224f-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf nux-tools (2.6.0-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf os-prober (1.50ubuntu1 Ubuntu:12.04/precise [i386])
Conf python-debtagshw (1.9+git20120312 Ubuntu:12.04/precise [all])
Conf python-pyatspi2 (2.3.5-0ubuntu2 Ubuntu:12.04/precise [all])
Conf thunderbird (11.0+build1-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf thunderbird-globalmenu (11.0+build1-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf thunderbird-gnome-support (11.0+build1-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf udisks (1.0.4-3ubuntu1 Ubuntu:12.04/precise [i386])
Conf unity-2d (5.6.0-0ubuntu2 Ubuntu:12.04/precise [all])
Conf unity-greeter (0.2.5-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf unity-lens-applications (5.6.0-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf unity-lens-files (5.6.0-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf unixodbc (2.2.14p2-5ubuntu3 Ubuntu:12.04/precise [i386])
Conf usb-creator-common (0.2.37 Ubuntu:12.04/precise [i386])
Conf usb-creator-gtk (0.2.37 Ubuntu:12.04/precise [i386])
Conf whoopsie (0.1.16 Ubuntu:12.04/precise [i386])
Conf xserver-xorg-input-evdev (1:2.7.0-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf xserver-xorg-input-synaptics (1.5.99.901-0ubuntu1 Ubuntu:12.04/precise [i386])
Conf cups-pk-helper (0.2.1.2-1 Ubuntu:12.04/precise [i386])
Conf gnome-exe-thumbnailer (0.9-0ubuntu1 Ubuntu:12.04/precise [all])
Conf ubuntuone-installer (2.99.90-0ubuntu2 Ubuntu:12.04/precise [all])
Conf python-ubuntuone-control-panel (2.99.90-0ubuntu2 Ubuntu:12.04/precise [all])
Conf ubuntuone-control-panel (2.99.90-0ubuntu2 Ubuntu:12.04/precise [all])
Conf ubuntuone-control-panel-common (2.99.90-0ubuntu2 Ubuntu:12.04/precise [all])
Conf ubuntuone-control-panel-qt (2.99.90-0ubuntu2 Ubuntu:12.04/precise [all])
Conf ubuntuone-control-panel-gtk (2.99.90-0ubuntu2 Ubuntu:12.04/precise [all])
Conf sessioninstaller (0.20+bzr123-0ubuntu2 Ubuntu:12.04/precise [all])
Conf wine (1.4-0ubuntu1 Ubuntu:12.04/precise [i386])
```

---

### Post by hrickh on 2012-03-17
Well, I should have looked elsewhere before posting...

There's a sticky in another thread dealing with this.

R.
==

---

### Post by howefield on 2012-03-17
Thread moved to the "*Ubuntu +1 (Precise Pangolin)*" forum.

---

### Post by Mathor on 2012-03-17
This might go without saying, but until the release, I would recommend only updating through ```
sudo apt-get update && sudo apt-get dist-upgrade
``` or by running synaptic package manager.

---

### Post by ptn107 on 2012-03-17
> **Mathor said:**
> This might go without saying, but until the release, I would recommend only updating through ```
sudo apt-get update && sudo apt-get dist-upgrade
``` or by running synaptic package manager.

Be careful with
```
sudo apt-get dist-upgrade
```
as it will remove packages as well.  Use this instead:
```
sudo apt-get upgrade
```

*Note that if new packages are introduced to the default precise installation you can only get them by doing a dist-upgrade.

---

### Post by Subidubi32 on 2012-03-17
When you use gnome shell above Unity don't you lost your menu bar, with Files Edit View.etc.? I tried to do this on my Ubuntu, but first it was a mixed unity/shell, where i could see the menu bar, but couldn't use it, then i lost it. So now im using the original unity.

---

### Post by grahammechanical on 2012-03-17
This is a common message. Sometimes you do not get this message.

I guess that this is to do with certain packages not being ready for inclusion in 12.04. You will notice that as you look through the list of stuff that is going to be updated there are packages without the tick mark against them. These are the ones that are not yet ready. You may get them in an update a day or two later. Then you will see that there are other packages that are supposed to be updated but not yet ready.

You will also experience things closing unexpectedly. This is often due to some packages being updated and others held back.

A message will appear giving an option to report the crash. If you accept it a report will be generated. You may then get another message saying that it cannot be reported because it is due to obsolete packages. And if you look at the Details you will see what those packages are.

There is two things you can do in this situation. One is to wait. These obsolete packages will usually be updated over the next few days.

The other thing is to use the Synaptic Package Manger (it is not installed by default) to search for the package. It may be marked with a grey icon that indicates it can be upgraded. By clicking on that line in Synaptic you can mark the package to be upgraded which you can do by clicking apply.

Look carefully at the list of packages that are going to be removed. You may find that something very important is going to be removed (such as Ubuntu-Desktop) which will break the OS. Do not let anything be removed that you are not confident about.

Regards.

---

