---
title: "Unable to apply upgrades from Update Manager"
date: 2012-08-14
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by radus on 2012-08-14
Hello,

   I've recently decided to try the Quantal Quetzal packages, so I added the repository sources to my Update Manager.  Some (Most) of the packages updated automatically.

  But there are some packages which will not upgrade. I tried sudo apt-get upgrade, this is what I get:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  command-not-found dbus dconf-gsettings-backend dconf-service dconf-tools
  debhelper devhelp dpkg-dev eog evince evince-common evolution-data-server
  evolution-data-server-common foomatic-db-compressed-ppds g++ gettext
  gettext-base ghostscript ghostscript-x gir1.2-gkbd-3.0
  gir1.2-gnomebluetooth-1.0 gir1.2-mutter-3.0 gir1.2-peas-1.0 gir1.2-rb-3.0
  gir1.2-totem-1.0 gjs gnome-applets gnome-applets-data gnome-bluetooth
  gnome-contacts gnome-control-center gnome-control-center-data
  gnome-desktop3-data gnome-disk-utility gnome-font-viewer gnome-games-data
  gnome-nettool gnome-orca gnome-panel gnome-panel-data gnome-screensaver
  gnome-settings-daemon gnome-shell gnome-shell-common gnome-sudoku
  gnome-user-share gnomine gstreamer0.10-plugins-ugly gvfs gvfs-backends
  gvfs-bin gvfs-common gvfs-daemons gvfs-fuse gvfs-libs indicator-datetime
  indicator-session jadetex kde-runtime kde-runtime-data libatk-adaptor
  libdb5.1-java libdb5.1-java-gcj libdconf-dbus-1-0 libdpkg-perl
  libedataserverui-3.0-1 libfolks-eds25 libgcj-bc libgettextpo0 libgjs0c
  libgpod-common libgpod-dev libgpod4 libgs9 libgs9-common
  libimobiledevice-dev libmutter0 libnepomuksync4 libnunit-cil-dev
  libpackagekit-glib2-14 libpeas-1.0-0 libpeas-dev libplymouth2 libraptor2-0
  libsdl-image1.2 libsoprano4 libsvn1 libtiff4 libtiff4-dev libtiffxx0c2
  libtotem0 libunity-2d-private0 libusbmuxd-dev linux-headers-generic
  linux-image-generic luatex mahjongg mutter-common nautilus nautilus-data
  nautilus-sendto network-manager-gnome onboard overlay-scrollbar
  plasma-scriptengine-javascript plymouth plymouth-label procps python-apt
  python-aptdaemon python-aptdaemon-gtk python-aptdaemon.gtk3widgets
  python-aptdaemon.gtkwidgets python-packagekit python-ubuntu-sso-client
  python-ubuntuone-control-panel rhythmbox rhythmbox-data rhythmbox-mozilla
  rhythmbox-plugin-cdrecorder rhythmbox-plugin-magnatune
  rhythmbox-plugin-zeitgeist rhythmbox-plugins software-center
  software-properties-common software-properties-gtk soprano-daemon subversion
  tex-common texlive-base texlive-binaries texlive-common texlive-doc-base
  texlive-fonts-recommended texlive-latex-base texlive-latex-recommended
  thunderbird thunderbird-globalmenu thunderbird-gnome-support tipa totem
  totem-common totem-mozilla totem-plugins ttf-freefont ubuntu-sso-client
  ubuntu-sso-client-qt ubuntuone-client-gnome ubuntuone-control-panel
  ubuntuone-control-panel-common ubuntuone-control-panel-gtk
  ubuntuone-control-panel-qt unity-2d-common unity-2d-panel unity-2d-shell
  unity-2d-spread unity-services upower usbmuxd valac vim-common vim-gnome
  vim-gui-common vim-runtime vim-tiny virtualbox virtualbox-dkms virtualbox-qt
  vlc vlc-nox vlc-plugin-notify vlc-plugin-pulse whoopsie xz-utils zlib1g
  zlib1g-dev
0 upgraded, 0 newly installed, 0 to remove and 176 not upgraded.

```One solution for this that I found: I search one of the packages on the ubuntuupdates site and manually install it. Usually, this will also automatically upgrade some of the other packages. Repeat for the next package. This seems to work ok.

  But I'd like to understand why apt-get upgrade doesn't work.

---

### Post by philinux on 2012-08-14
sudo apt-get dist-upgrade Be careful with that in case it wants to remove packages.

or use synaptic.

See the stickies on the forum.

---

### Post by johnathansmith on 2012-08-14
This's look like a problem with dependency.

---

### Post by Harry33 on 2012-08-14
What exactly are trying to do?
Are you upgrading from Precise to Quantal?
If so, you need to change the word "precise" to the word "quantal" in your sources.list file.
Do not keep both there.
Also, you need to purge all additional PPA's first.

The upgrading is better done with synaptic. Do not install manually anything (with dpkg) to prevent the troubles.

---

### Post by radus on 2012-08-14
Thanks for the replies.

I changed "precise" to "quantal" in the /etc/apt/source.list and after that I could do a proper upgrade with apt-get dist-upgrade.

---

