---
title: "Tried the apparmor for Firefox, don't like it.  How the heck do I turn it off"
date: 2010-11-12
forum: Security
---

### Post by MechaMechanism on 2010-11-12
Tried the apparmor profile for Firefox.  I don't care for it.  I can't fire out how to turn it off.  No matter what I do, it still shows up as being on in apparmor status.

---

### Post by FuturePilot on 2010-11-12
```
sudo ln -s /etc/apparmor.d/usr.bin.firefox /etc/apparmor.d/disable/
sudo apparmor_parser -R /etc/apparmor.d/usr.bin.firefox
```

---

### Post by MechaMechanism on 2010-11-12
> **FuturePilot said:**
> ```
sudo ln -s /etc/apparmor.d/usr.bin.firefox /etc/apparmor.d/disable/
sudo apparmor_parser -R /etc/apparmor.d/usr.bin.firefox
```
Thanks a bunch.  All the Google results show how to turn it on but not to turn it off.  Much obliged.

---

### Post by ptn107 on 2010-11-12
Why not just use...

to enable:
```
sudo enforce firefox
```

to disable:
```
sudo complain firefox
```

---

