---
title: "Kernel 5.17 RC (Release Candidate) series"
date: 2022-01-23
forum: Ubuntu Development Version
---

### Post by zika on 2022-01-23
[https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.17-rc1/](https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.17-rc1/)
Looking forward to try pstate ...

---

### Post by Doug S on 2022-01-23
The release candidate is out early this week. I see the Ubuntu PPA AMD64 version failed to compile, among other failures.

EDIT: My own compile, using the Ubuntu Kernel configuration file from kernel 5.16, worked fine:

```
doug@s19:~$ uname -a
Linux s19 5.17.0-rc1-stock #1001 SMP PREEMPT Sun Jan 23 10:22:26 PST 2022 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by xyz-t on 2022-02-24
Synaptic is a good place for removing Kernels, just search for the  package and/or leftover in residual config folder. The extraction of Debian packages come with  some hesitation in the terminal. The rest is OK.

---

### Post by xyz-t on 2022-02-26
There's a bug with the GUFW app. Import .profile works, but selecting our home blend profile takes long enough to close the app. After 15 minutes and a restart, only one fourth of the rules we're imported. Switching profile and status switch are also affected. This issue is not present in stock Kernel (5.13.0-30)..

```
Operating System: KDE neon 5.24
KDE Plasma Version: 5.24.2
KDE Frameworks Version: 5.91.0
Qt Version: 5.15.3
Kernel Version: 5.17.0-051700rc5-generic (64-bit)
Graphics Platform: Wayland or X11
```

---

### Post by cbotmk3 on 2022-03-08
Hi, why are there no lowlatency for builds after RC4?
Will there be any for the final build of 5.17?

---

### Post by Doug S on 2022-03-08
> **cbotmk3 said:**
> Hi, why are there no lowlatency for builds after [COLOR="#FF0000"]RC5[/COLOR]?
Will there be any for the final build of 5.17?Well, I guess the build broke, yet again. It breaks much much more often than it used to. Often the Kernel team doesn't even seem to notice, but you can search through the [IRC logs]("https://irclogs.ubuntu.com/2022/03/") to see if anyone inquired. For example [this day]("https://irclogs.ubuntu.com/2022/03/07/%23ubuntu-kernel.html") (I only know how to look day by day).

For my part of it, I didn't notice because I am still on kernel 5.17-rc3 (lowlatency) due to ongoing testing requiring no other changes than specific intel_pstate CPU frequency scaling driver test patches.

---

### Post by xyz-t on 2022-03-08
The GUFW bug is a Debian issue. It is present in Mint 20.3 (cinnamon 5.2.7), but not in Arch. I've seen that there no low latency packages.Hopefully, for those who use it,  it will be back next week. If there is no rc-8?

All good here with Ryzen 2nd gen..

---

### Post by IanW on 2022-03-15
Final release is delayed due to new Spectre attacks. There is an RC8 instead.

[https://www.phoronix.com/scan.php?page=news_item&px=Linux-5.17-rc8-Released](https://www.phoronix.com/scan.php?page=news_item&px=Linux-5.17-rc8-Released)

---

### Post by cbotmk3 on 2022-03-16
But again, no low-latency builds for rc8. IanW, do you know why or if the final build will get those again?

---

### Post by IanW on 2022-03-16
> **cbotmk3 said:**
> But again, no low-latency builds for rc8. IanW, do you know why or if the final build will get those again?

Sorry, no. I just read about what's already been done on Phoronix.

---

### Post by Claus7 on 2022-03-16
Hello,

> **zika said:**
> [https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.17-rc1/](https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.17-rc1/)
Looking forward to try pstate ...

does this mean [https://www.kernel.org/doc/html/v4.19/admin-guide/pm/intel_pstate.html](https://www.kernel.org/doc/html/v4.19/admin-guide/pm/intel_pstate.html) that:

1) all intel cpus will be affected ~ 10 years old having sandybridge+ technology?
2) that either performance or powersave option will be possible? 

As a result: this means that less power will be used according to operation required?

Regards!

---

### Post by Doug S on 2022-03-16
> **Claus7 said:**
> Hello,



does this mean [https://www.kernel.org/doc/html/v4.19/admin-guide/pm/intel_pstate.html](https://www.kernel.org/doc/html/v4.19/admin-guide/pm/intel_pstate.html) that:

1) all intel cpus will be affected ~ 10 years old having sandybridge+ technology?
2) that either performance or powersave option will be possible? 

As a result: this means that less power will be used according to operation required?

Regards!If you have an old intel sandybridge processor, you should have already been using the intel_pstate CPU frequency driver by default for years and years. I think [the new AMD pstate driver might have been included in 5.17]("https://www.phoronix.com/scan.php?page=news_item&px=AMD-P-State-Linux-5.17"). For intel (and I suppose AMD), the way to check is:

```
doug@s19:~$ [COLOR="#FF0000"]grep . /sys/devices/system/cpu/cpu*/cpufreq/scaling_driver[/COLOR]
/sys/devices/system/cpu/cpu0/cpufreq/scaling_driver:intel_cpufreq
/sys/devices/system/cpu/cpu10/cpufreq/scaling_driver:intel_cpufreq
/sys/devices/system/cpu/cpu11/cpufreq/scaling_driver:intel_cpufreq
/sys/devices/system/cpu/cpu1/cpufreq/scaling_driver:intel_cpufreq
/sys/devices/system/cpu/cpu2/cpufreq/scaling_driver:intel_cpufreq
/sys/devices/system/cpu/cpu3/cpufreq/scaling_driver:intel_cpufreq
/sys/devices/system/cpu/cpu4/cpufreq/scaling_driver:intel_cpufreq
/sys/devices/system/cpu/cpu5/cpufreq/scaling_driver:intel_cpufreq
/sys/devices/system/cpu/cpu6/cpufreq/scaling_driver:intel_cpufreq
/sys/devices/system/cpu/cpu7/cpufreq/scaling_driver:intel_cpufreq
/sys/devices/system/cpu/cpu8/cpufreq/scaling_driver:intel_cpufreq
/sys/devices/system/cpu/cpu9/cpufreq/scaling_driver:intel_cpufreq
```

Where I am using the intel_cpufreq CPU frequency scaling driver, which is just the intel_pstate driver in passive mode. The way to check which governor is being used:

```
doug@s19:~$ [COLOR="#FF0000"]grep . /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor[/COLOR]
/sys/devices/system/cpu/cpu0/cpufreq/scaling_governor:schedutil
/sys/devices/system/cpu/cpu10/cpufreq/scaling_governor:schedutil
/sys/devices/system/cpu/cpu11/cpufreq/scaling_governor:schedutil
/sys/devices/system/cpu/cpu1/cpufreq/scaling_governor:schedutil
/sys/devices/system/cpu/cpu2/cpufreq/scaling_governor:schedutil
/sys/devices/system/cpu/cpu3/cpufreq/scaling_governor:schedutil
/sys/devices/system/cpu/cpu4/cpufreq/scaling_governor:schedutil
/sys/devices/system/cpu/cpu5/cpufreq/scaling_governor:schedutil
/sys/devices/system/cpu/cpu6/cpufreq/scaling_governor:schedutil
/sys/devices/system/cpu/cpu7/cpufreq/scaling_governor:schedutil
/sys/devices/system/cpu/cpu8/cpufreq/scaling_governor:schedutil
/sys/devices/system/cpu/cpu9/cpufreq/scaling_governor:schedutil
```

Just for completeness, I'll change to active mode, A.K.A. the intel_pstate driver.

```
doug@s19:~$ [COLOR="#FF0000"]echo active | sudo tee /sys/devices/system/cpu/intel_pstate/status[/COLOR]
active
doug@s19:~$ [COLOR="#FF0000"]grep . /sys/devices/system/cpu/cpu*/cpufreq/scaling_driver[/COLOR]
/sys/devices/system/cpu/cpu0/cpufreq/scaling_driver:intel_pstate
/sys/devices/system/cpu/cpu10/cpufreq/scaling_driver:intel_pstate
/sys/devices/system/cpu/cpu11/cpufreq/scaling_driver:intel_pstate
/sys/devices/system/cpu/cpu1/cpufreq/scaling_driver:intel_pstate
/sys/devices/system/cpu/cpu2/cpufreq/scaling_driver:intel_pstate
/sys/devices/system/cpu/cpu3/cpufreq/scaling_driver:intel_pstate
/sys/devices/system/cpu/cpu4/cpufreq/scaling_driver:intel_pstate
/sys/devices/system/cpu/cpu5/cpufreq/scaling_driver:intel_pstate
/sys/devices/system/cpu/cpu6/cpufreq/scaling_driver:intel_pstate
/sys/devices/system/cpu/cpu7/cpufreq/scaling_driver:intel_pstate
/sys/devices/system/cpu/cpu8/cpufreq/scaling_driver:intel_pstate
/sys/devices/system/cpu/cpu9/cpufreq/scaling_driver:intel_pstate
doug@s19:~$ [COLOR="#FF0000"]grep . /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor[/COLOR]
/sys/devices/system/cpu/cpu0/cpufreq/scaling_governor:powersave
/sys/devices/system/cpu/cpu10/cpufreq/scaling_governor:powersave
/sys/devices/system/cpu/cpu11/cpufreq/scaling_governor:powersave
/sys/devices/system/cpu/cpu1/cpufreq/scaling_governor:powersave
/sys/devices/system/cpu/cpu2/cpufreq/scaling_governor:powersave
/sys/devices/system/cpu/cpu3/cpufreq/scaling_governor:powersave
/sys/devices/system/cpu/cpu4/cpufreq/scaling_governor:powersave
/sys/devices/system/cpu/cpu5/cpufreq/scaling_governor:powersave
/sys/devices/system/cpu/cpu6/cpufreq/scaling_governor:powersave
/sys/devices/system/cpu/cpu7/cpufreq/scaling_governor:powersave
/sys/devices/system/cpu/cpu8/cpufreq/scaling_governor:powersave
/sys/devices/system/cpu/cpu9/cpufreq/scaling_governor:powersave
```

---

### Post by Doug S on 2022-03-16
On the subject of no lowlatency kernel: I have been looking at the IRC logs and still no mention of it. I have not had time to actually go on IRC and ask, but someone should.

EDIT: Actually, I do not even have IRC setup on my current main computer.

---

### Post by Claus7 on 2022-03-16
Hello,

> **Doug S said:**
> If you have an old intel sandybridge processor, you should have already been using the intel_pstate CPU frequency driver by default for years and years. I think the new AMD pstate driver might have been included in 5.17, not sure. For intel, the way to check is:
...
Where I am using the intel_cpufreq CPU frequency scaling driver, which is just the intel_pstate driver in passive mode. The way to check which governor is being used:
...


Indeed, in both cases the situation is as you mention it. Didn't know that.

Now you mention:
> **Doug S said:**
> Just for completeness, I'll change to active mode, A.K.A. the intel_pstate driver.

What difference are you expecting to observe with that change? E.g. better performance? Lower power consumption?
By checking at this one:
[https://askubuntu.com/questions/1380386/permanently-setting-intel-pstate-driver-to-passive](https://askubuntu.com/questions/1380386/permanently-setting-intel-pstate-driver-to-passive)
it seems that even if not needed, all processors will start working, even if there is no actual need to do so.

Now with the way things are, if I submit for example a fortran or c++ code (no parallel compiling), it will take only one of my cpus/cores. With active enabled, will it be possible to use more than one, as a result to get the job done faster? Is this something that you expect to happen with that new configuration?

Regards!

---

### Post by Doug S on 2022-03-16
> **Claus7 said:**
> Now you mention:


What difference are you expecting to observe with that change? E.g. better performance? Lower power consumption?
By checking at this one:
[https://askubuntu.com/questions/1380386/permanently-setting-intel-pstate-driver-to-passive](https://askubuntu.com/questions/1380386/permanently-setting-intel-pstate-driver-to-passive)
it seems that even if not needed, all processors will start working, even if there is no actual need to do so.

Now with the way things are, if I submit for example a fortran or c++ code (no parallel compiling), it will take only one of my cpus/cores. With active enabled, will it be possible to use more than one, as a result to get the job done faster? Is this something that you expect to happen with that new configuration?

Regards!The intel_cpufreq (intel_pstate in passive mode) CPU frequency scaling driver merely provides all the governors and functionality of the acpi-cpufreq CPU frequency scaling driver, but with much more granularity on the requested CPU frequency. Performance and power consumption tradeoffs are much to big a topic for herein. In rough terms, intel_cpufreq/ondemand is equivalent to intel_pstate/powersave for performance/power tradeoffs. Upstream most efforts are going into the schedutil governor for quick response to step function type load changes.

None of this has anything to do with single threaded workflows. Your single threaded compiles will remain single threaded. You would have to rewrite your make file to utilize multiple CPUs, if it is even possible. For example, I compile the kernel using 13 threads (I have 12 CPUs), but it only works because of the make file (I think).

---

### Post by Claus7 on 2022-03-16
Hello,
> **Doug S said:**
> The intel_cpufreq (intel_pstate in passive mode) CPU frequency scaling driver merely provides all the governors and functionality of the acpi-cpufreq CPU frequency scaling driver, but with much more granularity on the requested CPU frequency. Performance and power consumption tradeoffs are much to big a topic for herein. In rough terms, intel_cpufreq/ondemand is equivalent to intel_pstate/powersave for performance/power tradeoffs. Upstream most efforts are going into the schedutil governor for quick response to step function type load changes.
So you control the frequency you will be getting depending on the load you provide.

> **Doug S said:**
> None of this has anything to do with single threaded workflows. Your single threaded compiles will remain single threaded. You would have to rewrite your make file to utilize multiple CPUs, if it is even possible. For example, I compile the kernel using 13 threads (I have 12 CPUs), but it only works because of the make file (I think).
Thank you, very clear.

Regards!

---

### Post by xyz-t on 2022-03-17
This app (cpupower-gui 1.0) sets the governer policy the way you want. It is also possible to increase the minimum frequency with a result of plus or minus 100. The screenshot is from Arch, but Debian has the same package. It is always set the way you see it.


 Hope this help,

---

### Post by Claus7 on 2022-03-17
Hello,

> **xyz-t said:**
> This app (cpupower-gui 1.0) **sets the governer policy the way you want**. It is also possible to increase the minimum frequency with a result of plus or minus 100. The screenshot is from Arch, but Debian has the same package. It is always set the way you see it.


 Hope this help,

yes it does. So, you are able to choose how your car will change gears, if I can use that parallelism. 

One aspect can be that of mobile devices, e.g. their performance and battery life. Checking also this one: [https://www.kernel.org/doc/html/v4.14/admin-guide/pm/cpufreq.html](https://www.kernel.org/doc/html/v4.14/admin-guide/pm/cpufreq.html) 
made things more clear.

Thank you for the input,
Regards!

---

### Post by xyz-t on 2022-03-19
```
upgraded spectre-meltdown-checker (0.44+15+ga485c78-1 -> 0.44+18+g16f2160-1)


