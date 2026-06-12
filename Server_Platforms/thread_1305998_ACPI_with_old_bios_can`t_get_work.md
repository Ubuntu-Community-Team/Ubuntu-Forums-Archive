---
title: "ACPI with old bios can`t get work"
date: 2009-10-30
forum: Server Platforms
---

### Post by gkali on 2009-10-30
Hello!

I`m running a Netfinity 3500 with ubuntu server jaunty.
My problem is that my BIOS is from 98 and it writes : it can`t be older than 2000 and i have to use acpi=force.
I gave grub a acpi=force but then it can`t load the root.
Loading, please wait...
// takes aprox. 30 secs
Gave up waiting for root device. Common problems:
- Boot args (cat /proc/cmdline)
 - Check rootdelay
 - Check root
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/md0 does not exist. Dropping to a shell!

Thank you in advice!
Gkali

---

### Post by elvinatom on 2009-10-30
had that happen - don't know the solution, but Arch Linux installed just fine on it.

---

### Post by elvinatom on 2009-10-30
actually, (if it helps) I _think_ the problem comes from missing kernel-drivers for long outdated hardware.  For example I can't use my old sb awe64 under modern linux kernel: not supported anymore (at least by default).

---

