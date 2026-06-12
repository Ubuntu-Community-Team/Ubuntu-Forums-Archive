---
title: "KVM won't load on quad core HP workstation"
date: 2009-01-22
forum: Virtualisation
---

### Post by codfather on 2009-01-22
Hi,

I'm trying to get kvm running on this HP machine:
Model: DC7800sC9
Quad core intel with vmx support:
processor	: 3
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
stepping	: 11
cpu MHz		: 1596.000
cache size	: 4096 KB
....
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm

4GB Ram
1TB Sata HD's

Ubuntu 8.10 intrepid 2.6.27-11-generic kernel

I have checked the BIOS, and there is no mention of turning the virtualisation elements of the processor on or off, it is a very simple BIOS.

When I attempt to load kvm I get this error message: 
open /dev/kvm: No such file or directory
Could not initialize KVM, will disable KVM support

When I attempt to load the kvm kernel module I get this error message:
FATAL: Error inserting kvm_intel (/lib/modules/2.6.27-11-generic/kernel/arch/x86/kvm/kvm-intel.ko): Operation not supported

Any hints as to how I can work around this would be gratefully appreciated.

Cod

---

### Post by bodhi.zazen on 2009-01-22
You have to activate it in the BIOS

I have a similar box and it is obtuse to say the least, there certainly is NOT a box saying "hey for KVM select this option"

I found mine under the "security" section (best hint I can give you at this time).

You will have to hunt and search through your bios menus unless someone can give you more specific advice. The problem is , as you can imagine, every BIOS is a little different and when you call tech support and ask for help activating KVM they think you are talking a splitter for your Keyboard/Mouse/Video :lolflag:

Don't try to explain it, it only seems to confuse them more ;)

Perhaps if you can get someone at tech support who uses linux (they usually hide one or two in the back rooms) you will have more luck (asking for such a person has helped me several times in the past).

HTH

---

### Post by codfather on 2009-01-22
Ok, I will go through the BIOS again with a magnifying glass and see if it is hidden under security. 

Cod

---

### Post by codfather on 2009-01-27
I found it under security, odd place to put it, but it's working now, thanks for the hint.

Cod

---

### Post by bodhi.zazen on 2009-01-27
> **codfather said:**
> I found it under security, odd place to put it, but it's working now, thanks for the hint.

Cod

You are most welcome, and yes it took me a while to find it as well ;)

If you have a chance -> post exact location for others. I know, I should do it, but that means rebooting my KVM server farm ;).

---

### Post by sriniva7 on 2011-07-07
On an HP 4530s ProBook in System Configuration -> Device Configuration -> Virtualization Technology.

It might require removing power from the system (remove battery and  unplug power cord) (a minute or two worked for me) for the BIOS config  updates to take.

---

