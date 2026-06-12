---
title: "Ubuntu Server 12.04 High CPU Load"
date: 2012-09-26
forum: Server Platforms
---

### Post by zertux on 2012-09-26
[LEFT]Hello,

I have a Server (2x Hexa-Core Xeon E5649 2.53GHz w/HT with 32GB RAM and 20000 GB Bandwidth) running Ubuntu Server 12.04 LTS. The server runs LAMP and serves one website only, the estimated number of users is to be ~ 15,000 at the same time.

At the moment i have around 2000 users online each of them runs 50 MySQL queries (small values mostly select and insert) from the beginning until the end of the session. Server CPU Load is high at this number of connections while the RAM usage is almost 1GB out of 32GB its worth mentioning that the server was running very fast with no problems at all but am concerned about the load average. [http://s12.postimage.org/z7hi6mz3h/photo.png](http://s12.postimage.org/z7hi6mz3h/photo.png)

I have not changed any of the default configurations that comes with Ubuntu. Is this load normal for such powerful server ? is there any optimization i can make to Apache/MySQL to minimize the load ? What do you recommend ?[/LEFT]

---

### Post by Doug S on 2012-09-26
Hi and welcome to Ubuntu forums.
 
I can not answer your question about optimizations for minimizing load.
 
However, I will mention that the load average calculations do not know anything about cpu frequency scaling, and with that in mind load average can, perhaps, be misleading as to how busy the server is at 2,000 users verses trying to estimate how busy it will be with 15,000. The suggestion, just for estimating, is to force the CPU clock frequencies to maximum and then observe the load average numbers (after about 45 minutes, to allow for filter settling time on the 15 minute average). You would want to use "performance" mode, whereas if you haven't changed anything you should find that "ondemand" is the current setting. Note, you can do these changes on the fly. Example script (for setting powersave mode, and for an i7):```
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
```And an example script for inquiring about the srttings:```
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
doug@s15:~/temp$

```And an example of execution:```
doug@s15:~/temp$ sudo ./set_cpu_powersave
[sudo] password for doug:
ondemand
ondemand
ondemand
ondemand
ondemand
ondemand
ondemand
ondemand
powersave
powersave
powersave
powersave
powersave
powersave
powersave
powersave
doug@s15:~/temp$ sudo ./set_cpu_inquire
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
doug@s15:~/temp$

```Also please know that there were some issues with incorrect reported load averages. However issues with your particular use case were fixed just days prior to the 12.04 kernel freeze. Issues which I do not think apply to your use case were fixed with kernel 3.2.0-29.

---

### Post by SeijiSensei on 2012-09-26
I'd bet the MySQL settings are not optimal for an application of the scale zertux describes.  I'd look into performance tuning for MySQL.  This site looks like a good starting point: [http://www.mysqlperformanceblog.com/](http://www.mysqlperformanceblog.com/)

---

