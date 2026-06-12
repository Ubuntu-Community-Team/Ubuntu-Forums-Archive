---
title: "Lucid Server won't install in virtualbox"
date: 2010-05-25
forum: Server Platforms
---

### Post by grcunning on 2010-05-25
I'm trying to install 10.04 server into a virtual machine using virtualbox.  When I start the virtual machine and try to install using the server ISO, I get the following error:

```
This kernel requires an x86-64 CPU, but only detected an i686 CPU.
Unable to boot - please use a kernel appropriate for your CPU.
```

Here is my cpuinfo from lshw:

```

*-cpu:0
          description: CPU
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 5200+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 15.11.2
          slot: Socket M2
          size: 2700MHz
          capacity: 3GHz
          [COLOR="Red"]width: 64 bits[/COLOR]
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae 
mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht
 syscall nx mmxext fxsr_opt rdtscp [COLOR="Red"]x86-64[/COLOR] 3dnowext
 3dnow extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy
 3dnowprefetch cpufreq

```

The host OS is 32bit Lucid Lynx desktop, and virtualbox works fine with a Win7 guest. Does anyone know why this might be happening?

---

### Post by CharlesA on 2010-05-25
Try the i386 version.

I've run into problems running a x64 VM on a 32-bit host.

---

### Post by arrrghhh on 2010-05-25
Is your Win7 guest i386 / x86?

I didn't think running a 32bit host on a 64bit guest didn't work.  Try what was suggested above.

---

### Post by grcunning on 2010-05-25
The 32 bit version worked. Thanks

---

### Post by Talk2sys on 2010-05-26
Intel VT
AMD VT

should be enable.Then it will work with 64,32 all

Thanks

---

### Post by arrrghhh on 2010-05-26
> **Talk2sys said:**
> Intel VT
AMD VT

should be enable.Then it will work with 64,32 all

Thanks

Ah yes, I believe this is true as well.  If you have this technology, you can use a 64-bit guest on a 32-bit host.

---

### Post by CharlesA on 2010-05-26
Ah, that explains why it wouldn't run on that 32-bit host I had, since the processor doesn't support hardware virtualization.

---

