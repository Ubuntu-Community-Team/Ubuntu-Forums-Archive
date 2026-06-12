---
title: "calibrate_APIC_clock problem with kvm-irqchip"
date: 2009-12-02
forum: Virtualisation
---

### Post by jschaef on 2009-12-02
Hi,

I have a problem with some virtual machines and kvm-irqchip option.
I get a calibrate_APIC_clock: SMI flood message during booting and machines hang.

I can prevent this with the no-kvm-irqchip option, when starting machines manually.

The question is - can I specify this option somehow in the xml-file for libvirt?
I didn't find anything how to achieve that at libvirt.org.


Thanks

---

