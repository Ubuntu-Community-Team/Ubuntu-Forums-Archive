---
title: "nested kvm"
date: 2012-02-20
forum: Virtualisation
---

### Post by Metallion on 2012-02-20
Hi all. I am having trouble setting up a nested kvm environment.Here's what I'm doing:

I have one bare metal machine. Let's call it the host.
On it I have I have 1 virtual machine that will act as a hypervisor with its own VMs. Let's call it the guest hypervisor.

When I try to start a kvm accelerated VM on the guest hypervisor, it just hangs with a black screen in vnc. When I start one without kvm, it works but of course, very slowly. I do think it should be possible to get nested kvm VMs with my currenct configuration.

**Configuration of the host:**

uname -a
```

Linux hadaka 2.6.32-38-server #83-Ubuntu SMP Wed Jan 4 11:26:59 UTC 2012 x86_64 GNU/Linux

```

cat /proc/cpuinfo
```

processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 16
model		: 2
model name	: AMD Phenom(tm) 9950 Quad-Core Processor
stepping	: 3
cpu MHz		: 1300.000
cache size	: 512 KB
physical id	: 0
siblings	: 4
core id		: 0
cpu cores	: 4
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs
bogomips	: 5200.55
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

processor	: 1
vendor_id	: AuthenticAMD
cpu family	: 16
model		: 2
model name	: AMD Phenom(tm) 9950 Quad-Core Processor
stepping	: 3
cpu MHz		: 1300.000
cache size	: 512 KB
physical id	: 0
siblings	: 4
core id		: 1
cpu cores	: 4
apicid		: 1
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs
bogomips	: 5200.11
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

processor	: 2
vendor_id	: AuthenticAMD
cpu family	: 16
model		: 2
model name	: AMD Phenom(tm) 9950 Quad-Core Processor
stepping	: 3
cpu MHz		: 1300.000
cache size	: 512 KB
physical id	: 0
siblings	: 4
core id		: 3
cpu cores	: 4
apicid		: 2
initial apicid	: 3
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs
bogomips	: 5200.00
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

processor	: 3
vendor_id	: AuthenticAMD
cpu family	: 16
model		: 2
model name	: AMD Phenom(tm) 9950 Quad-Core Processor
stepping	: 3
cpu MHz		: 2600.000
cache size	: 512 KB
physical id	: 0
siblings	: 4
core id		: 2
cpu cores	: 4
apicid		: 3
initial apicid	: 2
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs
bogomips	: 5200.02
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

```

virsh nodeinfo
```

CPU model:           x86_64
CPU(s):              4
CPU frequency:       2600 MHz
CPU socket(s):       1
Core(s) per socket:  4
Thread(s) per core:  1
NUMA cell(s):        1
Memory size:         8064924 kB

```

modinfo kvm_amd | grep -i nested
```

parm:           nested:int

```

cat /sys/module/kvm_amd/parameters/nested
```

1

```

systool -m kvm_amd -v   | grep -i nested
```

    nested              = "1"

```

The script to start the guest hypervisor:
```

#!/bin/bash
USERID=`whoami`
IFACE=$(sudo tunctl -b -u $USERID)

kvm -smp 2 -cpu host -enable-nesting -vnc :3 -drive file=wakame_11.12_nested_test.raw -m 2048 -net nic,macaddr=52:54:00:12:34:59 -net tap,ifname="$IFACE" -enable-kvm
 
sudo tunctl -d $IFACE &> /dev/null

```

**Configuration of the guest hypervisor:**

uname -a
```

Linux wakame-nested-test 2.6.32-33-server #70-Ubuntu SMP Thu Jul 7 22:28:30 UTC 2011 x86_64 GNU/Linux

```

file /dev/kvm
```
 
/dev/kvm: character special

```

modinfo kvm_amd
```
filename:       /lib/modules/2.6.32-33-server/kernel/arch/x86/kvm/kvm-amd.ko
license:        GPL
author:         Qumranet
srcversion:     787D165670C0AB2CE74096D
depends:        kvm
vermagic:       2.6.32-33-server SMP mod_unload modversions 
parm:           npt:int
parm:           nested:int

```

cat /proc/cpuinfo
```

processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 16
model           : 2
model name      : AMD Phenom(tm) 9950 Quad-Core Processor
stepping        : 3
cpu MHz         : 2600.276
cache size      : 512 KB
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt pdpe1gb lm rep_good extd_apicid pni cx16 popcnt hypervisor lahf_lm cmp_legacy svm cr8_legacy abm sse4a misalignsse 3dnowprefetch
bogomips        : 5200.55
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management:

processor       : 1
vendor_id       : AuthenticAMD
cpu family      : 16
model           : 2
model name      : AMD Phenom(tm) 9950 Quad-Core Processor
stepping        : 3
cpu MHz         : 2600.276
cache size      : 512 KB
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt pdpe1gb lm rep_good extd_apicid pni cx16 popcnt hypervisor lahf_lm cmp_legacy svm cr8_legacy abm sse4a misalignsse 3dnowprefetch
bogomips        : 5200.55
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management:

```

command to start kvm:
```

sudo kvm -m 512 -smp 2 -name joske -vnc :3 -hda ubuntu-10.04_secgtest_kvm_i386.raw

```

Does anybody see a problem with my configuration? Thanks in advance.

---

### Post by Metallion on 2012-02-20
Ok I tried the same thing on an amd opteron host and there it worked. So I suspect the host's phenom processor to be the culprit. Does anyone know if nested kvm is possible on amd phenom processors?

---

