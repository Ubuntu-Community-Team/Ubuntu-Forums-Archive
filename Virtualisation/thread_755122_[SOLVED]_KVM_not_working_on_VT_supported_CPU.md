---
title: "[SOLVED] KVM not working on VT supported CPU"
date: 2008-04-14
forum: Virtualisation
---

### Post by Daishiman on 2008-04-14
Hey all, I have an Intel Core Duo T2400 type processor, yet when I try to launch kvm I get this error:

root@PcChica:~# kvm
open /dev/kvm: No such file or directory
Could not initialize KVM, will disable KVM support
Ubuntu does not support running KVM without hardware acceleration. Sorry

Here's the cpuinfo for one of the cores:
processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 14
model name	: Intel(R) Core(TM) Duo CPU      T2400  @ 1.83GHz
stepping	: 12
cpu MHz		: 1000.000
cache size	: 2048 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon bts pni monitor vmx est tm2 xtpr
bogomips	: 3657.56
clflush size	: 64

Thanks

---

### Post by ericy on 2008-04-14
Did you load the kernel module?

modprobe kvm_intel
(I hope I remember it right because mine is kvm_amd)

---

### Post by Daishiman on 2008-04-15
I tried it and I got this back:

root@PcChica:~# modprobe kvm_intel
FATAL: Error inserting kvm_intel (/lib/modules/2.6.24-16-generic/kernel/arch/x86/kvm/kvm-intel.ko): Operation not supported

---

### Post by cguy09 on 2008-04-15
Some BIOS's give you the ability to disable the Virtualization features of the CPU.

Suggest you check the BIOS settings to see if this is the case, and be sure that they are enabled.

Then try loading kvm again, or see if the error msg shows up in your log files...

Mark

---

### Post by soapytheclown on 2008-04-15
thanks mine wasnt working and it was a flag in the bios =D

---

### Post by Daishiman on 2008-04-16
I've upgraded to the latest BIOS level and enabled VT, but I still get the error message :(

---

### Post by Daishiman on 2008-04-17
Well, it seems that cold booting the machine and changin ownership of /dev/kvm solved it :D

---

### Post by dendrobates on 2008-04-20
you should add your user to the kvm group, not change the permissions of /dev/kvm.

If you are using Hardy and are a member of kvm group, the module is loaded automatically.

---

### Post by WendyWeber on 2008-05-01
I'm having the same problem, "qemu: could not open disk image windows.img", regardless of what I do. Any other solutions?

---

