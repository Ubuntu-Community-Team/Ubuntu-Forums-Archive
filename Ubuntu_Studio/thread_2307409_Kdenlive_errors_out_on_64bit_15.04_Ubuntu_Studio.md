---
title: "Kdenlive errors out on 64bit 15.04 Ubuntu Studio"
date: 2015-12-24
forum: Ubuntu Studio
---

### Post by csaba-toth on 2015-12-24
I installed Ubuntu Studio and performed regular updates. I want to try Kdenlive, but it errors out on Qt. Please tell me what additional error information should I provide, and what could be a solution or workaround.

```

csaba@P570WM:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 15.04
Release:    15.04
Codename:    vivid
csaba@P570WM:~$ kdenlive
Cannot mix incompatible Qt library (version 0x40806) with this library (version 0x40803)
KCrash: Application 'kdenlive' crashing...
KCrash: Attempting to start /usr/lib/kde4/libexec/drkonqi from kdeinit
KCrash: Connect sock_file=/home/csaba/.kde/socket-P570WM/kdeinit4__0
Warning: connect() failed: : No such file or directory
KCrash: Attempting to start /usr/lib/kde4/libexec/drkonqi directly
/usr/lib/kde4/libexec/drkonqi: symbol lookup error: /usr/lib/x86_64-linux-gnu/libQtWebKit.so.4: undefined symbol: _ZN10QSslSocket16staticMetaObjectE
Unable to start Dr. Konqi
Not forwarding the crash to Apport.

```

I guess all of the KCrash and Dr Kongi stuff is an aftermath of the "Cannot mix incompatible Qt library (version 0x40806) with this library (version 0x40803)". It's bad enough that even the crash report cannot be completed. What am I doing wrong?

