---
title: "flag vmx is not present on /proc/cpuinfo but processor must support VT"
date: 2014-07-18
forum: Virtualisation
---

### Post by viktoriia_taraniuk on 2014-07-18
VT-d and VTx is enabled on BIOS but according to flags is not. Also before I use virtualization with vmware. I try to use XEN HVM now. According to my cpuinfo I can't because vmx flag is not preset. I'm not understand why. Thanks in advance for your answer 

```
cat /proc/cpuinfo

processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 58
model name	: Intel(R) Core(TM) i5-3470 CPU @ 3.20GHz
stepping	: 9
microcode	: 0x15
cpu MHz		: 3192.838
cache size	: 6144 KB
physical id	: 0
siblings	: 4
core id		: 0
cpu cores	: 4
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu de tsc msr pae mce cx8 apic mca cmov pat clflush acpi mmx fxsr sse sse2 ss ht nx constant_tsc nonstop_tsc pni pclmulqdq est ssse3 sse4_1 sse4_2 popcnt tsc_deadline_timer aes f16c rdrand hypervisor ida arat epb pln pts dtherm fsgsbase erms
bogomips	: 6385.67
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:


processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 58
model name	: Intel(R) Core(TM) i5-3470 CPU @ 3.20GHz
stepping	: 9
microcode	: 0x15
cpu MHz		: 3192.838
cache size	: 6144 KB
physical id	: 0
siblings	: 4
core id		: 1
cpu cores	: 4
apicid		: 2
initial apicid	: 2
fdiv_bug	: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu de tsc msr pae mce cx8 apic mca cmov pat clflush acpi mmx fxsr sse sse2 ss ht nx constant_tsc nonstop_tsc pni pclmulqdq est ssse3 sse4_1 sse4_2 popcnt tsc_deadline_timer aes f16c rdrand hypervisor ida arat epb pln pts dtherm fsgsbase erms
bogomips	: 6385.67
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:


processor	: 2
vendor_id	: GenuineIntel
cpu family	: 6
model		: 58
model name	: Intel(R) Core(TM) i5-3470 CPU @ 3.20GHz
stepping	: 9
microcode	: 0x15
cpu MHz		: 3192.838
cache size	: 6144 KB
physical id	: 0
siblings	: 4
core id		: 2
cpu cores	: 4
apicid		: 4
initial apicid	: 4
fdiv_bug	: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu de tsc msr pae mce cx8 apic mca cmov pat clflush acpi mmx fxsr sse sse2 ss ht nx constant_tsc nonstop_tsc pni pclmulqdq est ssse3 sse4_1 sse4_2 popcnt tsc_deadline_timer aes f16c rdrand hypervisor ida arat epb pln pts dtherm fsgsbase erms
bogomips	: 6385.67
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:


processor	: 3
vendor_id	: GenuineIntel
cpu family	: 6
model		: 58
model name	: Intel(R) Core(TM) i5-3470 CPU @ 3.20GHz
stepping	: 9
microcode	: 0x15
cpu MHz		: 3192.838
cache size	: 6144 KB
physical id	: 0
siblings	: 4
core id		: 3
cpu cores	: 4
apicid		: 6
initial apicid	: 6
fdiv_bug	: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu de tsc msr pae mce cx8 apic mca cmov pat clflush acpi mmx fxsr sse sse2 ss ht nx constant_tsc nonstop_tsc pni pclmulqdq est ssse3 sse4_1 sse4_2 popcnt tsc_deadline_timer aes f16c rdrand hypervisor ida arat epb pln pts dtherm fsgsbase erms
bogomips	: 6385.67
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:
```

---

### Post by TheFu on 2014-07-18
Check the setting in your BIOS. Not all vendors set that to enable VT-x or even have the setting control available in the BIOS, so it may not be possible.

In the future, if you ask vmware questions, please be certain to provide the exact product name - they make 6 (or more) virtualization products - any one of which could be asked in this forum. It saves confusion and you don't want us to guess.

---

### Post by viktoriia_taraniuk on 2014-07-21
Please see my BIOS settings
[ATTACH=CONFIG]254879[/ATTACH]
Thank you for fast response. Under vmware product meant ESXi5.5. It works on the same hardware

---

### Post by TheFu on 2014-07-21
Well, that looks good. The most common way to check for VT-x that I know is:
```
$ cat /proc/cpuinfo| egrep "vmx|svm"
```  Looking through all that output isn't exciting. If anything shows up with that command, it is good.

---

### Post by viktoriia_taraniuk on 2014-07-21
Nothing :(

celeno@celeno:~$ 
celeno@celeno:~$ 
celeno@celeno:~$ cat /proc/cpuinfo| egrep "vmx|svm"
celeno@celeno:~$ 
celeno@celeno:~$

celeno@celeno:~$ uname -a
Linux celeno 3.11.0-26-generic #45~precise1-Ubuntu SMP Tue Jul 15 04:04:35 UTC 2014 i686 i686 i386 GNU/Linux

celeno@celeno:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.4 LTS
Release:	12.04
Codename:	precise
celeno@celeno:~$

---

### Post by TheFu on 2014-07-21
Ouch!  [http://ark.intel.com/products/68316/Intel-Core-i5-3470-Processor-6M-Cache-up-to-3_60-GHz](http://ark.intel.com/products/68316/Intel-Core-i5-3470-Processor-6M-Cache-up-to-3_60-GHz) says that CPU definitely has the capabilities.
I'd check for new BIOS and firmware from the maker to see if this is considered a bug.
Also, I thought ESXi required vt-x to boot?  But I could be wrong.  Stopped using Xen a few years ago, using KVM happily now.

The only other idea I have, which isn't much of an idea, is to run **sudo kvm-ok** and see if it provides any clues.

---

### Post by viktoriia_taraniuk on 2014-07-21
Thanks!

---

### Post by viktoriia_taraniuk on 2014-07-21
One more question. If needed I could create new thread
I have task. 
1. 1 server with 8 OS on it. Each OS has own USB or USB controller. This USB will be tested for different tasks. USB wifi adapter, storage, driver for propiate equipment.

Please suggest hypervisor:
- KVM
- XEN over Centos
- Citrix Xen


EXSi was tested but I have perfomance issue with it. Two wifi adapters can't share one controller well from different OS. I could see huge interruption on network traffic. 
Also vmware esxi Passthough has defect. It was tested with small list of equipment and long list of equipment don't work via passthrough 

Please help me to choose my next step

Thanks a lot!

---

### Post by TheFu on 2014-07-22
I would never expect ESXi to be used for video passthru - mainly just disk controllers.
I would never expect anyone to use wifi with ESX/ESXi systems.  Sorta doesn't make sense to me.  People spending $8K on a license will probably want 10G+ networking - GigE wired at a minimum.

As to the other questions, I've already written my reasons for preferring KVM here a few times. Search these forums, if you care.

---

