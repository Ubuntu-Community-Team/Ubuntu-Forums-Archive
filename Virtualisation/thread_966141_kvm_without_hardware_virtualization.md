---
title: "kvm without hardware virtualization"
date: 2008-11-01
forum: Virtualisation
---

### Post by el_baby on 2008-11-01
Hi,

I want to start using virtualization in a couple of servers... I made a couple of tests with vmware server and it worked but I'd rather use non-propietary software.

Ubuntu and linux in genera seem to be gearing towards kvm+qemu and JeOS + ubuntu-vm-builder seems like a really nice addition in the mix.

However, I have to do my tests on spare hardware or my own desktop, neither of which support virtualization (no Intel VT or AMD-V).

For what I read in [the wiki](https://help.ubuntu.com/community/KVM) and [the FAQ](http://kvm.qumranet.com/kvmwiki/FAQ) it seems that kvm only works with CPUs that support virtualization... My servers do support it but I can't use them to run tests... what are my best choices in this situation?

Can I create plain qemu with ubuntu-vm-builder on my test machine?... other than performance issues, will that be somehow similar or is it a waste of time?

TIA

---

### Post by Weissbier on 2008-11-01
The answer is yes, you can install it (QEMU) even on Machines without KVM installed for creating the image/testing/installing guest-system(s)/ whatever reasons.
QEMU will then automatically take advantage of KVM if it is installed/loaded on a target host system.
But keep in mind to not use [COLOR="Red"]k[/COLOR]QEMU - you should not use it together with KVM enhanced.

---

