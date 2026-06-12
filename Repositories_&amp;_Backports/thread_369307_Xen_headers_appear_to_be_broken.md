---
title: "Xen headers appear to be broken"
date: 2007-02-24
forum: Repositories &amp; Backports
---

### Post by SeanHodges on 2007-02-24
Hello, I'm having a problem compiling my Wireless network driver for the Xen-enabled kernel (xen-image-xen0-2.6.17-6-generic-xen0). The header package appears to be broken, there are some directories/files missing, and it is causing my build to fail.

this is what I see:

sean@metis:/$ ls /usr/src/xen-headers-2.6.17-6/
arch  block  crypto  drivers  fs  include  init  ipc  kernel  lib  Makefile  mm  net  security  sound  usr

sean@metis:/$ ls /usr/src/linux-headers-2.6.17-11
arch  block  crypto  debian  drivers  fs  include  init  ipc  kernel  lib  linux-headers.revision  Makefile  mm  net  scripts  security  sound  usr

Does anyone have an idea where I need to go with this?

---

