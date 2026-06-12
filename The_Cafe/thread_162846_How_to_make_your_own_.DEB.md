---
title: "How to make your own .DEB?"
date: 2006-04-19
forum: The Cafe
---

### Post by tikal26 on 2006-04-19
I am wondering how do you make your own .deb packages. I jsut starting thinking about that since some Debian packages can break Ubuntu, but I always hear people sayinf that ubuntu uses Debian and their packages as a base.

---

### Post by krusbjorn on 2006-04-19
Easiest way is to "sudo apt-get install checkinstall".
And then, when you have run "./configure" and "make" on your source code, do "checkinstall" instead of "make install".

---

### Post by John.Michael.Kane on 2006-04-19
[http://www.debian.org/doc/FAQ/ch-pkg_basics.en.html](http://www.debian.org/doc/FAQ/ch-pkg_basics.en.html)
[http://www.debian.org/doc/maint-guide/](http://www.debian.org/doc/maint-guide/)
[http://www.maemo.org/platform/docs/howtos/howto_making_an_application_package.html](http://www.maemo.org/platform/docs/howtos/howto_making_an_application_package.html)
[http://www.ubuntuforums.org/showthread.php?t=2356](http://www.ubuntuforums.org/showthread.php?t=2356)

---

