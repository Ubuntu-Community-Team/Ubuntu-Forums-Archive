---
title: "Qemu Fedora 7 or 8 won't install"
date: 2008-01-22
forum: Virtualisation
---

### Post by RIchard James13 on 2008-01-22
I have Qemu working with and without Kqemu. I can install Slackware 12 from a DVD or DVD iso image but when I try to install Fedora 7 or 8 from the DVD or DVD ISO image, the installer complains it cannot find the install media.

[b]
[COLOR="Red"]No driver found[/COLOR]
Unable to find any devices of the type
needed for this installation type.
Would you like to manually select your
driver or use a driver disk?

Select driver | Use a driver disk | Back
[/b]
I can get the DVD to boot on my PC past this normally but in Qemu it just stops there.

Does anyone know a way around this?

Qemu Version 0.9.0

---

### Post by RIchard James13 on 2008-01-23
Also while trying to find a fix I discovered that OpenSUSE 10.3 and Ubuntu 7.10 have the same problem. It seems that the Kernel is not seeing the IDE subsystem in QEMU.

Further research leads to this thread
[https://bugs.launchpad.net/ubuntu/+source/qemu/+bug/154591]("https://bugs.launchpad.net/ubuntu/+source/qemu/+bug/154591")
they mention that to get Ubuntu to install you need to pass the Kernel parameter
all_generic_ide

The Ubuntu installer runs now, how to track down the others?

---

### Post by RIchard James13 on 2008-01-23
With Open SUSE I needed the boot option
insmod=ide-generic

Then it works
[http://forums.suselinuxsupport.de/index.php?showtopic=43745]("http://forums.suselinuxsupport.de/index.php?showtopic=43745")

Actually It only installs, it won't boot with the insmod=ide-generic option

Now for the ultimate test Fedora.

---

