---
title: "Should I remove libsdl1.2debian-pulseaudio?"
date: 2011-12-06
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by zika on 2011-12-06
```
:~$ sudo aptitude dist-upgrade 
The following packages will be upgraded: 
  libsdl1.2debian{b} 
1 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 197 kB of archives. After unpacking 449 kB will be used.
The following packages have unmet dependencies:
  libsdl1.2debian: Conflicts: libsdl1.2debian-pulseaudio but 1.2.14-6.1ubuntu5 is installed.
The following actions will resolve these dependencies:

     Remove the following packages:
1)     libsdl1.2debian-pulseaudio  



Accept this solution? [Y/n/q/?] 
```

I looked into changelogs but...

---

### Post by kansasnoob on 2011-12-06
I just got done upgrading a Precise for the first time in days and here's what it did:

```
Commit Log for Tue Dec  6 02:18:52 2011


Removed the following packages:
libsdl1.2debian-pulseaudio

Upgraded the following packages:
alsa-utils (1.0.24.2-4ubuntu1) to 1.0.24.2-4ubuntu2
bluez (4.96-3ubuntu2) to 4.96-3ubuntu3
bluez-alsa (4.96-3ubuntu2) to 4.96-3ubuntu3
bluez-cups (4.96-3ubuntu2) to 4.96-3ubuntu3
bluez-gstreamer (4.96-3ubuntu2) to 4.96-3ubuntu3
compiz (1:0.9.6+bzr20110929-0ubuntu7) to 1:0.9.6+bzr20110929-0ubuntu8
compiz-core (1:0.9.6+bzr20110929-0ubuntu7) to 1:0.9.6+bzr20110929-0ubuntu8
compiz-gnome (1:0.9.6+bzr20110929-0ubuntu7) to 1:0.9.6+bzr20110929-0ubuntu8
compiz-plugins-default (1:0.9.6+bzr20110929-0ubuntu7) to 1:0.9.6+bzr20110929-0ubuntu8
cups (1.5.0-12) to 1.5.0-13build1
cups-bsd (1.5.0-12) to 1.5.0-13build1
cups-client (1.5.0-12) to 1.5.0-13build1
cups-common (1.5.0-12) to 1.5.0-13build1
cups-ppdc (1.5.0-12) to 1.5.0-13build1
dconf-gsettings-backend (0.10.0-2) to 0.10.0-3
dconf-service (0.10.0-2) to 0.10.0-3
dmsetup (2:1.02.48-4ubuntu5) to 2:1.02.48-4ubuntu7
dpkg (1.16.1.2ubuntu1) to 1.16.1.2ubuntu3
empathy (3.2.1.2-0ubuntu1) to 3.3.1-0ubuntu1
empathy-common (3.2.1.2-0ubuntu1) to 3.3.1-0ubuntu1
eog (3.2.2-2ubuntu1) to 3.2.2-2ubuntu2
evince (3.2.1-1ubuntu1) to 3.2.1-1ubuntu2
evince-common (3.2.1-1ubuntu1) to 3.2.1-1ubuntu2
firefox (9.0~b3+build1-0ubuntu1) to 9.0~b4+build1-0ubuntu2
firefox-globalmenu (9.0~b3+build1-0ubuntu1) to 9.0~b4+build1-0ubuntu2
firefox-gnome-support (9.0~b3+build1-0ubuntu1) to 9.0~b4+build1-0ubuntu2
firefox-locale-en (9.0~b3+build1-0ubuntu1) to 9.0~b4+build1-0ubuntu2
gcalctool (6.2.0-1ubuntu1) to 6.2.0-1ubuntu3
gdebi (0.8.2ubuntu1) to 0.8.3
gdebi-core (0.8.2ubuntu1) to 0.8.3
gettext-base (0.18.1.1-5ubuntu2) to 0.18.1.1-5ubuntu3
ghostscript (9.04~dfsg-2ubuntu3) to 9.04~dfsg-2ubuntu5
ghostscript-cups (9.04~dfsg-2ubuntu3) to 9.04~dfsg-2ubuntu5
ghostscript-x (9.04~dfsg-2ubuntu3) to 9.04~dfsg-2ubuntu5
gir1.2-appindicator3-0.1 (0.4.1-0ubuntu2) to 0.4.1-0ubuntu3
gir1.2-dbusmenu-glib-0.4 (0.5.1-0ubuntu1) to 0.5.1-0ubuntu2
gir1.2-dbusmenu-gtk-0.4 (0.5.1-0ubuntu1) to 0.5.1-0ubuntu2
gir1.2-gtk-2.0 (2.24.6-0ubuntu6) to 2.24.8-0ubuntu4
gir1.2-gtk-3.0 (3.2.2-2ubuntu1) to 3.2.2-2ubuntu3
gir1.2-rb-3.0 (2.90.1~20110908-0ubuntu1) to 2.90.1~20111126.89c872b0-0ubuntu1
gir1.2-soup-2.4 (2.36.1-1) to 2.36.1-1ubuntu1
gir1.2-totem-1.0 (3.0.1-0ubuntu10) to 3.0.1-0ubuntu11
gir1.2-vte-2.90 (1:0.28.2-0ubuntu3) to 1:0.28.2-0ubuntu4
glib-networking (2.30.1-2) to 2.30.1-3
glib-networking-common (2.30.1-2) to 2.30.1-3
glib-networking-services (2.30.1-2) to 2.30.1-3
gnome-games-common (1:3.2.1-0ubuntu1) to 1:3.2.1-0ubuntu2
gnome-mahjongg (1:3.2.1-0ubuntu1) to 1:3.2.1-0ubuntu2
gnome-nettool (3.0.0-0ubuntu2) to 3.0.0-0ubuntu3
gnome-orca (3.3.2-0ubuntu1) to 3.3.2-0ubuntu2
gnome-session (3.2.1-0ubuntu1) to 3.2.1-0ubuntu3
gnome-session-bin (3.2.1-0ubuntu1) to 3.2.1-0ubuntu3
gnome-session-canberra (0.28-0ubuntu11) to 0.28-0ubuntu12
gnome-session-common (3.2.1-0ubuntu1) to 3.2.1-0ubuntu3
gnome-session-fallback (3.2.1-0ubuntu1) to 3.2.1-0ubuntu3
gnome-settings-daemon (3.2.2-0ubuntu3) to 3.2.2-0ubuntu4
gnome-sudoku (1:3.2.1-0ubuntu1) to 1:3.2.1-0ubuntu2
gnome-system-monitor (3.2.1-1ubuntu1) to 3.2.1-1ubuntu2
gnomine (1:3.2.1-0ubuntu1) to 1:3.2.1-0ubuntu2
gstreamer0.10-alsa (0.10.35-1) to 0.10.35-1build1
gstreamer0.10-gnomevfs (0.10.35-1) to 0.10.35-1build1
gstreamer0.10-plugins-base (0.10.35-1) to 0.10.35-1build1
gstreamer0.10-plugins-base-apps (0.10.35-1) to 0.10.35-1build1
gstreamer0.10-x (0.10.35-1) to 0.10.35-1build1
gtk2-engines (1:2.20.2-0ubuntu2) to 1:2.20.2-1ubuntu1
gtk2-engines-pixbuf (2.24.6-0ubuntu6) to 2.24.8-0ubuntu4
indicator-sound (0.7.9.1-0ubuntu2) to 0.8.0.0-0ubuntu1
iproute (20110629-1) to 20111117-1
libappindicator0.1-cil (0.4.1-0ubuntu2) to 0.4.1-0ubuntu3
libappindicator1 (0.4.1-0ubuntu2) to 0.4.1-0ubuntu3
libappindicator3-1 (0.4.1-0ubuntu2) to 0.4.1-0ubuntu3
libatasmart4 (0.18-1) to 0.18-1ubuntu2
libavc1394-0 (0.5.3-1build4) to 0.5.3-1ubuntu1
libbluetooth3 (4.96-3ubuntu2) to 4.96-3ubuntu3
libburn4 (1.1.6-1) to 1.1.8-1
libc-bin (2.13-20ubuntu6) to 2.13-20ubuntu9
libc-dev-bin (2.13-20ubuntu6) to 2.13-20ubuntu9
libc6 (2.13-20ubuntu6) to 2.13-20ubuntu9
libc6-dev (2.13-20ubuntu6) to 2.13-20ubuntu9
libcaca0 (0.99.beta17-2.1) to 0.99.beta17-2.1ubuntu1
libcanberra-gtk-module (0.28-0ubuntu11) to 0.28-0ubuntu12
libcanberra-gtk0 (0.28-0ubuntu11) to 0.28-0ubuntu12
libcanberra-gtk3-0 (0.28-0ubuntu11) to 0.28-0ubuntu12
libcanberra-gtk3-module (0.28-0ubuntu11) to 0.28-0ubuntu12
libcanberra-pulse (0.28-0ubuntu11) to 0.28-0ubuntu12
libcanberra0 (0.28-0ubuntu11) to 0.28-0ubuntu12
libcdparanoia0 (3.10.2+debian-10) to 3.10.2+debian-10ubuntu1
libclass-isa-perl (0.36-2) to 0.36-3
libcups2 (1.5.0-12) to 1.5.0-13build1
libcupscgi1 (1.5.0-12) to 1.5.0-13build1
libcupsdriver1 (1.5.0-12) to 1.5.0-13build1
libcupsimage2 (1.5.0-12) to 1.5.0-13build1
libcupsmime1 (1.5.0-12) to 1.5.0-13build1
libcupsppdc1 (1.5.0-12) to 1.5.0-13build1
libdb5.1 (5.1.25-11) to 5.1.25-11build1
libdbusmenu-glib4 (0.5.1-0ubuntu1) to 0.5.1-0ubuntu2
libdbusmenu-gtk3-4 (0.5.1-0ubuntu1) to 0.5.1-0ubuntu2
libdbusmenu-gtk4 (0.5.1-0ubuntu1) to 0.5.1-0ubuntu2
libdconf-dbus-1-0 (0.10.0-2) to 0.10.0-3
libdconf0 (0.10.0-2) to 0.10.0-3
libdecoration0 (1:0.9.6+bzr20110929-0ubuntu7) to 1:0.9.6+bzr20110929-0ubuntu8
libdevmapper-event1.02.1 (2:1.02.48-4ubuntu5) to 2:1.02.48-4ubuntu7
libdevmapper1.02.1 (2:1.02.48-4ubuntu5) to 2:1.02.48-4ubuntu7
libdirectfb-1.2-9 (1.2.10.0-4ubuntu4) to 1.2.10.0-4.3ubuntu1
libdmapsharing-3.0-2 (2.9.12-1) to 2.9.13-1
libdv4 (1.0.0-3) to 1.0.0-3ubuntu1
libedit2 (2.11-20080614-3) to 2.11-20080614-3ubuntu1
libevince3-3 (3.2.1-1ubuntu1) to 3.2.1-1ubuntu2
libfftw3-3 (3.2.2-1ubuntu2) to 3.2.2-1ubuntu3
libgail-3-0 (3.2.2-2ubuntu1) to 3.2.2-2ubuntu3
libgail-common (2.24.6-0ubuntu6) to 2.24.8-0ubuntu4
libgail18 (2.24.6-0ubuntu6) to 2.24.8-0ubuntu4
libgksu2-0 (2.0.13~pre1-4ubuntu2) to 2.0.13~pre1-5ubuntu1
libglade2-0 (1:2.6.4-1build1) to 1:2.6.4-1ubuntu1
libglib-perl (2:1.240-1build2) to 2:1.241-1
libglibmm-2.4-1c2a (2.30.0-1) to 2.30.0-2
libgnomecanvas2-0 (2.30.3-1) to 2.30.3-1ubuntu1
libgnomecanvas2-common (2.30.3-1) to 2.30.3-1ubuntu1
libgs9 (9.04~dfsg-2ubuntu3) to 9.04~dfsg-2ubuntu5
libgs9-common (9.04~dfsg-2ubuntu3) to 9.04~dfsg-2ubuntu5
libgstfarsight0.10-0 (0.0.31-1ubuntu1) to 0.0.31-1ubuntu2
libgstreamer-plugins-base0.10-0 (0.10.35-1) to 0.10.35-1build1
libgtk-3-0 (3.2.2-2ubuntu1) to 3.2.2-2ubuntu3
libgtk-3-bin (3.2.2-2ubuntu1) to 3.2.2-2ubuntu3
libgtk-3-common (3.2.2-2ubuntu1) to 3.2.2-2ubuntu3
libgtk2.0-0 (2.24.6-0ubuntu6) to 2.24.8-0ubuntu4
libgtk2.0-bin (2.24.6-0ubuntu6) to 2.24.8-0ubuntu4
libgtk2.0-common (2.24.6-0ubuntu6) to 2.24.8-0ubuntu4
libgtkmm-3.0-1 (3.2.0-0ubuntu1) to 3.2.0-1
libicu48 (4.8.1.1-1) to 4.8.1.1-1ubuntu1
libiec61883-0 (1.2.0-0.1build1) to 1.2.0-0.1ubuntu1
libisofs6 (1.1.6-1) to 1.1.6-1ubuntu1
liblvm2app2.2 (2.02.66-4ubuntu5) to 2.02.66-4ubuntu7
libnautilus-extension1 (1:3.2.1-0ubuntu4) to 1:3.2.1-0ubuntu6
liborc-0.4-0 (1:0.4.16-1) to 1:0.4.16-1ubuntu2
libprotobuf7 (2.4.0a-2ubuntu2) to 2.4.1-1ubuntu2
libprotoc7 (2.4.0a-2ubuntu2) to 2.4.1-1ubuntu2
libproxy0 (0.3.1-2ubuntu6) to 0.3.1-4ubuntu2
libpulse-mainloop-glib0 (1:1.1-0ubuntu1) to 1:1.1-0ubuntu3
libpulse0 (1:1.1-0ubuntu1) to 1:1.1-0ubuntu3
libpulsedsp (1:1.1-0ubuntu1) to 1:1.1-0ubuntu3
libpython2.7 (2.7.2-8) to 2.7.2-8build1
libqt4-dbus (4:4.7.4-1ubuntu5) to 4:4.7.4-1ubuntu6
libqt4-declarative (4:4.7.4-1ubuntu5) to 4:4.7.4-1ubuntu6
libqt4-designer (4:4.7.4-1ubuntu5) to 4:4.7.4-1ubuntu6
libqt4-help (4:4.7.4-1ubuntu5) to 4:4.7.4-1ubuntu6
libqt4-network (4:4.7.4-1ubuntu5) to 4:4.7.4-1ubuntu6
libqt4-opengl (4:4.7.4-1ubuntu5) to 4:4.7.4-1ubuntu6
libqt4-script (4:4.7.4-1ubuntu5) to 4:4.7.4-1ubuntu6
libqt4-scripttools (4:4.7.4-1ubuntu5) to 4:4.7.4-1ubuntu6
libqt4-sql (4:4.7.4-1ubuntu5) to 4:4.7.4-1ubuntu6
libqt4-sql-mysql (4:4.7.4-1ubuntu5) to 4:4.7.4-1ubuntu6
libqt4-svg (4:4.7.4-1ubuntu5) to 4:4.7.4-1ubuntu6
libqt4-test (4:4.7.4-1ubuntu5) to 4:4.7.4-1ubuntu6
libqt4-xml (4:4.7.4-1ubuntu5) to 4:4.7.4-1ubuntu6
libqt4-xmlpatterns (4:4.7.4-1ubuntu5) to 4:4.7.4-1ubuntu6
libqtcore4 (4:4.7.4-1ubuntu5) to 4:4.7.4-1ubuntu6
libqtgui4 (4:4.7.4-1ubuntu5) to 4:4.7.4-1ubuntu6
librasqal3 (0.9.27-1) to 0.9.28-1
libreoffice-base-core (1:3.4.4-0ubuntu1) to 1:3.4.4-0ubuntu2
libreoffice-calc (1:3.4.4-0ubuntu1) to 1:3.4.4-0ubuntu2
libreoffice-common (1:3.4.4-0ubuntu1) to 1:3.4.4-0ubuntu2
libreoffice-core (1:3.4.4-0ubuntu1) to 1:3.4.4-0ubuntu2
libreoffice-draw (1:3.4.4-0ubuntu1) to 1:3.4.4-0ubuntu2
libreoffice-emailmerge (1:3.4.4-0ubuntu1) to 1:3.4.4-0ubuntu2
libreoffice-gnome (1:3.4.4-0ubuntu1) to 1:3.4.4-0ubuntu2
libreoffice-gtk (1:3.4.4-0ubuntu1) to 1:3.4.4-0ubuntu2
libreoffice-help-en-us (1:3.4.4-0ubuntu1) to 1:3.4.4-0ubuntu2
libreoffice-impress (1:3.4.4-0ubuntu1) to 1:3.4.4-0ubuntu2
libreoffice-math (1:3.4.4-0ubuntu1) to 1:3.4.4-0ubuntu2
libreoffice-style-human (1:3.4.4-0ubuntu1) to 1:3.4.4-0ubuntu2
libreoffice-writer (1:3.4.4-0ubuntu1) to 1:3.4.4-0ubuntu2
librest-0.7-0 (0.7.10-1) to 0.7.12-1ubuntu1
librhythmbox-core4 (2.90.1~20110908-0ubuntu1) to 2.90.1~20111126.89c872b0-0ubuntu1
libsane (1.0.22-2ubuntu2) to 1.0.22-7ubuntu1
libsdl1.2debian (1.2.14-6.1ubuntu4) to 1.2.14-6.4ubuntu1
libselinux1 (2.1.0-4) to 2.1.0-4ubuntu1
libshout3 (2.2.2-5ubuntu3) to 2.2.2-5ubuntu4
libsoundtouch0 (1.6.0-2) to 1.6.0-2build1
libsoup-gnome2.4-1 (2.36.1-1) to 2.36.1-1ubuntu1
libsoup2.4-1 (2.36.1-1) to 2.36.1-1ubuntu1
libspeechd2 (0.7.1-6ubuntu1) to 0.7.1-6ubuntu2
libsqlite0 (2.8.17-7fakesync1) to 2.8.17-7fakesync1build1
libt1-5 (5.1.2-3ubuntu1) to 5.1.2-3ubuntu2
libtag1-vanilla (1.7-1) to 1.7-1ubuntu1
libtag1c2a (1.7-1) to 1.7-1ubuntu1
libtheora0 (1.1.1+dfsg.1-3ubuntu1) to 1.1.1+dfsg.1-3ubuntu2
libtidy-0.99-0 (20091223cvs-1ubuntu1) to 20091223cvs-1ubuntu2
libtotem0 (3.0.1-0ubuntu10) to 3.0.1-0ubuntu11
libubuntuone-1.0-1 (0.11.0-0ubuntu2) to 0.11.0-0ubuntu4
libubuntuone1.0-cil (0.11.0-0ubuntu2) to 0.11.0-0ubuntu4
libupower-glib1 (0.9.14-3) to 0.9.15-1
libutouch-evemu1 (1.0.7-0ubuntu1) to 1.0.8-0ubuntu1
libvte-2.90-9 (1:0.28.2-0ubuntu3) to 1:0.28.2-0ubuntu4
libvte-common (1:0.28.2-0ubuntu3) to 1:0.28.2-0ubuntu4
libvte9 (1:0.28.2-0ubuntu3) to 1:0.28.2-0ubuntu4
libwavpack1 (4.60.1-1) to 4.60.1-2
linux-generic (3.2.0.2.2) to 3.2.0.3.3
linux-headers-generic (3.2.0.2.2) to 3.2.0.3.3
linux-image-generic (3.2.0.2.2) to 3.2.0.3.3
linux-libc-dev (3.2.0-2.5) to 3.2.0-3.8
ltrace (0.5.3-2.1ubuntu1) to 0.5.3-2.1ubuntu2
menu (2.1.45ubuntu1) to 2.1.46ubuntu1
mobile-broadband-provider-info (20110806-1) to 20111113-1
multiarch-support (2.13-20ubuntu6) to 2.13-20ubuntu9
nautilus (1:3.2.1-0ubuntu4) to 1:3.2.1-0ubuntu6
nautilus-data (1:3.2.1-0ubuntu4) to 1:3.2.1-0ubuntu6
nautilus-sendto-empathy (3.2.1.2-0ubuntu1) to 3.3.1-0ubuntu1
openoffice.org-common (1:3.3.0-7ubuntu4) to 1:3.3.0-7ubuntu5
opera (11.52.1100) to 11.60.1185
poppler-utils (0.16.7-2ubuntu3) to 0.18.2-0ubuntu1
procps (1:3.2.8-11ubuntu4) to 1:3.2.8-11ubuntu5
protobuf-compiler (2.4.0a-2ubuntu2) to 2.4.1-1ubuntu2
pulseaudio (1:1.1-0ubuntu1) to 1:1.1-0ubuntu3
pulseaudio-esound-compat (1:1.1-0ubuntu1) to 1:1.1-0ubuntu3
pulseaudio-module-bluetooth (1:1.1-0ubuntu1) to 1:1.1-0ubuntu3
pulseaudio-module-gconf (1:1.1-0ubuntu1) to 1:1.1-0ubuntu3
pulseaudio-module-x11 (1:1.1-0ubuntu1) to 1:1.1-0ubuntu3
pulseaudio-utils (1:1.1-0ubuntu1) to 1:1.1-0ubuntu3
python-appindicator (0.4.1-0ubuntu2) to 0.4.1-0ubuntu3
python-farsight (0.0.31-1ubuntu1) to 0.0.31-1ubuntu2
python-gobject-2 (2.28.6-7) to 2.28.6-8
python-gst0.10 (0.10.21-2.1ubuntu1) to 0.10.21-2.1ubuntu2
python-libproxy (0.3.1-2ubuntu6) to 0.3.1-4ubuntu2
python-protobuf (2.4.0a-2ubuntu2) to 2.4.1-1ubuntu2
python-psutil (0.3.0+r1123-1ubuntu1) to 0.4.0-1ubuntu1
python-speechd (0.7.1-6ubuntu1) to 0.7.1-6ubuntu2
python-tagpy (0.94.8-3) to 0.94.8-3build1
python-uno (1:3.4.4-0ubuntu1) to 1:3.4.4-0ubuntu2
python-vte (1:0.28.2-0ubuntu3) to 1:0.28.2-0ubuntu4
python-webkit (1.1.8-2ubuntu1) to 1.1.8-2ubuntu2
python2.7 (2.7.2-8) to 2.7.2-8build1
python2.7-minimal (2.7.2-8) to 2.7.2-8build1
python3.2 (3.2.2-1) to 3.2.2-1build1
python3.2-minimal (3.2.2-1) to 3.2.2-1build1
qdbus (4:4.7.4-1ubuntu5) to 4:4.7.4-1ubuntu6
rhythmbox (2.90.1~20110908-0ubuntu1) to 2.90.1~20111126.89c872b0-0ubuntu1
rhythmbox-plugin-cdrecorder (2.90.1~20110908-0ubuntu1) to 2.90.1~20111126.89c872b0-0ubuntu1
rhythmbox-plugins (2.90.1~20110908-0ubuntu1) to 2.90.1~20111126.89c872b0-0ubuntu1
rsyslog (5.8.6-1ubuntu2) to 5.8.6-1ubuntu3
sane-utils (1.0.22-2ubuntu2) to 1.0.22-7ubuntu1
software-center (5.1.2.1) to 5.1.3
speech-dispatcher (0.7.1-6ubuntu1) to 0.7.1-6ubuntu2
synaptic (0.75.2ubuntu8) to 0.75.2ubuntu9
syslinux (2:4.04+dfsg-8) to 2:4.04+dfsg-9
syslinux-common (2:4.04+dfsg-8) to 2:4.04+dfsg-9
telepathy-gabble (0.15.0-1) to 0.15.0-1build1
thunderbird (9.0~b2+build1-0ubuntu1) to 9.0~b3+build1-0ubuntu2
thunderbird-globalmenu (9.0~b2+build1-0ubuntu1) to 9.0~b3+build1-0ubuntu2
thunderbird-gnome-support (9.0~b2+build1-0ubuntu1) to 9.0~b3+build1-0ubuntu2
thunderbird-locale-en (1:9.0~b2+build1-0ubuntu1) to 1:9.0~b3+build1-0ubuntu2
thunderbird-locale-en-gb (1:9.0~b2+build1-0ubuntu1) to 1:9.0~b3+build1-0ubuntu2
thunderbird-locale-en-us (1:9.0~b2+build1-0ubuntu1) to 1:9.0~b3+build1-0ubuntu2
totem (3.0.1-0ubuntu10) to 3.0.1-0ubuntu11
totem-common (3.0.1-0ubuntu10) to 3.0.1-0ubuntu11
totem-mozilla (3.0.1-0ubuntu10) to 3.0.1-0ubuntu11
totem-plugins (3.0.1-0ubuntu10) to 3.0.1-0ubuntu11
totem-plugins-extra (3.0.1-0ubuntu10) to 3.0.1-0ubuntu11
ttf-opensymbol (2:2.4.3+LibO3.4.4-0ubuntu1) to 2:2.4.3+LibO3.4.4-0ubuntu2
ttf-ubuntu-font-family (0.80-0ubuntu1) to 0.80-0ubuntu1+console
ubuntu-desktop (1.251) to 1.253
ubuntu-minimal (1.251) to 1.253
ubuntu-standard (1.251) to 1.253
ubuntu-tweak (0.6.0-0~20111117+bzr1619~precise1) to 0.6.0-0~20111205+bzr1622~precise1
unity-lens-files (0.6.12-0ubuntu1) to 0.6.12-0ubuntu2
uno-libs3 (3.4.4-0ubuntu1) to 3.4.4-0ubuntu2
upower (0.9.14-3) to 0.9.15-1
ure (3.4.4-0ubuntu1) to 3.4.4-0ubuntu2
usb-modeswitch (1.1.9-1ubuntu3) to 1.2.0+repack0-1ubuntu1
vim-common (2:7.3.333-1ubuntu2) to 2:7.3.346-1ubuntu1
vim-tiny (2:7.3.333-1ubuntu2) to 2:7.3.346-1ubuntu1
xdiagnose (1.7) to 1.8
zukitwo-dark-gtk-theme (2011.11.10-1~webupd8~oneiric) to 2011.12.05-1~webupd8~oneiric

Installed the following packages:
gir1.2-gst-plugins-base-0.10 (0.10.35-1build1)
libpoppler-glib8 (0.18.2-0ubuntu1)
libpoppler19 (0.18.2-0ubuntu1)
libsane-common (1.0.22-7ubuntu1)
linux-headers-3.2.0-3 (3.2.0-3.8)
linux-headers-3.2.0-3-generic (3.2.0-3.8)
linux-image-3.2.0-3-generic (3.2.0-3.8)
software-center-aptdaemon-plugins (0.1.1)

```