``` With this package Alongside Kernel 5.15.29-1update (a few others), the machine did not restart. It was in a frozen state with 3 unknown flashing characters top left. It was back to normal after a cold shut down.


 Arch Stable Legacy Mode

 ```
# /usr/bin/spectre-meltdown-checker
Spectre and Meltdown mitigation detection tool v0.44+

 Checking for vulnerabilities on current system
Kernel is Linux 5.17-rc8 #1 SMP PREEMPT Mon Mar 14 09:21:06 UTC 2022 x86_64
CPU is AMD Ryzen 7 2700U with Radeon Vega Mobile Gfx

 Hardware check
* Hardware support (CPU microcode) for mitigation techniques
 * Indirect Branch Restricted Speculation (IBRS)
 * SPEC_CTRL MSR is available: NO 
 * CPU indicates IBRS capability: NO 
 * CPU indicates preferring IBRS always-on: NO 
 * CPU indicates preferring IBRS over retpoline: NO 
 * Indirect Branch Prediction Barrier (IBPB)
 * PRED_CMD MSR is available: YES 
 * CPU indicates IBPB capability: YES (IBPB_SUPPORT feature bit)
 * Single Thread Indirect Branch Predictors (STIBP)
 * SPEC_CTRL MSR is available: NO 
 * CPU indicates STIBP capability: NO 
 * CPU indicates preferring STIBP always-on: NO 
 * Speculative Store Bypass Disable (SSBD)
 * CPU indicates SSBD capability: YES (AMD non-architectural MSR)
 * L1 data cache invalidation
 * FLUSH_CMD MSR is available: NO 
 * CPU indicates L1D flush capability: NO 
 * CPU supports Transactional Synchronization Extensions (TSX): NO 
 * CPU supports Software Guard Extensions (SGX): NO 
 * CPU supports Special Register Buffer Data Sampling (SRBDS): NO 
 * CPU microcode is known to cause stability problems: NO (family 0x17 model 0x11 stepping 0x0 ucode 0x810100b cpuid 0x810f10)
 * CPU microcode is the latest known available version: NO (latest version is 0x8101016 dated 2019/04/30 according to builtin firmwares DB v220+i20220208)
