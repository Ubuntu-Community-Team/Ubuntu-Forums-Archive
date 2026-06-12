---
title: "Only getting 32 bit options in Virtual Box"
date: 2020-10-26
forum: Virtualisation
---

### Post by rsteinmetz70112 on 2020-10-26
As far as I can tell my motherboard  (Asrock N68C-GS4 FX) has no setting for AMD-V only "Secure Virtual Machine" and it is [ENABLED]
The processor is an AMD FX8320E. It says it has AMD-V. The Motherboard has the most recent version of the firmware.
I installed Virtual Box on a 64 bit Ubuntu 20.04 desktop but all I get are 32-bit options. 
How can I enable 64bit options? I want to install 64bit Windows as a VM.

---

### Post by TheFu on 2020-10-26
```
$ lscpu |grep svm
Flags:                 fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 
ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc rep_good nopl nonstop_tsc cpuid extd_apicid aperfmperf 
pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 movbe popcnt aes xsave avx f16c rdrand lahf_lm cmp_legacy 
**[COLOR="#FF0000"]svm[/COLOR]** extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw skinit wdt tce 
topoext perfctr_core perfctr_nb bpext perfctr_llc mwaitx cpb hw_pstate sme ssbd ibpb vmmcall fsgsbase bmi1 avx2 smep 
bmi2 rdseed adx smap clflushopt sha_ni xsaveopt xsavec xgetbv1 xsaves clzero irperf xsaveerptr arat npt lbrv **[COLOR="#FF0000"]svm_lock[/COLOR]** 
nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold avic v_vmsave_vmload vgif 
overflow_recov succor smca
```

---

### Post by rsteinmetz70112 on 2020-10-26
I had already checked that. I don't exactly get the same thing, but I do get those flags.
```
~$ lscpu |grep svm
Flags:                 fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb 
rdtscp lm constant_tsc rep_good nonstop_tsc extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 popcnt aes xsave avx f16c lahf_lm 
cmp_legacy** [COLOR=blue]svm[/COLOR] **extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs xop skinit wdt lwp fma4 tce nodeid_msr tbm topoext perfctr_core perfctr_nb 
cpb hw_pstate vmmcall bmi1 arat npt lbrv**[COLOR=blue] svm_lock[/COLOR] **nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold
```

---

### Post by TheFu on 2020-10-26
Well, my only AMD CPU is a Ryzen 5 2600. ;)

Do you have only 1 hypervisor installed?  Only 1 can "grab" the hardware.

---

### Post by rsteinmetz70112 on 2020-10-26
> **TheFu said:**
> Well, my only AMD CPU is a Ryzen 5 2600. ;)

Do you have only 1 hypervisor installed?  Only 1 can "grab" the hardware.

I only have Virtual BOx installed. it opens just fine but doesn't offer to install 64 bit options

---

### Post by TheFu on 2020-10-26
The only other thing I could guess is that it really isn't a 64-bit Ubuntu installed?  **uname -m** should show the architecture.
```
$ uname -m
armv7l

$ uname -m
x86_64
```

I don't have any other 32-bit left here. Migrated a desktop from 32-bit 16.04 to 64-bit 20.04 in June. ;(

How tied are you to virtualbox?

---

### Post by rsteinmetz70112 on 2020-10-26
Here's what I get.

```
~$ uname -m
x86_64
```

---

### Post by TheFu on 2020-10-26
[https://superuser.com/questions/866962/why-does-virtualbox-only-have-32-bit-option-no-64-bit-option-on-windows-7](https://superuser.com/questions/866962/why-does-virtualbox-only-have-32-bit-option-no-64-bit-option-on-windows-7)
Is hyper-v enabled and all hyper-v services disabled?

---

### Post by rsteinmetz70112 on 2020-10-27
I'm not sure how to enable Hyper-V on Linux. I understood it was a Windows thing not a hardware thing. I have seen how to enable it in Windows 10. I have no Windows installed on the computer.

In a effort to be very sure I went back through all of the options to make sure there were no virtualization options hidden in the mother board. I opened every menu based on a comment I found about a different motherboard saying the setting was "hidden" in the overclocking menu. I still only found the option I listed above. "Secure Virtual Machine" and it was [ENABLED]. I set is to DISABLED] saved the changes rebooted and I still had only 32 bit options. I went back into the Motherboard and went through event menu again and still didn't see any other virtualization options. I changed "Secure Virtual Machine" to [ENABLED] saved and rebooted, this time I have 64 bit options in Virtual Box, I have no idea what happened. 

I've now installed Windows 7 64 bit in Virtual Box and it's busy downloading all of the 160 odd Windows 7 updates, about 1.5 GB. I'm sure there will be a round 2 of updates.

For my next trick I'm going to see if I can enable the lpt port pass through in Virtual Box. That will have to wait until I have Windows 7 fully updated and see what else I need to do to actually use the VM, like secure it but maintain some connection to the Internet.

---

### Post by TheFu on 2020-10-27
Great!  Glad you found the solution!

The Hyper-V thing was me forgetting that people use Virtualbox on Linux.  I never did after my first attempt kept crashing the entire physical machine. Oddly, that same machine has been running without issues using KVM all these years. Hopefully, it will be retired soon, replaced by a cheap Ryzen that is 4+x faster.

---

