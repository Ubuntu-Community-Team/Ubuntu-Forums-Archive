---
title: "KVM: Giving video hardware to guest os"
date: 2008-11-16
forum: Virtualisation
---

### Post by blaster32 on 2008-11-16
Hi,

I'd like to have one of my guest os direct access to my video cards tv out.
I belive the guest vm would need exclusive access to the video hardware but I can't find any documentation on that. Is it even possible to achive this?

Thanks,
blaster

---

### Post by David Cartwright on 2008-11-17
KVM-79 includes support for PCI pass-thru and hot-plugging.

More info here for more details and the command format:
[http://www.linux-kvm.com/content/kvm-79-released-pci-device-assignment-pci-device-hot-plug](http://www.linux-kvm.com/content/kvm-79-released-pci-device-assignment-pci-device-hot-plug)

I haven't tried it as yet, but I understand that the VM host cannot have a driver loaded for the relevant PCI card. Hence the driver must only be in loaded on the VM guest.

Let us know how you get on.

---

