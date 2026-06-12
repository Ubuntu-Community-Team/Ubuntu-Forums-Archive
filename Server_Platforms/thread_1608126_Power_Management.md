---
title: "Power Management"
date: 2010-10-28
forum: Server Platforms
---

### Post by Vegan on 2010-10-28
I am using 10.10 and I see the console is now tuned off after a period of time, this is good.

I was wondering if the kernel supports the Intel Speed-Step technology that is used by processors the reduce power consumption when the load is low.

AMD has a similar approach called Cool & Quiet.

They work by reducing the multiplier to bring the CPU clock down. This reduces power consumption big time.

My goal is to keep the server operating costs as low as practical.

---

### Post by Vegan on 2010-10-28
Looking on Intel's site it mentioned that 2.6.9 and up support Speedstep so I guess its OK.

I also noted some programs around to fiddle with the power management.

All I want is the CPU to slow down when its not loaded and up when it is.

---

### Post by Vegan on 2010-11-03
```
sudo apt-get install cpufrequtils sysfsutils
```


Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  libcpufreq0 libsysfs2
The following NEW packages will be installed:
  cpufrequtils libcpufreq0 libsysfs2 sysfsutils
0 upgraded, 4 newly installed, 0 to remove and 1 not upgraded.
Need to get 88.3kB of archives.
After this operation, 586kB of additional disk space will be used.
Do you want to continue [Y/n]?
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe libcpufreq0 i386 007-1 [13.6kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe cpufrequtils i386 007-1 [38.3kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main libsysfs2 i386 2.1.0+repack-1 [23.4kB]
Get:4 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe sysfsutils i386 2.1.0+repack-1 [13.0kB]
Fetched 88.3kB in 1s (66.4kB/s)
Preconfiguring packages ...
Selecting previously deselected package libcpufreq0.
(Reading database ... 51926 files and directories currently installed.)
Unpacking libcpufreq0 (from .../libcpufreq0_007-1_i386.deb) ...
Selecting previously deselected package cpufrequtils.
Unpacking cpufrequtils (from .../cpufrequtils_007-1_i386.deb) ...
Selecting previously deselected package libsysfs2.
Unpacking libsysfs2 (from .../libsysfs2_2.1.0+repack-1_i386.deb) ...
Selecting previously deselected package sysfsutils.
Unpacking sysfsutils (from .../sysfsutils_2.1.0+repack-1_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up libcpufreq0 (007-1) ...
Setting up cpufrequtils (007-1) ...
 * Loading cpufreq kernel modules...                                     [fail]
 * CPUFreq Utilities: Setting ondemand CPUFreq governor...                       * disabled, governor not available...                                   [ OK ]
Setting up libsysfs2 (2.1.0+repack-1) ...
Setting up sysfsutils (2.1.0+repack-1) ...
 * Setting sysfs variables...                                            [ OK ]
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place



So what is the problem with cpufreq kernel module on my Celeron 335 failing for?



```
sudo modprobe p4_clockmod
```

was liked to brute force my CPU, but I am still having problems/

---

### Post by Vegan on 2010-11-03
I should mention my machine is hard set to performance which is the worst case for wasting power.

This is not acceptable behavior and I see this as a major defect that needs immediate attention.

---

### Post by Vegan on 2010-11-04
Nobody able to help?

---

### Post by arnavk007 on 2010-11-05
Vegan in most of your threads you post some problem and solve it yourself
how do u expect someone to help you
btw u are an MVP why do you use ubuntu

---

### Post by Vegan on 2010-11-08
Linux is found all over the place these days, so its important to maintain top skills.

---

### Post by yazdzik on 2010-11-13
Dear Friends,

Vegan's observations are similar to my own.  While running either 10.10 or the mint verions 9, or a fresh deb testing, the latest kernel does not appear to support ondemand for some reason.

On my everyday all purpose laptop, older dell latitude 930, nvs 140, 


 uname -a
Linux deblap1 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010 x86_64 GNU/Linux


the speedstep works if I start with no AC power, wait like an eagle, plug it in less than a second after the nvdia screen appears.

Speedstep works fine on batteries, and, if I leave the laptop on battery power and run a high consumer for a few minutes then plug in, on demand stays and works as expected.

From a laptop user's view, this is absurd.  Everything used to work until some kernel developer had his own ideas about thermal efficiency.  cpufreqd places the laptop in constant  performance mode, which runs too hot, powernowd does nothing.

We need a patched kernel over-riding the kernel developers idea, so that we get maximum performance when we need it, as many of us use desktop linux as everyday, meaning lots of multi media, OS.


modeset and niveau interfering with nvidia drivers, speedstep no longer working, in other words, devs deciding what is good for us based upon someone whose computer usage is different than the everyday user's usage or upon some political ideal is just plain irritating. 


So, whether running three year old racks or three year old lappes to help business or watch streaming telly, a desktop should do what the user wants, and the desktop distro should allow for this to happen, in spite of what kernel devs and other such elite sorts presume is better for the rest of us.

So, end of speech, observed behaviour:

1. on ac power, on demand no longer spools up cpu when needed "right now"
2. throttling, ironically, does not slow when temps rise, so half an hour compiling at max speed, pc shuts down, rather than throttling down earlier. 
3. programmes do, indeed, respond more crisply, with higher cpu usage
4. certain graphics intensive things, like .mov absolutely require max cpu, for whatever reason, and without the ability to up the speed "right now" are unviewable

There are a lot of older cpus out there, like
```

Arch: X86-64
  Vendor: "GenuineIntel"
  Model: 6.15.11 "Intel(R) Core(TM)2 Duo CPU     T7700  @ 2.40GHz"
  Features: fpu,vme,de,pse,tsc,msr,pae,mce,cx8,apic,sep,mtrr,pge,mca,cmov,pat,pse36,clflush,dts,acpi,mmx,fxsr,sse,sse2,ss,ht,tm,pbe,syscall,nx,lm,constant_tsc,arch_perfmon,pebs,bts,rep_good,aperfmperf,pni,dtes64,monitor,ds_cpl,vmx,est,tm2,ssse3,cx16,xtpr,pdcm,lahf_lm
  Clock: 2400 MHz
  BogoMips: 4786.65
  Cache: 4096 kb
  Units/Processor: 2
  Config Status: cfg=new, avail=yes, need=no, active=unknown

```

Making these things, and we are not talking six year old celerons here, after all, is not helpful.  Furthermore, it leads those of us less stellar in our abilities to wonder whether that new laptop with the latest cpu with variable speed will work with the coolest video card to give us the performance we shall need to future proof, not because the technology and programming are not there, but because we cannot access them. 

And, yes, I do have the latest nvidia driver working, but why should anyone have to deal with "modestep" or blacklisting more modules that I had in my first kernel just to get tux racer to work?

At some point, we need to rethink.

While I offer no solution, since rebooting a rack of servers on battery power (!) to jumpstart ondemand freq control is rather impractical, this only real value to this post is to note that the problem is very real, affects laptop users generally, and is something some kernel developer thought of as a feature not a a bug.  He was wrong.

Peace,
Martin

---

### Post by gdahlm on 2010-11-13
You may want to install powertop

sudo install powertop

then run it with

sudo powertop


10.10 works with speed step just fine, but you may have it disable in the bios or you may not have your host configured to use it.

I have Several servers running on 10.10 as KVM hosts, I have checked with three of them and they are all running speed step



     PowerTOP version 1.13      (C) 2007 Intel Corporation

Cn                Avg residency       P-states (frequencies)
C0 (cpu running)        ( 6.7%)       Turbo Mode     5.5%
polling           0.1ms ( 0.0%)         2.40 Ghz     0.3%
C1 mwait          0.2ms ( 7.8%)         2.13 Ghz     0.2%
C2 mwait          0.6ms (24.2%)         1.87 Ghz     0.3%
C3 mwait          4.0ms (61.3%)         1.60 Ghz    93.2%


As you can see this server is not only spending 93.2% of it's time at the lowest CPU level, it is also spending the majority of it's time in a C3 or C2 state.

If you are using it on a laptop right click on your top panel and select "Add to Panel"

from there you can add "CPU Frequency Scaling Monitor"

This applet will show you the current speed and let you set the speed step strategy.

Check in your BIOS settings, many servers come with speedstep/powernow/cool'n'quiet disabled.

Some laptops disable it if your are plugged into AC also.

---

### Post by Vegan on 2010-11-16
I already have installed PowerTop but it grumbles for a build option.

CONFIG_PM_ADVANCED_DEBUG

Then it can figure out power consumption of modules.

Powertop has been around for years, so what is the problem?

---

