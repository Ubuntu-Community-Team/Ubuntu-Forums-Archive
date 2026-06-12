---
title: "Xen Kernel on Intel Q6600 hasn't VMX cpu flag"
date: 2008-10-30
forum: Virtualisation
---

### Post by Rmanola on 2008-10-30
Hello, I've installed xen from the sources on my Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz  with Ubuntu Server 8.04 x64 . Running with the default installation Ubuntu Kernel, when I type: 
```

# cat /proc/cpuinfo
...
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr
 pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm
 pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni
 monitor ds_cpl **vmx** est tm2 ssse3 cx16 xtpr lahf_lm
...

```
I see all the CPU flags OK, including the most important to me, the "vmx" flag that enables my CPU to run Xen on HVM.

After compiling the modified kernel for using with XEN and rebooting the computer, I get no more the "vmx" cpu flags when I list the cpuinfo:

```

# cat /proc/cpuinfo
...
flags		: fpu de tsc msr pae cx8 apic sep mtrr cmov pat 
clflush acpi mmx fxsr sse sse2 ss ht syscall nx lm constant_tsc
 rep_good pni est ssse3 cx16 lahf_lm
... 

```

Even trying to install a compiled kernel xen-ready from Launchpad ([https://launchpad.net/ubuntu/hardy/amd64/linux-image-2.6.24-21-xen/2.6.24-21.42](https://launchpad.net/ubuntu/hardy/amd64/linux-image-2.6.24-21-xen/2.6.24-21.42)) I get the same listing without the "vmx" cpu flag.

I have compiled the XEN kernel using the default procedure:
[LIST]
[*]Downloading the kernel from kernel.ubuntu.com through git (git clone [git://kernel.ubuntu.com/kernel/ubuntu-hardy.git](git://kernel.ubuntu.com/kernel/ubuntu-hardy.git))
[*]And, then, compiling (fakeroot debian/rules custom-binary-xen)
[*]Finally, installing (dpkg -i linux-image ... -xen.deb)
[/LIST]

I would like to know why is this happening and what could I do to get the VMX cpu flag to be shown when I list the cpuinfo.

(The VT technology is enabled at my motherboard's Setup)

Greetings.

---

