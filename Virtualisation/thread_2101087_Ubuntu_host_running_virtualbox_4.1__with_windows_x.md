---
title: "Ubuntu host running virtualbox 4.1  with windows xp sp2 guest"
date: 2013-01-03
forum: Virtualisation
---

### Post by MontrealCorp on 2013-01-03
hi, this is my first post so give me a chance :)

i decide last week to change from windows to Ubuntu 12.04 , so i am a new user too.
until now, i am pretty happy about my migration :)

what are the risk of not upgrading windows XP sp2 if i do not plan of using this OS much beside playing video games and reading forum in a virtual setting ?

why not sp3 ?
situation : i install virtual box on my ubuntu 12.04 , i install windows xp sp2 on my virtual machine ( everything went well) to upgrade it to sp3 in virtual box .
i do not have the windows xp sp3 cd  so i have no choice to use sp2 :( .
i have my sp3 package on my window xp virtual HD on the desktop.
everything goes well ( extracting and backing up file ) until when the work of upgrading to sp3  actually begin, window just shut down and i see virtualbox program saying it got aborted.

it seem i will never be able to upgrade my windows xp 2 to sp3 in virtualbox, i have search a lot and could not find any solution .

here is the log :

 ```
p, li { white-space: pre-wrap; }  VirtualBox VM 4.2.6 r82870 linux.x86 (Dec 19 2012 14:55:50) release log
 00:00:00.700914 Log opened 2013-01-03T19:45:06.308494000Z
 00:00:00.700919 OS Product: Linux
 00:00:00.700920 OS Release: 3.2.0-35-generic-pae
 00:00:00.700921 OS Version: #55-Ubuntu SMP Wed Dec 5 18:04:39 UTC 2012
 00:00:00.700948 DMI Product Name: System Product Name
 00:00:00.700956 DMI Product Version: System Version
 00:00:00.700968 Host RAM: 3774MB total, 3073MB available
 00:00:00.700972 Executable: /usr/lib/virtualbox/VirtualBox
 00:00:00.700973 Process ID: 2653
 00:00:00.700974 Package type: LINUX_32BITS_UBUNTU_12_04
 00:00:00.755042 Installed Extension Packs:
 00:00:00.755061   Oracle VM VirtualBox Extension Pack (Version: 4.2.6 r82870; VRDE Module: VBoxVRDP)
 00:00:00.763103 Using XKB for keycode to scan code conversion
 00:00:00.801015 SUP: Loaded VMMR0.r0 (/usr/lib/virtualbox/VMMR0.r0) at 0xfc8cd020 - ModuleInit at 00000000fc8e3560 and ModuleTerm at 00000000fc8e38c0
 00:00:00.801102 SUP: VMMR0EntryEx located at 00000000fc8e4a80, VMMR0EntryFast at 00000000fc8e47d0 and VMMR0EntryInt at 00000000fc8e47c0
 00:00:00.811795 OS type: 'WindowsXP'
 00:00:00.834933 File system of '/home/simon/VirtualBox VMs/Windows XP sp2 with sp3 manually/Snapshots' (snapshots) is unknown
 00:00:00.834998 File system of '/home/simon/VirtualBox VMs/Windows XP sp2 with sp3 manually/Windows XP sp2 with sp3 manually.vdi' is ext4
 00:00:00.877628 Shared clipboard mode: Off
 00:00:00.888091 Drag'n'drop mode: Off
 00:00:00.924813 ************************* CFGM dump *************************
 00:00:00.924817 [/] (level 0)
 00:00:00.924823   CSAMEnabled     <integer> = 0x0000000000000001 (1)
 00:00:00.924870   CpuExecutionCap <integer> = 0x0000000000000064 (100)
 00:00:00.924872   EnablePAE       <integer> = 0x0000000000000000 (0)
 00:00:00.924873   HwVirtExtForced <integer> = 0x0000000000000000 (0)
 00:00:00.924874   MemBalloonSize  <integer> = 0x0000000000000000 (0)
 00:00:00.924875   Name            <string>  = "Windows XP sp2 with sp3 manually" (cb=33)
 00:00:00.924877   NumCPUs         <integer> = 0x0000000000000001 (1)
 00:00:00.924878   PATMEnabled     <integer> = 0x0000000000000001 (1)
 00:00:00.924879   PageFusion      <integer> = 0x0000000000000000 (0)
 00:00:00.924880   RamHoleSize     <integer> = 0x0000000020000000 (536 870 912, 512 MB)
 00:00:00.924883   RamSize         <integer> = 0x000000006d600000 (1 835 008 000, 1 750 MB)
 00:00:00.924885   RawR0Enabled    <integer> = 0x0000000000000001 (1)
 00:00:00.924887   RawR3Enabled    <integer> = 0x0000000000000001 (1)
 00:00:00.924888   TimerMillies    <integer> = 0x000000000000000a (10)
 00:00:00.924889   UUID            <bytes>   = "0d b0 63 ca 06 2e 52 44 9e 51 29 9d 55 e5 dd c7" (cb=16)
 00:00:00.924893 
 00:00:00.924894 [/CPUM/] (level 1)
 00:00:00.924895   SyntheticCpu <integer> = 0x0000000000000000 (0)
 00:00:00.924896 
 00:00:00.924897 [/DBGF/] (level 1)
 00:00:00.924898   Path <string>  = "/home/simon/VirtualBox VMs/Windows XP sp2 with sp3 manually/debug/;/home/simon/VirtualBox VMs/Windows XP sp2 with sp3 manually/;/home/simon/" (cb=141)
 00:00:00.924900 
 00:00:00.924900 [/Devices/] (level 1)
 00:00:00.924901 
 00:00:00.924902 [/Devices/8237A/] (level 2)
 00:00:00.924903 
 00:00:00.924904 [/Devices/8237A/0/] (level 3)
 00:00:00.924905   Trusted <integer> = 0x0000000000000001 (1)
 00:00:00.924906 
 00:00:00.924907 [/Devices/AudioSniffer/] (level 2)
 00:00:00.924909 
 00:00:00.924909 [/Devices/AudioSniffer/0/] (level 3)
 00:00:00.924911 
 00:00:00.924911 [/Devices/AudioSniffer/0/Config/] (level 4)
 00:00:00.924913 
 00:00:00.924913 [/Devices/AudioSniffer/0/LUN#0/] (level 4)
 00:00:00.924915   Driver <string>  = "MainAudioSniffer" (cb=17)
 00:00:00.924916 
 00:00:00.924917 [/Devices/AudioSniffer/0/LUN#0/Config/] (level 5)
 00:00:00.924919   Object <integer> = 0x00000000b03018e0 (2 955 942 112)
 00:00:00.924920 
 00:00:00.924921 [/Devices/VMMDev/] (level 2)
 00:00:00.924923 
 00:00:00.924923 [/Devices/VMMDev/0/] (level 3)
 00:00:00.924925   PCIBusNo      <integer> = 0x0000000000000000 (0)
 00:00:00.924926   PCIDeviceNo   <integer> = 0x0000000000000004 (4)
 00:00:00.924927   PCIFunctionNo <integer> = 0x0000000000000000 (0)
 00:00:00.924928   Trusted       <integer> = 0x0000000000000001 (1)
 00:00:00.924930 
 00:00:00.924930 [/Devices/VMMDev/0/Config/] (level 4)
 00:00:00.924932   GuestCoreDumpDir <string>  = "/home/simon/VirtualBox VMs/Windows XP sp2 with sp3 manually/Snapshots" (cb=70)
 00:00:00.924933   RamSize          <integer> = 0x000000006d600000 (1 835 008 000, 1 750 MB)
 00:00:00.924935 
 00:00:00.924936 [/Devices/VMMDev/0/LUN#0/] (level 4)
 00:00:00.924938   Driver <string>  = "HGCM" (cb=5)
 00:00:00.924939 
 00:00:00.924939 [/Devices/VMMDev/0/LUN#0/Config/] (level 5)
 00:00:00.924942   Object <integer> = 0x00000000b170c1b8 (2 976 956 856)
 00:00:00.924943 
 00:00:00.924944 [/Devices/VMMDev/0/LUN#999/] (level 4)
 00:00:00.924946   Driver <string>  = "MainStatus" (cb=11)
 00:00:00.924947 
 00:00:00.924947 [/Devices/VMMDev/0/LUN#999/Config/] (level 5)
 00:00:00.924949   First   <integer> = 0x0000000000000000 (0)
 00:00:00.924950   Last    <integer> = 0x0000000000000000 (0)
 00:00:00.924952   papLeds <integer> = 0x00000000b03013cc (2 955 940 812)
 00:00:00.924953 
 00:00:00.924954 [/Devices/acpi/] (level 2)
 00:00:00.924955 
 00:00:00.924956 [/Devices/acpi/0/] (level 3)
 00:00:00.924958   PCIBusNo      <integer> = 0x0000000000000000 (0)
 00:00:00.924959   PCIDeviceNo   <integer> = 0x0000000000000007 (7)
 00:00:00.924960   PCIFunctionNo <integer> = 0x0000000000000000 (0)
 00:00:00.924961   Trusted       <integer> = 0x0000000000000001 (1)
 00:00:00.924963 
 00:00:00.924963 [/Devices/acpi/0/Config/] (level 4)
 00:00:00.924966   CpuHotPlug        <integer> = 0x0000000000000000 (0)
 00:00:00.924967   FdcEnabled        <integer> = 0x0000000000000000 (0)
 00:00:00.924968   HostBusPciAddress <integer> = 0x0000000000000000 (0)
 00:00:00.924970   HpetEnabled       <integer> = 0x0000000000000000 (0)
 00:00:00.924971   IOAPIC            <integer> = 0x0000000000000001 (1)
 00:00:00.924972   IocPciAddress     <integer> = 0x0000000000010000 (65 536)
 00:00:00.924974   NumCPUs           <integer> = 0x0000000000000001 (1)
 00:00:00.924975   RamHoleSize       <integer> = 0x0000000020000000 (536 870 912, 512 MB)
 00:00:00.924977   RamSize           <integer> = 0x000000006d600000 (1 835 008 000, 1 750 MB)
 00:00:00.924980   Serial0IoPortBase <integer> = 0x0000000000000000 (0)
 00:00:00.924981   Serial0Irq        <integer> = 0x0000000000000000 (0)
 00:00:00.924982   Serial1IoPortBase <integer> = 0x0000000000000000 (0)
 00:00:00.924983   Serial1Irq        <integer> = 0x0000000000000000 (0)
 00:00:00.924985   ShowCpu           <integer> = 0x0000000000000001 (1)
 00:00:00.924986   ShowRtc           <integer> = 0x0000000000000000 (0)
 00:00:00.924987   SmcEnabled        <integer> = 0x0000000000000000 (0)
 00:00:00.924988 
 00:00:00.924989 [/Devices/acpi/0/LUN#0/] (level 4)
 00:00:00.924991   Driver <string>  = "ACPIHost" (cb=9)
 00:00:00.924992 
 00:00:00.924992 [/Devices/acpi/0/LUN#0/Config/] (level 5)
 00:00:00.924994 
 00:00:00.924995 [/Devices/apic/] (level 2)
 00:00:00.924996 
 00:00:00.924997 [/Devices/apic/0/] (level 3)
 00:00:00.924998   Trusted <integer> = 0x0000000000000001 (1)
 00:00:00.925000 
 00:00:00.925000 [/Devices/apic/0/Config/] (level 4)
 00:00:00.925002   IOAPIC  <integer> = 0x0000000000000001 (1)
 00:00:00.925003   NumCPUs <integer> = 0x0000000000000001 (1)
 00:00:00.925004 
 00:00:00.925005 [/Devices/e1000/] (level 2)
 00:00:00.925006 
 00:00:00.925007 [/Devices/i8254/] (level 2)
 00:00:00.925008 
 00:00:00.925009 [/Devices/i8254/0/] (level 3)
 00:00:00.925010 
 00:00:00.925011 [/Devices/i8254/0/Config/] (level 4)
 00:00:00.925013 
 00:00:00.925013 [/Devices/i8259/] (level 2)
 00:00:00.925015 
 00:00:00.925015 [/Devices/i8259/0/] (level 3)
 00:00:00.925017   Trusted <integer> = 0x0000000000000001 (1)
 00:00:00.925018 
 00:00:00.925018 [/Devices/i8259/0/Config/] (level 4)
 00:00:00.925020 
 00:00:00.925021 [/Devices/ichac97/] (level 2)
 00:00:00.925022 
 00:00:00.925022 [/Devices/ichac97/0/] (level 3)
 00:00:00.925024   PCIBusNo      <integer> = 0x0000000000000000 (0)
 00:00:00.925025   PCIDeviceNo   <integer> = 0x0000000000000005 (5)
 00:00:00.925027   PCIFunctionNo <integer> = 0x0000000000000000 (0)
 00:00:00.925028   Trusted       <integer> = 0x0000000000000001 (1)
 00:00:00.925029 
 00:00:00.925029 [/Devices/ichac97/0/Config/] (level 4)
 00:00:00.925031 
 00:00:00.925032 [/Devices/ichac97/0/LUN#0/] (level 4)
 00:00:00.925034   Driver <string>  = "AUDIO" (cb=6)
 00:00:00.925034 
 00:00:00.925035 [/Devices/ichac97/0/LUN#0/Config/] (level 5)
 00:00:00.925037   AudioDriver <string>  = "pulse" (cb=6)
 00:00:00.925038   StreamName  <string>  = "Windows XP sp2 with sp3 manually" (cb=33)
 00:00:00.925039 
 00:00:00.925039 [/Devices/ioapic/] (level 2)
 00:00:00.925041 
 00:00:00.925041 [/Devices/ioapic/0/] (level 3)
 00:00:00.925043   Trusted <integer> = 0x0000000000000001 (1)
 00:00:00.925044 
 00:00:00.925044 [/Devices/ioapic/0/Config/] (level 4)
 00:00:00.925046   NumCPUs <integer> = 0x0000000000000001 (1)
 00:00:00.925047 
 00:00:00.925048 [/Devices/mc146818/] (level 2)
 00:00:00.925049 
 00:00:00.925050 [/Devices/mc146818/0/] (level 3)
 00:00:00.925052 
 00:00:00.925052 [/Devices/mc146818/0/Config/] (level 4)
 00:00:00.925054   UseUTC <integer> = 0x0000000000000000 (0)
 00:00:00.925055 
 00:00:00.925056 [/Devices/parallel/] (level 2)
 00:00:00.925057 
 00:00:00.925057 [/Devices/pcarch/] (level 2)
 00:00:00.925059 
 00:00:00.925059 [/Devices/pcarch/0/] (level 3)
 00:00:00.925061   Trusted <integer> = 0x0000000000000001 (1)
 00:00:00.925062 
 00:00:00.925063 [/Devices/pcarch/0/Config/] (level 4)
 00:00:00.925064 
 00:00:00.925065 [/Devices/pcbios/] (level 2)
 00:00:00.925066 
 00:00:00.925067 [/Devices/pcbios/0/] (level 3)
 00:00:00.925068   Trusted <integer> = 0x0000000000000001 (1)
 00:00:00.925070 
 00:00:00.925070 [/Devices/pcbios/0/Config/] (level 4)
 00:00:00.925072   BootDevice0    <string>  = "DVD" (cb=4)
 00:00:00.925073   BootDevice1    <string>  = "IDE" (cb=4)
 00:00:00.925074   BootDevice2    <string>  = "NONE" (cb=5)
 00:00:00.925075   BootDevice3    <string>  = "NONE" (cb=5)
 00:00:00.925076   FloppyDevice   <string>  = "i82078" (cb=7)
 00:00:00.925077   HardDiskDevice <string>  = "piix3ide" (cb=9)
 00:00:00.925078   IOAPIC         <integer> = 0x0000000000000001 (1)
 00:00:00.925079   LanBootRom     <string>  = "/usr/lib/virtualbox/ExtensionPacks/Oracle_VM_VirtualBox_Extension_Pack/PXE-Intel.rom" (cb=85)
 00:00:00.925080   McfgBase       <integer> = 0x0000000000000000 (0)
 00:00:00.925081   McfgLength     <integer> = 0x0000000000000000 (0)
 00:00:00.925083   NumCPUs        <integer> = 0x0000000000000001 (1)
 00:00:00.925084   PXEDebug       <integer> = 0x0000000000000000 (0)
 00:00:00.925085   RamHoleSize    <integer> = 0x0000000020000000 (536 870 912, 512 MB)
 00:00:00.925087   RamSize        <integer> = 0x000000006d600000 (1 835 008 000, 1 750 MB)
 00:00:00.925089   UUID           <bytes>   = "0d b0 63 ca 06 2e 52 44 9e 51 29 9d 55 e5 dd c7" (cb=16)
 00:00:00.925093 
 00:00:00.925093 [/Devices/pcbios/0/Config/NetBoot/] (level 5)
 00:00:00.925095 
 00:00:00.925096 [/Devices/pcbios/0/Config/NetBoot/0/] (level 6)
 00:00:00.925098   NIC           <integer> = 0x0000000000000000 (0)
 00:00:00.925100   PCIBusNo      <integer> = 0x0000000000000000 (0)
 00:00:00.925101   PCIDeviceNo   <integer> = 0x0000000000000003 (3)
 00:00:00.925102   PCIFunctionNo <integer> = 0x0000000000000000 (0)
 00:00:00.925103 
 00:00:00.925104 [/Devices/pci/] (level 2)
 00:00:00.925105 
 00:00:00.925106 [/Devices/pci/0/] (level 3)
 00:00:00.925107   Trusted <integer> = 0x0000000000000001 (1)
 00:00:00.925108 
 00:00:00.925109 [/Devices/pci/0/Config/] (level 4)
 00:00:00.925111   IOAPIC <integer> = 0x0000000000000001 (1)
 00:00:00.925112 
 00:00:00.925112 [/Devices/pckbd/] (level 2)
 00:00:00.925114 
 00:00:00.925114 [/Devices/pckbd/0/] (level 3)
 00:00:00.925116   Trusted <integer> = 0x0000000000000001 (1)
 00:00:00.925117 
 00:00:00.925118 [/Devices/pckbd/0/Config/] (level 4)
 00:00:00.925119 
 00:00:00.925120 [/Devices/pckbd/0/LUN#0/] (level 4)
 00:00:00.925122   Driver <string>  = "KeyboardQueue" (cb=14)
 00:00:00.925123 
 00:00:00.925123 [/Devices/pckbd/0/LUN#0/AttachedDriver/] (level 5)
 00:00:00.925125   Driver <string>  = "MainKeyboard" (cb=13)
 00:00:00.925126 
 00:00:00.925127 [/Devices/pckbd/0/LUN#0/AttachedDriver/Config/] (level 6)
 00:00:00.925129   Object <integer> = 0x00000000b030a828 (2 955 978 792)
 00:00:00.925131 
 00:00:00.925131 [/Devices/pckbd/0/LUN#0/Config/] (level 5)
 00:00:00.925133   QueueSize <integer> = 0x0000000000000040 (64)
 00:00:00.925134 
 00:00:00.925135 [/Devices/pckbd/0/LUN#1/] (level 4)
 00:00:00.925137   Driver <string>  = "MouseQueue" (cb=11)
 00:00:00.925138 
 00:00:00.925138 [/Devices/pckbd/0/LUN#1/AttachedDriver/] (level 5)
 00:00:00.925140   Driver <string>  = "MainMouse" (cb=10)
 00:00:00.925141 
 00:00:00.925142 [/Devices/pckbd/0/LUN#1/AttachedDriver/Config/] (level 6)
 00:00:00.925144   Object <integer> = 0x00000000b030d4f0 (2 955 990 256)
 00:00:00.925146 
 00:00:00.925146 [/Devices/pckbd/0/LUN#1/Config/] (level 5)
 00:00:00.925148   QueueSize <integer> = 0x0000000000000080 (128)
 00:00:00.925149 
 00:00:00.925150 [/Devices/pcnet/] (level 2)
 00:00:00.925151 
 00:00:00.925152 [/Devices/pcnet/0/] (level 3)
 00:00:00.925154   PCIBusNo      <integer> = 0x0000000000000000 (0)
 00:00:00.925155   PCIDeviceNo   <integer> = 0x0000000000000003 (3)
 00:00:00.925156   PCIFunctionNo <integer> = 0x0000000000000000 (0)
 00:00:00.925157   Trusted       <integer> = 0x0000000000000001 (1)
 00:00:00.925159 
 00:00:00.925159 [/Devices/pcnet/0/Config/] (level 4)
 00:00:00.925161   Am79C973       <integer> = 0x0000000000000001 (1)
 00:00:00.925162   CableConnected <integer> = 0x0000000000000001 (1)
 00:00:00.925163   LineSpeed      <integer> = 0x0000000000000000 (0)
 00:00:00.925165   MAC            <bytes>   = "08 00 27 7a 57 ca" (cb=6)
 00:00:00.925167 
 00:00:00.925167 [/Devices/pcnet/0/LUN#0/] (level 4)
 00:00:00.925169   Driver <string>  = "IntNet" (cb=7)
 00:00:00.925170 
 00:00:00.925170 [/Devices/pcnet/0/LUN#0/Config/] (level 5)
 00:00:00.925173   IfPolicyPromisc      <string>  = "deny" (cb=5)
 00:00:00.925174   IgnoreConnectFailure <integer> = 0x0000000000000000 (0)
 00:00:00.925175   Network              <string>  = "HostInterfaceNetworking-wlan0" (cb=30)
 00:00:00.925176   SharedMacOnWire      <integer> = 0x0000000000000001 (1)
 00:00:00.925177   Trunk                <string>  = "wlan0" (cb=6)
 00:00:00.925179   TrunkType            <integer> = 0x0000000000000003 (3)
 00:00:00.925180 
 00:00:00.925181 [/Devices/pcnet/0/LUN#999/] (level 4)
 00:00:00.925183   Driver <string>  = "MainStatus" (cb=11)
 00:00:00.925183 
 00:00:00.925184 [/Devices/pcnet/0/LUN#999/Config/] (level 5)
 00:00:00.925186   First   <integer> = 0x0000000000000000 (0)
 00:00:00.925187   Last    <integer> = 0x0000000000000000 (0)
 00:00:00.925188   papLeds <integer> = 0x00000000b030133c (2 955 940 668)
 00:00:00.925190 
 00:00:00.925191 [/Devices/piix3ide/] (level 2)
 00:00:00.925192 
 00:00:00.925193 [/Devices/piix3ide/0/] (level 3)
 00:00:00.925195   PCIBusNo      <integer> = 0x0000000000000000 (0)
 00:00:00.925196   PCIDeviceNo   <integer> = 0x0000000000000001 (1)
 00:00:00.925197   PCIFunctionNo <integer> = 0x0000000000000001 (1)
 00:00:00.925198   Trusted       <integer> = 0x0000000000000001 (1)
 00:00:00.925199 
 00:00:00.925200 [/Devices/piix3ide/0/Config/] (level 4)
 00:00:00.925202   Type <string>  = "PIIX4" (cb=6)
 00:00:00.925203 
 00:00:00.925203 [/Devices/piix3ide/0/Config/PrimaryMaster/] (level 5)
 00:00:00.925206   NonRotationalMedium <integer> = 0x0000000000000000 (0)
 00:00:00.925207 
 00:00:00.925207 [/Devices/piix3ide/0/Config/SecondaryMaster/] (level 5)
 00:00:00.925210   NonRotationalMedium <integer> = 0x0000000000000000 (0)
 00:00:00.925211 
 00:00:00.925211 [/Devices/piix3ide/0/LUN#0/] (level 4)
 00:00:00.925213   Driver <string>  = "Block" (cb=6)
 00:00:00.925214 
 00:00:00.925215 [/Devices/piix3ide/0/LUN#0/AttachedDriver/] (level 5)
 00:00:00.925217   Driver <string>  = "VD" (cb=3)
 00:00:00.925218 
 00:00:00.925219 [/Devices/piix3ide/0/LUN#0/AttachedDriver/Config/] (level 6)
 00:00:00.925221   Format <string>  = "VDI" (cb=4)
 00:00:00.925222   Path   <string>  = "/home/simon/VirtualBox VMs/Windows XP sp2 with sp3 manually/Windows XP sp2 with sp3 manually.vdi" (cb=97)
 00:00:00.925223   Type   <string>  = "HardDisk" (cb=9)
 00:00:00.925224 
 00:00:00.925225 [/Devices/piix3ide/0/LUN#0/Config/] (level 5)
 00:00:00.925227   Mountable <integer> = 0x0000000000000000 (0)
 00:00:00.925228   Type      <string>  = "HardDisk" (cb=9)
 00:00:00.925229 
 00:00:00.925230 [/Devices/piix3ide/0/LUN#2/] (level 4)
 00:00:00.925232   Driver <string>  = "Block" (cb=6)
 00:00:00.925232 
 00:00:00.925233 [/Devices/piix3ide/0/LUN#2/Config/] (level 5)
 00:00:00.925235   Mountable <integer> = 0x0000000000000001 (1)
 00:00:00.925236   Type      <string>  = "DVD" (cb=4)
 00:00:00.925237 
 00:00:00.925238 [/Devices/piix3ide/0/LUN#999/] (level 4)
 00:00:00.925239   Driver <string>  = "MainStatus" (cb=11)
 00:00:00.925240 
 00:00:00.925241 [/Devices/piix3ide/0/LUN#999/Config/] (level 5)
 00:00:00.925243   DeviceInstance        <string>  = "piix3ide/0" (cb=11)
 00:00:00.925244   First                 <integer> = 0x0000000000000000 (0)
 00:00:00.925246   Last                  <integer> = 0x0000000000000003 (3)
 00:00:00.925247   pConsole              <integer> = 0x00000000b0301060 (2 955 939 936)
 00:00:00.925249   papLeds               <integer> = 0x00000000b0301254 (2 955 940 436)
 00:00:00.925251   pmapMediumAttachments <integer> = 0x00000000b03013d8 (2 955 940 824)
 00:00:00.925253 
 00:00:00.925254 [/Devices/serial/] (level 2)
 00:00:00.925255 
 00:00:00.925256 [/Devices/usb-ehci/] (level 2)
 00:00:00.925257 
 00:00:00.925258 [/Devices/usb-ehci/0/] (level 3)
 00:00:00.925259   PCIBusNo      <integer> = 0x0000000000000000 (0)
 00:00:00.925261   PCIDeviceNo   <integer> = 0x000000000000000b (11)
 00:00:00.925262   PCIFunctionNo <integer> = 0x0000000000000000 (0)
 00:00:00.925263   Trusted       <integer> = 0x0000000000000001 (1)
 00:00:00.925264 
 00:00:00.925265 [/Devices/usb-ehci/0/Config/] (level 4)
 00:00:00.925266 
 00:00:00.925267 [/Devices/usb-ehci/0/LUN#0/] (level 4)
 00:00:00.925269   Driver <string>  = "VUSBRootHub" (cb=12)
 00:00:00.925270 
 00:00:00.925270 [/Devices/usb-ehci/0/LUN#0/Config/] (level 5)
 00:00:00.925272 
 00:00:00.925273 [/Devices/usb-ehci/0/LUN#999/] (level 4)
 00:00:00.925274   Driver <string>  = "MainStatus" (cb=11)
 00:00:00.925275 
 00:00:00.925276 [/Devices/usb-ehci/0/LUN#999/Config/] (level 5)
 00:00:00.925278   First   <integer> = 0x0000000000000000 (0)
 00:00:00.925279   Last    <integer> = 0x0000000000000000 (0)
 00:00:00.925280   papLeds <integer> = 0x00000000b03013d4 (2 955 940 820)
 00:00:00.925282 
 00:00:00.925282 [/Devices/usb-ohci/] (level 2)
 00:00:00.925284 
 00:00:00.925284 [/Devices/usb-ohci/0/] (level 3)
 00:00:00.925286   PCIBusNo      <integer> = 0x0000000000000000 (0)
 00:00:00.925287   PCIDeviceNo   <integer> = 0x0000000000000006 (6)
 00:00:00.925288   PCIFunctionNo <integer> = 0x0000000000000000 (0)
 00:00:00.925290   Trusted       <integer> = 0x0000000000000001 (1)
 00:00:00.925291 
 00:00:00.925291 [/Devices/usb-ohci/0/Config/] (level 4)
 00:00:00.925293 
 00:00:00.925294 [/Devices/usb-ohci/0/LUN#0/] (level 4)
 00:00:00.925295   Driver <string>  = "VUSBRootHub" (cb=12)
 00:00:00.925296 
 00:00:00.925297 [/Devices/usb-ohci/0/LUN#0/Config/] (level 5)
 00:00:00.925299 
 00:00:00.925299 [/Devices/usb-ohci/0/LUN#999/] (level 4)
 00:00:00.925301   Driver <string>  = "MainStatus" (cb=11)
 00:00:00.925302 
 00:00:00.925302 [/Devices/usb-ohci/0/LUN#999/Config/] (level 5)
 00:00:00.925304   First   <integer> = 0x0000000000000000 (0)
 00:00:00.925306   Last    <integer> = 0x0000000000000000 (0)
 00:00:00.925307   papLeds <integer> = 0x00000000b03013d0 (2 955 940 816)
 00:00:00.925308 
 00:00:00.925309 [/Devices/vga/] (level 2)
 00:00:00.925310 
 00:00:00.925311 [/Devices/vga/0/] (level 3)
 00:00:00.925313   PCIBusNo      <integer> = 0x0000000000000000 (0)
 00:00:00.925314   PCIDeviceNo   <integer> = 0x0000000000000002 (2)
 00:00:00.925315   PCIFunctionNo <integer> = 0x0000000000000000 (0)
 00:00:00.925316   Trusted       <integer> = 0x0000000000000001 (1)
 00:00:00.925317 
 00:00:00.925318 [/Devices/vga/0/Config/] (level 4)
 00:00:00.925320   CustomVideoModes <integer> = 0x0000000000000000 (0)
 00:00:00.925321   FadeIn           <integer> = 0x0000000000000001 (1)
 00:00:00.925323   FadeOut          <integer> = 0x0000000000000001 (1)
 00:00:00.925324   HeightReduction  <integer> = 0x0000000000000000 (0)
 00:00:00.925325   LogoFile         <string>  = "" (cb=1)
 00:00:00.925326   LogoTime         <integer> = 0x0000000000000000 (0)
 00:00:00.925327   MonitorCount     <integer> = 0x0000000000000001 (1)
 00:00:00.925329   ShowBootMenu     <integer> = 0x0000000000000002 (2)
 00:00:00.925330   VRamSize         <integer> = 0x0000000008000000 (134 217 728, 128 MB)
 00:00:00.925332 
 00:00:00.925332 [/Devices/vga/0/LUN#0/] (level 4)
 00:00:00.925334   Driver <string>  = "MainDisplay" (cb=12)
 00:00:00.925335 
 00:00:00.925336 [/Devices/vga/0/LUN#0/Config/] (level 5)
 00:00:00.925338   Object <integer> = 0x00000000b030ad40 (2 955 980 096)
 00:00:00.925340 
 00:00:00.925340 [/Devices/virtio-net/] (level 2)
 00:00:00.925342 
 00:00:00.925342 [/HWVirtExt/] (level 1)
 00:00:00.925344   64bitEnabled       <integer> = 0x0000000000000000 (0)
 00:00:00.925345   EnableLargePages   <integer> = 0x0000000000000000 (0)
 00:00:00.925346   EnableNestedPaging <integer> = 0x0000000000000001 (1)
 00:00:00.925347   EnableVPID         <integer> = 0x0000000000000001 (1)
 00:00:00.925349   Enabled            <integer> = 0x0000000000000001 (1)
 00:00:00.925350   Exclusive          <integer> = 0x0000000000000001 (1)
 00:00:00.925351   TPRPatchingEnabled <integer> = 0x0000000000000001 (1)
 00:00:00.925352 
 00:00:00.925353 [/MM/] (level 1)
 00:00:00.925354   CanUseLargerHeap <integer> = 0x0000000000000000 (0)
 00:00:00.925355 
 00:00:00.925356 [/PDM/] (level 1)
 00:00:00.925357 
 00:00:00.925357 [/PDM/AsyncCompletion/] (level 2)
 00:00:00.925359 
 00:00:00.925359 [/PDM/AsyncCompletion/File/] (level 3)
 00:00:00.925361 
 00:00:00.925361 [/PDM/AsyncCompletion/File/BwGroups/] (level 4)
 00:00:00.925363 
 00:00:00.925364 [/PDM/BlkCache/] (level 2)
 00:00:00.925365   CacheSize <integer> = 0x0000000000500000 (5 242 880, 5 MB)
 00:00:00.925367 
 00:00:00.925368 [/PDM/Devices/] (level 2)
 00:00:00.925369 
 00:00:00.925369 [/PDM/Devices/VBoxEhci/] (level 3)
 00:00:00.925371   Path         <string>  = "/usr/lib/virtualbox/ExtensionPacks/Oracle_VM_VirtualBox_Extension_Pack/linux.x86/VBoxEhciR3.so" (cb=95)
 00:00:00.925372   R0SearchPath <string>  = "/usr/lib/virtualbox/ExtensionPacks/Oracle_VM_VirtualBox_Extension_Pack/linux.x86" (cb=81)
 00:00:00.925373   RCSearchPath <string>  = "/usr/lib/virtualbox/ExtensionPacks/Oracle_VM_VirtualBox_Extension_Pack/linux.x86" (cb=81)
 00:00:00.925374 
 00:00:00.925375 [/PDM/Devices/VBoxPciRaw/] (level 3)
 00:00:00.925376   Path         <string>  = "/usr/lib/virtualbox/ExtensionPacks/Oracle_VM_VirtualBox_Extension_Pack/linux.x86/VBoxPciRawR3.so" (cb=97)
 00:00:00.925378   R0SearchPath <string>  = "/usr/lib/virtualbox/ExtensionPacks/Oracle_VM_VirtualBox_Extension_Pack/linux.x86" (cb=81)
 00:00:00.925379 
 00:00:00.925379 [/PDM/Drivers/] (level 2)
 00:00:00.925381 
 00:00:00.925381 [/PDM/Drivers/VBoxC/] (level 3)
 00:00:00.925383   Path <string>  = "/usr/lib/virtualbox/components/VBoxC" (cb=37)
 00:00:00.925384 
 00:00:00.925384 [/PDM/Drivers/VBoxPciRawDrv/] (level 3)
 00:00:00.925386   Path <string>  = "/usr/lib/virtualbox/ExtensionPacks/Oracle_VM_VirtualBox_Extension_Pack/linux.x86/VBoxPciRawDrv.so" (cb=98)
 00:00:00.925387 
 00:00:00.925387 [/PDM/NetworkShaper/] (level 2)
 00:00:00.925389 
 00:00:00.925389 [/PDM/NetworkShaper/BwGroups/] (level 3)
 00:00:00.925391 
 00:00:00.925391 [/PDM/USB/] (level 2)
 00:00:00.925393 
 00:00:00.925393 [/PDM/USB/VBoxUsbCardReader/] (level 3)
 00:00:00.925395   Path <string>  = "/usr/lib/virtualbox/ExtensionPacks/Oracle_VM_VirtualBox_Extension_Pack/linux.x86/VBoxUsbCardReaderR3.so" (cb=104)
 00:00:00.925396 
 00:00:00.925396 [/TM/] (level 1)
 00:00:00.925398   UTCOffset <integer> = 0x0000000000000000 (0)
 00:00:00.925399 
 00:00:00.925399 [/USB/] (level 1)
 00:00:00.925400 
 00:00:00.925401 [/USB/HidMouse/] (level 2)
 00:00:00.925402 
 00:00:00.925403 [/USB/HidMouse/0/] (level 3)
 00:00:00.925405 
 00:00:00.925405 [/USB/HidMouse/0/Config/] (level 4)
 00:00:00.925407   Absolute <integer> = 0x0000000000000001 (1)
 00:00:00.925408 
 00:00:00.925408 [/USB/HidMouse/0/LUN#0/] (level 4)
 00:00:00.925410   Driver <string>  = "MouseQueue" (cb=11)
 00:00:00.925411 
 00:00:00.925412 [/USB/HidMouse/0/LUN#0/AttachedDriver/] (level 5)
 00:00:00.925414   Driver <string>  = "MainMouse" (cb=10)
 00:00:00.925414 
 00:00:00.925415 [/USB/HidMouse/0/LUN#0/AttachedDriver/Config/] (level 6)
 00:00:00.925417   Object <integer> = 0x00000000b030d4f0 (2 955 990 256)
 00:00:00.925419 
 00:00:00.925419 [/USB/HidMouse/0/LUN#0/Config/] (level 5)
 00:00:00.925421   QueueSize <integer> = 0x0000000000000080 (128)
 00:00:00.925423 
 00:00:00.925423 [/USB/USBProxy/] (level 2)
 00:00:00.925425 
 00:00:00.925425 [/USB/USBProxy/GlobalConfig/] (level 3)
 00:00:00.925427 
 00:00:00.925428 ********************* End of CFGM dump **********************
 00:00:00.925500 MM: cbHyperHeap=0x140000 (1310720)
 00:00:00.927277 Host paging mode: PAE+PGE
 00:00:00.927300 PGMPool: cMaxPages=912 (u64MaxPages=908)
 00:00:00.927306 pgmR3PoolInit: cMaxPages=0x390 cMaxUsers=0x720 cMaxPhysExts=0x720 fCacheEnable=true 
 00:00:00.969473 REM: VBoxREM32
 00:00:00.997346 TM: GIP - u32Mode=1 (SyncTSC) u32UpdateHz=83
 00:00:01.029797 TM: cTSCTicksPerSecond=0x9e368f0a (2 654 375 690) fTSCVirtualized=true  fTSCUseRealTSC=false
 00:00:01.029816 TM: fMaybeUseOffsettedHostTSC=true  TSCTiedToExecution=false TSCNotTiedToHalt=false
 00:00:01.030488 CoreCode: R3=ae54c000 R0=fbc0d000 RC=a0876000 Phys=000000002f2dc000 cb=0x3000
 00:00:01.054334 AIOMgr: Default manager type is "Async"
 00:00:01.054402 AIOMgr: Default file backend is "NonBuffered"
 00:00:01.058555 BlkCache: Cache successfully initialised. Cache size is 5242880 bytes
 00:00:01.058726 BlkCache: Cache commit interval is 10000 ms
 00:00:01.058743 BlkCache: Cache commit threshold is 2621440 bytes
 00:00:01.167398 [SMP] BIOS with 1 CPUs
 00:00:01.168484 DevPcBios: Using LAN ROM '/usr/lib/virtualbox/ExtensionPacks/Oracle_VM_VirtualBox_Extension_Pack/PXE-Intel.rom' with a size of 0xc000 bytes
 00:00:01.218817 SUP: Loaded VBoxDDR0.r0 (/usr/lib/virtualbox/VBoxDDR0.r0) at 0xfcb25020 - ModuleInit at 0000000000000000 and ModuleTerm at 0000000000000000
 00:00:01.234793 SUP: Loaded VBoxDD2R0.r0 (/usr/lib/virtualbox/VBoxDD2R0.r0) at 0xfcb62020 - ModuleInit at 0000000000000000 and ModuleTerm at 0000000000000000
 00:00:01.234850 Activating Local APIC
 00:00:01.234857 CPUMSetGuestCpuIdFeature: Enabled APIC
 00:00:01.234863 CPUMClearGuestCpuIdFeature: Disabled x2APIC
 00:00:01.235151 PIT: mode=3 count=0x10000 (65536) - 18.20 Hz (ch=0)
 00:00:01.239361 Shared Folders service loaded.
 00:00:01.347154 DrvBlock: Flushes will be ignored
 00:00:01.347192 DrvBlock: Async flushes will be passed to the disk
 00:00:01.347384 VDInit finished
 00:00:01.347997 VD: Opening the disk took 783036 ns
 00:00:01.348141 PIIX3 ATA: LUN#0: disk, PCHS=16383/16/63, total number of sectors 209715200
 00:00:01.348155 PIIX3 ATA: LUN#1: no unit
 00:00:01.348225 DrvBlock: Flushes will be ignored
 00:00:01.348231 DrvBlock: Async flushes will be passed to the disk
 00:00:01.348327 PIIX3 ATA: LUN#2: CD/DVD, total number of sectors 0, passthrough disabled
 00:00:01.348337 PIIX3 ATA: LUN#3: no unit
 00:00:01.348367 PIIX3 ATA: Ctl#0: finished processing RESET
 00:00:01.348390 PIIX3 ATA: Ctl#1: finished processing RESET
 00:00:01.348953 IntNet#0: szNetwork={HostInterfaceNetworking-wlan0} enmTrunkType=3 szTrunk={wlan0} fFlags=0x8001 cbRecv=325632 cbSend=196608 fIgnoreConnectFailure=false
 00:00:01.349760 Audio: Trying driver 'pulse'.
 00:00:01.353366 Audio: set_record_source ars=0 als=0 (not implemented)
 00:00:01.353400 Pulse: open PCM_IN rate=44100Hz channels=2 format=s16le
 00:00:01.353417 Pulse: Requested record buffer attributes: maxlength=26460 fragsize=17640
 00:00:01.362700 Pulse:  Obtained record buffer attributes: maxlength=26460 fragsize=8820
 00:00:01.362867 Pulse: open PCM_OUT rate=44100Hz channels=2 format=s16le
 00:00:01.362882 Pulse: Requested playback buffer attributes: maxlength=26460 tlength=17640 prebuf=-1 minreq=-1
 00:00:01.364264 Pulse:  Obtained playback buffer attributes: maxlength=26460 tlength=12348 prebuf=8824 minreq=3528
 00:00:01.365066 VUSB: attached 'HidMouse' to port 1
 00:00:01.400318 SUP: Loaded VBoxEhciR0.r0 (/usr/lib/virtualbox/ExtensionPacks/Oracle_VM_VirtualBox_Extension_Pack/linux.x86/VBoxEhciR0.r0) at 0xfbb45020 - ModuleInit at 0000000000000000 and ModuleTerm at 0000000000000000
 00:00:01.400423 DevPcBios: ATA LUN#0 LCHS=1024/255/63
 00:00:01.400643 PGM: The CPU physical address width is 36 bits
 00:00:01.400650 PGMR3InitFinalize: 4 MB PSE mask 0000000fffffffff
 00:00:01.430141 VMM: fUsePeriodicPreemptionTimers=true 
 00:00:01.434311 Logical host processors: 2 present, 2 max, 2 online, online mask: 0000000000000003
 00:00:01.434317 ************************* CPUID dump ************************
 00:00:01.434332          RAW Standard CPUIDs
 00:00:01.434333      Function  eax      ebx      ecx      edx
 00:00:01.434333 Gst: 00000000  00000005 756e6547 6c65746e 49656e69
 00:00:01.434335 Hst:           0000000a 756e6547 6c65746e 49656e69
 00:00:01.434337 Gst: 00000001  00010676 00000800 00000209 078bf3bf
 00:00:01.434338 Hst:           00010676 01020800 0008e39d bfebfbff
 00:00:01.434339 Gst: 00000002  05b0b101 005657f0 00000000 2cb43048
 00:00:01.434341 Hst:           05b0b101 005657f0 00000000 2cb43048
 00:00:01.434342 Gst: 00000003  00000000 00000000 00000000 00000000
 00:00:01.434343 Hst:           00000000 00000000 00000000 00000000
 00:00:01.434344 Gst: 00000004  00000000 00000000 00000000 00000000
 00:00:01.434345 Hst:           04000121 01c0003f 0000003f 00000001
 00:00:01.434346 Gst: 00000005  00000040 00000040 00000000 00000000
 00:00:01.434347 Hst:           00000040 00000040 00000003 00022220
 00:00:01.434348 Name:                            GenuineIntel
 00:00:01.434349 Supports:                        0-5
 00:00:01.434350 Family:                          6      Extended: 0     Effective: 6
 00:00:01.434351 Model:                           7      Extended: 1     Effective: 23
 00:00:01.434352 Stepping:                        6
 00:00:01.434353 Type:                            0 (primary)
 00:00:01.434353 APIC ID:                         0x00
 00:00:01.434354 Logical CPUs:                    0
 00:00:01.434354 CLFLUSH Size:                    8
 00:00:01.434355 Brand ID:                        0x00
 00:00:01.434356 Mnemonic - Description                 = guest (host)
 00:00:01.434357 FPU - x87 FPU on Chip                  = 1 (1)
 00:00:01.434358 VME - Virtual 8086 Mode Enhancements   = 1 (1)
 00:00:01.434358 DE - Debugging extensions              = 1 (1)
 00:00:01.434359 PSE - Page Size Extension              = 1 (1)
 00:00:01.434360 TSC - Time Stamp Counter               = 1 (1)
 00:00:01.434361 MSR - Model Specific Registers         = 1 (1)
 00:00:01.434362 PAE - Physical Address Extension       = 0 (1)
 00:00:01.434362 MCE - Machine Check Exception          = 1 (1)
 00:00:01.434363 CX8 - CMPXCHG8B instruction            = 1 (1)
 00:00:01.434364 APIC - APIC On-Chip                    = 1 (1)
 00:00:01.434365 10 - Reserved                          = 0 (0)
 00:00:01.434365 SEP - SYSENTER and SYSEXIT             = 0 (1)
 00:00:01.434366 MTRR - Memory Type Range Registers     = 1 (1)
 00:00:01.434367 PGE - PTE Global Bit                   = 1 (1)
 00:00:01.434367 MCA - Machine Check Architecture       = 1 (1)
 00:00:01.434368 CMOV - Conditional Move Instructions   = 1 (1)
 00:00:01.434369 PAT - Page Attribute Table             = 1 (1)
 00:00:01.434370 PSE-36 - 36-bit Page Size Extention    = 1 (1)
 00:00:01.434370 PSN - Processor Serial Number          = 0 (0)
 00:00:01.434371 CLFSH - CLFLUSH Instruction.           = 1 (1)
 00:00:01.434372 20 - Reserved                          = 0 (0)
 00:00:01.434373 DS - Debug Store                       = 0 (1)
 00:00:01.434373 ACPI - Thermal Mon. & Soft. Clock Ctrl.= 0 (1)
 00:00:01.434374 MMX - Intel MMX Technology             = 1 (1)
 00:00:01.434375 FXSR - FXSAVE and FXRSTOR Instructions = 1 (1)
 00:00:01.434376 SSE - SSE Support                      = 1 (1)
 00:00:01.434376 SSE2 - SSE2 Support                    = 1 (1)
 00:00:01.434377 SS - Self Snoop                        = 0 (1)
 00:00:01.434378 HTT - Hyper-Threading Technology       = 0 (1)
 00:00:01.434379 TM - Thermal Monitor                   = 0 (1)
 00:00:01.434380 30 - Reserved                          = 0 (0)
 00:00:01.434381 PBE - Pending Break Enable             = 0 (1)
 00:00:01.434381 Supports SSE3                          = 1 (1)
 00:00:01.434382 PCLMULQDQ                              = 0 (0)
 00:00:01.434383 DS Area 64-bit layout                  = 0 (1)
 00:00:01.434384 Supports MONITOR/MWAIT                 = 1 (1)
 00:00:01.434384 CPL-DS - CPL Qualified Debug Store     = 0 (1)
 00:00:01.434385 VMX - Virtual Machine Technology       = 0 (0)
 00:00:01.434386 SMX - Safer Mode Extensions            = 0 (0)
 00:00:01.434386 Enhanced SpeedStep Technology          = 0 (1)
 00:00:01.434387 Terminal Monitor 2                     = 0 (1)
 00:00:01.434388 Supplemental SSE3 instructions         = 1 (1)
 00:00:01.434390 L1 Context ID                          = 0 (0)
 00:00:01.434391 11 - Reserved                          = 0 (0)
 00:00:01.434392 FMA extensions using YMM state         = 0 (0)
 00:00:01.434392 CMPXCHG16B instruction                 = 0 (1)
 00:00:01.434393 xTPR Update Control                    = 0 (1)
 00:00:01.434394 Perf/Debug Capability MSR              = 0 (1)
 00:00:01.434395 16 - Reserved                          = 0 (0)
 00:00:01.434395 PCID - Process-context identifiers     = 0 (0)
 00:00:01.434396 DCA - Direct Cache Access              = 0 (0)
 00:00:01.434397 SSE4.1 instruction extensions          = 0 (1)
 00:00:01.434398 SSE4.2 instruction extensions          = 0 (0)
 00:00:01.434398 Supports the x2APIC extensions         = 0 (0)
 00:00:01.434399 MOVBE instruction                      = 0 (0)
 00:00:01.434400 POPCNT instruction                     = 0 (0)
 00:00:01.434401 TSC-Deadline LAPIC timer mode          = 0 (0)
 00:00:01.434401 AESNI instruction extensions           = 0 (0)
 00:00:01.434402 XSAVE/XRSTOR extended state feature    = 0 (0)
 00:00:01.434403 Supports OSXSAVE                       = 0 (0)
 00:00:01.434403 AVX instruction extensions             = 0 (0)
 00:00:01.434404 29/30 - Reserved                       = 0x0 (0x0)
 00:00:01.434405 Hypervisor Present (we're a guest)     = 0 (0)
 00:00:01.434406 
 00:00:01.434406          RAW Extended CPUIDs
 00:00:01.434407      Function  eax      ebx      ecx      edx
 00:00:01.434407 Gst: 80000000  80000008 00000000 00000000 00000000
 00:00:01.434409 Hst:           80000008 00000000 00000000 00000000
 00:00:01.434410 Gst: 80000001  00000000 00000000 00000000 00000000
 00:00:01.434411 Hst:           00000000 00000000 00000001 20100000
 00:00:01.434412 Gst: 80000002  65746e49 2952286c 726f4320 4d542865
 00:00:01.434413 Hst:           65746e49 2952286c 726f4320 4d542865
 00:00:01.434415 Gst: 80000003  44203229 43206f75 20205550 45202020
 00:00:01.434416 Hst:           44203229 43206f75 20205550 45202020
 00:00:01.434417 Gst: 80000004  30303337 20402020 36362e32 007a4847
 00:00:01.434418 Hst:           30303337 20402020 36362e32 007a4847
 00:00:01.434420 Gst: 80000005  00000000 00000000 00000000 00000000
 00:00:01.434421 Hst:           00000000 00000000 00000000 00000000
 00:00:01.434422 Gst: 80000006  00000000 00000000 0c006040 00000000
 00:00:01.434423 Hst:           00000000 00000000 0c006040 00000000
 00:00:01.434425 Gst: 80000007  00000000 00000000 00000000 00000000
 00:00:01.434426 Hst:           00000000 00000000 00000000 00000000
 00:00:01.434427 Gst: 80000008  00003024 00000000 00000000 00000000
 00:00:01.434428 Hst:           00003024 00000000 00000000 00000000
 00:00:01.434429 Gst: 80000009  07280202 00000000 00000000 00000503*
 00:00:01.434430 Hst:           07280202 00000000 00000000 00000503
 00:00:01.434432 Ext Name:                        
 00:00:01.434432 Ext Supports:                    0x80000000-0x80000008
 00:00:01.434433 Family:                          0      Extended: 0     Effective: 0
 00:00:01.434434 Model:                           0      Extended: 0     Effective: 0
 00:00:01.434435 Stepping:                        0
 00:00:01.434436 Brand ID:                        0x000
 00:00:01.434436 Mnemonic - Description                 = guest (host)
 00:00:01.434437 FPU - x87 FPU on Chip                  = 0 (0)
 00:00:01.434438 VME - Virtual 8086 Mode Enhancements   = 0 (0)
 00:00:01.434439 DE - Debugging extensions              = 0 (0)
 00:00:01.434439 PSE - Page Size Extension              = 0 (0)
 00:00:01.434440 TSC - Time Stamp Counter               = 0 (0)
 00:00:01.434441 MSR - K86 Model Specific Registers     = 0 (0)
 00:00:01.434442 PAE - Physical Address Extension       = 0 (0)
 00:00:01.434442 MCE - Machine Check Exception          = 0 (0)
 00:00:01.434443 CX8 - CMPXCHG8B instruction            = 0 (0)
 00:00:01.434444 APIC - APIC On-Chip                    = 0 (0)
 00:00:01.434444 10 - Reserved                          = 0 (0)
 00:00:01.434445 SEP - SYSCALL and SYSRET               = 0 (0)
 00:00:01.434446 MTRR - Memory Type Range Registers     = 0 (0)
 00:00:01.434447 PGE - PTE Global Bit                   = 0 (0)
 00:00:01.434447 MCA - Machine Check Architecture       = 0 (0)
 00:00:01.434448 CMOV - Conditional Move Instructions   = 0 (0)
 00:00:01.434449 PAT - Page Attribute Table             = 0 (0)
 00:00:01.434449 PSE-36 - 36-bit Page Size Extention    = 0 (0)
 00:00:01.434450 18 - Reserved                          = 0 (0)
 00:00:01.434451 19 - Reserved                          = 0 (0)
 00:00:01.434452 NX - No-Execute Page Protection        = 0 (1)
 00:00:01.434452 DS - Debug Store                       = 0 (0)
 00:00:01.434453 AXMMX - AMD Extensions to MMX Instr.   = 0 (0)
 00:00:01.434454 MMX - Intel MMX Technology             = 0 (0)
 00:00:01.434455 FXSR - FXSAVE and FXRSTOR Instructions = 0 (0)
 00:00:01.434455 25 - AMD fast FXSAVE and FXRSTOR Instr.= 0 (0)
 00:00:01.434456 26 - 1 GB large page support           = 0 (0)
 00:00:01.434457 27 - RDTSCP instruction                = 0 (0)
 00:00:01.434457 28 - Reserved                          = 0 (0)
 00:00:01.434458 29 - AMD Long Mode                     = 0 (1)
 00:00:01.434459 30 - AMD Extensions to 3DNow!          = 0 (0)
 00:00:01.434460 31 - AMD 3DNow!                        = 0 (0)
 00:00:01.434460 LahfSahf - LAHF/SAHF in 64-bit mode    = 0 (1)
 00:00:01.434461 CmpLegacy - Core MP legacy mode (depr) = 0 (0)
 00:00:01.434462 SVM - AMD VM Extensions                = 0 (0)
 00:00:01.434463 APIC registers starting at 0x400       = 0 (0)
 00:00:01.434463 AltMovCR8 - LOCK MOV CR0 means MOV CR8 = 0 (0)
 00:00:01.434464 5  - Advanced bit manipulation         = 0 (0)
 00:00:01.434465 6  - SSE4A instruction support         = 0 (0)
 00:00:01.434465 7  - Misaligned SSE mode               = 0 (0)
 00:00:01.434466 8  - PREFETCH and PREFETCHW instruction= 0 (0)
 00:00:01.434467 9  - OS visible workaround             = 0 (0)
 00:00:01.434468 10 - Instruction based sampling        = 0 (0)
 00:00:01.434468 11 - SSE5 support                      = 0 (0)
 00:00:01.434469 12 - SKINIT, STGI, and DEV support     = 0 (0)
 00:00:01.434470 13 - Watchdog timer support.           = 0 (0)
 00:00:01.434470 31:14 - Reserved                       = 0x0 (0x0)
 00:00:01.434472 Full Name:                       Intel(R) Core(TM)2 Duo CPU     E7300  @ 2.66GHz
 00:00:01.434473 TLB 2/4M Instr/Uni:              res0     0 entries
 00:00:01.434473 TLB 2/4M Data:                   res0     0 entries
 00:00:01.434474 TLB 4K Instr/Uni:                res0     0 entries
 00:00:01.434475 TLB 4K Data:                     res0     0 entries
 00:00:01.434476 L1 Instr Cache Line Size:        0 bytes
 00:00:01.434476 L1 Instr Cache Lines Per Tag:    0
 00:00:01.434477 L1 Instr Cache Associativity:    res0  
 00:00:01.434477 L1 Instr Cache Size:             0 KB
 00:00:01.434478 L1 Data Cache Line Size:         0 bytes
 00:00:01.434479 L1 Data Cache Lines Per Tag:     0
 00:00:01.434479 L1 Data Cache Associativity:     res0  
 00:00:01.434480 L1 Data Cache Size:              0 KB
 00:00:01.434480 L2 TLB 2/4M Instr/Uni:           off       0 entries
 00:00:01.434481 L2 TLB 2/4M Data:                off       0 entries
 00:00:01.434482 L2 TLB 4K Instr/Uni:             off       0 entries
 00:00:01.434482 L2 TLB 4K Data:                  off       0 entries
 00:00:01.434483 L2 Cache Line Size:              0 bytes
 00:00:01.434484 L2 Cache Lines Per Tag:          0
 00:00:01.434484 L2 Cache Associativity:          off   
 00:00:01.434485 L2 Cache Size:                   0 KB
 00:00:01.434486 APM Features:                   
 00:00:01.434486 Physical Address Width:          36 bits
 00:00:01.434487 Virtual Address Width:           48 bits
 00:00:01.434488 Guest Physical Address Width:    0 bits
 00:00:01.434488 Physical Core Count:             0
 00:00:01.434489 
 00:00:01.434489          RAW Centaur CPUIDs
 00:00:01.434490      Function  eax      ebx      ecx      edx
 00:00:01.434490 Gst: c0000000  07280202 00000000 00000000 00000503
 00:00:01.434492 Hst:           07280202 00000000 00000000 00000503
 00:00:01.434493 Gst: c0000001  07280202 00000000 00000000 00000503
 00:00:01.434494 Hst:           07280202 00000000 00000000 00000503
 00:00:01.434495 Gst: c0000002  07280202 00000000 00000000 00000503
 00:00:01.434497 Hst:           07280202 00000000 00000000 00000503
 00:00:01.434498 Gst: c0000003  07280202 00000000 00000000 00000503
 00:00:01.434499 Hst:           07280202 00000000 00000000 00000503
 00:00:01.434501 Centaur Supports:                0xc0000000-0x07280202
 00:00:01.434503 Mnemonic - Description                 = guest (host)
 00:00:01.434503 AIS - Alternate Instruction Set        = 0 (1)
 00:00:01.434504 AIS-E - AIS enabled                    = 0 (1)
 00:00:01.434505 RNG - Random Number Generator          = 0 (0)
 00:00:01.434506 RNG-E - RNG enabled                    = 0 (0)
 00:00:01.434506 LH - LongHaul MSR 0000_110Ah           = 0 (0)
 00:00:01.434507 FEMMS - FEMMS                          = 0 (0)
 00:00:01.434508 ACE - Advanced Cryptography Engine     = 0 (0)
 00:00:01.434509 ACE-E - ACE enabled                    = 0 (0)
 00:00:01.434510 ACE2 - Advanced Cryptography Engine 2  = 0 (1)
 00:00:01.434510 ACE2-E - ACE enabled                   = 0 (0)
 00:00:01.434511 PHE - Padlock Hash Engine              = 0 (1)
 00:00:01.434512 PHE-E - PHE enabled                    = 0 (0)
 00:00:01.434513 PMM - Montgomery Multiplier            = 0 (0)
 00:00:01.434513 PMM-E - PMM enabled                    = 0 (0)
 00:00:01.434514 14 - Reserved                          = 0 (0)
 00:00:01.434515 15 - Reserved                          = 0 (0)
 00:00:01.434516 Parallax                               = 0 (0)
 00:00:01.434516 Parallax enabled                       = 0 (0)
 00:00:01.434517 Overstress                             = 0 (0)
 00:00:01.434518 Overstress enabled                     = 0 (0)
 00:00:01.434519 TM3 - Temperature Monitoring 3         = 0 (0)
 00:00:01.434519 TM3-E - TM3 enabled                    = 0 (0)
 00:00:01.434520 RNG2 - Random Number Generator 2       = 0 (0)
 00:00:01.434521 RNG2-E - RNG2 enabled                  = 0 (0)
 00:00:01.434521 24 - Reserved                          = 0 (0)
 00:00:01.434522 PHE2 - Padlock Hash Engine 2           = 0 (0)
 00:00:01.434523 PHE2-E - PHE2 enabled                  = 0 (0)
 00:00:01.434524 
 00:00:01.434524 
 00:00:01.434525 ******************** End of CPUID dump **********************
 00:00:01.434572 HWACCM: No VT-x or AMD-V CPU extension found. Reason VERR_VMX_NO_VMX
 00:00:01.434586 HWACCM: VMX MSR_IA32_FEATURE_CONTROL=0
 00:00:01.453073 VM: Halt method global1 (5)
 00:00:01.453109 HaltedGlobal1 config: cNsSpinBlockThresholdCfg=2000
 00:00:01.453116 Changing the VM state from 'CREATING' to 'CREATED'.
 00:00:01.453598 Changing the VM state from 'CREATED' to 'POWERING_ON'.
 00:00:01.453692 Changing the VM state from 'POWERING_ON' to 'RUNNING'.
 00:00:01.472258 Guest Log: BIOS: VirtualBox 4.2.6
 00:00:01.472639 PIT: mode=2 count=0x10000 (65536) - 18.20 Hz (ch=0)
 00:00:01.485639 2D video acceleration is enabled.
 00:00:01.494844 PIIX3 ATA: Ctl#0: RESET, DevSel=0 AIOIf=0 CmdIf0=0x00 (-1 usec ago) CmdIf1=0x00 (-1 usec ago)
 00:00:01.494928 PIIX3 ATA: Ctl#0: finished processing RESET
 00:00:01.495904 Guest Log: BIOS: ata0-0: PCHS=16383/16/63 LCHS=1024/255/63
 00:00:01.497043 PIIX3 ATA: Ctl#0: RESET, DevSel=1 AIOIf=0 CmdIf0=0xec (-1 usec ago) CmdIf1=0x00 (-1 usec ago)
 00:00:01.497206 PIIX3 ATA: Ctl#0: finished processing RESET
 00:00:01.497333 PIIX3 ATA: Ctl#1: RESET, DevSel=0 AIOIf=0 CmdIf0=0x00 (-1 usec ago) CmdIf1=0x00 (-1 usec ago)
 00:00:01.497361 PIIX3 ATA: Ctl#1: finished processing RESET
 00:00:01.499689 PIT: mode=2 count=0x48d3 (18643) - 64.00 Hz (ch=0)
 00:00:01.499857 ERROR [COM]: aRC=VBOX_E_IPRT_ERROR (0x80bb0005) aIID={b83ee395-8679-40ca-8d60-1a0cbe724930} aComponent={Display} aText={Could not take a screenshot (VERR_NOT_SUPPORTED)}, preserve=false
 00:00:01.500147 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=00000000 w=720 h=400 bpp=0 cbLine=0x0, flags=0x1
 00:00:01.524777 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=a20ab000 w=640 h=480 bpp=32 cbLine=0xA00, flags=0x1
 00:00:03.977683 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=00000000 w=720 h=400 bpp=0 cbLine=0x0, flags=0x1
 00:00:03.981588 PIT: mode=2 count=0x10000 (65536) - 18.20 Hz (ch=0)
 00:00:03.982289 Guest Log: BIOS: Boot : bseqnr=1, bootseq=0023
 00:00:03.983665 Guest Log: BIOS: CDROM boot failure code : 0003
 00:00:03.983833 Guest Log: BIOS: Boot from CD-ROM failed
 00:00:03.983986 Guest Log: BIOS: Boot : bseqnr=2, bootseq=0002
 00:00:03.985437 Guest Log: BIOS: Booting from Hard Disk...
 00:00:04.245637 Guest Log: int13_harddisk: function 15, unmapped device for ELDL=81
 00:00:06.523582 RTC: period=0x200 (512) 64 Hz
 00:00:06.523826 PIT: mode=2 count=0xffff (65535) - 18.20 Hz (ch=0)
 00:00:06.780310 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=a20ab000 w=640 h=480 bpp=0 cbLine=0x140, flags=0x1
 00:00:09.294151 PIIX3 ATA: LUN#0: IDLE IMMEDIATE, CmdIf=0xef (-1 usec ago)
 00:00:09.294188 PIIX3 ATA: LUN#0: aborting current command
 00:00:10.426880 Guest Additions information report: Version 4.2.6 r82870 '4.2.6'
 00:00:10.427046 Guest Additions information report: Interface = 0x00010004 osType = 0x00033000
 00:00:10.427258 Guest Additions capability report: (0x0) seamless: no, hostWindowMapping: no, graphics: no
 00:00:10.438749 Guest reported fixed hypervisor window at 0xb9800000 (size = 0x1000000, rc = VINF_SUCCESS)
 00:00:19.609732 EHCI: Hardware reset
 00:00:19.609998 EHCI: USB Operational
 00:00:19.827330 Guest Log: VBoxMP::VBoxDrvFindAdapter: using HGSMI
 00:00:19.905143 PCNet#0: Init: ss32=1 GCRDRA=0x097c6420[64] GCTDRA=0x097c6020[64]
 00:00:20.914513 Audio: set_record_source ars=0 als=0 (not implemented)
 00:00:20.916979 Audio: set_record_source ars=0 als=0 (not implemented)
 00:00:20.937372 OHCI: Software reset
 00:00:20.937734 OHCI: USB Reset
 00:00:20.937771 OHCI: USB Operational
 00:00:21.523449 PCNet#0: Init: ss32=1 GCRDRA=0x097c6420[64] GCTDRA=0x097c6020[64]
 00:00:22.220967 EHCI: USB Suspended
 00:00:23.393241 Guest Log: VBoxDisp[0]: VBVA enabled
 00:00:23.393434 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=a20ab000 w=1855 h=1034 bpp=32 cbLine=0x1CFC, flags=0x1
 00:00:23.403697 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=a20ab000 w=1855 h=1034 bpp=32 cbLine=0x1CFC, flags=0x1
 00:00:23.512911 gl version string: 02.1 Mesa 8.0.4
 00:00:23.513024 gl version: 0x20100
 00:00:23.513032 gl extensions: GL_ARB_multisample GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_copy_texture GL_EXT_polygon_offset GL_EXT_subtexture GL_EXT_texture_object GL_EXT_vertex_array GL_EXT_compiled_vertex_array GL_EXT_texture GL_EXT_texture3D GL_IBM_rasterpos_clip GL_ARB_point_parameters GL_EXT_draw_range_elements GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_separate_specular_color GL_EXT_texture_edge_clamp GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_ARB_framebuffer_sRGB GL_ARB_multitexture GL_EXT_framebuffer_sRGB GL_IBM_multimode_draw_arrays GL_IBM_texture_mirrored_repeat GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_transpose_matrix GL_EXT_blend_func_separate GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_secondary_color GL_EXT_texture_env_add GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_INGR_blend_func_separate GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texgen_reflection GL_NV_texture_env_combine4 GL_SUN_multi_draw_arrays GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_EXT_framebuffer_object GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_MESA_window_pos GL_NV_packed_depth_stencil GL_NV_texture_rectangle GL_ARB_depth_texture GL_ARB_occlusion_query GL_ARB_shadow GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_window_pos GL_EXT_stencil_two_side GL_EXT_texture_cube_map GL_NV_depth_clamp GL_NV_fog_distance GL_APPLE_packed_pixels GL_APPLE_vertex_array_object GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_fragment_shader GL_ARB_shader_objects GL_ARB_vertex_program GL_ARB_vertex_shader GL_ATI_draw_buffers GL_ATI_texture_env_combine3 GL_ATI_texture_float GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_MESA_pack_invert GL_NV_primitive_restart GL_ARB_depth_clamp GL_ARB_fragment_program_shadow GL_ARB_half_float_pixel GL_ARB_occlusion_query2 GL_ARB_point_sprite GL_ARB_shading_language_100 GL_ARB_sync GL_ARB_texture_non_power_of_two GL_ARB_vertex_buffer_object GL_ATI_blend_equation_separate GL_EXT_blend_equation_separate GL_OES_read_format GL_ARB_color_buffer_float GL_ARB_pixel_buffer_object GL_ARB_texture_compression_rgtc GL_ARB_texture_float GL_ARB_texture_rectangle GL_ATI_texture_compression_3dc GL_EXT_packed_float GL_EXT_pixel_buffer_object GL_EXT_texture_compression_rgtc GL_EXT_texture_mirror_clamp GL_EXT_texture_rectangle GL_EXT_texture_sRGB GL_EXT_texture_shared_exponent GL_ARB_framebuffer_object GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXT_packed_depth_stencil GL_ARB_vertex_array_object GL_ATI_separate_stencil GL_ATI_texture_mirror_once GL_EXT_draw_buffers2 GL_EXT_draw_instanced GL_EXT_gpu_program_parameters GL_EXT_texture_compression_latc GL_EXT_texture_sRGB_decode GL_EXT_timer_query GL_OES_EGL_image GL_ARB_copy_buffer GL_ARB_depth_buffer_float GL_ARB_draw_instanced GL_ARB_half_float_vertex GL_ARB_instanced_arrays GL_ARB_map_buffer_range GL_ARB_texture_rg GL_ARB_texture_swizzle GL_ARB_vertex_array_bgra GL_EXT_separate_shader_objects GL_EXT_texture_swizzle GL_EXT_vertex_array_bgra GL_NV_conditional_render GL_ARB_ES2_compatibility GL_ARB_draw_elements_base_vertex GL_ARB_explicit_attrib_location GL_ARB_fragment_coord_conventions GL_ARB_provoking_vertex GL_ARB_sampler_objects GL_ARB_seamless_cube_map GL_ARB_shader_texture_lod GL_EXT_provoking_vertex GL_EXT_texture_snorm GL_MESA_texture_signed_rgba GL_NV_texture_barrier GL_ARB_robustness GL_ARB_texture_storage 
 00:00:23.513058 GL_ARB_multitexture: 1
 00:00:23.513076 GL_ARB_shader_objects: 1
 00:00:23.513093 GL_ARB_fragment_shader: 1
 00:00:23.513114 GL_ARB_pixel_buffer_object: 1
 00:00:23.513134 GL_ARB_texture_rectangle: 1
 00:00:23.513167 GL_EXT_texture_rectangle: 1
 00:00:23.513180 GL_NV_texture_rectangle: 1
 00:00:23.513199 GL_ARB_texture_non_power_of_two: 1
 00:00:23.513212 GL_EXT_framebuffer_object: 1
 00:00:23.513293 Max Tex Coords (8), Img Units (16)
 00:00:23.588241 2D is supported!
 00:00:32.331097 PCNet#0: Init: ss32=1 GCRDRA=0x097c6420[64] GCTDRA=0x097c6020[64]
 00:00:34.842988 Starting host clipboard service
 00:00:34.843107 Initializing X11 clipboard backend
 00:00:34.856776 Shared clipboard: starting shared clipboard thread
 00:00:34.864892 Guest Additions capability report: (0x4) seamless: no, hostWindowMapping: no, graphics: yes
 00:00:34.872256 Guest Additions capability report: (0x5) seamless: yes, hostWindowMapping: no, graphics: yes
 00:00:36.840690 Audio: set_record_source ars=0 als=0 (not implemented)
 00:00:36.840746 Audio: set_record_source ars=0 als=0 (not implemented)
 00:00:52.085031 PATM: Disable block at 8070991c - write 80709976-8070a976
 00:01:00.682181 PCNet#0: Init: ss32=1 GCRDRA=0x097c6420[64] GCTDRA=0x097c6020[64]
 00:01:08.081033 PCNet#0: Init: ss32=1 GCRDRA=0x097c6420[64] GCTDRA=0x097c6020[64]
 00:01:08.087213 PCNet#0: Init: ss32=1 GCRDRA=0x097c6420[64] GCTDRA=0x097c6020[64]
 00:01:11.403902 PCNet#0: Init: ss32=1 GCRDRA=0x097c6420[64] GCTDRA=0x097c6020[64]
 
```

(hope it is ok to post it ? )
if no security issue is possible i do not really care about staying at sp2 , since my use of windows will only be about video games and some browsing of forums, email and newspaper.

i just find it sad that virtualbox do not allowed upgrading xp sp2 to sp3 it seem ?

ps: everything is in 32 bytes

ty for help

---

### Post by Ms. Daisy on 2013-01-04
What log is that?

How are you updating Windows? How do you have the virtual network configured? If you either bridge or NAT the Windows guest, then you would just get windows updates as if it were a normal, stand-alone computer.

---

### Post by MontrealCorp on 2013-01-04
> **Ms. Daisy said:**
> What log is that?

How are you updating Windows? How do you have the virtual network configured? If you either bridge or NAT the Windows guest, then you would just get windows updates as if it were a normal, stand-alone computer.


hi ty for answering .

after so many visits and close to 24hours of posting with no answer, i was asking myself did i made something wrong in my post ?

the log is from virtualbox after my upgrade from sp 2 to sp3 failed, hoping some explanation would of been acknowledge in it.

i d/l sp3 , and was installing it manually when i was using windows xp 2 in virtualbox ( latest version)

my network is simply using a bridge with the host.

as u said , i guess trying to install it with windows update is my last solution, but if i remember correctly, couple of months ago i try  but could not install it cause microsoft was not supporting sp2 anymore, so i had to download it and installed it manually
 ( this is why i had a copy already on my usb hard drive ).

i shall try again to see 

ps: btw i d/l sp3 today to make sure the sp3 i had on my hard drive was not corrupted , both upgrade to sp3 failed by shutting down windows , where the virtualbox program was written aborted for my virtual machine .

if the windows updates does not allow me to upgrade, i guess my only alternative will be first to wipe out and reformat everything and install windows xp has my main operating system and see if i can upgrade my windows xp sp2 to sp3 , wich i should cause when i validate my sp2 cd, it worked !

after if i find this operation a success, then my only alternative going to be to slipstreaming my my windows xp2 with the sp3 .
i never done this and have not find a guide yet, if anyone has any suggestion ?

kind of like maybe doing a window slipstream on ubuntu might be better before i wipe out my entire drive or just wipe it out and doing in in windows my even be better and easier ?

i will wait until tomorrow in case someone gives me other advise on course to follow for another solution.

anyway, for now i will try upgrading it through windows updates and i shall be back to tell if it worked.

ty for further interest in my thread:)

