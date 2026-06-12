---
title: "simulated upgrade to ubuntu 14.04.2 would remove ubuntu-desktop and install unity8"
date: 2015-02-15
forum: Ubuntu Development Version
---

### Post by thorstenr_42 on 2015-02-15
Hi, 
i am curious about upgrading to the new lts enablement stack and just did a simulation with
 ```
 
apt-get install --install-recommends linux-generic-lts-utopic xserver-xorg-lts-utopic libgl1-mesa-glx-lts-utopic
```

However in the simulation it seems unity 7 would be replaced by unity 8 (ubuntu desktop package would be removed and unity8 installed). Here is the corresponding output (sry its in german)


```
HINWEIS: Dies ist nur eine Simulation!         apt-get benötigt root-Privilegien für die reale Ausführung.
         Behalten Sie ebenfalls in Hinterkopf, dass die Sperren deaktiviert
         sind, verlassen Sie sich also bezüglich des reellen aktuellen
         Status der Sperre nicht darauf!
Paketlisten werden gelesen...
Abhängigkeitsbaum wird aufgebaut....
Statusinformationen werden eingelesen....
Die folgenden zusätzlichen Pakete werden installiert:
  apparmor-easyprof apparmor-easyprof-ubuntu click click-apparmor
  gir1.2-click-0.4 gir1.2-gee-0.8 gir1.2-json-1.0 libandroid-properties1
  libboost-iostreams1.54.0 libboost-program-options1.54.0
  libboost-serialization1.54.0 libcapnp-0.4.0 libclick-0.4-0 libcontent-hub0
  libdbus-cpp2 libdee-qt5-3 libegl1-mesa-lts-utopic libepoxy0 libevdev2
  libgbm1-lts-utopic libgflags2 libgl1-mesa-dri-lts-utopic
  libglapi-mesa-lts-utopic libgles1-mesa-lts-utopic libgles2-mesa-lts-utopic
  libgoogle-glog0 libhud-client2 libhybris-common1 libjsoncpp0 libllvm3.5
  liblttng-ust-ctl2 liblttng-ust0 libmediascanner-2.0-0 libmirclient7
  libmirclientplatform-mesa libmirplatform libmirplatformgraphics-mesa
  libmirprotobuf0 libmirserver18 libpgm-5.1-0 libprocess-cpp1 libqdjango-db0
  libqmenumodel0 libqt5xmlpatterns5 libubuntu-application-api-mirserver1
  libubuntu-location-service0 libubuntu-platform-hardware-api1 libunity-api0
  libunity-mir1 libunity-scopes1 libupstart-app-launch2 liburcu1
  libusermetricsoutput1 libxatracker2-lts-utopic libzmq3 libzmqpp3
  linux-headers-3.16.0-30 linux-headers-3.16.0-30-generic
  linux-headers-generic-lts-utopic linux-image-3.16.0-30-generic
  linux-image-extra-3.16.0-30-generic linux-image-generic-lts-utopic
  mediascanner2.0 python3-apparmor python3-apparmor-click python3-click
  python3-libapparmor qmenumodel-qml qtdeclarative5-dee-plugin
  qtdeclarative5-gsettings1.0 qtdeclarative5-ubuntu-content0.1
  qtdeclarative5-ubuntu-settings-components
  qtdeclarative5-ubuntu-settings-components-assets
  qtdeclarative5-ubuntu-thumbnailer0.1
  qtdeclarative5-unity-notifications-plugin qtdeclarative5-xmllistmodel-plugin
  sqlite3 thumbnailer-service unity-plugin-scopes unity-scope-mediascanner2
  unity-scope-scopes unity8 unity8-private upstart-app-launch
  upstart-app-launch-tools usermetricsservice xserver-xorg-core-lts-utopic
  xserver-xorg-input-all-lts-utopic xserver-xorg-input-evdev-lts-utopic
  xserver-xorg-input-mouse-lts-utopic xserver-xorg-input-synaptics-lts-utopic
  xserver-xorg-input-vmmouse-lts-utopic xserver-xorg-input-wacom-lts-utopic
  xserver-xorg-video-all-lts-utopic xserver-xorg-video-ati-lts-utopic
  xserver-xorg-video-cirrus-lts-utopic xserver-xorg-video-fbdev-lts-utopic
  xserver-xorg-video-intel-lts-utopic xserver-xorg-video-mach64-lts-utopic
  xserver-xorg-video-mga-lts-utopic xserver-xorg-video-modesetting-lts-utopic
  xserver-xorg-video-neomagic-lts-utopic xserver-xorg-video-nouveau-lts-utopic
  xserver-xorg-video-openchrome-lts-utopic xserver-xorg-video-r128-lts-utopic
  xserver-xorg-video-radeon-lts-utopic xserver-xorg-video-savage-lts-utopic
  xserver-xorg-video-siliconmotion-lts-utopic
  xserver-xorg-video-sisusb-lts-utopic xserver-xorg-video-tdfx-lts-utopic
  xserver-xorg-video-trident-lts-utopic xserver-xorg-video-vesa-lts-utopic
  xserver-xorg-video-vmware-lts-utopic
Vorgeschlagene Pakete:
  content-hub fdutils linux-lts-utopic-tools sqlite3-doc xfonts-100dpi
  xfonts-75dpi gpointing-device-settings touchfreeze firmware-linux
Empfohlene Pakete:
  libegl1-mesa-drivers-lts-utopic unity-scope-click
Die folgenden Pakete werden ENTFERNT:
  account-plugin-aim account-plugin-jabber account-plugin-salut
  account-plugin-yahoo cheese empathy gir1.2-totem-1.0 gnome-contacts
  gstreamer1.0-clutter indicator-bluetooth libcheese-gtk23 libcheese7
  libclutter-1.0-0 libclutter-gst-2.0-0 libclutter-gtk-1.0-0 libcogl-pango15
  libcogl15 libegl1-mesa libegl1-mesa-drivers libgl1-mesa-dev libgl1-mesa-dri
  libgl1-mesa-glx libglapi-mesa libgles2-mesa libopenvg1-mesa libtotem0
  libwayland-egl1-mesa libxatracker2 mcp-account-manager-uoa
  nautilus-sendto-empathy totem totem-mozilla totem-plugins ubuntu-desktop
  unity-control-center unity-control-center-signon
  webaccounts-extension-common xorg xserver-xorg xserver-xorg-core
  xserver-xorg-input-all xserver-xorg-input-evdev xserver-xorg-input-mouse
  xserver-xorg-input-synaptics xserver-xorg-input-vmmouse
  xserver-xorg-input-wacom xserver-xorg-video-all xserver-xorg-video-ati
  xserver-xorg-video-cirrus xserver-xorg-video-fbdev
  xserver-xorg-video-glamoregl xserver-xorg-video-intel
  xserver-xorg-video-mach64 xserver-xorg-video-mga
  xserver-xorg-video-modesetting xserver-xorg-video-neomagic
  xserver-xorg-video-nouveau xserver-xorg-video-openchrome
  xserver-xorg-video-qxl xserver-xorg-video-r128 xserver-xorg-video-radeon
  xserver-xorg-video-s3 xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident
  xserver-xorg-video-vesa xserver-xorg-video-vmware xul-ext-webaccounts
Die folgenden NEUEN Pakete werden installiert:
  apparmor-easyprof apparmor-easyprof-ubuntu click click-apparmor
  gir1.2-click-0.4 gir1.2-gee-0.8 gir1.2-json-1.0 libandroid-properties1
  libboost-iostreams1.54.0 libboost-program-options1.54.0
  libboost-serialization1.54.0 libcapnp-0.4.0 libclick-0.4-0 libcontent-hub0
  libdbus-cpp2 libdee-qt5-3 libegl1-mesa-lts-utopic libepoxy0 libevdev2
  libgbm1-lts-utopic libgflags2 libgl1-mesa-dri-lts-utopic
  libgl1-mesa-glx-lts-utopic libglapi-mesa-lts-utopic libgles1-mesa-lts-utopic
  libgles2-mesa-lts-utopic libgoogle-glog0 libhud-client2 libhybris-common1
  libjsoncpp0 libllvm3.5 liblttng-ust-ctl2 liblttng-ust0 libmediascanner-2.0-0
  libmirclient7 libmirclientplatform-mesa libmirplatform
  libmirplatformgraphics-mesa libmirprotobuf0 libmirserver18 libpgm-5.1-0
  libprocess-cpp1 libqdjango-db0 libqmenumodel0 libqt5xmlpatterns5
  libubuntu-application-api-mirserver1 libubuntu-location-service0
  libubuntu-platform-hardware-api1 libunity-api0 libunity-mir1
  libunity-scopes1 libupstart-app-launch2 liburcu1 libusermetricsoutput1
  libxatracker2-lts-utopic libzmq3 libzmqpp3 linux-generic-lts-utopic
  linux-headers-3.16.0-30 linux-headers-3.16.0-30-generic
  linux-headers-generic-lts-utopic linux-image-3.16.0-30-generic
  linux-image-extra-3.16.0-30-generic linux-image-generic-lts-utopic
  mediascanner2.0 python3-apparmor python3-apparmor-click python3-click
  python3-libapparmor qmenumodel-qml qtdeclarative5-dee-plugin
  qtdeclarative5-gsettings1.0 qtdeclarative5-ubuntu-content0.1
  qtdeclarative5-ubuntu-settings-components
  qtdeclarative5-ubuntu-settings-components-assets
  qtdeclarative5-ubuntu-thumbnailer0.1
  qtdeclarative5-unity-notifications-plugin qtdeclarative5-xmllistmodel-plugin
  sqlite3 thumbnailer-service unity-plugin-scopes unity-scope-mediascanner2
  unity-scope-scopes unity8 unity8-private upstart-app-launch
  upstart-app-launch-tools usermetricsservice xserver-xorg-core-lts-utopic
  xserver-xorg-input-all-lts-utopic xserver-xorg-input-evdev-lts-utopic
  xserver-xorg-input-mouse-lts-utopic xserver-xorg-input-synaptics-lts-utopic
  xserver-xorg-input-vmmouse-lts-utopic xserver-xorg-input-wacom-lts-utopic
  xserver-xorg-lts-utopic xserver-xorg-video-all-lts-utopic
  xserver-xorg-video-ati-lts-utopic xserver-xorg-video-cirrus-lts-utopic
  xserver-xorg-video-fbdev-lts-utopic xserver-xorg-video-intel-lts-utopic
  xserver-xorg-video-mach64-lts-utopic xserver-xorg-video-mga-lts-utopic
  xserver-xorg-video-modesetting-lts-utopic
  xserver-xorg-video-neomagic-lts-utopic xserver-xorg-video-nouveau-lts-utopic
  xserver-xorg-video-openchrome-lts-utopic xserver-xorg-video-r128-lts-utopic
  xserver-xorg-video-radeon-lts-utopic xserver-xorg-video-savage-lts-utopic
  xserver-xorg-video-siliconmotion-lts-utopic
  xserver-xorg-video-sisusb-lts-utopic xserver-xorg-video-tdfx-lts-utopic
  xserver-xorg-video-trident-lts-utopic xserver-xorg-video-vesa-lts-utopic
  xserver-xorg-video-vmware-lts-utopic
0 aktualisiert, 116 neu installiert, 71 zu entfernen und 0 nicht aktualisiert.
Remv account-plugin-aim [3.8.6-0ubuntu9.1]
Remv account-plugin-jabber [3.8.6-0ubuntu9.1]
Remv account-plugin-salut [3.8.6-0ubuntu9.1]
Remv account-plugin-yahoo [3.8.6-0ubuntu9.1]
Remv cheese [3.10.2-0ubuntu2]
Remv nautilus-sendto-empathy [3.8.6-0ubuntu9.1]
Remv mcp-account-manager-uoa [3.8.6-0ubuntu9.1]
Remv empathy [3.8.6-0ubuntu9.1]
Remv totem-plugins [3.10.1-1ubuntu4]
Remv gir1.2-totem-1.0 [3.10.1-1ubuntu4]
Remv gnome-contacts [3.8.3-1ubuntu1]
Remv totem-mozilla [3.10.1-1ubuntu4]
Remv totem [3.10.1-1ubuntu4]
Remv xul-ext-webaccounts [0.5-0ubuntu2]
Remv webaccounts-extension-common [0.5-0ubuntu2]
Remv unity-control-center-signon [0.1.7~+14.04.20140211.2-0ubuntu4]
Remv unity-control-center [14.04.3+14.04.20140922-0ubuntu1] [indicator-bluetooth:amd64 ubuntu-desktop:amd64 ]
Remv libcheese7 [3.10.2-0ubuntu2] [indicator-bluetooth:amd64 ubuntu-desktop:amd64 libcheese-gtk23:amd64 ]
Remv gstreamer1.0-clutter [2.0.8-1build1] [indicator-bluetooth:amd64 ubuntu-desktop:amd64 libcheese-gtk23:amd64 ]
Remv indicator-bluetooth [0.0.6+14.04.20140207-0ubuntu2] [ubuntu-desktop:amd64 libcheese-gtk23:amd64 ]
Remv libcheese-gtk23 [3.10.2-0ubuntu2] [ubuntu-desktop:amd64 ]
Remv libtotem0 [3.10.1-1ubuntu4] [ubuntu-desktop:amd64 ]
Remv libclutter-gtk-1.0-0 [1.4.4-3ubuntu2.2] [ubuntu-desktop:amd64 ]
Remv libclutter-gst-2.0-0 [2.0.8-1build1] [ubuntu-desktop:amd64 ]
Remv libclutter-1.0-0 [1.16.4-0ubuntu2] [ubuntu-desktop:amd64 ]
Remv libcogl-pango15 [1.16.2-1] [ubuntu-desktop:amd64 ]
Remv libcogl15 [1.16.2-1] [ubuntu-desktop:amd64 ]
Remv libegl1-mesa-drivers [10.1.3-0ubuntu0.3] [ubuntu-desktop:amd64 ]
Remv libwayland-egl1-mesa [10.1.3-0ubuntu0.3] [ubuntu-desktop:amd64 ]
Remv ubuntu-desktop [1.325]
Remv xorg [1:7.7+1ubuntu8]
Remv xserver-xorg [1:7.7+1ubuntu8]
Remv xserver-xorg-video-all [1:7.7+1ubuntu8]
Remv xserver-xorg-video-ati [1:7.3.0-1ubuntu3.1]
Remv xserver-xorg-video-glamoregl [0.6.0-0ubuntu4]
Inst libllvm3.5 (1:3.5-4ubuntu2~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Remv xserver-xorg-video-vmware [1:13.0.2-2ubuntu1]
Remv libxatracker2 [10.1.3-0ubuntu0.3]
Remv xserver-xorg-video-radeon [1:7.3.0-1ubuntu3.1]
Remv xserver-xorg-video-intel [2:2.99.910-0ubuntu1.4]
Remv xserver-xorg-video-vesa [1:2.3.3-1build1]
Remv xserver-xorg-video-trident [1:1.3.6-0ubuntu5]
Remv xserver-xorg-video-tdfx [1:1.4.5-1build1]
Remv xserver-xorg-video-sisusb [1:0.9.6-2build1]
Remv xserver-xorg-video-sis [1:0.10.7-0ubuntu6]
Remv xserver-xorg-video-siliconmotion [1:1.7.7-2build1]
Remv xserver-xorg-video-savage [1:2.3.7-2ubuntu2]
Remv xserver-xorg-video-s3 [1:0.6.5-0ubuntu4]
Remv xserver-xorg-video-r128 [6.9.2-1build1]
Remv xserver-xorg-video-qxl [0.1.1-0ubuntu3]
Remv xserver-xorg-video-openchrome [1:0.3.3-1build1]
Remv xserver-xorg-video-nouveau [1:1.0.10-1ubuntu2]
Remv xserver-xorg-video-neomagic [1:1.2.8-1build1]
Remv xserver-xorg-video-modesetting [0.8.1-1build1]
Remv xserver-xorg-video-mga [1:1.6.3-1build1]
Remv xserver-xorg-video-mach64 [6.9.4-1build1]
Remv xserver-xorg-video-fbdev [1:0.4.4-1build1]
Remv xserver-xorg-video-cirrus [1:1.5.2-1build1]
Remv xserver-xorg-input-all [1:7.7+1ubuntu8]
Remv xserver-xorg-input-wacom [1:0.23.0-0ubuntu2]
Remv xserver-xorg-input-vmmouse [1:13.0.0-1build1]
Remv xserver-xorg-input-synaptics [1.7.4-0ubuntu1]
Remv xserver-xorg-input-mouse [1:1.9.0-1build1]
Remv xserver-xorg-input-evdev [1:2.8.2-1ubuntu2]
Remv xserver-xorg-core [2:1.15.1-0ubuntu2.6] [nvidia-331:amd64 ]
Inst xserver-xorg-core-lts-utopic (2:1.16.0-1ubuntu1.2~trusty1 Ubuntu:14.04/trusty-updates [amd64]) []
Remv libgl1-mesa-dri [10.1.3-0ubuntu0.3] [qtdeclarative5-qtquick2-plugin:amd64 libgbm1:amd64 ]
Inst libgl1-mesa-dri-lts-utopic (10.3.2-0ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst libepoxy0 (1.1-1 Ubuntu:14.04/trusty [amd64]) []
Remv libgl1-mesa-dev [10.1.3-0ubuntu0.3] []
Remv libgl1-mesa-glx [10.1.3-0ubuntu0.3] [libopencv-core2.4:amd64 phonon-backend-gstreamer:amd64 libglew1.10:amd64 gnome-session-bin:amd64 libnux-4.0-0:amd64 x11-utils:amd64 libqt5opengl5:amd64 libqt4-opengl:amd64 libwebkitgtk-1.0-0:amd64 unity:amd64 libgnome-desktop-3-7:amd64 libqtwebkit4:amd64 libreoffice-core:amd64 libvisual-0.4-plugins:amd64 libqt5quick5:amd64 libreoffice-ogltrans:amd64 libwebkitgtk-3.0-0:amd64 libglamor0:amd64 libglewmx1.10:amd64 libqt5webkit5:amd64 openjdk-7-jre:amd64 libopencv-highgui2.4:amd64 libgtkglext1:amd64 compiz-plugins-default:amd64 qtdeclarative5-ubuntu-ui-toolkit-plugin:amd64 nux-tools:amd64 vlc:amd64 libqt5gui5:amd64 libglu1-mesa:amd64 libwxgtk2.8-0:amd64 ]
Inst libgl1-mesa-glx-lts-utopic (10.3.2-0ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64]) []
Remv libgles2-mesa [10.1.3-0ubuntu0.3] [gstreamer1.0-plugins-bad:amd64 libqt5gui5:amd64 ]
Inst libgles2-mesa-lts-utopic (10.3.2-0ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64]) []
Remv libglapi-mesa [10.1.3-0ubuntu0.3] []
Inst libglapi-mesa-lts-utopic (10.3.2-0ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst libgbm1-lts-utopic (10.3.2-0ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Remv libegl1-mesa [10.1.3-0ubuntu0.3] [gstreamer1.0-plugins-bad:amd64 libqt5gui5:amd64 libgstreamer-plugins-bad1.0-0:amd64 ]
Inst libegl1-mesa-lts-utopic (10.3.2-0ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Remv libopenvg1-mesa [10.1.3-0ubuntu0.3]
Inst gir1.2-gee-0.8 (0.10.5-1ubuntu1 Ubuntu:14.04/trusty [amd64])
Inst gir1.2-json-1.0 (0.16.2-1ubuntu1 Ubuntu:14.04/trusty [amd64])
Inst libclick-0.4-0 (0.4.21.1 Ubuntu:14.04/trusty [amd64])
Inst gir1.2-click-0.4 (0.4.21.1 Ubuntu:14.04/trusty [amd64])
Inst python3-click (0.4.21.1 Ubuntu:14.04/trusty [amd64])
Inst click (0.4.21.1 Ubuntu:14.04/trusty [amd64])
Inst libboost-iostreams1.54.0 (1.54.0-4ubuntu3.1 Ubuntu:14.04/trusty-updates [amd64])
Inst libboost-program-options1.54.0 (1.54.0-4ubuntu3.1 Ubuntu:14.04/trusty-updates [amd64])
Inst libboost-serialization1.54.0 (1.54.0-4ubuntu3.1 Ubuntu:14.04/trusty-updates [amd64])
Inst liburcu1 (0.7.12-0ubuntu2 Ubuntu:14.04/trusty [amd64])
Inst liblttng-ust-ctl2 (2.4.0-4ubuntu1 Ubuntu:14.04/trusty [amd64])
Inst liblttng-ust0 (2.4.0-4ubuntu1 Ubuntu:14.04/trusty [amd64])
Inst libupstart-app-launch2 (0.3+14.04.20140411-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Inst libcontent-hub0 (0.0+14.04.20140415-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Inst libdee-qt5-3 (3.3+14.04.20140317-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Inst libgflags2 (2.0-1.1ubuntu1 Ubuntu:14.04/trusty [amd64])
Inst libgles1-mesa-lts-utopic (10.3.2-0ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Inst libgoogle-glog0 (0.3.3-1 Ubuntu:14.04/trusty [amd64])
Inst libhud-client2 (14.04+14.04.20140604-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Inst libmediascanner-2.0-0 (0.100+14.04.20140403-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Inst libmirprotobuf0 (0.1.8+14.04.20140411-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Inst libmirclientplatform-mesa (0.1.8+14.04.20140411-0ubuntu1 Ubuntu:14.04/trusty [amd64]) []
Inst libmirclient7 (0.1.8+14.04.20140411-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Inst libmirplatform (0.1.8+14.04.20140411-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Inst libmirplatformgraphics-mesa (0.1.8+14.04.20140411-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Inst libmirserver18 (0.1.8+14.04.20140411-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Inst libpgm-5.1-0 (5.1.118-1~dfsg-0.1ubuntu3 Ubuntu:14.04/trusty [amd64])
Inst libprocess-cpp1 (1.0.0+14.04.20140328-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Inst libqdjango-db0 (0.4.0-1ubuntu2 Ubuntu:14.04/trusty [amd64])
Inst libqmenumodel0 (0.2.7+14.04.20140305-0ubuntu2 Ubuntu:14.04/trusty [amd64])
Inst libqt5xmlpatterns5 (5.2.1-3 Ubuntu:14.04/trusty [amd64])
Inst libdbus-cpp2 (2.0.0+14.04.20140326-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Inst libandroid-properties1 (0.1.0+git20131207+e452e83-0ubuntu12 Ubuntu:14.04/trusty [amd64])
Inst libhybris-common1 (0.1.0+git20131207+e452e83-0ubuntu12 Ubuntu:14.04/trusty [amd64])
Inst libubuntu-platform-hardware-api1 (0.20+14.04.20140411-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Inst libubuntu-location-service0 (0.0.2+14.04.20140307-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Inst libubuntu-application-api-mirserver1 (0.20+14.04.20140411-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Inst libunity-api0 (7.80.6+14.04.20140402-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Inst libunity-mir1 (0.3+14.04.20140417-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Inst libcapnp-0.4.0 (0.4.0-1ubuntu2 Ubuntu:14.04/trusty [amd64])
Inst libjsoncpp0 (0.6.0~rc2-3ubuntu1 Ubuntu:14.04/trusty [amd64])
Inst libzmq3 (4.0.4+dfsg-2 Ubuntu:14.04/trusty [amd64])
Inst libzmqpp3 (3.2.0-0ubuntu3 Ubuntu:14.04/trusty [amd64])
Inst libunity-scopes1 (0.4.2+14.04.20140408-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Inst sqlite3 (3.8.2-1ubuntu2 Ubuntu:14.04/trusty [amd64])
Inst usermetricsservice (1.1.1+14.04.20140305-0ubuntu2 Ubuntu:14.04/trusty [amd64])
Inst libusermetricsoutput1 (1.1.1+14.04.20140305-0ubuntu2 Ubuntu:14.04/trusty [amd64])
Inst libxatracker2-lts-utopic (10.3.2-0ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Inst linux-image-3.16.0-30-generic (3.16.0-30.40~14.04.1 Ubuntu:14.04/trusty-updates [amd64])
Inst qtdeclarative5-dee-plugin (3.3+14.04.20140317-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Inst qtdeclarative5-ubuntu-content0.1 (0.0+14.04.20140415-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Inst qtdeclarative5-ubuntu-settings-components-assets (0.1+14.04.20140306-0ubuntu1 Ubuntu:14.04/trusty [all])
Inst qtdeclarative5-ubuntu-settings-components (0.1+14.04.20140306-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Inst qtdeclarative5-ubuntu-thumbnailer0.1 (1.1+14.04.20150205-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Inst qtdeclarative5-unity-notifications-plugin (0.1.1+14.04.20140402-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Inst qtdeclarative5-xmllistmodel-plugin (5.2.1-3ubuntu15.1 Ubuntu:14.04/trusty-updates [amd64])
Inst unity-plugin-scopes (0.4.0+14.04.20140408-0ubuntu2 Ubuntu:14.04/trusty [amd64])
Inst libevdev2 (1.0.99.2+dfsg-2ubuntu2 Ubuntu:14.04/trusty [amd64])
Inst qtdeclarative5-gsettings1.0 (0.1+14.04.20140408-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Inst apparmor-easyprof-ubuntu (1.1.16 Ubuntu:14.04/trusty [all])
Inst python3-libapparmor (2.8.95~2430-0ubuntu5.1 Ubuntu:14.04/trusty-updates [amd64])
Inst python3-apparmor (2.8.95~2430-0ubuntu5.1 Ubuntu:14.04/trusty-updates [amd64])
Inst apparmor-easyprof (2.8.95~2430-0ubuntu5.1 Ubuntu:14.04/trusty-updates [all])
Inst python3-apparmor-click (0.2 Ubuntu:14.04/trusty [all])
Inst click-apparmor (0.2 Ubuntu:14.04/trusty [amd64])
Inst linux-image-extra-3.16.0-30-generic (3.16.0-30.40~14.04.1 Ubuntu:14.04/trusty-updates [amd64])
Inst linux-image-generic-lts-utopic (3.16.0.30.23 Ubuntu:14.04/trusty-updates [amd64])
Inst linux-headers-3.16.0-30 (3.16.0-30.40~14.04.1 Ubuntu:14.04/trusty-updates [all])
Inst linux-headers-3.16.0-30-generic (3.16.0-30.40~14.04.1 Ubuntu:14.04/trusty-updates [amd64])
Inst linux-headers-generic-lts-utopic (3.16.0.30.23 Ubuntu:14.04/trusty-updates [amd64])
Inst linux-generic-lts-utopic (3.16.0.30.23 Ubuntu:14.04/trusty-updates [amd64])
Inst mediascanner2.0 (0.100+14.04.20140403-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Inst qmenumodel-qml (0.2.7+14.04.20140305-0ubuntu2 Ubuntu:14.04/trusty [amd64])
Inst thumbnailer-service (1.1+14.04.20150205-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Inst unity-scope-mediascanner2 (0.2+14.04.20140404-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Inst unity-scope-scopes (0.1+14.04.20140404-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Inst unity8-private (7.85+14.04.20140416-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Inst unity8 (7.85+14.04.20140416-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Inst upstart-app-launch (0.3+14.04.20140411-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Inst upstart-app-launch-tools (0.3+14.04.20140411-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Inst xserver-xorg-input-evdev-lts-utopic (1:2.9.0-1ubuntu2~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Inst xserver-xorg-input-mouse-lts-utopic (1:1.9.0-1build2~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Inst xserver-xorg-input-vmmouse-lts-utopic (1:13.0.0-1build2~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Inst xserver-xorg-input-synaptics-lts-utopic (1.8.1-1ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Inst xserver-xorg-input-wacom-lts-utopic (1:0.25.0-0ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Inst xserver-xorg-input-all-lts-utopic (1:7.7+7ubuntu2~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Inst xserver-xorg-video-r128-lts-utopic (6.9.2-1build2~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Inst xserver-xorg-video-mach64-lts-utopic (6.9.4-2~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Inst xserver-xorg-video-radeon-lts-utopic (1:7.4.0-2ubuntu2~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Inst xserver-xorg-video-ati-lts-utopic (1:7.4.0-2ubuntu2~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Inst xserver-xorg-video-cirrus-lts-utopic (1:1.5.2-2build1~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Inst xserver-xorg-video-fbdev-lts-utopic (1:0.4.4-1build2~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Inst xserver-xorg-video-intel-lts-utopic (2:2.99.914-1~exp1ubuntu4.2~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Inst xserver-xorg-video-mga-lts-utopic (1:1.6.3-2build1~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Inst xserver-xorg-video-modesetting-lts-utopic (0.9.0-1build1~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Inst xserver-xorg-video-neomagic-lts-utopic (1:1.2.8-1build2~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Inst xserver-xorg-video-nouveau-lts-utopic (1:1.0.11-1ubuntu2~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Inst xserver-xorg-video-openchrome-lts-utopic (1:0.3.3-1build2~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Inst xserver-xorg-video-savage-lts-utopic (1:2.3.7-2ubuntu3~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Inst xserver-xorg-video-siliconmotion-lts-utopic (1:1.7.7-2build2~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Inst xserver-xorg-video-sisusb-lts-utopic (1:0.9.6-2build2~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Inst xserver-xorg-video-tdfx-lts-utopic (1:1.4.5-1build2~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Inst xserver-xorg-video-trident-lts-utopic (1:1.3.6-0ubuntu6~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Inst xserver-xorg-video-vesa-lts-utopic (1:2.3.3-1build2~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Inst xserver-xorg-video-vmware-lts-utopic (1:13.0.2-3ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Inst xserver-xorg-video-all-lts-utopic (1:7.7+7ubuntu2~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Inst xserver-xorg-lts-utopic (1:7.7+7ubuntu2~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf libllvm3.5 (1:3.5-4ubuntu2~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf libgl1-mesa-dri-lts-utopic (10.3.2-0ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf libgbm1-lts-utopic (10.3.2-0ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf libegl1-mesa-lts-utopic (10.3.2-0ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf libepoxy0 (1.1-1 Ubuntu:14.04/trusty [amd64])
Conf libglapi-mesa-lts-utopic (10.3.2-0ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf libgl1-mesa-glx-lts-utopic (10.3.2-0ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-core-lts-utopic (2:1.16.0-1ubuntu1.2~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf libgles2-mesa-lts-utopic (10.3.2-0ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf gir1.2-gee-0.8 (0.10.5-1ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf gir1.2-json-1.0 (0.16.2-1ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf libclick-0.4-0 (0.4.21.1 Ubuntu:14.04/trusty [amd64])
Conf gir1.2-click-0.4 (0.4.21.1 Ubuntu:14.04/trusty [amd64])
Conf python3-click (0.4.21.1 Ubuntu:14.04/trusty [amd64])
Conf click (0.4.21.1 Ubuntu:14.04/trusty [amd64])
Conf libboost-iostreams1.54.0 (1.54.0-4ubuntu3.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libboost-program-options1.54.0 (1.54.0-4ubuntu3.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libboost-serialization1.54.0 (1.54.0-4ubuntu3.1 Ubuntu:14.04/trusty-updates [amd64])
Conf liburcu1 (0.7.12-0ubuntu2 Ubuntu:14.04/trusty [amd64])
Conf liblttng-ust-ctl2 (2.4.0-4ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf liblttng-ust0 (2.4.0-4ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf libupstart-app-launch2 (0.3+14.04.20140411-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf libcontent-hub0 (0.0+14.04.20140415-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf libdee-qt5-3 (3.3+14.04.20140317-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf libgflags2 (2.0-1.1ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf libgles1-mesa-lts-utopic (10.3.2-0ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf libgoogle-glog0 (0.3.3-1 Ubuntu:14.04/trusty [amd64])
Conf libhud-client2 (14.04+14.04.20140604-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Conf libmediascanner-2.0-0 (0.100+14.04.20140403-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf libmirprotobuf0 (0.1.8+14.04.20140411-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf libmirclientplatform-mesa (0.1.8+14.04.20140411-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf libmirclient7 (0.1.8+14.04.20140411-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf libmirplatform (0.1.8+14.04.20140411-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf libmirplatformgraphics-mesa (0.1.8+14.04.20140411-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf libmirserver18 (0.1.8+14.04.20140411-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf libpgm-5.1-0 (5.1.118-1~dfsg-0.1ubuntu3 Ubuntu:14.04/trusty [amd64])
Conf libprocess-cpp1 (1.0.0+14.04.20140328-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf libqdjango-db0 (0.4.0-1ubuntu2 Ubuntu:14.04/trusty [amd64])
Conf libqmenumodel0 (0.2.7+14.04.20140305-0ubuntu2 Ubuntu:14.04/trusty [amd64])
Conf libqt5xmlpatterns5 (5.2.1-3 Ubuntu:14.04/trusty [amd64])
Conf libdbus-cpp2 (2.0.0+14.04.20140326-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf libandroid-properties1 (0.1.0+git20131207+e452e83-0ubuntu12 Ubuntu:14.04/trusty [amd64])
Conf libhybris-common1 (0.1.0+git20131207+e452e83-0ubuntu12 Ubuntu:14.04/trusty [amd64])
Conf libubuntu-platform-hardware-api1 (0.20+14.04.20140411-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf libubuntu-location-service0 (0.0.2+14.04.20140307-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf libubuntu-application-api-mirserver1 (0.20+14.04.20140411-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf libunity-api0 (7.80.6+14.04.20140402-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf libunity-mir1 (0.3+14.04.20140417-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf libcapnp-0.4.0 (0.4.0-1ubuntu2 Ubuntu:14.04/trusty [amd64])
Conf libjsoncpp0 (0.6.0~rc2-3ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf libzmq3 (4.0.4+dfsg-2 Ubuntu:14.04/trusty [amd64])
Conf libzmqpp3 (3.2.0-0ubuntu3 Ubuntu:14.04/trusty [amd64])
Conf libunity-scopes1 (0.4.2+14.04.20140408-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf sqlite3 (3.8.2-1ubuntu2 Ubuntu:14.04/trusty [amd64])
Conf usermetricsservice (1.1.1+14.04.20140305-0ubuntu2 Ubuntu:14.04/trusty [amd64])
Conf libusermetricsoutput1 (1.1.1+14.04.20140305-0ubuntu2 Ubuntu:14.04/trusty [amd64])
Conf libxatracker2-lts-utopic (10.3.2-0ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf linux-image-3.16.0-30-generic (3.16.0-30.40~14.04.1 Ubuntu:14.04/trusty-updates [amd64])
Conf qtdeclarative5-dee-plugin (3.3+14.04.20140317-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf qtdeclarative5-ubuntu-content0.1 (0.0+14.04.20140415-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf qtdeclarative5-ubuntu-settings-components-assets (0.1+14.04.20140306-0ubuntu1 Ubuntu:14.04/trusty [all])
Conf qtdeclarative5-ubuntu-settings-components (0.1+14.04.20140306-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf qtdeclarative5-ubuntu-thumbnailer0.1 (1.1+14.04.20150205-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Conf qtdeclarative5-unity-notifications-plugin (0.1.1+14.04.20140402-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf qtdeclarative5-xmllistmodel-plugin (5.2.1-3ubuntu15.1 Ubuntu:14.04/trusty-updates [amd64])
Conf unity-plugin-scopes (0.4.0+14.04.20140408-0ubuntu2 Ubuntu:14.04/trusty [amd64])
Conf libevdev2 (1.0.99.2+dfsg-2ubuntu2 Ubuntu:14.04/trusty [amd64])
Conf qtdeclarative5-gsettings1.0 (0.1+14.04.20140408-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf apparmor-easyprof-ubuntu (1.1.16 Ubuntu:14.04/trusty [all])
Conf python3-libapparmor (2.8.95~2430-0ubuntu5.1 Ubuntu:14.04/trusty-updates [amd64])
Conf python3-apparmor (2.8.95~2430-0ubuntu5.1 Ubuntu:14.04/trusty-updates [amd64])
Conf apparmor-easyprof (2.8.95~2430-0ubuntu5.1 Ubuntu:14.04/trusty-updates [all])
Conf python3-apparmor-click (0.2 Ubuntu:14.04/trusty [all])
Conf click-apparmor (0.2 Ubuntu:14.04/trusty [amd64])
Conf linux-image-extra-3.16.0-30-generic (3.16.0-30.40~14.04.1 Ubuntu:14.04/trusty-updates [amd64])
Conf linux-image-generic-lts-utopic (3.16.0.30.23 Ubuntu:14.04/trusty-updates [amd64])
Conf linux-headers-3.16.0-30 (3.16.0-30.40~14.04.1 Ubuntu:14.04/trusty-updates [all])
Conf linux-headers-3.16.0-30-generic (3.16.0-30.40~14.04.1 Ubuntu:14.04/trusty-updates [amd64])
Conf linux-headers-generic-lts-utopic (3.16.0.30.23 Ubuntu:14.04/trusty-updates [amd64])
Conf linux-generic-lts-utopic (3.16.0.30.23 Ubuntu:14.04/trusty-updates [amd64])
Conf mediascanner2.0 (0.100+14.04.20140403-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf qmenumodel-qml (0.2.7+14.04.20140305-0ubuntu2 Ubuntu:14.04/trusty [amd64])
Conf thumbnailer-service (1.1+14.04.20150205-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Conf unity-scope-mediascanner2 (0.2+14.04.20140404-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf unity-scope-scopes (0.1+14.04.20140404-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf unity8-private (7.85+14.04.20140416-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf unity8 (7.85+14.04.20140416-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf upstart-app-launch (0.3+14.04.20140411-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf upstart-app-launch-tools (0.3+14.04.20140411-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf xserver-xorg-input-evdev-lts-utopic (1:2.9.0-1ubuntu2~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-input-mouse-lts-utopic (1:1.9.0-1build2~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-input-vmmouse-lts-utopic (1:13.0.0-1build2~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-input-synaptics-lts-utopic (1.8.1-1ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-input-wacom-lts-utopic (1:0.25.0-0ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-input-all-lts-utopic (1:7.7+7ubuntu2~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-video-r128-lts-utopic (6.9.2-1build2~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-video-mach64-lts-utopic (6.9.4-2~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-video-radeon-lts-utopic (1:7.4.0-2ubuntu2~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-video-ati-lts-utopic (1:7.4.0-2ubuntu2~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-video-cirrus-lts-utopic (1:1.5.2-2build1~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-video-fbdev-lts-utopic (1:0.4.4-1build2~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-video-intel-lts-utopic (2:2.99.914-1~exp1ubuntu4.2~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-video-mga-lts-utopic (1:1.6.3-2build1~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-video-modesetting-lts-utopic (0.9.0-1build1~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-video-neomagic-lts-utopic (1:1.2.8-1build2~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-video-nouveau-lts-utopic (1:1.0.11-1ubuntu2~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-video-openchrome-lts-utopic (1:0.3.3-1build2~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-video-savage-lts-utopic (1:2.3.7-2ubuntu3~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-video-siliconmotion-lts-utopic (1:1.7.7-2build2~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-video-sisusb-lts-utopic (1:0.9.6-2build2~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-video-tdfx-lts-utopic (1:1.4.5-1build2~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-video-trident-lts-utopic (1:1.3.6-0ubuntu6~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-video-vesa-lts-utopic (1:2.3.3-1build2~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-video-vmware-lts-utopic (1:13.0.2-3ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-video-all-lts-utopic (1:7.7+7ubuntu2~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-lts-utopic (1:7.7+7ubuntu2~trusty1 Ubuntu:14.04/trusty-updates [amd64])
```

