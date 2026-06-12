---
title: "Problems with QjackCtl"
date: 2013-05-28
forum: Ubuntu Studio
---

### Post by rva1945 on 2013-05-28
(Ubuntu 12.04)

After checking No memory lock (just for trying as I was getting some messages about invalid parameters) in setup, qjackctl crashes. I uninstalled it (apt-get uninstall--purge), then I installed it again, and the problem is still there, the option is ckecked but qjackctl seems to be frozen so I can't change it (I guess that is the problem).

So, is there any config file to be edited?

Thanks

---

### Post by zequence on 2013-05-29
The user config file for Qjackctl is at:

```
~/.config/rncbc.org/QjackCtl.conf
```

When you purge a package, only system wide settings might get purged, not user settings, so you still need to delete the user settings manually.

---

### Post by rva1945 on 2013-05-29
To my surprise, I installed Rakarrack again, the first time you launch it it seems to load jack automatically, then it asks for jack to be launched, and everything seems to be working again.

---

