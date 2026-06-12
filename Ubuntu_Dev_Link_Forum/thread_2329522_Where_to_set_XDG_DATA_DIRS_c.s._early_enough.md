---
title: "Where to set XDG_DATA_DIRS c.s. early enough"
date: 2016-07-02
forum: Ubuntu Dev Link Forum
---

### Post by rjvbertin on 2016-07-02
Hi,

Where are the XDG env. variables set on [K]Ubuntu 14.04? I have been rolling my own Project Neon5 replacement, installing Qt 5.6 and KF5 into a separate prefix (/opt/local). I've been using a `/etc/dbus-1/session-local.conf` file to be sure the session DBus daemon knows about /opt/local/share, /opt/local/etc/xdg etc. when it starts up, but I'd prefer to add the /opt/local paths to the corresponding XDG_ env. variables.

Is this possible before the session dbus is started and if so, what file(s) should I edit?

Thanks,
René

---

