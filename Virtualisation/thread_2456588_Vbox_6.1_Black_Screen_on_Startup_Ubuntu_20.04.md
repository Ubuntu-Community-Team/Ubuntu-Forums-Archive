---
title: "Vbox 6.1 Black Screen on Startup Ubuntu 20.04"
date: 2021-01-14
forum: Virtualisation
---

### Post by linuxnoob1232 on 2021-01-14
Hi! I had installed Ubuntu VM using virtualbox and was out of disk space.  I was trying to resize my disk(without success) and I had to remove my disk. After I added back my disk, when I start my VM I get a black screen. How can I solve this problem? Or how can I get the data on my VM back? When I start the VM I can see the ubuntu logo then it goes black.

---

### Post by linuxnoob1232 on 2021-01-14
Hi! I had installed Ubuntu VM using virtualbox and was out of disk space. I was trying to resize my disk(without success) and I had to remove my disk. After I added back my disk, when I start my VM I get a black screen. How can I solve this problem? Or how can I get the data on my VM back? When I start the VM I can see the ubuntu logo then it goes black.

Here are the logs:

```

00:00:02.837785 VirtualBox VM 6.1.16 r140961 win.amd64 (Oct 16 2020 16:33:17) release log
00:00:02.837790 Log opened 2021-01-14T00:28:46.765872700Z
00:00:02.837790 Build Type: release
00:00:02.837793 OS Product: Windows 10
00:00:02.837794 OS Release: 10.0.19041
00:00:02.837795 OS Service Pack: 
00:00:03.051943 DMI Product Name: GS65 Stealth 9SE
00:00:03.055587 DMI Product Version: REV:1.0
00:00:03.055592 Firmware type: UEFI
00:00:03.055969 Secure Boot: VERR_PRIVILEGE_NOT_HELD
00:00:03.055982 Host RAM: 32612MB (31.8GB) total, 17965MB (17.5GB) available
00:00:03.055985 Executable: C:\Program Files\Oracle\VirtualBox\VirtualBoxVM.exe
00:00:03.055985 Process ID: 12992
00:00:03.055985 Package type: WINDOWS_64BITS_GENERIC
00:00:03.056737 Installed Extension Packs:
00:00:03.056761   None installed!
00:00:03.057281 Console: Machine state changed to 'Starting'
00:00:03.057378 Qt version: 5.6.2
00:00:03.059207 GUI: UIMediumEnumerator: Medium-enumeration finished!
00:00:03.153512 SUP: seg #0: R   0x00000000 LB 0x00001000
00:00:03.153537 SUP: seg #1: R X 0x00001000 LB 0x0010a000
00:00:03.153549 SUP: seg #2: R   0x0010b000 LB 0x0004a000
00:00:03.153559 SUP: seg #3: RW  0x00155000 LB 0x00013000
00:00:03.153569 SUP: seg #4: R   0x00168000 LB 0x0000f000
00:00:03.153579 SUP: seg #5: RW  0x00177000 LB 0x00003000
00:00:03.153589 SUP: seg #6: R   0x0017a000 LB 0x0000b000
00:00:03.153598 SUP: seg #7: RWX 0x00185000 LB 0x00002000
00:00:03.153608 SUP: seg #8: R   0x00187000 LB 0x00007000
00:00:03.154455 SUP: Loaded VMMR0.r0 (C:\Program Files\Oracle\VirtualBox\VMMR0.r0) at 0xXXXXXXXXXXXXXXXX - ModuleInit at XXXXXXXXXXXXXXXX and ModuleTerm at XXXXXXXXXXXXXXXX using the native ring-0 loader
00:00:03.154475 SUP: VMMR0EntryEx located at XXXXXXXXXXXXXXXX and VMMR0EntryFast at XXXXXXXXXXXXXXXX
00:00:03.154486 SUP: windbg> .reload /f C:\Program Files\Oracle\VirtualBox\VMMR0.r0=0xXXXXXXXXXXXXXXXX
00:00:03.155618 Guest OS type: 'Ubuntu_64'
00:00:03.156202 fHMForced=true - No raw-mode support in this build!
00:00:03.158786 File system of 'C:\Program Files\Oracle\VirtualBox\VBoxGuestAdditions.iso' (DVD) is ntfs
00:00:03.160829 File system of 'C:\Users\amruta.deshmukh\VirtualBox VMs\Ubuntu\Snapshots' (snapshots) is ntfs
00:00:03.160847 File system of 'C:\Users\amruta.deshmukh\Ubuntu.vdi' is ntfs
00:00:03.174226 Shared Clipboard: Service loaded
00:00:03.174249 Shared Clipboard: Mode: Bidirectional
00:00:03.174543 Shared Clipboard: Service running in normal mode
00:00:03.183960 Drag and drop service loaded
00:00:03.183980 Drag and drop mode: Bidirectional
00:00:03.185236 ************************* CFGM dump *************************
00:00:03.185237 [/] (level 0)
00:00:03.185239   CpuExecutionCap   <integer> = 0x0000000000000064 (100)
00:00:03.185240   EnablePAE         <integer> = 0x0000000000000000 (0)
00:00:03.185241   HMEnabled         <integer> = 0x0000000000000001 (1)
00:00:03.185241   MemBalloonSize    <integer> = 0x0000000000000000 (0)
00:00:03.185242   Name              <string>  = "Ubuntu" (cb=7)
00:00:03.185243   NumCPUs           <integer> = 0x0000000000000002 (2)
00:00:03.185243   PageFusionAllowed <integer> = 0x0000000000000000 (0)
00:00:03.185244   RamHoleSize       <integer> = 0x0000000020000000 (536 870 912, 512 MB)
00:00:03.185245   RamSize           <integer> = 0x0000000100000000 (4 294 967 296, 4 096 MB, 4.0 GB)
00:00:03.185247   TimerMillies      <integer> = 0x000000000000000a (10)
00:00:03.185247   UUID              <bytes>   = "55 c1 81 5a 42 f0 1c 40 81 ca 16 ac 0b d4 9b cf" (cb=16)
00:00:03.185252 
00:00:03.185252 [/CPUM/] (level 1)
00:00:03.185253   GuestCpuName       <string>  = "host" (cb=5)
00:00:03.185254   NestedHWVirt       <integer> = 0x0000000000000000 (0)
00:00:03.185254   PortableCpuIdLevel <integer> = 0x0000000000000000 (0)
00:00:03.185255   SpecCtrl           <integer> = 0x0000000000000000 (0)
00:00:03.185256 [/CPUM/IsaExts/] (level 2)
00:00:03.185257 [/DBGC/] (level 1)
00:00:03.185257   GlobalInitScript <string>  = "C:\Users\amruta.deshmukh\.VirtualBox/dbgc-init" (cb=47)
00:00:03.185258   HistoryFile      <string>  = "C:\Users\amruta.deshmukh\.VirtualBox/dbgc-history" (cb=50)
00:00:03.185258   LocalInitScript  <string>  = "C:\Users\amruta.deshmukh\VirtualBox VMs\Ubuntu/dbgc-init" (cb=57)
00:00:03.185259 [/DBGF/] (level 1)
00:00:03.185260   Path <string>  = "C:\Users\amruta.deshmukh\VirtualBox VMs\Ubuntu/debug/;C:\Users\amruta.deshmukh\VirtualBox VMs\Ubuntu/;cache*C:\Users\amruta.deshmukh\VirtualBox VMs\Ubuntu/dbgcache/;C:\Users\amruta.deshmukh\" (cb=191)
00:00:03.185260 [/Devices/] (level 1)
00:00:03.185261 [/Devices/8237A/] (level 2)
00:00:03.185262 [/Devices/8237A/0/] (level 3)
00:00:03.185262   Trusted <integer> = 0x0000000000000001 (1)
00:00:03.185263 [/Devices/GIMDev/] (level 2)
00:00:03.185264 [/Devices/GIMDev/0/] (level 3)
00:00:03.185264   Trusted <integer> = 0x0000000000000001 (1)
00:00:03.185265 [/Devices/VMMDev/] (level 2)
00:00:03.185266 [/Devices/VMMDev/0/] (level 3)
00:00:03.185266   PCIBusNo      <integer> = 0x0000000000000000 (0)
00:00:03.185267   PCIDeviceNo   <integer> = 0x0000000000000004 (4)
00:00:03.185267   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:03.185268   Trusted       <integer> = 0x0000000000000001 (1)
00:00:03.185268 [/Devices/VMMDev/0/Config/] (level 4)
00:00:03.185269   GuestCoreDumpDir <string>  = "C:\Users\amruta.deshmukh\VirtualBox VMs\Ubuntu\Snapshots" (cb=57)
00:00:03.185270 [/Devices/VMMDev/0/LUN#0/] (level 4)
00:00:03.185271   Driver <string>  = "HGCM" (cb=5)
00:00:03.185271 [/Devices/VMMDev/0/LUN#0/Config/] (level 5)
00:00:03.185272   Object <integer> = 0x0000000007138e20 (118 722 080)
00:00:03.185273 [/Devices/VMMDev/0/LUN#999/] (level 4)
00:00:03.185274   Driver <string>  = "MainStatus" (cb=11)
00:00:03.185274 [/Devices/VMMDev/0/LUN#999/Config/] (level 5)
00:00:03.185275   First   <integer> = 0x0000000000000000 (0)
00:00:03.185276   Last    <integer> = 0x0000000000000000 (0)
00:00:03.185276   papLeds <integer> = 0x00000000024da230 (38 642 224)
00:00:03.185277 [/Devices/acpi/] (level 2)
00:00:03.185278 [/Devices/acpi/0/] (level 3)
00:00:03.185278   PCIBusNo      <integer> = 0x0000000000000000 (0)
00:00:03.185279   PCIDeviceNo   <integer> = 0x0000000000000007 (7)
00:00:03.185279   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:03.185280   Trusted       <integer> = 0x0000000000000001 (1)
00:00:03.185280 [/Devices/acpi/0/Config/] (level 4)
00:00:03.185281   CpuHotPlug          <integer> = 0x0000000000000000 (0)
00:00:03.185281   FdcEnabled          <integer> = 0x0000000000000000 (0)
00:00:03.185282   HostBusPciAddress   <integer> = 0x0000000000000000 (0)
00:00:03.185282   HpetEnabled         <integer> = 0x0000000000000000 (0)
00:00:03.185283   IOAPIC              <integer> = 0x0000000000000001 (1)
00:00:03.185283   IocPciAddress       <integer> = 0x0000000000010000 (65 536)
00:00:03.185284   NumCPUs             <integer> = 0x0000000000000002 (2)
00:00:03.185285   Parallel0IoPortBase <integer> = 0x0000000000000000 (0)
00:00:03.185285   Parallel0Irq        <integer> = 0x0000000000000000 (0)
00:00:03.185286   Parallel1IoPortBase <integer> = 0x0000000000000000 (0)
00:00:03.185286   Parallel1Irq        <integer> = 0x0000000000000000 (0)
00:00:03.185286   Serial0IoPortBase   <integer> = 0x0000000000000000 (0)
00:00:03.185287   Serial0Irq          <integer> = 0x0000000000000000 (0)
00:00:03.185287   Serial1IoPortBase   <integer> = 0x0000000000000000 (0)
00:00:03.185288   Serial1Irq          <integer> = 0x0000000000000000 (0)
00:00:03.185288   ShowCpu             <integer> = 0x0000000000000001 (1)
00:00:03.185289   ShowRtc             <integer> = 0x0000000000000000 (0)
00:00:03.185289   SmcEnabled          <integer> = 0x0000000000000000 (0)
00:00:03.185290 [/Devices/acpi/0/LUN#0/] (level 4)
00:00:03.185290   Driver <string>  = "ACPIHost" (cb=9)
00:00:03.185291 [/Devices/acpi/0/LUN#0/Config/] (level 5)
00:00:03.185292 [/Devices/acpi/0/LUN#1/] (level 4)
00:00:03.185292   Driver <string>  = "ACPICpu" (cb=8)
00:00:03.185293 [/Devices/acpi/0/LUN#1/Config/] (level 5)
00:00:03.185294 [/Devices/ahci/] (level 2)
00:00:03.185294 [/Devices/ahci/0/] (level 3)
00:00:03.185295   PCIBusNo      <integer> = 0x0000000000000000 (0)
00:00:03.185296   PCIDeviceNo   <integer> = 0x000000000000000d (13)
00:00:03.185296   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:03.185297   Trusted       <integer> = 0x0000000000000001 (1)
00:00:03.185297 [/Devices/ahci/0/Config/] (level 4)
00:00:03.185298   Bootable  <integer> = 0x0000000000000001 (1)
00:00:03.185298   PortCount <integer> = 0x0000000000000001 (1)
00:00:03.185299 [/Devices/ahci/0/Config/Port0/] (level 5)
00:00:03.185300   Hotpluggable <integer> = 0x0000000000000000 (0)
00:00:03.185300 [/Devices/ahci/0/LUN#0/] (level 4)
00:00:03.185301   Driver <string>  = "VD" (cb=3)
00:00:03.185301 [/Devices/ahci/0/LUN#0/Config/] (level 5)
00:00:03.185302   BlockCache <integer> = 0x0000000000000001 (1)
00:00:03.185303   Format     <string>  = "VDI" (cb=4)
00:00:03.185303   Mountable  <integer> = 0x0000000000000000 (0)
00:00:03.185303   Path       <string>  = "C:\Users\amruta.deshmukh\Ubuntu.vdi" (cb=36)
00:00:03.185304   Type       <string>  = "HardDisk" (cb=9)
00:00:03.185304   UseNewIo   <integer> = 0x0000000000000001 (1)
00:00:03.185305 [/Devices/ahci/0/LUN#0/Config/VDConfig/] (level 6)
00:00:03.185306   AllocationBlockSize <string>  = "1048576" (cb=8)
00:00:03.185306 [/Devices/ahci/0/LUN#999/] (level 4)
00:00:03.185307   Driver <string>  = "MainStatus" (cb=11)
00:00:03.185308 [/Devices/ahci/0/LUN#999/Config/] (level 5)
00:00:03.185309   DeviceInstance        <string>  = "ahci/0" (cb=7)
00:00:03.185309   First                 <integer> = 0x0000000000000000 (0)
00:00:03.185310   Last                  <integer> = 0x0000000000000000 (0)
00:00:03.185310   pConsole              <integer> = 0x00000000024d9970 (38 639 984)
00:00:03.185311   papLeds               <integer> = 0x00000000024d9db0 (38 641 072)
00:00:03.185312   pmapMediumAttachments <integer> = 0x00000000024da250 (38 642 256)
00:00:03.185313 [/Devices/apic/] (level 2)
00:00:03.185313 [/Devices/apic/0/] (level 3)
00:00:03.185314   Trusted <integer> = 0x0000000000000001 (1)
00:00:03.185314 [/Devices/apic/0/Config/] (level 4)
00:00:03.185315   IOAPIC  <integer> = 0x0000000000000001 (1)
00:00:03.185316   Mode    <integer> = 0x0000000000000003 (3)
00:00:03.185316   NumCPUs <integer> = 0x0000000000000002 (2)
00:00:03.185317 [/Devices/e1000/] (level 2)
00:00:03.185317 [/Devices/e1000/0/] (level 3)
00:00:03.185318   PCIBusNo      <integer> = 0x0000000000000000 (0)
00:00:03.185318   PCIDeviceNo   <integer> = 0x0000000000000003 (3)
00:00:03.185319   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:03.185319   Trusted       <integer> = 0x0000000000000001 (1)
00:00:03.185320 [/Devices/e1000/0/Config/] (level 4)
00:00:03.185320   AdapterType    <integer> = 0x0000000000000000 (0)
00:00:03.185321   CableConnected <integer> = 0x0000000000000001 (1)
00:00:03.185321   LineSpeed      <integer> = 0x0000000000000000 (0)
00:00:03.185322   MAC            <bytes>   = "08 00 27 df d8 6e" (cb=6)
00:00:03.185323 [/Devices/e1000/0/LUN#0/] (level 4)
00:00:03.185323   Driver <string>  = "NAT" (cb=4)
00:00:03.185324 [/Devices/e1000/0/LUN#0/Config/] (level 5)
00:00:03.185325   AliasMode       <integer> = 0x0000000000000000 (0)
00:00:03.185325   BootFile        <string>  = "Ubuntu.pxe" (cb=11)
00:00:03.185326   DNSProxy        <integer> = 0x0000000000000000 (0)
00:00:03.185326   Network         <string>  = "10.0.2.0/24" (cb=12)
00:00:03.185327   PassDomain      <integer> = 0x0000000000000001 (1)
00:00:03.185327   TFTPPrefix      <string>  = "C:\Users\amruta.deshmukh\.VirtualBox\TFTP" (cb=42)
00:00:03.185328   UseHostResolver <integer> = 0x0000000000000000 (0)
00:00:03.185328 [/Devices/e1000/0/LUN#999/] (level 4)
00:00:03.185329   Driver <string>  = "MainStatus" (cb=11)
00:00:03.185330 [/Devices/e1000/0/LUN#999/Config/] (level 5)
00:00:03.185330   First   <integer> = 0x0000000000000000 (0)
00:00:03.185331   Last    <integer> = 0x0000000000000000 (0)
00:00:03.185331   papLeds <integer> = 0x00000000024da110 (38 641 936)
00:00:03.185332 [/Devices/i8254/] (level 2)
00:00:03.185333 [/Devices/i8254/0/] (level 3)
00:00:03.185333 [/Devices/i8254/0/Config/] (level 4)
00:00:03.185334 [/Devices/i8259/] (level 2)
00:00:03.185335 [/Devices/i8259/0/] (level 3)
00:00:03.185336   Trusted <integer> = 0x0000000000000001 (1)
00:00:03.185336 [/Devices/i8259/0/Config/] (level 4)
00:00:03.185337 [/Devices/ichac97/] (level 2)
00:00:03.185337 [/Devices/ichac97/0/] (level 3)
00:00:03.185338   PCIBusNo      <integer> = 0x0000000000000000 (0)
00:00:03.185338   PCIDeviceNo   <integer> = 0x0000000000000005 (5)
00:00:03.185339   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:03.185339   Trusted       <integer> = 0x0000000000000001 (1)
00:00:03.185340 [/Devices/ichac97/0/AudioConfig/] (level 4)
00:00:03.185341 [/Devices/ichac97/0/Config/] (level 4)
00:00:03.185341   Codec        <string>  = "AD1980" (cb=7)
00:00:03.185342   DebugEnabled <integer> = 0x0000000000000000 (0)
00:00:03.185342 [/Devices/ichac97/0/LUN#0/] (level 4)
00:00:03.185343   Driver <string>  = "AUDIO" (cb=6)
00:00:03.185343 [/Devices/ichac97/0/LUN#0/AttachedDriver/] (level 5)
00:00:03.185344   Driver <string>  = "DSoundAudio" (cb=12)
00:00:03.185345 [/Devices/ichac97/0/LUN#0/AttachedDriver/Config/] (level 6)
00:00:03.185346   StreamName <string>  = "Ubuntu" (cb=7)
00:00:03.185346 [/Devices/ichac97/0/LUN#0/Config/] (level 5)
00:00:03.185347   BufferSizeMs    <integer> = 0x0000000000000000 (0)
00:00:03.185347   DriverName      <string>  = "DSoundAudio" (cb=12)
00:00:03.185348   InputEnabled    <integer> = 0x0000000000000000 (0)
00:00:03.185348   OutputEnabled   <integer> = 0x0000000000000001 (1)
00:00:03.185349   PeriodSizeMs    <integer> = 0x0000000000000000 (0)
00:00:03.185349   PreBufferSizeMs <integer> = 0x00000000ffffffff (4 294 967 295)
00:00:03.185350 [/Devices/ichac97/0/LUN#1/] (level 4)
00:00:03.185351   Driver <string>  = "AUDIO" (cb=6)
00:00:03.185351 [/Devices/ichac97/0/LUN#2/] (level 4)
00:00:03.185352   Driver <string>  = "AUDIO" (cb=6)
00:00:03.185352 [/Devices/ioapic/] (level 2)
00:00:03.185353 [/Devices/ioapic/0/] (level 3)
00:00:03.185353   Trusted <integer> = 0x0000000000000001 (1)
00:00:03.185354 [/Devices/ioapic/0/Config/] (level 4)
00:00:03.185355   NumCPUs <integer> = 0x0000000000000002 (2)
00:00:03.185355 [/Devices/mc146818/] (level 2)
00:00:03.185356 [/Devices/mc146818/0/] (level 3)
00:00:03.185357 [/Devices/mc146818/0/Config/] (level 4)
00:00:03.185357   UseUTC <integer> = 0x0000000000000001 (1)
00:00:03.185358 [/Devices/parallel/] (level 2)
00:00:03.185358 [/Devices/pcarch/] (level 2)
00:00:03.185359 [/Devices/pcarch/0/] (level 3)
00:00:03.185360   Trusted <integer> = 0x0000000000000001 (1)
00:00:03.185361 [/Devices/pcarch/0/Config/] (level 4)
00:00:03.185361 [/Devices/pcbios/] (level 2)
00:00:03.185362 [/Devices/pcbios/0/] (level 3)
00:00:03.185362   Trusted <integer> = 0x0000000000000001 (1)
00:00:03.185363 [/Devices/pcbios/0/Config/] (level 4)
00:00:03.185364   APIC               <integer> = 0x0000000000000001 (1)
00:00:03.185365   BootDevice0        <string>  = "FLOPPY" (cb=7)
00:00:03.185365   BootDevice1        <string>  = "DVD" (cb=4)
00:00:03.185366   BootDevice2        <string>  = "IDE" (cb=4)
00:00:03.185366   BootDevice3        <string>  = "NONE" (cb=5)
00:00:03.185366   FloppyDevice       <string>  = "i82078" (cb=7)
00:00:03.185367   HardDiskDevice     <string>  = "piix3ide" (cb=9)
00:00:03.185367   IOAPIC             <integer> = 0x0000000000000001 (1)
00:00:03.185368   McfgBase           <integer> = 0x0000000000000000 (0)
00:00:03.185368   McfgLength         <integer> = 0x0000000000000000 (0)
00:00:03.185369   NumCPUs            <integer> = 0x0000000000000002 (2)
00:00:03.185369   PXEDebug           <integer> = 0x0000000000000000 (0)
00:00:03.185370   SataHardDiskDevice <string>  = "ahci" (cb=5)
00:00:03.185370   SataLUN1           <integer> = 0x0000000000000000 (0)
00:00:03.185371   UUID               <bytes>   = "55 c1 81 5a 42 f0 1c 40 81 ca 16 ac 0b d4 9b cf" (cb=16)
00:00:03.185372   UuidLe             <integer> = 0x0000000000000001 (1)
00:00:03.185373 [/Devices/pcbios/0/Config/NetBoot/] (level 5)
00:00:03.185373 [/Devices/pcbios/0/Config/NetBoot/0/] (level 6)
00:00:03.185374   NIC           <integer> = 0x0000000000000000 (0)
00:00:03.185375   PCIBusNo      <integer> = 0x0000000000000000 (0)
00:00:03.185375   PCIDeviceNo   <integer> = 0x0000000000000003 (3)
00:00:03.185376   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:03.185376 [/Devices/pci/] (level 2)
00:00:03.185377 [/Devices/pci/0/] (level 3)
00:00:03.185377   Trusted <integer> = 0x0000000000000001 (1)
00:00:03.185378 [/Devices/pci/0/Config/] (level 4)
00:00:03.185379   IOAPIC <integer> = 0x0000000000000001 (1)
00:00:03.185379 [/Devices/pcibridge/] (level 2)
00:00:03.185380 [/Devices/pckbd/] (level 2)
00:00:03.185381 [/Devices/pckbd/0/] (level 3)
00:00:03.185381   Trusted <integer> = 0x0000000000000001 (1)
00:00:03.185382 [/Devices/pckbd/0/Config/] (level 4)
00:00:03.185382 [/Devices/pckbd/0/LUN#0/] (level 4)
00:00:03.185383   Driver <string>  = "KeyboardQueue" (cb=14)
00:00:03.185384 [/Devices/pckbd/0/LUN#0/AttachedDriver/] (level 5)
00:00:03.185384   Driver <string>  = "MainKeyboard" (cb=13)
00:00:03.185385 [/Devices/pckbd/0/LUN#0/AttachedDriver/Config/] (level 6)
00:00:03.185386   Object <integer> = 0x00000000024644b0 (38 159 536)
00:00:03.185387 [/Devices/pckbd/0/LUN#0/Config/] (level 5)
00:00:03.185387   QueueSize <integer> = 0x0000000000000040 (64)
00:00:03.185388 [/Devices/pckbd/0/LUN#1/] (level 4)
00:00:03.185389   Driver <string>  = "MouseQueue" (cb=11)
00:00:03.185389 [/Devices/pckbd/0/LUN#1/AttachedDriver/] (level 5)
00:00:03.185390   Driver <string>  = "MainMouse" (cb=10)
00:00:03.185391 [/Devices/pckbd/0/LUN#1/AttachedDriver/Config/] (level 6)
00:00:03.185391   Object <integer> = 0x0000000002583fd0 (39 337 936)
00:00:03.185392 [/Devices/pckbd/0/LUN#1/Config/] (level 5)
00:00:03.185393   QueueSize <integer> = 0x0000000000000080 (128)
00:00:03.185393 [/Devices/pcnet/] (level 2)
00:00:03.185394 [/Devices/piix3ide/] (level 2)
00:00:03.185395 [/Devices/piix3ide/0/] (level 3)
00:00:03.185395   PCIBusNo      <integer> = 0x0000000000000000 (0)
00:00:03.185396   PCIDeviceNo   <integer> = 0x0000000000000001 (1)
00:00:03.185396   PCIFunctionNo <integer> = 0x0000000000000001 (1)
00:00:03.185397   Trusted       <integer> = 0x0000000000000001 (1)
00:00:03.185397 [/Devices/piix3ide/0/Config/] (level 4)
00:00:03.185398   Type <string>  = "PIIX4" (cb=6)
00:00:03.185399 [/Devices/piix3ide/0/LUN#0/] (level 4)
00:00:03.185399   Driver <string>  = "VD" (cb=3)
00:00:03.185400 [/Devices/piix3ide/0/LUN#0/Config/] (level 5)
00:00:03.185400   Format    <string>  = "RAW" (cb=4)
00:00:03.185401   Mountable <integer> = 0x0000000000000001 (1)
00:00:03.185401   Path      <string>  = "C:\Program Files\Oracle\VirtualBox\VBoxGuestAdditions.iso" (cb=58)
00:00:03.185402   ReadOnly  <integer> = 0x0000000000000001 (1)
00:00:03.185402   Type      <string>  = "DVD" (cb=4)
00:00:03.185403 [/Devices/piix3ide/0/LUN#999/] (level 4)
00:00:03.185403   Driver <string>  = "MainStatus" (cb=11)
00:00:03.185404 [/Devices/piix3ide/0/LUN#999/Config/] (level 5)
00:00:03.185404   DeviceInstance        <string>  = "piix3ide/0" (cb=11)
00:00:03.185405   First                 <integer> = 0x0000000000000000 (0)
00:00:03.185405   Last                  <integer> = 0x0000000000000003 (3)
00:00:03.185406   pConsole              <integer> = 0x00000000024d9970 (38 639 984)
00:00:03.185407   papLeds               <integer> = 0x00000000024d9d90 (38 641 040)
00:00:03.185407   pmapMediumAttachments <integer> = 0x00000000024da250 (38 642 256)
00:00:03.185408 [/Devices/serial/] (level 2)
00:00:03.185409 [/Devices/usb-ohci/] (level 2)
00:00:03.185409 [/Devices/usb-ohci/0/] (level 3)
00:00:03.185410   PCIBusNo      <integer> = 0x0000000000000000 (0)
00:00:03.185411   PCIDeviceNo   <integer> = 0x0000000000000006 (6)
00:00:03.185411   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:03.185411   Trusted       <integer> = 0x0000000000000001 (1)
00:00:03.185412 [/Devices/usb-ohci/0/Config/] (level 4)
00:00:03.185413 [/Devices/usb-ohci/0/LUN#0/] (level 4)
00:00:03.185413   Driver <string>  = "VUSBRootHub" (cb=12)
00:00:03.185414 [/Devices/usb-ohci/0/LUN#0/Config/] (level 5)
00:00:03.185415 [/Devices/usb-ohci/0/LUN#999/] (level 4)
00:00:03.185415   Driver <string>  = "MainStatus" (cb=11)
00:00:03.185416 [/Devices/usb-ohci/0/LUN#999/Config/] (level 5)
00:00:03.185416   First   <integer> = 0x0000000000000000 (0)
00:00:03.185417   Last    <integer> = 0x0000000000000000 (0)
00:00:03.185417   papLeds <integer> = 0x00000000024da238 (38 642 232)
00:00:03.185418 [/Devices/vga/] (level 2)
00:00:03.185419 [/Devices/vga/0/] (level 3)
00:00:03.185419   PCIBusNo      <integer> = 0x0000000000000000 (0)
00:00:03.185420   PCIDeviceNo   <integer> = 0x0000000000000002 (2)
00:00:03.185420   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:03.185421   Trusted       <integer> = 0x0000000000000001 (1)
00:00:03.185421 [/Devices/vga/0/Config/] (level 4)
00:00:03.185422   3DEnabled          <integer> = 0x0000000000000000 (0)
00:00:03.185423   CustomVideoModes   <integer> = 0x0000000000000000 (0)
00:00:03.185423   FadeIn             <integer> = 0x0000000000000001 (1)
00:00:03.185424   FadeOut            <integer> = 0x0000000000000001 (1)
00:00:03.185424   HeightReduction    <integer> = 0x0000000000000000 (0)
00:00:03.185424   LogoFile           <string>  = "" (cb=1)
00:00:03.185425   LogoTime           <integer> = 0x0000000000000000 (0)
00:00:03.185425   MonitorCount       <integer> = 0x0000000000000001 (1)
00:00:03.185426   ShowBootMenu       <integer> = 0x0000000000000002 (2)
00:00:03.185426   VMSVGA3dEnabled    <integer> = 0x0000000000000000 (0)
00:00:03.185427   VMSVGAEnabled      <integer> = 0x0000000000000001 (1)
00:00:03.185427   VMSVGAPciBarLayout <integer> = 0x0000000000000001 (1)
00:00:03.185428   VMSVGAPciId        <integer> = 0x0000000000000001 (1)
00:00:03.185428   VRamSize           <integer> = 0x0000000008000000 (134 217 728, 128 MB)
00:00:03.185429 [/Devices/vga/0/LUN#0/] (level 4)
00:00:03.185430   Driver <string>  = "MainDisplay" (cb=12)
00:00:03.185431 [/Devices/vga/0/LUN#0/Config/] (level 5)
00:00:03.185431   Object <integer> = 0x00000000025847c0 (39 339 968)
00:00:03.185432 [/Devices/vga/0/LUN#999/] (level 4)
00:00:03.185433   Driver <string>  = "MainStatus" (cb=11)
00:00:03.185433 [/Devices/vga/0/LUN#999/Config/] (level 5)
00:00:03.185434   First   <integer> = 0x0000000000000000 (0)
00:00:03.185434   Last    <integer> = 0x0000000000000000 (0)
00:00:03.185435   papLeds <integer> = 0x00000000024da248 (38 642 248)
00:00:03.185435 [/Devices/virtio-net/] (level 2)
00:00:03.185436 [/EM/] (level 1)
00:00:03.185437   TripleFaultReset <integer> = 0x0000000000000000 (0)
00:00:03.185437 [/GIM/] (level 1)
00:00:03.185438   Provider <string>  = "KVM" (cb=4)
00:00:03.185438 [/HM/] (level 1)
00:00:03.185439   64bitEnabled            <integer> = 0x0000000000000001 (1)
00:00:03.185439   EnableLargePages        <integer> = 0x0000000000000001 (1)
00:00:03.185440   EnableNestedPaging      <integer> = 0x0000000000000001 (1)
00:00:03.185440   EnableUX                <integer> = 0x0000000000000001 (1)
00:00:03.185441   EnableVPID              <integer> = 0x0000000000000001 (1)
00:00:03.185441   Exclusive               <integer> = 0x0000000000000000 (0)
00:00:03.185442   HMForced                <integer> = 0x0000000000000001 (1)
00:00:03.185442   IBPBOnVMEntry           <integer> = 0x0000000000000000 (0)
00:00:03.185442   IBPBOnVMExit            <integer> = 0x0000000000000000 (0)
00:00:03.185443   L1DFlushOnSched         <integer> = 0x0000000000000001 (1)
00:00:03.185443   L1DFlushOnVMEntry       <integer> = 0x0000000000000000 (0)
00:00:03.185444   LovelyMesaDrvWorkaround <integer> = 0x0000000000000001 (1)
00:00:03.185444   MDSClearOnSched         <integer> = 0x0000000000000001 (1)
00:00:03.185445   MDSClearOnVMEntry       <integer> = 0x0000000000000000 (0)
00:00:03.185445   SpecCtrlByHost          <integer> = 0x0000000000000000 (0)
00:00:03.185446   UseNEMInstead           <integer> = 0x0000000000000000 (0)
00:00:03.185446 [/MM/] (level 1)
00:00:03.185447   CanUseLargerHeap <integer> = 0x0000000000000000 (0)
00:00:03.185447 [/NEM/] (level 1)
00:00:03.185448   Allow64BitGuests        <integer> = 0x0000000000000001 (1)
00:00:03.185448   LovelyMesaDrvWorkaround <integer> = 0x0000000000000001 (1)
00:00:03.185449 [/PDM/] (level 1)
00:00:03.185449 
00:00:03.185449 [/PDM/AsyncCompletion/] (level 2)
00:00:03.185450 
00:00:03.185450 [/PDM/AsyncCompletion/File/] (level 3)
00:00:03.185451 
00:00:03.185451 [/PDM/AsyncCompletion/File/BwGroups/] (level 4)
00:00:03.185451 
00:00:03.185452 [/PDM/BlkCache/] (level 2)
00:00:03.185452   CacheSize <integer> = 0x0000000000500000 (5 242 880, 5 MB)
00:00:03.185453 
00:00:03.185453 [/PDM/Devices/] (level 2)
00:00:03.185454 
00:00:03.185454 [/PDM/Drivers/] (level 2)
00:00:03.185454 
00:00:03.185454 [/PDM/Drivers/VBoxC/] (level 3)
00:00:03.185455   Path <string>  = "VBoxC" (cb=6)
00:00:03.185456 
00:00:03.185456 [/PDM/NetworkShaper/] (level 2)
00:00:03.185456 
00:00:03.185456 [/PDM/NetworkShaper/BwGroups/] (level 3)
00:00:03.185457 
00:00:03.185457 [/TM/] (level 1)
00:00:03.185458   UTCOffset <integer> = 0x0000000000000000 (0)
00:00:03.185458 
00:00:03.185458 [/USB/] (level 1)
00:00:03.185459 
00:00:03.185459 [/USB/HidMouse/] (level 2)
00:00:03.185459 
00:00:03.185459 [/USB/HidMouse/0/] (level 3)
00:00:03.185460 
00:00:03.185460 [/USB/HidMouse/0/Config/] (level 4)
00:00:03.185461   Mode <string>  = "absolute" (cb=9)
00:00:03.185461 
00:00:03.185461 [/USB/HidMouse/0/LUN#0/] (level 4)
00:00:03.185462   Driver <string>  = "MouseQueue" (cb=11)
00:00:03.185462 
00:00:03.185462 [/USB/HidMouse/0/LUN#0/AttachedDriver/] (level 5)
00:00:03.185463   Driver <string>  = "MainMouse" (cb=10)
00:00:03.185463 
00:00:03.185464 [/USB/HidMouse/0/LUN#0/AttachedDriver/Config/] (level 6)
00:00:03.185464   Object <integer> = 0x0000000002583fd0 (39 337 936)
00:00:03.185465 
00:00:03.185465 [/USB/HidMouse/0/LUN#0/Config/] (level 5)
00:00:03.185466   QueueSize <integer> = 0x0000000000000080 (128)
00:00:03.185466 
00:00:03.185467 [/USB/USBProxy/] (level 2)
00:00:03.185467 
00:00:03.185467 [/USB/USBProxy/GlobalConfig/] (level 3)
00:00:03.185468 
00:00:03.185468 ********************* End of CFGM dump **********************
00:00:03.185615 HM: HMR3Init: VT-x w/ nested paging and unrestricted guest execution hw support
00:00:03.185707 MM: cbHyperHeap=0x240000 (2359296)
00:00:03.188544 CPUM: fXStateHostMask=0x7; initial: 0x7; host XCR0=0x1f
00:00:03.189398 CPUM: Matched host CPU INTEL 0x6/0x9e/0xa Intel_Core7_CoffeeLake with CPU DB entry 'Intel Core i7-6700K' (INTEL 0x6/0x5e/0x3 Intel_Core7_Skylake)
00:00:03.189463 CPUM: MXCSR_MASK=0xffff (host: 0xffff)
00:00:03.189485 CPUM: Microcode revision 0x000000B4
00:00:03.189501 CPUM: Changing leaf 13[0]: EBX=0x440 -> 0x340, ECX=0x440 -> 0x340
00:00:03.189519 CPUM: MSR/CPUID reconciliation insert: 0x0000010b IA32_FLUSH_CMD
00:00:03.189640 PGM: Host paging mode: AMD64+NX
00:00:03.189655 PGM: PGMPool: cMaxPages=2304 (u64MaxPages=2084)
00:00:03.189666 PGM: pgmR3PoolInit: cMaxPages=0x900 cMaxUsers=0x1200 cMaxPhysExts=0x1200 fCacheEnable=true
00:00:03.210858 TM: GIP - u32Mode=3 (Invariant) u32UpdateHz=93 u32UpdateIntervalNS=10736000 enmUseTscDelta=2 (Practically Zero) fGetGipCpu=0x1b cCpus=12
00:00:03.210883 TM: GIP - u64CpuHz=2 592 003 342 (0x9a7ed50e)  SUPGetCpuHzFromGip => 2 592 003 342
00:00:03.210896 TM: GIP - CPU: iCpuSet=0x0 idCpu=0x0 idApic=0x0 iGipCpu=0x9 i64TSCDelta=0 enmState=3 u64CpuHz=2592003296(*) cErrors=0
00:00:03.210907 TM: GIP - CPU: iCpuSet=0x1 idCpu=0x1 idApic=0x1 iGipCpu=0x8 i64TSCDelta=0 enmState=3 u64CpuHz=2592003280(*) cErrors=0
00:00:03.210918 TM: GIP - CPU: iCpuSet=0x2 idCpu=0x2 idApic=0x2 iGipCpu=0x1 i64TSCDelta=1 enmState=3 u64CpuHz=2592007620(*) cErrors=0
00:00:03.210928 TM: GIP - CPU: iCpuSet=0x3 idCpu=0x3 idApic=0x3 iGipCpu=0x2 i64TSCDelta=0 enmState=3 u64CpuHz=2592000236(*) cErrors=0
00:00:03.210938 TM: GIP - CPU: iCpuSet=0x4 idCpu=0x4 idApic=0x4 iGipCpu=0xb i64TSCDelta=0 enmState=3 u64CpuHz=2592003334(*) cErrors=0
00:00:03.210948 TM: GIP - CPU: iCpuSet=0x5 idCpu=0x5 idApic=0x5 iGipCpu=0x5 i64TSCDelta=0 enmState=3 u64CpuHz=2592003144(*) cErrors=0
00:00:03.210958 TM: GIP - CPU: iCpuSet=0x6 idCpu=0x6 idApic=0x6 iGipCpu=0x3 i64TSCDelta=0 enmState=3 u64CpuHz=2592002674(*) cErrors=0
00:00:03.210968 TM: GIP - CPU: iCpuSet=0x7 idCpu=0x7 idApic=0x7 iGipCpu=0x4 i64TSCDelta=0 enmState=3 u64CpuHz=2592003065(*) cErrors=0
00:00:03.210979 TM: GIP - CPU: iCpuSet=0x8 idCpu=0x8 idApic=0x8 iGipCpu=0x7 i64TSCDelta=0 enmState=3 u64CpuHz=2592003252(*) cErrors=0
00:00:03.210989 TM: GIP - CPU: iCpuSet=0x9 idCpu=0x9 idApic=0x9 iGipCpu=0x0 i64TSCDelta=0 enmState=3 u64CpuHz=2592003342(*) cErrors=0
00:00:03.210999 TM: GIP - CPU: iCpuSet=0xa idCpu=0xa idApic=0xa iGipCpu=0xa i64TSCDelta=0 enmState=3 u64CpuHz=2592003337(*) cErrors=0
00:00:03.211009 TM: GIP - CPU: iCpuSet=0xb idCpu=0xb idApic=0xb iGipCpu=0x6 i64TSCDelta=0 enmState=3 u64CpuHz=2592003199(*) cErrors=0
00:00:03.211050 TM: cTSCTicksPerSecond=2 592 003 342 (0x9a7ed50e) enmTSCMode=1 (VirtTscEmulated)
00:00:03.211053 TM: TSCTiedToExecution=false TSCNotTiedToHalt=false
00:00:03.211673 EMR3Init: fIemExecutesAll=false fGuruOnTripleFault=true 
00:00:03.212028 IEM: TargetCpu=CURRENT, Microarch=Intel_Core7_CoffeeLake
00:00:03.212140 GIM: Using provider 'KVM' (Implementation version: 0)
00:00:03.212160 CPUM: SetGuestCpuIdFeature: Enabled Hypervisor Present bit
00:00:03.212245 AIOMgr: Default manager type is 'Async'
00:00:03.212258 AIOMgr: Default file backend is 'NonBuffered'
00:00:03.212489 BlkCache: Cache successfully initialized. Cache size is 5242880 bytes
00:00:03.212508 BlkCache: Cache commit interval is 10000 ms
00:00:03.212519 BlkCache: Cache commit threshold is 2621440 bytes
00:00:03.699274 PcBios: [SMP] BIOS with 2 CPUs
00:00:03.699305 PcBios: Using the 386+ BIOS image.
00:00:03.699388 PcBios: MPS table at 000e1300
00:00:03.701679 PcBios: fCheckShutdownStatusForSoftReset=true   fClearShutdownStatusOnHardReset=true
00:00:03.720512 SUP: seg #0: R   0x00000000 LB 0x00001000
00:00:03.720534 SUP: seg #1: R X 0x00001000 LB 0x0001e000
00:00:03.720546 SUP: seg #2: R   0x0001f000 LB 0x0000d000
00:00:03.720556 SUP: seg #3: RW  0x0002c000 LB 0x00001000
00:00:03.720566 SUP: seg #4: R   0x0002d000 LB 0x00003000
00:00:03.720576 SUP: seg #5: RWX 0x00030000 LB 0x00001000
00:00:03.720585 SUP: seg #6: R   0x00031000 LB 0x00002000
00:00:03.720635 SUP: Loaded VBoxDDR0.r0 (C:\Program Files\Oracle\VirtualBox\VBoxDDR0.r0) at 0xXXXXXXXXXXXXXXXX - ModuleInit at XXXXXXXXXXXXXXXX and ModuleTerm at XXXXXXXXXXXXXXXX using the native ring-0 loader
00:00:03.720648 SUP: windbg> .reload /f C:\Program Files\Oracle\VirtualBox\VBoxDDR0.r0=0xXXXXXXXXXXXXXXXX
00:00:03.720912 CPUM: SetGuestCpuIdFeature: Enabled xAPIC
00:00:03.720928 CPUM: SetGuestCpuIdFeature: Enabled x2APIC
00:00:03.721135 IOAPIC: Using implementation 2.0! Chipset type ICH9
00:00:03.721196 PIT: mode=3 count=0x10000 (65536) - 18.20 Hz (ch=0)
00:00:03.736621 Shared Folders service loaded
00:00:03.746631 Guest Control service loaded
00:00:03.949555 VGA: Using the 386+ BIOS image.
00:00:03.951211 DrvVD: Flushes will be ignored
00:00:03.951235 DrvVD: Async flushes will be passed to the disk
00:00:03.952359 VD: VDInit finished with VINF_SUCCESS
00:00:03.956032 AIOMgr: Endpoint for file 'C:\Users\xxxxx\Ubuntu.vdi' (flags 000c0723) created successfully
00:00:03.957826 VD: Opening the disk took 5768911 ns
00:00:03.957909 AHCI: LUN#0: disk, PCHS=16383/16/63, total number of sectors 42038336
00:00:03.958174 AHCI#0: Reset the HBA
00:00:03.958193 VD#0: Cancelling all active requests
00:00:03.960767 DrvVD: Flushes will be ignored
00:00:03.960783 DrvVD: Async flushes will be passed to the disk
00:00:03.961287 VD: Opening the disk took 489104 ns
00:00:03.961335 PIIX3 ATA: LUN#0: CD/DVD, total number of sectors 29779, passthrough disabled
00:00:03.961384 PIIX3 ATA: LUN#1: no unit
00:00:03.961455 PIIX3 ATA: LUN#2: no unit
00:00:03.961470 PIIX3 ATA: LUN#3: no unit
00:00:03.961527 PIIX3 ATA: Ctl#0: finished processing RESET
00:00:03.961604 PIIX3 ATA: Ctl#1: finished processing RESET
00:00:03.961703 E1000#0: Chip=82540EM LinkUpDelay=3000ms EthernetCRC=on GSO=enabled Itr=disabled ItrRx=enabled TID=disabled R0=enabled RC=disabled
00:00:03.973876 NAT: Guest address guess set to 10.0.2.15 by initialization
00:00:03.992888 NAT: DNS#0: 192.168.31.1
00:00:03.993801 AC97: Using codec 'AD1980'
00:00:03.993862 Audio: Initializing DirectSound audio driver
00:00:04.802671 Audio: Found 5 devices for driver 'DSoundAudio'
00:00:04.802695 Audio: Device 'Primary Sound Driver':
00:00:04.802708 Audio:     Usage           = Output
00:00:04.802718 Audio:     Flags           = DEFAULT
00:00:04.802729 Audio:     Input channels  = 0
00:00:04.802739 Audio:     Output channels = 8
00:00:04.802750 Audio: Device 'Speakers (Realtek(R) Audio)':
00:00:04.802760 Audio:     Usage           = Output
00:00:04.802770 Audio:     Flags           = NONE
00:00:04.802780 Audio:     Input channels  = 0
00:00:04.802790 Audio:     Output channels = 8
00:00:04.802801 Audio: Device 'ASUS MG278 (NVIDIA High Definition Audio)':
00:00:04.802811 Audio:     Usage           = Output
00:00:04.802821 Audio:     Flags           = NONE
00:00:04.802831 Audio:     Input channels  = 0
00:00:04.802841 Audio:     Output channels = 2
00:00:04.802851 Audio: Device 'Primary Sound Capture Driver':
00:00:04.802862 Audio:     Usage           = Input
00:00:04.802872 Audio:     Flags           = NONE
00:00:04.802882 Audio:     Input channels  = 2
00:00:04.802892 Audio:     Output channels = 0
00:00:04.802902 Audio: Device 'Microphone (Realtek(R) Audio)':
00:00:04.802912 Audio:     Usage           = Input
00:00:04.802922 Audio:     Flags           = NONE
00:00:04.802932 Audio:     Input channels  = 2
00:00:04.802942 Audio:     Output channels = 0
00:00:04.802992 AC97: Reset
00:00:04.803007 AC97: Mixer reset (EAID=0x809, EACS=0x9)
00:00:04.803020 AC97: Record select to left=Microphone In, right=Microphone In
00:00:04.803491 VUSB: Attached 'HidMouse' to port 1 on RootHub#0 (FullSpeed)
00:00:04.803524 PGM: The CPU physical address width is 39 bits
00:00:04.803537 PGM: PGMR3InitFinalize: 4 MB PSE mask 0000007fffffffff -> VINF_SUCCESS
00:00:04.803675 TM: TMR3InitFinalize: fTSCModeSwitchAllowed=true 
00:00:04.803818 VMM: Thread-context hooks unavailable
00:00:04.803832 VMM: RTThreadPreemptIsPending() can be trusted
00:00:04.803842 VMM: Kernel preemption is possible
00:00:04.809236 HM: fWorldSwitcher=0x0 (fIbpbOnVmExit=false fIbpbOnVmEntry=false fL1dFlushOnVmEntry=false); fL1dFlushOnSched=true  fMdsClearOnVmEntry=false
00:00:04.809255 HM: Using VT-x implementation 3.0
00:00:04.809259 HM: Max resume loops                  = 8192
00:00:04.809259 HM: Host CR4                          = 0x370678
00:00:04.809260 HM: Host EFER                         = 0xd01
00:00:04.809260 HM: MSR_IA32_SMM_MONITOR_CTL          = 0x0
00:00:04.809261 HM: MSR_IA32_FEATURE_CONTROL          = 0x20005
00:00:04.809261 HM:   LOCK
00:00:04.809262 HM:   VMXON
00:00:04.809262 HM:   SGX_LAUNCH_EN
00:00:04.809262 HM: MSR_IA32_VMX_BASIC                = 0xda040000000004
00:00:04.809263 HM:   VMCS id                           = 0x4
00:00:04.809263 HM:   VMCS size                         = 1024 bytes
00:00:04.809264 HM:   VMCS physical address limit       = None
00:00:04.809264 HM:   VMCS memory type                  = Write Back (WB)
00:00:04.809264 HM:   Dual-monitor treatment support    = true 
00:00:04.809265 HM:   OUTS & INS instruction-info       = true 
00:00:04.809265 HM:   Supports true-capability MSRs     = true 
00:00:04.809265 HM:   VM-entry Xcpt error-code optional = false
00:00:04.809266 HM: MSR_IA32_VMX_PINBASED_CTLS        = 0x7f00000016
00:00:04.809266 HM:   EXT_INT_EXIT
00:00:04.809267 HM:   NMI_EXIT
00:00:04.809267 HM:   VIRTUAL_NMI
00:00:04.809267 HM:   PREEMPT_TIMER
00:00:04.809267 HM:   POSTED_INT (must be cleared)
00:00:04.809269 HM: MSR_IA32_VMX_PROCBASED_CTLS       = 0xfff9fffe0401e172
00:00:04.809270 HM:   INT_WINDOW_EXIT
00:00:04.809270 HM:   USE_TSC_OFFSETTING
00:00:04.809270 HM:   HLT_EXIT
00:00:04.809270 HM:   INVLPG_EXIT
00:00:04.809271 HM:   MWAIT_EXIT
00:00:04.809271 HM:   RDPMC_EXIT
00:00:04.809271 HM:   RDTSC_EXIT
00:00:04.809271 HM:   CR3_LOAD_EXIT (must be set)
00:00:04.809272 HM:   CR3_STORE_EXIT (must be set)
00:00:04.809272 HM:   CR8_LOAD_EXIT
00:00:04.809272 HM:   CR8_STORE_EXIT
00:00:04.809272 HM:   USE_TPR_SHADOW
00:00:04.809273 HM:   NMI_WINDOW_EXIT
00:00:04.809273 HM:   MOV_DR_EXIT
00:00:04.809273 HM:   UNCOND_IO_EXIT
00:00:04.809273 HM:   USE_IO_BITMAPS
00:00:04.809274 HM:   MONITOR_TRAP_FLAG
00:00:04.809274 HM:   USE_MSR_BITMAPS
00:00:04.809274 HM:   MONITOR_EXIT
00:00:04.809276 HM:   PAUSE_EXIT
00:00:04.809276 HM:   USE_SECONDARY_CTLS
00:00:04.809276 HM: MSR_IA32_VMX_PROCBASED_CTLS2      = 0x5fbcff00000000
00:00:04.809277 HM:   VIRT_APIC_ACCESS
00:00:04.809277 HM:   EPT
00:00:04.809277 HM:   DESC_TABLE_EXIT
00:00:04.809278 HM:   RDTSCP
00:00:04.809278 HM:   VIRT_X2APIC_MODE
00:00:04.809278 HM:   VPID
00:00:04.809278 HM:   WBINVD_EXIT
00:00:04.809279 HM:   UNRESTRICTED_GUEST
00:00:04.809279 HM:   APIC_REG_VIRT (must be cleared)
00:00:04.809279 HM:   VIRT_INT_DELIVERY (must be cleared)
00:00:04.809279 HM:   PAUSE_LOOP_EXIT
00:00:04.809280 HM:   RDRAND_EXIT
00:00:04.809280 HM:   INVPCID
00:00:04.809280 HM:   VMFUNC
00:00:04.809280 HM:   VMCS_SHADOWING (must be cleared)
00:00:04.809281 HM:   ENCLS_EXIT
00:00:04.809281 HM:   RDSEED_EXIT
00:00:04.809281 HM:   PML
00:00:04.809281 HM:   EPT_VE
00:00:04.809282 HM:   CONCEAL_VMX_FROM_PT
00:00:04.809282 HM:   XSAVES_XRSTORS
00:00:04.809282 HM:   MODE_BASED_EPT_PERM
00:00:04.809282 HM:   SPPTP_EPT (must be cleared)
00:00:04.809283 HM:   PT_EPT (must be cleared)
00:00:04.809283 HM:   TSC_SCALING (must be cleared)
00:00:04.809283 HM:   USER_WAIT_PAUSE (must be cleared)
00:00:04.809283 HM:   ENCLV_EXIT (must be cleared)
00:00:04.809284 HM: MSR_IA32_VMX_ENTRY_CTLS           = 0x3ffff000011ff
00:00:04.809284 HM:   LOAD_DEBUG (must be set)
00:00:04.809284 HM:   IA32E_MODE_GUEST
00:00:04.809285 HM:   ENTRY_TO_SMM
00:00:04.809285 HM:   DEACTIVATE_DUAL_MON
00:00:04.809285 HM:   LOAD_PERF_MSR
00:00:04.809285 HM:   LOAD_PAT_MSR
00:00:04.809286 HM:   LOAD_EFER_MSR
00:00:04.809286 HM:   LOAD_BNDCFGS_MSR
00:00:04.809286 HM:   CONCEAL_VMX_FROM_PT
00:00:04.809286 HM:   LOAD_RTIT_CTL_MSR (must be cleared)
00:00:04.809287 HM: MSR_IA32_VMX_EXIT_CTLS            = 0x1ffffff00036dff
00:00:04.809287 HM:   SAVE_DEBUG (must be set)
00:00:04.809287 HM:   HOST_ADDR_SPACE_SIZE
00:00:04.809288 HM:   LOAD_PERF_MSR
00:00:04.809288 HM:   ACK_EXT_INT
00:00:04.809288 HM:   SAVE_PAT_MSR
00:00:04.809288 HM:   LOAD_PAT_MSR
00:00:04.809290 HM:   SAVE_EFER_MSR
00:00:04.809290 HM:   LOAD_EFER_MSR
00:00:04.809291 HM:   SAVE_PREEMPT_TIMER
00:00:04.809291 HM:   CLEAR_BNDCFGS_MSR
00:00:04.809291 HM:   CONCEAL_VMX_FROM_PT
00:00:04.809291 HM:   CLEAR_RTIT_CTL_MSR (must be cleared)
00:00:04.809292 HM: MSR_IA32_VMX_TRUE_PINBASED_CTLS   = 0x7f00000016
00:00:04.809292 HM: MSR_IA32_VMX_TRUE_PROCBASED_CTLS  = 0xfff9fffe04006172
00:00:04.809293 HM: MSR_IA32_VMX_TRUE_ENTRY_CTLS      = 0x3ffff000011fb
00:00:04.809293 HM: MSR_IA32_VMX_TRUE_EXIT_CTLS       = 0x1ffffff00036dfb
00:00:04.809294 HM: MSR_IA32_VMX_MISC                 = 0x7004c1e7
00:00:04.809295 HM:   PREEMPT_TIMER_TSC                 = 0x7
00:00:04.809295 HM:   EXIT_SAVE_EFER_LMA                = true 
00:00:04.809295 HM:   ACTIVITY_STATES                   = 0x7 ( HLT SHUTDOWN SIPI_WAIT )
00:00:04.809296 HM:   INTEL_PT                          = true 
00:00:04.809296 HM:   SMM_READ_SMBASE_MSR               = true 
00:00:04.809296 HM:   CR3_TARGET                        = 0x4
00:00:04.809297 HM:   MAX_MSR                           = 0x0 ( 512 )
00:00:04.809297 HM:   VMXOFF_BLOCK_SMI                  = true 
00:00:04.809297 HM:   VMWRITE_ALL                       = true 
00:00:04.809298 HM:   ENTRY_INJECT_SOFT_INT             = 0x1
00:00:04.809298 HM:   MSEG_ID                           = 0x0
00:00:04.809298 HM: MSR_IA32_VMX_VMCS_ENUM            = 0x2e
00:00:04.809299 HM:   HIGHEST_IDX                       = 0x17
00:00:04.809299 HM: MSR_IA32_VMX_EPT_VPID_CAP         = 0xf0106734141
00:00:04.809300 HM:   RWX_X_ONLY
00:00:04.809300 HM:   PAGE_WALK_LENGTH_4
00:00:04.809300 HM:   EMT_UC
00:00:04.809300 HM:   EMT_WB
00:00:04.809300 HM:   PDE_2M
00:00:04.809301 HM:   PDPTE_1G
00:00:04.809301 HM:   INVEPT
00:00:04.809301 HM:   EPT_ACCESS_DIRTY
00:00:04.809301 HM:   ADVEXITINFO_EPT
00:00:04.809302 HM:   INVEPT_SINGLE_CONTEXT
00:00:04.809302 HM:   INVEPT_ALL_CONTEXTS
00:00:04.809302 HM:   INVVPID
00:00:04.809302 HM:   INVVPID_INDIV_ADDR
00:00:04.809302 HM:   INVVPID_SINGLE_CONTEXT
00:00:04.809303 HM:   INVVPID_ALL_CONTEXTS
00:00:04.809303 HM:   INVVPID_SINGLE_CONTEXT_RETAIN_GLOBALS
00:00:04.809303 HM: MSR_IA32_VMX_VMFUNC               = 0x1
00:00:04.809304 HM:   EPTP_SWITCHING
00:00:04.809304 HM: MSR_IA32_VMX_CR0_FIXED0           = 0x80000021
00:00:04.809304 HM: MSR_IA32_VMX_CR0_FIXED1           = 0xffffffff
00:00:04.809305 HM: MSR_IA32_VMX_CR4_FIXED0           = 0x2000
00:00:04.809305 HM: MSR_IA32_VMX_CR4_FIXED1           = 0x3727ff
00:00:04.809306 HM: APIC-access page physaddr         = 0x000000052030e000
00:00:04.809306 HM: VCPU  0: MSR bitmap physaddr      = 0x00000006d7a12000
00:00:04.809307 HM: VCPU  0: VMCS physaddr            = 0x00000006c1f0f000
00:00:04.809308 HM: VCPU  1: MSR bitmap physaddr      = 0x000000021cc16000
00:00:04.809308 HM: VCPU  1: VMCS physaddr            = 0x00000003a4a13000
00:00:04.809309 HM: Guest support: 32-bit and 64-bit
00:00:04.809314 HM: Supports VMCS EFER fields         = true 
00:00:04.809314 HM: Enabled VMX
00:00:04.809317 CPUM: SetGuestCpuIdFeature: Enabled SYSENTER/EXIT
00:00:04.809317 CPUM: SetGuestCpuIdFeature: Enabled PAE
00:00:04.809317 CPUM: SetGuestCpuIdFeature: Enabled LONG MODE
00:00:04.809318 CPUM: SetGuestCpuIdFeature: Enabled SYSCALL/RET
00:00:04.809318 CPUM: SetGuestCpuIdFeature: Enabled LAHF/SAHF
00:00:04.809318 CPUM: SetGuestCpuIdFeature: Enabled NX
00:00:04.809319 HM: Enabled nested paging
00:00:04.809319 HM:   EPT flush type                  = Single context
00:00:04.809319 HM: Enabled unrestricted guest execution
00:00:04.809320 HM: Enabled large page support
00:00:04.809320 HM: Enabled VPID
00:00:04.809320 HM:   VPID flush type                 = Single context
00:00:04.809320 HM: Enabled VMX-preemption timer (cPreemptTimerShift=7)
00:00:04.809321 HM: VT-x/AMD-V init method: Local
00:00:04.809321 EM: Exit history optimizations: enabled=true  enabled-r0=true  enabled-r0-no-preemption=false
00:00:04.809352 PcBios: SATA LUN#0 LCHS=1024/255/63
00:00:04.809370 APIC: fPostedIntrsEnabled=false fVirtApicRegsEnabled=false fSupportsTscDeadline=false
00:00:04.809382 TMR3UtcNow: nsNow=1 610 584 128 737 319 000 nsPrev=0 -> cNsDelta=1 610 584 128 737 319 000 (offLag=0 offVirtualSync=0 offVirtualSyncGivenUp=0, NowAgain=1 610 584 128 737 319 000)
00:00:04.809395 VMM: fUsePeriodicPreemptionTimers=false
00:00:04.809410 CPUM: Logical host processors: 12 present, 12 max, 12 online, online mask: 0000000000000fff
00:00:04.809411 CPUM: Physical host cores: 6
00:00:04.809411 ************************* CPUID dump ************************
00:00:04.809416          Raw Standard CPUID Leaves
00:00:04.809416      Leaf/sub-leaf  eax      ebx      ecx      edx
00:00:04.809418 Gst: 00000000/0000  00000016 756e6547 6c65746e 49656e69
00:00:04.809419 Hst:                00000016 756e6547 6c65746e 49656e69
00:00:04.809420 Gst: 00000001/0000  000906ea 00020800 d6fa2203 178bfbff
00:00:04.809420 Hst:                000906ea 03100800 7ffafbbf bfebfbff
00:00:04.809421 Gst: 00000002/0000  76036301 00f0b5ff 00000000 00c30000
00:00:04.809422 Hst:                76036301 00f0b5ff 00000000 00c30000
00:00:04.809423 Gst: 00000003/0000  00000000 00000000 00000000 00000000
00:00:04.809423 Hst:                00000000 00000000 00000000 00000000
00:00:04.809424 Gst: 00000004/0000  04000121 01c0003f 0000003f 00000000
00:00:04.809424 Hst:                1c004121 01c0003f 0000003f 00000000
00:00:04.809425 Gst: 00000004/0001  04000122 01c0003f 0000003f 00000000
00:00:04.809426 Hst:                1c004122 01c0003f 0000003f 00000000
00:00:04.809427 Gst: 00000004/0002  04000143 00c0003f 000003ff 00000000
00:00:04.809427 Hst:                1c004143 00c0003f 000003ff 00000000
00:00:04.809428 Gst: 00000004/0003  04000163 03c0003f 00002fff 00000006
00:00:04.809428 Hst:                1c03c163 03c0003f 00002fff 00000006
00:00:04.809429 Gst: 00000004/0004  04000000 00000000 00000000 00000000
00:00:04.809430 Hst:                00000000 00000000 00000000 00000000
00:00:04.809430 Gst: 00000005/0000  00000000 00000000 00000000 00000000
00:00:04.809431 Hst:                00000040 00000040 00000003 11142120
00:00:04.809432 Gst: 00000006/0000  00000000 00000000 00000000 00000000
00:00:04.809432 Hst:                000027f7 00000002 00000009 00000000
00:00:04.809433 Gst: 00000007/0000  00000000 00842421 00000000 10000400
00:00:04.809433 Hst:                00000000 029c67af 40000000 9c002400
00:00:04.809434 Gst: 00000007/0001  00000000 00000000 00000000 00000000
00:00:04.809434 Hst:                00000000 00000000 00000000 00000000
00:00:04.809435 Gst: 00000008/0000  00000000 00000000 00000000 00000000
00:00:04.809435 Hst:                00000000 00000000 00000000 00000000
00:00:04.809436 Gst: 00000009/0000  00000000 00000000 00000000 00000000
00:00:04.809436 Hst:                00000000 00000000 00000000 00000000
00:00:04.809436 Gst: 0000000a/0000  00000000 00000000 00000000 00000000
00:00:04.809437 Hst:                07300404 00000000 00000000 00000603
00:00:04.809437 Gst: 0000000b/0000  00000000 00000001 00000100 00000000
00:00:04.809438 Hst:                00000001 00000002 00000100 00000003
00:00:04.809438 Gst: 0000000b/0001  00000001 00000002 00000201 00000000
00:00:04.809439 Hst:                00000004 0000000c 00000201 00000003
00:00:04.809439 Gst: 0000000b/0002  00000000 00000000 00000002 00000000
00:00:04.809440 Hst:                00000000 00000000 00000002 00000003
00:00:04.809440 Gst: 0000000c/0000  00000000 00000000 00000000 00000000
00:00:04.809441 Hst:                00000000 00000000 00000000 00000000
00:00:04.809441 Gst: 0000000d/0000  00000007 00000340 00000340 00000000
00:00:04.809442 Hst:                0000001f 00000440 00000440 00000000
00:00:04.809442 Gst: 0000000d/0001  00000000 00000440 00000000 00000000
00:00:04.809443 Hst:                0000000f 00000440 00000100 00000000
00:00:04.809443 Gst: 0000000d/0002  00000100 00000240 00000000 00000000
00:00:04.809444 Hst:                00000100 00000240 00000000 00000000
00:00:04.809444 Gst: 0000000d/0003  00000000 00000000 00000000 00000000
00:00:04.809444 Hst:                00000040 000003c0 00000000 00000000
00:00:04.809445 Gst: 0000000d/0004  00000000 00000000 00000000 00000000
00:00:04.809445 Hst:                00000040 00000400 00000000 00000000
00:00:04.809446 Gst: 0000000d/0005  00000000 00000000 00000000 00000000
00:00:04.809446 Hst:                00000000 00000000 00000000 00000000
00:00:04.809447 Gst: 0000000d/0006  00000000 00000000 00000000 00000000
00:00:04.809447 Hst:                00000000 00000000 00000000 00000000
00:00:04.809448 Gst: 0000000d/0007  00000000 00000000 00000000 00000000
00:00:04.809448 Hst:                00000000 00000000 00000000 00000000
00:00:04.809449 Gst: 0000000d/0008  00000000 00000000 00000000 00000000
00:00:04.809449 Hst:                00000080 00000000 00000001 00000000
00:00:04.809450 Gst: 0000000d/0009  00000000 00000000 00000000 00000000
00:00:04.809450 Hst:                00000000 00000000 00000000 00000000
00:00:04.809464 Gst: 0000000e/0000  00000000 00000000 00000000 00000000
00:00:04.809465 Hst:                00000000 00000000 00000000 00000000
00:00:04.809465 Gst: 0000000f/0000  00000000 00000000 00000000 00000000
00:00:04.809466 Hst:                00000000 00000000 00000000 00000000
00:00:04.809466 Gst: 00000010/0000  00000000 00000000 00000000 00000000
00:00:04.809467 Hst:                00000000 00000000 00000000 00000000
00:00:04.809467 Gst: 00000011/0000  00000000 00000000 00000000 00000000
00:00:04.809467 Hst:                00000000 00000000 00000000 00000000
00:00:04.809468 Gst: 00000012/0000  00000000 00000000 00000000 00000000
00:00:04.809468 Hst:                00000000 00000000 00000000 00000000
00:00:04.809469 Gst: 00000013/0000  00000000 00000000 00000000 00000000
00:00:04.809469 Hst:                00000000 00000000 00000000 00000000
00:00:04.809470 Gst: 00000014/0000  00000000 00000000 00000000 00000000
00:00:04.809470 Hst:                00000001 0000000f 00000007 00000000
00:00:04.809471 Hst: 00000015/0000  00000002 000000d8 00000000 00000000
00:00:04.809471 Hst: 00000016/0000  00000a28 00001194 00000064 00000000
00:00:04.809472                                Name: GenuineIntel
00:00:04.809473                            Supports: 0x00000000-0x00000016
00:00:04.809475                              Family:  6 	Extended: 0 	Effective: 6
00:00:04.809476                               Model: 14 	Extended: 9 	Effective: 158
00:00:04.809477                            Stepping: 10
00:00:04.809477                                Type: 0 (primary)
00:00:04.809478                             APIC ID: 0x00
00:00:04.809478                        Logical CPUs: 2
00:00:04.809479                        CLFLUSH Size: 8
00:00:04.809479                            Brand ID: 0x00
00:00:04.809480 Features
00:00:04.809480   Mnemonic - Description                                  = guest (host)
00:00:04.809482   FPU - x87 FPU on Chip                                   = 1 (1)
00:00:04.809483   VME - Virtual 8086 Mode Enhancements                    = 1 (1)
00:00:04.809484   DE - Debugging extensions                               = 1 (1)
00:00:04.809484   PSE - Page Size Extension                               = 1 (1)
00:00:04.809485   TSC - Time Stamp Counter                                = 1 (1)
00:00:04.809485   MSR - Model Specific Registers                          = 1 (1)
00:00:04.809486   PAE - Physical Address Extension                        = 1 (1)
00:00:04.809487   MCE - Machine Check Exception                           = 1 (1)
00:00:04.809487   CX8 - CMPXCHG8B instruction                             = 1 (1)
00:00:04.809488   APIC - APIC On-Chip                                     = 1 (1)
00:00:04.809488   SEP - SYSENTER and SYSEXIT Present                      = 1 (1)
00:00:04.809489   MTRR - Memory Type Range Registers                      = 1 (1)
00:00:04.809490   PGE - PTE Global Bit                                    = 1 (1)
00:00:04.809490   MCA - Machine Check Architecture                        = 1 (1)
00:00:04.809491   CMOV - Conditional Move instructions                    = 1 (1)
00:00:04.809491   PAT - Page Attribute Table                              = 1 (1)
00:00:04.809492   PSE-36 - 36-bit Page Size Extension                     = 1 (1)
00:00:04.809492   PSN - Processor Serial Number                           = 0 (0)
00:00:04.809493   CLFSH - CLFLUSH instruction                             = 1 (1)
00:00:04.809494   DS - Debug Store                                        = 0 (1)
00:00:04.809494   ACPI - Thermal Mon. & Soft. Clock Ctrl.                 = 0 (1)
00:00:04.809495   MMX - Intel MMX Technology                              = 1 (1)
00:00:04.809495   FXSR - FXSAVE and FXRSTOR instructions                  = 1 (1)
00:00:04.809496   SSE - SSE support                                       = 1 (1)
00:00:04.809497   SSE2 - SSE2 support                                     = 1 (1)
00:00:04.809497   SS - Self Snoop                                         = 0 (1)
00:00:04.809498   HTT - Hyper-Threading Technology                        = 1 (1)
00:00:04.809498   TM - Therm. Monitor                                     = 0 (1)
00:00:04.809499   PBE - Pending Break Enabled                             = 0 (1)
00:00:04.809500   SSE3 - SSE3 support                                     = 1 (1)
00:00:04.809500   PCLMUL - PCLMULQDQ support (for AES-GCM)                = 1 (1)
00:00:04.809501   DTES64 - DS Area 64-bit Layout                          = 0 (1)
00:00:04.809502   MONITOR - MONITOR/MWAIT instructions                    = 0 (1)
00:00:04.809502   CPL-DS - CPL Qualified Debug Store                      = 0 (1)
00:00:04.809503   VMX - Virtual Machine Extensions                        = 0 (1)
00:00:04.809503   SMX - Safer Mode Extensions                             = 0 (0)
00:00:04.809504   EST - Enhanced SpeedStep Technology                     = 0 (1)
00:00:04.809504   TM2 - Terminal Monitor 2                                = 0 (1)
00:00:04.809505   SSSE3 - Supplemental Streaming SIMD Extensions 3        = 1 (1)
00:00:04.809505   CNTX-ID - L1 Context ID                                 = 0 (0)
00:00:04.809506   SDBG - Silicon Debug interface                          = 0 (1)
00:00:04.809507   FMA - Fused Multiply Add extensions                     = 0 (1)
00:00:04.809507   CX16 - CMPXCHG16B instruction                           = 1 (1)
00:00:04.809508   TPRUPDATE - xTPR Update Control                         = 0 (1)
00:00:04.809508   PDCM - Perf/Debug Capability MSR                        = 0 (1)
00:00:04.809509   PCID - Process Context Identifiers                      = 1 (1)
00:00:04.809510   DCA - Direct Cache Access                               = 0 (0)
00:00:04.809510   SSE4_1 - SSE4_1 support                                 = 1 (1)
00:00:04.809511   SSE4_2 - SSE4_2 support                                 = 1 (1)
00:00:04.809511   X2APIC - x2APIC support                                 = 1 (1)
00:00:04.809512   MOVBE - MOVBE instruction                               = 1 (1)
00:00:04.809513   POPCNT - POPCNT instruction                             = 1 (1)
00:00:04.809513   TSCDEADL - Time Stamp Counter Deadline                  = 0 (1)
00:00:04.809514   AES - AES instructions                                  = 1 (1)
00:00:04.809514   XSAVE - XSAVE instruction                               = 1 (1)
00:00:04.809515   OSXSAVE - OSXSAVE instruction                           = 0 (1)
00:00:04.809516   AVX - AVX support                                       = 1 (1)
00:00:04.809516   F16C - 16-bit floating point conversion instructions    = 0 (1)
00:00:04.809517   RDRAND - RDRAND instruction                             = 1 (1)
00:00:04.809517   HVP - Hypervisor Present (we're a guest)                = 1 (0)
00:00:04.809518 Structured Extended Feature Flags Enumeration (leaf 7):
00:00:04.809518   Mnemonic - Description                                  = guest (host)
00:00:04.809519   FSGSBASE - RDFSBASE/RDGSBASE/WRFSBASE/WRGSBASE instr.   = 1 (1)
00:00:04.809519   TSCADJUST - Supports MSR_IA32_TSC_ADJUST                = 0 (1)
00:00:04.809520   SGX - Supports Software Guard Extensions                = 0 (1)
00:00:04.809520   BMI1 - Advanced Bit Manipulation extension 1            = 0 (1)
00:00:04.809521   HLE - Hardware Lock Elision                             = 0 (0)
00:00:04.809521   AVX2 - Advanced Vector Extensions 2                     = 1 (1)
00:00:04.809522   FDP_EXCPTN_ONLY - FPU DP only updated on exceptions     = 0 (0)
00:00:04.809522   SMEP - Supervisor Mode Execution Prevention             = 0 (1)
00:00:04.809523   BMI2 - Advanced Bit Manipulation extension 2            = 0 (1)
00:00:04.809523   ERMS - Enhanced REP MOVSB/STOSB instructions            = 0 (1)
00:00:04.809524   INVPCID - INVPCID instruction                           = 1 (1)
00:00:04.809524   RTM - Restricted Transactional Memory                   = 0 (0)
00:00:04.809525   PQM - Platform Quality of Service Monitoring            = 0 (0)
00:00:04.809525   DEPFPU_CS_DS - Deprecates FPU CS, FPU DS values if set  = 1 (1)
00:00:04.809526   MPE - Intel Memory Protection Extensions                = 0 (1)
00:00:04.809526   PQE - Platform Quality of Service Enforcement           = 0 (0)
00:00:04.809527   AVX512F - AVX512 Foundation instructions                = 0 (0)
00:00:04.809527   RDSEED - RDSEED instruction                             = 1 (1)
00:00:04.809528   ADX - ADCX/ADOX instructions                            = 0 (1)
00:00:04.809529   SMAP - Supervisor Mode Access Prevention                = 0 (1)
00:00:04.809529   CLFLUSHOPT - CLFLUSHOPT (Cache Line Flush) instruction  = 1 (1)
00:00:04.809530   INTEL_PT - Intel Processor Trace                        = 0 (1)
00:00:04.809530   AVX512PF - AVX512 Prefetch instructions                 = 0 (0)
00:00:04.809531   AVX512ER - AVX512 Exponential & Reciprocal instructions = 0 (0)

```

---

### Post by yancek on 2021-01-15
How did you try to resize your disk?  How large did you create the disk?  What is the host operating system on which you installed VirtualBox and Ubuntu inside Virtualbox?  That's my understanding of what you did from your post, correct?  I've only done this once and don't have any notes from it but the link below explains how to do it?

[https://www.howtogeek.com/124622/how-to-enlarge-a-virtual-machines-disk-in-virtualbox-or-vmware/](https://www.howtogeek.com/124622/how-to-enlarge-a-virtual-machines-disk-in-virtualbox-or-vmware/)

>  After I added back my disk,  

Not sure what that means, what disk?  The disk/iso you used to install Ubuntu?

---

### Post by slickymaster on 2021-01-15
*Thread moved to **Virtualisation**.*

---

### Post by QIII on 2021-01-15
Threads merged.

---

