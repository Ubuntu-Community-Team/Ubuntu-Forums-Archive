---
title: "Could not initialize KVM, will disable KVM support"
date: 2010-03-18
forum: Virtualisation
---

### Post by Aubergines on 2010-03-18
Due to a recent machine upgrade from an old Pentium 4 to a (and also old) Core2 Duo I decided to make the switch to KVM from Vmware ESXi3. I did a fresh Ubuntu server install and I'm running into the following error:
```
open /dev/kvm: Is a directory
Could not initialize KVM, will disable KVM support
commandline read: kvm
```

My processor is an [Intel Core2 Duo E6300](http://ark.intel.com/Product.aspx?id=27248) which has Intel® Virtualization Technology (VT-x).

Output of proc/cpuinfo is as follows:
```

del@kvm:~$ cat /proc/cpuinfo | grep vmx
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl [color=red]vmx[/color] est tm2 ssse3 cx16 xtpr pdcm lahf_lm tpr_shadow
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl [color=red]vmx[/color] est tm2 ssse3 cx16 xtpr pdcm lahf_lm tpr_shadow
```

Here's is the lsmod output:
```
del@kvm:~$ lsmod | grep kvm
kvm_intel              51528  0
kvm                   190648  1 kvm_intel
```
Does anyone have any idea on why KVM is falling back to no hardware acceleration mode?

---

### Post by casylum on 2011-12-04
I am having the exact same problem.  What was your solution?

---

### Post by casylum on 2011-12-04
[Solved]

I fixed my problem and I thought I would update this post.

If you use "kvm" for your hostname and use LVM then LVM will create a folder "/dev/kvm" that inhibits the kvm driver from being loaded.

This specifically fixes the error "open /dev/kvm: Is a directory".

My solution was to re-install the OS with a different hostname.

Hopes this helps someone, it took me a few days to figure this one out.

---

