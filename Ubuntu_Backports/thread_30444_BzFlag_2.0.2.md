---
title: "BzFlag 2.0.2"
date: 2005-04-28
forum: Ubuntu Backports
---

### Post by Virtual DarKness on 2005-04-28
Hi,
I've tried to compile/backport BzFlag 2.0.2 from sid but I get this error:

> configure: WARNING: Client build has been requested, but GL is not fully available (missing gl.h)
     ... disabling client generation


I've searched but i didn't found anything  ](*,) 

any idea?
...I've the gl.h file in */usr/include/GL/*


bye,
Giovanni.

---

### Post by ep_ on 2005-07-20
I got the same error at first.

try this: ./configure --enable-debug LDFLAGS="-lpthread"

---

### Post by redlabour on 2005-07-20
[QUOTE=ep_]I got the same error at first.

try this: ./configure --enable-debug LDFLAGS="-lpthread"[/QUOTE]
 [http://www.ubuntuforums.org/showpost.php?p=262251&postcount=3](http://www.ubuntuforums.org/showpost.php?p=262251&postcount=3)

---

### Post by fourchannel on 2006-01-08
had problems with gl.h not being found to compile really slick screensavers. what finally fixed it for me, was to install GLUT and glut dev packages.

---

