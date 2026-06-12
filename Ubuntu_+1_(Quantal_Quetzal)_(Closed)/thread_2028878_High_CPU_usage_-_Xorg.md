---
title: "High CPU usage - Xorg"
date: 2012-07-19
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by QIII on 2012-07-19
Anyone else seeing this?
Check out PID 1317 -- 22.2% of one CPU core.   The other 5 cores are 1 - 3%.

```
xxxxxxxx@Ubuntu-Quantal:~$ top

top - 22:16:53 up 21 min,  2 users,  load average: 0.54, 0.47, 0.30
Tasks: 192 total,   1 running, 191 sleeping,   0 stopped,   0 zombie
%Cpu(s):  2.4 us,  3.6 sy,  0.0 ni, 93.1 id,  0.0 wa,  0.0 hi,  0.9 si,  0.0 st
KiB Mem:  16433724 total,  1249580 used, 15184144 free,    62952 buffers
KiB Swap:        0 total,        0 used,        0 free,   433700 cached

  PID USER      PR  NI  VIRT  RES  SHR S  %CPU %MEM    TIME+  COMMAND           
[COLOR=Red] 1317 root      20   0  242m 100m 9.9m S  22.2  0.6   2:33.41 Xorg       [/COLOR]       
 2788 xxxxxxx   20   0  655m 8264 3868 S   5.3  0.1   0:19.52 conky             
 2248 xxxxxxx  20   0 1170m  84m  35m S   0.7  0.5   0:27.28 compiz            
 8759 xxxxxxx   20   0  516m  16m  11m S   0.7  0.1   0:01.12 gnome-terminal    
   14 root      20   0     0    0    0 S   0.3  0.0   0:00.44 ksoftirqd/2       
   18 root      20   0     0    0    0 S   0.3  0.0   0:00.33 ksoftirqd/3       
 2329 xxxxxxx   20   0  421m 4888 3336 S   0.3  0.0   0:00.46 hud-service       
 2623 root      20   0     0    0    0 S   0.3  0.0   0:00.50 kworker/0:1       
 4224 root      20   0     0    0    0 S   0.3  0.0   0:00.18 kworker/2:0       
    1 root      20   0 24452 2372 1272 S   0.0  0.0   0:00.57 init              
    2 root      20   0     0    0    0 S   0.0  0.0   0:00.00 kthreadd          
    3 root      20   0     0    0    0 S   0.0  0.0   0:00.60 ksoftirqd/0       
    6 root      rt   0     0    0    0 S   0.0  0.0   0:00.00 migration/0       
    7 root      rt   0     0    0    0 S   0.0  0.0   0:00.00 watchdog/0        
    8 root      rt   0     0    0    0 S   0.0  0.0   0:00.00 migration/1       
   10 root      20   0     0    0    0 S   0.0  0.0   0:00.39 ksoftirqd/1       
   11 root      rt   0     0    0    0 S   0.0  0.0   0:00.00 watchdog/1        


```Here's what it looks like in Xubuntu

```
xxxxxxx@Xubuntu-Quantal:~$ top

top - 22:22:54 up 0 min,  1 user,  load average: 1.01, 0.29, 0.10
Tasks: 197 total,   1 running, 195 sleeping,   0 stopped,   1 zombie
%Cpu(s):  2.0 us,  1.8 sy,  0.3 ni, 76.0 id, 19.1 wa,  0.0 hi,  0.7 si,  0.0 st
KiB Mem:  16433724 total,   652216 used, 15781508 free,    26644 buffers
KiB Swap:        0 total,        0 used,        0 free,   197220 cached

  PID USER      PR  NI  VIRT  RES  SHR S  %CPU %MEM    TIME+  COMMAND           
[COLOR=Red] 1387 root      20   0  194m  44m  11m S   6.5  0.3   0:01.84 Xorg  [/COLOR]            
    1 root      20   0 24432 2364 1272 S   0.0  0.0   0:00.55 init              
    2 root      20   0     0    0    0 S   0.0  0.0   0:00.00 kthreadd          
    3 root      20   0     0    0    0 S   0.0  0.0   0:00.02 ksoftirqd/0       
    4 root      20   0     0    0    0 S   0.0  0.0   0:00.00 kworker/0:0       
    5 root      20   0     0    0    0 S   0.0  0.0   0:00.17 kworker/u:0       
    6 root      rt   0     0    0    0 S   0.0  0.0   0:00.00 migration/0       
    7 root      rt   0     0    0    0 S   0.0  0.0   0:00.00 watchdog/0        
    8 root      rt   0     0    0    0 S   0.0  0.0   0:00.00 migration/1       
    9 root      20   0     0    0    0 S   0.0  0.0   0:00.00 kworker/1:0       
   10 root      20   0     0    0    0 S   0.0  0.0   0:00.01 ksoftirqd/1       
   11 root      rt   0     0    0    0 S   0.0  0.0   0:00.00 watchdog/1        
   12 root      rt   0     0    0    0 S   0.0  0.0   0:00.00 migration/2       
   13 root      20   0     0    0    0 S   0.0  0.0   0:00.00 kworker/2:0       
   14 root      20   0     0    0    0 S   0.0  0.0   0:00.01 ksoftirqd/2       
   15 root      rt   0     0    0    0 S   0.0  0.0   0:00.00 watchdog/2        
   16 root      rt   0     0    0    0 S   0.0  0.0   0:00.00 migration/3       

```
As a comparison for each, here is Precise Xubuntu (one difference here is the use of the proprietary ATI drver, not used in either of the above)

