---
title: "virtual box window shutdown during installing win xp"
date: 2009-01-25
forum: Virtualisation
---

### Post by rahul_bhise on 2009-01-25
when i try to install XP the virtual box shuts down. i have attached the log file hear. what would be the problem
```
00:00:03.566 VirtualBox 1.6.6 r35336 linux.x86 (Aug 26 2008 10:24:44) release log
00:00:03.566 Log opened 2009-01-25T17:38:02.670356000Z
00:00:03.567 OS Product: Linux
00:00:03.567 OS Release: 2.6.24-23-generic
00:00:03.567 OS Version: #1 SMP Thu Nov 27 18:44:42 UTC 2008
00:00:03.702 SUP: Loaded VMMR0.r0 (/usr/lib/virtualbox/VMMR0.r0) at 0xe0de1060 - ModuleInit at e0dede50 and ModuleTerm at e0dede10
00:00:03.702 SUP: VMMR0EntryEx located at e0dedbe0, VMMR0EntryFast at e0dedea0 and VMMR0EntryInt at e0ded4c0
00:00:03.779 vboxClipboardInit: initializing host clipboard
00:00:03.779 vboxClipboardThread: starting clipboard thread
00:00:03.840 VBoxSharedClipboard mode: Bidirectional
00:00:03.901 ************************* CFGM dump *************************
00:00:03.901 pRoot=083ef978:{/}
00:00:03.901 [/] (level 0)
00:00:03.901   Name         <string>  = "xpcd" (cch=5)
00:00:03.901   UUID         <bytes>   = "a1 8c 99 3c 2b 9b 10 42 7a bd b6 f2 31 2a 9b 3f" (cb=16)
00:00:03.901   RamSize      <integer> = 0x0000000012c00000 (314572800)
00:00:03.901   TimerMillies <integer> = 0x000000000000000a (10)
00:00:03.901   RawR3Enabled <integer> = 0x0000000000000001 (1)
00:00:03.901   RawR0Enabled <integer> = 0x0000000000000001 (1)
00:00:03.901   PATMEnabled  <integer> = 0x0000000000000001 (1)
00:00:03.901   CSAMEnabled  <integer> = 0x0000000000000001 (1)
00:00:03.901   EnablePAE    <integer> = 0x0000000000000000 (0)
00:00:03.901 
00:00:03.901 [/PDM/] (level 1)
00:00:03.901 
00:00:03.901 [/PDM/Drivers/] (level 2)
00:00:03.901 
00:00:03.901 [/PDM/Drivers/VBoxC/] (level 3)
00:00:03.901   Path <string>  = "/usr/lib/virtualbox/components/VBoxC" (cch=37)
00:00:03.901 
00:00:03.901 [/Devices/] (level 1)
00:00:03.901 
00:00:03.901 [/Devices/pcarch/] (level 2)
00:00:03.901 
00:00:03.901 [/Devices/pcarch/0/] (level 3)
00:00:03.901   Trusted <integer> = 0x0000000000000001 (1)
00:00:03.901 
00:00:03.901 [/Devices/pcarch/0/Config/] (level 4)
00:00:03.901 
00:00:03.901 [/Devices/pcbios/] (level 2)
00:00:03.901 
00:00:03.901 [/Devices/pcbios/0/] (level 3)
00:00:03.901   Trusted <integer> = 0x0000000000000001 (1)
00:00:03.901 
00:00:03.901 [/Devices/pcbios/0/Config/] (level 4)
00:00:03.901   RamSize        <integer> = 0x0000000012c00000 (314572800)
00:00:03.901   HardDiskDevice <string>  = "piix3ide" (cch=9)
00:00:03.901   FloppyDevice   <string>  = "i82078" (cch=7)
00:00:03.901   IOAPIC         <integer> = 0x0000000000000000 (0)
00:00:03.901   PXEDebug       <integer> = 0x0000000000000000 (0)
00:00:03.901   UUID           <bytes>   = "a1 8c 99 3c 2b 9b 10 42 7a bd b6 f2 31 2a 9b 3f" (cb=16)
00:00:03.901   BootDevice0    <string>  = "FLOPPY" (cch=7)
00:00:03.901   BootDevice1    <string>  = "DVD" (cch=4)
00:00:03.901   BootDevice2    <string>  = "IDE" (cch=4)
00:00:03.901   BootDevice3    <string>  = "NONE" (cch=5)
00:00:03.901 
00:00:03.901 [/Devices/8237A/] (level 2)
00:00:03.901 
00:00:03.901 [/Devices/8237A/0/] (level 3)
00:00:03.902   Trusted <integer> = 0x0000000000000001 (1)
00:00:03.902 
00:00:03.902 [/Devices/pci/] (level 2)
00:00:03.902 
00:00:03.902 [/Devices/pci/0/] (level 3)
00:00:03.902   Trusted <integer> = 0x0000000000000001 (1)
00:00:03.902 
00:00:03.902 [/Devices/pci/0/Config/] (level 4)
00:00:03.902   IOAPIC <integer> = 0x0000000000000000 (0)
00:00:03.902 
00:00:03.902 [/Devices/pckbd/] (level 2)
00:00:03.902 
00:00:03.902 [/Devices/pckbd/0/] (level 3)
00:00:03.902   Trusted <integer> = 0x0000000000000001 (1)
00:00:03.902 
00:00:03.902 [/Devices/pckbd/0/Config/] (level 4)
00:00:03.902 
00:00:03.902 [/Devices/pckbd/0/LUN#0/] (level 4)
00:00:03.902   Driver <string>  = "KeyboardQueue" (cch=14)
00:00:03.902 
00:00:03.902 [/Devices/pckbd/0/LUN#0/Config/] (level 5)
00:00:03.902   QueueSize <integer> = 0x0000000000000040 (64)
00:00:03.902 
00:00:03.902 [/Devices/pckbd/0/LUN#0/AttachedDriver/] (level 5)
00:00:03.902   Driver <string>  = "MainKeyboard" (cch=13)
00:00:03.902 
00:00:03.902 [/Devices/pckbd/0/LUN#0/AttachedDriver/Config/] (level 6)
00:00:03.902   Object <integer> = 0x00000000083c4598 (138167704)
00:00:03.902 
00:00:03.902 [/Devices/pckbd/0/LUN#1/] (level 4)
00:00:03.902   Driver <string>  = "MouseQueue" (cch=11)
00:00:03.902 
00:00:03.902 [/Devices/pckbd/0/LUN#1/Config/] (level 5)
00:00:03.902   QueueSize <integer> = 0x0000000000000080 (128)
00:00:03.902 
00:00:03.902 [/Devices/pckbd/0/LUN#1/AttachedDriver/] (level 5)
00:00:03.902   Driver <string>  = "MainMouse" (cch=10)
00:00:03.902 
00:00:03.902 [/Devices/pckbd/0/LUN#1/AttachedDriver/Config/] (level 6)
00:00:03.902   Object <integer> = 0x00000000083c46a0 (138167968)
00:00:03.902 
00:00:03.902 [/Devices/i82078/] (level 2)
00:00:03.902 
00:00:03.902 [/Devices/i82078/0/] (level 3)
00:00:03.902   Trusted <integer> = 0x0000000000000001 (1)
00:00:03.902 
00:00:03.902 [/Devices/i82078/0/Config/] (level 4)
00:00:03.902   IRQ       <integer> = 0x0000000000000006 (6)
00:00:03.902   DMA       <integer> = 0x0000000000000002 (2)
00:00:03.902   MemMapped <integer> = 0x0000000000000000 (0)
00:00:03.902   IOBase    <integer> = 0x00000000000003f0 (1008)
00:00:03.902 
00:00:03.902 [/Devices/i82078/0/LUN#999/] (level 4)
00:00:03.902   Driver <string>  = "MainStatus" (cch=11)
00:00:03.902 
00:00:03.902 [/Devices/i82078/0/LUN#999/Config/] (level 5)
00:00:03.902   papLeds <integer> = 0x00000000083c3f78 (138166136)
00:00:03.902   First   <integer> = 0x0000000000000000 (0)
00:00:03.902   Last    <integer> = 0x0000000000000000 (0)
00:00:03.902 
00:00:03.902 [/Devices/i82078/0/LUN#0/] (level 4)
00:00:03.902   Driver <string>  = "Block" (cch=6)
00:00:03.902 
00:00:03.902 [/Devices/i82078/0/LUN#0/Config/] (level 5)
00:00:03.902   Type      <string>  = "Floppy 1.44" (cch=12)
00:00:03.902   Mountable <integer> = 0x0000000000000001 (1)
00:00:03.902 
00:00:03.902 [/Devices/acpi/] (level 2)
00:00:03.902 
00:00:03.902 [/Devices/acpi/0/] (level 3)
00:00:03.902   Trusted       <integer> = 0x0000000000000001 (1)
00:00:03.902   PCIDeviceNo   <integer> = 0x0000000000000007 (7)
00:00:03.902   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:03.902 
00:00:03.902 [/Devices/acpi/0/Config/] (level 4)
00:00:03.902   RamSize    <integer> = 0x0000000012c00000 (314572800)
00:00:03.902   IOAPIC     <integer> = 0x0000000000000000 (0)
00:00:03.902   FdcEnabled <integer> = 0x0000000000000001 (1)
00:00:03.902 
00:00:03.902 [/Devices/acpi/0/LUN#0/] (level 4)
00:00:03.903   Driver <string>  = "ACPIHost" (cch=9)
00:00:03.903 
00:00:03.903 [/Devices/acpi/0/LUN#0/Config/] (level 5)
00:00:03.903 
00:00:03.903 [/Devices/i8254/] (level 2)
00:00:03.903 
00:00:03.903 [/Devices/i8254/0/] (level 3)
00:00:03.903 
00:00:03.903 [/Devices/i8254/0/Config/] (level 4)
00:00:03.903 
00:00:03.903 [/Devices/i8259/] (level 2)
00:00:03.903 
00:00:03.903 [/Devices/i8259/0/] (level 3)
00:00:03.903   Trusted <integer> = 0x0000000000000001 (1)
00:00:03.903 
00:00:03.903 [/Devices/i8259/0/Config/] (level 4)
00:00:03.903 
00:00:03.903 [/Devices/apic/] (level 2)
00:00:03.903 
00:00:03.903 [/Devices/apic/0/] (level 3)
00:00:03.903   Trusted <integer> = 0x0000000000000001 (1)
00:00:03.903 
00:00:03.903 [/Devices/apic/0/Config/] (level 4)
00:00:03.903   IOAPIC <integer> = 0x0000000000000000 (0)
00:00:03.903 
00:00:03.903 [/Devices/mc146818/] (level 2)
00:00:03.903 
00:00:03.903 [/Devices/mc146818/0/] (level 3)
00:00:03.903 
00:00:03.903 [/Devices/mc146818/0/Config/] (level 4)
00:00:03.903 
00:00:03.903 [/Devices/vga/] (level 2)
00:00:03.903 
00:00:03.903 [/Devices/vga/0/] (level 3)
00:00:03.903   Trusted       <integer> = 0x0000000000000001 (1)
00:00:03.903   PCIDeviceNo   <integer> = 0x0000000000000002 (2)
00:00:03.903   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:03.903 
00:00:03.903 [/Devices/vga/0/Config/] (level 4)
00:00:03.903   VRamSize         <integer> = 0x0000000000800000 (8388608)
00:00:03.903   FadeIn           <integer> = 0x0000000000000001 (1)
00:00:03.903   FadeOut          <integer> = 0x0000000000000001 (1)
00:00:03.903   LogoTime         <integer> = 0x0000000000000000 (0)
00:00:03.903   LogoFile         <string>  = "" (cch=1)
00:00:03.903   ShowBootMenu     <integer> = 0x0000000000000002 (2)
00:00:03.903   CustomVideoModes <integer> = 0x0000000000000000 (0)
00:00:03.903   HeightReduction  <integer> = 0x0000000000000000 (0)
00:00:03.903 
00:00:03.903 [/Devices/vga/0/LUN#0/] (level 4)
00:00:03.903   Driver <string>  = "MainDisplay" (cch=12)
00:00:03.903 
00:00:03.903 [/Devices/vga/0/LUN#0/Config/] (level 5)
00:00:03.903   Object <integer> = 0x00000000083c47a0 (138168224)
00:00:03.903 
00:00:03.903 [/Devices/piix3ide/] (level 2)
00:00:03.903 
00:00:03.903 [/Devices/piix3ide/0/] (level 3)
00:00:03.903   Trusted       <integer> = 0x0000000000000001 (1)
00:00:03.903   PCIDeviceNo   <integer> = 0x0000000000000001 (1)
00:00:03.903   PCIFunctionNo <integer> = 0x0000000000000001 (1)
00:00:03.903 
00:00:03.903 [/Devices/piix3ide/0/Config/] (level 4)
00:00:03.903   PIIX4 <integer> = 0x0000000000000001 (1)
00:00:03.903 
00:00:03.903 [/Devices/piix3ide/0/LUN#999/] (level 4)
00:00:03.903   Driver <string>  = "MainStatus" (cch=11)
00:00:03.903 
00:00:03.903 [/Devices/piix3ide/0/LUN#999/Config/] (level 5)
00:00:03.903   papLeds <integer> = 0x00000000083c3f80 (138166144)
00:00:03.903   First   <integer> = 0x0000000000000000 (0)
00:00:03.903   Last    <integer> = 0x0000000000000003 (3)
00:00:03.903 
00:00:03.903 [/Devices/piix3ide/0/LUN#0/] (level 4)
00:00:03.903   Driver <string>  = "Block" (cch=6)
00:00:03.903 
00:00:03.903 [/Devices/piix3ide/0/LUN#0/Config/] (level 5)
00:00:03.903   Type      <string>  = "HardDisk" (cch=9)
00:00:03.903   Mountable <integer> = 0x0000000000000000 (0)
00:00:03.904 
00:00:03.904 [/Devices/piix3ide/0/LUN#0/AttachedDriver/] (level 5)
00:00:03.904   Driver <string>  = "VBoxHDD" (cch=8)
00:00:03.904 
00:00:03.904 [/Devices/piix3ide/0/LUN#0/AttachedDriver/Config/] (level 6)
00:00:03.904   Path <string>  = "/home/brahul/Desktop/xpcd.vdi" (cch=30)
00:00:03.904 
00:00:03.904 [/Devices/piix3ide/0/LUN#2/] (level 4)
00:00:03.904   Driver <string>  = "HostDVD" (cch=8)
00:00:03.904 
00:00:03.904 [/Devices/piix3ide/0/LUN#2/Config/] (level 5)
00:00:03.904   Path        <string>  = "/dev/scd0" (cch=10)
00:00:03.904   Passthrough <integer> = 0x0000000000000000 (0)
00:00:03.904 
00:00:03.904 [/Devices/pcnet/] (level 2)
00:00:03.904 
00:00:03.904 [/Devices/pcnet/0/] (level 3)
00:00:03.904   Trusted       <integer> = 0x0000000000000001 (1)
00:00:03.904   PCIDeviceNo   <integer> = 0x0000000000000003 (3)
00:00:03.904   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:03.904 
00:00:03.904 [/Devices/pcnet/0/Config/] (level 4)
00:00:03.904   Am79C973       <integer> = 0x0000000000000001 (1)
00:00:03.904   MAC            <bytes>   = "08 00 27 10 e9 d5" (cb=6)
00:00:03.904   CableConnected <integer> = 0x0000000000000001 (1)
00:00:03.904   LineSpeed      <integer> = 0x0000000000000000 (0)
00:00:03.904 
00:00:03.904 [/Devices/pcnet/0/LUN#999/] (level 4)
00:00:03.904   Driver <string>  = "MainStatus" (cch=11)
00:00:03.904 
00:00:03.904 [/Devices/pcnet/0/LUN#999/Config/] (level 5)
00:00:03.904   papLeds <integer> = 0x00000000083c4008 (138166280)
00:00:03.904 
00:00:03.904 [/Devices/pcnet/0/LUN#0/] (level 4)
00:00:03.904   Driver <string>  = "NAT" (cch=4)
00:00:03.904 
00:00:03.904 [/Devices/pcnet/0/LUN#0/Config/] (level 5)
00:00:03.904   TFTPPrefix <string>  = "/home/brahul/.VirtualBox/TFTP" (cch=30)
00:00:03.904   BootFile   <string>  = "xpcd.pxe" (cch=9)
00:00:03.904 
00:00:03.904 [/Devices/e1000/] (level 2)
00:00:03.904 
00:00:03.904 [/Devices/serial/] (level 2)
00:00:03.904 
00:00:03.904 [/Devices/parallel/] (level 2)
00:00:03.904 
00:00:03.904 [/Devices/VMMDev/] (level 2)
00:00:03.904 
00:00:03.904 [/Devices/VMMDev/0/] (level 3)
00:00:03.904   Trusted       <integer> = 0x0000000000000001 (1)
00:00:03.904   PCIDeviceNo   <integer> = 0x0000000000000004 (4)
00:00:03.904   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:03.904 
00:00:03.904 [/Devices/VMMDev/0/Config/] (level 4)
00:00:03.904 
00:00:03.904 [/Devices/VMMDev/0/LUN#0/] (level 4)
00:00:03.904   Driver <string>  = "MainVMMDev" (cch=11)
00:00:03.904 
00:00:03.904 [/Devices/VMMDev/0/LUN#0/Config/] (level 5)
00:00:03.904   Object <integer> = 0x00000000083c4de0 (138169824)
00:00:03.904 
00:00:03.904 [/Devices/VMMDev/0/LUN#999/] (level 4)
00:00:03.904   Driver <string>  = "MainStatus" (cch=11)
00:00:03.904 
00:00:03.904 [/Devices/VMMDev/0/LUN#999/Config/] (level 5)
00:00:03.904   papLeds <integer> = 0x00000000083c4028 (138166312)
00:00:03.904   First   <integer> = 0x0000000000000000 (0)
00:00:03.904   Last    <integer> = 0x0000000000000000 (0)
00:00:03.904 
00:00:03.904 [/Devices/AudioSniffer/] (level 2)
00:00:03.904 
00:00:03.904 [/Devices/AudioSniffer/0/] (level 3)
00:00:03.904 
00:00:03.904 [/Devices/AudioSniffer/0/Config/] (level 4)
00:00:03.904 
00:00:03.904 [/Devices/AudioSniffer/0/LUN#0/] (level 4)
00:00:03.904   Driver <string>  = "MainAudioSniffer" (cch=17)
00:00:03.904 
00:00:03.904 [/Devices/AudioSniffer/0/LUN#0/Config/] (level 5)
00:00:03.905   Object <integer> = 0x00000000083c4e00 (138169856)
00:00:03.905 
00:00:03.905 [/TM/] (level 1)
00:00:03.905   UTCOffset <integer> = 0x0000000000000000 (0)
00:00:03.905 
00:00:03.905 ********************* End of CFGM dump **********************
00:00:03.909 Logical host processors: 1, processor active mask: 00000001
00:00:03.909 ************************* CPUID dump ************************
00:00:03.909          RAW Standard CPUIDs
00:00:03.909      Function  eax      ebx      ecx      edx
00:00:03.909 Gst: 00000000  00000002 756e6547 6c65746e 49656e69
00:00:03.909 Hst:           00000005 756e6547 6c65746e 49656e69
00:00:03.909 Gst: 00000001  00000f41 00000800 00000008 0788a1bf
00:00:03.909 Hst:           00000f41 00010800 0000441d bfebfbff
00:00:03.909 Gst: 00000002  605b5101 00000000 00000000 007c7040
00:00:03.909 Hst:           605b5101 00000000 00000000 007c7040
00:00:03.909 Gst: 00000003  00000040 00000040 00000000 00000000*
00:00:03.909 Hst:           00000000 00000000 00000000 00000000
00:00:03.909 Gst: 00000004  00000000 00000040 00000000 00000000*
00:00:03.909 Hst:           00000121 01c0003f 0000001f 00000000
00:00:03.909 Name:                            GenuineIntel
00:00:03.909 Supports:                        0-2
00:00:03.909 Family:                          15  	Extended: 0 	Effectiv: 15
00:00:03.909 Model:                           4  	Extended: 0 	Effectiv: 4
00:00:03.909 Stepping:                        1
00:00:03.909 APIC ID:                         0x00
00:00:03.909 Logical CPUs:                    0
00:00:03.909 CLFLUSH Size:                    8
00:00:03.909 Brand ID:                        0x00
00:00:03.909 Mnemonic - Description                 = guest (host)
00:00:03.909 FPU - x87 FPU on Chip                  = 1 (1)
00:00:03.909 VME - Virtual 8086 Mode Enhancements   = 1 (1)
00:00:03.909 DE - Debugging extensions              = 1 (1)
00:00:03.909 PSE - Page Size Extension              = 1 (1)
00:00:03.909 TSC - Time Stamp Counter               = 1 (1)
00:00:03.909 MSR - Model Specific Registers         = 1 (1)
00:00:03.909 PAE - Physical Address Extension       = 0 (1)
00:00:03.909 MCE - Machine Check Exception          = 1 (1)
00:00:03.909 CX8 - CMPXCHG8B instruction            = 1 (1)
00:00:03.909 APIC - APIC On-Chip                    = 0 (1)
00:00:03.909 Reserved                               = 0 (0)
00:00:03.909 SEP - SYSENTER and SYSEXIT             = 0 (1)
00:00:03.909 MTRR - Memory Type Range Registers     = 0 (1)
00:00:03.909 PGE - PTE Global Bit                   = 1 (1)
00:00:03.909 MCA - Machine Check Architecture       = 0 (1)
00:00:03.909 CMOV - Conditional Move Instructions   = 1 (1)
00:00:03.909 PAT - Page Attribute Table             = 0 (1)
00:00:03.909 PSE-36 - 36-bit Page Size Extention    = 0 (1)
00:00:03.909 PSN - Processor Serial Number          = 0 (0)
00:00:03.909 CLFSH - CLFLUSH Instruction.           = 1 (1)
00:00:03.909 Reserved                               = 0 (0)
00:00:03.909 DS - Debug Store                       = 0 (1)
00:00:03.909 ACPI - Thermal Mon. & Soft. Clock Ctrl.= 0 (1)
00:00:03.909 MMX - Intel MMX Technology             = 1 (1)
00:00:03.909 FXSR - FXSAVE and FXRSTOR Instructions = 1 (1)
00:00:03.909 SSE - SSE Support                      = 1 (1)
00:00:03.909 SSE2 - SSE2 Support                    = 1 (1)
00:00:03.909 SS - Self Snoop                        = 0 (1)
00:00:03.909 HTT - Hyper-Threading Technolog        = 0 (1)
00:00:03.909 TM - Thermal Monitor                   = 0 (1)
00:00:03.909 30 - Reserved                          = 0 (0)
00:00:03.909 PBE - Pending Break Enable             = 0 (1)
00:00:03.909 Supports SSE3 or not                   = 0 (1)
00:00:03.909 Reserved                               = 0 (2)
00:00:03.909 Supports MONITOR/MWAIT                 = 1 (1)
00:00:03.909 CPL-DS - CPL Qualified Debug Store     = 0 (1)
00:00:03.909 VMX - Virtual Machine Technology       = 0 (0)
00:00:03.909 Reserved                               = 0 (0)
00:00:03.909 Enhanced SpeedStep Technology          = 0 (0)
00:00:03.909 Terminal Monitor 2                     = 0 (0)
00:00:03.909 Supports Supplemental SSE3 or not      = 0 (0)
00:00:03.909 L1 Context ID                          = 0 (1)
00:00:03.909 Reserved                               = 0x0 (0x0)
00:00:03.909 CMPXCHG16B                             = 0 (0)
00:00:03.909 xTPR Update Control                    = 0 (1)
00:00:03.909 Reserved                               = 0x0 (0x0)
00:00:03.909 
00:00:03.909          RAW Extended CPUIDs
00:00:03.909      Function  eax      ebx      ecx      edx
00:00:03.909 Gst: 80000000  80000004 00000000 00000000 00000000
00:00:03.909 Hst:           80000008 00000000 00000000 00000000
00:00:03.909 Gst: 80000001  00000000 00000000 00000000 00000000
00:00:03.909 Hst:           00000000 00000000 00000000 00000000
00:00:03.909 Gst: 80000002  20202020 20202020 20202020 6e492020
00:00:03.909 Hst:           20202020 20202020 20202020 6e492020
00:00:03.909 Gst: 80000003  286c6574 50202952 69746e65 52286d75
00:00:03.909 Hst:           286c6574 50202952 69746e65 52286d75
00:00:03.909 Gst: 80000004  20342029 20555043 30342e32 007a4847
00:00:03.909 Hst:           20342029 20555043 30342e32 007a4847
00:00:03.909 Gst: 80000005  00000040 00000040 00000000 00000000*
00:00:03.909 Hst:           00000000 00000000 00000000 00000000
00:00:03.909 Gst: 80000006  00000040 00000040 00000000 00000000*
00:00:03.909 Hst:           00000000 00000000 04006040 00000000
00:00:03.909 Gst: 80000007  00000040 00000040 00000000 00000000*
00:00:03.909 Hst:           00000000 00000000 00000000 00000000
00:00:03.909 Gst: 80000008  00000040 00000040 00000000 00000000*
00:00:03.909 Hst:           00002024 00000000 00000000 00000000
00:00:03.909 Gst: 80000009  00000040 00000040 00000000 00000000*
00:00:03.909 Hst:           00000040 00000040 00000000 00000000
00:00:03.909 Ext Name:                        
00:00:03.909 Ext Supports:                    0x80000000-0x80000004
00:00:03.909 Family:                          0  	Extended: 0 	Effectiv: 0
00:00:03.909 Model:                           0  	Extended: 0 	Effectiv: 0
00:00:03.909 Stepping:                        0
00:00:03.909 Brand ID:                        0x000
00:00:03.909 Mnemonic - Description                 = guest (host)
00:00:03.909 FPU - x87 FPU on Chip                  = 0 (0)
00:00:03.909 VME - Virtual 8086 Mode Enhancements   = 0 (0)
00:00:03.909 DE - Debugging extensions              = 0 (0)
00:00:03.909 PSE - Page Size Extension              = 0 (0)
00:00:03.909 TSC - Time Stamp Counter               = 0 (0)
00:00:03.909 MSR - K86 Model Specific Registers     = 0 (0)
00:00:03.909 PAE - Physical Address Extension       = 0 (0)
00:00:03.909 MCE - Machine Check Exception          = 0 (0)
00:00:03.909 CX8 - CMPXCHG8B instruction            = 0 (0)
00:00:03.909 APIC - APIC On-Chip                    = 0 (0)
00:00:03.909 10 - Reserved                          = 0 (0)
00:00:03.909 SEP - SYSCALL and SYSRET               = 0 (0)
00:00:03.909 MTRR - Memory Type Range Registers     = 0 (0)
00:00:03.909 PGE - PTE Global Bit                   = 0 (0)
00:00:03.909 MCA - Machine Check Architecture       = 0 (0)
00:00:03.909 CMOV - Conditional Move Instructions   = 0 (0)
00:00:03.909 PAT - Page Attribute Table             = 0 (0)
00:00:03.909 PSE-36 - 36-bit Page Size Extention    = 0 (0)
00:00:03.909 18 - Reserved                          = 0 (0)
00:00:03.909 19 - Reserved                          = 0 (0)
00:00:03.909 NX - No-Execute Page Protection        = 0 (0)
00:00:03.909 DS - Debug Store                       = 0 (0)
00:00:03.909 AXMMX - AMD Extensions to MMX Instr.   = 0 (0)
00:00:03.909 MMX - Intel MMX Technology             = 0 (0)
00:00:03.909 FXSR - FXSAVE and FXRSTOR Instructions = 0 (0)
00:00:03.909 25 - AMD fast FXSAVE and FXRSTOR Instr.= 0 (0)
00:00:03.909 26 - 1 GB large page support           = 0 (0)
00:00:03.909 27 - RDTSCP instruction                = 0 (0)
00:00:03.909 28 - Reserved                          = 0 (0)
00:00:03.909 29 - AMD Long Mode                     = 0 (0)
00:00:03.909 30 - AMD Extensions to 3DNow           = 0 (0)
00:00:03.909 31 - AMD 3DNow                         = 0 (0)
00:00:03.909 LahfSahf - LAHF/SAHF in 64-bit mode    = 0 (0)
00:00:03.909 CmpLegacy - Core MP legacy mode (depr) = 0 (0)
00:00:03.909 SVM - AMD VM Extensions                = 0 (0)
00:00:03.909 APIC registers starting at 0x400       = 0 (0)
00:00:03.909 AltMovCR8 - LOCK MOV CR0 means MOV CR8 = 0 (0)
00:00:03.909 Advanced bit manipulation              = 0 (0)
00:00:03.909 SSE4A instruction support              = 0 (0)
00:00:03.909 Misaligned SSE mode                    = 0 (0)
00:00:03.909 PREFETCH and PREFETCHW instruction     = 0 (0)
00:00:03.909 OS visible workaround                  = 0 (0)
00:00:03.909 Instruction based sampling             = 0 (0)
00:00:03.909 SSE5 support                           = 0 (0)
00:00:03.909 SKINIT, STGI, and DEV support          = 0 (0)
00:00:03.909 Watchdog timer support.                = 0 (0)
00:00:03.909 31:14 - Reserved                       = 0x0 (0x0)
00:00:03.909 Full Name:                                     Intel(R) Pentium(R) 4 CPU 2.40GHz
00:00:03.909 
00:00:03.909          RAW Centaur CPUIDs
00:00:03.909      Function  eax      ebx      ecx      edx
00:00:03.909 Gst: c0000000  00000040 00000040 00000000 00000000
00:00:03.909 Hst:           00000040 00000040 00000000 00000000
00:00:03.909 Gst: c0000001  00000040 00000040 00000000 00000000
00:00:03.909 Hst:           00000040 00000040 00000000 00000000
00:00:03.909 Gst: c0000002  00000040 00000040 00000000 00000000
00:00:03.909 Hst:           00000040 00000040 00000000 00000000
00:00:03.910 Gst: c0000003  00000040 00000040 00000000 00000000
00:00:03.910 Hst:           00000040 00000040 00000000 00000000
00:00:03.910 Centaur Supports:                0xc0000000-0x00000040
00:00:03.910 Mnemonic - Description                 = guest (host)
00:00:03.910 AIS - Alternate Instruction Set        = 0 (0)
00:00:03.910 AIS-E - AIS enabled                    = 0 (0)
00:00:03.910 RNG - Random Number Generator          = 0 (0)
00:00:03.910 RNG-E - RNG enabled                    = 0 (0)
00:00:03.910 LH - LongHaul MSR 0000_110Ah           = 0 (0)
00:00:03.910 FEMMS - FEMMS                          = 0 (0)
00:00:03.910 ACE - Advanced Cryptography Engine     = 0 (0)
00:00:03.910 ACE-E - ACE enabled                    = 0 (0)
00:00:03.910 ACE2 - Advanced Cryptography Engine 2  = 0 (0)
00:00:03.910 ACE2-E - ACE enabled                   = 0 (0)
00:00:03.910 PHE - Hash Engine                      = 0 (0)
00:00:03.910 PHE-E - PHE enabled                    = 0 (0)
00:00:03.910 PMM - Montgomery Multiplier            = 0 (0)
00:00:03.910 PMM-E - PMM enabled                    = 0 (0)
00:00:03.910 
00:00:03.910 
00:00:03.910 ******************** End of CPUID dump **********************
00:00:03.957 TM: cTSCTicksPerSecond=0x8f18c736 (2400765750) fTSCVirtualized=true  fTSCUseRealTSC=false fMaybeUseOffsettedHostTSC=true 
00:00:03.957 CoreCode: R3=b2d09000 R0=e0cb7000 GC=a02c7000 Phys=000000000bbc4000 cb=0x2000
00:00:04.183 SUP: Loaded VBoxDDR0.r0 (/usr/lib/virtualbox/VBoxDDR0.r0) at 0xe0e60060 - ModuleInit at 00000000 and ModuleTerm at 00000000
00:00:04.197 SUP: Loaded VBoxDD2R0.r0 (/usr/lib/virtualbox/VBoxDD2R0.r0) at 0xe0cda060 - ModuleInit at 00000000 and ModuleTerm at 00000000
00:00:04.198 Activating Local APIC
00:00:04.198 PIT: mode=3 count=0x10000 (65536) - 18.20 Hz (ch=0)
00:00:04.217 Shared Folders service loaded.
00:00:04.283 PIIX3 ATA: LUN#0: disk, PCHS=14563/16/63, total number of sectors 14680064
00:00:04.283 PIIX3 ATA: LUN#1: no unit
00:00:04.285 PIIX3 ATA: LUN#2: CD/DVD, total number of sectors 315563, passthrough disabled
00:00:04.285 PIIX3 ATA: LUN#3: no unit
00:00:04.285 PIIX3 ATA: Ctl#0: finished processing RESET
00:00:04.285 PIIX3 ATA: Ctl#1: finished processing RESET
00:00:04.294 NAT: DNS address: 208.67.222.222
00:00:04.294 NAT: ignored DNS address: 208.67.220.220
00:00:04.294 NAT: ignored DNS address: 61.1.96.69
00:00:04.294 NAT: ignored DNS address: 61.1.96.71
00:00:04.305 DevPcBios: ATA LUN#0 LCHS=913/255/63
00:00:04.323 HWACCM: No VMX or SVM CPU extension found. Reason VERR_VMX_NO_VMX
00:00:04.323 HWACCM: VMX MSR_IA32_FEATURE_CONTROL=0
00:00:04.340 VM: Halt method global1 (5)
00:00:04.340 Changing the VM state from 'CREATING' to 'CREATED'.
00:00:04.340 Changing the VM state from 'CREATED' to 'RUNNING'.
00:00:04.407 Guest Log: BIOS: VirtualBox 1.6.6
00:00:04.407 PIT: mode=2 count=0x10000 (65536) - 18.20 Hz (ch=0)
00:00:04.430 PIIX3 ATA: Ctl#0: RESET, DevSel=0 AIOIf=0 CmdIf0=0x00 (-1 usec ago) CmdIf1=0x00 (-1 usec ago)
00:00:04.430 PIIX3 ATA: Ctl#0: finished processing RESET
00:00:04.431 Guest Log: BIOS: ata0-0: PCHS=14563/16/63 LCHS=913/255/63
00:00:04.432 PIIX3 ATA: Ctl#1: RESET, DevSel=0 AIOIf=0 CmdIf0=0x00 (-1 usec ago) CmdIf1=0x00 (-1 usec ago)
00:00:04.432 PIIX3 ATA: Ctl#1: finished processing RESET
00:00:04.433 PIT: mode=2 count=0x48d3 (18643) - 64.00 Hz (ch=0)
00:00:04.442 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=b1ae2000 w=640 h=480 bpp=32 cbLine=0xA00
00:00:06.957 PIT: mode=2 count=0x10000 (65536) - 18.20 Hz (ch=0)
00:00:06.958 Guest Log: BIOS: Boot from Floppy 0 failed
00:00:06.968 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=00000000 w=720 h=400 bpp=0 cbLine=0x0
00:00:07.252 Guest Log: BIOS: Booting from CD-ROM...
00:00:08.455 Guest Log: BIOS: int13_harddisk: function 15, unmapped device for ELDL=81
00:00:54.499 PIT: mode=2 count=0x2ead (11949) - 99.85 Hz (ch=0)
00:00:58.534 PIIX3 ATA: LUN#0: IDLE IMMEDIATE, CmdIf=0xc4 (-1 usec ago)
00:00:58.534 PIIX3 ATA: LUN#0: aborting current command
00:01:02.749 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=00000000 w=720 h=396 bpp=0 cbLine=0x0
```

---

### Post by rahul_bhise on 2009-01-26
bump

---

### Post by x33a on 2009-01-26
have you tried installing any other OS under virtualbox?

does this happen only with xp?

---

