---
title: "Problem installing latest version of Ardour (3.5.357)"
date: 2014-02-26
forum: Ubuntu Studio
---

### Post by catquarks on 2014-02-26
Hello,

I've been using Ubuntu Studio 13.10. I tried to install the latest version of Ardour, using their instructions ([http://ardour.org/first_time_linux.html](http://ardour.org/first_time_linux.html)), and got the following output:[INDENT]person@Surak:~/Downloads/Ardour_64bit-3.5.357-dbg$ sh ./install.sh

Welcome to the Ardour installer

Ardour will be installed for user person in /opt

[sudo] password for person: 
Wed Feb 26 20:36:44 GMT 2014
Architecture is x86
Checking for required disk space

!!! ERROR !!! Can't locate .size file for x86 bundle.
This package is broken or does not support x86.

Press ENTER to exit installer:

[/INDENT]


If applicable, here is my output for the following:[INDENT]person@Surak:~$ lshw -C CPU
WARNING: you should run this program as super-user.
  *-cpu                   
       product: Intel(R) Core(TM) i7-3770 CPU @ 3.40GHz
       vendor: Intel Corp.
       physical id: 1
       bus info: cpu@0
       version: 6.10.9
       serial: 0003-06A9-0000-0000-0000-0000
       size: 1600MHz
       capacity: 1600MHz
       width: 64 bits
       capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp x86-64 constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid fsgsbase smep erms cpufreq
       configuration: id=6
     *-logicalcpu:0
          description: Logical CPU
          physical id: 6.1
          width: 64 bits
          capabilities: logical
     *-logicalcpu:1
          description: Logical CPU
          physical id: 6.2
          width: 64 bits
          capabilities: logical
     *-logicalcpu:2
          description: Logical CPU
          physical id: 6.3
          width: 64 bits
          capabilities: logical
     *-logicalcpu:3
          description: Logical CPU
          physical id: 6.4
          width: 64 bits
          capabilities: logical
     *-logicalcpu:4
          description: Logical CPU
          physical id: 6.5
          width: 64 bits
          capabilities: logical
     *-logicalcpu:5
          description: Logical CPU
          physical id: 6.6
          width: 64 bits
          capabilities: logical
     *-logicalcpu:6
          description: Logical CPU
          physical id: 6.7
          width: 64 bits
          capabilities: logical
     *-logicalcpu:7
          description: Logical CPU
          physical id: 6.8
          width: 64 bits
          capabilities: logical
     *-logicalcpu:8
          description: Logical CPU
          physical id: 6.9
          width: 64 bits
          capabilities: logical
     *-logicalcpu:9
          description: Logical CPU
          physical id: 6.a
          width: 64 bits
          capabilities: logical
     *-logicalcpu:10
          description: Logical CPU
          physical id: 6.b
          width: 64 bits
          capabilities: logical
     *-logicalcpu:11
          description: Logical CPU
          physical id: 6.c
          width: 64 bits
          capabilities: logical
     *-logicalcpu:12
          description: Logical CPU
          physical id: 6.d
          width: 64 bits
          capabilities: logical
     *-logicalcpu:13
          description: Logical CPU
          physical id: 6.e
          width: 64 bits
          capabilities: logical
     *-logicalcpu:14
          description: Logical CPU
          physical id: 6.f
          width: 64 bits
          capabilities: logical
     *-logicalcpu:15
          description: Logical CPU
          physical id: 6.10
          width: 64 bits
          capabilities: logical
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
[/INDENT]

-and-[INDENT]person@Surak:~$ uname -a
Linux Surak 3.11.0-17-lowlatency #11-Ubuntu SMP PREEMPT Fri Feb 7 00:49:23 UTC 2014 i686 i686 i686 GNU/Linux
[/INDENT]


Help would be appreciated! I've been using Ardour with Ubuntu Studio to make music for a little over 3 years. It felt great to donate to them, but I'd love if this new version would install, too.

---

### Post by catquarks on 2014-02-26
Just a note: I know that this would be a typical problem if I were using a 32-bit system and simply needed to download that version -- but this is a 64-bit system! Yet it doesn't look like it's being recognized as such. So I think this issue may be indicative of a bigger problem. Please let me know what's going on... Thanks for reading.

---

### Post by jejeman on 2014-02-26
Well, actually you are running 32bit OS. So, that is why you got that error.
This is how output looks on 64bit OS:
```
$ uname -a
Linux HOST 3.2.0-59-lowlatency #61-Ubuntu SMP PREEMPT Tue Jan 28 09:16:18 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```Notice the difference
x86_64 = 64bit
i686 = 32bit

You do have 64bit capable hardware, but your OS is 32bit, and thats what counts.

---

### Post by catquarks on 2014-02-26
Aha! That's very weird, but hopefully easy to fix. Thanks for the response!

---