* CPU vulnerability to the speculative execution attack variants
 * Affected by CVE-2017-5753 (Spectre Variant 1, bounds check bypass): YES 
 * Affected by CVE-2017-5715 (Spectre Variant 2, branch target injection): YES 
 * Affected by CVE-2017-5754 (Variant 3, Meltdown, rogue data cache load): NO 
 * Affected by CVE-2018-3640 (Variant 3a, rogue system register read): NO 
 * Affected by CVE-2018-3639 (Variant 4, speculative store bypass): YES 
 * Affected by CVE-2018-3615 (Foreshadow (SGX), L1 terminal fault): NO 
 * Affected by CVE-2018-3620 (Foreshadow-NG (OS), L1 terminal fault): NO 
 * Affected by CVE-2018-3646 (Foreshadow-NG (VMM), L1 terminal fault): NO 
 * Affected by CVE-2018-12126 (Fallout, microarchitectural store buffer data sampling (MSBDS)): NO 
 * Affected by CVE-2018-12130 (ZombieLoad, microarchitectural fill buffer data sampling (MFBDS)): NO 
 * Affected by CVE-2018-12127 (RIDL, microarchitectural load port data sampling (MLPDS)): NO 
 * Affected by CVE-2019-11091 (RIDL, microarchitectural data sampling uncacheable memory (MDSUM)): NO 
 * Affected by CVE-2019-11135 (ZombieLoad V2, TSX Asynchronous Abort (TAA)): NO 
 * Affected by CVE-2018-12207 (No eXcuses, iTLB Multihit, machine check exception on page size changes (MCEPSC)): NO 
 * Affected by CVE-2020-0543 (Special Register Buffer Data Sampling (SRBDS)): NO

 CVE-2017-5753 aka 'Spectre Variant 1, bounds check bypass'
