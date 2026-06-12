---
title: "After switching to full-screen the system becomes unstable"
date: 2023-09-25
forum: Virtualisation
---

### Post by pioflor on 2023-09-25
After switching to full-screen mode on Oracle VM VirtualBox, the system becomes unstable.
```

hubble@main01:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 22.04.2 LTS
Release:    22.04
Codename:    jammy
hubble@main01:~$ VBoxManage --version
6.1.38_Ubuntur153438
hubble@main01:~$ 

```

[COLOR=#374151][FONT=Söhne]I have the Guest Additions installed.[/FONT][/COLOR]

---

### Post by MAFoElffen on 2023-09-25
What is the host?

How much RAM and disk did you allocate the Guest?

Do you have vbox guest additions installed in the VM?

How do you have the grapics setting setupfor the VM Guest machine configuration? (ie- 3D acceleration enabled?)

How do you have the Graphics settings set in the Guest OS, using which Graphics engine? (i.e.- wayland?)

What is the GPU of the host, and graphics details of the host?

---

### Post by pioflor on 2023-09-25
I have updated the version.
```

hubble@main01:~/Downloads$ VBoxManage --version
7.0.10r158379


```

Host:
```

lscpu
Architecture:            x86_64
  CPU op-mode(s):        32-bit, 64-bit
  Address sizes:         39 bits physical, 48 bits virtual
  Byte Order:            Little Endian
CPU(s):                  8
  On-line CPU(s) list:   0-7
Vendor ID:               GenuineIntel
  Model name:            Intel(R) Core(TM) i5-8365U CPU @ 1.60GHz
    CPU family:          6
    Model:               142
    Thread(s) per core:  2
    Core(s) per socket:  4
    Socket(s):           1
    Stepping:            12
    CPU max MHz:         4100,0000
    CPU min MHz:         400,0000
    BogoMIPS:            3799.90
    Flags:               fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe
                         1gb rdtscp lm constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq dtes64 monitor 
                         ds_cpl vmx smx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdran
                         d lahf_lm abm 3dnowprefetch cpuid_fault epb invpcid_single ssbd ibrs ibpb stibp ibrs_enhanced tpr_shadow vnmi flexpriority ept vpid ept
                         _ad fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid mpx rdseed adx smap clflushopt intel_pt xsaveopt xsavec xgetbv1 xsaves dtherm 
                         ida arat pln pts hwp hwp_notify hwp_act_window hwp_epp md_clear flush_l1d arch_capabilities
Virtualization features: 
  Virtualization:        VT-x
Caches (sum of all):     
  L1d:                   128 KiB (4 instances)
  L1i:                   128 KiB (4 instances)
  L2:                    1 MiB (4 instances)
  L3:                    6 MiB (1 instance)
NUMA:                    
  NUMA node(s):          1
  NUMA node0 CPU(s):     0-7
Vulnerabilities:         
  Itlb multihit:         KVM: Mitigation: VMX disabled
  L1tf:                  Not affected
  Mds:                   Not affected
  Meltdown:              Not affected
  Mmio stale data:       Mitigation; Clear CPU buffers; SMT vulnerable
  Retbleed:              Mitigation; Enhanced IBRS
  Spec store bypass:     Mitigation; Speculative Store Bypass disabled via prctl
  Spectre v1:            Mitigation; usercopy/swapgs barriers and __user pointer sanitization
  Spectre v2:            Mitigation; Enhanced IBRS, IBPB conditional, RSB filling, PBRSB-eIBRS SW sequence
  Srbds:                 Mitigation; Microcode
  Tsx async abort:       Mitigation; TSX disabled
hubble@main01:~/Downloads$ lshw -C display
WARNING: you should run this program as super-user.
  *-display                 
       description: VGA compatible controller
       product: WhiskeyLake-U GT2 [UHD Graphics 620]
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       logical name: /dev/fb0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom fb
       configuration: depth=32 driver=i915 latency=0 resolution=1920,1080
       resources: irq:181 memory:cb000000-cbffffff memory:80000000-8fffffff ioport:3000(size=64) memory:c0000-dffff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
hubble@main01:~/Downloads$ 





```

Guest:
```

$ VBoxManage showvminfo Lubuntu
Name:                        Lubuntu
Encryption:     disabled
Groups:                      /
Guest OS:                    Ubuntu (64-bit)
UUID:                        e2f842a3-41b7-42ff-bf85-a22c48d7c96b
Config file:                 /home/hubble/VirtualBox VMs/Lubuntu/Lubuntu.vbox
Snapshot folder:             /home/hubble/VirtualBox VMs/Lubuntu/Snapshots
Log folder:                  /home/hubble/VirtualBox VMs/Lubuntu/Logs
Hardware UUID:               e2f842a3-41b7-42ff-bf85-a22c48d7c96b
Memory size:                 8048MB
Page Fusion:                 disabled
VRAM size:                   16MB
CPU exec cap:                100%
HPET:                        disabled
CPUProfile:                  host
Chipset:                     piix3
Firmware:                    BIOS
Number of CPUs:              1
PAE:                         disabled
Long Mode:                   enabled
Triple Fault Reset:          disabled
APIC:                        enabled
X2APIC:                      enabled
Nested VT-x/AMD-V:           disabled
CPUID Portability Level:     0
CPUID overrides:             None
Boot menu mode:              message and menu
Boot Device 1:               Floppy
Boot Device 2:               DVD
Boot Device 3:               HardDisk
Boot Device 4:               Not Assigned
ACPI:                        enabled
IOAPIC:                      enabled
BIOS APIC mode:              APIC
Time offset:                 0ms
BIOS NVRAM File:             /home/hubble/VirtualBox VMs/Lubuntu/Lubuntu.nvram
RTC:                         UTC
Hardware Virtualization:     enabled
Nested Paging:               enabled
Large Pages:                 enabled
VT-x VPID:                   enabled
VT-x Unrestricted Exec.:     enabled
AMD-V Virt. Vmsave/Vmload:   enabled
IOMMU:                       None
Paravirt. Provider:          Default
Effective Paravirt. Prov.:   KVM
State:                       powered off (since 2023-09-25T15:36:23.197000000)
Graphics Controller:         VMSVGA
Monitor count:               1
3D Acceleration:             disabled
2D Video Acceleration:       disabled
Teleporter Enabled:          disabled
Teleporter Port:             0
Teleporter Address:          
Teleporter Password:         
Tracing Enabled:             disabled
Allow Tracing to Access VM:  disabled
Tracing Configuration:       
Autostart Enabled:           disabled
Autostart Delay:             0
Default Frontend:            
VM process priority:         default
Storage Controllers:
#0: 'IDE', Type: PIIX4, Instance: 0, Ports: 2 (max 2), Bootable
  Port 1, Unit 0: UUID: 7aaf4da6-5258-4853-a457-6756a1646ff6
    Location: "/usr/share/virtualbox/VBoxGuestAdditions.iso"
#1: 'SATA', Type: IntelAhci, Instance: 0, Ports: 1 (max 30), Bootable
  Port 0, Unit 0: UUID: 0e4d1b62-0537-4e67-972e-8c3cf54de3a7
    Location: "/home/hubble/VirtualBox VMs/Lubuntu/Lubuntu.vdi"
NIC 1:                       MAC: 080027D3F368, Attachment: NAT, Cable connected: on, Trace: off (file: none), Type: 82540EM, Reported speed: 0 Mbps, Boot priority: 0, Promisc Policy: deny, Bandwidth group: none
NIC 1 Settings:  MTU: 0, Socket (send: 64, receive: 64), TCP Window (send:64, receive: 64)
NIC 2:                       disabled
NIC 3:                       disabled
NIC 4:                       disabled
NIC 5:                       disabled
NIC 6:                       disabled
NIC 7:                       disabled
NIC 8:                       disabled
Pointing Device:             USB Tablet
Keyboard Device:             PS/2 Keyboard
UART 1:                      disabled
UART 2:                      disabled
UART 3:                      disabled
UART 4:                      disabled
LPT 1:                       disabled
LPT 2:                       disabled
Audio:                       enabled (Driver: Default, Controller: AC97, Codec: AD1980)
Audio playback:              enabled
Audio capture:               disabled
Clipboard Mode:              disabled
Drag and drop Mode:          disabled
VRDE:                        disabled
OHCI USB:                    enabled
EHCI USB:                    enabled
xHCI USB:                    disabled
USB Device Filters:          <none>
Bandwidth groups:            <none>
Shared folders:              <none>
Recording enabled:           no
Recording screens:           1
 Screen 0:
    Enabled:                 yes
    ID:                      0
    Record video:            yes
    Destination:             File
    File:                    /home/hubble/VirtualBox VMs/Lubuntu/Lubuntu-screen0.webm
    Options:                 vc_enabled=true,ac_enabled=false,ac_profile=med
    Video dimensions:        1024x768
    Video rate:              512kbps
    Video FPS:               25fps
* Guest:
Configured memory balloon:   0MB

hubble@main01:~/Downloads$ 



```

---

