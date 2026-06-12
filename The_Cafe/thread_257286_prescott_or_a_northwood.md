---
title: "prescott or a northwood?"
date: 2006-09-14
forum: The Cafe
---

### Post by Thanatios on 2006-09-14
How to find out, if I have a prescott or a northwood?

I have bought my PC like in 2003-2004. And got a new motherboard (because my old one burned down) in 2005. So now I dont know exacly what kind of PC I have.

Any way to find it out, without opening the case? Thanks in advance.

---

### Post by jdong on 2006-09-14
Take a look at cat /proc/cpuinfo

Note the model number and stepping numbers.


Then, match it to [http://en.wikipedia.org/wiki/List_of_Intel_Pentium_4_microprocessors](http://en.wikipedia.org/wiki/List_of_Intel_Pentium_4_microprocessors)

---

### Post by Thanatios on 2006-09-14
Well, I have been looking, and looking. And just coulnt find out wich one I have.

This is what I got:
```
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Pentium(R) 4 CPU 3.06GHz
stepping        : 7
cpu MHz         : 3074.203
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe cid xtpr
bogomips        : 6153.88

```

So can anyone explain it to me?

---

### Post by jdong on 2006-09-14
It's a family 15 model 2, which according to that wikipedia page would be a Northwood.

---

### Post by Thanatios on 2006-09-14
Thank you for your answer!

I wonder, how can it be a Family 15 model 2 northwood, if its 3066 MHz. =/
The highest amount of MHZ I found on the Family 15 Model 2's whas 2800 MHz.

Can anyone explain this?

---

### Post by Roger Mudd on 2006-09-14
Scroll down a bit under "Pentium 4 HT"
Looks like you may find your culprit under "'Northwood' (130 nm)"

---

### Post by jdong on 2006-09-14
> **Thanatios said:**
> Thank you for your answer!

I wonder, how can it be a Family 15 model 2 northwood, if its 3066 MHz. =/
The highest amount of MHZ I found on the Family 15 Model 2's whas 2800 MHz.

Can anyone explain this?

Sure, it's a hyperthreading northwood. Take a look lower under the HT sections.

---

### Post by Thanatios on 2006-09-14
To bad its Northwood. I guess I wont be seeing a mac on my PC then =( (/me bought a Mac x86 CD for nothing)

---

### Post by jdong on 2006-09-14
Umm, it's not legal to install OSX on a non-Apple machine anyway...

---

### Post by kigina on 2006-09-14
northwood

---

### Post by Stew2 on 2006-09-14
I believe the Prescotts have 1MB of level 2 cache as well, whereas your processor has 512KB. Don't feel bad though, that is an awesome processor :D . The Northwoods run cooler as well. I thought I read somewhere that independent testing showed that the Prescotts didn't really run any faster than the Northwoods anyway (in real world benchmark tests). Don't quote me on that though 'cause I can't remember where I read it :D 

Regards,
Stew2

---

### Post by jdong on 2006-09-14
Performance numbers were strange, inconsistent, and disappointing for netburst in general.... thank god for Athlon64's in the meantime, and the Intel Cores now :)

---

