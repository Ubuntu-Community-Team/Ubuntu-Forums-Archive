---
title: "Request: Celestia 1.3.2"
date: 2005-06-19
forum: Ubuntu Backports
---

### Post by ioliver on 2005-06-19
This can be built from sources, but you need loads of dev libs to manage it.

When built, it's working 99.5% OK for me on Hoary.  The missing 0.5% is that the tab key doesn't cycle through options to complete the names of objects after hitting Enter.

I'm happy to help test a backport - I can easily do a clean Hoary install specially for this.

Ian

---

### Post by jromer on 2005-07-01
I'm new to Debian/Ubuntu/Kubuntu but I did successfully install .deb package of  Celestia 1.3.2 on Kubuntu 5.04. from the following...

[http://packages.debian.org/unstable/kde/celestia](http://packages.debian.org/unstable/kde/celestia)

I download the following and the below dependencies into a locally created repository and it all works well. (I couldn't use an operating system that couldn't run Celestia :)

 Depends: libc6 (>= 2.3.2.ds1-21)  
 Depends: libfontconfig1 (>= 2.3.0) 
 Depends: libidn11 (>= 0.5.13)
 Depends: libqt3c102-mt (>= 3:3.3.4)

---

### Post by ulisse on 2005-07-17
I have built Celestia from source, but it doesn't start.
It says "art_render_invoke: no image source given" and exits.
If I run it as root, i get segfault.
I get the same thing with the 1.3.0 package in the repository.
Maybe could it be due to my ATI drivers?

---

