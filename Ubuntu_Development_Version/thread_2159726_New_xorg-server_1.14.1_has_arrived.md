---
title: "New xorg-server 1.14.1 has arrived"
date: 2013-07-04
forum: Ubuntu Development Version
---

### Post by Harry33 on 2013-07-04
We have now xorg-server 1.14.1 in Ubuntu official repos (proposed).
If you have proposed enabled, do not try to upgrade your xorg-server 1.13 branch yet.
It would break the X completely.
There is a ABI change:
 - xorg-input-abi-18                          to xorg-input-abi-19
 - xorg-video-abi-13 to xorg-video-abi-14

Before a successful installation we need new graphic drivers and input drivers built against the new ABIs.

Here:
[https://launchpad.net/ubuntu/saucy/+source/xorg-server/2:1.14.1-0ubuntu0.8](https://launchpad.net/ubuntu/saucy/+source/xorg-server/2:1.14.1-0ubuntu0.8)

---

### Post by VinDSL on 2013-07-04
Thanks, for the *WARNING* Harry!  ;)

Actually, I think I'll wait for Ricotz to release a  'xserver-xorg-core' upgrade, before replacing 1.13

---

### Post by slickymaster on 2013-07-04
Great news. Thanks for the heads up.

---

### Post by zika on 2013-07-04
```
The following packages will be REMOVED:  xserver-xorg-input-all xserver-xorg-input-synaptics xserver-xorg-video-all
  xserver-xorg-video-ati xserver-xorg-video-cirrus xserver-xorg-video-intel
  xserver-xorg-video-mach64 xserver-xorg-video-r128 xserver-xorg-video-radeon
The following packages have been kept back:
  libmirserver0 unity-system-compositor
The following packages will be upgraded:
  xserver-xorg-core xserver-xorg-input-evdev xserver-xorg-input-mouse
  xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-fbdev
  xserver-xorg-video-mga xserver-xorg-video-modesetting
  xserver-xorg-video-neomagic xserver-xorg-video-nouveau
  xserver-xorg-video-openchrome xserver-xorg-video-qxl xserver-xorg-video-s3
  xserver-xorg-video-savage xserver-xorg-video-siliconmotion
  xserver-xorg-video-sis xserver-xorg-video-sisusb xserver-xorg-video-tdfx
  xserver-xorg-video-trident xserver-xorg-video-vesa xserver-xorg-video-vmware
21 upgraded, 1 newly installed, 9 to remove and 2 not upgraded.
Need to get 3,162 kB of archives.
After this operation, 2,843 kB disk space will be freed.
```
It is coming slowly... Yesterday and the day before yesterday it was even worse... ATI comes always latest... ;)
(&#8222;proposed&#8220; not enabled...)

With &#8222;proposed&#8220; enabled:
```
The following packages will be REMOVED:  lightdm-remote-session-uccsconfigure ubuntu-desktop unity unity-tweak-tool xserver-xorg-input-all xserver-xorg-input-synaptics xserver-xorg-video-all xserver-xorg-video-ati xserver-xorg-video-cirrus xserver-xorg-video-intel xserver-xorg-video-mach64 xserver-xorg-video-r128 xserver-xorg-video-radeon
The following NEW packages will be installed:
  libgc1c2
The following packages have been kept back:
  libmirserver0 unity-system-compositor usb-modeswitch-data
The following packages will be upgraded:
  account-plugin-facebook account-plugin-flickr account-plugin-google account-plugin-identica account-plugin-twitter account-plugin-windows-live compiz compiz-core compiz-gnome compiz-plugins compiz-plugins-default compizconfig-settings-manager guile-2.0-libs libaccount-plugin-generic-oauth libaccount-plugin-google libcompizconfig0
  libdecoration0 libqt4-dbus libqt4-declarative libqt4-designer libqt4-help libqt4-network libqt4-opengl libqt4-script libqt4-scripttools libqt4-sql libqt4-sql-sqlite libqt4-svg libqt4-test libqt4-xml libqt4-xmlpatterns libqtcore4 libqtgui4 libxfixes3 libxi6 python-compizconfig qdbus xserver-common xserver-xephyr xserver-xorg
  xserver-xorg-core xserver-xorg-input-evdev xserver-xorg-input-mouse xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-fbdev xserver-xorg-video-mga xserver-xorg-video-modesetting xserver-xorg-video-neomagic xserver-xorg-video-nouveau xserver-xorg-video-openchrome xserver-xorg-video-qxl xserver-xorg-video-s3
  xserver-xorg-video-savage xserver-xorg-video-siliconmotion xserver-xorg-video-sis xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident xserver-xorg-video-vesa xserver-xorg-video-vmware
61 upgraded, 1 newly installed, 13 to remove and 3 not upgraded.
Need to get 27.5 MB of archives.
After this operation, 12.3 MB disk space will be freed.
Do you want to continue [Y/n]? 
```

---

### Post by slickymaster on 2013-07-04
> **zika said:**
> [code]...
... ATI comes always latest... ;)
...

Yes, unfortunately.

---

### Post by dino99 on 2013-07-04
the installation/upgrade can be done now, except it remove unity (need at least 7.02) and also unity-tweak-tool.

if you have activated > ppa:ubuntu-unity/daily-build then the whole upgrade can be done without trouble.

---

### Post by zika on 2013-07-04
> **dino99 said:**
> the installation/upgrade can be done now, except it remove unity (need at least 7.02) and also unity-tweak-tool.

if you have activated  then the whole upgrade can be done without trouble.
Thank You!
One more pebble in my show called 13.10... ;)

Update&#8321;: Nope, That did not help... Same situation... :P

---

### Post by xeizo on 2013-07-04
It works fine here(1.14.1) with Nvidia 319.32, but only on the daily kernel from 0107, any later daily kernel fails to build the nvidia-blob and the official 3.10.0-1 freezes during boot even without Nvidia. I haven't tried 3.10.0-2, it's possible it works. Good that the daily from 0107 works anyway, I wonder how long before I can update it  :mrgreen:

I don't use ppa:ubuntu-unity/daily-build...

---

### Post by Harry33 on 2013-07-04
> **xeizo said:**
> It works fine here(1.14.1) with Nvidia 319.32, but only on the daily kernel from 0107, any later daily kernel fails to build the nvidia-blob and the official 3.10.0-1 freezes during boot even without Nvidia. I haven't tried 3.10.0-2, it's possible it works. Good that the daily from 0107 works anyway, I wonder how long before I can update it  :mrgreen:

I don't use ppa:ubuntu-unity/daily-build...

