---
title: "Anyone running Compiz 0.9.0 w/ Ubuntu 10.04"
date: 2010-07-09
forum: The Cafe
---

### Post by bonfire89 on 2010-07-09
Compiz 0.9.0, it's out, is anyone running it with ubuntu 10.04 yet? How is it?

---

### Post by Excedio on 2010-07-09
Nope. But I hear good things. Pretty much a complete re-write.

---

### Post by 5735guy on 2010-08-05
Here is the method I used to succesfully compile Compiz 0.9.0 on Ubuntu 10.04 and Linux Mint 9 

Download Desktop.tar.gz from the site below then use my script
[http://santiance.com/2010/07/compile-compiz-0-9-0-in-ubuntu/](http://santiance.com/2010/07/compile-compiz-0-9-0-in-ubuntu/)

SYNAPTIC
Default Compiz (complete removal)

TERMINAL
sudo add-apt-repository ppa:falk-t-j/lucid-latest
sudo apt-get update

sudo apt-get install compiz-git

SYNAPTIC

compiz-git (complete removal)

TERMINAL

cd ~/Desktop && tar -xf Desktop.tar.gz

./install_compiz_090.sh

Alt+F2

/opt/compiz/bin/compiz++

set up CCSM

REBOOT

Alt+F2

/opt/compiz/bin/compiz++

SYNAPTIC

Remove falkTX repository

TERMINAL

sudo apt-get autoremove

SYNAPTIC

Purge package residuals


Compiz 0.9.0 installation complete

---

### Post by Tracy177 on 2010-09-01
> **5735guy said:**
> Here is the method I used to succesfully compile Compiz 0.9.0 on Ubuntu 10.04 and Linux Mint 9 

Download Desktop.tar.gz from the site below then use my script
[http://santiance.com/2010/07/compile-compiz-0-9-0-in-ubuntu/](http://santiance.com/2010/07/compile-compiz-0-9-0-in-ubuntu/)

SYNAPTIC
Default Compiz (complete removal)

TERMINAL
sudo add-apt-repository ppa:falk-t-j/lucid-latest
sudo apt-get update

sudo apt-get install compiz-git

SYNAPTIC

compiz-git (complete removal)

TERMINAL

cd ~/Desktop && tar -xf Desktop.tar.gz

./install_compiz_090.sh

Alt+F2

/opt/compiz/bin/compiz++

set up CCSM

REBOOT

Alt+F2

/opt/compiz/bin/compiz++

SYNAPTIC

Remove falkTX repository

TERMINAL

sudo apt-get autoremove

SYNAPTIC

Purge package residuals


Compiz 0.9.0 installation complete


there is something wrong with it when i type sudo apt-get install compiz-git it try to install a lot of packages is this normall? why does it want to install kde ?


sudo apt-get install compiz-git
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  exiv2 gdebi-kde icoutils install-package kdebase-runtime
  kdebase-runtime-data kdelibs-bin kdelibs5 kdelibs5-data kdepimlibs-data
  kdepimlibs5 kdesudo kpackagekit kubuntu-debug-installer libakonadiprivate1
  libattica0 libboost-program-options1.40.0 libboost-serialization1.40.0
  libclucene0ldbl libdbusmenu-qt2 libexiv2-6 libiodbc2 libkdecorations4
  libmysqlclient16 libpackagekit-glib2-12 libpackagekit-qt-12 libphonon4
  libplasma3 libpolkit-qt-1-0 libqca2 libqt4-assistant libqt4-dbus
  libqt4-designer libqt4-help libqt4-qt3support libqt4-script
  libqt4-scripttools libqt4-sql libqt4-sql-mysql libqt4-svg libqt4-test
  libqt4-webkit libqt4-xml libqt4-xmlpatterns libsoprano4 libssh-4
  libstreamanalyzer0 libstreams0 libx11-xcb1 libxcb-shape0 libxcb-shm0
  libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-misc-plugins
  libxine1-x mysql-common oxygen-icon-theme packagekit packagekit-backend-apt
  phonon phonon-backend-xine plasma-scriptengine-javascript polkit-kde-1
  python-kde4 python-packagekit python-qt4 python-sip
  shared-desktop-ontologies software-properties-kde soprano-daemon ttf-dejavu
  update-manager-kde virtuoso-nepomuk
Suggested packages:
  libterm-readline-gnu-perl libterm-readline-perl-perl djvulibre-bin hspell
  akonadi-server libqca2-plugin-cyrus-sasl libqca2-plugin-gnupg
  libqca2-plugin-ossl libqca2-plugin-pkcs11 libqt4-dev gxine xine-ui
  libxine1-doc libxine-doc libxine1-ffmpeg phonon-backend-gstreamer
  phonon-backend-vlc phonon-backend-mplayer kcm-phonon-xine python-qt4-dbg
The following NEW packages will be installed
  compiz-git exiv2 gdebi-kde icoutils install-package kdebase-runtime
  kdebase-runtime-data kdelibs-bin kdelibs5 kdelibs5-data kdepimlibs-data
  kdepimlibs5 kdesudo kpackagekit kubuntu-debug-installer libakonadiprivate1
  libattica0 libboost-program-options1.40.0 libboost-serialization1.40.0
  libclucene0ldbl libdbusmenu-qt2 libexiv2-6 libiodbc2 libkdecorations4
  libmysqlclient16 libpackagekit-glib2-12 libpackagekit-qt-12 libphonon4
  libplasma3 libpolkit-qt-1-0 libqca2 libqt4-assistant libqt4-dbus
  libqt4-designer libqt4-help libqt4-qt3support libqt4-script
  libqt4-scripttools libqt4-sql libqt4-sql-mysql libqt4-svg libqt4-test
  libqt4-webkit libqt4-xml libqt4-xmlpatterns libsoprano4 libssh-4
  libstreamanalyzer0 libstreams0 libx11-xcb1 libxcb-shape0 libxcb-shm0
  libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-misc-plugins
  libxine1-x mysql-common oxygen-icon-theme packagekit packagekit-backend-apt
  phonon phonon-backend-xine plasma-scriptengine-javascript polkit-kde-1
  python-kde4 python-packagekit python-qt4 python-sip
  shared-desktop-ontologies software-properties-kde soprano-daemon ttf-dejavu
  update-manager-kde virtuoso-nepomuk
0 upgraded, 76 newly installed, 0 to remove and 40 not upgraded.
Need to get 81.0MB of archives.
After this operation, 283MB of additional disk space will be used.
Do you want to continue [Y/n]?

---

### Post by 5735guy on 2010-09-09
Only recommended to those who know what they are doing

Make sure build-essential is installed

Download Desktop.tar.gz from the site below then use my script
[http://santiance.com/2010/07/compile-compiz-0-9-0-in-ubuntu/](http://santiance.com/2010/07/compile-compiz-0-9-0-in-ubuntu/)

SYNAPTIC

Default Compiz (complete removal)

TERMINAL

cd ~/Desktop && tar -xf Desktop.tar.gz

./install_compiz_090.sh

Alt+F2

/opt/compiz/bin/compiz++

set up CCSM

REBOOT

Alt+F2

/opt/compiz/bin/compiz++

Compiz 0.9.0 compilation is now complete 

The build takes around 30-45 minutes to complete


LUg.

---

