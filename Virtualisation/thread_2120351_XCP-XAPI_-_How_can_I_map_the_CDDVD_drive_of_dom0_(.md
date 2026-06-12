---
title: "XCP-XAPI - How can I map the CD/DVD drive of dom0 (host) for use by domu (VMs)"
date: 2013-02-26
forum: Virtualisation
---

### Post by eduardolucioac on 2013-02-26
How can I map/mount the CD/DVD drive of Dom0 for use by virtual machines (DomU). I'm talking about XCP-XAPI running with Ubuntu Server 12.04 LTS (on Dom0). I can not find anywhere how I can solve this!

In this link ([https://help.ubuntu.com/community/Setting%20up%20Xen%20and%20XAPI%20%28XenAPI%29%20on%20Ubuntu%20Server%2012.04%20LTS%20and%20Managing%20it%20With%20Citrix%20XenCenter%20or%20OpenXenManager](https://help.ubuntu.com/community/Setting%20up%20Xen%20and%20XAPI%20%28XenAPI%29%20on%20Ubuntu%20Server%2012.04%20LTS%20and%20Managing%20it%20With%20Citrix%20XenCenter%20or%20OpenXenManager)) I created a complete roadmap on installing XCP-XAPI on Ubuntu Server 12.04 LTS, but lack resolve the problem that I put here!

I would like a command that was something like this: "xe sr-create content-type=iso device-config:location=/dev/sr0 name-label="HostDVDDrive0" shared=true type=iso"

In this command example I cited above, the device "HostDVDDrive0" appears in "XenCenter" but not as a DVD/CD that I can attach to the virtual machines.

Comrades, if you do not know the answer, give me a clue! A little help here would be appreciated!

I need this information to complete my Wiki. This information is important for the Ubuntu and XEN community!

[]'s

---

