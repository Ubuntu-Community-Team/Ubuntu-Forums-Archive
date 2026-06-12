---
title: "Is this system 32 bit, or 64 bit?"
date: 2009-09-16
forum: The Cafe
---

### Post by Sporkman on 2009-09-16
[http://www.newegg.com/Product/Product.aspx?Item=N82E16856167032](http://www.newegg.com/Product/Product.aspx?Item=N82E16856167032)

I bought the above to use as a home fileserver, next I'll be installing Ubuntu server.

Does anybody know which specific Atom processor is on this? It's a 1.6gz processor, but there are both 32 bit:

[http://ark.intel.com/Product.aspx?id=35463](http://ark.intel.com/Product.aspx?id=35463)

and 64 bit:

[http://ark.intel.com/Product.aspx?id=35635](http://ark.intel.com/Product.aspx?id=35635)

...versions. Googling didn't help, though one reviewer on newegg said "I ran Securable from grc.com and the utility says that it is capable of 64-bit."...

---

### Post by dragos240 on 2009-09-16
Buy it, install it, install Linux, run lspci.

---

### Post by Sporkman on 2009-09-16
> **dragos240 said:**
> Buy it, install it, install Linux, run lspci.

Do I install 32-bit linux, or 64-bit linux?

---

### Post by dragos240 on 2009-09-16
Both will work. I set up 32 bit linux OSes on my computer.

---

### Post by Sporkman on 2009-09-16
> **dragos240 said:**
> Both will work.

So this machine has a 64 bit processor?

---

### Post by dragos240 on 2009-09-16
I'm not sure, I was joking by the way when I said buy it first. but a 32 bit os Will work on a 64 bit processor AND a 32 bit processor. So either way, it'll work.

---

### Post by PurposeOfReason on 2009-09-16
> **dragos240 said:**
> Both will work. I set up 32 bit linux OSes on my computer.

EDIT - Looks like it has the 64bit atom 230.
[http://shopper.cnet.com/desktops/msi-wind-pc-atom/4014-3118_9-33346974.html](http://shopper.cnet.com/desktops/msi-wind-pc-atom/4014-3118_9-33346974.html) [+]

---

### Post by MasterNetra on 2009-09-16
I believe it should run 64bit: [http://en.wikipedia.org/wiki/Intel_Atom](http://en.wikipedia.org/wiki/Intel_Atom) When in doubt though use 32 bit.

---

### Post by Sporkman on 2009-09-16
> **PurposeOfReason said:**
> EDIT - Looks like it has the 64bit atom 230.
[http://shopper.cnet.com/desktops/msi-wind-pc-atom/4014-3118_9-33346974.html](http://shopper.cnet.com/desktops/msi-wind-pc-atom/4014-3118_9-33346974.html) [+]

Good find, thanks!

---

### Post by cariboo on 2009-09-16
You could boot from a Live CD and run:

```
cat /proc/cpuinfo
```

To see what type of cpu it is running.

---

### Post by dragos240 on 2009-09-16
> **cariboo907 said:**
> You could boot from a Live CD and run:

```
cat /proc/cpuinfo
```To see what type of cpu it is running.

It's already solved caiboo.

---

### Post by cariboo on 2009-09-16
It hadn't been marked solved yet when I started the post. :)

---

### Post by Sporkman on 2009-09-16
Not a bad price for a new 64 bit, low power server platform, eh?

I also bought 1G ram, a pair of 500G HDs (will run as RAID1), and an external CD/DVD drive.

All together went for $358 including shipping.

---

### Post by Sporkman on 2009-09-20
Works great - ubuntu 9.04 server 64-bit works fine on it.

FYI - a floating-point intensive program (single thread) I have runs about half as fast on it as it does on my pentium D 3gz machine with the exact same memory & OS. Not too shabby, given how low power & inexpensive it is.

Here's its /proc/cpuinfo:

processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 28
model name	: Intel(R) Atom(TM) CPU  230   @ 1.60GHz
stepping	: 2
cpu MHz		: 1596.140
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 1
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm lahf_lm
bogomips	: 3192.28
clflush size	: 64
cache_alignment	: 64
address sizes	: 32 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 28
model name	: Intel(R) Atom(TM) CPU  230   @ 1.60GHz
stepping	: 2
cpu MHz		: 1596.140
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 1
apicid		: 1
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm lahf_lm
bogomips	: 3192.02
clflush size	: 64
cache_alignment	: 64
address sizes	: 32 bits physical, 48 bits virtual
power management:


Uh... Does this mean it's dual-core??

---

### Post by Sporkman on 2009-09-20
Core ID is 0 on both, whereas it's 0 & 1 on my actual dual-core pentium D... Hmm...

---

### Post by Sporkman on 2009-09-20
The benchmarks run only slightly longer when I run them around the same time... Did I get a second core for free?! :D

---

### Post by Tipped OuT on 2009-09-20
For future reference....

If you're unsure, always go with the 32 bit so you can check later.

---

### Post by Sporkman on 2009-09-20
> **Tipped OuT said:**
> For future reference....

If you're unsure, always go with the 32 bit so you can check later.

I didn't want to go through all that, when it's easier to ask the good, helpful folks on UF. :)

---

### Post by Mike'sHardLinux on 2009-09-20
> **Sporkman said:**
> Uh... Does this mean it's dual-core??

The Atom 230 is single core, but hyperthreading. The HT is why it looks like 2 cores. 

I bought the version with the Atom 330 (dual core). Great combination of price, performance, and power usage and has been perfectly stable.

---

### Post by Tipped OuT on 2009-09-20
> **Mike'sHardLinux said:**
> The Atom 230 is single core, but hyperthreading. The HT is why it looks like 2 cores. 


Yeah, I have HT too. Got to love it, speeds things up a lot.

---

### Post by Sporkman on 2009-09-20
> **Mike'sHardLinux said:**
> The Atom 230 is single core, but hyperthreading. The HT is why it looks like 2 cores. 


Well that's a nice feature. :) Pretty impressive.

---

### Post by Exodist on 2009-09-20
> **MasterNetra said:**
> I believe it should run 64bit: [http://en.wikipedia.org/wiki/Intel_Atom](http://en.wikipedia.org/wiki/Intel_Atom) When in doubt though use 32 bit.

Agreed,
32bit will work on them all in case you are unsure.

---

### Post by nowin4me on 2009-09-20
Sorry for going off topic but how "eco friendly" is it?
Lol my browser doesn't think "eco" is a word!

---

### Post by Sporkman on 2009-09-20
> **nowin4me said:**
> Sorry for going off topic but how "eco friendly" is it?
Lol my browser doesn't think "eco" is a word!

Well the system comes with a 65 W power supply, so presumably it runs <65 W. The CPU itself is 4 W.

---

### Post by nowin4me on 2009-09-20
4 WATTS? WOW! Thanks for the info!

---

### Post by Sporkman on 2009-09-20
> **nowin4me said:**
> 4 WATTS? WOW! Thanks for the info!

Sure, here are the specs:

[http://ark.intel.com/Product.aspx?id=35635](http://ark.intel.com/Product.aspx?id=35635)

---

