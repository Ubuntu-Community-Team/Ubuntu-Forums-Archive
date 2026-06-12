---
title: "KVM / Windows 7: Winlogon.exe error upon boot"
date: 2009-12-19
forum: Virtualisation
---

### Post by pneumatic on 2009-12-19
I'm running KVM under 9.10.  Upon installing a Windows 7 guest, I boot the machine and get a "Winlogon.exe - The instruction at 0x77b0a7c9 referenced memory... The memory could not be read".

Thoughts?

---

### Post by smetj on 2010-03-02
Hi,

I had exactly the same problem and managed to get around it by first loading both storage & network drivers found here:

[http://blog.famzah.net/2010/01/09/kvm-qemu-virtio-storage-and-network-drivers-for-32-bit64-bit-windows-7-windows-vista-windows-xp-and-windows-2000/](http://blog.famzah.net/2010/01/09/kvm-qemu-virtio-storage-and-network-drivers-for-32-bit64-bit-windows-7-windows-vista-windows-xp-and-windows-2000/)

At the beginning of the win7 installer you have to chance to load additional drivers, that is what you need to do with the above files.

If you can't find the drivers in the load interface, unselect "only show certified/signed drivers" or something similar, then you'll have the opportunity to load them...

It solved the problem you described, ...

Hope this helps, 

Jelle

---

