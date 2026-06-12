---
title: "How to reinstall kvm?"
date: 2014-11-01
forum: Virtualisation
---

### Post by eezacque on 2014-11-01
I accidently unloaded and trashed the kvm kernel modules in /lib/modules/3.13.0-39-generic/kernel/arch/x86/kvm/  
I though I could get 'm back by reinstalling kvm, but for some reason both 'apt-get remove kvm' and 'apt-get install kvm' end with 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. How do I reinstall kvm?

---

### Post by TheFu on 2014-11-02
sudo apt-get --reinstall install kvm

Or

Just use **aptitude** (may need to install it - for some reason it isn't installed by default).

BTW, I vaguely remember there are other packages needed for KVM to work.

How does someone accidentally trash anything under /lib? I'm just curious.

---

### Post by eezacque on 2014-11-03
> **TheFu said:**
> sudo apt-get --reinstall install kvm

Or

Just use **aptitude** (may need to install it - for some reason it isn't installed by default).

BTW, I vaguely remember there are other packages needed for KVM to work.

How does someone accidentally trash anything under /lib? I'm just curious.

I had overwritten kernel modules with versions that were compiled for a different kernel  \\:D/
Anyways, the kvm modules are installed with the kernel, and not with the kvm package, so a kernel reinstall solved the problem.

Thanks, anyways...

---

