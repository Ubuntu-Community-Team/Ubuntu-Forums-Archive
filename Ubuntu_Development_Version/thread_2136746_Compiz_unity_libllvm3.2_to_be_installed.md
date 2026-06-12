---
title: "Compiz /unity: libllvm3.2 to be installed?"
date: 2013-04-18
forum: Ubuntu Development Version
---

### Post by ventrical on 2013-04-18
I was reading another message from a poster who had a borked update with compiz /unity. I just ran synaptic and noticed a bunch of compiz updates and the libllvm3.2 to be installed. This is giving me the willys .. ya kn w.. the hair standing up on the back of my head - kind of stuff. Does this have anything to do with llvmpipe? and if so .. why now .. so late in the cycle?

---

### Post by arpanaut on 2013-04-18
I don't know for sure if that package itself is responsible...
BUT I just ran today's (around noon ET) and now my desktop is totally borked.
That is I get to the desktop but nothing but background is there, none of the usual fixes seem to work.
This is on a very base install with no prop. drivers, AMD graphics.
In failsafe graphics I get no desktop background, only way out is REISUB.
At one point apport tried to send, but I doubt success.
Good Luck!

---

### Post by ventrical on 2013-04-18
> **arpanaut said:**
> I don't know for sure if that package itself is responsible...
BUT I just ran today's (around noon ET) and now my desktop is totally borked.
That is I get to the desktop but nothing but background is there, none of the usual fixes seem to work.
This is on a very base install with no prop. drivers, AMD graphics.
In failsafe graphics I get no desktop background, only way out is REISUB.
At one point apport tried to send, but I doubt success.
Good Luck!


 Ahhh .. boy oh boy .. I went ahead and installed those updates.... well.. that's why were here .. to test all of this .. ok . here goes re-boot.

---

### Post by ventrical on 2013-04-18
Appears that  the most recent set of updates has had no adverse effects here. All is well.

---

### Post by grahammechanical on 2013-04-18
Low-Level Virtual Machine (LLVM) run time library

[http://packages.ubuntu.com/raring/libllvm3.2](http://packages.ubuntu.com/raring/libllvm3.2)

Having said that I am at the moment running the update and it seems to be stuck at "ldconfig deferred processing now taking place." I just hope I am being impatient. It reminds me of a few weeks back when processing an updated kernel seemed to break Update Manager. I am using Synaptic, by the way.

Update.

No worries. I noticed that synaptic said, changes applied and when I ticked the box to close Synaptic when changes applied the utility closed. Time to take some more tablets I think. :) Getting paranoid.

Regards.

---

### Post by arpanaut on 2013-04-18
Yup, that's why I have multiple installs on multiple machines.
Here we go... The waiting begins, LOL

This cycle has been pretty uneventful for the most part.
So, this makes it interesting.
Funny how at the end of the cycle they seem to start throwing curveballs
 when a fastball down the middle would suffice.

---

### Post by ventrical on 2013-04-18
> **grahammechanical said:**
> Low-Level Virtual Machine (LLVM) run time library

