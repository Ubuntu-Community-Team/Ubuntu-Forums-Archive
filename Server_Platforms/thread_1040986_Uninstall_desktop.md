---
title: "Uninstall desktop"
date: 2009-01-16
forum: Server Platforms
---

### Post by Intruder on 2009-01-16
Hi guys im running 8.04 server and installed ubuntu desktop I have no need for this now and its a waste of resources is there a way to uninstall this?

[EDIT] or even disable it at boot and boot to console, done this before but for the life in me cant remember how

---

### Post by hyper_ch on 2009-01-16
[http://www.psychocats.net](http://www.psychocats.net) --> tutorials "pure KDE" --> there you'll get the command to remove all gnome packages as added by "ubuntu-desktop"

---

### Post by amauk on 2009-01-16
```
sudo chmod 644 /etc/init.d/gdm
```

This will disable execution of the Gnome desktop manager
you can now only boot into the terminal

```
sudo chmod 755 /etc/init.d/gdm
```
to re-enable GUI

---

### Post by Intruder on 2009-01-16
thanks for the replies guys :)

---

