---
title: "Install qgtkstyle, gtk+ theme for your qt 4 applications :D"
date: 2008-11-06
forum: The Cafe
---

### Post by wersdaluv on 2008-11-06
> Compiling:

You will need gtk2-x11-dev packages in addition to Qt 4.4. Provided you have already installed Qt 4.4 and GTK2 correctly, all you should have to do is this:

svn co svn://labs.trolltech.com/svn/styles/gtkstyle

cd gtkstyle/

qmake && make

sudo make install 
[http://labs.trolltech.com/page/Projects/Styles/GtkStyle](http://labs.trolltech.com/page/Projects/Styles/GtkStyle)

System->Preferences->QT 4 Settings, Select GTK as the GUI style, and File->Save.

For KDE4 applications, run System Settings from /usr/share/applications/kde4, go to Appearance, and Choose GTK as Widget Style.

---

### Post by etnlIcarus on 2008-11-06
Qgtkstyle is my favourite linux enhancement of the last year or so. I just wish more apps had been ported to Qt4 instead of 3 and didn't rely on kdelibs.

Still, VirtualBox and VLC look perfect so it's all good.

---

