---
title: "Ubuntu 16.04 - VirtualBox 5.0 - Host crashes"
date: 2018-01-14
forum: Virtualisation
---

### Post by sanosay on 2018-01-14
[COLOR=#111111][FONT=Ubuntu]Without performing any update, suddenly today when I tried to power on a VM in VirtualBox, the host machine (running Ubuntu 16.04) freezed.[/FONT][/COLOR]

[LIST]
[*][FONT=inherit]I tried couple of times and the problem keep repeating.[/FONT]
[*][FONT=inherit]I run memtest: all good[/FONT]
[*][FONT=inherit]Tried to create a new VM just in case: same issue.[/FONT]
[*]Downgraded the VirtualBox installation: didn't help at all.
[*]Disabled network, shared folders etc: Nothing.
[*]On the same PC I've got dual boot with Windows 10, tried there VirtualBox & VMWare -> no problem at all starting the machines. 
*(just to minimize the probability of HW issue)*
[/LIST]
[COLOR=#111111][FONT=Ubuntu]Any idea?[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]The only way to recover the host was to hard-reset.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]ps: The freeze happens as soon as I click the "Start" button.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Host details:[/FONT][/COLOR]

[LIST]
[*][FONT=inherit]VirtualBox: Version 5.0.40_Ubuntu[/FONT]
[*][FONT=inherit]Kernel: 4.13.0-26-generic[/FONT]
[*][FONT=inherit]Guest: irrelevant (windows 10, OpenSuse, CentOS)[/FONT]
[*][FONT=inherit]The log file of VirtualBox is empty.[/FONT]
[/LIST]

---

### Post by DuckHook on 2018-01-15
Welcome to the forums, sanosay.

Please see this thread: [https://ubuntuforums.org/showthread.php?t=2382314](https://ubuntuforums.org/showthread.php?t=2382314)

While it is impossible to say that your issue is the same one, it is worth a try.

Also, although you believe you have not updated, still, let's just check (and complete the picture at the same time). Please post back to this thread results of:```
uname -a
``````
lsb_release -a
``````
lscpu
``````
tail -n 50 /var/log/apt/history.log
```
Please post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

---

### Post by sanosay on 2018-01-15
Hello and thank you for the reply.
I did an update after trying couple of things before posting here.

```

uname -a:

Linux sanosay-pc 4.13.0-26-generic #29~16.04.2-Ubuntu SMP Tue Jan 9 22:00:44 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

```

```

lsb_release -a:

No LSB modules are available. Distributor ID: Ubuntu Description: Ubuntu 16.04.3 LTS Release: 16.04 Codename: xenial

```

```

lscpu:

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
Model:                 58
Model name:            Intel(R) Core(TM) i7-3770K CPU @ 3.50GHz
Stepping:              9
CPU MHz:               3503.442
CPU max MHz:           3900.0000
CPU min MHz:           1600.0000
BogoMIPS:              7006.88
Virtualization:        VT-x
L1d cache:             32K
L1i cache:             32K
L2 cache:              256K
L3 cache:              8192K
NUMA node0 CPU(s):     0-7
Flags:                 fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm cpuid_fault epb pti tpr_shadow vnmi flexpriority ept vpid fsgsbase smep erms xsaveopt dtherm ida arat pln pts

```

```

tail -n 50 /var/log/apt/history.log

End-Date: 2018-01-08  08:52:14


Start-Date: 2018-01-10  08:03:30
Commandline: /usr/bin/unattended-upgrade
Upgrade: libservlet3.1-java:amd64 (8.0.32-1ubuntu1.4, 8.0.32-1ubuntu1.5), poppler-utils:amd64 (0.41.0-0ubuntu1.5, 0.41.0-0ubuntu1.6), linux-libc-dev:amd64 (4.4.0-104.127, 4.4.0-108.131), libcuda1-384:amd64 (384.98-0ubuntu0~gpu16.04.1, 384.111-0ubuntu0.16.04.1), libpoppler-glib8:amd64 (0.41.0-0ubuntu1.5, 0.41.0-0ubuntu1.6), libpoppler58:amd64 (0.41.0-0ubuntu1.5, 0.41.0-0ubuntu1.6), nvidia-opencl-icd-384:amd64 (384.98-0ubuntu0~gpu16.04.1, 384.111-0ubuntu0.16.04.1), nvidia-375:amd64 (384.98-0ubuntu0~gpu16.04.1, 384.111-0ubuntu0.16.04.1), nvidia-384:amd64 (384.98-0ubuntu0~gpu16.04.1, 384.111-0ubuntu0.16.04.1)
End-Date: 2018-01-10  08:04:27


Start-Date: 2018-01-11  08:02:32
Commandline: /usr/bin/unattended-upgrade
Install: linux-image-4.13.0-26-generic:amd64 (4.13.0-26.29~16.04.2, automatic), linux-headers-4.13.0-26:amd64 (4.13.0-26.29~16.04.2, automatic), linux-image-extra-4.13.0-26-generic:amd64 (4.13.0-26.29~16.04.2, automatic), linux-headers-4.13.0-26-generic:amd64 (4.13.0-26.29~16.04.2, automatic)
Upgrade: linux-libc-dev:amd64 (4.4.0-108.131, 4.4.0-109.132), ruby2.3:amd64 (2.3.1-2~16.04.4, 2.3.1-2~16.04.5), linux-image-generic-hwe-16.04:amd64 (4.10.0.42.44, 4.13.0.26.46), linux-generic-hwe-16.04:amd64 (4.10.0.42.44, 4.13.0.26.46), ruby2.3-dev:amd64 (2.3.1-2~16.04.4, 2.3.1-2~16.04.5), libruby2.3:amd64 (2.3.1-2~16.04.4, 2.3.1-2~16.04.5), linux-headers-generic-hwe-16.04:amd64 (4.10.0.42.44, 4.13.0.26.46)
Error: Sub-process /usr/bin/dpkg returned an error code (2)
End-Date: 2018-01-11  08:02:32


Start-Date: 2018-01-12  08:03:49
Commandline: /usr/bin/unattended-upgrade
Install: linux-image-4.13.0-26-generic:amd64 (4.13.0-26.29~16.04.2, automatic), linux-headers-4.13.0-26:amd64 (4.13.0-26.29~16.04.2, automatic), linux-image-extra-4.13.0-26-generic:amd64 (4.13.0-26.29~16.04.2, automatic), linux-headers-4.13.0-26-generic:amd64 (4.13.0-26.29~16.04.2, automatic)
Upgrade: linux-libc-dev:amd64 (4.4.0-108.131, 4.4.0-109.132), ruby2.3:amd64 (2.3.1-2~16.04.4, 2.3.1-2~16.04.5), linux-image-generic-hwe-16.04:amd64 (4.10.0.42.44, 4.13.0.26.46), linux-generic-hwe-16.04:amd64 (4.10.0.42.44, 4.13.0.26.46), ruby2.3-dev:amd64 (2.3.1-2~16.04.4, 2.3.1-2~16.04.5), libruby2.3:amd64 (2.3.1-2~16.04.4, 2.3.1-2~16.04.5), libwebkit2gtk-4.0-37:amd64 (2.18.4-0ubuntu0.16.04.1, 2.18.5-0ubuntu0.16.04.1), gir1.2-webkit2-4.0:amd64 (2.18.4-0ubuntu0.16.04.1, 2.18.5-0ubuntu0.16.04.1), linux-headers-generic-hwe-16.04:amd64 (4.10.0.42.44, 4.13.0.26.46), libjavascriptcoregtk-4.0-18:amd64 (2.18.4-0ubuntu0.16.04.1, 2.18.5-0ubuntu0.16.04.1), libwebkit2gtk-4.0-37-gtk2:amd64 (2.18.4-0ubuntu0.16.04.1, 2.18.5-0ubuntu0.16.04.1), gir1.2-javascriptcoregtk-4.0:amd64 (2.18.4-0ubuntu0.16.04.1, 2.18.5-0ubuntu0.16.04.1)
End-Date: 2018-01-12  08:06:02


Start-Date: 2018-01-13  12:10:14
Commandline: /usr/bin/unattended-upgrade
Upgrade: intel-microcode:amd64 (3.20170707.1~ubuntu16.04.0, 3.20180108.0~ubuntu16.04.2), flashplugin-installer:amd64 (28.0.0.126ubuntu0.16.04.1, 28.0.0.137ubuntu0.16.04.1)
End-Date: 2018-01-13  12:10:46


Start-Date: 2018-01-13  12:10:52
Commandline: /usr/bin/unattended-upgrade
Remove: linux-image-4.10.0-40-generic:amd64 (4.10.0-40.44~16.04.1), libqt5x11extras5:amd64 (5.5.1-3build1), linux-image-extra-4.10.0-40-generic:amd64 (4.10.0-40.44~16.04.1), linux-headers-4.10.0-40:amd64 (4.10.0-40.44~16.04.1), linux-headers-4.10.0-40-generic:amd64 (4.10.0-40.44~16.04.1)
End-Date: 2018-01-13  12:11:16


Start-Date: 2018-01-14  16:04:59
Commandline: apt-get remove virtualbox virtualbox-5.1
Remove: virtualbox-ext-pack:amd64 (5.0.40-0ubuntu1.16.04.1), virtualbox:amd64 (5.0.40-dfsg-0ubuntu1.16.04.2), virtualbox-qt:amd64 (5.0.40-dfsg-0ubuntu1.16.04.2)
End-Date: 2018-01-14  16:05:04


Start-Date: 2018-01-14  16:06:45
Commandline: apt-get install virtualbox-5.2
Install: libsdl-ttf2.0-0:amd64 (2.0.11-3, automatic), virtualbox-5.2:amd64 (5.2.4-119785~Ubuntu~xenial)
End-Date: 2018-01-14  16:07:11


Start-Date: 2018-01-14  17:12:50
Commandline: apt-get upgrade
Requested-By: sanosay (1000)
Upgrade: suru-icon-theme:amd64 (14.04+16.04.20161024-0ubuntu1, 14.04+16.04.20171116-0ubuntu1), ubuntu-mobile-icons:amd64 (14.04+16.04.20161024-0ubuntu1, 14.04+16.04.20171116-0ubuntu1), light-themes:amd64 (14.04+16.04.20161024-0ubuntu1, 14.04+16.04.20171116-0ubuntu1), ubuntu-artwork:amd64 (1:14.04+16.04.20161024-0ubuntu1, 1:14.04+16.04.20171116-0ubuntu1), ubuntu-mono:amd64 (14.04+16.04.20161024-0ubuntu1, 14.04+16.04.20171116-0ubuntu1)
End-Date: 2018-01-14  17:12:52


Start-Date: 2018-01-15  08:17:31
Commandline: /usr/bin/unattended-upgrade
Remove: libsdl-ttf2.0-0:amd64 (2.0.11-3)
End-Date: 2018-01-15  08:17:32

```


Thank you

---

### Post by DuckHook on 2018-01-15
Try solution in thread I linked to.

I will shortly be signing off (bedtime in my time zone). You may not receive further responses from me for a few hours.

---

### Post by sanosay on 2018-01-15
Yeah, just installed the 5.2 version and all seems working alright.
Thank you very much.

---

### Post by DuckHook on 2018-01-15
You're welcome. Glad it worked out.

*Please mark thread **solved** using *Thread Tools* in the top toolbar for the benefit of others searching for solutions*.

---

