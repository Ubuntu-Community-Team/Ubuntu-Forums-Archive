---
title: "Why are Linux and OSX programs larger?"
date: 2006-05-06
forum: The Cafe
---

### Post by BWF89 on 2006-05-06
I've noticed this with alot of the programs that are cross-platform. Does anyone know why?

Firefox download page:
Windows 4.9MB
Linux 8.1MB
Mac OSX 16.0MB

OpenOffice download page:
Windows (without JRE) 92.1MB
Linux 119.62MB
Mac OSX 135.6MB

---

### Post by tuxcantfly on 2006-05-06
Really, it's due to the libraries. Windows has only one major library: the windows library, which is built in, so nobody has to bundle them into the program. But, if you notice, a lot of cross-platform applications bundle lots of additional libraries for linux and osx instead of using the native ones like they do in windows, so the libraries make the programs larger. However, linux applications are tiny if they use native libraries; for example, KDE applications are just a few megabytes if you already have the KDE libraries. Since KDE isn't available for native windows, and kde-cygwin is impractical, they can't use KDE libraries in firefox or openoffice, so they use their own, making the linux and osx applications huge.

---

### Post by prizrak on 2006-05-06
They are not. OOO and FF are pretty bad examples. If you look at other programs for Linux vs Windows, the former are much smaller than the latter while doing the same thing.

---

