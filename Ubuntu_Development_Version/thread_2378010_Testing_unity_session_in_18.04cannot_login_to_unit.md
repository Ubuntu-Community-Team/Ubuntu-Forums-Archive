---
title: "Testing unity session in 18.04/cannot login to unity session"
date: 2017-11-19
forum: Ubuntu Development Version
---

### Post by monkeybrain20122 on 2017-11-19
I think this happens after some updates of the Unity stuffs on Friday. I can no longer login to unity session on one of my machines. 

I tried both ubuntu and [ventrical's Ubuntu-unity-edition]("http://people.ubuntu.com/~twocamels/?_ga=2.149497846.1161564998.1510407443-1546152944.1510407443") iso.

On ubuntu default login to both gnome sessions work from GDM before installing unity-session. After installing unity-session (system fully up to date) login to gnome sessions from GDM still works. There is a unity option, click it goes to the unity desktop but immediately switches backed to the GDM login screen.

 On ubuntu-unity  login takes me to the unity desktop and then it jumps right back to lightdm. Right after fresh install from iso it worked fine, problem only happened after I did an update and upgrade (with proposed enabled), the system is otherwise vanilla from the iso.

I think this is hardware related since it works with no issue on another laptop. The problem only happens on the  older Dell Latititude E5510. This is some info about the hardware

processors 4 xintel core i5 cpu m460 @2.53 GHZ
RAM 7.6 g
graphic card intel Ironlake mobile

Not sure what info is needed for some diagnostic. Thanks.

---

### Post by monkeybrain20122 on 2017-11-19
the culprit is among these, login problem appeared only after these upgrades (on unity remix)
```

The following NEW packages will be installed:
  e2fsprogs-l10n fonts-smc-anjalioldlipi fonts-smc-chilanka fonts-smc-dyuthi
  fonts-smc-karumbi fonts-smc-keraleeyam fonts-smc-manjari fonts-smc-meera
  fonts-smc-rachana fonts-smc-raghumalayalamsans fonts-smc-suruma
  fonts-smc-uroob libdata-dump-perl libicu60 libtry-tiny-perl
  linux-headers-4.13.0-17 linux-headers-4.13.0-17-generic
  linux-image-4.13.0-17-generic linux-image-extra-4.13.0-17-generic
The following packages have been kept back:
  debconf debconf-i18n
The following packages will be upgraded:
  apparmor brltty bsdutils dbus dbus-user-session dbus-x11 dconf-cli
  dconf-gsettings-backend dconf-service e2fslibs e2fsprogs
  evolution-data-server evolution-data-server-common fdisk fonts-freefont-ttf
  fonts-liberation fonts-opensymbol fonts-smc geoip-database gir1.2-dee-1.0
  gir1.2-gtk-3.0 gir1.2-javascriptcoregtk-4.0 gir1.2-pango-1.0
  gir1.2-webkit2-4.0 gtk-update-icon-cache imagemagick imagemagick-6-common
  imagemagick-6.q16 info install-info iso-codes krb5-locales libapparmor-perl
  libapparmor1 libapt-pkg-perl libblkid1 libboost-date-time1.65.1
  libboost-filesystem1.65.1 libboost-iostreams1.65.1 libboost-system1.65.1
  libboost-thread1.65.1 libbrlapi0.6 libcairo-perl libcamel-1.2-60
  libcdio-cdda2 libcdio-paranoia2 libcdio16 libcdr-0.1-1 libclone-perl
  libcolumbus1-common libcolumbus1v5 libcomerr2 libdbus-1-3 libdconf1
  libdee-1.0-4 libe-book-0.1-1 libebackend-1.2-10 libebook-1.2-19
  libebook-contacts-1.2-2 libecal-1.2-19 libedata-book-1.2-25
  libedata-cal-1.2-28 libedataserver-1.2-22 libedataserverui-1.2-1
  libegl1-mesa libfdisk1 libgail-3-0 libgbm1 libgcrypt20 libgl1-mesa-dri
  libgl1-mesa-glx libglapi-mesa libgles2-mesa libgmp10 libgphoto2-6
  libgphoto2-l10n libgphoto2-port12 libgsettings-qt1 libgssapi-krb5-2
  libgtk-3-0 libgtk-3-bin libgtk-3-common libharfbuzz-icu0 libharfbuzz0b
  libical2 libjavascriptcoregtk-4.0-18 libk5crypto3 libkpathsea6 libkrb5-3
  libkrb5support0 libldb1 libmagickcore-6.q16-3 libmagickcore-6.q16-3-extra
  libmagickwand-6.q16-3 libmount1 libmspub-0.1-1 libpango-1.0-0
  libpangocairo-1.0-0 libpangoft2-1.0-0 libpangoxft-1.0-0 libperl5.26
  libphonenumber7 libpython3-stdlib libqt5core5a libqt5dbus5 libqt5gui5
  libqt5network5 libqt5sql5 libqt5sql5-sqlite libqt5widgets5
  libreoffice-avmedia-backend-gstreamer libreoffice-base-core libreoffice-calc
  libreoffice-common libreoffice-core libreoffice-draw libreoffice-gnome
  libreoffice-gtk3 libreoffice-help-en-us libreoffice-impress libreoffice-math
  libreoffice-ogltrans libreoffice-pdfimport libreoffice-style-breeze
  libreoffice-style-elementary libreoffice-style-galaxy
  libreoffice-style-tango libreoffice-writer libsmartcols1 libsmbclient
  libsqlite3-0 libss2 libssl1.0.0 libtag1v5 libtag1v5-vanilla
  libtracker-sparql-2.0-0 libuuid1 libvisio-0.1-1 libwayland-egl1-mesa
  libwbclient0 libwebkit2gtk-4.0-37 libwww-perl libxatracker2
  libxml-libxml-perl libxml2 linux-generic linux-headers-generic
  linux-image-generic mount openssh-client openssl perl perl-base
  perl-modules-5.26 python3 python3-brlapi python3-minimal python3-pil
  python3-pkg-resources python3-pyatspi python3-uno qtchooser samba-libs snapd
  uno-libs3 ure util-linux uuid-runtime xbrlapi
169 upgraded, 19 newly installed, 0 to remove and 2 not upgraded.
```

---

### Post by Chanath on 2017-11-19
No problem whatsoever in login into in lightdm.

---

### Post by DogMatix on 2017-11-19
Not seeing this issue either with Unity only edition logging in with lightdm. Intel graphics. However proposed is off.

---

### Post by mc4man on 2017-11-19
> **monkeybrain20122 said:**
> the culprit is among these, login problem appeared only after these upgrades (on unity remix)

Wholesale upgrading from proposed is guaranteed to break things, don't know why people do that. (current ex. librubberband rename.
Using selectively can be useful.

In this case (apparent hardware issue) I'd start over & upgrade fully (not proposed), set up unity, whatever.
Then enable proposed, upgrade kernel, see..
If still good upgrade mesa, see
If still good upgrade the dbus packages, ect.

---

### Post by ventrical on 2017-11-19
Works like a dream on all my bare metal installs (proposed -off).

Just a note @ all -you might want to install notify-osd. I hope to update the .ISO sometime this week.

regards..

---

### Post by monkeybrain20122 on 2017-11-19
> **ventrical said:**
> Works like a dream on all my bare metal installs (proposed -off).

Just a note @ all -you might want to install notify-osd. I hope to update the .ISO sometime this week.

regards..

I think proposed is the culprit (works when fully up to date without proposed) and also it only affects one machine,-- both bare metal, it works without issue on the Toshiba. Will try mc4man's idea of testing package by package but chances are things may get updated when I get around to reinstall OS tomorrow.

---

