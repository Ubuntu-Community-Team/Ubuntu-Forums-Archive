---
title: "Cannot mix incompatible Qt library..."
date: 2017-12-20
forum: Ubuntu Development Version
---

### Post by 3vi1 on 2017-12-20
One of the Bionic updates in the last day or two seems to have broken a lot of things on my test system, such as sddm, plasma-shell, etc.

After flipping to my gnome desktop and looking at the logs, I'm seeing what appears to be a mix of Qt versions.  For instance, when I attempt to start vlc (even under gnome), I get:

```
Cannot mix incompatible Qt library (version 0x50903) with this library (version 0x50902)

```
Is this a result of only some new Qt packages being uploaded, or am I the only one running into this?

Thx!

---

### Post by zika on 2017-12-20
What environment/list on Your machine does qtchooser report?

---

### Post by 3vi1 on 2017-12-20
> **zika said:**
> What environment/list on Your machine does qtchooser report?

```
08:20:44 evil@sager ~» qtchooser -l
4
5
default
qt4-x86_64-linux-gnu
qt4
qt5-x86_64-linux-gnu
qt5
```

Everything's been running fine on this machine for years, the only change in the last couple of days were my daily apt updates, which I saw included various KDE platform and Qt packages.  The VLC error seems to indicate some libraries compiled with minor version changes of Qt5, which is why I was wondering if I had just had the bad luck to update while new Qt packages were still being uploaded.

---

### Post by 3vi1 on 2017-12-20
Looks like I was right.  Some new packages just got thrown in the repo during my last meeting, including new qtbase and qt5-default packages.  

VLC works again and I'm betting plasma will after I flip back to it!

Thanks!

---

### Post by acheronuk on 2017-12-20
Yes, usually most of a new Qt release upload migrates from -proposed to -release in more or less one go. This time for a few reasons it was a bit more staggered, so that type of version mismatch on installed library versions cropped up.

Seems that the last of Qt 5.9.3 is on the way to the -release pocket as of tonight.

---

### Post by flocculant on 2017-12-21
> **acheronuk said:**
> Yes, usually most of a new Qt release upload migrates from -proposed to -release in more or less one go. This time for a few reasons it was a bit more staggered, so that type of version mismatch on installed library versions cropped up.

Seems that the last of Qt 5.9.3 is on the way to the -release pocket as of tonight.

Fully updated. No qt5 updates available in -proposed.

qmmp fails to run

cantata fails to run

(running xubuntu)

---

### Post by acheronuk on 2017-12-21
> **flocculant said:**
> Fully updated. No qt5 updates available in -proposed.

qmmp fails to run

cantata fails to run

(running xubuntu)

Probably need to see what Qt with what version you have installed, as they both launch fine here on a fully updated system (no proposed enabled).

[IMG]https://i.imgur.com/JTROwcE.png[/IMG]

---

### Post by flocculant on 2017-12-21
```
dpkg -l qt5* | grep ii
ii  qt5-gtk-platformtheme:amd64 5.9.3+dfsg-0ubuntu1          amd64        Qt 5 GTK+ 3 platform theme
ii  qt5-qmake:amd64             5.9.3+dfsg-0ubuntu1          amd64        Qt 5 qmake Makefile generator tool
ii  qt5-qmake-bin               5.9.3+dfsg-0ubuntu1          amd64        Qt 5 qmake Makefile generator tool — binary file
ii  qt5-style-plugins:amd64     5.0.0+git23.g335dbec-2build2 amd64        Qt 5 extra widget styles
```

```
dpkg -l qt4* | grep ii
ii  qt4-linguist-tools 4:4.8.7+dfsg-7ubuntu1 amd64        Qt 4 Linguist tools
```


