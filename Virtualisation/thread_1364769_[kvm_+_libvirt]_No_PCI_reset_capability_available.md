---
title: "[kvm + libvirt] No PCI reset capability available"
date: 2009-12-26
forum: Virtualisation
---

### Post by Quetschke on 2009-12-26
Hello guys,

I am having the following issue when I try to start the domain 'lenny':
```
manager@charlie:~$ virsh start lenny
Connecting to uri: qemu:///system
Fehler: Domain lenny konnte nicht gestartet werden
Fehler: this function is not supported by the hypervisor: No PCI reset capability available for 0000:11:09.0
```

The domain's configuration is:
```
<domain type='kvm'>
  <name>lenny</name>
  <uuid>daf58316-7529-6b91-38d0-c77128c6e83e</uuid>
  <memory>524288</memory>
  <currentMemory>524288</currentMemory>
  <vcpu>1</vcpu>
  <os>
    <type arch='x86_64' machine='pc-0.11'>hvm</type>
    <boot dev='hd'/>
  </os>
  <features>
    <acpi/>
    <apic/>
    <pae/>
  </features>
  <clock offset='utc'/>
  <on_poweroff>destroy</on_poweroff>
  <on_reboot>restart</on_reboot>
  <on_crash>restart</on_crash>
  <devices>
    <emulator>/usr/bin/kvm</emulator>
    <disk type='file' device='cdrom'>
      <target dev='hdc' bus='ide'/>
      <readonly/>
    </disk>
    <disk type='file' device='disk'>
      <source file='/usr/local/vm/disks/lenny0.img'/>
      <target dev='vda' bus='virtio'/>
    </disk>
    <interface type='bridge'>
      <mac address='54:52:00:50:8f:be'/>
      <source bridge='br30'/>
      <model type='virtio'/>
    </interface>
    <interface type='bridge'>
      <mac address='52:54:00:b3:d7:22'/>
      <source bridge='brS'/>
      <model type='virtio'/>
    </interface>
    <serial type='pty'>
      <target port='0'/>
    </serial>
    <console type='pty'>
      <target port='0'/>
    </console>
    <input type='mouse' bus='ps2'/>
    <graphics type='vnc' port='-1' autoport='yes' keymap='de'/>
    <video>
      <model type='cirrus' vram='9216' heads='1'/>
    </video>
    <hostdev mode='subsystem' type='pci' managed='no'>
      <source>
        <address domain='0x0000' bus='0x11' slot='0x09' function='0x0'/>
      </source>
    </hostdev>
    <hostdev mode='subsystem' type='pci' managed='no'>
      <source>
        <address domain='0x0000' bus='0x11' slot='0x09' function='0x1'/>
      </source>
    </hostdev>
    <hostdev mode='subsystem' type='pci' managed='no'>
      <source>
        <address domain='0x0000' bus='0x11' slot='0x09' function='0x2'/>
      </source>
    </hostdev>
  </devices>
</domain>
```

This is the output of lspci (I have bound the devices to the pci-stub driver):
```
11:09.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
        Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
        Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV+ VGASnoop- ParErr+ Stepping- SERR+ FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Interrupt: pin A routed to IRQ 23
        Region 4: I/O ports at 3020 [size=32]
        Capabilities: [80] Power Management version 2
                Flags: PMEClk+ DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Kernel driver in use: pci-stub

11:09.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
        Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
        Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV+ VGASnoop- ParErr+ Stepping- SERR+ FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Interrupt: pin B routed to IRQ 20
        Region 4: I/O ports at 3040 [size=32]
        Capabilities: [80] Power Management version 2
                Flags: PMEClk+ DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Kernel driver in use: pci-stub

11:09.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 65) (prog-if 20)
        Subsystem: VIA Technologies, Inc. USB 2.0
        Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV+ VGASnoop- ParErr+ Stepping- SERR+ FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Interrupt: pin C routed to IRQ 21
        Region 0: Memory at d5102000 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2
                Flags: PMEClk+ DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Kernel driver in use: pci-stub
```

vt-d has been enabled in BIOS. vmx is supported by the CPU:
```
manager@charlie:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 23
model name      : Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz
stepping        : 10
cpu MHz         : 2000.000
cache size      : 6144 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
apicid          : 0
initial apicid  : 0
fpu             : yes
fpu_exception   : yes
cpuid level     : 13
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm tpr_shadow vnmi flexpriority
bogomips        : 6000.96
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 23
model name      : Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz
stepping        : 10
cpu MHz         : 2000.000
cache size      : 6144 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
apicid          : 1
initial apicid  : 1
fpu             : yes
fpu_exception   : yes
cpuid level     : 13
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm tpr_shadow vnmi flexpriority
bogomips        : 6000.46
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:
```

I have also compiled my own kernel variant with these options:```
[*] PCI support                                                                             &#9474; &#9474;
  &#9474; &#9474;                      [*]   Support mmconfig PCI config space access                                              &#9474; &#9474;
  &#9474; &#9474;                      [*] Support for DMA Remapping Devices (EXPERIMENTAL)                                        &#9474; &#9474;
  &#9474; &#9474;                      [*]   Enable DMA Remapping Devices by default                                               &#9474; &#9474;
  &#9474; &#9474;                      [*]   Workaround broken graphics drivers (going away soon)                                  &#9474; &#9474;
  &#9474; &#9474;                      [*] Support for Interrupt Remapping (EXPERIMENTAL)
```


So where is the problem? I've already followed every tip I found in certain howtos.


Thank you very much in advance.


Tobias

---

### Post by Quetschke on 2009-12-28
No ideas so far? :-(

This additional information may be useful:
```
root@charlie:/usr/src# uname -a
Linux charlie 2.6.31.4-my #1 SMP Fri Dec 25 12:44:20 CET 2009 x86_64 GNU/Linux
```

And syslog says:
```
Dec 28 13:31:28 charlie libvirtd: 13:31:28.825: warning : pciTrySecondaryBusReset:483 : Other devices on bus with 0000:11:09.0, not doing bus reset
Dec 28 13:31:28 charlie libvirtd: 13:31:28.826: warning : pciTryPowerManagementReset:546 : 0000:11:09.0 contains other functions, not resetting
Dec 28 13:31:28 charlie libvirtd: 13:31:28.826: error : pciResetDevice:618 : this function is not supported by the hypervisor: No PCI reset capability available for 0000:11:09.0
```

---

### Post by runderwo on 2010-01-05
I'm having the same problem.  It's probably related to the fact that it's a multifunction device.

[https://bugzilla.redhat.com/show_bug.cgi?id=499678](https://bugzilla.redhat.com/show_bug.cgi?id=499678)

I wonder if the fix made it into the 0.70 release in Karmic.

---

### Post by slick666 on 2010-03-14
Having the same problem here but I don't know the wor around either.

---

