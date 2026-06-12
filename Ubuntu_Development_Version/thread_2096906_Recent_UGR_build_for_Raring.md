---
title: "Recent UGR build for Raring?"
date: 2012-12-21
forum: Ubuntu Development Version
---

### Post by sgage on 2012-12-21
I tried to use the IsoBuild script on a daily build of Raring, but no joy. Is there a fairly recent build of UGR available somewhere?

---

### Post by Stinger on 2012-12-21
The most recent I can find is [revision 30]("http://bazaar.launchpad.net/~ubuntu-gnome-dev/+junk/iso-build-script/revision/30").

Did you try using that one ?

sorry, I can see you are looking for an ISO of UGR Raring, no one available yet.

---

### Post by sgage on 2012-12-21
> **Stinger said:**
> The most recent I can find is [revision 30]("http://bazaar.launchpad.net/~ubuntu-gnome-dev/+junk/iso-build-script/revision/30").

Did you try using that one ?

sorry, I can see you are looking for an ISO of UGR Raring, no one available yet.

Indeed, I'm looking for a Raring version. My main system is a UGR based on Quantal, upgraded daily, which runs fine. I just was wondering what jbicha had up his sleeve :KS

---

### Post by Stinger on 2012-12-21
Well.. If it's any comfort, you are not the only one looking who hasn't got an answer yet, I am too.

Marcus Moeller asked basically the same question on the [ubuntu-gnome team mailing list]("https://lists.launchpad.net/ubuntu-gnome/msg00247.html") on 15 Dec 2012, and he hasn't got an answer either.

Roaring silence of the Raring Ringtail UGR :-$   :biggrin:

---

### Post by jbicha on 2012-12-21
> **sgage said:**
> I tried to use the IsoBuild script on a daily build of Raring, but no joy. Is there a fairly recent build of UGR available somewhere?

There is a bug in the build script which means it currently doesn't build on Raring. When we figure that out, we can publish a Raring Alpha or monthly milestone.

---

### Post by jbicha on 2012-12-21
> **Stinger said:**
> 
Marcus Moeller asked basically the same question on the [ubuntu-gnome team mailing list]("https://lists.launchpad.net/ubuntu-gnome/msg00247.html") on 15 Dec 2012, and he hasn't got an answer either.

There basically won't be *daily* builds unless we become an official flavor or someone with plenty of bandwidth volunteers to build and host dailies.

---

### Post by kansasnoob on 2012-12-21
It's still a small team, and as far that goes there is no alpha build of Ubuntu itself either ;)

The only flavors that had Alpha 1 builds were Edubuntu and Kubuntu :)

---

### Post by Stinger on 2012-12-21
@jbicha

Your most kind answers basically covers the above questions :biggrin:

---

### Post by sgage on 2012-12-21
> **jbicha said:**
> There is a bug in the build script which means it currently doesn't build on Raring. When we figure that out, we can publish a Raring Alpha or monthly milestone.

Thanks for the reply. Once the script is sorted out, I'll have no problem 'rolling my own', as it were, but having a monthly milestone would be a good thing. 

And thanks for all your efforts!

---

### Post by kansasnoob on 2012-12-21
> **jbicha said:**
> There basically won't be *daily* builds unless we become an official flavor or someone with plenty of bandwidth volunteers to build and host dailies.

I hope you mean "until" we become an official flavor rather than "unless" :D

IMHO we're badly needed to fill the pure Gnome gap.

---

### Post by VideoRoy on 2012-12-22
> **kansasnoob said:**
> I hope you mean "until" we become an official flavor rather than "unless" :D

IMHO we're badly needed to fill the pure Gnome gap.

Another convert here!  I have been using the Quantal version on my desktop since I ran across the build.  I made just a few tweaks but this will probably become my standard distro for all but my netbook.

The biggest tweak I made was replacing packagekit with Software Center so I am looking forward to Raring as I understand that will be the default.

Thanks for the work!

---

### Post by grahammechanical on 2012-12-23
> **jbicha said:**
> There basically won't be *daily* builds unless we become an official flavor or someone with plenty of bandwidth volunteers to build and host dailies.

Might I suggest Gnome organisation?

Just joking. Are there pure Gnome distributions other than this one? Pure Gnome based upon Debian?

Regards.

---

### Post by kansasnoob on 2012-12-23
I did some piddling with this mini.iso today:

