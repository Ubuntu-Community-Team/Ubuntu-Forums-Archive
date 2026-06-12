---
title: "Virtualbox on my Intrepid AMD64 only offers 32bit virtualisation"
date: 2008-11-27
forum: Virtualisation
---

### Post by jarl on 2008-11-27
When I create a virtual machin in virtualbox OSE, it apparently only creates a 32bit machine. Nowhere in the settings can I see the CPU architecture of the virtual machine, however when I try to install ubuntu-server AMD64 on it, the boot CD complains "This kernel requires an x86-64 CPU, but only detected an i686 CPU. Unable to boot - please use a kernel appropriate for your system.

Why does virtualbox on Intrepid 64 bit not support 64 bit guests?

Jarl

---

### Post by void_false on 2008-11-27
Some say that you should enable virtualization and PAE support to be able to run x64 OS. However that didnt help me.

---

### Post by bodhi.zazen on 2008-11-27
I have this issue on one of my 64 bit hosts, it must be something with the processor but I do not know what.

What version of virtualbox are you using ? OSE or PUEL ? what version ?

Also I believe you must be running x86_64 on the host as well (Just checking).

---

### Post by jarl on 2008-11-28
> **void_false said:**
> Some say that you should enable virtualization and PAE support to be able to run x64 OS. However that didnt help me.

It didn´t help me either.

Jarl

---

### Post by jarl on 2008-11-28
> **bodhi.zazen said:**
> I have this issue on one of my 64 bit hosts, it must be something with the processor but I do not know what.

What version of virtualbox are you using ? OSE or PUEL ? what version ?

Also I believe you must be running x86_64 on the host as well (Just checking).

Yes, my host is AMD64. Good point, I didn't mention that explicitely in my initial post. More precisely it is (from /proc/cpuinfo)
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 36
model name      : AMD Turion(tm) 64 Mobile Technology ML-40
stepping        : 2
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmovpat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt lm 3dnowext 3dnow up rep_good nopl pni lahf_lm

I am using virtualbox-ose 2.0.4. What is PUEL?

Jarl

---

### Post by bodhi.zazen on 2008-11-28
PUEL = the version you DL from Sun. I suggest you try that version.

[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

[http://www.virtualbox.org/wiki/Editions](http://www.virtualbox.org/wiki/Editions)

---

