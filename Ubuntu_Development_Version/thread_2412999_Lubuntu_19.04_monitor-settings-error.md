---
title: "Lubuntu 19.04 monitor-settings-error"
date: 2019-02-19
forum: Ubuntu Development Version
---

### Post by VMC on 2019-02-19
```
$ /usr/bin/lxqt-config-monitor
 (0x7ffffe4183c0) Warning: Failed to request backend: "org.freedesktop.DBus.Error.Spawn.ChildExited" : "Process org.kde.KScreen exited with status 1"             
 (0x7ffffe4183c0) Debug: Connecting to KScreen...
 (0x7ffffe4183c0) Debug: Error: Config is invalid, probably backend couldn't load

```

There is a reference to this error if your using ".xinitrc", which I am, here:
[https://github.com/lxqt/lxqt/issues/932#issuecomment-270213947](https://github.com/lxqt/lxqt/issues/932#issuecomment-270213947)

But that didn't solve my problem. For one thing I don't have "xinitrc.d", but "xinitrc", which I changed to reflect in the script.

I recall having this error in the past, but I don't find any reference.

---