* Mitigated according to the /sys interface: YES (Mitigation: usercopy/swapgs barriers and __user pointer sanitization)
* Kernel has array_index_mask_nospec: YES (1 occurrence(s) found of x86 64 bits array_index_mask_nospec())
* Kernel has the Red Hat/Ubuntu patch: NO 
* Kernel has mask_nospec64 (arm64): NO 
* Kernel has array_index_nospec (arm64): NO 
> STATUS: NOT VULNERABLE (Mitigation: usercopy/swapgs barriers and __user pointer sanitization)
 CVE-2017-5715 aka 'Spectre Variant 2, branch target injection'
* Mitigated according to the /sys interface: YES (Mitigation: Retpolines, IBPB: conditional, STIBP: disabled, RSB filling)
* Mitigation 1
 * Kernel is compiled with IBRS support: YES 
 * IBRS enabled and active: NO 
 * Kernel is compiled with IBPB support: YES 
 * IBPB enabled and active: YES 
* Mitigation 2
 * Kernel has branch predictor hardening (arm): NO 
 * Kernel compiled with retpoline option: YES 
 * Kernel compiled with a retpoline-aware compiler: YES (kernel reports full retpoline compilation)
> STATUS: NOT VULNERABLE (Full retpoline + IBPB are mitigating the vulnerability)

 CVE-2017-5754 aka 'Variant 3, Meltdown, rogue data cache load'
