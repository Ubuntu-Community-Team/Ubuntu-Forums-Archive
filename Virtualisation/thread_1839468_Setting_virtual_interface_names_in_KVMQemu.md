---
title: "Setting virtual interface names in KVM/Qemu"
date: 2011-09-05
forum: Virtualisation
---

### Post by methos.oldest on 2011-09-05
(Pardon me if this has already been asked, a quick search did not show anything similar)

I have a few KVM machines that I put under a private network using tap devices. I have also setup their /etc/network/interfaces so that each one gets proper ip address.

I copied my setup to another machine and I see that when KVM VM's are brought up, the virtual interfaces get different names than the orginal setup. Thus /etc/network/interfaces does not work.

I tried to set virtual interface name using "name" attribute of the "-net nic" option. But that did not work.

Does anyone know how to fix this problem?

---