Nvidia-325 (the latest beta release) from xorg-edgers is just fine.
I use it with main line kernel (3.10.0-031000).

---

### Post by xeizo on 2013-07-04
> **Harry33 said:**
> Nvidia-325 (the latest beta release) from xorg-edgers is just fine.
I use it with main line kernel (3.10.0-031000).

Nvidia-325, good you mentioned that one, forgot about it. Yes, it runs fine too on 3.10.0-999-generic from the first of July. But now I don't have the patience to test more kernels today :P

---

### Post by zika on 2013-07-05
With &#8222;proposed&#8220; turned on it **is **moving forward:
```
 The following packages will be REMOVED:  activity-log-manager-common xserver-xorg-input-all xserver-xorg-input-synaptics xserver-xorg-video-all xserver-xorg-video-ati xserver-xorg-video-cirrus xserver-xorg-video-mach64 xserver-xorg-video-r128
The following NEW packages will be installed:
  libgc1c2
The following packages have been kept back:
  libmirserver0 unity-system-compositor usb-modeswitch-data
The following packages will be upgraded:
  activity-log-manager apparmor compiz compiz-core compiz-gnome compiz-plugins compiz-plugins-default compizconfig-settings-manager gir1.2-gudev-1.0 guile-2.0-libs libapparmor-perl libapparmor1 libcompizconfig0 libdecoration0 libgudev-1.0-0 libpam-systemd libqt4-dbus libqt4-declarative libqt4-designer libqt4-help libqt4-network
  libqt4-opengl libqt4-script libqt4-scripttools libqt4-sql libqt4-sql-sqlite libqt4-svg libqt4-test libqt4-xml libqt4-xmlpatterns libqtcore4 libqtgui4 libsystemd-daemon0 libsystemd-journal0 libsystemd-login0 libudev1 libunity-core-6.0-7 libxfixes3 libxi6 mesa-utils python-compizconfig qdbus systemd-services ubuntu-drivers-common udev
  unity unity-common unity-services xserver-common xserver-xephyr xserver-xorg xserver-xorg-core xserver-xorg-input-evdev xserver-xorg-input-mouse xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-fbdev xserver-xorg-video-intel xserver-xorg-video-mga xserver-xorg-video-modesetting xserver-xorg-video-neomagic
  xserver-xorg-video-nouveau xserver-xorg-video-openchrome xserver-xorg-video-qxl xserver-xorg-video-radeon xserver-xorg-video-s3 xserver-xorg-video-savage xserver-xorg-video-siliconmotion xserver-xorg-video-sis xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident xserver-xorg-video-vesa
  xserver-xorg-video-vmware
```...
Just a small step... Virtual packages, mostly...

For comparison purposes, without &#8222;proposed&#8220; turned on, at my machine (lots of other PPAs turned on, Ricotz's, xorg-edgers and others...):
```
The following packages have been kept back:  activity-log-manager libmirserver0 libunity-core-6.0-7 unity unity-common unity-services unity-system-compositor xserver-xorg-core xserver-xorg-input-evdev xserver-xorg-input-mouse xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-ati xserver-xorg-video-fbdev xserver-xorg-video-intel xserver-xorg-video-mga
  xserver-xorg-video-modesetting xserver-xorg-video-neomagic xserver-xorg-video-nouveau xserver-xorg-video-openchrome xserver-xorg-video-qxl xserver-xorg-video-radeon xserver-xorg-video-s3 xserver-xorg-video-savage xserver-xorg-video-siliconmotion xserver-xorg-video-sis xserver-xorg-video-sisusb xserver-xorg-video-tdfx
  xserver-xorg-video-trident xserver-xorg-video-vesa xserver-xorg-video-vmware
The following packages will be upgraded:
  xserver-common xserver-xephyr
```

---

### Post by xeizo on 2013-07-05
Today I got 1.14.2, I tried with todays daily kernel but nvidia-325 didn't build(header error). So, I tried with 3.10.0-2 from the repos instead and nvidia-325 did build allright, so now I'm running Xorg 1.14.2 with the latest Nvidia-blob  :-)

---

### Post by Scofa on 2013-07-06
How do i install xorg-server 1.14.1 and configure it?
My system is:

MSI GT70ONE Laptop with Nvidia GTX675MX
Intel Core I7-3630QM

---

### Post by VinDSL on 2013-07-06
> **Scofa said:**
> How do i install xorg-server 1.14.1 on Ubuntu Saucy Salamander ?
There are several ways...

I installed xserver-xephyr & xserver-common, via the edger's PPA, using Synaptic.

xserver-xorg-core is available on the edger's PPA also, but it wants to strip my system to bare-bones.

Put another way, I did a partial install (which I don't recommend, if you're new to testing).  ;)

At this point, I'm trying to figure out a way to force xserver-xorg-core, without wiping out my install...

---

### Post by zika on 2013-07-07
Any news on ETA?
New xorg-server 1.14.1 has not yet arrived.. ;)

---

### Post by VinDSL on 2013-07-07
> **zika said:**
> Any news on ETA?
New xorg-server 1.14.1 has not yet arrived.. ;)
I'm watching for it in Ricotz's PPAs.

