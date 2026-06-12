---
title: "Need help installing windows under virtual box lucid lynx 11.04"
date: 2011-08-11
forum: Virtualisation
---

### Post by LifeOfRyan on 2011-08-11
I would like to install preferably windows 7 from an .iso image(have tried an xp disc aswell) under virtualbox but unfortunately i keep coming to the same problem so i guess this eliminates a problem with my installation sources. Have never done this before so more than likely missing something or other. I have an Acer Aspire 7530G laptop running lucid lynx 10.04. After adding the user for virtual box in users and groups i started the machine and tried to run the install but i cannot even reach the setup screen as the computer freezes after the first initial ' Windows Is Loading  Files' this also happens with xp after loading files just before booting into the actual windows setup.

I also tried adding a SATA controller, as i recall, I think i had to install a sata controller previously when installing xp in the standard manner but this didnt fix the problem and neither did switching the hard drive into IDE mode from the bios settings.

Log from Virtual Box:
p, li { white-space: pre-wrap; }>  p, li { white-space: pre-wrap; } VirtualBox 4.1.0 r73009 linux.x86 (Jul 19 2011 11:30:11) release log
 00:00:02.521 Log opened 2011-08-11T16:06:17.267137000Z
 00:00:02.521 OS Product: Linux
 00:00:02.521 OS Release: 2.6.32-33-generic
 00:00:02.521 OS Version: #70-Ubuntu SMP Thu Jul 7 21:09:46 UTC 2011
 00:00:02.521 DMI Product Name: Aspire 7530G    
 00:00:02.521 DMI Product Version: Not Applicable
 00:00:02.524 Host RAM: 2517MB RAM, available: 2091MB
 00:00:02.524 Executable: /usr/lib/virtualbox/VirtualBox
 00:00:02.524 Process ID: 2955
 00:00:02.524 Package type: LINUX_32BITS_UBUNTU_10_04
 00:00:02.590 Installed Extension Packs:
 00:00:02.590   None installed!
 00:00:02.617 Using XKB for keycode to scan code conversion
 00:00:02.626 SUP: Loaded VMMR0.r0 (/usr/lib/virtualbox/VMMR0.r0) at 0xfdc02020 - ModuleInit at 00000000fdc18e30 and ModuleTerm at 00000000fdc18e00
 00:00:02.626 SUP: VMMR0EntryEx located at 00000000fdc18ce0, VMMR0EntryFast at 00000000fdc17bc0 and VMMR0EntryInt at 00000000fdc179b0
 00:00:02.684 File system of '/home/ryan/VirtualBox VMs/xp/Snapshots' (snapshots) is unknown
 00:00:02.684 File system of '/home/ryan/VirtualBox VMs/xp/NewHardDisk1.vdi' is ext4
 00:00:02.719 VBoxSharedClipboard mode: Bidirectional
 00:00:02.729 ************************* CFGM dump *************************
 00:00:02.730 [/] (level 0)
 00:00:02.730   CSAMEnabled     <integer> = 0x0000000000000001 (1)
 00:00:02.730   CpuExecutionCap <integer> = 0x0000000000000064 (100)
 00:00:02.730   EnablePAE       <integer> = 0x0000000000000000 (0)
 00:00:02.730   HwVirtExtForced <integer> = 0x0000000000000000 (0)
 00:00:02.730   MemBalloonSize  <integer> = 0x0000000000000000 (0)
 00:00:02.730   Name            <string>  = "xp" (cb=3)
 00:00:02.730   NumCPUs         <integer> = 0x0000000000000001 (1)
 00:00:02.730   PATMEnabled     <integer> = 0x0000000000000001 (1)
 00:00:02.730   PageFusion      <integer> = 0x0000000000000000 (0)
 00:00:02.730   RamHoleSize     <integer> = 0x0000000020000000 (536870912)
 00:00:02.730   RamSize         <integer> = 0x0000000040000000 (1073741824)
 00:00:02.730   RawR0Enabled    <integer> = 0x0000000000000001 (1)
 00:00:02.730   RawR3Enabled    <integer> = 0x0000000000000001 (1)
 00:00:02.730   TimerMillies    <integer> = 0x000000000000000a (10)
 00:00:02.730   UUID            <bytes>   = "f0 c7 df ab 44 e5 2c 47 86 19 eb 0f 3a fb 7b 46" (cb=16)
 00:00:02.730 
 00:00:02.730 [/CPUM/] (level 1)
 00:00:02.730   SyntheticCpu <integer> = 0x0000000000000000 (0)
 00:00:02.730 
 00:00:02.730 [/Devices/] (level 1)
 00:00:02.730 
 00:00:02.730 [/Devices/8237A/] (level 2)
 00:00:02.730 
 00:00:02.730 [/Devices/8237A/0/] (level 3)
 00:00:02.730   Trusted <integer> = 0x0000000000000001 (1)
 00:00:02.730 
 00:00:02.730 [/Devices/AudioSniffer/] (level 2)
 00:00:02.730 
 00:00:02.730 [/Devices/AudioSniffer/0/] (level 3)
 00:00:02.730 
 00:00:02.730 [/Devices/AudioSniffer/0/Config/] (level 4)
 00:00:02.730 
 00:00:02.730 [/Devices/AudioSniffer/0/LUN#0/] (level 4)
 00:00:02.730   Driver <string>  = "MainAudioSniffer" (cb=17)
 00:00:02.730 
 00:00:02.730 [/Devices/AudioSniffer/0/LUN#0/Config/] (level 5)
 00:00:02.730   Object <integer> = 0x00000000b5900f80 (3046117248)
 00:00:02.730 
 00:00:02.730 [/Devices/VMMDev/] (level 2)
 00:00:02.730 
 00:00:02.730 [/Devices/VMMDev/0/] (level 3)
 00:00:02.730   PCIBusNo      <integer> = 0x0000000000000000 (0)
 00:00:02.730   PCIDeviceNo   <integer> = 0x0000000000000004 (4)
 00:00:02.730   PCIFunctionNo <integer> = 0x0000000000000000 (0)
 00:00:02.730   Trusted       <integer> = 0x0000000000000001 (1)
 00:00:02.730 
 00:00:02.730 [/Devices/VMMDev/0/Config/] (level 4)
 00:00:02.730   GuestCoreDumpDir <string>  = "/home/ryan/VirtualBox VMs/xp/Snapshots" (cb=39)
 00:00:02.730   RamSize          <integer> = 0x0000000040000000 (1073741824)
 00:00:02.730 
 00:00:02.730 [/Devices/VMMDev/0/LUN#0/] (level 4)
 00:00:02.730   Driver <string>  = "HGCM" (cb=5)
 00:00:02.730 
 00:00:02.730 [/Devices/VMMDev/0/LUN#0/Config/] (level 5)
 00:00:02.730   Object <integer> = 0x000000000988c340 (159957824)
 00:00:02.730 
 00:00:02.730 [/Devices/VMMDev/0/LUN#999/] (level 4)
 00:00:02.730   Driver <string>  = "MainStatus" (cb=11)
 00:00:02.730 
 00:00:02.730 [/Devices/VMMDev/0/LUN#999/Config/] (level 5)
 00:00:02.730   First   <integer> = 0x0000000000000000 (0)
 00:00:02.730   Last    <integer> = 0x0000000000000000 (0)
 00:00:02.730   papLeds <integer> = 0x000000000973f430 (158594096)
 00:00:02.730 
 00:00:02.730 [/Devices/acpi/] (level 2)
 00:00:02.730 
 00:00:02.730 [/Devices/acpi/0/] (level 3)
 00:00:02.730   PCIBusNo      <integer> = 0x0000000000000000 (0)
 00:00:02.730   PCIDeviceNo   <integer> = 0x0000000000000007 (7)
 00:00:02.730   PCIFunctionNo <integer> = 0x0000000000000000 (0)
 00:00:02.730   Trusted       <integer> = 0x0000000000000001 (1)
 00:00:02.730 
 00:00:02.730 [/Devices/acpi/0/Config/] (level 4)
 00:00:02.730   CpuHotPlug        <integer> = 0x0000000000000000 (0)
 00:00:02.730   FdcEnabled        <integer> = 0x0000000000000000 (0)
 00:00:02.730   HostBusPciAddress <integer> = 0x0000000000000000 (0)
 00:00:02.730   HpetEnabled       <integer> = 0x0000000000000000 (0)
 00:00:02.730   IOAPIC            <integer> = 0x0000000000000000 (0)
 00:00:02.730   IocPciAddress     <integer> = 0x0000000000010000 (65536)
 00:00:02.730   NumCPUs           <integer> = 0x0000000000000001 (1)
 00:00:02.730   RamHoleSize       <integer> = 0x0000000020000000 (536870912)
 00:00:02.730   RamSize           <integer> = 0x0000000040000000 (1073741824)
 00:00:02.730   Serial0IoPortBase <integer> = 0x0000000000000000 (0)
 00:00:02.730   Serial0Irq        <integer> = 0x0000000000000000 (0)
 00:00:02.730   Serial1IoPortBase <integer> = 0x0000000000000000 (0)
 00:00:02.730   Serial1Irq        <integer> = 0x0000000000000000 (0)
 00:00:02.730   ShowCpu           <integer> = 0x0000000000000000 (0)
 00:00:02.730   ShowRtc           <integer> = 0x0000000000000000 (0)
 00:00:02.730   SmcEnabled        <integer> = 0x0000000000000000 (0)
 00:00:02.730 
 00:00:02.730 [/Devices/acpi/0/LUN#0/] (level 4)
 00:00:02.730   Driver <string>  = "ACPIHost" (cb=9)
 00:00:02.730 
 00:00:02.730 [/Devices/acpi/0/LUN#0/Config/] (level 5)
 00:00:02.730 
 00:00:02.730 [/Devices/ahci/] (level 2)
 00:00:02.730 
 00:00:02.730 [/Devices/ahci/0/] (level 3)
 00:00:02.730   PCIBusNo      <integer> = 0x0000000000000000 (0)
 00:00:02.730   PCIDeviceNo   <integer> = 0x000000000000000d (13)
 00:00:02.730   PCIFunctionNo <integer> = 0x0000000000000000 (0)
 00:00:02.730   Trusted       <integer> = 0x0000000000000001 (1)
 00:00:02.730 
 00:00:02.730 [/Devices/ahci/0/Config/] (level 4)
 00:00:02.730   Bootable        <integer> = 0x0000000000000001 (1)
 00:00:02.730   PortCount       <integer> = 0x0000000000000001 (1)
 00:00:02.730   PrimaryMaster   <integer> = 0x0000000000000000 (0)
 00:00:02.730   PrimarySlave    <integer> = 0x0000000000000001 (1)
 00:00:02.730   SecondaryMaster <integer> = 0x0000000000000002 (2)
 00:00:02.730   SecondarySlave  <integer> = 0x0000000000000003 (3)
 00:00:02.730 
 00:00:02.730 [/Devices/ahci/0/Config/Port0/] (level 5)
 00:00:02.730   NonRotationalMedium <integer> = 0x0000000000000000 (0)
 00:00:02.730 
 00:00:02.730 [/Devices/ahci/0/LUN#0/] (level 4)
 00:00:02.730   Driver <string>  = "Block" (cb=6)
 00:00:02.730 
 00:00:02.730 [/Devices/ahci/0/LUN#0/AttachedDriver/] (level 5)
 00:00:02.730   Driver <string>  = "VD" (cb=3)
 00:00:02.730 
 00:00:02.730 [/Devices/ahci/0/LUN#0/AttachedDriver/Config/] (level 6)
 00:00:02.730   Format <string>  = "VDI" (cb=4)
 00:00:02.730   Path   <string>  = "/home/ryan/VirtualBox VMs/xp/NewHardDisk1.vdi" (cb=46)
 00:00:02.730   Type   <string>  = "HardDisk" (cb=9)
 00:00:02.730 
 00:00:02.730 [/Devices/ahci/0/LUN#0/Config/] (level 5)
 00:00:02.730   Mountable <integer> = 0x0000000000000000 (0)
 00:00:02.730   Type      <string>  = "HardDisk" (cb=9)
 00:00:02.730 
 00:00:02.730 [/Devices/ahci/0/LUN#999/] (level 4)
 00:00:02.730   Driver <string>  = "MainStatus" (cb=11)
 00:00:02.730 
 00:00:02.730 [/Devices/ahci/0/LUN#999/Config/] (level 5)
 00:00:02.730   DeviceInstance        <string>  = "ahci/0" (cb=7)
 00:00:02.730   First                 <integer> = 0x0000000000000000 (0)
 00:00:02.730   Last                  <integer> = 0x0000000000000000 (0)
 00:00:02.730   pConsole              <integer> = 0x000000000973f128 (158593320)
 00:00:02.730   papLeds               <integer> = 0x000000000973f338 (158593848)
 00:00:02.730   pmapMediumAttachments <integer> = 0x000000000973f43c (158594108)
 00:00:02.730 
 00:00:02.730 [/Devices/apic/] (level 2)
 00:00:02.730 
 00:00:02.730 [/Devices/apic/0/] (level 3)
 00:00:02.730   Trusted <integer> = 0x0000000000000001 (1)
 00:00:02.730 
 00:00:02.730 [/Devices/apic/0/Config/] (level 4)
 00:00:02.730   IOAPIC  <integer> = 0x0000000000000000 (0)
 00:00:02.730   NumCPUs <integer> = 0x0000000000000001 (1)
 00:00:02.730 
 00:00:02.730 [/Devices/e1000/] (level 2)
 00:00:02.730 
 00:00:02.730 [/Devices/i8254/] (level 2)
 00:00:02.730 
 00:00:02.730 [/Devices/i8254/0/] (level 3)
 00:00:02.730 
 00:00:02.730 [/Devices/i8254/0/Config/] (level 4)
 00:00:02.730 
 00:00:02.730 [/Devices/i8259/] (level 2)
 00:00:02.730 
 00:00:02.730 [/Devices/i8259/0/] (level 3)
 00:00:02.730   Trusted <integer> = 0x0000000000000001 (1)
 00:00:02.730 
 00:00:02.730 [/Devices/i8259/0/Config/] (level 4)
 00:00:02.730 
 00:00:02.730 [/Devices/ichac97/] (level 2)
 00:00:02.730 
 00:00:02.730 [/Devices/ichac97/0/] (level 3)
 00:00:02.730   PCIBusNo      <integer> = 0x0000000000000000 (0)
 00:00:02.730   PCIDeviceNo   <integer> = 0x0000000000000005 (5)
 00:00:02.730   PCIFunctionNo <integer> = 0x0000000000000000 (0)
 00:00:02.730   Trusted       <integer> = 0x0000000000000001 (1)
 00:00:02.730 
 00:00:02.730 [/Devices/ichac97/0/Config/] (level 4)
 00:00:02.730 
 00:00:02.730 [/Devices/ichac97/0/LUN#0/] (level 4)
 00:00:02.730   Driver <string>  = "AUDIO" (cb=6)
 00:00:02.730 
 00:00:02.730 [/Devices/ichac97/0/LUN#0/Config/] (level 5)
 00:00:02.730   AudioDriver <string>  = "pulse" (cb=6)
 00:00:02.730   StreamName  <string>  = "xp" (cb=3)
 00:00:02.730 
 00:00:02.730 [/Devices/mc146818/] (level 2)
 00:00:02.730 
 00:00:02.730 [/Devices/mc146818/0/] (level 3)
 00:00:02.730 
 00:00:02.730 [/Devices/mc146818/0/Config/] (level 4)
 00:00:02.730   UseUTC <integer> = 0x0000000000000000 (0)
 00:00:02.730 
 00:00:02.730 [/Devices/parallel/] (level 2)
 00:00:02.730 
 00:00:02.730 [/Devices/pcarch/] (level 2)
 00:00:02.730 
 00:00:02.730 [/Devices/pcarch/0/] (level 3)
 00:00:02.730   Trusted <integer> = 0x0000000000000001 (1)
 00:00:02.730 
 00:00:02.730 [/Devices/pcarch/0/Config/] (level 4)
 00:00:02.730 
 00:00:02.730 [/Devices/pcbios/] (level 2)
 00:00:02.730 
 00:00:02.730 [/Devices/pcbios/0/] (level 3)
 00:00:02.730   Trusted <integer> = 0x0000000000000001 (1)
 00:00:02.730 
 00:00:02.730 [/Devices/pcbios/0/Config/] (level 4)
 00:00:02.730   BootDevice0            <string>  = "FLOPPY" (cb=7)
 00:00:02.731   BootDevice1            <string>  = "DVD" (cb=4)
 00:00:02.731   BootDevice2            <string>  = "IDE" (cb=4)
 00:00:02.731   BootDevice3            <string>  = "NONE" (cb=5)
 00:00:02.731   FloppyDevice           <string>  = "i82078" (cb=7)
 00:00:02.731   HardDiskDevice         <string>  = "piix3ide" (cb=9)
 00:00:02.731   IOAPIC                 <integer> = 0x0000000000000000 (0)
 00:00:02.731   McfgBase               <integer> = 0x0000000000000000 (0)
 00:00:02.731   McfgLength             <integer> = 0x0000000000000000 (0)
 00:00:02.731   NumCPUs                <integer> = 0x0000000000000001 (1)
 00:00:02.731   PXEDebug               <integer> = 0x0000000000000000 (0)
 00:00:02.731   RamHoleSize            <integer> = 0x0000000020000000 (536870912)
 00:00:02.731   RamSize                <integer> = 0x0000000040000000 (1073741824)
 00:00:02.731   SataHardDiskDevice     <string>  = "ahci" (cb=5)
 00:00:02.731   SataPrimaryMasterLUN   <integer> = 0x0000000000000000 (0)
 00:00:02.731   SataPrimarySlaveLUN    <integer> = 0x0000000000000001 (1)
 00:00:02.731   SataSecondaryMasterLUN <integer> = 0x0000000000000002 (2)
 00:00:02.731   SataSecondarySlaveLUN  <integer> = 0x0000000000000003 (3)
 00:00:02.731   UUID                   <bytes>   = "f0 c7 df ab 44 e5 2c 47 86 19 eb 0f 3a fb 7b 46" (cb=16)
 00:00:02.731 
 00:00:02.731 [/Devices/pcbios/0/Config/NetBoot/] (level 5)
 00:00:02.731 
 00:00:02.731 [/Devices/pcbios/0/Config/NetBoot/0/] (level 6)
 00:00:02.731   NIC           <integer> = 0x0000000000000000 (0)
 00:00:02.731   PCIBusNo      <integer> = 0x0000000000000000 (0)
 00:00:02.731   PCIDeviceNo   <integer> = 0x0000000000000003 (3)
 00:00:02.731   PCIFunctionNo <integer> = 0x0000000000000000 (0)
 00:00:02.731 
 00:00:02.731 [/Devices/pci/] (level 2)
 00:00:02.731 
 00:00:02.731 [/Devices/pci/0/] (level 3)
 00:00:02.731   Trusted <integer> = 0x0000000000000001 (1)
 00:00:02.731 
 00:00:02.731 [/Devices/pci/0/Config/] (level 4)
 00:00:02.731   IOAPIC <integer> = 0x0000000000000000 (0)
 00:00:02.731 
 00:00:02.731 [/Devices/pckbd/] (level 2)
 00:00:02.731 
 00:00:02.731 [/Devices/pckbd/0/] (level 3)
 00:00:02.731   Trusted <integer> = 0x0000000000000001 (1)
 00:00:02.731 
 00:00:02.731 [/Devices/pckbd/0/Config/] (level 4)
 00:00:02.731 
 00:00:02.731 [/Devices/pckbd/0/LUN#0/] (level 4)
 00:00:02.731   Driver <string>  = "KeyboardQueue" (cb=14)
 00:00:02.731 
 00:00:02.731 [/Devices/pckbd/0/LUN#0/AttachedDriver/] (level 5)
 00:00:02.731   Driver <string>  = "MainKeyboard" (cb=13)
 00:00:02.731 
 00:00:02.731 [/Devices/pckbd/0/LUN#0/AttachedDriver/Config/] (level 6)
 00:00:02.731   Object <integer> = 0x000000000973fad8 (158595800)
 00:00:02.731 
 00:00:02.731 [/Devices/pckbd/0/LUN#0/Config/] (level 5)
 00:00:02.731   QueueSize <integer> = 0x0000000000000040 (64)
 00:00:02.731 
 00:00:02.731 [/Devices/pckbd/0/LUN#1/] (level 4)
 00:00:02.731   Driver <string>  = "MouseQueue" (cb=11)
 00:00:02.731 
 00:00:02.731 [/Devices/pckbd/0/LUN#1/AttachedDriver/] (level 5)
 00:00:02.731   Driver <string>  = "MainMouse" (cb=10)
 00:00:02.731 
 00:00:02.731 [/Devices/pckbd/0/LUN#1/AttachedDriver/Config/] (level 6)
 00:00:02.731   Object <integer> = 0x000000000978eba8 (158919592)
 00:00:02.731 
 00:00:02.731 [/Devices/pckbd/0/LUN#1/Config/] (level 5)
 00:00:02.731   QueueSize <integer> = 0x0000000000000080 (128)
 00:00:02.731 
 00:00:02.731 [/Devices/pcnet/] (level 2)
 00:00:02.731 
 00:00:02.731 [/Devices/pcnet/0/] (level 3)
 00:00:02.731   PCIBusNo      <integer> = 0x0000000000000000 (0)
 00:00:02.731   PCIDeviceNo   <integer> = 0x0000000000000003 (3)
 00:00:02.731   PCIFunctionNo <integer> = 0x0000000000000000 (0)
 00:00:02.731   Trusted       <integer> = 0x0000000000000001 (1)
 00:00:02.731 
 00:00:02.731 [/Devices/pcnet/0/Config/] (level 4)
 00:00:02.731   Am79C973       <integer> = 0x0000000000000001 (1)
 00:00:02.731   CableConnected <integer> = 0x0000000000000001 (1)
 00:00:02.731   LineSpeed      <integer> = 0x0000000000000000 (0)
 00:00:02.731   MAC            <bytes>   = "08 00 27 3c 94 7b" (cb=6)
 00:00:02.731 
 00:00:02.731 [/Devices/pcnet/0/LUN#0/] (level 4)
 00:00:02.731   Driver <string>  = "NAT" (cb=4)
 00:00:02.731 
 00:00:02.731 [/Devices/pcnet/0/LUN#0/Config/] (level 5)
 00:00:02.731   AliasMode       <integer> = 0x0000000000000000 (0)
 00:00:02.731   BootFile        <string>  = "xp.pxe" (cb=7)
 00:00:02.731   DNSProxy        <integer> = 0x0000000000000000 (0)
 00:00:02.731   Network         <string>  = "10.0.2.0/24" (cb=12)
 00:00:02.731   PassDomain      <integer> = 0x0000000000000001 (1)
 00:00:02.731   TFTPPrefix      <string>  = "/home/ryan/.VirtualBox/TFTP" (cb=28)
 00:00:02.731   UseHostResolver <integer> = 0x0000000000000000 (0)
 00:00:02.731 
 00:00:02.731 [/Devices/pcnet/0/LUN#999/] (level 4)
 00:00:02.731   Driver <string>  = "MainStatus" (cb=11)
 00:00:02.731 
 00:00:02.731 [/Devices/pcnet/0/LUN#999/Config/] (level 5)
 00:00:02.731   First   <integer> = 0x0000000000000000 (0)
 00:00:02.731   Last    <integer> = 0x0000000000000000 (0)
 00:00:02.731   papLeds <integer> = 0x000000000973f410 (158594064)
 00:00:02.731 
 00:00:02.731 [/Devices/piix3ide/] (level 2)
 00:00:02.731 
 00:00:02.731 [/Devices/piix3ide/0/] (level 3)
 00:00:02.731   PCIBusNo      <integer> = 0x0000000000000000 (0)
 00:00:02.731   PCIDeviceNo   <integer> = 0x0000000000000001 (1)
 00:00:02.731   PCIFunctionNo <integer> = 0x0000000000000001 (1)
 00:00:02.731   Trusted       <integer> = 0x0000000000000001 (1)
 00:00:02.731 
 00:00:02.731 [/Devices/piix3ide/0/Config/] (level 4)
 00:00:02.731   Type <string>  = "PIIX4" (cb=6)
 00:00:02.731 
 00:00:02.731 [/Devices/piix3ide/0/Config/PrimaryMaster/] (level 5)
 00:00:02.731   NonRotationalMedium <integer> = 0x0000000000000000 (0)
 00:00:02.731 
 00:00:02.731 [/Devices/piix3ide/0/LUN#0/] (level 4)
 00:00:02.731   Driver <string>  = "HostDVD" (cb=8)
 00:00:02.731 
 00:00:02.731 [/Devices/piix3ide/0/LUN#0/Config/] (level 5)
 00:00:02.731   Passthrough <integer> = 0x0000000000000000 (0)
 00:00:02.731   Path        <string>  = "/dev/sr0" (cb=9)
 00:00:02.731 
 00:00:02.731 [/Devices/piix3ide/0/LUN#999/] (level 4)
 00:00:02.731   Driver <string>  = "MainStatus" (cb=11)
 00:00:02.731 
 00:00:02.731 [/Devices/piix3ide/0/LUN#999/Config/] (level 5)
 00:00:02.731   DeviceInstance        <string>  = "piix3ide/0" (cb=11)
 00:00:02.731   First                 <integer> = 0x0000000000000000 (0)
 00:00:02.731   Last                  <integer> = 0x0000000000000003 (3)
 00:00:02.731   pConsole              <integer> = 0x000000000973f128 (158593320)
 00:00:02.731   papLeds               <integer> = 0x000000000973f328 (158593832)
 00:00:02.731   pmapMediumAttachments <integer> = 0x000000000973f43c (158594108)
 00:00:02.731 
 00:00:02.731 [/Devices/serial/] (level 2)
 00:00:02.731 
 00:00:02.731 [/Devices/usb-ohci/] (level 2)
 00:00:02.731 
 00:00:02.731 [/Devices/usb-ohci/0/] (level 3)
 00:00:02.731   PCIBusNo      <integer> = 0x0000000000000000 (0)
 00:00:02.731   PCIDeviceNo   <integer> = 0x0000000000000006 (6)
 00:00:02.731   PCIFunctionNo <integer> = 0x0000000000000000 (0)
 00:00:02.731   Trusted       <integer> = 0x0000000000000001 (1)
 00:00:02.731 
 00:00:02.731 [/Devices/usb-ohci/0/Config/] (level 4)
 00:00:02.731 
 00:00:02.731 [/Devices/usb-ohci/0/LUN#0/] (level 4)
 00:00:02.731   Driver <string>  = "VUSBRootHub" (cb=12)
 00:00:02.731 
 00:00:02.731 [/Devices/usb-ohci/0/LUN#0/Config/] (level 5)
 00:00:02.731 
 00:00:02.731 [/Devices/usb-ohci/0/LUN#999/] (level 4)
 00:00:02.731   Driver <string>  = "MainStatus" (cb=11)
 00:00:02.731 
 00:00:02.731 [/Devices/usb-ohci/0/LUN#999/Config/] (level 5)
 00:00:02.731   First   <integer> = 0x0000000000000000 (0)
 00:00:02.731   Last    <integer> = 0x0000000000000000 (0)
 00:00:02.731   papLeds <integer> = 0x000000000973f434 (158594100)
 00:00:02.731 
 00:00:02.731 [/Devices/vga/] (level 2)
 00:00:02.731 
 00:00:02.731 [/Devices/vga/0/] (level 3)
 00:00:02.731   PCIBusNo      <integer> = 0x0000000000000000 (0)
 00:00:02.731   PCIDeviceNo   <integer> = 0x0000000000000002 (2)
 00:00:02.731   PCIFunctionNo <integer> = 0x0000000000000000 (0)
 00:00:02.731   Trusted       <integer> = 0x0000000000000001 (1)
 00:00:02.731 
 00:00:02.731 [/Devices/vga/0/Config/] (level 4)
 00:00:02.731   CustomVideoModes <integer> = 0x0000000000000000 (0)
 00:00:02.731   FadeIn           <integer> = 0x0000000000000001 (1)
 00:00:02.731   FadeOut          <integer> = 0x0000000000000001 (1)
 00:00:02.731   HeightReduction  <integer> = 0x0000000000000000 (0)
 00:00:02.731   LogoFile         <string>  = "" (cb=1)
 00:00:02.731   LogoTime         <integer> = 0x0000000000000000 (0)
 00:00:02.731   MonitorCount     <integer> = 0x0000000000000001 (1)
 00:00:02.731   ShowBootMenu     <integer> = 0x0000000000000002 (2)
 00:00:02.731   VRamSize         <integer> = 0x0000000001000000 (16777216)
 00:00:02.731 
 00:00:02.731 [/Devices/vga/0/LUN#0/] (level 4)
 00:00:02.731   Driver <string>  = "MainDisplay" (cb=12)
 00:00:02.731 
 00:00:02.731 [/Devices/vga/0/LUN#0/Config/] (level 5)
 00:00:02.731   Object <integer> = 0x000000000978f020 (158920736)
 00:00:02.731 
 00:00:02.731 [/Devices/virtio-net/] (level 2)
 00:00:02.731 
 00:00:02.731 [/HWVirtExt/] (level 1)
 00:00:02.731   64bitEnabled       <integer> = 0x0000000000000000 (0)
 00:00:02.731   EnableLargePages   <integer> = 0x0000000000000000 (0)
 00:00:02.731   EnableNestedPaging <integer> = 0x0000000000000001 (1)
 00:00:02.731   EnableVPID         <integer> = 0x0000000000000001 (1)
 00:00:02.731   Enabled            <integer> = 0x0000000000000001 (1)
 00:00:02.731   Exclusive          <integer> = 0x0000000000000001 (1)
 00:00:02.731 
 00:00:02.731 [/MM/] (level 1)
 00:00:02.731   CanUseLargerHeap <integer> = 0x0000000000000000 (0)
 00:00:02.731 
 00:00:02.731 [/PDM/] (level 1)
 00:00:02.731 
 00:00:02.731 [/PDM/AsyncCompletion/] (level 2)
 00:00:02.731 
 00:00:02.731 [/PDM/AsyncCompletion/File/] (level 3)
 00:00:02.731 
 00:00:02.731 [/PDM/AsyncCompletion/File/BwGroups/] (level 4)
 00:00:02.731 
 00:00:02.731 [/PDM/BlkCache/] (level 2)
 00:00:02.731   CacheSize <integer> = 0x0000000000500000 (5242880)
 00:00:02.731 
 00:00:02.731 [/PDM/Devices/] (level 2)
 00:00:02.731 
 00:00:02.731 [/PDM/Drivers/] (level 2)
 00:00:02.731 
 00:00:02.731 [/PDM/Drivers/VBoxC/] (level 3)
 00:00:02.732   Path <string>  = "/usr/lib/virtualbox/components/VBoxC" (cb=37)
 00:00:02.732 
 00:00:02.732 [/TM/] (level 1)
 00:00:02.732   UTCOffset <integer> = 0x0000000000000000 (0)
 00:00:02.732 
 00:00:02.732 [/USB/] (level 1)
 00:00:02.732 
 00:00:02.732 [/USB/USBProxy/] (level 2)
 00:00:02.732 
 00:00:02.732 [/USB/USBProxy/GlobalConfig/] (level 3)
 00:00:02.732 
 00:00:02.732 ********************* End of CFGM dump **********************
 00:00:02.732 MM: cbHyperHeap=0x140000 (1310720)
 00:00:02.737 Logical host processors: 2 present, 2 max, 2 online, online mask: 0000000000000003
 00:00:02.737 ************************* CPUID dump ************************
 00:00:02.737          RAW Standard CPUIDs
 00:00:02.737      Function  eax      ebx      ecx      edx
 00:00:02.737 Gst: 00000000  00000001 68747541 444d4163 69746e65
 00:00:02.737 Hst:           00000001 68747541 444d4163 69746e65
 00:00:02.737 Gst: 00000001  00200f31 00000800 00000001 078bf1bf
 00:00:02.737 Hst:           00200f31 00020800 00002001 178bfbff
 00:00:02.737 Gst: 00000002  00000000 00000000 00000000 00000000*
 00:00:02.737 Hst:           00000000 00000000 00000000 00000000
 00:00:02.737 Gst: 00000003  00000000 00000000 00000000 00000000*
 00:00:02.737 Hst:           00000000 00000000 00000000 00000000
 00:00:02.737 Gst: 00000004  00000000 00000000 00000000 00000000*
 00:00:02.737 Hst:           00000000 00000000 00000000 00000000
 00:00:02.737 Gst: 00000005  00000000 00000000 00000000 00000000*
 00:00:02.737 Hst:           00000000 00000000 00000000 00000000
 00:00:02.737 Name:                            AuthenticAMD
 00:00:02.737 Supports:                        0-1
 00:00:02.737 Family:                          15  	Extended: 2 	Effective: 17
 00:00:02.737 Model:                           3  	Extended: 0 	Effective: 3
 00:00:02.737 Stepping:                        1
 00:00:02.737 Type:                            0 (primary)
 00:00:02.737 APIC ID:                         0x00
 00:00:02.737 Logical CPUs:                    0
 00:00:02.737 CLFLUSH Size:                    8
 00:00:02.737 Brand ID:                        0x00
 00:00:02.737 Mnemonic - Description                 = guest (host)
 00:00:02.737 FPU - x87 FPU on Chip                  = 1 (1)
 00:00:02.737 VME - Virtual 8086 Mode Enhancements   = 1 (1)
 00:00:02.737 DE - Debugging extensions              = 1 (1)
 00:00:02.737 PSE - Page Size Extension              = 1 (1)
 00:00:02.737 TSC - Time Stamp Counter               = 1 (1)
 00:00:02.737 MSR - Model Specific Registers         = 1 (1)
 00:00:02.737 PAE - Physical Address Extension       = 0 (1)
 00:00:02.737 MCE - Machine Check Exception          = 1 (1)
 00:00:02.737 CX8 - CMPXCHG8B instruction            = 1 (1)
 00:00:02.737 APIC - APIC On-Chip                    = 0 (1)
 00:00:02.737 10 - Reserved                          = 0 (0)
 00:00:02.737 SEP - SYSENTER and SYSEXIT             = 0 (1)
 00:00:02.737 MTRR - Memory Type Range Registers     = 1 (1)
 00:00:02.737 PGE - PTE Global Bit                   = 1 (1)
 00:00:02.737 MCA - Machine Check Architecture       = 1 (1)
 00:00:02.737 CMOV - Conditional Move Instructions   = 1 (1)
 00:00:02.737 PAT - Page Attribute Table             = 1 (1)
 00:00:02.737 PSE-36 - 36-bit Page Size Extention    = 1 (1)
 00:00:02.737 PSN - Processor Serial Number          = 0 (0)
 00:00:02.737 CLFSH - CLFLUSH Instruction.           = 1 (1)
 00:00:02.737 20 - Reserved                          = 0 (0)
 00:00:02.737 DS - Debug Store                       = 0 (0)
 00:00:02.737 ACPI - Thermal Mon. & Soft. Clock Ctrl.= 0 (0)
 00:00:02.737 MMX - Intel MMX Technology             = 1 (1)
 00:00:02.737 FXSR - FXSAVE and FXRSTOR Instructions = 1 (1)
 00:00:02.737 SSE - SSE Support                      = 1 (1)
 00:00:02.737 SSE2 - SSE2 Support                    = 1 (1)
 00:00:02.737 SS - Self Snoop                        = 0 (0)
 00:00:02.737 HTT - Hyper-Threading Technology       = 0 (1)
 00:00:02.737 TM - Thermal Monitor                   = 0 (0)
 00:00:02.737 30 - Reserved                          = 0 (0)
 00:00:02.737 PBE - Pending Break Enable             = 0 (0)
 00:00:02.737 Supports SSE3                          = 1 (1)
 00:00:02.737 PCLMULQDQ                              = 0 (0)
 00:00:02.737 DS Area 64-bit layout                  = 0 (0)
 00:00:02.737 Supports MONITOR/MWAIT                 = 0 (0)
 00:00:02.737 CPL-DS - CPL Qualified Debug Store     = 0 (0)
 00:00:02.737 VMX - Virtual Machine Technology       = 0 (0)
 00:00:02.737 SMX - Safer Mode Extensions            = 0 (0)
 00:00:02.737 Enhanced SpeedStep Technology          = 0 (0)
 00:00:02.737 Terminal Monitor 2                     = 0 (0)
 00:00:02.737 Supplemental SSE3 instructions         = 0 (0)
 00:00:02.737 L1 Context ID                          = 0 (0)
 00:00:02.737 11 - Reserved                          = 0 (0)
 00:00:02.737 FMA extensions using YMM state         = 0 (0)
 00:00:02.737 CMPXCHG16B instruction                 = 0 (1)
 00:00:02.737 xTPR Update Control                    = 0 (0)
 00:00:02.737 Perf/Debug Capability MSR              = 0 (0)
 00:00:02.737 16 - Reserved                          = 0 (0)
 00:00:02.737 PCID - Process-context identifiers     = 0 (0)
 00:00:02.737 DCA - Direct Cache Access              = 0 (0)
 00:00:02.737 SSE4.1 instruction extensions          = 0 (0)
 00:00:02.737 SSE4.2 instruction extensions          = 0 (0)
 00:00:02.737 Supports the x2APIC extensions         = 0 (0)
 00:00:02.737 MOVBE instruction                      = 0 (0)
 00:00:02.737 POPCNT instruction                     = 0 (0)
 00:00:02.737 TSC-Deadline LAPIC timer mode          = 0 (0)
 00:00:02.737 AESNI instruction extensions           = 0 (0)
 00:00:02.737 XSAVE/XRSTOR extended state feature    = 0 (0)
 00:00:02.737 Supports OSXSAVE                       = 0 (0)
 00:00:02.737 AVX instruction extensions             = 0 (0)
 00:00:02.737 29/30 - Reserved                       = 0x0 (0x0)
 00:00:02.737 Hypervisor Present (we're a guest)     = 0 (0)
 00:00:02.737 
 00:00:02.737          RAW Extended CPUIDs
 00:00:02.737      Function  eax      ebx      ecx      edx
 00:00:02.738 Gst: 80000000  80000008 68747541 444d4163 69746e65
 00:00:02.738 Hst:           8000001a 68747541 444d4163 69746e65
 00:00:02.738 Gst: 80000001  00200f31 20000cb0 00000010 c383f13f
 00:00:02.738 Hst:           00200f31 20000cb0 0000131f ebd3fbff
 00:00:02.738 Gst: 80000002  20444d41 69727554 74286e6f 5820296d
 00:00:02.738 Hst:           20444d41 69727554 74286e6f 5820296d
 00:00:02.738 Gst: 80000003  75442032 432d6c61 2065726f 69626f4d
 00:00:02.738 Hst:           75442032 432d6c61 2065726f 69626f4d
 00:00:02.738 Gst: 80000004  5220656c 35372d4d 00000000 00000000
 00:00:02.738 Hst:           5220656c 35372d4d 00000000 00000000
 00:00:02.738 Gst: 80000005  ff08ff08 ff20ff20 40020140 40020140
 00:00:02.738 Hst:           ff08ff08 ff20ff20 40020140 40020140
 00:00:02.738 Gst: 80000006  00000000 42004200 02008140 00000000
 00:00:02.738 Hst:           00000000 42004200 02008140 00000000
 00:00:02.738 Gst: 80000007  00000000 00000000 00000000 00000000
 00:00:02.738 Hst:           00000000 00000000 00000000 000001f9
 00:00:02.738 Gst: 80000008  00003028 00000000 00000000 00000000
 00:00:02.738 Hst:           00003028 00000000 00001001 00000000
 00:00:02.738 Gst: 80000009  00000000 00000000 00000000 00000000*
 00:00:02.738 Hst:           00000000 00000000 00000000 00000000
 00:00:02.738 Ext Name:                        AuthenticAMD
 00:00:02.738 Ext Supports:                    0x80000000-0x80000008
 00:00:02.738 Family:                          15  	Extended: 2 	Effective: 17
 00:00:02.738 Model:                           3  	Extended: 0 	Effective: 3
 00:00:02.738 Stepping:                        1
 00:00:02.738 Brand ID:                        0xcb0
 00:00:02.738 Mnemonic - Description                 = guest (host)
 00:00:02.738 FPU - x87 FPU on Chip                  = 1 (1)
 00:00:02.738 VME - Virtual 8086 Mode Enhancements   = 1 (1)
 00:00:02.738 DE - Debugging extensions              = 1 (1)
 00:00:02.738 PSE - Page Size Extension              = 1 (1)
 00:00:02.738 TSC - Time Stamp Counter               = 1 (1)
 00:00:02.738 MSR - K86 Model Specific Registers     = 1 (1)
 00:00:02.738 PAE - Physical Address Extension       = 0 (1)
 00:00:02.738 MCE - Machine Check Exception          = 0 (1)
 00:00:02.738 CX8 - CMPXCHG8B instruction            = 1 (1)
 00:00:02.738 APIC - APIC On-Chip                    = 0 (1)
 00:00:02.738 10 - Reserved                          = 0 (0)
 00:00:02.738 SEP - SYSCALL and SYSRET               = 0 (1)
 00:00:02.738 MTRR - Memory Type Range Registers     = 1 (1)
 00:00:02.738 PGE - PTE Global Bit                   = 1 (1)
 00:00:02.738 MCA - Machine Check Architecture       = 1 (1)
 00:00:02.738 CMOV - Conditional Move Instructions   = 1 (1)
 00:00:02.738 PAT - Page Attribute Table             = 1 (1)
 00:00:02.738 PSE-36 - 36-bit Page Size Extention    = 1 (1)
 00:00:02.738 18 - Reserved                          = 0 (0)
 00:00:02.738 19 - Reserved                          = 0 (0)
 00:00:02.738 NX - No-Execute Page Protection        = 0 (1)
 00:00:02.738 DS - Debug Store                       = 0 (0)
 00:00:02.738 AXMMX - AMD Extensions to MMX Instr.   = 0 (1)
 00:00:02.738 MMX - Intel MMX Technology             = 1 (1)
 00:00:02.738 FXSR - FXSAVE and FXRSTOR Instructions = 1 (1)
 00:00:02.738 25 - AMD fast FXSAVE and FXRSTOR Instr.= 1 (1)
 00:00:02.738 26 - 1 GB large page support           = 0 (0)
 00:00:02.738 27 - RDTSCP instruction                = 0 (1)
 00:00:02.738 28 - Reserved                          = 0 (0)
 00:00:02.738 29 - AMD Long Mode                     = 0 (1)
 00:00:02.738 30 - AMD Extensions to 3DNow           = 1 (1)
 00:00:02.738 31 - AMD 3DNow                         = 1 (1)
 00:00:02.738 LahfSahf - LAHF/SAHF in 64-bit mode    = 0 (1)
 00:00:02.738 CmpLegacy - Core MP legacy mode (depr) = 0 (1)
 00:00:02.738 SVM - AMD VM Extensions                = 0 (1)
 00:00:02.738 APIC registers starting at 0x400       = 0 (1)
 00:00:02.738 AltMovCR8 - LOCK MOV CR0 means MOV CR8 = 1 (1)
 00:00:02.738 Advanced bit manipulation              = 0 (0)
 00:00:02.738 SSE4A instruction support              = 0 (0)
 00:00:02.738 Misaligned SSE mode                    = 0 (0)
 00:00:02.738 PREFETCH and PREFETCHW instruction     = 0 (1)
 00:00:02.738 OS visible workaround                  = 0 (1)
 00:00:02.738 Instruction based sampling             = 0 (0)
 00:00:02.738 SSE5 support                           = 0 (0)
 00:00:02.738 SKINIT, STGI, and DEV support          = 0 (1)
 00:00:02.738 Watchdog timer support.                = 0 (0)
 00:00:02.738 31:14 - Reserved                       = 0x0 (0x0)
 00:00:02.738 Full Name:                       AMD Turion(tm) X2 Dual-Core Mobile RM-75
 00:00:02.738 TLB 2/4M Instr/Uni:              fully   8 entries
 00:00:02.738 TLB 2/4M Data:                   fully   8 entries
 00:00:02.738 TLB 4K Instr/Uni:                fully  32 entries
 00:00:02.738 TLB 4K Data:                     fully  32 entries
 00:00:02.738 L1 Instr Cache Line Size:        64 bytes
 00:00:02.738 L1 Instr Cache Lines Per Tag:    1
 00:00:02.738 L1 Instr Cache Associativity:    2 way
 00:00:02.738 L1 Instr Cache Size:             64 KB
 00:00:02.738 L1 Data Cache Line Size:         64 bytes
 00:00:02.738 L1 Data Cache Lines Per Tag:     1
 00:00:02.738 L1 Data Cache Associativity:     2 way
 00:00:02.738 L1 Data Cache Size:              64 KB
 00:00:02.738 L2 TLB 2/4M Instr/Uni:           off       0 entries
 00:00:02.738 L2 TLB 2/4M Data:                off       0 entries
 00:00:02.738 L2 TLB 4K Instr/Uni:             4 way   512 entries
 00:00:02.738 L2 TLB 4K Data:                  4 way   512 entries
 00:00:02.738 L2 Cache Line Size:              0 bytes
 00:00:02.738 L2 Cache Lines Per Tag:          0
 00:00:02.738 L2 Cache Associativity:          off   
 00:00:02.738 L2 Cache Size:                   0 KB
 00:00:02.738 APM Features:                   
 00:00:02.738 Physical Address Width:          40 bits
 00:00:02.738 Virtual Address Width:           48 bits
 00:00:02.738 Guest Physical Address Width:    0 bits
 00:00:02.738 Physical Core Count:             0
 00:00:02.738 
 00:00:02.738          RAW Centaur CPUIDs
 00:00:02.738      Function  eax      ebx      ecx      edx
 00:00:02.738 Gst: c0000000  00000000 00000000 00000000 00000000
 00:00:02.738 Hst:           00000000 00000000 00000000 00000000
 00:00:02.738 Gst: c0000001  00000000 00000000 00000000 00000000*
 00:00:02.738 Hst:           00000000 00000000 00000000 00000000
 00:00:02.738 Gst: c0000002  00000000 00000000 00000000 00000000*
 00:00:02.738 Hst:           00000000 00000000 00000000 00000000
 00:00:02.738 Gst: c0000003  00000000 00000000 00000000 00000000*
 00:00:02.738 Hst:           00000000 00000000 00000000 00000000
 00:00:02.738 Centaur Supports:                0xc0000000-0x00000000
 00:00:02.738 
 00:00:02.738 ******************** End of CPUID dump **********************
 00:00:02.738 PGMPool: cMaxPages=560 (u64MaxPages=545)
 00:00:02.738 pgmR3PoolInit: cMaxPages=0x230 cMaxUsers=0x460 cMaxPhysExts=0x460 fCacheEnable=true 
 00:00:02.738 REM: VBoxREM32
 00:00:02.758 TM: GIP - u32Mode=2 (AsyncTSC) u32UpdateHz=83
 00:00:02.798 TM: cTSCTicksPerSecond=0x829af510 (2 191 193 360) fTSCVirtualized=true  fTSCUseRealTSC=false
 00:00:02.798 TM: fMaybeUseOffsettedHostTSC=false TSCTiedToExecution=false TSCNotTiedToHalt=false
 00:00:02.798 CoreCode: R3=00ab2000 R0=fa3f9000 RC=a0594000 Phys=000000000394c000 cb=0x3000
 00:00:02.802 AIOMgr: Default manager type is "Async"
 00:00:02.802 AIOMgr: Default file backend is "NonBuffered"
 00:00:02.802 BlkCache: Cache successfully initialised. Cache size is 5242880 bytes
 00:00:02.802 BlkCache: Cache commit interval is 10000 ms
 00:00:02.802 BlkCache: Cache commit threshold is 2621440 bytes
 00:00:02.807 [SMP] BIOS with 1 CPUs
 00:00:02.818 SUP: Loaded VBoxDDR0.r0 (/usr/lib/virtualbox/VBoxDDR0.r0) at 0xfa507020 - ModuleInit at 0000000000000000 and ModuleTerm at 0000000000000000
 00:00:02.821 SUP: Loaded VBoxDD2R0.r0 (/usr/lib/virtualbox/VBoxDD2R0.r0) at 0xfa4d2020 - ModuleInit at 0000000000000000 and ModuleTerm at 0000000000000000
 00:00:02.821 Activating Local APIC
 00:00:02.821 CPUMSetGuestCpuIdFeature: Enabled APIC
 00:00:02.821 CPUMSetGuestCpuIdFeature: Disabled x2APIC
 00:00:02.821 PIT: mode=3 count=0x10000 (65536) - 18.20 Hz (ch=0)
 00:00:02.826 Shared Folders service loaded.
 00:00:02.839 Chipset cannot do MSI: VERR_NOT_IMPLEMENTED
 00:00:02.839 DrvBlock: Flushes will be ignored
 00:00:02.839 DrvBlock: Async flushes will be passed to the disk
 00:00:02.840 VDInit finished
 00:00:02.840 AHCI: LUN#0: disk, PCHS=16383/16/63, total number of sectors 20971520
 00:00:02.840 AHCI: LUN#0: using normal I/O
 00:00:02.840 AHCI ATA: LUN#0: disk, PCHS=16383/16/63, total number of sectors 20971520
 00:00:02.840 AHCI ATA: LUN#1: no unit
 00:00:02.840 AHCI ATA: Ctl: finished processing RESET
 00:00:02.840 AHCI ATA: LUN#2: no unit
 00:00:02.840 AHCI ATA: LUN#3: no unit
 00:00:02.840 AHCI ATA: Ctl: finished processing RESET
 00:00:02.840 AHCI ATA: Ctl: finished processing RESET
 00:00:02.841 AHCI ATA: Ctl: finished processing RESET
 00:00:02.849 PIIX3 ATA: LUN#0: CD/DVD, total number of sectors 296660, passthrough disabled
 00:00:02.849 PIIX3 ATA: LUN#1: no unit
 00:00:02.849 PIIX3 ATA: LUN#2: no unit
 00:00:02.849 PIIX3 ATA: LUN#3: no unit
 00:00:02.849 PIIX3 ATA: Ctl#0: finished processing RESET
 00:00:02.849 PIIX3 ATA: Ctl#1: finished processing RESET
 00:00:02.875 NAT: value of BindIP has been ignored
 00:00:02.876 Audio: Trying driver 'pulse'.
 00:00:02.883 Audio: set_record_source ars=0 als=0 (not implemented)
 00:00:02.883 Pulse: open PCM_IN rate=44100Hz channels=2 format=s16le
 00:00:02.883 Pulse: Requested record buffer attributes: maxlength=26460 fragsize=17640
 00:00:02.902 Pulse:  Obtained record buffer attributes: maxlength=26460 fragsize=8820
 00:00:02.903 Pulse: open PCM_OUT rate=44100Hz channels=2 format=s16le
 00:00:02.903 Pulse: Requested playback buffer attributes: maxlength=26460 tlength=17640 prebuf=-1 minreq=-1
 00:00:02.970 Pulse:  Obtained playback buffer attributes: maxlength=26460 tlength=12348 prebuf=8824 minreq=3528
 00:00:02.975 DevPcBios: SATA LUN#0 LCHS=1024/255/63
 00:00:02.978 PGM: The CPU physical address width is 40 bits
 00:00:02.978 PGMR3InitFinalize: 4 MB PSE mask 000000ffffffffff
 00:00:02.993 VMM: fUsePeriodicPreemptionTimers=true 
 00:00:02.993 HWACMM: cpuid 0x80000001.u32AMDFeatureECX = 131f
 00:00:02.993 HWACMM: cpuid 0x80000001.u32AMDFeatureEDX = ebd3fbff
 00:00:02.993 HWACCM: AMD HWCR MSR                      = 1000041
 00:00:02.993 HWACCM: AMD-V revision                    = 1
 00:00:02.993 HWACCM: AMD-V max ASID                    = 64
 00:00:02.993 HWACCM: AMD-V features                    = E
 00:00:02.993 HWACCM:    AMD_CPUID_SVM_FEATURE_EDX_LBR_VIRT
 00:00:02.993 HWACCM:    AMD_CPUID_SVM_FEATURE_EDX_SVM_LOCK
 00:00:02.993 HWACCM:    AMD_CPUID_SVM_FEATURE_EDX_NRIP_SAVE
 00:00:02.993 CPUMSetGuestCpuIdFeature: Enabled sysenter/exit
 00:00:02.993 CPUMSetGuestCpuIdFeature: Enabled syscall/ret
 00:00:02.993 CPUMSetGuestCpuIdFeature: Enabled RDTSCP.
 00:00:02.993 HWACCM:    32-bit guest supported.
 00:00:02.993 HWACCM:    TPR Patching disabled.
 00:00:02.993 HWACCM:    VT-x/AMD-V init method: GLOBAL
 00:00:03.005 VM: Halt method global1 (5)
 00:00:03.005 HaltedGlobal1 config: cNsSpinBlockThresholdCfg=2000
 00:00:03.005 Changing the VM state from 'CREATING' to 'CREATED'.
 00:00:03.006 Changing the VM state from 'CREATED' to 'POWERING_ON'.
 00:00:03.006 Changing the VM state from 'POWERING_ON' to 'RUNNING'.
 00:00:03.024 Guest Log: BIOS: VirtualBox 4.1.0
 00:00:03.024 PIT: mode=2 count=0x10000 (65536) - 18.20 Hz (ch=0)
 00:00:03.032 PIIX3 ATA: Ctl#0: RESET, DevSel=0 AIOIf=0 CmdIf0=0x00 (-1 usec ago) CmdIf1=0x00 (-1 usec ago)
 00:00:03.032 PIIX3 ATA: Ctl#0: finished processing RESET
 00:00:03.033 AHCI ATA: Ctl: RESET, DevSel=0 AIOIf=0 CmdIf0=0x00 (-1 usec ago) CmdIf1=0x00 (-1 usec ago)
 00:00:03.033 AHCI ATA: Ctl: finished processing RESET
 00:00:03.034 Guest Log: BIOS: ata2-0: PCHS=16383/16/63 LCHS=1024/255/63
 00:00:03.034 PIT: mode=2 count=0x48d3 (18643) - 64.00 Hz (ch=0)
 00:00:03.047 ERROR [COM]: aRC=VBOX_E_IPRT_ERROR (0x80bb0005) aIID={09eed313-cd56-4d06-bd56-fac0f716b5dd} aComponent={Display} aText={Could not take a screenshot (VERR_NOT_SUPPORTED)}, preserve=false
 00:00:03.055 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=b2d15000 w=640 h=480 bpp=32 cbLine=0xA00, flags=0x1
 00:00:03.331 2D video acceleration is disabled.
 00:00:05.508 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=b2d15000 w=640 h=480 bpp=0 cbLine=0x280, flags=0x1
 00:00:05.529 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=00000000 w=720 h=400 bpp=0 cbLine=0x0, flags=0x1
 00:00:05.529 PIT: mode=2 count=0x10000 (65536) - 18.20 Hz (ch=0)
 00:00:05.529 Guest Log: BIOS: Boot from Floppy 0 failed
 00:00:07.848 Guest Log: BIOS: Booting from CD-ROM...
 00:00:59.977 PIT: mode=2 count=0x2ead (11949) - 99.85 Hz (ch=0)
 

Any suggestions on this will be much appreciated.

Thanks,

---

### Post by Jake.Debord on 2011-08-11
Looks like it doesn't like something about the volume you are trying to install to.

Is the .vdi (virtual hard disk) on your hard drive or some other media like usb hard drive?

---