[http://packages.ubuntu.com/raring/libllvm3.2](http://packages.ubuntu.com/raring/libllvm3.2)

Having said that I am at the moment running the update and it seems to be stuck at "ldconfig deferred processing now taking place." I just hope I am being impatient. It reminds me of a few weeks back when processing an updated kernel seemed to break Update Manager. I am using Synaptic, by the way.

Regards.

Good luck Graham.  Thanks for the description. The updates went well here.

```

Commit Log for Tue Apr 16 15:40:42 2013


Upgraded the following packages:
apparmor (2.8.0-0ubuntu10) to 2.8.0-0ubuntu11
apport (2.9.2-0ubuntu5) to 2.9.2-0ubuntu8
apport-gtk (2.9.2-0ubuntu5) to 2.9.2-0ubuntu8
apt (0.9.7.7ubuntu3) to 0.9.7.7ubuntu4
apt-transport-https (0.9.7.7ubuntu3) to 0.9.7.7ubuntu4
apt-utils (0.9.7.7ubuntu3) to 0.9.7.7ubuntu4
apturl (0.5.1ubuntu6) to 0.5.2ubuntu1
apturl-common (0.5.1ubuntu6) to 0.5.2ubuntu1
bind9-host (1:9.9.2.dfsg.P1-2ubuntu1) to 1:9.9.2.dfsg.P1-2ubuntu2
binutils (2.23.2-1ubuntu2) to 2.23.2-2ubuntu1
compiz (1:0.9.9~daily13.04.05-0ubuntu1) to 1:0.9.9~daily13.04.15-0ubuntu1
compiz-core (1:0.9.9~daily13.04.05-0ubuntu1) to 1:0.9.9~daily13.04.15-0ubuntu1
compiz-gnome (1:0.9.9~daily13.04.05-0ubuntu1) to 1:0.9.9~daily13.04.15-0ubuntu1
compiz-plugins (1:0.9.9~daily13.04.05-0ubuntu1) to 1:0.9.9~daily13.04.15-0ubuntu1
compiz-plugins-default (1:0.9.9~daily13.04.05-0ubuntu1) to 1:0.9.9~daily13.04.15-0ubuntu1
compiz-plugins-extra (1:0.9.9~daily13.04.05-0ubuntu1) to 1:0.9.9~daily13.04.15-0ubuntu1
compiz-plugins-main (1:0.9.9~daily13.04.05-0ubuntu1) to 1:0.9.9~daily13.04.15-0ubuntu1
compizconfig-settings-manager (1:0.9.9~daily13.04.05-0ubuntu1) to 1:0.9.9~daily13.04.15-0ubuntu1
cpp (4:4.7.2-1ubuntu8) to 4:4.7.3-1ubuntu9
cpp-4.7 (4.7.2-23ubuntu2) to 4.7.3-1ubuntu1
cups (1.6.2-1ubuntu3) to 1.6.2-1ubuntu5
cups-browsed (1.0.33-0ubuntu1) to 1.0.34-0ubuntu1
cups-bsd (1.6.2-1ubuntu3) to 1.6.2-1ubuntu5
cups-client (1.6.2-1ubuntu3) to 1.6.2-1ubuntu5
cups-common (1.6.2-1ubuntu3) to 1.6.2-1ubuntu5
cups-daemon (1.6.2-1ubuntu3) to 1.6.2-1ubuntu5
cups-filters (1.0.33-0ubuntu1) to 1.0.34-0ubuntu1
cups-ppdc (1.6.2-1ubuntu3) to 1.6.2-1ubuntu5
dnsutils (1:9.9.2.dfsg.P1-2ubuntu1) to 1:9.9.2.dfsg.P1-2ubuntu2
fonts-opensymbol (2:102.2+LibO4.0.1-0ubuntu2) to 2:102.2+LibO4.0.2-0ubuntu1
friends (0.1.3daily13.04.05-0ubuntu1) to 0.1.3daily13.04.10.1-0ubuntu1
friends-dispatcher (0.1.3daily13.04.05-0ubuntu1) to 0.1.3daily13.04.10.1-0ubuntu1
friends-facebook (0.1.3daily13.04.05-0ubuntu1) to 0.1.3daily13.04.10.1-0ubuntu1
friends-identica (0.1.3daily13.04.05-0ubuntu1) to 0.1.3daily13.04.10.1-0ubuntu1
friends-twitter (0.1.3daily13.04.05-0ubuntu1) to 0.1.3daily13.04.10.1-0ubuntu1
gcalctool (1:3.8.0-0ubuntu1) to 1:3.8.1-0ubuntu1
gcc (4:4.7.2-1ubuntu8) to 4:4.7.3-1ubuntu9
gcc-4.7 (4.7.2-23ubuntu2) to 4.7.3-1ubuntu1
gcc-4.7-base (4.7.2-23ubuntu2) to 4.7.3-1ubuntu1
gdb (7.5-0ubuntu4) to 7.6~20130408-0ubuntu1
gir1.2-appindicator3-0.1 (12.10.1daily13.03.13-0ubuntu1) to 12.10.1daily13.04.15-0ubuntu1
gir1.2-atk-1.0 (2.7.91-0ubuntu1) to 2.8.0-1
gir1.2-gtk-3.0 (3.6.4-0ubuntu6) to 3.6.4-0ubuntu7
gir1.2-gudev-1.0 (198-0ubuntu9) to 198-0ubuntu10
gir1.2-messagingmenu-1.0 (12.10.6daily13.02.13-0ubuntu1) to 12.10.6daily13.04.09-0ubuntu1
gir1.2-networkmanager-1.0 (0.9.8.0-0ubuntu2) to 0.9.8.0-0ubuntu4
gir1.2-rb-3.0 (2.98-0ubuntu3) to 2.98-0ubuntu5
gir1.2-totem-1.0 (3.6.3-0ubuntu4) to 3.6.3-0ubuntu6
glib-networking (2.35.9-1) to 2.36.1-0ubuntu1
glib-networking-common (2.35.9-1) to 2.36.1-0ubuntu1
glib-networking-services (2.35.9-1) to 2.36.1-0ubuntu1
gnome-calculator (1:3.8.0-0ubuntu1) to 1:3.8.1-0ubuntu1
gnome-control-center (1:3.6.3-0ubuntu18) to 1:3.6.3-0ubuntu24
gnome-control-center-data (1:3.6.3-0ubuntu18) to 1:3.6.3-0ubuntu24
gnome-control-center-unity (1.2daily13.04.01-0ubuntu1) to 1.2daily13.04.09-0ubuntu1
gnome-sudoku (1:3.8.0-0ubuntu1) to 1:3.8.1-0ubuntu2
grub-common (2.00-13ubuntu2) to 2.00-13ubuntu3
grub-pc (2.00-13ubuntu2) to 2.00-13ubuntu3
grub-pc-bin (2.00-13ubuntu2) to 2.00-13ubuntu3
grub2-common (2.00-13ubuntu2) to 2.00-13ubuntu3
gstreamer1.0-plugins-good (1.0.5-1ubuntu1) to 1.0.6-1ubuntu1
gstreamer1.0-pulseaudio (1.0.5-1ubuntu1) to 1.0.6-1ubuntu1
gvfs (1.16.0-1ubuntu4) to 1.16.1-0ubuntu1
gvfs-backends (1.16.0-1ubuntu4) to 1.16.1-0ubuntu1
gvfs-bin (1.16.0-1ubuntu4) to 1.16.1-0ubuntu1
gvfs-common (1.16.0-1ubuntu4) to 1.16.1-0ubuntu1
gvfs-daemons (1.16.0-1ubuntu4) to 1.16.1-0ubuntu1
gvfs-fuse (1.16.0-1ubuntu4) to 1.16.1-0ubuntu1
gvfs-libs (1.16.0-1ubuntu4) to 1.16.1-0ubuntu1
im-config (0.21ubuntu2) to 0.21ubuntu3
indicator-messages (12.10.6daily13.02.13-0ubuntu1) to 12.10.6daily13.04.09-0ubuntu1
indicator-sound (12.10.2daily13.03.07-0ubuntu1) to 12.10.2daily13.04.12-0ubuntu1
language-pack-en (1:13.04+20130328) to 1:13.04+20130411
language-pack-gnome-en (1:13.04+20130328) to 1:13.04+20130411
language-selector-common (0.108) to 0.109
language-selector-gnome (0.108) to 0.109
libappindicator1 (12.10.1daily13.03.13-0ubuntu1) to 12.10.1daily13.04.15-0ubuntu1
libappindicator3-1 (12.10.1daily13.03.13-0ubuntu1) to 12.10.1daily13.04.15-0ubuntu1
libapt-inst1.5 (0.9.7.7ubuntu3) to 0.9.7.7ubuntu4
libapt-pkg4.12 (0.9.7.7ubuntu3) to 0.9.7.7ubuntu4
libatk1.0-0 (2.7.91-0ubuntu1) to 2.8.0-1
libatk1.0-data (2.7.91-0ubuntu1) to 2.8.0-1
libbind9-90 (1:9.9.2.dfsg.P1-2ubuntu1) to 1:9.9.2.dfsg.P1-2ubuntu2
libcolumbus0-0 (0.4.0daily13.02.19-0ubuntu1) to 0.4.0daily13.04.16~13.04-0ubuntu1
libcolumbus0-0-common (0.4.0daily13.02.19-0ubuntu1) to 0.4.0daily13.04.16~13.04-0ubuntu1
libcompizconfig0 (1:0.9.9~daily13.04.05-0ubuntu1) to 1:0.9.9~daily13.04.15-0ubuntu1
libcups2 (1.6.2-1ubuntu3) to 1.6.2-1ubuntu5
libcupscgi1 (1.6.2-1ubuntu3) to 1.6.2-1ubuntu5
libcupsfilters1 (1.0.33-0ubuntu1) to 1.0.34-0ubuntu1
libcupsimage2 (1.6.2-1ubuntu3) to 1.6.2-1ubuntu5
libcupsmime1 (1.6.2-1ubuntu3) to 1.6.2-1ubuntu5
libcupsppdc1 (1.6.2-1ubuntu3) to 1.6.2-1ubuntu5
libcurl3 (7.29.0-1ubuntu2) to 7.29.0-1ubuntu3
libcurl3-gnutls (7.29.0-1ubuntu2) to 7.29.0-1ubuntu3
libdecoration0 (1:0.9.9~daily13.04.05-0ubuntu1) to 1:0.9.9~daily13.04.15-0ubuntu1
libdns95 (1:9.9.2.dfsg.P1-2ubuntu1) to 1:9.9.2.dfsg.P1-2ubuntu2
libfontembed1 (1.0.33-0ubuntu1) to 1.0.34-0ubuntu1
libgail-3-0 (3.6.4-0ubuntu6) to 3.6.4-0ubuntu7
libgcc-4.7-dev (4.7.2-23ubuntu2) to 4.7.3-1ubuntu1
libgcc1 (1:4.7.2-23ubuntu2) to 1:4.7.3-1ubuntu1
libglib2.0-0 (2.36.0-1ubuntu1) to 2.36.0-1ubuntu2
libglib2.0-bin (2.36.0-1ubuntu1) to 2.36.0-1ubuntu2
libglib2.0-data (2.36.0-1ubuntu1) to 2.36.0-1ubuntu2
libgnome-control-center1 (1:3.6.3-0ubuntu18) to 1:3.6.3-0ubuntu24
libgomp1 (4.7.2-23ubuntu2) to 4.7.3-1ubuntu1
libgstreamer-plugins-good1.0-0 (1.0.5-1ubuntu1) to 1.0.6-1ubuntu1
libgtk-3-0 (3.6.4-0ubuntu6) to 3.6.4-0ubuntu7
libgtk-3-bin (3.6.4-0ubuntu6) to 3.6.4-0ubuntu7
libgtk-3-common (3.6.4-0ubuntu6) to 3.6.4-0ubuntu7
libgudev-1.0-0 (1:198-0ubuntu9) to 1:198-0ubuntu10
libindicator3-7 (12.10.2daily13.02.25-0ubuntu1) to 12.10.2daily13.04.10-0ubuntu1
libindicator7 (12.10.2daily13.02.25-0ubuntu1) to 12.10.2daily13.04.10-0ubuntu1
libisc92 (1:9.9.2.dfsg.P1-2ubuntu1) to 1:9.9.2.dfsg.P1-2ubuntu2
libisccc90 (1:9.9.2.dfsg.P1-2ubuntu1) to 1:9.9.2.dfsg.P1-2ubuntu2
libisccfg90 (1:9.9.2.dfsg.P1-2ubuntu1) to 1:9.9.2.dfsg.P1-2ubuntu2
libitm1 (4.7.2-23ubuntu2) to 4.7.3-1ubuntu1
liblightdm-gobject-1-0 (1.5.3-0ubuntu1) to 1.6.0-0ubuntu2
liblwres90 (1:9.9.2.dfsg.P1-2ubuntu1) to 1:9.9.2.dfsg.P1-2ubuntu2
libmessaging-menu0 (12.10.6daily13.02.13-0ubuntu1) to 12.10.6daily13.04.09-0ubuntu1
libnautilus-extension1a (1:3.6.3-0ubuntu14) to 1:3.6.3-0ubuntu16
libnm-glib-vpn1 (0.9.8.0-0ubuntu2) to 0.9.8.0-0ubuntu4
libnm-glib4 (0.9.8.0-0ubuntu2) to 0.9.8.0-0ubuntu4
libnm-util2 (0.9.8.0-0ubuntu2) to 0.9.8.0-0ubuntu4
libnux-4.0-0 (4.0.0daily13.03.25-0ubuntu1) to 4.0.1daily13.04.15-0ubuntu1
libnux-4.0-common (4.0.0daily13.03.25-0ubuntu1) to 4.0.1daily13.04.15-0ubuntu1
libpci3 (1:3.1.9-6ubuntu2) to 1:3.1.9-6ubuntu3
libperl5.14 (5.14.2-20) to 5.14.2-21
libpython2.7 (2.7.4-1ubuntu1) to 2.7.4-1ubuntu4
libpython2.7-minimal (2.7.4-1ubuntu1) to 2.7.4-1ubuntu4
libpython2.7-stdlib (2.7.4-1ubuntu1) to 2.7.4-1ubuntu4
libpython3.3 (3.3.1-1ubuntu1) to 3.3.1-1ubuntu2
libpython3.3-minimal (3.3.1-1ubuntu1) to 3.3.1-1ubuntu2
libpython3.3-stdlib (3.3.1-1ubuntu1) to 3.3.1-1ubuntu2
libqtassistantclient4 (4.6.3-4) to 4.6.3-4ubuntu1
libquadmath0 (4.7.2-23ubuntu2) to 4.7.3-1ubuntu1
libreoffice-base-core (1:4.0.1-0ubuntu2) to 1:4.0.2-0ubuntu1
libreoffice-calc (1:4.0.1-0ubuntu2) to 1:4.0.2-0ubuntu1
libreoffice-common (1:4.0.1-0ubuntu2) to 1:4.0.2-0ubuntu1
libreoffice-core (1:4.0.1-0ubuntu2) to 1:4.0.2-0ubuntu1
libreoffice-draw (1:4.0.1-0ubuntu2) to 1:4.0.2-0ubuntu1
libreoffice-emailmerge (1:4.0.1-0ubuntu2) to 1:4.0.2-0ubuntu1
libreoffice-gnome (1:4.0.1-0ubuntu2) to 1:4.0.2-0ubuntu1
libreoffice-gtk (1:4.0.1-0ubuntu2) to 1:4.0.2-0ubuntu1
libreoffice-help-en-us (1:4.0.1-0ubuntu2) to 1:4.0.2-0ubuntu1
libreoffice-impress (1:4.0.1-0ubuntu2) to 1:4.0.2-0ubuntu1
libreoffice-math (1:4.0.1-0ubuntu2) to 1:4.0.2-0ubuntu1
libreoffice-ogltrans (1:4.0.1-0ubuntu2) to 1:4.0.2-0ubuntu1
libreoffice-pdfimport (1:4.0.1-0ubuntu2) to 1:4.0.2-0ubuntu1
libreoffice-presentation-minimizer (1.0.4+LibO4.0.1-0ubuntu2) to 1.0.4+LibO4.0.2-0ubuntu1
libreoffice-style-human (1:4.0.1-0ubuntu2) to 1:4.0.2-0ubuntu1
libreoffice-style-tango (1:4.0.1-0ubuntu2) to 1:4.0.2-0ubuntu1
libreoffice-writer (1:4.0.1-0ubuntu2) to 1:4.0.2-0ubuntu1
librhythmbox-core6 (2.98-0ubuntu3) to 2.98-0ubuntu5
libstdc++6 (4.7.2-23ubuntu2) to 4.7.3-1ubuntu1
libsystemd-daemon0 (198-0ubuntu9) to 198-0ubuntu10
libtotem0 (3.6.3-0ubuntu4) to 3.6.3-0ubuntu6
libudev1 (198-0ubuntu9) to 198-0ubuntu10
libufe-xidgetter0 (2.4.7bzr13.04.04-0ubuntu1) to 2.4.7bzr13.04.15-0ubuntu1
libunity-core-6.0-5 (7.0.0daily13.04.05.2-0ubuntu1) to 7.0.0daily13.04.15-0ubuntu1
light-themes (13.04daily13.03.13.1-0ubuntu1) to 13.04daily13.04.12-0ubuntu1
lightdm (1.5.3-0ubuntu1) to 1.6.0-0ubuntu2
linux-firmware (1.104) to 1.105
linux-headers-generic (3.8.0.16.31) to 3.8.0.18.34
linux-image-generic (3.8.0.16.31) to 3.8.0.18.34
linux-libc-dev (3.8.0-16.26) to 3.8.0-18.28
modemmanager (0.6.0.0.really-0ubuntu4) to 0.6.0.0.really-0ubuntu5
nautilus (1:3.6.3-0ubuntu14) to 1:3.6.3-0ubuntu16
nautilus-data (1:3.6.3-0ubuntu14) to 1:3.6.3-0ubuntu16
network-manager (0.9.8.0-0ubuntu2) to 0.9.8.0-0ubuntu4
nux-tools (4.0.0daily13.03.25-0ubuntu1) to 4.0.1daily13.04.15-0ubuntu1
nvidia-304-updates (304.84-0ubuntu2) to 304.88-0ubuntu2
nvidia-settings-304-updates (304.64-0ubuntu1) to 304.88-0ubuntu1
pciutils (1:3.1.9-6ubuntu2) to 1:3.1.9-6ubuntu3
perl (5.14.2-20) to 5.14.2-21
perl-base (5.14.2-20) to 5.14.2-21
perl-modules (5.14.2-20) to 5.14.2-21
printer-driver-splix (2.0.0+svn306-2ubuntu1) to 2.0.0+svn308-0ubuntu1
python-appindicator (12.10.1daily13.03.13-0ubuntu1) to 12.10.1daily13.04.15-0ubuntu1
python-compizconfig (1:0.9.9~daily13.04.05-0ubuntu1) to 1:0.9.9~daily13.04.15-0ubuntu1
python-cupshelpers (1.3.12+20130308-0ubuntu3) to 1.3.12+20130308-0ubuntu4
python-qt4 (4.10-0ubuntu2) to 4.10-0ubuntu3
python-qt4-dbus (4.10-0ubuntu2) to 4.10-0ubuntu3
python2.7 (2.7.4-1ubuntu1) to 2.7.4-1ubuntu4
python2.7-minimal (2.7.4-1ubuntu1) to 2.7.4-1ubuntu4
python3-apport (2.9.2-0ubuntu5) to 2.9.2-0ubuntu8
python3-distupgrade (1:0.192.6) to 1:0.192.8
python3-problem-report (2.9.2-0ubuntu5) to 2.9.2-0ubuntu8
python3-uno (1:4.0.1-0ubuntu2) to 1:4.0.2-0ubuntu1
python3.3 (3.3.1-1ubuntu1) to 3.3.1-1ubuntu2
python3.3-minimal (3.3.1-1ubuntu1) to 3.3.1-1ubuntu2
qtdeclarative5-friends-plugin (0.1.0bzr13.04.02-0ubuntu1) to 0.1.0bzr13.04.11-0ubuntu1
rhythmbox (2.98-0ubuntu3) to 2.98-0ubuntu5
rhythmbox-data (2.98-0ubuntu3) to 2.98-0ubuntu5
rhythmbox-mozilla (2.98-0ubuntu3) to 2.98-0ubuntu5
rhythmbox-plugin-cdrecorder (2.98-0ubuntu3) to 2.98-0ubuntu5
rhythmbox-plugin-magnatune (2.98-0ubuntu3) to 2.98-0ubuntu5
rhythmbox-plugin-zeitgeist (2.98-0ubuntu3) to 2.98-0ubuntu5
rhythmbox-plugins (2.98-0ubuntu3) to 2.98-0ubuntu5
sessioninstaller (0.20+bzr134-0ubuntu5) to 0.20+bzr134-0ubuntu6
software-center (5.6.0-0ubuntu1) to 5.6.0-0ubuntu2
system-config-printer-common (1.3.12+20130308-0ubuntu3) to 1.3.12+20130308-0ubuntu4
system-config-printer-gnome (1.3.12+20130308-0ubuntu3) to 1.3.12+20130308-0ubuntu4
system-config-printer-udev (1.3.12+20130308-0ubuntu3) to 1.3.12+20130308-0ubuntu4
systemd-services (198-0ubuntu9) to 198-0ubuntu10
totem (3.6.3-0ubuntu4) to 3.6.3-0ubuntu6
totem-common (3.6.3-0ubuntu4) to 3.6.3-0ubuntu6
totem-mozilla (3.6.3-0ubuntu4) to 3.6.3-0ubuntu6
totem-plugins (3.6.3-0ubuntu4) to 3.6.3-0ubuntu6
ubuntu-artwork (1:13.04daily13.03.13.1-0ubuntu1) to 1:13.04daily13.04.12-0ubuntu1
ubuntu-desktop (1.298) to 1.299
ubuntu-docs (12.10.3) to 13.04.1
ubuntu-minimal (1.298) to 1.299
ubuntu-mono (13.04daily13.03.13.1-0ubuntu1) to 13.04daily13.04.12-0ubuntu1
ubuntu-release-upgrader-core (1:0.192.6) to 1:0.192.8
ubuntu-release-upgrader-gtk (1:0.192.6) to 1:0.192.8
ubuntu-settings (12.10.7) to 12.10.8
ubuntu-standard (1.298) to 1.299
unity (7.0.0daily13.04.05.2-0ubuntu1) to 7.0.0daily13.04.15-0ubuntu1
unity-common (7.0.0daily13.04.05.2-0ubuntu1) to 7.0.0daily13.04.15-0ubuntu1
unity-lens-applications (6.10.0daily13.03.06-0ubuntu1) to 6.10.0daily13.04.15-0ubuntu1
unity-lens-files (7.0~daily13.02.28-0ubuntu1) to 7.0~daily13.04.15-0ubuntu1
unity-lens-friends (0.1.1bzr13.03.26-0ubuntu1) to 0.1.1bzr13.04.12-0ubuntu1
unity-lens-video (0.3.14daily13.03.04-0ubuntu1) to 0.3.14daily13.04.15-0ubuntu1
unity-scope-gdrive (0.8daily12.12.05-0ubuntu1) to 0.8daily13.04.15-0ubuntu1
unity-scope-video-remote (0.3.14daily13.03.04-0ubuntu1) to 0.3.14daily13.04.15-0ubuntu1
unity-services (7.0.0daily13.04.05.2-0ubuntu1) to 7.0.0daily13.04.15-0ubuntu1
uno-libs3 (4.0.1-0ubuntu2) to 4.0.2-0ubuntu1
update-notifier (0.132) to 0.133
update-notifier-common (0.132) to 0.133
ure (4.0.1-0ubuntu2) to 4.0.2-0ubuntu1
vino (3.6.2-0ubuntu3) to 3.6.2-0ubuntu4
xdiagnose (3.4.4) to 3.5
xserver-common (2:1.13.3-0ubuntu4) to 2:1.13.3-0ubuntu5
xserver-xorg-core (2:1.13.3-0ubuntu4) to 2:1.13.3-0ubuntu5
xserver-xorg-video-intel (2:2.21.5-0ubuntu1) to 2:2.21.6-0ubuntu3
xul-ext-unity (2.4.7bzr13.04.04-0ubuntu1) to 2.4.7bzr13.04.15-0ubuntu1

Installed the following packages:
liblangtag-common (0.4.0-6)
liblangtag1 (0.4.0-6)
linux-headers-3.8.0-18 (3.8.0-18.28)
linux-headers-3.8.0-18-generic (3.8.0-18.28)
linux-image-3.8.0-18-generic (3.8.0-18.28)
linux-image-extra-3.8.0-18-generic (3.8.0-18.28)
ubuntu-system-service (0.2.4)

```

edit:  But no libllvm3.2! ?

---

### Post by grahammechanical on 2013-04-18
> [COLOR=#000000]Funny how at the end of the cycle they seem to start throwing curveballs[/COLOR]

This is why I would be happy with Ubuntu having a 2 year release schedule (LTS) with a release date set not by a calendar but by the completion of development targets. No, interim. Just LTS and development branch.

---

### Post by arpanaut on 2013-04-18
> This is why I would be happy with Ubuntu having a 2 year release  schedule (LTS) with a release date set not by a calendar but by the  completion of development targets. No, interim. Just LTS and development  branch.                         

I have to agree, so with all this talk about "rolling", let's hope that is the direction development is heading.
It would probably help with the inexperienced  jumping in on the interim's and getting burned.

---

### Post by arpanaut on 2013-04-18
Well, I guess was just a matter of bad timing.
Just did an update && dist-upgrade and all is well, for now.

That was fun, got to work on my CLI chops.
:P

---

