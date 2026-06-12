---
title: "Ubuntu 14.04.2, now available, through the repository propesed on trusty."
date: 2015-01-29
forum: Ubuntu Development Version
---

### Post by hectorsales on 2015-01-29
hi, I'm running Ubuntu 14.04.1 and i has noticed that the next release of Ubuntu(14.04.2), is avalaible on proposed repository:

```
hs1974g@unity7:~$ apt-cache policy xserver-xorg-lts-utopic
```

> xserver-xorg-lts-utopic:
  Instalados: (ninguno)
  Candidato:  1:7.7+7ubuntu2~trusty1
  Tabla de versión:
     1:7.7+7ubuntu2~trusty1 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-proposed/main amd64 Packages

```
hs1974g@unity7:~$ apt-cache policy libgl1-mesa-glx-lts-utopic
```

> libgl1-mesa-glx-lts-utopic:
  Instalados: (ninguno)
  Candidato:  10.3.2-0ubuntu1~trusty1
  Tabla de versión:
     10.3.2-0ubuntu1~trusty1 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-proposed/main amd64 Packages



```
hs1974g@unity7:~$ apt-cache policy linux-generic-lts-utopic
```

> linux-generic-lts-utopic:
  Instalados: (ninguno)
  Candidato:  3.16.0.30.23
  Tabla de versión:
     3.16.0.30.23 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-proposed/main amd64 Packages
     3.16.0.29.22 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main amd64 Packages
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-security/main amd64 Packages

[B]
Note[/B]: This it's no official but the oficial release date is around 5 February. **¡¡¡** **Definitely Ubuntu 14.04.2 is comming !!!**

[B]
How to upgrade from ubuntu 14.04.1 to 14.04.2[/B] **?**

I think Oficial instructions aren't published because the oficial date is 5 February. The kernel(3.16) and XOrg (1.16) and drivers( mesa stack 10.3) is **OPTIONAL**, only upgrade if you wants.


Basically it would be something like :

```
sudo apt-get install --install-recommends linux-generic-lts-utopic xserver-xorg-lts-utopic libgl1-mesa-glx-lts-utopic
```

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

Regards.

---

### Post by kansasnoob on 2015-01-30
I'm performing some tests and it stilll looks a bit ugly in Ubuntu GNOME:

