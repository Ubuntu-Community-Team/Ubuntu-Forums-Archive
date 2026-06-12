---
title: "glib-compile-schemas crashes"
date: 2017-08-25
forum: Ubuntu Development Version
---

### Post by FarJumper on 2017-08-25
One of last updates broke glib-compile-schemas, so all gnome applications which will get updates with a schema change are doomed (see [1]) . Nautilus - as one of most visible - crashes with error: ```
Settings schema 'org.gnome.nautilus.preferences' does not contain a key named 'fts-default'.
```

[1] [https://bugs.launchpad.net/ubuntu/+source/glib2.0/+bug/1711545](https://bugs.launchpad.net/ubuntu/+source/glib2.0/+bug/1711545)

---