* Mitigated according to the /sys interface: YES (Not affected)
* Kernel supports Page Table Isolation (PTI): YES 
 * PTI enabled and active: NO 
 * Reduced performance impact of PTI: NO (PCID/INVPCID not supported, performance impact of PTI will be significant)
* Running as a Xen PV DomU: NO 
> STATUS: NOT VULNERABLE (your CPU vendor reported your CPU model as not vulnerable)
 CVE-2018-3640 aka 'Variant 3a, rogue system register read'
* CPU microcode mitigates the vulnerability: YES 
> STATUS: NOT VULNERABLE (your CPU vendor reported your CPU model as not vulnerable)
 CVE-2018-3639 aka 'Variant 4, speculative store bypass'
* Mitigated according to the /sys interface: YES (Mitigation: Speculative Store Bypass disabled via prctl)
* Kernel supports disabling speculative store bypass (SSB): YES (found in /proc/self/status)
* SSB mitigation is enabled and active: YES (per-thread through prctl)
* SSB mitigation currently active for selected processes: NO (no process found using SSB mitigation through prctl)
> STATUS: NOT VULNERABLE (Mitigation: Speculative Store Bypass disabled via prctl)
 CVE-2018-3615 aka 'Foreshadow (SGX), L1 terminal fault'
* CPU microcode mitigates the vulnerability: N/A 
> STATUS: NOT VULNERABLE (your CPU vendor reported your CPU model as not vulnerable)
 CVE-2018-3620 aka 'Foreshadow-NG (OS), L1 terminal fault'
