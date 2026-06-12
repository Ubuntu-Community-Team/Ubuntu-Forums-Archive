---
title: "files: mod_rewrite.c and mod_rewrite.h"
date: 2008-02-17
forum: Server Platforms
---

### Post by luapnor on 2008-02-17
mod_rewrite.c and mod_rewrite.h

I can't seem to find these files on apache in ubuntu.

Can someone tell me if this is because I'm not searching
good enough or because these files are not part of apache2 in ubuntu.

thanx in advance

---

### Post by astrotech226 on 2008-02-17
Not sure what you are trying to do, but you probably need the Apache source.  install "apache2-src" from Synaptic and you will get a gzipped tarball /usr/src/apache2.tar.gz.

```
cd /usr/src; sudo tar xvfz apache2.tar.gz
```

Your files are now located here:

/usr/src/apache2/modules/mappers/mod_rewrite.h
/usr/src/apache2/modules/mappers/mod_rewrite.c

---

### Post by luapnor on 2008-02-18
Thanks,

this gave me the files indeed.
btw, I'm trying to something described here:

[http://arkiv.netbsd.se/?ml=apache-httpd-dev&a=2006-12&t=2872446](http://arkiv.netbsd.se/?ml=apache-httpd-dev&a=2006-12&t=2872446)

---

