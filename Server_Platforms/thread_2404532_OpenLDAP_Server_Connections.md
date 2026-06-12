---
title: "OpenLDAP Server Connections"
date: 2018-10-25
forum: Server Platforms
---

### Post by rudders on 2018-10-25
Hi all - I have Ubuntu 16.04 with OpenLDAP installed connected to my LDAP server but when I look at output for "netstat -tapn | grep 389" I see a lot and they are process I would not expect to query the LDAP, for example:

dbus-daemon
lightdm
update-notifie
lightdm
unity-scope-h
nautilus
evolution-cale
systemd-udevd
upstart
dbus
ibus-daemon
dbus-daemon

Does anyone know why I would have established connections to the LDAP from these services? I have other Linux installs and they don't behave in this manner.

Thanks!

---

### Post by slickymaster on 2018-10-25
Thread moved to **Server Platforms** for a better fit

---

