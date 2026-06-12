---
title: "howto extract specific files/dirs from .deb package??"
date: 2005-06-23
forum: Repositories &amp; Backports
---

### Post by skoal on 2005-06-23
How do I extract specific files from .deb package, and *not* {re}install the whole package?

* problem: I installed my own Nvidia package using their installer (not Ubuntu packages).  It drops some GL header files in /usr/include/GL.  That's great for me as a developer, but not so great as a package maintainer for others wanting to use my 'libglfw-2.5.0.deb' package (aka - non Nvidia users).

These particular files come from the 'xlibmesa-gl-dev' package, and I do not want to reinstall that whole package (since it will overwrite my /usr/lib/libGL.{a,so} as well).

Suggestions? I just need to restore these header files: /usr/include/{gl.h,glx.h,glext.h,glxext.h}

thx.

\\//_

---

### Post by alred on 2005-06-23
you may try File Roller from the main menu :
[Applications] --> [Accesseries] --> [Archive Manager]

open the desired deb package
individual files usually reside in data.tar.gz
right click on the desired individual file and choose [extract]

it may be better to extract files to a temp scratch folder first then eventually copy them to your desired directory location 


that is how i uasually extract individual files though
hope this helps ...

good luck !

---

### Post by skoal on 2005-06-24
That worked great.  That 'file-roller' is a little gem for extracting .deb files, and for touching up my 'hybrid' package/source distro.  THanks for te help...

\\//_

---

