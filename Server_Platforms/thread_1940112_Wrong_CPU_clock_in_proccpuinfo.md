---
title: "Wrong CPU clock in /proc/cpuinfo"
date: 2012-03-13
forum: Server Platforms
---

### Post by ashi009 on 2012-03-13
Hi,

I'm running HPL on a cluster which runs Ubuntu 11.10 on each nodes, and the HPL reading was strange, so I checked around to see if there is anything went wrong. Here is what I got in /proc/cpuinfo, obviously the reading was wrong while the system is on a full load state.

Any ideas?

thanks

$ cat /proc/loadavg
7.99 6.52 5.77 9/146 13829

$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 23
model name      : Intel(R) Xeon(R) CPU           E5440  @ 2.83GHz
stepping        : 10
cpu MHz         : 1998.000
cache size      : 6144 KB
physical id     : 0
siblings        : 4
core id         : 0
cpu cores       : 4
apicid          : 0
initial apicid  : 0
fpu             : yes
fpu_exception   : yes
cpuid level     : 13
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm dca sse4_1 xsave lahf_lm dts tpr_shadow vnmi flexpriority
bogomips        : 5666.27
clflush size    : 64
cache_alignment : 64
address sizes   : 38 bits physical, 48 bits virtual
power management:

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 23
model name      : Intel(R) Xeon(R) CPU           E5440  @ 2.83GHz
stepping        : 10
cpu MHz         : 1998.000
cache size      : 6144 KB
physical id     : 1
siblings        : 4
core id         : 0
cpu cores       : 4
apicid          : 4
initial apicid  : 4
fpu             : yes
fpu_exception   : yes
cpuid level     : 13
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm dca sse4_1 xsave lahf_lm dts tpr_shadow vnmi flexpriority
bogomips        : 5667.31
clflush size    : 64
cache_alignment : 64
address sizes   : 38 bits physical, 48 bits virtual
power management:

processor       : 2
vendor_id       : GenuineIntel
cpu family      : 6
model           : 23
model name      : Intel(R) Xeon(R) CPU           E5440  @ 2.83GHz
stepping        : 10
cpu MHz         : 1998.000
cache size      : 6144 KB
physical id     : 0
siblings        : 4
core id         : 1
cpu cores       : 4
apicid          : 1
initial apicid  : 1
fpu             : yes
fpu_exception   : yes
cpuid level     : 13
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm dca sse4_1 xsave lahf_lm dts tpr_shadow vnmi flexpriority
bogomips        : 5667.31
clflush size    : 64
cache_alignment : 64
address sizes   : 38 bits physical, 48 bits virtual
power management:

processor       : 3
vendor_id       : GenuineIntel
cpu family      : 6
model           : 23
model name      : Intel(R) Xeon(R) CPU           E5440  @ 2.83GHz
stepping        : 10
cpu MHz         : 1998.000
cache size      : 6144 KB
physical id     : 0
siblings        : 4
core id         : 2
cpu cores       : 4
apicid          : 2
initial apicid  : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 13
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm dca sse4_1 xsave lahf_lm dts tpr_shadow vnmi flexpriority
bogomips        : 5667.40
clflush size    : 64
cache_alignment : 64
address sizes   : 38 bits physical, 48 bits virtual
power management:

processor       : 4
vendor_id       : GenuineIntel
cpu family      : 6
model           : 23
model name      : Intel(R) Xeon(R) CPU           E5440  @ 2.83GHz
stepping        : 10
cpu MHz         : 1998.000
cache size      : 6144 KB
physical id     : 0
siblings        : 4
core id         : 3
cpu cores       : 4
apicid          : 3
initial apicid  : 3
fpu             : yes
fpu_exception   : yes
cpuid level     : 13
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm dca sse4_1 xsave lahf_lm dts tpr_shadow vnmi flexpriority
bogomips        : 5667.29
clflush size    : 64
cache_alignment : 64
address sizes   : 38 bits physical, 48 bits virtual
power management:

