---
title: "xen and fglrx in 3.1"
date: 2008-02-22
forum: Virtualisation
---

### Post by stamina on 2008-02-22
hi.
I am currently trying to get the restricted driver's manager to work but with no luck.
the computer is a fujitsu siemens laptop with amd turion x2 (running 64 bit  ubuntu) and an ATI xpress1100 which is working fine with Ubunto, however, when virtualized with Xen, after installing the restricted (non-free)  module, the manager's "workaround" doesn't actually seem to work.

why xen? because my cpu actually works twice as fast while running the ubuntu virtualized kernel! it's a pitty gnome/kde is "slow-motion" because it's been rendered by software :(

Regards,
/Jorge.

---

### Post by gutsy08 on 2008-02-23
strange, why does your computer run faster when virtualized?  i thought xen would exert an (albeit small) performance penalty.

---

### Post by stamina on 2008-02-25
because xen supports the virtualizing extensions found on the amd turion 64 X2. This is a dual-core 64 bit cpu.. new Intel cpu's are being supported too.
Ubuntu successfully detects the GPU, the problem is enabling the fglrx driver.
Please find attached a striped down log /var/log/Xorg.0.log


Many Thanks,
Jorge.

---

### Post by stamina on 2008-03-03
could someone help?
the problem seems to be ubuntu can't compile the fglrx module.
I've got the ati sources to compile, the restricted packages and dkms also installed, after re-installing the desktop effects can't be enabled.

thank you.

---