[http://iso.qa.ubuntu.com/qatracker/milestones/243/builds/31224/downloads](http://iso.qa.ubuntu.com/qatracker/milestones/243/builds/31224/downloads)

I chose the Command Line Install and when it was complete I booted to TTY as expected, then I ran:

```
sudo apt-get install ubuntu-gnome-desktop
```

But like a dummy the only things I looked for was that it also installed 'ubuntu-gnome-default-settings' and 'gdm'.

Sadly my inattention resulted in the installation of a butt-load of 'unity*' packages (but not 'ubuntu-desktop'):

```
Start-Date: 2012-12-23  15:41:48
Commandline: apt-get install ubuntu-gnome-desktop
Install: xserver-xorg:i386 (7.7+1ubuntu4, automatic), ubuntuone-client:i386 (4.1.0-0ubuntu2, automatic), x11-apps:i386 (7.7~2ubuntu1, automatic), python-crypto:i386 (2.6-2build3, automatic), policykit-1-gnome:i386 (0.105-1ubuntu4, automatic), gir1.2-polkit-1.0:i386 (0.105-1ubuntu1, automatic), libgs9-common:i386 (9.06~dfsg-0ubuntu4, automatic), libfolks-telepathy25:i386 (0.8.0-1, automatic), gnome-sushi:i386 (3.6.1-0ubuntu1), libopencc1:i386 (0.3.0-3, automatic), libunity-core-6.0-5:i386 (6.12.0daily12.12.05-0ubuntu1, automatic), sane-utils:i386 (1.0.23-0ubuntu1, automatic), libglapi-mesa:i386 (9.0.1-0ubuntu1, automatic), gnome-keyring:i386 (3.6.2-0ubuntu1, automatic), fonts-tlwg-mono:i386 (0.5.0-5, automatic), libplist1:i386 (1.8-2, automatic), aspell-en:i386 (7.1-0-1, automatic), libgtk2.0-common:i386 (2.24.13-0ubuntu2, automatic), gstreamer0.10-alsa:i386 (0.10.36-1.1ubuntu1), bluez-alsa:i386 (4.101-0ubuntu8), evolution-common:i386 (3.6.2-0ubuntu2, automatic), libmusicbrainz5-0:i386 (5.0.1-2, automatic), libmetacity-private0a:i386 (2.34.13-0ubuntu1, automatic), mesa-utils:i386 (8.0.1+git20110129+d8f7d6b-0ubuntu2, automatic), unity-asset-pool:i386 (0.8.24daily12.12.05-0ubuntu1, automatic), libatk1.0-0:i386 (2.7.2-0ubuntu2, automatic), xorg-docs-core:i386 (1.6-1ubuntu2, automatic), libgnomekbd8:i386 (3.6.0-0ubuntu1, automatic), libpurple0:i386 (2.10.6-0ubuntu3, automatic), python-twisted-names:i386 (12.2.0-1, automatic), apturl-common:i386 (0.5.1ubuntu6, automatic), syslinux:i386 (4.06+dfsg-3, automatic), libtalloc2:i386 (2.0.7+git20120207-1, automatic), libpeas-common:i386 (1.4.0-2ubuntu4, automatic), libpanel-applet-4-0:i386 (3.6.2-0ubuntu3, automatic), libical0:i386 (0.48-2, automatic), unity-webapps-service:i386 (2.4.3daily12.12.05-0ubuntu2, automatic), libaccounts-glib0:i386 (1.3-0ubuntu2, automatic), ttf-dejavu-core:i386 (2.33-3ubuntu1, automatic), udisks2:i386 (2.0.0-3git1, automatic), geoclue:i386 (0.12.99-0ubuntu2, automatic), unity:i386 (6.12.0daily12.12.05-0ubuntu1, automatic), libcdio13:i386 (0.83-4, automatic), libmodplug1:i386 (0.8.8.4-3, automatic), mutter-common:i386 (3.6.2-0ubuntu1, automatic), libglib-perl:i386 (1.261-1, automatic), python-twisted-core:i386 (12.2.0-1, automatic), libxfixes3:i386 (5.0-4ubuntu5, automatic), wamerican:i386 (7.1-1, automatic), liborc-0.4-0:i386 (0.4.16-2, automatic), libgtkmm-3.0-1:i386 (3.6.0-0ubuntu1, automatic), gir1.2-totem-1.0:i386 (3.6.3-0ubuntu2, automatic), shared-mime-info:i386 (1.0-1ubuntu2, automatic), python-gst0.10:i386 (0.10.22-3ubuntu1, automatic), libfontembed1:i386 (1.0.25-1, automatic), libzbar0:i386 (0.10+doc-7build3, automatic), libcanberra-gtk-module:i386 (0.30-0ubuntu1, automatic), libmtp9:i386 (1.1.5-1, automatic), account-plugin-flickr:i386 (0.10bzr12.12.10-0ubuntu1, automatic), libenchant1c2a:i386 (1.6.0-7build1, automatic), xsltproc:i386 (1.1.26-14, automatic), gwibber-service:i386 (3.6.0-0ubuntu1, automatic), notification-daemon:i386 (0.7.6-1, automatic), libnm-glib-vpn1:i386 (0.9.6.0+git201211131441.e9e2c56-0ubuntu3, automatic), libatasmart4:i386 (0.19-1git1, automatic), gcalctool:i386 (6.6.2-0ubuntu1), libyelp0:i386 (3.6.2-0ubuntu1, automatic), libcolamd2.7.1:i386 (3.4.0-3ubuntu1, automatic), libegl1-mesa:i386 (9.0.1-0ubuntu1, automatic), xserver-xorg-input-evdev:i386 (2.7.3-0ubuntu2, automatic), libgmp10:i386 (5.0.5+dfsg-2ubuntu3, automatic), gir1.2-json-1.0:i386 (0.15.2-0ubuntu1, automatic), lp-solve:i386 (5.5.0.13-7, automatic), gstreamer0.10-x:i386 (0.10.36-1.1ubuntu1, automatic), gir1.2-gconf-2.0:i386 (3.2.5-0ubuntu5, automatic), libcompizconfig0:i386 (0.9.9~daily12.12.05-0ubuntu2, automatic), libpango-perl:i386 (1.223-0ubuntu1, automatic), python3-apport:i386 (2.7-0ubuntu2, automatic), libgail18:i386 (2.24.13-0ubuntu2, automatic), telepathy-salut:i386 (0.8.1-1, automatic), update-manager:i386 (0.175, automatic), libhttp-daemon-perl:i386 (6.01-1, automatic), libmpfr4:i386 (3.1.0-5, automatic), libwhoopsie0:i386 (0.2.9, automatic), fonts-khmeros-core:i386 (5.0-5ubuntu1), gnome-shell:i386 (3.6.2-0ubuntu4), libpth20:i386 (2.0.7-16ubuntu4, automatic), account-plugin-yahoo:i386 (3.6.2-0ubuntu1, automatic), gnuchess-book:i386 (1.02-1, automatic), libflite1:i386 (1.4-release-6, automatic), libqt4-declarative:i386 (4.8.3+dfsg-0ubuntu3, automatic), libegl1-mesa-drivers:i386 (9.0.1-0ubuntu1, automatic), libgphoto2-port0:i386 (2.4.14-2, automatic), python-pyinotify:i386 (0.9.3-1.1ubuntu1, automatic), gnome-media:i386 (3.4.0-1ubuntu1), libv4l-0:i386 (0.8.9-1, automatic), liblcms1:i386 (1.19.dfsg-1.2ubuntu2, automatic), gnome-games-extra-data:i386 (3.2.0-4, automatic), metacity:i386 (2.34.13-0ubuntu1, automatic), epiphany-browser:i386 (3.6.1-2ubuntu1), gnome-desktop-data:i386 (2.32.1-2ubuntu1, automatic), libraptor2-0:i386 (2.0.8-2, automatic), libcaribou0:i386 (0.4.4-1ubuntu1, automatic), python-pexpect:i386 (2.4-1, automatic), nautilus:i386 (3.6.3-0ubuntu3, automatic), libunity9:i386 (6.90.0daily12.12.05-0ubuntu1, automatic), libfile-listing-perl:i386 (6.04-1, automatic), aisleriot:i386 (3.4.1+really3.2.3.2-0ubuntu2), libgnome-media-profiles-3.0-0:i386 (3.0.0-1ubuntu1, automatic), libpackagekit-glib2-14:i386 (0.7.6-2, automatic), libnettle4:i386 (2.4-3, automatic), fonts-freefont-ttf:i386 (20120503-1), gtali:i386 (3.6.1-0ubuntu2, automatic), python-notify:i386 (0.1.1-3build1, automatic), diffstat:i386 (1.55-3, automatic), bluez-gstreamer:i386 (4.101-0ubuntu8), xfonts-scalable:i386 (1.0.3-1, automatic), python-aptdaemon.gtk3widgets:i386 (0.45+bzr883-0ubuntu1, automatic), python-renderpm:i386 (2.5-1.1build2, automatic), network-manager-pptp-gnome:i386 (0.9.6.0-0ubuntu1, automatic), gvfs-fuse:i386 (1.14.2-0ubuntu1), baobab:i386 (3.6.3-0ubuntu1), gir1.2-gtk-3.0:i386 (3.6.2-0ubuntu1, automatic), libgtop2-common:i386 (2.28.4-3, automatic), libgstreamer0.10-0:i386 (0.10.36-1ubuntu2, automatic), libtelepathy-glib0:i386 (0.20.1-1ubuntu1, automatic), ttf-punjabi-fonts:i386 (0.5.11ubuntu1), python-mako:i386 (0.7.3-1, automatic), libportaudio2:i386 (19+svn20111121-1build1, automatic), libgtksourceview-3.0-0:i386 (3.6.1-0ubuntu1, automatic), python-cloudfiles:i386 (1.7.9.2-1, automatic), aspell:i386 (0.60.7~20110707-1build1, automatic), libgtkspell-3-0:i386 (3.0.0~hg20110814-1build1, automatic), libnss3:i386 (3.14-1ubuntu1, automatic), libtracker-miner-0.14-0:i386 (0.14.4-0ubuntu1, automatic), libsensors4:i386 (3.3.2-2ubuntu1, automatic), usbmuxd:i386 (1.0.8-1, automatic), libwrap0:i386 (7.6.q-24, automatic), appmenu-gtk:i386 (12.10.3daily12.11.28-0ubuntu2, automatic), xserver-xorg-video-all:i386 (7.7+1ubuntu4, automatic), tracker:i386 (0.14.4-0ubuntu1), libcanberra-gtk3-0:i386 (0.30-0ubuntu1, automatic), glchess:i386 (3.6.1-0ubuntu2, automatic), libebook-1.2-14:i386 (3.6.2-0ubuntu1, automatic), pkg-config:i386 (0.26-1ubuntu2, automatic), libatk-bridge2.0-0:i386 (2.7.2-0ubuntu1, automatic), libglib2.0-bin:i386 (2.34.3-1, automatic), python-dirspec:i386 (4.1.0-0ubuntu1, automatic), gir1.2-gtkclutter-1.0:i386 (1.4.0-1, automatic), libwww-robotrules-perl:i386 (6.01-1, automatic), gir1.2-javascriptcoregtk-3.0:i386 (1.10.2-0ubuntu1, automatic), libcupscgi1:i386 (1.6.1-0ubuntu12, automatic), mobile-broadband-provider-info:i386 (20121112-1, automatic), libcaca0:i386 (0.99.beta18-1, automatic), python-zope.interface:i386 (4.0.2-0ubuntu2, automatic), gstreamer1.0-plugins-base:i386 (1.0.4-1, automatic), libgoffice-0.8-8-common:i386 (0.8.17-1.2ubuntu1, automatic), intltool-debian:i386 (0.35.0+20060710.1, automatic), libindicator7:i386 (12.10.1-0ubuntu1, automatic), enchant:i386 (1.6.0-7build1, automatic), libiec61883-0:i386 (1.2.0-0.1ubuntu2, automatic), libsnmp15:i386 (5.4.3~dfsg-2.7ubuntu1, automatic), genisoimage:i386 (1.1.11-2ubuntu3, automatic), xserver-xorg-video-ati:i386 (7.0.0-0ubuntu1, automatic), brasero-cdrkit:i386 (3.6.1-0ubuntu1, automatic), libwmf0.2-7:i386 (0.2.8.4-10.2ubuntu1, automatic), libdjvulibre21:i386 (3.5.25.3-3, automatic), oneconf:i386 (0.2.9.1, automatic), obex-data-server:i386 (0.4.6-0ubuntu2, automatic), gnome-settings-daemon:i386 (3.6.3-0ubuntu4, automatic), indicator-application:i386 (12.10.0-0ubuntu2, automatic), fonts-tlwg-typewriter:i386 (0.5.0-5, automatic), wireless-tools:i386 (30~pre9-8ubuntu1), gir1.2-unity-5.0:i386 (6.90.0daily12.12.05-0ubuntu1, automatic), librdf0:i386 (1.0.15-1, automatic), apport-symptoms:i386 (0.19, automatic), libutempter0:i386 (1.1.5-4build1, automatic), gir1.2-messagingmenu-1.0:i386 (12.10.6daily12.11.22-0ubuntu1, automatic), fonts-tlwg-garuda:i386 (0.5.0-5, automatic), libicu48:i386 (4.8.1.1-10, automatic), network-manager-pptp:i386 (0.9.6.0-0ubuntu1, automatic), smbclient:i386 (3.6.9-1ubuntu1, automatic), libraw5:i386 (0.14.7-0ubuntu1, automatic), python-protobuf:i386 (2.4.1-3ubuntu1, automatic), libjpeg8:i386 (8c-2ubuntu7, automatic), brasero-common:i386 (3.6.1-0ubuntu1, automatic), gir1.2-accountsservice-1.0:i386 (0.6.29-1ubuntu2, automatic), libvorbisfile3:i386 (1.3.2-1.3, automatic), python-debtagshw:i386 (1.10.2ubuntu1, automatic), xserver-xorg-video-tdfx:i386 (1.4.5-0ubuntu1, automatic), libsane-common:i386 (1.0.23-0ubuntu1, automatic), libclutter-gst-1.0-0:i386 (1.6.0-1ubuntu1, automatic), doc-base:i386 (0.10.4), gnome-video-effects:i386 (0.4.0-1ubuntu2), python-ubuntuone-storageprotocol:i386 (4.1.0-0ubuntu1, automatic), gucharmap:i386 (3.6.1-0ubuntu1), libcamel-1.2-40:i386 (3.6.2-0ubuntu1, automatic), network-manager:i386 (0.9.6.0+git201211131441.e9e2c56-0ubuntu3, automatic), printer-driver-c2esp:i386 (26-1ubuntu1), zenity:i386 (3.6.0-0ubuntu1, automatic), ubuntu-gnome-desktop:i386 (0.6), libcogl11:i386 (1.12.0-1, automatic), avahi-daemon:i386 (0.6.31-1ubuntu2, automatic), libnet-ssleay-perl:i386 (1.48-1, automatic), gnome-games:i386 (3.6.1-0ubuntu2), libgail-common:i386 (2.24.13-0ubuntu2, automatic), xserver-xorg-video-trident:i386 (1.3.6-0ubuntu2, automatic), qdbus:i386 (4.8.3+dfsg-0ubuntu3, automatic), libgnome-keyring0:i386 (3.6.0-1, automatic), gnome-desktop3-data:i386 (3.6.2-0ubuntu4, automatic), x11-utils:i386 (7.7~1ubuntu1, automatic), cheese:i386 (3.6.2-0ubuntu1), libecal-1.2-15:i386 (3.6.2-0ubuntu1, automatic), gnome-session-canberra:i386 (0.30-0ubuntu1), liburi-perl:i386 (1.60-1, automatic), python3-aptdaemon:i386 (0.45+bzr883-0ubuntu1, automatic), libpixman-1-0:i386 (0.26.0-3, automatic), gir1.2-gdkpixbuf-2.0:i386 (2.26.5-0ubuntu3, automatic), re2c:i386 (0.13.5-1build2, automatic), upower:i386 (0.9.17-1build1, automatic), libgck-1-0:i386 (3.6.2-0ubuntu1, automatic), quadrapassel:i386 (3.6.1-0ubuntu2, automatic), libots0:i386 (0.5.0-2.1, automatic), libdbusmenu-glib4:i386 (12.10.2-0ubuntu1, automatic), python-twisted-web:i386 (12.2.0-1, automatic), python3-xkit:i386 (0.5.0ubuntu1, automatic), pulseaudio:i386 (2.1-0ubuntu4, automatic), gnome-bluetooth:i386 (3.6.1-0ubuntu1, automatic), evolution:i386 (3.6.2-0ubuntu2), account-plugin-twitter:i386 (0.10bzr12.12.10-0ubuntu1, automatic), aptdaemon-data:i386 (0.45+bzr883-0ubuntu1, automatic), tracker-utils:i386 (0.14.4-0ubuntu1, automatic), libspectre1:i386 (0.2.7-2, automatic), libnm-gtk0:i386 (0.9.6.2+git201211052130.2d666bc-0ubuntu2, automatic), software-center-aptdaemon-plugins:i386 (0.1.5, automatic), xserver-xorg-video-fbdev:i386 (0.4.3-0ubuntu1, automatic), xserver-xorg-input-wacom:i386 (0.18.0-0ubuntu1, automatic), gnobots2:i386 (3.6.1-0ubuntu2, automatic), sound-theme-freedesktop:i386 (0.7.pristine-2, automatic), libart-2.0-2:i386 (2.3.21-2, automatic), app-install-data:i386 (13.04.1, automatic), ibus-gtk3:i386 (1.4.2-0ubuntu1, automatic), python3-aptdaemon.pkcompat:i386 (0.45+bzr883-0ubuntu1, automatic), libnux-4.0-0:i386 (4.0.0daily12.12.05-0ubuntu1, automatic), libfolks-eds25:i386 (0.8.0-1, automatic), libfile-fcntllock-perl:i386 (0.14-2, automatic), bamfdaemon:i386 (0.4.0daily12.12.05-0ubuntu2, automatic), gnome-themes-standard:i386 (3.6.2-0ubuntu2, automatic), gnome-power-manager:i386 (3.6.0-1, automatic), libavahi-common-data:i386 (0.6.31-1ubuntu2, automatic), patchutils:i386 (0.3.2-1.1build1, automatic), python3-crypto:i386 (2.6-2build3, automatic), glib-networking-services:i386 (2.34.2-0ubuntu1, automatic), libudisks2-0:i386 (2.0.0-3git1, automatic), libsane:i386 (1.0.23-0ubuntu1, automatic), unity-lens-gwibber:i386 (3.6.0-0ubuntu1, automatic), udisks:i386 (1.0.4-7, automatic), python-aptdaemon:i386 (0.45+bzr883-0ubuntu1, automatic), gir1.2-ubuntuoneui-3.0:i386 (4.1.0-0ubuntu1, automatic), gnome-mahjongg:i386 (3.6.1-0ubuntu2, automatic), unzip:i386 (6.0-8ubuntu1, automatic), gir1.2-clutter-1.0:i386 (1.12.2-0ubuntu1, automatic), gir1.2-atspi-2.0:i386 (2.7.2-0ubuntu1, automatic), glib-networking:i386 (2.34.2-0ubuntu1, automatic), python-pycurl:i386 (7.19.0-5ubuntu3, automatic), python3-software-properties:i386 (0.92.13, automatic), libunity-webapps0:i386 (2.4.3daily12.12.05-0ubuntu2, automatic), unity-lens-applications:i386 (6.10.0daily12.12.05-0ubuntu1, automatic), totem-plugins:i386 (3.6.3-0ubuntu2, automatic), libmail-spf-perl:i386 (2.8.0-1, automatic), libqpdf8:i386 (3.0.2-1, automatic), x11-xfs-utils:i386 (7.7~1, automatic), libqt4-sql-mysql:i386 (4.8.3+dfsg-0ubuntu3, automatic), epiphany-browser-data:i386 (3.6.1-2ubuntu1, automatic), libqt4-dbus:i386 (4.8.3+dfsg-0ubuntu3, automatic), libglew1.8:i386 (1.9.0.is.1.8.0-0ubuntu1, automatic), gnome-screensaver:i386 (3.6.1-0ubuntu2), libgucharmap-2-90-7:i386 (3.6.1-0ubuntu1, automatic), ibus-pinyin-db-open-phrase:i386 (1.4.0-1build1, automatic), rhythmbox:i386 (2.98-0ubuntu3, automatic), libburn4:i386 (1.2.4-0ubuntu1, automatic), libxxf86vm1:i386 (1.1.2-1, automatic), python3-cairo:i386 (1.10.0+dfsg-3~exp3ubuntu1, automatic), ubuntu-sso-client:i386 (4.1.0-0ubuntu1, automatic), tracker-gui:i386 (0.14.4-0ubuntu1, automatic), libproxy1:i386 (0.4.10-0ubuntu1, automatic), libpst4:i386 (0.6.54-4.1, automatic), xterm:i386 (278-1ubuntu2), liblcms2-2:i386 (2.4-0ubuntu1, automatic), gnome-screenshot:i386 (3.6.1-0ubuntu1), libwpg-0.2-2:i386 (0.2.1-1build1, automatic), xserver-xorg-video-mga:i386 (1.6.2-0ubuntu1, automatic), ibus-gtk:i386 (1.4.2-0ubuntu1, automatic), system-config-printer-gnome:i386 (1.3.11+20120807-0ubuntu11, automatic), manpages-dev:i386 (3.44-0ubuntu1, automatic), python-libxml2:i386 (2.9.0+dfsg1-4, automatic), gedit:i386 (3.6.2-0ubuntu1), libnm-util2:i386 (0.9.6.0+git201211131441.e9e2c56-0ubuntu3, automatic), libdecoration0:i386 (0.9.9~daily12.12.05-0ubuntu2, automatic), libhttp-date-perl:i386 (6.02-1, automatic), plymouth-label:i386 (0.8.8-0ubuntu5, automatic), gnome-menus:i386 (3.6.1-0ubuntu2, automatic), liblircclient0:i386 (0.9.0-0ubuntu3, automatic), xdg-user-dirs-gtk:i386 (0.9-1ubuntu1), libgexiv2-1:i386 (0.5.0-0ubuntu1, automatic), libproxy1-plugin-networkmanager:i386 (0.4.10-0ubuntu1), gtk2-engines-pixbuf:i386 (2.24.13-0ubuntu2, automatic), gnome-session-common:i386 (3.6.2-0ubuntu2, automatic), bluez-cups:i386 (4.101-0ubuntu8), xserver-xorg-input-vmmouse:i386 (12.9.0-0ubuntu3, automatic), libtdb1:i386 (1.2.10-2, automatic), foomatic-db-compressed-ppds:i386 (20120823-0ubuntu4), hunspell-en-us:i386 (20070829-4ubuntu3, automatic), x11-xserver-utils:i386 (7.7~3ubuntu2, automatic), libmutter0a:i386 (3.6.2-0ubuntu1, automatic), libaccounts-qt1:i386 (1.3-0ubuntu1, automatic), hpijs:i386 (3.12.11-0ubuntu1, automatic), liblwp-mediatypes-perl:i386 (6.02-1, automatic), dvd+rw-tools:i386 (7.1-10build1, automatic), protobuf-compiler:i386 (2.4.1-3ubuntu1, automatic), libfont-afm-perl:i386 (1.20-1, automatic), abiword-common:i386 (2.9.2+svn20120603-8, automatic), libmailtools-perl:i386 (2.09-1, automatic), signon-ui:i386 (0.12-0ubuntu1, automatic), libpam-gnome-keyring:i386 (3.6.2-0ubuntu1, automatic), libglu1-mesa:i386 (9.0.0-0ubuntu1, automatic), libgstreamer-plugins-base1.0-0:i386 (1.0.4-1, automatic), libxcb-glx0:i386 (1.8.1-2, automatic), xserver-xorg-input-mouse:i386 (1.7.2-3, automatic), cups-client:i386 (1.6.1-0ubuntu12, automatic), evince-common:i386 (3.6.1-1ubuntu1, automatic), inputattach:i386 (1.4.3-1), libjack-jackd2-0:i386 (1.9.8~dfsg.4+20121110git67ac4440-1, automatic), brltty:i386 (4.4-6ubuntu1), xserver-xorg-video-r128:i386 (6.9.1-0ubuntu1, automatic), libieee1284-3:i386 (0.2.11-10build2, automatic), fonts-sil-abyssinica:i386 (1.200-3), libcryptsetup4:i386 (1.4.3-4ubuntu2, automatic), libcupsmime1:i386 (1.6.1-0ubuntu12, automatic), abiword:i386 (2.9.2+svn20120603-8), libc-dev-bin:i386 (2.16-0ubuntu8, automatic), gir1.2-soup-2.4:i386 (2.40.2-0ubuntu1, automatic), libqtwebkit4:i386 (2.2.1-4ubuntu1, automatic), cheese-common:i386 (3.6.2-0ubuntu1, automatic), libgstreamer1.0-0:i386 (1.0.4-1, automatic), abiword-plugin-mathview:i386 (2.9.2+svn20120603-8, automatic), xserver-common:i386 (1.13.0.902-0ubuntu1, automatic), gir1.2-gkbd-3.0:i386 (3.6.0-0ubuntu1, automatic), libsocket6-perl:i386 (0.23-1build3, automatic), printer-driver-pxljr:i386 (1.3+repack0-2build1), libtxc-dxtn-s2tc0:i386 (0~git20110809-3, automatic), signon-keyring-extension:i386 (0.4daily12.12.06-0ubuntu1, automatic), mcp-account-manager-uoa:i386 (3.6.2-0ubuntu1, automatic), libdca0:i386 (0.0.5-5, automatic), libx86-1:i386 (1.1+ds1-10, automatic), python3-chardet:i386 (2.0.1-1, automatic), libhtml-parser-perl:i386 (3.69-2, automatic), gnome-control-center:i386 (3.6.3-0ubuntu9, automatic), gir1.2-dbusmenu-glib-0.4:i386 (12.10.2-0ubuntu1, automatic), fonts-lao:i386 (0.0.20060226-8), libspeex1:i386 (1.2~rc1-7, automatic), gir1.2-gnomedesktop-3.0:i386 (3.6.2-0ubuntu4, automatic), libnotify-bin:i386 (0.7.5-1build1), bc:i386 (1.06.95-4), lightsoff:i386 (3.6.1-0ubuntu2, automatic), printer-driver-postscript-hp:i386 (3.12.11-0ubuntu1, automatic), libdrm-intel1:i386 (2.4.40-1, automatic), gvfs-libs:i386 (1.14.2-0ubuntu1, automatic), libjs-jquery:i386 (1.7.2+debian-1ubuntu1, automatic), hplip:i386 (3.12.11-0ubuntu1), unity-scope-gdrive:i386 (0.8daily12.12.05-0ubuntu1, automatic), libcheese7:i386 (3.6.2-0ubuntu1, automatic), libsignon-qt1:i386 (8.44-0ubuntu1, automatic), libgcr-3-1:i386 (3.6.2-0ubuntu1, automatic), libglewmx1.8:i386 (1.9.0.is.1.8.0-0ubuntu1, automatic), ibus-pinyin:i386 (1.4.0-1build1), dc:i386 (1.06.95-4, automatic), gconf2:i386 (3.2.5-0ubuntu5, automatic), libminiupnpc8:i386 (1.6-3ubuntu2, automatic), libwnck-common:i386 (2.30.7-0ubuntu2, automatic), python-dbus-dev:i386 (1.1.1-1ubuntu2, automatic), libxatracker1:i386 (9.0.1-0ubuntu1, automatic), libupower-glib1:i386 (0.9.17-1build1, automatic), python3-six:i386 (1.2.0-1, automatic), gnome-color-manager:i386 (3.6.0-0ubuntu1), libxcb-xfixes0:i386 (1.8.1-2, automatic), xserver-xorg-video-openchrome:i386 (0.3.1-0ubuntu1, automatic), libxslt1.1:i386 (1.1.26-14, automatic), update-notifier-common:i386 (0.126, automatic), libfile-copy-recursive-perl:i386 (0.38-1, automatic), fonts-thai-tlwg:i386 (0.5.0-5), account-plugin-jabber:i386 (3.6.2-0ubuntu1, automatic), metacity-common:i386 (2.34.13-0ubuntu1, automatic), seahorse:i386 (3.6.3-0ubuntu1), deja-dup-backend-gvfs:i386 (25.3-0ubuntu1, automatic), xserver-xorg-video-vesa:i386 (2.3.2-0ubuntu1, automatic), libgtkhtml-4.0-0:i386 (4.6.1-0ubuntu1, automatic), libgettextpo-dev:i386 (0.18.1.1-10ubuntu1, automatic), fonts-lklug-sinhala:i386 (0.6-2), librest-0.7-0:i386 (0.7.90-0ubuntu1, automatic), libsignon-glib1:i386 (1.7-0ubuntu1, automatic), ubuntu-system-service:i386 (0.2.3, automatic), libgomp1:i386 (4.7.2-16ubuntu1, automatic), system-config-printer-udev:i386 (1.3.11+20120807-0ubuntu11, automatic), printer-driver-gutenprint:i386 (5.2.9-1ubuntu1, automatic), libsignon-plugins-common1:i386 (8.44-0ubuntu1, automatic), empathy:i386 (3.6.2-0ubuntu1), gir1.2-networkmanager-1.0:i386 (0.9.6.0+git201211131441.e9e2c56-0ubuntu3, automatic), libframe6:i386 (2.5.0daily12.12.13-0ubuntu1, automatic), xserver-xorg-video-siliconmotion:i386 (1.7.7-0ubuntu1, automatic), xserver-xorg-video-mach64:i386 (6.9.3-0ubuntu1, automatic), mysql-common:i386 (5.5.28-0ubuntu3, automatic), python3-debian:i386 (0.1.21+nmu2ubuntu1, automatic), printer-driver-foo2zjs:i386 (20120510dfsg0-1ubuntu1), xserver-xorg-video-sis:i386 (0.10.7-0ubuntu1, automatic), cups-filters:i386 (1.0.25-1, automatic), libtotem-plparser17:i386 (3.4.3-1, automatic), xserver-xorg-video-modesetting:i386 (0.5.0-0ubuntu1, automatic), python-lxml:i386 (3.0.1-1build1, automatic), totem-common:i386 (3.6.3-0ubuntu2, automatic), libcairo2:i386 (1.12.8-0ubuntu4, automatic), rfkill:i386 (0.4-2ubuntu1), libnotify4:i386 (0.7.5-1build1, automatic), libfontconfig1:i386 (2.10.2-0ubuntu1, automatic), unity-services:i386 (6.12.0daily12.12.05-0ubuntu1, automatic), ghostscript-x:i386 (9.06~dfsg-0ubuntu4), libnetfilter-conntrack3:i386 (1.0.1-1, automatic), libpoppler28:i386 (0.20.5-0ubuntu3, automatic), libx11-xcb1:i386 (1.5.0-1, automatic), libquvi-scripts:i386 (0.4.8-3, automatic), xserver-xorg-video-qxl:i386 (0.1.0-0ubuntu1, automatic), libxcb-util0:i386 (0.3.8-2build1, automatic), python-gconf:i386 (2.28.1+dfsg-1build1, automatic), python-simplejson:i386 (2.6.2-1, automatic), gir1.2-gudev-1.0:i386 (175-0ubuntu14, automatic), fontconfig-config:i386 (2.10.2-0ubuntu1, automatic), libass4:i386 (0.10.1-1, automatic), libclutter-gtk-1.0-0:i386 (1.4.0-1, automatic), libvo-aacenc0:i386 (0.1.2-1, automatic), libevent-2.0-5:i386 (2.0.19-stable-3, automatic), gvfs-bin:i386 (1.14.2-0ubuntu1, automatic), liberror-perl:i386 (0.17-1, automatic), libnetaddr-ip-perl:i386 (4.062+dfsg-1, automatic), fonts-takao-pgothic:i386 (003.02.01-7ubuntu1), python-reportlab-accel:i386 (2.5-1.1build2, automatic), libpulse-mainloop-glib0:i386 (2.1-0ubuntu4, automatic), gnumeric-common:i386 (1.10.17-1.1ubuntu1, automatic), fonts-lyx:i386 (2.0.3-3, automatic), libtotem0:i386 (3.6.3-0ubuntu2, automatic), libraw1394-11:i386 (2.0.9-1, automatic), policykit-1:i386 (0.105-1ubuntu1, automatic), gnome-control-center-unity:i386 (1.0-0ubuntu1, automatic), update-notifier:i386 (0.126, automatic), gvfs-common:i386 (1.14.2-0ubuntu1, automatic), apport:i386 (2.7-0ubuntu2, automatic), gstreamer0.10-gconf:i386 (0.10.31-3+nmu1ubuntu1, automatic), libvorbisenc2:i386 (1.3.2-1.3, automatic), gnumeric-doc:i386 (1.10.17-1.1ubuntu1, automatic), xserver-xorg-video-s3:i386 (0.6.5-0ubuntu1, automatic), libjbig0:i386 (2.0-2ubuntu1, automatic), libapt-pkg-perl:i386 (0.1.26, automatic), account-plugin-salut:i386 (3.6.2-0ubuntu1, automatic), gir1.2-atk-1.0:i386 (2.7.2-0ubuntu2, automatic), libgdk-pixbuf2.0-common:i386 (2.26.5-0ubuntu3, automatic), linux-libc-dev:i386 (3.7.0-7.15, automatic), xml-core:i386 (0.13+nmu2, automatic), libgoa-1.0-common:i386 (3.6.2-0ubuntu1, automatic), libfile-basedir-perl:i386 (0.03-1fakesync1, automatic), nautilus-data:i386 (3.6.3-0ubuntu3, automatic), libgpod4:i386 (0.8.2-7ubuntu1, automatic), mtools:i386 (4.0.17-1, automatic), librasqal3:i386 (0.9.29-1, automatic), bluez:i386 (4.101-0ubuntu8, automatic), spamassassin:i386 (3.3.2-4ubuntu2, automatic), libwacom-common:i386 (0.6-1, automatic), libnl-route-3-200:i386 (3.2.16-0ubuntu1, automatic), libdbusmenu-gtk3-4:i386 (12.10.2-0ubuntu1, automatic), gvfs-daemons:i386 (1.14.2-0ubuntu1, automatic), libabiword-2.9:i386 (2.9.2+svn20120603-8, automatic), libarchive-zip-perl:i386 (1.30-6, automatic), qpdf:i386 (3.0.2-1, automatic), python-gi-cairo:i386 (3.7.3-0ubuntu2, automatic), gnome-font-viewer:i386 (3.6.2-0ubuntu1), gir1.2-gtksource-3.0:i386 (3.6.1-0ubuntu1, automatic), gstreamer0.10-plugins-good:i386 (0.10.31-3+nmu1ubuntu1, automatic), libgettextpo0:i386 (0.18.1.1-10ubuntu1, automatic), libgeoclue0:i386 (0.12.99-0ubuntu2, automatic), libxcb-render0:i386 (1.8.1-2, automatic), tracker-miner-fs:i386 (0.14.4-0ubuntu1, automatic), libsoup2.4-1:i386 (2.40.2-0ubuntu1, automatic), libgcr-3-common:i386 (3.6.2-0ubuntu1, automatic), gnibbles:i386 (3.6.1-0ubuntu2, automatic), gnome-terminal:i386 (3.6.1-0ubuntu2), libgphoto2-2:i386 (2.4.14-2, automatic), xdg-user-dirs:i386 (0.14-0ubuntu4), liblvm2app2.2:i386 (2.02.95-5ubuntu1, automatic), printer-driver-hpijs:i386 (3.12.11-0ubuntu1, automatic), foomatic-db-engine:i386 (4.0.8-3, automatic), humanity-icon-theme:i386 (0.6.1, automatic), python3-oauthlib:i386 (0.3.4-0ubuntu1, automatic), rhythmbox-data:i386 (2.98-0ubuntu3, automatic), xserver-xorg-core:i386 (1.13.0.902-0ubuntu1, automatic), zeitgeist:i386 (0.9.5-0ubuntu1, automatic), libwavpack1:i386 (4.60.1-3, automatic), telepathy-indicator:i386 (0.3.0-0ubuntu3, automatic), libpaper-utils:i386 (1.1.24+nmu2ubuntu1, automatic), hicolor-icon-theme:i386 (0.12-1ubuntu2, automatic), gnome-user-share:i386 (3.0.4-0ubuntu1, automatic), libcolord1:i386 (0.1.23-0ubuntu3, automatic), libsmbclient:i386 (3.6.9-1ubuntu1, automatic), libcap2-bin:i386 (2.22-1.2ubuntu1, automatic), nautilus-sendto-empathy:i386 (3.6.2-0ubuntu1, automatic), pptp-linux:i386 (1.7.2-7, automatic), libmission-control-plugins0:i386 (5.13.1-0ubuntu3, automatic), gcc-4.7:i386 (4.7.2-16ubuntu1, automatic), avahi-utils:i386 (0.6.31-1ubuntu2, automatic), gsettings-desktop-schemas:i386 (3.6.1-0ubuntu1, automatic), unity-scope-gdocs:i386 (0.8daily12.12.05-0ubuntu1, automatic), libdpkg-perl:i386 (1.16.9ubuntu2, automatic), toshset:i386 (1.76-4, automatic), unity-lens-video:i386 (0.3.14daily12.12.05-0ubuntu1, automatic), network-manager-gnome:i386 (0.9.6.2+git201211052130.2d666bc-0ubuntu2, automatic), unity-scope-musicstores:i386 (6.8.1daily12.12.05-0ubuntu1, automatic), zeitgeist-core:i386 (0.9.5-0ubuntu1, automatic), gir1.2-gnomekeyring-1.0:i386 (3.6.0-1, automatic), cracklib-runtime:i386 (2.8.20-0ubuntu1, automatic), libgconf-2-4:i386 (3.2.5-0ubuntu5, automatic), libpciaccess0:i386 (0.13.1-2, automatic), libfolks25:i386 (0.8.0-1, automatic), libcanberra-gtk3-module:i386 (0.30-0ubuntu1, automatic), libpcsclite1:i386 (1.8.6-3ubuntu1, automatic), cups-ppdc:i386 (1.6.1-0ubuntu12, automatic), gir1.2-gdata-0.0:i386 (0.13.2-2, automatic), yelp-tools:i386 (3.6.1-1), fonts-tlwg-purisa:i386 (0.5.0-5, automatic), libmtp-common:i386 (1.1.5-1, automatic), plymouth-theme-ubuntu-gnome-logo:i386 (12.10.3), tcpd:i386 (7.6.q-24, automatic), glib-networking-common:i386 (2.34.2-0ubuntu1, automatic), guile-1.8-libs:i386 (1.8.8+1-8ubuntu1, automatic), libgoffice-0.8-8:i386 (0.8.17-1.2ubuntu1, automatic), libloudmouth1-0:i386 (1.4.3-8, automatic), shotwell:i386 (0.13.1-0ubuntu3), libnss-mdns:i386 (0.10-3.2build1, automatic), dnsmasq-base:i386 (2.65-1, automatic), duplicity:i386 (0.6.20-0ubuntu3, automatic), libelfg0:i386 (0.8.13-4~1, automatic), libck-connector0:i386 (0.4.5-3.1, automatic), libcogl-common:i386 (1.12.0-1, automatic), link-grammar-dictionaries-en:i386 (4.7.4-2, automatic), python3-pyatspi2:i386 (2.7.2+dfsg-0ubuntu1, automatic), printer-driver-sag-gdi:i386 (0.1-3), libproxy1-plugin-gsettings:i386 (0.4.10-0ubuntu1), libevolution:i386 (3.6.2-0ubuntu2, automatic), libdatrie1:i386 (0.2.5-3build1, automatic), libgnome-desktop-3-4:i386 (3.6.2-0ubuntu4, automatic), libnet-domain-tld-perl:i386 (1.69-1, automatic), python-defer:i386 (1.0.6-2, automatic), fontconfig:i386 (2.10.2-0ubuntu1, automatic), libdmapsharing-3.0-2:i386 (2.9.15-1ubuntu1, automatic), libgrip0:i386 (0.3.5-0ubuntu1, automatic), deja-dup:i386 (25.3-0ubuntu1), libwnck22:i386 (2.30.7-0ubuntu2, automatic), python-serial:i386 (2.5-3, automatic), libgwibber-gtk3:i386 (3.6.0-0ubuntu1, automatic), folks-common:i386 (0.8.0-1, automatic), spamc:i386 (3.3.2-4ubuntu2, automatic), libgnomekbd-common:i386 (3.6.0-0ubuntu1, automatic), appmenu-qt:i386 (0.2.6-1ubuntu1, automatic), gir1.2-gst-plugins-base-1.0:i386 (1.0.4-1, automatic), gedit-common:i386 (3.6.2-0ubuntu1, automatic), rhythmbox-mozilla:i386 (2.98-0ubuntu3, automatic), libqjson0:i386 (0.8.1-1, automatic), vbetool:i386 (1.1-3, automatic), libcairomm-1.0-1:i386 (1.10.0-1ubuntu2, automatic), libqt4-xmlpatterns:i386 (4.8.3+dfsg-0ubuntu3, automatic), gir1.2-clutter-gst-2.0:i386 (1.9.92-1build1, automatic), firefox-globalmenu:i386 (18.0~b4+build1-0ubuntu1, automatic), gir1.2-mutter-3.0:i386 (3.6.2-0ubuntu1, automatic), compiz-plugins-default:i386 (0.9.9~daily12.12.05-0ubuntu2, automatic), acl:i386 (2.2.51-8ubuntu3, automatic), software-center:i386 (5.5.3), libxfont1:i386 (1.4.5-2, automatic), python-pam:i386 (0.4.2-13ubuntu4, automatic), libsyncdaemon-1.0-1:i386 (4.1.0-0ubuntu2, automatic), libnice10:i386 (0.1.3-1, automatic), libclutter-gst-2.0-0:i386 (1.9.92-1build1, automatic), xserver-xorg-video-savage:i386 (2.3.6-0ubuntu1, automatic), libschroedinger-1.0-0:i386 (1.0.11-2, automatic), libevdocument3-4:i386 (3.6.1-1ubuntu1, automatic), python-openssl:i386 (0.13-2ubuntu3, automatic), rhythmbox-plugin-zeitgeist:i386 (2.98-0ubuntu3, automatic), xinput:i386 (1.6.0-1, automatic), gstreamer1.0-plugins-bad:i386 (1.0.3-1ubuntu1, automatic), libgtk-3-common:i386 (3.6.2-0ubuntu1, automatic), fonts-tlwg-typist:i386 (0.5.0-5, automatic), libgssdp-1.0-3:i386 (0.13.1-1, automatic), gir1.2-signon-1.0:i386 (1.7-0ubuntu1, automatic), libbrlapi0.5:i386 (4.4-6ubuntu1, automatic), libxres1:i386 (1.0.6-1, automatic), libwebkitgtk-3.0-0:i386 (1.10.2-0ubuntu1, automatic), python-gi:i386 (3.7.3-0ubuntu2, automatic), libmtdev1:i386 (1.1.2-1ubuntu1, automatic), acpid:i386 (2.0.17-1ubuntu2, automatic), simple-scan:i386 (3.6.0-0ubuntu1), libcupsppdc1:i386 (1.6.1-0ubuntu12, automatic), libjavascriptcoregtk-3.0-0:i386 (1.10.2-0ubuntu1, automatic), gir1.2-webkit-3.0:i386 (1.10.2-0ubuntu1, automatic), libvte-2.90-9:i386 (0.34.2-0ubuntu1, automatic), libtidy-0.99-0:i386 (20091223cvs-1.2, automatic), gir1.2-freedesktop:i386 (1.34.2-1, automatic), libpeas-1.0-0:i386 (1.4.0-2ubuntu4, automatic), gettext:i386 (0.18.1.1-10ubuntu1, automatic), libgbm1:i386 (9.0.1-0ubuntu1, automatic), libglibmm-2.4-1c2a:i386 (2.34.1-0ubuntu1, automatic), syslinux-legacy:i386 (3.63+dfsg-2ubuntu5, automatic), apg:i386 (2.2.3.dfsg.1-2build1, automatic), indicator-messages:i386 (12.10.6daily12.11.22-0ubuntu1, automatic), libtracker-extract-0.14-0:i386 (0.14.4-0ubuntu1, automatic), gnome-orca:i386 (3.7.2-0ubuntu1), python-markupsafe:i386 (0.15-1build3, automatic), deja-dup-backend-cloudfiles:i386 (25.3-0ubuntu1), libpam-xdg-support:i386 (0.2-0ubuntu1), firefox:i386 (18.0~b4+build1-0ubuntu1, automatic), xbitmaps:i386 (1.1.1-2, automatic), samba-common-bin:i386 (3.6.9-1ubuntu1, automatic), gstreamer1.0-plugins-base-apps:i386 (1.0.4-1), gstreamer1.0-tools:i386 (1.0.4-1, automatic), tracker-extract:i386 (0.14.4-0ubuntu1, automatic), deja-dup-backend-s3:i386 (25.3-0ubuntu1), libgee2:i386 (0.6.7-0ubuntu1, automatic), libsecret-1-0:i386 (0.12-0ubuntu1, automatic), libenca0:i386 (1.14-2, automatic), printer-driver-ptouch:i386 (1.3-4ubuntu1), libatkmm-1.6-1:i386 (2.22.6-1ubuntu2, automatic), cups-common:i386 (1.6.1-0ubuntu12, automatic), rtkit:i386 (0.10-2build1, automatic), libstartup-notification0:i386 (0.12-2, automatic), libedataserverui-3.0-4:i386 (3.6.2-0ubuntu1, automatic), rhythmbox-plugin-cdrecorder:i386 (2.98-0ubuntu3, automatic), telepathy-haze:i386 (0.6.0-1, automatic), libexempi3:i386 (2.2.0-1build1, automatic), gconf-service:i386 (3.2.5-0ubuntu5, automatic), libxxf86dga1:i386 (1.1.3-2, automatic), libfile-mimeinfo-perl:i386 (0.16-1, automatic), libcdio-cdda1:i386 (0.83-4, automatic), libhpmud0:i386 (3.12.11-0ubuntu1, automatic), libxaw7:i386 (1.0.10-2, automatic), libgdata13:i386 (0.13.2-2, automatic), gtk2-engines:i386 (2.20.2-2ubuntu1, automatic), gir1.2-ibus-1.0:i386 (1.4.2-0ubuntu1, automatic), cpp:i386 (4.7.2-1ubuntu8, automatic), swell-foop:i386 (3.6.1-0ubuntu2, automatic), libpango1.0-0:i386 (1.30.1-1ubuntu1, automatic), libubuntuoneui-3.0-1:i386 (4.1.0-0ubuntu1, automatic), libgtkhtml-4.0-common:i386 (4.6.1-0ubuntu1, automatic), libvo-amrwbenc0:i386 (0.1.2-1, automatic), python-imaging:i386 (1.1.7-4build1, automatic), librhythmbox-core6:i386 (2.98-0ubuntu3, automatic), libkpathsea6:i386 (2012.20120628-4, automatic), account-plugin-icons:i386 (0.10bzr12.12.10-0ubuntu1, automatic), xserver-xorg-input-all:i386 (7.7+1ubuntu4, automatic), fonts-tlwg-umpush:i386 (0.5.0-5, automatic), libijs-0.35:i386 (0.35-8build1, automatic), at-spi2-core:i386 (2.7.2-0ubuntu1), argyll:i386 (1.4.0-8ubuntu1, automatic), libcups2:i386 (1.6.1-0ubuntu12, automatic), libt1-5:i386 (5.1.2-3.5, automatic), gcc:i386 (4.7.2-1ubuntu8, automatic), libhunspell-1.3-0:i386 (1.3.2-4ubuntu1, automatic), gdb:i386 (7.5-0ubuntu4, automatic), libsonic0:i386 (0.1.18-0ubuntu1, automatic), libtag1-vanilla:i386 (1.8-1, automatic), libcurl3:i386 (7.28.0-3ubuntu1, automatic), eog:i386 (3.6.2-0ubuntu1), gdm:i386 (3.6.1-0ubuntu1), gcr:i386 (3.6.2-0ubuntu1), xfonts-base:i386 (1.0.3, automatic), libwebkitgtk-3.0-common:i386 (1.10.2-0ubuntu1, automatic), libavc1394-0:i386 (0.5.4-1, automatic), libdbusmenu-qt2:i386 (0.9.2-0ubuntu3, automatic), libsoundtouch0:i386 (1.7.0-2, automatic), pinyin-database:i386 (1.2.99-3, automatic), gnome-dictionary:i386 (3.6.0-0ubuntu1), gwibber-service-twitter:i386 (3.6.0-0ubuntu1, automatic), libpangomm-1.4-1:i386 (2.28.4-1ubuntu2, automatic), libqtcore4:i386 (4.8.3+dfsg-0ubuntu3, automatic), gnotski:i386 (3.6.1-0ubuntu2, automatic), libavahi-gobject0:i386 (0.6.31-1ubuntu2, automatic), gir1.2-gdesktopenums-3.0:i386 (3.6.1-0ubuntu1, automatic), libprotobuf7:i386 (2.4.1-3ubuntu1, automatic), libaccount-plugin-1.0-0:i386 (0.1.2bzr12.12.05-0ubuntu1, automatic), libwv-1.2-4:i386 (1.2.9-3, automatic), ubuntu-release-upgrader-gtk:i386 (0.192.3), gnome-disk-utility:i386 (3.6.1-1ubuntu1), geoclue-ubuntu-geoip:i386 (1.0.1-0ubuntu2, automatic), liblouis2:i386 (2.4.1-1ubuntu2, automatic), gjs:i386 (1.34.0-0ubuntu1), liblwp-protocol-https-perl:i386 (6.03-1, automatic), libgif4:i386 (4.1.6-10ubuntu1, automatic), gnome-backgrounds:i386 (3.6.1-0ubuntu1), itstool:i386 (1.2.0-0ubuntu1), gir1.2-evince-3.0:i386 (3.6.1-1ubuntu1, automatic), gir1.2-caribou-1.0:i386 (0.4.4-1ubuntu1, automatic), libgtk-3-0:i386 (3.6.2-0ubuntu1, automatic), libgdome2-0:i386 (0.8.1+debian-4.1build1, automatic), obexd-client:i386 (0.46-1ubuntu2, automatic), libgtk2.0-bin:i386 (2.24.13-0ubuntu2, automatic), python-xdg:i386 (0.24-1ubuntu3, automatic), fonts-tlwg-sawasdee:i386 (0.5.0-5, automatic), gconf-service-backend:i386 (3.2.5-0ubuntu5, automatic), fonts-tlwg-norasi:i386 (0.5.0-5, automatic), libxft2:i386 (2.3.1-1, automatic), fonts-tlwg-typo:i386 (0.5.0-5, automatic), gnome-search-tool:i386 (3.6.0-0ubuntu1), libgwibber3:i386 (3.6.0-0ubuntu1, automatic), sessioninstaller:i386 (0.20+bzr134-0ubuntu3, automatic), espeak-data:i386 (1.46.02-2ubuntu1, automatic), libdbusmenu-gtk4:i386 (12.10.2-0ubuntu1, automatic), libtelepathy-logger2:i386 (0.4.0-2, automatic), pulseaudio-module-bluetooth:i386 (2.1-0ubuntu4), libvpx1:i386 (1.1.0-1, automatic), telepathy-idle:i386 (0.1.14-1), account-plugin-identica:i386 (0.10bzr12.12.10-0ubuntu1, automatic), dictionaries-common:i386 (1.12.10, automatic), syslinux-common:i386 (4.06+dfsg-3, automatic), libgutenprint2:i386 (5.2.9-1ubuntu1, automatic), im-config:i386 (0.19ubuntu1), usb-creator-gtk:i386 (0.2.42), unattended-upgrades:i386 (0.79.3ubuntu7, automatic), libnm-glib4:i386 (0.9.6.0+git201211131441.e9e2c56-0ubuntu3, automatic), libxcb-shape0:i386 (1.8.1-2, automatic), gir1.2-dee-1.0:i386 (1.2.0daily12.12.06-0ubuntu1, automatic), libedata-cal-1.2-18:i386 (3.6.2-0ubuntu1, automatic), usb-creator-common:i386 (0.2.42, automatic), libgsf-1-common:i386 (1.14.24-0ubuntu1, automatic), libclutter-1.0-0:i386 (1.12.2-0ubuntu1, automatic), alsa-utils:i386 (1.0.25-3ubuntu4, automatic), gir1.2-telepathylogger-0.2:i386 (0.4.0-2, automatic), signon-plugin-password:i386 (8.44-0ubuntu1, automatic), gkbd-capplet:i386 (3.6.0-0ubuntu1, automatic), libxcomposite1:i386 (0.4.3-2build2, automatic), libgtk2-perl:i386 (1.244-1ubuntu1, automatic), abiword-plugin-grammar:i386 (2.9.2+svn20120603-8, automatic), libcroco3:i386 (0.6.8-1, automatic), libjbig2dec0:i386 (0.11+20120125-1ubuntu1, automatic), gnome-session-bin:i386 (3.6.2-0ubuntu2, automatic), libvte-2.90-common:i386 (0.34.2-0ubuntu1, automatic), gstreamer1.0-plugins-good:i386 (1.0.3-1ubuntu1, automatic), libtelepathy-farstream2:i386 (0.4.0-3, automatic), libgweather-common:i386 (3.6.2-0ubuntu1, automatic), libicc2:i386 (2.12+argyll1.4.0-8ubuntu1, automatic), python-smbc:i386 (1.0.13-0ubuntu4, automatic), dconf-service:i386 (0.14.1-0ubuntu1, automatic), app-install-data-partner:i386 (13.04), libgtkhtml-editor-4.0-0:i386 (4.6.1-0ubuntu1, automatic), python3-httplib2:i386 (0.7.4-2, automatic), libgme0:i386 (0.5.5-2, automatic), xserver-xorg-video-nouveau:i386 (1.0.4-0ubuntu1, automatic), libspandsp2:i386 (0.0.6~pre20-3ubuntu1, automatic), libipc-run-perl:i386 (0.92-1, automatic), gstreamer0.10-pulseaudio:i386 (0.10.31-3+nmu1ubuntu1, automatic), libtheora0:i386 (1.1.1+dfsg.1-3.1, automatic), libice6:i386 (1.0.8-2, automatic), xserver-xorg-video-vmware:i386 (12.0.2+git.e5ac80d8-0ubuntu1, automatic), update-inetd:i386 (4.43, automatic), gir1.2-wnck-3.0:i386 (3.4.4-0ubuntu2, automatic), libcogl-pango0:i386 (1.12.0-1, automatic), libaa1:i386 (1.4p5-40, automatic), fonts-liberation:i386 (1.07.2-6, automatic), avahi-autoipd:i386 (0.6.31-1ubuntu2), libnet-ip-perl:i386 (1.26-1, automatic), pulseaudio-module-x11:i386 (2.1-0ubuntu4, automatic), libqt4-sql-sqlite:i386 (4.8.3+dfsg-0ubuntu3, automatic), libgnome-bluetooth11:i386 (3.6.1-0ubuntu1, automatic), libgphoto2-l10n:i386 (2.4.14-2, automatic), wodim:i386 (1.1.11-2ubuntu3, automatic), gnome-control-center-signon:i386 (0.1.2bzr12.12.05-0ubuntu1, automatic), libthai0:i386 (0.1.18-2, automatic), ssl-cert:i386 (1.0.32, automatic), vino:i386 (3.6.2-0ubuntu1), python-dbus:i386 (1.1.1-1ubuntu2, automatic), gir1.2-pango-1.0:i386 (1.30.1-1ubuntu1, automatic), mousetweaks:i386 (3.6.0-0ubuntu2, automatic), aptdaemon:i386 (0.45+bzr883-0ubuntu1, automatic), libpython2.7:i386 (2.7.3-13ubuntu1, automatic), libgail-3-0:i386 (3.6.2-0ubuntu1, automatic), gnome-system-monitor:i386 (3.6.1-0ubuntu1), libgmime-2.6-0:i386 (2.6.12-0ubuntu1, automatic), system-config-printer-common:i386 (1.3.11+20120807-0ubuntu11, automatic), gnome-online-accounts:i386 (3.6.2-0ubuntu1, automatic), anacron:i386 (2.3-19ubuntu2), unity-lens-music:i386 (6.8.1daily12.12.05-0ubuntu1, automatic), libxml2:i386 (2.9.0+dfsg1-4, automatic), libgdict-common:i386 (3.6.0-0ubuntu1, automatic), libcanberra-gtk0:i386 (0.30-0ubuntu1, automatic), usb-modeswitch-data:i386 (20120815-2, automatic), libimobiledevice3:i386 (1.1.4-1ubuntu2, automatic), libsignon-extension1:i386 (8.44-0ubuntu1, automatic), unity-common:i386 (6.12.0daily12.12.05-0ubuntu1, automatic), libuuid-perl:i386 (0.02-5, automatic), libedata-book-1.2-15:i386 (3.6.2-0ubuntu1, automatic), libdee-1.0-4:i386 (1.2.0daily12.12.06-0ubuntu1, automatic), gir1.2-notify-0.7:i386 (0.7.5-1build1, automatic), cups:i386 (1.6.1-0ubuntu12, automatic), libgudev-1.0-0:i386 (175-0ubuntu14, automatic), libio-socket-inet6-perl:i386 (2.69-2, automatic), libsamplerate0:i386 (0.1.8-5, automatic), libdrm-nouveau2:i386 (2.4.40-1, automatic), libnet-dns-perl:i386 (0.68-1.1, automatic), account-plugin-windows-live:i386 (0.10bzr12.12.10-0ubuntu1, automatic), python-problem-report:i386 (2.7-0ubuntu2, automatic), evince:i386 (3.6.1-1ubuntu1), libpam-cap:i386 (2.22-1.2ubuntu1, automatic), libunity-protocol-private0:i386 (6.90.0daily12.12.05-0ubuntu1, automatic), libbluetooth3:i386 (4.101-0ubuntu8, automatic), libfile-desktopentry-perl:i386 (0.04-3, automatic), gnome-games-data:i386 (3.6.1-0ubuntu2, automatic), libgtksourceview-3.0-common:i386 (3.6.1-0ubuntu1, automatic), libgoa-1.0-0:i386 (3.6.2-0ubuntu1, automatic), growisofs:i386 (7.1-10build1, automatic), libjpeg-turbo8:i386 (1.2.1-0ubuntu2, automatic), libxmu6:i386 (1.1.1-1, automatic), python-boto:i386 (2.3.0-1, automatic), gnome-icon-theme-full:i386 (3.6.2-0ubuntu1), libcdparanoia0:i386 (3.10.2+debian-11, automatic), libgpm2:i386 (1.20.4-6, automatic), iagno:i386 (3.6.1-0ubuntu2, automatic), libtimezonemap1:i386 (0.3.2build1, automatic), glines:i386 (3.6.1-0ubuntu2, automatic), libasprintf-dev:i386 (0.18.1.1-10ubuntu1, automatic), media-player-info:i386 (17-1, automatic), pm-utils:i386 (1.4.1-9git1, automatic), python-piston-mini-client:i386 (0.7.3+bzr68-0ubuntu1, automatic), gir1.2-goa-1.0:i386 (3.6.2-0ubuntu1, automatic), telepathy-mission-control-5:i386 (5.13.1-0ubuntu3, automatic), libspeechd2:i386 (0.7.1-6.1ubuntu2, automatic), libqt4-sql:i386 (4.8.3+dfsg-0ubuntu3, automatic), gir1.2-gstreamer-1.0:i386 (1.0.4-1, automatic), libglib2.0-data:i386 (2.34.3-1, automatic), pulseaudio-utils:i386 (2.1-0ubuntu4, automatic), gnome-user-guide:i386 (3.6.2-0ubuntu1, automatic), account-plugin-aim:i386 (3.6.2-0ubuntu1, automatic), xdiagnose:i386 (3.3), fonts-tlwg-waree:i386 (0.5.0-5, automatic), libasound2:i386 (1.0.25-4ubuntu2, automatic), libatk1.0-data:i386 (2.7.2-0ubuntu2, automatic), libjson-glib-1.0-0:i386 (0.15.2-0ubuntu1, automatic), telepathy-logger:i386 (0.4.0-2, automatic), libwnck-3-0:i386 (3.4.4-0ubuntu2, automatic), libxpm4:i386 (3.5.10-1, automatic), libflac8:i386 (1.2.1-6build1, automatic), libimdi0:i386 (1.4.0-8ubuntu1, automatic), apturl:i386 (0.5.1ubuntu6, automatic), unity-lens-shopping:i386 (6.8.0daily12.12.05-0ubuntu1, automatic), gnome-sudoku:i386 (3.6.1-0ubuntu2, automatic), xdg-utils:i386 (1.1.0~rc1-2ubuntu6, automatic), libxrender1:i386 (0.9.7-1, automatic), gnome-icon-theme-extras:i386 (3.4.0-2ubuntu1), xinit:i386 (1.3.2-1, automatic), iputils-arping:i386 (20101006-3ubuntu1, automatic), printer-driver-pnm2ppa:i386 (1.13+nondbs-0ubuntu2), libgeis1:i386 (2.2.15daily12.12.10-0ubuntu1, automatic), python-appindicator:i386 (12.10.0-0ubuntu1, automatic), libmtp-runtime:i386 (1.1.5-1, automatic), libmessaging-menu0:i386 (12.10.6daily12.11.22-0ubuntu1, automatic), gir1.2-gnomebluetooth-1.0:i386 (3.6.1-0ubuntu1, automatic), evolution-plugins:i386 (3.6.2-0ubuntu2, automatic), libnspr4:i386 (4.9.3-1ubuntu1, automatic), libespeak1:i386 (1.46.02-2ubuntu1, automatic), x11-session-utils:i386 (7.6+2build1, automatic), libshout3:i386 (2.3.1-1ubuntu2, automatic), telepathy-gabble:i386 (0.16.1-2, automatic), libgsm1:i386 (1.0.13-4, automatic), libsync-menu1:i386 (12.10.4-0ubuntu1, automatic), sgml-base:i386 (1.26+nmu4ubuntu1, automatic), ibus-pinyin-db-android:i386 (1.4.0-1build1), libnautilus-extension1a:i386 (3.6.3-0ubuntu3, automatic), libdv4:i386 (1.0.0-6, automatic), libdvdnav4:i386 (4.2.0+20121016-1, automatic), gwibber-service-identica:i386 (3.6.0-0ubuntu1, automatic), libwbclient0:i386 (3.6.9-1ubuntu1, automatic), ubuntu-extras-keyring:i386 (2010.09.27), usb-modeswitch:i386 (1.2.3+repack0-1ubuntu3, automatic), indicator-datetime:i386 (12.10.3daily12.11.23-0ubuntu1, automatic), software-properties-common:i386 (0.92.13, automatic), python-oauth:i386 (1.0.1-3build1, automatic), nautilus-share:i386 (0.7.3-1ubuntu3), fonts-sil-padauk:i386 (2.80-1), signon-plugin-oauth2:i386 (0.14-0ubuntu1, automatic), libdevmapper-event1.02.1:i386 (1.02.74-5ubuntu1, automatic), openprinting-ppds:i386 (20120823-0ubuntu4), pcmciautils:i386 (018-8), gir1.2-xkl-1.0:i386 (5.2.1-1ubuntu2, automatic), libwps-0.2-2:i386 (0.2.7-1, automatic), printer-driver-splix:i386 (2.0.0+svn306-2ubuntu1), printer-driver-hpcups:i386 (3.12.11-0ubuntu1, automatic), libfs6:i386 (1.0.4-1, automatic), libgpod-common:i386 (0.8.2-7ubuntu1, automatic), libdvdread4:i386 (4.2.0+20121016-1ubuntu1, automatic), libqt4-xml:i386 (4.8.3+dfsg-0ubuntu3, automatic), libsoup-gnome2.4-1:i386 (2.40.2-0ubuntu1, automatic), evolution-data-server:i386 (3.6.2-0ubuntu1, automatic), python-gnomekeyring:i386 (2.32.0+dfsg-2ubuntu1, automatic), libasyncns0:i386 (0.8-4build1, automatic), gir1.2-gck-1:i386 (3.6.2-0ubuntu1, automatic), rhythmbox-plugins:i386 (2.98-0ubuntu3, automatic), libgusb2:i386 (0.1.3-5, automatic), python3-defer:i386 (1.0.6-2, automatic), libclutter-1.0-common:i386 (1.12.2-0ubuntu1, automatic), libdconf1:i386 (0.14.1-0ubuntu1, automatic), libdrm-radeon1:i386 (2.4.40-1, automatic), libxss1:i386 (1.2.2-1, automatic), libiw30:i386 (30~pre9-8ubuntu1, automatic), libgd2-xpm:i386 (2.0.36~rc1~dfsg-6.1ubuntu1, automatic), libido3-0.1-0:i386 (12.10.2-0ubuntu1, automatic), acpi-support:i386 (0.141), gconf2-common:i386 (3.2.5-0ubuntu5, automatic), libgs9:i386 (9.06~dfsg-0ubuntu4, automatic), python-ubuntu-sso-client:i386 (4.1.0-0ubuntu1, automatic), gstreamer1.0-pulseaudio:i386 (1.0.3-1ubuntu1, automatic), libappindicator1:i386 (12.10.0-0ubuntu1, automatic), session-migration:i386 (0.2, automatic), cups-bsd:i386 (1.6.1-0ubuntu12), libfontenc1:i386 (1.1.1-1, automatic), libtiff5:i386 (4.0.2-4ubuntu2, automatic), libevview3-3:i386 (3.6.1-1ubuntu1, automatic), gstreamer0.10-nice:i386 (0.1.3-1, automatic), xul-ext-ubufox:i386 (2.6-0ubuntu1, automatic), libpython3.3-dbg:i386 (3.3.0-7, automatic), libatk-adaptor:i386 (2.7.2-0ubuntu1), libhtml-form-perl:i386 (6.03-1, automatic), software-properties-gtk:i386 (0.92.13), libmimic0:i386 (1.0.4-2.1build1, automatic), libbrasero-media3-1:i386 (3.6.1-0ubuntu1, automatic), libjasper1:i386 (1.900.1-14, automatic), libqt4-network:i386 (4.8.3+dfsg-0ubuntu3, automatic), libgtop2-7:i386 (2.28.4-3, automatic), unity-lens-files:i386 (6.6.0daily12.12.05-0ubuntu1, automatic), libcrack2:i386 (2.8.20-0ubuntu1, automatic), rhythmbox-ubuntuone:i386 (4.1.0-0ubuntu1, automatic), xserver-xorg-video-neomagic:i386 (1.2.7-0ubuntu1, automatic), libusbmuxd2:i386 (1.0.8-1, automatic), yelp:i386 (3.6.2-0ubuntu1, automatic), xfonts-utils:i386 (7.7~1, automatic), fonts-cantarell:i386 (0.0.11-0ubuntu1), gnome-tweak-tool:i386 (3.6.1-1), libquvi7:i386 (0.4.1-1, automatic), libcupsfilters1:i386 (1.0.25-1, automatic), gir1.2-rb-3.0:i386 (2.98-0ubuntu3, automatic), libperl5.14:i386 (5.14.2-16, automatic), libexiv2-12:i386 (0.23-1, automatic), libcdio-paranoia1:i386 (0.83-4, automatic), gir1.2-indicate-0.7:i386 (12.10.1-0ubuntu1, automatic), python3-pkg-resources:i386 (0.6.30-0ubuntu1, automatic), libgstreamer-plugins-bad1.0-0:i386 (1.0.3-1ubuntu1, automatic), account-plugin-facebook:i386 (0.10bzr12.12.10-0ubuntu1, automatic), gir1.2-gmenu-3.0:i386 (3.6.1-0ubuntu2, automatic), wpasupplicant:i386 (1.0-3ubuntu1, automatic), xserver-xephyr:i386 (1.13.0.902-0ubuntu1, automatic), python3-brlapi:i386 (4.4-6ubuntu1, automatic), indicator-appmenu:i386 (12.10.4daily12.12.14-0ubuntu1, automatic), libcanberra0:i386 (0.30-0ubuntu1, automatic), signond:i386 (8.44-0ubuntu1, automatic), libhttp-negotiate-perl:i386 (6.00-2, automatic), libwacom2:i386 (0.6-1, automatic), libebackend-1.2-5:i386 (3.6.2-0ubuntu1, automatic), libedataserver-1.2-17:i386 (3.6.2-0ubuntu1, automatic), libmysqlclient18:i386 (5.5.28-0ubuntu3, automatic), gksu:i386 (2.0.2-6ubuntu2, automatic), libgdome2-cpp-smart0c2a:i386 (0.2.6-6build2, automatic), libdaemon0:i386 (0.14-2build1, automatic), libpam-ck-connector:i386 (0.4.5-3.1, automatic), python3-aptdaemon.gtk3widgets:i386 (0.45+bzr883-0ubuntu1, automatic), libthai-data:i386 (0.1.18-2, automatic), libxtst6:i386 (1.2.1-1, automatic), gnome-icon-theme:i386 (3.6.2-0ubuntu1, automatic), libasound2-plugins:i386 (1.0.25-2ubuntu3, automatic), python-oauthlib:i386 (0.3.4-0ubuntu1, automatic), zeitgeist-datahub:i386 (0.9.5-1ubuntu1, automatic), libxvmc1:i386 (1.0.7-1ubuntu1, automatic), libwnck-3-common:i386 (3.4.4-0ubuntu2, automatic), libhtml-format-perl:i386 (2.10-1, automatic), zip:i386 (3.0-6ubuntu1, automatic), cups-pk-helper:i386 (0.2.4-0ubuntu4, automatic), libio-pty-perl:i386 (1.08-1build3, automatic), libgdk-pixbuf2.0-0:i386 (2.26.5-0ubuntu3, automatic), python-cups:i386 (1.9.62-0ubuntu3, automatic), libgl1-mesa-dri:i386 (9.0.1-0ubuntu1, automatic), libcrypt-passwdmd5-perl:i386 (1.3-10, automatic), libgupnp-1.0-4:i386 (0.19.1-1, automatic), whoopsie:i386 (0.2.9), gnotravex:i386 (3.6.1-0ubuntu2, automatic), libavahi-client3:i386 (0.6.31-1ubuntu2, automatic), libarchive12:i386 (3.0.4-2git2, automatic), alsa-base:i386 (1.0.25+dfsg-0ubuntu3), libcaribou-common:i386 (0.4.4-1ubuntu1, automatic), gir1.2-syncmenu-0.1:i386 (12.10.4-0ubuntu1, automatic), ibus:i386 (1.4.2-0ubuntu1), libc6-dev:i386 (2.16-0ubuntu8, automatic), libqtgui4:i386 (4.8.3+dfsg-0ubuntu3, automatic), libencode-locale-perl:i386 (1.03-1, automatic), libunistring0:i386 (0.9.3-5build1, automatic), libcheese-gtk23:i386 (3.6.2-0ubuntu1, automatic), libgrail6:i386 (3.0.9daily12.12.07.1-0ubuntu1, automatic), libpurple-bin:i386 (2.10.6-0ubuntu3, automatic), libatspi2.0-0:i386 (2.7.2-0ubuntu1, automatic), gnect:i386 (3.6.1-0ubuntu2, automatic), dmz-cursor-theme:i386 (0.4.3), ttf-indic-fonts-core:i386 (0.5.11ubuntu1), libcupsimage2:i386 (1.6.1-0ubuntu12, automatic), gir1.2-upowerglib-1.0:i386 (0.9.17-1build1, automatic), libwayland0:i386 (1.0.2-0ubuntu2, automatic), poppler-data:i386 (0.4.6-2, automatic), policykit-desktop-privileges:i386 (0.12), python-configglue:i386 (1.0-1build1, automatic), liblua5.1-0:i386 (5.1.5-4, automatic), libwmf0.2-7-gtk:i386 (0.2.8.4-10.2ubuntu1), libtag1c2a:i386 (1.8-1, automatic), ghostscript:i386 (9.06~dfsg-0ubuntu4, automatic), pulseaudio-module-gconf:i386 (2.1-0ubuntu4), gir1.2-gcr-3:i386 (3.6.2-0ubuntu1, automatic), libgnome-keyring-common:i386 (3.6.0-1, automatic), librsvg2-2:i386 (2.36.4-1, automatic), libgnome-menu-3-0:i386 (3.6.1-0ubuntu2, automatic), libcairo-gobject2:i386 (1.12.8-0ubuntu4, automatic), libxcb-dri2-0:i386 (1.8.1-2, automatic), unity-lens-photos:i386 (0.9daily12.12.05-0ubuntu1, automatic), libpolkit-backend-1-0:i386 (0.105-1ubuntu1, automatic), colord:i386 (0.1.23-0ubuntu3, automatic), ibus-table:i386 (1.4.99.20121012-1), libxklavier16:i386 (5.2.1-1ubuntu2, automatic), x11-common:i386 (7.7+1ubuntu4, automatic), libsane-hpaio:i386 (3.12.11-0ubuntu1, automatic), foomatic-filters:i386 (4.0.17-1, automatic), libyajl2:i386 (2.0.4-2, automatic), gnome-terminal-data:i386 (3.6.1-0ubuntu2, automatic), libgl1-mesa-glx:i386 (9.0.1-0ubuntu1, automatic), dialog:i386 (1.1-20120215-3, automatic), ttf-wqy-microhei:i386 (0.2.0-beta-1.1), libmeanwhile1:i386 (1.0.2-4ubuntu2, automatic), libgksu2-0:i386 (2.0.13~pre1-6ubuntu1, automatic), poppler-utils:i386 (0.20.5-0ubuntu3, automatic), libmpg123-0:i386 (1.14.4-1, automatic), gstreamer0.10-plugins-base-apps:i386 (0.10.36-1.1ubuntu1), gnumeric:i386 (1.10.17-1.1ubuntu1), indicator-sound:i386 (12.10.2daily12.11.21.1-0ubuntu1, automatic), libsnmp-base:i386 (5.4.3~dfsg-2.7ubuntu1, automatic), libsysfs2:i386 (2.1.0+repack-2, automatic), libcanberra-pulse:i386 (0.30-0ubuntu1, automatic), python-pkg-resources:i386 (0.6.30-0ubuntu1, automatic), gir1.2-vte-2.90:i386 (0.34.2-0ubuntu1, automatic), xorg:i386 (7.7+1ubuntu4), libitm1:i386 (4.7.2-16ubuntu1, automatic), libclone-perl:i386 (0.31-1build4, automatic), libgpgme11:i386 (1.2.0-1.4ubuntu3, automatic), cryptsetup-bin:i386 (1.4.3-4ubuntu2, automatic), gir1.2-cogl-1.0:i386 (1.12.0-1, automatic), libindicate5:i386 (12.10.1-0ubuntu1, automatic), plymouth-theme-ubuntu-gnome-text:i386 (12.10.3), gstreamer1.0-alsa:i386 (1.0.4-1), libsgutils2-2:i386 (1.33-1build1, automatic), dconf-gsettings-backend:i386 (0.14.1-0ubuntu1, automatic), libgdict-1.0-6:i386 (3.6.0-0ubuntu1, automatic), zenity-common:i386 (3.6.0-0ubuntu1, automatic), libgweather-3-1:i386 (3.6.2-0ubuntu1, automatic), unity-scope-video-remote:i386 (0.3.10daily12.12.05-0ubuntu1, automatic), indicator-session:i386 (12.10.4-0ubuntu1, automatic), radeontool:i386 (1.6.2-1.1build1, automatic), liblink-grammar4:i386 (4.7.4-2, automatic), libzephyr4:i386 (3.0.2-2, automatic), gnome-control-center-data:i386 (3.6.3-0ubuntu9, automatic), samba-common:i386 (3.6.9-1ubuntu1, automatic), libquadmath0:i386 (4.7.2-16ubuntu1, automatic), libgtkmathview0c2a:i386 (0.8.0-8, automatic), libunity-misc4:i386 (4.0.4-0ubuntu3, automatic), libsm6:i386 (1.2.1-2, automatic), cpp-4.7:i386 (4.7.2-16ubuntu1, automatic), gnome-contacts:i386 (3.6.2-0ubuntu1), libpulse0:i386 (2.1-0ubuntu4, automatic), libhtml-tree-perl:i386 (5.02-1, automatic), brasero:i386 (3.6.1-0ubuntu1), linux-sound-base:i386 (1.0.25+dfsg-0ubuntu3, automatic), libmhash2:i386 (0.9.9.9-1.1, automatic), gnome-icon-theme-symbolic:i386 (3.6.2-0ubuntu1, automatic), libavahi-glib1:i386 (0.6.31-1ubuntu2, automatic), libappindicator3-1:i386 (12.10.0-0ubuntu1, automatic), account-plugin-google:i386 (0.10bzr12.12.10-0ubuntu1, automatic), nux-tools:i386 (4.0.0daily12.12.05-0ubuntu1, automatic), fonts-kacst:i386 (2.01+mry-7, automatic), libpulsedsp:i386 (2.1-0ubuntu4, automatic), libjte1:i386 (1.19-1build1, automatic), fonts-tibetan-machine:i386 (1.901b-4), compiz:i386 (0.9.9~daily12.12.05-0ubuntu2, automatic), libxdamage1:i386 (1.1.3-2build2, automatic), speech-dispatcher:i386 (0.7.1-6.1ubuntu2), fonts-kacst-one:i386 (5.0+svn11846-6), libxml2-utils:i386 (2.9.0+dfsg1-4, automatic), libopus0:i386 (1.0.1-0ubuntu1, automatic), gvfs:i386 (1.14.2-0ubuntu1, automatic), python-ubuntuone-client:i386 (4.1.0-0ubuntu2, automatic), patch:i386 (2.6.1-3ubuntu1, automatic), libindicator3-7:i386 (12.10.1-0ubuntu1, automatic), libmozjs185-1.0:i386 (1.8.5-1.0.0+dfsg-4, automatic), libio-socket-ssl-perl:i386 (1.76-2ubuntu1, automatic), libgtk-3-bin:i386 (3.6.2-0ubuntu1, automatic), x11-xkb-utils:i386 (7.7~1, automatic), gwibber-service-facebook:i386 (3.6.0-0ubuntu1, automatic), libcairo-perl:i386 (1.100-0ubuntu1, automatic), libwww-perl:i386 (6.04-1, automatic), ubuntu-drivers-common:i386 (0.2.73, automatic), yelp-xsl:i386 (3.6.1-1, automatic), gvfs-backends:i386 (1.14.2-0ubuntu1, automatic), libdigest-hmac-perl:i386 (1.03+dfsg-1, automatic), libemail-valid-perl:i386 (0.190-1, automatic), python-gobject-2:i386 (2.28.6-10ubuntu2, automatic), libisofs6:i386 (1.2.4-0ubuntu1, automatic), libnm-gtk-common:i386 (0.9.6.2+git201211052130.2d666bc-0ubuntu2, automatic), libopenvg1-mesa:i386 (9.0.1-0ubuntu1, automatic), gnuchess:i386 (6.0.2-1, automatic), python3-louis:i386 (2.4.1-1ubuntu2, automatic), fonts-nanum:i386 (3.020-2), gwibber:i386 (3.6.0-0ubuntu1), libvisual-0.4-0:i386 (0.4.0-5, automatic), python-apport:i386 (2.7-0ubuntu2, automatic), fonts-tlwg-kinnari:i386 (0.5.0-5, automatic), libexif12:i386 (0.6.20-3, automatic), libqt4-script:i386 (4.8.3+dfsg-0ubuntu3, automatic), libgxps2:i386 (0.2.2-2ubuntu1, automatic), dbus-x11:i386 (1.6.8-1ubuntu1, automatic), python3-speechd:i386 (0.7.1-6.1ubuntu2, automatic), libxi6:i386 (1.6.1-1, automatic), intel-gpu-tools:i386 (1.3-0ubuntu2, automatic), libvorbis0a:i386 (1.3.2-1.3, automatic), compiz-core:i386 (0.9.9~daily12.12.05-0ubuntu2, automatic), totem:i386 (3.6.3-0ubuntu2), libtracker-sparql-0.14-0:i386 (0.14.4-0ubuntu1, automatic), gnome-accessibility-themes:i386 (3.6.2-0ubuntu2, automatic), libhttp-cookies-perl:i386 (6.00-2, automatic), gir1.2-telepathyglib-0.12:i386 (0.20.1-1ubuntu1, automatic), linux-headers-generic-pae:i386 (3.7.0.7.11), liblouis-data:i386 (2.4.1-1ubuntu2, automatic), libgnome-control-center1:i386 (3.6.3-0ubuntu9, automatic), libv4lconvert0:i386 (0.8.9-1, automatic), xserver-xorg-input-synaptics:i386 (1.6.2-1ubuntu5, automatic), python-cupshelpers:i386 (1.3.11+20120807-0ubuntu11, automatic), evolution-data-server-common:i386 (3.6.2-0ubuntu1, automatic), libxp6:i386 (1.0.1-2build1), libaudio2:i386 (1.9.3-5, automatic), libhttp-message-perl:i386 (6.03-1, automatic), libxcursor1:i386 (1.1.13-1, automatic), xfonts-encodings:i386 (1.0.4-1ubuntu1, automatic), libxcb-shm0:i386 (1.8.1-2, automatic), libavahi-common3:i386 (0.6.31-1ubuntu2, automatic), python-ibus:i386 (1.4.2-0ubuntu1, automatic), binutils:i386 (2.23.1-0ubuntu5, automatic), gstreamer1.0-clutter:i386 (1.9.92-1build1, automatic), lintian:i386 (2.5.10.2ubuntu3, automatic), libdjvulibre-text:i386 (3.5.25.3-3, automatic), libxt6:i386 (1.1.3-1, automatic), gstreamer0.10-plugins-base:i386 (0.10.36-1.1ubuntu1, automatic), libhtml-tagset-perl:i386 (3.20-2, automatic), libytnef0:i386 (1.5-4build1, automatic), desktop-file-utils:i386 (0.21-0ubuntu2, automatic), libxinerama1:i386 (1.1.2-1, automatic), libzeitgeist-1.0-1:i386 (0.3.18-1ubuntu1, automatic), libaudit0:i386 (1.7.18-1ubuntu1, automatic), libxv1:i386 (1.0.7-1, automatic), indicator-power:i386 (12.10.6daily12.11.21.1-0ubuntu1, automatic), apport-gtk:i386 (2.7-0ubuntu2, automatic), libgstreamer-plugins-base0.10-0:i386 (0.10.36-1.1ubuntu1, automatic), transmission-common:i386 (2.73-1ubuntu1, automatic), xserver-xorg-video-sisusb:i386 (0.9.6-0ubuntu1, automatic), gnome-session:i386 (3.6.2-0ubuntu2, automatic), mscompress:i386 (0.3-4, automatic), ubuntu-gnome-default-settings:i386 (12.10.3), libreadline5:i386 (5.2-12, automatic), python-reportlab:i386 (2.5-1.1build2, automatic), gir1.2-coglpango-1.0:i386 (1.12.0-1, automatic), libgcc-4.7-dev:i386 (4.7.2-16ubuntu1, automatic), libprotoc7:i386 (2.4.1-3ubuntu1, automatic), printer-driver-min12xxw:i386 (0.0.9-6ubuntu2), libnatpmp1:i386 (20110808-3ubuntu2, automatic), ttf-ubuntu-font-family:i386 (0.80-0ubuntu5), librsync1:i386 (0.9.7-9, automatic), libxrandr2:i386 (1.4.0-1, automatic), libfarstream-0.1-0:i386 (0.1.2-1ubuntu1, automatic), libnet-http-perl:i386 (6.03-2, automatic), liboauth0:i386 (1.0.0-0ubuntu2, automatic), libbamf3-0:i386 (0.4.0daily12.12.05-0ubuntu2, automatic), libsecret-common:i386 (0.12-0ubuntu1, automatic), fonts-tlwg-loma:i386 (0.5.0-5, automatic), python-twisted-bin:i386 (12.2.0-1, automatic), libcurl3-nss:i386 (7.28.0-3ubuntu1, automatic), gstreamer0.10-tools:i386 (0.10.36-1ubuntu2, automatic), gir1.2-totem-plparser-1.0:i386 (3.4.3-1, automatic), appmenu-gtk3:i386 (12.10.3daily12.11.28-0ubuntu2, automatic), librsvg2-common:i386 (2.36.4-1, automatic), libavahi-core7:i386 (0.6.31-1ubuntu2, automatic), python-gtk2:i386 (2.24.0-3build1, automatic), dconf-tools:i386 (0.14.1-0ubuntu1, automatic), indicator-printers:i386 (0.1.6-0ubuntu3, automatic), libgjs0c:i386 (1.34.0-0ubuntu1, automatic), libcolord-gtk1:i386 (0.1.23-0ubuntu1, automatic), python3-problem-report:i386 (2.7-0ubuntu2, automatic), libsndfile1:i386 (1.0.25-5, automatic), libsys-hostname-long-perl:i386 (1.4-2, automatic), libaspell15:i386 (0.60.7~20110707-1build1, automatic), modemmanager:i386 (0.6.0.0.really-0ubuntu2, automatic), xserver-xorg-video-radeon:i386 (7.0.0-0ubuntu1, automatic), libgupnp-igd-1.0-4:i386 (0.2.1-2build1, automatic), libwpd-0.9-9:i386 (0.9.6-2, automatic), gir1.2-accounts-1.0:i386 (1.3-0ubuntu2, automatic), libmng1:i386 (1.0.10-3build1, automatic), kerneloops-daemon:i386 (0.12+git20090217-3ubuntu3), python-cairo:i386 (1.8.8-1ubuntu4, automatic), libgtk2.0-0:i386 (2.24.13-0ubuntu2, automatic), python-httplib2:i386 (0.7.4-2, automatic), gir1.2-peas-1.0:i386 (1.4.0-2ubuntu4, automatic), make:i386 (3.81-8.2ubuntu2, automatic), rhythmbox-plugin-magnatune:i386 (2.98-0ubuntu3), gstreamer1.0-x:i386 (1.0.4-1, automatic), libnux-4.0-common:i386 (4.0.0daily12.12.05-0ubuntu1, automatic), gnome-system-log:i386 (3.6.1-0ubuntu1), libgsf-1-114:i386 (1.14.24-0ubuntu1, automatic), example-content:i386 (46), libpolkit-agent-1-0:i386 (0.105-1ubuntu1, automatic), gsfonts:i386 (8.11+urwcyr1.0.7~pre44-4.2ubuntu1, automatic), libxkbfile1:i386 (1.0.8-1, automatic), file-roller:i386 (3.6.3-1ubuntu2), libmpc2:i386 (0.9-4build1, automatic), libmms0:i386 (0.6.2-3, automatic), libopenobex1:i386 (1.5-2build2, automatic), libspeexdsp1:i386 (1.2~rc1-7, automatic), compiz-gnome:i386 (0.9.9~daily12.12.05-0ubuntu2, automatic), libneon27-gnutls:i386 (0.29.6-3, automatic), python-zeitgeist:i386 (0.9.5-0ubuntu1, automatic), nautilus-sendto:i386 (3.6.0-0ubuntu1), libpaper1:i386 (1.1.24+nmu2ubuntu1, automatic), libiptcdata0:i386 (1.0.4-3, automatic), transmission-gtk:i386 (2.73-1ubuntu1), libltdl7:i386 (2.4.2-1.2ubuntu1, automatic), hardening-includes:i386 (2.3, automatic), libvisual-0.4-plugins:i386 (0.4.0.dfsg.1-7build1, automatic), gnome-shell-common:i386 (3.6.2-0ubuntu4, automatic), libgdata-common:i386 (0.13.2-2, automatic), empathy-common:i386 (3.6.2-0ubuntu1, automatic), ssh-askpass-gnome:i386 (6.1p1-2), xserver-xorg-video-cirrus:i386 (1.5.1-0ubuntu2, automatic), libpoppler-glib8:i386 (0.20.5-0ubuntu3, automatic), xserver-xorg-video-intel:i386 (2.20.16-0ubuntu1, automatic), hwdata:i386 (0.234-1, automatic), hplip-data:i386 (3.12.11-0ubuntu1, automatic), python-gobject:i386 (3.7.3-0ubuntu2, automatic), libllvm3.1:i386 (3.1-2ubuntu1, automatic), libdotconf1.0:i386 (1.0.13-3build1, automatic), libpwquality1:i386 (1.1.1-1, automatic), ghostscript-cups:i386 (9.06~dfsg-0ubuntu4, automatic), libogg0:i386 (1.3.0-4, automatic), libibus-1.0-0:i386 (1.4.2-0ubuntu1, automatic), mutter:i386 (3.6.2-0ubuntu1), libfaad2:i386 (2.7-8, automatic), gnomine:i386 (3.6.1-0ubuntu2, automatic), libyaml-tiny-perl:i386 (1.51-1, automatic), consolekit:i386 (0.4.5-3.1, automatic)
End-Date: 2012-12-23  16:11:57

```

So I think I need to rinse-n-repeat but the next time I'll try:

```
sudo apt-get install --no-install-recommends ubuntu-gnome-desktop
```

It's all good, clean fun :D

Edit: The "Ubuntu" boot option is displayed after just installing 'ubuntu-gnome-desktop' but booting into "Ubuntu" looks like crap:

[ATTACH]229061[/ATTACH]

And the crash has to do with plymouth:

[ATTACH]229062[/ATTACH]

---

### Post by kansasnoob on 2012-12-24
OK, I did another install with the mini.iso and this time I typed this command after completing the CLI install and booting to tty:

```
sudo apt-get install --no-install-recommends ubuntu-gnome-desktop
```

That worked much better. Without the "--no-install-recommends" I'd ended up with 'unity', 'compiz', and a lot of Ubuntu packages :(

But even doing it this way is far from perfect because you end up with no 'totem', no 'abiword', no 'cheese', no 'epiphany-browser', etc, etc.

You do get 'nautilus' though and 'gnome-terminal' is there so you can easily install 'synaptic' and parse the missing recommends :)