processor       : 5
vendor_id       : GenuineIntel
cpu family      : 6
model           : 23
model name      : Intel(R) Xeon(R) CPU           E5440  @ 2.83GHz
stepping        : 10
cpu MHz         : 1998.000
cache size      : 6144 KB
physical id     : 1
siblings        : 4
core id         : 1
cpu cores       : 4
apicid          : 5
initial apicid  : 5
fpu             : yes
fpu_exception   : yes
cpuid level     : 13
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm dca sse4_1 xsave lahf_lm dts tpr_shadow vnmi flexpriority
bogomips        : 5667.47
clflush size    : 64
cache_alignment : 64
address sizes   : 38 bits physical, 48 bits virtual
power management:

processor       : 6
vendor_id       : GenuineIntel
cpu family      : 6
model           : 23
model name      : Intel(R) Xeon(R) CPU           E5440  @ 2.83GHz
stepping        : 10
cpu MHz         : 1998.000
cache size      : 6144 KB
physical id     : 1
siblings        : 4
core id         : 2
cpu cores       : 4
apicid          : 6
initial apicid  : 6
fpu             : yes
fpu_exception   : yes
cpuid level     : 13
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm dca sse4_1 xsave lahf_lm dts tpr_shadow vnmi flexpriority
bogomips        : 5667.01
clflush size    : 64
cache_alignment : 64
address sizes   : 38 bits physical, 48 bits virtual
power management:

processor       : 7
vendor_id       : GenuineIntel
cpu family      : 6
model           : 23
model name      : Intel(R) Xeon(R) CPU           E5440  @ 2.83GHz
stepping        : 10
cpu MHz         : 1998.000
cache size      : 6144 KB
physical id     : 1
siblings        : 4
core id         : 3
cpu cores       : 4
apicid          : 7
initial apicid  : 7
fpu             : yes
fpu_exception   : yes
cpuid level     : 13
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm dca sse4_1 xsave lahf_lm dts tpr_shadow vnmi flexpriority
bogomips        : 5667.31
clflush size    : 64
cache_alignment : 64
address sizes   : 38 bits physical, 48 bits virtual
power management:

---

### Post by Doug S on 2012-03-13
Do you have the lm-sensors stuff installed? And did your CPU's slow down because of heat issues? I.E. how is your cooling?
 
Just a thought...

---

### Post by ashi009 on 2012-03-13
thanks.

no lm-sensors installed. and i checked /var/log/syslog, there is no complaint about sensors failures. may be I should install one to check out temperatures.

the system is in a IBM blade container, and the blade next to this with redhat 4 (really old version), its cpu freq changed proper while load rises. 

I also tried to reboot my system, and I found something more interesting: 
if I check out /proc/cpuinfo immediately after boot, and I will see all CPU running on theirs top speed, and If I start a heavy load program (like a infinity loop) running on one core, that core speed will keep up while all others drop. and if I terminated that program and started it again, the cpu freq will remain low.

and seems I lost my VPN connection to the server now... don't know what to do next.

---

### Post by ssam on 2012-03-13
most modern CPUs can adjust their clock speed. The default governor on linux is 'on demand' which keeps the clock speed low to save power when idle, and speeds it up to do work when needed.

