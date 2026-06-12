---
title: "KVM and libvirt: wrong CPU type in virtualized host"
date: 2012-12-27
forum: Virtualisation
---

### Post by Robert Kofler on 2012-12-27
We us KVM and libvirt on a 6 core (12 HT cores) machine for virtualization.

**Problem: wrong CPU type in virtualized host.**

used KVM, libvirt, kernel version:
```
libvirt version: 0.9.8
QEMU emulator version 1.0 (qemu-kvm-1.0), Copyright (c) 2003-2008 Fabrice Bellard
Ubuntu 12.04.1 LTS
kernel: 3.2.0-32-generic x86_64 
```

/usr/share/libvirt/cpu_map.xml does not support more recent cpu types than Westmere.

**Do I need this kind of virtualisation of the cpu at all? **because of some reasons we need maximum cpu-performance in the virtual host. 
Will be glad to have some cores of the server's i7-3930K CPU@3.20GHz available in my virtual machines.

Maybe we do too much virtualization...?

my virtual host's xml looks like: where can I set the cpu -host flag?

```
<domain type='kvm'>
  <name>myVirtualServer</name>
  <uuid>2344481d-f455-455e-9558</uuid>
  <description>Test-Server</description>
  <memory>4194304</memory>
  <currentMemory>4194304</currentMemory>
  <vcpu>2</vcpu>
  <cpu match='exact'>
    <model>Westmere</model>
    <vendor>Intel</vendor>
  </cpu>
  <os>
    <type arch='x86_64' machine='pc-1.0'>hvm</type>
    <boot dev='hd'/>
  </os>
  <features>
    <acpi/>
    <apic/>
    <pae/>
  </features>
```

$ lscpu of physical Server with 6 (12) cores with HT
```
Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                12
On-line CPU(s) list:   0-11
Thread(s) per core:    2
Core(s) per socket:    6
Socket(s):             1
NUMA node(s):          1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 45
Stepping:              7
CPU MHz:               1200.000
BogoMIPS:              6400.05
Virtualization:        VT-x
L1d cache:             32K
L1i cache:             32K
L2 cache:              256K
L3 cache:              12288K
NUMA node0 CPU(s):     0-11
```

$ lscpu of virtual Server (wrong CPU type, wrong L2-Cache)

```
Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                2
On-line CPU(s) list:   0,1
Thread(s) per core:    1
Core(s) per socket:    1
Socket(s):             2
NUMA node(s):          1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 15
Stepping:              11
CPU MHz:               3200.012
BogoMIPS:              6400.02
Virtualisation:        VT-x
Hypervisor vendor:     KVM
Virtualisation type:   full
L1d cache:             32K
L1i cache:             32K
L2 cache:              4096K
NUMA node0 CPU(s):     0,1
```

---