I might post a query at the mailing list later, but I first want to check some other things :guitar:

---

### Post by kansasnoob on 2012-12-24
I hate the way this looks but I did post at the mailing list:

[https://lists.launchpad.net/ubuntu-gnome/msg00249.html](https://lists.launchpad.net/ubuntu-gnome/msg00249.html)

I need to go back to "mail" school :(

It sucks to be old!

---

### Post by jbicha on 2012-12-24
I think the email would look better on that page if you could find the  option to send the email as plain text instead of as HTML.

---

### Post by kansasnoob on 2012-12-25
I just did another test with the same mini.iso, but per Jeremy's suggestion I began with:

```
sudo apt-get install gnome-shell
```

But I was still going to get some unity and compiz stuff when I installed 'ubuntu-gnome-desktop' so I just said no and then ran:

```
sudo apt-get install gnome-session
```

Yeah! That seemed to work because then installing 'ubuntu-gnome-desktop' seemed to be unity and compiz free :)

Now I need to rinse-n-repeat again but this time I'll try installing 'gnome-session' before installing 'gnome-shell'. Maybe 'gnome-session' will just automatically pull in 'gnome-shell' :confused:

It's all good, clean fun ;)

---

### Post by kansasnoob on 2012-12-25
Eerrrm, I decided this would be easier to work on in a chroot, so I have a fresh CLI install from the mini.iso and when I run "apt-get install gnome-shell" in a chroot I get:

```
The following NEW packages will be installed:
  acl apg aspell aspell-en at-spi2-core binutils bluez brasero brasero-cdrkit
  brasero-common colord consolekit cpp cpp-4.7 cracklib-runtime cups-pk-helper
  dbus-x11 dconf-gsettings-backend dconf-service dconf-tools
  desktop-file-utils dictionaries-common dnsmasq-base dvd+rw-tools enchant
  evolution-data-server evolution-data-server-common folks-common fontconfig
  fontconfig-config gconf-service gconf-service-backend gconf2 gconf2-common
  gcr gdm genisoimage gir1.2-accountsservice-1.0 gir1.2-atk-1.0
  gir1.2-caribou-1.0 gir1.2-clutter-1.0 gir1.2-cogl-1.0 gir1.2-coglpango-1.0
  gir1.2-freedesktop gir1.2-gck-1 gir1.2-gconf-2.0 gir1.2-gcr-3
  gir1.2-gdesktopenums-3.0 gir1.2-gdkpixbuf-2.0 gir1.2-gkbd-3.0
  gir1.2-gmenu-3.0 gir1.2-gnomebluetooth-1.0 gir1.2-gnomedesktop-3.0
  gir1.2-gtk-3.0 gir1.2-ibus-1.0 gir1.2-json-1.0 gir1.2-mutter-3.0
  gir1.2-networkmanager-1.0 gir1.2-pango-1.0 gir1.2-polkit-1.0 gir1.2-soup-2.4
  gir1.2-telepathyglib-0.12 gir1.2-telepathylogger-0.2 gir1.2-upowerglib-1.0
  gir1.2-xkl-1.0 gjs gkbd-capplet glib-networking glib-networking-common
  glib-networking-services gnome-accessibility-themes gnome-bluetooth
  gnome-contacts gnome-control-center gnome-control-center-data
  gnome-desktop3-data gnome-icon-theme gnome-icon-theme-full
  gnome-icon-theme-symbolic gnome-keyring gnome-menus gnome-online-accounts
  gnome-session gnome-session-bin gnome-session-common gnome-settings-daemon
  gnome-shell gnome-shell-common gnome-themes-standard gnome-user-guide
  gnome-user-share growisofs gsettings-desktop-schemas
  gstreamer0.10-pulseaudio gstreamer1.0-plugins-base gstreamer1.0-plugins-good
  gstreamer1.0-x gtk2-engines gtk2-engines-pixbuf gvfs gvfs-backends
  gvfs-common gvfs-daemons gvfs-libs hicolor-icon-theme hunspell-en-us hwdata
  indicator-application iputils-arping libaa1 libappindicator3-1 libarchive12
  libasound2 libasound2-plugins libaspell15 libasyncns0 libatasmart4
  libatk-bridge2.0-0 libatk1.0-0 libatk1.0-data libatspi2.0-0 libaudit0
  libavahi-client3 libavahi-common-data libavahi-common3 libavahi-glib1
  libavc1394-0 libbluetooth3 libbrasero-media3-1 libburn4 libcaca0
  libcairo-gobject2 libcairo2 libcamel-1.2-40 libcanberra-gtk-module
  libcanberra-gtk0 libcanberra-gtk3-0 libcanberra-gtk3-module
  libcanberra-pulse libcanberra0 libcap2-bin libcaribou-common libcaribou0
  libcdio-cdda1 libcdio-paranoia1 libcdio13 libcdparanoia0 libck-connector0
  libclutter-1.0-0 libclutter-1.0-common libcogl-common libcogl-pango0
  libcogl11 libcolord1 libcrack2 libcroco3 libcups2 libcurl3-nss libdatrie1
  libdbusmenu-glib4 libdbusmenu-gtk3-4 libdconf1 libdee-1.0-4 libdrm-intel1
  libdrm-nouveau2 libdrm-radeon1 libdv4 libebackend-1.2-5 libebook-1.2-14
  libecal-1.2-15 libedata-book-1.2-15 libedata-cal-1.2-18
  libedataserver-1.2-17 libegl1-mesa libegl1-mesa-drivers libelfg0
  libenchant1c2a libexempi3 libexif12 libflac8 libfolks-eds25
  libfolks-telepathy25 libfolks25 libfontconfig1 libfontenc1 libgail-3-0
  libgbm1 libgck-1-0 libgconf-2-4 libgcr-3-1 libgcr-3-common libgd2-xpm
  libgdata-common libgdata13 libgdk-pixbuf2.0-0 libgdk-pixbuf2.0-common
  libgee2 libgeoclue0 libgjs0c libgl1-mesa-dri libgl1-mesa-glx libglapi-mesa
  libglib2.0-bin libglib2.0-data libglu1-mesa libgmime-2.6-0 libgmp10
  libgnome-bluetooth11 libgnome-control-center1 libgnome-desktop-3-4
  libgnome-keyring-common libgnome-keyring0 libgnome-menu-3-0
  libgnomekbd-common libgnomekbd8 libgoa-1.0-0 libgoa-1.0-common libgpgme11
  libgphoto2-2 libgphoto2-l10n libgphoto2-port0 libgpm2
  libgstreamer-plugins-base0.10-0 libgstreamer-plugins-base1.0-0
  libgstreamer0.10-0 libgstreamer1.0-0 libgtk-3-0 libgtk-3-bin libgtk-3-common
  libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libgtop2-7 libgtop2-common
  libgudev-1.0-0 libgusb2 libgweather-3-1 libgweather-common libhunspell-1.3-0
  libibus-1.0-0 libical0 libice6 libicu48 libiec61883-0 libieee1284-3
  libimobiledevice3 libindicator3-7 libisofs6 libjack-jackd2-0 libjasper1
  libjavascriptcoregtk-3.0-0 libjbig0 libjpeg-turbo8 libjpeg8
  libjson-glib-1.0-0 libjte1 liblcms2-2 libllvm3.1 libltdl7 liblua5.1-0
  libmetacity-private0a libmission-control-plugins0 libmozjs185-1.0 libmpc2
  libmpfr4 libmtdev1 libmutter0a libnautilus-extension1a
  libnetfilter-conntrack3 libnettle4 libnl-route-3-200 libnm-glib-vpn1
  libnm-glib4 libnm-gtk-common libnm-gtk0 libnm-util2 libnotify4 libnspr4
  libnss3 liboauth0 libogg0 libopenobex1 libopenvg1-mesa liborc-0.4-0
  libpam-cap libpam-ck-connector libpam-gnome-keyring libpango1.0-0
  libpciaccess0 libpcsclite1 libpixman-1-0 libplist1 libpolkit-agent-1-0
  libpolkit-backend-1-0 libproxy1 libpth20 libpulse-mainloop-glib0 libpulse0
  libpulsedsp libpwquality1 libquvi-scripts libquvi7 libraw1394-11
  libreadline5 librest-0.7-0 librsvg2-2 librsvg2-common libsamplerate0 libsane
  libsane-common libsecret-1-0 libsecret-common libshout3 libsm6 libsmbclient
  libsndfile1 libsoup-gnome2.4-1 libsoup2.4-1 libspeex1 libspeexdsp1
  libstartup-notification0 libsysfs2 libtag1-vanilla libtag1c2a libtalloc2
  libtdb1 libtelepathy-glib0 libtelepathy-logger2 libthai-data libthai0
  libtheora0 libtiff5 libtotem-plparser17 libtxc-dxtn-s2tc0 libudisks2-0
  **[COLOR="Red"]libunity-protocol-private0 libunity9[/COLOR]** libupower-glib1 libusbmuxd2 libv4l-0
  libv4lconvert0 libvisual-0.4-0 libvisual-0.4-plugins libvorbis0a
  libvorbisenc2 libvorbisfile3 libvpx1 libwacom-common libwacom2 libwavpack1
  libwayland0 libwbclient0 libwebkitgtk-3.0-0 libwebkitgtk-3.0-common libwrap0
  libx11-xcb1 libx86-1 libxatracker1 libxaw7 libxcb-dri2-0 libxcb-glx0
  libxcb-render0 libxcb-shape0 libxcb-shm0 libxcb-util0 libxcb-xfixes0
  libxcomposite1 libxcursor1 libxdamage1 libxfixes3 libxfont1 libxft2 libxi6
  libxinerama1 libxkbfile1 libxklavier16 libxml2 libxmu6 libxpm4 libxrandr2
  libxrender1 libxslt1.1 libxt6 libxtst6 libxv1 libxvmc1 libxxf86dga1
  libxxf86vm1 libyelp0 libzeitgeist-1.0-1 mesa-utils metacity metacity-common
  mobile-broadband-provider-info modemmanager mousetweaks mutter-common
  nautilus nautilus-data network-manager network-manager-gnome
  network-manager-pptp network-manager-pptp-gnome notification-daemon
  obex-data-server obexd-client pm-utils policykit-1 policykit-1-gnome
  pptp-linux pulseaudio pulseaudio-module-x11 pulseaudio-utils python-dbus
  python-dbus-dev python-gi python-gobject python-gobject-2 python-xdg
  python-zeitgeist rtkit session-migration sgml-base shared-mime-info
  sound-theme-freedesktop tcpd telepathy-mission-control-5 ttf-dejavu-core
  ubuntu-system-service udisks2 unzip upower usb-modeswitch
  usb-modeswitch-data usbmuxd vbetool wamerican wodim wpasupplicant x11-common
  x11-utils x11-xkb-utils x11-xserver-utils xfonts-base xfonts-encodings
  xfonts-utils xml-core xserver-common xserver-xephyr xserver-xorg
  xserver-xorg-core xserver-xorg-input-all xserver-xorg-input-evdev
  xserver-xorg-input-mouse xserver-xorg-input-synaptics
  xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-all
  xserver-xorg-video-ati xserver-xorg-video-cirrus xserver-xorg-video-fbdev
  xserver-xorg-video-intel xserver-xorg-video-mach64 xserver-xorg-video-mga
  xserver-xorg-video-modesetting xserver-xorg-video-neomagic
  xserver-xorg-video-nouveau xserver-xorg-video-openchrome
  xserver-xorg-video-qxl xserver-xorg-video-r128 xserver-xorg-video-radeon
  xserver-xorg-video-s3 xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident
  xserver-xorg-video-vesa xserver-xorg-video-vmware yelp yelp-xsl zeitgeist
  zeitgeist-core zeitgeist-datahub zenity zenity-common

```

Just a couple of libunity* pkgs **[COLOR="Red"](highlighted)[/COLOR]** so maybe that's normal?

So I'll go ahead with that one :)

EDIT: As I look closer I can see that 'gnome-session' is being installed so maybe I just didn't see it working in pure tty .......... that is difficult for me because I'm blind as a bat and I generally use screen magnification when I can to look at text more closely ........... can't do that in tty unless I'm using a VM.

---

### Post by kansasnoob on 2012-12-25
Ouch, things did not go that well in the chroot:

```
Errors were encountered while processing:
 bluez
 gnome-bluetooth
 gnome-shell
 gnome-user-share
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Thinking cap time :-k

---

### Post by kansasnoob on 2012-12-25
It looks like that error is going to be hard to resolve but I still wanted to see what happened if I installed 'ubuntu-gnome-desktop' and here it is:

```
The following NEW packages will be installed:
  abiword abiword-common abiword-plugin-grammar abiword-plugin-mathview account-plugin-aim account-plugin-facebook account-plugin-flickr
  account-plugin-google account-plugin-icons account-plugin-identica account-plugin-jabber account-plugin-salut account-plugin-twitter
  account-plugin-windows-live account-plugin-yahoo acpi-support acpid aisleriot alsa-base alsa-utils anacron app-install-data
  app-install-data-partner apport apport-gtk apport-symptoms aptdaemon aptdaemon-data apturl apturl-common argyll avahi-autoipd avahi-daemon baobab
  bc bluez-alsa bluez-cups bluez-gstreamer brltty cheese cheese-common cryptsetup-bin cups cups-bsd cups-client cups-common cups-filters cups-ppdc
  dc deja-dup deja-dup-backend-cloudfiles deja-dup-backend-gvfs deja-dup-backend-s3 dialog diffstat dmz-cursor-theme doc-base duplicity empathy
  empathy-common eog epiphany-browser epiphany-browser-data espeak-data evince evince-common evolution evolution-common evolution-plugins
  example-content file-roller fonts-cantarell fonts-freefont-ttf fonts-kacst fonts-kacst-one fonts-khmeros-core fonts-lao fonts-liberation
  fonts-lklug-sinhala fonts-lyx fonts-nanum fonts-sil-abyssinica fonts-sil-padauk fonts-takao-pgothic fonts-thai-tlwg fonts-tibetan-machine
  fonts-tlwg-garuda fonts-tlwg-kinnari fonts-tlwg-loma fonts-tlwg-mono fonts-tlwg-norasi fonts-tlwg-purisa fonts-tlwg-sawasdee fonts-tlwg-typewriter
  fonts-tlwg-typist fonts-tlwg-typo fonts-tlwg-umpush fonts-tlwg-waree foomatic-db-compressed-ppds foomatic-db-engine foomatic-filters gcalctool gcc
  gcc-4.7 gdb gedit gedit-common gettext ghostscript ghostscript-cups ghostscript-x gir1.2-accounts-1.0 gir1.2-atspi-2.0 gir1.2-clutter-gst-2.0
  gir1.2-dbusmenu-glib-0.4 gir1.2-dee-1.0 gir1.2-evince-3.0 gir1.2-gnomekeyring-1.0 gir1.2-gst-plugins-base-1.0 gir1.2-gstreamer-1.0
  gir1.2-gtkclutter-1.0 gir1.2-gtksource-3.0 gir1.2-gudev-1.0 gir1.2-indicate-0.7 gir1.2-javascriptcoregtk-3.0 gir1.2-messagingmenu-1.0
  gir1.2-notify-0.7 gir1.2-peas-1.0 gir1.2-rb-3.0 gir1.2-signon-1.0 gir1.2-syncmenu-0.1 gir1.2-totem-1.0 gir1.2-totem-plparser-1.0
  **[COLOR="Red"]gir1.2-ubuntuoneui-3.0 gir1.2-unity-5.0[/COLOR]** gir1.2-vte-2.90 gir1.2-webkit-3.0 gir1.2-wnck-3.0 gksu glchess glines gnect gnibbles gnobots2
  gnome-backgrounds gnome-color-manager gnome-control-center-signon gnome-desktop-data gnome-dictionary gnome-disk-utility gnome-font-viewer
  gnome-games gnome-games-data gnome-games-extra-data gnome-icon-theme-extras gnome-mahjongg gnome-media gnome-orca gnome-power-manager
  gnome-screensaver gnome-screenshot gnome-search-tool gnome-session-canberra gnome-sudoku gnome-sushi gnome-system-log gnome-system-monitor
  gnome-terminal gnome-terminal-data gnome-tweak-tool gnome-video-effects gnomine gnotravex gnotski gnuchess gnuchess-book gnumeric gnumeric-common
  gnumeric-doc gsfonts gstreamer0.10-alsa gstreamer0.10-gconf gstreamer0.10-nice gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps
  gstreamer0.10-plugins-good gstreamer0.10-tools gstreamer0.10-x gstreamer1.0-alsa gstreamer1.0-clutter gstreamer1.0-plugins-bad
  gstreamer1.0-plugins-base-apps gstreamer1.0-pulseaudio gstreamer1.0-tools gtali gucharmap guile-1.8-libs gvfs-bin gvfs-fuse gwibber
  gwibber-service gwibber-service-facebook gwibber-service-identica gwibber-service-twitter hardening-includes hpijs hplip hplip-data
  humanity-icon-theme iagno ibus ibus-gtk ibus-gtk3 ibus-pinyin ibus-pinyin-db-android ibus-pinyin-db-open-phrase ibus-table im-config inputattach
  intel-gpu-tools intltool-debian itstool kerneloops-daemon libabiword-2.9 libaccount-plugin-1.0-0 libaccounts-glib0 libaccounts-qt1
  libappindicator1 libapt-pkg-perl libarchive-zip-perl libart-2.0-2 libasprintf-dev libass4 libatk-adaptor libatkmm-1.6-1 libaudio2 libavahi-core7
  libavahi-gobject0 libbrlapi0.5 libc-dev-bin libc6-dev libcairo-perl libcairomm-1.0-1 libcheese-gtk23 libcheese7 libclone-perl libclutter-gst-1.0-0
  libclutter-gst-2.0-0 libclutter-gtk-1.0-0 libcolamd2.7.1 libcolord-gtk1 libcrypt-passwdmd5-perl libcryptsetup4 libcupscgi1 libcupsfilters1
  libcupsimage2 libcupsmime1 libcupsppdc1 libcurl3 libdaemon0 libdbusmenu-gtk4 libdca0 libdevmapper-event1.02.1 libdigest-hmac-perl
  libdjvulibre-text libdjvulibre21 libdmapsharing-3.0-2 libdotconf1.0 libdpkg-perl libdvdnav4 libdvdread4 libedataserverui-3.0-4 libemail-valid-perl
  libenca0 libencode-locale-perl liberror-perl libespeak1 libevdocument3-4 libevent-2.0-5 libevolution libevview3-3 libexiv2-12 libfaad2
  libfarstream-0.1-0 libfile-basedir-perl libfile-copy-recursive-perl libfile-desktopentry-perl libfile-fcntllock-perl libfile-listing-perl
  libfile-mimeinfo-perl libflite1 libfont-afm-perl libfontembed1 libframe6 libfs6 libgail-common libgail18 libgcc-4.7-dev libgdict-1.0-6
  libgdict-common libgdome2-0 libgdome2-cpp-smart0c2a libgeis1 libgettextpo-dev libgettextpo0 libgexiv2-1 libgif4 libgksu2-0 libglib-perl
  libglibmm-2.4-1c2a libgme0 libgnome-media-profiles-3.0-0 libgoffice-0.8-8 libgoffice-0.8-8-common libgomp1 libgpod-common libgpod4 libgrail6
  libgrip0 libgs9 libgs9-common libgsf-1-114 libgsf-1-common libgsm1 libgssdp-1.0-3 libgstreamer-plugins-bad1.0-0 libgtk2-perl libgtkhtml-4.0-0
  libgtkhtml-4.0-common libgtkhtml-editor-4.0-0 libgtkmathview0c2a libgtkmm-3.0-1 libgtksourceview-3.0-0 libgtksourceview-3.0-common libgtkspell-3-0
  libgucharmap-2-90-7 libgupnp-1.0-4 libgupnp-igd-1.0-4 libgutenprint2 libgwibber-gtk3 libgwibber3 libgxps2 libhpmud0 libhtml-form-perl
  libhtml-format-perl libhtml-parser-perl libhtml-tagset-perl libhtml-tree-perl libhttp-cookies-perl libhttp-daemon-perl libhttp-date-perl
  libhttp-message-perl libhttp-negotiate-perl libicc2 libido3-0.1-0 libijs-0.35 libimdi0 libindicate5 libindicator7 libio-pty-perl
  libio-socket-inet6-perl libio-socket-ssl-perl libipc-run-perl libiptcdata0 libitm1 libiw30 libjbig2dec0 libjs-jquery libkpathsea6 liblcms1
  liblink-grammar4 liblircclient0 libloudmouth1-0 liblouis-data liblouis2 liblvm2app2.2 liblwp-mediatypes-perl liblwp-protocol-https-perl
  libmail-spf-perl libmailtools-perl libmeanwhile1 libmessaging-menu0 libmhash2 libmimic0 libminiupnpc8 libmms0 libmng1 libmodplug1 libmpg123-0
  libmtp-common libmtp-runtime libmtp9 libmusicbrainz5-0 libmysqlclient18 libnatpmp1 libneon27-gnutls libnet-dns-perl libnet-domain-tld-perl
  libnet-http-perl libnet-ip-perl libnet-ssleay-perl libnetaddr-ip-perl libnice10 libnotify-bin libnss-mdns libopencc1 libopus0 libots0
  libpam-xdg-support libpanel-applet-4-0 libpango-perl libpangomm-1.4-1 libpaper-utils libpaper1 libpeas-1.0-0 libpeas-common libperl5.14
  libpoppler-glib8 libpoppler28 libportaudio2 libprotobuf7 libprotoc7 libproxy1-plugin-gsettings libproxy1-plugin-networkmanager libpst4
  libpurple-bin libpurple0 libpython2.7 libqjson0 libqpdf8 libqt4-dbus libqt4-declarative libqt4-network libqt4-script libqt4-sql libqt4-sql-mysql
  libqt4-sql-sqlite libqt4-xml libqt4-xmlpatterns libqtcore4 libqtgui4 libqtwebkit4 libquadmath0 libraptor2-0 librasqal3 libraw5 librdf0
  librhythmbox-core6 librsync1 libsane-hpaio libschroedinger-1.0-0 libsensors4 libsgutils2-2 libsignon-extension1 libsignon-glib1
  libsignon-plugins-common1 libsignon-qt1 libsnmp-base libsnmp15 libsocket6-perl libsonic0 libsoundtouch0 libspandsp2 libspectre1 libspeechd2
  libsync-menu1 libsyncdaemon-1.0-1 libsys-hostname-long-perl libt1-5 libtelepathy-farstream2 libtidy-0.99-0 libtotem0 libtracker-extract-0.14-0
  libtracker-miner-0.14-0 libtracker-sparql-0.14-0 libubuntuoneui-3.0-1 libunistring0 liburi-perl libutempter0 libuuid-perl libvo-aacenc0
  libvo-amrwbenc0 libvte-2.90-9 libvte-2.90-common libwhoopsie0 libwmf0.2-7 libwmf0.2-7-gtk libwnck-3-0 libwnck-3-common libwpd-0.9-9 libwpg-0.2-2
  libwps-0.2-2 libwv-1.2-4 libwww-perl libwww-robotrules-perl libxml2-utils libxp6 libxres1 libxss1 libyajl2 libyaml-tiny-perl libytnef0 libzbar0
  libzephyr4 lightsoff link-grammar-dictionaries-en lintian linux-headers-generic-pae linux-libc-dev linux-sound-base lp-solve make manpages-dev
  mcp-account-manager-uoa media-player-info mscompress mtools mutter mysql-common nautilus-sendto nautilus-sendto-empathy nautilus-share oneconf
  openprinting-ppds patch patchutils pcmciautils pinyin-database pkg-config plymouth-label plymouth-theme-ubuntu-gnome-logo
  plymouth-theme-ubuntu-gnome-text policykit-desktop-privileges poppler-data poppler-utils printer-driver-c2esp printer-driver-foo2zjs
  printer-driver-gutenprint printer-driver-hpcups printer-driver-hpijs printer-driver-min12xxw printer-driver-pnm2ppa printer-driver-postscript-hp
  printer-driver-ptouch printer-driver-pxljr printer-driver-sag-gdi printer-driver-splix protobuf-compiler pulseaudio-module-bluetooth
  pulseaudio-module-gconf python-appindicator python-apport python-aptdaemon python-aptdaemon.gtk3widgets python-boto python-cairo python-cloudfiles
  python-configglue python-crypto python-cups python-debtagshw python-defer python-dirspec python-gi-cairo python-gst0.10 python-gtk2
  python-httplib2 python-ibus python-imaging python-libxml2 python-lxml python-mako python-markupsafe python-notify python-oauth python-oauthlib
  python-openssl python-pam python-pexpect python-piston-mini-client python-pkg-resources python-problem-report python-protobuf python-pyinotify
  python-renderpm python-reportlab python-reportlab-accel python-serial python-simplejson python-twisted-bin python-twisted-core
  python-twisted-names python-twisted-web python-ubuntu-sso-client **[COLOR="Red"]python-ubuntuone-client[/COLOR]** python-ubuntuone-storageprotocol python-zope.interface
  python3-apport python3-aptdaemon python3-aptdaemon.gtk3widgets python3-aptdaemon.pkcompat python3-brlapi python3-cairo python3-chardet
  python3-debian python3-defer python3-louis python3-pkg-resources python3-problem-report python3-pyatspi2 python3-six python3-software-properties
  python3-speechd python3-xkit qdbus qpdf quadrapassel radeontool re2c rfkill rhythmbox rhythmbox-data rhythmbox-mozilla rhythmbox-plugin-cdrecorder
  rhythmbox-plugin-magnatune rhythmbox-plugin-zeitgeist rhythmbox-plugins rhythmbox-ubuntuone samba-common samba-common-bin sane-utils seahorse
  sessioninstaller shotwell signon-keyring-extension signon-plugin-oauth2 signon-plugin-password signon-ui signond simple-scan smbclient
  software-center software-center-aptdaemon-plugins software-properties-common software-properties-gtk spamassassin spamc speech-dispatcher
  ssh-askpass-gnome ssl-cert swell-foop syslinux syslinux-common syslinux-legacy telepathy-gabble telepathy-haze telepathy-idle telepathy-indicator
  telepathy-logger telepathy-salut toshset totem totem-common totem-plugins tracker tracker-extract tracker-gui tracker-miner-fs tracker-utils
  transmission-common transmission-gtk ttf-indic-fonts-core ttf-punjabi-fonts ttf-ubuntu-font-family ttf-wqy-microhei ubuntu-drivers-common
  ubuntu-extras-keyring ubuntu-gnome-default-settings ubuntu-gnome-desktop ubuntu-release-upgrader-gtk ubuntu-sso-client **[COLOR="Red"]ubuntuone-client[/COLOR]** udisks
  unattended-upgrades **[COLOR="Red"]unity-lens-gwibber[/COLOR]** update-inetd update-manager update-notifier update-notifier-common usb-creator-common usb-creator-gtk vino
  whoopsie wireless-tools x11-apps x11-session-utils x11-xfs-utils xbitmaps xdg-user-dirs xdg-user-dirs-gtk xdg-utils xdiagnose xfonts-scalable
  xinit xinput xorg xorg-docs-core xsltproc xterm yelp-tools zip

```

You'll see there that I highlighted several unity and ubuntu-one pkgs :confused:

---

### Post by ronacc on 2012-12-25
they just won't let us be rid of unity altogether :lolflag:

---

### Post by kansasnoob on 2012-12-25
Well it's time to see what happens when I reboot but I'm not optimistic:

```
root@lance-desktop:/# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
7 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up bluez (4.101-0ubuntu8) ...
runlevel:/var/run/utmp: No such file or directory
reload: Unknown instance: 
invoke-rc.d: initscript dbus, action "force-reload" failed.
runlevel:/var/run/utmp: No such file or directory
start: Job failed to start
invoke-rc.d: initscript bluetooth, action "start" failed.
dpkg: error processing bluez (--configure):
 subprocess installed post-installation script returned error exit status 1
/bin/df: ‘/run/lock’: No such file or directory
                                               /bin/df: ‘/run/shm’: No such file or directory
                                                                                             /bin/df: ‘/run/user’: No such file or directory
                                                                                                                                            dpkg: dependency problems prevent configuration of bluez-alsa:i386:
 bluez-alsa:i386 depends on bluez; however:
  Package bluez is not configured yet.

dpkg: error processing bluez-alsa:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bluez-gstreamer:
 bluez-gstreamer depends on bluez; however:
  Package bluez is not configured yet.

dpkg: error processing bluez-gstreamer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-bluetooth:
 gnome-bluetooth depends on bluez (>= 4.36); however:
  Package bluez is not configured yet.

dpkg: error processing gnome-bluetooth (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-shell:
 gnome-shell depends on gnome-bluetooth (>= 3.0.0); however:
  Package gnome-bluetooth is not configured yet.

dpkg: error processing gnome-shell (--configure):
 dependency probNo apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                                              No apport report written because MaxReports is reached already
                                                                                                                                            No apport report written because MaxReports is reached already
                                                    No apport report written because MaxReports is reached already
                                                                                                                  lems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-user-share:
 gnome-user-share depends on gnome-bluetooth; however:
  Package gnome-bluetooth is not configured yet.

dpkg: error processing gnome-user-share (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-gnome-desktop:
 ubuntu-gnome-desktop depends on gnome-shell; however:
  Package gnome-shell is not configured yet.
 ubuntu-gnome-desktop depends on gnome-user-share; however:
  Package gnome-user-share is not configured yet.

dpkg: error processing ubuntu-gnome-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 bluez
 bluez-alsa:i386
 bluez-gstreamer
 gnome-bluetooth
 gnome-shell
 gnome-user-share
 ubuntu-gnome-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

That said I did just have to redo my chroot script so there could be a problem there :(

---

### Post by kansasnoob on 2012-12-25
Well she booted OK and things were easily resolved:

```
lance@lance-desktop:~$ sudo apt-get -f install
[sudo] password for lance: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
7 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up bluez (4.101-0ubuntu8) ...
Setting up bluez-alsa:i386 (4.101-0ubuntu8) ...
Setting up bluez-gstreamer (4.101-0ubuntu8) ...
Setting up gnome-bluetooth (3.6.1-0ubuntu1) ...
Setting up gnome-shell (3.6.2-0ubuntu4) ...
Setting up gnome-user-share (3.0.4-0ubuntu1) ...
Setting up ubuntu-gnome-desktop (0.6) ...
```

So it looks like I was just being anal retentive about those small bits of ubuntu-one and unity ;)

Now I need to do one last test .......... later!

Step #1: Perform a CLI install via mini.iso and when complete boot to tty as expected.

Step #2: Login and run:

```
sudo apt-get install gnome-shell
```

Step #3: When that command quits running also run:

```
sudo apt-get install ubuntu-gnome-desktop
```

NOTE: the screen may go blank while running either command in a tty that way so you'll need to briefly tap the Esc button to display the tty again. DO NOT ABORT just because the screen goes blank!

Step #4: When that is complete boot into your new Ubuntu GNOME Remix.

It looks fairly good to me. I'm particularly amazed at how fast Nautilus is now at copying files, like I have a stored .mozilla that's over 1 GB and it takes under 2 minutes :D

You can install any OS with a fork and a spoon :lolflag:

---

### Post by jbicha on 2012-12-25
I believe the libunity dependency is essential for apps that want to add Unity integration.

The Ubuntu One libraries are pulled in because we explicitly include the Ubuntu One Music Store in Rhythmbox, but I think we can drop that since "Ubuntu One Music Store" is easy to find in Software Center.

I consider gwibber-service recommending unity-lens-gwibber to be a bug.

You might be interested in [http://people.ubuntu.com/~jbicha/germinate-output/desktop](http://people.ubuntu.com/~jbicha/germinate-output/desktop) . I generated that by running
```
germinate -s ubuntu-gnome.raring -d raring -c main,restricted,universe -S http://people.ubuntu.com/~jbicha/seeds/
```

Once we're official, that would show up at [http://people.canonical.com/~ubuntu-archive/germinate-output/](http://people.canonical.com/~ubuntu-archive/germinate-output/)

---

### Post by ronacc on 2012-12-25
tried to install the mini iso on my amd64 box. It hangs as soon as the install starts no matter if you chose install or command line install . The cd drive light comes on for about 30 or so seconds then goes out , the screen then blanks and and nothing , it seems like the kernel is active because alt>sysreq>b will reboot the machine .

---

### Post by kansasnoob on 2012-12-26
> **ronacc said:**
> tried to install the mini iso on my amd64 box. It hangs as soon as the install starts no matter if you chose install or command line install . The cd drive light comes on for about 30 or so seconds then goes out , the screen then blanks and and nothing , it seems like the kernel is active because alt>sysreq>b will reboot the machine .

I've been testing i386 here. My Intel Atom 230 w/2GB of RAM will run amd64 but I've always found that i386 manages RAM more prudently and just runs better overall for me, so there could be a bug in the amd64 image that I'm not aware of.

---

### Post by Harry33 on 2012-12-26
To get rid of libunity9 you have to remove the package nautilus too.
You cannot get rid of all of the nautilus stuff (= libnautilus) however, because also evince and fole-roller depends on than library.

However, you can get rid of the package libunity-protocol-private0 by downgrading the package libunity9 to the version 5.12.0. (at that time those two packages were in one).

---

### Post by kansasnoob on 2012-12-26
I'm actually using this mini.iso install right now and it's working great. I've only installed 'firefox', 'synaptic', and 'gufw' so far, and I changed the cursor theme to DMZ White, but that's it.

Over the past few weeks I've been comparing performance between Ubuntu Quantal which uses Compiz+llvmpipe, a couple versions of Cinnamon (Mint and Snowlinux) which uses it's own fork of Mutter (Muffin), and the Ubuntu GNOME Remix with Mutter itself. And on this low end hardware Mutter is the hands down winner :D

I'm just dying to see how GNOME's Mutter+llvmpipe "classic-mode" performs, but I know that's months away. That aside I'm actually amazed at just how intuitive Gnome Shell actually is, I'd just spent very little time with it until recently. It seems to work equally well for a mouse-centric user and for a keyboard-centric user :D

---

### Post by ronacc on 2012-12-26
> **kansasnoob said:**
> I've been testing i386 here. My Intel Atom 230 w/2GB of RAM will run amd64 but I've always found that i386 manages RAM more prudently and just runs better overall for me, so there could be a bug in the amd64 image that I'm not aware of.

do you know what kernel the mini iso is running ? none of the 3.6 0r 3.7 kernels will boot on my machine . I couldn't boot raring with any thing later than the 3.5-7 kernel from quantal until  I installed the 3.8rc1 .

---

### Post by sgage on 2012-12-26
> **kansasnoob said:**
> Well she booted OK and things were easily resolved:

```
lance@lance-desktop:~$ sudo apt-get -f install
[sudo] password for lance: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
7 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up bluez (4.101-0ubuntu8) ...
Setting up bluez-alsa:i386 (4.101-0ubuntu8) ...
Setting up bluez-gstreamer (4.101-0ubuntu8) ...
Setting up gnome-bluetooth (3.6.1-0ubuntu1) ...
Setting up gnome-shell (3.6.2-0ubuntu4) ...
Setting up gnome-user-share (3.0.4-0ubuntu1) ...
Setting up ubuntu-gnome-desktop (0.6) ...
```

So it looks like I was just being anal retentive about those small bits of ubuntu-one and unity ;)

Now I need to do one last test .......... later!

Step #1: Perform a CLI install via mini.iso and when complete boot to tty as expected.

Step #2: Login and run:

```
sudo apt-get install gnome-shell
```

Step #3: When that command quits running also run:

```
sudo apt-get install ubuntu-gnome-desktop
```

NOTE: the screen may go blank while running either command in a tty that way so you'll need to briefly tap the Esc button to display the tty again. DO NOT ABORT just because the screen goes blank!

Step #4: When that is complete boot into your new Ubuntu GNOME Remix.

It looks fairly good to me. I'm particularly amazed at how fast Nautilus is now at copying files, like I have a stored .mozilla that's over 1 GB and it takes under 2 minutes :D

You can install any OS with a fork and a spoon :lolflag:

This worked for me. The only glitch is that the network icon in the top bar has a little 'x' in it, and it declares that my Wired connection is 'unmanaged'. However, the connection is working just fine. Anyone know how I can fix it?

Other than that, this mini->UGR installation is working fine...

---

### Post by kansasnoob on 2012-12-26
> **ronacc said:**
> do you know what kernel the mini iso is running ? none of the 3.6 0r 3.7 kernels will boot on my machine . I couldn't boot raring with any thing later than the 3.5-7 kernel from quantal until  I installed the 3.8rc1 .

It's 3.7.0-7-generic.

---

### Post by kansasnoob on 2012-12-26
> **sgage said:**
> This worked for me. The only glitch is that the network icon in the top bar has a little 'x' in it, and it declares that my Wired connection is 'unmanaged'. However, the connection is working just fine. Anyone know how I can fix it?

Other than that, this mini->UGR installation is working fine...

Same here, I just chalked it up to early dev borked artwork :)

---

### Post by sgage on 2012-12-26
> **kansasnoob said:**
> Same here, I just chalked it up to early dev borked artwork :)

Normally I would to, but usually when that 'x' is there is says 'disconnected' - I've never seen 'unmanaged' before, and wonder if some piece of plumbing wasn't brought in by u-g-r.

But hey, as long as it works... :-)

