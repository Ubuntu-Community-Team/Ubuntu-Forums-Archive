---
title: "Re: Boot an existing XP (Physical HD) install with VirtualBox"
date: 2012-10-27
forum: Virtualisation
---

### Post by kiaeix on 2012-10-27
Hello, I tried to get my XP partition working with Virtual-Box 4.2 (not OSE) under Ubuntu 12.10 using this "manual":

[http://geekery.amhill.net/2010/01/27/virtualbox-with-existing-windows-partition/](http://geekery.amhill.net/2010/01/27/virtualbox-with-existing-windows-partition/)

The result is that after MBR I get this screen

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=226188&stc=1&d=1351325536[/IMG]

_VBoxSVC.log_ shows these errors:

```
00:00:08.176516 nspr-2   ERROR [COM]: aRC=VBOX_E_INVALID_VM_STATE (0x80bb0002) aIID={22781af3-1c96-4126-9edf-67a020e0e858} aComponent={Machine} aText={Machine is not locked for session (session state: Unlocked)}, preserve=false
00:00:08.614300 nspr-3   ERROR [COM]: aRC=VBOX_E_IPRT_ERROR (0x80bb0005) aIID={22781af3-1c96-4126-9edf-67a020e0e858} aComponent={SessionMachine} aText={Saved screenshot data is not available (VERR_NOT_SUPPORTED)}, preserve=false
00:00:10.295730 nspr-3   NetIfAdpCtlOut: VBoxNetAdpCtl: Error while retrieving link speed for wlan0: VBoxNetAdpCtl: ioctl failed: Operation not supported
00:00:23.468033 main     ERROR [COM]: aRC=VBOX_E_OBJECT_IN_USE (0x80bb000c) aIID={29989373-b111-4654-8493-2e1176cba890} aComponent={Medium} aText={Medium '/home/nima/.VirtualBox/winxp.vmdk' cannot be closed because it is still attached to 1 virtual machines}, preserve=false
00:00:23.472192 Watcher  ERROR [COM]: aRC=E_ACCESSDENIED (0x80070005) aIID={3b2f08eb-b810-4715-bee0-bb06b9880ad2} aComponent={VirtualBox} aText={The object is not ready}, preserve=false
```Has anybody any idea? :-k

---

### Post by howefield on 2012-10-27
Post moved to its own thread.

---

### Post by kiaeix on 2012-10-27
Here is the full log:

```

VirtualBox VM 4.2.2 r81494 linux.x86 (Oct 18 2012 15:47:21) release log
00:00:02.073129 Log opened 2012-10-27T10:26:07.720470000Z
00:00:02.073134 OS Product: Linux
00:00:02.073136 OS Release: 3.5.0-18-generic
00:00:02.073137 OS Version: #29-Ubuntu SMP Fri Oct 19 10:27:31 UTC 2012
00:00:02.073163 DMI Product Name: 2007CTO
00:00:02.073174 DMI Product Version: ThinkPad T60
00:00:02.073186 Host RAM: 3029MB total, 1226MB available
00:00:02.073190 Executable: /usr/lib/virtualbox/VirtualBox
00:00:02.073191 Process ID: 3316
00:00:02.073193 Package type: LINUX_32BITS_UBUNTU_12_10
00:00:02.074990 Installed Extension Packs:
00:00:02.075011   None installed!
00:00:02.084143 Using XKB for keycode to scan code conversion
00:00:02.085941 SUP: Loaded VMMR0.r0 (/usr/lib/virtualbox/VMMR0.r0) at 0xf997d020 - ModuleInit at 00000000f9993080 and ModuleTerm at 00000000f99933e0
00:00:02.085969 SUP: VMMR0EntryEx located at 00000000f9994690, VMMR0EntryFast at 00000000f99943e0 and VMMR0EntryInt at 00000000f99943d0
00:00:02.120261 File system of '/home/nima/VirtualBox VMs/test/Snapshots' (snapshots) is unknown
00:00:02.120287 File system of '/home/nima/.VirtualBox/winxp.vmdk' is ext4
00:00:02.162885 Shared clipboard mode: Off
00:00:02.163990 Drag'n'drop mode: Off
00:00:02.168660 ************************* CFGM dump *************************
00:00:02.168664 [/] (level 0)
00:00:02.168669   CSAMEnabled     <integer> = 0x0000000000000001 (1)
00:00:02.168677   CpuExecutionCap <integer> = 0x0000000000000064 (100)
00:00:02.168679   EnablePAE       <integer> = 0x0000000000000000 (0)
00:00:02.168681   HwVirtExtForced <integer> = 0x0000000000000000 (0)
00:00:02.168683   MemBalloonSize  <integer> = 0x0000000000000000 (0)
00:00:02.168685   Name            <string>  = "test" (cb=5)
00:00:02.168687   NumCPUs         <integer> = 0x0000000000000001 (1)
00:00:02.168689   PATMEnabled     <integer> = 0x0000000000000001 (1)
00:00:02.168691   PageFusion      <integer> = 0x0000000000000000 (0)
00:00:02.168693   RamHoleSize     <integer> = 0x0000000024000000 (603 979 776, 576 MB)
00:00:02.168696   RamSize         <integer> = 0x0000000040000000 (1 073 741 824, 1 024 MB)
00:00:02.168700   RawR0Enabled    <integer> = 0x0000000000000001 (1)
00:00:02.168702   RawR3Enabled    <integer> = 0x0000000000000001 (1)
00:00:02.168704   TimerMillies    <integer> = 0x000000000000000a (10)
00:00:02.168706   UUID            <bytes>   = "00 96 13 0d 02 b9 d3 41 ba 1e 61 b2 25 97 43 cc" (cb=16)
00:00:02.168714 
00:00:02.168715 [/CPUM/] (level 1)
00:00:02.168717   SyntheticCpu <integer> = 0x0000000000000000 (0)
00:00:02.168719 
00:00:02.168720 [/DBGF/] (level 1)
00:00:02.168722   Path <string>  = "/home/nima/VirtualBox VMs/test/debug/;/home/nima/VirtualBox VMs/test/;/home/nima/" (cb=82)
00:00:02.168724 
00:00:02.168725 [/Devices/] (level 1)
00:00:02.168727 
00:00:02.168728 [/Devices/8237A/] (level 2)
00:00:02.168730 
00:00:02.168731 [/Devices/8237A/0/] (level 3)
00:00:02.168734   Trusted <integer> = 0x0000000000000001 (1)
00:00:02.168736 
00:00:02.168737 [/Devices/AudioSniffer/] (level 2)
00:00:02.168740 
00:00:02.168741 [/Devices/AudioSniffer/0/] (level 3)
00:00:02.168743 
00:00:02.168744 [/Devices/AudioSniffer/0/Config/] (level 4)
00:00:02.168747 
00:00:02.168748 [/Devices/AudioSniffer/0/LUN#0/] (level 4)
00:00:02.168751   Driver <string>  = "MainAudioSniffer" (cb=17)
00:00:02.168753 
00:00:02.168754 [/Devices/AudioSniffer/0/LUN#0/Config/] (level 5)
00:00:02.168757   Object <integer> = 0x0000000009518640 (156 337 728)
00:00:02.168760 
00:00:02.168761 [/Devices/VMMDev/] (level 2)
00:00:02.168763 
00:00:02.168764 [/Devices/VMMDev/0/] (level 3)
00:00:02.168767   PCIBusNo      <integer> = 0x0000000000000000 (0)
00:00:02.168769   PCIDeviceNo   <integer> = 0x0000000000000004 (4)
00:00:02.168771   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:02.168773   Trusted       <integer> = 0x0000000000000001 (1)
00:00:02.168774 
00:00:02.168775 [/Devices/VMMDev/0/Config/] (level 4)
00:00:02.168778   GuestCoreDumpDir <string>  = "/home/nima/VirtualBox VMs/test/Snapshots" (cb=41)
00:00:02.168780   RamSize          <integer> = 0x0000000040000000 (1 073 741 824, 1 024 MB)
00:00:02.168784 
00:00:02.168785 [/Devices/VMMDev/0/LUN#0/] (level 4)
00:00:02.168788   Driver <string>  = "HGCM" (cb=5)
00:00:02.168789 
00:00:02.168790 [/Devices/VMMDev/0/LUN#0/Config/] (level 5)
00:00:02.168793   Object <integer> = 0x00000000b0806d68 (2 961 206 632)
00:00:02.168796 
00:00:02.168797 [/Devices/VMMDev/0/LUN#999/] (level 4)
00:00:02.168800   Driver <string>  = "MainStatus" (cb=11)
00:00:02.168802 
00:00:02.168803 [/Devices/VMMDev/0/LUN#999/Config/] (level 5)
00:00:02.168806   First   <integer> = 0x0000000000000000 (0)
00:00:02.168808   Last    <integer> = 0x0000000000000000 (0)
00:00:02.168810   papLeds <integer> = 0x000000000944c5b4 (155 502 004)
00:00:02.168813 
00:00:02.168814 [/Devices/acpi/] (level 2)
00:00:02.168816 
00:00:02.168817 [/Devices/acpi/0/] (level 3)
00:00:02.168820   PCIBusNo      <integer> = 0x0000000000000000 (0)
00:00:02.168822   PCIDeviceNo   <integer> = 0x0000000000000007 (7)
00:00:02.168824   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:02.168825   Trusted       <integer> = 0x0000000000000001 (1)
00:00:02.168827 
00:00:02.168828 [/Devices/acpi/0/Config/] (level 4)
00:00:02.168831   CpuHotPlug        <integer> = 0x0000000000000000 (0)
00:00:02.168833   FdcEnabled        <integer> = 0x0000000000000000 (0)
00:00:02.168835   HostBusPciAddress <integer> = 0x00000000001e0000 (1 966 080)
00:00:02.168838   HpetEnabled       <integer> = 0x0000000000000001 (1)
00:00:02.168840   IOAPIC            <integer> = 0x0000000000000001 (1)
00:00:02.168842   IocPciAddress     <integer> = 0x00000000001f0000 (2 031 616)
00:00:02.168844   McfgBase          <integer> = 0x00000000dc000000 (3 690 987 520)
00:00:02.168848   McfgLength        <integer> = 0x0000000004000000 (67 108 864)
00:00:02.168851   NumCPUs           <integer> = 0x0000000000000001 (1)
00:00:02.168853   RamHoleSize       <integer> = 0x0000000024000000 (603 979 776, 576 MB)
00:00:02.168857   RamSize           <integer> = 0x0000000040000000 (1 073 741 824, 1 024 MB)
00:00:02.168861   Serial0IoPortBase <integer> = 0x0000000000000000 (0)
00:00:02.168863   Serial0Irq        <integer> = 0x0000000000000000 (0)
00:00:02.168864   Serial1IoPortBase <integer> = 0x0000000000000000 (0)
00:00:02.168866   Serial1Irq        <integer> = 0x0000000000000000 (0)
00:00:02.168868   ShowCpu           <integer> = 0x0000000000000001 (1)
00:00:02.168870   ShowRtc           <integer> = 0x0000000000000001 (1)
00:00:02.168872   SmcEnabled        <integer> = 0x0000000000000000 (0)
00:00:02.168874 
00:00:02.168875 [/Devices/acpi/0/LUN#0/] (level 4)
00:00:02.168878   Driver <string>  = "ACPIHost" (cb=9)
00:00:02.168879 
00:00:02.168880 [/Devices/acpi/0/LUN#0/Config/] (level 5)
00:00:02.168884 
00:00:02.168885 [/Devices/apic/] (level 2)
00:00:02.168887 
00:00:02.168888 [/Devices/apic/0/] (level 3)
00:00:02.168890   Trusted <integer> = 0x0000000000000001 (1)
00:00:02.168897 
00:00:02.168898 [/Devices/apic/0/Config/] (level 4)
00:00:02.168901   IOAPIC  <integer> = 0x0000000000000001 (1)
00:00:02.168903   NumCPUs <integer> = 0x0000000000000001 (1)
00:00:02.168905 
00:00:02.168906 [/Devices/e1000/] (level 2)
00:00:02.168908 
00:00:02.168909 [/Devices/hpet/] (level 2)
00:00:02.168912 
00:00:02.168913 [/Devices/hpet/0/] (level 3)
00:00:02.168915   Trusted <integer> = 0x0000000000000001 (1)
00:00:02.168917 
00:00:02.168918 [/Devices/hpet/0/Config/] (level 4)
00:00:02.168921   ICH9 <integer> = 0x0000000000000001 (1)
00:00:02.168923 
00:00:02.168924 [/Devices/i8254/] (level 2)
00:00:02.168926 
00:00:02.168927 [/Devices/i8254/0/] (level 3)
00:00:02.168930 
00:00:02.168931 [/Devices/i8254/0/Config/] (level 4)
00:00:02.168934 
00:00:02.168935 [/Devices/i8259/] (level 2)
00:00:02.168937 
00:00:02.168938 [/Devices/i8259/0/] (level 3)
00:00:02.168940   Trusted <integer> = 0x0000000000000001 (1)
00:00:02.168942 
00:00:02.168943 [/Devices/i8259/0/Config/] (level 4)
00:00:02.168946 
00:00:02.168947 [/Devices/ich9pci/] (level 2)
00:00:02.168949 
00:00:02.168950 [/Devices/ich9pci/0/] (level 3)
00:00:02.168953   Trusted <integer> = 0x0000000000000001 (1)
00:00:02.168954 
00:00:02.168955 [/Devices/ich9pci/0/Config/] (level 4)
00:00:02.168958   IOAPIC     <integer> = 0x0000000000000001 (1)
00:00:02.168960   McfgBase   <integer> = 0x00000000dc000000 (3 690 987 520)
00:00:02.168963   McfgLength <integer> = 0x0000000004000000 (67 108 864)
00:00:02.168966 
00:00:02.168967 [/Devices/ich9pcibridge/] (level 2)
00:00:02.168969 
00:00:02.168970 [/Devices/ich9pcibridge/0/] (level 3)
00:00:02.168973   PCIBusNo      <integer> = 0x0000000000000000 (0)
00:00:02.168975   PCIDeviceNo   <integer> = 0x0000000000000018 (24)
00:00:02.168977   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:02.168979   Trusted       <integer> = 0x0000000000000001 (1)
00:00:02.168981 
00:00:02.168982 [/Devices/ich9pcibridge/1/] (level 3)
00:00:02.168985   PCIBusNo      <integer> = 0x0000000000000000 (0)
00:00:02.168986   PCIDeviceNo   <integer> = 0x0000000000000019 (25)
00:00:02.168988   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:02.168990   Trusted       <integer> = 0x0000000000000001 (1)
00:00:02.168992 
00:00:02.168993 [/Devices/ichac97/] (level 2)
00:00:02.168995 
00:00:02.168996 [/Devices/ichac97/0/] (level 3)
00:00:02.168999   PCIBusNo      <integer> = 0x0000000000000000 (0)
00:00:02.169001   PCIDeviceNo   <integer> = 0x0000000000000005 (5)
00:00:02.169003   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:02.169004   Trusted       <integer> = 0x0000000000000001 (1)
00:00:02.169006 
00:00:02.169007 [/Devices/ichac97/0/Config/] (level 4)
00:00:02.169010 
00:00:02.169011 [/Devices/ichac97/0/LUN#0/] (level 4)
00:00:02.169014   Driver <string>  = "AUDIO" (cb=6)
00:00:02.169015 
00:00:02.169016 [/Devices/ichac97/0/LUN#0/Config/] (level 5)
00:00:02.169020   AudioDriver <string>  = "pulse" (cb=6)
00:00:02.169021   StreamName  <string>  = "test" (cb=5)
00:00:02.169022 
00:00:02.169023 [/Devices/ioapic/] (level 2)
00:00:02.169026 
00:00:02.169027 [/Devices/ioapic/0/] (level 3)
00:00:02.169029   Trusted <integer> = 0x0000000000000001 (1)
00:00:02.169031 
00:00:02.169032 [/Devices/ioapic/0/Config/] (level 4)
00:00:02.169035   NumCPUs <integer> = 0x0000000000000001 (1)
00:00:02.169037 
00:00:02.169038 [/Devices/lpc/] (level 2)
00:00:02.169040 
00:00:02.169041 [/Devices/lpc/0/] (level 3)
00:00:02.169044   PCIBusNo      <integer> = 0x0000000000000000 (0)
00:00:02.169046   PCIDeviceNo   <integer> = 0x000000000000001f (31)
00:00:02.169048   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:02.169050   Trusted       <integer> = 0x0000000000000001 (1)
00:00:02.169051 
00:00:02.169052 [/Devices/mc146818/] (level 2)
00:00:02.169055 
00:00:02.169056 [/Devices/mc146818/0/] (level 3)
00:00:02.169058 
00:00:02.169059 [/Devices/mc146818/0/Config/] (level 4)
00:00:02.169062   UseUTC <integer> = 0x0000000000000000 (0)
00:00:02.169064 
00:00:02.169065 [/Devices/parallel/] (level 2)
00:00:02.169067 
00:00:02.169071 [/Devices/pcarch/] (level 2)
00:00:02.169074 
00:00:02.169075 [/Devices/pcarch/0/] (level 3)
00:00:02.169077   Trusted <integer> = 0x0000000000000001 (1)
00:00:02.169079 
00:00:02.169080 [/Devices/pcarch/0/Config/] (level 4)
00:00:02.169083 
00:00:02.169084 [/Devices/pcbios/] (level 2)
00:00:02.169086 
00:00:02.169087 [/Devices/pcbios/0/] (level 3)
00:00:02.169090   Trusted <integer> = 0x0000000000000001 (1)
00:00:02.169092 
00:00:02.169093 [/Devices/pcbios/0/Config/] (level 4)
00:00:02.169096   BootDevice0    <string>  = "DVD" (cb=4)
00:00:02.169098   BootDevice1    <string>  = "IDE" (cb=4)
00:00:02.169099   BootDevice2    <string>  = "NONE" (cb=5)
00:00:02.169101   BootDevice3    <string>  = "NONE" (cb=5)
00:00:02.169102   FloppyDevice   <string>  = "i82078" (cb=7)
00:00:02.169104   HardDiskDevice <string>  = "piix3ide" (cb=9)
00:00:02.169105   IOAPIC         <integer> = 0x0000000000000001 (1)
00:00:02.169107   McfgBase       <integer> = 0x00000000dc000000 (3 690 987 520)
00:00:02.169111   McfgLength     <integer> = 0x0000000004000000 (67 108 864)
00:00:02.169114   NumCPUs        <integer> = 0x0000000000000001 (1)
00:00:02.169115   PXEDebug       <integer> = 0x0000000000000000 (0)
00:00:02.169117   RamHoleSize    <integer> = 0x0000000024000000 (603 979 776, 576 MB)
00:00:02.169121   RamSize        <integer> = 0x0000000040000000 (1 073 741 824, 1 024 MB)
00:00:02.169125   UUID           <bytes>   = "00 96 13 0d 02 b9 d3 41 ba 1e 61 b2 25 97 43 cc" (cb=16)
00:00:02.169129 
00:00:02.169130 [/Devices/pcbios/0/Config/NetBoot/] (level 5)
00:00:02.169133 
00:00:02.169134 [/Devices/pckbd/] (level 2)
00:00:02.169137 
00:00:02.169138 [/Devices/pckbd/0/] (level 3)
00:00:02.169140   Trusted <integer> = 0x0000000000000001 (1)
00:00:02.169142 
00:00:02.169143 [/Devices/pckbd/0/Config/] (level 4)
00:00:02.169146 
00:00:02.169147 [/Devices/pckbd/0/LUN#0/] (level 4)
00:00:02.169150   Driver <string>  = "KeyboardQueue" (cb=14)
00:00:02.169151 
00:00:02.169152 [/Devices/pckbd/0/LUN#0/AttachedDriver/] (level 5)
00:00:02.169156   Driver <string>  = "MainKeyboard" (cb=13)
00:00:02.169157 
00:00:02.169158 [/Devices/pckbd/0/LUN#0/AttachedDriver/Config/] (level 6)
00:00:02.169161   Object <integer> = 0x000000000944cdd8 (155 504 088)
00:00:02.169164 
00:00:02.169165 [/Devices/pckbd/0/LUN#0/Config/] (level 5)
00:00:02.169168   QueueSize <integer> = 0x0000000000000040 (64)
00:00:02.169170 
00:00:02.169171 [/Devices/pckbd/0/LUN#1/] (level 4)
00:00:02.169174   Driver <string>  = "MouseQueue" (cb=11)
00:00:02.169175 
00:00:02.169176 [/Devices/pckbd/0/LUN#1/AttachedDriver/] (level 5)
00:00:02.169179   Driver <string>  = "MainMouse" (cb=10)
00:00:02.169181 
00:00:02.169182 [/Devices/pckbd/0/LUN#1/AttachedDriver/Config/] (level 6)
00:00:02.169185   Object <integer> = 0x0000000009517848 (156 334 152)
00:00:02.169188 
00:00:02.169189 [/Devices/pckbd/0/LUN#1/Config/] (level 5)
00:00:02.169192   QueueSize <integer> = 0x0000000000000080 (128)
00:00:02.169194 
00:00:02.169195 [/Devices/pcnet/] (level 2)
00:00:02.169198 
00:00:02.169199 [/Devices/piix3ide/] (level 2)
00:00:02.169201 
00:00:02.169202 [/Devices/piix3ide/0/] (level 3)
00:00:02.169205   PCIBusNo      <integer> = 0x0000000000000000 (0)
00:00:02.169207   PCIDeviceNo   <integer> = 0x000000000000001f (31)
00:00:02.169209   PCIFunctionNo <integer> = 0x0000000000000001 (1)
00:00:02.169211   Trusted       <integer> = 0x0000000000000001 (1)
00:00:02.169212 
00:00:02.169213 [/Devices/piix3ide/0/Config/] (level 4)
00:00:02.169216   Type <string>  = "PIIX4" (cb=6)
00:00:02.169218 
00:00:02.169219 [/Devices/piix3ide/0/Config/PrimaryMaster/] (level 5)
00:00:02.169222   NonRotationalMedium <integer> = 0x0000000000000000 (0)
00:00:02.169224 
00:00:02.169225 [/Devices/piix3ide/0/Config/SecondaryMaster/] (level 5)
00:00:02.169228   NonRotationalMedium <integer> = 0x0000000000000000 (0)
00:00:02.169230 
00:00:02.169231 [/Devices/piix3ide/0/LUN#0/] (level 4)
00:00:02.169234   Driver <string>  = "Block" (cb=6)
00:00:02.169235 
00:00:02.169236 [/Devices/piix3ide/0/LUN#0/AttachedDriver/] (level 5)
00:00:02.169243   Driver <string>  = "VD" (cb=3)
00:00:02.169244 
00:00:02.169245 [/Devices/piix3ide/0/LUN#0/AttachedDriver/Config/] (level 6)
00:00:02.169249   Format <string>  = "VMDK" (cb=5)
00:00:02.169250   Path   <string>  = "/home/nima/.VirtualBox/winxp.vmdk" (cb=34)
00:00:02.169252   Type   <string>  = "HardDisk" (cb=9)
00:00:02.169253 
00:00:02.169254 [/Devices/piix3ide/0/LUN#0/Config/] (level 5)
00:00:02.169257   Mountable <integer> = 0x0000000000000000 (0)
00:00:02.169259   Type      <string>  = "HardDisk" (cb=9)
00:00:02.169261 
00:00:02.169262 [/Devices/piix3ide/0/LUN#2/] (level 4)
00:00:02.169265   Driver <string>  = "Block" (cb=6)
00:00:02.169266 
00:00:02.169267 [/Devices/piix3ide/0/LUN#2/Config/] (level 5)
00:00:02.169270   Mountable <integer> = 0x0000000000000001 (1)
00:00:02.169272   Type      <string>  = "DVD" (cb=4)
00:00:02.169274 
00:00:02.169275 [/Devices/piix3ide/0/LUN#999/] (level 4)
00:00:02.169277   Driver <string>  = "MainStatus" (cb=11)
00:00:02.169279 
00:00:02.169280 [/Devices/piix3ide/0/LUN#999/Config/] (level 5)
00:00:02.169283   DeviceInstance        <string>  = "piix3ide/0" (cb=11)
00:00:02.169285   First                 <integer> = 0x0000000000000000 (0)
00:00:02.169287   Last                  <integer> = 0x0000000000000003 (3)
00:00:02.169289   pConsole              <integer> = 0x000000000944c248 (155 501 128)
00:00:02.169293   papLeds               <integer> = 0x000000000944c43c (155 501 628)
00:00:02.169296   pmapMediumAttachments <integer> = 0x000000000944c5c0 (155 502 016)
00:00:02.169299 
00:00:02.169300 [/Devices/serial/] (level 2)
00:00:02.169302 
00:00:02.169303 [/Devices/usb-ohci/] (level 2)
00:00:02.169305 
00:00:02.169306 [/Devices/usb-ohci/0/] (level 3)
00:00:02.169309   PCIBusNo      <integer> = 0x0000000000000000 (0)
00:00:02.169311   PCIDeviceNo   <integer> = 0x000000000000001f (31)
00:00:02.169313   PCIFunctionNo <integer> = 0x0000000000000004 (4)
00:00:02.169315   Trusted       <integer> = 0x0000000000000001 (1)
00:00:02.169317 
00:00:02.169318 [/Devices/usb-ohci/0/Config/] (level 4)
00:00:02.169321 
00:00:02.169322 [/Devices/usb-ohci/0/LUN#0/] (level 4)
00:00:02.169325   Driver <string>  = "VUSBRootHub" (cb=12)
00:00:02.169326 
00:00:02.169327 [/Devices/usb-ohci/0/LUN#0/Config/] (level 5)
00:00:02.169330 
00:00:02.169331 [/Devices/usb-ohci/0/LUN#999/] (level 4)
00:00:02.169334   Driver <string>  = "MainStatus" (cb=11)
00:00:02.169335 
00:00:02.169336 [/Devices/usb-ohci/0/LUN#999/Config/] (level 5)
00:00:02.169340   First   <integer> = 0x0000000000000000 (0)
00:00:02.169341   Last    <integer> = 0x0000000000000000 (0)
00:00:02.169343   papLeds <integer> = 0x000000000944c5b8 (155 502 008)
00:00:02.169346 
00:00:02.169347 [/Devices/vga/] (level 2)
00:00:02.169350 
00:00:02.169350 [/Devices/vga/0/] (level 3)
00:00:02.169353   PCIBusNo      <integer> = 0x0000000000000000 (0)
00:00:02.169355   PCIDeviceNo   <integer> = 0x0000000000000002 (2)
00:00:02.169357   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:02.169359   Trusted       <integer> = 0x0000000000000001 (1)
00:00:02.169361 
00:00:02.169362 [/Devices/vga/0/Config/] (level 4)
00:00:02.169365   CustomVideoModes <integer> = 0x0000000000000000 (0)
00:00:02.169367   FadeIn           <integer> = 0x0000000000000001 (1)
00:00:02.169368   FadeOut          <integer> = 0x0000000000000001 (1)
00:00:02.169370   HeightReduction  <integer> = 0x0000000000000000 (0)
00:00:02.169372   LogoFile         <string>  = "" (cb=1)
00:00:02.169374   LogoTime         <integer> = 0x0000000000000000 (0)
00:00:02.169376   MonitorCount     <integer> = 0x0000000000000001 (1)
00:00:02.169378   ShowBootMenu     <integer> = 0x0000000000000002 (2)
00:00:02.169379   VRamSize         <integer> = 0x0000000002000000 (33 554 432, 32 MB)
00:00:02.169383 
00:00:02.169384 [/Devices/vga/0/LUN#0/] (level 4)
00:00:02.169387   Driver <string>  = "MainDisplay" (cb=12)
00:00:02.169388 
00:00:02.169389 [/Devices/vga/0/LUN#0/Config/] (level 5)
00:00:02.169392   Object <integer> = 0x0000000009517cf8 (156 335 352)
00:00:02.169395 
00:00:02.169396 [/Devices/virtio-net/] (level 2)
00:00:02.169402 
00:00:02.169403 [/HWVirtExt/] (level 1)
00:00:02.169405   EnableLargePages   <integer> = 0x0000000000000000 (0)
00:00:02.169407   EnableNestedPaging <integer> = 0x0000000000000001 (1)
00:00:02.169409   EnableVPID         <integer> = 0x0000000000000001 (1)
00:00:02.169411   Exclusive          <integer> = 0x0000000000000001 (1)
00:00:02.169412 
00:00:02.169414 [/MM/] (level 1)
00:00:02.169416   CanUseLargerHeap <integer> = 0x0000000000000001 (1)
00:00:02.169417 
00:00:02.169418 [/PDM/] (level 1)
00:00:02.169420 
00:00:02.169421 [/PDM/AsyncCompletion/] (level 2)
00:00:02.169424 
00:00:02.169425 [/PDM/AsyncCompletion/File/] (level 3)
00:00:02.169427 
00:00:02.169428 [/PDM/AsyncCompletion/File/BwGroups/] (level 4)
00:00:02.169431 
00:00:02.169432 [/PDM/BlkCache/] (level 2)
00:00:02.169434   CacheSize <integer> = 0x0000000000500000 (5 242 880, 5 MB)
00:00:02.169438 
00:00:02.169439 [/PDM/Devices/] (level 2)
00:00:02.169441 
00:00:02.169442 [/PDM/Drivers/] (level 2)
00:00:02.169444 
00:00:02.169445 [/PDM/Drivers/VBoxC/] (level 3)
00:00:02.169448   Path <string>  = "/usr/lib/virtualbox/components/VBoxC" (cb=37)
00:00:02.169449 
00:00:02.169450 [/PDM/NetworkShaper/] (level 2)
00:00:02.169452 
00:00:02.169453 [/PDM/NetworkShaper/BwGroups/] (level 3)
00:00:02.169456 
00:00:02.169457 [/TM/] (level 1)
00:00:02.169459   UTCOffset <integer> = 0x0000000000000000 (0)
00:00:02.169461 
00:00:02.169462 [/USB/] (level 1)
00:00:02.169464 
00:00:02.169465 [/USB/HidMouse/] (level 2)
00:00:02.169467 
00:00:02.169468 [/USB/HidMouse/0/] (level 3)
00:00:02.169470 
00:00:02.169471 [/USB/HidMouse/0/Config/] (level 4)
00:00:02.169474   Absolute <integer> = 0x0000000000000001 (1)
00:00:02.169476 
00:00:02.169477 [/USB/HidMouse/0/LUN#0/] (level 4)
00:00:02.169480   Driver <string>  = "MouseQueue" (cb=11)
00:00:02.169482 
00:00:02.169483 [/USB/HidMouse/0/LUN#0/AttachedDriver/] (level 5)
00:00:02.169486   Driver <string>  = "MainMouse" (cb=10)
00:00:02.169487 
00:00:02.169488 [/USB/HidMouse/0/LUN#0/AttachedDriver/Config/] (level 6)
00:00:02.169492   Object <integer> = 0x0000000009517848 (156 334 152)
00:00:02.169494 
00:00:02.169495 [/USB/HidMouse/0/LUN#0/Config/] (level 5)
00:00:02.169499   QueueSize <integer> = 0x0000000000000080 (128)
00:00:02.169501 
00:00:02.169502 [/USB/USBProxy/] (level 2)
00:00:02.169504 
00:00:02.169505 [/USB/USBProxy/GlobalConfig/] (level 3)
00:00:02.169508 
00:00:02.169509 ********************* End of CFGM dump **********************
00:00:02.169550 MM: cbHyperHeap=0x200000 (2097152)
00:00:02.180852 Logical host processors: 2 present, 2 max, 2 online, online mask: 0000000000000003
00:00:02.180859 ************************* CPUID dump ************************
00:00:02.180868          RAW Standard CPUIDs
00:00:02.180869      Function  eax      ebx      ecx      edx
00:00:02.180870 Gst: 00000000  00000005 756e6547 6c65746e 49656e69
00:00:02.180873 Hst:           0000000a 756e6547 6c65746e 49656e69
00:00:02.180875 Gst: 00000001  000006f6 00000800 00000209 078bf1bf
00:00:02.180878 Hst:           000006f6 01020800 0000e3bd bfebfbff
00:00:02.180880 Gst: 00000002  05b0b101 005657f0 00000000 2cb43049
00:00:02.180882 Hst:           05b0b101 005657f0 00000000 2cb43049
00:00:02.180885 Gst: 00000003  00000000 00000000 00000000 00000000
00:00:02.180886 Hst:           00000000 00000000 00000000 00000000
00:00:02.180888 Gst: 00000004  00000000 00000000 00000000 00000000
00:00:02.180890 Hst:           04000121 01c0003f 0000003f 00000001
00:00:02.180892 Gst: 00000005  00000040 00000040 00000000 00000000
00:00:02.180894 Hst:           00000040 00000040 00000003 00022220
00:00:02.180896 Name:                            GenuineIntel
00:00:02.180897 Supports:                        0-5
00:00:02.180899 Family:                          6      Extended: 0     Effective: 6
00:00:02.180900 Model:                           15      Extended: 0     Effective: 15
00:00:02.180902 Stepping:                        6
00:00:02.180903 Type:                            0 (primary)
00:00:02.180904 APIC ID:                         0x00
00:00:02.180905 Logical CPUs:                    0
00:00:02.180906 CLFLUSH Size:                    8
00:00:02.180907 Brand ID:                        0x00
00:00:02.180909 Mnemonic - Description                 = guest (host)
00:00:02.180911 FPU - x87 FPU on Chip                  = 1 (1)
00:00:02.180912 VME - Virtual 8086 Mode Enhancements   = 1 (1)
00:00:02.180914 DE - Debugging extensions              = 1 (1)
00:00:02.180915 PSE - Page Size Extension              = 1 (1)
00:00:02.180916 TSC - Time Stamp Counter               = 1 (1)
00:00:02.180918 MSR - Model Specific Registers         = 1 (1)
00:00:02.180919 PAE - Physical Address Extension       = 0 (1)
00:00:02.180921 MCE - Machine Check Exception          = 1 (1)
00:00:02.180922 CX8 - CMPXCHG8B instruction            = 1 (1)
00:00:02.180923 APIC - APIC On-Chip                    = 0 (1)
00:00:02.180925 10 - Reserved                          = 0 (0)
00:00:02.180926 SEP - SYSENTER and SYSEXIT             = 0 (1)
00:00:02.180928 MTRR - Memory Type Range Registers     = 1 (1)
00:00:02.180929 PGE - PTE Global Bit                   = 1 (1)
00:00:02.180930 MCA - Machine Check Architecture       = 1 (1)
00:00:02.180932 CMOV - Conditional Move Instructions   = 1 (1)
00:00:02.180933 PAT - Page Attribute Table             = 1 (1)
00:00:02.180934 PSE-36 - 36-bit Page Size Extention    = 1 (1)
00:00:02.180936 PSN - Processor Serial Number          = 0 (0)
00:00:02.180937 CLFSH - CLFLUSH Instruction.           = 1 (1)
00:00:02.180938 20 - Reserved                          = 0 (0)
00:00:02.180940 DS - Debug Store                       = 0 (1)
00:00:02.180941 ACPI - Thermal Mon. & Soft. Clock Ctrl.= 0 (1)
00:00:02.180942 MMX - Intel MMX Technology             = 1 (1)
00:00:02.180944 FXSR - FXSAVE and FXRSTOR Instructions = 1 (1)
00:00:02.180945 SSE - SSE Support                      = 1 (1)
00:00:02.180946 SSE2 - SSE2 Support                    = 1 (1)
00:00:02.180948 SS - Self Snoop                        = 0 (1)
00:00:02.180949 HTT - Hyper-Threading Technology       = 0 (1)
00:00:02.180950 TM - Thermal Monitor                   = 0 (1)
00:00:02.180952 30 - Reserved                          = 0 (0)
00:00:02.180953 PBE - Pending Break Enable             = 0 (1)
00:00:02.180955 Supports SSE3                          = 1 (1)
00:00:02.180956 PCLMULQDQ                              = 0 (0)
00:00:02.180957 DS Area 64-bit layout                  = 0 (1)
00:00:02.180958 Supports MONITOR/MWAIT                 = 1 (1)
00:00:02.180960 CPL-DS - CPL Qualified Debug Store     = 0 (1)
00:00:02.180961 VMX - Virtual Machine Technology       = 0 (1)
00:00:02.180963 SMX - Safer Mode Extensions            = 0 (0)
00:00:02.180964 Enhanced SpeedStep Technology          = 0 (1)
00:00:02.180965 Terminal Monitor 2                     = 0 (1)
00:00:02.180967 Supplemental SSE3 instructions         = 1 (1)
00:00:02.180968 L1 Context ID                          = 0 (0)
00:00:02.180969 11 - Reserved                          = 0 (0)
00:00:02.180971 FMA extensions using YMM state         = 0 (0)
00:00:02.180972 CMPXCHG16B instruction                 = 0 (1)
00:00:02.180973 xTPR Update Control                    = 0 (1)
00:00:02.180975 Perf/Debug Capability MSR              = 0 (1)
00:00:02.180976 16 - Reserved                          = 0 (0)
00:00:02.180977 PCID - Process-context identifiers     = 0 (0)
00:00:02.180979 DCA - Direct Cache Access              = 0 (0)
00:00:02.180980 SSE4.1 instruction extensions          = 0 (0)
00:00:02.180982 SSE4.2 instruction extensions          = 0 (0)
00:00:02.180985 Supports the x2APIC extensions         = 0 (0)
00:00:02.180986 MOVBE instruction                      = 0 (0)
00:00:02.180988 POPCNT instruction                     = 0 (0)
00:00:02.180989 TSC-Deadline LAPIC timer mode          = 0 (0)
00:00:02.180990 AESNI instruction extensions           = 0 (0)
00:00:02.180992 XSAVE/XRSTOR extended state feature    = 0 (0)
00:00:02.180993 Supports OSXSAVE                       = 0 (0)
00:00:02.180994 AVX instruction extensions             = 0 (0)
00:00:02.180996 29/30 - Reserved                       = 0x0 (0x0)
00:00:02.180997 Hypervisor Present (we're a guest)     = 0 (0)
00:00:02.180999 
00:00:02.181000          RAW Extended CPUIDs
00:00:02.181000      Function  eax      ebx      ecx      edx
00:00:02.181001 Gst: 80000000  80000008 00000000 00000000 00000000
00:00:02.181004 Hst:           80000008 00000000 00000000 00000000
00:00:02.181006 Gst: 80000001  00000000 00000000 00000000 00000000
00:00:02.181008 Hst:           00000000 00000000 00000001 20100000
00:00:02.181010 Gst: 80000002  65746e49 2952286c 726f4320 4d542865
00:00:02.181012 Hst:           65746e49 2952286c 726f4320 4d542865
00:00:02.181015 Gst: 80000003  43203229 20205550 20202020 54202020
00:00:02.181017 Hst:           43203229 20205550 20202020 54202020
00:00:02.181020 Gst: 80000004  30303237 20402020 30302e32 007a4847
00:00:02.181022 Hst:           30303237 20402020 30302e32 007a4847
00:00:02.181025 Gst: 80000005  00000000 00000000 00000000 00000000
00:00:02.181026 Hst:           00000000 00000000 00000000 00000000
00:00:02.181028 Gst: 80000006  00000000 00000000 10008040 00000000
00:00:02.181030 Hst:           00000000 00000000 10008040 00000000
00:00:02.181032 Gst: 80000007  00000000 00000000 00000000 00000000
00:00:02.181034 Hst:           00000000 00000000 00000000 00000000
00:00:02.181036 Gst: 80000008  00003024 00000000 00000000 00000000
00:00:02.181037 Hst:           00003024 00000000 00000000 00000000
00:00:02.181039 Gst: 80000009  07280202 00000000 00000000 00000000*
00:00:02.181042 Hst:           07280202 00000000 00000000 00000000
00:00:02.181044 Ext Name:                        
00:00:02.181045 Ext Supports:                    0x80000000-0x80000008
00:00:02.181047 Family:                          0      Extended: 0     Effective: 0
00:00:02.181048 Model:                           0      Extended: 0     Effective: 0
00:00:02.181050 Stepping:                        0
00:00:02.181051 Brand ID:                        0x000
00:00:02.181052 Mnemonic - Description                 = guest (host)
00:00:02.181053 FPU - x87 FPU on Chip                  = 0 (0)
00:00:02.181054 VME - Virtual 8086 Mode Enhancements   = 0 (0)
00:00:02.181056 DE - Debugging extensions              = 0 (0)
00:00:02.181057 PSE - Page Size Extension              = 0 (0)
00:00:02.181058 TSC - Time Stamp Counter               = 0 (0)
00:00:02.181060 MSR - K86 Model Specific Registers     = 0 (0)
00:00:02.181061 PAE - Physical Address Extension       = 0 (0)
00:00:02.181062 MCE - Machine Check Exception          = 0 (0)
00:00:02.181064 CX8 - CMPXCHG8B instruction            = 0 (0)
00:00:02.181065 APIC - APIC On-Chip                    = 0 (0)
00:00:02.181066 10 - Reserved                          = 0 (0)
00:00:02.181068 SEP - SYSCALL and SYSRET               = 0 (0)
00:00:02.181069 MTRR - Memory Type Range Registers     = 0 (0)
00:00:02.181070 PGE - PTE Global Bit                   = 0 (0)
00:00:02.181072 MCA - Machine Check Architecture       = 0 (0)
00:00:02.181073 CMOV - Conditional Move Instructions   = 0 (0)
00:00:02.181074 PAT - Page Attribute Table             = 0 (0)
00:00:02.181076 PSE-36 - 36-bit Page Size Extention    = 0 (0)
00:00:02.181077 18 - Reserved                          = 0 (0)
00:00:02.181078 19 - Reserved                          = 0 (0)
00:00:02.181080 NX - No-Execute Page Protection        = 0 (1)
00:00:02.181081 DS - Debug Store                       = 0 (0)
00:00:02.181083 AXMMX - AMD Extensions to MMX Instr.   = 0 (0)
00:00:02.181084 MMX - Intel MMX Technology             = 0 (0)
00:00:02.181085 FXSR - FXSAVE and FXRSTOR Instructions = 0 (0)
00:00:02.181087 25 - AMD fast FXSAVE and FXRSTOR Instr.= 0 (0)
00:00:02.181088 26 - 1 GB large page support           = 0 (0)
00:00:02.181090 27 - RDTSCP instruction                = 0 (0)
00:00:02.181091 28 - Reserved                          = 0 (0)
00:00:02.181092 29 - AMD Long Mode                     = 0 (1)
00:00:02.181094 30 - AMD Extensions to 3DNow!          = 0 (0)
00:00:02.181095 31 - AMD 3DNow!                        = 0 (0)
00:00:02.181096 LahfSahf - LAHF/SAHF in 64-bit mode    = 0 (1)
00:00:02.181098 CmpLegacy - Core MP legacy mode (depr) = 0 (0)
00:00:02.181099 SVM - AMD VM Extensions                = 0 (0)
00:00:02.181100 APIC registers starting at 0x400       = 0 (0)
00:00:02.181102 AltMovCR8 - LOCK MOV CR0 means MOV CR8 = 0 (0)
00:00:02.181103 5  - Advanced bit manipulation         = 0 (0)
00:00:02.181104 6  - SSE4A instruction support         = 0 (0)
00:00:02.181106 7  - Misaligned SSE mode               = 0 (0)
00:00:02.181107 8  - PREFETCH and PREFETCHW instruction= 0 (0)
00:00:02.181109 9  - OS visible workaround             = 0 (0)
00:00:02.181110 10 - Instruction based sampling        = 0 (0)
00:00:02.181111 11 - SSE5 support                      = 0 (0)
00:00:02.181113 12 - SKINIT, STGI, and DEV support     = 0 (0)
00:00:02.181114 13 - Watchdog timer support.           = 0 (0)
00:00:02.181115 31:14 - Reserved                       = 0x0 (0x0)
00:00:02.181117 Full Name:                       Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz
00:00:02.181118 TLB 2/4M Instr/Uni:              res0     0 entries
00:00:02.181120 TLB 2/4M Data:                   res0     0 entries
00:00:02.181121 TLB 4K Instr/Uni:                res0     0 entries
00:00:02.181123 TLB 4K Data:                     res0     0 entries
00:00:02.181124 L1 Instr Cache Line Size:        0 bytes
00:00:02.181125 L1 Instr Cache Lines Per Tag:    0
00:00:02.181126 L1 Instr Cache Associativity:    res0  
00:00:02.181127 L1 Instr Cache Size:             0 KB
00:00:02.181128 L1 Data Cache Line Size:         0 bytes
00:00:02.181129 L1 Data Cache Lines Per Tag:     0
00:00:02.181130 L1 Data Cache Associativity:     res0  
00:00:02.181131 L1 Data Cache Size:              0 KB
00:00:02.181132 L2 TLB 2/4M Instr/Uni:           off       0 entries
00:00:02.181134 L2 TLB 2/4M Data:                off       0 entries
00:00:02.181135 L2 TLB 4K Instr/Uni:             off       0 entries
00:00:02.181136 L2 TLB 4K Data:                  off       0 entries
00:00:02.181138 L2 Cache Line Size:              0 bytes
00:00:02.181139 L2 Cache Lines Per Tag:          0
00:00:02.181140 L2 Cache Associativity:          off   
00:00:02.181141 L2 Cache Size:                   0 KB
00:00:02.181142 APM Features:                   
00:00:02.181143 Physical Address Width:          36 bits
00:00:02.181144 Virtual Address Width:           48 bits
00:00:02.181145 Guest Physical Address Width:    0 bits
00:00:02.181147 Physical Core Count:             0
00:00:02.181148 
00:00:02.181149          RAW Centaur CPUIDs
00:00:02.181149      Function  eax      ebx      ecx      edx
00:00:02.181151 Gst: c0000000  07280202 00000000 00000000 00000000
00:00:02.181153 Hst:           07280202 00000000 00000000 00000000
00:00:02.181155 Gst: c0000001  07280202 00000000 00000000 00000000
00:00:02.181157 Hst:           07280202 00000000 00000000 00000000
00:00:02.181159 Gst: c0000002  07280202 00000000 00000000 00000000
00:00:02.181161 Hst:           07280202 00000000 00000000 00000000
00:00:02.181163 Gst: c0000003  07280202 00000000 00000000 00000000
00:00:02.181165 Hst:           07280202 00000000 00000000 00000000
00:00:02.181167 Centaur Supports:                0xc0000000-0x07280202
00:00:02.181169 Mnemonic - Description                 = guest (host)
00:00:02.181170 AIS - Alternate Instruction Set        = 0 (0)
00:00:02.181171 AIS-E - AIS enabled                    = 0 (0)
00:00:02.181172 RNG - Random Number Generator          = 0 (0)
00:00:02.181174 RNG-E - RNG enabled                    = 0 (0)
00:00:02.181175 LH - LongHaul MSR 0000_110Ah           = 0 (0)
00:00:02.181177 FEMMS - FEMMS                          = 0 (0)
00:00:02.181178 ACE - Advanced Cryptography Engine     = 0 (0)
00:00:02.181179 ACE-E - ACE enabled                    = 0 (0)
00:00:02.181181 ACE2 - Advanced Cryptography Engine 2  = 0 (0)
00:00:02.181184 ACE2-E - ACE enabled                   = 0 (0)
00:00:02.181185 PHE - Padlock Hash Engine              = 0 (0)
00:00:02.181187 PHE-E - PHE enabled                    = 0 (0)
00:00:02.181188 PMM - Montgomery Multiplier            = 0 (0)
00:00:02.181189 PMM-E - PMM enabled                    = 0 (0)
00:00:02.181191 14 - Reserved                          = 0 (0)
00:00:02.181192 15 - Reserved                          = 0 (0)
00:00:02.181193 Parallax                               = 0 (0)
00:00:02.181195 Parallax enabled                       = 0 (0)
00:00:02.181196 Overstress                             = 0 (0)
00:00:02.181197 Overstress enabled                     = 0 (0)
00:00:02.181199 TM3 - Temperature Monitoring 3         = 0 (0)
00:00:02.181200 TM3-E - TM3 enabled                    = 0 (0)
00:00:02.181201 RNG2 - Random Number Generator 2       = 0 (0)
00:00:02.181203 RNG2-E - RNG2 enabled                  = 0 (0)
00:00:02.181204 24 - Reserved                          = 0 (0)
00:00:02.181205 PHE2 - Padlock Hash Engine 2           = 0 (0)
00:00:02.181206 PHE2-E - PHE2 enabled                  = 0 (0)
00:00:02.181208 
00:00:02.181209 
00:00:02.181210 ******************** End of CPUID dump **********************
00:00:02.181560 Host paging mode: PAE+PGE
00:00:02.181570 PGMPool: cMaxPages=560 (u64MaxPages=545)
00:00:02.181576 pgmR3PoolInit: cMaxPages=0x230 cMaxUsers=0x460 cMaxPhysExts=0x460 fCacheEnable=true 
00:00:02.182565 REM: VBoxREM32
00:00:02.203615 TM: GIP - u32Mode=2 (AsyncTSC) u32UpdateHz=83
00:00:02.235816 TM: cTSCTicksPerSecond=0x7675bc24 (1 987 427 364) fTSCVirtualized=true  fTSCUseRealTSC=false
00:00:02.235826 TM: fMaybeUseOffsettedHostTSC=true  TSCTiedToExecution=false TSCNotTiedToHalt=false
00:00:02.236163 CoreCode: R3=a7a7c000 R0=f9b44000 RC=a0653000 Phys=0000000023880000 cb=0x3000
00:00:02.239821 AIOMgr: Default manager type is "Async"
00:00:02.239871 AIOMgr: Default file backend is "NonBuffered"
00:00:02.240046 BlkCache: Cache successfully initialised. Cache size is 5242880 bytes
00:00:02.240055 BlkCache: Cache commit interval is 10000 ms
00:00:02.240061 BlkCache: Cache commit threshold is 2621440 bytes
00:00:02.244235 [SMP] BIOS with 1 CPUs
00:00:02.254998 SUP: Loaded VBoxDDR0.r0 (/usr/lib/virtualbox/VBoxDDR0.r0) at 0xf9b8b020 - ModuleInit at 0000000000000000 and ModuleTerm at 0000000000000000
00:00:02.261485 SUP: Loaded VBoxDD2R0.r0 (/usr/lib/virtualbox/VBoxDD2R0.r0) at 0xf9bc8020 - ModuleInit at 0000000000000000 and ModuleTerm at 0000000000000000
00:00:02.261518 Activating Local APIC
00:00:02.261524 CPUMSetGuestCpuIdFeature: Enabled APIC
00:00:02.261529 CPUMClearGuestCpuIdFeature: Disabled x2APIC
00:00:02.261800 PIT: mode=3 count=0x10000 (65536) - 18.20 Hz (ch=0)
00:00:02.266094 Shared Folders service loaded.
00:00:02.287378 DrvBlock: Flushes will be ignored
00:00:02.287416 DrvBlock: Async flushes will be passed to the disk
00:00:02.287647 VDInit finished
00:00:02.289750 PIIX3 ATA: LUN#0: disk, PCHS=16383/16/63, total number of sectors 234441648
00:00:02.289766 PIIX3 ATA: LUN#1: no unit
00:00:02.289811 DrvBlock: Flushes will be ignored
00:00:02.289817 DrvBlock: Async flushes will be passed to the disk
00:00:02.289911 PIIX3 ATA: LUN#2: CD/DVD, total number of sectors 0, passthrough disabled
00:00:02.289922 PIIX3 ATA: LUN#3: no unit
00:00:02.289922 PIIX3 ATA: Ctl#0: finished processing RESET
00:00:02.289933 PIIX3 ATA: Ctl#1: finished processing RESET
00:00:02.290048 Audio: Trying driver 'pulse'.
00:00:02.292818 Audio: set_record_source ars=0 als=0 (not implemented)
00:00:02.292847 Pulse: open PCM_IN rate=44100Hz channels=2 format=s16le
00:00:02.292867 Pulse: Requested record buffer attributes: maxlength=26460 fragsize=17640
00:00:02.300770 Pulse:  Obtained record buffer attributes: maxlength=26460 fragsize=8820
00:00:02.300872 Pulse: open PCM_OUT rate=44100Hz channels=2 format=s16le
00:00:02.300888 Pulse: Requested playback buffer attributes: maxlength=26460 tlength=17640 prebuf=-1 minreq=-1
00:00:02.317844 Pulse:  Obtained playback buffer attributes: maxlength=26460 tlength=12348 prebuf=8824 minreq=3528
00:00:02.318724 VUSB: attached 'HidMouse' to port 1
00:00:02.322647 DevPcBios: ATA LUN#0 LCHS=1024/255/63
00:00:02.322963 PGM: The CPU physical address width is 36 bits
00:00:02.322978 PGMR3InitFinalize: 4 MB PSE mask 0000000fffffffff
00:00:02.338372 VMM: fUsePeriodicPreemptionTimers=true 
00:00:02.338395 HWACCM: No VT-x or AMD-V CPU extension found. Reason VERR_VMX_MSR_LOCKED_OR_DISABLED
00:00:02.338414 HWACCM: VMX MSR_IA32_FEATURE_CONTROL=1
00:00:02.350680 VM: Halt method global1 (5)
00:00:02.350695 HaltedGlobal1 config: cNsSpinBlockThresholdCfg=2000
00:00:02.350701 Changing the VM state from 'CREATING' to 'CREATED'.
00:00:02.351145 Changing the VM state from 'CREATED' to 'POWERING_ON'.
00:00:02.351234 Changing the VM state from 'POWERING_ON' to 'RUNNING'.
00:00:02.359346 Guest Log: BIOS: VirtualBox 4.2.2
00:00:02.359823 PIT: mode=2 count=0x10000 (65536) - 18.20 Hz (ch=0)
00:00:02.376108 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=00000000 w=720 h=400 bpp=0 cbLine=0x0, flags=0x1
00:00:02.437090 2D video acceleration is disabled.
00:00:02.509006 PIIX3 ATA: Ctl#0: RESET, DevSel=0 AIOIf=0 CmdIf0=0x00 (-1 usec ago) CmdIf1=0x00 (-1 usec ago)
00:00:02.509105 PIIX3 ATA: Ctl#0: finished processing RESET
00:00:02.510487 Guest Log: BIOS: ata0-0: PCHS=16383/16/63 LCHS=1024/255/63
00:00:02.511819 PIIX3 ATA: Ctl#0: RESET, DevSel=1 AIOIf=0 CmdIf0=0xec (-1 usec ago) CmdIf1=0x00 (-1 usec ago)
00:00:02.511999 PIIX3 ATA: Ctl#0: finished processing RESET
00:00:02.512184 PIIX3 ATA: Ctl#1: RESET, DevSel=0 AIOIf=0 CmdIf0=0x00 (-1 usec ago) CmdIf1=0x00 (-1 usec ago)
00:00:02.512218 PIIX3 ATA: Ctl#1: finished processing RESET
00:00:02.515387 PIT: mode=2 count=0x48d3 (18643) - 64.00 Hz (ch=0)
00:00:02.526037 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=a4a00000 w=640 h=480 bpp=32 cbLine=0xA00, flags=0x1
00:00:05.004255 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=00000000 w=720 h=400 bpp=0 cbLine=0x0, flags=0x1
00:00:05.006877 PIT: mode=2 count=0x10000 (65536) - 18.20 Hz (ch=0)
00:00:05.007336 Guest Log: BIOS: Boot : bseqnr=1, bootseq=0023
00:00:05.008409 Guest Log: BIOS: CDROM boot failure code : 0003
00:00:05.008519 Guest Log: BIOS: Boot from CD-ROM failed
00:00:05.008652 Guest Log: BIOS: Boot : bseqnr=2, bootseq=0002
00:00:05.011731 Guest Log: BIOS: Booting from Hard Disk...
00:00:06.056097 
00:00:06.056099 Trying to execute code with memory type addr_code=00000000000a4020 addend=00000000a7085000 at 00000000000a4817! (iHandlerMemType=0x38 iMMIOMemType=0x30 IOTLB=0000000000000030)
00:00:06.056107 *** handlers
00:00:06.056136 Physical handlers: (PhysHandlers=54032 (0xd310))
00:00:06.056138 From             - To (incl)         HandlerHC UserHC    HandlerGC UserGC    Type     Description
00:00:06.056146 00000000000a0000 - 00000000000bffff  b5d0af50  a8f23690  ff88f870  ff07b690  MMIO     VGA - VGA Video Buffer
00:00:06.056154 00000000000c0000 - 00000000000c8fff  b5cadb20  a8f23800  ff8ace50  ff07b800  Write    VGA BIOS
00:00:06.056161 00000000000e0000 - 00000000000e0fff  b5cadb20  a8f272c0  ff8ace50  ff07f2c0  Write    ACPI RSDP
00:00:06.056169 00000000000e1000 - 00000000000e1fff  b5cadb20  a8ed7150  ff8ace50  ff02f150  Write    DMI tables
00:00:06.056176 00000000000e2000 - 00000000000effff  b5cadb20  a8ed7a30  ff8ace50  ff02fa30  Write    Net Boot ROM
00:00:06.056183 00000000000f0000 - 00000000000fffff  b5cadb20  a8ed7240  ff8ace50  ff02f240  Write    PC BIOS - 0xfffff
00:00:06.056190 00000000dc000000 - 00000000dfffffff  b5d0af50  a8ed8750  ff88f870  ff030750  MMIO     MCFG ranges
00:00:06.056198 00000000e0000000 - 00000000e1ffffff  a73a6f40  a6bd10c0  ff8f2510  ff9110c0  Write    VGA LFB
00:00:06.056206 00000000f0500000 - 00000000f0500fff  b5d0af50  a8f27c30  ff88f870  ff07fc30  MMIO     USB OHCI
00:00:06.056214 00000000fec00000 - 00000000fec00fff  b5d0af50  a8f1b360  ff88f870  ff073360  MMIO     I/O APIC Memory
00:00:06.056221 00000000fed00000 - 00000000fed00fff  b5d0af50  a8f1b8f0  ff88f870  ff0738f0  MMIO     HPET Memory
00:00:06.056229 00000000fed1c000 - 00000000fed1ffff  b5d0af50  a8f27790  ff88f870  ff07f790  MMIO     LPC Memory
00:00:06.056236 00000000fee00000 - 00000000fee00fff  b5d0af50  a8f1ab10  ff88f870  ff072b10  MMIO     APIC Memory
00:00:06.056243 00000000ffff0000 - 00000000ffffffff  b5cadb20  a8ed7580  ff8ace50  ff02f580  Write    PC BIOS - 0xffffffff
00:00:06.056250 Virtual handlers:
00:00:06.056251 From             - To (excl)         HandlerHC HandlerGC Type       Description
00:00:06.056256 Hypervisor Virtual handlers:
00:00:06.056257 From             - To (excl)         HandlerHC HandlerGC Type       Description
00:00:06.056264 00000000ff006c50 - 00000000ff00744f  00000000  ff883610  WriteHyp   Shadow IDT write access handler
00:00:06.056271 00000000ff008110 - 00000000ff008197  00000000  ff883490  WriteHyp   Shadow TSS write access handler
00:00:06.056277 00000000ff657000 - 00000000ff666fff  00000000  ff883330  WriteHyp   Shadow GDT write access handler
00:00:06.056284 00000000ff668000 - 00000000ff678fff  00000000  ff8833e0  WriteHyp   Shadow LDT write access handler
00:00:06.056290 *** mmio
00:00:06.056295 MMIO ranges (pVM=a92dc000)
00:00:06.056297 GC Phys Range                     pDevIns  Read     Write    Fill     pvUser   Description
00:00:06.056303 00000000000a0000-00000000000bffff a6bd1000 a73a7290 a73a5c30 a73a66f0 00000000 VGA - VGA Video Buffer
00:00:06.056310                                R0 a6bd1000 f9b8e210 f9b8e4a0 f9b8d9a0 00000000
00:00:06.056317                                RC ff911000 ff8f1f80 ff8f2230 ff8f16e0 00000000
00:00:06.056337 00000000dc000000-00000000dfffffff a8ed7d20 a739be30 a739bfe0 00000000 00000000 MCFG ranges
00:00:06.056344                                R0 a8ed7d20 f9b8bc80 f9b8bbd0 00000000 00000000
00:00:06.056350                                RC ff02fd20 ff8efc60 ff8efbb0 00000000 00000000
00:00:06.056358 00000000f0500000-00000000f0500fff a8f24f20 a740e610 a740e030 00000000 00000000 USB OHCI
00:00:06.056364                                R0 a8f24f20 f9b9bc20 f9b9bcb0 00000000 00000000
00:00:06.056370                                RC ff07cf20 ff8ff390 ff8ff420 00000000 00000000
00:00:06.056377 00000000fec00000-00000000fec00fff a8f1b150 a72d30a0 a72d2f70 00000000 a8f1b210 I/O APIC Memory
00:00:06.056384                                R0 a8f1b150 f9bca0f0 f9bca270 00000000 00000000
00:00:06.056391                                RC ff073150 ff90e0d0 ff90e250 00000000 00000000
00:00:06.056398 00000000fed00000-00000000fed00fff a8f1b4d0 a73e75f0 a73e7d90 00000000 a8f1b590 HPET Memory
00:00:06.056405                                R0 a8f1b4d0 f9b928f0 f9b92bd0 00000000 00000000
00:00:06.056411                                RC ff0734d0 ff8f6680 ff8f6960 00000000 00000000
00:00:06.056418 00000000fed1c000-00000000fed1ffff a79f2760 a72d3b20 a72d3bb0 00000000 a79f2820 LPC Memory
00:00:06.056425                                R0 00000000 00000000 00000000 00000000 00000000
00:00:06.056431                                RC 00000000 00000000 00000000 00000000 00000000
00:00:06.056438 00000000fee00000-00000000fee00fff a8f19ff0 a72d0f50 a72d2090 00000000 a8f1a0b0 APIC Memory
00:00:06.056444                                R0 a8f19ff0 f9bc9c70 f9bc9db0 00000000 00000000
00:00:06.056451                                RC ff071ff0 ff90dc50 ff90dd90 00000000 00000000
00:00:06.056457 *** phys
00:00:06.056462 RAM ranges (pVM=a92dc000)
00:00:06.056464 GC Phys Range                     pvHC    
00:00:06.056468 0000000000000000-000000003fffffff 00000000 Base RAM
00:00:06.056475 00000000dc000000-00000000dfffffff 00000000 MCFG ranges
00:00:06.056481 00000000e0000000-00000000e1ffffff a4a00000 VRam
00:00:06.056487 00000000f0000000-00000000f03fffff a6c70000 VMMDev
00:00:06.056493 00000000f0400000-00000000f0403fff aa997000 VMMDev Heap
00:00:06.056500 00000000f0500000-00000000f0500fff 00000000 USB OHCI
00:00:06.056505 00000000fec00000-00000000fec00fff 00000000 I/O APIC Memory
00:00:06.056512 00000000fed00000-00000000fed00fff 00000000 HPET Memory
00:00:06.056518 00000000fed1c000-00000000fed1ffff 00000000 LPC Memory
00:00:06.056524 00000000fee00000-00000000fee00fff 00000000 APIC Memory
00:00:06.056530 00000000ffff0000-00000000ffffffff 00000000 PC BIOS - 0xffffffff
00:00:06.057469 fatal error in recompiler cpu: Trying to execute code with memory type addr_code=00000000000a4020 addend=00000000a7085000 at 00000000000a4817. (iHandlerMemType=0x38 iMMIOMemType=0x30)
00:00:06.057471 
00:00:06.057486 !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
00:00:06.057487 !!
00:00:06.057488 !!                 Guru Meditation -2301 (VERR_REM_VIRTUAL_CPU_ERROR)
00:00:06.057499 !!
00:00:06.057531 !!
00:00:06.057532 !! {mappings, <NULL>}
00:00:06.057533 !!
00:00:06.057542 
00:00:06.057542 The mappings are FLOATING.
00:00:06.057546 00000000ff000000 - 00000000ffbfffff  Hypervisor Memory Area
00:00:06.057559 !!
00:00:06.057560 !! {hma, <NULL>}
00:00:06.057561 !!
00:00:06.057569 Hypervisor Memory Area (HMA) Layout: Base 00000000ff000000, 0x00c00000 bytes
00:00:06.057581 00000000ffa1a000-00000000ffa1b000                   DYNAMIC          fence
00:00:06.057619 00000000ffa0a000-00000000ffa1a000                   DYNAMIC          Dynamic mapping not crossing
00:00:06.057658 00000000ff9fa000-00000000ffa0a000                   DYNAMIC          Dynamic mapping
00:00:06.057695 00000000ff9f9000-00000000ff9fa000                   DYNAMIC          fence
00:00:06.057733 00000000ff9d9000-00000000ff9f9000 a6b90000 a6b90000 LOCKED           alloc once (PDM_DEVICE_USER)
00:00:06.057761 00000000ff9d8000-00000000ff9d9000                   DYNAMIC          fence
00:00:06.057799 00000000ff9c8000-00000000ff9d8000 a7a09000 a7a09000 LOCKED           alloc once (PDM_DEVICE_USER)
00:00:06.057827 00000000ff948000-00000000ff9c8000                   MMIO2   0000000000000000 VGA VRam
00:00:06.057860 00000000ff947000-00000000ff948000                   DYNAMIC          fence
00:00:06.057897 00000000ff926000-00000000ff947000 a7a3a000 a7a3a000 LOCKED           alloc once (PGM_PHYS)
00:00:06.057925 00000000ff925000-00000000ff926000                   DYNAMIC          fence
00:00:06.057963 00000000ff911000-00000000ff925000 a6bd1000 a6bd1000 LOCKED           alloc once (PDM_DEVICE)
00:00:06.057991 00000000ff910000-00000000ff911000                   DYNAMIC          fence
00:00:06.058028 00000000ff90c000-00000000ff910000 b0600000 00000000 LOCKED           VBoxDD2GC.gc
00:00:06.058055 00000000ff90b000-00000000ff90c000                   DYNAMIC          fence
00:00:06.058093 00000000ff8ef000-00000000ff90b000 a7070000 00000000 LOCKED           VBoxDDGC.gc
00:00:06.058120 00000000ff8ee000-00000000ff8ef000                   DYNAMIC          fence
00:00:06.058157 00000000ff881000-00000000ff8ee000 a7c0b000 00000000 LOCKED           VMMGC.gc
00:00:06.058184 00000000ff880000-00000000ff881000                   DYNAMIC          fence
00:00:06.058225 00000000ff67a000-00000000ff880000 a76fa000 a76fa000 LOCKED           alloc once (PATM)
00:00:06.058253 00000000ff679000-00000000ff67a000                   DYNAMIC          fence
00:00:06.058291 00000000ff668000-00000000ff679000 a7a5b000 a7a5b000 LOCKED           alloc once (SELM)
00:00:06.058318 00000000ff667000-00000000ff668000                   DYNAMIC          fence
00:00:06.058356 00000000ff657000-00000000ff667000 a7a6c000 a7a6c000 LOCKED           alloc once (SELM)
00:00:06.058383 00000000ff656000-00000000ff657000                   DYNAMIC          fence
00:00:06.058421 00000000ff653000-00000000ff656000 a7a7c000 f9b44000 HCPHYS  0000000023880000 Core Code
00:00:06.058444 00000000ff652000-00000000ff653000                   DYNAMIC          fence
00:00:06.058482 00000000ff651000-00000000ff652000 b6518000 00000000 HCPHYS  0000000031f24000 GIP
00:00:06.058504 00000000ff650000-00000000ff651000                   DYNAMIC          fence
00:00:06.058542 00000000ff24f000-00000000ff650000 a7c78000 a7c78000 LOCKED           alloc once (PGM_PHYS)
00:00:06.058569 00000000ff24e000-00000000ff24f000                   DYNAMIC          fence
00:00:06.058607 00000000ff229000-00000000ff24e000 a8e05000 a8e05000 LOCKED           alloc once (PGM_POOL)
00:00:06.058634 00000000ff228000-00000000ff229000                   DYNAMIC          fence
00:00:06.058672 00000000ff223000-00000000ff228000                   DYNAMIC          CR3 mapping
00:00:06.058709 00000000ff222000-00000000ff223000                   DYNAMIC          fence
00:00:06.058746 00000000ff022000-00000000ff222000 a8eca000 a8eca000 LOCKED           Heap
00:00:06.058774 00000000ff021000-00000000ff022000                   DYNAMIC          fence
00:00:06.058811 00000000ff001000-00000000ff021000 a92dc000 f9abe000 LOCKED           VM
00:00:06.058838 00000000ff000000-00000000ff001000                   DYNAMIC          fence
00:00:06.058875 !!
00:00:06.058875 !! {cpumguest, verbose}
00:00:06.058877 !!
00:00:06.058888 Guest CPUM (VCPU 0) state: 
00:00:06.058898 eax=00009600 ebx=0000f000 ecx=0000adb2 edx=00000180 esi=000007be edi=00000005
00:00:06.058901 eip=0000ad57 esp=00002e66 ebp=00001b74 iopl=0         nv up di pl zr na pe nc
00:00:06.058904 cs={99ac base=0000000000099ac0 limit=0000ffff flags=0000009b} dr0=00000000 dr1=00000000
00:00:06.058908 ds={002e base=00000000000002e0 limit=0000ffff flags=00000093} dr2=00000000 dr3=00000000
00:00:06.058910 es={0d00 base=000000000000d000 limit=0000ffff flags=00000093} dr4=00000000 dr5=00000000
00:00:06.058914 fs={0000 base=0000000000000000 limit=0000ffff flags=00000093} dr6=ffff0ff0 dr7=00000400
00:00:06.058917 gs={0000 base=0000000000000000 limit=0000ffff flags=00000093} cr0=00000010 cr2=00000000
00:00:06.058920 ss={0000 base=0000000000000000 limit=0000ffff flags=00000093} cr3=00000000 cr4=00000000
00:00:06.058923 gdtr=00000000000fe898:0047  idtr=0000000000000000:ffff  eflags=00000002
00:00:06.058926 ldtr={0000 base=00000000 limit=0000ffff flags=00000082}
00:00:06.058928 tr  ={0000 base=00000000 limit=0000ffff flags=0000008b}
00:00:06.058930 SysEnter={cs=0000 eip=00000000 esp=00000000}
00:00:06.059136 FCW=037f FSW=0000 FTW=0000 FOP=0000 MXCSR=00001f80 MXCSR_MASK=0000ffff
00:00:06.059138 FPUIP=00000000 CS=0000 Rsrvd1=0000  FPUDP=00000000 DS=0000 Rsvrd2=0000
00:00:06.059183 ST(0)=FPR0={0000'00000000'00000000} t0 +0.0000000000000000000000 ^ 0
00:00:06.059212 ST(1)=FPR1={0000'00000000'00000000} t0 +0.0000000000000000000000 ^ 0
00:00:06.059240 ST(2)=FPR2={0000'00000000'00000000} t0 +0.0000000000000000000000 ^ 0
00:00:06.059283 ST(3)=FPR3={0000'00000000'00000000} t0 +0.0000000000000000000000 ^ 0
00:00:06.059311 ST(4)=FPR4={0000'00000000'00000000} t0 +0.0000000000000000000000 ^ 0
00:00:06.059338 ST(5)=FPR5={0000'00000000'00000000} t0 +0.0000000000000000000000 ^ 0
00:00:06.059366 ST(6)=FPR6={0000'00000000'00000000} t0 +0.0000000000000000000000 ^ 0
00:00:06.059393 ST(7)=FPR7={0000'00000000'00000000} t0 +0.0000000000000000000000 ^ 0
00:00:06.059420 XMM0 =00000000'00000000'00000000'00000000  XMM1 =00000000'00000000'00000000'00000000
00:00:06.059453 XMM2 =00000000'00000000'00000000'00000000  XMM3 =00000000'00000000'00000000'00000000
00:00:06.059484 XMM4 =00000000'00000000'00000000'00000000  XMM5 =00000000'00000000'00000000'00000000
00:00:06.059515 XMM6 =00000000'00000000'00000000'00000000  XMM7 =00000000'00000000'00000000'00000000
00:00:06.059546 XMM8 =00000000'00000000'00000000'00000000  XMM9 =00000000'00000000'00000000'00000000
00:00:06.059577 XMM10=00000000'00000000'00000000'00000000  XMM11=00000000'00000000'00000000'00000000
00:00:06.059606 XMM12=00000000'00000000'00000000'00000000  XMM13=00000000'00000000'00000000'00000000
00:00:06.059635 XMM14=00000000'00000000'00000000'00000000  XMM15=00000000'00000000'00000000'00000000
00:00:06.059664 EFER         =0000000000000000
00:00:06.059666 PAT          =0007040600070406
00:00:06.059668 STAR         =0000000000000000
00:00:06.059669 CSTAR        =0000000000000000
00:00:06.059670 LSTAR        =0000000000000000
00:00:06.059672 SFMASK       =0000000000000000
00:00:06.059673 KERNELGSBASE =0000000000000000
00:00:06.059704 !!
00:00:06.059705 !! {cpumguestinstr, verbose}
00:00:06.059706 !!
00:00:06.059734 !!
00:00:06.059735 !! {cpumhyper, verbose}
00:00:06.059737 !!
00:00:06.059745 Hypervisor CPUM state: 
00:00:06.059750 .eax=00000000 .ebx=00000000 .ecx=00000000 .edx=00000000 .esi=00000000 .edi=00000014
00:00:06.059753 .eip=ff6549cb .esp=ff220000 .ebp=00000000 .iopl=0           nv up di pl zr na pe nc
00:00:06.059756 .cs={fff8 base=0000000000000000 limit=00000000 flags=00000000} .dr0=00000000 .dr1=00000000
00:00:06.059759 .ds={fff0 base=0000000000000000 limit=00000000 flags=00000000} .dr2=00000000 .dr3=00000000
00:00:06.059762 .es={fff0 base=0000000000000000 limit=00000000 flags=00000000} .dr4=00000000 .dr5=00000000
00:00:06.059765 .fs={0000 base=0000000000000000 limit=00000000 flags=00000000} .dr6=00000000 .dr7=00000000
00:00:06.059767 .gs={0000 base=0000000000000000 limit=00000000 flags=00000000} .cr0=00000000 .cr2=00000000
00:00:06.059770 .ss={fff0 base=0000000000000000 limit=00000000 flags=00000000} .cr3=2bccd000 .cr4=00000000
00:00:06.059773 .gdtr=00000000ff657000:ffff  .idtr=00000000ff006c50:07ff  .eflags=00000000
00:00:06.059777 .ldtr={0000 base=00000000 limit=00000000 flags=00000000}
00:00:06.059779 .tr  ={ffe0 base=00000000 limit=00000000 flags=00000000}
00:00:06.059781 .SysEnter={cs=0000 eip=00000000 esp=00000000}
00:00:06.060044 .FCW=0000 .FSW=0000 .FTW=0000 .FOP=0000 .MXCSR=00000000 .MXCSR_MASK=00000000
00:00:06.060046 .FPUIP=00000000 .CS=0000 .Rsrvd1=0000  .FPUDP=00000000 .DS=0000 .Rsvrd2=0000
00:00:06.060100 .ST(0)=.FPR0={0000'00000000'00000000} t0 +0.0000000000000000000000 ^ 0
00:00:06.060131 .ST(1)=.FPR1={0000'00000000'00000000} t0 +0.0000000000000000000000 ^ 0
00:00:06.060161 .ST(2)=.FPR2={0000'00000000'00000000} t0 +0.0000000000000000000000 ^ 0
00:00:06.060190 .ST(3)=.FPR3={0000'00000000'00000000} t0 +0.0000000000000000000000 ^ 0
00:00:06.060219 .ST(4)=.FPR4={0000'00000000'00000000} t0 +0.0000000000000000000000 ^ 0
00:00:06.060248 .ST(5)=.FPR5={0000'00000000'00000000} t0 +0.0000000000000000000000 ^ 0
00:00:06.060278 .ST(6)=.FPR6={0000'00000000'00000000} t0 +0.0000000000000000000000 ^ 0
00:00:06.060307 .ST(7)=.FPR7={0000'00000000'00000000} t0 +0.0000000000000000000000 ^ 0
00:00:06.060336 .XMM0 =00000000'00000000'00000000'00000000  .XMM1 =00000000'00000000'00000000'00000000
00:00:06.060370 .XMM2 =00000000'00000000'00000000'00000000  .XMM3 =00000000'00000000'00000000'00000000
00:00:06.060404 .XMM4 =00000000'00000000'00000000'00000000  .XMM5 =00000000'00000000'00000000'00000000
00:00:06.060436 .XMM6 =00000000'00000000'00000000'00000000  .XMM7 =00000000'00000000'00000000'00000000
00:00:06.060469 .XMM8 =00000000'00000000'00000000'00000000  .XMM9 =00000000'00000000'00000000'00000000
00:00:06.060502 .XMM10=00000000'00000000'00000000'00000000  .XMM11=00000000'00000000'00000000'00000000
00:00:06.060534 .XMM12=00000000'00000000'00000000'00000000  .XMM13=00000000'00000000'00000000'00000000
00:00:06.060565 .XMM14=00000000'00000000'00000000'00000000  .XMM15=00000000'00000000'00000000'00000000
00:00:06.060596 .EFER         =0000000000000000
00:00:06.060598 .PAT          =0000000000000000
00:00:06.060599 .STAR         =0000000000000000
00:00:06.060600 .CSTAR        =0000000000000000
00:00:06.060601 .LSTAR        =0000000000000000
00:00:06.060603 .SFMASK       =0000000000000000
00:00:06.060604 .KERNELGSBASE =0000000000000000
00:00:06.060639 CR4OrMask=0x204 CR4AndMask=0x403
00:00:06.060647 !!
00:00:06.060648 !! {cpumhost, verbose}
00:00:06.060649 !!
00:00:06.060656 Host CPUM state: 
00:00:06.060661 eax=xxxxxxxx ebx=f9abe000 ecx=xxxxxxxx edx=xxxxxxxx esi=00000000 edi=00200206
00:00:06.060663 eip=xxxxxxxx esp=eb3e3dcc ebp=eb3e3e20 iopl=0         nv up di nt zr na po nc
00:00:06.060665 cs=0000 ds=007b es=007b fs=00d8 gs=00e0                       eflags=00200086
00:00:06.060668 cr0=23e6800080050033 cr2=xxxxxxxx cr3=000007f0 cr4=00000000 gdtr=00000000:0000 ldtr=0000
00:00:06.060672 dr[0]=fff7bdd000 dr[1]=6000000000x dr[2]=00000000 dr[3]=00000000x dr[6]=1d00000000 dr[7]=b5ddc2bcb75b8584
00:00:06.060678 SysEnter={cs=b74d74b0 eip=9fd00018 esp=b5ddc2aa}
00:00:06.060769 !!
00:00:06.060769 !! {mode, all}
00:00:06.060771 !!
00:00:06.060779 Guest paging mode:  Real (changed 3 times), A20 disabled (changed 1 times)
00:00:06.060793 Shadow paging mode: PAE
00:00:06.060798 Host paging mode:   PAE+G
00:00:06.060803 !!
00:00:06.060804 !! {cpuid, verbose}
00:00:06.060805 !!
00:00:06.060813          RAW Standard CPUIDs
00:00:06.060814      Function  eax      ebx      ecx      edx
00:00:06.060817 Gst: 00000000  00000005 756e6547 6c65746e 49656e69
00:00:06.060820 Hst:           0000000a 756e6547 6c65746e 49656e69
00:00:06.060846 Gst: 00000001  000006f6 00000800 00000209 078bf3bf
00:00:06.060848 Hst:           000006f6 00020800 0000e3bd bfebfbff
00:00:06.060874 Gst: 00000002  05b0b101 005657f0 00000000 2cb43049
00:00:06.060877 Hst:           05b0b101 005657f0 00000000 2cb43049
00:00:06.060903 Gst: 00000003  00000000 00000000 00000000 00000000
00:00:06.060905 Hst:           00000000 00000000 00000000 00000000
00:00:06.060927 Gst: 00000004  00000000 00000000 00000000 00000000
00:00:06.060929 Hst:           04000121 01c0003f 0000003f 00000001
00:00:06.060953 Gst: 00000005  00000040 00000040 00000000 00000000
00:00:06.060955 Hst:           00000040 00000040 00000003 00022220
00:00:06.060979 Name:                            GenuineIntel
00:00:06.060980 Supports:                        0-5
00:00:06.060991 Family:                          6      Extended: 0     Effective: 6
00:00:06.060992 Model:                           15      Extended: 0     Effective: 15
00:00:06.060993 Stepping:                        6
00:00:06.060994 Type:                            0 (primary)
00:00:06.060996 APIC ID:                         0x00
00:00:06.060997 Logical CPUs:                    0
00:00:06.060998 CLFLUSH Size:                    8
00:00:06.060998 Brand ID:                        0x00
00:00:06.061033 Mnemonic - Description                 = guest (host)
00:00:06.061036 FPU - x87 FPU on Chip                  = 1 (1)
00:00:06.061043 VME - Virtual 8086 Mode Enhancements   = 1 (1)
00:00:06.061051 DE - Debugging extensions              = 1 (1)
00:00:06.061058 PSE - Page Size Extension              = 1 (1)
00:00:06.061065 TSC - Time Stamp Counter               = 1 (1)
00:00:06.061072 MSR - Model Specific Registers         = 1 (1)
00:00:06.061080 PAE - Physical Address Extension       = 0 (1)
00:00:06.061087 MCE - Machine Check Exception          = 1 (1)
00:00:06.061094 CX8 - CMPXCHG8B instruction            = 1 (1)
00:00:06.061101 APIC - APIC On-Chip                    = 1 (1)
00:00:06.061108 10 - Reserved                          = 0 (0)
00:00:06.061115 SEP - SYSENTER and SYSEXIT             = 0 (1)
00:00:06.061122 MTRR - Memory Type Range Registers     = 1 (1)
00:00:06.061129 PGE - PTE Global Bit                   = 1 (1)
00:00:06.061136 MCA - Machine Check Architecture       = 1 (1)
00:00:06.061143 CMOV - Conditional Move Instructions   = 1 (1)
00:00:06.061150 PAT - Page Attribute Table             = 1 (1)
00:00:06.061157 PSE-36 - 36-bit Page Size Extention    = 1 (1)
00:00:06.061164 PSN - Processor Serial Number          = 0 (0)
00:00:06.061171 CLFSH - CLFLUSH Instruction.           = 1 (1)
00:00:06.061178 20 - Reserved                          = 0 (0)
00:00:06.061185 DS - Debug Store                       = 0 (1)
00:00:06.061192 ACPI - Thermal Mon. & Soft. Clock Ctrl.= 0 (1)
00:00:06.061199 MMX - Intel MMX Technology             = 1 (1)
00:00:06.061206 FXSR - FXSAVE and FXRSTOR Instructions = 1 (1)
00:00:06.061213 SSE - SSE Support                      = 1 (1)
00:00:06.061221 SSE2 - SSE2 Support                    = 1 (1)
00:00:06.061228 SS - Self Snoop                        = 0 (1)
00:00:06.061235 HTT - Hyper-Threading Technology       = 0 (1)
00:00:06.061242 TM - Thermal Monitor                   = 0 (1)
00:00:06.061249 30 - Reserved                          = 0 (0)
00:00:06.061256 PBE - Pending Break Enable             = 0 (1)
00:00:06.061263 Supports SSE3                          = 1 (1)
00:00:06.061270 PCLMULQDQ                              = 0 (0)
00:00:06.061277 DS Area 64-bit layout                  = 0 (1)
00:00:06.061284 Supports MONITOR/MWAIT                 = 1 (1)
00:00:06.061291 CPL-DS - CPL Qualified Debug Store     = 0 (1)
00:00:06.061298 VMX - Virtual Machine Technology       = 0 (1)
00:00:06.061305 SMX - Safer Mode Extensions            = 0 (0)
00:00:06.061312 Enhanced SpeedStep Technology          = 0 (1)
00:00:06.061319 Terminal Monitor 2                     = 0 (1)
00:00:06.061326 Supplemental SSE3 instructions         = 1 (1)
00:00:06.061333 L1 Context ID                          = 0 (0)
00:00:06.061340 11 - Reserved                          = 0 (0)
00:00:06.061347 FMA extensions using YMM state         = 0 (0)
00:00:06.061354 CMPXCHG16B instruction                 = 0 (1)
00:00:06.061361 xTPR Update Control                    = 0 (1)
00:00:06.061368 Perf/Debug Capability MSR              = 0 (1)
00:00:06.061375 16 - Reserved                          = 0 (0)
00:00:06.061382 PCID - Process-context identifiers     = 0 (0)
00:00:06.061389 DCA - Direct Cache Access              = 0 (0)
00:00:06.061396 SSE4.1 instruction extensions          = 0 (0)
00:00:06.061403 SSE4.2 instruction extensions          = 0 (0)
00:00:06.061411 Supports the x2APIC extensions         = 0 (0)
00:00:06.061418 MOVBE instruction                      = 0 (0)
00:00:06.061425 POPCNT instruction                     = 0 (0)
00:00:06.061432 TSC-Deadline LAPIC timer mode          = 0 (0)
00:00:06.061439 AESNI instruction extensions           = 0 (0)
00:00:06.061446 XSAVE/XRSTOR extended state feature    = 0 (0)
00:00:06.061453 Supports OSXSAVE                       = 0 (0)
00:00:06.061460 AVX instruction extensions             = 0 (0)
00:00:06.061467 29/30 - Reserved                       = 0x0 (0x0)
00:00:06.061475 Hypervisor Present (we're a guest)     = 0 (0)
00:00:06.061482 
00:00:06.061483          RAW Extended CPUIDs
00:00:06.061483      Function  eax      ebx      ecx      edx
00:00:06.061486 Gst: 80000000  80000008 00000000 00000000 00000000
00:00:06.061489 Hst:           80000008 00000000 00000000 00000000
00:00:06.061513 Gst: 80000001  00000000 00000000 00000000 00000000
00:00:06.061515 Hst:           00000000 00000000 00000001 20100000
00:00:06.061539 Gst: 80000002  65746e49 2952286c 726f4320 4d542865
00:00:06.061541 Hst:           65746e49 2952286c 726f4320 4d542865
00:00:06.061568 Gst: 80000003  43203229 20205550 20202020 54202020
00:00:06.061570 Hst:           43203229 20205550 20202020 54202020
00:00:06.061597 Gst: 80000004  30303237 20402020 30302e32 007a4847
00:00:06.061599 Hst:           30303237 20402020 30302e32 007a4847
00:00:06.061625 Gst: 80000005  00000000 00000000 00000000 00000000
00:00:06.061627 Hst:           00000000 00000000 00000000 00000000
00:00:06.061650 Gst: 80000006  00000000 00000000 10008040 00000000
00:00:06.061652 Hst:           00000000 00000000 10008040 00000000
00:00:06.061676 Gst: 80000007  00000000 00000000 00000000 00000000
00:00:06.061678 Hst:           00000000 00000000 00000000 00000000
00:00:06.061701 Gst: 80000008  00003024 00000000 00000000 00000000
00:00:06.061703 Hst:           00003024 00000000 00000000 00000000
00:00:06.061726 Gst: 80000009  07280202 00000000 00000000 00000000*
00:00:06.061729 Hst:           07280202 00000000 00000000 00000000
00:00:06.061754 Ext Name:                        
00:00:06.061755 Ext Supports:                    0x80000000-0x80000008
00:00:06.061764 Family:                          0      Extended: 0     Effective: 0
00:00:06.061765 Model:                           0      Extended: 0     Effective: 0
00:00:06.061767 Stepping:                        0
00:00:06.061767 Brand ID:                        0x000
00:00:06.061789 Mnemonic - Description                 = guest (host)
00:00:06.061792 FPU - x87 FPU on Chip                  = 0 (0)
00:00:06.061799 VME - Virtual 8086 Mode Enhancements   = 0 (0)
00:00:06.061807 DE - Debugging extensions              = 0 (0)
00:00:06.061814 PSE - Page Size Extension              = 0 (0)
00:00:06.061821 TSC - Time Stamp Counter               = 0 (0)
00:00:06.061828 MSR - K86 Model Specific Registers     = 0 (0)
00:00:06.061835 PAE - Physical Address Extension       = 0 (0)
00:00:06.061842 MCE - Machine Check Exception          = 0 (0)
00:00:06.061849 CX8 - CMPXCHG8B instruction            = 0 (0)
00:00:06.061856 APIC - APIC On-Chip                    = 0 (0)
00:00:06.061863 10 - Reserved                          = 0 (0)
00:00:06.061870 SEP - SYSCALL and SYSRET               = 0 (0)
00:00:06.061877 MTRR - Memory Type Range Registers     = 0 (0)
00:00:06.061884 PGE - PTE Global Bit                   = 0 (0)
00:00:06.061891 MCA - Machine Check Architecture       = 0 (0)
00:00:06.061898 CMOV - Conditional Move Instructions   = 0 (0)
00:00:06.061905 PAT - Page Attribute Table             = 0 (0)
00:00:06.061912 PSE-36 - 36-bit Page Size Extention    = 0 (0)
00:00:06.061919 18 - Reserved                          = 0 (0)
00:00:06.061926 19 - Reserved                          = 0 (0)
00:00:06.061933 NX - No-Execute Page Protection        = 0 (1)
00:00:06.061940 DS - Debug Store                       = 0 (0)
00:00:06.061947 AXMMX - AMD Extensions to MMX Instr.   = 0 (0)
00:00:06.061954 MMX - Intel MMX Technology             = 0 (0)
00:00:06.061961 FXSR - FXSAVE and FXRSTOR Instructions = 0 (0)
00:00:06.061968 25 - AMD fast FXSAVE and FXRSTOR Instr.= 0 (0)
00:00:06.061975 26 - 1 GB large page support           = 0 (0)
00:00:06.061982 27 - RDTSCP instruction                = 0 (0)
00:00:06.061989 28 - Reserved                          = 0 (0)
00:00:06.061996 29 - AMD Long Mode                     = 0 (1)
00:00:06.062003 30 - AMD Extensions to 3DNow!          = 0 (0)
00:00:06.062010 31 - AMD 3DNow!                        = 0 (0)
00:00:06.062017 LahfSahf - LAHF/SAHF in 64-bit mode    = 0 (1)
00:00:06.062024 CmpLegacy - Core MP legacy mode (depr) = 0 (0)
00:00:06.062031 SVM - AMD VM Extensions                = 0 (0)
00:00:06.062038 APIC registers starting at 0x400       = 0 (0)
00:00:06.062045 AltMovCR8 - LOCK MOV CR0 means MOV CR8 = 0 (0)
00:00:06.062052 5  - Advanced bit manipulation         = 0 (0)
00:00:06.062059 6  - SSE4A instruction support         = 0 (0)
00:00:06.062066 7  - Misaligned SSE mode               = 0 (0)
00:00:06.062073 8  - PREFETCH and PREFETCHW instruction= 0 (0)
00:00:06.062081 9  - OS visible workaround             = 0 (0)
00:00:06.062092 10 - Instruction based sampling        = 0 (0)
00:00:06.062099 11 - SSE5 support                      = 0 (0)
00:00:06.062106 12 - SKINIT, STGI, and DEV support     = 0 (0)
00:00:06.062113 13 - Watchdog timer support.           = 0 (0)
00:00:06.062120 31:14 - Reserved                       = 0x0 (0x0)
00:00:06.062128 Full Name:                       Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz
00:00:06.062134 TLB 2/4M Instr/Uni:              res0     0 entries
00:00:06.062135 TLB 2/4M Data:                   res0     0 entries
00:00:06.062148 TLB 4K Instr/Uni:                res0     0 entries
00:00:06.062149 TLB 4K Data:                     res0     0 entries
00:00:06.062161 L1 Instr Cache Line Size:        0 bytes
00:00:06.062162 L1 Instr Cache Lines Per Tag:    0
00:00:06.062163 L1 Instr Cache Associativity:    res0  
00:00:06.062164 L1 Instr Cache Size:             0 KB
00:00:06.062177 L1 Data Cache Line Size:         0 bytes
00:00:06.062178 L1 Data Cache Lines Per Tag:     0
00:00:06.062179 L1 Data Cache Associativity:     res0  
00:00:06.062180 L1 Data Cache Size:              0 KB
00:00:06.062192 L2 TLB 2/4M Instr/Uni:           off       0 entries
00:00:06.062193 L2 TLB 2/4M Data:                off       0 entries
00:00:06.062206 L2 TLB 4K Instr/Uni:             off       0 entries
00:00:06.062207 L2 TLB 4K Data:                  off       0 entries
00:00:06.062219 L2 Cache Line Size:              0 bytes
00:00:06.062220 L2 Cache Lines Per Tag:          0
00:00:06.062221 L2 Cache Associativity:          off   
00:00:06.062221 L2 Cache Size:                   0 KB
00:00:06.062234 APM Features:                   
00:00:06.062238 Physical Address Width:          36 bits
00:00:06.062239 Virtual Address Width:           48 bits
00:00:06.062240 Guest Physical Address Width:    0 bits
00:00:06.062250 Physical Core Count:             0
00:00:06.062255 
00:00:06.062256          RAW Centaur CPUIDs
00:00:06.062257      Function  eax      ebx      ecx      edx
00:00:06.062260 Gst: c0000000  07280202 00000000 00000000 00000000
00:00:06.062262 Hst:           07280202 00000000 00000000 00000000
00:00:06.062287 Gst: c0000001  07280202 00000000 00000000 00000000
00:00:06.062289 Hst:           07280202 00000000 00000000 00000000
00:00:06.062313 Gst: c0000002  07280202 00000000 00000000 00000000
00:00:06.062315 Hst:           07280202 00000000 00000000 00000000
00:00:06.062340 Gst: c0000003  07280202 00000000 00000000 00000000
00:00:06.062342 Hst:           07280202 00000000 00000000 00000000
00:00:06.062366 Centaur Supports:                0xc0000000-0x07280202
00:00:06.062372 Mnemonic - Description                 = guest (host)
00:00:06.062375 AIS - Alternate Instruction Set        = 0 (0)
00:00:06.062382 AIS-E - AIS enabled                    = 0 (0)
00:00:06.062389 RNG - Random Number Generator          = 0 (0)
00:00:06.062397 RNG-E - RNG enabled                    = 0 (0)
00:00:06.062404 LH - LongHaul MSR 0000_110Ah           = 0 (0)
00:00:06.062411 FEMMS - FEMMS                          = 0 (0)
00:00:06.062418 ACE - Advanced Cryptography Engine     = 0 (0)
00:00:06.062425 ACE-E - ACE enabled                    = 0 (0)
00:00:06.062432 ACE2 - Advanced Cryptography Engine 2  = 0 (0)
00:00:06.062439 ACE2-E - ACE enabled                   = 0 (0)
00:00:06.062447 PHE - Padlock Hash Engine              = 0 (0)
00:00:06.062454 PHE-E - PHE enabled                    = 0 (0)
00:00:06.062461 PMM - Montgomery Multiplier            = 0 (0)
00:00:06.062468 PMM-E - PMM enabled                    = 0 (0)
00:00:06.062475 14 - Reserved                          = 0 (0)
00:00:06.062482 15 - Reserved                          = 0 (0)
00:00:06.062489 Parallax                               = 0 (0)
00:00:06.062496 Parallax enabled                       = 0 (0)
00:00:06.062503 Overstress                             = 0 (0)
00:00:06.062510 Overstress enabled                     = 0 (0)
00:00:06.062517 TM3 - Temperature Monitoring 3         = 0 (0)
00:00:06.062524 TM3-E - TM3 enabled                    = 0 (0)
00:00:06.062531 RNG2 - Random Number Generator 2       = 0 (0)
00:00:06.062542 RNG2-E - RNG2 enabled                  = 0 (0)
00:00:06.062549 24 - Reserved                          = 0 (0)
00:00:06.062556 PHE2 - Padlock Hash Engine 2           = 0 (0)
00:00:06.062563 PHE2-E - PHE2 enabled                  = 0 (0)
00:00:06.062570 
00:00:06.062572 !!
00:00:06.062573 !! {handlers, phys virt hyper stats}
00:00:06.062574 !!
00:00:06.062584 Physical handlers: (PhysHandlers=54032 (0xd310))
00:00:06.062586 From             - To (incl)         HandlerHC UserHC    HandlerGC UserGC    Type     Description
00:00:06.062626 00000000000a0000 - 00000000000bffff  b5d0af50  a8f23690  ff88f870  ff07b690  MMIO     VGA - VGA Video Buffer
00:00:06.062653 00000000000c0000 - 00000000000c8fff  b5cadb20  a8f23800  ff8ace50  ff07b800  Write    VGA BIOS
00:00:06.062678 00000000000e0000 - 00000000000e0fff  b5cadb20  a8f272c0  ff8ace50  ff07f2c0  Write    ACPI RSDP
00:00:06.062704 00000000000e1000 - 00000000000e1fff  b5cadb20  a8ed7150  ff8ace50  ff02f150  Write    DMI tables
00:00:06.062729 00000000000e2000 - 00000000000effff  b5cadb20  a8ed7a30  ff8ace50  ff02fa30  Write    Net Boot ROM
00:00:06.062755 00000000000f0000 - 00000000000fffff  b5cadb20  a8ed7240  ff8ace50  ff02f240  Write    PC BIOS - 0xfffff
00:00:06.062781 00000000dc000000 - 00000000dfffffff  b5d0af50  a8ed8750  ff88f870  ff030750  MMIO     MCFG ranges
00:00:06.062808 00000000e0000000 - 00000000e1ffffff  a73a6f40  a6bd10c0  ff8f2510  ff9110c0  Write    VGA LFB
00:00:06.062835 00000000f0500000 - 00000000f0500fff  b5d0af50  a8f27c30  ff88f870  ff07fc30  MMIO     USB OHCI
00:00:06.062862 00000000fec00000 - 00000000fec00fff  b5d0af50  a8f1b360  ff88f870  ff073360  MMIO     I/O APIC Memory
00:00:06.062889 00000000fed00000 - 00000000fed00fff  b5d0af50  a8f1b8f0  ff88f870  ff0738f0  MMIO     HPET Memory
00:00:06.062916 00000000fed1c000 - 00000000fed1ffff  b5d0af50  a8f27790  ff88f870  ff07f790  MMIO     LPC Memory
00:00:06.062943 00000000fee00000 - 00000000fee00fff  b5d0af50  a8f1ab10  ff88f870  ff072b10  MMIO     APIC Memory
00:00:06.062970 00000000ffff0000 - 00000000ffffffff  b5cadb20  a8ed7580  ff8ace50  ff02f580  Write    PC BIOS - 0xffffffff
00:00:06.062996 Virtual handlers:
00:00:06.062997 From             - To (excl)         HandlerHC HandlerGC Type       Description
00:00:06.063027 Hypervisor Virtual handlers:
00:00:06.063028 From             - To (excl)         HandlerHC HandlerGC Type       Description
00:00:06.063059 00000000ff006c50 - 00000000ff00744f  00000000  ff883610  WriteHyp   Shadow IDT write access handler
00:00:06.063080 00000000ff008110 - 00000000ff008197  00000000  ff883490  WriteHyp   Shadow TSS write access handler
00:00:06.063101 00000000ff657000 - 00000000ff666fff  00000000  ff883330  WriteHyp   Shadow GDT write access handler
00:00:06.063122 00000000ff668000 - 00000000ff678fff  00000000  ff8833e0  WriteHyp   Shadow LDT write access handler
00:00:06.063142 !!
00:00:06.063143 !! {timers, <NULL>}
00:00:06.063144 !!
00:00:06.063155 Timers (pVM=a92dc000)
00:00:06.063156 pTimerR3 offNext  offPrev  offSched Clock               Time             Expire HzHint State                     Description
00:00:06.063225 a8f27fe0 ffffba50 00000000 00000000 Real             1186791            1186787      0 2-ACTIVE                  EMT Yielder
00:00:06.063272 a8f27f80 00000000 ffffbab0 00000000 Real             1186791            1187054      0 2-ACTIVE                  CPU Load Timer
00:00:06.063319 a8f27930 00000000 00000000 00000000 Virt          3704543930                  0      0 1-STOPPED                 USB Device Reset Timer
00:00:06.063363 a8f27730 00000000 ffff4ac0 00000000 VrSy          3697517334      1199864031601      0 2-ACTIVE                  ACPI PM Timer
00:00:06.063412 a8f25d60 00000000 00000000 00000000 Virt          3704543930                  0      0 1-STOPPED                 USB Frame Timer
00:00:06.063456 a8f24ec0 00000000 00000000 00000000 Virt          3704543930         3708122589      0 2-ACTIVE                  Audio timer
00:00:06.063504 a8f23a30 00004550 000045b0 00000000 Real             1186791            1186804      0 2-ACTIVE                  VGA Refresh Timer
00:00:06.063554 a8f1c250 00000000 00000000 00000000 VrSy          3697517334         2990244140      0 1-STOPPED                 MC146818 RTC/CMOS - Second2
00:00:06.063600 a8f1c1f0 0000b540 fffffb00 00000000 VrSy          3697517334         3990000000      0 2-ACTIVE                  MC146818 RTC/CMOS - Second
00:00:06.063648 a8f1c190 00000000 00000000 00000000 VrSy          3697517334                  0      0 1-STOPPED                 MC146818 RTC/CMOS - Periodic
00:00:06.063693 a8f1bcf0 00000500 00000000 00000000 VrSy          3697517334         3752442736     18 2-ACTIVE                  i8254 Programmable Interval Timer
00:00:06.063741 a8f1b890 00000000 00000000 00000000 VrSy          3697517334                  0      0 1-STOPPED                 HPET Timer
00:00:06.063785 a8f1b830 00000000 00000000 00000000 VrSy          3697517334                  0      0 1-STOPPED                 HPET Timer
00:00:06.063978 a8f1b7d0 00000000 00000000 00000000 VrSy          3697517334                  0      0 1-STOPPED                 HPET Timer
00:00:06.064023 a8f1b770 00000000 00000000 00000000 VrSy          3697517334                  0      0 1-STOPPED                 HPET Timer
00:00:06.064068 a8f1ac80 00000000 00000000 00000000 VrSy          3697517334                  0      0 1-STOPPED                 APIC Timer #0
00:00:06.064113 a8f19e10 00000000 00000000 00000000 Virt          3704543930            9073198      0 1-STOPPED                 PS2K Delay Timer
00:00:06.064159 a8f19db0 00000000 00000000 00000000 Real             1186792                  0      0 1-STOPPED                 PS2K Typematic Timer
00:00:06.064203 a8ed6d10 00000000 00000000 00000000 Real             1186792                  0      0 1-STOPPED                 BlkCache-Commit
00:00:06.064248 !!
00:00:06.064249 !! {activetimers, <NULL>}
00:00:06.064250 !!
00:00:06.064260 Active Timers (pVM=a92dc000)
00:00:06.064262 pTimerR3 offNext  offPrev  offSched Clock               Time             Expire HzHint State                     Description
00:00:06.064331 a8f27fe0 ffffba50 00000000 00000000 Real             1186792            1186787      0 2-ACTIVE                  EMT Yielder
00:00:06.064378 a8f23a30 00004550 000045b0 00000000 Real             1186792            1186804      0 2-ACTIVE                  VGA Refresh Timer
00:00:06.064425 a8f27f80 00000000 ffffbab0 00000000 Real             1186792            1187054      0 2-ACTIVE                  CPU Load Timer
00:00:06.064473 a8f24ec0 00000000 00000000 00000000 Virt          3704543930         3708122589      0 2-ACTIVE                  Audio timer
00:00:06.064520 a8f1bcf0 00000500 00000000 00000000 VrSy          3697517334         3752442736     18 2-ACTIVE                  i8254 Programmable Interval Timer
00:00:06.064568 a8f1c1f0 0000b540 fffffb00 00000000 VrSy          3697517334         3990000000      0 2-ACTIVE                  MC146818 RTC/CMOS - Second
00:00:06.064617 a8f27730 00000000 ffff4ac0 00000000 VrSy          3697517334      1199864031601      0 2-ACTIVE                  ACPI PM Timer
00:00:06.064670 !!
00:00:06.064671 !! {apic}
00:00:06.064672 !!
00:00:06.064678 Invalid argument. Recognized arguments are 'basic', 'lvt', 'timer'.
00:00:06.064682 !!
00:00:06.064683 !! {cfgm}
00:00:06.064683 !!
00:00:06.064688 pRoot=b1208fb0:{/}
00:00:06.064697 [/] (level 0)
00:00:06.064707   CSAMEnabled     <integer> = 0x0000000000000001 (1)
00:00:06.064724   CpuExecutionCap <integer> = 0x0000000000000064 (100)
00:00:06.064736   EnablePAE       <integer> = 0x0000000000000000 (0)
00:00:06.064752   HwVirtExtForced <integer> = 0x0000000000000000 (0)
00:00:06.064763   MemBalloonSize  <integer> = 0x0000000000000000 (0)
00:00:06.064774   Name            <string>  = "test" (cb=5)
00:00:06.064795   NumCPUs         <integer> = 0x0000000000000001 (1)
00:00:06.064813   PATMEnabled     <integer> = 0x0000000000000001 (1)
00:00:06.064827   PageFusion      <integer> = 0x0000000000000000 (0)
00:00:06.064842   RamHoleSize     <integer> = 0x0000000024000000 (603 979 776, 576 MB)
00:00:06.064869   RamSize         <integer> = 0x0000000040000000 (1 073 741 824, 1 024 MB)
00:00:06.064896   RawR0Enabled    <integer> = 0x0000000000000001 (1)
00:00:06.064909   RawR3Enabled    <integer> = 0x0000000000000001 (1)
00:00:06.064923   TimerMillies    <integer> = 0x000000000000000a (10)
00:00:06.064936   UUID            <bytes>   = "00 96 13 0d 02 b9 d3 41 ba 1e 61 b2 25 97 43 cc" (cb=16)
00:00:06.064992 
00:00:06.064994 [/CPUM/] (level 1)
00:00:06.065007   SyntheticCpu <integer> = 0x0000000000000000 (0)
00:00:06.065017 
00:00:06.065020 [/DBGF/] (level 1)
00:00:06.065031   Path <string>  = "/home/nima/VirtualBox VMs/test/debug/;/home/nima/VirtualBox VMs/test/;/home/nima/" (cb=82)
00:00:06.065042 
00:00:06.065044 [/Devices/] (level 1)
00:00:06.065056 
00:00:06.065058 [/Devices/8237A/] (level 2)
00:00:06.065072 
00:00:06.065075 [/Devices/8237A/0/] (level 3)
00:00:06.065091   Trusted <integer> = 0x0000000000000001 (1)
00:00:06.065102 
00:00:06.065104 [/Devices/8237A/0/Config/] (level 4) (restricted root)
00:00:06.065124 
00:00:06.065127 [/Devices/AudioSniffer/] (level 2)
00:00:06.065141 
00:00:06.065143 [/Devices/AudioSniffer/0/] (level 3)
00:00:06.065160 
00:00:06.065162 [/Devices/AudioSniffer/0/Config/] (level 4) (restricted root)
00:00:06.065182 
00:00:06.065185 [/Devices/AudioSniffer/0/LUN#0/] (level 4)
00:00:06.065203   Driver <string>  = "MainAudioSniffer" (cb=17)
00:00:06.065213 
00:00:06.065215 [/Devices/AudioSniffer/0/LUN#0/Config/] (level 5) (restricted root)
00:00:06.065239   Object <integer> = 0x0000000009518640 (156 337 728)
00:00:06.065253 
00:00:06.065255 [/Devices/VMMDev/] (level 2)
00:00:06.065269 
00:00:06.065271 [/Devices/VMMDev/0/] (level 3)
00:00:06.065288   PCIBusNo      <integer> = 0x0000000000000000 (0)
00:00:06.065303   PCIDeviceNo   <integer> = 0x0000000000000004 (4)
00:00:06.065316   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:06.065327   Trusted       <integer> = 0x0000000000000001 (1)
00:00:06.065343 
00:00:06.065345 [/Devices/VMMDev/0/Config/] (level 4) (restricted root)
00:00:06.065365   GuestCoreDumpDir <string>  = "/home/nima/VirtualBox VMs/test/Snapshots" (cb=41)
00:00:06.065376   RamSize          <integer> = 0x0000000040000000 (1 073 741 824, 1 024 MB)
00:00:06.065404 
00:00:06.065406 [/Devices/VMMDev/0/LUN#0/] (level 4)
00:00:06.065425   Driver <string>  = "HGCM" (cb=5)
00:00:06.065435 
00:00:06.065437 [/Devices/VMMDev/0/LUN#0/Config/] (level 5) (restricted root)
00:00:06.065460   Object <integer> = 0x00000000b0806d68 (2 961 206 632)
00:00:06.065475 
00:00:06.065477 [/Devices/VMMDev/0/LUN#999/] (level 4)
00:00:06.065496   Driver <string>  = "MainStatus" (cb=11)
00:00:06.065506 
00:00:06.065508 [/Devices/VMMDev/0/LUN#999/Config/] (level 5) (restricted root)
00:00:06.065531   First   <integer> = 0x0000000000000000 (0)
00:00:06.065544   Last    <integer> = 0x0000000000000000 (0)
00:00:06.065558   papLeds <integer> = 0x000000000944c5b4 (155 502 004)
00:00:06.065571 
00:00:06.065574 [/Devices/acpi/] (level 2)
00:00:06.065588 
00:00:06.065590 [/Devices/acpi/0/] (level 3)
00:00:06.065607   PCIBusNo      <integer> = 0x0000000000000000 (0)
00:00:06.065623   PCIDeviceNo   <integer> = 0x0000000000000007 (7)
00:00:06.065636   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:06.065646   Trusted       <integer> = 0x0000000000000001 (1)
00:00:06.065662 
00:00:06.065664 [/Devices/acpi/0/Config/] (level 4) (restricted root)
00:00:06.065686   CpuHotPlug        <integer> = 0x0000000000000000 (0)
00:00:06.065703   FdcEnabled        <integer> = 0x0000000000000000 (0)
00:00:06.065720   HostBusPciAddress <integer> = 0x00000000001e0000 (1 966 080)
00:00:06.065733   HpetEnabled       <integer> = 0x0000000000000001 (1)
00:00:06.065749   IOAPIC            <integer> = 0x0000000000000001 (1)
00:00:06.065770   IocPciAddress     <integer> = 0x00000000001f0000 (2 031 616)
00:00:06.065787   McfgBase          <integer> = 0x00000000dc000000 (3 690 987 520)
00:00:06.065810   McfgLength        <integer> = 0x0000000004000000 (67 108 864)
00:00:06.065833   NumCPUs           <integer> = 0x0000000000000001 (1)
00:00:06.065854   RamHoleSize       <integer> = 0x0000000024000000 (603 979 776, 576 MB)
00:00:06.065878   RamSize           <integer> = 0x0000000040000000 (1 073 741 824, 1 024 MB)
00:00:06.065906   Serial0IoPortBase <integer> = 0x0000000000000000 (0)
00:00:06.065917   Serial0Irq        <integer> = 0x0000000000000000 (0)
00:00:06.065934   Serial1IoPortBase <integer> = 0x0000000000000000 (0)
00:00:06.065945   Serial1Irq        <integer> = 0x0000000000000000 (0)
00:00:06.065962   ShowCpu           <integer> = 0x0000000000000001 (1)
00:00:06.065981   ShowRtc           <integer> = 0x0000000000000001 (1)
00:00:06.066001   SmcEnabled        <integer> = 0x0000000000000000 (0)
00:00:06.066018 
00:00:06.066021 [/Devices/acpi/0/LUN#0/] (level 4)
00:00:06.066040   Driver <string>  = "ACPIHost" (cb=9)
00:00:06.066053 
00:00:06.066055 [/Devices/acpi/0/LUN#0/Config/] (level 5) (restricted root)
00:00:06.066079 
00:00:06.066081 [/Devices/apic/] (level 2)
00:00:06.066095 
00:00:06.066097 [/Devices/apic/0/] (level 3)
00:00:06.066114   Trusted <integer> = 0x0000000000000001 (1)
00:00:06.066125 
00:00:06.066127 [/Devices/apic/0/Config/] (level 4) (restricted root)
00:00:06.066147   IOAPIC  <integer> = 0x0000000000000001 (1)
00:00:06.066159   NumCPUs <integer> = 0x0000000000000001 (1)
00:00:06.066169 
00:00:06.066172 [/Devices/e1000/] (level 2)
00:00:06.066186 
00:00:06.066188 [/Devices/hpet/] (level 2)
00:00:06.066202 
00:00:06.066204 [/Devices/hpet/0/] (level 3)
00:00:06.066221   Trusted <integer> = 0x0000000000000001 (1)
00:00:06.066232 
00:00:06.066234 [/Devices/hpet/0/Config/] (level 4) (restricted root)
00:00:06.066255   ICH9 <integer> = 0x0000000000000001 (1)
00:00:06.066265 
00:00:06.066267 [/Devices/i8254/] (level 2)
00:00:06.066282 
00:00:06.066284 [/Devices/i8254/0/] (level 3)
00:00:06.066300 
00:00:06.066302 [/Devices/i8254/0/Config/] (level 4) (restricted root)
00:00:06.066322 
00:00:06.066325 [/Devices/i8259/] (level 2)
00:00:06.066339 
00:00:06.066341 [/Devices/i8259/0/] (level 3)
00:00:06.066357   Trusted <integer> = 0x0000000000000001 (1)
00:00:06.066368 
00:00:06.066370 [/Devices/i8259/0/Config/] (level 4) (restricted root)
00:00:06.066390 
00:00:06.066393 [/Devices/ich9pci/] (level 2)
00:00:06.066407 
00:00:06.066409 [/Devices/ich9pci/0/] (level 3)
00:00:06.066425   Trusted <integer> = 0x0000000000000001 (1)
00:00:06.066436 
00:00:06.066438 [/Devices/ich9pci/0/Config/] (level 4) (restricted root)
00:00:06.066458   IOAPIC     <integer> = 0x0000000000000001 (1)
00:00:06.066473   McfgBase   <integer> = 0x00000000dc000000 (3 690 987 520)
00:00:06.066489   McfgLength <integer> = 0x0000000004000000 (67 108 864)
00:00:06.066503 
00:00:06.066505 [/Devices/ich9pcibridge/] (level 2)
00:00:06.066519 
00:00:06.066522 [/Devices/ich9pcibridge/0/] (level 3)
00:00:06.066539   PCIBusNo      <integer> = 0x0000000000000000 (0)
00:00:06.066554   PCIDeviceNo   <integer> = 0x0000000000000018 (24)
00:00:06.066567   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:06.066578   Trusted       <integer> = 0x0000000000000001 (1)
00:00:06.066594 
00:00:06.066596 [/Devices/ich9pcibridge/0/Config/] (level 4) (restricted root)
00:00:06.066617 
00:00:06.066619 [/Devices/ich9pcibridge/1/] (level 3)
00:00:06.066635   PCIBusNo      <integer> = 0x0000000000000000 (0)
00:00:06.066651   PCIDeviceNo   <integer> = 0x0000000000000019 (25)
00:00:06.066664   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:06.066674   Trusted       <integer> = 0x0000000000000001 (1)
00:00:06.066690 
00:00:06.066693 [/Devices/ich9pcibridge/1/Config/] (level 4) (restricted root)
00:00:06.066714 
00:00:06.066716 [/Devices/ichac97/] (level 2)
00:00:06.066730 
00:00:06.066732 [/Devices/ichac97/0/] (level 3)
00:00:06.066749   PCIBusNo      <integer> = 0x0000000000000000 (0)
00:00:06.066764   PCIDeviceNo   <integer> = 0x0000000000000005 (5)
00:00:06.066777   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:06.066787   Trusted       <integer> = 0x0000000000000001 (1)
00:00:06.066803 
00:00:06.066805 [/Devices/ichac97/0/Config/] (level 4) (restricted root)
00:00:06.066830 
00:00:06.066832 [/Devices/ichac97/0/LUN#0/] (level 4)
00:00:06.066851   Driver <string>  = "AUDIO" (cb=6)
00:00:06.066863 
00:00:06.066865 [/Devices/ichac97/0/LUN#0/Config/] (level 5) (restricted root)
00:00:06.066889   AudioDriver <string>  = "pulse" (cb=6)
00:00:06.066898   StreamName  <string>  = "test" (cb=5)
00:00:06.066909 
00:00:06.066912 [/Devices/ioapic/] (level 2)
00:00:06.066926 
00:00:06.066928 [/Devices/ioapic/0/] (level 3)
00:00:06.066945   Trusted <integer> = 0x0000000000000001 (1)
00:00:06.066956 
00:00:06.066958 [/Devices/ioapic/0/Config/] (level 4) (restricted root)
00:00:06.066978   NumCPUs <integer> = 0x0000000000000001 (1)
00:00:06.066989 
00:00:06.066992 [/Devices/lpc/] (level 2)
00:00:06.067006 
00:00:06.067008 [/Devices/lpc/0/] (level 3)
00:00:06.067024   PCIBusNo      <integer> = 0x0000000000000000 (0)
00:00:06.067040   PCIDeviceNo   <integer> = 0x000000000000001f (31)
00:00:06.067053   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:06.067064   Trusted       <integer> = 0x0000000000000001 (1)
00:00:06.067080 
00:00:06.067082 [/Devices/lpc/0/Config/] (level 4) (restricted root)
00:00:06.067103 
00:00:06.067105 [/Devices/mc146818/] (level 2)
00:00:06.067119 
00:00:06.067121 [/Devices/mc146818/0/] (level 3)
00:00:06.067137 
00:00:06.067140 [/Devices/mc146818/0/Config/] (level 4) (restricted root)
00:00:06.067160   UseUTC <integer> = 0x0000000000000000 (0)
00:00:06.067171 
00:00:06.067173 [/Devices/parallel/] (level 2)
00:00:06.067187 
00:00:06.067189 [/Devices/pcarch/] (level 2)
00:00:06.067203 
00:00:06.067206 [/Devices/pcarch/0/] (level 3)
00:00:06.067266   Trusted <integer> = 0x0000000000000001 (1)
00:00:06.067277 
00:00:06.067279 [/Devices/pcarch/0/Config/] (level 4) (restricted root)
00:00:06.067300 
00:00:06.067302 [/Devices/pcbios/] (level 2)
00:00:06.067316 
00:00:06.067318 [/Devices/pcbios/0/] (level 3)
00:00:06.067335   Trusted <integer> = 0x0000000000000001 (1)
00:00:06.067346 
00:00:06.067348 [/Devices/pcbios/0/Config/] (level 4) (restricted root)
00:00:06.067369   BootDevice0    <string>  = "DVD" (cb=4)
00:00:06.067382   BootDevice1    <string>  = "IDE" (cb=4)
00:00:06.067394   BootDevice2    <string>  = "NONE" (cb=5)
00:00:06.067407   BootDevice3    <string>  = "NONE" (cb=5)
00:00:06.067420   FloppyDevice   <string>  = "i82078" (cb=7)
00:00:06.067431   HardDiskDevice <string>  = "piix3ide" (cb=9)
00:00:06.067441   IOAPIC         <integer> = 0x0000000000000001 (1)
00:00:06.067459   McfgBase       <integer> = 0x00000000dc000000 (3 690 987 520)
00:00:06.067479   McfgLength     <integer> = 0x0000000004000000 (67 108 864)
00:00:06.067496   NumCPUs        <integer> = 0x0000000000000001 (1)
00:00:06.067513   PXEDebug       <integer> = 0x0000000000000000 (0)
00:00:06.067530   RamHoleSize    <integer> = 0x0000000024000000 (603 979 776, 576 MB)
00:00:06.067551   RamSize        <integer> = 0x0000000040000000 (1 073 741 824, 1 024 MB)
00:00:06.067577   UUID           <bytes>   = "00 96 13 0d 02 b9 d3 41 ba 1e 61 b2 25 97 43 cc" (cb=16)
00:00:06.067632 
00:00:06.067634 [/Devices/pcbios/0/Config/NetBoot/] (level 5)
00:00:06.067656 
00:00:06.067658 [/Devices/pckbd/] (level 2)
00:00:06.067672 
00:00:06.067674 [/Devices/pckbd/0/] (level 3)
00:00:06.067691   Trusted <integer> = 0x0000000000000001 (1)
00:00:06.067702 
00:00:06.067704 [/Devices/pckbd/0/Config/] (level 4) (restricted root)
00:00:06.067725 
00:00:06.067727 [/Devices/pckbd/0/LUN#0/] (level 4)
00:00:06.067746   Driver <string>  = "KeyboardQueue" (cb=14)
00:00:06.067756 
00:00:06.067758 [/Devices/pckbd/0/LUN#0/AttachedDriver/] (level 5)
00:00:06.067780   Driver <string>  = "MainKeyboard" (cb=13)
00:00:06.067789 
00:00:06.067792 [/Devices/pckbd/0/LUN#0/AttachedDriver/Config/] (level 6) (restricted root)
00:00:06.067817   Object <integer> = 0x000000000944cdd8 (155 504 088)
00:00:06.067832 
00:00:06.067834 [/Devices/pckbd/0/LUN#0/Config/] (level 5) (restricted root)
00:00:06.067857   QueueSize <integer> = 0x0000000000000040 (64)
00:00:06.067868 
00:00:06.067870 [/Devices/pckbd/0/LUN#1/] (level 4)
00:00:06.067889   Driver <string>  = "MouseQueue" (cb=11)
00:00:06.067909 
00:00:06.067911 [/Devices/pckbd/0/LUN#1/AttachedDriver/] (level 5)
00:00:06.067933   Driver <string>  = "MainMouse" (cb=10)
00:00:06.067943 
00:00:06.067945 [/Devices/pckbd/0/LUN#1/AttachedDriver/Config/] (level 6) (restricted root)
00:00:06.067971   Object <integer> = 0x0000000009517848 (156 334 152)
00:00:06.067985 
00:00:06.067987 [/Devices/pckbd/0/LUN#1/Config/] (level 5) (restricted root)
00:00:06.068010   QueueSize <integer> = 0x0000000000000080 (128)
00:00:06.068021 
00:00:06.068023 [/Devices/pcnet/] (level 2)
00:00:06.068038 
00:00:06.068040 [/Devices/piix3ide/] (level 2)
00:00:06.068054 
00:00:06.068056 [/Devices/piix3ide/0/] (level 3)
00:00:06.068073   PCIBusNo      <integer> = 0x0000000000000000 (0)
00:00:06.068089   PCIDeviceNo   <integer> = 0x000000000000001f (31)
00:00:06.068102   PCIFunctionNo <integer> = 0x0000000000000001 (1)
00:00:06.068113   Trusted       <integer> = 0x0000000000000001 (1)
00:00:06.068129 
00:00:06.068131 [/Devices/piix3ide/0/Config/] (level 4) (restricted root)
00:00:06.068152   Type <string>  = "PIIX4" (cb=6)
00:00:06.068162 
00:00:06.068164 [/Devices/piix3ide/0/Config/PrimaryMaster/] (level 5)
00:00:06.068186   NonRotationalMedium <integer> = 0x0000000000000000 (0)
00:00:06.068197 
00:00:06.068199 [/Devices/piix3ide/0/Config/SecondaryMaster/] (level 5)
00:00:06.068221   NonRotationalMedium <integer> = 0x0000000000000000 (0)
00:00:06.068232 
00:00:06.068234 [/Devices/piix3ide/0/LUN#0/] (level 4)
00:00:06.068254   Driver <string>  = "Block" (cb=6)
00:00:06.068263 
00:00:06.068265 [/Devices/piix3ide/0/LUN#0/AttachedDriver/] (level 5)
00:00:06.068287   Driver <string>  = "VD" (cb=3)
00:00:06.068297 
00:00:06.068299 [/Devices/piix3ide/0/LUN#0/AttachedDriver/Config/] (level 6) (restricted root)
00:00:06.068325   Format <string>  = "VMDK" (cb=5)
00:00:06.068335   Path   <string>  = "/home/nima/.VirtualBox/winxp.vmdk" (cb=34)
00:00:06.068347   Type   <string>  = "HardDisk" (cb=9)
00:00:06.068359 
00:00:06.068361 [/Devices/piix3ide/0/LUN#0/Config/] (level 5) (restricted root)
00:00:06.068384   Mountable <integer> = 0x0000000000000000 (0)
00:00:06.068467   Type      <string>  = "HardDisk" (cb=9)
00:00:06.068483 
00:00:06.068485 [/Devices/piix3ide/0/LUN#2/] (level 4)
00:00:06.068504   Driver <string>  = "Block" (cb=6)
00:00:06.068514 
00:00:06.068516 [/Devices/piix3ide/0/LUN#2/Config/] (level 5) (restricted root)
00:00:06.068540   Mountable <integer> = 0x0000000000000001 (1)
00:00:06.068551   Type      <string>  = "DVD" (cb=4)
00:00:06.068565 
00:00:06.068567 [/Devices/piix3ide/0/LUN#999/] (level 4)
00:00:06.068587   Driver <string>  = "MainStatus" (cb=11)
00:00:06.068596 
00:00:06.068598 [/Devices/piix3ide/0/LUN#999/Config/] (level 5) (restricted root)
00:00:06.068622   DeviceInstance        <string>  = "piix3ide/0" (cb=11)
00:00:06.068638   First                 <integer> = 0x0000000000000000 (0)
00:00:06.068664   Last                  <integer> = 0x0000000000000003 (3)
00:00:06.068690   pConsole              <integer> = 0x000000000944c248 (155 501 128)
00:00:06.068716   papLeds               <integer> = 0x000000000944c43c (155 501 628)
00:00:06.068743   pmapMediumAttachments <integer> = 0x000000000944c5c0 (155 502 016)
00:00:06.068757 
00:00:06.068759 [/Devices/serial/] (level 2)
00:00:06.068773 
00:00:06.068776 [/Devices/usb-ohci/] (level 2)
00:00:06.068790 
00:00:06.068792 [/Devices/usb-ohci/0/] (level 3)
00:00:06.068809   PCIBusNo      <integer> = 0x0000000000000000 (0)
00:00:06.068824   PCIDeviceNo   <integer> = 0x000000000000001f (31)
00:00:06.068837   PCIFunctionNo <integer> = 0x0000000000000004 (4)
00:00:06.068848   Trusted       <integer> = 0x0000000000000001 (1)
00:00:06.068864 
00:00:06.068866 [/Devices/usb-ohci/0/Config/] (level 4) (restricted root)
00:00:06.068887 
00:00:06.068890 [/Devices/usb-ohci/0/LUN#0/] (level 4)
00:00:06.068909   Driver <string>  = "VUSBRootHub" (cb=12)
00:00:06.068918 
00:00:06.068920 [/Devices/usb-ohci/0/LUN#0/Config/] (level 5) (restricted root)
00:00:06.068943 
00:00:06.068946 [/Devices/usb-ohci/0/LUN#999/] (level 4)
00:00:06.068965   Driver <string>  = "MainStatus" (cb=11)
00:00:06.068974 
00:00:06.068976 [/Devices/usb-ohci/0/LUN#999/Config/] (level 5) (restricted root)
00:00:06.069000   First   <integer> = 0x0000000000000000 (0)
00:00:06.069012   Last    <integer> = 0x0000000000000000 (0)
00:00:06.069026   papLeds <integer> = 0x000000000944c5b8 (155 502 008)
00:00:06.069040 
00:00:06.069042 [/Devices/vga/] (level 2)
00:00:06.069056 
00:00:06.069058 [/Devices/vga/0/] (level 3)
00:00:06.069075   PCIBusNo      <integer> = 0x0000000000000000 (0)
00:00:06.069091   PCIDeviceNo   <integer> = 0x0000000000000002 (2)
00:00:06.069103   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:06.069114   Trusted       <integer> = 0x0000000000000001 (1)
00:00:06.069130 
00:00:06.069132 [/Devices/vga/0/Config/] (level 4) (restricted root)
00:00:06.069153   CustomVideoModes <integer> = 0x0000000000000000 (0)
00:00:06.069164   FadeIn           <integer> = 0x0000000000000001 (1)
00:00:06.069184   FadeOut          <integer> = 0x0000000000000001 (1)
00:00:06.069202   HeightReduction  <integer> = 0x0000000000000000 (0)
00:00:06.069214   LogoFile         <string>  = "" (cb=1)
00:00:06.069230   LogoTime         <integer> = 0x0000000000000000 (0)
00:00:06.069248   MonitorCount     <integer> = 0x0000000000000001 (1)
00:00:06.069262   ShowBootMenu     <integer> = 0x0000000000000002 (2)
00:00:06.069276   VRamSize         <integer> = 0x0000000002000000 (33 554 432, 32 MB)
00:00:06.069302 
00:00:06.069304 [/Devices/vga/0/LUN#0/] (level 4)
00:00:06.069323   Driver <string>  = "MainDisplay" (cb=12)
00:00:06.069333 
00:00:06.069336 [/Devices/vga/0/LUN#0/Config/] (level 5) (restricted root)
00:00:06.069359   Object <integer> = 0x0000000009517cf8 (156 335 352)
00:00:06.069373 
00:00:06.069375 [/Devices/virtio-net/] (level 2)
00:00:06.069389 
00:00:06.069391 [/HWVirtExt/] (level 1)
00:00:06.069403   EnableLargePages   <integer> = 0x0000000000000000 (0)
00:00:06.069416   EnableNestedPaging <integer> = 0x0000000000000001 (1)
00:00:06.069427   EnableVPID         <integer> = 0x0000000000000001 (1)
00:00:06.069444   Exclusive          <integer> = 0x0000000000000001 (1)
00:00:06.069463 
00:00:06.069466 [/MM/] (level 1)
00:00:06.069477   CanUseLargerHeap <integer> = 0x0000000000000001 (1)
00:00:06.069488 
00:00:06.069490 [/PDM/] (level 1)
00:00:06.069502 
00:00:06.069504 [/PDM/AsyncCompletion/] (level 2)
00:00:06.069518 
00:00:06.069520 [/PDM/AsyncCompletion/File/] (level 3)
00:00:06.069537 
00:00:06.069539 [/PDM/AsyncCompletion/File/BwGroups/] (level 4)
00:00:06.069558 
00:00:06.069561 [/PDM/BlkCache/] (level 2)
00:00:06.069575   CacheSize <integer> = 0x0000000000500000 (5 242 880, 5 MB)
00:00:06.069592 
00:00:06.069595 [/PDM/Devices/] (level 2)
00:00:06.069609 
00:00:06.069611 [/PDM/Drivers/] (level 2)
00:00:06.069625 
00:00:06.069627 [/PDM/Drivers/VBoxC/] (level 3)
00:00:06.069643   Path <string>  = "/usr/lib/virtualbox/components/VBoxC" (cb=37)
00:00:06.069653 
00:00:06.069656 [/PDM/NetworkShaper/] (level 2)
00:00:06.069670 
00:00:06.069672 [/PDM/NetworkShaper/BwGroups/] (level 3)
00:00:06.069689 
00:00:06.069691 [/TM/] (level 1)
00:00:06.069702   UTCOffset <integer> = 0x0000000000000000 (0)
00:00:06.069713 
00:00:06.069715 [/USB/] (level 1)
00:00:06.069726 
00:00:06.069729 [/USB/HidMouse/] (level 2)
00:00:06.069742 
00:00:06.069745 [/USB/HidMouse/0/] (level 3)
00:00:06.069761 
00:00:06.069763 [/USB/HidMouse/0/Config/] (level 4) (restricted root)
00:00:06.069783   Absolute <integer> = 0x0000000000000001 (1)
00:00:06.069794 
00:00:06.069796 [/USB/HidMouse/0/LUN#0/] (level 4)
00:00:06.069816   Driver <string>  = "MouseQueue" (cb=11)
00:00:06.069825 
00:00:06.069828 [/USB/HidMouse/0/LUN#0/AttachedDriver/] (level 5)
00:00:06.069849   Driver <string>  = "MainMouse" (cb=10)
00:00:06.069859 
00:00:06.069861 [/USB/HidMouse/0/LUN#0/AttachedDriver/Config/] (level 6) (restricted root)
00:00:06.069887   Object <integer> = 0x0000000009517848 (156 334 152)
00:00:06.069901 
00:00:06.069903 [/USB/HidMouse/0/LUN#0/Config/] (level 5) (restricted root)
00:00:06.069927   QueueSize <integer> = 0x0000000000000080 (128)
00:00:06.069938 
00:00:06.069940 [/USB/HidMouse/GlobalConfig/] (level 3) (restricted root)
00:00:06.069959 
00:00:06.069961 [/USB/USBProxy/] (level 2)
00:00:06.069975 
00:00:06.069977 [/USB/USBProxy/GlobalConfig/] (level 3)
00:00:06.069993 
00:00:06.069997 !!
00:00:06.069998 !! {clocks}
00:00:06.069999 !!
00:00:06.070007 Cpu Tick:         7348547128 (0x000001b601ee38) 1987427364Hz paused - virtualized - virtual clock
00:00:06.070031  Virtual:         3704543930 (0x000000dccedaba) 1000000000Hz paused
00:00:06.070052 VirtSync:         3697517334 (0x000000dc63a316) paused - catchup
00:00:06.070067           offset 5596157  catch-up rate 10 %
00:00:06.070080     Real:            1186798 (0x00000000121bee) 1000Hz
00:00:06.070096 !!
00:00:06.070097 !! {cmos1}
00:00:06.070098 !!
00:00:06.070103 First CMOS bank, offsets 0x0E - 0x7F
00:00:06.070104 Offset 00 : --- use 'info rtc' to show CMOS clock --- 00 00
00:00:06.070117 Offset 10 : 00 00 f0 00 0e 80 02 ff-ff 2f 00 00 00 00 00 04
00:00:06.070165 Offset 20 : ff ff ff ff ff 3f 00 00-00 00 00 00 00 00 08 eb
00:00:06.070212 Offset 30 : ff ff 20 00 00 3f 00 20-00 00 00 00 00 23 00 00
00:00:06.070259 Offset 40 : 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00
00:00:06.070306 Offset 50 : 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00
00:00:06.070353 Offset 60 : 01 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00
00:00:06.070400 Offset 70 : 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00
00:00:06.070447 !!
00:00:06.070448 !! {cmos2}
00:00:06.070449 !!
00:00:06.070454 Second CMOS bank, offsets 0x80 - 0xFF
00:00:06.070456 Offset 80 : 00 00 ff ff ff ff ff ff-ff ff 00 00 00 00 00 00
00:00:06.070504 Offset 90 : 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00
00:00:06.070551 Offset a0 : 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00
00:00:06.070597 Offset b0 : 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00
00:00:06.070644 Offset c0 : 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00
00:00:06.070691 Offset d0 : 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00
00:00:06.070738 Offset e0 : 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00
00:00:06.070784 Offset f0 : 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00
00:00:06.070834 !!
00:00:06.070835 !! {fflags}
00:00:06.070836 !!
00:00:06.070840 Global FFs: 0x0
00:00:06.070848 CPU 0 FFs: 0xfb0004
00:00:06.070855     TIMER, PGM_SYNC_CR3, PGM_SYNC_CR3_NON_GLOBAL, TLB_FLUSH, TRPM_SYNC_IDT, SELM_SYNC_TSS,
00:00:06.070874     SELM_SYNC_GDT, SELM_SYNC_LDT
00:00:06.070884   Groups:
00:00:06.070885     EXTERNAL_HALTED, HIGH_PRIORITY_PRE, HIGH_PRIORITY_PRE_RAW, HWACCM_TO_R3, ALL_REM
00:00:06.070904 !!
00:00:06.070904 !! {gdt}
00:00:06.070905 !!
00:00:06.070911 Shadow GDT (GCAddr=ff657000):
00:00:06.070944 ffd8 - 81980087 ff008900 - base=ff008198 limit=00000087 dpl=0 TSS32Avail Present 16-bit  HyperTSSTrap08
00:00:06.070952 ffe0 - 81100087 ff008b00 - base=ff008110 limit=00000087 dpl=0 TSS32Busy Present 16-bit  HyperTSS
00:00:06.070960 ffe8 - 0000ffff 00af9b00 - base=00000000 limit=ffffffff dpl=0 CodeER Accessed Present Page 16-bit  HyperCS64
00:00:06.070967 fff0 - 0000ffff 00cf9300 - base=00000000 limit=ffffffff dpl=0 DataRW Accessed Present Page 32-bit  HyperDS
00:00:06.070974 fff8 - 0000ffff 00cf9b00 - base=00000000 limit=ffffffff dpl=0 CodeER Accessed Present Page 32-bit  HyperCS
00:00:06.070980 !!
00:00:06.070981 !! {gdtguest}
00:00:06.070982 !!
00:00:06.070987 Guest GDT (GCAddr=00000000000fe898 limit=47):
00:00:06.071002 0010 - 0000ffff 00cf9b00 - base=00000000 limit=ffffffff dpl=0 CodeER Accessed Present Page 32-bit 
00:00:06.071009 0018 - 0000ffff 00cf9300 - base=00000000 limit=ffffffff dpl=0 DataRW Accessed Present Page 32-bit 
00:00:06.071016 0020 - 0000ffff 00009b0f - base=000f0000 limit=0000ffff dpl=0 CodeER Accessed Present 16-bit 
00:00:06.071022 0028 - 0000ffff 00009300 - base=00000000 limit=0000ffff dpl=0 DataRW Accessed Present 16-bit 
00:00:06.071029 0040 - 0400ffff 00009300 - base=00000400 limit=0000ffff dpl=0 DataRW Accessed Present 16-bit 
00:00:06.071034 !!
00:00:06.071035 !! {guestprops}
00:00:06.071036 !!
00:00:06.071042 /VirtualBox/HostInfo/GUI/LanguageID: 'de_DE', 1351333568068446000
00:00:06.071058 /VirtualBox/HostInfo/VBoxVerExt: '4.2.2', 1351333567812847000 (TRANSIENT, RDONLYGUEST)
00:00:06.071077 /VirtualBox/HostGuest/SysprepExec: '', 1351333567812411000 (TRANSIENT, RDONLYGUEST)
00:00:06.071095 /VirtualBox/HostGuest/SysprepArgs: '', 1351333567812465000 (TRANSIENT, RDONLYGUEST)
00:00:06.071113 /VirtualBox/HostInfo/VBoxRev: '81494', 1351333567812882000 (TRANSIENT, RDONLYGUEST)
00:00:06.071131 /VirtualBox/HostInfo/VBoxVer: '4.2.2', 1351333567812810000 (TRANSIENT, RDONLYGUEST)
00:00:06.071152 !!
00:00:06.071153 !! {hpet}
00:00:06.071154 !!
00:00:06.071159 HPET status:
00:00:06.071160  config=0000000000000000     isr=0000000000000000
00:00:06.071162  offset=0000000000000000 counter=0000000000000000 frequency=0429b17f
00:00:06.071164  legacy-mode=off  timer-count=3
00:00:06.071185 Timers:
00:00:06.071187  0: comparator=ffffffffffffffff period(hidden)=0000000000000000 cfg=ffffffff00000030
00:00:06.071210  1: comparator=00000000ffffffff period(hidden)=0000000000000000 cfg=ffffffff00000000
00:00:06.071230  2: comparator=00000000ffffffff period(hidden)=0000000000000000 cfg=ffffffff00000000
00:00:06.071249  3: comparator=00000000ffffffff period(hidden)=0000000000000000 cfg=ffffffff00000000
00:00:06.071270 !!
00:00:06.071270 !! {ioapic}
00:00:06.071271 !!
00:00:06.071276 I/O APIC at fec00000:
00:00:06.071282   IOAPICID  : 01000000
00:00:06.071288     APIC ID = 01
00:00:06.071293   IOAPICVER : 00170011
00:00:06.071298     version = 11
00:00:06.071303     redirs  = 24
00:00:06.071308   IOAPICARB : 00000000
00:00:06.071313     arb ID  = 00
00:00:06.071317 I/O redirection table
00:00:06.071320  idx dst_mode dst_addr mask trigger rirr polarity dlvr_st dlvr_mode vector
00:00:06.071323   00   phys      00     1    edge    0   activehi  idle     Fixed      0 (0000000000010000)
00:00:06.071354   01   phys      00     1    edge    0   activehi  idle     Fixed      0 (0000000000010000)
00:00:06.071384   02   phys      00     1    edge    0   activehi  idle     Fixed      0 (0000000000010000)
00:00:06.071414   03   phys      00     1    edge    0   activehi  idle     Fixed      0 (0000000000010000)
00:00:06.071443   04   phys      00     1    edge    0   activehi  idle     Fixed      0 (0000000000010000)
00:00:06.071473   05   phys      00     1    edge    0   activehi  idle     Fixed      0 (0000000000010000)
00:00:06.071502   06   phys      00     1    edge    0   activehi  idle     Fixed      0 (0000000000010000)
00:00:06.071532   07   phys      00     1    edge    0   activehi  idle     Fixed      0 (0000000000010000)
00:00:06.071561   08   phys      00     1    edge    0   activehi  idle     Fixed      0 (0000000000010000)
00:00:06.071591   09   phys      00     1    edge    0   activehi  idle     Fixed      0 (0000000000010000)
00:00:06.071620   10   phys      00     1    edge    0   activehi  idle     Fixed      0 (0000000000010000)
00:00:06.071650   11   phys      00     1    edge    0   activehi  idle     Fixed      0 (0000000000010000)
00:00:06.071679   12   phys      00     1    edge    0   activehi  idle     Fixed      0 (0000000000010000)
00:00:06.071709   13   phys      00     1    edge    0   activehi  idle     Fixed      0 (0000000000010000)
00:00:06.071738   14   phys      00     1    edge    0   activehi  idle     Fixed      0 (0000000000010000)
00:00:06.071767   15   phys      00     1    edge    0   activehi  idle     Fixed      0 (0000000000010000)
00:00:06.071796   16   phys      00     1    edge    0   activehi  idle     Fixed      0 (0000000000010000)
00:00:06.071826   17   phys      00     1    edge    0   activehi  idle     Fixed      0 (0000000000010000)
00:00:06.071881   18   phys      00     1    edge    0   activehi  idle     Fixed      0 (0000000000010000)
00:00:06.071911   19   phys      00     1    edge    0   activehi  idle     Fixed      0 (0000000000010000)
00:00:06.071940   20   phys      00     1    edge    0   activehi  idle     Fixed      0 (0000000000010000)
00:00:06.071970   21   phys      00     1    edge    0   activehi  idle     Fixed      0 (0000000000010000)
00:00:06.071999   22   phys      00     1    edge    0   activehi  idle     Fixed      0 (0000000000010000)
00:00:06.072029   23   phys      00     1    edge    0   activehi  idle     Fixed      0 (0000000000010000)
00:00:06.072059 !!
00:00:06.072060 !! {ioport}
00:00:06.072061 !!
00:00:06.072066 I/O Port R3 ranges (pVM=a92dc000)
00:00:06.072067 Range     pDevIns  In       Out      pvUser   Description
00:00:06.072084 0000-0007 a79da750 a73e4c40 a73e5620 a79da818 DMA8 Address
00:00:06.072104 0008-000f a79da750 a73e4cc0 a73e5700 a79da818 DMA8 Control
00:00:06.072124 0020-0021 a8f1ace0 a73b9670 a73b97e0 00000000 i8259 PIC #0
00:00:06.072144 0040-0043 a8f1ba60 a73b7b50 a73b8d30 00000000 i8254 Programmable Interval Timer
00:00:06.072163 0060-0060 a8f19750 a7392760 a7392840 00000000 PC Keyboard - Data
00:00:06.072182 0061-0061 a8f1ba60 a73b8380 a73b8bc0 00000000 PC Speaker
00:00:06.072201 0064-0064 a8f19750 a73914a0 a7392430 00000000 PC Keyboard - Command / Status
00:00:06.072221 0070-0073 a8f1be90 a73c01c0 a73c0ec0 00000000 MC146818 RTC/CMOS
00:00:06.072240 0080-0087 a79da750 a73e4db0 a73e5830 a79da818 DMA8 Page
00:00:06.072259 0088-008f a79da750 a73e4db0 a73e5830 a79da884 DMA16 Page
00:00:06.072279 0092-0092 a794aa10 a73c7650 a73c7680 00000000 PS/2 system control port A (A20 and more)
00:00:06.072298 00a0-00a1 a8f1ace0 a73b9670 a73b97e0 00000001 i8259 PIC #1
00:00:06.072317 00c0-00cf a79da750 a73e4c40 a73e5620 a79da884 DMA16 Address
00:00:06.072337 00d0-00df a79da750 a73e4cc0 a73e5700 a79da884 DMA16 Control
00:00:06.072356 00f0-00ff a794aa10 a73c7520 a73c7610 00000000 Math Co-Processor (DOS/OS2 mode)
00:00:06.072376 0170-0177 a8f23b10 a73af670 a73b6480 00000001 ATA I/O Base 1
00:00:06.072395 01ce-01ce a6bd1000 a73a4a90 a73a4b50 00000000 VGA/VBE - Index
00:00:06.072414 01cf-01cf a6bd1000 a73a6260 a73aaa20 00000000 VGA/VBE - Data
00:00:06.072433 01f0-01f7 a8f23b10 a73af670 a73b6480 00000000 ATA I/O Base 1
00:00:06.072452 0376-0376 a8f23b10 a73ac8e0 a73afc80 00000001 ATA I/O Base 2
00:00:06.072472 03b0-03b3 a6bd1000 a73a5f10 a73a5fb0 00000000 VGA - 3b0 (HGSMI host)
00:00:06.072491 03b4-03b5 a6bd1000 a73a52a0 a73a7b00 00000000 VGA - 3b4
00:00:06.072510 03b6-03b6 a6bd1000 a73a48e0 a73a49b0 00000000 VBE BIOS Extra Data
00:00:06.072529 03b7-03b7 a6bd1000 a73a2630 a73a4a10 00000000 VGA BIOS debug/panic
00:00:06.072549 03b8-03b8 a6bd1000 a73a2b30 a73a6350 00000000 BIOS Logo
00:00:06.072568 03ba-03ba a6bd1000 a73a52a0 a73a7b00 00000000 VGA - 3ba
00:00:06.072587 03c0-03cf a6bd1000 a73a52a0 a73a7b00 00000000 VGA - 3c0
00:00:06.072606 03d0-03d3 a6bd1000 a73a5f10 a73a5fb0 00000000 VGA - 3d0 (HGSMI guest)
00:00:06.072706 03d4-03d5 a6bd1000 a73a52a0 a73a7b00 00000000 VGA - 3d4
00:00:06.072725 03da-03da a6bd1000 a73a52a0 a73a7b00 00000000 VGA - 3da
00:00:06.072744 03f6-03f6 a8f23b10 a73ac8e0 a73afc80 00000000 ATA I/O Base 2
00:00:06.072764 0400-0403 a794ad18 a73c16e0 a73c26f0 00000000 Bochs PC BIOS - Panic & Debug
00:00:06.072783 04d0-04d0 a8f1ace0 a73b9420 a73b94a0 a8f1ada0 i8259 PIC #0 - elcr
00:00:06.072803 04d1-04d1 a8f1ace0 a73b9420 a73b94a0 a8f1ade0 i8259 PIC #1 - elcr
00:00:06.072823 0504-0504 a8f1c4f0 b5c7dab0 a73c8e50 00000000 VMMDev backdoor logging
00:00:06.072842 0505-0505 a8f1c4f0 a73c7770 a73c85c0 00000000 VMMDev timesync backdoor
00:00:06.072861 0cf8-0cf8 a8ed7d20 a739ba90 a739ba40 00000000 ICH9 (PCI)
00:00:06.072880 0cfc-0cff a8ed7d20 a739bd30 a739c090 00000000 ICH9 (PCI)
00:00:06.072900 4000-4000 a8f25dc0 a73bad40 a73bbe90 a8f25e80 ACPI PM1a Status
00:00:06.072920 4002-4002 a8f25dc0 a73bada0 a73bbf20 a8f25e80 ACPI PM1a Enable
00:00:06.072940 4004-4004 a8f25dc0 a73bace0 a73bb8b0 a8f25e80 ACPI PM1a Control
00:00:06.072960 4008-4008 a8f25dc0 a73bb320 b5c7d300 a8f25e80 ACPI PM Timer
00:00:06.072980 4020-4020 a8f25dc0 a73bac20 a73bede0 a8f25e80 ACPI GPE0 Status
00:00:06.073000 4021-4021 a8f25dc0 a73bac80 a73bee40 a8f25e80 ACPI GPE0 Enable
00:00:06.073020 4040-4040 a8f25dc0 b5c7dab0 a73bb5e0 a8f25e80 ACPI Battery status index
00:00:06.073040 4044-4044 a8f25dc0 a73bb0c0 b5c7d300 a8f25e80 ACPI Battery status data
00:00:06.073060 4048-4048 a8f25dc0 b5c7dab0 a73bb530 a8f25e80 ACPI system info index
00:00:06.073080 404c-404c a8f25dc0 a73bae00 a73bbbf0 a8f25e80 ACPI system info data
00:00:06.073100 4050-4050 a8f25dc0 b5c7dab0 a73bbb70 a8f25e80 ACPI Reset
00:00:06.073120 442e-442e a8f25dc0 b5c7dab0 a73bb660 a8f25e80 ACPI SMI
00:00:06.073139 8900-8900 a794ad18 a73c16e0 a73c26f0 00000000 Bochs PC BIOS - Shutdown
00:00:06.073159 d000-d000 a8f1c4f0 b5c7dab0 a73c9fb0 a8f1c5b0 VMMDev Request Handler
00:00:06.073179 d100-d1ff a79e6900 a73db310 a73db0a0 a79e69c0 ICHAC97 NAM
00:00:06.073199 d200-d23f a79e6900 a73d9210 a73d9a60 a79e69c0 ICHAC97 NABM
00:00:06.073219 e000-e007 a8f23b10 a73ac9a0 a73afae0 00000000 ATA Bus Master DMA
00:00:06.073238 e008-e00f a8f23b10 a73ac9a0 a73afae0 00000001 ATA Bus Master DMA
00:00:06.073258 I/O Port R0 ranges (pVM=a92dc000)
00:00:06.073259 Range     pDevIns  In       Out      pvUser   Description
00:00:06.073275 0020-0021 a8f1ace0 f9b90f90 f9b91100 00000000 i8259 PIC #0
00:00:06.073294 0040-0043 a8f1ba60 f9b90620 f9b907d0 00000000 i8254 Programmable Interval Timer
00:00:06.073313 0060-0060 a8f19750 f9b8ed40 f9b8ee10 00000000 PC Keyboard - Data
00:00:06.073332 0064-0064 a8f19750 f9b8fa40 f9b8fab0 00000000 PC Keyboard - Command / Status
00:00:06.073352 0070-0073 a8f1be90 f9b916d0 f9b917d0 00000000 MC146818 RTC/CMOS
00:00:06.073371 00a0-00a1 a8f1ace0 f9b90f90 f9b91100 00000001 i8259 PIC #1
00:00:06.073390 0170-0177 a8f23b10 f9b93360 f9b93010 00000001 ATA I/O Base 1
00:00:06.073409 01ce-01ce a6bd1000 f9b8d8e0 f9b8d730 00000000 VGA/VBE - Index (GC)
00:00:06.073428 01cf-01cf a6bd1000 f9b8d7f0 f9b8d630 00000000 VGA/VBE - Data (GC)
00:00:06.073448 01f0-01f7 a8f23b10 f9b93360 f9b93010 00000000 ATA I/O Base 1
00:00:06.073467 0376-0376 a8f23b10 f9b93840 f9b936f0 00000001 ATA I/O Base 2
00:00:06.073486 03b4-03b5 a6bd1000 f9b8d580 f9b8d4e0 00000000 VGA - 3b4 (GC)
00:00:06.073505 03b7-03b7 a6bd1000 f9b8e8b0 f9b8e8c0 00000000 VGA BIOS debug/panic
00:00:06.073525 03ba-03ba a6bd1000 f9b8d580 f9b8d4e0 00000000 VGA - 3ba (GC)
00:00:06.073544 03c0-03cf a6bd1000 f9b8d580 f9b8d4e0 00000000 VGA - 3c0 (GC)
00:00:06.073563 03d4-03d5 a6bd1000 f9b8d580 f9b8d4e0 00000000 VGA - 3d4 (GC)
00:00:06.073582 03da-03da a6bd1000 f9b8d580 f9b8d4e0 00000000 VGA - 3da (GC)
00:00:06.073601 03f6-03f6 a8f23b10 f9b93840 f9b936f0 00000000 ATA I/O Base 2
00:00:06.073620 04d0-04d0 a8f1ace0 f9b914b0 f9b91530 a8f1ada0 i8259 PIC #0 - elcr
00:00:06.073640 04d1-04d1 a8f1ace0 f9b914b0 f9b91530 a8f1ade0 i8259 PIC #1 - elcr
00:00:06.073660 0cf8-0cf8 a8ed7d20 f9b8b9b0 f9b8b960 00000000 ICH9 (PCI)
00:00:06.073679 0cfc-0cff a8ed7d20 f9b8bac0 f9b8ba20 00000000 ICH9 (PCI)
00:00:06.073698 4008-4008 a8f25dc0 f9b90200 00000000 00000000 ACPI PM Timer
00:00:06.073717 e000-e007 a8f23b10 f9b92df0 f9b92ee0 00000000 ATA Bus Master DMA
00:00:06.073737 e008-e00f a8f23b10 f9b92df0 f9b92ee0 00000001 ATA Bus Master DMA
00:00:06.073756 I/O Port GC ranges (pVM=a92dc000)
00:00:06.073758 Range     pDevIns  In       Out      pvUser   Description
00:00:06.073773 0020-0021 ff072ce0 ff8f4d20 ff8f4e90 00000000 i8259 PIC #0
00:00:06.073794 0040-0043 ff073a60 ff8f43b0 ff8f4560 00000000 i8254 Programmable Interval Timer
00:00:06.073814 0060-0060 ff071750 ff8f2ad0 ff8f2ba0 00000000 PC Keyboard - Data
00:00:06.073834 0061-0061 ff073a60 ff8f47e0 00000000 00000000 PC Speaker
00:00:06.073853 0064-0064 ff071750 ff8f37d0 ff8f3840 00000000 PC Keyboard - Command / Status
00:00:06.073873 0070-0073 ff073e90 ff8f5460 ff8f5560 00000000 MC146818 RTC/CMOS
00:00:06.073893 00a0-00a1 ff072ce0 ff8f4d20 ff8f4e90 00000001 i8259 PIC #1
00:00:06.073913 0170-0177 ff07bb10 ff8f70f0 ff8f6da0 00000001 ATA I/O Base 1
00:00:06.073933 01ce-01ce ff911000 ff8f1620 ff8f1470 00000000 VGA/VBE - Index (GC)
00:00:06.073953 01cf-01cf ff911000 ff8f1530 ff8f1370 00000000 VGA/VBE - Data (GC)
00:00:06.073973 01f0-01f7 ff07bb10 ff8f70f0 ff8f6da0 00000000 ATA I/O Base 1
00:00:06.073993 0376-0376 ff07bb10 ff8f7890 ff8f7740 00000001 ATA I/O Base 2
00:00:06.074013 03b4-03b5 ff911000 ff8f12c0 ff8f1220 00000000 VGA - 3b4 (GC)
00:00:06.074033 03ba-03ba ff911000 ff8f12c0 ff8f1220 00000000 VGA - 3ba (GC)
00:00:06.074053 03c0-03cf ff911000 ff8f12c0 ff8f1220 00000000 VGA - 3c0 (GC)
00:00:06.074073 03d4-03d5 ff911000 ff8f12c0 ff8f1220 00000000 VGA - 3d4 (GC)
00:00:06.074093 03da-03da ff911000 ff8f12c0 ff8f1220 00000000 VGA - 3da (GC)
00:00:06.074113 03f6-03f6 ff07bb10 ff8f7890 ff8f7740 00000000 ATA I/O Base 2
00:00:06.074133 04d0-04d0 ff072ce0 ff8f5240 ff8f52c0 ff072da0 i8259 PIC #0 - elcr
00:00:06.074154 04d1-04d1 ff072ce0 ff8f5240 ff8f52c0 ff072de0 i8259 PIC #1 - elcr
00:00:06.074174 0cf8-0cf8 ff02fd20 ff8ef990 ff8ef940 00000000 ICH9 (PCI)
00:00:06.074194 0cfc-0cff ff02fd20 ff8efaa0 ff8efa00 00000000 ICH9 (PCI)
00:00:06.074214 4008-4008 ff07ddc0 ff8f3f90 00000000 00000000 ACPI PM Timer
00:00:06.074233 e000-e007 ff07bb10 ff8f6b80 ff8f6c70 00000000 ATA Bus Master DMA
00:00:06.074254 e008-e00f ff07bb10 ff8f6b80 ff8f6c70 00000001 ATA Bus Master DMA
00:00:06.074274 R3 Read  Ports: 0x1f0-0x1f8 a8f24ac0 ATA I/O Base 1
00:00:06.074288 R3 Write Ports: 0x3f6-0x3f7 a8f24b80 ATA I/O Base 2
00:00:06.074301 !!
00:00:06.074302 !! {ldt}
00:00:06.074303 !!
00:00:06.074308 Shadow LDT (GCAddr=ff668000 limit=0x0):
00:00:06.074318 !!
00:00:06.074319 !! {ldtguest}
00:00:06.074320 !!
00:00:06.074325 Guest LDT (Sel=0): Null-Selector
00:00:06.074331 !!
00:00:06.074331 !! {lpc}
00:00:06.074332 !!
00:00:06.074337 APIC backdoor closed: 00 00
00:00:06.074345 PIRQA -> IRQ11
00:00:06.074352 PIRQB -> IRQ9
00:00:06.074359 PIRQC -> IRQ11
00:00:06.074366 PIRQD -> IRQ9
00:00:06.074373 PIRQE disabled
00:00:06.074378 PIRQF disabled
00:00:06.074382 PIRQG disabled
00:00:06.074386 PIRQH disabled
00:00:06.074392 !!
00:00:06.074393 !! {mmio}
00:00:06.074394 !!
00:00:06.074398 MMIO ranges (pVM=a92dc000)
00:00:06.074400 GC Phys Range                     pDevIns  Read     Write    Fill     pvUser   Description
00:00:06.074423 00000000000a0000-00000000000bffff a6bd1000 a73a7290 a73a5c30 a73a66f0 00000000 VGA - VGA Video Buffer
00:00:06.074450                                R0 a6bd1000 f9b8e210 f9b8e4a0 f9b8d9a0 00000000
00:00:06.074497                                RC ff911000 ff8f1f80 ff8f2230 ff8f16e0 00000000
00:00:06.074545 00000000dc000000-00000000dfffffff a8ed7d20 a739be30 a739bfe0 00000000 00000000 MCFG ranges
00:00:06.074571                                R0 a8ed7d20 f9b8bc80 f9b8bbd0 00000000 00000000
00:00:06.074617                                RC ff02fd20 ff8efc60 ff8efbb0 00000000 00000000
00:00:06.074664 00000000f0500000-00000000f0500fff a8f24f20 a740e610 a740e030 00000000 00000000 USB OHCI
00:00:06.074690                                R0 a8f24f20 f9b9bc20 f9b9bcb0 00000000 00000000
00:00:06.074736                                RC ff07cf20 ff8ff390 ff8ff420 00000000 00000000
00:00:06.074783 00000000fec00000-00000000fec00fff a8f1b150 a72d30a0 a72d2f70 00000000 a8f1b210 I/O APIC Memory
00:00:06.074810                                R0 a8f1b150 f9bca0f0 f9bca270 00000000 00000000
00:00:06.074856                                RC ff073150 ff90e0d0 ff90e250 00000000 00000000
00:00:06.074906 00000000fed00000-00000000fed00fff a8f1b4d0 a73e75f0 a73e7d90 00000000 a8f1b590 HPET Memory
00:00:06.074933                                R0 a8f1b4d0 f9b928f0 f9b92bd0 00000000 00000000
00:00:06.074979                                RC ff0734d0 ff8f6680 ff8f6960 00000000 00000000
00:00:06.075026 00000000fed1c000-00000000fed1ffff a79f2760 a72d3b20 a72d3bb0 00000000 a79f2820 LPC Memory
00:00:06.075053                                R0 00000000 00000000 00000000 00000000 00000000
00:00:06.075098                                RC 00000000 00000000 00000000 00000000 00000000
00:00:06.075142 00000000fee00000-00000000fee00fff a8f19ff0 a72d0f50 a72d2090 00000000 a8f1a0b0 APIC Memory
00:00:06.075170                                R0 a8f19ff0 f9bc9c70 f9bc9db0 00000000 00000000
00:00:06.075216                                RC ff071ff0 ff90dc50 ff90dd90 00000000 00000000
00:00:06.075263 !!
00:00:06.075264 !! {ohci}
00:00:06.075265 !!
00:00:06.075270 HcControl: 00000200 - CBSR=0 PLE=0 IE=0 CLE=0 BLE=0 HCFS=0x0 IR=0 RWC=1 RWE=0
00:00:06.075297 HcCommandStatus:   00000000 - HCR=0 CLF=0 BLF=0 OCR=0 SOC=0
00:00:06.075314 HcInterruptStatus: 00000040 - SO=0 WDH=0 SF=0 RD=0 UE=0 FNO=0 RHSC=1 OC=0
00:00:06.075338 HcInterruptEnable: 80000000 - SO=0 WDH=0 SF=0 RD=0 UE=0 FNO=0 RHSC=0 OC=0 MIE=1
00:00:06.075365 HcHCCA: 00000000
00:00:06.075370 HcPeriodCurrentED:  00000000
00:00:06.075375 HcControlHeadED:    00000000
00:00:06.075380 HcControlCurrentED: 00000000
00:00:06.075385 HcBulkHeadED:       00000000
00:00:06.075389 HcBulkCurrentED:    00000000
00:00:06.075394 HcDoneHead:         00000000
00:00:06.075399 
00:00:06.075402 !!
00:00:06.075403 !! {pci}
00:00:06.075404 !!
00:00:06.075409 Invalid argument. Recognized arguments are 'basic', 'verbose'.
00:00:06.075413 !!
00:00:06.075414 !! {pdmtracingids}
00:00:06.075415 !!
00:00:06.075420 Device tracing IDs:
00:00:06.075423 00001  pcarch
00:00:06.075429 00002  pcbios
00:00:06.075435 00003  ich9pci
00:00:06.075441 00004  ich9pcibridge
00:00:06.075447 00005  ich9pcibridge
00:00:06.075453 00006  pckbd
00:00:06.075459 00007  apic
00:00:06.075464 00008  i8259
00:00:06.075470 00009  ioapic
00:00:06.075476 00010  hpet
00:00:06.075482 00011  i8254
00:00:06.075487 00012  mc146818
00:00:06.075493 00013  8237A
00:00:06.075499 00014  VMMDev
00:00:06.075505 00015  vga
00:00:06.075510 00016  piix3ide
00:00:06.075516 00017  AudioSniffer
00:00:06.075522 00018  ichac97
00:00:06.075528 00019  usb-ohci
00:00:06.075534 00020  acpi
00:00:06.075540 00021  lpc
00:00:06.075545 USB device tracing IDs:
00:00:06.075548 01041  HidMouse
00:00:06.075554 Driver tracing IDs:
00:00:06.075557 01025  KeyboardQueue (level 0, lun 0, dev pckbd)
00:00:06.075571 01026  MainKeyboard (level 1, lun 0, dev pckbd)
00:00:06.075585 01027  MouseQueue (level 0, lun 1, dev pckbd)
00:00:06.075599 01028  MainMouse (level 1, lun 1, dev pckbd)
00:00:06.075613 01029  HGCM (level 0, lun 0, dev VMMDev)
00:00:06.075626 01030  MainStatus (level 0, lun 999, dev VMMDev)
00:00:06.075640 01031  MainDisplay (level 0, lun 0, dev vga)
00:00:06.075653 01032  MainStatus (level 0, lun 999, dev piix3ide)
00:00:06.075667 01033  Block (level 0, lun 0, dev piix3ide)
00:00:06.075681 01034  VD (level 1, lun 0, dev piix3ide)
00:00:06.075694 01035  Block (level 0, lun 2, dev piix3ide)
00:00:06.075708 01036  MainAudioSniffer (level 0, lun 0, dev AudioSniffer)
00:00:06.075721 01037  AUDIO (level 0, lun 0, dev ichac97)
00:00:06.075735 01038  VUSBRootHub (level 0, lun 0, dev usb-ohci)
00:00:06.075749 01039  MainStatus (level 0, lun 999, dev usb-ohci)
00:00:06.075762 01040  ACPIHost (level 0, lun 0, dev acpi)
00:00:06.075776 01042  MouseQueue (level 0, lun 0, dev HidMouse)
00:00:06.075789 01043  MainMouse (level 1, lun 0, dev HidMouse)
00:00:06.075955 !!
00:00:06.075956 !! {phys}
00:00:06.075957 !!
00:00:06.075962 RAM ranges (pVM=a92dc000)
00:00:06.075963 GC Phys Range                     pvHC    
00:00:06.075974 0000000000000000-000000003fffffff 00000000 Base RAM
00:00:06.076004 00000000dc000000-00000000dfffffff 00000000 MCFG ranges
00:00:06.076019 00000000e0000000-00000000e1ffffff a4a00000 VRam
00:00:06.076035 00000000f0000000-00000000f03fffff a6c70000 VMMDev
00:00:06.076051 00000000f0400000-00000000f0403fff aa997000 VMMDev Heap
00:00:06.076066 00000000f0500000-00000000f0500fff 00000000 USB OHCI
00:00:06.076083 00000000fec00000-00000000fec00fff 00000000 I/O APIC Memory
00:00:06.076099 00000000fed00000-00000000fed00fff 00000000 HPET Memory
00:00:06.076113 00000000fed1c000-00000000fed1ffff 00000000 LPC Memory
00:00:06.076128 00000000fee00000-00000000fee00fff 00000000 APIC Memory
00:00:06.076143 00000000ffff0000-00000000ffffffff 00000000 PC BIOS - 0xffffffff
00:00:06.076158 !!
00:00:06.076159 !! {pic}
00:00:06.076160 !!
00:00:06.076165 PIC0:
00:00:06.076170  IMR :b8 ISR   :01 IRR   :00 LIRR:01
00:00:06.076182  Base:08 PriAdd:00 RegSel:00
00:00:06.076192  Poll:00 SpMask:00 IState:00
00:00:06.076201  AEOI:00 Rotate:00 FNest :00 Ini4:01
00:00:06.076213  ELCR:00 ELMask:f8
00:00:06.076220 PIC1:
00:00:06.076225  IMR :8f ISR   :00 IRR   :00 LIRR:00
00:00:06.076237  Base:70 PriAdd:00 RegSel:00
00:00:06.076246  Poll:00 SpMask:00 IState:00
00:00:06.076255  AEOI:00 Rotate:00 FNest :00 Ini4:01
00:00:06.076267  ELCR:00 ELMask:de
00:00:06.076275 !!
00:00:06.076276 !! {pit}
00:00:06.076277 !!
00:00:06.076281 PIT (i8254) channel 0 status: irq=0x0
00:00:06.076283       count=00010000  latched_count=0000  count_latched=00
00:00:06.076285            status=00   status_latched=00     read_state=03
00:00:06.076286       write_state=03      write_latch=00        rw_mode=03
00:00:06.076287              mode=02              bcd=00           gate=01
00:00:06.076289   count_load_time=000000009e2fd478 next_transition_time=00000000dfa9bb70
00:00:06.076292       u64ReloadTS=00000000dc63a316            u64NextTS=00000000dfa9bb70
00:00:06.076344 PIT (i8254) channel 1 status: irq=0x0
00:00:06.076346       count=00010000  latched_count=0000  count_latched=00
00:00:06.076347            status=00   status_latched=00     read_state=00
00:00:06.076348       write_state=00      write_latch=00        rw_mode=00
00:00:06.076350              mode=03              bcd=00           gate=01
00:00:06.076351   count_load_time=0000000000000000 next_transition_time=0000000000000000
00:00:06.076353       u64ReloadTS=0000000000000000            u64NextTS=ffffffffffffffff
00:00:06.076403 PIT (i8254) channel 2 status: irq=0x0
00:00:06.076405       count=00010000  latched_count=0000  count_latched=00
00:00:06.076406            status=00   status_latched=00     read_state=00
00:00:06.076407       write_state=00      write_latch=00        rw_mode=00
00:00:06.076409              mode=03              bcd=00           gate=00
00:00:06.076410   count_load_time=0000000000000000 next_transition_time=0000000000000000
00:00:06.076412       u64ReloadTS=0000000000000000            u64NextTS=ffffffffffffffff
00:00:06.076462 speaker_data_on=0x0
00:00:06.076468 !!
00:00:06.076469 !! {ps2k}
00:00:06.076470 !!
00:00:06.076475 PS/2 Keyboard: scan set 2, scanning enabled
00:00:06.076482 Active command 00
00:00:06.076487 LED state 00, Num Lock off
00:00:06.076495 Typematic delay 500ms, repeat period 91ms
00:00:06.076503 Command queue: 0 items (4 max)
00:00:06.076511 Input queue  : 0 items (64 max)
00:00:06.076519 !!
00:00:06.076520 !! {rtc}
00:00:06.076521 !!
00:00:06.076526 Time: 12:26:09  Date: 12-10-27
00:00:06.076543 REG A=26 B=02 C=00 D=80
00:00:06.076556 !!
00:00:06.076557 !! {tracebuf}
00:00:06.076558 !!
00:00:06.076563 Tracing is disable
00:00:06.076566 !!
00:00:06.076567 !! {vbe}
00:00:06.076568 !!
00:00:06.076573 LFB at 00000000e0000000
00:00:06.076580 VBE disabled
00:00:06.076583 !!
00:00:06.076584 !! {vga}
00:00:06.076585 !!
00:00:06.076590 pixel clock: 28.322 MHz
00:00:06.076595 double scanning off
00:00:06.076599 double clocking off
00:00:06.076604 htotal: 900 px (100 cclk)
00:00:06.076612 vtotal: 449 px
00:00:06.076616 hdisp : 720 px (80 cclk)
00:00:06.076624 vdisp : 400 px
00:00:06.076629 split : 1023 ln
00:00:06.076634 start : 0x0
00:00:06.076639 char height 16
00:00:06.076644 text mode 80x25
00:00:06.076651 display refresh interval: 20 ms
00:00:06.076657 !!
00:00:06.076658 !! {vgaar}
00:00:06.076659 !!
00:00:06.076664 VGA Attribute Controller (3C0): index reg 20, flip-flop: 0 (index)
00:00:06.076674  Palette: 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
00:00:06.076721  AR10:0C AR11:00 AR12:0F AR13:08 AR14:00
00:00:06.076749 !!
00:00:06.076750 !! {vgacr}
00:00:06.076751 !!
00:00:06.076755 VGA CRTC (3D5): CRTC index 3D4:0F
00:00:06.076760  CR00:5F CR01:4F CR02:50 CR03:82 CR04:55 CR05:81 CR06:BF CR07:1F CR08:00 CR09:4F
00:00:06.076812  CR0A:0E CR0B:0F CR0C:00 CR0D:00 CR0E:00 CR0F:50 CR10:9C CR11:8E CR12:8F CR13:28
00:00:06.076864  CR14:1F CR15:96 CR16:B9 CR17:A3 CR18:FF
00:00:06.076891 !!
00:00:06.076892 !! {vgadac}
00:00:06.076893 !!
00:00:06.076898 VGA DAC contents:
00:00:06.076900  00: 00 00 00
00:00:06.076912  01: 00 00 2A
00:00:06.076923  02: 00 2A 00
00:00:06.076934  03: 00 2A 2A
00:00:06.076945  04: 2A 00 00
00:00:06.076956  05: 2A 00 2A
00:00:06.076968  06: 2A 2A 00
00:00:06.076979  07: 2A 2A 2A
00:00:06.076990  08: 00 00 15
00:00:06.077004  09: 00 00 3F
00:00:06.077015  0A: 00 2A 15
00:00:06.077027  0B: 00 2A 3F
00:00:06.077038  0C: 2A 00 15
00:00:06.077050  0D: 2A 00 3F
00:00:06.077062  0E: 2A 2A 15
00:00:06.077073  0F: 2A 2A 3F
00:00:06.077084  10: 00 15 00
00:00:06.077095  11: 00 15 2A
00:00:06.077107  12: 00 3F 00
00:00:06.077118  13: 00 3F 2A
00:00:06.077129  14: 2A 15 00
00:00:06.077140  15: 2A 15 2A
00:00:06.077151  16: 2A 3F 00
00:00:06.077162  17: 2A 3F 2A
00:00:06.077173  18: 00 15 15
00:00:06.077185  19: 00 15 3F
00:00:06.077196  1A: 00 3F 15
00:00:06.077207  1B: 00 3F 3F
00:00:06.077218  1C: 2A 15 15
00:00:06.077229  1D: 2A 15 3F
00:00:06.077240  1E: 2A 3F 15
00:00:06.077251  1F: 2A 3F 3F
00:00:06.077262  20: 15 00 00
00:00:06.077314  21: 15 00 2A
00:00:06.077328  22: 15 2A 00
00:00:06.077339  23: 15 2A 2A
00:00:06.077350  24: 3F 00 00
00:00:06.077361  25: 3F 00 2A
00:00:06.077372  26: 3F 2A 00
00:00:06.077383  27: 3F 2A 2A
00:00:06.077394  28: 15 00 15
00:00:06.077405  29: 15 00 3F
00:00:06.077416  2A: 15 2A 15
00:00:06.077428  2B: 15 2A 3F
00:00:06.077439  2C: 3F 00 15
00:00:06.077450  2D: 3F 00 3F
00:00:06.077461  2E: 3F 2A 15
00:00:06.077472  2F: 3F 2A 3F
00:00:06.077483  30: 15 15 00
00:00:06.077494  31: 15 15 2A
00:00:06.077505  32: 15 3F 00
00:00:06.077516  33: 15 3F 2A
00:00:06.077527  34: 3F 15 00
00:00:06.077538  35: 3F 15 2A
00:00:06.077549  36: 3F 3F 00
00:00:06.077560  37: 3F 3F 2A
00:00:06.077571  38: 15 15 15
00:00:06.077582  39: 15 15 3F
00:00:06.077593  3A: 15 3F 15
00:00:06.077605  3B: 15 3F 3F
00:00:06.077616  3C: 3F 15 15
00:00:06.077627  3D: 3F 15 3F
00:00:06.077640  3E: 3F 3F 15
00:00:06.077652  3F: 3F 3F 3F
00:00:06.077663  40: 00 00 00
00:00:06.077674  41: 00 00 00
00:00:06.077685  42: 00 00 00
00:00:06.077696  43: 00 00 00
00:00:06.077707  44: 00 00 00
00:00:06.077718  45: 00 00 00
00:00:06.077730  46: 00 00 00
00:00:06.077741  47: 00 00 00
00:00:06.077752  48: 00 00 00
00:00:06.077763  49: 00 00 00
00:00:06.077774  4A: 00 00 00
00:00:06.077785  4B: 00 00 00
00:00:06.077796  4C: 00 00 00
00:00:06.077808  4D: 00 00 00
00:00:06.077819  4E: 00 00 00
00:00:06.077830  4F: 00 00 00
00:00:06.077841  50: 00 00 00
00:00:06.077852  51: 00 00 00
00:00:06.077863  52: 00 00 00
00:00:06.077874  53: 00 00 00
00:00:06.077885  54: 00 00 00
00:00:06.077896  55: 00 00 00
00:00:06.077907  56: 00 00 00
00:00:06.077918  57: 00 00 00
00:00:06.077929  58: 00 00 00
00:00:06.077940  59: 00 00 00
00:00:06.077951  5A: 00 00 00
00:00:06.077962  5B: 00 00 00
00:00:06.077973  5C: 00 00 00
00:00:06.077984  5D: 00 00 00
00:00:06.077995  5E: 00 00 00
00:00:06.078006  5F: 00 00 00
00:00:06.078017  60: 00 00 00
00:00:06.078028  61: 00 00 00
00:00:06.078039  62: 00 00 00
00:00:06.078050  63: 00 00 00
00:00:06.078062  64: 00 00 00
00:00:06.078073  65: 00 00 00
00:00:06.078084  66: 00 00 00
00:00:06.078095  67: 00 00 00
00:00:06.078106  68: 00 00 00
00:00:06.078117  69: 00 00 00
00:00:06.078128  6A: 00 00 00
00:00:06.078139  6B: 00 00 00
00:00:06.078150  6C: 00 00 00
00:00:06.078161  6D: 00 00 00
00:00:06.078172  6E: 00 00 00
00:00:06.078183  6F: 00 00 00
00:00:06.078194  70: 00 00 00
00:00:06.078205  71: 00 00 00
00:00:06.078216  72: 00 00 00
00:00:06.078227  73: 00 00 00
00:00:06.078238  74: 00 00 00
00:00:06.078249  75: 00 00 00
00:00:06.078260  76: 00 00 00
00:00:06.078271  77: 00 00 00
00:00:06.078282  78: 00 00 00
00:00:06.078293  79: 00 00 00
00:00:06.078304  7A: 00 00 00
00:00:06.078315  7B: 00 00 00
00:00:06.078326  7C: 00 00 00
00:00:06.078337  7D: 00 00 00
00:00:06.078348  7E: 00 00 00
00:00:06.078359  7F: 00 00 00
00:00:06.078370  80: 00 00 00
00:00:06.078381  81: 00 00 00
00:00:06.078392  82: 00 00 00
00:00:06.078403  83: 00 00 00
00:00:06.078414  84: 00 00 00
00:00:06.078425  85: 00 00 00
00:00:06.078436  86: 00 00 00
00:00:06.078447  87: 00 00 00
00:00:06.078458  88: 00 00 00
00:00:06.078469  89: 00 00 00
00:00:06.078480  8A: 00 00 00
00:00:06.078491  8B: 00 00 00
00:00:06.078502  8C: 00 00 00
00:00:06.078513  8D: 00 00 00
00:00:06.078524  8E: 00 00 00
00:00:06.078535  8F: 00 00 00
00:00:06.078546  90: 00 00 00
00:00:06.078557  91: 00 00 00
00:00:06.078568  92: 00 00 00
00:00:06.078580  93: 00 00 00
00:00:06.078591  94: 00 00 00
00:00:06.078602  95: 00 00 00
00:00:06.078613  96: 00 00 00
00:00:06.078624  97: 00 00 00
00:00:06.078635  98: 00 00 00
00:00:06.078646  99: 00 00 00
00:00:06.078657  9A: 00 00 00
00:00:06.078668  9B: 00 00 00
00:00:06.078679  9C: 00 00 00
00:00:06.078690  9D: 00 00 00
00:00:06.078701  9E: 00 00 00
00:00:06.078712  9F: 00 00 00
00:00:06.078723  A0: 00 00 00
00:00:06.078734  A1: 00 00 00
00:00:06.078745  A2: 00 00 00
00:00:06.078756  A3: 00 00 00
00:00:06.078767  A4: 00 00 00
00:00:06.078778  A5: 00 00 00
00:00:06.078789  A6: 00 00 00
00:00:06.078800  A7: 00 00 00
00:00:06.078811  A8: 00 00 00
00:00:06.078822  A9: 00 00 00
00:00:06.078833  AA: 00 00 00
00:00:06.078844  AB: 00 00 00
00:00:06.078855  AC: 00 00 00
00:00:06.078866  AD: 00 00 00
00:00:06.078877  AE: 00 00 00
00:00:06.078889  AF: 00 00 00
00:00:06.078900  B0: 00 00 00
00:00:06.078911  B1: 00 00 00
00:00:06.078922  B2: 00 00 00
00:00:06.078933  B3: 00 00 00
00:00:06.078944  B4: 00 00 00
00:00:06.078955  B5: 00 00 00
00:00:06.078966  B6: 00 00 00
00:00:06.078977  B7: 00 00 00
00:00:06.078988  B8: 00 00 00
00:00:06.078999  B9: 00 00 00
00:00:06.079010  BA: 00 00 00
00:00:06.079021  BB: 00 00 00
00:00:06.079032  BC: 00 00 00
00:00:06.079043  BD: 00 00 00
00:00:06.079054  BE: 00 00 00
00:00:06.079065  BF: 00 00 00
00:00:06.079076  C0: 00 00 00
00:00:06.079087  C1: 00 00 00
00:00:06.079099  C2: 00 00 00
00:00:06.079110  C3: 00 00 00
00:00:06.079121  C4: 00 00 00
00:00:06.079132  C5: 00 00 00
00:00:06.079143  C6: 00 00 00
00:00:06.079154  C7: 00 00 00
00:00:06.079165  C8: 00 00 00
00:00:06.079176  C9: 00 00 00
00:00:06.079187  CA: 00 00 00
00:00:06.079198  CB: 00 00 00
00:00:06.079209  CC: 00 00 00
00:00:06.079220  CD: 00 00 00
00:00:06.079231  CE: 00 00 00
00:00:06.079242  CF: 00 00 00
00:00:06.079253  D0: 00 00 00
00:00:06.079264  D1: 00 00 00
00:00:06.079275  D2: 00 00 00
00:00:06.079286  D3: 00 00 00
00:00:06.079297  D4: 00 00 00
00:00:06.079308  D5: 00 00 00
00:00:06.079319  D6: 00 00 00
00:00:06.079330  D7: 00 00 00
00:00:06.079341  D8: 00 00 00
00:00:06.079352  D9: 00 00 00
00:00:06.079363  DA: 00 00 00
00:00:06.079374  DB: 00 00 00
00:00:06.079385  DC: 00 00 00
00:00:06.079396  DD: 00 00 00
00:00:06.079407  DE: 00 00 00
00:00:06.079418  DF: 00 00 00
00:00:06.079429  E0: 00 00 00
00:00:06.079440  E1: 00 00 00
00:00:06.079451  E2: 00 00 00
00:00:06.079462  E3: 00 00 00
00:00:06.079473  E4: 00 00 00
00:00:06.079484  E5: 00 00 00
00:00:06.079495  E6: 00 00 00
00:00:06.079506  E7: 00 00 00
00:00:06.079517  E8: 00 00 00
00:00:06.079528  E9: 00 00 00
00:00:06.079539  EA: 00 00 00
00:00:06.079550  EB: 00 00 00
00:00:06.079561  EC: 00 00 00
00:00:06.079572  ED: 00 00 00
00:00:06.079584  EE: 00 00 00
00:00:06.079595  EF: 00 00 00
00:00:06.079606  F0: 00 00 00
00:00:06.079617  F1: 00 00 00
00:00:06.079628  F2: 00 00 00
00:00:06.079639  F3: 00 00 00
00:00:06.079650  F4: 00 00 00
00:00:06.079661  F5: 00 00 00
00:00:06.079672  F6: 00 00 00
00:00:06.079683  F7: 00 00 00
00:00:06.079694  F8: 00 00 00
00:00:06.079705  F9: 00 00 00
00:00:06.079716  FA: 00 00 00
00:00:06.079727  FB: 00 00 00
00:00:06.079738  FC: 00 00 00
00:00:06.079750  FD: 00 00 00
00:00:06.079761  FE: 00 00 00
00:00:06.079772  FF: 00 00 00
00:00:06.079784 !!
00:00:06.079785 !! {vgagr}
00:00:06.079786 !!
00:00:06.079790 VGA Graphics Controller (3CF): GR index 3CE:05
00:00:06.079796  GR00:00 GR01:00 GR02:00 GR03:00 GR04:00 GR05:10 GR06:0E GR07:0F GR08:FF
00:00:06.079844 !!
00:00:06.079845 !! {vgapl}
00:00:06.079845 !!
00:00:06.079850 read mode     : 0     write mode: 0
00:00:06.079858 set/reset data: 00    S/R enable: 00
00:00:06.079865 color compare : 00    read map  : 0
00:00:06.079873 rotate        : 0     function  : 0
00:00:06.079880 don't care    : 0F    bit mask  : FF
00:00:06.079887 seq plane mask: 03    chain-4   : off
00:00:06.079905 !!
00:00:06.079906 !! {vgasr}
00:00:06.079907 !!
00:00:06.079912 VGA Sequencer (3C5): SR index 3C4:03
00:00:06.079917  SR00:03 SR01:00 SR02:03 SR03:00 SR04:02
00:00:06.079945 !!
00:00:06.079946 !! {vgatext}
00:00:06.079947 !!
00:00:06.079953 ------------------------------------ 80x25 -------------------------------------
00:00:06.080059 MBR                                                                             
00:00:06.080175                                                                                 
00:00:06.080290                                                                                 
00:00:06.080503                .                                                                
00:00:06.080618                                                                                 
00:00:06.080733                                                                                 
00:00:06.080848                                .                                                
00:00:06.080962                                                                                 
00:00:06.081077                                                                                 
00:00:06.081191                                                .                                
00:00:06.081305                                                                                 
00:00:06.081419                                                                                 
00:00:06.081533                                                                .                
00:00:06.081647                                                                                 
00:00:06.081762                                                                                 
00:00:06.081876                                                                                .
00:00:06.081989                                                                                 
00:00:06.082104                                                                                 
00:00:06.082219                                                                                 
00:00:06.082333                .                                                                
00:00:06.082447                                                                                 
00:00:06.082562                                                                                 
00:00:06.082677                                .                                                
00:00:06.082790                                                                                 
00:00:06.082904                                                                                 
00:00:06.083018 --------------------------------------------------------------------------------
00:00:06.083130 !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
00:00:07.084281 Changing the VM state from 'RUNNING' to 'GURU_MEDITATION'.
00:00:09.772247 Console::powerDown(): A request to power off the VM has been issued (mMachineState=Stopping, InUninit=0)
00:00:09.773129 Changing the VM state from 'GURU_MEDITATION' to 'POWERING_OFF'.
00:00:09.773155 ****************** Guest state at power off ******************
00:00:09.773162 Guest CPUM (VCPU 0) state: 
00:00:09.773170 eax=00009600 ebx=0000f000 ecx=0000adb2 edx=00000180 esi=000007be edi=00000005
00:00:09.773176 eip=0000ad57 esp=00002e66 ebp=00001b74 iopl=0         nv up di pl zr na pe nc
00:00:09.773181 cs={99ac base=0000000000099ac0 limit=0000ffff flags=0000009b} dr0=00000000 dr1=00000000
00:00:09.773191 ds={002e base=00000000000002e0 limit=0000ffff flags=00000093} dr2=00000000 dr3=00000000
00:00:09.773197 es={0d00 base=000000000000d000 limit=0000ffff flags=00000093} dr4=00000000 dr5=00000000
00:00:09.773204 fs={0000 base=0000000000000000 limit=0000ffff flags=00000093} dr6=ffff0ff0 dr7=00000400
00:00:09.773211 gs={0000 base=0000000000000000 limit=0000ffff flags=00000093} cr0=00000010 cr2=00000000
00:00:09.773217 ss={0000 base=0000000000000000 limit=0000ffff flags=00000093} cr3=00000000 cr4=00000000
00:00:09.773223 gdtr=00000000000fe898:0047  idtr=0000000000000000:ffff  eflags=00000002
00:00:09.773229 ldtr={0000 base=00000000 limit=0000ffff flags=00000082}
00:00:09.773233 tr  ={0000 base=00000000 limit=0000ffff flags=0000008b}
00:00:09.773237 SysEnter={cs=0000 eip=00000000 esp=00000000}
00:00:09.773241 FCW=037f FSW=0000 FTW=0000 FOP=0000 MXCSR=00001f80 MXCSR_MASK=0000ffff
00:00:09.773246 FPUIP=00000000 CS=0000 Rsrvd1=0000  FPUDP=00000000 DS=0000 Rsvrd2=0000
00:00:09.773252 ST(0)=FPR0={0000'00000000'00000000} t0 +0.0000000000000000000000 ^ 0
00:00:09.773260 ST(1)=FPR1={0000'00000000'00000000} t0 +0.0000000000000000000000 ^ 0
00:00:09.773267 ST(2)=FPR2={0000'00000000'00000000} t0 +0.0000000000000000000000 ^ 0
00:00:09.773274 ST(3)=FPR3={0000'00000000'00000000} t0 +0.0000000000000000000000 ^ 0
00:00:09.773280 ST(4)=FPR4={0000'00000000'00000000} t0 +0.0000000000000000000000 ^ 0
00:00:09.773286 ST(5)=FPR5={0000'00000000'00000000} t0 +0.0000000000000000000000 ^ 0
00:00:09.773292 ST(6)=FPR6={0000'00000000'00000000} t0 +0.0000000000000000000000 ^ 0
00:00:09.773298 ST(7)=FPR7={0000'00000000'00000000} t0 +0.0000000000000000000000 ^ 0
00:00:09.773304 XMM0 =00000000'00000000'00000000'00000000  XMM1 =00000000'00000000'00000000'00000000
00:00:09.773313 XMM2 =00000000'00000000'00000000'00000000  XMM3 =00000000'00000000'00000000'00000000
00:00:09.773320 XMM4 =00000000'00000000'00000000'00000000  XMM5 =00000000'00000000'00000000'00000000
00:00:09.773327 XMM6 =00000000'00000000'00000000'00000000  XMM7 =00000000'00000000'00000000'00000000
00:00:09.773334 XMM8 =00000000'00000000'00000000'00000000  XMM9 =00000000'00000000'00000000'00000000
00:00:09.773342 XMM10=00000000'00000000'00000000'00000000  XMM11=00000000'00000000'00000000'00000000
00:00:09.773349 XMM12=00000000'00000000'00000000'00000000  XMM13=00000000'00000000'00000000'00000000
00:00:09.773356 XMM14=00000000'00000000'00000000'00000000  XMM15=00000000'00000000'00000000'00000000
00:00:09.773363 EFER         =0000000000000000
00:00:09.773366 PAT          =0007040600070406
00:00:09.773370 STAR         =0000000000000000
00:00:09.773373 CSTAR        =0000000000000000
00:00:09.773375 LSTAR        =0000000000000000
00:00:09.773378 SFMASK       =0000000000000000
00:00:09.773380 KERNELGSBASE =0000000000000000
00:00:09.773383 ***
00:00:09.773390 Guest paging mode:  Real (changed 3 times), A20 disabled (changed 1 times)
00:00:09.773395 Shadow paging mode: PAE
00:00:09.773397 Host paging mode:   PAE+G
00:00:09.773400 ***
00:00:09.773408 Active Timers (pVM=a92dc000)
00:00:09.773411 pTimerR3 offNext  offPrev  offSched Clock               Time             Expire HzHint State                     Description
00:00:09.773422 a8f27fe0 ffffba50 00000000 00000000 Real             1190501            1186787      0 2-ACTIVE                  EMT Yielder
00:00:09.773435 a8f23a30 00004550 000045b0 00000000 Real             1190501            1186804      0 2-ACTIVE                  VGA Refresh Timer
00:00:09.773447 a8f27f80 00000000 ffffbab0 00000000 Real             1190501            1187054      0 2-ACTIVE                  CPU Load Timer
00:00:09.773458 a8f24ec0 00000000 00000000 00000000 Virt          3704543930         3708122589      0 2-ACTIVE                  Audio timer
00:00:09.773470 a8f1bcf0 00000500 00000000 00000000 VrSy          3697517334         3752442736     18 2-ACTIVE                  i8254 Programmable Interval Timer
00:00:09.773482 a8f1c1f0 0000b540 fffffb00 00000000 VrSy          3697517334         3990000000      0 2-ACTIVE                  MC146818 RTC/CMOS - Second
00:00:09.773494 a8f27730 00000000 ffff4ac0 00000000 VrSy          3697517334      1199864031601      0 2-ACTIVE                  ACPI PM Timer
00:00:09.773507 ***
00:00:09.773514 Shadow GDT (GCAddr=ff657000):
00:00:09.773553 ffd8 - 81980087 ff008900 - base=ff008198 limit=00000087 dpl=0 TSS32Avail Present 16-bit  HyperTSSTrap08
00:00:09.773560 ffe0 - 81100087 ff008b00 - base=ff008110 limit=00000087 dpl=0 TSS32Busy Present 16-bit  HyperTSS
00:00:09.773567 ffe8 - 0000ffff 00af9b00 - base=00000000 limit=ffffffff dpl=0 CodeER Accessed Present Page 16-bit  HyperCS64
00:00:09.773573 fff0 - 0000ffff 00cf9300 - base=00000000 limit=ffffffff dpl=0 DataRW Accessed Present Page 32-bit  HyperDS
00:00:09.773579 fff8 - 0000ffff 00cf9b00 - base=00000000 limit=ffffffff dpl=0 CodeER Accessed Present Page 32-bit  HyperCS
00:00:09.773582 ***
00:00:09.773584 ***
00:00:09.773586 ss:sp=0000:2e66 0000:2e40 TO 0000:2f3f:
00:00:09.773595 a94b30ec 0000: 78 78 78 78 78 78 78 78-78 78 78 78 78 78 78 78 xxxxxxxxxxxxxxxx
00:00:09.773606 a94b30fc 0010: 78 78 78 78 78 78 78 78-78 78 78 78 78 78 78 78 xxxxxxxxxxxxxxxx
00:00:09.773615 a94b310c 0020: 78 78 78 78 78 78 7b 00-00 0d 07 02 78 02 2e 00 xxxxxx{.....x...
00:00:09.773625 a94b311c 0030: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:09.773634 a94b312c 0040: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:09.773643 a94b313c 0050: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:09.773652 a94b314c 0060: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:09.773660 a94b315c 0070: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:09.773669 a94b316c 0080: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:09.773678 a94b317c 0090: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:09.773686 a94b318c 00a0: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:09.773695 a94b319c 00b0: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:09.773703 a94b31ac 00c0: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:09.773712 a94b31bc 00d0: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:09.773720 a94b31cc 00e0: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:09.773729 a94b31dc 00f0: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:09.773739 2000:0000 TO 2000:01ff:
00:00:09.773741 a94b30ec 0000: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:09.773750 a94b30fc 0010: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:09.773759 a94b310c 0020: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:09.773768 a94b311c 0030: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:09.773776 a94b312c 0040: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:09.773785 a94b313c 0050: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:09.773794 a94b314c 0060: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:09.773802 a94b315c 0070: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:09.773811 a94b316c 0080: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:09.773820 a94b317c 0090: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:09.773828 a94b318c 00a0: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:09.773837 a94b319c 00b0: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:09.773845 a94b31ac 00c0: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:09.773853 a94b31bc 00d0: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:09.773862 a94b31cc 00e0: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:09.773871 a94b31dc 00f0: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:09.773879 a94b31ec 0100: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:09.773888 a94b31fc 0110: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:09.773897 a94b320c 0120: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:09.773905 a94b321c 0130: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:09.773914 a94b322c 0140: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:09.773923 a94b323c 0150: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:09.773932 a94b324c 0160: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:09.773941 a94b325c 0170: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:09.773949 a94b326c 0180: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:09.773958 a94b327c 0190: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:09.773967 a94b328c 01a0: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:09.773976 a94b329c 01b0: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:09.773985 a94b32ac 01c0: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:09.773993 a94b32bc 01d0: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:09.774002 a94b32cc 01e0: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:09.774011 a94b32dc 01f0: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:09.774020 ************** End of Guest state at power off ***************
00:00:09.858180 PDMR3PowerOff: 84 103 579 ns run time
00:00:09.858209 Changing the VM state from 'POWERING_OFF' to 'OFF'.
00:00:09.859879 Changing the VM state from 'OFF' to 'DESTROYING'.
00:00:09.859930 ************************* Statistics *************************
00:00:09.859985 /Devices/IDE0/ATA0/Unit0/AtapiDMA        0 times
00:00:09.859992 /Devices/IDE0/ATA0/Unit0/AtapiPIO        0 times
00:00:09.859996 /Devices/IDE0/ATA0/Unit0/DMA            0 times
00:00:09.860001 /Devices/IDE0/ATA0/Unit0/PIO           22 times
00:00:09.860006 /Devices/IDE0/ATA0/Unit0/ReadBytes    10752 bytes
00:00:09.860011 /Devices/IDE0/ATA0/Unit0/WrittenBytes        0 bytes
00:00:09.860016 /Devices/IDE0/ATA0/Unit1/AtapiDMA        0 times
00:00:09.860020 /Devices/IDE0/ATA0/Unit1/AtapiPIO        0 times
00:00:09.860024 /Devices/IDE0/ATA0/Unit1/DMA            0 times
00:00:09.860029 /Devices/IDE0/ATA0/Unit1/PIO            0 times
00:00:09.860034 /Devices/IDE0/ATA0/Unit1/ReadBytes        0 bytes
00:00:09.860038 /Devices/IDE0/ATA0/Unit1/WrittenBytes        0 bytes
00:00:09.860042 /Devices/IDE0/ATA1/Unit0/AtapiDMA        0 times
00:00:09.860047 /Devices/IDE0/ATA1/Unit0/AtapiPIO        0 times
00:00:09.860051 /Devices/IDE0/ATA1/Unit0/DMA            0 times
00:00:09.860055 /Devices/IDE0/ATA1/Unit0/PIO            0 times
00:00:09.860060 /Devices/IDE0/ATA1/Unit0/ReadBytes        0 bytes
00:00:09.860064 /Devices/IDE0/ATA1/Unit0/WrittenBytes        0 bytes
00:00:09.860069 /Devices/IDE0/ATA1/Unit1/AtapiDMA        0 times
00:00:09.860073 /Devices/IDE0/ATA1/Unit1/AtapiPIO        0 times
00:00:09.860077 /Devices/IDE0/ATA1/Unit1/DMA            0 times
00:00:09.860082 /Devices/IDE0/ATA1/Unit1/PIO            0 times
00:00:09.860086 /Devices/IDE0/ATA1/Unit1/ReadBytes        0 bytes
00:00:09.860091 /Devices/IDE0/ATA1/Unit1/WrittenBytes        0 bytes
00:00:09.860095 /Devices/VMMDev/BalloonChunks           0 count
00:00:09.860100 /FT/Checkpoint/Network                  0 times
00:00:09.860105 /FT/Checkpoint/Storage                  0 times
00:00:09.860109 /FT/Received/Mem                        0 bytes
00:00:09.860114 /FT/Received/State                      0 bytes
00:00:09.860118 /FT/Sent/Mem                            0 bytes
00:00:09.860123 /FT/Sent/State                          0 bytes
00:00:09.860128 /FT/Sync/DeltaMem                       0 times
00:00:09.860133 /FT/Sync/DeltaVM                        0 times
00:00:09.860137 /FT/Sync/Full                           0 times
00:00:09.860142 /GMM/VM/Allocated/cBasePages         2105 pages
00:00:09.860147 /GMM/VM/Allocated/cFixedPages           0 pages
00:00:09.860152 /GMM/VM/Allocated/cShadowPages          0 pages
00:00:09.860169 /GMM/VM/Reserved/cBasePages        262302 pages
00:00:09.860174 /GMM/VM/Reserved/cFixedPages         9220 pages
00:00:09.860179 /GMM/VM/Reserved/cShadowPages           1 pages
00:00:09.860183 /GMM/VM/cBalloonedPages                 0 pages
00:00:09.860188 /GMM/VM/cMaxBalloonedPages              0 pages
00:00:09.860192 /GMM/VM/cPrivatePages                2105 pages
00:00:09.860197 /GMM/VM/cReqActuallyBalloonedPages        0 pages
00:00:09.860202 /GMM/VM/cReqBalloonedPages              0 pages
00:00:09.860206 /GMM/VM/cReqDeflatePages                0 pages
00:00:09.860210 /GMM/VM/cShareableModules               0 count
00:00:09.860215 /GMM/VM/cSharedPages                    0 pages
00:00:09.860220 /GMM/VM/enmPolicy                       1 
00:00:09.860224 /GMM/VM/enmPriority                     2 
00:00:09.860229 /GMM/VM/fBallooningEnabled       false    
00:00:09.860234 /GMM/VM/fMayAllocate             false    
00:00:09.860238 /GMM/VM/fSharedPagingEnabled     false    
00:00:09.860242 /GMM/cAllocatedPages                 2105 pages
00:00:09.860247 /GMM/cBalloonedPages                    0 pages
00:00:09.860252 /GMM/cChunks                            5 count
00:00:09.860257 /GMM/cDuplicatePages                    0 pages
00:00:09.860261 /GMM/cFreedChunks                       0 count
00:00:09.860266 /GMM/cLeftBehindSharedPages             0 pages
00:00:09.860270 /GMM/cMaxPages                   4294967295 pages
00:00:09.860276 /GMM/cOverCommittedPages                0 pages
00:00:09.860280 /GMM/cReservedPages                271523 pages
00:00:09.860285 /GMM/cShareableModules                  0 count
00:00:09.860290 /GMM/cSharedPages                       0 pages
00:00:09.860294 /GVMM/EMTs                              1 calls
00:00:09.860299 /GVMM/HostCPUs                          2 calls
00:00:09.860304 /GVMM/HostCpus/0                        0 
00:00:09.860308 /GVMM/HostCpus/0/CurTimerHz             0 Hz
00:00:09.860313 /GVMM/HostCpus/0/DesiredHz              0 Hz
00:00:09.860317 /GVMM/HostCpus/0/PPTChanges             0 times
00:00:09.860322 /GVMM/HostCpus/0/PPTStarts              0 times
00:00:09.860326 /GVMM/HostCpus/0/idxCpuSet              0 
00:00:09.860330 /GVMM/HostCpus/1                        1 
00:00:09.860335 /GVMM/HostCpus/1/CurTimerHz             0 Hz
00:00:09.860339 /GVMM/HostCpus/1/DesiredHz              0 Hz
00:00:09.860344 /GVMM/HostCpus/1/PPTChanges             0 times
00:00:09.860348 /GVMM/HostCpus/1/PPTStarts              0 times
00:00:09.860352 /GVMM/HostCpus/1/idxCpuSet              1 
00:00:09.860357 /GVMM/Sum/HaltBlocking                943 calls
00:00:09.860362 /GVMM/Sum/HaltCalls                   963 calls
00:00:09.860366 /GVMM/Sum/HaltNotBlocking              20 calls
00:00:09.860371 /GVMM/Sum/HaltTimeouts                684 calls
00:00:09.860376 /GVMM/Sum/HaltWakeUps                   0 calls
00:00:09.860380 /GVMM/Sum/PokeCalls                     0 calls
00:00:09.860385 /GVMM/Sum/PokeNotBusy                   0 calls
00:00:09.860390 /GVMM/Sum/PollCalls                     0 calls
00:00:09.860394 /GVMM/Sum/PollHalts                     0 calls
00:00:09.860399 /GVMM/Sum/PollWakeUps                   0 calls
00:00:09.860403 /GVMM/Sum/WakeUpCalls                 259 calls
00:00:09.860408 /GVMM/Sum/WakeUpNotHalted             158 calls
00:00:09.860413 /GVMM/Sum/WakeUpWakeUps                 0 calls
00:00:09.860417 /GVMM/VM/HaltBlocking                 943 calls
00:00:09.860422 /GVMM/VM/HaltCalls                    963 calls
00:00:09.860427 /GVMM/VM/HaltNotBlocking               20 calls
00:00:09.860432 /GVMM/VM/HaltTimeouts                 684 calls
00:00:09.860436 /GVMM/VM/HaltWakeUps                    0 calls
00:00:09.860441 /GVMM/VM/PokeCalls                      0 calls
00:00:09.860446 /GVMM/VM/PokeNotBusy                    0 calls
00:00:09.860450 /GVMM/VM/PollCalls                      0 calls
00:00:09.860455 /GVMM/VM/PollHalts                      0 calls
00:00:09.860460 /GVMM/VM/PollWakeUps                    0 calls
00:00:09.860464 /GVMM/VM/WakeUpCalls                  259 calls
00:00:09.860476 /GVMM/VM/WakeUpNotHalted              158 calls
00:00:09.860481 /GVMM/VM/WakeUpWakeUps                  0 calls
00:00:09.860485 /GVMM/VMs                               1 calls
00:00:09.860491 /IEM/CPU0/cInstructions                 0 count
00:00:09.860495 /IEM/CPU0/cPotentialExits               0 count
00:00:09.860500 /IEM/CPU0/cRetAspectNotImplemented        0 count
00:00:09.860504 /IEM/CPU0/cRetErrStatuses               0 count
00:00:09.860508 /IEM/CPU0/cRetInfStatuses               0 count
00:00:09.860513 /IEM/CPU0/cRetInstrNotImplemented        0 count
00:00:09.860517 /IEM/CPU0/cbWritten                     0 bytes
00:00:09.860522 /MM/HyperHeap/cbFree              1656592 bytes
00:00:09.860527 /MM/HyperHeap/cbHeap              2096960 bytes
00:00:09.860532 /PDM/BlkCache/cbCached                  0 bytes
00:00:09.860536 /PDM/BlkCache/cbCachedFru               0 bytes
00:00:09.860541 /PDM/BlkCache/cbCachedMruIn             0 bytes
00:00:09.860545 /PDM/BlkCache/cbCachedMruOut            0 bytes
00:00:09.860549 /PDM/BlkCache/cbMax               5242880 bytes
00:00:09.860554 /PDM/CritSects/8237A#0 Auto/ContentionR3        0 times
00:00:09.860559 /PDM/CritSects/8237A#0 Auto/ContentionRZLock        0 times
00:00:09.860563 /PDM/CritSects/8237A#0 Auto/ContentionRZUnlock        0 times
00:00:09.860568 /PDM/CritSects/ATA#0/ContentionR3        0 times
00:00:09.860572 /PDM/CritSects/ATA#0/ContentionRZLock        0 times
00:00:09.860576 /PDM/CritSects/ATA#0/ContentionRZUnlock        0 times
00:00:09.860581 /PDM/CritSects/ATA#1/ContentionR3        0 times
00:00:09.860585 /PDM/CritSects/ATA#1/ContentionRZLock        0 times
00:00:09.860589 /PDM/CritSects/ATA#1/ContentionRZUnlock        0 times
00:00:09.860594 /PDM/CritSects/AudioSniffer#0 Auto/ContentionR3        0 times
00:00:09.860598 /PDM/CritSects/AudioSniffer#0 Auto/ContentionRZLock        0 times
00:00:09.860603 /PDM/CritSects/AudioSniffer#0 Auto/ContentionRZUnlock        0 times
00:00:09.860607 /PDM/CritSects/EM-REM/ContentionR3        0 times
00:00:09.860612 /PDM/CritSects/EM-REM/ContentionRZLock        0 times
00:00:09.860616 /PDM/CritSects/EM-REM/ContentionRZUnlock        0 times
00:00:09.860620 /PDM/CritSects/FTM/ContentionR3         0 times
00:00:09.860625 /PDM/CritSects/FTM/ContentionRZLock        0 times
00:00:09.860629 /PDM/CritSects/FTM/ContentionRZUnlock        0 times
00:00:09.860634 /PDM/CritSects/HPET#0/ContentionR3        0 times
00:00:09.860638 /PDM/CritSects/HPET#0/ContentionRZLock        0 times
00:00:09.860642 /PDM/CritSects/HPET#0/ContentionRZUnlock        0 times
00:00:09.860647 /PDM/CritSects/IOM Lock/ContentionR3        0 times
00:00:09.860651 /PDM/CritSects/IOM Lock/ContentionRZLock        0 times
00:00:09.860656 /PDM/CritSects/IOM Lock/ContentionRZUnlock        0 times
00:00:09.860660 /PDM/CritSects/MM-HYPER/ContentionR3        0 times
00:00:09.860664 /PDM/CritSects/MM-HYPER/ContentionRZLock        0 times
00:00:09.860668 /PDM/CritSects/MM-HYPER/ContentionRZUnlock        0 times
00:00:09.860673 /PDM/CritSects/NOP/ContentionR3         0 times
00:00:09.860677 /PDM/CritSects/NOP/ContentionRZLock        0 times
00:00:09.860681 /PDM/CritSects/NOP/ContentionRZUnlock        0 times
00:00:09.860686 /PDM/CritSects/PDM/ContentionR3         0 times
00:00:09.860690 /PDM/CritSects/PDM/ContentionRZLock        0 times
00:00:09.860694 /PDM/CritSects/PDM/ContentionRZUnlock        0 times
00:00:09.860699 /PDM/CritSects/PGM/ContentionR3         0 times
00:00:09.860703 /PDM/CritSects/PGM/ContentionRZLock        0 times
00:00:09.860707 /PDM/CritSects/PGM/ContentionRZUnlock        0 times
00:00:09.860712 /PDM/CritSects/PS2K#0/ContentionR3        0 times
00:00:09.860716 /PDM/CritSects/PS2K#0/ContentionRZLock        0 times
00:00:09.860720 /PDM/CritSects/PS2K#0/ContentionRZUnlock        0 times
00:00:09.860725 /PDM/CritSects/PS2KM#0/ContentionR3        0 times
00:00:09.860729 /PDM/CritSects/PS2KM#0/ContentionRZLock        0 times
00:00:09.860733 /PDM/CritSects/PS2KM#0/ContentionRZUnlock        0 times
00:00:09.860744 /PDM/CritSects/REM-Register/ContentionR3        0 times
00:00:09.860749 /PDM/CritSects/REM-Register/ContentionRZLock        0 times
00:00:09.860753 /PDM/CritSects/REM-Register/ContentionRZUnlock        0 times
00:00:09.860758 /PDM/CritSects/TM Timer Lock/ContentionR3        0 times
00:00:09.860762 /PDM/CritSects/TM Timer Lock/ContentionRZLock        0 times
00:00:09.860766 /PDM/CritSects/TM Timer Lock/ContentionRZUnlock        0 times
00:00:09.860771 /PDM/CritSects/TM VirtualSync Lock/ContentionR3        0 times
00:00:09.860775 /PDM/CritSects/TM VirtualSync Lock/ContentionRZLock        0 times
00:00:09.860779 /PDM/CritSects/TM VirtualSync Lock/ContentionRZUnlock        0 times
00:00:09.860784 /PDM/CritSects/VGA#u/ContentionR3        0 times
00:00:09.860788 /PDM/CritSects/VGA#u/ContentionRZLock        0 times
00:00:09.860792 /PDM/CritSects/VGA#u/ContentionRZUnlock        0 times
00:00:09.860797 /PDM/CritSects/VMMDev#0 Auto/ContentionR3        0 times
00:00:09.860801 /PDM/CritSects/VMMDev#0 Auto/ContentionRZLock        0 times
00:00:09.860805 /PDM/CritSects/VMMDev#0 Auto/ContentionRZUnlock        0 times
00:00:09.860810 /PDM/CritSects/VMMDev#u/ContentionR3        0 times
00:00:09.860814 /PDM/CritSects/VMMDev#u/ContentionRZLock        0 times
00:00:09.860819 /PDM/CritSects/VMMDev#u/ContentionRZUnlock        0 times
00:00:09.860823 /PDM/CritSects/acpi0/ContentionR3        0 times
00:00:09.860827 /PDM/CritSects/acpi0/ContentionRZLock        0 times
00:00:09.860831 /PDM/CritSects/acpi0/ContentionRZUnlock        0 times
00:00:09.860836 /PDM/CritSects/ich9pci#0 Auto/ContentionR3        0 times
00:00:09.860841 /PDM/CritSects/ich9pci#0 Auto/ContentionRZLock        0 times
00:00:09.860845 /PDM/CritSects/ich9pci#0 Auto/ContentionRZUnlock        0 times
00:00:09.860850 /PDM/CritSects/ichac97#0 Auto/ContentionR3        0 times
00:00:09.860854 /PDM/CritSects/ichac97#0 Auto/ContentionRZLock        0 times
00:00:09.860858 /PDM/CritSects/ichac97#0 Auto/ContentionRZUnlock        0 times
00:00:09.860863 /PDM/CritSects/lpc#0 Auto/ContentionR3        0 times
00:00:09.860867 /PDM/CritSects/lpc#0 Auto/ContentionRZLock        0 times
00:00:09.860871 /PDM/CritSects/lpc#0 Auto/ContentionRZUnlock        0 times
00:00:09.860876 /PDM/CritSects/mc146818#0 Auto/ContentionR3        0 times
00:00:09.860880 /PDM/CritSects/mc146818#0 Auto/ContentionRZLock        0 times
00:00:09.860884 /PDM/CritSects/mc146818#0 Auto/ContentionRZUnlock        0 times
00:00:09.860889 /PDM/CritSects/pcarch#0 Auto/ContentionR3        0 times
00:00:09.860893 /PDM/CritSects/pcarch#0 Auto/ContentionRZLock        0 times
00:00:09.860898 /PDM/CritSects/pcarch#0 Auto/ContentionRZUnlock        0 times
00:00:09.860902 /PDM/CritSects/pcbios#0 Auto/ContentionR3        0 times
00:00:09.860906 /PDM/CritSects/pcbios#0 Auto/ContentionRZLock        0 times
00:00:09.860911 /PDM/CritSects/pcbios#0 Auto/ContentionRZUnlock        0 times
00:00:09.860915 /PDM/CritSects/pckbd#0 Auto/ContentionR3        0 times
00:00:09.860919 /PDM/CritSects/pckbd#0 Auto/ContentionRZLock        0 times
00:00:09.860924 /PDM/CritSects/pckbd#0 Auto/ContentionRZUnlock        0 times
00:00:09.860928 /PDM/CritSects/piix3ide#0 Auto/ContentionR3        0 times
00:00:09.860932 /PDM/CritSects/piix3ide#0 Auto/ContentionRZLock        0 times
00:00:09.860937 /PDM/CritSects/piix3ide#0 Auto/ContentionRZUnlock        0 times
00:00:09.860941 /PDM/CritSects/pit/ContentionR3         0 times
00:00:09.860945 /PDM/CritSects/pit/ContentionRZLock        0 times
00:00:09.860949 /PDM/CritSects/pit/ContentionRZUnlock        0 times
00:00:09.860954 /PDM/CritSects/usb-ohci#0 Auto/ContentionR3        0 times
00:00:09.860958 /PDM/CritSects/usb-ohci#0 Auto/ContentionRZLock        0 times
00:00:09.860963 /PDM/CritSects/usb-ohci#0 Auto/ContentionRZUnlock        0 times
00:00:09.860967 /PDM/CritSects/vga#0 Auto/ContentionR3        0 times
00:00:09.860972 /PDM/CritSects/vga#0 Auto/ContentionRZLock        0 times
00:00:09.860976 /PDM/CritSects/vga#0 Auto/ContentionRZUnlock        0 times
00:00:09.860980 /PDM/Queue/DevHlp/AllocFailures         0 times
00:00:09.860992 /PDM/Queue/DevHlp/Flush                 0 calls
00:00:09.860996 /PDM/Queue/DevHlp/FlushLeftovers        0 times
00:00:09.861001 /PDM/Queue/DevHlp/Insert                0 calls
00:00:09.861005 /PDM/Queue/DevHlp/cItems                8 count
00:00:09.861010 /PDM/Queue/DevHlp/cbItem               40 bytes
00:00:09.861015 /PDM/Queue/Keyboard/AllocFailures        0 times
00:00:09.861019 /PDM/Queue/Keyboard/Flush               0 calls
00:00:09.861023 /PDM/Queue/Keyboard/FlushLeftovers        0 times
00:00:09.861028 /PDM/Queue/Keyboard/Insert              0 calls
00:00:09.861032 /PDM/Queue/Keyboard/cItems             64 count
00:00:09.861037 /PDM/Queue/Keyboard/cbItem             16 bytes
00:00:09.861042 /PDM/Queue/Mouse/AllocFailures          0 times
00:00:09.861046 /PDM/Queue/Mouse/Flush                  0 calls
00:00:09.861051 /PDM/Queue/Mouse/FlushLeftovers         0 times
00:00:09.861055 /PDM/Queue/Mouse/Insert                 0 calls
00:00:09.861060 /PDM/Queue/Mouse/cItems               128 count
00:00:09.861064 /PDM/Queue/Mouse/cbItem                48 bytes
00:00:09.861069 /PDM/Queue/Mouse_1/AllocFailures        0 times
00:00:09.861073 /PDM/Queue/Mouse_1/Flush                0 calls
00:00:09.861078 /PDM/Queue/Mouse_1/FlushLeftovers        0 times
00:00:09.861082 /PDM/Queue/Mouse_1/Insert               0 calls
00:00:09.861087 /PDM/Queue/Mouse_1/cItems             128 count
00:00:09.861091 /PDM/Queue/Mouse_1/cbItem              48 bytes
00:00:09.861096 /PGM/CPU0/cA20Changes                   1 times
00:00:09.861101 /PGM/CPU0/cGuestModeChanges             3 times
00:00:09.861105 /PGM/ChunkR3Map/Mapped                  5 count
00:00:09.861110 /PGM/ChunkR3Map/Unmapped                0 count
00:00:09.861115 /PGM/ChunkR3Map/c                       5 count
00:00:09.861119 /PGM/ChunkR3Map/cMax                  512 count
00:00:09.861124 /PGM/LargePage/Recheck                  0 times
00:00:09.861129 /PGM/LargePage/Refused                  0 times
00:00:09.861133 /PGM/LargePage/Reused                   0 times
00:00:09.861139 /PGM/Page/cAllPages                287786 count
00:00:09.861144 /PGM/Page/cBalloonedPages               0 count
00:00:09.861148 /PGM/Page/cHandyPages                 105 count
00:00:09.861153 /PGM/Page/cLargePages                   0 count
00:00:09.861157 /PGM/Page/cLargePagesDisabled           0 count
00:00:09.861162 /PGM/Page/cMonitoredPages               0 count
00:00:09.861166 /PGM/Page/cPrivatePages             11220 count
00:00:09.861171 /PGM/Page/cPureMmioPages            16392 count
00:00:09.861175 /PGM/Page/cReadLockedPages              0 count
00:00:09.861180 /PGM/Page/cReusedSharedPages            0 count
00:00:09.861184 /PGM/Page/cSharedPages                  0 count
00:00:09.861189 /PGM/Page/cWriteLockedPages             0 count
00:00:09.861193 /PGM/Page/cWrittenToPages               0 count
00:00:09.861197 /PGM/Page/cZeroPages               260174 count
00:00:09.861202 /PGM/ShMod/Check                        0 ticks/call (           0 ticks,       0 times, max         0, min      -1)
00:00:09.861208 /PGM/cRelocations                       0 times
00:00:09.861213 /PROF/CPU0/EM/Capped                    0 ticks/call (           0 ticks,       0 times, max         0, min      -1)
00:00:09.861219 /PROF/CPU0/EM/ForcedActions           176 times
00:00:09.861224 /PROF/CPU0/EM/Halted                  172 times
00:00:09.861229 /PROF/CPU0/EM/RAWTotal                  0 times
00:00:09.861233 /PROF/CPU0/EM/REMTotal                158 times
00:00:09.861238 /PROF/CPU0/EM/Total              9438381960 ticks/call (  9438381960 ticks,       1 times, max 9438381960, min 9438381960)
00:00:09.861247 /PROF/VM/CPU0/Halt/Block          2406575 ns/call (  2303092415 ticks,     957 times, max   5757539, min       1)
00:00:09.861254 /PROF/VM/CPU0/Halt/BlockInsomnia        0 ns/call (           0 ticks,       0 times, max         0, min      -1)
00:00:09.861260 /PROF/VM/CPU0/Halt/BlockOnTime          0 ns/call (           0 ticks,       0 times, max         0, min      -1)
00:00:09.861265 /PROF/VM/CPU0/Halt/BlockOverslept        0 ns/call (           0 ticks,       0 times, max         0, min      -1)
00:00:09.861278 /PROF/VM/CPU0/Halt/Timers           18128 ns/call (    20575687 ticks,    1135 times, max   8862130, min       2)
00:00:09.861285 /PROF/VM/CPU0/Halt/Yield                0 ns/call (           0 ticks,       0 times, max         0, min      -1)
00:00:09.861291 /REM/TbFlushCount                       0 times
00:00:09.861296 /REM/TbPhysInvldCount                  57 times
00:00:09.861301 /REM/TlbFlushCount                      5 times
00:00:09.861306 /SELM/HyperSels/Changed                 0 times
00:00:09.861310 /SELM/HyperSels/Scan                    0 times
00:00:09.861315 /SELM/LoadHidSel/GstReadErrors          0 times
00:00:09.861320 /SELM/LoadHidSel/NoGoodGuest            0 times
00:00:09.861324 /SELM/UpdateFromCPUM/AlreadyStaleCS        0 times
00:00:09.861328 /SELM/UpdateFromCPUM/AlreadyStaleDS        0 times
00:00:09.861333 /SELM/UpdateFromCPUM/AlreadyStaleES        0 times
00:00:09.861337 /SELM/UpdateFromCPUM/AlreadyStaleFS        0 times
00:00:09.861341 /SELM/UpdateFromCPUM/AlreadyStaleGS        0 times
00:00:09.861346 /SELM/UpdateFromCPUM/AlreadyStaleSS        0 times
00:00:09.861350 /SELM/UpdateFromCPUM/DetectedStaleCS        0 times
00:00:09.861354 /SELM/UpdateFromCPUM/DetectedStaleDS        0 times
00:00:09.861359 /SELM/UpdateFromCPUM/DetectedStaleES        0 times
00:00:09.861363 /SELM/UpdateFromCPUM/DetectedStaleFS        0 times
00:00:09.861367 /SELM/UpdateFromCPUM/DetectedStaleGS        0 times
00:00:09.861371 /SELM/UpdateFromCPUM/DetectedStaleSS        0 times
00:00:09.861376 /SELM/UpdateFromCPUM/StaleToUnstale        0 times
00:00:09.861381 /TM/CPU/00/cNsExecuting          783751717 ns
00:00:09.861386 /TM/CPU/00/cNsHalted             2327728977 ns
00:00:09.861391 /TM/CPU/00/cNsOther              593066150 ns
00:00:09.861397 /TM/CPU/00/cNsTotal              3704546844 ns
00:00:09.861402 /TM/CPU/00/cPeriodsExecuting          161 count
00:00:09.861407 /TM/CPU/00/cPeriodsHalted             172 count
00:00:09.861411 /TM/CPU/00/pctExecuting                 9 %
00:00:09.861416 /TM/CPU/00/pctHalted                   89 %
00:00:09.861421 /TM/CPU/00/pctOther                     0 %
00:00:09.861426 /TM/CPU/pctExecuting                    9 %
00:00:09.861430 /TM/CPU/pctHalted                      89 %
00:00:09.861435 /TM/CPU/pctOther                        0 %
00:00:09.861439 /TM/MaxHzHint                           0 Hz
00:00:09.861445 /TM/R3/1nsSteps                      1601 times
00:00:09.861450 /TM/TSC/offCPU0                         0 ticks
00:00:09.861454 /TM/VirtualSync/CurrentOffset     5596157 ns
00:00:09.861459 /VUSB/0/cUrbsInPool                     0 count
00:00:09.861464 ********************* End of statistics **********************
00:00:09.873517 Changing the VM state from 'DESTROYING' to 'TERMINATED'.

```

---

