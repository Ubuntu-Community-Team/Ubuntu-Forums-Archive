---
title: "Server won't shutdown"
date: 2012-06-16
forum: Server Platforms
---

### Post by Jimgary on 2012-06-16
Couldn't seem to find a thread, plz refer is already started.

If I select shutdown or restart, server acts like I'm locking and enter password screen pops up.
If I go to terminal and sudo shutdown now
GUI shuts down but terminal seems to hang on modem manager, can't find bus.
Any ideas?

---

### Post by codemaniac on 2012-06-16
Have you been able to check the syslog if any suspicious things you can see?

---

### Post by codemaniac on 2012-06-16
Also try killing network-manager before you shutdown your system .

```
sudo service network-manager stop
```
```
sudo shutdown -h now
```

---