* Mitigated according to the /sys interface: YES (Not affected)
* Kernel supports PTE inversion: YES (found in kernel image)
* PTE inversion enabled and active: NO 
> STATUS: NOT VULNERABLE (your CPU vendor reported your CPU model as not vulnerable)

 CVE-2018-3646 aka 'Foreshadow-NG (VMM), L1 terminal fault'
* Information from the /sys interface: Not affected
* This system is a host running a hypervisor: NO 
* Mitigation 1 (KVM)
 * EPT is disabled: N/A (the kvm_intel module is not loaded)
* Mitigation 2
 * L1D flush is supported by kernel: YES (found flush_l1d in kernel image)
 * L1D flush enabled: NO 
 * Hardware-backed L1D flush supported: NO (flush will be done in software, this is slower)
 * Hyper-Threading (SMT) is enabled: YES 
> STATUS: NOT VULNERABLE (your CPU vendor reported your CPU model as not vulnerable)

 CVE-2018-12126 aka 'Fallout, microarchitectural store buffer data sampling (MSBDS)'
* Mitigated according to the /sys interface: YES (Not affected)
* Kernel supports using MD_CLEAR mitigation: YES (found md_clear implementation evidence in kernel image)
* Kernel mitigation is enabled and active: NO 
* SMT is either mitigated or disabled: NO 
> STATUS: NOT VULNERABLE (your CPU vendor reported your CPU model as not vulnerable)

 CVE-2018-12130 aka 'ZombieLoad, microarchitectural fill buffer data sampling (MFBDS)'
