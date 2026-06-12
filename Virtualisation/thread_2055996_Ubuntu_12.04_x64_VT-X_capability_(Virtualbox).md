---
title: "Ubuntu 12.04 x64 VT-X capability (Virtualbox)"
date: 2012-09-10
forum: Virtualisation
---

### Post by justjustin on 2012-09-10
Hi, I am having trouble with Ubuntu 12.04 and Virtualbox - AMD VT-X support for 64bit guest OS in particular. I have existing VMs from a previous install and I cannot use them, I am also unable to create new x64 VMs. Virtualbox says:

> VT-x/AMD-V hardware acceleration has been enabled, but is not operational. Your 64-bit guest will fail to detect a 64-bit CPU and will not be able to boot.
Please ensure that you have enabled VT-x/AMD-V properly in the BIOS of your host computer.

I had 64bit guest support on 12.04 before, but since then I have reinstalled the system. I had been using 3.2.0-29-generic until yesterday. No hardware has been changed and no BIOS settings have been altered.

I first tried Virtualbox from repo and I am currently using Virtualbox 4.1.22 closed-source(extensions installed).

```
# uname -sri
Linux 3.2.0-30-generic x86_64
```

```
# cat /proc/cpuinfo | grep flags
flags		: fpu vme de pse tsc msr pae mce cx8 apic 
sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr 
sse sse2 ss ht tm pbe 
syscall nx [COLOR="Red"]lm[/COLOR] constant_tsc arch_perfmon pebs bts rep_good 
nopl aperfmperf pni dtes64 monitor ds_cpl [COLOR="Red"]vmx[/COLOR] est 
tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm tpr_shadow vnmi flexpriority
```

As far as I'm aware, "lm" and "vmx" flags are important here - they indicate that the Cpu is capable of virtualisation. They don't tell us, however, whether or not the capabilities are enabled, either in BIOS or by Linux Kernel.

```
# lshw -c cpu | grep capabilities
       capabilities: fpu fpu_exception wp vme de pse tsc 
msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush 
dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx [COLOR="Red"]x86-64[/COLOR] 
constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf 
pni dtes64 monitor ds_cpl [COLOR="Red"]vmx[/COLOR] est tm2 ssse3 cx16 xtpr pdcm 
lahf_lm dtherm tpr_shadow vnmi flexpriority cpufreq

```

Am I wrong in thinking that these are the cpu capabilities enabled and working on my linux system? vmx is present here, no lm.

> nx lm constant_tsc
nx x86-64 constant_tsc

```
# apt-get install msr-tools
# modprobe msr
# rdmsr 0x3A
```

If I understand this correctly, a return value of 3 or 5 here indicates that VT-X is enabled and working. My system returns 1.

Are there some packages or utilities I am missing which prevents this from working? I built the linux system myself from a mini.iso and everything else seems to be working fine.

Thanks for any help or advice in advance

ps, wasn't sure where to put this.

---

### Post by justjustin on 2012-09-14
This seems to have automagically started working, I have absolutely no idea how or why. I haven't changed any settings in either the Bios or VBox, the only thing that has changed on my system is a mysql update. 

I suppose it's possible that mysql was utilising VT-X until the update, but I really have no idea.

Should be marked as working, not really solved.

---

### Post by justjustin on 2012-09-18
This is not working again. I have no idea what is going on, can anyone give me any help here please?

Even if I could narrow it down to some other process or service using Vt-X this would be a start.

---

