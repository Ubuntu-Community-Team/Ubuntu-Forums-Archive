---
title: "What should I add to kde-core?"
date: 2007-01-17
forum: The Cafe
---

### Post by Steveire on 2007-01-17
I've done a ground-up install of edgy, starting off with a base install from the mini.iso (None of that server stuff).

Funny thing was openoffice was part of the basic command line system, so I removed that.
```

sudo aptitude purge openoffice.org-core mozilla-firefox-locale-en-gb thunderbird-locale-en-gb language-pack-gnome-en language-pack-gnome-en-base python-uno openoffice.org-writer openoffice.org-help-en-us openoffice.org-common openoffice.org-style-default openoffice.org-thesaurus-en-us language-support-en openoffice.org-l10n-common openoffice.org-l10n-en-gb openoffice.org-l10n-en-za

```

Then I ran the mother of all aptitude commands to install everything I wanted at once. Some programs are in their own command because they ask the user questions. After that's done you can walk away from it and let it rip through. When it's finished there's no updating it or anything. It already has the latest from the repos. Also it takes just over 2GB, and it's really zippy.

```

sudo aptitude install localepurge postfix && sudo aptitude install x-window-system kde-core kde-guidance-powermanager amarok kaffeine kile kpdf kword akregator katapult kview kjots kate-plugins konq-plugins ipython python-tk kmix konversation msttcorefonts build-essential flashplugin-nonfree usplash kdmtheme kubuntu-artwork-usplash vim-python subversion kolourpaint ksnapshot ksvg karbon kxmleditor k3b gnuplot python-gnuplot python-scipy python-mechanize python-matplotlib python-reportlab foomatic-db-hpijs kcheckgmail pdfjam pdftk kooka libxine-extracodecs kig ksokoban digikam kasablanca python-pmw kplato kftpgrabber ksplash-engine-moodin opera w32codecs libdvdcss2 knetworkmanager

```

I'd like to know what else I should consider installing to get the benefits that come with kubuntu-desktop. For example, the volume keys on my laptop don't work and konqueror does not show me thumbnail of pdf/ps/dvi files. I did this with feisty last week and had the same issues. I kinda thought it was caused by using a development branch. I installed the package kubuntu-default settings, but that didn't help. I don't want to do that now, because I had to fix it after it had finished. I also removed my .kde folder, allowing it to be regenerated, but no joy from that either. I have installed the package hotkey-setup, but it has not done the magic for me. Here's what I don't have of kubuntu-desktop. If you recognise anything useful used at the system level, do tell me, but remember I'm going for minimal here...