```
xxxxxxx@ZACK:~$ top

top - 22:39:04 up 0 min,  0 users,  load average: 0.22, 0.07, 0.03
Tasks: 197 total,   1 running, 195 sleeping,   0 stopped,   1 zombie
Cpu(s):  0.7%us,  1.1%sy,  0.0%ni, 98.3%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:  16433880k total,   969640k used, 15464240k free,    76076k buffers
Swap: 16799740k total,        0k used, 16799740k free,   283352k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
[COLOR=Red] 1425 root      20   0  363m  72m  58m S    2  0.5   0:01.48 Xorg  [/COLOR]             
 2296 xxxxxxx  20   0  292m  33m  21m S    2  0.2   0:02.71 compiz             
 2354 xxxxxxx   20   0  645m 7768 4308 S    2  0.0   0:00.48 conky              
 3181 xxxxxxx   20   0 17432 1348  928 R    0  0.0   0:00.01 top                
    1 root      20   0 24440 2356 1268 S    0  0.0   0:00.97 init               
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      20   0     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0        
    4 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/0:0        
    5 root      20   0     0    0    0 S    0  0.0   0:00.16 kworker/u:0        
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0        
    7 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    8 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1        
    9 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/1:0        
   10 root      20   0     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1        
   11 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/0:1        
   12 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1         
   13 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/2        

```

---

### Post by ventrical on 2012-07-19
Not here on my dual core.

Are you running Kubuntu??

---

### Post by QIII on 2012-07-19
No.  The first is Unity, the second Xubuntu.

The last is my current Precise Xubuntu.  All are on the same machine.

---

### Post by ventrical on 2012-07-19
I can confirm that after a time of idle that xorg cpu usage will increase. Also , when using compiz cube rotate(zoom) option it will increase to 22.x to 44.x of cpu usage when I hold the mouse scroll button in and then release it.

---

### Post by QIII on 2012-07-19
Anything in Launchpad?  Hadn't considered uptime.

I'm on my cell right now so a bit hard to do much reporting.

---

### Post by effenberg0x0 on 2012-07-19
On the Phenom 2 X6 (6 cores) I see some weirdness like one core trying to take the world when the CPU is in "On Demand" mode. When I manually set the governor to "Performance", there's a tiny load for all processes as expected and everything is also more equally distributed between cores. On Intel platform (i5) I don't see anything unusual. Maybe the way powernow-k8 handles it is not ideal or was changed recently?
```

[22:07:18] ahsl@AL-DESK01:[~]: dmesg | grep -i cpu
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] KERNEL supported cpus:
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] SMP: Allowing 8 CPUs, 2 hotplug CPUs
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88042fc00000 s83520 r8192 d22976 u262144
[    0.000000] pcpu-alloc: s83520 r8192 d22976 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.007015] Initializing cgroup subsys cpuacct
[    0.007055] CPU: Physical Processor ID: 0
[    0.007055] CPU: Processor Core ID: 0
[    0.007057] mce: CPU supports 6 MCE banks
[    0.157203] CPU0: AMD Phenom(tm) II X6 1100T Processor stepping 00
[    0.263136] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.276352] Switch to broadcast mode on CPU1
[    0.289391] Switch to broadcast mode on CPU2
[    0.302456] Switch to broadcast mode on CPU3
[    0.315556] Switch to broadcast mode on CPU4
[    0.328627] Brought up 6 CPUs
[    0.328640] Switch to broadcast mode on CPU5
[    0.335505] Switch to broadcast mode on CPU0
[    4.842085] cpuidle: using governor ladder
[    4.842086] cpuidle: using governor menu
[    4.849250] powernow-k8: Found 1 AMD Phenom(tm) II X6 1100T Processor (6 cpu cores) (version 2.20.00)
[    5.924294] microcode: CPU0: patch_level=0x010000bf
[    5.979826] microcode: CPU0: new patch_level=0x010000dc
[    5.979835] microcode: CPU1: patch_level=0x010000bf
[    5.984257] microcode: CPU1: new patch_level=0x010000dc
[    5.984266] microcode: CPU2: patch_level=0x010000bf
[    5.987550] microcode: CPU2: new patch_level=0x010000dc
[    5.987558] microcode: CPU3: patch_level=0x010000bf
[    5.989485] microcode: CPU3: new patch_level=0x010000dc
[    5.989491] microcode: CPU4: patch_level=0x010000bf
[    5.991567] microcode: CPU4: new patch_level=0x010000dc
[    5.991575] microcode: CPU5: patch_level=0x010000bf
[    5.993330] microcode: CPU5: new patch_level=0x010000dc

```
```

[22:12:04] ahsl@AL-DESK01:[~]: dmesg | grep -i power
[    0.000000] ACPI: SSDT 00000000cfe8f8f0 00E10 (v01 A M I  POWERNOW 00000001 AMD  00000001)
[    4.511680] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    4.511683] ACPI: Power Button [PWRB]
[    4.511722] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    4.511723] ACPI: Power Button [PWRF]
[    4.849250] powernow-k8: Found 1 AMD Phenom(tm) II X6 1100T Processor (6 cpu cores) (version 2.20.00)
[    4.849260] powernow-k8: Core Performance Boosting: on.
[    4.849286] powernow-k8:    0 : pstate 0 (3500 MHz)
[    4.849287] powernow-k8:    1 : pstate 1 (2500 MHz)
[    4.849288] powernow-k8:    2 : pstate 2 (1700 MHz)
[    4.849289] powernow-k8:    3 : pstate 3 (800 MHz)

```
Regards,
Effenberg

