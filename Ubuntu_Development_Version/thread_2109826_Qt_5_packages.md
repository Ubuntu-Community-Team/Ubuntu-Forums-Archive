---
title: "Qt 5 packages?"
date: 2013-01-28
forum: Ubuntu Development Version
---

### Post by kernco on 2013-01-28
As far as I can tell, there are no Qt 5 packages for Ubuntu, Qt 4 is still the only one available. Are Qt 5 packages planned to be available before Raring Ringtail is released? Will they be made available on older releases?

---

### Post by jbicha on 2013-01-28
I don't know about your first question (except that it would need to land by FeatureFreeze unless the Release Team gives an exception) but the answer to the second question is probably not as there isn't anything that needs it (someone may make it available in a PPA though).

---

### Post by moma on 2013-01-29
Hello,
I do not know about QT5.
I have started to learn QT/QML to port my (ancient) [calc...]("http://www.futuredesktop.com/") from Android to Ubuntu Phone and TV.

This laptop runs Ubuntu 13.04 daily.

The installation guide ([http://developer.ubuntu.com/get-started/gomobile/](http://developer.ubuntu.com/get-started/gomobile/) ) partly failed in 13.04, but all QT/QML things seems to work right.

Bug report: [https://bugs.launchpad.net/ubuntu-ui-toolkit/+bug/1104311](https://bugs.launchpad.net/ubuntu-ui-toolkit/+bug/1104311)

I have tested, 
$ /usr/bin/qtdemo
$ ls -lR /usr/lib/qt4/demos/qtdemo

And QML-samples in 
$ ls -lR /usr/lib/qt4/demos/declarative
$ qmlviewer /usr/lib/qt4/demos/declarative/snake/qml/snake/snake.qml 

Works fine in 13.04 daily.
Let^s hope they update the dev-guide for Ubuntu Phone soon.

And Ubuntu SDK is almost ready too, with awesome feature to remote-test apps on phones.
Ref: [http://developer.ubuntu.com/2013/01/develop-locally-run-remotely/](http://developer.ubuntu.com/2013/01/develop-locally-run-remotely/)

The article mensions this QT5 PPA:
[https://launchpad.net/~canonical-qt5-edgers](https://launchpad.net/~canonical-qt5-edgers)

---

### Post by dino99 on 2013-01-29
will probably see it landing soon into the repo

[https://launchpad.net/~canonical-qt5-edgers/+archive/qt5-beta1?field.series_filter=raring](https://launchpad.net/~canonical-qt5-edgers/+archive/qt5-beta1?field.series_filter=raring)

---

### Post by forcecore on 2013-01-30
Does not QT5 require 3D GPU too?

---

