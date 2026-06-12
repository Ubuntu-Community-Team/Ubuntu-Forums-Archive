---
title: "How to stop KVM starting at boot"
date: 2010-03-10
forum: Virtualisation
---

### Post by satimis on 2010-03-10
Hi folks.

Host - ubuntu 9.10 64bit
Virtualizer - KVM

I need to stop KVM starting at boot.  I added following 2 lines at the bottom of /etc/modprobe.d/blacklist.conf```

blacklist kvm
blacklist kvm-amd

```

Reboot PC

It doesn't work.

$ lsmod | grep kvm```

kvm_amd                41556  0 
kvm                   190648  1 kvm_amd

```

Please what further command I have to run in order to activate the new blacklist.conf ?

TIA

B.R.
satimis

---

