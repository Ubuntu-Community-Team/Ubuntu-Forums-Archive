---
title: "VirtualBox | Installation of Mac OS X"
date: 2012-04-25
forum: Virtualisation
---

### Post by RowanEmslie on 2012-04-25
Hi all

I need to do some work with Indesign CS4. My office has given me their copy but it is a Mac licensed version. I heard that I can run this through OS X using Virutalbox. I followed a bunch of installation videos on Youtube etc and everything was fine except when I tried to start the program I got the following error:

[INDENT]VT-x/AMD-V hardware acceleration is not available on your system. Certain guest (e.g. OS/2 and QNX) require this feature and will fail to boot without it.[/INDENT]

This is obviously rather maddening. I ran cat: /proc/cpuinfo and got the following:

[INDENT]processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Pentium(R) Dual-Core CPU       T4200  @ 2.00GHz
stepping	: 10
cpu MHz		: 2000.000
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm xsave lahf_lm
bogomips	: 3990.33
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Pentium(R) Dual-Core CPU       T4200  @ 2.00GHz
stepping	: 10
cpu MHz		: 1200.000
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm xsave lahf_lm
bogomips	: 3989.96
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:
[/INDENT]

The Intel T4200 do appear to be incompatible with VT-x.

This is very frustrating.

Is there a) any way I could work around this issue on Virtualbox or b) any other way I can run a Mac licensed copy of Indesign on my computer?

My laptop is a Packard Bell ETNA-GL, if that helps.

---

### Post by haqking on 2012-04-25
Running Mac OSX on anything other than Mac hardware i believe violates its EULA.

Peace

---

### Post by SeijiSensei on 2012-04-25
Have your office lend you a Mac.

---

### Post by RowanEmslie on 2012-04-25
It seems as though there's no other work around. I guess that'll have to be the thing to do. Very irritating!

---

### Post by QIII on 2012-04-25
If your hardware does not support virtualization and installation of the OS is a violation of the EULA, there is little reason to let the frustration bother you.

Nothing to be done except, as suggested above, get a laptop from your employer if you are expected to perform work outside of the workplace.

---

### Post by RowanEmslie on 2012-04-25
We have one Mac machine (desktop) and it is used by our comms guy. Luckily, my gf has a macbook so I'll have to beg it off her for a day or two. The joys of consultancy contracts...

---

### Post by coffeecat on 2012-04-25
@RowanEmslie, running MacOS in a VM is a violation of the EULA and as such cannot be supported here. See the forum [Code of Conduct]("http://ubuntuforums.org/index.php?page=policy"). Therefore, I shall close this thread. But good luck with borrowing the Macbook.

Thread closed.

---

