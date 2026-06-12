---
title: "Resuming Suspend Fails When Virtualbox VM Is Running"
date: 2012-12-20
forum: Virtualisation
---

### Post by user2037 on 2012-12-20
Anyone know how to fix resume failing? It works when a VM is not running.

EDIT:
Xubuntu 12.04, Virtualbox 4.1.2 and 4.2.6
Susending with:
```

dbus-send --print-reply --system --dest=org.freedesktop.UPower \
  /org/freedesktop/UPower org.freedesktop.UPower.Suspend

```

---