---

### Post by zika on 2012-12-26
Isn't it unmanaged if You take control over it through ifupdown by entering appropriate lines in /etc/network/interfaces and/or in NM config file...?
It was like that since couple of releases ago...
At my place it is umnanaged (almost) all the time...

---

### Post by grahammechanical on 2012-12-26
> **sgage said:**
> Normally I would to, but usually when that 'x' is there is says 'disconnected' - I've never seen 'unmanaged' before, and wonder if some piece of plumbing wasn't brought in by u-g-r.

But hey, as long as it works... :-)

I guess it means that the wired network is unmanaged by Network Manager which does not need or use the interfaces file. I think that putting anything in /etc/network/interfaces except 

> # interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

will interfere with Network manager.

I do not have this issue on my Gnome Remix. Try seeing what is in the interfaces file.

Regards.

---

### Post by sgage on 2012-12-26
> **grahammechanical said:**
> I guess it means that the wired network is unmanaged by Network Manager which does not need or use the interfaces file. I think that putting anything in /etc/network/interfaces except 



will interfere with Network manager.

I do not have this issue on my Gnome Remix. Try seeing what is in the interfaces file.

Regards.

Ah, my interfaces file had, in addition to the lines you mentioned, the following:

# The primary network interface
auto eth0
iface eth0 inet dhcp

