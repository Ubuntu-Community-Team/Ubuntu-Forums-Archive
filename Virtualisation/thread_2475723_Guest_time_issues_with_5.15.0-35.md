---
title: "Guest time issues with 5.15.0-35 ?"
date: 2022-06-06
forum: Virtualisation
---

### Post by mdtancsa on 2022-06-06
I was doing some kernel updates this morning on a pair of AMD EPYC 7281 servers.  Both were running ubuntu 22 5.15.0-33.  When I migrated the VMs away from one and then back to the one I updated to 5.15.0-35, I noticed the time jumped in crazy ways on the VM.  The hypervisor's clock is correct.  But if I reboot a guest after setting the time, it seems to be OK on the 5.15.0-35 kernel. But if I do a cold start of the guest on the 5.15.0-35, it starts up about 2-20 min in the future.  
OS time of the host looks fine as the the BIOS clock
$ sudo hwclock
2022-06-06 15:18:20.202135+00:00
$ date
Mon Jun  6 15:18:22 UTC 2022
I noticed this both with Ubuntu 20.x guests and FreeBSD guests

---

### Post by #&amp;thj^% on 2022-06-06
I'm  seeing that here: With a VPN, different locale
Ubuntu KVM
```

sudo  hwclock --verbose
[sudo] password for me: 
hwclock from util-linux 2.37.2
System Time: 1654529849.681149
Trying to open: /dev/rtc0
Using the rtc interface to the clock.
Assuming hardware clock is kept in UTC time.
Waiting for clock tick...
...got clock tick
Time read from Hardware Clock: 2022/06/06 15:37:30
Hw clock time : 2022/06/06 15:37:30 = 1654529850 seconds since 1969
Time since last adjustment is 1654529850 seconds
Calculated Hardware Clock drift is 0.000000 seconds
2022-06-06 11:37:29.491736-04:00
```
Host Arch:
```
sudo  hwclock --verbose
[sudo] password for me: 
hwclock from util-linux 2.38
System Time: 1654529751.258294
Trying to open: /dev/rtc0
Using the rtc interface to the clock.
Last drift adjustment done at 1651595368 seconds after 1969
Last calibration done at 1651595368 seconds after 1969
Hardware clock is on UTC time
Assuming hardware clock is kept in UTC time.
Waiting for clock tick...
...got clock tick
Time read from Hardware Clock: 2022/06/06 15:35:51
Hw clock time : 2022/06/06 15:35:51 = 1654529751 seconds since 1969
Time since last adjustment is 2934383 seconds
Calculated Hardware Clock drift is 0.000000 seconds
2022-06-06 09:35:50.764942-06:00

```
```
 uname -r
5.17.0-1003-oem

```
If I set the Guest to the proper time Zone I get the correct results:
```
sudo  hwclock --verbose
hwclock from util-linux 2.37.2
System Time: 1654531807.966651
Trying to open: /dev/rtc0
Using the rtc interface to the clock.
Assuming hardware clock is kept in UTC time.
Waiting for clock tick...
...got clock tick
Time read from Hardware Clock: 2022/06/06 16:10:08
Hw clock time : 2022/06/06 16:10:08 = 1654531808 seconds since 1969
Time since last adjustment is 1654531808 seconds
Calculated Hardware Clock drift is 0.000000 seconds
2022-06-06 10:10:07.936529-06:00

```

---

### Post by mdtancsa on 2022-06-06
My KVM is/always was set to UTC, but the guests are not.  In the past (5.15.0-33), this hasnt been an issue, but seems to be an issue with 5.15.0-35 ? Also there seems to be significant / random drift for the time in the guest. One that I had booted up an hour ago all of a sudden thought it was tomorrow. Rebooting back to 5.15.0-33 restores functionality back to normal

Board is 
H11SSL-i with an 


```
processor       : 31
vendor_id       : AuthenticAMD
cpu family      : 23
model           : 1
model name      : AMD EPYC 7281 16-Core Processor
stepping        : 2
microcode       : 0x800126e
cpu MHz         : 1200.000
cache size      : 512 KB
physical id     : 0
siblings        : 32
core id         : 29
cpu cores       : 16
apicid          : 59
initial apicid  : 59
fpu             : yes
fpu_exception   : yes
cpuid level     : 13
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc rep_good nopl nonstop_tsc cpuid extd_apicid amd_dcm aperfmperf rapl pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 movbe popcnt aes xsave avx f16c rdrand lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw skinit wdt tce topoext perfctr_core perfctr_nb bpext perfctr_llc mwaitx cpb hw_pstate ssbd ibpb vmmcall fsgsbase bmi1 avx2 smep bmi2 rdseed adx smap clflushopt sha_ni xsaveopt xsavec xgetbv1 xsaves clzero irperf xsaveerptr arat npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold avic v_vmsave_vmload vgif overflow_recov succor smca
bugs            : sysret_ss_attrs null_seg spectre_v1 spectre_v2 spec_store_bypass
bogomips        : 4199.76
TLB size        : 2560 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 48 bits physical, 48 bits virtual
power management: ts ttp tm hwpstate cpb eff_freq_ro [13] [14]



```

---

