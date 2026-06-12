---
title: "More uses for upstart?"
date: 2008-09-15
forum: Ubuntu Brainstorm
---

### Post by paste on 2008-09-15
This may be aimed more at developers, so feel free to skip over this if you aren't aware of things like upstart and udev.

I recently ran into a problem with Bluetooth on my laptop that required me to install the "omnibook" driver, a cute little program and adds a /proc interface to certain controls like soft power toggles for laptop Bluetooth devices.  You see, the Bluetooth device on my laptop defaults to the powered-off condition at boot, so I need to load this driver and issue the command "echo 1 > /proc/omnibook/blueooth" in order for the device to begin working.

I wanted it to work immediately at boot, so I started looking at upstart, Ubuntu's (and soon Linux's, I hope) replacement for the aging sysvinit.  I found that if I add the following udev rule (as 50-upstart-events.rules):
```
# emit events for upstart at the loading and unloading of modules

SUBSYSTEM=="drivers", ACTION=="add" RUN+="/sbin/initctl emit udev add %k"
SUBSYSTEM=="drivers", ACTION=="remove" RUN+="/sbin/initctl emit udev remove %k"
```
I was able to tie upstart and udev together in what seems to me to be a really useful way.  There are a lot of cases where you might want to issue certain commands once a driver is loaded (like in my case, where I want to turn the Bluetooth antenna on immediately), or wait until a driver is loaded before you start certain services or whatever.  I understand that udev can do this functionality for me just by adding custom rules to start services for each specific driver, but I feel that udev is a very unwieldy beast and that it is best to leave service handling to the more elegant upstart.

If this is a stupid way to handle this, or if there is a better way that is already in use, please let me know.  But if not, I think something like this should be included with either upstart or Ubuntu to make development of module-based services easier and more elegant.

---

### Post by UbuWu on 2008-09-15
You will probably get more response if you post this on the upstart-devel mailing list: [https://lists.ubuntu.com/mailman/listinfo/upstart-devel](https://lists.ubuntu.com/mailman/listinfo/upstart-devel)

---

