---
title: "Ubuntu Server 6.06 hibernates by users"
date: 2006-07-18
forum: Server Platforms
---

### Post by nicolas.clementz@uha.fr on 2006-07-18
Currently I'm installing a application server for X terminals. I'm surprised thas standards users are able to hibernate the server. 
Anyboby has noted this point ? How can I disable hibernate and suspend fonctions ?

The DBUS command :dbus-send --system --type=method_call --dest=org.freedesktop.Hal /org/freedesktop/Hal/devices/computer org.freedesktop.Hal.Device.SystemPowerManagement.Hibernate

Thanks.

---

### Post by joerg8472 on 2006-07-20
Hi,

i faced the same problem with Edubuntu.

The following thread solved it well:
[http://www.ubuntuforums.org/showthread.php?t=188162](http://www.ubuntuforums.org/showthread.php?t=188162)

Bye
joerg8472

---