SOURCE:  [https://launchpad.net/~ricotz/+ppa-packages](https://launchpad.net/~ricotz/+ppa-packages)

He's got a wayland-enabled version in 'unstable' right now.

The Edger's version has dependency issues on this machine...

---

### Post by P-I H on 2013-07-08
Just made these updates and it worked

```
Commit Log for Mon Jul  8 20:25:24 2013




Upgraded the following packages:
apparmor (2.8.0-0ubuntu19) to 2.8.0-0ubuntu19.1
apport (2.10.2-0ubuntu3) to 2.10.2-0ubuntu4
apport-gtk (2.10.2-0ubuntu3) to 2.10.2-0ubuntu4
dpkg (1.16.10ubuntu2) to 1.16.10ubuntu3
dpkg-dev (1.16.10ubuntu2) to 1.16.10ubuntu3
gtk2-engines-pixbuf (2.24.19-0ubuntu1) to 2.24.20-1ubuntu1
indicator-datetime (12.10.3+13.10.20130703.1-0ubuntu1) to 12.10.3+13.10.20130708-0ubuntu1
indicator-power (12.10.6+13.10.20130703.1-0ubuntu1) to 12.10.6+13.10.20130708-0ubuntu1
libapparmor-perl (2.8.0-0ubuntu19) to 2.8.0-0ubuntu19.1
libapparmor1 (2.8.0-0ubuntu19) to 2.8.0-0ubuntu19.1
libdpkg-perl (1.16.10ubuntu2) to 1.16.10ubuntu3
libgail-common (2.24.19-0ubuntu1) to 2.24.20-1ubuntu1
libgail18 (2.24.19-0ubuntu1) to 2.24.20-1ubuntu1
libgtk2.0-0 (2.24.19-0ubuntu1) to 2.24.20-1ubuntu1
libgtk2.0-bin (2.24.19-0ubuntu1) to 2.24.20-1ubuntu1
libgtk2.0-common (2.24.19-0ubuntu1) to 2.24.20-1ubuntu1
libqpdf10 (4.1.0-2) to 4.2.0-1
libunity-core-6.0-7 (7.0.1+13.10.20130703-0ubuntu1) to 7.0.2+13.10.20130705.1-0ubuntu1
libunity-gtk2-parser0 (0.0.0+13.10.20130702-0ubuntu1) to 0.0.0+13.10.20130708-0ubuntu1
libunity-gtk3-parser0 (0.0.0+13.10.20130702-0ubuntu1) to 0.0.0+13.10.20130708-0ubuntu1
libxfixes3 (1:5.0-4ubuntu6) to 1:5.0.1-1ubuntu1
libxfixes3:i386 (1:5.0-4ubuntu6) to 1:5.0.1-1ubuntu1
libxi6 (2:1.6.99.1-0ubuntu4) to 2:1.7.1.901-1ubuntu1
libxi6:i386 (2:1.6.99.1-0ubuntu4) to 2:1.7.1.901-1ubuntu1
nvidia-319 (319.32-0ubuntu1) to 319.32-0ubuntu2
python3-apport (2.10.2-0ubuntu3) to 2.10.2-0ubuntu4
python3-problem-report (2.10.2-0ubuntu3) to 2.10.2-0ubuntu4
qpdf (4.1.0-2) to 4.2.0-1
unity (7.0.1+13.10.20130703-0ubuntu1) to 7.0.2+13.10.20130705.1-0ubuntu1
unity-common (7.0.1+13.10.20130703-0ubuntu1) to 7.0.2+13.10.20130705.1-0ubuntu1
unity-gtk-module-common (0.0.0+13.10.20130702-0ubuntu1) to 0.0.0+13.10.20130708-0ubuntu1
unity-gtk2-module (0.0.0+13.10.20130702-0ubuntu1) to 0.0.0+13.10.20130708-0ubuntu1
unity-gtk3-module (0.0.0+13.10.20130702-0ubuntu1) to 0.0.0+13.10.20130708-0ubuntu1
unity-services (7.0.1+13.10.20130703-0ubuntu1) to 7.0.2+13.10.20130705.1-0ubuntu1
xserver-common (2:1.13.3-0ubuntu13) to 2:1.14.1-0ubuntu0.8
xserver-xorg-core (2:1.13.3-0ubuntu13) to 2:1.14.1-0ubuntu0.8
xserver-xorg-input-evdev (1:2.7.3-0ubuntu2b2) to 1:2.7.3-0ubuntu3.1
xserver-xorg-input-mouse (1:1.7.2-3) to 1:1.7.2-3build1
xserver-xorg-input-synaptics (1.6.2-1ubuntu6) to 1.6.3-0ubuntu1.1
xserver-xorg-input-vmmouse (1:12.9.0-0ubuntu3) to 1:12.9.0-0ubuntu4
xserver-xorg-input-wacom (1:0.19.0-0ubuntu1) to 1:0.19.0-0ubuntu3.3
xserver-xorg-video-ati (1:7.1.0-0ubuntu2) to 1:7.1.0-0ubuntu2.1
xserver-xorg-video-cirrus (1:1.5.2-0ubuntu1) to 1:1.5.2-0ubuntu2
xserver-xorg-video-fbdev (1:0.4.3-0ubuntu1) to 1:0.4.3-0ubuntu3
xserver-xorg-video-intel (2:2.21.9-0ubuntu2) to 2:2.21.9-0ubuntu3
xserver-xorg-video-mach64 (6.9.3-0ubuntu1) to 6.9.3-0ubuntu3
xserver-xorg-video-mga (1:1.6.2-0ubuntu1) to 1:1.6.2-0ubuntu2
xserver-xorg-video-modesetting (0.8.0-0ubuntu1) to 0.8.0-0ubuntu1.1
xserver-xorg-video-neomagic (1:1.2.7-0ubuntu1) to 1:1.2.7-0ubuntu3
xserver-xorg-video-nouveau (1:1.0.8-0ubuntu1) to 1:1.0.8-0ubuntu1.1
xserver-xorg-video-openchrome (1:0.3.1-0ubuntu2) to 1:0.3.1-0ubuntu2.1
xserver-xorg-video-qxl (0.1.0-0ubuntu3) to 0.1.0-0ubuntu3.1
xserver-xorg-video-r128 (6.9.1-0ubuntu1) to 6.9.1-0ubuntu2
xserver-xorg-video-radeon (1:7.1.0-0ubuntu2) to 1:7.1.0-0ubuntu2.1
xserver-xorg-video-s3 (1:0.6.5-0ubuntu3) to 1:0.6.5-0ubuntu3.1
xserver-xorg-video-savage (1:2.3.6-0ubuntu2) to 1:2.3.6-0ubuntu3
xserver-xorg-video-siliconmotion (1:1.7.7-0ubuntu1) to 1:1.7.7-0ubuntu3
xserver-xorg-video-sis (1:0.10.7-0ubuntu1) to 1:0.10.7-0ubuntu4
xserver-xorg-video-sisusb (1:0.9.6-0ubuntu1) to 1:0.9.6-0ubuntu3
xserver-xorg-video-tdfx (1:1.4.5-0ubuntu1) to 1:1.4.5-0ubuntu3
xserver-xorg-video-trident (1:1.3.6-0ubuntu2) to 1:1.3.6-0ubuntu4
xserver-xorg-video-vesa (1:2.3.2-0ubuntu1) to 1:2.3.2-0ubuntu3
xserver-xorg-video-vmware (1:12.0.2+git.e5ac80d8-0ubuntu1) to 1:13.0.0-0ubuntu0.2
```

---

### Post by zika on 2013-07-08
Here at my place:```
The following packages will be REMOVED:
  activity-log-manager-common audacious xserver-xorg-input-all
  xserver-xorg-input-synaptics xserver-xorg-video-all xserver-xorg-video-ati
  xserver-xorg-video-cirrus xserver-xorg-video-mach64 xserver-xorg-video-r128
The following NEW packages will be installed:
  libgc1c2
The following packages have been kept back:
  libmirserver0 unity-system-compositor usb-modeswitch-data
The following packages will be upgraded:
  activity-log-manager apparmor compiz compiz-core compiz-gnome compiz-plugins
  compiz-plugins-default compizconfig-settings-manager gir1.2-gudev-1.0
  guile-2.0-libs krb5-locales libapparmor-perl libapparmor1 libaudclient2
  libaudcore1 libcompizconfig0 libdecoration0 libexpat1 libgssapi-krb5-2
  libgudev-1.0-0 libjs-jquery libk5crypto3 libkrb5-3 libkrb5support0
  libpam-systemd libqt4-dbus libqt4-declarative libqt4-designer libqt4-help
  libqt4-network libqt4-opengl libqt4-script libqt4-scripttools libqt4-sql
  libqt4-sql-sqlite libqt4-svg libqt4-test libqt4-xml libqt4-xmlpatterns
  libqt5core5 libqt5dbus5 libqt5gui5 libqt5network5 libqt5opengl5
  libqt5printsupport5 libqt5sql5 libqt5sql5-sqlite libqt5test5 libqt5widgets5
  libqt5xml5 libqtcore4 libqtgui4 libsystemd-daemon0 libsystemd-journal0
  libsystemd-login0 libudev1 libunity-core-6.0-7 libxfixes3 libxi6
  python-compizconfig qdbus systemd-services ucf udev unity unity-common
  unity-services xserver-xorg-core xserver-xorg-input-evdev
  xserver-xorg-input-mouse xserver-xorg-input-vmmouse xserver-xorg-input-wacom
  xserver-xorg-video-fbdev xserver-xorg-video-intel xserver-xorg-video-mga
  xserver-xorg-video-modesetting xserver-xorg-video-neomagic
  xserver-xorg-video-nouveau xserver-xorg-video-openchrome
  xserver-xorg-video-qxl xserver-xorg-video-radeon xserver-xorg-video-s3
  xserver-xorg-video-savage xserver-xorg-video-siliconmotion
  xserver-xorg-video-sis xserver-xorg-video-sisusb xserver-xorg-video-tdfx
  xserver-xorg-video-trident xserver-xorg-video-vesa xserver-xorg-video-vmware
```with &#8222;proposed&#8220; enabled...
Still waiting for *-all packages to be build right... It is improving... Nevertheless, I do have almost everything already from Ricotz at right version... ;)

