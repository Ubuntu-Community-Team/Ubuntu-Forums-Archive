---
title: "Using Eclipse C++ toolchain on Linux"
date: 2009-07-22
forum: Ubuntu Dev Link Forum
---

### Post by iceman2 on 2009-07-22
Hello,
I want to use Eclipse to develop C++ projects on Linux. Particularly I want to modify stable and widely used open source projects using the Eclipse CDT. One of them is Intel Opencv  ( sourceforge.net/projects/opencvlibrary ) . There are tutorials to create simple c++ projects like here : [http://www.ibm.com/developerworks/opensource/library/os-eclipse-stlcdt/](http://www.ibm.com/developerworks/opensource/library/os-eclipse-stlcdt/) . 

I have seen plenty of tutorials for using Eclipse CDT to write programs in
OpenCv like here : [http://opencv.willowgarage.com/wiki/Eclipse](http://opencv.willowgarage.com/wiki/Eclipse) or
[http://tommy.chheng.com/development/windows_development_setup.html](http://tommy.chheng.com/development/windows_development_setup.html) . However i
want to use Eclipse to make changes to the OpenCv platform itself and compile it
from there. I really like many of Eclipse's features like :Syntax highlighting
,Outline ,Code assist, Code templates, Code history etc .. Would someone write a
small tutorial on how can one make a project in Eclipse from the OpenCv tarball
? I would use Eclipse CDT on Linux .

Can Eclipse CDT recognize Makefile as it can do for ant scripts?

---

### Post by Lawand on 2009-09-01
If you need help using CDT, after installing eclipse select: Help > Help Contents

The help system is pretty good.

---

### Post by dinxter on 2009-09-28
you can simply extract the tarball and import it into eclipse as a new project. but the plugin you want to make it build/compile is the highly useful linux-tools project. it contains an autotools support option for configure/make builds. As well as valgrind integration and some other good stuff
[http://www.eclipse.org/linuxtools/](http://www.eclipse.org/linuxtools/)

---

