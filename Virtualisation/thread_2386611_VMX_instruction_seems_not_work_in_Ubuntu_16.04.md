---
title: "VMX instruction seems not work in Ubuntu 16.04"
date: 2018-03-07
forum: Virtualisation
---

### Post by wangt13 on 2018-03-07
I am testing a small open-source VMM in Linux for Intel.
And I found in Ubuntu 16.04, the vmlaunch instruction failed with no more clues.

The VMM's logic is as follows.
Set bit13 of CR4.
Allocate regions for VMXON, and VMCS, set them up with correct revision number, setup VMCS correctly.
Then, call vmlaunch to start VM to run.
VMXOFF, and clear bit13 of CR4 when done.

The VM just has a CPUID instruction, but VMEXIT could NOT get the reason of CPUID, it shows
[ 4084.644009]  VM-instruction error: 00000000  Exit Reason: 00000000
[ 4084.644015]  VMexit-interruption-information: 00000000
[ 4084.644018]  VMexit-interruption-error-code:  00000000

I ran the same code in Ubuntu 9.04 (linux-2.6.28), and it worked as expected.

If you need I pasted the code, please let me know.
Any helps, tips are appreciated.

Thanks,
-Tao

---

