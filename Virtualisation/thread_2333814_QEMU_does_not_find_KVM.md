---
title: "QEMU does not find KVM"
date: 2016-08-13
forum: Virtualisation
---

### Post by martin30002 on 2016-08-13
Many times I have started Win7 on my second hard disk with 
```
sudo qemu-system-x86_64 -enable-kvm -boot order=c -m 512 -device ahci,id=c -drive file=/dev/sdc,index=0,media=disk,format=raw
```

Today, I got the error:[INDENT]

Could not access KVM kernel module: No such file or directory
failed to initialize KVM: No such file or directory



[/INDENT]
lscpu shows:
```
Architecture:          x86_64CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                8
On-line CPU(s) list:   0-7
Thread(s) per core:    2
Core(s) per socket:    4
Socket(s):             1
NUMA node(s):          1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 94
Model name:            Intel(R) Core(TM) i7-6700T CPU @ 2.80GHz
Stepping:              3
CPU MHz:               799.968
CPU max MHz:           3600,0000
CPU min MHz:           800,0000
BogoMIPS:              5616.51
Virtualization:        VT-x
L1d cache:             32K
L1i cache:             32K
L2 cache:              256K
L3 cache:              8192K
NUMA node0 CPU(s):     0-7

```

uname -a:
```
Linux JMS-lnx 4.4.0-34-generic #53-Ubuntu SMP Wed Jul 27 16:06:39 UTC 2016 x86_64 x86_64 x86_64 
```

modinfo kvm:
```
filename:       /lib/modules/4.4.0-34-generic/kernel/arch/x86/kvm/kvm.ko
license:        GPL
author:         Qumranet
srcversion:     8CAD4F0C9CB1D62DB2778B3
depends:        irqbypass
intree:         Y
vermagic:       4.4.0-34-generic SMP mod_unload modversions 
parm:           allow_unsafe_assigned_interrupts:Enable device assignment on platforms without interrupt remapping support. (bool)
parm:           ignore_msrs:bool
parm:           min_timer_period_us:uint
parm:           kvmclock_periodic_sync:bool
parm:           tsc_tolerance_ppm:uint
parm:           lapic_timer_advance_ns:uint
parm:           halt_poll_ns:uint
parm:           halt_poll_ns_grow:int
parm:           halt_poll_ns_shrink:int

```


I think this arised with the new kernel, but I'm not sure since I did not use qemu for a few weeks.

---

### Post by MAFoElffen on 2016-08-13
And if on boot, at the grub2 boot menu, if you  select advanced option and boot to an earlier kernel, does it then work for you?

---

### Post by martin30002 on 2016-08-13
Sorry, I am stupid. It was disabled in BIOS, don't know why. Since lscpu and /proc/cpuinfo showed virtualization, I thought is is on.

---

### Post by MAFoElffen on 2016-08-14
So after enabling in BIOS, this works again (and was not related to your last update)?

---

