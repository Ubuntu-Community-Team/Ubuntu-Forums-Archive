---
title: "I seem to have broken apt/dpkg"
date: 2004-12-09
forum: Repositories &amp; Backports
---

### Post by maus on 2004-12-09
Okay, so. Whenever I try to install or update something with apt, I get this error:

```
dpkg: error processing /var/cache/apt/archives/libc6_2.3.2.ds1-19_i386.deb (--unpack):
 unable to stat `./lib/libanl.so.1' (which I was about to install): Permission denied
``` 

I tried running sudo apt-get -f install, but to no avail. I don't think I have any broken packages, but that's what the signs seem to be pointing to... how to I diagnose/fix this?

---

### Post by adbak on 2004-12-09
If you have a broken package, open up Synaptic.
Click Edit, then Fix Broken Packages.

---