---

### Post by QIII on 2012-07-19
All three of those are on the same machine with an 1100T.  So something is clearly different between versions.  It's not hardware.

---

### Post by mc4man on 2012-07-19
Are you saying that xorg's cpu use never drops below 22% or is that just one point in time?
In a unity session the cpu use of xorg should fluctuate quite a bit from 0.0 if you're doing absolutely nothing to bursts up to 40 - 50% or more for many common actions.

Can't see that one could say there is any 'typical' xorg cpu at any 1 point, depends on many things.

Maybe you should log xorg over a period of typical use time & compare to a similar, typical unity session in 12.04.
 Don't see much purpose in comparing Xubuntu to Ubuntu/unity, it's a known fact that performance/efficiency  in unity/compiz needs add. work

If curious attached is a log here of xorg over a typical 15 min. period, (no vids), reports taken every 5 sec.'s so actual highs for shorter periods could be higher at certain times
(a report every sec could possibly show the wider fluctuations

---

### Post by QIII on 2012-07-20
What I am saying is that at idle, just top and conky running, my hands in my lap, xorg stays at roughly 22% and my conky draws a straight line without wavering.  My conky redraws every second.

Again, it does not do this in the other two boots.

---

### Post by mc4man on 2012-07-20
Well there are other conky users around here, maybe they can compare their xorg cpu usage in an ubuntu session to yours.
(though possibly this thread should have been - 
High Xorg CPU usage with conky running
or thereabouts

---

### Post by QIII on 2012-07-20
Actually, two of the three show conky values.  Looks like on the other top snapshot the conky value must have been pretty low at the instant I captured it.  So I can see what conky is doing.

I don't think this is conky at all, since that is a measured value in top.

This may be nothing more than an odd blip, an odd condition or I just need to do another daily.

I was really just asking if anyone has seen the same to decide if I was just seeing something anomalous.

(Sorry if that rambled and was incoherent.  Wife and I just got back from a stage musical, it's late and I'm tired!)

---

### Post by dino99 on 2012-07-20
> **QIII said:**
>  My conky redraws every second.



do you really needs it to redraw on each second, set it on 5 for testing. :P

---

### Post by QIII on 2012-07-20
I like the fine grain I get with one second intervals.  Call me obsessive.

The point is that conky is known and measured quantity in top.  It's what drew my attention in the first place - and why conky is valuable as a monitoring tool.

---

### Post by mc4man on 2012-07-20
Turn it off & see what the diff is. Anytime the screen changes xorg is used

---

### Post by QIII on 2012-07-20
Yes, I realize the xorg is used when the screen changes.

Yes, I realize that conky takes resources and, in necessitating a screen change, cause xorg activity.

But conky is running in all three cases.  It's common to all three cases.  It is a condition each of the three cases shares.

Top and htop cause screen changes, too.  Using it is common in all three cases.  It is a condition each of the three cases shares.

I have Ubuntu Precise running on a different machine, running an identical conky.  This condition does not present itself on that machine.  However, a comparison is probably not entirely valid because it is running on different hardware.  It is a Phenom II x4 BE.

(I hope you all realize I am not being contrary here.  Just a discussion.  Should I add a smiley because I sound grumpy?  :) )

This has sort of turned from my original purpose to see if this was something worth looking into because others saw it, or if it was just me.

---

### Post by ventrical on 2012-07-20
Thanks for sharing it because we can keep an eye on it now. In past testing there were a lot of bugs with Oneiric that were using a lot of CPU resource and heating up nVidia adapter cards.

You are doing a good work.

---

### Post by QIII on 2012-07-21
Just updated.

The issue has disappeared. 

I'm calling this one a transient oddity.

---

