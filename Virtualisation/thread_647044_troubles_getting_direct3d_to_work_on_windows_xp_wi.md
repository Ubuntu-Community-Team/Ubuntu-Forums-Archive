---
title: "troubles getting direct3d to work on windows xp with vmware 6"
date: 2007-12-21
forum: Virtualisation
---

### Post by yipeskop on 2007-12-21
I've recently installed vmware workstation 6.0.2 on my ubuntu 7.10 (64bit) and installed Windows XP pro edition on it (32bit) and installed directx 9 on it but when I goto Dxdiag it says
"Direct3D functionality not available.  You should verify that the driver is a final version from the hardware manufacturer."
so I decide to go download a nvidia driver for my 6150LE GeForce graphics card to see if that would work but when I goto install it I get this error: [http://img172.imageshack.us/img172/8601/nvidiaerrorin9.png](http://img172.imageshack.us/img172/8601/nvidiaerrorin9.png)

any ideas how to get this to work?

---

### Post by Shazaam on 2007-12-22
VMware uses a hard coded virtual SVGA video driver with limited 3d support so you are wasting your time trying to install those drivers. You could go to the VMWare forums and search 3d there.

[http://communities.vmware.com/index.jspa](http://communities.vmware.com/index.jspa)

---

