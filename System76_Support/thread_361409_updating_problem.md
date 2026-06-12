---
title: "updating problem"
date: 2007-02-14
forum: System76 Support
---

### Post by ubarry on 2007-02-14
I've got an nvidia Serval, and I tried doing today's updates and ran into a problem. Synaptic hung on configuring the kernel. I killed it and ran dpkg in the terminal, and got these errors:

dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.15-28-686:
 linux-restricted-modules-2.6.15-28-686 depends on linux-image-2.6.15-28-686; however:
  Package linux-image-2.6.15-28-686 is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.15-28-686 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-686: linux-restricted-modules-686 depends on linux-restricted-modules-2.6.15-28-686; however:
  Package linux-restricted-modules-2.6.15-28-686 is not configured yet.
dpkg: error processing linux-restricted-modules-686 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-686-smp:
 linux-686-smp depends on linux-restricted-modules-686; however:
  Package linux-restricted-modules-686 is not configured yet.
dpkg: error processing linux-686-smp (--configure):
 dependency problems - leaving unconfigured
Setting up linux-headers-2.6.15-28-686 (2.6.15-28.51) ...
dpkg: dependency problems prevent configuration of linux-image-686:
 linux-image-686 depends on linux-image-2.6.15-28-686; however:
  Package linux-image-2.6.15-28-686 is not configured yet.
dpkg: error processing linux-image-686 (--configure):
 dependency problems - leaving unconfigured
Setting up linux-headers-686 (2.6.15.26) ...
Errors were encountered while processing:
 linux-image-2.6.15-28-686
 linux-restricted-modules-2.6.15-28-686
 linux-restricted-modules-686
 linux-686-smp
 linux-image-686


Barry

---

### Post by crichell on 2007-02-14
Lets give the easy fix a shot first.

Open up Synaptic.
Click "Reload" to make sure we have the latest package information.
Click Edit > Fix Broken Packages
"Apply" (if it's available.)

If Fix broken packages doesn't come back with anything you can try
```
sudo apt-get -f install
```

---

### Post by ubarry on 2007-02-14
Thanks Carl.  That did it.

---

