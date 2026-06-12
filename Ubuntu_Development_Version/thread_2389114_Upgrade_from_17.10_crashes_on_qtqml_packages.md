---
title: "Upgrade from 17.10 crashes on qt/qml packages"
date: 2018-04-11
forum: Ubuntu Development Version
---

### Post by doctordruidphd on 2018-04-11
I am trying to upgrade from 17.10 to 18.04. I posted this on the kubuntu forums, but so far no responses, so I am trying here in the hopes that someone has some ideas.

Doing the upgrade either way -- either using **do-release-upgrade -d** or manually changing the repositories from artful to bionic -- the upgrade proceeds for a while then halts with dpkg dependency errors. I have tried **apt-get install -f**, **apt --fix-broken install**, and **dpkg --configure -a** multiple times, but can't get past this problem.  I have also tried with and without the gui disabled, from the console, same results.

Here is the output:

```


root@Crynfyd:/# apt --fix-broken install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  fonts-ubuntu-font-family-console libbotan-1.10-1 libclang1-3.9 libegl1-mesa:i386 libicu57:i386
  libqt5location5 libre2-3 plasma-discover-common sqliteman-doc
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  hplip hplip-data initramfs-tools-bin libhpmud0 libklibc libpython3.6-minimal libpython3.6-stdlib
  libqscintilla2-qt4-13 libqscintilla2-qt4-l10n libqt5core5a libqt5multimediawidgets5
  libqt5texttospeech5 libsane-hpaio libsnmp-dev libsnmp30 libssl-dev plasma-integration
  printer-driver-hpcups printer-driver-hpijs python-numpy python-pyqt5 python-qscintilla2 python-qt4
  python-qt4-sql python-qwt5-qt4 python-sip python3-cryptography python3-distupgrade python3-openssl
  python3-pyasn1 python3-pycryptodome python3-pysmi python3-pysnmp4 python3.6-minimal qdbus-qt5
  qmlscene qt5-assistant qt5-qmake-bin qt5-style-plugins qtbase5-dev-tools qttools5-dev-tools
  skrooge skrooge-common snmp tora ubuntu-release-upgrader-core ubuntu-release-upgrader-gtk
Suggested packages:
  hplip-gui libqscintilla2-doc python-nose python-numpy-dbg python-numpy-doc python-pyqt5-dbg
  python-qt4-dbg libqwt5-qt4-dev python-cryptography-doc python3-cryptography-vectors
  python-openssl-doc python3-openssl-dbg qt5-doc
Recommended packages:
  libssl-doc
The following packages will be REMOVED:
  apport-kde apturl-kde git-cola hplip-gui kajongg kubuntu-desktop kubuntu-driver-manager
  kubuntu-notification-helper libqscintilla2-12v5 libqscintilla2-l10n muon muon-discover
  muon-notifier muon-updater plasma-discover plasma-scriptengine-python plasma-widget-facebook
  pyqt5-dev-tools python-kde4 python3-pyqt5 python3-pyqt5.qtmultimedia python3-pyqt5.qtopengl
  python3-pyqt5.qtpositioning python3-pyqt5.qtsensors python3-pyqt5.qtsql python3-pyqt5.qtsvg
  python3-pyqt5.qtwebkit python3-pyqt5.qtx11extras python3-pyqt5.qtxmlpatterns python3-qtpy
  software-properties-kde sqliteman sshconf ubuntu-release-upgrader-qt update-manager-kde
  usb-creator-kde
The following NEW packages will be installed:
  libqscintilla2-qt4-13 libqscintilla2-qt4-l10n libssl-dev python3-openssl python3-pycryptodome
  python3-pysmi qt5-assistant qt5-qmake-bin
The following packages will be upgraded:
  hplip hplip-data initramfs-tools-bin libhpmud0 libklibc libpython3.6-minimal libpython3.6-stdlib
  libqt5core5a libqt5multimediawidgets5 libqt5texttospeech5 libsane-hpaio libsnmp-dev libsnmp30
  plasma-integration printer-driver-hpcups printer-driver-hpijs python-numpy python-pyqt5
  python-qscintilla2 python-qt4 python-qt4-sql python-qwt5-qt4 python-sip python3-cryptography
  python3-distupgrade python3-pyasn1 python3-pysnmp4 python3.6-minimal qdbus-qt5 qmlscene
  qt5-style-plugins qtbase5-dev-tools qttools5-dev-tools skrooge skrooge-common snmp tora
  ubuntu-release-upgrader-core ubuntu-release-upgrader-gtk
39 upgraded, 8 newly installed, 36 to remove and 4044 not upgraded.
97 not fully installed or removed.
Need to get 0 B/52.9 MB of archives.
After this operation, 27.4 MB disk space will be freed.
Do you want to continue? [Y/n] y
apt-listchanges: Reading changelogs...
Extracting templates from packages: 100%
(Reading database ... 762329 files and directories currently installed.)
Preparing to unpack .../0-qmlscene_5.9.4-0ubuntu1_amd64.deb ...
Unpacking qmlscene (5.9.4-0ubuntu1) over (5.9.1-4ubuntu1) ...
dpkg: error processing archive /tmp/user/0/apt-dpkg-install-D2Wr7x/0-qmlscene_5.9.4-0ubuntu1_amd64.deb (--unpack):
 unable to open '/usr/lib/qt5/bin/qmlscene.dpkg-new': No such file or directory
No apport report written because the error message indicates an issue on the local system
                                                                                         Preparing to unpack .../1-qt5-qmake-bin_5.9.4+dfsg-0ubuntu4_amd64.deb ...
Unpacking qt5-qmake-bin (5.9.4+dfsg-0ubuntu4) ...
dpkg: error processing archive /tmp/user/0/apt-dpkg-install-D2Wr7x/1-qt5-qmake-bin_5.9.4+dfsg-0ubuntu4_amd64.deb (--unpack):
 unable to open '/usr/lib/qt5/bin/qmake.dpkg-new': No such file or directory
No apport report written because the error message indicates an issue on the local system
                                                                                         Preparing to unpack .../2-qttools5-dev-tools_5.9.4-0ubuntu1_amd64.deb ...
Unpacking qttools5-dev-tools (5.9.4-0ubuntu1) over (5.9.1-2) ...
dpkg: error processing archive /tmp/user/0/apt-dpkg-install-D2Wr7x/2-qttools5-dev-tools_5.9.4-0ubuntu1_amd64.deb (--unpack):
 unable to open '/usr/lib/qt5/bin/designer.dpkg-new': No such file or directory
No apport report written because the error message indicates an issue on the local system
                                                                                         Preparing to unpack .../3-qtbase5-dev-tools_5.9.4+dfsg-0ubuntu4_amd64.deb ...
Unpacking qtbase5-dev-tools (5.9.4+dfsg-0ubuntu4) over (5.9.1+dfsg-10ubuntu1) ...
dpkg: error processing archive /tmp/user/0/apt-dpkg-install-D2Wr7x/3-qtbase5-dev-tools_5.9.4+dfsg-0ubuntu4_amd64.deb (--unpack):
 unable to open '/usr/lib/qt5/bin/fixqt4headers.pl.dpkg-new': No such file or directory
No apport report written because MaxReports is reached already
                                                              dpkg: considering deconfiguration of qttools5-dev-tools:amd64, which would be broken by installation of qt5-assistant ...
dpkg: yes, will deconfigure qttools5-dev-tools:amd64 (broken by qt5-assistant)
Preparing to unpack .../4-qt5-assistant_5.9.4-0ubuntu1_amd64.deb ...
De-configuring qttools5-dev-tools:amd64 (5.9.1-2) ...
Unpacking qt5-assistant (5.9.4-0ubuntu1) ...
Replacing files in old package qttools5-dev-tools:amd64 (5.9.1-2) ...
dpkg: error processing archive /tmp/user/0/apt-dpkg-install-D2Wr7x/4-qt5-assistant_5.9.4-0ubuntu1_amd64.deb (--unpack):
 unable to open '/usr/lib/qt5/bin/assistant.dpkg-new': No such file or directory
No apport report written because MaxReports is reached already
                                                              Preparing to unpack .../5-qdbus-qt5_5.9.4-0ubuntu1_amd64.deb ...
Unpacking qdbus-qt5 (5.9.4-0ubuntu1) over (5.9.1-2) ...
dpkg: error processing archive /tmp/user/0/apt-dpkg-install-D2Wr7x/5-qdbus-qt5_5.9.4-0ubuntu1_amd64.deb (--unpack):
 unable to open '/usr/lib/qt5/bin/qdbus.dpkg-new': No such file or directory
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 /tmp/user/0/apt-dpkg-install-D2Wr7x/0-qmlscene_5.9.4-0ubuntu1_amd64.deb
 /tmp/user/0/apt-dpkg-install-D2Wr7x/1-qt5-qmake-bin_5.9.4+dfsg-0ubuntu4_amd64.deb
 /tmp/user/0/apt-dpkg-install-D2Wr7x/2-qttools5-dev-tools_5.9.4-0ubuntu1_amd64.deb
 /tmp/user/0/apt-dpkg-install-D2Wr7x/3-qtbase5-dev-tools_5.9.4+dfsg-0ubuntu4_amd64.deb
 /tmp/user/0/apt-dpkg-install-D2Wr7x/4-qt5-assistant_5.9.4-0ubuntu1_amd64.deb
 /tmp/user/0/apt-dpkg-install-D2Wr7x/5-qdbus-qt5_5.9.4-0ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

FYI - the "root" user name is there because on this particular try, I used a console logged in with sudo -i. Same thing happens if I use a regular terminal with sudo.

Further FYI: there also seems to be a problem that the upgrade process is de-configuring locales, which several packages complain about. I tried manually resetting the locale, but it didn't help the problem.

---

### Post by kc1di on 2018-04-12
In this particular case I would do a fresh install , 18.04 is still beta and the upgrade path may not yet be smooth until a bit after final is released. 
Good luck.

---

### Post by doctordruidphd on 2018-04-12
"Fresh install" is no solution, too much to reconfigure and reinstall for that to be reasonable. I guess I just wait and hope it works at final release, though my confidence in time healing the problem, without even knowing what it is, is not high.

---

