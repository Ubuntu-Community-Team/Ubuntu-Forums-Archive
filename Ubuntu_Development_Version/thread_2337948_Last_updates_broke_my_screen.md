---
title: "Last updates broke my screen"
date: 2016-09-23
forum: Ubuntu Development Version
---

### Post by enricobe on 2016-09-23
Hi, 
yesterday I've launched a regular dist-updgrade on my 16.10 install. My notebook has a 1366*768 resolution and it alwyas worked fine with Ubuntu.

With yesterday updates I have a max of 1024*768 (or 800*600) 4:3 resolution. Can you please help me to find which package "broke my screen" ?

This is what I've upgraded:
```

Start-Date: 2016-09-22  20:57:41
Commandline: apt-get dist-upgrade
Requested-By: enrico (1000)
Install: 
linux-headers-4.8.0-14:amd64 (4.8.0-14.15, automatic)
linux-image-4.8.0-14-generic:amd64 (4.8.0-14.15, automatic)
linux-image-extra-4.8.0-14-generic:amd64 (4.8.0-14.15, automatic),
 linux-headers-4.8.0-14-generic:amd64 (4.8.0-14.15, automatic),
 libreadline7:amd64 (7.0-0ubuntu2, automatic)
 libappstream4:amd64 (0.10.1-1, automatic),
 libstemmer0d:amd64 (0+svn585-1, automatic)

Upgrade:
hunspell-en-gb:amd64 (1:5.2.1-1, 1:5.2.1-2)
 evince:amd64 (3.21.92-0ubuntu1, 3.22.0-0ubuntu1)
 init:amd64 (1.44, 1.45)
 hunspell-en-za:amd64 (1:5.2.1-1, 1:5.2.1-2)
 libnm-glib4:amd64 (1.2.2-0ubuntu8, 1.2.2-0ubuntu10)
 libfolks-eds25:amd64 (0.11.2-1build1, 0.11.2-1build3)
 bluez:amd64 (5.41-0ubuntu2 5.41-0ubuntu3)
 init-system-helpers:amd64 (1.44, 1.45)
 gnome-power-manager:amd64 (3.21.92-1ubuntu2, 3.22.0-1ubuntu1)
 gucharmap:amd64 (1:9.0.0-1, 1:9.0.1-1)
 ubuntu-keyring:amd64 (2016.09.01, 2016.09.19)
 libcups2:amd64 (2.2~rc1-4, 2.2.0-1)
 qtdeclarative5-ubuntu-contacts0.1:amd64 (0.2+16.10.20160913-0ubuntu1, 0.2+16.10.20160920-0ubuntu1)
 linux-headers-generic:amd64 (4.4.0.9136.37, 4.8.0.14.23)
 gnupg1-l10n:amd64 (1.4.20-7ubuntu1, 1.4.20-7ubuntu2)
 gedit:amd64 (3.21.90-2ubuntu1, 3.22.0-1ubuntu1)
 libqt5test5:amd64 (5.6.1+dfsg-3ubuntu4~6, 5.6.1+dfsg-3ubuntu5~1)
 xserver-xorg-video-amdgpu:amd64 (1.1.0-1, 1.1.2-1)
 hunspell-it:amd64 (1:5.2.1-1, 1:5.2.1-2)
 bc:amd64 (1.06.95-9build1, 1.06.95-9build2)
 dc:amd64 (1.06.95-9build1, 1.06.95-9build2)
 linux-libc-dev:amd64 (4.4.0-9136.55, 4.8.0-14.15)
 libevdocument3-4:amd64 (3.21.92-0ubuntu1, 3.22.0-0ubuntu1)
 pay-ui:amd64 (15.10+16.10.20160816.1-0ubuntu1, 15.10+16.10.20160825-0ubuntu1)
 libwacom-common:amd64 (0.19-1, 0.22-1)
 gnupg-agent:amd64 (2.1.15-1ubuntu2, 2.1.15-1ubuntu3)
 bluez-cups:amd64 (5.41-0ubuntu2, 5.41-0ubuntu3)
 gnome-system-monitor:amd64 (3.21.91-0ubuntu1, 3.22.0-1)
 gnupg-l10n:amd64 (2.1.15-1ubuntu2, 2.1.15-1ubuntu3)
 appstream:amd64 (0.9.8-4build1, 0.10.1-1)
 unity8-desktop-session-mir:amd64 (1.0.13+16.10.20160809-0ubuntu1, 1.0.13+16.10.20160919-0ubuntu1)
 baobab:amd64 (3.21.92-1ubuntu1, 3.22.0-1ubuntu1)
 unity8-desktop-session:amd64 (1.0.13+16.10.20160809-0ubuntu1, 1.0.13+16.10.20160919-0ubuntu1)
 libsystemd0:amd64 (231-6, 231-6git1)
 libsystemd0:i386 (231-6, 231-6git1)
 libpulsedsp:amd64 (1:9.0-2ubuntu1, 1:9.0-2ubuntu2)
 hyphen-en-gb:amd64 (1:5.2.1-1, 1:5.2.1-2)
 qml-module-qtsysteminfo:amd64 (5.0~git20141206~44f70d99-0ubuntu9~8, 5.0~git20141206~44f70d99-0ubuntu10~13)
 gir1.2-click-0.4:amd64 (0.4.44+16.10.20160811.1-0ubuntu1, 0.4.45.1+16.10.20160916-0ubuntu1)
 linux-image-generic:amd64 (4.4.0.9136.37, 4.8.0.14.23)
 gnupg1-curl:amd64 (1.4.20-7ubuntu1, 1.4.20-7ubuntu2)
 folks-common:amd64 (0.11.2-1build1, 0.11.2-1build3)
 libfcitx-gclient0:amd64 (1:4.2.9.1-2, 1:4.2.9.1-3)
 libparted2:amd64 (3.2-15, 3.2-15build1)
 pulseaudio:amd64 (1:9.0-2ubuntu1, 1:9.0-2ubuntu2)
 yelp:amd64 (3.21.3-1ubuntu1, 3.22.0-1ubuntu1)
 libyelp0:amd64 (3.21.3-1ubuntu1, 3.22.0-1ubuntu1)
 python2.7-minimal:amd64 (2.7.12-3, 2.7.12-3build1)
 libsqlite3-0:amd64 (3.14.1-1, 3.14.1-1build1)
 click:amd64 (0.4.44+16.10.20160811.1-0ubuntu1, 0.4.45.1+16.10.20160916-0ubuntu1)
 snap-confine:amd64 (1.0.40-0ubuntu1, 1.0.41-0ubuntu2)
 qtcontact5-galera:amd64 (0.1.2+16.10.20160908-0ubuntu1, 0.1.2+16.10.20160920-0ubuntu1)
 libqt5dbus5:amd64 (5.6.1+dfsg-3ubuntu4~6, 5.6.1+dfsg-3ubuntu5~1)
 libpython2.7:amd64 (2.7.12-3, 2.7.12-3build1)
 python2.7:amd64 (2.7.12-3, 2.7.12-3build1)
 libqt5sql5-sqlite:amd64 (5.6.1+dfsg-3ubuntu4~6, 5.6.1+dfsg-3ubuntu5~1)
 libpeas-1.0-0:amd64 (1.18.0-3, 1.20.0-1)
 ftp:amd64 (0.17-33, 0.17-33build1)
 libpython3.5:amd64 (3.5.2-4ubuntu2, 3.5.2-4ubuntu3)
 python3.5:amd64 (3.5.2-4ubuntu2, 3.5.2-4ubuntu3)
 gdb:amd64 (7.11.90.20160906-0ubuntu1, 7.11.90.20160917-0ubuntu2)
 libfolks25:amd64 (0.11.2-1build1, 0.11.2-1build3)
 libqt5widgets5:amd64 (5.6.1+dfsg-3ubuntu4~6, 5.6.1+dfsg-3ubuntu5~1)
 libnm-glib-vpn1:amd64 (1.2.2-0ubuntu8, 1.2.2-0ubuntu10)
 python3.5-minimal:amd64 (3.5.2-4ubuntu2, 3.5.2-4ubuntu3)
 gawk:amd64 (1:4.1.3+dfsg-0.1, 1:4.1.3+dfsg-0.1build1)
 udev:amd64 (231-6, 231-6git1)
 libwacom-bin:amd64 (0.19-1, 0.22-1)
 hyphen-it:amd64 (1:5.2.1-1, 1:5.2.1-2)
 cups-server-common:amd64 (2.2~rc1-4, 2.2.0-1)
 libnm0:amd64 (1.2.2-0ubuntu8, 1.2.2-0ubuntu10)
 address-book-updater:amd64 (0.1.2+16.10.20160908-0ubuntu1, 0.1.2+16.10.20160920-0ubuntu1)
 passwd:amd64 (1:4.2-3.1ubuntu6, 1:4.2-3.2ubuntu1)
 gnome-screenshot:amd64 (3.20.1-1ubuntu1, 3.22.0-1ubuntu1)
 readline-common:amd64 (6.3-8ubuntu2, 7.0-0ubuntu2)
 iio-sensor-proxy:amd64 (1.2-1, 1.3-1)
 cups-common:amd64 (2.2~rc1-4, 2.2.0-1)
 network-manager:amd64 (1.2.2-0ubuntu8, 1.2.2-0ubuntu10)
 unity-scope-click-departmentsdb:amd64 (0.1.1+16.10.20160808-0ubuntu1, 0.1.1+16.10.20160920.1-0ubuntu1)
 cheese:amd64 (3.21.3-0ubuntu1, 3.22.0-1ubuntu1)
 libudev1:amd64 (231-6, 231-6git1)
 libfluidsynth1:amd64 (1.1.6-3, 1.1.6-3build1)
 libqt5xml5:amd64 (5.6.1+dfsg-3ubuntu4~6, 5.6.1+dfsg-3ubuntu5~1)
 gnome-disk-utility:amd64 (3.21.91-1ubuntu1, 3.22.0-1ubuntu1)
 evolution-data-server-utouch:amd64 (0.1.2+16.10.20160908-0ubuntu1, 0.1.2+16.10.20160920-0ubuntu1)
 gnome-user-guide:amd64 (3.20.2-1, 3.22.0-1)
 libqt5printsupport5:amd64 (5.6.1+dfsg-3ubuntu4~6, 5.6.1+dfsg-3ubuntu5~1)
 dirmngr:amd64 (2.1.15-1ubuntu2, 2.1.15-1ubuntu3)
 libfcitx-config4:amd64 (1:4.2.9.1-2, 1:4.2.9.1-3)
 libnm-util2:amd64 (1.2.2-0ubuntu8, 1.2.2-0ubuntu10)
 python-cryptography:amd64 (1.5-1ubuntu1, 1.5-2)
 libqt5concurrent5:amd64 (5.6.1+dfsg-3ubuntu4~6, 5.6.1+dfsg-3ubuntu5~1)
 ubuntu-sdk-libs:amd64 (1.282, 1.284)
 sqlite3:amd64 (3.14.1-1, 3.14.1-1build1)
 gnome-font-viewer:amd64 (3.20.2-2, 3.22.0-1)
 qtdeclarative5-buteo-syncfw0.1:amd64 (0.1+15.10.20151008-0ubuntu1, 0.1+16.10.20160919-0ubuntu1)
 unity-scope-click:amd64 (0.1.1+16.10.20160808-0ubuntu1, 0.1.1+16.10.20160920.1-0ubuntu1)
 gnome-calculator:amd64 (1:3.21.92-1ubuntu1, 1:3.22.0-1ubuntu1)
 cups-filters:amd64 (1.11.1-0ubuntu1, 1.11.3-0ubuntu1)
 libqt5gui5:amd64 (5.6.1+dfsg-3ubuntu4~6, 5.6.1+dfsg-3ubuntu5~1)
 evince-common:amd64 (3.21.92-0ubuntu1, 3.22.0-0ubuntu1)
 libpeas-common:amd64 (1.18.0-3, 1.20.0-1)
 gir1.2-peas-1.0:amd64 (1.18.0-3, 1.20.0-1)
 python3-cryptography:amd64 (1.5-1ubuntu1, 1.5-2)
 libpulse0:amd64 (1:9.0-2ubuntu1, 1:9.0-2ubuntu2)
 cups-ppdc:amd64 (2.2~rc1-4, 2.2.0-1)
 libcupsmime1:amd64 (2.2~rc1-4, 2.2.0-1)
 libevview3-3:amd64 (3.21.92-0ubuntu1, 3.22.0-0ubuntu1)
 python3-click-package:amd64 (0.4.44+16.10.20160811.1-0ubuntu1, 0.4.45.1+16.10.20160916-0ubuntu1)
 address-book-service:amd64 (0.1.2+16.10.20160908-0ubuntu1, 0.1.2+16.10.20160920-0ubuntu1)
 sed:amd64 (4.2.2-7.1, 4.2.2-8)
 libgucharmap-2-90-7:amd64 (1:9.0.0-1, 1:9.0.1-1)
 libcupsfilters1:amd64 (1.11.1-0ubuntu1, 1.11.3-0ubuntu1)
 libpulse-mainloop-glib0:amd64 (1:9.0-2ubuntu1, 1:9.0-2ubuntu2)
 systemd-sysv:amd64 (231-6, 231-6git1)
 libjack-jackd2-0:amd64 (1.9.10+20150825git1ed50c92~dfsg-2ubuntu1, 1.9.10+20150825git1ed50c92~dfsg-2ubuntu2)
 printer-driver-gutenprint:amd64 (5.2.11-1, 5.2.11-1build1)
 zenity:amd64 (3.20.0-1, 3.22.0-1)
 gpgv:amd64 (2.1.15-1ubuntu2, 2.1.15-1ubuntu3)
 ubuntu-core-launcher:amd64 (1.0.40-0ubuntu1, 1.0.41-0ubuntu2)
 libpam-systemd:amd64 (231-6, 231-6git1)
 parted:amd64 (3.2-15, 3.2-15build1)
 gedit-common:amd64 (3.21.90-2ubuntu1, 3.22.0-1ubuntu1)
 liblua5.2-0:amd64 (5.2.4-1.1, 5.2.4-1.1build1)
 systemd:amd64 (231-6, 231-6git1)
 libqt5core5a:amd64 (5.6.1+dfsg-3ubuntu4~6, 5.6.1+dfsg-3ubuntu5~1)
 wpasupplicant:amd64 (2.4-0ubuntu7, 2.4-0ubuntu8)
 login:amd64 (1:4.2-3.1ubuntu6, 1:4.2-3.2ubuntu1)
 libfontembed1:amd64 (1.11.1-0ubuntu1, 1.11.3-0ubuntu1)
 address-book-app:amd64 (0.2+16.10.20160913-0ubuntu1, 0.2+16.10.20160920-0ubuntu1)
 libgutenprint2:amd64 (5.2.11-1, 5.2.11-1build1)
 xserver-xorg-video-ati:amd64 (1:7.7.0-1, 1:7.7.1-1)
 libfam0:amd64 (2.7.0-17.1, 2.7.0-17.2)
 libreadline6:amd64 (6.3-8ubuntu2, 6.3-8ubuntu8)
 libclick-0.4-0:amd64 (0.4.44+16.10.20160811.1-0ubuntu1, 0.4.45.1+16.10.20160916-0ubuntu1)
 libcheese-gtk25:amd64 (3.21.3-0ubuntu1, 3.22.0-1ubuntu1)
 cheese-common:amd64 (3.21.3-0ubuntu1, 3.22.0-1ubuntu1)
 bluez-obexd:amd64 (5.41-0ubuntu2, 5.41-0ubuntu3)
 gnupg1:amd64 (1.4.20-7ubuntu1, 1.4.20-7ubuntu2)
 gnupg2:amd64 (2.1.15-1ubuntu2, 2.1.15-1ubuntu3)
 cups-filters-core-drivers:amd64 (1.11.1-0ubuntu1, 1.11.3-0ubuntu1)
 libqt5opengl5:amd64 (5.6.1+dfsg-3ubuntu4~6, 5.6.1+dfsg-3ubuntu5~1)
 file-roller:amd64 (3.21.91-0ubuntu1, 3.22.0-1ubuntu1)
 xserver-xorg-video-radeon:amd64 (1:7.7.0-1, 1:7.7.1-1)
 libhunspell-1.4-0:amd64 (1.4.1-2, 1.4.1-2build1)
 upstart:amd64 (1.13.2-0ubuntu28, 1.13.2-0ubuntu31)
 libfcitx-utils0:amd64 (1:4.2.9.1-2, 1:4.2.9.1-3)
 libcupsppdc1:amd64 (2.2~rc1-4, 2.2.0-1)
 libnss-resolve:amd64 (231-6, 231-6git1)
 mythes-en-us:amd64 (1:5.2.1-1, 1:5.2.1-2)
 libpython2.7-minimal:amd64 (2.7.12-3, 2.7.12-3build1)
 libgnutls30:amd64 (3.5.3-4ubuntu1, 3.5.3-5ubuntu1)
 pulseaudio-module-bluetooth:amd64 (1:9.0-2ubuntu1, 1:9.0-2ubuntu2)
 libwacom2:amd64 (0.19-1, 0.22-1)
 libcheese8:amd64 (3.21.3-0ubuntu1, 3.22.0-1ubuntu1)
 gdbserver:amd64 (7.11.90.20160906-0ubuntu1, 7.11.90.20160917-0ubuntu2)
 cups-bsd:amd64 (2.2~rc1-4, 2.2.0-1)
 libpay2:amd64 (15.10+16.10.20160816.1-0ubuntu1, 15.10+16.10.20160825-0ubuntu1)
 aethercast-tools:amd64 (0.1+16.10.20160808-0ubuntu1, 0.1+16.10.20160808-0ubuntu3)
 qtdeclarative5-ubuntu-addressbook0.1:amd64 (0.2+16.10.20160913-0ubuntu1, 0.2+16.10.20160920-0ubuntu1)
 libpython3.5-stdlib:amd64 (3.5.2-4ubuntu2, 3.5.2-4ubuntu3)
 cups-core-drivers:amd64 (2.2~rc1-4, 2.2.0-1)
 cups-daemon:amd64 (2.2~rc1-4, 2.2.0-1)
 libqt5network5:amd64 (5.6.1+dfsg-3ubuntu4~6, 5.6.1+dfsg-3ubuntu5~1)
 gnupg:amd64 (2.1.15-1ubuntu2, 2.1.15-1ubuntu3)
 pay-service:amd64 (15.10+16.10.20160816.1-0ubuntu1, 15.10+16.10.20160825-0ubuntu1)
 libbluetooth3:amd64 (5.41-0ubuntu2, 5.41-0ubuntu3)
 libqt5systeminfo5:amd64 (5.0~git20141206~44f70d99-0ubuntu9~8, 5.0~git20141206~44f70d99-0ubuntu10~13)
 mythes-it:amd64 (1:5.2.1-1, 1:5.2.1-2)
 libcupsimage2:amd64 (2.2~rc1-4, 2.2.0-1)
 libpython2.7-stdlib:amd64 (2.7.12-3, 2.7.12-3build1)
 libpython3.5-minimal:amd64 (3.5.2-4ubuntu2, 3.5.2-4ubuntu3)
 cups:amd64 (2.2~rc1-4, 2.2.0-1)
 pulseaudio-utils:amd64 (1:9.0-2ubuntu1, 1:9.0-2ubuntu2)
 libcupscgi1:amd64 (2.2~rc1-4, 2.2.0-1)
 cups-client:amd64 (2.2~rc1-4, 2.2.0-1)
 linux-generic:amd64 (4.4.0.9136.37, 4.8.0.14.23)
 aethercast:amd64 (0.1+16.10.20160808-0ubuntu1, 0.1+16.10.20160808-0ubuntu3)
 zenity-common:amd64 (3.20.0-1, 3.22.0-1)
 libqt5sql5:amd64 (5.6.1+dfsg-3ubuntu4~6, 5.6.1+dfsg-3ubuntu5~1)
 cups-browsed:amd64 (1.11.1-0ubuntu1, 1.11.3-0ubuntu1)
 hunspell-en-au:amd64 (1:5.2.1-1, 1:5.2.1-2)
 hunspell-en-ca:amd64 (1:5.2.1-1, 1:5.2.1-2)
End-Date: 2016-09-22  21:06:30

```

