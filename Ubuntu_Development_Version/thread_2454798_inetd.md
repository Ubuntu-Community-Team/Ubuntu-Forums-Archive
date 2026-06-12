---
title: "inetd"
date: 2020-12-06
forum: Ubuntu Development Version
---

### Post by Frogs Hair on 2020-12-06
Saw this message during an update and all internet applications including update,mail, and browsers seem to be working fine. Any need for concern ? 

[inetd]("https://en.wikipedia.org/wiki/Inetd")

```
update-inetd: warning: cannot add service, /etc/inetd.conf does not exist
saned.socket is a disabled or a static unit not running, not starting it.

```

---

### Post by dino99 on 2020-12-06
Devs should remove their debugging output before packaging the final package (here: sane)  ;)

Nothing to worry, its a simple info.

---

### Post by Frogs Hair on 2020-12-06
Thanks

---

