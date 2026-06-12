---
title: "i5 and multicore"
date: 2011-04-22
forum: Server Platforms
---

### Post by matux on 2011-04-22
Hi everyone,
I'm looking for my problem's solution by search function, but I didn't find it.
There are some similar threads, but no solutions.. :-(

My system is an ubuntu server 10.10 on an Intel i5.
The system detect only one core, but this is not correct (i5 processor is multicore).
How can I resolve my problem?
Do you have any suggestions?
Thank you very much!

```

$ uname -a
Linux erdos 2.6.35-28-server #50-Ubuntu SMP Fri Mar 18 18:59:25 UTC 2011 x86_64 GNU/Linux

$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 37
model name      : Intel(R) Core(TM) i5 CPU         650  @ 3.20GHz
stepping        : 5
cpu MHz         : 1200.000
cache size      : 4096 KB
physical id     : 0
siblings        : 1
core id         : 0
cpu cores       : 1
apicid          : 0
initial apicid  : 0
fpu             : yes
fpu_exception   : yes
cpuid level     : 11
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt aes lahf_lm ida arat dts tpr_shadow vnmi flexpriority ept vpid
bogomips        : 6422.63
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

```

Have a nice day,

--
matteo

---

### Post by yota on 2011-04-22
Hi Matteo,

are you sure you've not disabled the other cores in BIOS?

I've an i5 and all cores are detected properly, but I saw that my motherboard offers the option to disable cores to save power.

Hope this helps!

---

### Post by matux on 2011-04-22
Hi Yota,
thank you for your answer.
Two weeks ago, I tried to change the options on my motherboard, but I did solve the problem.
I will try again to check the motherboard options.

Did you do anything by software (kernel re-configuration or installed some programs), to use both core?
Thank you again,


--
matteo

---

### Post by yota on 2011-04-22
Hi Matteo,

no, all of my cores (4 since I'm on a i5 2500K) were detected out of the box, no software tuning was needed.

a rapid forum search shows that you are apparently not alone: [http://ubuntuforums.org/showthread.php?t=1604334](http://ubuntuforums.org/showthread.php?t=1604334)
In both case the cpu is an i5 650 I see...

Ubuntu 11.04 will be released next week; if the bios is up to date and all the settings are fine I'd give the latest version a try.

---

### Post by matux on 2011-04-22
I'll waiting for the new version and I'll cross the finger! :)
Thank you!

---

### Post by msandoy on 2011-04-22
Make sure you check your BIOS settings. I do not have Intel, but in my BIOS, there are options to enable or disable all cores. It also has a Auto choise. I do keep it stricktly on enable all, and all my cores are detected out of the box.
The only hickup I have seen is that my CPU has a turbo function while using only one core, but I have not seen the corresponding CPU frequency being used at any time.

I know the 3.3GHz is working, because when I boot into the excellent multi threading OS called windows, it will prefer to use only one core at turbo speed, no matter how heavy the load is.

---

