---
title: "Ubuntu host, WinXP geust- &quot;aborted&quot;?"
date: 2007-12-05
forum: Virtualisation
---

### Post by painterh on 2007-12-05
I have VirtualBox 1.52 installed on Ubuntu 7.10.  I was able to successfully install Windows XP sp2 in a virtual machine, and was even able to get Microsoft to activate it when I have the same copy installed on my other hard drive (dual boot).
The problem is yesterday it became unresponsive after I changed the monitor resolution higher, so I checked the settings for the virtual machine and realized I had allocated more ram for the virtual machine and video memory than I had in my system, (I know, pretty dumb mistake).  Hence I tried to shut down the XP machine using "start menu-programs-shutdown", and it seemed to shutdown alright.  However now when I open VirtualBox,  the XP virtual machine says "aborted" instead of "powered off".  I am not even able to start it.  I made a copy of my log file, so if anyone has a clue as to what happened, and more importantly,, is it salvagable.  Here is the log file;

00:00:08.804 VirtualBox 1.5.2 r25433 linux.x86 (Oct 18 2007 08:59:10) release log
00:00:08.804 Log opened 2007-12-05T06:12:18.868591000Z
00:00:08.845 vboxClipboardInit: initializing host clipboard
00:00:08.845 vboxClipboardThread: starting clipboard thread
00:00:08.872 VBoxSharedClipboard mode: Bidirectional
00:00:08.991 ************************* CFGM dump *************************
00:00:08.991 pRoot=083380a0:{/}
00:00:08.991 [/] (level 0)
00:00:08.992   Name         <string>  = "XP2" (cch=4)
00:00:08.992   UUID         <bytes>   = "31 1d 51 e0 7d 81 f2 4d b1 a2 7b 5a b2 ee 2d 49" (cb=16)
00:00:08.992   RamSize      <integer> = 0x000000002be00000 (736100352)
00:00:08.992   TimerMillies <integer> = 0x000000000000000a (10)
00:00:08.992   RawR3Enabled <integer> = 0x0000000000000001 (1)
00:00:08.992   RawR0Enabled <integer> = 0x0000000000000001 (1)
00:00:08.992   PATMEnabled  <integer> = 0x0000000000000001 (1)
00:00:08.992   CSAMEnabled  <integer> = 0x0000000000000001 (1)
00:00:08.992 
00:00:08.992 [/PDM/] (level 1)
00:00:08.992 
00:00:08.992 [/PDM/Drivers/] (level 2)
00:00:08.992 
00:00:08.992 [/PDM/Drivers/VBoxC/] (level 3)
00:00:08.992   Path <string>  = "/usr/lib/virtualbox/components/VBoxC" (cch=37)
00:00:08.992 
00:00:08.992 [/Devices/] (level 1)
00:00:08.992 
00:00:08.992 [/Devices/pcarch/] (level 2)
00:00:08.992 
00:00:08.992 [/Devices/pcarch/0/] (level 3)
00:00:08.992   Trusted <integer> = 0x0000000000000001 (1)
00:00:08.992 
00:00:08.992 [/Devices/pcarch/0/Config/] (level 4)
00:00:08.992 
00:00:08.992 [/Devices/pcbios/] (level 2)
00:00:08.992 
00:00:08.992 [/Devices/pcbios/0/] (level 3)
00:00:08.992   Trusted <integer> = 0x0000000000000001 (1)
00:00:08.992 
00:00:08.992 [/Devices/pcbios/0/Config/] (level 4)
00:00:08.992   RamSize        <integer> = 0x000000002be00000 (736100352)
00:00:08.992   HardDiskDevice <string>  = "piix3ide" (cch=9)
00:00:08.992   FloppyDevice   <string>  = "i82078" (cch=7)
00:00:08.992   IOAPIC         <integer> = 0x0000000000000001 (1)
00:00:08.992   PXEDebug       <integer> = 0x0000000000000000 (0)
00:00:08.992   UUID           <bytes>   = "31 1d 51 e0 7d 81 f2 4d b1 a2 7b 5a b2 ee 2d 49" (cb=16)
00:00:08.992   BootDevice0    <string>  = "FLOPPY" (cch=7)
00:00:08.992   BootDevice1    <string>  = "DVD" (cch=4)
00:00:08.992   BootDevice2    <string>  = "IDE" (cch=4)
00:00:08.992   BootDevice3    <string>  = "NONE" (cch=5)
00:00:08.992   FadeIn         <integer> = 0x0000000000000001 (1)
00:00:08.992   FadeOut        <integer> = 0x0000000000000001 (1)
00:00:08.992   LogoTime       <integer> = 0x0000000000000000 (0)
00:00:08.992   LogoFile       <string>  = "" (cch=1)
00:00:08.992   ShowBootMenu   <integer> = 0x0000000000000002 (2)
00:00:08.992 
00:00:08.992 [/Devices/acpi/] (level 2)
00:00:08.992 
00:00:08.992 [/Devices/acpi/0/] (level 3)
00:00:08.992   Trusted       <integer> = 0x0000000000000001 (1)
00:00:08.992   PCIDeviceNo   <integer> = 0x0000000000000007 (7)
00:00:08.992   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:08.992 
00:00:08.992 [/Devices/acpi/0/Config/] (level 4)
00:00:08.992   RamSize <integer> = 0x000000002be00000 (736100352)
00:00:08.992   IOAPIC  <integer> = 0x0000000000000001 (1)
00:00:08.992 
00:00:08.992 [/Devices/acpi/0/LUN#0/] (level 4)
00:00:08.992   Driver <string>  = "ACPIHost" (cch=9)
00:00:08.992 
00:00:08.992 [/Devices/acpi/0/LUN#0/Config/] (level 5)
00:00:08.992 
00:00:08.992 [/Devices/8237A/] (level 2)
00:00:08.992 
00:00:08.992 [/Devices/8237A/0/] (level 3)
00:00:08.992   Trusted <integer> = 0x0000000000000001 (1)
00:00:08.992 
00:00:08.992 [/Devices/pci/] (level 2)
00:00:08.992 
00:00:08.992 [/Devices/pci/0/] (level 3)
00:00:08.992   Trusted <integer> = 0x0000000000000001 (1)
00:00:08.992 
00:00:08.992 [/Devices/pci/0/Config/] (level 4)
00:00:08.992   IOAPIC <integer> = 0x0000000000000001 (1)
00:00:08.992 
00:00:08.992 [/Devices/pckbd/] (level 2)
00:00:08.992 
00:00:08.992 [/Devices/pckbd/0/] (level 3)
00:00:08.992   Trusted <integer> = 0x0000000000000001 (1)
00:00:08.992 
00:00:08.992 [/Devices/pckbd/0/Config/] (level 4)
00:00:08.992 
00:00:08.992 [/Devices/pckbd/0/LUN#0/] (level 4)
00:00:08.992   Driver <string>  = "KeyboardQueue" (cch=14)
00:00:08.992 
00:00:08.992 [/Devices/pckbd/0/LUN#0/Config/] (level 5)
00:00:08.992   QueueSize <integer> = 0x0000000000000040 (64)
00:00:08.992 
00:00:08.992 [/Devices/pckbd/0/LUN#0/AttachedDriver/] (level 5)
00:00:08.992   Driver <string>  = "MainKeyboard" (cch=13)
00:00:08.992 
00:00:08.992 [/Devices/pckbd/0/LUN#0/AttachedDriver/Config/] (level 6)
00:00:08.992   Object <integer> = 0x00000000083376d0 (137590480)
00:00:08.992 
00:00:08.992 [/Devices/pckbd/0/LUN#1/] (level 4)
00:00:08.992   Driver <string>  = "MouseQueue" (cch=11)
00:00:08.992 
00:00:08.992 [/Devices/pckbd/0/LUN#1/Config/] (level 5)
00:00:08.992   QueueSize <integer> = 0x0000000000000080 (128)
00:00:08.992 
00:00:08.992 [/Devices/pckbd/0/LUN#1/AttachedDriver/] (level 5)
00:00:08.992   Driver <string>  = "MainMouse" (cch=10)
00:00:08.992 
00:00:08.992 [/Devices/pckbd/0/LUN#1/AttachedDriver/Config/] (level 6)
00:00:08.992   Object <integer> = 0x000000000833cdf0 (137612784)
00:00:08.992 
00:00:08.993 [/Devices/i82078/] (level 2)
00:00:08.993 
00:00:08.993 [/Devices/i82078/0/] (level 3)
00:00:08.993   Trusted <integer> = 0x0000000000000001 (1)
00:00:08.993 
00:00:08.993 [/Devices/i82078/0/Config/] (level 4)
00:00:08.993   IRQ       <integer> = 0x0000000000000006 (6)
00:00:08.993   DMA       <integer> = 0x0000000000000002 (2)
00:00:08.993   MemMapped <integer> = 0x0000000000000000 (0)
00:00:08.993   IOBase    <integer> = 0x00000000000003f0 (1008)
00:00:08.993 
00:00:08.993 [/Devices/i82078/0/LUN#999/] (level 4)
00:00:08.993   Driver <string>  = "MainStatus" (cch=11)
00:00:08.993 
00:00:08.993 [/Devices/i82078/0/LUN#999/Config/] (level 5)
00:00:08.993   papLeds <integer> = 0x000000000833719c (137589148)
00:00:08.993   First   <integer> = 0x0000000000000000 (0)
00:00:08.993   Last    <integer> = 0x0000000000000000 (0)
00:00:08.993 
00:00:08.993 [/Devices/i82078/0/LUN#0/] (level 4)
00:00:08.993   Driver <string>  = "Block" (cch=6)
00:00:08.993 
00:00:08.993 [/Devices/i82078/0/LUN#0/Config/] (level 5)
00:00:08.993   Type      <string>  = "Floppy 1.44" (cch=12)
00:00:08.993   Mountable <integer> = 0x0000000000000001 (1)
00:00:08.993 
00:00:08.993 [/Devices/i8254/] (level 2)
00:00:08.993 
00:00:08.993 [/Devices/i8254/0/] (level 3)
00:00:08.993 
00:00:08.993 [/Devices/i8254/0/Config/] (level 4)
00:00:08.993 
00:00:08.993 [/Devices/i8259/] (level 2)
00:00:08.993 
00:00:08.993 [/Devices/i8259/0/] (level 3)
00:00:08.993   Trusted <integer> = 0x0000000000000001 (1)
00:00:08.993 
00:00:08.993 [/Devices/i8259/0/Config/] (level 4)
00:00:08.993 
00:00:08.993 [/Devices/apic/] (level 2)
00:00:08.993 
00:00:08.993 [/Devices/apic/0/] (level 3)
00:00:08.993   Trusted <integer> = 0x0000000000000001 (1)
00:00:08.993 
00:00:08.993 [/Devices/apic/0/Config/] (level 4)
00:00:08.993   IOAPIC <integer> = 0x0000000000000001 (1)
00:00:08.993 
00:00:08.993 [/Devices/ioapic/] (level 2)
00:00:08.993 
00:00:08.993 [/Devices/ioapic/0/] (level 3)
00:00:08.993   Trusted <integer> = 0x0000000000000001 (1)
00:00:08.993 
00:00:08.993 [/Devices/ioapic/0/Config/] (level 4)
00:00:08.993 
00:00:08.993 [/Devices/mc146818/] (level 2)
00:00:08.993 
00:00:08.993 [/Devices/mc146818/0/] (level 3)
00:00:08.993 
00:00:08.993 [/Devices/mc146818/0/Config/] (level 4)
00:00:08.993 
00:00:08.993 [/Devices/vga/] (level 2)
00:00:08.993 
00:00:08.993 [/Devices/vga/0/] (level 3)
00:00:08.993   Trusted       <integer> = 0x0000000000000001 (1)
00:00:08.993   PCIDeviceNo   <integer> = 0x0000000000000002 (2)
00:00:08.993   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:08.993 
00:00:08.993 [/Devices/vga/0/Config/] (level 4)
00:00:08.993   VRamSize         <integer> = 0x0000000006500000 (105906176)
00:00:08.993   CustomVideoModes <integer> = 0x0000000000000000 (0)
00:00:08.993   HeightReduction  <integer> = 0x0000000000000000 (0)
00:00:08.993 
00:00:08.993 [/Devices/vga/0/LUN#0/] (level 4)
00:00:08.993   Driver <string>  = "MainDisplay" (cch=12)
00:00:08.993 
00:00:08.993 [/Devices/vga/0/LUN#0/Config/] (level 5)
00:00:08.993   Object <integer> = 0x000000000833cf08 (137613064)
00:00:08.993 
00:00:08.993 [/Devices/piix3ide/] (level 2)
00:00:08.993 
00:00:08.993 [/Devices/piix3ide/0/] (level 3)
00:00:08.993   Trusted       <integer> = 0x0000000000000001 (1)
00:00:08.993   PCIDeviceNo   <integer> = 0x0000000000000001 (1)
00:00:08.993   PCIFunctionNo <integer> = 0x0000000000000001 (1)
00:00:08.993 
00:00:08.993 [/Devices/piix3ide/0/Config/] (level 4)
00:00:08.993 
00:00:08.993 [/Devices/piix3ide/0/LUN#999/] (level 4)
00:00:08.993   Driver <string>  = "MainStatus" (cch=11)
00:00:08.993 
00:00:08.993 [/Devices/piix3ide/0/LUN#999/Config/] (level 5)
00:00:08.993   papLeds <integer> = 0x00000000083371a4 (137589156)
00:00:08.993   First   <integer> = 0x0000000000000000 (0)
00:00:08.993   Last    <integer> = 0x0000000000000003 (3)
00:00:08.993 
00:00:08.993 [/Devices/piix3ide/0/LUN#0/] (level 4)
00:00:08.993   Driver <string>  = "Block" (cch=6)
00:00:08.993 
00:00:08.993 [/Devices/piix3ide/0/LUN#0/Config/] (level 5)
00:00:08.993   Type      <string>  = "HardDisk" (cch=9)
00:00:08.993   Mountable <integer> = 0x0000000000000000 (0)
00:00:08.993 
00:00:08.993 [/Devices/piix3ide/0/LUN#0/AttachedDriver/] (level 5)
00:00:08.993   Driver <string>  = "VBoxHDD" (cch=8)
00:00:08.993 
00:00:08.993 [/Devices/piix3ide/0/LUN#0/AttachedDriver/Config/] (level 6)
00:00:08.994   Path <string>  = "/home/harlund/.VirtualBox/VDI/WinXP2.vdi" (cch=41)
00:00:08.994 
00:00:08.994 [/Devices/piix3ide/0/LUN#2/] (level 4)
00:00:08.994   Driver <string>  = "HostDVD" (cch=8)
00:00:08.994 
00:00:08.994 [/Devices/piix3ide/0/LUN#2/Config/] (level 5)
00:00:08.994   Path        <string>  = "/dev/hda" (cch=9)
00:00:08.994   Passthrough <integer> = 0x0000000000000000 (0)
00:00:08.994 
00:00:08.994 [/Devices/pcnet/] (level 2)
00:00:08.994 
00:00:08.994 [/Devices/pcnet/0/] (level 3)
00:00:08.994   Trusted       <integer> = 0x0000000000000001 (1)
00:00:08.994   PCIDeviceNo   <integer> = 0x0000000000000003 (3)
00:00:08.994   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:08.994 
00:00:08.994 [/Devices/pcnet/0/Config/] (level 4)
00:00:08.994   Am79C973       <integer> = 0x0000000000000001 (1)
00:00:08.994   MAC            <bytes>   = "08 00 27 8c 90 15" (cb=6)
00:00:08.994   CableConnected <integer> = 0x0000000000000001 (1)
00:00:08.994 
00:00:08.994 [/Devices/pcnet/0/LUN#999/] (level 4)
00:00:08.994   Driver <string>  = "MainStatus" (cch=11)
00:00:08.994 
00:00:08.994 [/Devices/pcnet/0/LUN#999/Config/] (level 5)
00:00:08.994   papLeds <integer> = 0x00000000083371b4 (137589172)
00:00:08.994 
00:00:08.994 [/Devices/pcnet/0/LUN#0/] (level 4)
00:00:08.994   Driver <string>  = "HostInterface" (cch=14)
00:00:08.994 
00:00:08.994 [/Devices/pcnet/0/LUN#0/Config/] (level 5)
00:00:08.994   FileHandle <integer> = 0x0000000000000021 (33)
00:00:08.994 
00:00:08.994 [/Devices/serial/] (level 2)
00:00:08.994 
00:00:08.994 [/Devices/parallel/] (level 2)
00:00:08.994 
00:00:08.994 [/Devices/VMMDev/] (level 2)
00:00:08.994 
00:00:08.994 [/Devices/VMMDev/0/] (level 3)
00:00:08.994   Trusted       <integer> = 0x0000000000000001 (1)
00:00:08.994   PCIDeviceNo   <integer> = 0x0000000000000004 (4)
00:00:08.994   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:08.994 
00:00:08.994 [/Devices/VMMDev/0/Config/] (level 4)
00:00:08.994 
00:00:08.994 [/Devices/VMMDev/0/LUN#0/] (level 4)
00:00:08.994   Driver <string>  = "MainVMMDev" (cch=11)
00:00:08.994 
00:00:08.994 [/Devices/VMMDev/0/LUN#0/Config/] (level 5)
00:00:08.994   Object <integer> = 0x0000000008330f68 (137564008)
00:00:08.994 
00:00:08.994 [/Devices/VMMDev/0/LUN#999/] (level 4)
00:00:08.994   Driver <string>  = "MainStatus" (cch=11)
00:00:08.994 
00:00:08.994 [/Devices/VMMDev/0/LUN#999/Config/] (level 5)
00:00:08.994   papLeds <integer> = 0x00000000083371d4 (137589204)
00:00:08.994   First   <integer> = 0x0000000000000000 (0)
00:00:08.994   Last    <integer> = 0x0000000000000000 (0)
00:00:08.994 
00:00:08.994 [/Devices/AudioSniffer/] (level 2)
00:00:08.994 
00:00:08.994 [/Devices/AudioSniffer/0/] (level 3)
00:00:08.994 
00:00:08.994 [/Devices/AudioSniffer/0/Config/] (level 4)
00:00:09.007 
00:00:09.007 [/Devices/AudioSniffer/0/LUN#0/] (level 4)
00:00:09.007   Driver <string>  = "MainAudioSniffer" (cch=17)
00:00:09.007 
00:00:09.007 [/Devices/AudioSniffer/0/LUN#0/Config/] (level 5)
00:00:09.007   Object <integer> = 0x00000000083373c8 (137589704)
00:00:09.007 
00:00:09.007 [/Devices/ichac97/] (level 2)
00:00:09.007 
00:00:09.007 [/Devices/ichac97/0/] (level 3)
00:00:09.007   Trusted       <integer> = 0x0000000000000001 (1)
00:00:09.007   PCIDeviceNo   <integer> = 0x0000000000000005 (5)
00:00:09.007   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:09.007 
00:00:09.007 [/Devices/ichac97/0/Config/] (level 4)
00:00:09.007 
00:00:09.007 [/Devices/ichac97/0/LUN#0/] (level 4)
00:00:09.007   Driver <string>  = "AUDIO" (cch=6)
00:00:09.007 
00:00:09.007 [/Devices/ichac97/0/LUN#0/Config/] (level 5)
00:00:09.007   AudioDriver <string>  = "alsa" (cch=5)
00:00:09.007 
00:00:09.007 [/TM/] (level 1)
00:00:09.007   UTCOffset <integer> = 0x0000000000000000 (0)
00:00:09.007 
00:00:09.007 ********************* End of CFGM dump **********************
00:00:09.008 Logical host processors: 2, processor active mask: 00000003
00:00:09.008 ************************* CPUID dump ************************
00:00:09.008          RAW Standard CPUIDs
00:00:09.008      Function  eax      ebx      ecx      edx
00:00:09.008 Gst: 00000000  00000001 68747541 444d4163 69746e65
00:00:09.008 Hst:           00000001 68747541 444d4163 69746e65
00:00:09.008 Gst: 00000001  00020f32 00000800 00000000 0788a1bf
00:00:09.008 Hst:           00020f32 00020800 00000001 178bfbff
00:00:09.008 Gst: 00000002  00000000 00000000 00000000 00000000*
00:00:09.008 Hst:           00000000 00000000 00000000 00000000
00:00:09.008 Gst: 00000003  00000000 00000000 00000000 00000000*
00:00:09.008 Hst:           00000000 00000000 00000000 00000000
00:00:09.009 Gst: 00000004  00000000 00000000 00000000 00000000*
00:00:09.009 Hst:           00000000 00000000 00000000 00000000
00:00:09.009 Gst: 00000005  80000004 68747541 444d4163 69746e65*
00:00:09.009 Hst:           00000000 00000000 00000000 00000000
00:00:09.009 Name:                            AuthenticAMD
00:00:09.009 Supports:                        0-1
00:00:09.009 Family:                          15  	Extended: 0 	Effectiv: 15
00:00:09.009 Model:                           3  	Extended: 2 	Effectiv: 3
00:00:09.009 Stepping:                        2
00:00:09.009 APIC ID:                         0x00
00:00:09.009 Logical CPUs:                    0
00:00:09.009 CLFLUSH Size:                    8
00:00:09.009 Brand ID:                        0x00
00:00:09.009 Mnemonic - Description                 = guest (host)
00:00:09.009 FPU - x87 FPU on Chip                  = 1 (1)
00:00:09.009 VME - Virtual 8086 Mode Enhancements   = 1 (1)
00:00:09.009 DE - Debugging extensions              = 1 (1)
00:00:09.009 PSE - Page Size Extension              = 1 (1)
00:00:09.009 TSC - Time Stamp Counter               = 1 (1)
00:00:09.009 MSR - Model Specific Registers         = 1 (1)
00:00:09.009 PAE - Physical Address Extension       = 0 (1)
00:00:09.009 MCE - Machine Check Exception          = 1 (1)
00:00:09.009 CX8 - CMPXCHG8B instruction            = 1 (1)
00:00:09.009 APIC - APIC On-Chip                    = 0 (1)
00:00:09.009 Reserved                               = 0 (0)
00:00:09.009 SEP - SYSENTER and SYSEXIT             = 0 (1)
00:00:09.009 MTRR - Memory Type Range Registers     = 0 (1)
00:00:09.009 PGE - PTE Global Bit                   = 1 (1)
00:00:09.009 MCA - Machine Check Architecture       = 0 (1)
00:00:09.009 CMOV - Conditional Move Instructions   = 1 (1)
00:00:09.009 PAT - Page Attribute Table             = 0 (1)
00:00:09.009 PSE-36 - 36-bit Page Size Extention    = 0 (1)
00:00:09.009 PSN - Processor Serial Number          = 0 (0)
00:00:09.009 CLFSH - CLFLUSH Instruction.           = 1 (1)
00:00:09.009 Reserved                               = 0 (0)
00:00:09.009 DS - Debug Store                       = 0 (0)
00:00:09.009 ACPI - Thermal Mon. & Soft. Clock Ctrl.= 0 (0)
00:00:09.009 MMX - Intel MMX Technology             = 1 (1)
00:00:09.009 FXSR - FXSAVE and FXRSTOR Instructions = 1 (1)
00:00:09.009 SSE - SSE Support                      = 1 (1)
00:00:09.009 SSE2 - SSE2 Support                    = 1 (1)
00:00:09.009 SS - Self Snoop                        = 0 (0)
00:00:09.009 HTT - Hyper-Threading Technolog        = 0 (1)
00:00:09.009 TM - Thermal Monitor                   = 0 (0)
00:00:09.009 30 - Reserved                          = 0 (0)
00:00:09.009 PBE - Pending Break Enable             = 0 (0)
00:00:09.009 Supports SSE3 or not                   = 0 (1)
00:00:09.009 Reserved                               = 0 (0)
00:00:09.009 Supports MONITOR/MWAIT                 = 0 (0)
00:00:09.009 CPL-DS - CPL Qualified Debug Store     = 0 (0)
00:00:09.009 VMX - Virtual Machine Technology       = 0 (0)
00:00:09.009 Reserved                               = 0 (0)
00:00:09.009 Enhanced SpeedStep Technology          = 0 (0)
00:00:09.009 Terminal Monitor 2                     = 0 (0)
00:00:09.009 Supports Supplemental SSE3 or not      = 0 (0)
00:00:09.009 L1 Context ID                          = 0 (0)
00:00:09.009 Reserved                               = 0x0 (0x0)
00:00:09.009 CMPXCHG16B                             = 0 (0)
00:00:09.009 xTPR Update Control                    = 0 (0)
00:00:09.009 Reserved                               = 0x0 (0x0)
00:00:09.009 
00:00:09.009          RAW Extended CPUIDs
00:00:09.009      Function  eax      ebx      ecx      edx
00:00:09.009 Gst: 80000000  80000004 68747541 444d4163 69746e65
00:00:09.009 Hst:           80000018 68747541 444d4163 69746e65
00:00:09.009 Gst: 80000001  00020f32 00000b05 00000000 c381a13f
00:00:09.009 Hst:           00020f32 00000b05 00000003 e3d3fbff
00:00:09.009 Gst: 80000002  6c617544 726f4320 4d412065 704f2044
00:00:09.009 Hst:           6c617544 726f4320 4d412065 704f2044
00:00:09.009 Gst: 80000003  6f726574 6d74286e 72502029 7365636f
00:00:09.009 Hst:           6f726574 6d74286e 72502029 7365636f
00:00:09.009 Gst: 80000004  20726f73 00303731 00000000 00000000
00:00:09.009 Hst:           20726f73 00303731 00000000 00000000
00:00:09.009 Gst: 80000005  00000000 00000000 00000000 00000000*
00:00:09.009 Hst:           ff08ff08 ff20ff20 40020140 40020140
00:00:09.009 Gst: 80000006  00000000 00000000 00000000 00000000*
00:00:09.009 Hst:           00000000 42004200 04008140 00000000
00:00:09.009 Gst: 80000007  00000000 00000000 00000000 00000000*
00:00:09.009 Hst:           00000000 00000000 00000000 0000000f
00:00:09.009 Gst: 80000008  00000000 00000000 00000000 00000000*
00:00:09.009 Hst:           00003028 00000000 00000001 00000000
00:00:09.009 Gst: 80000009  00000000 00000000 00000000 00000000*
00:00:09.009 Hst:           00000000 00000000 00000000 00000000
00:00:09.009 Gst: 8000000a  00000000 00000000 00000000 00000000*
00:00:09.009 Hst:           00000000 00000000 00000000 00000000
00:00:09.009 Ext Name:                        AuthenticAMD
00:00:09.009 Ext Supports:                    0x80000000-0x80000004
00:00:09.009 Family:                          15  	Extended: 0 	Effectiv: 15
00:00:09.009 Model:                           3  	Extended: 2 	Effectiv: 3
00:00:09.009 Stepping:                        2
00:00:09.009 Brand ID:                        0xb05
00:00:09.009 Mnemonic - Description                 = guest (host)
00:00:09.009 FPU - x87 FPU on Chip                  = 1 (1)
00:00:09.009 VME - Virtual 8086 Mode Enhancements   = 1 (1)
00:00:09.009 DE - Debugging extensions              = 1 (1)
00:00:09.009 PSE - Page Size Extension              = 1 (1)
00:00:09.009 TSC - Time Stamp Counter               = 1 (1)
00:00:09.009 MSR - K86 Model Specific Registers     = 1 (1)
00:00:09.009 PAE - Physical Address Extension       = 0 (1)
00:00:09.009 MCE - Machine Check Exception          = 0 (1)
00:00:09.009 CX8 - CMPXCHG8B instruction            = 1 (1)
00:00:09.009 APIC - APIC On-Chip                    = 0 (1)
00:00:09.009 10 - Reserved                          = 0 (0)
00:00:09.009 SEP - SYSCALL and SYSRET               = 0 (1)
00:00:09.009 MTRR - Memory Type Range Registers     = 0 (1)
00:00:09.009 PGE - PTE Global Bit                   = 1 (1)
00:00:09.009 MCA - Machine Check Architecture       = 0 (1)
00:00:09.009 CMOV - Conditional Move Instructions   = 1 (1)
00:00:09.009 PAT - Page Attribute Table             = 1 (1)
00:00:09.009 PSE-36 - 36-bit Page Size Extention    = 0 (1)
00:00:09.009 18 - Reserved                          = 0 (0)
00:00:09.009 19 - Reserved                          = 0 (0)
00:00:09.009 NX - No-Execute Page Protection        = 0 (1)
00:00:09.009 DS - Debug Store                       = 0 (0)
00:00:09.009 AXMMX - AMD Extensions to MMX Instr.   = 0 (1)
00:00:09.009 MMX - Intel MMX Technology             = 1 (1)
00:00:09.009 FXSR - FXSAVE and FXRSTOR Instructions = 1 (1)
00:00:09.009 25 - AMD fast FXSAVE and FXRSTOR Instr.= 1 (1)
00:00:09.009 26 - Reserved                          = 0 (0)
00:00:09.009 27 - Reserved                          = 0 (0)
00:00:09.009 28 - Reserved                          = 0 (0)
00:00:09.009 29 - AMD Long Mode                     = 0 (1)
00:00:09.009 30 - AMD Extensions to 3DNow           = 1 (1)
00:00:09.009 31 - AMD 3DNow                         = 1 (1)
00:00:09.009 LahfSahf - LAHF/SAHF in 64-bit mode    = 0 (1)
00:00:09.009 CmpLegacy - Core MP legacy mode (depr) = 0 (1)
00:00:09.009 SVM - AMD VM Extensions                = 0 (0)
00:00:09.009 APIC registers starting at 0x400       = 0 (0)
00:00:09.009 AltMovCR8 - LOCK MOV CR0 means MOV CR8 = 0 (0)
00:00:09.009 Advanced bit manipulation              = 0 (0)
00:00:09.009 SSE4A instruction support              = 0 (0)
00:00:09.009 Misaligned SSE mode                    = 0 (0)
00:00:09.009 PREFETCH and PREFETCHW instruction     = 0 (0)
00:00:09.009 OS visible workaround                  = 0 (0)
00:00:09.009 11:10 - Reserved                       = 0x0 (0x0)
00:00:09.009 SKINIT, STGI, and DEV support          = 0 (0)
00:00:09.009 Watchdog timer support.                = 0 (0)
00:00:09.009 31:14 - Reserved                       = 0x0 (0x0)
00:00:09.009 Full Name:                       Dual Core AMD Opteron(tm) Processor 170
00:00:09.009 
00:00:09.009 ******************** End of CPUID dump **********************
00:00:09.057 TM: cTSCTicksPerSecond=0xa0fb8b46 (2700839750) fTSCVirtualized=true  fTSCUseRealTSC=false fMaybeUseOffsettedHostTSC=false
00:00:09.057 CoreCode: R3=b3358000 R0=f8f82000 GC=a02f9000 Phys=000000000a75c000 cb=0x2000
00:00:09.084 VMMR0.r0 module loaded. VMMR0Entry located at f8f852f0.
00:00:09.125 Activating Local APIC
00:00:09.125 PIT: mode=3 count=0x10000 (65536) - 18.20 Hz (ch=0)
00:00:09.132 Shared Folders service loaded.
00:00:09.248 PIIX3 ATA: LUN#0: disk, CHS=20805/16/63, total number of sectors 20971520
00:00:09.248 PIIX3 ATA: LUN#1: no unit
00:00:09.254 PIIX3 ATA: LUN#2: CD/DVD, total number of sectors 0, passthrough disabled
00:00:09.254 PIIX3 ATA: LUN#3: no unit
00:00:09.254 PIIX3 ATA: Ctl#0: finished processing RESET
00:00:09.354 PIIX3 ATA: Ctl#1: finished processing RESET
00:00:09.454 Audio: Trying driver 'alsa'.
00:00:09.454 Audio: set_record_source ars=0 als=0 (not implemented)
00:00:09.461 ALSA: ADC frequency 44100Hz, period size 940, buffer size 3763
00:00:09.463 ALSA: DAC frequency 44100Hz, period size 940, buffer size 3763
00:00:09.490 Changing the VM state from 'CREATING' to 'CREATED'.
00:00:09.490 Changing the VM state from 'CREATED' to 'RUNNING'.
00:00:09.498 Guest Log: BIOS: VirtualBox 1.5.2
00:00:09.498 PIT: mode=2 count=0x10000 (65536) - 18.20 Hz (ch=0)
00:00:09.510 PIT: mode=2 count=0x48d3 (18643) - 64.00 Hz (ch=0)
00:00:09.517 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=ac556000 w=640 h=480 bpp=8 cbLine=0x280
00:00:11.591 PIT: mode=2 count=0x10000 (65536) - 18.20 Hz (ch=0)
00:00:11.592 PIIX3 ATA: Ctl#0: RESET, DevSel=0 AIOIf=0 CmdIf0=0x00 (-1 usec ago) CmdIf1=0x00 (-1 usec ago)
00:00:11.592 PIIX3 ATA: Ctl#0: finished processing RESET
00:00:11.592 Guest Log: BIOS: ata0-0: PCHS=16383/16/63 translation=lba LCHS=1024/255/63
00:00:11.593 PIIX3 ATA: Ctl#1: RESET, DevSel=0 AIOIf=0 CmdIf0=0x00 (-1 usec ago) CmdIf1=0x00 (-1 usec ago)
00:00:11.593 PIIX3 ATA: Ctl#1: finished processing RESET
00:00:11.594 Guest Log: BIOS: Boot from Floppy 0 failed
00:00:11.594 Guest Log: BIOS: CDROM boot failure code : 0003
00:00:11.594 Guest Log: BIOS: Boot from CD-ROM failed
00:00:11.594 Guest Log: BIOS: Booting from Hard Disk...
00:00:11.595 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=00000000 w=720 h=400 bpp=0 cbLine=0x0
00:00:11.842 Guest Log: BIOS: int13_harddisk: function 15, unmapped device for ELDL=81
00:00:14.067 PIT: mode=2 count=0x2ead (11949) - 99.85 Hz (ch=0)
00:00:14.201 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=ac556000 w=640 h=480 bpp=0 cbLine=0x140
00:00:15.572 PIIX3 ATA: LUN#0: IDLE IMMEDIATE, CmdIf=0xef (-1 usec ago)
00:00:15.572 PIIX3 ATA: LUN#0: aborting current command
00:00:21.522 Audio: set_record_source ars=0 als=0 (not implemented)
00:00:21.523 Audio: set_record_source ars=0 als=0 (not implemented)
00:00:21.538 Guest adapter information contains unsupported type 5. The block has been skipped.
00:00:21.544 PCNet#0: Init: ss32=1 GCRDRA=0x028e1420[64] GCTDRA=0x028e1020[64]
00:00:21.549 Guest Additions information report: additionsVersion = 0x00010004  osType = 0x00033000
00:00:21.566 Guest reported fixed hypervisor window at 0xf6c00000 (size = 0x800000, rc = VINF_SUCCESS)
00:00:25.362 PATM: Disable block at 828e5314 - write 828e5408-828e540c
00:00:25.656 PCNet#0: Init: ss32=1 GCRDRA=0x028e1420[64] GCTDRA=0x028e1020[64]
00:00:34.091 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=ac556000 w=1152 h=864 bpp=32 cbLine=0x1200
00:00:34.091 VBVA: Enabled.
00:00:34.421 Guest requests mouse pointer integration
00:00:35.547 PATM: Stop monitoring IDT handler pages at 82a47dd4 - invalid write 82a475a4-82a475a8 (this is not a fatal error)
00:00:36.856 PCNet#0: Init: ss32=1 GCRDRA=0x028e1420[64] GCTDRA=0x028e1020[64]
00:00:43.008 PCNet#0: Init: ss32=1 GCRDRA=0x028e1420[64] GCTDRA=0x028e1020[64]
00:00:53.364 PATM: Disable block at 829a0a74 - write 829a0b68-829a0b6c
00:01:07.001 Audio: set_record_source ars=0 als=0 (not implemented)
00:01:07.014 Audio: set_record_source ars=0 als=0 (not implemented)
00:01:23.167 Guest Additions capability report: (0x1) VMMDEV_GUEST_SUPPORTS_SEAMLESS: yes VMMDEV_GUEST_SUPPORTS_GUEST_HOST_WINDOW_MAPPING: no
00:01:23.458 PCNet#0: Init: ss32=1 GCRDRA=0x028e1420[64] GCTDRA=0x028e1020[64]
00:01:24.119 PATM: Stop monitoring IDT handler pages at 82b94dd4 - invalid write 82b94888-82b9488c (this is not a fatal error)
00:02:03.452 PATM: Stop monitoring IDT handler pages at 806f2d50 - invalid write 806f3ac8-806f3acc (this is not a fatal error)
00:02:03.461 PATM: Disable block at 806f304d - invalid write 806f3ac8-806f3acc 
00:02:59.915 PIT: mode=2 count=0x4ad (1197) - 996.81 Hz (ch=0)
00:03:00.463 PIT: mode=2 count=0x2ead (11949) - 99.85 Hz (ch=0)
00:03:00.553 PIT: mode=2 count=0x4ad (1197) - 996.81 Hz (ch=0)
00:03:09.698 PIT: mode=2 count=0x2ead (11949) - 99.85 Hz (ch=0)
00:03:13.034 PIT: mode=2 count=0x4ad (1197) - 996.81 Hz (ch=0)
00:03:13.044 PIT: mode=2 count=0x2ead (11949) - 99.85 Hz (ch=0)
00:03:13.114 PIT: mode=2 count=0x4ad (1197) - 996.81 Hz (ch=0)
00:03:16.819 PIT: mode=2 count=0x2ead (11949) - 99.85 Hz (ch=0)
00:03:17.689 PIT: mode=2 count=0x4ad (1197) - 996.81 Hz (ch=0)
00:03:17.697 PIT: mode=2 count=0x2ead (11949) - 99.85 Hz (ch=0)
00:03:18.929 PIT: mode=2 count=0x4ad (1197) - 996.81 Hz (ch=0)
00:03:23.137 PIT: mode=2 count=0x2ead (11949) - 99.85 Hz (ch=0)
00:03:23.806 PIT: mode=2 count=0x4ad (1197) - 996.81 Hz (ch=0)
00:03:23.815 PIT: mode=2 count=0x2ead (11949) - 99.85 Hz (ch=0)
00:03:23.825 PIT: mode=2 count=0x4ad (1197) - 996.81 Hz (ch=0)
00:03:28.052 PIT: mode=2 count=0x2ead (11949) - 99.85 Hz (ch=0)
00:03:29.771 PIT: mode=2 count=0x4ad (1197) - 996.81 Hz (ch=0)
00:03:29.779 PIT: mode=2 count=0x2ead (11949) - 99.85 Hz (ch=0)
00:03:29.789 PIT: mode=2 count=0x4ad (1197) - 996.81 Hz (ch=0)
00:13:48.802 PATM: Stop monitoring IDT handler pages at 828e78ec - invalid write 828e7450-828e7454 (this is not a fatal error)
00:22:31.926 PATM: Stop monitoring IDT handler pages at 828e9044 - invalid write 828e9e50-828e9e54 (this is not a fatal error)
00:25:43.618 PIT: mode=2 count=0x2ead (11949) - 99.85 Hz (ch=0)
00:29:12.722 PCNet#0: Init: ss32=1 GCRDRA=0x028e1420[64] GCTDRA=0x028e1020[64]
00:29:16.903 PIIX3 ATA: LUN#0: IDLE IMMEDIATE, CmdIf=0xe7 (-1 usec ago)
00:29:16.903 PIIX3 ATA: LUN#0: aborting current command
00:29:18.446 Guest requests the VM to be turned off
00:29:18.453 ****************** Guest state at power off ******************
00:29:18.456 Guest CPUM state: se
00:29:18.485 eax=0282f100 ebx=828e53b0 ecx=0282f100 edx=0000c040 esi=8282f100 edi=80560168
00:29:18.485 eip=f81d2a05 esp=f832dc94 ebp=f832dc9c iopl=0      rf nv up ei pl zr na po nc
00:29:18.485 cs={0008 base=00000000 limit=ffffffff flags=0000c09a} dr0=00000000 dr1=00000000
00:29:18.485 ds={0023 base=00000000 limit=ffffffff flags=0000c0f3} dr2=00000000 dr3=00000000
00:29:18.510 es={0023 base=00000000 limit=ffffffff flags=0000c0f3} dr4=00000000 dr5=00000000
00:29:18.510 fs={0030 base=ffdff000 limit=00001fff flags=0000c093} dr6=ffff0ff0 dr7=00000400
00:29:18.510 gs={0000 base=00000000 limit=0000ffff flags=00000000} cr0=e001003b cr2=8003f03f
00:29:18.510 ss={0010 base=00000000 limit=ffffffff flags=0000c093} cr3=00039000 cr4=00000699
00:29:18.510 gdtr=8003f000:03ff  idtr=8003f400:07ff  eflags=00010206
00:29:18.510 ldtr={0000 base=00000000 limit=00000000 flags=00000080}
00:29:18.510 tr  ={0028 base=80042000 limit=000020ab flags=00000089}
00:29:18.510 SysEnter={cs=0000 eip=00000000 esp=00000000}
00:29:18.510 FPU:
00:29:18.510 FCW=027f FSW=0000 FTW=00
00:29:18.510 res1=00 FOP=0000 FPUIP=00000000 CS=0000 Rsvrd1=0000
00:29:18.510 FPUDP=0000 DS=0000 Rsvrd2=0000 MXCSR=00001f80 MXCSR_MASK=0000ffff
00:29:18.510 ***
00:29:18.510 Guest paging mode:  32-bit, changed 1954 times, A20 enabled
00:29:18.534 Shadow paging mode: 32-bit
00:29:18.534 Host paging mode:   32-bit+G
00:29:18.534 ***
00:29:18.534 Active Timers (pVM=b418a000)
00:29:18.534 pTimerR3 offNext  offPrev  offSched Clock Time               Expire             State                     Description
00:29:18.534 b3747f30 000353b0 00000000 00000000 Real  000000017182651810 000000017182651741 ACTIVE                    VGA Refresh Timer
00:29:18.534 b377d2e0 00000000 fffcac50 00000000 Real  000000017182651810 000000017182651745 ACTIVE                    EMT Yielder
00:29:18.534 b377b560 00000000 00000000 00000000 Virt  000001749043806062 000001748964530922 ACTIVE                    Audio timer
00:29:18.550 b3746b80 00000320 00000000 00000000 VrSy  000001748955444508 000001748955444508 ACTIVE                    i8254 Programmable Interval Timer
00:29:18.550 b3746ea0 00035d80 fffffce0 00000000 VrSy  000001748955444508 000001748990000000 ACTIVE                    MC146818 RTC/CMOS - Second
00:29:18.550 b377cc20 00000000 fffca280 00000000 VrSy  000001748955444508 000002399728063202 ACTIVE                    ACPI Timer
00:29:18.550 ***
00:29:18.556 Shadow GDT (GCAddr=f6efc000):
00:29:18.556 0008 - 0000ffff 00cfbb00 - base=00000000 limit=ffffffff dpl=1 CodeER Accessed Present Page 32-bit 
00:29:18.556 0010 - 0000ffff 00cfb300 - base=00000000 limit=ffffffff dpl=1 DataRW Accessed Present Page 32-bit 
00:29:18.556 0018 - 0000ffff 00cffb00 - base=00000000 limit=ffffffff dpl=3 CodeER Accessed Present Page 32-bit 
00:29:18.556 0020 - 0000ffff 00cff300 - base=00000000 limit=ffffffff dpl=3 DataRW Accessed Present Page 32-bit 
00:29:18.556 0030 - f0000001 ffc0b3df - base=ffdff000 limit=00001fff dpl=1 DataRW Accessed Present Page 32-bit 
00:29:18.557 0038 - 00000fff 0040f300 - base=00000000 limit=00000fff dpl=3 DataRW Accessed Present 32-bit 
00:29:18.557 0040 - 0400ffff 0000f300 - base=00000400 limit=0000ffff dpl=3 DataRW Accessed Present 16-bit 
00:29:18.557 0060 - 2f30ffff 0000b302 - base=00022f30 limit=0000ffff dpl=1 DataRW Accessed Present 16-bit 
00:29:18.557 0068 - 80003fff 0000b30b - base=000b8000 limit=00003fff dpl=1 DataRW Accessed Present 16-bit 
00:29:18.557 0070 - 700003ff ff00b3ff - base=ffff7000 limit=000003ff dpl=1 DataRW Accessed Present 16-bit 
00:29:18.557 0078 - 0000ffff 8000bb40 - base=80400000 limit=0000ffff dpl=1 CodeER Accessed Present 16-bit 
00:29:18.568 0080 - 0000ffff 8000b340 - base=80400000 limit=0000ffff dpl=1 DataRW Accessed Present 16-bit 
00:29:18.568 0088 - 00000000 0000b300 - base=00000000 limit=00000000 dpl=1 DataRW Accessed Present 16-bit 
00:29:18.568 00e8 - 0000ffff 0000b300 - base=00000000 limit=0000ffff dpl=1 DataRW Accessed Present 16-bit 
00:29:18.568 00f0 - 8b28b2f7 8003b94d - base=804d8b28 limit=0003b2f7 dpl=1 CodeEO Accessed Present 16-bit 
00:29:18.568 00f8 - 0000ffff 0000b300 - base=00000000 limit=0000ffff dpl=1 DataRW Accessed Present 16-bit 
00:29:18.568 ffd8 - 06080087 f60089c1 - base=f6c10608 limit=00000087 dpl=0 TSS32Avail Present 16-bit  HyperTSSTrap08
00:29:18.568 ffe0 - 05800087 f6008bc1 - base=f6c10580 limit=00000087 dpl=0 TSS32Busy Present 16-bit  HyperTSS
00:29:18.568 ffe8 - 0000ffff 00af9b00 - base=00000000 limit=ffffffff dpl=0 CodeER Accessed Present Page 16-bit  HyperCS64
00:29:18.568 fff0 - 0000ffff 00cf9300 - base=00000000 limit=ffffffff dpl=0 DataRW Accessed Present Page 32-bit  HyperDS
00:29:18.568 fff8 - 0000ffff 00cf9b00 - base=00000000 limit=ffffffff dpl=0 CodeER Accessed Present Page 32-bit  HyperCS
00:29:18.568 ***
00:29:18.568 ************** End of Guest state at power off ***************
00:29:18.568 Changing the VM state from 'RUNNING' to 'OFF'.
00:29:20.119 Console::powerDown(): a request to power off the VM has been issued (mMachineState=8, InUninit=0)
00:29:20.131 Changing the VM state from 'OFF' to 'DESTROYING'.
00:29:20.247 ************************* Statistics *************************
00:29:20.247 /Devices/ATA0/Unit0/AtapiDMA            0 times
00:29:20.328 /Devices/ATA0/Unit0/AtapiPIO            0 times
00:29:20.328 /Devices/ATA0/Unit0/DMA             21562 times
00:29:20.328 /Devices/ATA0/Unit0/PIO              3282 times
00:29:20.328 /Devices/ATA0/Unit1/AtapiDMA            0 times
00:29:20.328 /Devices/ATA0/Unit1/AtapiPIO            0 times
00:29:20.328 /Devices/ATA0/Unit1/DMA                 0 times
00:29:20.328 /Devices/ATA0/Unit1/PIO                 0 times
00:29:20.328 /Devices/ATA1/Unit0/AtapiDMA            0 times
00:29:20.328 /Devices/ATA1/Unit0/AtapiPIO         1783 times
00:29:20.328 /Devices/ATA1/Unit0/DMA                 0 times
00:29:20.328 /Devices/ATA1/Unit0/PIO                 0 times
00:29:20.328 /Devices/ATA1/Unit1/AtapiDMA            0 times
00:29:20.328 /Devices/ATA1/Unit1/AtapiPIO            0 times
00:29:20.328 /Devices/ATA1/Unit1/DMA                 0 times
00:29:20.328 /Devices/ATA1/Unit1/PIO                 0 times
00:29:20.328 /MM/HyperHeap/cbFree               718928 bytes
00:29:20.328 /MM/HyperHeap/cbHeap              1310656 bytes
00:29:20.328 /PGM/cGuestModeChanges               1954 times
00:29:20.328 /PROF/EM/Halted                   2902521 ticks/call (3465401131304 ticks, 1193928 times, max 18446744073708618918, min      50)
00:29:20.328 /PROF/EM/Total                   4727823737248 ticks/call (4727823737248 ticks,       1 times, max 4727823737248, min 4727823737248)
00:29:20.328 /PROF/VM/Halt/Block               2401090 ticks/call (2961345955119 ticks, 1233334 times, max 18446744073709135630, min    4276)
00:29:20.328 /PROF/VM/Halt/Poll                     17 ticks/call (  3126600066 ticks, 180499696 times, max   2715507, min      14)
00:29:20.328 /PROF/VM/Halt/Timers                 1938 ticks/call (349903992200 ticks, 180499696 times, max 18446744073701543834, min    1571)
00:29:20.328 /PROF/VM/Halt/Yield                     0 ticks/call (           0 ticks,       0 times, max         0, min      -1)
00:29:20.328 /TM/1nsSteps                      1589241 times
00:29:20.328 /TM/BadPrevTime                         1 times
00:29:20.328 /TM/VirtualSync/CurrentOffset           0 ns
00:29:20.328 ********************* End of statistics **********************
00:29:25.584 Changing the VM state from 'DESTROYING' to 'TERMINATED'.
00:29:43.480 vboxClipboardDestroy: shutting down host clipboard
00:29:43.533 vboxClipboardThread: clipboard thread terminated successfully with return code VINF_SUCCESS

---

### Post by painterh on 2007-12-10
Update:  After leaving it alone for a couple of days, I started my WinXP virtual machine and no problems.  I dont know what the problem was, but it seems to be alright now.  I wish I could post info about something I did to fix it, but it seems to have sorted itself out.  For now anyway.

---