---

### Post by VinDSL on 2013-07-08
I'm in...  :D

```
vindsl@Zuul:~$ echo && echo "~ VinDSL Unity Debug Script 13.07.08 (vindsl.com) ~" && echo -n "Current Date/Time: " && TZ='UTC' date && echo -n "Distro Release: " && lsb_release -sd && echo -n "Kernel Release: " || cat /etc/*release && uname -s -r && echo -n "Gnome Release: " && gnome-shell --version && echo -n "Unity Release: " && unity --version && echo && /usr/lib/nux/unity_support_test -p -f && echo || echo && dpkg -s mesa-utils && echo || echo && echo "Package: mesa-common-dev" && dpkg -s mesa-common-dev | sed 's/^/  /' | grep Version && echo || echo && echo "Package: xserver-xorg-core" && apt-cache policy xserver-xorg-core | grep Installed && echo || echo && echo "Package: xserver-common" && apt-cache policy xserver-common | grep Installed && echo || echo && echo "Package: xserver-xephyr" && apt-cache policy xserver-xephyr | grep Installed && echo || echo && echo "Tree Map of PCI Devices:" && lspci -tv && echo || echo && echo "Display Properties:" && echo -n " lcd monitor:    Dell UltraSharp 1907FP (analog input)" && echo && xdpyinfo | grep -E '(resolution|dimensions)' && echo

~ VinDSL Unity Debug Script 13.07.08 (vindsl.com) ~
Current Date/Time: Tue Jul  9 02:03:41 UTC 2013
Distro Release: Ubuntu Saucy Salamander (development branch)
Kernel Release: Linux 3.10.0-031000-generic
Gnome Release: GNOME Shell 3.9.3
Unity Release: unity 7.0.2

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 7600 GT/AGP/SSE2
OpenGL version string:  2.1.2 NVIDIA 304.88

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

Package: mesa-utils
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 115
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Architecture: i386
Source: mesa-demos
Version: 8.1.0-0ubuntu1
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.4), libgl1-mesa-glx | libgl1, libx11-6
Description: Miscellaneous Mesa GL utilities
 This package provides several basic GL utilities built by Mesa, including
 glxinfo and glxgears.
Homepage: http://mesa3d.sourceforge.net/

Package: mesa-common-dev
  Version: 9.2.0~git20130701.acc6a141-0ubuntu0sarvatt

Package: xserver-xorg-core
  **[COLOR="#FF0000"]Installed: 2:1.14.2+git20130705+server-1.14-branch.2767d9a1-0ubuntu0ricotz[/COLOR]**

Package: xserver-common
  **[COLOR="#FF0000"]Installed: 2:1.14.2+git20130705+server-1.14-branch.2767d9a1-0ubuntu0ricotz[/COLOR]**

Package: xserver-xephyr
  **[COLOR="#FF0000"]Installed: 2:1.14.2+git20130705+server-1.14-branch.2767d9a1-0ubuntu0ricotz[/COLOR]**

Tree Map of PCI Devices:
-[0000:00]-+-00.0  Intel Corporation 82875P/E7210 Memory Controller Hub
           +-01.0-[01]----00.0  NVIDIA Corporation G73 [GeForce 7600 GT]
           +-06.0  Intel Corporation 82875P/E7210 Processor to I/O Memory Interface
           +-1d.0  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
           +-1d.1  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
           +-1d.2  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3
           +-1d.3  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
           +-1d.7  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
           +-1e.0-[02]----0c.0  Lite-On Communications Inc LNE100TX
           +-1f.0  Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
           +-1f.2  Intel Corporation 82801EB (ICH5) SATA Controller
           +-1f.3  Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller
           \-1f.5  Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller

Display Properties:
 lcd monitor:    Dell UltraSharp 1907FP (analog input)
  dimensions:    1280x1024 pixels (339x271 millimeters)
  resolution:    96x96 dots per inch

vindsl@Zuul:~$ 
```

---

