---
title: "Virtual box quit running disk image Windows XP"
date: 2010-05-10
forum: Virtualisation
---

### Post by discord on 2010-05-10
Hi,

I just recently installed VB 3.1.8 on ubuntu 10.04 . Loaded my disk image and it worked fine. Asked me to install 3.1.8 addons, which I did, told me to restart. Now XP shows the loading screen and then terminates? Can I get this XP image running again?

```
00:00:03.665 VirtualBox 3.1.8 r61349 linux.x86 (May  9 2010 21:39:10) release log
00:00:03.665 Log opened 2010-05-11T03:38:15.516555000Z
00:00:03.665 OS Product: Linux
00:00:03.665 OS Release: 2.6.32-22-generic
00:00:03.665 OS Version: #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010
00:00:03.665 Host RAM: 1498MB RAM, available: 1101MB
00:00:03.665 Executable: /usr/lib/virtualbox/VirtualBox
00:00:03.665 Process ID: 8158
00:00:03.665 Package type: LINUX_32BITS_UBUNTU_10_04
00:00:03.704 SUP: Loaded VMMR0.r0 (/usr/lib/virtualbox/VMMR0.r0) at 0xfb32b060 - ModuleInit at 00000000fb33e8a0 and ModuleTerm at 00000000fb33e860
00:00:03.704 SUP: VMMR0EntryEx located at 00000000fb33e740, VMMR0EntryFast at 00000000fb33da70 and VMMR0EntryInt at 00000000fb33d880
00:00:03.856 VBoxSharedClipboard mode: Bidirectional
00:00:03.878 ************************* CFGM dump *************************
00:00:03.878 [/] (level 0)
00:00:03.878   CSAMEnabled     <integer> = 0x0000000000000001 (1)
00:00:03.878   EnablePAE       <integer> = 0x0000000000000000 (0)
00:00:03.878   HwVirtExtForced <integer> = 0x0000000000000000 (0)
00:00:03.878   Name            <string>  = "windozeXP" (cb=10)
00:00:03.878   NumCPUs         <integer> = 0x0000000000000001 (1)
00:00:03.878   PATMEnabled     <integer> = 0x0000000000000001 (1)
00:00:03.878   RamHoleSize     <integer> = 0x0000000020000000 (536870912)
00:00:03.878   RamSize         <integer> = 0x0000000020000000 (536870912)
00:00:03.878   RawR0Enabled    <integer> = 0x0000000000000001 (1)
00:00:03.878   RawR3Enabled    <integer> = 0x0000000000000001 (1)
00:00:03.878   SyntheticCpu    <integer> = 0x0000000000000000 (0)
00:00:03.878   TimerMillies    <integer> = 0x000000000000000a (10)
00:00:03.878   UUID            <bytes>   = "13 ab a7 7a 2e 37 46 45 b3 7d c0 f0 67 24 90 d3" (cb=16)
00:00:03.878 
00:00:03.878 [/Devices/] (level 1)
00:00:03.878 
00:00:03.878 [/Devices/8237A/] (level 2)
00:00:03.878 
00:00:03.878 [/Devices/8237A/0/] (level 3)
00:00:03.878   Trusted <integer> = 0x0000000000000001 (1)
00:00:03.878 
00:00:03.878 [/Devices/AudioSniffer/] (level 2)
00:00:03.878 
00:00:03.878 [/Devices/AudioSniffer/0/] (level 3)
00:00:03.878 
00:00:03.878 [/Devices/AudioSniffer/0/Config/] (level 4)
00:00:03.878 
00:00:03.878 [/Devices/AudioSniffer/0/LUN#0/] (level 4)
00:00:03.878   Driver <string>  = "MainAudioSniffer" (cb=17)
00:00:03.878 
00:00:03.878 [/Devices/AudioSniffer/0/LUN#0/Config/] (level 5)
00:00:03.879   Object <integer> = 0x0000000008ffc3e8 (150979560)
00:00:03.879 
00:00:03.879 [/Devices/VMMDev/] (level 2)
00:00:03.879 
00:00:03.879 [/Devices/VMMDev/0/] (level 3)
00:00:03.879   PCIDeviceNo   <integer> = 0x0000000000000004 (4)
00:00:03.879   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:03.879   Trusted       <integer> = 0x0000000000000001 (1)
00:00:03.879 
00:00:03.879 [/Devices/VMMDev/0/Config/] (level 4)
00:00:03.879 
00:00:03.879 [/Devices/VMMDev/0/LUN#0/] (level 4)
00:00:03.879   Driver <string>  = "HGCM" (cb=5)
00:00:03.879 
00:00:03.879 [/Devices/VMMDev/0/LUN#0/Config/] (level 5)
00:00:03.879   Object <integer> = 0x0000000008ffad60 (150973792)
00:00:03.879 
00:00:03.879 [/Devices/VMMDev/0/LUN#999/] (level 4)
00:00:03.879   Driver <string>  = "MainStatus" (cb=11)
00:00:03.879 
00:00:03.879 [/Devices/VMMDev/0/LUN#999/Config/] (level 5)
00:00:03.879   First   <integer> = 0x0000000000000000 (0)
00:00:03.879   Last    <integer> = 0x0000000000000000 (0)
00:00:03.879   papLeds <integer> = 0x0000000008ffb238 (150975032)
00:00:03.879 
00:00:03.879 [/Devices/acpi/] (level 2)
00:00:03.879 
00:00:03.879 [/Devices/acpi/0/] (level 3)
00:00:03.879   PCIDeviceNo   <integer> = 0x0000000000000007 (7)
00:00:03.879   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:03.879   Trusted       <integer> = 0x0000000000000001 (1)
00:00:03.879 
00:00:03.879 [/Devices/acpi/0/Config/] (level 4)
00:00:03.879   FdcEnabled  <integer> = 0x0000000000000001 (1)
00:00:03.879   HpetEnabled <integer> = 0x0000000000000000 (0)
00:00:03.879   IOAPIC      <integer> = 0x0000000000000000 (0)
00:00:03.879   NumCPUs     <integer> = 0x0000000000000001 (1)
00:00:03.879   RamHoleSize <integer> = 0x0000000020000000 (536870912)
00:00:03.879   RamSize     <integer> = 0x0000000020000000 (536870912)
00:00:03.879   ShowCpu     <integer> = 0x0000000000000000 (0)
00:00:03.879   ShowRtc     <integer> = 0x0000000000000000 (0)
00:00:03.879 
00:00:03.879 [/Devices/acpi/0/LUN#0/] (level 4)
00:00:03.879   Driver <string>  = "ACPIHost" (cb=9)
00:00:03.879 
00:00:03.879 [/Devices/acpi/0/LUN#0/Config/] (level 5)
00:00:03.879 
00:00:03.879 [/Devices/apic/] (level 2)
00:00:03.879 
00:00:03.879 [/Devices/apic/0/] (level 3)
00:00:03.880   Trusted <integer> = 0x0000000000000001 (1)
00:00:03.880 
00:00:03.880 [/Devices/apic/0/Config/] (level 4)
00:00:03.880   IOAPIC  <integer> = 0x0000000000000000 (0)
00:00:03.880   NumCPUs <integer> = 0x0000000000000001 (1)
00:00:03.880 
00:00:03.880 [/Devices/e1000/] (level 2)
00:00:03.880 
00:00:03.880 [/Devices/i82078/] (level 2)
00:00:03.880 
00:00:03.880 [/Devices/i82078/0/] (level 3)
00:00:03.880   Trusted <integer> = 0x0000000000000001 (1)
00:00:03.880 
00:00:03.880 [/Devices/i82078/0/Config/] (level 4)
00:00:03.880   DMA       <integer> = 0x0000000000000002 (2)
00:00:03.880   IOBase    <integer> = 0x00000000000003f0 (1008)
00:00:03.880   IRQ       <integer> = 0x0000000000000006 (6)
00:00:03.880   MemMapped <integer> = 0x0000000000000000 (0)
00:00:03.880 
00:00:03.880 [/Devices/i82078/0/LUN#0/] (level 4)
00:00:03.880   Driver <string>  = "Block" (cb=6)
00:00:03.880 
00:00:03.880 [/Devices/i82078/0/LUN#0/Config/] (level 5)
00:00:03.880   Mountable <integer> = 0x0000000000000001 (1)
00:00:03.880   Type      <string>  = "Floppy 1.44" (cb=12)
00:00:03.880 
00:00:03.880 [/Devices/i82078/0/LUN#999/] (level 4)
00:00:03.880   Driver <string>  = "MainStatus" (cb=11)
00:00:03.880 
00:00:03.880 [/Devices/i82078/0/LUN#999/Config/] (level 5)
00:00:03.880   First   <integer> = 0x0000000000000000 (0)
00:00:03.880   Last    <integer> = 0x0000000000000000 (0)
00:00:03.880   papLeds <integer> = 0x0000000008ffb14c (150974796)
00:00:03.880 
00:00:03.880 [/Devices/i8254/] (level 2)
00:00:03.880 
00:00:03.880 [/Devices/i8254/0/] (level 3)
00:00:03.880 
00:00:03.880 [/Devices/i8254/0/Config/] (level 4)
00:00:03.880 
00:00:03.880 [/Devices/i8259/] (level 2)
00:00:03.880 
00:00:03.880 [/Devices/i8259/0/] (level 3)
00:00:03.880   Trusted <integer> = 0x0000000000000001 (1)
00:00:03.880 
00:00:03.880 [/Devices/i8259/0/Config/] (level 4)
00:00:03.881 
00:00:03.881 [/Devices/ichac97/] (level 2)
00:00:03.881 
00:00:03.881 [/Devices/ichac97/0/] (level 3)
00:00:03.881   PCIDeviceNo   <integer> = 0x0000000000000005 (5)
00:00:03.881   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:03.881   Trusted       <integer> = 0x0000000000000001 (1)
00:00:03.881 
00:00:03.881 [/Devices/ichac97/0/Config/] (level 4)
00:00:03.881 
00:00:03.881 [/Devices/ichac97/0/LUN#0/] (level 4)
00:00:03.881   Driver <string>  = "AUDIO" (cb=6)
00:00:03.881 
00:00:03.881 [/Devices/ichac97/0/LUN#0/Config/] (level 5)
00:00:03.881   AudioDriver <string>  = "pulse" (cb=6)
00:00:03.881   StreamName  <string>  = "windozeXP" (cb=10)
00:00:03.881 
00:00:03.881 [/Devices/mc146818/] (level 2)
00:00:03.881 
00:00:03.881 [/Devices/mc146818/0/] (level 3)
00:00:03.881 
00:00:03.881 [/Devices/mc146818/0/Config/] (level 4)
00:00:03.881 
00:00:03.881 [/Devices/parallel/] (level 2)
00:00:03.881 
00:00:03.881 [/Devices/pcarch/] (level 2)
00:00:03.881 
00:00:03.881 [/Devices/pcarch/0/] (level 3)
00:00:03.881   Trusted <integer> = 0x0000000000000001 (1)
00:00:03.881 
00:00:03.881 [/Devices/pcarch/0/Config/] (level 4)
00:00:03.881 
00:00:03.881 [/Devices/pcbios/] (level 2)
00:00:03.881 
00:00:03.881 [/Devices/pcbios/0/] (level 3)
00:00:03.881   Trusted <integer> = 0x0000000000000001 (1)
00:00:03.881 
00:00:03.881 [/Devices/pcbios/0/Config/] (level 4)
00:00:03.881   BootDevice0    <string>  = "FLOPPY" (cb=7)
00:00:03.881   BootDevice1    <string>  = "DVD" (cb=4)
00:00:03.881   BootDevice2    <string>  = "IDE" (cb=4)
00:00:03.881   BootDevice3    <string>  = "NONE" (cb=5)
00:00:03.881   FloppyDevice   <string>  = "i82078" (cb=7)
00:00:03.881   HardDiskDevice <string>  = "piix3ide" (cb=9)
00:00:03.881   IOAPIC         <integer> = 0x0000000000000000 (0)
00:00:03.881   NumCPUs        <integer> = 0x0000000000000001 (1)
00:00:03.881   PXEDebug       <integer> = 0x0000000000000000 (0)
00:00:03.881   RamHoleSize    <integer> = 0x0000000020000000 (536870912)
00:00:03.881   RamSize        <integer> = 0x0000000020000000 (536870912)
00:00:03.882   UUID           <bytes>   = "13 ab a7 7a 2e 37 46 45 b3 7d c0 f0 67 24 90 d3" (cb=16)
00:00:03.882 
00:00:03.882 [/Devices/pci/] (level 2)
00:00:03.882 
00:00:03.882 [/Devices/pci/0/] (level 3)
00:00:03.882   Trusted <integer> = 0x0000000000000001 (1)
00:00:03.882 
00:00:03.882 [/Devices/pci/0/Config/] (level 4)
00:00:03.882   IOAPIC <integer> = 0x0000000000000000 (0)
00:00:03.882 
00:00:03.882 [/Devices/pckbd/] (level 2)
00:00:03.882 
00:00:03.882 [/Devices/pckbd/0/] (level 3)
00:00:03.882   Trusted <integer> = 0x0000000000000001 (1)
00:00:03.882 
00:00:03.882 [/Devices/pckbd/0/Config/] (level 4)
00:00:03.882 
00:00:03.882 [/Devices/pckbd/0/LUN#0/] (level 4)
00:00:03.882   Driver <string>  = "KeyboardQueue" (cb=14)
00:00:03.882 
00:00:03.882 [/Devices/pckbd/0/LUN#0/AttachedDriver/] (level 5)
00:00:03.882   Driver <string>  = "MainKeyboard" (cb=13)
00:00:03.882 
00:00:03.882 [/Devices/pckbd/0/LUN#0/AttachedDriver/Config/] (level 6)
00:00:03.882   Object <integer> = 0x0000000008ffb660 (150976096)
00:00:03.882 
00:00:03.882 [/Devices/pckbd/0/LUN#0/Config/] (level 5)
00:00:03.882   QueueSize <integer> = 0x0000000000000040 (64)
00:00:03.882 
00:00:03.882 [/Devices/pckbd/0/LUN#1/] (level 4)
00:00:03.882   Driver <string>  = "MouseQueue" (cb=11)
00:00:03.882 
00:00:03.882 [/Devices/pckbd/0/LUN#1/AttachedDriver/] (level 5)
00:00:03.882   Driver <string>  = "MainMouse" (cb=10)
00:00:03.882 
00:00:03.882 [/Devices/pckbd/0/LUN#1/AttachedDriver/Config/] (level 6)
00:00:03.882   Object <integer> = 0x0000000008ffb738 (150976312)
00:00:03.882 
00:00:03.882 [/Devices/pckbd/0/LUN#1/Config/] (level 5)
00:00:03.882   QueueSize <integer> = 0x0000000000000080 (128)
00:00:03.882 
00:00:03.882 [/Devices/pcnet/] (level 2)
00:00:03.891 
00:00:03.891 [/Devices/pcnet/0/] (level 3)
00:00:03.891   PCIDeviceNo   <integer> = 0x0000000000000003 (3)
00:00:03.891   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:03.891   Trusted       <integer> = 0x0000000000000001 (1)
00:00:03.891 
00:00:03.891 [/Devices/pcnet/0/Config/] (level 4)
00:00:03.891   Am79C973       <integer> = 0x0000000000000001 (1)
00:00:03.891   CableConnected <integer> = 0x0000000000000001 (1)
00:00:03.891   LineSpeed      <integer> = 0x0000000000000000 (0)
00:00:03.891   MAC            <bytes>   = "08 00 27 70 86 89" (cb=6)
00:00:03.891 
00:00:03.891 [/Devices/pcnet/0/LUN#0/] (level 4)
00:00:03.891   Driver <string>  = "NAT" (cb=4)
00:00:03.891 
00:00:03.891 [/Devices/pcnet/0/LUN#0/Config/] (level 5)
00:00:03.891   BootFile   <string>  = "windozeXP.pxe" (cb=14)
00:00:03.891   TFTPPrefix <string>  = "/home/discord/.VirtualBox/TFTP" (cb=31)
00:00:03.891 
00:00:03.891 [/Devices/pcnet/0/LUN#999/] (level 4)
00:00:03.891   Driver <string>  = "MainStatus" (cb=11)
00:00:03.891 
00:00:03.891 [/Devices/pcnet/0/LUN#999/Config/] (level 5)
00:00:03.891   papLeds <integer> = 0x0000000008ffb218 (150975000)
00:00:03.891 
00:00:03.891 [/Devices/piix3ide/] (level 2)
00:00:03.891 
00:00:03.891 [/Devices/piix3ide/0/] (level 3)
00:00:03.891   PCIDeviceNo   <integer> = 0x0000000000000001 (1)
00:00:03.891   PCIFunctionNo <integer> = 0x0000000000000001 (1)
00:00:03.891   Trusted       <integer> = 0x0000000000000001 (1)
00:00:03.891 
00:00:03.891 [/Devices/piix3ide/0/Config/] (level 4)
00:00:03.891   Type <string>  = "PIIX4" (cb=6)
00:00:03.891 
00:00:03.891 [/Devices/piix3ide/0/LUN#0/] (level 4)
00:00:03.891   Driver <string>  = "Block" (cb=6)
00:00:03.891 
00:00:03.891 [/Devices/piix3ide/0/LUN#0/AttachedDriver/] (level 5)
00:00:03.891   Driver <string>  = "VD" (cb=3)
00:00:03.891 
00:00:03.891 [/Devices/piix3ide/0/LUN#0/AttachedDriver/Config/] (level 6)
00:00:03.891   Format <string>  = "VDI" (cb=4)
00:00:03.891   Path   <string>  = "/media/15776f4c-a37a-4dd1-ab57-ea9f06c55cc6/Zune2.vdi" (cb=54)
00:00:03.891 
00:00:03.891 [/Devices/piix3ide/0/LUN#0/Config/] (level 5)
00:00:03.891   Mountable <integer> = 0x0000000000000000 (0)
00:00:03.891   Type      <string>  = "HardDisk" (cb=9)
00:00:03.892 
00:00:03.892 [/Devices/piix3ide/0/LUN#2/] (level 4)
00:00:03.892   Driver <string>  = "Block" (cb=6)
00:00:03.892 
00:00:03.892 [/Devices/piix3ide/0/LUN#2/AttachedDriver/] (level 5)
00:00:03.892   Driver <string>  = "VD" (cb=3)
00:00:03.892 
00:00:03.892 [/Devices/piix3ide/0/LUN#2/AttachedDriver/Config/] (level 6)
00:00:03.892   Format   <string>  = "RAW" (cb=4)
00:00:03.892   Path     <string>  = "/usr/share/virtualbox/VBoxGuestAdditions.iso" (cb=45)
00:00:03.892   ReadOnly <integer> = 0x0000000000000001 (1)
00:00:03.892 
00:00:03.892 [/Devices/piix3ide/0/LUN#2/Config/] (level 5)
00:00:03.892   Mountable <integer> = 0x0000000000000001 (1)
00:00:03.892   Type      <string>  = "DVD" (cb=4)
00:00:03.892 
00:00:03.892 [/Devices/piix3ide/0/LUN#999/] (level 4)
00:00:03.892   Driver <string>  = "MainStatus" (cb=11)
00:00:03.892 
00:00:03.892 [/Devices/piix3ide/0/LUN#999/Config/] (level 5)
00:00:03.892   First   <integer> = 0x0000000000000000 (0)
00:00:03.892   Last    <integer> = 0x0000000000000003 (3)
00:00:03.892   papLeds <integer> = 0x0000000008ffb150 (150974800)
00:00:03.892 
00:00:03.892 [/Devices/serial/] (level 2)
00:00:03.892 
00:00:03.892 [/Devices/usb-ehci/] (level 2)
00:00:03.892 
00:00:03.892 [/Devices/usb-ehci/0/] (level 3)
00:00:03.892   PCIDeviceNo   <integer> = 0x000000000000000b (11)
00:00:03.892   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:03.892   Trusted       <integer> = 0x0000000000000001 (1)
00:00:03.892 
00:00:03.892 [/Devices/usb-ehci/0/Config/] (level 4)
00:00:03.892 
00:00:03.892 [/Devices/usb-ehci/0/LUN#0/] (level 4)
00:00:03.892   Driver <string>  = "VUSBRootHub" (cb=12)
00:00:03.892 
00:00:03.892 [/Devices/usb-ehci/0/LUN#0/Config/] (level 5)
00:00:03.892 
00:00:03.892 [/Devices/usb-ehci/0/LUN#999/] (level 4)
00:00:03.892   Driver <string>  = "MainStatus" (cb=11)
00:00:03.892 
00:00:03.892 [/Devices/usb-ehci/0/LUN#999/Config/] (level 5)
00:00:03.892   First   <integer> = 0x0000000000000000 (0)
00:00:03.892   Last    <integer> = 0x0000000000000000 (0)
00:00:03.892   papLeds <integer> = 0x0000000008ffb240 (150975040)
00:00:03.892 
00:00:03.892 [/Devices/usb-ohci/] (level 2)
00:00:03.893 
00:00:03.893 [/Devices/usb-ohci/0/] (level 3)
00:00:03.893   PCIDeviceNo   <integer> = 0x0000000000000006 (6)
00:00:03.893   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:03.893   Trusted       <integer> = 0x0000000000000001 (1)
00:00:03.893 
00:00:03.893 [/Devices/usb-ohci/0/Config/] (level 4)
00:00:03.893 
00:00:03.893 [/Devices/usb-ohci/0/LUN#0/] (level 4)
00:00:03.893   Driver <string>  = "VUSBRootHub" (cb=12)
00:00:03.893 
00:00:03.893 [/Devices/usb-ohci/0/LUN#0/Config/] (level 5)
00:00:03.893 
00:00:03.893 [/Devices/usb-ohci/0/LUN#999/] (level 4)
00:00:03.893   Driver <string>  = "MainStatus" (cb=11)
00:00:03.893 
00:00:03.893 [/Devices/usb-ohci/0/LUN#999/Config/] (level 5)
00:00:03.893   First   <integer> = 0x0000000000000000 (0)
00:00:03.893   Last    <integer> = 0x0000000000000000 (0)
00:00:03.893   papLeds <integer> = 0x0000000008ffb23c (150975036)
00:00:03.893 
00:00:03.893 [/Devices/vga/] (level 2)
00:00:03.893 
00:00:03.893 [/Devices/vga/0/] (level 3)
00:00:03.893   PCIDeviceNo   <integer> = 0x0000000000000002 (2)
00:00:03.893   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:03.893   Trusted       <integer> = 0x0000000000000001 (1)
00:00:03.893 
00:00:03.893 [/Devices/vga/0/Config/] (level 4)
00:00:03.893   CustomVideoModes <integer> = 0x0000000000000000 (0)
00:00:03.893   FadeIn           <integer> = 0x0000000000000001 (1)
00:00:03.893   FadeOut          <integer> = 0x0000000000000001 (1)
00:00:03.893   HeightReduction  <integer> = 0x0000000000000000 (0)
00:00:03.893   LogoFile         <string>  = "" (cb=1)
00:00:03.893   LogoTime         <integer> = 0x0000000000000000 (0)
00:00:03.893   MonitorCount     <integer> = 0x0000000000000001 (1)
00:00:03.893   ShowBootMenu     <integer> = 0x0000000000000002 (2)
00:00:03.893   VRamSize         <integer> = 0x0000000001000000 (16777216)
00:00:03.893 
00:00:03.893 [/Devices/vga/0/LUN#0/] (level 4)
00:00:03.893   Driver <string>  = "MainDisplay" (cb=12)
00:00:03.893 
00:00:03.893 [/Devices/vga/0/LUN#0/Config/] (level 5)
00:00:03.893   Object <integer> = 0x0000000008ffb810 (150976528)
00:00:03.893 
00:00:03.893 [/Devices/virtio-net/] (level 2)
00:00:03.893 
00:00:03.893 [/HWVirtExt/] (level 1)
00:00:03.893   64bitEnabled       <integer> = 0x0000000000000000 (0)
00:00:03.893   EnableNestedPaging <integer> = 0x0000000000000001 (1)
00:00:03.893   EnableVPID         <integer> = 0x0000000000000001 (1)
00:00:03.893   Enabled            <integer> = 0x0000000000000001 (1)
00:00:03.893   Exclusive          <integer> = 0x0000000000000001 (1)
00:00:03.893 
00:00:03.893 [/PDM/] (level 1)
00:00:03.893 
00:00:03.893 [/PDM/Drivers/] (level 2)
00:00:03.893 
00:00:03.893 [/PDM/Drivers/VBoxC/] (level 3)
00:00:03.893   Path <string>  = "/usr/lib/virtualbox/components/VBoxC" (cb=37)
00:00:03.893 
00:00:03.893 [/TM/] (level 1)
00:00:03.894   UTCOffset <integer> = 0x0000000000000000 (0)
00:00:03.894 
00:00:03.894 ********************* End of CFGM dump **********************
00:00:03.894 MM: cbHyperHeap=0x140000 (1310720)
00:00:03.896 Logical host processors: 2, processor active mask: 0000000000000003
00:00:03.896 ************************* CPUID dump ************************
00:00:03.896          RAW Standard CPUIDs
00:00:03.896      Function  eax      ebx      ecx      edx
00:00:03.896 Gst: 00000000  00000005 756e6547 6c65746e 49656e69
00:00:03.896 Hst:           0000000a 756e6547 6c65746e 49656e69
00:00:03.896 Gst: 00000001  000006ec 00000800 00000009 0789f1bf
00:00:03.896 Hst:           000006ec 01020800 0000c1a9 bfe9fbff
00:00:03.896 Gst: 00000002  02b3b001 000000f0 00000000 2c04307d
00:00:03.896 Hst:           02b3b001 000000f0 00000000 2c04307d
00:00:03.896 Gst: 00000003  00000000 00000000 00000000 00000000
00:00:03.896 Hst:           00000000 00000000 00000000 00000000
00:00:03.896 Gst: 00000004  00000000 00000000 00000000 00000000
00:00:03.896 Hst:           04000121 01c0003f 0000003f 00000001
00:00:03.896 Gst: 00000005  00000040 00000040 00000000 00000000
00:00:03.896 Hst:           00000040 00000040 00000003 00022220
00:00:03.896 Name:                            GenuineIntel
00:00:03.896 Supports:                        0-5
00:00:03.896 Family:                          6  	Extended: 0 	Effective: 6
00:00:03.896 Model:                           14  	Extended: 0 	Effective: 14
00:00:03.896 Stepping:                        12
00:00:03.896 Type:                            0
00:00:03.896 APIC ID:                         0x00
00:00:03.896 Logical CPUs:                    0
00:00:03.896 CLFLUSH Size:                    8
00:00:03.896 Brand ID:                        0x00
00:00:03.896 Mnemonic - Description                 = guest (host)
00:00:03.896 FPU - x87 FPU on Chip                  = 1 (1)
00:00:03.896 VME - Virtual 8086 Mode Enhancements   = 1 (1)
00:00:03.896 DE - Debugging extensions              = 1 (1)
00:00:03.896 PSE - Page Size Extension              = 1 (1)
00:00:03.896 TSC - Time Stamp Counter               = 1 (1)
00:00:03.896 MSR - Model Specific Registers         = 1 (1)
00:00:03.896 PAE - Physical Address Extension       = 0 (1)
00:00:03.896 MCE - Machine Check Exception          = 1 (1)
00:00:03.896 CX8 - CMPXCHG8B instruction            = 1 (1)
00:00:03.896 APIC - APIC On-Chip                    = 0 (1)
00:00:03.896 Reserved                               = 0 (0)
00:00:03.896 SEP - SYSENTER and SYSEXIT             = 0 (1)
00:00:03.896 MTRR - Memory Type Range Registers     = 1 (1)
00:00:03.896 PGE - PTE Global Bit                   = 1 (1)
00:00:03.896 MCA - Machine Check Architecture       = 1 (1)
00:00:03.896 CMOV - Conditional Move Instructions   = 1 (1)
00:00:03.896 PAT - Page Attribute Table             = 1 (1)
00:00:03.896 PSE-36 - 36-bit Page Size Extention    = 0 (0)
00:00:03.896 PSN - Processor Serial Number          = 0 (0)
00:00:03.896 CLFSH - CLFLUSH Instruction.           = 1 (1)
00:00:03.896 Reserved                               = 0 (0)
00:00:03.896 DS - Debug Store                       = 0 (1)
00:00:03.896 ACPI - Thermal Mon. & Soft. Clock Ctrl.= 0 (1)
00:00:03.896 MMX - Intel MMX Technology             = 1 (1)
00:00:03.896 FXSR - FXSAVE and FXRSTOR Instructions = 1 (1)
00:00:03.896 SSE - SSE Support                      = 1 (1)
00:00:03.896 SSE2 - SSE2 Support                    = 1 (1)
00:00:03.896 SS - Self Snoop                        = 0 (1)
00:00:03.896 HTT - Hyper-Threading Technolog        = 0 (1)
00:00:03.896 TM - Thermal Monitor                   = 0 (1)
00:00:03.896 30 - Reserved                          = 0 (0)
00:00:03.896 PBE - Pending Break Enable             = 0 (1)
00:00:03.896 Supports SSE3 or not                   = 1 (1)
00:00:03.896 Reserved                               = 0 (0)
00:00:03.896 DS Area 64-bit layout                  = 0 (0)
00:00:03.896 Supports MONITOR/MWAIT                 = 1 (1)
00:00:03.896 CPL-DS - CPL Qualified Debug Store     = 0 (0)
00:00:03.896 VMX - Virtual Machine Technology       = 0 (1)
00:00:03.896 SMX - Safer Mode Extensions            = 0 (0)
00:00:03.896 Enhanced SpeedStep Technology          = 0 (1)
00:00:03.896 Terminal Monitor 2                     = 0 (1)
00:00:03.896 Supports Supplemental SSE3 or not      = 0 (0)
00:00:03.896 L1 Context ID                          = 0 (0)
00:00:03.896 FMA                                    = 0 (0)
00:00:03.896 Reserved                               = 0 (0)
00:00:03.896 CMPXCHG16B                             = 0 (0)
00:00:03.896 xTPR Update Control                    = 0 (1)
00:00:03.896 Perf/Debug Capability MSR              = 0 (1)
00:00:03.896 Reserved                               = 0x0 (0x0)
00:00:03.896 Direct Cache Access                    = 0 (0)
00:00:03.897 Supports SSE4_1 or not                 = 0 (0)
00:00:03.897 Supports SSE4_2 or not                 = 0 (0)
00:00:03.897 Supports the x2APIC extensions         = 0 (0)
00:00:03.897 Supports MOVBE                         = 0 (0)
00:00:03.897 Supports POPCNT                        = 0 (0)
00:00:03.897 Reserved                               = 0x0 (0x0)
00:00:03.897 Supports XSAVE                         = 0 (0)
00:00:03.897 Supports OSXSAVE                       = 0 (0)
00:00:03.897 Reserved                               = 0x0 (0x0)
00:00:03.897 
00:00:03.897          RAW Extended CPUIDs
00:00:03.897      Function  eax      ebx      ecx      edx
00:00:03.897 Gst: 80000000  80000008 00000000 00000000 00000000
00:00:03.897 Hst:           80000008 00000000 00000000 00000000
00:00:03.897 Gst: 80000001  00000000 00000000 00000000 00000000
00:00:03.897 Hst:           00000000 00000000 00000000 00100000
00:00:03.897 Gst: 80000002  65746e49 2952286c 726f4320 4d542865
00:00:03.897 Hst:           65746e49 2952286c 726f4320 4d542865
00:00:03.897 Gst: 80000003  75442029 5043206f 20202055 4c202020
00:00:03.897 Hst:           75442029 5043206f 20202055 4c202020
00:00:03.897 Gst: 80000004  30303432 20402020 36362e31 007a4847
00:00:03.897 Hst:           30303432 20402020 36362e31 007a4847
00:00:03.897 Gst: 80000005  00000000 00000000 00000000 00000000
00:00:03.897 Hst:           00000000 00000000 00000000 00000000
00:00:03.897 Gst: 80000006  00000000 00000000 08006040 00000000
00:00:03.897 Hst:           00000000 00000000 08006040 00000000
00:00:03.897 Gst: 80000007  00000000 00000000 00000000 00000000
00:00:03.897 Hst:           00000000 00000000 00000000 00000000
00:00:03.897 Gst: 80000008  00002020 00000000 00000000 00000000
00:00:03.897 Hst:           00002020 00000000 00000000 00000000
00:00:03.897 Gst: 80000009  07280201 00000000 00000000 00000000*
00:00:03.897 Hst:           07280201 00000000 00000000 00000000
00:00:03.897 Ext Name:                        
00:00:03.897 Ext Supports:                    0x80000000-0x80000008
00:00:03.897 Family:                          0  	Extended: 0 	Effective: 0
00:00:03.897 Model:                           0  	Extended: 0 	Effective: 0
00:00:03.897 Stepping:                        0
00:00:03.897 Brand ID:                        0x000
00:00:03.897 Mnemonic - Description                 = guest (host)
00:00:03.897 FPU - x87 FPU on Chip                  = 0 (0)
00:00:03.897 VME - Virtual 8086 Mode Enhancements   = 0 (0)
00:00:03.897 DE - Debugging extensions              = 0 (0)
00:00:03.897 PSE - Page Size Extension              = 0 (0)
00:00:03.897 TSC - Time Stamp Counter               = 0 (0)
00:00:03.897 MSR - K86 Model Specific Registers     = 0 (0)
00:00:03.897 PAE - Physical Address Extension       = 0 (0)
00:00:03.897 MCE - Machine Check Exception          = 0 (0)
00:00:03.897 CX8 - CMPXCHG8B instruction            = 0 (0)
00:00:03.897 APIC - APIC On-Chip                    = 0 (0)
00:00:03.897 10 - Reserved                          = 0 (0)
00:00:03.897 SEP - SYSCALL and SYSRET               = 0 (0)
00:00:03.897 MTRR - Memory Type Range Registers     = 0 (0)
00:00:03.897 PGE - PTE Global Bit                   = 0 (0)
00:00:03.897 MCA - Machine Check Architecture       = 0 (0)
00:00:03.897 CMOV - Conditional Move Instructions   = 0 (0)
00:00:03.897 PAT - Page Attribute Table             = 0 (0)
00:00:03.897 PSE-36 - 36-bit Page Size Extention    = 0 (0)
00:00:03.897 18 - Reserved                          = 0 (0)
00:00:03.897 19 - Reserved                          = 0 (0)
00:00:03.897 NX - No-Execute Page Protection        = 0 (1)
00:00:03.897 DS - Debug Store                       = 0 (0)
00:00:03.897 AXMMX - AMD Extensions to MMX Instr.   = 0 (0)
00:00:03.897 MMX - Intel MMX Technology             = 0 (0)
00:00:03.897 FXSR - FXSAVE and FXRSTOR Instructions = 0 (0)
00:00:03.897 25 - AMD fast FXSAVE and FXRSTOR Instr.= 0 (0)
00:00:03.897 26 - 1 GB large page support           = 0 (0)
00:00:03.897 27 - RDTSCP instruction                = 0 (0)
00:00:03.897 28 - Reserved                          = 0 (0)
00:00:03.897 29 - AMD Long Mode                     = 0 (0)
00:00:03.897 30 - AMD Extensions to 3DNow           = 0 (0)
00:00:03.897 31 - AMD 3DNow                         = 0 (0)
00:00:03.897 LahfSahf - LAHF/SAHF in 64-bit mode    = 0 (0)
00:00:03.897 CmpLegacy - Core MP legacy mode (depr) = 0 (0)
00:00:03.897 SVM - AMD VM Extensions                = 0 (0)
00:00:03.897 APIC registers starting at 0x400       = 0 (0)
00:00:03.897 AltMovCR8 - LOCK MOV CR0 means MOV CR8 = 0 (0)
00:00:03.897 Advanced bit manipulation              = 0 (0)
00:00:03.897 SSE4A instruction support              = 0 (0)
00:00:03.897 Misaligned SSE mode                    = 0 (0)
00:00:03.897 PREFETCH and PREFETCHW instruction     = 0 (0)
00:00:03.897 OS visible workaround                  = 0 (0)
00:00:03.897 Instruction based sampling             = 0 (0)
00:00:03.897 SSE5 support                           = 0 (0)
00:00:03.897 SKINIT, STGI, and DEV support          = 0 (0)
00:00:03.897 Watchdog timer support.                = 0 (0)
00:00:03.897 31:14 - Reserved                       = 0x0 (0x0)
00:00:03.897 Full Name:                       Intel(R) Core(TM) Duo CPU      L2400  @ 1.66GHz
00:00:03.897 TLB 2/4M Instr/Uni:              res0     0 entries
00:00:03.897 TLB 2/4M Data:                   res0     0 entries
00:00:03.897 TLB 4K Instr/Uni:                res0     0 entries
00:00:03.897 TLB 4K Data:                     res0     0 entries
00:00:03.897 L1 Instr Cache Line Size:        0 bytes
00:00:03.897 L1 Instr Cache Lines Per Tag:    0
00:00:03.897 L1 Instr Cache Associativity:    res0  
00:00:03.897 L1 Instr Cache Size:             0 KB
00:00:03.897 L1 Data Cache Line Size:         0 bytes
00:00:03.897 L1 Data Cache Lines Per Tag:     0
00:00:03.897 L1 Data Cache Associativity:     res0  
00:00:03.897 L1 Data Cache Size:              0 KB
00:00:03.897 L2 TLB 2/4M Instr/Uni:           off       0 entries
00:00:03.897 L2 TLB 2/4M Data:                off       0 entries
00:00:03.897 L2 TLB 4K Instr/Uni:             off       0 entries
00:00:03.897 L2 TLB 4K Data:                  off       0 entries
00:00:03.897 L2 Cache Line Size:              0 bytes
00:00:03.897 L2 Cache Lines Per Tag:          0
00:00:03.897 L2 Cache Associativity:          off   
00:00:03.897 L2 Cache Size:                   0 KB
00:00:03.897 APM Features:                   
00:00:03.897 Physical Address Width:          32 bits
00:00:03.897 Virtual Address Width:           32 bits
00:00:03.897 Physical Core Count:             0
00:00:03.897 
00:00:03.897          RAW Centaur CPUIDs
00:00:03.897      Function  eax      ebx      ecx      edx
00:00:03.897 Gst: c0000000  07280201 00000000 00000000 00000000
00:00:03.897 Hst:           07280201 00000000 00000000 00000000
00:00:03.897 Gst: c0000001  07280201 00000000 00000000 00000000
00:00:03.897 Hst:           07280201 00000000 00000000 00000000
00:00:03.897 Gst: c0000002  07280201 00000000 00000000 00000000
00:00:03.897 Hst:           07280201 00000000 00000000 00000000
00:00:03.897 Gst: c0000003  07280201 00000000 00000000 00000000
00:00:03.897 Hst:           07280201 00000000 00000000 00000000
00:00:03.897 Centaur Supports:                0xc0000000-0x07280201
00:00:03.897 Mnemonic - Description                 = guest (host)
00:00:03.897 AIS - Alternate Instruction Set        = 0 (0)
00:00:03.897 AIS-E - AIS enabled                    = 0 (0)
00:00:03.897 RNG - Random Number Generator          = 0 (0)
00:00:03.897 RNG-E - RNG enabled                    = 0 (0)
00:00:03.897 LH - LongHaul MSR 0000_110Ah           = 0 (0)
00:00:03.897 FEMMS - FEMMS                          = 0 (0)
00:00:03.897 ACE - Advanced Cryptography Engine     = 0 (0)
00:00:03.897 ACE-E - ACE enabled                    = 0 (0)
00:00:03.897 ACE2 - Advanced Cryptography Engine 2  = 0 (0)
00:00:03.897 ACE2-E - ACE enabled                   = 0 (0)
00:00:03.898 PHE - Hash Engine                      = 0 (0)
00:00:03.898 PHE-E - PHE enabled                    = 0 (0)
00:00:03.898 PMM - Montgomery Multiplier            = 0 (0)
00:00:03.898 PMM-E - PMM enabled                    = 0 (0)
00:00:03.898 
00:00:03.898 
00:00:03.898 ******************** End of CPUID dump **********************
00:00:03.909 REM: VBoxREM32
00:00:03.942 TM: GIP - u32Mode=1 (SyncTSC) u32UpdateHz=83
00:00:03.974 TM: cTSCTicksPerSecond=0x62aeef5e (1 655 631 710) fTSCVirtualized=true  fTSCUseRealTSC=false
00:00:03.974 TM: fMaybeUseOffsettedHostTSC=true  TSCTiedToExecution=false TSCNotTiedToHalt=false
00:00:03.975 CoreCode: R3=00e78000 R0=fb52f000 RC=a03c5000 Phys=0000000035220000 cb=0x2000
00:00:03.980 AIOMgr: Cache was globally disabled
00:00:03.980 AIOMgr: I/O bandwidth not limited
00:00:03.985 [SMP] BIOS with 1 CPUs
00:00:04.024 SUP: Loaded VBoxDDR0.r0 (/usr/lib/virtualbox/VBoxDDR0.r0) at 0xfb5a5060 - ModuleInit at 0000000000000000 and ModuleTerm at 0000000000000000
00:00:04.033 SUP: Loaded VBoxDD2R0.r0 (/usr/lib/virtualbox/VBoxDD2R0.r0) at 0xfb5d1060 - ModuleInit at 0000000000000000 and ModuleTerm at 0000000000000000
00:00:04.033 Activating Local APIC
00:00:04.033 CPUMSetGuestCpuIdFeature: Enabled APIC
00:00:04.033 CPUMSetGuestCpuIdFeature: Disabled x2APIC
00:00:04.034 PIT: mode=3 count=0x10000 (65536) - 18.20 Hz (ch=0)
00:00:04.043 Shared Folders service loaded.
00:00:04.081 VDInit finished
00:00:04.081 PIIX3 ATA: LUN#0: disk, PCHS=16383/16/63, total number of sectors 18874368
00:00:04.081 PIIX3 ATA: LUN#1: no unit
00:00:04.081 PIIX3 ATA: LUN#2: CD/DVD, total number of sectors 14675, passthrough disabled
00:00:04.081 PIIX3 ATA: LUN#3: no unit
00:00:04.082 PIIX3 ATA: Ctl#1: finished processing RESET
00:00:04.082 PIIX3 ATA: Ctl#0: finished processing RESET
00:00:04.083 NAT: adding domain name westell.com to search list
00:00:04.083 NAT: value of BindIP has been ignored
00:00:04.083 Audio: Trying driver 'pulse'.
00:00:04.089 Audio: set_record_source ars=0 als=0 (not implemented)
00:00:04.090 Pulse: open PCM_IN rate=44100Hz channels=2 format=s16le
00:00:04.090 Pulse: Requested record buffer attributes: maxlength=26460 fragsize=17640
00:00:04.111 Pulse:  Obtained record buffer attributes: maxlength=26460 fragsize=8820
00:00:04.111 Pulse: open PCM_OUT rate=44100Hz channels=2 format=s16le
00:00:04.111 Pulse: Requested playback buffer attributes: maxlength=26460 tlength=17640 prebuf=-1 minreq=-1
00:00:04.152 Pulse:  Obtained playback buffer attributes: maxlength=26460 tlength=12348 prebuf=8824 minreq=3528
00:00:04.158 DevPcBios: ATA LUN#0 LCHS=1024/255/63
00:00:04.158 PGMR3InitFinalize: 4 MB PSE mask 00000000ffffffff
00:00:04.192 HWACCM: No VT-x or AMD-V CPU extension found. Reason VERR_VMX_MSR_LOCKED_OR_DISABLED
00:00:04.192 HWACCM: VMX MSR_IA32_FEATURE_CONTROL=1
00:00:04.226 VM: Halt method global1 (5)
00:00:04.226 Changing the VM state from 'CREATING' to 'CREATED'.
00:00:04.226 Changing the VM state from 'CREATED' to 'POWERING_ON'.
00:00:04.227 Changing the VM state from 'POWERING_ON' to 'RUNNING'.
00:00:04.266 Guest Log: BIOS: VirtualBox 3.1.8
00:00:04.267 PIT: mode=2 count=0x10000 (65536) - 18.20 Hz (ch=0)
00:00:04.425 PIIX3 ATA: Ctl#0: RESET, DevSel=0 AIOIf=0 CmdIf0=0x00 (-1 usec ago) CmdIf1=0x00 (-1 usec ago)
00:00:04.425 PIIX3 ATA: Ctl#0: finished processing RESET
00:00:04.429 Guest Log: BIOS: ata0-0: PCHS=16383/16/63 LCHS=1024/255/63
00:00:04.432 PIIX3 ATA: Ctl#1: RESET, DevSel=0 AIOIf=0 CmdIf0=0x00 (-1 usec ago) CmdIf1=0x00 (-1 usec ago)
00:00:04.432 PIIX3 ATA: Ctl#1: finished processing RESET
00:00:04.434 PIT: mode=2 count=0x48d3 (18643) - 64.00 Hz (ch=0)
00:00:04.450 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=b3974000 w=640 h=480 bpp=32 cbLine=0xA00
00:00:06.953 PIT: mode=2 count=0x10000 (65536) - 18.20 Hz (ch=0)
00:00:06.955 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=00000000 w=720 h=400 bpp=0 cbLine=0x0
00:00:06.970 Guest Log: BIOS: Boot from Floppy 0 failed
00:00:06.975 Guest Log: BIOS: CDROM boot failure code : 0004
00:00:06.976 Guest Log: BIOS: Boot from CD-ROM failed
00:00:06.979 Guest Log: BIOS: Booting from Hard Disk...
00:00:07.329 Guest Log: BIOS: int13_harddisk: function 15, unmapped device for ELDL=81
00:00:12.315 PIT: mode=2 count=0x2ead (11949) - 99.85 Hz (ch=0)
00:00:12.713 CPUMSetGuestCpuIdFeature: Disabled x2APIC
00:00:12.745 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=b3974000 w=640 h=480 bpp=0 cbLine=0x140
00:00:14.728 PIIX3 ATA: LUN#0: IDLE IMMEDIATE, CmdIf=0xef (-1 usec ago)
00:00:14.728 PIIX3 ATA: LUN#0: aborting current command
00:00:15.814 Guest Additions information report: additionsVersion = 0x00010004  osType = 0x00033000
00:00:17.901 Guest reported fixed hypervisor window at 0xf7400000 (size = 0x800000, rc = VINF_SUCCESS)
00:00:18.019 EHCI: Hardware reset
00:00:18.019 EHCI: USB Operational
00:00:18.209 OHCI: Software reset
00:00:18.209 OHCI: USB Reset
00:00:18.209 OHCI: USB Operational
00:00:18.214 Guest Log: VBoxVideo: using HGSMI
00:00:18.286 PCNet#0: Init: ss32=1 GCRDRA=0x02246420[64] GCTDRA=0x02246020[64]
00:00:19.316 Audio: set_record_source ars=0 als=0 (not implemented)
00:00:19.319 Audio: set_record_source ars=0 als=0 (not implemented)
00:00:19.475 SharedFolders host service: connected, u32ClientID = 1
00:00:20.053 PCNet#0: Init: ss32=1 GCRDRA=0x02246420[64] GCTDRA=0x02246020[64]
00:00:20.592 EHCI: USB Suspended
00:00:20.831 OHCI: USB Suspended
00:00:22.126 Guest requests the VM to be turned off
00:00:22.126 Changing the VM state from 'RUNNING' to 'POWERING_OFF'.
00:00:22.126 ****************** Guest state at power off ******************
00:00:22.126 Guest CPUM (VCPU 0) state: se
00:00:22.126 eax=0236006c ebx=821f8008 ecx=00000000 edx=0000d040 esi=8236006c edi=00000000
00:00:22.126 eip=f8438011 esp=f898fc94 ebp=f898fc9c iopl=0      rf nv up ei pl nz na po nc
00:00:22.126 cs={0008 base=0000000000000000 limit=ffffffff flags=0000c09a} dr0=00000000 dr1=00000000
00:00:22.126 ds={0023 base=0000000000000000 limit=ffffffff flags=0000c0f3} dr2=00000000 dr3=00000000
00:00:22.126 es={0023 base=0000000000000000 limit=ffffffff flags=0000c0f3} dr4=00000000 dr5=00000000
00:00:22.126 fs={0030 base=00000000ffdff000 limit=00001fff flags=0000c093} dr6=ffff0ff0 dr7=00000000
00:00:22.126 gs={0000 base=0000000000000000 limit=0000ffff flags=000000f3} cr0=e001003b cr2=806f5790
00:00:22.126 ss={0010 base=0000000000000000 limit=ffffffff flags=0000c093} cr3=00039000 cr4=000006d9
00:00:22.126 gdtr=000000008003f000:03ff  idtr=000000008003f400:07ff  eflags=00010246
00:00:22.126 ldtr={0000 base=00000000 limit=00000000 flags=00000082}
00:00:22.126 tr  ={0028 base=80042000 limit=000020ab flags=0000008b}
00:00:22.126 SysEnter={cs=0000 eip=00000000 esp=00000000}
00:00:22.126 FCW=027f FSW=0000 FTW=0000 FOP=023f MXCSR=00001f80 MXCSR_MASK=0000ffff
00:00:22.126 FPUIP=00000000 CS=0000 Rsvrd1=0000  FPUDP=00000000 DS=0000 Rsvrd2=0000
00:00:22.126 ST(0)=FPR0={f5ac'f8c15000'00111000} t0 -1.0008701323915987849216 ^ 30124
00:00:22.126 ST(1)=FPR1={f5ac'f8c15000'00111000} t0 -1.0008701323915987849216 ^ 30124
00:00:22.126 ST(2)=FPR2={f5ac'f8c15000'00111000} t0 -1.0008701323915987849216 ^ 30124
00:00:22.126 ST(3)=FPR3={f5ac'f8c15000'00111000} t0 -1.0008701323915987849216 ^ 30124
00:00:22.126 ST(4)=FPR4={f5ac'f8c15000'00111000} t0 -1.0008701323915987849216 ^ 30124
00:00:22.126 ST(5)=FPR5={f5ac'f8c15000'00111000} t0 -1.0008701323915987849216 ^ 30124
00:00:22.126 ST(6)=FPR6={f5ac'f8c15000'00111000} t0 -1.0008701323915987849216 ^ 30124
00:00:22.126 ST(7)=FPR7={f5ac'f8c15000'00111000} t0 -1.0008701323915987849216 ^ 30124
00:00:22.126 XMM0 =00000032'00000001'00000159'00000004  XMM1 =00000000'822b38c8'823c89c8'f896f640
00:00:22.126 XMM2 =00000001'07ef7000'00000000'822e2190  XMM3 =00000001'00000000'822e2218'00000000
00:00:22.126 XMM4 =00000000'7ffd9014'00000000'00000000  XMM5 =f896f410'00000000'f896f7f0'00000000
00:00:22.126 XMM6 =804e24a0'f896f6e4'80564ba5'f896f404  XMM7 =80574c7c'80574f52'ffffffff'804f1618
00:00:22.126 XMM8 =00000000'00000000'00000000'00000000  XMM9 =00000000'00000000'00000000'00000000
00:00:22.126 XMM10=00000000'00000000'00000000'00000000  XMM11=00000000'00000000'00000000'00000000
00:00:22.126 XMM12=00000000'00000000'00000000'00000000  XMM13=00000000'00000000'00000000'00000000
00:00:22.126 XMM14=00000000'00000000'00000000'00000000  XMM15=00000000'00000000'00000000'00000000
00:00:22.126 EFER         =0000000000000000
00:00:22.126 PAT          =0007010600070106
00:00:22.126 STAR         =0000000000000000
00:00:22.126 CSTAR        =0000000000000000
00:00:22.126 LSTAR        =0000000000000000
00:00:22.126 SFMASK       =0000000000000000
00:00:22.126 KERNELGSBASE =0000000000000000
00:00:22.126 ***
00:00:22.126 Guest paging mode:  32-bit, changed 2010 times, A20 enabled
00:00:22.126 Shadow paging mode: 32-bit
00:00:22.126 Host paging mode:   32-bit+G
00:00:22.126 ***
00:00:22.126 Active Timers (pVM=b597c000)
00:00:22.126 pTimerR3 offNext  offPrev  offSched Clock Time               Expire             State                     Description
00:00:22.126 07b64210 00008460 00000000 00000000 Real  000000000020903860 000000000020903868 2-ACTIVE                  VGA Refresh Timer
00:00:22.126 07b6c670 00000000 ffff7ba0 00000000 Real  000000000020903860 000000000020903882 2-ACTIVE                  EMT Yielder
00:00:22.126 07b689f0 00000000 00000000 00000000 Virt  000000017896512594 000000017904760861 2-ACTIVE                  Audio timer
00:00:22.126 07b5e6b0 000003a0 00000000 00000000 VrSy  000000017895710401 000000017900987112 2-ACTIVE                  i8254 Programmable Interval Timer
00:00:22.126 07b5ea50 0000d240 fffffc60 00000000 VrSy  000000017895811583 000000017990000000 2-ACTIVE                  MC146818 RTC/CMOS - Second
00:00:22.126 07b6bc90 00000000 ffff2dc0 00000000 VrSy  000000017895903609 000001199864031601 2-ACTIVE                  ACPI Timer
00:00:22.126 ***
00:00:22.126 Shadow GDT (GCAddr=f77c8000):
00:00:22.126 0008 - 0000ffff 00cfbb00 - base=00000000 limit=ffffffff dpl=1 CodeER Accessed Present Page 32-bit 
00:00:22.126 0010 - 0000ffff 00cfb300 - base=00000000 limit=ffffffff dpl=1 DataRW Accessed Present Page 32-bit 
00:00:22.126 0018 - 0000ffff 00cffb00 - base=00000000 limit=ffffffff dpl=3 CodeER Accessed Present Page 32-bit 
00:00:22.126 0020 - 0000ffff 00cff300 - base=00000000 limit=ffffffff dpl=3 DataRW Accessed Present Page 32-bit 
00:00:22.126 0030 - f0000001 ffc0b3df - base=ffdff000 limit=00001fff dpl=1 DataRW Accessed Present Page 32-bit 
00:00:22.126 0038 - 00000fff 0040f300 - base=00000000 limit=00000fff dpl=3 DataRW Accessed Present 32-bit 
00:00:22.126 0040 - 0400ffff 0000f300 - base=00000400 limit=0000ffff dpl=3 DataRW Accessed Present 16-bit 
00:00:22.127 0060 - 2f40ffff 0000b302 - base=00022f40 limit=0000ffff dpl=1 DataRW Accessed Present 16-bit 
00:00:22.127 0068 - 80003fff 0000b30b - base=000b8000 limit=00003fff dpl=1 DataRW Accessed Present 16-bit 
00:00:22.127 0070 - 700003ff ff00b3ff - base=ffff7000 limit=000003ff dpl=1 DataRW Accessed Present 16-bit 
00:00:22.127 0078 - 0000ffff 8000bb40 - base=80400000 limit=0000ffff dpl=1 CodeER Accessed Present 16-bit 
00:00:22.127 0080 - 0000ffff 8000b340 - base=80400000 limit=0000ffff dpl=1 DataRW Accessed Present 16-bit 
00:00:22.127 0088 - 00000000 0000b300 - base=00000000 limit=00000000 dpl=1 DataRW Accessed Present 16-bit 
00:00:22.127 00e8 - 0000ffff 0000b300 - base=00000000 limit=0000ffff dpl=1 DataRW Accessed Present 16-bit 
00:00:22.127 00f0 - 8b2884e7 8003b94d - base=804d8b28 limit=000384e7 dpl=1 CodeEO Accessed Present 16-bit 
00:00:22.127 00f8 - 0000ffff 0000b300 - base=00000000 limit=0000ffff dpl=1 DataRW Accessed Present 16-bit 
00:00:22.127 ffd8 - 80d80087 f7008940 - base=f74080d8 limit=00000087 dpl=0 TSS32Avail Present 16-bit  HyperTSSTrap08
00:00:22.127 ffe0 - 80500087 f7008b40 - base=f7408050 limit=00000087 dpl=0 TSS32Busy Present 16-bit  HyperTSS
00:00:22.127 ffe8 - 0000ffff 00af9b00 - base=00000000 limit=ffffffff dpl=0 CodeER Accessed Present Page 16-bit  HyperCS64
00:00:22.127 fff0 - 0000ffff 00cf9300 - base=00000000 limit=ffffffff dpl=0 DataRW Accessed Present Page 32-bit  HyperDS
00:00:22.127 fff8 - 0000ffff 00cf9b00 - base=00000000 limit=ffffffff dpl=0 CodeER Accessed Present Page 32-bit  HyperCS
00:00:22.127 ***
00:00:22.127 ************** End of Guest state at power off ***************
00:00:22.590 Changing the VM state from 'POWERING_OFF' to 'OFF'.
00:00:22.591 Console::powerDown(): A request to power off the VM has been issued (mMachineState=Stopping, InUninit=0)
00:00:22.597 SharedFolders host service: disconnected, u32ClientID = 1
00:00:22.597 Changing the VM state from 'OFF' to 'DESTROYING'.
00:00:22.597 ************************* Statistics *************************
00:00:22.598 /Devices/IDE0/ATA0/Unit0/AtapiDMA        0 times
00:00:22.598 /Devices/IDE0/ATA0/Unit0/AtapiPIO        0 times
00:00:22.598 /Devices/IDE0/ATA0/Unit0/DMA         3016 times
00:00:22.598 /Devices/IDE0/ATA0/Unit0/PIO         1517 times
00:00:22.598 /Devices/IDE0/ATA0/Unit0/ReadBytes 135374848 bytes
00:00:22.598 /Devices/IDE0/ATA0/Unit0/WrittenBytes   322560 bytes
00:00:22.598 /Devices/IDE0/ATA0/Unit1/AtapiDMA        0 times
00:00:22.598 /Devices/IDE0/ATA0/Unit1/AtapiPIO        0 times
00:00:22.598 /Devices/IDE0/ATA0/Unit1/DMA            0 times
00:00:22.598 /Devices/IDE0/ATA0/Unit1/PIO            0 times
00:00:22.598 /Devices/IDE0/ATA0/Unit1/ReadBytes        0 bytes
00:00:22.598 /Devices/IDE0/ATA0/Unit1/WrittenBytes        0 bytes
00:00:22.598 /Devices/IDE0/ATA1/Unit0/AtapiDMA        1 times
00:00:22.598 /Devices/IDE0/ATA1/Unit0/AtapiPIO       19 times
00:00:22.598 /Devices/IDE0/ATA1/Unit0/DMA            0 times
00:00:22.598 /Devices/IDE0/ATA1/Unit0/PIO            0 times
00:00:22.598 /Devices/IDE0/ATA1/Unit0/ReadBytes     2048 bytes
00:00:22.598 /Devices/IDE0/ATA1/Unit0/WrittenBytes        0 bytes
00:00:22.598 /Devices/IDE0/ATA1/Unit1/AtapiDMA        0 times
00:00:22.598 /Devices/IDE0/ATA1/Unit1/AtapiPIO        0 times
00:00:22.598 /Devices/IDE0/ATA1/Unit1/DMA            0 times
00:00:22.598 /Devices/IDE0/ATA1/Unit1/PIO            0 times
00:00:22.598 /Devices/IDE0/ATA1/Unit1/ReadBytes        0 bytes
00:00:22.598 /Devices/IDE0/ATA1/Unit1/WrittenBytes        0 bytes
00:00:22.598 /Devices/PCNet0/ReceiveBytes            0 bytes
00:00:22.598 /Devices/PCNet0/TransmitBytes           0 bytes
00:00:22.598 /GVMM/EMTs                              1 calls
00:00:22.598 /GVMM/Sum/HaltBlocking               1672 calls
00:00:22.598 /GVMM/Sum/HaltCalls                 17815 calls
00:00:22.598 /GVMM/Sum/HaltNotBlocking           16143 calls
00:00:22.598 /GVMM/Sum/HaltTimeouts               1009 calls
00:00:22.598 /GVMM/Sum/HaltWakeUps                   0 calls
00:00:22.598 /GVMM/Sum/PokeCalls                   422 calls
00:00:22.598 /GVMM/Sum/PokeNotBusy                   4 calls
00:00:22.598 /GVMM/Sum/PollCalls                    15 calls
00:00:22.598 /GVMM/Sum/PollHalts                     0 calls
00:00:22.598 /GVMM/Sum/PollWakeUps                   0 calls
00:00:22.598 /GVMM/Sum/WakeUpCalls                1424 calls
00:00:22.598 /GVMM/Sum/WakeUpNotHalted            1125 calls
00:00:22.598 /GVMM/Sum/WakeUpWakeUps                 0 calls
00:00:22.598 /GVMM/VM/HaltBlocking                1672 calls
00:00:22.598 /GVMM/VM/HaltCalls                  17815 calls
00:00:22.598 /GVMM/VM/HaltNotBlocking            16143 calls
00:00:22.598 /GVMM/VM/HaltTimeouts                1009 calls
00:00:22.598 /GVMM/VM/HaltWakeUps                    0 calls
00:00:22.598 /GVMM/VM/PokeCalls                    422 calls
00:00:22.598 /GVMM/VM/PokeNotBusy                    4 calls
00:00:22.598 /GVMM/VM/PollCalls                     15 calls
00:00:22.598 /GVMM/VM/PollHalts                      0 calls
00:00:22.598 /GVMM/VM/PollWakeUps                    0 calls
00:00:22.598 /GVMM/VM/WakeUpCalls                 1424 calls
00:00:22.598 /GVMM/VM/WakeUpNotHalted             1125 calls
00:00:22.598 /GVMM/VM/WakeUpWakeUps                  0 calls
00:00:22.598 /GVMM/VMs                               1 calls
00:00:22.598 /MM/HyperHeap/cbFree              1011408 bytes
00:00:22.598 /MM/HyperHeap/cbHeap              1310464 bytes
00:00:22.598 /PDM/CritSects/ATA0/ContentionR3        0 times
00:00:22.598 /PDM/CritSects/ATA0/ContentionRZLock        0 times
00:00:22.598 /PDM/CritSects/ATA0/ContentionRZUnlock        0 times
00:00:22.598 /PDM/CritSects/ATA1/ContentionR3        0 times
00:00:22.598 /PDM/CritSects/ATA1/ContentionRZLock        0 times
00:00:22.598 /PDM/CritSects/ATA1/ContentionRZUnlock        0 times
00:00:22.598 /PDM/CritSects/EM-REM/ContentionR3        0 times
00:00:22.598 /PDM/CritSects/EM-REM/ContentionRZLock        0 times
00:00:22.598 /PDM/CritSects/EM-REM/ContentionRZUnlock        0 times
00:00:22.598 /PDM/CritSects/IOM EMT Lock/ContentionR3        0 times
00:00:22.598 /PDM/CritSects/IOM EMT Lock/ContentionRZLock        0 times
00:00:22.598 /PDM/CritSects/IOM EMT Lock/ContentionRZUnlock        0 times
00:00:22.598 /PDM/CritSects/MM-HYPER/ContentionR3        0 times
00:00:22.598 /PDM/CritSects/MM-HYPER/ContentionRZLock        0 times
00:00:22.598 /PDM/CritSects/MM-HYPER/ContentionRZUnlock        0 times
00:00:22.598 /PDM/CritSects/PCNet#0/ContentionR3        0 times
00:00:22.598 /PDM/CritSects/PCNet#0/ContentionRZLock        0 times
00:00:22.598 /PDM/CritSects/PCNet#0/ContentionRZUnlock        0 times
00:00:22.598 /PDM/CritSects/PDM/ContentionR3         0 times
00:00:22.598 /PDM/CritSects/PDM/ContentionRZLock        4 times
00:00:22.598 /PDM/CritSects/PDM/ContentionRZUnlock        0 times
00:00:22.598 /PDM/CritSects/PGM/ContentionR3         0 times
00:00:22.598 /PDM/CritSects/PGM/ContentionRZLock      222 times
00:00:22.598 /PDM/CritSects/PGM/ContentionRZUnlock      760 times
00:00:22.598 /PDM/CritSects/PS2KM#0/ContentionR3        0 times
00:00:22.598 /PDM/CritSects/PS2KM#0/ContentionRZLock        0 times
00:00:22.598 /PDM/CritSects/PS2KM#0/ContentionRZUnlock        0 times
00:00:22.598 /PDM/CritSects/REM-Register/ContentionR3        0 times
00:00:22.598 /PDM/CritSects/REM-Register/ContentionRZLock        0 times
00:00:22.598 /PDM/CritSects/REM-Register/ContentionRZUnlock        0 times
00:00:22.598 /PDM/CritSects/TM Timer Lock/ContentionR3        0 times
00:00:22.598 /PDM/CritSects/TM Timer Lock/ContentionRZLock        0 times
00:00:22.598 /PDM/CritSects/TM Timer Lock/ContentionRZUnlock        0 times
00:00:22.598 /PDM/CritSects/TM VirtualSync Lock/ContentionR3        0 times
00:00:22.598 /PDM/CritSects/TM VirtualSync Lock/ContentionRZLock        0 times
00:00:22.598 /PDM/CritSects/TM VirtualSync Lock/ContentionRZUnlock        0 times
00:00:22.598 /PDM/CritSects/VGA/ContentionR3         0 times
00:00:22.598 /PDM/CritSects/VGA/ContentionRZLock        0 times
00:00:22.598 /PDM/CritSects/VGA/ContentionRZUnlock        0 times
00:00:22.598 /PDM/CritSects/VMMDev/ContentionR3        0 times
00:00:22.598 /PDM/CritSects/VMMDev/ContentionRZLock        0 times
00:00:22.598 /PDM/CritSects/VMMDev/ContentionRZUnlock        0 times
00:00:22.598 /PDM/Queue/DevHlp/AllocFailures         0 times
00:00:22.598 /PDM/Queue/DevHlp/Flush                 0 calls
00:00:22.598 /PDM/Queue/DevHlp/FlushLeftovers        0 times
00:00:22.598 /PDM/Queue/DevHlp/Insert                0 calls
00:00:22.598 /PDM/Queue/DevHlp/cItems                8 count
00:00:22.598 /PDM/Queue/DevHlp/cbItem               32 bytes
00:00:22.598 /PDM/Queue/Keyboard/AllocFailures        0 times
00:00:22.598 /PDM/Queue/Keyboard/Flush               0 calls
00:00:22.598 /PDM/Queue/Keyboard/FlushLeftovers        0 times
00:00:22.598 /PDM/Queue/Keyboard/Insert              0 calls
00:00:22.598 /PDM/Queue/Keyboard/cItems             64 count
00:00:22.598 /PDM/Queue/Keyboard/cbItem             16 bytes
00:00:22.598 /PDM/Queue/Mouse/AllocFailures          0 times
00:00:22.598 /PDM/Queue/Mouse/Flush                  0 calls
00:00:22.598 /PDM/Queue/Mouse/FlushLeftovers         0 times
00:00:22.598 /PDM/Queue/Mouse/Insert                 1 calls
00:00:22.598 /PDM/Queue/Mouse/cItems               128 count
00:00:22.598 /PDM/Queue/Mouse/cbItem                32 bytes
00:00:22.598 /PDM/Queue/PCNet-Rcv/AllocFailures        0 times
00:00:22.598 /PDM/Queue/PCNet-Rcv/Flush              0 calls
00:00:22.598 /PDM/Queue/PCNet-Rcv/FlushLeftovers        0 times
00:00:22.598 /PDM/Queue/PCNet-Rcv/Insert             0 calls
00:00:22.598 /PDM/Queue/PCNet-Rcv/cItems             1 count
00:00:22.598 /PDM/Queue/PCNet-Rcv/cbItem            16 bytes
00:00:22.598 /PDM/Queue/PCNet-Xmit/AllocFailures        0 times
00:00:22.598 /PDM/Queue/PCNet-Xmit/Flush             0 calls
00:00:22.598 /PDM/Queue/PCNet-Xmit/FlushLeftovers        0 times
00:00:22.598 /PDM/Queue/PCNet-Xmit/Insert            0 calls
00:00:22.598 /PDM/Queue/PCNet-Xmit/cItems            1 count
00:00:22.598 /PDM/Queue/PCNet-Xmit/cbItem           16 bytes
00:00:22.598 /PGM/CPU0/cGuestModeChanges          2010 times
00:00:22.598 /PGM/ChunkR3Map/c                     128 count
00:00:22.598 /PGM/ChunkR3Map/cMax             4294967295 count
00:00:22.598 /PGM/Page/cAllPages                136399 count
00:00:22.598 /PGM/Page/cHandyPages                  76 count
00:00:22.598 /PGM/Page/cMonitoredPages               0 count
00:00:22.598 /PGM/Page/cPrivatePages             37744 count
00:00:22.598 /PGM/Page/cReadLockedPages              0 count
00:00:22.598 /PGM/Page/cSharedPages                  0 count
00:00:22.598 /PGM/Page/cWriteLockedPages             0 count
00:00:22.598 /PGM/Page/cWrittenToPages               0 count
00:00:22.598 /PGM/Page/cZeroPages                98655 count
00:00:22.598 /PGM/cRelocations                       2 times
00:00:22.598 /PROF/CPU0/EM/ForcedActions         19363 times
00:00:22.598 /PROF/CPU0/EM/Halted                  649 times
00:00:22.598 /PROF/CPU0/EM/RAWTotal               1056 times
00:00:22.598 /PROF/CPU0/EM/REMTotal                278 times
00:00:22.598 /PROF/CPU0/EM/Total              30525266770 ticks/call ( 30525266770 ticks,       1 times, max 30525266770, min 30525266770)
00:00:22.599 /PROF/VM/CPU0/Halt/Block           574121 ticks/call ( 10226254440 ticks,   17812 times, max  21619530, min    2520)
00:00:22.599 /PROF/VM/CPU0/Halt/Timers           17203 ticks/call (   372035680 ticks,   21626 times, max  14691390, min    1940)
00:00:22.599 /PROF/VM/CPU0/Halt/Yield             7526 ticks/call (      112900 ticks,      15 times, max     20070, min    4170)
00:00:22.599 /REM/TbFlushCount                      66 times
00:00:22.599 /REM/TbPhysInvldCount                1569 times
00:00:22.599 /REM/TlbFlushCount                   4089 times
00:00:22.599 /TM/R3/1nsSteps                       426 times
00:00:22.599 /TM/RC/1nsSteps                       256 times
00:00:22.599 /TM/TSC/offCPU0                         0 ticks
00:00:22.599 /TM/VirtualSync/CurrentOffset      660266 ns
00:00:22.599 /VUSB/0/cUrbsInPool                     0 count
00:00:22.599 /VUSB/1/cUrbsInPool                     0 count
00:00:22.599 ********************* End of statistics **********************
00:00:22.613 Changing the VM state from 'DESTROYING' to 'TERMINATED'.

```

