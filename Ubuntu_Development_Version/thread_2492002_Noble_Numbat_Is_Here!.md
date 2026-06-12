---
title: "Noble Numbat Is Here!"
date: 2023-10-27
forum: Ubuntu Development Version
---

### Post by MAFoElffen on 2023-10-27
Let the Bug Report race begin!
```

mafoelffen@noble00:~$ uname -r
6.5.0-9-generic
mafoelffen@noble00:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Noble N (development branch)
Release:    24.04
Codename:    noble

```
Were 38 packages updated in the repo...

Already have my first bug to report. As soon as I upgraded, now it will not reboot. Not even on a forced reboot. It locks up. It has to fully shutdown, and cold boot. But not sure what to file it against.

Didn't that same issue start for some near the end of the Mantic DEV cycle?

---

### Post by MAFoElffen on 2023-10-27
I found it, it was Rubi1200... But it was "different" enough, in that his would not "shut down" at all, except it he did a physical power off with the power button. ([https://bugs.launchpad.net/ubuntu/+bug/2036987](https://bugs.launchpad.net/ubuntu/+bug/2036987))

This is similar to a Bug Report I have filed on 22.04 for one of my physical machines here, where it will not do a "reboot". ([https://bugs.launchpad.net/ubuntu/+source/linux-signed-hwe-6.2/+bug/2032136](https://bugs.launchpad.net/ubuntu/+source/linux-signed-hwe-6.2/+bug/2032136))

[s]Trying to figure out if I should add it to it to that, or if I should file a new one, since it is DEV 24.04, so that they can link the two(???)[/s]

[s]EDIT: Different outcomes. That old one reboots to the BIOS boot screen. This one locks up when you try to do "reboot". So trying to figure out what to file a systemd reboot.target issue against... Hmmm(???)[/s]

EDIT2: 14 more packages updated. The reboot issue worked itself out.

---