### Post by Harry33 on 2013-07-09
> **zika said:**
> Here at my place:```
The following packages will be REMOVED:
  activity-log-manager-common audacious xserver-xorg-input-all
  xserver-xorg-input-synaptics xserver-xorg-video-all xserver-xorg-video-ati
  xserver-xorg-video-cirrus xserver-xorg-video-mach64 xserver-xorg-video-r128
The following NEW packages will be installed:
  libgc1c2
The following packages have been kept back:
  libmirserver0 unity-system-compositor usb-modeswitch-data
The following packages will be upgraded:
  activity-log-manager apparmor compiz compiz-core compiz-gnome compiz-plugins
  compiz-plugins-default compizconfig-settings-manager gir1.2-gudev-1.0
  guile-2.0-libs krb5-locales libapparmor-perl libapparmor1 libaudclient2
  libaudcore1 libcompizconfig0 libdecoration0 libexpat1 libgssapi-krb5-2
  libgudev-1.0-0 libjs-jquery libk5crypto3 libkrb5-3 libkrb5support0
  libpam-systemd libqt4-dbus libqt4-declarative libqt4-designer libqt4-help
  libqt4-network libqt4-opengl libqt4-script libqt4-scripttools libqt4-sql
  libqt4-sql-sqlite libqt4-svg libqt4-test libqt4-xml libqt4-xmlpatterns
  libqt5core5 libqt5dbus5 libqt5gui5 libqt5network5 libqt5opengl5
  libqt5printsupport5 libqt5sql5 libqt5sql5-sqlite libqt5test5 libqt5widgets5
  libqt5xml5 libqtcore4 libqtgui4 libsystemd-daemon0 libsystemd-journal0
  libsystemd-login0 libudev1 libunity-core-6.0-7 libxfixes3 libxi6
  python-compizconfig qdbus systemd-services ucf udev unity unity-common
  unity-services xserver-xorg-core xserver-xorg-input-evdev
  xserver-xorg-input-mouse xserver-xorg-input-vmmouse xserver-xorg-input-wacom
  xserver-xorg-video-fbdev xserver-xorg-video-intel xserver-xorg-video-mga
  xserver-xorg-video-modesetting xserver-xorg-video-neomagic
  xserver-xorg-video-nouveau xserver-xorg-video-openchrome
  xserver-xorg-video-qxl xserver-xorg-video-radeon xserver-xorg-video-s3
  xserver-xorg-video-savage xserver-xorg-video-siliconmotion
  xserver-xorg-video-sis xserver-xorg-video-sisusb xserver-xorg-video-tdfx
  xserver-xorg-video-trident xserver-xorg-video-vesa xserver-xorg-video-vmware
```with „proposed“ enabled...
Still waiting for *-all packages to be build right... It is improving... Nevertheless, I do have almost everything already from Ricotz at right version... ;)

Just remove these stupid harmfull meta packages:
- xserver-xorg-input-all
- xserver-xorg-video-all

Look at the amount of different input and video drivers you have installed.
Then, see which of them you actually need or even "can" make use of (nouveau, tdfx, siliconmotion, s3, openchrome, neomagic, mga and on and on). Remove them.
I have "proposed" enabled, fully updated setup, and I have absulutely no issues with xserver 1.14.1 ATM).

---

### Post by zika on 2013-07-09
> **Harry33 said:**
> Just remove these stupid harmfull meta packages:
- xserver-xorg-input-all
- xserver-xorg-video-all

Look at the amount of different input and video drivers you have installed.
Then, see which of them you actually need or even "can" make use of (nouveau, tdfx, siliconmotion, s3, openchrome, neomagic, mga and on and on). Remove them.
I have "proposed" enabled, fully updated setup, and I have absulutely no issues with xserver 1.14.1 ATM).Actually I did not install any of drivers You see and complain about... That is what is automatically installed... In earlier days I was cleaning system from them, but now I've learned that it is a small gain for all the pain... ;)
If You look closer You'll see that there are couple of packages that should not be removed without seriuos thought. Also, there are some packages that are suggester but do not exist (anymore) in Ubuntu universe... ;)
Never mind, I think it will be sorted today...
As I said I do have almost all drivers that I need already at versions that I wish... I'm just waiting for xserver-xorg-core...
```
:~$ sudo apt-get install --reinstall -s xserver-xorg-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libunity-core-6.0-7 libxfixes3 libxi6 unity unity-common unity-services
  xserver-xorg-input-evdev xserver-xorg-input-mouse xserver-xorg-input-vmmouse
  xserver-xorg-input-wacom xserver-xorg-video-fbdev xserver-xorg-video-intel
  xserver-xorg-video-mga xserver-xorg-video-modesetting
  xserver-xorg-video-neomagic xserver-xorg-video-nouveau
  xserver-xorg-video-openchrome xserver-xorg-video-qxl
  xserver-xorg-video-radeon xserver-xorg-video-s3 xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident
  xserver-xorg-video-vesa xserver-xorg-video-vmware
Suggested packages:
  xfonts-100dpi xfonts-75dpi firmware-linux
Recommended packages:
  indicator-bluetooth
The following packages will be REMOVED:
  xserver-xorg-input-all xserver-xorg-input-synaptics xserver-xorg-video-all
  xserver-xorg-video-ati xserver-xorg-video-cirrus xserver-xorg-video-mach64
  xserver-xorg-video-r128
The following packages will be upgraded:
  libunity-core-6.0-7 libxfixes3 libxi6 unity unity-common unity-services
  xserver-xorg-core xserver-xorg-input-evdev xserver-xorg-input-mouse
  xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-fbdev
  xserver-xorg-video-intel xserver-xorg-video-mga
  xserver-xorg-video-modesetting xserver-xorg-video-neomagic
  xserver-xorg-video-nouveau xserver-xorg-video-openchrome
  xserver-xorg-video-qxl xserver-xorg-video-radeon xserver-xorg-video-s3
  xserver-xorg-video-savage xserver-xorg-video-siliconmotion
  xserver-xorg-video-sis xserver-xorg-video-sisusb xserver-xorg-video-tdfx
  xserver-xorg-video-trident xserver-xorg-video-vesa xserver-xorg-video-vmware
29 upgraded, 0 newly installed, 7 to remove and 3 not upgraded.
```

---