---

### Post by discord on 2010-05-10
It looks to me like 

```
00:00:22.126 Guest requests the VM to be turned off
00:00:22.126 Changing the VM state from 'RUNNING' to 'POWERING_OFF'.

```

is the source of my problems, any suggestions?

---

### Post by Matti L on 2010-05-11
I installed Ubuntu 10.04 last Sunday and my Windows XP SP3 is still running fine on VirtualBox 3.1.6 and can't help with any VirtualBox problems but if the problem is with Windows then here's somethings you could try out:

Have you got any snapshots to revert to a older working state of your Windows guest?
[HOWTO: VirtualBox Snapshots. The Ins and Outs of Snapshots.]("http://ubuntuforums.org/showthread.php?t=689982")

If not the maybe you could try going into the Windows safe mode to fix if there's something broken.
[Getting into Windows Safe Mode.]("http://www.computerhope.com/issues/chsafe.htm#02")

Do you get the BSOD?
[Windows Patch Leaves Many XP Users With Blue Screens]("http://tech.slashdot.org/story/10/02/11/2217239/Windows-Patch-Leaves-Many-XP-Users-With-Blue-Screens")

---

### Post by discord on 2010-05-11
I tried safe mode. No snapshots, no BSOD. I'm not the only person experiencing this issue, maybe it's time to file a bug report.