```

csaba@P570WM:~$ dpkg -l | grep qt
ii  ffado-mixer-qt4                             2.2.1-2build1                              all          FFADO D-Bus mixer applets (QT4)
ii  gem-plugin-lqt                              1:0.93.3-8                                 amd64        Graphics Environment for Multimedia - LQT support
ii  libdbusmenu-qt2:amd64                       0.9.3+14.10.20140619-0ubuntu1              amd64        Qt implementation of the DBusMenu protocol
ii  libdbusmenu-qt5:amd64                       0.9.3+14.10.20140619-0ubuntu1              amd64        Qt5 implementation of the DBusMenu protocol
ii  libkf5dbusaddons-bin                        5.9.0-0ubuntu1                             amd64        class library for qtdbus
ii  libkf5dbusaddons-data                       5.9.0-0ubuntu1                             all          class library for qtdbus
ii  libkf5dbusaddons5:amd64                     5.9.0-0ubuntu1                             amd64        class library for qtdbus
ii  libntrack-qt4-1                             016-1.3                                    amd64        Qt 4 API for ntrack
ii  libphonon4qt5-4:amd64                       4:4.8.3-0ubuntu2                           amd64        multimedia framework from KDE using Qt 5 - core library
ii  libpolkit-qt-1-1                            0.112.0-0ubuntu3                           amd64        PolicyKit-qt-1 library
ii  libpolkit-qt5-1-1                           0.112.0-0ubuntu2                           amd64        PolicyKit-qt5-1 library
ii  libpoppler-qt4-4:amd64                      0.30.0-0ubuntu1                            amd64        PDF rendering library (Qt 4 based shared library)
ii  libqt4-dbus:amd64                           4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu6.1    amd64        Qt 4 D-Bus module
ii  libqt4-dbus:i386                            4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu6.1    i386         Qt 4 D-Bus module
ii  libqt4-declarative:amd64                    4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu6.1    amd64        Qt 4 Declarative module
ii  libqt4-declarative:i386                     4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu6.1    i386         Qt 4 Declarative module
ii  libqt4-designer:amd64                       4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu6.1    amd64        Qt 4 designer module
ii  libqt4-help:amd64                           4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu6.1    amd64        Qt 4 help module
ii  libqt4-network:amd64                        4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu6.1    amd64        Qt 4 network module
ii  libqt4-network:i386                         4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu6.1    i386         Qt 4 network module
ii  libqt4-opengl:amd64                         4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu6.1    amd64        Qt 4 OpenGL module
ii  libqt4-opengl:i386                          4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu6.1    i386         Qt 4 OpenGL module
ii  libqt4-qt3support:amd64                     4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu6.1    amd64        Qt 3 compatibility library for Qt 4
ii  libqt4-script:amd64                         4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu6.1    amd64        Qt 4 script module
ii  libqt4-script:i386                          4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu6.1    i386         Qt 4 script module
ii  libqt4-scripttools:amd64                    4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu6.1    amd64        Qt 4 script tools module
ii  libqt4-sql:amd64                            4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu6.1    amd64        Qt 4 SQL module
ii  libqt4-sql:i386                             4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu6.1    i386         Qt 4 SQL module
ii  libqt4-sql-mysql:amd64                      4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu6.1    amd64        Qt 4 MySQL database driver
ii  libqt4-sql-mysql:i386                       4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu6.1    i386         Qt 4 MySQL database driver
ii  libqt4-svg:amd64                            4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu6.1    amd64        Qt 4 SVG module
ii  libqt4-test:amd64                           4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu6.1    amd64        Qt 4 test module
ii  libqt4-xml:amd64                            4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu6.1    amd64        Qt 4 XML module
ii  libqt4-xml:i386                             4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu6.1    i386         Qt 4 XML module
ii  libqt4-xmlpatterns:amd64                    4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu6.1    amd64        Qt 4 XML patterns module
ii  libqt4-xmlpatterns:i386                     4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu6.1    i386         Qt 4 XML patterns module
ii  libqt5core5a:amd64                          5.4.1+dfsg-2ubuntu4.1                      amd64        Qt 5 core module
ii  libqt5dbus5:amd64                           5.4.1+dfsg-2ubuntu4.1                      amd64        Qt 5 D-Bus module
ii  libqt5gui5:amd64                            5.4.1+dfsg-2ubuntu4.1                      amd64        Qt 5 GUI module
ii  libqt5network5:amd64                        5.4.1+dfsg-2ubuntu4.1                      amd64        Qt 5 network module
ii  libqt5opengl5:amd64                         5.4.1+dfsg-2ubuntu4.1                      amd64        Qt 5 OpenGL module
ii  libqt5printsupport5:amd64                   5.4.1+dfsg-2ubuntu4.1                      amd64        Qt 5 print support module
ii  libqt5qml5:amd64                            5.4.1-1ubuntu5                             amd64        Qt 5 QML module
ii  libqt5quick5:amd64                          5.4.1-1ubuntu5                             amd64        Qt 5 Quick library
ii  libqt5script5:amd64                         5.4.1+dfsg-3                               amd64        Qt 5 script module
ii  libqt5sql5:amd64                            5.4.1+dfsg-2ubuntu4.1                      amd64        Qt 5 SQL module
ii  libqt5sql5-sqlite:amd64                     5.4.1+dfsg-2ubuntu4.1                      amd64        Qt 5 SQLite 3 database driver
ii  libqt5svg5:amd64                            5.4.1-1                                    amd64        Qt 5 SVG module
ii  libqt5test5:amd64                           5.4.1+dfsg-2ubuntu4.1                      amd64        Qt 5 test module
ii  libqt5webkit5:amd64                         5.4.1+dfsg-2ubuntu1                        amd64        Web content engine library for Qt
ii  libqt5widgets5:amd64                        5.4.1+dfsg-2ubuntu4.1                      amd64        Qt 5 widgets module
ii  libqt5x11extras5:amd64                      5.4.1-1                                    amd64        Qt 5 X11 extras
ii  libqt5xml5:amd64                            5.4.1+dfsg-2ubuntu4.1                      amd64        Qt 5 XML module
ii  libqtassistantclient4:amd64                 4.6.3-6                                    amd64        Qt Assistant client library (runtime)
ii  libqtcore4:amd64                            4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu6.1    amd64        Qt 4 core module
ii  libqtcore4:i386                             4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu6.1    i386         Qt 4 core module
ii  libqtdbus4:amd64                            4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu6.1    amd64        Qt 4 D-Bus module library
ii  libqtdbus4:i386                             4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu6.1    i386         Qt 4 D-Bus module library
ii  libqtgui4:amd64                             4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu6.1    amd64        Qt 4 GUI module
ii  libqtgui4:i386                              4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu6.1    i386         Qt 4 GUI module
ii  libqtlocation1:amd64                        1.2.0-3ubuntu5                             amd64        Qt Mobility Location module
ii  libqtscript4-core:amd64                     0.2.0-1                                    amd64        QtScript bindings for the Qt 4 Core library
ii  libqtscript4-gui:amd64                      0.2.0-1                                    amd64        QtScript bindings for the Qt 4 Gui library
ii  libqtscript4-network:amd64                  0.2.0-1                                    amd64        QtScript bindings for the Qt 4 Network library
ii  libqtscript4-uitools:amd64                  0.2.0-1                                    amd64        QtScript bindings for the Qt 4 UiTools library
ii  libqtscript4-xml:amd64                      0.2.0-1                                    amd64        QtScript bindings for the Qt 4 XML library
ii  libqtwebkit4:amd64                          2.3.2-0ubuntu7                             amd64        Web content engine library for Qt
ii  libqtwebkit4:i386                           2.3.2-0ubuntu7                             i386         Web content engine library for Qt
ii  oxideqt-codecs-extra:amd64                  1.11.3-0ubuntu0.15.04.1                    amd64        Web browser engine library for Qt (codecs)
ii  python-qt4                                  4.11.3+dfsg-1                              amd64        Python bindings for Qt4
ii  python-qt4-dbus                             4.11.3+dfsg-1                              amd64        D-Bus Support for PyQt4
ii  qt-at-spi:amd64                             0.3.1-5fakesync1                           amd64        at-spi accessibility plugin for Qt
ii  qt-faststart                                7:2.5.9-0ubuntu0.15.04.1                   amd64        Utility to rearrange a Quicktime file
ii  qtchooser                                   52-gae5eeef-1                              amd64        Wrapper to select between Qt development binary versions
ii  qtcore4-l10n                                4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu6.1    all          Qt 4 core module translations
ii  qtractor                                    0.6.3-1                                    amd64        MIDI/Audio multi-track sequencer application
ii  qttranslations5-l10n                        5.4.1-1                                    all          translations for Qt 5
ii  virtualbox-qt                               4.3.34-dfsg-1+deb8u1ubuntu1.15.04.1        amd64        x86 virtualization solution - Qt based user interface

```