I think it could be the " xserver-xorg-video-radeon:amd64 (1:7.7.0-1, 1:7.7.1-1)" package, but I'm not sure.

---

### Post by enricobe on 2016-09-23
I've tried to downgrade the xorg packages to previous version

xserver-xorg-video-radeon_7.7.0-1_amd64
xserver-xorg-video-amdgpu_1.1.0-1_amd64
xserver-xorg-video-ati_7.7.0-1_amd64

but nothing changed. I still have giant icons and less space on screen than a 7" tablet :(

I think I'll reinstall the whole system. I can't wait for new updates and I can't understand which package has "broken" my screen for report it

---

### Post by enricobe on 2016-09-25
I've tried with Kubuntu 16.10 and I got the same screen resolution. Now I'm running kubuntu 16.04 and works fine with all the updates. I think there is a new version of some package which "broke" my screen resolution.
Is there a simple way to see which version of the packages above I'm running on 16.04? If I find different versions I can report them...

P.S. Same problem with Fedora 25 Alpha

---

### Post by ventrical on 2016-09-26
What brand of notebook?

Regards..

---

### Post by enricobe on 2016-09-26
> **ventrical said:**
> What brand of notebook?

Regards..
Hi,
it's a toshiba.

[http://www.toshiba.it/discontinued-products/satellite-c855-2j5/](http://www.toshiba.it/discontinued-products/satellite-c855-2j5/)

Thank you for your (always) reply :)