ps: i saved the last logged with the new sp3 d/l today where it failed in virtualbox, if need to i can show it here.

---

### Post by MontrealCorp on 2013-01-05
well further developpement.

when i try activate windows update it did not work has i suspected on the 4th try.

so after that  i decide to retry manually and i did go further then usual , has i saw some files being copy and installed !!

unfortunately it did shut down again before sp 3 upgrade was complete.
now strange thing happened with virtualbox, it said it needed to close and restart twice to be able to get the installed sp 3 out of the system and to reinstalled sp2 ( in reality to restore sp2 has it was before the installation attempt of sp3 ).

after being done , the system seem to work more slowly, had couple of time indicated errors while loading windows and some programs .

since i went further then usual the last time, and knowing i had couple of errors and maybe my system was not has good a shape has i wanted, i decide i had nothing to loose to try one last time since i was ready to scrap that virtual system .


well it finally worked at the 5th time !!! i was able to install sp3 completely.
tho i really think my system got a bit screwed , i still going to erase it and install a fresh copy.
i did not  took a snapshot before trying earlier before i has so much trouble and errors :( .

i just hope by reinstalling right after i validate windows i wont have any problem reinstall it with a second validation in 2 days ?

because i had so much trouble. i think its a good idea to try slipstream , putting the sp3 i d/l today and trying to incorporate it into my cd windows xp2 for less hassle and less probability of having problems with updates.

i just do not think it is normal that it worked at the 5th time .

if anyone got any tip for slipstream, i will welcome them and ty them greatly .

ty

---

### Post by Habitual on 2013-01-06
[QUOTE=]if anyone got any tip for slipstream, i will welcome them and ty them greatly .

ty[/QUOTE]
[Slipstream Service Pack 3 into Your Windows XP Installation CD]("http://lifehacker.com/386526/slipstream-service-pack-3-into-your-windows-xp-installation-cd")

---

### Post by MontrealCorp on 2013-01-07
ty ill check it out

---

### Post by MontrealCorp on 2013-01-10
ty habitual, tho i find a link that was easier to me for accomplishing a slipstream .

[http://www.howtohaven.com/system/slipstream-xp-service-pack-3.shtml](http://www.howtohaven.com/system/slipstream-xp-service-pack-3.shtml)

i succeed on my first try to splitstream a windows xp sp2 with sp3 .

everything went like a charm and sp3 was installled on my first try with the disk i splitstream.

ty

---