```
dpkg -l libqt* | grep ii
ii  libqt4-dbus:amd64                  4:4.8.7+dfsg-7ubuntu1  amd64        Qt 4 D-Bus module
ii  libqt4-declarative:amd64           4:4.8.7+dfsg-7ubuntu1  amd64        Qt 4 Declarative module
ii  libqt4-network:amd64               4:4.8.7+dfsg-7ubuntu1  amd64        Qt 4 network module
ii  libqt4-opengl:amd64                4:4.8.7+dfsg-7ubuntu1  amd64        Qt 4 OpenGL module
ii  libqt4-script:amd64                4:4.8.7+dfsg-7ubuntu1  amd64        Qt 4 script module
ii  libqt4-sql:amd64                   4:4.8.7+dfsg-7ubuntu1  amd64        Qt 4 SQL module
ii  libqt4-sql-mysql:amd64             4:4.8.7+dfsg-7ubuntu1  amd64        Qt 4 MySQL database driver
ii  libqt4-sql-sqlite:amd64            4:4.8.7+dfsg-7ubuntu1  amd64        Qt 4 SQLite 3 database driver
ii  libqt4-xml:amd64                   4:4.8.7+dfsg-7ubuntu1  amd64        Qt 4 XML module
ii  libqt4-xmlpatterns:amd64           4:4.8.7+dfsg-7ubuntu1  amd64        Qt 4 XML patterns module
ii  libqt5concurrent5:amd64            5.9.3+dfsg-0ubuntu1    amd64        Qt 5 concurrent module
ii  libqt5core5a:amd64                 5.9.3+dfsg-0ubuntu1    amd64        Qt 5 core module
ii  libqt5dbus5:amd64                  5.9.3+dfsg-0ubuntu1    amd64        Qt 5 D-Bus module
ii  libqt5designer5:amd64              5.9.3-0ubuntu3         amd64        Qt 5 designer module
ii  libqt5designercomponents5:amd64    5.9.3-0ubuntu3         amd64        Qt 5 Designer components module
ii  libqt5gui5:amd64                   5.9.3+dfsg-0ubuntu1    amd64        Qt 5 GUI module
ii  libqt5help5:amd64                  5.9.3-0ubuntu3         amd64        Qt 5 help module
ii  libqt5multimedia5:amd64            5.9.3-0ubuntu3         amd64        Qt 5 Multimedia module
ii  libqt5network5:amd64               5.9.3+dfsg-0ubuntu1    amd64        Qt 5 network module
ii  libqt5opengl5:amd64                5.9.3+dfsg-0ubuntu1    amd64        Qt 5 OpenGL module
ii  libqt5opengl5-dev:amd64            5.9.3+dfsg-0ubuntu1    amd64        Qt 5 OpenGL library development files
ii  libqt5positioning5:amd64           5.9.3+dfsg-0ubuntu1    amd64        Qt Positioning module
ii  libqt5printsupport5:amd64          5.9.3+dfsg-0ubuntu1    amd64        Qt 5 print support module
ii  libqt5qml5:amd64                   5.9.3-0ubuntu1         amd64        Qt 5 QML module
ii  libqt5quick5:amd64                 5.9.3-0ubuntu1         amd64        Qt 5 Quick library
ii  libqt5quickwidgets5:amd64          5.9.3-0ubuntu1         amd64        Qt 5 Quick Widgets library
ii  libqt5sensors5:amd64               5.9.3-0ubuntu1         amd64        Qt Sensors module
ii  libqt5sql5:amd64                   5.9.3+dfsg-0ubuntu1    amd64        Qt 5 SQL module
ii  libqt5sql5-sqlite:amd64            5.9.3+dfsg-0ubuntu1    amd64        Qt 5 SQLite 3 database driver
ii  libqt5svg5:amd64                   5.9.3-0ubuntu1         amd64        Qt 5 SVG module
ii  libqt5svg5-dev:amd64               5.9.3-0ubuntu1         amd64        Qt 5 SVG module development files
ii  libqt5test5:amd64                  5.9.3+dfsg-0ubuntu1    amd64        Qt 5 test module
ii  libqt5webchannel5:amd64            5.9.3-0ubuntu1         amd64        Web communication library for Qt
ii  libqt5webkit5:amd64                5.212.0~alpha2-5build4 amd64        Web content engine library for Qt
ii  libqt5widgets5:amd64               5.9.3+dfsg-0ubuntu1    amd64        Qt 5 widgets module
ii  libqt5x11extras5:amd64             5.9.3-0ubuntu1         amd64        Qt 5 X11 extras
ii  libqt5xml5:amd64                   5.9.3+dfsg-0ubuntu1    amd64        Qt 5 XML module
ii  libqtcore4:amd64                   4:4.8.7+dfsg-7ubuntu1  amd64        Qt 4 core module
ii  libqtdbus4:amd64                   4:4.8.7+dfsg-7ubuntu1  amd64        Qt 4 D-Bus module library
ii  libqtgui4:amd64                    4:4.8.7+dfsg-7ubuntu1  amd64        Qt 4 GUI module
```

```
qtchooser -l
4
5
default
qt4-x86_64-linux-gnu
qt4
qt5-x86_64-linux-gnu
qt5
```

is what I've got locally

also cantata is built from git - rebuilt short while ago - not unexpected errors

---

### Post by acheronuk on 2017-12-21
Output of:

dpkg -l | grep ii | grep 5.9.3

&

dpkg -l | grep ii | grep 5.9.2

Is more likely to catch the actual installed Qt libs

---

