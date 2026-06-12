---
title: "KVM &quot;enabling virtualization on CPU0 failed&quot;"
date: 2012-07-03
forum: Server Platforms
---

### Post by jasonin2d on 2012-07-03
Hi guys,

I have recently upgraded my home computer from an old Debian Lenny install to a new Ubuntu Server 12.04 install.  The box just serves as media storage, a few multimedia functions, and as a VM host.

However, I have a problem - since installing 12.04, I cannot get KVM to work properly.  This is strange, as it used to work perfectly on my Debian Leny install on the exact same hardware, and I've re-checked that hardware aceleration is enabled in the BIOS.

When starting a VM, I get the following message:

```
$ kvm -cdrom BT5R2-KDE-32.iso -m 256 -net nic -net user -vnc 127.0.0.1:2
failed to initialize KVM: Device or resource busy
Back to tcg accelerator.
```

And I them get the following line appear in the dmesg output:

```
kvm: enabling virtualization on CPU0 failed
```

I am fairly sure I have everything set up as I should.  My account is in the KVM group (but I get the same symptoms even running as root):

```
$ ls -l /dev/kvm
crw-rw---- 1 root kvm 10, 232 Jun 30 07:42 /dev/kvm
$ whoami
jason
$ grep kvm /etc/group
kvm:x:105:jason
$
```

The KVM kernel modules are loaded:

```
$ lsmod | grep kvm
kvm_amd                55848  0
kvm                   415459  1 kvm_amd
$
```

Please help me to fix this.  I'm guessing it's a bug, but I wanted to get advice here on the forums first to be sure.

Here is some background info on the host to hopefully help:

```
$ uname -a
Linux cube 3.2.0-23-generic #36-Ubuntu SMP Tue Apr 10 20:39:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
$ lscpu
Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                2
On-line CPU(s) list:   0,1
Thread(s) per core:    1
Core(s) per socket:    2
Socket(s):             1
NUMA node(s):          1
Vendor ID:             AuthenticAMD
CPU family:            16
Model:                 4
Stepping:              2
CPU MHz:               800.000
BogoMIPS:              4431.12
Virtualisation:        AMD-V
L1d cache:             64K
L1i cache:             64K
L2 cache:              512K
NUMA node0 CPU(s):     0,1
$ cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 16
model           : 4
model name      : AMD Athlon(tm) 5000 Dual-Core Processor
stepping        : 2
microcode       : 0x1000086
cpu MHz         : 800.000
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
apicid          : 0
initial apicid  : 0
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt npt lbrv svm_lock nrip_save
bogomips        : 4431.17
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

processor       : 1
vendor_id       : AuthenticAMD
cpu family      : 16
model           : 4
model name      : AMD Athlon(tm) 5000 Dual-Core Processor
stepping        : 2
microcode       : 0x1000086
cpu MHz         : 800.000
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
apicid          : 1
initial apicid  : 1
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt npt lbrv svm_lock nrip_save
bogomips        : 4431.12
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

$
```


Many thanks for the help!

---

### Post by jasonin2d on 2012-07-04
Morning.

So, does nobody have any ideas on this issue?

I think I'll have to file it as a bug if nobody has any ideas today...

Thanks again!

---

### Post by jasonin2d on 2012-07-05
For information of anyone else experiencing this problem:

Logged as [Bug ID 1021271]("https://bugs.launchpad.net/ubuntu/+source/kvm/+bug/1021271").

---