[http://www.mjmwired.net/kernel/Documentation/cpu-freq/governors.txt](http://www.mjmwired.net/kernel/Documentation/cpu-freq/governors.txt)

it takes slightly odd workloads for 'performance' to beat 'on demand', for example if you need very short spikes of processing so there is not enough time for the clock speed to ramp up.

---

### Post by ashi009 on 2012-03-13
> **ssam said:**
> most modern CPUs can adjust their clock speed. The default governor on linux is 'on demand' which keeps the clock speed low to save power when idle, and speeds it up to do work when needed.

[http://www.mjmwired.net/kernel/Documentation/cpu-freq/governors.txt](http://www.mjmwired.net/kernel/Documentation/cpu-freq/governors.txt)

it takes slightly odd workloads for 'performance' to beat 'on demand', for example if you need very short spikes of processing so there is not enough time for the clock speed to ramp up.


the problem is, even after hours of working at high load it remains at the lowest speed.

---

### Post by HugoSerrano on 2012-03-13
> **ashi009 said:**
> the problem is, even after hours of working at high load it remains at the lowest speed.

try:
echo performance > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
echo performance > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor
echo performance > /sys/devices/system/cpu/cpu2/cpufreq/scaling_governor
echo performance > /sys/devices/system/cpu/cpu3/cpufreq/scaling_governor
echo performance > /sys/devices/system/cpu/cpu4/cpufreq/scaling_governor                 
echo performance > /sys/devices/system/cpu/cpu5/cpufreq/scaling_governor
echo performance > /sys/devices/system/cpu/cpu6/cpufreq/scaling_governor
echo performance > /sys/devices/system/cpu/cpu7/cpufreq/scaling_governor

and re-check

---

### Post by Doug S on 2012-03-13
I would be interested to know the results of the HugoSerrno suggestion above.
I would also suggest that you monitor core temperatures, see matt_symes post [here]("http://ubuntuforums.org/showpost.php?p=11760086&postcount=2") for how to install the lm-sensors stuff.
 
I also have an 11.10 server test machine with 8 cpus and I also have a case where, under 93% load on two CPUs they appear to need some other stimulous (such as some cron job or some other temp task) to throttle up to full speed. In my case the worst delay I have seen has been 7 minutes before throttle up. I have not been able to figure out why, other than it is definately a function of idle frequencies (perhaps as eluded to by ssam above). I have never seen any delay under load conditions you described.

---

### Post by ashi009 on 2012-03-13
> **Doug S said:**
> I would be interested to know the results of the HugoSerrno suggestion above.
I would also suggest that you monitor core temperatures, see matt_symes post [here]("http://ubuntuforums.org/showpost.php?p=11760086&postcount=2") for how to install the lm-sensors stuff.
 
I also have an 11.10 server test machine with 8 cpus and I also have a case where, under 93% load on two CPUs they appear to need some other stimulous (such as some cron job or some other temp task) to throttle up to full speed. In my case the worst delay I have seen has been 7 minutes before throttle up. I have not been able to figure out why, other than it is definately a function of idle frequencies (perhaps as eluded to by ssam above). I have never seen any delay under load conditions you described.

$ sensors
i5k_amb-isa-0000
Adapter: ISA adapter
Ch. 0 DIMM 0:  +45.5Â°C  (low  = +127.5Â°C, high = +127.5Â°C)
Ch. 0 DIMM 1:  +39.5Â°C  (low  = +127.5Â°C, high = +127.5Â°C)
Ch. 1 DIMM 0:  +45.0Â°C  (low  = +127.5Â°C, high = +127.5Â°C)
Ch. 1 DIMM 1:  +41.0Â°C  (low  = +127.5Â°C, high = +127.5Â°C)

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +38.0Â°C  (high = +84.0Â°C, crit = +100.0Â°C)
Core 1:       +37.0Â°C  (high = +84.0Â°C, crit = +100.0Â°C)
Core 2:       +34.0Â°C  (high = +84.0Â°C, crit = +100.0Â°C)
Core 3:       +34.0Â°C  (high = +84.0Â°C, crit = +100.0Â°C)

coretemp-isa-0001
Adapter: ISA adapter
Core 0:       +34.0Â°C  (high = +84.0Â°C, crit = +100.0Â°C)
Core 1:       +33.0Â°C  (high = +84.0Â°C, crit = +100.0Â°C)
Core 2:       +33.0Â°C  (high = +84.0Â°C, crit = +100.0Â°C)
Core 3:       +35.0Â°C  (high = +84.0Â°C, crit = +100.0Â°C)

$ grep MHz /proc/cpuinfo
cpu MHz         : 1998.000
cpu MHz         : 1998.000
cpu MHz         : 1998.000
cpu MHz         : 1998.000
cpu MHz         : 1998.000
cpu MHz         : 1998.000
cpu MHz         : 1998.000
cpu MHz         : 1998.000

some readings I have before changing the governor.

and now:

$ grep MHz /proc/cpuinfo
cpu MHz         : 2664.000
cpu MHz         : 2664.000
cpu MHz         : 2664.000
cpu MHz         : 2664.000
cpu MHz         : 2664.000
cpu MHz         : 2664.000
cpu MHz         : 2664.000
cpu MHz         : 2664.000

and the performance improvement was significant.

thank you guys so much!

---

### Post by Doug S on 2012-03-16
I finally got around to reading the link given by ssam, so I inderstand why my CPUs were not ramping up with 93% load. I had not realized the up_threshold for ondemand mode was so high at 95%.
 
However, it makes no sense to me why ahsi009's CPUs were not ramping up, under such load average conidtions or with the infinite loop example. Yes, perhaps the ondemand stuff gets confused by short spikes of processing, but under such conditions I think the reported load averages would be 0.0. (since [there is a kernel bug and they are broken under such conditions]("http://ubuntuforums.org/showthread.php?t=1909253")). Anyway, this was/is interesting.
 
Edit: adding an example:```
doug@s15:~/sguide-1204/test-pdf-gen-on-1204$ grep MHz /proc/cpuinfo
cpu MHz         : 3401.000
cpu MHz         : 3401.000
cpu MHz         : 3100.000
cpu MHz         : 2800.000
cpu MHz         : 3401.000
cpu MHz         : 3401.000
cpu MHz         : 3401.000
cpu MHz         : 3401.000
doug@s15:~/sguide-1204/test-pdf-gen-on-1204$ cat /proc/loadavg
[COLOR=red]0.00 0.01 0.05 12/188 23703[/COLOR]

``` You can see 12 processes running, and the actual load average is about 6.6 but is reported as 0.0 (this has been running for about 40 minutes).

---

### Post by warburp on 2012-09-10
hey i have the same problem here and im trying to fix it using the

echo performance > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

commands as shown earlier but even when i run them as sudo it tells me my permission is denied

---

### Post by Doug S on 2012-09-10
If the file exists, i.e. if your system has the cpu throtteling stuff then:
Put the desired stuff into a script and run the script under "sudo".
Example:```
doug@s15:~/temp$ cat set_cpu_powersave
#! /bin/bash
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
cat /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor
cat /sys/devices/system/cpu/cpu2/cpufreq/scaling_governor
cat /sys/devices/system/cpu/cpu3/cpufreq/scaling_governor
cat /sys/devices/system/cpu/cpu4/cpufreq/scaling_governor
cat /sys/devices/system/cpu/cpu5/cpufreq/scaling_governor
cat /sys/devices/system/cpu/cpu6/cpufreq/scaling_governor
cat /sys/devices/system/cpu/cpu7/cpufreq/scaling_governor
echo "powersave" > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
echo "powersave" > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor
echo "powersave" > /sys/devices/system/cpu/cpu2/cpufreq/scaling_governor
echo "powersave" > /sys/devices/system/cpu/cpu3/cpufreq/scaling_governor
echo "powersave" > /sys/devices/system/cpu/cpu4/cpufreq/scaling_governor
echo "powersave" > /sys/devices/system/cpu/cpu5/cpufreq/scaling_governor
echo "powersave" > /sys/devices/system/cpu/cpu6/cpufreq/scaling_governor
echo "powersave" > /sys/devices/system/cpu/cpu7/cpufreq/scaling_governor
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
cat /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor
cat /sys/devices/system/cpu/cpu2/cpufreq/scaling_governor
cat /sys/devices/system/cpu/cpu3/cpufreq/scaling_governor
cat /sys/devices/system/cpu/cpu4/cpufreq/scaling_governor
cat /sys/devices/system/cpu/cpu5/cpufreq/scaling_governor
cat /sys/devices/system/cpu/cpu6/cpufreq/scaling_governor
cat /sys/devices/system/cpu/cpu7/cpufreq/scaling_governor

```Example to inquire as to state:```
doug@s15:~/temp$ cat set_cpu_inquire
#! /bin/bash
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
cat /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor
cat /sys/devices/system/cpu/cpu2/cpufreq/scaling_governor
cat /sys/devices/system/cpu/cpu3/cpufreq/scaling_governor
cat /sys/devices/system/cpu/cpu4/cpufreq/scaling_governor
cat /sys/devices/system/cpu/cpu5/cpufreq/scaling_governor
cat /sys/devices/system/cpu/cpu6/cpufreq/scaling_governor
cat /sys/devices/system/cpu/cpu7/cpufreq/scaling_governor
grep MHz /proc/cpuinfo

```

---

