---
title: "Windows Guest use host's 3D graphic card?"
date: 2011-09-01
forum: Virtualisation
---

### Post by laurocgb on 2011-09-01
I have Windows guests running on the top of KVM, here are the versions:
---
Ubuntu 11.04 (GNU/Linux 2.6.38-11-server x86_64)

qemu-kvm 0.14.0+noroms-0ubuntu4.4
ubuntu-virt-server 1.3
virt-manager 0.8.6-1ubuntu8.1
virt-viewer 0.2.1-1ubuntu4
virtinst 0.500.5-1ubuntu4
kvm 1:84+dfsg-0ubuntu16+0.14.0+noroms+0ubuntu4.4
qemu-common 0.14.0+noroms-0ubuntu4.4
qemu-kvm 0.14.0+noroms-0ubuntu4.4  
kvm-pxe 5.4.4-7ubuntu2
---

 Here is the detected VGA 

02:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 8400 GS] (rev a1)

 I didn't install Linux Nvidia drivers, as I didn't need the VGA on the Windows guests until now.

 Is it possible to have the Windows guests detect and use the Nvidia 3D physical card? Is it just a matter of installing nvidia drivers on both the guest and host? Any additional steps?



 Thanks in advance,

 Lauro

---

### Post by disabledaccount on 2011-09-02
No.
In VirtalBox it's possible, but dx3D support is experimental and unstable. In fact only 3d test in dxdiag works properly.

---

