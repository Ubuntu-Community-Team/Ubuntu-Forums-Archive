---
title: "Unlock button for remote administration"
date: 2009-07-23
forum: Server Platforms
---

### Post by bobthechemist on 2009-07-23
Just installed 9.04 server (64bit) and added gnome-desktop.  At the console, I can unlock administrative tools such as users-admin, however when I connect remotely, the unlock button remains grayed out.  I noticed this was a problem with 8.04 but couldn't tell if it was ever resolved.  I'm not sure if this is a bug, feature, or configuration error on my part.

---

### Post by bobthechemist on 2009-07-23
Kept digging and found the solution

[https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/187335](https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/187335)

in terminal sudo polkit-gnome-authorization

then

System -> Administration -> Authorizations -> org, freedesktop, systemtoolsbackends, Manage system configuration.

Modify the "Implicit Authorizations" with the Edit button, and change the "Anyone" value to "Admin Authentication".

---

