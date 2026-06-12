---
title: "MySQL init script gone, breaks ZoneMinder install / upgrade"
date: 2013-02-22
forum: Ubuntu Development Version
---

### Post by tekoholix on 2013-02-22
I've 2 machines running 64-bit Raring.  On one, I had ZoneMinder installed and running.  On the other, just yesterday, I decided to install ZM.  Coincidentally, it seems, both systems received updates that removed the old /etc/init.d/mysql script, and caused the ZM install and an apparent upgrade to fail with the following:

```
Setting up zoneminder (1.25.0-4ubuntu1) ...
invoke-rc.d: unknown initscript, /etc/init.d/mysql not found.
dpkg: error processing zoneminder (--configure):
 subprocess installed post-installation script returned error exit status 100
Errors were encountered while processing:
 zoneminder
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Is this a known issue?  Even better, might it be easily worked around, until a fix is released?

---

