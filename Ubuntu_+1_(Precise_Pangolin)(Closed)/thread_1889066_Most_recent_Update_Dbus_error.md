---
title: "Most recent Update Dbus error?"
date: 2011-11-30
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ventrical on 2011-11-30
I just updated Precise conversion module(64bit) and got this error:



Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Error org.freedesktop.DBus.Error.TimedOut: Activation of org.freedesktop.PackageKit timed out
ventrical@ventrical-Extensa-4420:~$

---

### Post by seeker5528 on 2011-12-01
```
sudo dpkg --purge gstreamer0.10-packagekit packagekit
```

Seems to take care of it.

Later, Seeker

---

### Post by FrDarryl on 2011-12-02
FWIW, I had to delete these three to get rid of that (recurring) DBus error:

sudo dpkg --purge kpackagekit apper packagekit

---