---

### Post by ventrical on 2016-09-26
> **enricobe said:**
> I've tried to downgrade the xorg packages to previous version

xserver-xorg-video-radeon_7.7.0-1_amd64
xserver-xorg-video-amdgpu_1.1.0-1_amd64
xserver-xorg-video-ati_7.7.0-1_amd64

but nothing changed. I still have giant icons and less space on screen than a 7" tablet :(

I think I'll reinstall the whole system. I can't wait for new updates and I can't understand which package has "broken" my screen for report it

I think you have to get rid of all three of those. I have ati graphics on some boxes and it usually just installs a standard driver.. umm .. i think with nouveau..

Hey .. lemme get back and I'll fire up my ati box..

---

### Post by ventrical on 2016-09-26
Ok.. I have same pkgs as you but my box is running on llvm... so i am  updating now. It may be you might have to install with nomodeset ..ahh umm.. but there is not much support for ati cards anymore..

---

### Post by ventrical on 2016-09-26
...and this  

```

ventrical@ventrical-MS-7850:~$ inxi -Fxz
System:    Host: ventrical-MS-7850 Kernel: 4.4.0-9136-generic x86_64 (64 bit gcc: 5.4.1)
           Desktop: Unity 7.5.0 (Gtk 3.20.9-1ubuntu1) Distro: Ubuntu 16.10
Machine:   Mobo: ASUSTeK model: P5QL PRO v: Rev 1.xx
           BIOS: American Megatrends v: 1004 date: 07/01/2009
CPU:       Quad core Intel Core2 Quad Q6600 (-MCP-) cache: 4096 KB
           flags: (lm nx sse sse2 sse3 ssse3 vmx) bmips: 19151
           clock speeds: max: 2393 MHz 1: 2393 MHz 2: 2393 MHz 3: 2393 MHz
           4: 2393 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Cedar [Radeon HD 5000/6000/7350/8350 Series]
           bus-ID: 01:00.0
           Display Server: X.Org 1.18.4 drivers: ati,radeon (unloaded: fbdev,vesa)
           Resolution: 1440x900@59.89hz
           GLX Renderer: Gallium 0.4 on AMD CEDAR (DRM 2.43.0 / 4.4.0-9136-generic, LLVM 3.8.1)
           GLX Version: 3.0 Mesa 12.0.2 Direct Rendering: Yes
Audio:     Card-1 Advanced Micro Devices [AMD/ATI] Cedar HDMI Audio [Radeon HD 5400/6300 Series]
           driver: snd_hda_intel bus-ID: 01:00.1
           Card-2 Intel 82801JI (ICH10 Family) HD Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Sound: Advanced Linux Sound Architecture v: k4.4.0-9136-generic
Network:   Card: Qualcomm Atheros AR8121/AR8113/AR8114 Gigabit or Fast Ethernet
           driver: ATL1E port: ec00 bus-ID: 02:00.0
           IF: enp2s0 state: up speed: 100 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 120.0GB (10.8% used)
           ID-1: /dev/sda model: KINGSTON_SV300S3 size: 120.0GB temp: 26C
Partition: ID-1: / size: 52G used: 9.3G (19%) fs: ext4 dev: /dev/sda6
           ID-2: swap-1 size: 3.21GB used: 0.07GB (2%) fs: swap dev: /dev/sda5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 24.5C mobo: 32.0C gpu: 42.0
           Fan Speeds (in rpm): cpu: 4560 psu: 0 sys-1: 2518
Info:      Processes: 248 Uptime: 12 min Memory: 1156.3/1999.6MB
           Init: systemd runlevel: 5 Gcc sys: 6.2.0
           Client: Shell (bash 4.3.461) inxi: 2.3.1 
ventrical@ventrical-MS-7850:~$ 

```

