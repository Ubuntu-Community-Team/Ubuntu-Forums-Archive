---
title: "Qt library problem: linked by .conf file in ld.so.conf.d"
date: 2013-08-10
forum: Ubuntu Application Development
---

### Post by nhanlm0601 on 2013-08-10
I have problem while installing the program rthlibs. I have linked the library of Qt5.1.0 with the standard library via this command: 
```
sudo sh -c "echo /usr/local/Qt5.1.0/5.1.0/gcc_64/lib > /etc/ld.so.conf.d/qt5.conf"

```and then
```
sudo ldconfig -v
```
which shows the library already linked. However the rthlibs program (the one I want to install) complain:

```
rthlibs depends on libdcmtk2 (>= 3.6.0); however:
  Package libdcmtk2 is not installed.
 rthlibs depends on liblog4cxx10 (>= 0.10.0); however:
  Package liblog4cxx10 is not installed.
 rthlibs depends on libqt5widgets5 (>= 5.0.1); however:
  Package libqt5widgets5 is not installed.
 rthlibs depends on libqt5core5 (>= 5.0.1); however:
  Package libqt5core5 is not installed.
 rthlibs depends on libqt5core5 (>= 5.0.1); however:
  Package libqt5core5 is not installed.
 rthlibs depends on libqt5opengl5 (>= 5.0.1); however:
  Package libqt5opengl5 is not installed.
 rthlibs depends on libatlas3gf-base (>= 3.8.4); however:
  Package libatlas3gf-base is not installed.
 rthlibs depends on libqhull5 (>= 2009.1-2); however:
  Package libqhull5 is not installed.
 rthlibs depends on libqt5script5 (>= 5.0.1); however:
  Package libqt5script5 is not installed.
 rthlibs depends on libqt5sql5 (>= 5.0.1); however:
  Package libqt5sql5 is not installed.
 rthlibs depends on
dpkg: error processing rthlibs (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sbwavegen:
 sbwavegen depends on libgnustep-base1.24 (>= 1.24.0); however:
  Package libgnustep-base1.24 is not installed.
 sbwavegen depends on libgnustep-gui0.22 (>= 0.22.0); however:
  Package libgnustep-gui0.22 is not installed.

```

I search the library by using sudo ldconfig -v again and notice that some library (already linked and shown up) is somehow similar to the one "rthlibs" complains.
E.g:
libQt5Widgets.so.5
libQt5Core.so.5
libQt5OpenGL.so.5 
....



Please help, it is really frustrated :( :( :(

---

### Post by steeldriver on 2013-08-10
I think you're confusing *libraries* and *packages*

When you install a package like rthlibs via the apt package management system, as far as I know it doesn't look directly at what individual *libraries* you have installed on the system - instead, it looks at what prerequisite *packages* you have already installed. So, for example, if you installed the Qt5 libraries by building them from source, then apt-get will not know that those dependencies are satisfied, and will still want to install the packages listed in the 'depends' section of the rthlib package. If those packages contain versions of libraries that conflict with the ones already on your system, then apt-get may not be able to resolve those dependencies and the installation will fail.

---

### Post by nhanlm0601 on 2013-08-10
[SOLVED] please delete this thread as I solved this problem. Thanks

---

### Post by nhanlm0601 on 2013-08-10
Hi steeldriver,
It is interesting to know more about this. So do you know how to tell the apt-get to recognize the dependencies ? Please correct me if I'm talking nonsense as I am new to Ubuntu and this whole idea of packages and libraries

---

