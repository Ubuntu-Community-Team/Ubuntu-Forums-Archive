---
title: "Speedstepping on server"
date: 2009-07-23
forum: Server Platforms
---

### Post by smeerbartje on 2009-07-23
I know it's not common to have a server CPU running at lower speeds, but since it is a home server, I want to try this and to see what the impact is in power consumption. The output of /etc/cpuinfo is:

```

rogier@server:~$ more /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 23
model name      : Intel(R) Core(TM)2 Duo CPU     E7300  @ 2.66GHz
stepping        : 6
cpu MHz         : 1596.000
cache size      : 3072 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
apicid          : 0
initial apicid  : 0
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm const
ant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm
bogomips        : 5306.81
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 23
model name      : Intel(R) Core(TM)2 Duo CPU     E7300  @ 2.66GHz
stepping        : 6
cpu MHz         : 1596.000
cache size      : 3072 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
apicid          : 1
initial apicid  : 1
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm const
ant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm
bogomips        : 5306.75
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

```
Now how can I see on what frequency my processor is running at? On Ubuntu desktop (running on my laptop) I see that the CPU is automatically slowing down or speeding up; depending on the jobs it's doing. It would be very nice to have the same functionality on my server.

---

### Post by bacil on 2009-07-23
try this

```

cat /proc/cpuinfo|grep 'cpu MHz' | sed -e 's/.*: //'| sed -e 's/\..../ MHz/' | head -n 1

```this will give you cpu speed in exact time of the run

and

```

cat /proc/cpuinfo|grep 'cpu MHz'


```

show both cores

---

### Post by smeerbartje on 2009-07-23
My processor is an Intel [Core Duo E7300](http://processorfinder.intel.com/details.aspx?sSpec=SLAPB). Does this mean it is not running at it's full speed at the moment? CPUINFO shows a speed of 1596.000 Mhz, while the intel website shows 2.66 GHz.

---

### Post by dragos2 on 2009-07-23
> **smeerbartje said:**
> My processor is an Intel [Core Duo E7300]("http://processorfinder.intel.com/details.aspx?sSpec=SLAPB"). Does this mean it is not running at it's full speed at the moment? CPUINFO shows a speed of 1596.000 Mhz, while the intel website shows 2.66 GHz.

It has smart power control build into it, you can try to disable it from the bios - if your
bios supports it.

---

### Post by bacil on 2009-07-23
yup .. my laptop is 1600 atom and is running 800 most of the time

you may try to get cpudyn for your server and acpid

```
sudo apt-get install cpudyn
```
and
```
sudo apt-get install acpid
```

cpudyn -is deamon for dynamicalichanging cpu speed and acpid takes care of powering it :-)

---

### Post by smeerbartje on 2009-07-23
Okay, I have installed cpudyn; but when I type: cpudynd, it says:

```

cpydynd version 1.0 Copyright: Ricardo Galli <gallir@uib.es>
cpydynd: CPU frequency control disables
Error: Nothing to do, exiting

```
What to do next?

---

### Post by bacil on 2009-07-23
does it really say cpydynd ?

```
man cpudyn
```

check if you have these modules 
acpi_cpufreq cpufreq_powersave cpufreq_userspace freq_table

---

