---
title: "Virtualbox error..."
date: 2010-02-07
forum: Virtualisation
---

### Post by MindFusion on 2010-02-07
Hi everyone. I am running a 64-bit, 4 GIG RAM, AMD dual core 2.1 mgz, nvidia m 8200 system and i've been trying to install a virtual machine on it.

I install virtualbox, set up my Windows Vista 64-bit, then i double click it, with my official vista 64-bit boot cd already in it, but when the black screen pops up, i get this error message:

[I]VT-x/AMD-V hardware acceleration has been enabled, but is not operational. Your 64-bit guest will fail to detect a 64-bit CPU and will not be able to boot.
Please ensure that you have enabled VT-x/AMD-V properly in the BIOS of your host computer.[/I]

Can anyone resolve this issue??

---

### Post by MindFusion on 2010-02-08
bumpity bump

---

### Post by MindFusion on 2010-02-10
please help ...

---

### Post by SecretCode on 2010-02-10
I presume you have VT-x/AMD-V enabled in the vbox settings - System > Acceleration.

Have you gone into the BIOS settings as that error message suggested? What is available?

Have you checked whether your specific CPU model actually supports AMD-V?

---

### Post by MindFusion on 2010-02-10
> **SecretCode said:**
> I presume you have VT-x/AMD-V enabled in the vbox settings - System > Acceleration.

Have you gone into the BIOS settings as that error message suggested? What is available?

Have you checked whether your specific CPU model actually supports AMD-V?


1) yeah it is already enabled..
2) i get the error message before installing it
3) well I guess so, since i have an AMD processor...

---

### Post by SecretCode on 2010-02-10
That refers to the BIOS settings of the host computer, I'm pretty sure. 

And AMD makes more than one processor! What is your model?
```
grep name /proc/cpuinfo
```
Not all have AMD-V: [http://en.wikipedia.org/wiki/X86_virtualization#AMD_virtualization_.28AMD-V.29](http://en.wikipedia.org/wiki/X86_virtualization#AMD_virtualization_.28AMD-V.29)
```
grep svm /proc/cpuinfo
```

---

### Post by MindFusion on 2010-02-11
If i do the first code, i get:
model name	: AMD Athlon Dual-Core QL-64
model name	: AMD Athlon Dual-Core QL-64

if i do the second one, i get:
grep svm /proc/cpuinfo
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch osvw skinit
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch osvw skinit

---

### Post by SecretCode on 2010-02-11
Since svm appears in the processor capabilities, you're OK.

But you still need to go into the host's BIOS and see if there is a setting to enable it.

---

