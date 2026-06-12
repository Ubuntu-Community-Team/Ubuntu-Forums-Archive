---
title: "Creating 32-bit Python run-time on 64-bit server?"
date: 2010-02-17
forum: Server Platforms
---

### Post by mikko.ohtamaa on 2010-02-17
Hi,

Some server-side Python problems have huge memory usage. This is especially true for 64-bit platforms, since Python programs are all about references and objects and 64-bit effectively doubles reference size.

Example:

[http://jstahl.org/archives/2010/01/24/plone-4-uses-29-less-memory-than-plone-3-thanks-python-2-6/](http://jstahl.org/archives/2010/01/24/plone-4-uses-29-less-memory-than-plone-3-thanks-python-2-6/)

How one could create 32-bit Python run-time enviroment e.g. to run on 64-bit Ubuntu VPS, so that the memory usage could be easily reduced? This also could be faster, due to better memory cache use.

---