### Post by Harry33 on 2013-07-09
> **zika said:**
> Actually I did not install any of drivers You see and complain about... That is what is automatically installed... In earlier days I was cleaning system from them, but now I've learned that it is a small gain for all the pain... ;)
If You look closer You'll see that there are couple of packages that should not be removed without seriuos thought. Also, there are some packages that are suggester but do not exist (anymore) in Ubuntu universe... ;)
Never mind, I think it will be sorted today...
As I said I do have almost all drivers that I need already at versions that I wish... I'm just waiting for xserver-xorg-core...
```
:~$ sudo apt-get install --reinstall -s xserver-xorg-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libunity-core-6.0-7 libxfixes3 libxi6 unity unity-common unity-services
  xserver-xorg-input-evdev xserver-xorg-input-mouse xserver-xorg-input-vmmouse
  xserver-xorg-input-wacom xserver-xorg-video-fbdev xserver-xorg-video-intel
  xserver-xorg-video-mga xserver-xorg-video-modesetting
  xserver-xorg-video-neomagic xserver-xorg-video-nouveau
  xserver-xorg-video-openchrome xserver-xorg-video-qxl
  xserver-xorg-video-radeon xserver-xorg-video-s3 xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident
  xserver-xorg-video-vesa xserver-xorg-video-vmware
Suggested packages:
  xfonts-100dpi xfonts-75dpi firmware-linux
Recommended packages:
  indicator-bluetooth
The following packages will be REMOVED:
  xserver-xorg-input-all xserver-xorg-input-synaptics xserver-xorg-video-all
  xserver-xorg-video-ati xserver-xorg-video-cirrus xserver-xorg-video-mach64
  xserver-xorg-video-r128
The following packages will be upgraded:
  libunity-core-6.0-7 libxfixes3 libxi6 unity unity-common unity-services
  xserver-xorg-core xserver-xorg-input-evdev xserver-xorg-input-mouse
  xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-fbdev
  xserver-xorg-video-intel xserver-xorg-video-mga
  xserver-xorg-video-modesetting xserver-xorg-video-neomagic
  xserver-xorg-video-nouveau xserver-xorg-video-openchrome
  xserver-xorg-video-qxl xserver-xorg-video-radeon xserver-xorg-video-s3
  xserver-xorg-video-savage xserver-xorg-video-siliconmotion
  xserver-xorg-video-sis xserver-xorg-video-sisusb xserver-xorg-video-tdfx
  xserver-xorg-video-trident xserver-xorg-video-vesa xserver-xorg-video-vmware
29 upgraded, 0 newly installed, 7 to remove and 3 not upgraded.
```

Which version of xserver-xorg-core are you installing?
If it is the official 1.14.1 from saucy repos, you have some issues with your setup.
That one shoud not create your issue.

---

### Post by zika on 2013-07-09
No &#8222;issue&#8220; at my place... Just waiting for dozen of PPAs to consolidate and cohabitate...
As far as I can see, it is (almost) the same without them... I'll try to get a hold (ssh) of a machine that has vanilla SS to check... If time permits...

---

### Post by slickymaster on 2013-07-09
I've got it with today's updates.```
~$ Xorg -version

X.Org X Server 1.14.1
Release Date: 2013-04-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 3.2.0-37-generic i686 Ubuntu
Current Operating System: Linux IMT-VirtualBox 3.10.0-031000rc5-generic #201306082135 SMP Sun Jun 9 01:42:44 UTC 2013 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.10.0-031000rc5-generic root=UUID=a27a7e47-4ba6-48ae-bb0e-3b18f7c6ab1f ro quiet splash vt.handoff=7
Build Date: 04 July 2013  10:10:47AM
xorg-server 2:1.14.1-0ubuntu0.8 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.28.2
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
```

---

### Post by zika on 2013-07-09
Had some spare time on my keyboard...
Done careful manual dist-upgrade and after that reinstalled all removed packages without any problem...
So, I'm in completely, without any scars... At least those that I could see...
```
:~$ Xorg -version

X.Org X Server 1.14.2
Release Date: 2013-06-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-32-xen x86_64 Ubuntu
Current Operating System: Linux .... 3.10.0-996-generic #201307090409 SMP Tue Jul 9 08:10:38 UTC 2013 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.10.0-996-generic root=UUID=... ro radeon.audio=0 radeon.dpm=1 quiet splash
Build Date: 05 July 2013  01:22:00PM
xorg-server 2:1.14.2+git20130705+server-1.14-branch.2767d9a1-0ubuntu0ricotz (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.28.2
```

---

### Post by slickymaster on 2013-07-09
> **zika said:**
> Had some spare time on my keyboard...
Done careful manual dist-upgrade and after that reinstalled all removed packages without any problem...
So, I'm in completely, without any scars... At least those that I could see...
```
:~$ Xorg -version

X.Org X Server 1.14.2
Release Date: 2013-06-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-32-xen x86_64 Ubuntu
Current Operating System: Linux .... 3.10.0-996-generic #201307090409 SMP Tue Jul 9 08:10:38 UTC 2013 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.10.0-996-generic root=UUID=... ro radeon.audio=0 radeon.dpm=1 quiet splash
Build Date: 05 July 2013  01:22:00PM
xorg-server 2:1.14.2+git20130705+server-1.14-branch.2767d9a1-0ubuntu0ricotz (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.28.2
```

You're way ahead of me :)

Got try to find same spare time, today, to catch up.

---

### Post by zika on 2013-07-09
> **slickymaster said:**
> You're way ahead of me :)

Got try to find same spare time, today, to catch up.No package from „proposed“ was used during this experiment... ;)
I do not need time to do this, I needed time in case it went south... ;)

---

### Post by slickymaster on 2013-07-09
> **zika said:**
> No package from „proposed“ was used during this experiment... ;)
Yeah, I only went with the proposed ones.
> **zika said:**
> I do not need time to do this, I needed time in case it went south... ;)
That's what I was referring, when I mentioned the need of time. When testing, things tend to go south. But that's were we get the fun ;)

---

### Post by VinDSL on 2013-07-09
I dunno... Maybe I just got lucky.

I couldn't get anywhere with 1.14.1 on this legacy machine, soooo...

I installed (edgers) xserver-xephyr 1.14.2 & xserver-common 1.14.2, and waited patiently for xserver-xorg-core 1.14.2 to be fully cooked (it was being held back, after the partial upgrade).

Yesterday, one or more of the dependencies that xserver-xorg-core 1.14.2 was waiting for was fulfilled. 

Of note...

```
Commit Log for Mon Jul  8 12:46:19 2013

Removed the following packages:
xserver-xorg-input-mouse
xserver-xorg-video-vesa
```

I *thought* this was rather odd.

Just saying...

---

### Post by zika on 2013-07-09
> **slickymaster said:**
> Yeah, I only went with the proposed ones.
Vive la différence
> **slickymaster said:**
>  That's what I was referring, when I mentioned the need of time. When testing, things tend to go south. But that's were we get the fun ;)Apart from the fun of being on the edge I find even greater fun in escaping southbound trips...

