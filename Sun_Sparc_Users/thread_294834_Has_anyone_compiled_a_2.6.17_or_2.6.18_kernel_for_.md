---
title: "Has anyone compiled a 2.6.17 or 2.6.18 kernel for Blade 1000 ???"
date: 2006-11-07
forum: Sun Sparc Users
---

### Post by jcrenner on 2006-11-07
Hi All,

Has anyone compiled a 2.6.17 or 2.6.18 kernel for a Blade 1000 including:

- smp
- bbc_i2c drivers so that fans don't run at full speed
- qlogic FC HBA drivers for the disks

If anyone has done it, I would be interested (can host it if that helps), otherwise will do it myself and post a link...

Thanks,

Jon

---

### Post by calixtine on 2006-11-09
I've compiled a 2.6.18 kernel for this machine, but stumbled on loading the Qlogic firmware via the firmware loader interface. I hit a dead end on this one as there is a paucity of info, there is a bug filed which relates to this at :

[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/67463](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/67463)

It appears that the qlogic driver has to be loaded as a module (search the sparc kernel mailing list for qlogic), so the firmware must be included in initramfs, I assume also loading /lib/udev/firmware_helper but am not sure how this works once it's there. There might be a further config needed in udev to get the firmware_helper to execute at the initrd stage of boot-up(??)

Debian has a qlogic driver as a separate package, this appears to just load the firmware and "firmware.agent" into the initramfs using a script in /usr/share/initramfs-tools/hooks/. You can install the debian package but have to edit the script as the paths are wrong.

[http://packages.debian.org/testing/admin/firmware-qlogic](http://packages.debian.org/testing/admin/firmware-qlogic)

 If you have any ideas how to get this working or pointers to documentation then please post as I'm bored of my howling fans (without a working bbc_i2c driver on 2.6.15!)

cheers
Andy

---

### Post by kthakore on 2006-11-09
srry, for dropping in like this. But I am really curious whats a blade 1000?

---

### Post by netztier on 2006-11-10
> **kthakore said:**
> srry, for dropping in like this. But I am really curious whats a blade 1000?

Sun Microsystems, [SunBlade1000]("http://sunsolve.sun.com/handbook_pub/Systems/SunBlade1000/SunBlade1000.html").

regards

Marc

---