I commented it out, rebooted, and no more little 'x' in the icon. Live and learn!

Thanks for the tip...

---

### Post by kansasnoob on 2012-12-26
> **sgage said:**
> Ah, my interfaces file had, in addition to the lines you mentioned, the following:

# The primary network interface
auto eth0
iface eth0 inet dhcp

I commented it out, rebooted, and no more little 'x' in the icon. Live and learn!

Thanks for the tip...

Ditto. I wonder if this is just a mini.iso thing?

---

### Post by sgage on 2012-12-26
> **kansasnoob said:**
> Ditto. I wonder if this is just a mini.iso thing?

I expect it is - the mini.iso isn't counting on any particular DE being installed with its Network Managers and such, and is not worrying about any indicators in some panel...

I seem to have anthropomorphized the mini.iso. I really shouldn't - she hates when I do that... :KS

---

### Post by zika on 2012-12-26
> **grahammechanical said:**
> I guess it means that the wired network is unmanaged by Network Manager which does not need or use the interfaces file. I think that putting anything in /etc/network/interfaces except 



will interfere with Network manager.

I do not have this issue on my Gnome Remix. Try seeing what is in the interfaces file.

Regards.It might but it doesn't have to, depending of ifupdown settings in NM config file...

---

### Post by mc4man on 2012-12-29
> **grahammechanical said:**
> I guess it means that the wired network is unmanaged by Network Manager which does not need or use the interfaces file. I think that putting anything in /etc/network/interfaces except 



