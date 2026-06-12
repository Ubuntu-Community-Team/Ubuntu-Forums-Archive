---
title: "Xen Kernel Issues"
date: 2013-12-14
forum: Virtualisation
---

### Post by sronk510 on 2013-12-14
So im running Ubuntu Server 12.04LTS and have Xen Server installed. I want to install some more Ubuntu Server Installs on Xen as paravirtualization machines. After finally getting an HTTP:// install setup i got the error "ERROR[COLOR=#444444][FONT=arial] Couldn't find Xen kernel for Ubuntu Tree" Initially i thought maybe Ubuntu didnt have a supported Xen Kernel but [/FONT][/COLOR][http://wiki.xenproject.org/wiki/Dom0_Kernels_for_Xen](http://wiki.xenproject.org/wiki/Dom0_Kernels_for_Xen) seems to tell me otherwise. Can anybody help me finish getting Ubuntu Server 12.04LTS setup as a Xen Server to host Ubuntu 12.04LTS as a host.

---

### Post by tgalati4 on 2013-12-14
I presume that you have gone through these help guides?

[https://help.ubuntu.com/community/Xen](https://help.ubuntu.com/community/Xen)

[https://help.ubuntu.com/community/Setting%20up%20Xen%20and%20XAPI%20%28XenAPI%29%20on%20Ubuntu%20Server%2012.04%20LTS%20and%20Managing%20it%20With%20Citrix%20XenCenter%20or%20OpenXenManager](https://help.ubuntu.com/community/Setting%20up%20Xen%20and%20XAPI%20%28XenAPI%29%20on%20Ubuntu%20Server%2012.04%20LTS%20and%20Managing%20it%20With%20Citrix%20XenCenter%20or%20OpenXenManager)

Xen has gone under a lot of changes over the past couple of years, so the version of Xen may be an issue.

---