Specific to pulse audio it also upgraded:

> libpulse-mainloop-glib0 (1:1.1-0ubuntu1) to 1:1.1-0ubuntu3
libpulse0 (1:1.1-0ubuntu1) to 1:1.1-0ubuntu3
libpulsedsp (1:1.1-0ubuntu1) to 1:1.1-0ubuntu3

pulseaudio (1:1.1-0ubuntu1) to 1:1.1-0ubuntu3
pulseaudio-esound-compat (1:1.1-0ubuntu1) to 1:1.1-0ubuntu3
pulseaudio-module-bluetooth (1:1.1-0ubuntu1) to 1:1.1-0ubuntu3
pulseaudio-module-gconf (1:1.1-0ubuntu1) to 1:1.1-0ubuntu3
pulseaudio-module-x11 (1:1.1-0ubuntu1) to 1:1.1-0ubuntu3
pulseaudio-utils (1:1.1-0ubuntu1) to 1:1.1-0ubuntu3

And sound is working fine :D

---

### Post by zika on 2011-12-06
At my place it did not go without problems:
```
:~$ sudo aptitude dist-upgrade 
The following packages will be upgraded: 
  libsdl1.2debian{b} 
1 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 197 kB of archives. After unpacking 449 kB will be used.
The following packages have unmet dependencies:
  libsdl1.2debian: Conflicts: libsdl1.2debian-pulseaudio but 1.2.14-6.1ubuntu5 is installed.
The following actions will resolve these dependencies:

     Remove the following packages:
1)     libsdl1.2debian-pulseaudio  



Accept this solution? [Y/n/q/?] y
The following packages will be REMOVED:
  libsdl1.2debian-pulseaudio{a} 
The following packages will be upgraded:
  libsdl1.2debian 
1 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 197 kB of archives. After unpacking 34.8 kB will be freed.
Do you want to continue? [Y/n/?] 
Get: 1 http://us.archive.ubuntu.com/ubuntu/ precise/main libsdl1.2debian amd64 1.2.14-6.4ubuntu1 [197 kB]
Fetched 197 kB in 0s (428 kB/s)      
dpkg: libsdl1.2debian-pulseaudio: dependency problems, but removing anyway as you requested:
 libsdl1.2debian depends on libsdl1.2debian-alsa (= 1.2.14-6.1ubuntu5) | libsdl1.2debian-all (= 1.2.14-6.1ubuntu5) | libsdl1.2debian-esd (= 1.2.14-6.1ubuntu5) | libsdl1.2debian-oss (= 1.2.14-6.1ubuntu5) | libsdl1.2debian-nas (= 1.2.14-6.1ubuntu5) | libsdl1.2debian-pulseaudio (= 1.2.14-6.1ubuntu5); however:
  Package libsdl1.2debian-alsa is not installed.
  Package libsdl1.2debian-all is not installed.
  Package libsdl1.2debian-esd is not installed.
  Package libsdl1.2debian-oss is not installed.
  Package libsdl1.2debian-nas is not installed.
  Package libsdl1.2debian-pulseaudio is to be removed.
(Reading database ... 215354 files and directories currently installed.)
Removing libsdl1.2debian-pulseaudio ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 215346 files and directories currently installed.)
Preparing to replace libsdl1.2debian 1.2.14-6.1ubuntu5 (using .../libsdl1.2debian_1.2.14-6.4ubuntu1_amd64.deb) ...
Unpacking replacement libsdl1.2debian ...
Setting up libsdl1.2debian (1.2.14-6.4ubuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
                                         
Current status: 0 updates [-1], 57559 new [-1].
:~$ sudo aptitude install libsdl1.2debian-pulseaudio
No candidate version found for libsdl1.2debian-pulseaudio
No candidate version found for libsdl1.2debian-pulseaudio
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.
```

```
libsdl1.2debian-pulseaudio:

Package libsdl1.2debian-pulseaudio has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list
```

---

### Post by zika on 2011-12-06
Finally, I've found a line in dependencies: libsdl1.2debian conflicts and replaces libsdl1.2debian-pulseaudio... ;)
It does not correlate, in any sense, with output I received, given above...

---

### Post by Harry33 on 2011-12-06
> **zika said:**
> Finally, I've found a line in dependencies: libsdl1.2debian conflicts and replaces libsdl1.2debian-pulseaudio... ;)
It does not correlate, in any sense, with output I received, given above...

Right, the new package libsdl1.2debian does not accept the libsdl1.2debian-* packages.
So these must be purged.

---

### Post by zika on 2011-12-06
Yeah, I figured that. Even though, messages that it propagated while purging/upgrading were a bit misleading.
I'll mark this [solved]...

---

