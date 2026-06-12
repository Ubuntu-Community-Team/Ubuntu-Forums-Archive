---
title: "libvirt is being restarted with ABRT signal"
date: 2013-12-24
forum: Virtualisation
---

### Post by jefims on 2013-12-24
Hi,

After moving all VMs to hugepages and disabling KSM libvirtd is being restarted from time to time with ABRT signal:
```
[Tue Dec 24 10:44:38 2013] init: libvirt-bin main process (100286) killed by ABRT signal
[Tue Dec 24 10:44:38 2013] init: libvirt-bin main process ended, respawning
```

In /var/log/libvirt/libvirtd.log I see multiple errors:
```
2013-12-24 09:05:59.405+0000: 24039: error : virNetSocketReadWire:1016 : End of file while reading data: Input/output error
2013-12-24 09:06:24.655+0000: 24039: error : virNetSocketReadWire:1016 : End of file while reading data: Input/output error
2013-12-24 09:06:59.186+0000: 24039: error : virNetSocketReadWire:1016 : End of file while reading data: Input/output error
```

VMs are working fine.

**Software used:**
Ubuntu 12.10
Kernel 3.5.0-41-generic
Libvirt 0.9.13-0ubuntu12.5

What might be the cause of this? Thank you!

---