---

### Post by grahammechanical on 2015-02-15
Is this a default install of 14.04.1? Or have you installed the Unity8 desktop session. I do see where it is going to remove ubuntu desktop and that is a worry but I do not see where it is going to remove Unity 7 (package name unity).

Unity 7 and Unity 8 do coexist. I am running Vivid and I have both Unity 7 and Unity 8 (installed by unity8-desktop-session-mir). I do not know why ubuntu-desktop 1.325 is being removed. The version in vivid is 1.328. I do not know the version in utopic.

We do know that the build images for the 14.04.2 ISOs were failing the automatic tests and release date was put back. Could the removal of ubuntu-desktop be the reason?

Regards.

---

### Post by thorstenr_42 on 2015-02-15
oh sry, I wrongly assumed unity7 would be in ubuntu-desktop. Yes, it is a default ubuntu 14.04.1 installation and i have not installed unity 8

---

### Post by mc4man on 2015-02-15
The mesa libs are always a bit of an issue. This was something that would work ok on one install, but not on another 
(on the non-working it would be a matter of discovering an offending installed package, could be a non repo mesa or Intel driver package

edit; a shorter command
```
sudo apt-get install -s --install-recommends linux-generic-lts-utopic xserver-xorg-lts-utopic \
libgl1-mesa-glx-lts-utopic libegl1-mesa-drivers-lts-utopic
```

What your are looking for is number of packages removed to be very close or the same to number of packages installed, example here - 
[http://ubuntuforums.org/showthread.php?t=2264341&p=13224623&viewfull=1#post13224623](http://ubuntuforums.org/showthread.php?t=2264341&p=13224623&viewfull=1#post13224623)
(- do note unity8 should not be installed as part of the mesa lts install...

By & large best way is to just install 14.04.2 when it releases or wait for the next lts - 14.10 mesa isn't much improved & Ubuntu has few resources for the Desktop atm

---

### Post by grahammechanical on 2015-02-15
My advice if you want to run this upgrade as a test would be to first install an alternative desktop, such as gnome flashback. Then if ubuntu-desktop is removed and you cannot load into Unity, then at the login screen you can select either Gnome Flashback (Compiz) or Gnome Flashback (Metacity). That should get you to a working desktop where you can reinstall ubuntu-desktop.

I have Gnome Flashback installed just for those occasions when Compiz or Unity gets broken. When testing it is useful to have an alternative desktop installed. I am waiting for 14.04.2 to be officially released then I shall see what happens when my install of 14.04.1 is upgraded.

I have no idea why you are getting those unity8 bits.

Regards.

---

### Post by mc4man on 2015-02-15
> **grahammechanical said:**
> My advice if you want to run this upgrade as a test would be to first install an alternative desktop, such as gnome flashback. Then if ubuntu-desktop is removed and you cannot load into Unity, then at the login screen you can select either Gnome Flashback (Compiz) or Gnome Flashback (Metacity). That should get you to a working desktop where you can reinstall ubuntu-desktop.

I have Gnome Flashback installed just for those occasions when Compiz or Unity gets broken. When testing it is useful to have an alternative desktop installed. I am waiting for 14.04.2 to be officially released then I shall see what happens when my install of 14.04.1 is upgraded.

I have no idea why you are getting those unity8 bits.

Regards.

It's because the command he used is wrong (incomplete). What may have been good for 12.04.x isn't necessarily so for 14.04.
I would not recommend doing a screwed up install & then try to fix later.

Just run simulations till it comes up clean ( the -s option for apt-get
For most default installs of 14.04.1 it will be mid 40 or so packages removed & the same installed (may be slight difference

The kernel can be installed by itself, the mesa install will bring in the lts kernel so in that case doesn't matter if it's part of the command or not.
There may be some obsure packages that will be removed in a lts upgrade, [one example]("https://bugs.launchpad.net/ubuntu/+source/desmume/+bug/1422139") would be libosmesa6 which is a dep of desmume. There could be others..

Users with non standard installs may need to manage a little differently, that's why running a sim till good is the best way for this.

Ex. here where I've already done the kernel - 42 packages in, 43 out. 
```
doug@doug-Lenovo-IdeaPad-Y510P:~$ sudo apt-get install -s --install-recommends xserver-xorg-lts-utopic libgl1-mesa-glx-lts-utopic libgl1-mesa-dri-lts-utopic libgles2-mesa-lts-utopic libgles1-mesa-lts-utopic libopenvg1-mesa-lts-utopic  xserver-xorg-core-lts-utopic
[sudo] password for doug: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libegl1-mesa-drivers-lts-utopic libegl1-mesa-lts-utopic libepoxy0 libevdev2
  libgbm1-lts-utopic libglapi-mesa-lts-utopic libllvm3.5
  libwayland-egl1-mesa-lts-utopic libxatracker2-lts-utopic
  xserver-xorg-input-all-lts-utopic xserver-xorg-input-evdev-lts-utopic
  xserver-xorg-input-mouse-lts-utopic xserver-xorg-input-synaptics-lts-utopic
  xserver-xorg-input-vmmouse-lts-utopic xserver-xorg-input-wacom-lts-utopic
  xserver-xorg-video-all-lts-utopic xserver-xorg-video-ati-lts-utopic
  xserver-xorg-video-cirrus-lts-utopic xserver-xorg-video-fbdev-lts-utopic
  xserver-xorg-video-intel-lts-utopic xserver-xorg-video-mach64-lts-utopic
  xserver-xorg-video-mga-lts-utopic xserver-xorg-video-modesetting-lts-utopic
  xserver-xorg-video-neomagic-lts-utopic xserver-xorg-video-nouveau-lts-utopic
  xserver-xorg-video-openchrome-lts-utopic xserver-xorg-video-r128-lts-utopic
  xserver-xorg-video-radeon-lts-utopic xserver-xorg-video-savage-lts-utopic
  xserver-xorg-video-siliconmotion-lts-utopic
  xserver-xorg-video-sisusb-lts-utopic xserver-xorg-video-tdfx-lts-utopic
  xserver-xorg-video-trident-lts-utopic xserver-xorg-video-vesa-lts-utopic
  xserver-xorg-video-vmware-lts-utopic
Suggested packages:
  xfonts-100dpi xfonts-75dpi gpointing-device-settings touchfreeze
  firmware-linux
The following packages will be REMOVED:
  libegl1-mesa libegl1-mesa-drivers libgl1-mesa-dri libgl1-mesa-glx
  libglapi-mesa libgles1-mesa libgles2-mesa libopenvg1-mesa
  libwayland-egl1-mesa libxatracker2 mesa-vdpau-drivers xserver-xorg
  xserver-xorg-core xserver-xorg-input-all xserver-xorg-input-evdev
  xserver-xorg-input-mouse xserver-xorg-input-synaptics
  xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-all
  xserver-xorg-video-ati xserver-xorg-video-cirrus xserver-xorg-video-fbdev
  xserver-xorg-video-glamoregl xserver-xorg-video-intel
  xserver-xorg-video-mach64 xserver-xorg-video-mga
  xserver-xorg-video-modesetting xserver-xorg-video-neomagic
  xserver-xorg-video-nouveau xserver-xorg-video-openchrome
  xserver-xorg-video-qxl xserver-xorg-video-r128 xserver-xorg-video-radeon
  xserver-xorg-video-s3 xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident
  xserver-xorg-video-vesa xserver-xorg-video-vmware
The following NEW packages will be installed:
  libegl1-mesa-drivers-lts-utopic libegl1-mesa-lts-utopic libepoxy0 libevdev2
  libgbm1-lts-utopic libgl1-mesa-dri-lts-utopic libgl1-mesa-glx-lts-utopic
  libglapi-mesa-lts-utopic libgles1-mesa-lts-utopic libgles2-mesa-lts-utopic
  libllvm3.5 libopenvg1-mesa-lts-utopic libwayland-egl1-mesa-lts-utopic
  libxatracker2-lts-utopic xserver-xorg-core-lts-utopic
  xserver-xorg-input-all-lts-utopic xserver-xorg-input-evdev-lts-utopic
  xserver-xorg-input-mouse-lts-utopic xserver-xorg-input-synaptics-lts-utopic
  xserver-xorg-input-vmmouse-lts-utopic xserver-xorg-input-wacom-lts-utopic
  xserver-xorg-lts-utopic xserver-xorg-video-all-lts-utopic
  xserver-xorg-video-ati-lts-utopic xserver-xorg-video-cirrus-lts-utopic
  xserver-xorg-video-fbdev-lts-utopic xserver-xorg-video-intel-lts-utopic
  xserver-xorg-video-mach64-lts-utopic xserver-xorg-video-mga-lts-utopic
  xserver-xorg-video-modesetting-lts-utopic
  xserver-xorg-video-neomagic-lts-utopic xserver-xorg-video-nouveau-lts-utopic
  xserver-xorg-video-openchrome-lts-utopic xserver-xorg-video-r128-lts-utopic
  xserver-xorg-video-radeon-lts-utopic xserver-xorg-video-savage-lts-utopic
  xserver-xorg-video-siliconmotion-lts-utopic
  xserver-xorg-video-sisusb-lts-utopic xserver-xorg-video-tdfx-lts-utopic
  xserver-xorg-video-trident-lts-utopic xserver-xorg-video-vesa-lts-utopic
  xserver-xorg-video-vmware-lts-utopic
0 upgraded, 42 newly installed, 43 to remove and 55 not upgraded.
Remv xserver-xorg-video-all [1:7.7+1ubuntu8.1]
Remv xserver-xorg-video-ati [1:7.3.0-1ubuntu3.1]
Remv xserver-xorg-video-glamoregl [0.6.0-0ubuntu4]
Remv libegl1-mesa [10.1.3-0ubuntu0.3] [libcogl15:amd64 libegl1-mesa-drivers:amd64 gstreamer1.0-plugins-bad:amd64 libwayland-egl1-mesa:amd64 vlc:amd64 libqt5gui5:amd64 libgstreamer-plugins-bad1.0-0:amd64 ]
Remv xserver-xorg [1:7.7+1ubuntu8.1] [libcogl15:amd64 xorg:amd64 libegl1-mesa-drivers:amd64 gstreamer1.0-plugins-bad:amd64 libwayland-egl1-mesa:amd64 vlc:amd64 libqt5gui5:amd64 libgstreamer-plugins-bad1.0-0:amd64 ]
Inst libegl1-mesa-lts-utopic (10.3.2-0ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64]) [xorg:amd64 libegl1-mesa-drivers:amd64 libwayland-egl1-mesa:amd64 ]
Remv xserver-xorg-video-radeon [1:7.3.0-1ubuntu3.1] [xorg:amd64 libegl1-mesa-drivers:amd64 libwayland-egl1-mesa:amd64 ]
Remv xserver-xorg-video-intel [2:2.99.910-0ubuntu1.4] [xorg:amd64 libegl1-mesa-drivers:amd64 libwayland-egl1-mesa:amd64 ]
Remv xserver-xorg-input-all [1:7.7+1ubuntu8.1] [xorg:amd64 libegl1-mesa-drivers:amd64 libwayland-egl1-mesa:amd64 ]
Remv xserver-xorg-input-wacom [1:0.23.0-0ubuntu2] [xorg:amd64 libegl1-mesa-drivers:amd64 libwayland-egl1-mesa:amd64 ]
Remv xserver-xorg-core [2:1.15.1-0ubuntu2.6] [xserver-xorg-video-vmware:amd64 xserver-xorg-video-siliconmotion:amd64 xorg:amd64 libegl1-mesa-drivers:amd64 xserver-xorg-video-sisusb:amd64 xserver-xorg-video-savage:amd64 xserver-xorg-video-neomagic:amd64 xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-vesa:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-qxl:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-tdfx:amd64 xserver-xorg-video-fbdev:amd64 libwayland-egl1-mesa:amd64 xserver-xorg-video-trident:amd64 xserver-xorg-video-openchrome:amd64 xserver-xorg-input-vmmouse:amd64 xserver-xorg-video-sis:amd64 xserver-xorg-video-s3:amd64 xserver-xorg-video-modesetting:amd64 xserver-xorg-video-r128:amd64 xserver-xorg-video-mga:amd64 xserver-xorg-video-nouveau:amd64 ]
Remv libgl1-mesa-dri [10.1.3-0ubuntu0.3] [xserver-xorg-video-vmware:amd64 xserver-xorg-video-siliconmotion:amd64 xorg:amd64 libegl1-mesa-drivers:amd64 xserver-xorg-video-sisusb:amd64 xserver-xorg-video-savage:amd64 xserver-xorg-video-neomagic:amd64 xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 mesa-vdpau-drivers:amd64 xserver-xorg-video-vesa:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-qxl:amd64 libxatracker2:amd64 qtdeclarative5-qtquick2-plugin:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-tdfx:amd64 xserver-xorg-video-fbdev:amd64 libwayland-egl1-mesa:amd64 xserver-xorg-video-trident:amd64 libgbm1:amd64 xserver-xorg-video-openchrome:amd64 xserver-xorg-input-vmmouse:amd64 xserver-xorg-video-sis:amd64 xserver-xorg-video-s3:amd64 xserver-xorg-video-modesetting:amd64 xserver-xorg-video-r128:amd64 xserver-xorg-video-mga:amd64 xserver-xorg-video-nouveau:amd64 ]
Inst libgl1-mesa-dri-lts-utopic (10.3.2-0ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64]) [xserver-xorg-video-vmware:amd64 xserver-xorg-video-siliconmotion:amd64 xorg:amd64 libegl1-mesa-drivers:amd64 xserver-xorg-video-sisusb:amd64 xserver-xorg-video-savage:amd64 xserver-xorg-video-neomagic:amd64 xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-vesa:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-qxl:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-tdfx:amd64 xserver-xorg-video-fbdev:amd64 libwayland-egl1-mesa:amd64 xserver-xorg-video-trident:amd64 xserver-xorg-video-openchrome:amd64 xserver-xorg-input-vmmouse:amd64 xserver-xorg-video-sis:amd64 xserver-xorg-video-s3:amd64 xserver-xorg-video-modesetting:amd64 xserver-xorg-video-r128:amd64 xserver-xorg-video-mga:amd64 xserver-xorg-video-nouveau:amd64 ]
Remv mesa-vdpau-drivers [10.1.3-0ubuntu0.3] [xserver-xorg-video-vmware:amd64 xserver-xorg-video-siliconmotion:amd64 xorg:amd64 libegl1-mesa-drivers:amd64 xserver-xorg-video-sisusb:amd64 xserver-xorg-video-savage:amd64 xserver-xorg-video-neomagic:amd64 xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-vesa:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-qxl:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-tdfx:amd64 xserver-xorg-video-fbdev:amd64 libwayland-egl1-mesa:amd64 xserver-xorg-video-trident:amd64 xserver-xorg-video-openchrome:amd64 xserver-xorg-input-vmmouse:amd64 xserver-xorg-video-sis:amd64 xserver-xorg-video-s3:amd64 xserver-xorg-video-modesetting:amd64 xserver-xorg-video-r128:amd64 xserver-xorg-video-mga:amd64 xserver-xorg-video-nouveau:amd64 ]
Remv libgl1-mesa-glx [10.1.3-0ubuntu0.3] [libopencv-core2.4:amd64 xserver-xorg-video-vmware:amd64 xserver-xorg-video-siliconmotion:amd64 compiz-plugins:amd64 libcogl15:amd64 libglew1.10:amd64 gnome-session-bin:amd64 mesa-utils:amd64 libnux-4.0-0:amd64 xorg:amd64 x11-utils:amd64 libegl1-mesa-drivers:amd64 libqt5opengl5:amd64 xserver-xorg-video-sisusb:amd64 audacious-plugins:amd64 xserver-xorg-video-savage:amd64 libavdevice-ffmpeg56:amd64 libqt4-opengl:amd64 libwebkitgtk-1.0-0:amd64 xserver-xorg-video-neomagic:amd64 unity:amd64 libgnome-desktop-3-7:amd64 vdpau-va-driver:amd64 xserver-xorg-input-synaptics:amd64 libqtwebkit4:amd64 libreoffice-core:amd64 libvisual-0.4-plugins:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 gnome-control-center:amd64 libmpv1:amd64 xserver-xorg-video-vesa:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-qxl:amd64 libqt5quick5:amd64 libwebkitgtk-3.0-0:amd64 libglamor0:amd64 libglewmx1.10:amd64 bomi:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-tdfx:amd64 mpv:amd64 xserver-xorg-video-fbdev:amd64 libwayland-egl1-mesa:amd64 libqt5webkit5:amd64 openjdk-7-jre:amd64 xserver-xorg-video-trident:amd64 libopencv-highgui2.4:amd64 libgtkglext1:amd64 libwxgtk3.0-0:amd64 compiz-plugins-default:amd64 unity-control-center:amd64 xserver-xorg-video-openchrome:amd64 qtdeclarative5-ubuntu-ui-toolkit-plugin:amd64 xserver-xorg-input-vmmouse:amd64 nux-tools:amd64 vlc:amd64 xserver-xorg-video-sis:amd64 libqt5gui5:amd64 mplayer:amd64 xserver-xorg-video-s3:amd64 libwebkit2gtk-3.0-25:amd64 xserver-xorg-video-modesetting:amd64 xserver-xorg-video-r128:amd64 libva-glx1:amd64 libglu1-mesa:amd64 xserver-xorg-video-mga:amd64 xserver-xorg-video-nouveau:amd64 ]
Inst libgl1-mesa-glx-lts-utopic (10.3.2-0ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64]) [xserver-xorg-video-vmware:amd64 xserver-xorg-video-siliconmotion:amd64 xorg:amd64 libegl1-mesa-drivers:amd64 xserver-xorg-video-sisusb:amd64 xserver-xorg-video-savage:amd64 xserver-xorg-video-neomagic:amd64 xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-vesa:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-qxl:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-tdfx:amd64 xserver-xorg-video-fbdev:amd64 libwayland-egl1-mesa:amd64 xserver-xorg-video-trident:amd64 xserver-xorg-video-openchrome:amd64 xserver-xorg-input-vmmouse:amd64 xserver-xorg-video-sis:amd64 xserver-xorg-video-s3:amd64 xserver-xorg-video-modesetting:amd64 xserver-xorg-video-r128:amd64 xserver-xorg-video-mga:amd64 xserver-xorg-video-nouveau:amd64 ]
Remv libgles2-mesa [10.1.3-0ubuntu0.3] [xserver-xorg-video-vmware:amd64 xserver-xorg-video-siliconmotion:amd64 xorg:amd64 libegl1-mesa-drivers:amd64 xserver-xorg-video-sisusb:amd64 xserver-xorg-video-savage:amd64 xserver-xorg-video-neomagic:amd64 xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-vesa:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-qxl:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-tdfx:amd64 gstreamer1.0-plugins-bad:amd64 xserver-xorg-video-fbdev:amd64 libwayland-egl1-mesa:amd64 xserver-xorg-video-trident:amd64 xserver-xorg-video-openchrome:amd64 xserver-xorg-input-vmmouse:amd64 vlc:amd64 xserver-xorg-video-sis:amd64 libqt5gui5:amd64 xserver-xorg-video-s3:amd64 xserver-xorg-video-modesetting:amd64 xserver-xorg-video-r128:amd64 xserver-xorg-video-mga:amd64 xserver-xorg-video-nouveau:amd64 ]
Inst libgles2-mesa-lts-utopic (10.3.2-0ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64]) [xserver-xorg-video-vmware:amd64 xserver-xorg-video-siliconmotion:amd64 xorg:amd64 libegl1-mesa-drivers:amd64 xserver-xorg-video-sisusb:amd64 xserver-xorg-video-savage:amd64 xserver-xorg-video-neomagic:amd64 xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-vesa:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-qxl:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-tdfx:amd64 xserver-xorg-video-fbdev:amd64 libwayland-egl1-mesa:amd64 xserver-xorg-video-trident:amd64 xserver-xorg-video-openchrome:amd64 xserver-xorg-input-vmmouse:amd64 xserver-xorg-video-sis:amd64 xserver-xorg-video-s3:amd64 xserver-xorg-video-modesetting:amd64 xserver-xorg-video-r128:amd64 xserver-xorg-video-mga:amd64 xserver-xorg-video-nouveau:amd64 ]
Remv libglapi-mesa [10.1.3-0ubuntu0.3] [xserver-xorg-video-vmware:amd64 xserver-xorg-video-siliconmotion:amd64 xorg:amd64 libegl1-mesa-drivers:amd64 xserver-xorg-video-sisusb:amd64 xserver-xorg-video-savage:amd64 xserver-xorg-video-neomagic:amd64 xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-vesa:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-qxl:amd64 libgles1-mesa:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-tdfx:amd64 xserver-xorg-video-fbdev:amd64 libwayland-egl1-mesa:amd64 xserver-xorg-video-trident:amd64 xserver-xorg-video-openchrome:amd64 xserver-xorg-input-vmmouse:amd64 xserver-xorg-video-sis:amd64 xserver-xorg-video-s3:amd64 xserver-xorg-video-modesetting:amd64 xserver-xorg-video-r128:amd64 xserver-xorg-video-mga:amd64 xserver-xorg-video-nouveau:amd64 ]
Remv libgles1-mesa [10.1.3-0ubuntu0.3] [xserver-xorg-video-vmware:amd64 xserver-xorg-video-siliconmotion:amd64 xorg:amd64 libegl1-mesa-drivers:amd64 xserver-xorg-video-sisusb:amd64 xserver-xorg-video-savage:amd64 xserver-xorg-video-neomagic:amd64 xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-vesa:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-qxl:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-tdfx:amd64 xserver-xorg-video-fbdev:amd64 libwayland-egl1-mesa:amd64 xserver-xorg-video-trident:amd64 xserver-xorg-video-openchrome:amd64 xserver-xorg-input-vmmouse:amd64 vlc:amd64 xserver-xorg-video-sis:amd64 xserver-xorg-video-s3:amd64 xserver-xorg-video-modesetting:amd64 xserver-xorg-video-r128:amd64 xserver-xorg-video-mga:amd64 xserver-xorg-video-nouveau:amd64 ]
Inst libgles1-mesa-lts-utopic (10.3.2-0ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64]) [xserver-xorg-video-vmware:amd64 xserver-xorg-video-siliconmotion:amd64 xorg:amd64 libegl1-mesa-drivers:amd64 xserver-xorg-video-sisusb:amd64 xserver-xorg-video-savage:amd64 xserver-xorg-video-neomagic:amd64 xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-vesa:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-qxl:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-tdfx:amd64 xserver-xorg-video-fbdev:amd64 libwayland-egl1-mesa:amd64 xserver-xorg-video-trident:amd64 xserver-xorg-video-openchrome:amd64 xserver-xorg-input-vmmouse:amd64 xserver-xorg-video-sis:amd64 xserver-xorg-video-s3:amd64 xserver-xorg-video-modesetting:amd64 xserver-xorg-video-r128:amd64 xserver-xorg-video-mga:amd64 xserver-xorg-video-nouveau:amd64 ]
Remv libopenvg1-mesa [10.1.3-0ubuntu0.3] [xserver-xorg-video-vmware:amd64 xserver-xorg-video-siliconmotion:amd64 xorg:amd64 libegl1-mesa-drivers:amd64 xserver-xorg-video-sisusb:amd64 xserver-xorg-video-savage:amd64 xserver-xorg-video-neomagic:amd64 xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-vesa:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-qxl:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-tdfx:amd64 xserver-xorg-video-fbdev:amd64 libwayland-egl1-mesa:amd64 xserver-xorg-video-trident:amd64 xserver-xorg-video-openchrome:amd64 xserver-xorg-input-vmmouse:amd64 xserver-xorg-video-sis:amd64 xserver-xorg-video-s3:amd64 xserver-xorg-video-modesetting:amd64 xserver-xorg-video-r128:amd64 xserver-xorg-video-mga:amd64 xserver-xorg-video-nouveau:amd64 ]
Remv xserver-xorg-video-vmware [1:13.0.2-2ubuntu1] [xserver-xorg-video-siliconmotion:amd64 xorg:amd64 libegl1-mesa-drivers:amd64 xserver-xorg-video-sisusb:amd64 xserver-xorg-video-savage:amd64 xserver-xorg-video-neomagic:amd64 xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-vesa:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-qxl:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-tdfx:amd64 xserver-xorg-video-fbdev:amd64 libwayland-egl1-mesa:amd64 xserver-xorg-video-trident:amd64 xserver-xorg-video-openchrome:amd64 xserver-xorg-input-vmmouse:amd64 xserver-xorg-video-sis:amd64 xserver-xorg-video-s3:amd64 xserver-xorg-video-modesetting:amd64 xserver-xorg-video-r128:amd64 xserver-xorg-video-mga:amd64 xserver-xorg-video-nouveau:amd64 ]
Remv libxatracker2 [10.1.3-0ubuntu0.3] [xserver-xorg-video-siliconmotion:amd64 xorg:amd64 libegl1-mesa-drivers:amd64 xserver-xorg-video-sisusb:amd64 xserver-xorg-video-savage:amd64 xserver-xorg-video-neomagic:amd64 xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-vesa:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-qxl:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-tdfx:amd64 xserver-xorg-video-fbdev:amd64 libwayland-egl1-mesa:amd64 xserver-xorg-video-trident:amd64 xserver-xorg-video-openchrome:amd64 xserver-xorg-input-vmmouse:amd64 xserver-xorg-video-sis:amd64 xserver-xorg-video-s3:amd64 xserver-xorg-video-modesetting:amd64 xserver-xorg-video-r128:amd64 xserver-xorg-video-mga:amd64 xserver-xorg-video-nouveau:amd64 ]
Remv libegl1-mesa-drivers [10.1.3-0ubuntu0.3] [xserver-xorg-video-siliconmotion:amd64 libcogl15:amd64 xorg:amd64 xserver-xorg-video-sisusb:amd64 xserver-xorg-video-savage:amd64 xserver-xorg-video-neomagic:amd64 xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-vesa:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-qxl:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-tdfx:amd64 xserver-xorg-video-fbdev:amd64 libwayland-egl1-mesa:amd64 xserver-xorg-video-trident:amd64 xserver-xorg-video-openchrome:amd64 xserver-xorg-input-vmmouse:amd64 xserver-xorg-video-sis:amd64 xserver-xorg-video-s3:amd64 xserver-xorg-video-modesetting:amd64 xserver-xorg-video-r128:amd64 xserver-xorg-video-mga:amd64 xserver-xorg-video-nouveau:amd64 ]
Remv libwayland-egl1-mesa [10.1.3-0ubuntu0.3] [xserver-xorg-video-siliconmotion:amd64 libcogl15:amd64 xorg:amd64 xserver-xorg-video-sisusb:amd64 xserver-xorg-video-savage:amd64 xserver-xorg-video-neomagic:amd64 xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-vesa:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-qxl:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-tdfx:amd64 xserver-xorg-video-fbdev:amd64 xserver-xorg-video-trident:amd64 xserver-xorg-video-openchrome:amd64 xserver-xorg-input-vmmouse:amd64 xserver-xorg-video-sis:amd64 xserver-xorg-video-s3:amd64 xserver-xorg-video-modesetting:amd64 xserver-xorg-video-r128:amd64 xserver-xorg-video-mga:amd64 xserver-xorg-video-nouveau:amd64 ]
Inst xserver-xorg-lts-utopic (1:7.7+7ubuntu2~trusty1 Ubuntu:14.04/trusty-updates [amd64]) [xserver-xorg-video-siliconmotion:amd64 libcogl15:amd64 xserver-xorg-video-sisusb:amd64 xserver-xorg-video-savage:amd64 xserver-xorg-video-neomagic:amd64 xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-vesa:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-qxl:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-tdfx:amd64 xserver-xorg-video-fbdev:amd64 xserver-xorg-video-trident:amd64 xserver-xorg-video-openchrome:amd64 xserver-xorg-input-vmmouse:amd64 xserver-xorg-video-sis:amd64 xserver-xorg-video-s3:amd64 xserver-xorg-video-modesetting:amd64 xserver-xorg-video-r128:amd64 xserver-xorg-video-mga:amd64 xserver-xorg-video-nouveau:amd64 ]
Inst libegl1-mesa-drivers-lts-utopic (10.3.2-0ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64]) [xserver-xorg-video-siliconmotion:amd64 xserver-xorg-video-sisusb:amd64 xserver-xorg-video-savage:amd64 xserver-xorg-video-neomagic:amd64 xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-vesa:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-qxl:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-tdfx:amd64 xserver-xorg-video-fbdev:amd64 xserver-xorg-video-trident:amd64 xserver-xorg-video-openchrome:amd64 xserver-xorg-input-vmmouse:amd64 xserver-xorg-video-sis:amd64 xserver-xorg-video-s3:amd64 xserver-xorg-video-modesetting:amd64 xserver-xorg-video-r128:amd64 xserver-xorg-video-mga:amd64 xserver-xorg-video-nouveau:amd64 ]
Inst libllvm3.5 (1:3.5-4ubuntu2~trusty1 Ubuntu:14.04/trusty-updates [amd64]) [xserver-xorg-video-siliconmotion:amd64 xserver-xorg-video-sisusb:amd64 xserver-xorg-video-savage:amd64 xserver-xorg-video-neomagic:amd64 xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-vesa:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-qxl:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-tdfx:amd64 xserver-xorg-video-fbdev:amd64 xserver-xorg-video-trident:amd64 xserver-xorg-video-openchrome:amd64 xserver-xorg-input-vmmouse:amd64 xserver-xorg-video-sis:amd64 xserver-xorg-video-s3:amd64 xserver-xorg-video-modesetting:amd64 xserver-xorg-video-r128:amd64 xserver-xorg-video-mga:amd64 xserver-xorg-video-nouveau:amd64 ]
Inst libgbm1-lts-utopic (10.3.2-0ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64]) [xserver-xorg-video-siliconmotion:amd64 xserver-xorg-video-sisusb:amd64 xserver-xorg-video-savage:amd64 xserver-xorg-video-neomagic:amd64 xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-vesa:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-qxl:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-tdfx:amd64 xserver-xorg-video-fbdev:amd64 xserver-xorg-video-trident:amd64 xserver-xorg-video-openchrome:amd64 xserver-xorg-input-vmmouse:amd64 xserver-xorg-video-sis:amd64 xserver-xorg-video-s3:amd64 xserver-xorg-video-modesetting:amd64 xserver-xorg-video-r128:amd64 xserver-xorg-video-mga:amd64 xserver-xorg-video-nouveau:amd64 ]
Inst libglapi-mesa-lts-utopic (10.3.2-0ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64]) [xserver-xorg-video-siliconmotion:amd64 xserver-xorg-video-sisusb:amd64 xserver-xorg-video-savage:amd64 xserver-xorg-video-neomagic:amd64 xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-vesa:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-qxl:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-tdfx:amd64 xserver-xorg-video-fbdev:amd64 xserver-xorg-video-trident:amd64 xserver-xorg-video-openchrome:amd64 xserver-xorg-input-vmmouse:amd64 xserver-xorg-video-sis:amd64 xserver-xorg-video-s3:amd64 xserver-xorg-video-modesetting:amd64 xserver-xorg-video-r128:amd64 xserver-xorg-video-mga:amd64 xserver-xorg-video-nouveau:amd64 ]
Inst libopenvg1-mesa-lts-utopic (10.3.2-0ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64]) [xserver-xorg-video-siliconmotion:amd64 xserver-xorg-video-sisusb:amd64 xserver-xorg-video-savage:amd64 xserver-xorg-video-neomagic:amd64 xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-vesa:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-qxl:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-tdfx:amd64 xserver-xorg-video-fbdev:amd64 xserver-xorg-video-trident:amd64 xserver-xorg-video-openchrome:amd64 xserver-xorg-input-vmmouse:amd64 xserver-xorg-video-sis:amd64 xserver-xorg-video-s3:amd64 xserver-xorg-video-modesetting:amd64 xserver-xorg-video-r128:amd64 xserver-xorg-video-mga:amd64 xserver-xorg-video-nouveau:amd64 ]
Inst libwayland-egl1-mesa-lts-utopic (10.3.2-0ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64]) [xserver-xorg-video-siliconmotion:amd64 xserver-xorg-video-sisusb:amd64 xserver-xorg-video-savage:amd64 xserver-xorg-video-neomagic:amd64 xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-vesa:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-qxl:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-tdfx:amd64 xserver-xorg-video-fbdev:amd64 xserver-xorg-video-trident:amd64 xserver-xorg-video-openchrome:amd64 xserver-xorg-input-vmmouse:amd64 xserver-xorg-video-sis:amd64 xserver-xorg-video-s3:amd64 xserver-xorg-video-modesetting:amd64 xserver-xorg-video-r128:amd64 xserver-xorg-video-mga:amd64 xserver-xorg-video-nouveau:amd64 ]
Remv xserver-xorg-video-vesa [1:2.3.3-1build1] [xserver-xorg-video-siliconmotion:amd64 xserver-xorg-video-sisusb:amd64 xserver-xorg-video-savage:amd64 xserver-xorg-video-neomagic:amd64 xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-qxl:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-tdfx:amd64 xserver-xorg-video-fbdev:amd64 xserver-xorg-video-trident:amd64 xserver-xorg-video-openchrome:amd64 xserver-xorg-input-vmmouse:amd64 xserver-xorg-video-sis:amd64 xserver-xorg-video-s3:amd64 xserver-xorg-video-modesetting:amd64 xserver-xorg-video-r128:amd64 xserver-xorg-video-mga:amd64 xserver-xorg-video-nouveau:amd64 ]
Remv xserver-xorg-video-trident [1:1.3.6-0ubuntu5] [xserver-xorg-video-siliconmotion:amd64 xserver-xorg-video-sisusb:amd64 xserver-xorg-video-savage:amd64 xserver-xorg-video-neomagic:amd64 xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-qxl:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-tdfx:amd64 xserver-xorg-video-fbdev:amd64 xserver-xorg-video-openchrome:amd64 xserver-xorg-input-vmmouse:amd64 xserver-xorg-video-sis:amd64 xserver-xorg-video-s3:amd64 xserver-xorg-video-modesetting:amd64 xserver-xorg-video-r128:amd64 xserver-xorg-video-mga:amd64 xserver-xorg-video-nouveau:amd64 ]
Remv xserver-xorg-video-tdfx [1:1.4.5-1build1] [xserver-xorg-video-siliconmotion:amd64 xserver-xorg-video-sisusb:amd64 xserver-xorg-video-savage:amd64 xserver-xorg-video-neomagic:amd64 xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-qxl:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-fbdev:amd64 xserver-xorg-video-openchrome:amd64 xserver-xorg-input-vmmouse:amd64 xserver-xorg-video-sis:amd64 xserver-xorg-video-s3:amd64 xserver-xorg-video-modesetting:amd64 xserver-xorg-video-r128:amd64 xserver-xorg-video-mga:amd64 xserver-xorg-video-nouveau:amd64 ]
Remv xserver-xorg-video-sisusb [1:0.9.6-2build1] [xserver-xorg-video-siliconmotion:amd64 xserver-xorg-video-savage:amd64 xserver-xorg-video-neomagic:amd64 xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-qxl:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-fbdev:amd64 xserver-xorg-video-openchrome:amd64 xserver-xorg-input-vmmouse:amd64 xserver-xorg-video-sis:amd64 xserver-xorg-video-s3:amd64 xserver-xorg-video-modesetting:amd64 xserver-xorg-video-r128:amd64 xserver-xorg-video-mga:amd64 xserver-xorg-video-nouveau:amd64 ]
Remv xserver-xorg-video-sis [1:0.10.7-0ubuntu6] [xserver-xorg-video-siliconmotion:amd64 xserver-xorg-video-savage:amd64 xserver-xorg-video-neomagic:amd64 xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-qxl:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-fbdev:amd64 xserver-xorg-video-openchrome:amd64 xserver-xorg-input-vmmouse:amd64 xserver-xorg-video-s3:amd64 xserver-xorg-video-modesetting:amd64 xserver-xorg-video-r128:amd64 xserver-xorg-video-mga:amd64 xserver-xorg-video-nouveau:amd64 ]
Remv xserver-xorg-video-siliconmotion [1:1.7.7-2build1] [xserver-xorg-video-savage:amd64 xserver-xorg-video-neomagic:amd64 xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-qxl:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-fbdev:amd64 xserver-xorg-video-openchrome:amd64 xserver-xorg-input-vmmouse:amd64 xserver-xorg-video-s3:amd64 xserver-xorg-video-modesetting:amd64 xserver-xorg-video-r128:amd64 xserver-xorg-video-mga:amd64 xserver-xorg-video-nouveau:amd64 ]
Remv xserver-xorg-video-savage [1:2.3.7-2ubuntu2] [xserver-xorg-video-neomagic:amd64 xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-qxl:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-fbdev:amd64 xserver-xorg-video-openchrome:amd64 xserver-xorg-input-vmmouse:amd64 xserver-xorg-video-s3:amd64 xserver-xorg-video-modesetting:amd64 xserver-xorg-video-r128:amd64 xserver-xorg-video-mga:amd64 xserver-xorg-video-nouveau:amd64 ]
Remv xserver-xorg-video-s3 [1:0.6.5-0ubuntu4] [xserver-xorg-video-neomagic:amd64 xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-qxl:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-fbdev:amd64 xserver-xorg-video-openchrome:amd64 xserver-xorg-input-vmmouse:amd64 xserver-xorg-video-modesetting:amd64 xserver-xorg-video-r128:amd64 xserver-xorg-video-mga:amd64 xserver-xorg-video-nouveau:amd64 ]
Remv xserver-xorg-video-r128 [6.9.2-1build1] [xserver-xorg-video-neomagic:amd64 xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-qxl:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-fbdev:amd64 xserver-xorg-video-openchrome:amd64 xserver-xorg-input-vmmouse:amd64 xserver-xorg-video-modesetting:amd64 xserver-xorg-video-mga:amd64 xserver-xorg-video-nouveau:amd64 ]
Remv xserver-xorg-video-qxl [0.1.1-0ubuntu3] [xserver-xorg-video-neomagic:amd64 xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-fbdev:amd64 xserver-xorg-video-openchrome:amd64 xserver-xorg-input-vmmouse:amd64 xserver-xorg-video-modesetting:amd64 xserver-xorg-video-mga:amd64 xserver-xorg-video-nouveau:amd64 ]
Remv xserver-xorg-video-openchrome [1:0.3.3-1build1] [xserver-xorg-video-neomagic:amd64 xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-fbdev:amd64 xserver-xorg-input-vmmouse:amd64 xserver-xorg-video-modesetting:amd64 xserver-xorg-video-mga:amd64 xserver-xorg-video-nouveau:amd64 ]
Remv xserver-xorg-video-nouveau [1:1.0.10-1ubuntu2] [xserver-xorg-video-neomagic:amd64 xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-fbdev:amd64 xserver-xorg-input-vmmouse:amd64 xserver-xorg-video-modesetting:amd64 xserver-xorg-video-mga:amd64 ]
Remv xserver-xorg-video-neomagic [1:1.2.8-1build1] [xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-fbdev:amd64 xserver-xorg-input-vmmouse:amd64 xserver-xorg-video-modesetting:amd64 xserver-xorg-video-mga:amd64 ]
Remv xserver-xorg-video-modesetting [0.8.1-1build1] [xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-fbdev:amd64 xserver-xorg-input-vmmouse:amd64 xserver-xorg-video-mga:amd64 ]
Remv xserver-xorg-video-mga [1:1.6.3-1build1] [xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-fbdev:amd64 xserver-xorg-input-vmmouse:amd64 ]
Remv xserver-xorg-video-mach64 [6.9.4-1build1] [xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-fbdev:amd64 xserver-xorg-input-vmmouse:amd64 ]
Remv xserver-xorg-video-fbdev [1:0.4.4-1build1] [xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-input-vmmouse:amd64 ]
Remv xserver-xorg-video-cirrus [1:1.5.2-1build1] [xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-input-vmmouse:amd64 ]
Remv xserver-xorg-input-vmmouse [1:13.0.0-1build1] [xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 ]
Remv xserver-xorg-input-synaptics [1.7.4-0ubuntu1] [xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 ]
Remv xserver-xorg-input-mouse [1:1.9.0-1build1] [xserver-xorg-input-evdev:amd64 ]
Remv xserver-xorg-input-evdev [1:2.8.2-1ubuntu2] []
Inst libepoxy0 (1.1-1 Ubuntu:14.04/trusty [amd64]) []
Inst xserver-xorg-core-lts-utopic (2:1.16.0-1ubuntu1.2~trusty1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst xserver-xorg-video-r128-lts-utopic (6.9.2-1build2~trusty1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst xserver-xorg-video-mach64-lts-utopic (6.9.4-2~trusty1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst xserver-xorg-video-radeon-lts-utopic (1:7.4.0-2ubuntu2~trusty1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst xserver-xorg-video-ati-lts-utopic (1:7.4.0-2ubuntu2~trusty1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst xserver-xorg-video-cirrus-lts-utopic (1:1.5.2-2build1~trusty1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst xserver-xorg-video-fbdev-lts-utopic (1:0.4.4-1build2~trusty1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst xserver-xorg-video-intel-lts-utopic (2:2.99.914-1~exp1ubuntu4.2~trusty1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst xserver-xorg-video-mga-lts-utopic (1:1.6.3-2build1~trusty1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst xserver-xorg-video-modesetting-lts-utopic (0.9.0-1build1~trusty1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst xserver-xorg-video-neomagic-lts-utopic (1:1.2.8-1build2~trusty1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst xserver-xorg-video-nouveau-lts-utopic (1:1.0.11-1ubuntu2~trusty1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst xserver-xorg-video-openchrome-lts-utopic (1:0.3.3-1build2~trusty1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst xserver-xorg-video-savage-lts-utopic (1:2.3.7-2ubuntu3~trusty1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst xserver-xorg-video-siliconmotion-lts-utopic (1:1.7.7-2build2~trusty1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst xserver-xorg-video-sisusb-lts-utopic (1:0.9.6-2build2~trusty1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst xserver-xorg-video-tdfx-lts-utopic (1:1.4.5-1build2~trusty1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst xserver-xorg-video-trident-lts-utopic (1:1.3.6-0ubuntu6~trusty1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst xserver-xorg-video-vesa-lts-utopic (1:2.3.3-1build2~trusty1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst libxatracker2-lts-utopic (10.3.2-0ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst xserver-xorg-video-vmware-lts-utopic (1:13.0.2-3ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst xserver-xorg-video-all-lts-utopic (1:7.7+7ubuntu2~trusty1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst libevdev2 (1.0.99.2+dfsg-2ubuntu2 Ubuntu:14.04/trusty [amd64]) []
Inst xserver-xorg-input-evdev-lts-utopic (1:2.9.0-1ubuntu2~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Inst xserver-xorg-input-mouse-lts-utopic (1:1.9.0-1build2~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Inst xserver-xorg-input-vmmouse-lts-utopic (1:13.0.0-1build2~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Inst xserver-xorg-input-synaptics-lts-utopic (1.8.1-1ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Inst xserver-xorg-input-wacom-lts-utopic (1:0.25.0-0ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Inst xserver-xorg-input-all-lts-utopic (1:7.7+7ubuntu2~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf libllvm3.5 (1:3.5-4ubuntu2~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf libgl1-mesa-dri-lts-utopic (10.3.2-0ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf libgbm1-lts-utopic (10.3.2-0ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf libegl1-mesa-lts-utopic (10.3.2-0ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf libglapi-mesa-lts-utopic (10.3.2-0ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf libgl1-mesa-glx-lts-utopic (10.3.2-0ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf libgles2-mesa-lts-utopic (10.3.2-0ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf libgles1-mesa-lts-utopic (10.3.2-0ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf libepoxy0 (1.1-1 Ubuntu:14.04/trusty [amd64])
Conf xserver-xorg-core-lts-utopic (2:1.16.0-1ubuntu1.2~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-video-r128-lts-utopic (6.9.2-1build2~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-video-mach64-lts-utopic (6.9.4-2~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-video-radeon-lts-utopic (1:7.4.0-2ubuntu2~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-video-ati-lts-utopic (1:7.4.0-2ubuntu2~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-video-cirrus-lts-utopic (1:1.5.2-2build1~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-video-fbdev-lts-utopic (1:0.4.4-1build2~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-video-intel-lts-utopic (2:2.99.914-1~exp1ubuntu4.2~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-video-mga-lts-utopic (1:1.6.3-2build1~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-video-modesetting-lts-utopic (0.9.0-1build1~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-video-neomagic-lts-utopic (1:1.2.8-1build2~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-video-nouveau-lts-utopic (1:1.0.11-1ubuntu2~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-video-openchrome-lts-utopic (1:0.3.3-1build2~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-video-savage-lts-utopic (1:2.3.7-2ubuntu3~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-video-siliconmotion-lts-utopic (1:1.7.7-2build2~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-video-sisusb-lts-utopic (1:0.9.6-2build2~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-video-tdfx-lts-utopic (1:1.4.5-1build2~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-video-trident-lts-utopic (1:1.3.6-0ubuntu6~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-video-vesa-lts-utopic (1:2.3.3-1build2~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf libxatracker2-lts-utopic (10.3.2-0ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-video-vmware-lts-utopic (1:13.0.2-3ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-video-all-lts-utopic (1:7.7+7ubuntu2~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf libevdev2 (1.0.99.2+dfsg-2ubuntu2 Ubuntu:14.04/trusty [amd64])
Conf xserver-xorg-input-evdev-lts-utopic (1:2.9.0-1ubuntu2~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-input-mouse-lts-utopic (1:1.9.0-1build2~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-input-vmmouse-lts-utopic (1:13.0.0-1build2~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-input-synaptics-lts-utopic (1.8.1-1ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-input-wacom-lts-utopic (1:0.25.0-0ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-input-all-lts-utopic (1:7.7+7ubuntu2~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-lts-utopic (1:7.7+7ubuntu2~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf libopenvg1-mesa-lts-utopic (10.3.2-0ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf libwayland-egl1-mesa-lts-utopic (10.3.2-0ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf libegl1-mesa-drivers-lts-utopic (10.3.2-0ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64])
doug@doug-Lenovo-IdeaPad-Y510P:~$ 
```

---

### Post by mc4man on 2015-02-16
It appears one could shorten the command to - 
```
sudo apt-get install -s --install-recommends linux-generic-lts-utopic xserver-xorg-lts-utopic \
libgl1-mesa-glx-lts-utopic libegl1-mesa-drivers-lts-utopic


```
or maybe even just
```
sudo apt-get install  -s --install-recommends  xserver-xorg-lts-utopic \
libgl1-mesa-glx-lts-utopic libegl1-mesa-drivers-lts-utopic

```
if it looked good then re-run removing the -s

---

### Post by thorstenr_42 on 2015-02-16
thanks a lot, your first command worked fine, however i run into trouble with the nvidia driver and cuda packages... i will probably just do a reinstall if 14.04.2 becomes released

---

### Post by mc4man on 2015-02-16
> **thorstenr_42 said:**
> thanks a lot, your first command worked fine, however i run into trouble with the nvidia driver and cuda packages... i will probably just do a reinstall if 14.04.2 becomes released
They said this week, we'll see.

Here on this laptop - Haswell, GeForce GT 755M, Intel 4600,  I just use Intel for graphics. I've noticed with the lts kernel that sometimes log outs end in a kernel panic & restarts hang. Removing the xserver-xorg-video-nouveau-lts-utopic package seems to 'fix' that..

---

### Post by Elfy on 2015-02-16
> **mc4man said:**
> They said this week, we'll see.

Here on this laptop - Haswell, GeForce GT 755M, Intel 4600,  I just use Intel for graphics. I've noticed with the lts kernel that sometimes log outs end in a kernel panic & resets hang. Removing the xserver-xorg-video-nouveau-lts-utopic package seems to 'fix' that..

It's 22:00 UTC - those looking at the issues have said nothing as yet. The chances of *us* at least getting a workable image to do even smoketests on so I can mark them as released is looking slim.

---

### Post by mc4man on 2015-02-18
> **Elfy said:**
> It's 22:00 UTC - those looking at the issues have said nothing as yet. The chances of *us* at least getting a workable image to do even smoketests on so I can mark them as released is looking slim.
See some new images up - (Ubuntu
[http://cdimage.ubuntu.com/trusty/daily-live/current/](http://cdimage.ubuntu.com/trusty/daily-live/current/)
Xubuntu ?
[http://cdimage.ubuntu.com/xubuntu/trusty/daily-live/pending/](http://cdimage.ubuntu.com/xubuntu/trusty/daily-live/pending/)

---

### Post by Elfy on 2015-02-18
all looking pretty good for xubuntu currently, place to see what the current state of affairs is 

[http://iso.qa.ubuntu.com/qatracker/milestones/332/builds](http://iso.qa.ubuntu.com/qatracker/milestones/332/builds)

and for the reports from previous builds(2 in the last couple of days) hit the superseded button

Currently if anyone has time for some smoketesting, Kubuntu, Lubuntu could do with a bit of help.

Mythbuntu with loads :)

---

### Post by mickee384 on 2015-02-22
Hi there! I was wondering what the point is for upgrading say 14.04 to 14.04.2? Just very curious about these interim LTS releases. What do they offer?

---

### Post by mc4man on 2015-02-22
If one happened to use intel-linux-graphics-installer in 14.04.1 then they will find it not possible to install the lts-utopic mesa packages.
Easiest would be to just do a 14.04.2 install if that's what's desired. Otherwise some if not all of the Intel supplied packages would need to be replaced by the Ubuntu repo versions, preferably from trusty-updates & trusty-security  (mesa versions usually have to match

Ex. here where the upgrade/instal was blocked
removed, either not needed or not absolutely needed atm, some can be re-installed later - 
> 
intel-linux-graphics-installer
i915-3.16-3.13-dkms
libosmesa6
mesa-vdpau-drivers
va-driver-all
intel-gpu-tools


packages used to replace Intel ones (amd64) all dl'ed, placed in folder & install via sudo dpkg -i *.deb
*may not be complete elsewhere*
> libdrm2_2.4.56-1~ubuntu2_amd64.deb
libdrm-intel1_2.4.56-1~ubuntu2_amd64.deb
libdrm-nouveau2_2.4.56-1~ubuntu2_amd64.deb
libdrm-radeon1_2.4.56-1~ubuntu2_amd64.deb
libegl1-mesa_10.1.3-0ubuntu0.3_amd64.deb
libegl1-mesa-drivers_10.1.3-0ubuntu0.3_amd64.deb
libgbm1_10.1.3-0ubuntu0.3_amd64.deb
libgl1-mesa-dri_10.1.3-0ubuntu0.3_amd64.deb
libgl1-mesa-glx_10.1.3-0ubuntu0.3_amd64.deb
libglapi-mesa_10.1.3-0ubuntu0.3_amd64.deb
libgles1-mesa_10.1.3-0ubuntu0.3_amd64.deb
libgles2-mesa_10.1.3-0ubuntu0.3_amd64.deb
libopenvg1-mesa_10.1.3-0ubuntu0.3_amd64.deb
libwayland-egl1-mesa_10.1.3-0ubuntu0.3_amd64.deb
libxatracker2_10.1.3-0ubuntu0.3_amd64.deb
xserver-xorg-video-intel_2.99.910-0ubuntu1.4_amd64.deb

If one had also installed wine on amd64 install  then the task could be more complicated then worth as there would be some related :i386 packages involved

---

### Post by mc4man on 2015-02-22
Well at least with my  Intel mobile that can show issues, here Haswell (mobile), using the Intel Graphics Controller. (nvidia-prime remains generally useless except maybe for some gamers or non compositing installs

What can happen is log outs & restarts get slow or hang up. The culprit seem to be xserver-xorg-video-nouveau & to a much lesser extent ibus
Removing xserver-xorg-video-nouveau which is not needed when using Intel graphics resolves immediately, log outs are now 1/2 sec or so, restarts/shutdowns are good & quick

In regards to ibus - if you don't use it then better to turn off > System settings > Language Support > Keyboard Input method system > none
Also some ibus packages can be safely & gladly removed if desired - 
ibus-gtk3
ibus-pinyin
ibus-table
python-ibus

---

### Post by mc4man on 2015-02-22
If one would like to be able to install devel packages in 14.04 then I'd suggest staying away from 14.04.2 & the mesa lts-utopic stack. There will be some packages not installable & in light of the available resources to fix things on Desktop installs  not a great chance of prompt fixes. (or any fixes
2 new there - 
[https://bugs.launchpad.net/ubuntu/+source/freeglut/+bug/1424466](https://bugs.launchpad.net/ubuntu/+source/freeglut/+bug/1424466)
[https://bugs.launchpad.net/ubuntu/+source/mesa-lts-utopic/+bug/1424059](https://bugs.launchpad.net/ubuntu/+source/mesa-lts-utopic/+bug/1424059)

likely there are more..

---

