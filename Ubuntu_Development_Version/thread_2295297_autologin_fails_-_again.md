---
title: "autologin fails - again"
date: 2015-09-17
forum: Ubuntu Development Version
---

### Post by VMC on 2015-09-17
From this [topic]("http://ubuntuforums.org/showthread.php?t=2290845&p=13339050#post13339050"), we now have it reversed, once again!

Change "/etc/lightdm/lightdm.conf", to this:

```
[Seat:*]
user-session=xubuntu
autologin-user=XXX
```

Should fix it (for now).

This is from the current Xubuntu Wily.

---