---

### Post by csaba-toth on 2015-12-24
Looks like maybe I cannot even start any Qt based app?

```

csaba@P570WM:~$ qtractor 
qtractor: symbol lookup error: qtractor: undefined symbol: _ZN9QGtkStyle16staticMetaObjectE

```

That's sad.

---

### Post by blm-ubunet on 2015-12-24
Have you added some ppa to upgrade your libqt4 libraries ?
Is that the case or do I read it wrong?

The kdenlive in the std package repos looks to be quite out of date..
The latest is using Qt5.
[https://userbase.kde.org/Kdenlive/Manual/Installation](https://userbase.kde.org/Kdenlive/Manual/Installation)

[https://launchpad.net/~sunab/+archive/ubuntu/kdenlive-release?field.series_filter=vivid](https://launchpad.net/~sunab/+archive/ubuntu/kdenlive-release?field.series_filter=vivid)
But this could have unforeseen consequences..

---

### Post by csaba-toth on 2015-12-24
Thanks for the heads up.

```

csaba@P570WM:~$ dpkg -l | grep kden
ii  kdenlive                                    0.9.10-2ubuntu1.1                          amd64        non-linear video editor
ii  kdenlive-data                               0.9.10-2ubuntu1.1                          all          non-linear video editor (data files)

```

Now I looked at kdenlive website and it talks about version 15.xy, so I don't know what's that 0.9.10. As for the Qt version, the version 0x40806 doesn't look like too far mismatch from 0x40803. If the last digit is probably not even minor version but patch level. I need to identify what version does it miss. But I don't recollect fiddling with any Qt versions, so I wonder if that's package maintenance problem generically for Ubuntu Studio 15.04, or am I the only one? I'm thinking about a dist upgrade to 15.10 BTW.

---

### Post by csaba-toth on 2015-12-24
Oooh! Kdenlive 0.9.10 is only mentioned for Ubuntu 14.10 and below on the Kdenlive website. But still, it seems like there some generic problem with Qt on my system.
See Recommended versions at [https://kdenlive.org/download-ubuntu](https://kdenlive.org/download-ubuntu)

---

### Post by blm-ubunet on 2015-12-25
If you're not on a LTS version you have to keep up..

I find synaptic package manager the best tool to find out the problems with packages etc.
I'm not sure there is any problem with your Qt4 packages.

The kdenlive site seemed to suggest that the ubuntu distribution versions were very conservative so fixing the (possible) Qt4 problem could be time wasted.

---

### Post by csaba-toth on 2016-02-14
Just for the record: after dist upgrade from 15.04 to 15.10 Ubuntu Studio, kdenlive suddenly works. I haven't tried editing yet, but went through the wizard for the first start. It crashes upon exit, but that should be the biggest problem.
Version numbers changed significantly:

ii  kdenlive                                      4:15.08.2.1~really15.08.1-0ubuntu2         amd64        non-linear video editor
ii  kdenlive-data                                 4:15.08.2.1~really15.08.1-0ubuntu2         all          non-linear video editor (data files)

qtractor still exits with the same error.

---