```

stephen@flea:~$ sudo aptitude install kubuntu-desktop
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following NEW packages will be automatically installed:
  acpi-support adept adept-batch adept-common adept-installer adept-manager
  adept-notifier adept-updater anacron apmd app-install-data avahi-daemon
  bc bluez-cups bluez-passkey-gnome bluez-pin bluez-utils bogofilter
  bogofilter-bdb bogofilter-common brltty bsh cupsys
  cupsys-driver-gutenprint dc diveintopython doc-base docbook-xml
  example-content finger flac foo2zjs foomatic-filters-ppds fortune-mod
  fortunes-min fping gcc-3.3-base gettext gij gij-4.1 gs-esp
  gtk2-engines-gtk-qt gwenview hpijs-ppds hplip hplip-data
  hwdb-client-common hwdb-client-kde intltool-debian iso-codes karm
  kaudiocreator kbstate kcron kde-guidance kde-icons-mono
  kde-systemsettings kdeadmin-kfile-plugins kdebluetooth
  kdegraphics-kfile-plugins kdemultimedia-kfile-plugins
  kdenetwork-filesharing kdenetwork-kfile-plugins kdepim-kresources
  kdepim-wizards kdnssd keep kio-apt kio-locate kitchensync kmag kmailcvt
  kmilo kmousetool kmplayer-base kmplayer-konq-plugins knetworkconf knode
  knotes kontact kopete korganizer kpf kppp krdc krfb krita krita-data kscd
  kscreensaver kscreensaver-xsavers ksystemlog ktorrent
  kubuntu-default-settings kubuntu-docs kubuntu-konqueror-shortcuts
  kwin-style-crystal landscape-client language-selector-common
  language-selector-qt laptop-mode-tools lftp libao2 libapm1 libavahi-core4
  libbluetooth2 libbrlapi1 libcupsimage2 libcurl3-gnutls libdaemon0
  libenchant1c2a libgcj-bc libglade2-0 libglib1.2 libgmp3c2 libgsl0
  libgutenprint2 libhsqldb-java libjasper-runtime libjaxp1.2-java
  libjline-java libkpimexchange1 liblockdev1 libmail-sendmail-perl
  libmdbtools libnotify1 libopenobex-1.0-0 libpoppler1-qt libpythonize0
  libqt-perl libqt4-core libqt4-gui libqt4-qt3support libqt4-sql librecode0
  librsync1 libscim8c2a libscrollkeeper0 libservlet2.3-java libsexy2
  libskim0 libslp1 libsmokeqt1 libsqlite0 libstdc++5 libtdb1 libuniconf4.2
  libwnck-common libwnck18 libwvstreams4.2-base libwvstreams4.2-extras
  libxalan2-java libxerces2-java libxplc0.3.13 libxres1 libxt-java
  linux-headers-2.6.17-10 linux-headers-2.6.17-10-generic
  linux-headers-generic min12xxw notification-daemon openoffice.org
  openoffice.org-base openoffice.org-calc openoffice.org-common
  openoffice.org-core openoffice.org-draw openoffice.org-impress
  openoffice.org-java-common openoffice.org-kde openoffice.org-math
  openoffice.org-style-crystal openoffice.org-style-default
  openoffice.org-style-hicontrast openoffice.org-style-industrial
  openoffice.org-writer pnm2ppa po-debconf powermanagement-interface
  powermgmt-base powernowd pykdeextensions python-apt python-elementtree
  python-qt4 python-uno qca-tls qobex qt4-qtconfig radeontool rdiff-backup
  readahead samba-common scim-qtimm screen scrollkeeper sdparm sgml-data
  skim slocate smartdimmer smbclient speedcrunch toshset ttf-arabeyes
  ttf-arphic-ukai ttf-arphic-uming ttf-baekmuk ttf-bengali-fonts
  ttf-bitstream-vera ttf-devanagari-fonts ttf-freefont ttf-gentium
  ttf-gujarati-fonts ttf-indic-fonts ttf-kannada-fonts ttf-kochi-gothic
  ttf-kochi-mincho ttf-lao ttf-malayalam-fonts ttf-mgopen ttf-oriya-fonts
  ttf-punjabi-fonts ttf-tamil-fonts ttf-telugu-fonts ttf-thai-tlwg vbetool
  vorbis-tools wlassistant wvdial xcursor-themes xkeyboard-config xli
  xscreensaver xscreensaver-data xscreensaver-gl
The following NEW packages will be installed:
  acpi-support adept adept-batch adept-common adept-installer adept-manager
  adept-notifier adept-updater anacron apmd app-install-data
  apt-index-watcher avahi-daemon bc bluez-cups bluez-passkey-gnome
  bluez-pin bluez-utils bogofilter bogofilter-bdb bogofilter-common brltty
  bsh cupsys cupsys-driver-gutenprint dc debtags diveintopython doc-base
  docbook-xml example-content finger flac foo2zjs foomatic-filters-ppds
  fortune-mod fortunes-min fping gcc-3.3-base gettext gij gij-4.1 gs-esp
  gtk2-engines-gtk-qt gwenview hpijs-ppds hplip hplip-data
  hwdb-client-common hwdb-client-kde intltool-debian iso-codes karm
  kaudiocreator kbstate kcron kde-guidance kde-icons-mono
  kde-systemsettings kdeadmin-kfile-plugins kdebluetooth
  kdegraphics-kfile-plugins kdemultimedia-kfile-plugins
  kdenetwork-filesharing kdenetwork-kfile-plugins kdepim-kresources
  kdepim-wizards kdnssd keep kio-apt kio-locate kitchensync kmag kmailcvt
  kmilo kmousetool kmplayer-base kmplayer-konq-plugins knetworkconf knode
  knotes kontact kopete korganizer kpf kppp krdc krfb krita krita-data kscd
  kscreensaver kscreensaver-xsavers ksystemlog ktorrent
  kubuntu-default-settings kubuntu-desktop kubuntu-docs
  kubuntu-konqueror-shortcuts kwin-style-crystal landscape-client
  language-selector-common language-selector-qt laptop-mode-tools lftp
  libao2 libapm1 libavahi-core4 libbluetooth2 libbrlapi1 libcupsimage2
  libcurl3-gnutls libdaemon0 libenchant1c2a libgcj-bc libglade2-0
  libglib1.2 libgmp3c2 libgsl0 libgutenprint2 libhsqldb-java
  libjasper-runtime libjaxp1.2-java libjline-java libkpimexchange1
  liblockdev1 libmail-sendmail-perl libmdbtools libnotify1
  libopenobex-1.0-0 libpoppler1-qt libpythonize0 libqt-perl libqt4-core
  libqt4-gui libqt4-qt3support libqt4-sql librecode0 librsync1 libscim8c2a
  libscrollkeeper0 libservlet2.3-java libsexy2 libskim0 libslp1 libsmokeqt1
  libsqlite0 libstdc++5 libtdb1 libuniconf4.2 libwnck-common libwnck18
  libwvstreams4.2-base libwvstreams4.2-extras libxalan2-java
  libxerces2-java libxplc0.3.13 libxres1 libxt-java linux-headers-2.6.17-10
  linux-headers-2.6.17-10-generic linux-headers-generic min12xxw
  notification-daemon openoffice.org openoffice.org-base
  openoffice.org-calc openoffice.org-common openoffice.org-core
  openoffice.org-draw openoffice.org-impress openoffice.org-java-common
  openoffice.org-kde openoffice.org-math openoffice.org-style-crystal
  openoffice.org-style-default openoffice.org-style-hicontrast
  openoffice.org-style-industrial openoffice.org-writer pnm2ppa po-debconf
  powermanagement-interface powermgmt-base powernowd pykdeextensions
  python-apt python-elementtree python-qt4 python-uno qca-tls qobex
  qt4-qtconfig radeontool rdiff-backup readahead samba-common scim-qtimm
  screen scrollkeeper sdparm sgml-data skim slocate smartdimmer smbclient
  speedcrunch toshset ttf-arabeyes ttf-arphic-ukai ttf-arphic-uming
  ttf-baekmuk ttf-bengali-fonts ttf-bitstream-vera ttf-devanagari-fonts
  ttf-freefont ttf-gentium ttf-gujarati-fonts ttf-indic-fonts
  ttf-kannada-fonts ttf-kochi-gothic ttf-kochi-mincho ttf-lao
  ttf-malayalam-fonts ttf-mgopen ttf-oriya-fonts ttf-punjabi-fonts
  ttf-tamil-fonts ttf-telugu-fonts ttf-thai-tlwg vbetool vorbis-tools
  wlassistant wvdial xcursor-themes xkeyboard-config xli xscreensaver
  xscreensaver-data xscreensaver-gl
0 packages upgraded, 239 newly installed, 0 to remove and 0 not upgraded.
Need to get 278MB of archives. After unpacking 770MB will be used.
Do you want to continue? [Y/n/?]

```

---

### Post by Steveire on 2007-01-17
I now have thumbnails and laptopkeys working thanks to pinotree on irc. I had to install kmilo and kdegraphics-kfile-plugins

---

### Post by bionnaki on 2007-01-18
does your install auto-mount removable media like cds & usb drives?

---

### Post by Steveire on 2007-01-18
yep. hal was installed automatically.

---

