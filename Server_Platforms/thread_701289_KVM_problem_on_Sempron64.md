---
title: "KVM problem on Sempron64"
date: 2008-02-19
forum: Server Platforms
---

### Post by insulae on 2008-02-19
hi i want to try KVM, because at work we need a Server with Virtualization, but i have a problem i want i try to insert the kvm module and i have the next error:
```

$ sudo modprobe kvm
$ sudo modprobe kvm_amd FATAL: Error inserting kvm_amd (/lib/modules/2.6.22-14-generic/kernel/drivers/kvm/kvm-amd.ko): Operation not supported

```

i try to compile the last KVM and i have the same error.
I read in a forum that is due because my proc is sempron64 and don't have the SVM instrucction.

there any way to test KVM without the SVM instrucction?
i work for my goverment and dont have much many for hardware, for this reason we want use virtualization (we have a 1 server only :D) but i don't have hard available to try KVM, then i going to put KVM on the server, is a opteron). any idea?

i am using:
* Sempron64
* flags: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow up pni cx16 lahf_lm extapic cr8_legacy
* Ubuntu 7.10 X68_64
* 2.6.22-14-generic

Grettings
insulae

---