---

### Post by zika on 2013-07-09
> **VinDSL said:**
> I dunno... Maybe I just got lucky.
I couldn't get anywhere with 1.14.1 on this legacy machine, soooo...
I installed (edgers) xserver-xephyr 1.14.2 & xserver-common 1.14.2, and waited patiently for xserver-xorg-core 1.14.2 to be fully cooked (it was being held back, after the partial upgrade).
Yesterday, one or more of the dependencies that xserver-xorg-core 1.14.2 was waiting for was fulfilled. 
Of note...
```
Commit Log for Mon Jul  8 12:46:19 2013
Removed the following packages:
xserver-xorg-input-mouse
xserver-xorg-video-vesa
```
I *thought* this was rather odd.
Just saying...
Did You try to re-install these two packages?

---

### Post by VinDSL on 2013-07-09
> **zika said:**
> Did You try to re-install these two packages?
No.  Everything seems to be running fine without them...

```
vindsl@Zuul:~$ apt-cache policy xserver-xorg-input-mouse
xserver-xorg-input-mouse:
  Installed: (none)
  Candidate: 1:1.7.2-3build1
  Version table:
     1:1.7.2-3build1 0
        500 http://archive.ubuntu.com/ubuntu/ saucy/main i386 Packages
vindsl@Zuul:~$ apt-cache policy xserver-xorg-video-vesa
xserver-xorg-video-vesa:
  Installed: (none)
  Candidate: 1:2.3.2-0ubuntu3
  Version table:
     1:2.3.2-0ubuntu3 0
        500 http://archive.ubuntu.com/ubuntu/ saucy/main i386 Packages
vindsl@Zuul:~$
```

---

### Post by zika on 2013-07-09
> **VinDSL said:**
> No.  Everything seems to be running fine without them...My mistake, I thought You need them...

---

### Post by VinDSL on 2013-07-09
> **zika said:**
> My mistake, I thought You need them...
I thought so, too.

Weird, eh?

Here's something even weirder...

I've **always** had a problem with my mouse pointer jumping around the screen, for no apparent reason.  For instance, I'll just be sitting here, reading a page, and the pointer will jump to the bottom, or top-left corner of the screen... whenever, wherever.  It's like some poltergeist moves it on me.

It doesn't *seem* to be doing that now.

I'll keep an eye on it, and see if it's my imagination, or it's been fixed.

---

### Post by VinDSL on 2013-07-09
Hrm...

I was just checking the description of x11-xserver-utils, and it says:

> An X client is a program that interfaces with an X server (almost always via
the X libraries), and thus with some input and output hardware like a
graphics card, monitor, keyboard, **[COLOR="#FF0000"]and pointing device (such as a mouse)[/COLOR]**.

Perhaps, I've been inadvertently running two (or more) mouse drivers, all these years.  :confused:

BTW, here's the extent of my xserver stable...


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-9-jul-2013-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-9-jul-2013-1.png")[/INDENT]


Working a treat, on this old dog...  ;)

---

### Post by Harry33 on 2013-07-10
> **VinDSL said:**
> Hrm...

I was just checking the description of x11-xserver-utils, and it says:

An X client is a program that interfaces with an X server (almost always via
the X libraries), and thus with some input and output hardware like a
graphics card, monitor, keyboard, **[COLOR=#FF0000]and pointing device (such as a mouse)[/COLOR]**. 			 		

Perhaps, I've been inadvertently running two (or more) mouse drivers, all these years.  :confused:
...
Working a treat, on this old dog...  ;)

Xserver-utils interfaces with some hardware...
It does not mean it includes drivers.

However, xserver-xorg-input-mouse is generally not needed at all.
That is because the newer pointing device driver system, xserver-xorg-input-evdev, takes care of it.
So if you have both -mouse and -evdev packages installed, your setup will use -evdev, not -mouse package.

---

### Post by paul_in_london on 2013-07-17
With proposed updates and xorg-edgers enabled there wasn't much sign that I would be able to upgrade to X Server 1.14.2 any time soon without removing anything.

Note to self of packages removed/upgraded:

```
paul@lubuntu-64:~$ sudo aptitude full-upgrade
The following packages will be upgraded: 
  libxfixes3 libxi6 xserver-xorg-core xserver-xorg-input-evdev xserver-xorg-input-wacom xserver-xorg-video-ati xserver-xorg-video-intel xserver-xorg-video-mga 
  xserver-xorg-video-modesetting xserver-xorg-video-nouveau xserver-xorg-video-openchrome xserver-xorg-video-qxl xserver-xorg-video-radeon xserver-xorg-video-tdfx 
  xserver-xorg-video-vmware 
15 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 3,317 kB of archives. After unpacking 1,024 B will be used.
The following packages have unmet dependencies:
 xserver-xorg-video-siliconmotion : Depends: xorg-video-abi-13 which is a virtual package.
 xserver-xorg-video-sisusb : Depends: xorg-video-abi-13 which is a virtual package.
 xserver-xorg-video-savage : Depends: xorg-video-abi-13 which is a virtual package.
 xserver-xorg-video-neomagic : Depends: xorg-video-abi-13 which is a virtual package.
 xserver-xorg-input-synaptics : Depends: xorg-input-abi-18 which is a virtual package.
 xserver-xorg-input-mouse : Depends: xorg-input-abi-18 which is a virtual package.
 xserver-xorg-video-vesa : Depends: xorg-video-abi-13 which is a virtual package.
 xserver-xorg-video-cirrus : Depends: xorg-video-abi-13 which is a virtual package.
 xserver-xorg-video-mach64 : Depends: xorg-video-abi-13 which is a virtual package.
 xserver-xorg-video-fbdev : Depends: xorg-video-abi-13 which is a virtual package.
 xserver-xorg-video-trident : Depends: xorg-video-abi-13 which is a virtual package.
 xserver-xorg-input-vmmouse : Depends: xorg-input-abi-18 which is a virtual package.
 xserver-xorg-video-sis : Depends: xorg-video-abi-13 which is a virtual package.
 xserver-xorg-video-s3 : Depends: xorg-video-abi-13 which is a virtual package.
 xserver-xorg-video-r128 : Depends: xorg-video-abi-13 which is a virtual package.
The following actions will resolve these dependencies:

      Remove the following packages:    
1)      xserver-xorg-input-all          
2)      xserver-xorg-input-mouse        
3)      xserver-xorg-input-synaptics    
4)      xserver-xorg-input-vmmouse      
5)      xserver-xorg-video-all          
6)      xserver-xorg-video-ati          
7)      xserver-xorg-video-cirrus       
8)      xserver-xorg-video-fbdev        
9)      xserver-xorg-video-mach64       
10)     xserver-xorg-video-neomagic     
11)     xserver-xorg-video-r128         
12)     xserver-xorg-video-s3           
13)     xserver-xorg-video-savage       
14)     xserver-xorg-video-siliconmotion
15)     xserver-xorg-video-sis          
16)     xserver-xorg-video-sisusb       
17)     xserver-xorg-video-trident      
18)     xserver-xorg-video-vesa         



Accept this solution? [Y/n/q/?] q
Abandoning all efforts to resolve these dependencies.
Abort.
paul@lubuntu-64:~$ 
```

