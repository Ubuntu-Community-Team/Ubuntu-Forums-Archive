---
title: "qemu/KVM: Win7 guest sees only 2 CPUs"
date: 2010-09-09
forum: Server Platforms
---

### Post by oudalrich on 2010-09-09
I run Lucid 64bit on a 2x6 core Xeon X5650 server. I have a Win7 64bit guest running in qemu/KVM (installed with virt-install) that I have given 4 VCPUs. However, wherever I look in the guest OS (task manager, system information), only two CPUs are used.

Here's the guest definition:
```

<domain type='kvm'>
  <name>arkadi7</name>
  <uuid>f2637346-76c3-e0cd-e5e9-242bfb822782</uuid>
  <memory>16777216</memory>
  <currentMemory>16777216</currentMemory>
  <vcpu>4</vcpu>
  <os>
    <type arch='x86_64' machine='pc-0.12'>hvm</type>
    <boot dev='hd'/>
  </os>
  <features>
    <acpi/>
    <apic/>
    <pae/>
  </features>
  <clock offset='localtime'/>
  <on_poweroff>destroy</on_poweroff>
  <on_reboot>restart</on_reboot>
  <on_crash>restart</on_crash>
  <devices>
    <emulator>/usr/bin/kvm</emulator>
    <disk type='file' device='disk'>
      <driver name='qemu' cache='writeback'/>
      <source file='/home/uli/arkadi7.img'/>
      <target dev='hda' bus='ide'/>
    </disk>
    <disk type='file' device='cdrom'>
      <driver name='qemu'/>
      <source file='/home/uli/isos/SW_DVD5_SA_Win_Ent_7_64BIT_English_Full_MLF_X15-70749.ISO'/>
      <target dev='hdc' bus='ide'/>
      <readonly/>
    </disk>
    <interface type='bridge'>
      <mac address='52:54:00:5f:04:dc'/>
      <source bridge='br0'/>
    </interface>
    <console type='pty'>
      <target port='0'/>
    </console>
    <console type='pty'>
      <target port='0'/>
    </console>
    <input type='tablet' bus='usb'/>
    <input type='mouse' bus='ps2'/>
    <graphics type='vnc' port='-1' autoport='yes' listen='0.0.0.0' keymap='en-us'/>
    <video>
      <model type='cirrus' vram='9216' heads='1'/>
    </video>
  </devices>
</domain>

```

dominfo:

```

virsh # dominfo arkadi7
Id:             9
Name:           arkadi7
UUID:           f2637346-76c3-e0cd-e5e9-242bfb822782
OS Type:        hvm
State:          running
CPU(s):         4
CPU time:       55.3s
Max memory:     16777216 kB
Used memory:    16777216 kB
Autostart:      disable
Security model: apparmor
Security DOI:   0
Security label: libvirt-f2637346-76c3-e0cd-e5e9-242bfb822782 (enforcing)

```

virsh says that the 4 CPUs are running, but only 2 are used:

```

virsh # vcpuinfo arkadi7
VCPU:           0
CPU:            5
State:          running
CPU time:       19.5s
CPU Affinity:   yyyyyyyyyyyyyyyyyyyyyyyy

VCPU:           1
CPU:            12
State:          running
CPU time:       17.3s
CPU Affinity:   yyyyyyyyyyyyyyyyyyyyyyyy

VCPU:           2
CPU:            2
State:          running
CPU Affinity:   yyyyyyyyyyyyyyyyyyyyyyyy

VCPU:           3
CPU:            15
State:          running
CPU Affinity:   yyyyyyyyyyyyyyyyyyyyyyyy

```

I googled quite a bit but found no mention of KVM guests ignoring CPUs.

Could it have to do with this:

```

virsh # nodeinfo
CPU model:           x86_64
CPU(s):              24
CPU frequency:       2659 MHz
CPU socket(s):       4
Core(s) per socket:  6
Thread(s) per core:  1
NUMA cell(s):        1
Memory size:         74374984 kB

```

virsh thinks I have 4 processors with 6 cores, while in fact I have 2 processors with 6 cores, each with 2 threads.

Any ideas?

---

### Post by jek on 2011-01-18
See this topic for cpu vs core configuration:

[http://serverfault.com/questions/101434/why-does-my-windows-7-vm-running-under-linux-kvm-not-use-all-the-virtual-process](http://serverfault.com/questions/101434/why-does-my-windows-7-vm-running-under-linux-kvm-not-use-all-the-virtual-process)

---

