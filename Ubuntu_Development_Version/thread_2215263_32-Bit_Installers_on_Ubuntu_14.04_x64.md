---
title: "32-Bit Installers on Ubuntu 14.04 x64"
date: 2014-04-05
forum: Ubuntu Development Version
---

### Post by oxsyn on 2014-04-05
I've noticed that in 14.04 x64 desktop, none of the statically compiled 32-bit installers (that have always worked in the past) will work anymore.
One of the applications is 010 Editor: [http://www.sweetscape.com/download/010EditorLinuxInstaller.tar.gz](http://www.sweetscape.com/download/010EditorLinuxInstaller.tar.gz)

When I run sudo ./010EditorInstaller - nothing happens. Some of the others segfault.
i386 multiarch support appeared to be enabled by default on my system - but I ran:
sudo dpkg -add-architecture i386 anyway.
dpkg --print-foreign-architectures outputs:
i386

... any ideas whats up?

---

