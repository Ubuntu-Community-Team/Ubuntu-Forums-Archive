---
title: "hal on server edition?"
date: 2010-01-20
forum: Server Platforms
---

### Post by thinking on 2010-01-20
hi all

i currently try to mount 4 internal sata disks using hal on a server installation?
i did
apt-get install hal
and copied a .fdi script to 
/usr/share/hal/fdi/policy/10osvendor/30-storage-all.fdi

as far is i understand now i need a hal/dbus client
gnome-volumen-manager seems to be one
apt-get install gnome-volume-manager

now im stuck
there is no such executable like gnome-volumen-manager
thus, how does it work?
how can i start it?
how do i know if and why the .fdi script works or fails?

since its a server edition and its purpose should be a very minimized server install i dont want a GUI like gnome fully installed

any hints on this would be great, thx

---

### Post by boudies on 2010-01-20
Ubuntu release notes say that:
> hal deprecation Ubuntu 9.10 RC's underlying technology for power management, laptop hotkeys, and handling of storage devices and cameras maps has moved from "hal" (which is in the process of being deprecated) to "DeviceKit-power", "DeviceKit-disks" and "udev".   



Couldn't devicekit-disks do what you're looking for? Full documentation can be found on:

[http://hal.freedesktop.org/docs/DeviceKit-disks/](http://hal.freedesktop.org/docs/DeviceKit-disks/)

---

