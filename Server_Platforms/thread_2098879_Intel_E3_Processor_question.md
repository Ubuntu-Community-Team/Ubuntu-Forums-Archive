---
title: "Intel E3 Processor question"
date: 2012-12-27
forum: Server Platforms
---

### Post by kpholmes on 2012-12-27
I'm building a entry level server and stuck between two CPUs.

[CENTER]_Intel Xeon **E3-1265L V2**_ - 2.5GHz (3.5GHz Turbo) 45 Watts - [Newegg Link]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819117289&Tpk=1265L")

*or*

_Intel Xeon **E3-1245 V2**_- 3.4GHz (3.8GHz Turbo) 77 Watts - [Newegg Link]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819117284")[/CENTER]




The computer will be on 24/7, the **1265L V2** would be less costly to operate, but the clock speed is *so0* much slower compared with the cheaper and faster **1245 V2**. 

In regards to the **1245 V2** dont all newer CPU's have a power saving features built-in? like turning off unused cores, and lowering clock speeds? would the **1245 V2** always run at 3.4GHz?

Any and all help, comments, or personal opinion is appreciated!:P

---

### Post by darkod on 2012-12-28
I think it will always run at 3.4GHz. Lowering the clock on low usage is a feature found in mobile CPUs more than desktop or server. I wouldn't expect to find that in a server cpu. But I have never really investigated that.

I am more curious about the Watts consumed. Manufacturers state the maximum dissipation it can take, which doesn't mean it will use the full 77W all the time. I would expect to lower the consumption when it doesn't need it. But this is only my assumption, can't provide any evidence for it.

---

### Post by spynappels on 2012-12-28
It also depends what the server will be used for and where it will be used. Low wattage processor and low power/speed HDDs will mean less fan running and will run quieter and cheaper. Unless you will definitely need the extra speed for video rendering or transcoding or for compiling software or something.

---

### Post by CharlesA on 2012-12-28
> **spynappels said:**
> It also depends what the server will be used for and where it will be used. Low wattage processor and low power/speed HDDs will mean less fan running and will run quieter and cheaper. Unless you will definitely need the extra speed for video rendering or transcoding or for compiling software or something.

What he said. I've been running a 3.something Ghz i7 on my server but I use it for VMs and streaming (among other things).

The load on the UPS was around 85W when I checked the other day, but I wasn't doing anything CPU intensive at the time.

Of course that box doesn't have a monitor hooked up.

FWIW: I would grab the higher clock speed one. Never know when they can come in handy.

---

### Post by NigelRen on 2012-12-29
You could always go for the E3-1240 instead of the 1245 - it's basically the same but without the integrated graphics - a bit cheaper and 67W.

I use AMD (Opterons) and they all support power saving features - lower clock rates etc. when not pushed.

If the power saving kicks in - you will probably find the power costs are going to be very similar and so I would go for the faster processor.

---

### Post by sandyd on 2012-12-29
> **kpholmes said:**
> I'm building a entry level server and stuck between two CPUs.

[CENTER]_Intel Xeon **E3-1265L V2**_ - 2.5GHz (3.5GHz Turbo) 45 Watts - [Newegg Link]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819117289&Tpk=1265L")

*or*

_Intel Xeon **E3-1245 V2**_- 3.4GHz (3.8GHz Turbo) 77 Watts - [Newegg Link]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819117284")[/CENTER]




The computer will be on 24/7, the **1265L V2** would be less costly to operate, but the clock speed is *so0* much slower compared with the cheaper and faster **1245 V2**. 

In regards to the **1245 V2** dont all newer CPU's have a power saving features built-in? like turning off unused cores, and lowering clock speeds? would the **1245 V2** always run at 3.4GHz?

Any and all help, comments, or personal opinion is appreciated!:P

I have a 1270
at low loads...
```

root@sv3:~# cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 58
model name      : Intel(R) Xeon(R) CPU E3-1270 V2 @ 3.50GHz
stepping        : 9
cpu MHz         : 874.984
cache size      : 8192 KB
physical id     : 0
siblings        : 8
core id         : 0
cpu cores       : 4
apicid          : 0
initial apicid  : 0
fpu             : yes
fpu_exception   : yes
cpuid level     : 13
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 x2apic popcnt aes xsave avx f16c rdrand lahf_lm ida arat epb xsaveopt pln pts dts tpr_shadow vnmi flexpriority ept vpid fsgsbase smep erms
bogomips        : 6999.87
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 58
model name      : Intel(R) Xeon(R) CPU E3-1270 V2 @ 3.50GHz
stepping        : 9
cpu MHz         : 874.984
cache size      : 8192 KB
physical id     : 0
siblings        : 8
core id         : 1
cpu cores       : 4
apicid          : 2
initial apicid  : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 13
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 x2apic popcnt aes xsave avx f16c rdrand lahf_lm ida arat epb xsaveopt pln pts dts tpr_shadow vnmi flexpriority ept vpid fsgsbase smep erms
bogomips        : 6999.87
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

processor       : 2
vendor_id       : GenuineIntel
cpu family      : 6
model           : 58
model name      : Intel(R) Xeon(R) CPU E3-1270 V2 @ 3.50GHz
stepping        : 9
cpu MHz         : 874.984
cache size      : 8192 KB
physical id     : 0
siblings        : 8
core id         : 2
cpu cores       : 4
apicid          : 4
initial apicid  : 4
fpu             : yes
fpu_exception   : yes
cpuid level     : 13
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 x2apic popcnt aes xsave avx f16c rdrand lahf_lm ida arat epb xsaveopt pln pts dts tpr_shadow vnmi flexpriority ept vpid fsgsbase smep erms
bogomips        : 6999.87
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

processor       : 3
vendor_id       : GenuineIntel
cpu family      : 6
model           : 58
model name      : Intel(R) Xeon(R) CPU E3-1270 V2 @ 3.50GHz
stepping        : 9
cpu MHz         : 874.984
cache size      : 8192 KB
physical id     : 0
siblings        : 8
core id         : 3
cpu cores       : 4
apicid          : 6
initial apicid  : 6
fpu             : yes
fpu_exception   : yes
cpuid level     : 13
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 x2apic popcnt aes xsave avx f16c rdrand lahf_lm ida arat epb xsaveopt pln pts dts tpr_shadow vnmi flexpriority ept vpid fsgsbase smep erms
bogomips        : 6999.87
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

```

The frequency is controlled by cpufreq, so you might want to switch to the ondemand governer using cpufreqd or something. I have set mine up with cpufreqd so that there are emergency heat shutoffs (downclocks processor to the lowest setting when it reaches a certain temperature, and shuts down when it gets too hot)

---