what does your inxi report?

Regards..

---

### Post by ventrical on 2016-09-26
updated all pkgs ..working here

---

### Post by enricobe on 2016-10-02
> **ventrical said:**
> updated all pkgs ..working here

Hi, sorry for my big delay. 

I'm sorry but I really needed to have a working desktop so I'm now running Kubuntu 16.04. I'll try to download the lastest daily and see if it works. One week ago also the liveDVD wasn't working.

---

### Post by enricobe on 2016-10-31
I still have the same problem with 16.10 or 17.04....

I'm stuck on 16.04 LTS :|:|:|

---

### Post by cantastefano on 2016-10-31
I have a similar issue. The DPI scaling is stuck at 2x for the content of the windows, despite the rest of the UI being set at 1x.

---

### Post by enricobe on 2016-11-01
Do you have your normal display resolution? E.g. 1366*768 for a 15" laptop. 
Because my problem is the display resolution which is 1024*768 instead of 1366*768.

I have a Radeon 7610 but I don't use proprietary drivers

---

### Post by cantastefano on 2016-11-01
The laptop resolution is correct at 3200x1600. The scaling is wrong for the content of the windows, not for the decoration or the rest of the unity UI. Lightdm starts with the wrong scaling, too.
The background image is zoomed 2x, and so is the top unity bar in length.

---

