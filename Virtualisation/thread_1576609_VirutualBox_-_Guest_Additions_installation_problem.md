---
title: "VirutualBox - Guest Additions installation problem"
date: 2010-09-17
forum: Virtualisation
---

### Post by maciejso on 2010-09-17
on my Debian 2.6.26-2 as host and Ubuntu 9.04 as gues I'm getting the following message when I'm trying to mount cd with additions

```

maciej@debian:~$ sudo mount /dev/cdrom
mount: block device /dev/sr0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       (could this be the IDE device where you in fact use
       ide-scsi so that sr0 or sda or so is needed?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


```

The same message pops up when I change guest for Debian, so I guess it must be host-related, but have no clue what it is.
Any help appreciated.

Here's the VBox.log
```

00:00:03.459 VirtualBox 1.6.6_OSE r35336 linux.x86 (Nov  7 2008 12:08:16) release log
00:00:03.459 Log opened 2010-09-17T18:34:59.115304000Z
00:00:03.460 OS Product: Linux
00:00:03.460 OS Release: 2.6.26-2-686
00:00:03.460 OS Version: #1 SMP Mon Aug 30 07:01:57 UTC 2010
00:00:03.490 SUP: Loaded VMMR0.r0 (/usr/lib/virtualbox/VMMR0.r0) at 0xf8e2f060 - ModuleInit at f8e3be50 and ModuleTerm at f8e3be10
00:00:03.490 SUP: VMMR0EntryEx located at f8e3bbe0, VMMR0EntryFast at f8e3bea0 and VMMR0EntryInt at f8e3b4c0
00:00:03.559 vboxClipboardInit: initializing host clipboard
00:00:03.559 vboxClipboardThread: starting clipboard thread
00:00:03.562 VBoxSharedClipboard mode: Bidirectional
00:00:03.644 ************************* CFGM dump *************************
00:00:03.644 pRoot=09c02060:{/}
00:00:03.644 [/] (level 0)
00:00:03.644   Name         <string>  = "Debian" (cch=7)
00:00:03.644   UUID         <bytes>   = "33 ef a7 65 45 4e 14 45 c6 b2 a0 0b ed 39 a7 e3" (cb=16)
00:00:03.644   RamSize      <integer> = 0x0000000022800000 (578813952)
00:00:03.644   TimerMillies <integer> = 0x000000000000000a (10)
00:00:03.644   RawR3Enabled <integer> = 0x0000000000000001 (1)
00:00:03.644   RawR0Enabled <integer> = 0x0000000000000001 (1)
00:00:03.644   PATMEnabled  <integer> = 0x0000000000000001 (1)
00:00:03.644   CSAMEnabled  <integer> = 0x0000000000000001 (1)
00:00:03.644   EnablePAE    <integer> = 0x0000000000000000 (0)
00:00:03.644 
00:00:03.644 [/PDM/] (level 1)
00:00:03.644 
00:00:03.644 [/PDM/Drivers/] (level 2)
00:00:03.644 
00:00:03.644 [/PDM/Drivers/VBoxC/] (level 3)
00:00:03.644   Path <string>  = "/usr/lib/virtualbox/components/VBoxC" (cch=37)
00:00:03.644 
00:00:03.644 [/Devices/] (level 1)
00:00:03.644 
00:00:03.644 [/Devices/pcarch/] (level 2)
00:00:03.644 
00:00:03.644 [/Devices/pcarch/0/] (level 3)
00:00:03.644   Trusted <integer> = 0x0000000000000001 (1)
00:00:03.644 
00:00:03.644 [/Devices/pcarch/0/Config/] (level 4)
00:00:03.644 
00:00:03.644 [/Devices/pcbios/] (level 2)
00:00:03.644 
00:00:03.644 [/Devices/pcbios/0/] (level 3)
00:00:03.644   Trusted <integer> = 0x0000000000000001 (1)
00:00:03.645 
00:00:03.645 [/Devices/pcbios/0/Config/] (level 4)
00:00:03.645   RamSize        <integer> = 0x0000000022800000 (578813952)
00:00:03.645   HardDiskDevice <string>  = "piix3ide" (cch=9)
00:00:03.645   FloppyDevice   <string>  = "i82078" (cch=7)
00:00:03.645   IOAPIC         <integer> = 0x0000000000000000 (0)
00:00:03.645   PXEDebug       <integer> = 0x0000000000000000 (0)
00:00:03.645   UUID           <bytes>   = "33 ef a7 65 45 4e 14 45 c6 b2 a0 0b ed 39 a7 e3" (cb=16)
00:00:03.645   BootDevice0    <string>  = "FLOPPY" (cch=7)
00:00:03.645   BootDevice1    <string>  = "DVD" (cch=4)
00:00:03.645   BootDevice2    <string>  = "IDE" (cch=4)
00:00:03.645   BootDevice3    <string>  = "NONE" (cch=5)
00:00:03.645 
00:00:03.645 [/Devices/8237A/] (level 2)
00:00:03.645 
00:00:03.645 [/Devices/8237A/0/] (level 3)
00:00:03.645   Trusted <integer> = 0x0000000000000001 (1)
00:00:03.645 
00:00:03.645 [/Devices/pci/] (level 2)
00:00:03.645 
00:00:03.645 [/Devices/pci/0/] (level 3)
00:00:03.645   Trusted <integer> = 0x0000000000000001 (1)
00:00:03.645 
00:00:03.645 [/Devices/pci/0/Config/] (level 4)
00:00:03.645   IOAPIC <integer> = 0x0000000000000000 (0)
00:00:03.645 
00:00:03.645 [/Devices/pckbd/] (level 2)
00:00:03.645 
00:00:03.645 [/Devices/pckbd/0/] (level 3)
00:00:03.645   Trusted <integer> = 0x0000000000000001 (1)
00:00:03.645 
00:00:03.645 [/Devices/pckbd/0/Config/] (level 4)
00:00:03.645 
00:00:03.645 [/Devices/pckbd/0/LUN#0/] (level 4)
00:00:03.645   Driver <string>  = "KeyboardQueue" (cch=14)
00:00:03.645 
00:00:03.645 [/Devices/pckbd/0/LUN#0/Config/] (level 5)
00:00:03.645   QueueSize <integer> = 0x0000000000000040 (64)
00:00:03.645 
00:00:03.645 [/Devices/pckbd/0/LUN#0/AttachedDriver/] (level 5)
00:00:03.645   Driver <string>  = "MainKeyboard" (cch=13)
00:00:03.645 
00:00:03.645 [/Devices/pckbd/0/LUN#0/AttachedDriver/Config/] (level 6)
00:00:03.645   Object <integer> = 0x0000000009c08750 (163612496)
00:00:03.645 
00:00:03.645 [/Devices/pckbd/0/LUN#1/] (level 4)
00:00:03.645   Driver <string>  = "MouseQueue" (cch=11)
00:00:03.645 
00:00:03.645 [/Devices/pckbd/0/LUN#1/Config/] (level 5)
00:00:03.645   QueueSize <integer> = 0x0000000000000080 (128)
00:00:03.645 
00:00:03.645 [/Devices/pckbd/0/LUN#1/AttachedDriver/] (level 5)
00:00:03.646   Driver <string>  = "MainMouse" (cch=10)
00:00:03.646 
00:00:03.646 [/Devices/pckbd/0/LUN#1/AttachedDriver/Config/] (level 6)
00:00:03.646   Object <integer> = 0x0000000009c08858 (163612760)
00:00:03.646 
00:00:03.646 [/Devices/i82078/] (level 2)
00:00:03.646 
00:00:03.646 [/Devices/i82078/0/] (level 3)
00:00:03.646   Trusted <integer> = 0x0000000000000001 (1)
00:00:03.646 
00:00:03.646 [/Devices/i82078/0/Config/] (level 4)
00:00:03.646   IRQ       <integer> = 0x0000000000000006 (6)
00:00:03.646   DMA       <integer> = 0x0000000000000002 (2)
00:00:03.646   MemMapped <integer> = 0x0000000000000000 (0)
00:00:03.646   IOBase    <integer> = 0x00000000000003f0 (1008)
00:00:03.646 
00:00:03.646 [/Devices/i82078/0/LUN#999/] (level 4)
00:00:03.646   Driver <string>  = "MainStatus" (cch=11)
00:00:03.646 
00:00:03.646 [/Devices/i82078/0/LUN#999/Config/] (level 5)
00:00:03.646   papLeds <integer> = 0x0000000009c082c8 (163611336)
00:00:03.646   First   <integer> = 0x0000000000000000 (0)
00:00:03.646   Last    <integer> = 0x0000000000000000 (0)
00:00:03.646 
00:00:03.646 [/Devices/i82078/0/LUN#0/] (level 4)
00:00:03.646   Driver <string>  = "Block" (cch=6)
00:00:03.646 
00:00:03.646 [/Devices/i82078/0/LUN#0/Config/] (level 5)
00:00:03.646   Type      <string>  = "Floppy 1.44" (cch=12)
00:00:03.646   Mountable <integer> = 0x0000000000000001 (1)
00:00:03.646 
00:00:03.646 [/Devices/acpi/] (level 2)
00:00:03.646 
00:00:03.646 [/Devices/acpi/0/] (level 3)
00:00:03.646   Trusted       <integer> = 0x0000000000000001 (1)
00:00:03.646   PCIDeviceNo   <integer> = 0x0000000000000007 (7)
00:00:03.646   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:03.646 
00:00:03.646 [/Devices/acpi/0/Config/] (level 4)
00:00:03.646   RamSize    <integer> = 0x0000000022800000 (578813952)
00:00:03.646   IOAPIC     <integer> = 0x0000000000000000 (0)
00:00:03.646   FdcEnabled <integer> = 0x0000000000000001 (1)
00:00:03.646 
00:00:03.646 [/Devices/acpi/0/LUN#0/] (level 4)
00:00:03.646   Driver <string>  = "ACPIHost" (cch=9)
00:00:03.646 
00:00:03.646 [/Devices/acpi/0/LUN#0/Config/] (level 5)
00:00:03.646 
00:00:03.646 [/Devices/i8254/] (level 2)
00:00:03.646 
00:00:03.646 [/Devices/i8254/0/] (level 3)
00:00:03.646 
00:00:03.646 [/Devices/i8254/0/Config/] (level 4)
00:00:03.646 
00:00:03.646 [/Devices/i8259/] (level 2)
00:00:03.646 
00:00:03.646 [/Devices/i8259/0/] (level 3)
00:00:03.646   Trusted <integer> = 0x0000000000000001 (1)
00:00:03.646 
00:00:03.646 [/Devices/i8259/0/Config/] (level 4)
00:00:03.646 
00:00:03.646 [/Devices/apic/] (level 2)
00:00:03.646 
00:00:03.646 [/Devices/apic/0/] (level 3)
00:00:03.647   Trusted <integer> = 0x0000000000000001 (1)
00:00:03.647 
00:00:03.647 [/Devices/apic/0/Config/] (level 4)
00:00:03.647   IOAPIC <integer> = 0x0000000000000000 (0)
00:00:03.647 
00:00:03.647 [/Devices/mc146818/] (level 2)
00:00:03.647 
00:00:03.647 [/Devices/mc146818/0/] (level 3)
00:00:03.647 
00:00:03.647 [/Devices/mc146818/0/Config/] (level 4)
00:00:03.647 
00:00:03.647 [/Devices/vga/] (level 2)
00:00:03.647 
00:00:03.647 [/Devices/vga/0/] (level 3)
00:00:03.647   Trusted       <integer> = 0x0000000000000001 (1)
00:00:03.647   PCIDeviceNo   <integer> = 0x0000000000000002 (2)
00:00:03.647   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:03.647 
00:00:03.647 [/Devices/vga/0/Config/] (level 4)
00:00:03.647   VRamSize         <integer> = 0x0000000000800000 (8388608)
00:00:03.647   FadeIn           <integer> = 0x0000000000000001 (1)
00:00:03.647   FadeOut          <integer> = 0x0000000000000001 (1)
00:00:03.647   LogoTime         <integer> = 0x0000000000000000 (0)
00:00:03.647   LogoFile         <string>  = "" (cch=1)
00:00:03.647   ShowBootMenu     <integer> = 0x0000000000000002 (2)
00:00:03.647   CustomVideoModes <integer> = 0x0000000000000000 (0)
00:00:03.647   HeightReduction  <integer> = 0x0000000000000000 (0)
00:00:03.647 
00:00:03.647 [/Devices/vga/0/LUN#0/] (level 4)
00:00:03.647   Driver <string>  = "MainDisplay" (cch=12)
00:00:03.647 
00:00:03.647 [/Devices/vga/0/LUN#0/Config/] (level 5)
00:00:03.647   Object <integer> = 0x0000000009c08958 (163613016)
00:00:03.647 
00:00:03.647 [/Devices/piix3ide/] (level 2)
00:00:03.647 
00:00:03.647 [/Devices/piix3ide/0/] (level 3)
00:00:03.647   Trusted       <integer> = 0x0000000000000001 (1)
00:00:03.647   PCIDeviceNo   <integer> = 0x0000000000000001 (1)
00:00:03.647   PCIFunctionNo <integer> = 0x0000000000000001 (1)
00:00:03.647 
00:00:03.647 [/Devices/piix3ide/0/Config/] (level 4)
00:00:03.647   PIIX4 <integer> = 0x0000000000000001 (1)
00:00:03.647 
00:00:03.647 [/Devices/piix3ide/0/LUN#999/] (level 4)
00:00:03.647   Driver <string>  = "MainStatus" (cch=11)
00:00:03.647 
00:00:03.647 [/Devices/piix3ide/0/LUN#999/Config/] (level 5)
00:00:03.647   papLeds <integer> = 0x0000000009c082d0 (163611344)
00:00:03.647   First   <integer> = 0x0000000000000000 (0)
00:00:03.647   Last    <integer> = 0x0000000000000003 (3)
00:00:03.647 
00:00:03.647 [/Devices/piix3ide/0/LUN#0/] (level 4)
00:00:03.647   Driver <string>  = "Block" (cch=6)
00:00:03.647 
00:00:03.647 [/Devices/piix3ide/0/LUN#0/Config/] (level 5)
00:00:03.647   Type      <string>  = "HardDisk" (cch=9)
00:00:03.647   Mountable <integer> = 0x0000000000000000 (0)
00:00:03.647 
00:00:03.647 [/Devices/piix3ide/0/LUN#0/AttachedDriver/] (level 5)
00:00:03.647   Driver <string>  = "VBoxHDD" (cch=8)
00:00:03.647 
00:00:03.647 [/Devices/piix3ide/0/LUN#0/AttachedDriver/Config/] (level 6)
00:00:03.647   Path <string>  = "/home/maciej/.VirtualBox/VDI/DebianHardDisk.vdi" (cch=48)
00:00:03.647 
00:00:03.647 [/Devices/piix3ide/0/LUN#2/] (level 4)
00:00:03.648   Driver <string>  = "Block" (cch=6)
00:00:03.648 
00:00:03.648 [/Devices/piix3ide/0/LUN#2/Config/] (level 5)
00:00:03.648   Type      <string>  = "DVD" (cch=4)
00:00:03.648   Mountable <integer> = 0x0000000000000001 (1)
00:00:03.648 
00:00:03.648 [/Devices/piix3ide/0/LUN#2/AttachedDriver/] (level 5)
00:00:03.648   Driver <string>  = "MediaISO" (cch=9)
00:00:03.648 
00:00:03.648 [/Devices/piix3ide/0/LUN#2/AttachedDriver/Config/] (level 6)
00:00:03.648   Path <string>  = "/home/maciej/.VirtualBox/VBoxGuestAdditions_1.6.6.iso" (cch=54)
00:00:03.648 
00:00:03.648 [/Devices/pcnet/] (level 2)
00:00:03.648 
00:00:03.648 [/Devices/pcnet/0/] (level 3)
00:00:03.648   Trusted       <integer> = 0x0000000000000001 (1)
00:00:03.648   PCIDeviceNo   <integer> = 0x0000000000000003 (3)
00:00:03.648   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:03.648 
00:00:03.648 [/Devices/pcnet/0/Config/] (level 4)
00:00:03.648   Am79C973       <integer> = 0x0000000000000001 (1)
00:00:03.648   MAC            <bytes>   = "08 00 27 a8 bc fc" (cb=6)
00:00:03.648   CableConnected <integer> = 0x0000000000000001 (1)
00:00:03.648   LineSpeed      <integer> = 0x0000000000000000 (0)
00:00:03.648 
00:00:03.648 [/Devices/pcnet/0/LUN#999/] (level 4)
00:00:03.648   Driver <string>  = "MainStatus" (cch=11)
00:00:03.648 
00:00:03.648 [/Devices/pcnet/0/LUN#999/Config/] (level 5)
00:00:03.648   papLeds <integer> = 0x0000000009c08358 (163611480)
00:00:03.648 
00:00:03.648 [/Devices/pcnet/0/LUN#0/] (level 4)
00:00:03.648   Driver <string>  = "NAT" (cch=4)
00:00:03.648 
00:00:03.648 [/Devices/pcnet/0/LUN#0/Config/] (level 5)
00:00:03.648   TFTPPrefix <string>  = "/home/maciej/.VirtualBox/TFTP" (cch=30)
00:00:03.648   BootFile   <string>  = "Debian.pxe" (cch=11)
00:00:03.648 
00:00:03.648 [/Devices/serial/] (level 2)
00:00:03.648 
00:00:03.648 [/Devices/parallel/] (level 2)
00:00:03.648 
00:00:03.648 [/Devices/VMMDev/] (level 2)
00:00:03.648 
00:00:03.648 [/Devices/VMMDev/0/] (level 3)
00:00:03.648   Trusted       <integer> = 0x0000000000000001 (1)
00:00:03.648   PCIDeviceNo   <integer> = 0x0000000000000004 (4)
00:00:03.648   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:03.648 
00:00:03.648 [/Devices/VMMDev/0/Config/] (level 4)
00:00:03.648 
00:00:03.648 [/Devices/VMMDev/0/LUN#0/] (level 4)
00:00:03.648   Driver <string>  = "MainVMMDev" (cch=11)
00:00:03.648 
00:00:03.648 [/Devices/VMMDev/0/LUN#0/Config/] (level 5)
00:00:03.648   Object <integer> = 0x0000000009c08e58 (163614296)
00:00:03.648 
00:00:03.648 [/Devices/VMMDev/0/LUN#999/] (level 4)
00:00:03.648   Driver <string>  = "MainStatus" (cch=11)
00:00:03.648 
00:00:03.648 [/Devices/VMMDev/0/LUN#999/Config/] (level 5)
00:00:03.648   papLeds <integer> = 0x0000000009c08378 (163611512)
00:00:03.648   First   <integer> = 0x0000000000000000 (0)
00:00:03.648   Last    <integer> = 0x0000000000000000 (0)
00:00:03.649 
00:00:03.649 [/Devices/AudioSniffer/] (level 2)
00:00:03.649 
00:00:03.649 [/Devices/AudioSniffer/0/] (level 3)
00:00:03.649 
00:00:03.649 [/Devices/AudioSniffer/0/Config/] (level 4)
00:00:03.649 
00:00:03.649 [/Devices/AudioSniffer/0/LUN#0/] (level 4)
00:00:03.649   Driver <string>  = "MainAudioSniffer" (cch=17)
00:00:03.649 
00:00:03.649 [/Devices/AudioSniffer/0/LUN#0/Config/] (level 5)
00:00:03.649   Object <integer> = 0x0000000009c08ee8 (163614440)
00:00:03.649 
00:00:03.649 [/TM/] (level 1)
00:00:03.649   UTCOffset <integer> = 0x0000000000000000 (0)
00:00:03.649 
00:00:03.649 ********************* End of CFGM dump **********************
00:00:03.653 Logical host processors: 2, processor active mask: 00000003
00:00:03.653 ************************* CPUID dump ************************
00:00:03.653          RAW Standard CPUIDs
00:00:03.653      Function  eax      ebx      ecx      edx
00:00:03.653 Gst: 00000000  00000002 756e6547 6c65746e 49656e69
00:00:03.653 Hst:           00000005 756e6547 6c65746e 49656e69
00:00:03.653 Gst: 00000001  00000f47 00000800 00000008 0788a1bf
00:00:03.653 Hst:           00000f47 01020800 0000651d bfebfbff
00:00:03.653 Gst: 00000002  605b5101 00000000 00000000 007c7040
00:00:03.653 Hst:           605b5101 00000000 00000000 007c7040
00:00:03.653 Gst: 00000003  00000040 00000040 00000000 00000000*
00:00:03.653 Hst:           00000000 00000000 00000000 00000000
00:00:03.653 Gst: 00000004  00000000 00000040 00000000 00000000*
00:00:03.653 Hst:           04000121 01c0003f 0000001f 00000000
00:00:03.653 Name:                            GenuineIntel
00:00:03.653 Supports:                        0-2
00:00:03.653 Family:                          15  	Extended: 0 	Effectiv: 15
00:00:03.653 Model:                           4  	Extended: 0 	Effectiv: 4
00:00:03.653 Stepping:                        7
00:00:03.653 APIC ID:                         0x00
00:00:03.653 Logical CPUs:                    0
00:00:03.653 CLFLUSH Size:                    8
00:00:03.653 Brand ID:                        0x00
00:00:03.653 Mnemonic - Description                 = guest (host)
00:00:03.653 FPU - x87 FPU on Chip                  = 1 (1)
00:00:03.653 VME - Virtual 8086 Mode Enhancements   = 1 (1)
00:00:03.653 DE - Debugging extensions              = 1 (1)
00:00:03.653 PSE - Page Size Extension              = 1 (1)
00:00:03.653 TSC - Time Stamp Counter               = 1 (1)
00:00:03.653 MSR - Model Specific Registers         = 1 (1)
00:00:03.653 PAE - Physical Address Extension       = 0 (1)
00:00:03.653 MCE - Machine Check Exception          = 1 (1)
00:00:03.653 CX8 - CMPXCHG8B instruction            = 1 (1)
00:00:03.653 APIC - APIC On-Chip                    = 0 (1)
00:00:03.653 Reserved                               = 0 (0)
00:00:03.653 SEP - SYSENTER and SYSEXIT             = 0 (1)
00:00:03.653 MTRR - Memory Type Range Registers     = 0 (1)
00:00:03.653 PGE - PTE Global Bit                   = 1 (1)
00:00:03.653 MCA - Machine Check Architecture       = 0 (1)
00:00:03.653 CMOV - Conditional Move Instructions   = 1 (1)
00:00:03.653 PAT - Page Attribute Table             = 0 (1)
00:00:03.653 PSE-36 - 36-bit Page Size Extention    = 0 (1)
00:00:03.653 PSN - Processor Serial Number          = 0 (0)
00:00:03.653 CLFSH - CLFLUSH Instruction.           = 1 (1)
00:00:03.653 Reserved                               = 0 (0)
00:00:03.653 DS - Debug Store                       = 0 (1)
00:00:03.653 ACPI - Thermal Mon. & Soft. Clock Ctrl.= 0 (1)
00:00:03.653 MMX - Intel MMX Technology             = 1 (1)
00:00:03.653 FXSR - FXSAVE and FXRSTOR Instructions = 1 (1)
00:00:03.653 SSE - SSE Support                      = 1 (1)
00:00:03.653 SSE2 - SSE2 Support                    = 1 (1)
00:00:03.653 SS - Self Snoop                        = 0 (1)
00:00:03.653 HTT - Hyper-Threading Technolog        = 0 (1)
00:00:03.653 TM - Thermal Monitor                   = 0 (1)
00:00:03.653 30 - Reserved                          = 0 (0)
00:00:03.653 PBE - Pending Break Enable             = 0 (1)
00:00:03.653 Supports SSE3 or not                   = 0 (1)
00:00:03.653 Reserved                               = 0 (2)
00:00:03.653 Supports MONITOR/MWAIT                 = 1 (1)
00:00:03.653 CPL-DS - CPL Qualified Debug Store     = 0 (1)
00:00:03.653 VMX - Virtual Machine Technology       = 0 (0)
00:00:03.653 Reserved                               = 0 (0)
00:00:03.653 Enhanced SpeedStep Technology          = 0 (0)
00:00:03.653 Terminal Monitor 2                     = 0 (1)
00:00:03.653 Supports Supplemental SSE3 or not      = 0 (0)
00:00:03.653 L1 Context ID                          = 0 (1)
00:00:03.653 Reserved                               = 0x0 (0x0)
00:00:03.653 CMPXCHG16B                             = 0 (1)
00:00:03.653 xTPR Update Control                    = 0 (1)
00:00:03.653 Reserved                               = 0x0 (0x0)
00:00:03.653 
00:00:03.653          RAW Extended CPUIDs
00:00:03.653      Function  eax      ebx      ecx      edx
00:00:03.653 Gst: 80000000  80000004 00000000 00000000 00000000
00:00:03.653 Hst:           80000008 00000000 00000000 00000000
00:00:03.653 Gst: 80000001  00000000 00000000 00000000 00000000
00:00:03.653 Hst:           00000000 00000000 00000001 20000000
00:00:03.653 Gst: 80000002  20202020 20202020 20202020 746e4920
00:00:03.653 Hst:           20202020 20202020 20202020 746e4920
00:00:03.653 Gst: 80000003  52286c65 65502029 7569746e 2952286d
00:00:03.653 Hst:           52286c65 65502029 7569746e 2952286d
00:00:03.653 Gst: 80000004  20204420 20555043 36362e32 007a4847
00:00:03.653 Hst:           20204420 20555043 36362e32 007a4847
00:00:03.653 Gst: 80000005  00000040 00000040 00000000 00000000*
00:00:03.653 Hst:           00000000 00000000 00000000 00000000
00:00:03.653 Gst: 80000006  00000040 00000040 00000000 00000000*
00:00:03.653 Hst:           00000000 00000000 04006040 00000000
00:00:03.653 Gst: 80000007  00000040 00000040 00000000 00000000*
00:00:03.653 Hst:           00000000 00000000 00000000 00000000
00:00:03.653 Gst: 80000008  00000040 00000040 00000000 00000000*
00:00:03.653 Hst:           00003024 00000000 00000000 00000000
00:00:03.653 Gst: 80000009  00000040 00000040 00000000 00000000*
00:00:03.653 Hst:           00000040 00000040 00000000 00000000
00:00:03.653 Ext Name:                        
00:00:03.653 Ext Supports:                    0x80000000-0x80000004
00:00:03.653 Family:                          0  	Extended: 0 	Effectiv: 0
00:00:03.653 Model:                           0  	Extended: 0 	Effectiv: 0
00:00:03.653 Stepping:                        0
00:00:03.653 Brand ID:                        0x000
00:00:03.653 Mnemonic - Description                 = guest (host)
00:00:03.654 FPU - x87 FPU on Chip                  = 0 (0)
00:00:03.654 VME - Virtual 8086 Mode Enhancements   = 0 (0)
00:00:03.654 DE - Debugging extensions              = 0 (0)
00:00:03.654 PSE - Page Size Extension              = 0 (0)
00:00:03.654 TSC - Time Stamp Counter               = 0 (0)
00:00:03.654 MSR - K86 Model Specific Registers     = 0 (0)
00:00:03.654 PAE - Physical Address Extension       = 0 (0)
00:00:03.654 MCE - Machine Check Exception          = 0 (0)
00:00:03.654 CX8 - CMPXCHG8B instruction            = 0 (0)
00:00:03.654 APIC - APIC On-Chip                    = 0 (0)
00:00:03.654 10 - Reserved                          = 0 (0)
00:00:03.654 SEP - SYSCALL and SYSRET               = 0 (0)
00:00:03.654 MTRR - Memory Type Range Registers     = 0 (0)
00:00:03.654 PGE - PTE Global Bit                   = 0 (0)
00:00:03.654 MCA - Machine Check Architecture       = 0 (0)
00:00:03.654 CMOV - Conditional Move Instructions   = 0 (0)
00:00:03.654 PAT - Page Attribute Table             = 0 (0)
00:00:03.654 PSE-36 - 36-bit Page Size Extention    = 0 (0)
00:00:03.654 18 - Reserved                          = 0 (0)
00:00:03.654 19 - Reserved                          = 0 (0)
00:00:03.654 NX - No-Execute Page Protection        = 0 (0)
00:00:03.654 DS - Debug Store                       = 0 (0)
00:00:03.654 AXMMX - AMD Extensions to MMX Instr.   = 0 (0)
00:00:03.654 MMX - Intel MMX Technology             = 0 (0)
00:00:03.654 FXSR - FXSAVE and FXRSTOR Instructions = 0 (0)
00:00:03.654 25 - AMD fast FXSAVE and FXRSTOR Instr.= 0 (0)
00:00:03.654 26 - 1 GB large page support           = 0 (0)
00:00:03.654 27 - RDTSCP instruction                = 0 (0)
00:00:03.654 28 - Reserved                          = 0 (0)
00:00:03.654 29 - AMD Long Mode                     = 0 (1)
00:00:03.654 30 - AMD Extensions to 3DNow           = 0 (0)
00:00:03.654 31 - AMD 3DNow                         = 0 (0)
00:00:03.654 LahfSahf - LAHF/SAHF in 64-bit mode    = 0 (1)
00:00:03.654 CmpLegacy - Core MP legacy mode (depr) = 0 (0)
00:00:03.654 SVM - AMD VM Extensions                = 0 (0)
00:00:03.654 APIC registers starting at 0x400       = 0 (0)
00:00:03.654 AltMovCR8 - LOCK MOV CR0 means MOV CR8 = 0 (0)
00:00:03.654 Advanced bit manipulation              = 0 (0)
00:00:03.654 SSE4A instruction support              = 0 (0)
00:00:03.654 Misaligned SSE mode                    = 0 (0)
00:00:03.654 PREFETCH and PREFETCHW instruction     = 0 (0)
00:00:03.654 OS visible workaround                  = 0 (0)
00:00:03.654 Instruction based sampling             = 0 (0)
00:00:03.654 SSE5 support                           = 0 (0)
00:00:03.654 SKINIT, STGI, and DEV support          = 0 (0)
00:00:03.654 Watchdog timer support.                = 0 (0)
00:00:03.654 31:14 - Reserved                       = 0x0 (0x0)
00:00:03.654 Full Name:                                    Intel(R) Pentium(R) D  CPU 2.66GHz
00:00:03.654 
00:00:03.654          RAW Centaur CPUIDs
00:00:03.654      Function  eax      ebx      ecx      edx
00:00:03.654 Gst: c0000000  00000040 00000040 00000000 00000000
00:00:03.654 Hst:           00000040 00000040 00000000 00000000
00:00:03.654 Gst: c0000001  00000040 00000040 00000000 00000000
00:00:03.654 Hst:           00000040 00000040 00000000 00000000
00:00:03.654 Gst: c0000002  00000040 00000040 00000000 00000000
00:00:03.654 Hst:           00000040 00000040 00000000 00000000
00:00:03.654 Gst: c0000003  00000040 00000040 00000000 00000000
00:00:03.654 Hst:           00000040 00000040 00000000 00000000
00:00:03.654 Centaur Supports:                0xc0000000-0x00000040
00:00:03.654 Mnemonic - Description                 = guest (host)
00:00:03.654 AIS - Alternate Instruction Set        = 0 (0)
00:00:03.654 AIS-E - AIS enabled                    = 0 (0)
00:00:03.654 RNG - Random Number Generator          = 0 (0)
00:00:03.654 RNG-E - RNG enabled                    = 0 (0)
00:00:03.654 LH - LongHaul MSR 0000_110Ah           = 0 (0)
00:00:03.654 FEMMS - FEMMS                          = 0 (0)
00:00:03.654 ACE - Advanced Cryptography Engine     = 0 (0)
00:00:03.654 ACE-E - ACE enabled                    = 0 (0)
00:00:03.654 ACE2 - Advanced Cryptography Engine 2  = 0 (0)
00:00:03.654 ACE2-E - ACE enabled                   = 0 (0)
00:00:03.654 PHE - Hash Engine                      = 0 (0)
00:00:03.654 PHE-E - PHE enabled                    = 0 (0)
00:00:03.654 PMM - Montgomery Multiplier            = 0 (0)
00:00:03.654 PMM-E - PMM enabled                    = 0 (0)
00:00:03.654 
00:00:03.654 
00:00:03.654 ******************** End of CPUID dump **********************
00:00:03.704 TM: cTSCTicksPerSecond=0x9e8dc090 (2660090000) fTSCVirtualized=true  fTSCUseRealTSC=false fMaybeUseOffsettedHostTSC=true 
00:00:03.704 CoreCode: R3=b776f000 R0=f8c30000 GC=a03c3000 Phys=0000000023c8a000 cb=0x2000
00:00:03.764 SUP: Loaded VBoxDDR0.r0 (/usr/lib/virtualbox/VBoxDDR0.r0) at 0xf8c33060 - ModuleInit at 00000000 and ModuleTerm at 00000000
00:00:03.768 SUP: Loaded VBoxDD2R0.r0 (/usr/lib/virtualbox/VBoxDD2R0.r0) at 0xf8c3d060 - ModuleInit at 00000000 and ModuleTerm at 00000000
00:00:03.768 Activating Local APIC
00:00:03.768 PIT: mode=3 count=0x10000 (65536) - 18.20 Hz (ch=0)
00:00:03.784 Shared Folders service loaded.
00:00:03.787 PIIX3 ATA: LUN#0: disk, PCHS=16383/16/63, total number of sectors 43753472
00:00:03.787 PIIX3 ATA: LUN#1: no unit
00:00:03.787 PIIX3 ATA: LUN#2: CD/DVD, total number of sectors 0, passthrough disabled
00:00:03.787 PIIX3 ATA: LUN#3: no unit
00:00:03.787 PIIX3 ATA: Ctl#0: finished processing RESET
00:00:03.887 PIIX3 ATA: Ctl#1: finished processing RESET
00:00:03.988 NAT: DNS address: 192.168.0.1
00:00:03.991 DevPcBios: ATA LUN#0 LCHS=1024/255/63
00:00:04.000 HWACCM: No VMX or SVM CPU extension found. Reason VERR_VMX_NO_VMX
00:00:04.000 HWACCM: VMX MSR_IA32_FEATURE_CONTROL=0
00:00:04.008 VM: Halt method global1 (5)
00:00:04.008 Changing the VM state from 'CREATING' to 'CREATED'.
00:00:04.008 Changing the VM state from 'CREATED' to 'RUNNING'.
00:00:04.030 Guest Log: BIOS: VirtualBox 1.6.6_OSE
00:00:04.030 PIT: mode=2 count=0x10000 (65536) - 18.20 Hz (ch=0)
00:00:04.053 PIIX3 ATA: Ctl#0: RESET, DevSel=0 AIOIf=0 CmdIf0=0x00 (-1 usec ago) CmdIf1=0x00 (-1 usec ago)
00:00:04.053 PIIX3 ATA: Ctl#0: finished processing RESET
00:00:04.054 Guest Log: BIOS: ata0-0: PCHS=16383/16/63 LCHS=1024/255/63
00:00:04.055 PIIX3 ATA: Ctl#1: RESET, DevSel=0 AIOIf=0 CmdIf0=0x00 (-1 usec ago) CmdIf1=0x00 (-1 usec ago)
00:00:04.055 PIIX3 ATA: Ctl#1: finished processing RESET
00:00:04.056 PIT: mode=2 count=0x48d3 (18643) - 64.00 Hz (ch=0)
00:00:04.070 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=b1ba4000 w=640 h=480 bpp=32 cbLine=0xA00
00:00:06.534 PIT: mode=2 count=0x10000 (65536) - 18.20 Hz (ch=0)
00:00:06.535 Guest Log: BIOS: Boot from Floppy 0 failed
00:00:06.536 PIIX3 ATA: LUN#2: CD-ROM block number 18 invalid (READ)
00:00:06.537 Guest Log: BIOS: CDROM boot failure code : 0003
00:00:06.537 Guest Log: BIOS: Boot from CD-ROM failed
00:00:06.537 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=00000000 w=720 h=400 bpp=0 cbLine=0x0
00:00:06.547 Guest Log: BIOS: Booting from Hard Disk...
00:00:06.561 PIIX3 ATA: Ctl#0: RESET, DevSel=0 AIOIf=0 CmdIf0=0x20 (-1 usec ago) CmdIf1=0x00 (-1 usec ago)
00:00:06.561 PIIX3 ATA: Ctl#0: finished processing RESET
00:00:09.645 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=b1ba4000 w=640 h=480 bpp=32 cbLine=0xA00
00:00:09.855 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=b1ba4000 w=640 h=480 bpp=32 cbLine=0xA00
00:00:14.535 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=b1ba4000 w=640 h=480 bpp=32 cbLine=0xA00
00:00:15.395 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=b1ba4000 w=640 h=480 bpp=32 cbLine=0xA00
00:00:15.715 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=b1ba4000 w=640 h=480 bpp=32 cbLine=0xA00
00:00:15.735 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=b1ba4000 w=640 h=480 bpp=32 cbLine=0xA00
00:00:16.735 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=b1ba4000 w=640 h=480 bpp=32 cbLine=0xA00
00:00:17.735 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=b1ba4000 w=640 h=480 bpp=32 cbLine=0xA00
00:00:18.735 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=b1ba4000 w=640 h=480 bpp=32 cbLine=0xA00
00:00:19.735 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=b1ba4000 w=640 h=480 bpp=32 cbLine=0xA00
00:00:20.155 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=b1ba4000 w=640 h=480 bpp=32 cbLine=0xA00
00:00:20.895 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=b1ba4000 w=640 h=480 bpp=32 cbLine=0xA00
00:00:27.896 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=00000000 w=720 h=400 bpp=0 cbLine=0x0
00:00:31.412 PIT: mode=2 count=0x12a5 (4773) - 249.98 Hz (ch=0)
00:00:31.855 PATM: patmR3RefreshPatch: succeeded to refresh patch at c1035252 
00:00:31.856 PATM: patmR3RefreshPatch: succeeded to refresh patch at c126c74c 
00:00:31.915 PATM: patmR3RefreshPatch: succeeded to refresh patch at c1005bff 
00:00:31.919 PATM: patmR3RefreshPatch: succeeded to refresh patch at c106bceb 
00:00:31.931 PATM: patmR3RefreshPatch: succeeded to refresh patch at c100341a 
00:00:31.956 PATM: Failed to refresh dirty patch at c102da44. Disabling it.
00:00:32.191 PIT: mode=0 count=0x10000 (65536) - 18.20 Hz (ch=0)
00:00:32.207 PATM: Disabling IDT ef patch handler c1003b04
00:00:32.207 PATM: patmR3RefreshPatch: succeeded to refresh patch at c1003b04 
00:00:33.730 PATM: Disable block at c13c87ce - write c13c883d-c13c8841
00:00:33.731 PATM: Disable block at c13c940e - write c13c948b-c13c948f
00:00:33.732 PATM: Disable block at c13e259b - write c13e260d-c13e2611
00:00:33.732 PATM: Disable block at c13e278d - write c13e27f7-c13e27fb
00:00:33.732 PATM: Disable block at c13e4e48 - write c13e4ea9-c13e4ead
00:00:33.777 PATM: patmR3RefreshPatch: succeeded to refresh patch at c102b320 
00:00:33.780 PATM: patmR3RefreshPatch: succeeded to refresh patch at c102b0f6 
00:00:34.314 PATM: Disabling IDT e patch handler c126c9c8
00:00:34.314 PATM: patmR3RefreshPatch: succeeded to refresh patch at c126c9c8 
00:00:35.192 PIIX3 ATA: Ctl#0: RESET, DevSel=0 AIOIf=0 CmdIf0=0x20 (-1 usec ago) CmdIf1=0x00 (-1 usec ago)
00:00:35.192 PIIX3 ATA: Ctl#0: finished processing RESET
00:00:35.194 PIIX3 ATA: Ctl#1: RESET, DevSel=0 AIOIf=0 CmdIf0=0xa0 (-1 usec ago) CmdIf1=0x00 (-1 usec ago)
00:00:35.194 PIIX3 ATA: Ctl#1: finished processing RESET
00:00:35.251 PATM: patmR3RefreshPatch: succeeded to refresh patch at c1034fa1 
00:00:35.666 PATM: Disable block at e308e3c8 - write e308e444-e308e448
00:00:51.380 PCNet#0: Init: ss32=1 GCRDRA=0x1991b000[32] GCTDRA=0x1991a000[16]
00:00:54.220 NAT: DHCP offered IP address 10.0.2.15
00:00:54.244 NAT: DHCP offered IP address 10.0.2.15
00:01:05.468 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=b1ba4000 w=640 h=400 bpp=0 cbLine=0x280
00:01:05.730 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=00000000 w=720 h=400 bpp=0 cbLine=0x0
00:01:05.837 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=b1ba4000 w=800 h=600 bpp=32 cbLine=0xC80
00:02:29.449 PIIX3 ATA: LUN#2: CD-ROM block number 17 invalid (READ)
00:02:51.026 PIIX3 ATA: LUN#2: CD-ROM block number 17 invalid (READ)
00:11:12.431 PATM: patmR3RefreshPatch: succeeded to refresh patch at c10037c0 
00:20:29.764 Changing the VM state from 'RUNNING' to 'SUSPENDED'.
00:20:30.103 Changing the VM state from 'SUSPENDED' to 'RUNNING'.


```