```
lance@lance-AMD-desktop:~$ sudo apt-get install --install-recommends linux-generic-lts-utopic xserver-xorg-lts-utopic libgl1-mesa-glx-lts-utopic -s
[sudo] password for lance: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-generic linux-image-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libegl1-mesa-lts-utopic libepoxy0 libevdev2 libgbm1-lts-utopic
  libgl1-mesa-dri-lts-utopic libglapi-mesa-lts-utopic libgles1-mesa-lts-utopic
  libgles2-mesa-lts-utopic libllvm3.5 libxatracker2-lts-utopic
  linux-headers-3.16.0-30 linux-headers-3.16.0-30-generic
  linux-headers-generic-lts-utopic linux-image-3.16.0-30-generic
  linux-image-extra-3.16.0-30-generic linux-image-generic-lts-utopic
  xserver-xorg-core-lts-utopic xserver-xorg-input-all-lts-utopic
  xserver-xorg-input-evdev-lts-utopic xserver-xorg-input-mouse-lts-utopic
  xserver-xorg-input-synaptics-lts-utopic
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
  fdutils linux-lts-utopic-tools xfonts-100dpi xfonts-75dpi
  gpointing-device-settings touchfreeze xserver-xorg-video-geode-lts-utopic
  firmware-linux
Recommended packages:
  libegl1-mesa-drivers-lts-utopic
[B][COLOR="#FF0000"]The following packages will be REMOVED:
  cheese empathy gdm gir1.2-clutter-1.0 gir1.2-clutter-gst-2.0 gir1.2-cogl-1.0
  gir1.2-coglpango-1.0 gir1.2-gtkclutter-1.0 gir1.2-mutter-3.0
  gir1.2-totem-1.0 gnome-contacts gnome-control-center gnome-shell
  gnome-shell-extensions gnome-sushi gstreamer1.0-clutter libcheese-gtk23
  libcheese7 libclutter-1.0-0 libclutter-gst-2.0-0 libclutter-gtk-1.0-0
  libcogl-pango15 libcogl15 libegl1-mesa libegl1-mesa-drivers libgl1-mesa-dri
  libgl1-mesa-glx libglapi-mesa libgles2-mesa libmutter0c libopenvg1-mesa
  libtotem0 libwayland-egl1-mesa libxatracker2 mcp-account-manager-goa mutter
  nautilus-sendto-empathy totem totem-plugins ubuntu-gnome-desktop[/COLOR][/B]
  xserver-xorg xserver-xorg-core xserver-xorg-input-all
  xserver-xorg-input-evdev xserver-xorg-input-mouse
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
  xserver-xorg-video-vesa xserver-xorg-video-vmware
The following NEW packages will be installed:
  libegl1-mesa-lts-utopic libepoxy0 libevdev2 libgbm1-lts-utopic
  libgl1-mesa-dri-lts-utopic libgl1-mesa-glx-lts-utopic
  libglapi-mesa-lts-utopic libgles1-mesa-lts-utopic libgles2-mesa-lts-utopic
  libllvm3.5 libxatracker2-lts-utopic linux-generic-lts-utopic
  linux-headers-3.16.0-30 linux-headers-3.16.0-30-generic
  linux-headers-generic-lts-utopic linux-image-3.16.0-30-generic
  linux-image-extra-3.16.0-30-generic linux-image-generic-lts-utopic
  xserver-xorg-core-lts-utopic xserver-xorg-input-all-lts-utopic
  xserver-xorg-input-evdev-lts-utopic xserver-xorg-input-mouse-lts-utopic
  xserver-xorg-input-synaptics-lts-utopic
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
0 upgraded, 46 newly installed, 72 to remove and 0 not upgraded.
Remv cheese [3.10.2-0ubuntu2]
Remv mcp-account-manager-goa [3.8.6-0ubuntu9.1]
Remv nautilus-sendto-empathy [3.8.6-0ubuntu9.1]
Remv empathy [3.8.6-0ubuntu9.1]
Remv ubuntu-gnome-desktop [0.32]
Remv gdm [3.10.0.1-0ubuntu3.1]
Remv gnome-shell-extensions [3.10.1-0ubuntu2]
Remv gnome-shell [3.10.4-0ubuntu5.2]
Remv gir1.2-mutter-3.0 [3.10.4-0ubuntu2.1]
Remv gir1.2-clutter-1.0 [1.16.4-0ubuntu2] [gnome-sushi:i386 gir1.2-gtkclutter-1.0:i386 gir1.2-clutter-gst-2.0:i386 ]
Remv gnome-sushi [3.11.90-0ubuntu1] [gir1.2-gtkclutter-1.0:i386 gir1.2-clutter-gst-2.0:i386 ]
Remv gir1.2-clutter-gst-2.0 [2.0.8-1build1] [gir1.2-gtkclutter-1.0:i386 ]
Remv gir1.2-coglpango-1.0 [1.16.2-1] [gir1.2-gtkclutter-1.0:i386 ]
Remv gir1.2-cogl-1.0 [1.16.2-1] [gir1.2-gtkclutter-1.0:i386 ]
Remv gir1.2-gtkclutter-1.0 [1.4.4-3ubuntu2.2]
Remv totem-plugins [3.10.1-1ubuntu4]
Remv gir1.2-totem-1.0 [3.10.1-1ubuntu4]
Remv gnome-contacts [3.8.3-1ubuntu1]
Remv gnome-control-center [1:3.6.3-0ubuntu56.1]
Remv totem [3.10.1-1ubuntu4]
Remv libcheese-gtk23 [3.10.2-0ubuntu2]
Remv libcheese7 [3.10.2-0ubuntu2]
Remv gstreamer1.0-clutter [2.0.8-1build1]
Remv mutter [3.10.4-0ubuntu2.1]
Remv libmutter0c [3.10.4-0ubuntu2.1]
Remv libclutter-1.0-0 [1.16.4-0ubuntu2] [libclutter-gtk-1.0-0:i386 libtotem0:i386 libclutter-gst-2.0-0:i386 ]
Remv libtotem0 [3.10.1-1ubuntu4] [libclutter-gtk-1.0-0:i386 libclutter-gst-2.0-0:i386 ]
Remv libclutter-gst-2.0-0 [2.0.8-1build1] [libclutter-gtk-1.0-0:i386 ]
Remv libclutter-gtk-1.0-0 [1.4.4-3ubuntu2.2]
Remv libcogl-pango15 [1.16.2-1]
Remv libcogl15 [1.16.2-1]
Remv libegl1-mesa-drivers [10.1.3-0ubuntu0.3]
Remv libwayland-egl1-mesa [10.1.3-0ubuntu0.3]
Remv xserver-xorg-video-ati [1:7.3.0-1ubuntu3.1] [xserver-xorg-video-all:i386 ]
Remv xserver-xorg-video-glamoregl [0.6.0-0ubuntu4] [xserver-xorg-video-all:i386 ]
Remv libegl1-mesa [10.1.3-0ubuntu0.3] [libgstreamer-plugins-bad1.0-0:i386 xserver-xorg-video-all:i386 gstreamer1.0-plugins-bad:i386 ]
Remv xserver-xorg [1:7.7+1ubuntu8.1] [libgstreamer-plugins-bad1.0-0:i386 xorg:i386 xserver-xorg-video-all:i386 gstreamer1.0-plugins-bad:i386 ]
Inst libegl1-mesa-lts-utopic (10.3.2-0ubuntu1~trusty1 Ubuntu:14.04/trusty-proposed [i386]) [xorg:i386 xserver-xorg-video-all:i386 ]
Remv xserver-xorg-video-intel [2:2.99.910-0ubuntu1.4] [xorg:i386 xserver-xorg-video-all:i386 ]
Remv xserver-xorg-video-radeon [1:7.3.0-1ubuntu3.1] [xorg:i386 xserver-xorg-video-all:i386 ]
Remv xserver-xorg-video-vmware [1:13.0.2-2ubuntu1] [xorg:i386 xserver-xorg-video-all:i386 ]
Remv xserver-xorg-video-vesa [1:2.3.3-1build1] [xorg:i386 xserver-xorg-video-all:i386 ]
Remv xserver-xorg-video-trident [1:1.3.6-0ubuntu5] [xorg:i386 xserver-xorg-video-all:i386 ]
Remv xserver-xorg-video-tdfx [1:1.4.5-1build1] [xorg:i386 xserver-xorg-video-all:i386 ]
Remv xserver-xorg-video-sisusb [1:0.9.6-2build1] [xorg:i386 xserver-xorg-video-all:i386 ]
Remv xserver-xorg-video-sis [1:0.10.7-0ubuntu6] [xorg:i386 xserver-xorg-video-all:i386 ]
Remv xserver-xorg-video-siliconmotion [1:1.7.7-2build1] [xorg:i386 xserver-xorg-video-all:i386 ]
Remv xserver-xorg-video-savage [1:2.3.7-2ubuntu2] [xorg:i386 xserver-xorg-video-all:i386 ]
Remv xserver-xorg-video-s3 [1:0.6.5-0ubuntu4] [xorg:i386 xserver-xorg-video-all:i386 ]
Remv xserver-xorg-video-r128 [6.9.2-1build1] [xorg:i386 xserver-xorg-video-all:i386 ]
Remv xserver-xorg-video-qxl [0.1.1-0ubuntu3] [xorg:i386 xserver-xorg-video-all:i386 ]
Remv xserver-xorg-video-openchrome [1:0.3.3-1build1] [xorg:i386 xserver-xorg-video-all:i386 ]
Remv xserver-xorg-video-nouveau [1:1.0.10-1ubuntu2] [xorg:i386 xserver-xorg-video-all:i386 ]
Remv xserver-xorg-video-neomagic [1:1.2.8-1build1] [xorg:i386 xserver-xorg-video-all:i386 ]
Remv xserver-xorg-video-modesetting [0.8.1-1build1] [xorg:i386 xserver-xorg-video-all:i386 ]
Remv xserver-xorg-video-mga [1:1.6.3-1build1] [xorg:i386 xserver-xorg-video-all:i386 ]
Remv xserver-xorg-video-mach64 [6.9.4-1build1] [xorg:i386 xserver-xorg-video-all:i386 ]
Remv xserver-xorg-video-fbdev [1:0.4.4-1build1] [xorg:i386 xserver-xorg-video-all:i386 ]
Remv xserver-xorg-video-cirrus [1:1.5.2-1build1] [xorg:i386 xserver-xorg-video-all:i386 ]
Remv xserver-xorg-input-all [1:7.7+1ubuntu8.1] [xorg:i386 xserver-xorg-video-all:i386 ]
Remv xserver-xorg-input-wacom [1:0.23.0-0ubuntu2] [xorg:i386 xserver-xorg-video-all:i386 ]
Remv xserver-xorg-input-vmmouse [1:13.0.0-1build1] [xorg:i386 xserver-xorg-video-all:i386 ]
Remv xserver-xorg-input-synaptics [1.7.4-0ubuntu1] [xorg:i386 xserver-xorg-video-all:i386 ]
Remv xserver-xorg-input-mouse [1:1.9.0-1build1] [xorg:i386 xserver-xorg-video-all:i386 ]
Remv xserver-xorg-input-evdev [1:2.8.2-1ubuntu2] [xorg:i386 xserver-xorg-video-all:i386 ]
Remv xserver-xorg-core [2:1.15.1-0ubuntu2.6] [xorg:i386 xserver-xorg-video-all:i386 nvidia-304:i386 ]
Inst xserver-xorg-core-lts-utopic (2:1.16.0-1ubuntu1.2~trusty1 Ubuntu:14.04/trusty-proposed [i386]) [xorg:i386 xserver-xorg-video-all:i386 ]
Remv libgl1-mesa-dri [10.1.3-0ubuntu0.3] [xorg:i386 libgbm1:i386 libxatracker2:i386 xserver-xorg-video-all:i386 ]
Inst libgl1-mesa-dri-lts-utopic (10.3.2-0ubuntu1~trusty1 Ubuntu:14.04/trusty-proposed [i386]) [xorg:i386 xserver-xorg-video-all:i386 ]
Remv libxatracker2 [10.1.3-0ubuntu0.3] [xorg:i386 xserver-xorg-video-all:i386 ]
Remv libgl1-mesa-glx [10.1.3-0ubuntu0.3] [libreoffice-ogltrans:i386 xorg:i386 libgtkglext1:i386 libopencv-core2.4:i386 libwebkitgtk-3.0-0:i386 gnome-session-bin:i386 x11-utils:i386 libvisual-0.4-plugins:i386 xserver-xephyr:i386 libgnome-desktop-3-7:i386 libreoffice-core:i386 libglu1-mesa:i386 xserver-xorg-video-all:i386 libopencv-highgui2.4:i386 libglamor0:i386 ]
Inst libgl1-mesa-glx-lts-utopic (10.3.2-0ubuntu1~trusty1 Ubuntu:14.04/trusty-proposed [i386]) [xorg:i386 xserver-xorg-video-all:i386 ]
Remv libgles2-mesa [10.1.3-0ubuntu0.3] [xorg:i386 xserver-xorg-video-all:i386 gstreamer1.0-plugins-bad:i386 ]
Inst libgles2-mesa-lts-utopic (10.3.2-0ubuntu1~trusty1 Ubuntu:14.04/trusty-proposed [i386]) [xorg:i386 xserver-xorg-video-all:i386 ]
Remv libglapi-mesa [10.1.3-0ubuntu0.3] [xorg:i386 xserver-xorg-video-all:i386 ]
Remv libopenvg1-mesa [10.1.3-0ubuntu0.3] [xorg:i386 xserver-xorg-video-all:i386 ]
Remv xserver-xorg-video-all [1:7.7+1ubuntu8.1] [xorg:i386 ]
Inst xserver-xorg-lts-utopic (1:7.7+7ubuntu2~trusty1 Ubuntu:14.04/trusty-proposed [i386]) []
Inst libepoxy0 (1.1-1 Ubuntu:14.04/trusty [i386]) []
Inst libllvm3.5 (1:3.5-4ubuntu2~trusty1 Ubuntu:14.04/trusty-proposed [i386]) []
Inst libgbm1-lts-utopic (10.3.2-0ubuntu1~trusty1 Ubuntu:14.04/trusty-proposed [i386]) []
Inst libglapi-mesa-lts-utopic (10.3.2-0ubuntu1~trusty1 Ubuntu:14.04/trusty-proposed [i386]) []
Inst xserver-xorg-video-r128-lts-utopic (6.9.2-1build2~trusty1 Ubuntu:14.04/trusty-proposed [i386]) []
Inst xserver-xorg-video-mach64-lts-utopic (6.9.4-2~trusty1 Ubuntu:14.04/trusty-proposed [i386]) []
Inst xserver-xorg-video-radeon-lts-utopic (1:7.4.0-2ubuntu2~trusty1 Ubuntu:14.04/trusty-proposed [i386]) []
Inst xserver-xorg-video-ati-lts-utopic (1:7.4.0-2ubuntu2~trusty1 Ubuntu:14.04/trusty-proposed [i386]) []
Inst xserver-xorg-video-cirrus-lts-utopic (1:1.5.2-2build1~trusty1 Ubuntu:14.04/trusty-proposed [i386]) []
Inst xserver-xorg-video-fbdev-lts-utopic (1:0.4.4-1build2~trusty1 Ubuntu:14.04/trusty-proposed [i386]) []
Inst xserver-xorg-video-intel-lts-utopic (2:2.99.914-1~exp1ubuntu4.2~trusty1 Ubuntu:14.04/trusty-proposed [i386]) []
Inst xserver-xorg-video-mga-lts-utopic (1:1.6.3-2build1~trusty1 Ubuntu:14.04/trusty-proposed [i386]) []
Inst xserver-xorg-video-modesetting-lts-utopic (0.9.0-1build1~trusty1 Ubuntu:14.04/trusty-proposed [i386]) []
Inst xserver-xorg-video-neomagic-lts-utopic (1:1.2.8-1build2~trusty1 Ubuntu:14.04/trusty-proposed [i386]) []
Inst xserver-xorg-video-nouveau-lts-utopic (1:1.0.11-1ubuntu2~trusty1 Ubuntu:14.04/trusty-proposed [i386]) []
Inst xserver-xorg-video-openchrome-lts-utopic (1:0.3.3-1build2~trusty1 Ubuntu:14.04/trusty-proposed [i386]) []
Inst xserver-xorg-video-savage-lts-utopic (1:2.3.7-2ubuntu3~trusty1 Ubuntu:14.04/trusty-proposed [i386]) []
Inst xserver-xorg-video-siliconmotion-lts-utopic (1:1.7.7-2build2~trusty1 Ubuntu:14.04/trusty-proposed [i386]) []
Inst xserver-xorg-video-sisusb-lts-utopic (1:0.9.6-2build2~trusty1 Ubuntu:14.04/trusty-proposed [i386]) []
Inst xserver-xorg-video-tdfx-lts-utopic (1:1.4.5-1build2~trusty1 Ubuntu:14.04/trusty-proposed [i386]) []
Inst xserver-xorg-video-trident-lts-utopic (1:1.3.6-0ubuntu6~trusty1 Ubuntu:14.04/trusty-proposed [i386]) []
Inst xserver-xorg-video-vesa-lts-utopic (1:2.3.3-1build2~trusty1 Ubuntu:14.04/trusty-proposed [i386]) []
Inst libxatracker2-lts-utopic (10.3.2-0ubuntu1~trusty1 Ubuntu:14.04/trusty-proposed [i386]) []
Inst xserver-xorg-video-vmware-lts-utopic (1:13.0.2-3ubuntu1~trusty1 Ubuntu:14.04/trusty-proposed [i386]) []
Inst xserver-xorg-video-all-lts-utopic (1:7.7+7ubuntu2~trusty1 Ubuntu:14.04/trusty-proposed [i386]) []
Inst libevdev2 (1.0.99.2+dfsg-2ubuntu2 Ubuntu:14.04/trusty [i386]) []
Inst xserver-xorg-input-evdev-lts-utopic (1:2.9.0-1ubuntu2~trusty1 Ubuntu:14.04/trusty-proposed [i386])
Inst xserver-xorg-input-mouse-lts-utopic (1:1.9.0-1build2~trusty1 Ubuntu:14.04/trusty-proposed [i386])
Inst xserver-xorg-input-vmmouse-lts-utopic (1:13.0.0-1build2~trusty1 Ubuntu:14.04/trusty-proposed [i386])
Inst xserver-xorg-input-synaptics-lts-utopic (1.8.1-1ubuntu1~trusty1 Ubuntu:14.04/trusty-proposed [i386])
Inst xserver-xorg-input-wacom-lts-utopic (1:0.25.0-0ubuntu1~trusty1 Ubuntu:14.04/trusty-proposed [i386])
Inst xserver-xorg-input-all-lts-utopic (1:7.7+7ubuntu2~trusty1 Ubuntu:14.04/trusty-proposed [i386])
Inst libgles1-mesa-lts-utopic (10.3.2-0ubuntu1~trusty1 Ubuntu:14.04/trusty-proposed [i386])
Inst linux-image-3.16.0-30-generic (3.16.0-30.40~14.04.1 Ubuntu:14.04/trusty-proposed [i386])
Inst linux-image-extra-3.16.0-30-generic (3.16.0-30.40~14.04.1 Ubuntu:14.04/trusty-proposed [i386])
Inst linux-image-generic-lts-utopic (3.16.0.30.23 Ubuntu:14.04/trusty-proposed [i386])
Inst linux-headers-3.16.0-30 (3.16.0-30.40~14.04.1 Ubuntu:14.04/trusty-proposed [all])
Inst linux-headers-3.16.0-30-generic (3.16.0-30.40~14.04.1 Ubuntu:14.04/trusty-proposed [i386])
Inst linux-headers-generic-lts-utopic (3.16.0.30.23 Ubuntu:14.04/trusty-proposed [i386])
Inst linux-generic-lts-utopic (3.16.0.30.23 Ubuntu:14.04/trusty-proposed [i386])
Conf libllvm3.5 (1:3.5-4ubuntu2~trusty1 Ubuntu:14.04/trusty-proposed [i386])
Conf libgl1-mesa-dri-lts-utopic (10.3.2-0ubuntu1~trusty1 Ubuntu:14.04/trusty-proposed [i386])
Conf libgbm1-lts-utopic (10.3.2-0ubuntu1~trusty1 Ubuntu:14.04/trusty-proposed [i386])
Conf libegl1-mesa-lts-utopic (10.3.2-0ubuntu1~trusty1 Ubuntu:14.04/trusty-proposed [i386])
Conf libepoxy0 (1.1-1 Ubuntu:14.04/trusty [i386])
Conf libglapi-mesa-lts-utopic (10.3.2-0ubuntu1~trusty1 Ubuntu:14.04/trusty-proposed [i386])
Conf libgl1-mesa-glx-lts-utopic (10.3.2-0ubuntu1~trusty1 Ubuntu:14.04/trusty-proposed [i386])
Conf xserver-xorg-core-lts-utopic (2:1.16.0-1ubuntu1.2~trusty1 Ubuntu:14.04/trusty-proposed [i386])
Conf libgles2-mesa-lts-utopic (10.3.2-0ubuntu1~trusty1 Ubuntu:14.04/trusty-proposed [i386])
Conf xserver-xorg-video-r128-lts-utopic (6.9.2-1build2~trusty1 Ubuntu:14.04/trusty-proposed [i386])
Conf xserver-xorg-video-mach64-lts-utopic (6.9.4-2~trusty1 Ubuntu:14.04/trusty-proposed [i386])
Conf xserver-xorg-video-radeon-lts-utopic (1:7.4.0-2ubuntu2~trusty1 Ubuntu:14.04/trusty-proposed [i386])
Conf xserver-xorg-video-ati-lts-utopic (1:7.4.0-2ubuntu2~trusty1 Ubuntu:14.04/trusty-proposed [i386])
Conf xserver-xorg-video-cirrus-lts-utopic (1:1.5.2-2build1~trusty1 Ubuntu:14.04/trusty-proposed [i386])
Conf xserver-xorg-video-fbdev-lts-utopic (1:0.4.4-1build2~trusty1 Ubuntu:14.04/trusty-proposed [i386])
Conf xserver-xorg-video-intel-lts-utopic (2:2.99.914-1~exp1ubuntu4.2~trusty1 Ubuntu:14.04/trusty-proposed [i386])
Conf xserver-xorg-video-mga-lts-utopic (1:1.6.3-2build1~trusty1 Ubuntu:14.04/trusty-proposed [i386])
Conf xserver-xorg-video-modesetting-lts-utopic (0.9.0-1build1~trusty1 Ubuntu:14.04/trusty-proposed [i386])
Conf xserver-xorg-video-neomagic-lts-utopic (1:1.2.8-1build2~trusty1 Ubuntu:14.04/trusty-proposed [i386])
Conf xserver-xorg-video-nouveau-lts-utopic (1:1.0.11-1ubuntu2~trusty1 Ubuntu:14.04/trusty-proposed [i386])
Conf xserver-xorg-video-openchrome-lts-utopic (1:0.3.3-1build2~trusty1 Ubuntu:14.04/trusty-proposed [i386])
Conf xserver-xorg-video-savage-lts-utopic (1:2.3.7-2ubuntu3~trusty1 Ubuntu:14.04/trusty-proposed [i386])
Conf xserver-xorg-video-siliconmotion-lts-utopic (1:1.7.7-2build2~trusty1 Ubuntu:14.04/trusty-proposed [i386])
Conf xserver-xorg-video-sisusb-lts-utopic (1:0.9.6-2build2~trusty1 Ubuntu:14.04/trusty-proposed [i386])
Conf xserver-xorg-video-tdfx-lts-utopic (1:1.4.5-1build2~trusty1 Ubuntu:14.04/trusty-proposed [i386])
Conf xserver-xorg-video-trident-lts-utopic (1:1.3.6-0ubuntu6~trusty1 Ubuntu:14.04/trusty-proposed [i386])
Conf xserver-xorg-video-vesa-lts-utopic (1:2.3.3-1build2~trusty1 Ubuntu:14.04/trusty-proposed [i386])
Conf libxatracker2-lts-utopic (10.3.2-0ubuntu1~trusty1 Ubuntu:14.04/trusty-proposed [i386])
Conf xserver-xorg-video-vmware-lts-utopic (1:13.0.2-3ubuntu1~trusty1 Ubuntu:14.04/trusty-proposed [i386])
Conf xserver-xorg-video-all-lts-utopic (1:7.7+7ubuntu2~trusty1 Ubuntu:14.04/trusty-proposed [i386])
Conf libevdev2 (1.0.99.2+dfsg-2ubuntu2 Ubuntu:14.04/trusty [i386])
Conf xserver-xorg-input-evdev-lts-utopic (1:2.9.0-1ubuntu2~trusty1 Ubuntu:14.04/trusty-proposed [i386])
Conf xserver-xorg-input-mouse-lts-utopic (1:1.9.0-1build2~trusty1 Ubuntu:14.04/trusty-proposed [i386])
Conf xserver-xorg-input-vmmouse-lts-utopic (1:13.0.0-1build2~trusty1 Ubuntu:14.04/trusty-proposed [i386])
Conf xserver-xorg-input-synaptics-lts-utopic (1.8.1-1ubuntu1~trusty1 Ubuntu:14.04/trusty-proposed [i386])
Conf xserver-xorg-input-wacom-lts-utopic (1:0.25.0-0ubuntu1~trusty1 Ubuntu:14.04/trusty-proposed [i386])
Conf xserver-xorg-input-all-lts-utopic (1:7.7+7ubuntu2~trusty1 Ubuntu:14.04/trusty-proposed [i386])
Conf xserver-xorg-lts-utopic (1:7.7+7ubuntu2~trusty1 Ubuntu:14.04/trusty-proposed [i386])
Conf libgles1-mesa-lts-utopic (10.3.2-0ubuntu1~trusty1 Ubuntu:14.04/trusty-proposed [i386])
Conf linux-image-3.16.0-30-generic (3.16.0-30.40~14.04.1 Ubuntu:14.04/trusty-proposed [i386])
Conf linux-image-extra-3.16.0-30-generic (3.16.0-30.40~14.04.1 Ubuntu:14.04/trusty-proposed [i386])
Conf linux-image-generic-lts-utopic (3.16.0.30.23 Ubuntu:14.04/trusty-proposed [i386])
Conf linux-headers-3.16.0-30 (3.16.0-30.40~14.04.1 Ubuntu:14.04/trusty-proposed [all])
Conf linux-headers-3.16.0-30-generic (3.16.0-30.40~14.04.1 Ubuntu:14.04/trusty-proposed [i386])
Conf linux-headers-generic-lts-utopic (3.16.0.30.23 Ubuntu:14.04/trusty-proposed [i386])
Conf linux-generic-lts-utopic (3.16.0.30.23 Ubuntu:14.04/trusty-proposed [i386])

```

