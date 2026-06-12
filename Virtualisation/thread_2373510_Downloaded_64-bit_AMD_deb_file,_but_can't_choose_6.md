---
title: "Downloaded 64-bit AMD deb file, but can't choose 64-bit OS"
date: 2017-10-06
forum: Virtualisation
---

### Post by SciGuy1872 on 2017-10-06
I downloaded a 64-bit deb file to make sure I had the 64-bit version on this computer; I checked under Help in Virtualbox, but that window didn't report the architecture. Gdeb reported that the program was already installed. I ran commands to tell me if this particular AMD dual-core was Virtualization-capable; the output was to color "svm" if it was--I never received any output from the commands:
```

anthony@anthony-Aspire-X1200:~$ grep --color svm /proc/cpuinfo
anthony@anthony-Aspire-X1200:~$ egrep 'vmx|svm' /proc/cpuinfo
anthony@anthony-Aspire-X1200:~$ cat /proc/cpuinfo | grep "svm"



```

I read a post saying there were three things that needed to be met: 

>  
I figured out what the problem was. VT-x in Virtualbox requires 3 things to work. First, you need a processor that is VT-x capable (check, just got a brand new one). Second, you need an OS that is VT-x capable (Ubuntu - check). Next, your motherboard needs to be able to recognize VT-x. My MOBO wasn't able to recognize the VT-x part of the new processor, but was still able to use the processor. A BIOS update fixed everything.

I checked BIOS and virtualization is supported. I'm trying to run Mint 18.2 Cinammon in Vbox and I have 16.04 Mate. Why does the Virtualbox only show 32-bit Linux when trying to create an OS in Vbox, and how do I get the program to use both cores? I have 4GB of memory. I'm using Virtualbox Version 5.1.28.

---

### Post by RobGoss on 2017-10-07
Are you saying you have a 64-bit ISO but VM is only showing a 32-bit option?  if this is the case you will need to enable visualization within your BIOS, I had the same issue and this method worked for me. I hope I'm understanding you correctly, Please see this video it explains how to overcome this issue  [https://www.youtube.com/watch?v=ojkF4iYlYqc](https://www.youtube.com/watch?v=ojkF4iYlYqc)

---

### Post by deadflowr on 2017-10-07
Double check everything
what do
```
dpkg -l | grep virtualbox
uname -a
cat /proc/cpuinfo
``` 
show?
Please post back results.

---

### Post by SciGuy1872 on 2017-10-07
```
anthony@anthony-Aspire-X1200:~$ dpkg -l | grep virtualbox
ii  virtualbox-5.1                              5.1.28-117968~Ubuntu~xenial                  amd64        Oracle VM VirtualBox
```
```
anthony@anthony-Aspire-X1200:~$ uname -a
Linux anthony-Aspire-X1200 4.10.0-35-generic #39~16.04.1-Ubuntu SMP Wed Sep 13 09:02:42 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
```
```
anthony@anthony-Aspire-X1200:~$ cat /proc/cpuinfo
processor    : 0
vendor_id    : AuthenticAMD
cpu family    : 15
model        : 107
model name    : AMD Sempron(tm) Dual Core Processor 2300
stepping    : 2
cpu MHz        : 1000.000
cache size    : 256 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 2
apicid        : 0
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 1
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow rep_good nopl extd_apicid pni cx16 lahf_lm cmp_legacy extapic cr8_legacy 3dnowprefetch vmmcall
bugs        : fxsave_leak sysret_ss_attrs null_seg swapgs_fence amd_e400
bogomips    : 2000.08
TLB size    : 1024 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc 100mhzsteps


processor    : 1
vendor_id    : AuthenticAMD
cpu family    : 15
model        : 107
model name    : AMD Sempron(tm) Dual Core Processor 2300
stepping    : 2
cpu MHz        : 1000.000
cache size    : 256 KB
physical id    : 0
siblings    : 2
core id        : 1
cpu cores    : 2
apicid        : 1
initial apicid    : 1
fpu        : yes
fpu_exception    : yes
cpuid level    : 1
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow rep_good nopl extd_apicid pni cx16 lahf_lm cmp_legacy extapic cr8_legacy 3dnowprefetch vmmcall
bugs        : fxsave_leak sysret_ss_attrs null_seg swapgs_fence amd_e400
bogomips    : 2000.08
TLB size    : 1024 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc 100mhzsteps
```

Thanks for the help!

---

### Post by deadflowr on 2017-10-07
You don't seem to have svm enabled.
(Or I'm blind, it would listed in the flags section of the /proc/cpuinfo.)

Rest is fine.
(Proper OS proper virtualbox install...)

---

### Post by SciGuy1872 on 2017-10-07
[COLOR=#222222][FONT=Verdana]I double checked the BIOS--Virtualization is enabled; I also went through all the options of BIOS and didn't see any category that said svm[/FONT][/COLOR].  [COLOR=#222222][FONT=Verdana]I watched the YouTube video, but there was no new information--I'm not aware of a Hyper-V setting in Ubuntu. The date of the BIOS creation is 10/29/08 and the version is R01-B0 (both zeroes)--I just went to Acer's website and I have the only BIOS version listed.

I tried a couple of days before to run the 32-bit file, but Mint said it was running in Software Rendering Mode and was super slow--can I fix this by allocating the full 128MB of the system? I figure I can't do that because some has to go to the host. If I can make the 32-bit behave properly, then that would be golden.[/FONT][/COLOR]

---