will interfere with Network manager.

I do not have this issue on my Gnome Remix. Try seeing what is in the interfaces file.

Regards.
Here from the mini.iso install, - while I set up wireless to do the install afterwards it was as seen 'unmanaged'.
Even though wireless would work the g-c-c panel showed nothing & was basically worthless, certainly if wanting to connect to another wireless access.

Best fixed here by - 
sudo nano /etc/NetworkManager/NetworkManager.conf
and editing false to true

[ifupdown]
managed=[COLOR="Blue"]true[/COLOR]

Then 
sudo /etc/init.d/network-manager restart

brought back as expected

---

### Post by jbicha on 2013-01-01
> **sgage said:**
> I tried to use the IsoBuild script on a daily build of Raring, but no joy. Is there a fairly recent build of UGR available somewhere?

I think the build script works for amd64, it's i386 that needs work.

EDIT: And I think it's fixed for i386 too now.

EDIT2: Well I'm having some trouble actually booting the images so that needs more work too.

---

### Post by sgage on 2013-01-02
> **jbicha said:**
> I think the build script works for amd64, it's i386 that needs work.

EDIT: And I think it's fixed for i386 too now.

EDIT2: Well I'm having some trouble actually booting the images so that needs more work too.

Please let us know when it's working - I'll test it here...

