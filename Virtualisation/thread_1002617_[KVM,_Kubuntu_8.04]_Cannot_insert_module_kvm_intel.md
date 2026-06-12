---
title: "[KVM, Kubuntu 8.04] Cannot insert module kvm_intel"
date: 2008-12-05
forum: Virtualisation
---

### Post by jambalaya on 2008-12-05
When I invoke "sudo invoke-rc.d kvm start" I get in response:

FATAL: Error inserting kvm_intel (/lib/modules/2.6.24-22-generic/kernel/arch/x86/kvm/kvm-intel.ko): Operation not supported
 * Module kvm_intel failed to load

My processor supports this, as I was able to use it before. I recently upgraded the kernel to 2.6.24-22, and I think it worked before (2.6.24-21). Does anyone have similar problems?

The processor is Intel Core 2 Duo T7500.

Thanks.

---

### Post by Dedoimedo on 2008-12-05
In terminal, if you type sudo lsmod | grep kvm ... does it list a kvm module?
Dedoimedo

---

### Post by jambalaya on 2008-12-06
Yes, it prints:
kvm                   131800  0

Apart from this, wifi stopped working. What the heck is going on?
I installed 2.6.24-21 and 2.6.24.19 and the two things still don't work.
Thanks.

---

### Post by jambalaya on 2008-12-06
Hi. it turns out I had virtualization disabled in BIOS, that's why it didn't work. Strange - I am the only one using this computer, no other pesron in the house can even turn it on ;-) it works now that I enabled it in BIOS. Sorry for the trouble.

---

