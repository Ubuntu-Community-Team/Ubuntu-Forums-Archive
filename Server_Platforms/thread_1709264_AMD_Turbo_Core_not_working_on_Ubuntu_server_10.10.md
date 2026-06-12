---
title: "AMD Turbo Core not working on Ubuntu server 10.10"
date: 2011-03-18
forum: Server Platforms
---

### Post by baosheng on 2011-03-18
I have installed Ubuntu server 10.10 on my new computer which uses AMD Phenom II X6 1090T. 

But I have noticed that my CPU cores were not able to run at 3.6GHz at any time, even when I only have one CPU-intensive computing job. They are either at 3.2 GHz or 800 MHz, like this

```
$ cat /proc/cpuinfo | grep -i "cpu Mhz"
cpu MHz		: 800.000
cpu MHz		: 3200.000
cpu MHz		: 3200.000
cpu MHz		: 800.000
cpu MHz		: 800.000
cpu MHz		: 800.000

```

My maximum CPU frequency seems to be locked at 3.2 Ghz:
```
$ dmesg | grep "pstate 0"
[    1.595918] powernow-k8:    0 : pstate 0 (3200 MHz)

```

I googled around and it seems that Linux 2.8.35 kernel have solved the problem. I just do not understand why it does not work on mine. 

```
$ uname -a
Linux hogwarts 2.6.35-22-server #35-Ubuntu SMP Sat Oct 16 22:02:33 UTC 2010 x86_64 GNU/Linux

```

Does anyone have any idea?

---

### Post by disabledaccount on 2011-03-18
First of all, You should check available FID table entries with command:
>dmesg | grep fid
or
> cat /var/log/kern.log | grep fid

cpuinfo shows current core clocks, not all available frequancies.
You have powerfull cpu - are You sure that the load was sufficient to trigger switching to max FID? Maybe You should try some cpu benchmarks or some game?

If FID table is correct, then next step is to check frequency scaling governor settings.

---

### Post by baosheng on 2011-03-18
i have tried both but none returned an FID table. I saw nothing. 

```
$ dmesg | grep fid
$ cat /var/log/kern.log | grep fid

```

Yes, my load was very high. I was running Python computation code that requires several hours to finish. That's why I want Turbo Core to work to speed up.

---

### Post by disabledaccount on 2011-03-19
And what results are returned with this:
>dmesg | grep powernow-k8

It should give at least one line telling that powernow-k8 have recognized your CPU.

You can also check this:
>cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies

---

### Post by baosheng on 2011-03-19
Here is what I got:

$ dmesg | grep powernow-k8
[    1.595883] powernow-k8: Found 1 AMD Phenom(tm) II X6 1090T Processor (6 cpu cores) (version 2.20.00)
[    1.595889] powernow-k8: Core Performance Boosting: on.
[    1.595918] powernow-k8:    0 : pstate 0 (3200 MHz)
[    1.595919] powernow-k8:    1 : pstate 1 (2400 MHz)
[    1.595920] powernow-k8:    2 : pstate 2 (1600 MHz)
[    1.595921] powernow-k8:    3 : pstate 3 (800 MHz)
$ cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
3200000 2400000 1600000 800000

---

### Post by disabledaccount on 2011-03-19
So it seems that Your CPU is not properly detected or rather not fully supported by this version of powernow-k8. You can wait for next version, but I suppose You will be more satisfied by using k10ctl - although it will need some work for seemless integration into your system
:)

---

### Post by baosheng on 2011-03-19
thanks. but according to what i found thru googling, linux kernel 2.6.35 should support Turbo Core feature without any problem. That's why i am wondering why Ubunt userver 10.10 using this kernel does not work properly on this.

---

### Post by disabledaccount on 2011-03-20
Yes, that's strange - it's possible that ubuntu kernel hasn't been patched against that problem. You can patch it Yourself, it's really small piece of code:
[http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commitdiff;h=b810e94c9d8e3fff6741b66cd5a6f099a7887871](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commitdiff;h=b810e94c9d8e3fff6741b66cd5a6f099a7887871)

You can also just disable CnQ - this is the simplest way, but will result in significantly higher power consumption in idle.

edit: it's also possible that You have some BIOS issue - is Your BIOS properly reporting CPU Frequency?

---

