---
title: "Mitigating physical access attacks like inception (firewire) badusb et al"
date: 2014-10-27
forum: Security
---

### Post by rndmusr2 on 2014-10-27
Hi,

it came to my attention that several usb kernel drivers may have vulnerabilities (some researchers found out by massive fuzzing of emulated usb devices in a vm env) and the way to an exploit is usually not far from there. This could be used to disable the screensaver and gain access to a powered device that uses fde and pba.

The idea I had is to lock down the automatic driver loading capabilites of the linux system after boot, so that already connected devices continue functioning, but stuff that an attacker would attach to the physical machine cannot harm it.

lock.sh:
```

#!/bin/bash
rm /etc/modprobe.d/blacklist-lock.conf 2>/dev/null
umask 077
ls -w1 -R /lib/modules/$(uname -r)/kernel/drivers|grep '.ko'|sed 's/\.ko//g'|awk '{print "blacklist "$1"\ninstall "$1" false"}' > /dev/shm/lock
ln -s /dev/shm/lock /etc/modprobe.d/blacklist-lock.conf

```

To unlock, e.g. if you want to attach a pendrive this can be undone:

unlock.sh:
```
#!/bin/bash
rm /etc/modprobe.d/blacklist-lock.conf

```

You could execute lock.sh (as root) via /etc/rc.local for example or just invoke it when you leave the machine unattended, a more advanced method would be to check if the screensaver is active (dbus), then run lock.sh ...

Note: if your machine has a firewire device attached to it, you would need to modprobe -r the modules or permanently blacklist them.

What do you think?

---

### Post by TheFu on 2014-10-27
Would apparmor or SELinux be easier and result in a more secure outcome?

---

### Post by joris-lambrecht on 2015-03-11
In my experience SELinux is hard to handle but well supported. Personally i trust in grsecurity.net, takes manual patching but is best of class IMHO.

---

### Post by gordintoronto on 2015-03-12
If someone has physical access, they can just pop out the hard drive and take it away.

---

### Post by tripp98 on 2015-04-19
If physical access is the issue remove it.  Run everything virtual.

---

### Post by konrad6 on 2015-04-20
If you disable Firewire and USB ports in BIOS (also eSATA ports, Thunderbolt or whatever else), I suppose it's a solid remedy. As for an attacker taking out the hard drive, if you have an SSD with hardware encryption, there's nothing they can do with it if it's removed. However, if the OS is running and is in screensaver mode, any LUKS keys can be recovered from the RAM (cold boot attack), along with anything else you had running at the time. SSD encryption does prevent this however since keys are held in the internal RAM of the controller, not system RAM.

---

