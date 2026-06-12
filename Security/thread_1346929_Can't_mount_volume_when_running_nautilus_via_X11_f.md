---
title: "Can't mount volume when running nautilus via X11 forwarding"
date: 2009-12-05
forum: Security
---

### Post by nETPOBu4 on 2009-12-05
Hello!
Server running ubuntu 8.04. Client connects via ssh with ForwardX11 parameter enabled and runs nautilus. When client tries to mount usb volume in nautilus he gets error "Error org.freedesktop.DBus.Error.AccessDenied" (see attached picture).

How to configure security policy to enable remote clients to mount volumes?

---

### Post by Agent ME on 2009-12-05
On my old 9.04 install, there was an option under System -> Administration called "Authorizations..." which could change this setting and a lot of similar settings, but I can't seem to find it now. Either it was removed in 9.10 or it was a package I installed that I lost when I reformatted my system.

EDIT: I found what package it was in, but it seems it was deprecated in 9.10 as it can't do much now. I'm not sure what the replacement is supposed to be.

---

### Post by falconindy on 2009-12-06
Ubuntu uses at_console rules in HAL. By default, only those with a user file in /var/run/console are allowed to mount drives. If you want to change this behavior, I suggest creating a new security group (call it storage), and alter the rules in /etc/dbus-1/system.d/hal.conf.

---

