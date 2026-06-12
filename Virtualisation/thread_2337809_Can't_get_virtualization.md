---
title: "Can't get virtualization"
date: 2016-09-21
forum: Virtualisation
---

### Post by freeworld4 on 2016-09-21
My bios says I have virtualization enabled and all the virtual machine tools I have used thus far can't enable it. What should I do?

---

### Post by TheFu on 2016-09-22
$ egrep '(vmx|svm)' /proc/cpuinfo

Anything returned? If not, use containers. Those aren't dependent on AMD-V or VT-x support. 
Other alternative, get a new system with the support you want.  I've seen really cheap laptop BIOS not support virtualization even when the installed CPU does. Don't know why a vendor would do this, but they do.

 VT-d is a different question.

---

### Post by freeworld4 on 2016-09-23
Nothing is returned. What are containers?

---

### Post by TheFu on 2016-09-23
If that command doesn't return anything, then your CPU doesn't support VT-x or AMD-v ... that means you can only use a 32-bit hostOS with virtualbox to do virtualization AND that only 32-bit guestOSes are possible. [https://www.virtualbox.org/manual/ch10.html#hwvirt](https://www.virtualbox.org/manual/ch10.html#hwvirt) explains more.

Containers are a *completely different thing* that looks like virtualization, but it isn't. Use google to learn about "linux containers."  I use containers daily as a way to segment off 1 program from all the others in a way that they cannot do any harm to the main OS.  In large-scale deployments, containers are used to run 1 application/server and nothing else. It is not a desktop tool.  For example, running apache with a php web-app would be ideal for a container.  The back-end DB would run in another "container" ... .basically, 1 service/daemon for each container.  Best practices say that containers should be treated like zombies - if the container doesn't do what you want, shoot it in the head and build another that does.  Management of containers happens before you spin it up, during the build process. [https://linuxcontainers.org/](https://linuxcontainers.org/)

If you explain what your end goal is, perhaps we can suggest good alternatives?

---

### Post by 1clue on 2016-09-24
What do you get for uname -a?

If you're running a 32-bit operating system I'm not sure the vt-d or any other virtualization scheme will show up.

If your bios has support and it's turned on, then the only reason it wouldn't show up is lack of support in the kernel.

You should check:
[LIST=1]
[*]Your cpu specifically supports virtualization.
[*]Your motherboard supports virtualization. (evidently it does)
[*]Your bios has virtualization features that you want turned on.
[*]Your kernel supports virtualization.
[*]Your kernel is 64-bit.
[/LIST]

---

### Post by freeworld4 on 2016-10-24
How can I check that?

---

### Post by 1clue on 2016-10-24
First, type:```
uname -a
```
to get the Linux you're using. If it says something about x86_64 then you're running 64-bit Linux, which means you have a 64-bit processor.

For me I get:
```

% uname -a
Linux chronos 4.4.0-45-generic #66-Ubuntu SMP Wed Oct 19 14:12:37 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

```

on one box, and 

```

# uname -a
Linux spidermonkey 4.7.6-hardened-k1 #1 SMP Sun Oct 23 02:00:51 CDT 2016 x86_64 Intel(R) Atom(TM) CPU C2758 @ 2.40GHz GenuineIntel GNU/Linux

```

on another.

Second, find out what CPU you have:

```

% lscpu
Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                8
On-line CPU(s) list:   0-7
Thread(s) per core:    2
Core(s) per socket:    4
Socket(s):             1
NUMA node(s):          1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 26
Model name:            Intel(R) Core(TM) i7 CPU         920  @ 2.67GHz
Stepping:              5
CPU MHz:               2668.000
CPU max MHz:           2668.0000
CPU min MHz:           1600.0000
BogoMIPS:              5344.91
**Virtualization:        VT-x**
L1d cache:             32K
L1i cache:             32K
L2 cache:              256K
L3 cache:              8192K
NUMA node0 CPU(s):     0-7
Flags:                 fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm tpr_shadow vnmi flexpriority ept vpid dtherm ida

```

Finally, you need to look at what motherboard you use, to see if it supports virtualization and if it's turned on in the BIOS. Not really sure how you do that other than look inside, or if you bought the computer as a complete unit then look up the specs online.

---