---

### Post by slooksterpsv on 2010-09-17
So you have the guest additions burnt to a cd? If not you can go to Devices -> Install Guest Additions at the top and it will mount the ISO file for you that contains the Guest Additions. Then in Ubuntu it should either automount or you may have to open a terminal in Ubuntu and do the following:
```

sudo mkdir /media/vbxadd
sudo mount /dev/sr0 /media/vbxadd
sudo /media/vbxadd/VBoxLinuxAdditions-(arch).run 'replacing (arch) with either x86 or amd64'

```
EDIT: Changed to Open a Terminal in Ubuntu.

---

### Post by maciejso on 2010-09-17
> **slooksterpsv said:**
> So you have the guest additions burnt to a cd? If not you can go to Devices -> Install Guest Additions at the top and it will mount the ISO file for you that contains the Guest Additions. Then in Ubuntu it should either automount or you may have to open a terminal and do the following:
```

sudo mkdir /media/vbxadd
sudo mount /dev/sr0 /media/vbxadd
sudo /media/vbxadd/VBoxLinuxAdditions-(arch).run 'replacing (arch) with either x86 or amd64'

```
That's exactly what I'm trying to do, that is , to mount an iso image with guest additions and the error message above is the one I'm getting when mounting the iso image.

---

### Post by slooksterpsv on 2010-09-17
> **maciejso said:**
> That's exactly what I'm trying to do, that is , to mount an iso image with guest additions and the error message above is the one I'm getting when mounting the iso image.
```

... ' after you mkdir /media/vbxadd
sudo mount -o loop /usr/share/virtualbox/VBoxGuestAdditions.iso /media/vbxadd

```
Is how you would mount the ISO file. You didn't specify if you already burned the additions iso file to a cd.

And this isn't going to help to mount it in your debian either, you'll want to do it through Device -> Install Guest Additions in the virtualbox window. Or follow the steps above to mount it in Ubuntu (running the commands in a terminal in Ubuntu)

Unless you're going to share a folder from debian that ubuntu can access to get the additions.

---