The only ones I cared about keeping were xserver-xorg-video-fbdev and xserver-xorg-video-vesa, but in theory I should be able to add them again at some point.

All still seems to be working ok. :)

---

### Post by VinDSL on 2013-07-17
I'm running 1.14.2...

```
vindsl@Zuul:~$ apt-cache policy xserver-xorg-core
xserver-xorg-core:
  Installed: 2:1.14.2+git20130717+server-1.14-branch.54b125d1-0ubuntu0ricotz
  Candidate: 2:1.14.2+git20130717+server-1.14-branch.54b125d1-0ubuntu0ricotz
  Version table:
 *** 2:1.14.2+git20130717+server-1.14-branch.54b125d1-0ubuntu0ricotz 0
        500 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ saucy/main i386 Packages
        100 /var/lib/dpkg/status
     2:1.14.2-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ saucy/main i386 Packages
vindsl@Zuul:~$ apt-cache policy xserver-xorg-video-fbdev
xserver-xorg-video-fbdev:
  Installed: 1:0.4.3-0ubuntu3
  Candidate: 1:0.4.3-0ubuntu3
  Version table:
 *** 1:0.4.3-0ubuntu3 0
        500 http://archive.ubuntu.com/ubuntu/ saucy/main i386 Packages
        100 /var/lib/dpkg/status
vindsl@Zuul:~$ apt-cache policy xserver-xorg-video-vesa
xserver-xorg-video-vesa:
  Installed: 1:2.3.2-0ubuntu3
  Candidate: 1:2.3.2-0ubuntu3
  Version table:
 *** 1:2.3.2-0ubuntu3 0
        500 http://archive.ubuntu.com/ubuntu/ saucy/main i386 Packages
        100 /var/lib/dpkg/status
vindsl@Zuul:~$ apt-cache policy xserver-xorg-video-nouveau
xserver-xorg-video-nouveau:
  Installed: 1:1.0.8+git20130710.8c1c5d4f-0ubuntu0sarvatt
  Candidate: 1:1.0.8+git20130710.8c1c5d4f-0ubuntu0sarvatt
  Version table:
 *** 1:1.0.8+git20130710.8c1c5d4f-0ubuntu0sarvatt 0
        500 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ saucy/main i386 Packages
        100 /var/lib/dpkg/status
     1:1.0.8-0ubuntu1.1 0
        500 http://archive.ubuntu.com/ubuntu/ saucy/main i386 Packages
vindsl@Zuul:~$ 

```

Yes, it removed the stuff you listed (above), but I simply reinstalled what I wanted. 

Seems to work fine with 1.14.2 ;)

---

### Post by paul_in_london on 2013-07-17
Hi Vin,

Yep, seems to be ok here too.

I owe you another post about the 3.11-rc1 kernel and the legacy nvidia drivers! I'll do that quickly now.

Cheers,

Paul

---

### Post by xeizo on 2013-07-19
Yesterdays updates killed X hard for me,  and various kernels worked so-so but eventually I got everything back up using yesterdays daily 3.11-kernel. Gnome-shell is smooth etc but I have the segfaulting Gimp issue...

---

### Post by slickymaster on 2013-07-19
> **VinDSL said:**
> I'm running 1.14.2...
...
Seems to work fine with 1.14.2 ;)

Same here, but I'm not with the Ricotz's PPAs. And also everything seems to be running smoothly
```
slickymaster@IMT:~$ apt-cache policy xserver-xorg-core
xserver-xorg-core:
  Installed: 2:1.14.2-0ubuntu1
  Candidate: 2:1.14.2-0ubuntu1
  Version table:
 *** 2:1.14.2-0ubuntu1 0
        500 http://pt.archive.ubuntu.com/ubuntu/ saucy/main i386 Packages
        100 /var/lib/dpkg/status
slickymaster@IMT:~$ apt-cache policy xserver-xorg-video-vesa
xserver-xorg-video-vesa:
  Installed: 1:2.3.2-0ubuntu3
  Candidate: 1:2.3.2-0ubuntu3
  Version table:
 *** 1:2.3.2-0ubuntu3 0
        500 http://pt.archive.ubuntu.com/ubuntu/ saucy/main i386 Packages
        100 /var/lib/dpkg/status
slickymaster@IMT:~$ apt-cache policy xserver-xorg-video-nouveau
xserver-xorg-video-nouveau:
  Installed: 1:1.0.8-0ubuntu1.1
  Candidate: 1:1.0.8-0ubuntu1.1
  Version table:
 *** 1:1.0.8-0ubuntu1.1 0
        500 http://pt.archive.ubuntu.com/ubuntu/ saucy/main i386 Packages
        100 /var/lib/dpkg/status

```

---

### Post by VinDSL on 2013-07-19
> **xeizo said:**
> Yesterdays updates killed X hard for me,  and various kernels worked so-so but eventually I got everything back up using yesterdays daily 3.11-kernel. Gnome-shell is smooth etc but I have the segfaulting Gimp issue...
I'm using 1.14.2 on 3.10 Final (nVidia 304.88 patched for 3.11) and have seg faulting issues with GiMP and PCManFM, across the board, e.g. all DEs (GNOME 3.9.4 Staging, GNOME Classic, LXDE/Openbox, et cetera).

Haven't been able to pin down the exact cause of the seg faulting.

Seems odd that GiMP and PCManFM are both doing it.  What in the world could they possibly have in common :confused:

Everything else seems to be working fine.

BTW, this seg faulting nonsense only started a couple of days ago, after incremental upgrade(s).

Tried multiple versions of both apps...

Weird!

---

### Post by VinDSL on 2013-07-19
Installed 3.11-rc1 (19-Jul-2013 daily) and no lock-ups, so far, knock_on_wood.

See if it holds...

---