So I'll give a heads up to Ubuntu GNOME dev.

---

### Post by ian-weisser on 2015-01-30
Reminder to new users:

The -proposed repository is for testing, not regular use. Breakage happens there. You're welcome to try it...at your own risk. If you would like to get involved with testing, this is one place to start.

The -updates repository is for supported, tested, released updates in regular use. This forum supports these.

---

### Post by kansasnoob on 2015-01-30
> **ian-weisser said:**
> Reminder to new users:

The -proposed repository is for testing, not regular use. Breakage happens there. You're welcome to try it...at your own risk. If you would like to get involved with testing, this is one place to start.

The -updates repository is for supported, tested, released updates in regular use. This forum supports these.

+1! If you break it you get to keep both pieces :lolflag:

---

### Post by kansasnoob on 2015-01-30
Heads up given to Ubuntu GNOME dev and QA:

[https://lists.launchpad.net/ubuntugnome-qa/msg00692.html](https://lists.launchpad.net/ubuntugnome-qa/msg00692.html)

That's all part of the sausage making process ;)

---

### Post by zika on 2015-01-30
What is the reason to use```
--install-recommends
```?That way You'll get a lot of cruft that You do not really need. Is it not easiear and cleaner to go ordinary way?[COLOR=#000000][FONT=Ubuntu Mono]



[/FONT][/COLOR]

---

### Post by kansasnoob on 2015-01-30
> **zika said:**
> What is the reason to use```
--install-recommends
```?That way You'll get a lot of cruft that You do not really need. Is it not easiear and cleaner to go ordinary way?[COLOR=#000000][FONT=Ubuntu Mono]



[/FONT][/COLOR]

That basically just comes from here:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

But I just took it from what the OP posted with the -s suffix to see what would happen. I'm iso-testing the daily images anyway.

But I see there it says to just:

```
 sudo apt-get install --install-recommends linux-generic-lts-utopic
```

So maybe they're changing the way things work with HWE in Trusty. In Precise you had to upgrade both the kernel and Xstack but maybe they're going to do Trusty in such a way as to only upgrade the kernel :confused:

---

### Post by kansasnoob on 2015-01-30
This looks better:

```
lance@lance-desktop:~$  sudo apt-get install --install-recommends linux-generic-lts-utopic -s
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  linux-headers-3.16.0-30 linux-headers-3.16.0-30-generic
  linux-headers-generic-lts-utopic linux-image-3.16.0-30-generic
  linux-image-extra-3.16.0-30-generic linux-image-generic-lts-utopic
Suggested packages:
  fdutils linux-lts-utopic-tools
The following NEW packages will be installed:
  linux-generic-lts-utopic linux-headers-3.16.0-30
  linux-headers-3.16.0-30-generic linux-headers-generic-lts-utopic
  linux-image-3.16.0-30-generic linux-image-extra-3.16.0-30-generic
  linux-image-generic-lts-utopic
0 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
Inst linux-image-3.16.0-30-generic (3.16.0-30.40~14.04.1 Ubuntu:14.04/trusty-updates [i386])
Inst linux-image-extra-3.16.0-30-generic (3.16.0-30.40~14.04.1 Ubuntu:14.04/trusty-updates [i386])
Inst linux-image-generic-lts-utopic (3.16.0.30.23 Ubuntu:14.04/trusty-updates [i386])
Inst linux-headers-3.16.0-30 (3.16.0-30.40~14.04.1 Ubuntu:14.04/trusty-updates [all])
Inst linux-headers-3.16.0-30-generic (3.16.0-30.40~14.04.1 Ubuntu:14.04/trusty-updates [i386])
Inst linux-headers-generic-lts-utopic (3.16.0.30.23 Ubuntu:14.04/trusty-updates [i386])
Inst linux-generic-lts-utopic (3.16.0.30.23 Ubuntu:14.04/trusty-updates [i386])
Conf linux-image-3.16.0-30-generic (3.16.0-30.40~14.04.1 Ubuntu:14.04/trusty-updates [i386])
Conf linux-image-extra-3.16.0-30-generic (3.16.0-30.40~14.04.1 Ubuntu:14.04/trusty-updates [i386])
Conf linux-image-generic-lts-utopic (3.16.0.30.23 Ubuntu:14.04/trusty-updates [i386])
Conf linux-headers-3.16.0-30 (3.16.0-30.40~14.04.1 Ubuntu:14.04/trusty-updates [all])
Conf linux-headers-3.16.0-30-generic (3.16.0-30.40~14.04.1 Ubuntu:14.04/trusty-updates [i386])
Conf linux-headers-generic-lts-utopic (3.16.0.30.23 Ubuntu:14.04/trusty-updates [i386])
Conf linux-generic-lts-utopic (3.16.0.30.23 Ubuntu:14.04/trusty-updates [i386])

```

---

### Post by kansasnoob on 2015-01-30
> **kansasnoob said:**
> This looks better:

```
lance@lance-desktop:~$  sudo apt-get install --install-recommends linux-generic-lts-utopic -s
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  linux-headers-3.16.0-30 linux-headers-3.16.0-30-generic
  linux-headers-generic-lts-utopic linux-image-3.16.0-30-generic
  linux-image-extra-3.16.0-30-generic linux-image-generic-lts-utopic
Suggested packages:
  fdutils linux-lts-utopic-tools
The following NEW packages will be installed:
  linux-generic-lts-utopic linux-headers-3.16.0-30
  linux-headers-3.16.0-30-generic linux-headers-generic-lts-utopic
  linux-image-3.16.0-30-generic linux-image-extra-3.16.0-30-generic
  linux-image-generic-lts-utopic
0 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
Inst linux-image-3.16.0-30-generic (3.16.0-30.40~14.04.1 Ubuntu:14.04/trusty-updates [i386])
Inst linux-image-extra-3.16.0-30-generic (3.16.0-30.40~14.04.1 Ubuntu:14.04/trusty-updates [i386])
Inst linux-image-generic-lts-utopic (3.16.0.30.23 Ubuntu:14.04/trusty-updates [i386])
Inst linux-headers-3.16.0-30 (3.16.0-30.40~14.04.1 Ubuntu:14.04/trusty-updates [all])
Inst linux-headers-3.16.0-30-generic (3.16.0-30.40~14.04.1 Ubuntu:14.04/trusty-updates [i386])
Inst linux-headers-generic-lts-utopic (3.16.0.30.23 Ubuntu:14.04/trusty-updates [i386])
Inst linux-generic-lts-utopic (3.16.0.30.23 Ubuntu:14.04/trusty-updates [i386])
Conf linux-image-3.16.0-30-generic (3.16.0-30.40~14.04.1 Ubuntu:14.04/trusty-updates [i386])
Conf linux-image-extra-3.16.0-30-generic (3.16.0-30.40~14.04.1 Ubuntu:14.04/trusty-updates [i386])
Conf linux-image-generic-lts-utopic (3.16.0.30.23 Ubuntu:14.04/trusty-updates [i386])
Conf linux-headers-3.16.0-30 (3.16.0-30.40~14.04.1 Ubuntu:14.04/trusty-updates [all])
Conf linux-headers-3.16.0-30-generic (3.16.0-30.40~14.04.1 Ubuntu:14.04/trusty-updates [i386])
Conf linux-headers-generic-lts-utopic (3.16.0.30.23 Ubuntu:14.04/trusty-updates [i386])
Conf linux-generic-lts-utopic (3.16.0.30.23 Ubuntu:14.04/trusty-updates [i386])

```

I went ahead with that and the kernel upgrade worked great.

---

### Post by zika on 2015-01-30
What happens if You simply apply```
sudo apt-get update ; sudo apt-get dist-upgrade -s
```(with proposed turned on, just to allow packages that are waiting to propagate)...? That way we could see if I'm completely wrong... ;) I do not have any Trusty at hand to confirm that.
That way You just install/upgrade what is needed and ready and add only those packages that are marked as dependencies (taking care not to accept it if there are packages that are to be removed despite You do need them)...
Nothing seems to have changed in that process, except, maybe, some net-pages, I'm not sure because I did not read them before... ;) Just my 2¢... ;)

---

### Post by kansasnoob on 2015-01-30
> **zika said:**
> What happens if You simply apply```
sudo apt-get update ; sudo apt-get dist-upgrade -s
```(with proposed turned on, just to allow packages that are waiting to propagate)...? That way we could see if I'm completely wrong... ;) I do not have any Trusty at hand to confirm that.
That way You just install/upgrade what is needed and ready and add only those packages that are marked as dependencies (taking care not to accept it if there are packages that are to be removed despite You do need them)...
Nothing seems to have changed in that process, except, maybe, some net-pages, I'm not sure because I did not read them before... ;) Just my 2¢... ;)

If you install Trusty from the current daily images the proposed updates are enabled via /etc/apt/sources.list.d:

```
lance@lance-desktop:~$ ls /etc/apt/sources.list.d
proposed.list
lance@lance-desktop:~$ cat /etc/apt/sources.list.d/proposed.list
deb http://archive.ubuntu.com/ubuntu/ trusty-proposed main restricted universe

```

And dist-upgrade after install did nothing, but the images had just been re-spun about 2 hours earlier.

Things are just not quite ready yet.

---

### Post by mc4man on 2015-01-30
> **zika said:**
> What happens if You simply apply```
sudo apt-get update ; sudo apt-get dist-upgrade -s
```(with proposed turned on, just to allow packages that are waiting to propagate)...? That way we could see if I'm completely wrong... ;) I do not have any Trusty at hand to confirm that.
That way You just install/upgrade what is needed and ready and add only those packages that are marked as dependencies (taking care not to accept it if there are packages that are to be removed despite You do need them)...
Nothing seems to have changed in that process, except, maybe, some net-pages, I'm not sure because I did not read them before... ;) Just my 2¢... ;)

None of the lts packages that this thread is about are considered upgrades

---

### Post by zika on 2015-01-30
> **mc4man said:**
> None of the lts packages that this thread is about are considered upgradesThen I **am **&#8203;completely wrong. Thank You.

---

