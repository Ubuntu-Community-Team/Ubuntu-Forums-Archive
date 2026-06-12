---
title: "Setting up an Ubuntu Xen Server (Problems with Local Storage Repository)"
date: 2013-12-03
forum: Virtualisation
---

### Post by thom3 on 2013-12-03
Hello,

I recently rented a dedicated server, which I want to use as a hypervisor.  I'm currently following the tutorial found [here]("https://help.ubuntu.com/community/Setting%20up%20Xen%20and%20XAPI%20%28XenAPI%29%20on%20Ubuntu%20Server%2012.04%20LTS%20and%20Managing%20it%20With%20Citrix%20XenCenter%20or%20OpenXenManager?action=fullsearch&value=linkto%3A%22Setting+up+Xen+and+XAPI+%28XenAPI%29+on+Ubuntu+Server+12.04+LTS+and+Managing+it+With+Citrix+XenCenter+or+OpenXenManager%22&context=180"), however I'm struggling with the Local Storage Repository section.  The tech who provisioned the server did a basic install, with one / partition.  Which means I need to create a repository for my VMs on this partition.

Anybody know how I can go about doing this? I currently get this error:

**xe sr-create host-uuid=<UUID> type=ext name-label="Local Storage" device-config:device=/dev/sda6**
```
The SR operation cannot be performed because a device underlying the SR is in use by the host.
```

Any help would be greatly appreciated!

---

