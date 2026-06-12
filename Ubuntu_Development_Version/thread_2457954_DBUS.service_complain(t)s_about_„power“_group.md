---
title: "DBUS.service complain(t)s about „power“ group"
date: 2021-02-13
forum: Ubuntu Development Version
---

### Post by zika on 2021-02-13
There is solution for that```
/usr/bin/sudo /usr/sbin/groupadd power
/usr/bin/sudo /usr/sbin/usermod --groups power --append $USER
```Saturday's fiddling...

---

