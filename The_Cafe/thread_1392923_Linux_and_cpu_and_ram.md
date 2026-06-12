---
title: "Linux and cpu and ram"
date: 2010-01-28
forum: The Cafe
---

### Post by nothingspecial on 2010-01-28
like I said - boring

---

### Post by davec64 on 2010-01-28
For me it's being able to transcode video in 35mins on my Athlon X4 620 (4GB RAM) where as it use to take over 4 hours on my old XP2400 with 1.5gb ram. :)

---

### Post by RabbitWho on 2010-01-28
4GB of ram is better than the 192 mb of ram I had before, and the laptop only cost 500 euro, which I think is good going, fingers crossed it lasts a while.

---

### Post by pirateghost on 2010-01-28
This is my "SAN".  it has one samba share (not really used) but a lot of iscsi targets for my esxi hosts (2) and all my windows boxes to run backups.  my main interest in this set up was a lot of RAM for caching on the iscsi (unfortunately only had 2gb to spare for it) and a couple of quality Intel server gig nics running on the pci-ex slots.  i have a pci sata card for a couple of the drives but for the majority of the storage thats in it i have a rocketraid 2640x4 running 4x1tb drives RAID5

throughput is impressive
```
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 35
model name      : Dual Core AMD Opteron(tm) Processor 165
stepping        : 2
cpu MHz         : 1808.304
cache size      : 1024 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
apicid          : 0
initial apicid  : 0
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow rep_good pni lahf_lm cmp_legacy
bogomips        : 3616.60
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp

processor       : 1
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 35
model name      : Dual Core AMD Opteron(tm) Processor 165
stepping        : 2
cpu MHz         : 1808.304
cache size      : 1024 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
apicid          : 1
initial apicid  : 1
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow rep_good pni lahf_lm cmp_legacy
bogomips        : 3616.74
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp

```

my other debian machines are all VMs inside my esxi boxes and so they use the storage supplied by my ubuntu 9.10 server box.

my ubuntu desktop 9.10 64bit is on my laptop.  i have the need to run VMs sometimes on it, so i have 4gb ram in it with a 2.5ghz core 2 duo.

---

### Post by nothingspecial on 2010-01-28
even more boring

---

### Post by juancarlospaco on 2010-01-28
***Virtualization.***

---

### Post by squilookle on 2010-01-28
Nothing wrong with having more than you *need*. Allows you to do more stuff, and faster. It also sort of futureproofs the computer - everything is definately getting heavier. 

I have 512mb ram, and its ok for browsing the web, coding, playing music. It struggles with image editing if you have a lot of layers or arwe working from several images. And any video envcoding is painful. 

Games are no go, it will run compiz but you can't do anything usefull with it. Can't wait to upgrade, even though the computer has been a fantastic one for 5 years the more ram{aster the cpu. The better. I plan to replace it in 12 months.

---

### Post by nothingspecial on 2010-01-28
boring

---

### Post by nothingspecial on 2010-01-28
boring
boring

---

### Post by nothingspecial on 2010-01-28
boring
boring
boring

---

### Post by Paqman on 2010-01-28
> **nothingspecial said:**
> you can do pretty much anything, including video encoding, at a reasonable speed with an old pc. No?

Video encoding can never be too fast.

---