[http://forums.virtualbox.org/viewtopic.php?f=2&t=30799]("http://forums.virtualbox.org/viewtopic.php?f=2&t=30799")

---

### Post by Matti L on 2010-05-12
I googled around quickly and found these two similar cases:

[http://forums.virtualbox.org/viewtopic.php?f=6&t=26475&start=0](http://forums.virtualbox.org/viewtopic.php?f=6&t=26475&start=0)

[http://www.virtualbox.org/ticket/3666](http://www.virtualbox.org/ticket/3666)

Can't help you more with this, sorry.

---

### Post by sloan1919 on 2010-08-15
I have the same EXACT problem. I am running VB 3.2.8 and ubuntu 10.04. 
Problem: 
VB powers down right after WINXP loading screen
logs say "Guest requests the VM to be turned off"

Env:
Fresh copy of Win XP SP2
Addons are installed

Tried:
Safe mode --> same result
debugging mode --> same result
letting VB make new config files --> same result

This is definately a VB bug... have read several forum post with exact same result. WINXP isn't requesting to power down but VB seems to think it is. In almost all posts I have ready the users have 3.1 or higher and have installed the addons.... could be a problem with it might have to test a copy without adding addons.... also I am downloading 3.0 will try that version.

---

### Post by scrooge_74 on 2010-08-15
Did you try playing with the settings for the VM, that could fixed it.

Take out audio, serial, usb support see if any of that is stopping you from booting.

I had some issues the other day with the serial port.

---

