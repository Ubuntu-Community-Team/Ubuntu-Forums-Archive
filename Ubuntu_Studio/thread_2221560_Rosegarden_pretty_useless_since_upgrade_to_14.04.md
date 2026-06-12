---
title: "Rosegarden pretty useless since upgrade to 14.04"
date: 2014-05-02
forum: Ubuntu Studio
---

### Post by Steve_Conrad on 2014-05-02
Rosegarden crashes at the drop of a hat since switching to ubuntustudio 14.04. Simple cut and paste operations cause a core dump. Kind of frustrating.

RG 13.06 is getting a bit old anyway, so thought I might recompile. Looks like the RG configure script is not compatible with Ubuntu's file layout though. 

Couldn't find the Qt libs until I specified the folder explicitly:

$ ./configure --with-qtlibdir=/usr/lib/x86_64-linux-gnu


Then it just ran afoul of zlib. Zlib? Seriously? 


checking for gzopen in -lz... no
configure: error: Failed to find required libz library

I've never had to sort out any trouble with such a core package before.  Is there some zlib-dev package I'm supposed to install or what? Not really finding anything suitable in the package manager.


This is just the tip of the iceberg as far as the configure file goes, and it's already looking like a serious pain in the ass with an awful lot of configure left to plow through.

Anyone had any luck trying to compile RG on Ubuntu lately?
Any input would be appreciated.

---

### Post by Steve_Conrad on 2014-05-02
By way of answering my own question, installing libghc-zlib-dev seems to put out that particular spot fire.
However, now it can't find any alsa libs, which seems a bit unlikely to me.

My initial point that RG has a config  script that doesn't know where to find things on Ubuntu remains valid.

---