---

### Post by kansasnoob on 2013-01-02
> **sgage said:**
> Please let us know when it's working - I'll test it here...

+1!

But @ Jeremy, take your time and enjoy the new year :D

---

### Post by sgage on 2013-01-02
> **kansasnoob said:**
> +1!

But @ Jeremy, take your time and enjoy the new year :D

I just had a successful run of the iso-build script, made a USB with unetbootin, installed UGR, and here I am, coming to you from today's UGR...   :KS

PS - I built the 64-bit version, haven't tried 32-bit version yet.

---

### Post by Mr.JJ on 2013-01-04
> **mc4man said:**
> Here from the mini.iso install, ......
.........brought back as expected

Does your screenshot show a headphone icon (on the panel) alongside the volume icon? Is it a new addition? If so, thats great. Gnome guys are really doing wonderful things. Is it only visible when you connect a headphone?

---

### Post by Stinger on 2013-02-14
> **jbicha said:**
> There is a bug in the build script which means it currently doesn't build on Raring. When we figure that out, we can publish a Raring Alpha or monthly milestone.

Bump.
Just curious, did you manage to eliminate the bug in the build script, cause I haven't seen any release yet ?

---

### Post by sgage on 2013-02-16
> **Stinger said:**
> Bump.
Just curious, did you manage to eliminate the bug in the build script, cause I haven't seen any release yet ?

