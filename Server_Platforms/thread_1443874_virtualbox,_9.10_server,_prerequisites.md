---
title: "virtualbox, 9.10 server, prerequisites"
date: 2010-03-31
forum: Server Platforms
---

### Post by abiheiri on 2010-03-31
I am trying to install VirtualBox on server 9.10 but I have some concerns. Why does VirtualBox require so many packages?

 It seems like it is really unnecessary for it to require kde-icons, aspell, and X11. I dont want to install a GUI on the server! see output below. Am I correct in my assumptions? or is it dafe to continue and not worry because it will not install gnome or kde..


The following NEW packages will be installed:
  aspell aspell-en dictionaries-common exiv2 hal hal-info hunspell-en-us
  kde-icons-oxygen kdebase-runtime kdebase-runtime-bin-kde4
  kdebase-runtime-data kdebase-runtime-data-common kdelibs-bin kdelibs5
  kdelibs5-data khelpcenter4 libaspell15 libaudio2 libclucene0ldbl libcurl3
  libenchant1c2a libepub0 libexiv2-5 libhal-storage1 libhunspell-1.2-0
  libknotificationitem1 liblzma0 libmng1 libmodplug0c2 libmpcdec3
  libmysqlclient16 libokularcore1 libpciaccess0 libplasma3 libpoppler-qt4-3
  libpoppler5 libpq5 libpulse0 libqca2 libqimageblitz4 libqt4-dbus
  libqt4-designer libqt4-network libqt4-opengl libqt4-phonon libqt4-qt3support
  libqt4-script libqt4-sql libqt4-sql-mysql libqt4-svg libqt4-webkit
  libqt4-xml libqtcore4 libqtgui4 libraptor1 librasqal1 librdf0
  libsdl-ttf2.0-0 libslp1 libsoprano4 libspectre1 libstreamanalyzer0
  libstreams0 libx86-1 libxaw7 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxine1
  libxine1-bin libxine1-console libxine1-misc-plugins libxine1-x libxml2-utils
  libxmu6 libxpm4 libxslt1.1 libxtrap6 libxtst6 libxvmc1 libxxf86dga1
  libxxf86misc1 libzip1 mysql-common okular phonon-backend-xine pm-utils
  radeontool raptor-utils redland-utils smartdimmer soprano-daemon vbetool
  virtualbox-3.1 x11-utils x11-xserver-utils xdg-utils

0 upgraded, 97 newly installed, 0 to remove and 0 not upgraded.
Need to get 108MB of archives.
After this operation, 295MB of additional disk space will be used.
Do you want to continue [Y/n]? n

---

### Post by johngreth on 2010-03-31
I don't know of a way to install it without the gui packages, but if you aren't using gui and you don't have a desktop manager, installing all the extra packages shouldn't cause a problem or slow anything down because they just won't be used.

---

### Post by abiheiri on 2010-04-01
I installed it and everything looks good.. 

I'm in runlevel 2 and gnome-desktop did not install

---