* Mitigated according to the /sys interface: YES (Not affected)
* Kernel supports using MD_CLEAR mitigation: YES (found md_clear implementation evidence in kernel image)
* Kernel mitigation is enabled and active: NO 
* SMT is either mitigated or disabled: NO 
> STATUS: NOT VULNERABLE (your CPU vendor reported your CPU model as not vulnerable)
 CVE-2018-12127 aka 'RIDL, microarchitectural load port data sampling (MLPDS)'
* Mitigated according to the /sys interface: YES (Not affected)
* Kernel supports using MD_CLEAR mitigation: YES (found md_clear implementation evidence in kernel image)
* Kernel mitigation is enabled and active: NO 
* SMT is either mitigated or disabled: NO 
> STATUS: NOT VULNERABLE (your CPU vendor reported your CPU model as not vulnerable)

 CVE-2019-11091 aka 'RIDL, microarchitectural data sampling uncacheable memory (MDSUM)'
* Mitigated according to the /sys interface: YES (Not affected)
* Kernel supports using MD_CLEAR mitigation: YES (found md_clear implementation evidence in kernel image)
* Kernel mitigation is enabled and active: NO 
* SMT is either mitigated or disabled: NO 
> STATUS: NOT VULNERABLE (your CPU vendor reported your CPU model as not vulnerable)

 CVE-2019-11135 aka 'ZombieLoad V2, TSX Asynchronous Abort (TAA)'
* Mitigated according to the /sys interface: YES (Not affected)
* TAA mitigation is supported by kernel: YES (found tsx_async_abort in kernel image)
* TAA mitigation enabled and active: NO 
> STATUS: NOT VULNERABLE (your CPU vendor reported your CPU model as not vulnerable)
 CVE-2018-12207 aka 'No eXcuses, iTLB Multihit, machine check exception on page size changes (MCEPSC)'
* Mitigated according to the /sys interface: YES (Not affected)
* This system is a host running a hypervisor: NO 
* iTLB Multihit mitigation is supported by kernel: YES (found itlb_multihit in kernel image)
* iTLB Multihit mitigation enabled and active: NO 
> STATUS: NOT VULNERABLE (your CPU vendor reported your CPU model as not vulnerable)
 CVE-2020-0543 aka 'Special Register Buffer Data Sampling (SRBDS)'
* Mitigated according to the /sys interface: YES (Not affected)
* SRBDS mitigation control is supported by the kernel: YES (found SRBDS implementation evidence in kernel image. Your kernel is up to date for SRBDS mitigation)
* SRBDS mitigation control is enabled and active: NO 
> STATUS: NOT VULNERABLE (your CPU vendor reported your CPU model as not vulnerable)

 > SUMMARY: CVE-2017-5753:OK CVE-2017-5715:OK CVE-2017-5754:OK CVE-2018-3640:OK CVE-2018-3639:OK CVE-2018-3615:OK CVE-2018-3620:OK CVE-2018-3646:OK CVE-2018-12126:OK CVE-2018-12130:OK CVE-2018-12127:OK CVE-2019-11091:OK CVE-2019-11135:OK CVE-2018-12207:OK CVE-2020-0543:OK
 Need more detailed information about mitigation options? Use --explain
A false sense of security is worse than no security at all, see --disclaimer


