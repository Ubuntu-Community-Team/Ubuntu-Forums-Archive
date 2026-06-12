---
title: "installing module not as root to diff location"
date: 2010-05-17
forum: Server Platforms
---

### Post by xkaliburx on 2010-05-17
Using ZenOSS for some server monitoring and one dependency is a python-pgsql module.  I did install via apt but learned that the app has and uses it's own python and python directory.  When I issue a which python it shows;
/usr/local/zenoss/python/bin/python
and a python -V gives me 
Python 2.4.4
which is should.

So not being a 'python' guy and have spent 2+ day's reading, how do I install a module (python-pgsql) as a non-root person to a non-standard place?  Are python mod's like libpqmodule.so just like an apache mod that I can just stick in the module folder, restart and magically it works?

If not, can you download the .deb, somehow install that way?

---

