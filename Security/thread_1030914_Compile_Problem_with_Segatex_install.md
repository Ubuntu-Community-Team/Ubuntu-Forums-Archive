---
title: "Compile Problem with Segatex install"
date: 2009-01-04
forum: Security
---

### Post by BGFG on 2009-01-04
After seeing a tutorial on apparmor and doing some more researchin to linux security, I'm trying out SELinux and Segatex as a project of mine. Having problems with the compile, I've bolded the problem area.
Any thoughts ?

```

g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_QT3SUPPORT_LIB -DQT3_SUPPORT -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4/Qt3Support -I/usr/include/qt4/Qt3Support -I/usr/include/qt4 -I. -I. -o mainwindow.o mainwindow.cpp
In file included from mainwindow.cpp:45:
[B]segatex_state.h:27:29: error: selinux/selinux.h: No such file or directory
segatex_state.h:28:38: error: selinux/get_default_type.h: No such file or directory[/B]
make: *** [mainwindow.o] Error 1

```


These are the instructions i followed
```

###########################################
# How to compile segatex
###########################################
$cd src
$qmake-qt4 segatex.pro
or simply 
$qmake-qt4
$vim Makefile

Add -lselinux to LIBS line.

$make
Now you get the binary "segatex" in src directory.
###########################################

```

This is how i installed SELinux:
```

sudo apt-get install selinux

```

---

### Post by Xbehave on 2009-04-07
I've not used either but from the looks of the error, do you have libselinux1-dev installed? you may also need libqt4-dev and qt4-dev-tools

---

### Post by bodhi.zazen on 2009-04-07
To be honest, if you are interested in selinux I suggest you try Fedora.

Installing and configuring selinux on Ubuntu, in my experience, has been difficult.

---

### Post by YyYo on 2009-05-09
It seems that some files(headers files) are missing in your download directories: selinux.h, get_default_type.h  

The installation command: **sudo apt-get install selinux**
seems fine. I already insalled SELinux in the same way; type "**sestatus**" to see SELinux status.

If you are looking for GUI to SELinux check out SEAdmin. [https://sourceforge.net/projects/seadmin](https://sourceforge.net/projects/seadmin) 
or search **"SEAdmin"** in sourceforge.net site

Note: One of the reason I developed it, because there is no GUI tool for SELinux to Ubuntu and other Linux Distribution instead of Fedora and RedHat

---

### Post by BGFG on 2009-05-10
Thanks for the replies, I sincerely thought this was dead. I've since installed Jaunty and removed Segatex, but will attempt to re-implement on your advice or simply try SEadmin.

@bodhi.zazen, maybe for F11 :)

---

