---
title: "apt-getting python2.4 fails on configure"
date: 2005-04-14
forum: Repositories &amp; Backports
---

### Post by Guru3 on 2005-04-14
Everything goes fine until the configuration of the package python2.4 (and subsequent pythong related packages.) Here's the error:```
Setting up python2.4 (2.4.1-0) ...
Compiling python modules in /usr/lib/python2.4 ...
/var/lib/dpkg/info/python2.4.postints: line 16: 17343 Segmentation fault      /usr/bin/python2.4 /usr/lib/python2.4/compileall.py -q $i
dpkg: error processing python2.4 (--configure):
 subprocess post-installation script returned error exit status 139
Errors were encountered while processing:
 python2.4
```Any help would be apreciated. I'm on powerpc, btw. Thnx.

---

### Post by paulle on 2005-04-14
try    apt-get install -f        this worked for me.

---