I just successfully ran the script with today's build. In fact, I'm coming to you from a fresh install of Raring UGR...

If you burn the iso to a USB key with unetbootin, be advised when you try to boot it to use the menu items that say 'Ubuntu Gnome Remix' on them, or it won't boot.

Other than that, it's all good.  :KS

---

### Post by Mr.JJ on 2013-02-17
If its all good and fine (the bugs sorted out etc.) can we expect an alpha/beta release soon?

---

### Post by smartboyhw on 2013-02-17
> **Mr.JJ said:**
> If its all good and fine (the bugs sorted out etc.) can we expect an alpha/beta release soon?

I think we should expect an beta, but only according to the [Ubuntu Raring Ringtail Release Schedule  ]("https://wiki.ubuntu.com/RaringRingtail/ReleaseSchedule")and I think jbicha would not have any issues doing that.

---

### Post by Mr.JJ on 2013-02-18
> **smartboyhw said:**
> I think we should expect an beta, but only according to the [Ubuntu Raring Ringtail Release Schedule  ]("https://wiki.ubuntu.com/RaringRingtail/ReleaseSchedule")and I think jbicha would not have any issues doing that.

In my opinion, it will be better if we have a release as soon as possible (and not wait till RR beta schedule) for testing purposes. Considering the immature/nascent state of the project and that we not yet have a release this cycle.

---

### Post by smartboyhw on 2013-02-18
> **Mr.JJ said:**
> In my opinion, it will be better if we have a release as soon as possible (and not wait till RR beta schedule) for testing purposes. Considering the immature/nascent state of the project and that we not yet have a release this cycle.

If you want a release a.s.a.p. build your own daily:P Also Beta 1 is not far away I think...

---

### Post by Mr.JJ on 2013-02-18
> **smartboyhw said:**
> If you want a release a.s.a.p. build your own daily:P Also Beta 1 is not far away I think...

Don't be silly. I am using 13.04 with ubuntu-gnome-desktop installed (essentially UGR). 

Go read again what I said. And beta is still a month away from now.

---

### Post by Stinger on 2013-02-18
> **Mr.JJ said:**
> In my opinion, it will be better if we have a release as soon as possible (and not wait till RR beta schedule) for testing purposes. Considering the immature/nascent state of the project and that we not yet have a release this cycle.

+1 for that 
I would like to help testing the prebuild images like I did with the Quantal ones.

> **smartboyhw said:**
> If you want a release a.s.a.p. build your own daily:P Also Beta 1 is not far away I think...

If it comes to "build your own daily images" well not for me, find another testpilot. ;)

---

### Post by sgage on 2013-02-18
> **Stinger said:**
> +1 for that 
I would like to help testing the prebuild images like I did with the Quantal ones.



If it comes to "build your own daily images" well not for me, find another testpilot. ;)

It's really not that hard to build a UGR image - you simply download the daily live CD and run the iso-build script against it, and an hour later you have a UGR iso.

---

### Post by ronacc on 2013-02-18
> **sgage said:**
> It's really not that hard to build a UGR image - you simply download the daily live CD and run the iso-build script against it, and an hour later you have a UGR iso.

link to the build script please .

---

### Post by sgage on 2013-02-18
> **ronacc said:**
> link to the build script please .

First, install bzr and friends:

```
sudo apt-get install bzr debootstrap squashfs-tools genisoimage lzma
```

Download the latest raring daily live build.

Now you can get the script:

```
bzr branch lp:~ubuntu-gnome-dev/+junk/iso-build-script
```

Then cd to iso-build-script, and run the script (I'm assuming the 64-bit raring iso is on the Desktop, adjust accordingly).

```
./livecd-script.sh customize amd64 ../Desktop/raring-desktop-amd64.iso
```

After about an hour, you should have a freshly baked quantal-ubuntu-gnome-"architecture (amd64/i386)"-YYYYMMDD.iso in the iso-build-script directory.

To get latest version of the script:

```
bzr pull
```

If you've run the script before, do this before running it again:

```
./livecd-script.sh clean amd64
```

Everything was working fine as of yesterday's script and daily raring.

Good luck! :KS

---

### Post by ronacc on 2013-02-18
thanks I'll give it a whirl .

---

### Post by ronacc on 2013-02-19
yesterdays try built but booted to a blank screen , could get to a term with ctrl>alt>F1 and poked around abit , couldn't really see why the desktop didn't come up . trying another build today .

---

### Post by ronacc on 2013-02-19
well today it booted to a multi hued blue background , top does not show gdm to be running . lsmod shows the nouveau driver to be in use which works well with my video card .

---

### Post by sgage on 2013-02-19
> **ronacc said:**
> well today it booted to a multi hued blue background , top does not show gdm to be running . lsmod shows the nouveau driver to be in use which works well with my video card .

What did you use to make a boot device? If you used unetbootin, you will see two full sets of menu items in the initial screen - pick from the lower ones that have 'Ubuntu Gnome' in them. I had the same problem as you when booting from the upper ones...

---

### Post by ronacc on 2013-02-19
I used k3b to burn it to a dvd , I only saw one set of menu Items , I chose "try without installing" , I'll try unetbootin and see what I get .

---

### Post by sgage on 2013-02-19
> **ronacc said:**
> I used k3b to burn it to a dvd , I only saw one set of menu Items , I chose "try without installing" , I'll try unetbootin and see what I get .

Raring seems to be picky about its boot setup. Give unetbootin a try. Like I said, I saw two entire sets of boot options in the initial menu. The items from the top (first) set gave me results like what you saw. When I tried the 'Install Ubuntu Gnome" (something like that - I don't remember the exact wording) down below it worked perfectly.

---

### Post by ronacc on 2013-02-19
the problem is my test box not the .iso , I tried the dvd in my "WORK" box and it booted to desktop just fine , I'm going to get a different MB for my test box I've just had too much grief with the current one .

---

### Post by sgage on 2013-02-19
> **ronacc said:**
> the problem is my test box not the .iso , I tried the dvd in my "WORK" box and it booted to desktop just fine , I'm going to get a different MB for my test box I've just had too much grief with the current one .

Sorry your test computer is sick, but glad you got the UGR iso to build. :KS

---

### Post by ronacc on 2013-02-19
it isn't really sick its been been a problem since I built it . I normaly use MSI mobo's this is the first ( and last ) gigabyte I've tried . Its not so much that there is anything "wrong" with it, it's just too picky to coexist peacefully around here .

---

