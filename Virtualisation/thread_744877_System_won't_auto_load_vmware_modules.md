---
title: "System won't auto load vmware modules"
date: 2008-04-04
forum: Virtualisation
---

### Post by Goobie81 on 2008-04-04
I have Ubuntu Server 7.1 64 and i installed the system, everythings ok

had some issues apt-getting vmware-server with the commercial repo, so i used the vmware.com version and installed fine

However after a while i had some rtc clock issues with vmware so i compiled a new kernel, 2.6.22.9, with HPET_EMULATE_RTC and that corrected the issues with vmware however now it doesn't seem to automatically load the vmnet and vmmon modules on boot. Every time i boot i have to re-run vmware-config.pl and just spam enter 20 times and then the modules are loaded. Any ideas?

root@phantom:/etc/modprobe.d# modprobe vmnet
FATAL: Module vmnet not found.
root@phantom:/etc/modprobe.d# modprobe vmmon
FATAL: Module vmmon not found.
root@phantom:/etc/modprobe.d# lsmod | grep ^vm
vmnet                  45344  7
vmmon                 150124  15

---

### Post by Goobie81 on 2008-04-07
don't worry about this, after a few reboots it seemed to be fine? weird

---

