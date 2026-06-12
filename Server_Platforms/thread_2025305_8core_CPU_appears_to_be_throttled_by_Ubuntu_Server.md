---
title: "8core CPU appears to be throttled by Ubuntu Server?"
date: 2012-07-14
forum: Server Platforms
---

### Post by jdmcmillian on 2012-07-14
Using an Ubuntu Server as a testbed and benchmark for a number crunching application, I wrote the application, but its only able to squeeze 65% out of an 8core CPU.   I should be getting much much more than this, so im thinking throttling is enabled someplace in the server or kernel.

How can I disable any throttling or test if throttling is enabled?  I really want at least 95% CPU usage.

I just realized, this is in the wrong group, how do I change it from lubuntu to all, or just ubuntu?

---

### Post by Doug S on 2012-07-14
Yes, the CPU's are throttled. And yes, depending on your application, there are conceiveable senarios where they might not throttle up.
 
To inquire as to current settings for clock throttling and current clock rates:```
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
```Example output:```
doug@s15:~/temp$ ./set_cpu_inquire
powersave
powersave
powersave
powersave
powersave
powersave
powersave
powersave
cpu MHz         : 1600.000
cpu MHz         : 1600.000
cpu MHz         : 1600.000
cpu MHz         : 1600.000
cpu MHz         : 1600.000
cpu MHz         : 1600.000
cpu MHz         : 1600.000
cpu MHz         : 1600.000

```(For some specific testing, I have my CPU's locked at the lowest clock rate).
To set the CPU to "on demand":```
doug@s15:~/temp$ cat set_cpu_ondemand
#! /bin/bash
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
cat /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor
cat /sys/devices/system/cpu/cpu2/cpufreq/scaling_governor
cat /sys/devices/system/cpu/cpu3/cpufreq/scaling_governor
cat /sys/devices/system/cpu/cpu4/cpufreq/scaling_governor
cat /sys/devices/system/cpu/cpu5/cpufreq/scaling_governor
cat /sys/devices/system/cpu/cpu6/cpufreq/scaling_governor
cat /sys/devices/system/cpu/cpu7/cpufreq/scaling_governor
echo "ondemand" > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
echo "ondemand" > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor
echo "ondemand" > /sys/devices/system/cpu/cpu2/cpufreq/scaling_governor
echo "ondemand" > /sys/devices/system/cpu/cpu3/cpufreq/scaling_governor
echo "ondemand" > /sys/devices/system/cpu/cpu4/cpufreq/scaling_governor
echo "ondemand" > /sys/devices/system/cpu/cpu5/cpufreq/scaling_governor
echo "ondemand" > /sys/devices/system/cpu/cpu6/cpufreq/scaling_governor
echo "ondemand" > /sys/devices/system/cpu/cpu7/cpufreq/scaling_governor
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
cat /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor
cat /sys/devices/system/cpu/cpu2/cpufreq/scaling_governor
cat /sys/devices/system/cpu/cpu3/cpufreq/scaling_governor
cat /sys/devices/system/cpu/cpu4/cpufreq/scaling_governor
cat /sys/devices/system/cpu/cpu5/cpufreq/scaling_governor
cat /sys/devices/system/cpu/cpu6/cpufreq/scaling_governor
cat /sys/devices/system/cpu/cpu7/cpufreq/scaling_governor
```Example execution:```
doug@s15:~/temp$ sudo "./set_cpu_ondemand"
powersave
powersave
powersave
powersave
powersave
powersave
powersave
powersave
ondemand
ondemand
ondemand
ondemand
ondemand
ondemand
ondemand
ondemand

```And now an inquire with the new settings and 6 processes running at 95% CPU usage per process:```
doug@s15:~/temp$ ./set_cpu_inquire
ondemand
ondemand
ondemand
ondemand
ondemand
ondemand
ondemand
ondemand
cpu MHz         : 3401.000
cpu MHz         : 1600.000
cpu MHz         : 3401.000
cpu MHz         : 3401.000
cpu MHz         : 3401.000
cpu MHz         : 3401.000
cpu MHz         : 1600.000
cpu MHz         : 3401.000
```In your case you might want to set your CPU's to "performance" to lock the clocks at maximum. Make sure your cooling is all is top working condition first.
 
References:
[http://www.mjmwired.net/kernel/Documentation/cpu-freq/governors.txt](http://www.mjmwired.net/kernel/Documentation/cpu-freq/governors.txt)

---

### Post by jdmcmillian on 2012-07-14
Thanks Doug S,

my directories end at cpuX...

here the contents.

```

administrator@testbed:~$ ls /sys/devices/system/cpu/cpu0/ -al
total 0
drwxr-xr-x  5 root root    0 Jul  5 19:55 .
drwxr-xr-x 12 root root    0 Jul  5 19:55 ..
drwxr-xr-x  6 root root    0 Jul  5 19:55 cache
drwxr-xr-x  5 root root    0 Jul 14 08:29 cpuidle
-r--------  1 root root 4096 Jul 14 08:29 crash_notes
lrwxrwxrwx  1 root root    0 Jul 14 08:29 node0 -> ../../node/node0
drwxr-xr-x  2 root root    0 Jul  5 19:55 topology

```

I should also state im using Ubuntu Server 12.04, 

Linux testbed 3.2.0-25-generic #40-Ubuntu SMP Wed May 23 20:30:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

what else should I do to figure this out?

JD

---

### Post by Doug S on 2012-07-15
If you do not have those directories, then I do not think that you have CPU throttling on your system and that you will find that your CPUs are at maximum clock rate. (At least that is what I recall from times when my system did not have those directories).
 
you should still be able to check CPU clock rate with:```
doug@s15:~/temp-3.5rc7/linux-3.5-rc7/kernel/sched$ grep MHz /proc/cpuinfo
cpu MHz         : 1600.000
cpu MHz         : 1600.000
cpu MHz         : 1600.000
cpu MHz         : 1600.000
cpu MHz         : 1600.000
cpu MHz         : 1600.000
cpu MHz         : 1600.000
cpu MHz         : 1600.000
```My s15 test computer is 12.04 server edition.

---

### Post by jdmcmillian on 2012-07-15
hey, thanks for the fast responses.

I was able to get it to max out running burnK7 in 8 different processes.  so since it work for burnK7, I must, though unwillingly, admit that my threading doesn't utilize the processors to their maximum efficiency, but now that I know where the issue is at, I know where to concentrate my attention.

Thanks again.

For anyone else, if you want to verify your own system, I used 'nmon' to monitor the CPUs, and burnK7, part of the cpuburn package. Then each in a different terminal, started up burnK7 until each CPU was maxed out.

---