### Post by flocculant on 2017-12-21
```
dpkg -l | grep ii | grep 5.9.3
ii  fwupdate-signed                       1.15+9-3                                                   amd64        Linux Firmware Updater EFI signed binary
ii  libqt5concurrent5:amd64               5.9.3+dfsg-0ubuntu1                                        amd64        Qt 5 concurrent module
ii  libqt5core5a:amd64                    5.9.3+dfsg-0ubuntu1                                        amd64        Qt 5 core module
ii  libqt5dbus5:amd64                     5.9.3+dfsg-0ubuntu1                                        amd64        Qt 5 D-Bus module
ii  libqt5designer5:amd64                 5.9.3-0ubuntu3                                             amd64        Qt 5 designer module
ii  libqt5designercomponents5:amd64       5.9.3-0ubuntu3                                             amd64        Qt 5 Designer components module
ii  libqt5gui5:amd64                      5.9.3+dfsg-0ubuntu1                                        amd64        Qt 5 GUI module
ii  libqt5help5:amd64                     5.9.3-0ubuntu3                                             amd64        Qt 5 help module
ii  libqt5multimedia5:amd64               5.9.3-0ubuntu3                                             amd64        Qt 5 Multimedia module
ii  libqt5network5:amd64                  5.9.3+dfsg-0ubuntu1                                        amd64        Qt 5 network module
ii  libqt5opengl5:amd64                   5.9.3+dfsg-0ubuntu1                                        amd64        Qt 5 OpenGL module
ii  libqt5opengl5-dev:amd64               5.9.3+dfsg-0ubuntu1                                        amd64        Qt 5 OpenGL library development files
ii  libqt5positioning5:amd64              5.9.3+dfsg-0ubuntu1                                        amd64        Qt Positioning module
ii  libqt5printsupport5:amd64             5.9.3+dfsg-0ubuntu1                                        amd64        Qt 5 print support module
ii  libqt5qml5:amd64                      5.9.3-0ubuntu1                                             amd64        Qt 5 QML module
ii  libqt5quick5:amd64                    5.9.3-0ubuntu1                                             amd64        Qt 5 Quick library
ii  libqt5quickwidgets5:amd64             5.9.3-0ubuntu1                                             amd64        Qt 5 Quick Widgets library
ii  libqt5sensors5:amd64                  5.9.3-0ubuntu1                                             amd64        Qt Sensors module
ii  libqt5sql5:amd64                      5.9.3+dfsg-0ubuntu1                                        amd64        Qt 5 SQL module
ii  libqt5sql5-sqlite:amd64               5.9.3+dfsg-0ubuntu1                                        amd64        Qt 5 SQLite 3 database driver
ii  libqt5svg5:amd64                      5.9.3-0ubuntu1                                             amd64        Qt 5 SVG module
ii  libqt5svg5-dev:amd64                  5.9.3-0ubuntu1                                             amd64        Qt 5 SVG module development files
ii  libqt5test5:amd64                     5.9.3+dfsg-0ubuntu1                                        amd64        Qt 5 test module
ii  libqt5webchannel5:amd64               5.9.3-0ubuntu1                                             amd64        Web communication library for Qt
ii  libqt5widgets5:amd64                  5.9.3+dfsg-0ubuntu1                                        amd64        Qt 5 widgets module
ii  libqt5x11extras5:amd64                5.9.3-0ubuntu1                                             amd64        Qt 5 X11 extras
ii  libqt5xml5:amd64                      5.9.3+dfsg-0ubuntu1                                        amd64        Qt 5 XML module
ii  qt5-gtk-platformtheme:amd64           5.9.3+dfsg-0ubuntu1                                        amd64        Qt 5 GTK+ 3 platform theme
ii  qt5-qmake:amd64                       5.9.3+dfsg-0ubuntu1                                        amd64        Qt 5 qmake Makefile generator tool
ii  qt5-qmake-bin                         5.9.3+dfsg-0ubuntu1                                        amd64        Qt 5 qmake Makefile generator tool &#8212; binary file
ii  qtbase5-dev:amd64                     5.9.3+dfsg-0ubuntu1                                        amd64        Qt 5 base development files
ii  qtbase5-dev-tools                     5.9.3+dfsg-0ubuntu1                                        amd64        Qt 5 base development programs
ii  qttools5-dev-tools                    5.9.3-0ubuntu3                                             amd64        Qt 5 development tools
ii  qttranslations5-l10n                  5.9.3-0ubuntu1                                            all          translations for Qt 5 
```
```
wolf@wolf-wolf:~$ dpkg -l | grep ii | grep 5.9.2
ii  python3-cupshelpers                   1.5.9+20170825-0ubuntu1                                    all          Python utility modules around the CUPS printing system
ii  system-config-printer                 1.5.9+20170825-0ubuntu1                                    all          graphical interface to configure the printing system
ii  system-config-printer-common          1.5.9+20170825-0ubuntu1                                    all          backend and the translation files for system-config-printer
ii  system-config-printer-udev            1.5.9+20170825-0ubuntu1                                    amd64        Utilities to detect and configure printers automatically
```

would assume from that no qt5.9.2 :)

---

### Post by flocculant on 2017-12-21
thanks acheronuk on irc - qt5-style-plugins causing issues

---

### Post by acheronuk on 2017-12-21
> **flocculant said:**
> thanks acheronuk on irc - qt5-style-plugins causing issues

Indeed. Have passed that on to the people doing the actual Qt transition, to hopefully rebuild against new Qt.

---

### Post by acheronuk on 2017-12-21
Testing the amd64 .deb from [https://launchpad.net/ubuntu/+source/qtstyleplugins-src/5.0.0+git23.g335dbec-2build3](https://launchpad.net/ubuntu/+source/qtstyleplugins-src/5.0.0+git23.g335dbec-2build3)

Now no problem with qt5-style-plugins for Xubuntu

---

### Post by flocculant on 2017-12-22
I can concur with that :D

---