```

---

### Post by zika on 2022-03-21
[https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.17/](https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.17/)

---

### Post by Doug S on 2022-03-21
Someone finally asked about the missing low latency kernels on [IRC]("https://irclogs.ubuntu.com/2022/03/20/%23ubuntu-kernel.html"), but they got an incorrect response. That is the place to ask.

O.K. I installed a IRC client on my computer and [asked about the low latency kernels]("https://irclogs.ubuntu.com/2022/03/21/%23ubuntu-kernel.html").

EDIT: [Day carry over.]("https://irclogs.ubuntu.com/2022/03/22/%23ubuntu-kernel.html")
EDIT: [interesting follow up]("https://irclogs.ubuntu.com/2022/03/28/%23ubuntu-kernel.html")

---

### Post by xyz-t on 2022-03-21
There was a second spectre-meldown-checker (0.44-30) and it restarted OK this time. 5.18 is in the oven and 6.0 is not far.

---

### Post by Doug S on 2022-03-22
It seems there will no longer be any low latency versions on the Ubuntu Mainline PPA. For years now, and given that idle CPUs sleep for great periods of times regardless of the tick rate, it has not made any sense to me that all distros don't just use 1000 Hz as the default. Anyway, moving forward, I'll just run this script on the generic kernel configuration:

```
doug@s19:~/kernel/linux$ [COLOR="#FF0000"]cat mod-config[/COLOR]
#! /bin/bash
#
# mod-config 2022.03.22 Smythies
#       The standard changes to the Ubuntu Mainline
#       kernel configuration have become numerous.
#       Automate.
#       The script is located in the base directory of
#       the mainline git clone.

scripts/config --disable DEBUG_INFO
scripts/config --disable SYSTEM_TRUSTED_KEYS
scripts/config --disable SYSTEM_REVOCATION_KEYS

# convert generic config to lowlatency

scripts/config --disable COMEDI_TESTS_EXAMPLE
scripts/config --disable COMEDI_TESTS_NI_ROUTES
scripts/config --set-val CONFIG_HZ 1000
scripts/config --enable HZ_1000
scripts/config --disable HZ_250

scripts/config --enable LATENCYTOP
scripts/config --enable PREEMPT
scripts/config --disable PREEMPT_VOLUNTARY
scripts/config --set-val TEST_DIV64 m
``` 

Other info:

```
doug@s19:~/kernel/linux$ [COLOR="#FF0000"]scripts/diffconfig .config-5.17.0-051700rc3-generic .config-5.17.0-051700rc3-lowlatency[/COLOR]
 COMEDI_TESTS_EXAMPLE m -> n
 COMEDI_TESTS_NI_ROUTES m -> n
 HZ 250 -> 1000
 HZ_1000 n -> y
 HZ_250 y -> n
 LATENCYTOP n -> y
 PREEMPT n -> y
 PREEMPT_VOLUNTARY y -> n
 TEST_DIV64 n -> m
```

And after script execution, and compile (which makes a few adjustments to the resulting .config file). Compare my saved low latency config to the new one:

```
doug@s19:~/kernel/linux$ [COLOR="#FF0000"]scripts/diffconfig .config-5.17-rc3 .config[/COLOR]
doug@s19:~/kernel/linux$
```

i.e no differences.

---

### Post by tuxinvader2 on 2022-04-01
Thanks for looking into the lowlatency issue @DougS.

I have incorporated your settings into my mainline builder container for focal.

The image can now build lowlatency kernel packages again: [https://github.com/TuxInvader/focal-mainline-builder/issues/16](https://github.com/TuxInvader/focal-mainline-builder/issues/16)

Cheers

---

### Post by wamatech on 2022-07-01
This week's early release of the release candidate. Among other errors, I can see that the AMD64 version of Ubuntu PPA failed to compile.
[[COLOR=#1155CC][FONT=Roboto]top mobile app development company in USA[/FONT][/COLOR]]("https://www.wamatechnology.com/top-mobile-app-development-company-in-usa/")

---

### Post by Doug S on 2022-07-01
> **wamatech said:**
> This week's early release of the release candidate. Among other errors, I can see that the AMD64 version of Ubuntu PPA failed to compile.Huh? We are on [the kernel 5.19 RC series]("https://ubuntuforums.org/showthread.php?t=2475710") now, and the weekly release candidate (normally Sunday) hasn't been released yet. Yes, the daily for July 1st failed to compile, but that has been an ongoing hit or miss issue.

EDIT: Please do not put in a link to your web site with your posts.

---

