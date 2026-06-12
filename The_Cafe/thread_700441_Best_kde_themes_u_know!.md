---
title: "Best kde themes u know!"
date: 2008-02-18
forum: The Cafe
---

### Post by snakeeyes on 2008-02-18
Hi, which r the best kde themes u have seen, can u post a link cause I really want to find some good ones other than visiting kde-look.org cause searching there takes a long time and is nothing too special.

---

### Post by lzfy on 2008-02-18
[QTQurve]("http://www.kde-look.org/content/show.php/QtCurve+%28KDE3%29+Kubuntu+Gutsy+package?content=40920")

[Domino]("http://www.kde-look.org/content/show.php/Domino+Deb+package+for+Kubuntu?content=74031")

There are also many schemes for this two styles at kde-look.org

---

### Post by Northsider on 2008-02-18
Can you get a preview of those themes?

---

### Post by DeadSuperHero on 2008-02-18
Bespin is an up-and-coming theme for KDE4, it looks amazing.

---

### Post by snakeeyes on 2008-02-18
yeah bespin is good as well, I doubt anyone will bother with anything other than the oxygen style or bespin when kde 4 becomes stable enough to use.

---

### Post by Drone4four on 2008-04-06
There is a package for Bespin in the Hardy repos, but not for Gutsy. So I'm trying to compile Bespin from source on Gutsy and am running into an error:  ```
mary@ubuntu:~/cloudcity$ ./configure 
-e \e[0;34;47m
Welcome to Bespins interactive configurator\e[m
-e \e[0;31;47m
Warning: Qt4 could not be found in usual locations, pass it here\e[m
Path to Qt4: 
```
What directory is Qt4 installed into? ```
mary@ubuntu:~/cloudcity$ dpkg -L libqt4-core 
/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/libqt4-core
/usr/share/doc/libqt4-core/changelog.Debian.gz
/usr/share/doc/libqt4-core/copyright
/usr/share/doc/libqt4-core/changelog.gz
/usr/share/doc/libqt4-core/GPL_EXCEPTION_ADDENDUM.TXT.gz
/usr/share/qt4
/usr/share/qt4/translations
/usr/share/qt4/translations/assistant_de.qm
/usr/share/qt4/translations/assistant_ja.qm
/usr/share/qt4/translations/assistant_pl.qm
/usr/share/qt4/translations/assistant_zh_CN.qm
/usr/share/qt4/translations/designer_de.qm
/usr/share/qt4/translations/designer_ja.qm
/usr/share/qt4/translations/designer_pl.qm
/usr/share/qt4/translations/designer_zh_CN.qm
/usr/share/qt4/translations/linguist_ja.qm
/usr/share/qt4/translations/linguist_pl.qm
/usr/share/qt4/translations/linguist_zh_CN.qm
/usr/share/qt4/translations/qt_ar.qm
/usr/share/qt4/translations/qt_de.qm
/usr/share/qt4/translations/qt_es.qm
/usr/share/qt4/translations/qt_fr.qm
/usr/share/qt4/translations/qt_iw.qm
/usr/share/qt4/translations/qt_ja_jp.qm
/usr/share/qt4/translations/qt_pl.qm
/usr/share/qt4/translations/qt_pt.qm
/usr/share/qt4/translations/qt_ru.qm
/usr/share/qt4/translations/qt_sk.qm
/usr/share/qt4/translations/qt_sv.qm
/usr/share/qt4/translations/qt_uk.qm
/usr/share/qt4/translations/qt_zh_CN.qm
/usr/share/qt4/translations/qtconfig_pl.qm
/usr/share/qt4/translations/qtconfig_zh_CN.qm
/usr/share/qt4/translations/qvfb_pl.qm
/usr/share/qt4/translations/qvfb_zh_CN.qm
/usr/share/lintian
/usr/share/lintian/overrides
/usr/share/lintian/overrides/libqt4-core
/usr/lib
/usr/lib/libQtCore.so.4.3.2
/usr/lib/libQtNetwork.so.4.3.2
/usr/lib/libQtXml.so.4.3.2
/usr/lib/libQtTest.so.4.3.2
/usr/lib/libQtDBus.so.4.3.2
/usr/lib/libQtScript.so.4.3.2
/usr/bin
/usr/bin/qdbus
/usr/lib/libQtCore.so.4
/usr/lib/libQtCore.so.4.3
/usr/lib/libQtNetwork.so.4
/usr/lib/libQtNetwork.so.4.3
/usr/lib/libQtXml.so.4
/usr/lib/libQtXml.so.4.3
/usr/lib/libQtTest.so.4
/usr/lib/libQtTest.so.4.3
/usr/lib/libQtDBus.so.4
/usr/lib/libQtDBus.so.4.3
/usr/lib/libQtScript.so.4
/usr/lib/libQtScript.so.4.3

```
So I enter the dir, /usr/lib and it gives me this:```
Path to Qt4: /usr/lib
Path to Qt4: 
-e \e[0;31;47m
Warning: Qt4 not found - exiting\e[m
mary@ubuntu:~/cloudcity$ 
```

How do I install this program? Am I entering the correct location that qt is installed in? Is there a way to download the package from  the hardy repos on the web?

---

### Post by tubasoldier on 2008-04-06
Mandriva 2008 has a nice theme. They call it LaOra. I'm not sure where to get it other than Mandriva. They probably have it in their repositories and it wouldn't take much to get it installed in Ubuntu.

---

### Post by FuturePilot on 2008-04-06
> **Drone4four said:**
> There is a package for Bespin in the Hardy repos, but not for Gutsy. So I'm trying to compile Bespin from source on Gutsy and am running into an error:  ```
mary@ubuntu:~/cloudcity$ ./configure 
-e \e[0;34;47m
Welcome to Bespins interactive configurator\e[m
-e \e[0;31;47m
Warning: Qt4 could not be found in usual locations, pass it here\e[m
Path to Qt4: 
```
What directory is Qt4 installed into? ```
mary@ubuntu:~/cloudcity$ dpkg -L libqt4-core 
/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/libqt4-core
/usr/share/doc/libqt4-core/changelog.Debian.gz
/usr/share/doc/libqt4-core/copyright
/usr/share/doc/libqt4-core/changelog.gz
/usr/share/doc/libqt4-core/GPL_EXCEPTION_ADDENDUM.TXT.gz
/usr/share/qt4
/usr/share/qt4/translations
/usr/share/qt4/translations/assistant_de.qm
/usr/share/qt4/translations/assistant_ja.qm
/usr/share/qt4/translations/assistant_pl.qm
/usr/share/qt4/translations/assistant_zh_CN.qm
/usr/share/qt4/translations/designer_de.qm
/usr/share/qt4/translations/designer_ja.qm
/usr/share/qt4/translations/designer_pl.qm
/usr/share/qt4/translations/designer_zh_CN.qm
/usr/share/qt4/translations/linguist_ja.qm
/usr/share/qt4/translations/linguist_pl.qm
/usr/share/qt4/translations/linguist_zh_CN.qm
/usr/share/qt4/translations/qt_ar.qm
/usr/share/qt4/translations/qt_de.qm
/usr/share/qt4/translations/qt_es.qm
/usr/share/qt4/translations/qt_fr.qm
/usr/share/qt4/translations/qt_iw.qm
/usr/share/qt4/translations/qt_ja_jp.qm
/usr/share/qt4/translations/qt_pl.qm
/usr/share/qt4/translations/qt_pt.qm
/usr/share/qt4/translations/qt_ru.qm
/usr/share/qt4/translations/qt_sk.qm
/usr/share/qt4/translations/qt_sv.qm
/usr/share/qt4/translations/qt_uk.qm
/usr/share/qt4/translations/qt_zh_CN.qm
/usr/share/qt4/translations/qtconfig_pl.qm
/usr/share/qt4/translations/qtconfig_zh_CN.qm
/usr/share/qt4/translations/qvfb_pl.qm
/usr/share/qt4/translations/qvfb_zh_CN.qm
/usr/share/lintian
/usr/share/lintian/overrides
/usr/share/lintian/overrides/libqt4-core
/usr/lib
/usr/lib/libQtCore.so.4.3.2
/usr/lib/libQtNetwork.so.4.3.2
/usr/lib/libQtXml.so.4.3.2
/usr/lib/libQtTest.so.4.3.2
/usr/lib/libQtDBus.so.4.3.2
/usr/lib/libQtScript.so.4.3.2
/usr/bin
/usr/bin/qdbus
/usr/lib/libQtCore.so.4
/usr/lib/libQtCore.so.4.3
/usr/lib/libQtNetwork.so.4
/usr/lib/libQtNetwork.so.4.3
/usr/lib/libQtXml.so.4
/usr/lib/libQtXml.so.4.3
/usr/lib/libQtTest.so.4
/usr/lib/libQtTest.so.4.3
/usr/lib/libQtDBus.so.4
/usr/lib/libQtDBus.so.4.3
/usr/lib/libQtScript.so.4
/usr/lib/libQtScript.so.4.3

```
So I enter the dir, /usr/lib and it gives me this:```
Path to Qt4: /usr/lib
Path to Qt4: 
-e \e[0;31;47m
Warning: Qt4 not found - exiting\e[m
mary@ubuntu:~/cloudcity$ 
```

How do I install this program? Am I entering the correct location that qt is installed in? Is there a way to download the package from  the hardy repos on the web?

You probably need the qt4 *-dev packages.

---

### Post by Drone4four on 2008-04-06
I installed a lot of kde4 and qt4 packages with -dev endings.  I am getting the same error messages.

---

### Post by Drone4four on 2008-04-06
In fact, I installed every pacakge that begins with qt4:```
drone4four@ubuntu:~/Desktop/cloudcity$ sudo apt-get install qt4-
qt4-designer   qt4-dev-tools  qt4-doc        qt4-qtconfig 
```

---

### Post by chucky chuckaluck on 2008-04-06
knifty is my favorite window decoration and domino is my favorite style. i always tailor my color schemes to match the wallpaper. when i get it just right, it's almost as good as wmii.

---

### Post by Drone4four on 2008-04-06
what's wmii?

---

### Post by SunnyRabbiera on 2008-04-06
I like QTcurve, it is so versatile :D

---

### Post by chucky chuckaluck on 2008-04-07
> **Drone4four said:**
> what's wmii?

another window manager.

---

### Post by Drone4four on 2008-04-11
Bump.  Can anyone reply to my post below?> **Drone4four said:**
> There is a package for Bespin in the Hardy repos, but not for Gutsy. So I'm trying to compile Bespin from source on Gutsy and am running into an error:  ```
mary@ubuntu:~/cloudcity$ ./configure 
-e \e[0;34;47m
Welcome to Bespins interactive configurator\e[m
-e \e[0;31;47m
Warning: Qt4 could not be found in usual locations, pass it here\e[m
Path to Qt4: 
```
What directory is Qt4 installed into? ```
mary@ubuntu:~/cloudcity$ dpkg -L libqt4-core 
/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/libqt4-core
/usr/share/doc/libqt4-core/changelog.Debian.gz
/usr/share/doc/libqt4-core/copyright
/usr/share/doc/libqt4-core/changelog.gz
/usr/share/doc/libqt4-core/GPL_EXCEPTION_ADDENDUM.TXT.gz
/usr/share/qt4
/usr/share/qt4/translations
/usr/share/qt4/translations/assistant_de.qm
/usr/share/qt4/translations/assistant_ja.qm
/usr/share/qt4/translations/assistant_pl.qm
/usr/share/qt4/translations/assistant_zh_CN.qm
/usr/share/qt4/translations/designer_de.qm
/usr/share/qt4/translations/designer_ja.qm
/usr/share/qt4/translations/designer_pl.qm
/usr/share/qt4/translations/designer_zh_CN.qm
/usr/share/qt4/translations/linguist_ja.qm
/usr/share/qt4/translations/linguist_pl.qm
/usr/share/qt4/translations/linguist_zh_CN.qm
/usr/share/qt4/translations/qt_ar.qm
/usr/share/qt4/translations/qt_de.qm
/usr/share/qt4/translations/qt_es.qm
/usr/share/qt4/translations/qt_fr.qm
/usr/share/qt4/translations/qt_iw.qm
/usr/share/qt4/translations/qt_ja_jp.qm
/usr/share/qt4/translations/qt_pl.qm
/usr/share/qt4/translations/qt_pt.qm
/usr/share/qt4/translations/qt_ru.qm
/usr/share/qt4/translations/qt_sk.qm
/usr/share/qt4/translations/qt_sv.qm
/usr/share/qt4/translations/qt_uk.qm
/usr/share/qt4/translations/qt_zh_CN.qm
/usr/share/qt4/translations/qtconfig_pl.qm
/usr/share/qt4/translations/qtconfig_zh_CN.qm
/usr/share/qt4/translations/qvfb_pl.qm
/usr/share/qt4/translations/qvfb_zh_CN.qm
/usr/share/lintian
/usr/share/lintian/overrides
/usr/share/lintian/overrides/libqt4-core
/usr/lib
/usr/lib/libQtCore.so.4.3.2
/usr/lib/libQtNetwork.so.4.3.2
/usr/lib/libQtXml.so.4.3.2
/usr/lib/libQtTest.so.4.3.2
/usr/lib/libQtDBus.so.4.3.2
/usr/lib/libQtScript.so.4.3.2
/usr/bin
/usr/bin/qdbus
/usr/lib/libQtCore.so.4
/usr/lib/libQtCore.so.4.3
/usr/lib/libQtNetwork.so.4
/usr/lib/libQtNetwork.so.4.3
/usr/lib/libQtXml.so.4
/usr/lib/libQtXml.so.4.3
/usr/lib/libQtTest.so.4
/usr/lib/libQtTest.so.4.3
/usr/lib/libQtDBus.so.4
/usr/lib/libQtDBus.so.4.3
/usr/lib/libQtScript.so.4
/usr/lib/libQtScript.so.4.3

```
So I enter the dir, /usr/lib and it gives me this:```
Path to Qt4: /usr/lib
Path to Qt4: 
-e \e[0;31;47m
Warning: Qt4 not found - exiting\e[m
mary@ubuntu:~/cloudcity$ 
```

How do I install this program? Am I entering the correct location that qt is installed in? Is there a way to download the package from  the hardy repos on the web?

---

### Post by GeneralZod on 2008-04-11
> **Drone4four said:**
> Bump.  Can anyone reply to my post below?

> 
In fact, I installed every pacakge that begins with qt4:


The important one doesn't begin with "qt4" ;) Make absolutely sure that you have libqt4-dev installed; if you do, I'd suggest contacting the Bespin author.

---

