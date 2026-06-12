---
title: "Updating Lubuntu Guest crashes VirtualBox"
date: 2013-05-09
forum: Virtualisation
---

### Post by BlackWidower on 2013-05-09
I'm trying to wrap my head around this issue and it's past me.  I'm not sure if this is an issue with Lubuntu or VirtualBox, but more than likely, it's both.

I tried installing Lubuntu 64-bit desktop through VirtualBox (Host is Windows 7 64-bit), over and over again, and it kept crashing.  Eventually, I found a solution.  I disabled the 'download updates as I install' feature, and it worked like a clock.  The install would finish, everything would be grand.

Then, upon first boot, it would ask to install updates.  Natch.  So of course I installed updates.  And it'd crash again.

I want to be clear, this is not the operating system crashing.  It's VirtualBox.  Perhaps I'm just an idiot, but I didn't even know this was possible.  I thought this would be like a laptop spontaneously melting.

Actually, that almost happened to me once.

Anyway, the only way to get the VM to work again, was by restarting everything, which I did by deleting the hard drive, and building a new one, before reinstalling Lubuntu.  But this time I did create a Snapshot of a fresh, pre-update install.  Before trying to update again, so when it crashed, I could go back to the last time it actually worked.

I tried a few different things after this.  On a recent attempt, I thought it updated successfully, but I think it failed to update everything, since it wasn't long before my attempts to install more packages faced me with an update option.  Then it crashed.  

I know what you're thinking, you want details.  Here's a copy of the log file, and a screenshot from a millisecond before the crash, that VirtualBox captured.  Major clue in that screenshot, I assume.

Any ideas?

[IMG]http://theblackwidower.files.wordpress.com/2013/05/vboxlubuntu13-04crash.png[/IMG]

```
VirtualBox VM 4.2.12 r84980 win.amd64 (Apr 12 2013 11:35:06) release log
00:00:00.924568 Log opened 2013-05-10T02:17:38.862985900Z
00:00:00.924573 OS Product: Windows 7
00:00:00.924575 OS Release: 6.1.7601
00:00:00.924576 OS Service Pack: 1
00:00:00.924581 Host RAM: 8154MB total, 3389MB available
00:00:00.924584 Executable: C:\Program Files\Oracle\VirtualBox\VirtualBox.exe
00:00:00.924584 Process ID: 6844
00:00:00.924585 Package type: WINDOWS_64BITS_GENERIC
00:00:00.931450 Installed Extension Packs:
00:00:00.931494   Oracle VM VirtualBox Extension Pack (Version: 4.2.12 r84980; VRDE Module: VBoxVRDP)
00:00:00.937154 SUP: Opened VMMR0.r0 (C:\Program Files\Oracle\VirtualBox\VMMR0.r0) at 0xfffff8800de05000.
00:00:00.937190 SUP: windbg> .reload /f C:\Program Files\Oracle\VirtualBox\VMMR0.r0=0xfffff8800de05000
00:00:00.940083 OS type: 'Ubuntu_64'
00:00:00.952843 File system of 'C:\Users\BlackWidower\VirtualBox VMs\Rarity\Snapshots' (snapshots) is ntfs
00:00:00.952855 File system of 'C:\Users\BlackWidower\VirtualBox VMs\Rarity\Snapshots\{1aa35fb1-1e4e-4c3f-bd03-aa8f4e4005c1}.vdi' is ntfs
00:00:01.201806 Shared clipboard mode: Off
00:00:01.202620 Drag'n'drop mode: Off
00:00:01.204802 ************************* CFGM dump *************************
00:00:01.204806 [/] (level 0)
00:00:01.204809   CSAMEnabled     <integer> = 0x0000000000000001 (1)
00:00:01.204811   CpuExecutionCap <integer> = 0x0000000000000064 (100)
00:00:01.204812   EnablePAE       <integer> = 0x0000000000000000 (0)
00:00:01.204813   HwVirtExtForced <integer> = 0x0000000000000000 (0)
00:00:01.204814   MemBalloonSize  <integer> = 0x0000000000000000 (0)
00:00:01.204814   Name            <string>  = "Rarity" (cb=7)
00:00:01.204816   NumCPUs         <integer> = 0x0000000000000001 (1)
00:00:01.204817   PATMEnabled     <integer> = 0x0000000000000001 (1)
00:00:01.204817   PageFusion      <integer> = 0x0000000000000000 (0)
00:00:01.204818   RamHoleSize     <integer> = 0x0000000020000000 (536 870 912, 512 MB)
00:00:01.204820   RamSize         <integer> = 0x00000000c0000000 (3 221 225 472, 3 GB)
00:00:01.204821   RawR0Enabled    <integer> = 0x0000000000000001 (1)
00:00:01.204822   RawR3Enabled    <integer> = 0x0000000000000001 (1)
00:00:01.204823   TimerMillies    <integer> = 0x000000000000000a (10)
00:00:01.204824   UUID            <bytes>   = "fb ff bd 31 38 fb c3 4e a1 e2 be 60 59 a7 2f 75" (cb=16)
00:00:01.204827 
00:00:01.204828 [/CPUM/] (level 1)
00:00:01.204828   SyntheticCpu <integer> = 0x0000000000000000 (0)
00:00:01.204829 
00:00:01.204830 [/DBGF/] (level 1)
00:00:01.204830   Path <string>  = "C:\Users\BlackWidower\VirtualBox VMs\Rarity/debug/;C:\Users\BlackWidower\VirtualBox VMs\Rarity/;C:\Users\BlackWidower/" (cb=119)
00:00:01.204831 
00:00:01.204832 [/Devices/] (level 1)
00:00:01.204833 
00:00:01.204833 [/Devices/8237A/] (level 2)
00:00:01.204834 
00:00:01.204834 [/Devices/8237A/0/] (level 3)
00:00:01.204835   Trusted <integer> = 0x0000000000000001 (1)
00:00:01.204836 
00:00:01.204836 [/Devices/AudioSniffer/] (level 2)
00:00:01.204837 
00:00:01.204837 [/Devices/AudioSniffer/0/] (level 3)
00:00:01.204838 
00:00:01.204838 [/Devices/AudioSniffer/0/Config/] (level 4)
00:00:01.204839 
00:00:01.204840 [/Devices/AudioSniffer/0/LUN#0/] (level 4)
00:00:01.204841   Driver <string>  = "MainAudioSniffer" (cb=17)
00:00:01.204841 
00:00:01.204842 [/Devices/AudioSniffer/0/LUN#0/Config/] (level 5)
00:00:01.204843   Object <integer> = 0x0000000002f0a7a0 (49 325 984)
00:00:01.204844 
00:00:01.204844 [/Devices/VMMDev/] (level 2)
00:00:01.204845 
00:00:01.204845 [/Devices/VMMDev/0/] (level 3)
00:00:01.204846   PCIBusNo      <integer> = 0x0000000000000000 (0)
00:00:01.204847   PCIDeviceNo   <integer> = 0x0000000000000004 (4)
00:00:01.204848   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:01.204849   Trusted       <integer> = 0x0000000000000001 (1)
00:00:01.204849 
00:00:01.204850 [/Devices/VMMDev/0/Config/] (level 4)
00:00:01.204851   GuestCoreDumpDir <string>  = "C:\Users\BlackWidower\VirtualBox VMs\Rarity\Snapshots" (cb=54)
00:00:01.204852   RamSize          <integer> = 0x00000000c0000000 (3 221 225 472, 3 GB)
00:00:01.204853 
00:00:01.204853 [/Devices/VMMDev/0/LUN#0/] (level 4)
00:00:01.204854   Driver <string>  = "HGCM" (cb=5)
00:00:01.204855 
00:00:01.204855 [/Devices/VMMDev/0/LUN#0/Config/] (level 5)
00:00:01.204856   Object <integer> = 0x0000000001faa160 (33 202 528)
00:00:01.204857 
00:00:01.204857 [/Devices/VMMDev/0/LUN#999/] (level 4)
00:00:01.204858   Driver <string>  = "MainStatus" (cb=11)
00:00:01.204859 
00:00:01.204859 [/Devices/VMMDev/0/LUN#999/Config/] (level 5)
00:00:01.204860   First   <integer> = 0x0000000000000000 (0)
00:00:01.204861   Last    <integer> = 0x0000000000000000 (0)
00:00:01.204862   papLeds <integer> = 0x0000000002f08528 (49 317 160)
00:00:01.204863 
00:00:01.204863 [/Devices/acpi/] (level 2)
00:00:01.204864 
00:00:01.204864 [/Devices/acpi/0/] (level 3)
00:00:01.204865   PCIBusNo      <integer> = 0x0000000000000000 (0)
00:00:01.204866   PCIDeviceNo   <integer> = 0x0000000000000007 (7)
00:00:01.204867   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:01.204867   Trusted       <integer> = 0x0000000000000001 (1)
00:00:01.204868 
00:00:01.204868 [/Devices/acpi/0/Config/] (level 4)
00:00:01.204870   CpuHotPlug        <integer> = 0x0000000000000000 (0)
00:00:01.204870   FdcEnabled        <integer> = 0x0000000000000000 (0)
00:00:01.204871   HostBusPciAddress <integer> = 0x0000000000000000 (0)
00:00:01.204872   HpetEnabled       <integer> = 0x0000000000000000 (0)
00:00:01.204872   IOAPIC            <integer> = 0x0000000000000001 (1)
00:00:01.204873   IocPciAddress     <integer> = 0x0000000000010000 (65 536)
00:00:01.204874   NumCPUs           <integer> = 0x0000000000000001 (1)
00:00:01.204875   RamHoleSize       <integer> = 0x0000000020000000 (536 870 912, 512 MB)
00:00:01.204877   RamSize           <integer> = 0x00000000c0000000 (3 221 225 472, 3 GB)
00:00:01.204878   Serial0IoPortBase <integer> = 0x0000000000000000 (0)
00:00:01.204879   Serial0Irq        <integer> = 0x0000000000000000 (0)
00:00:01.204879   Serial1IoPortBase <integer> = 0x0000000000000000 (0)
00:00:01.204880   Serial1Irq        <integer> = 0x0000000000000000 (0)
00:00:01.204881   ShowCpu           <integer> = 0x0000000000000001 (1)
00:00:01.204881   ShowRtc           <integer> = 0x0000000000000000 (0)
00:00:01.204882   SmcEnabled        <integer> = 0x0000000000000000 (0)
00:00:01.204883 
00:00:01.204883 [/Devices/acpi/0/LUN#0/] (level 4)
00:00:01.204884   Driver <string>  = "ACPIHost" (cb=9)
00:00:01.204885 
00:00:01.204885 [/Devices/acpi/0/LUN#0/Config/] (level 5)
00:00:01.204886 
00:00:01.204886 [/Devices/ahci/] (level 2)
00:00:01.204887 
00:00:01.204887 [/Devices/ahci/0/] (level 3)
00:00:01.204888   PCIBusNo      <integer> = 0x0000000000000000 (0)
00:00:01.204889   PCIDeviceNo   <integer> = 0x000000000000000d (13)
00:00:01.204890   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:01.204891   Trusted       <integer> = 0x0000000000000001 (1)
00:00:01.204891 
00:00:01.204892 [/Devices/ahci/0/Config/] (level 4)
00:00:01.204893   Bootable  <integer> = 0x0000000000000001 (1)
00:00:01.204893   PortCount <integer> = 0x0000000000000001 (1)
00:00:01.204894 
00:00:01.204894 [/Devices/ahci/0/Config/Port0/] (level 5)
00:00:01.204895   NonRotationalMedium <integer> = 0x0000000000000000 (0)
00:00:01.204896 
00:00:01.204896 [/Devices/ahci/0/LUN#0/] (level 4)
00:00:01.204897   Driver <string>  = "Block" (cb=6)
00:00:01.204898 
00:00:01.204898 [/Devices/ahci/0/LUN#0/AttachedDriver/] (level 5)
00:00:01.204900   Driver <string>  = "VD" (cb=3)
00:00:01.204900 
00:00:01.204900 [/Devices/ahci/0/LUN#0/AttachedDriver/Config/] (level 6)
00:00:01.204902   BlockCache <integer> = 0x0000000000000001 (1)
00:00:01.204903   Format     <string>  = "VDI" (cb=4)
00:00:01.204903   Path       <string>  = "C:\Users\BlackWidower\VirtualBox VMs\Rarity\Snapshots\{1aa35fb1-1e4e-4c3f-bd03-aa8f4e4005c1}.vdi" (cb=97)
00:00:01.204904   Type       <string>  = "HardDisk" (cb=9)
00:00:01.204905   UseNewIo   <integer> = 0x0000000000000001 (1)
00:00:01.204906 
00:00:01.204906 [/Devices/ahci/0/LUN#0/AttachedDriver/Config/Parent/] (level 7)
00:00:01.204907   Format <string>  = "VDI" (cb=4)
00:00:01.204908   Path   <string>  = "D:\Rarity.vdi" (cb=14)
00:00:01.204909 
00:00:01.204909 [/Devices/ahci/0/LUN#0/Config/] (level 5)
00:00:01.204910   Mountable <integer> = 0x0000000000000000 (0)
00:00:01.204911   Type      <string>  = "HardDisk" (cb=9)
00:00:01.204911 
00:00:01.204911 [/Devices/ahci/0/LUN#999/] (level 4)
00:00:01.204912   Driver <string>  = "MainStatus" (cb=11)
00:00:01.204913 
00:00:01.204913 [/Devices/ahci/0/LUN#999/Config/] (level 5)
00:00:01.204914   DeviceInstance        <string>  = "ahci/0" (cb=7)
00:00:01.204915   First                 <integer> = 0x0000000000000000 (0)
00:00:01.204916   Last                  <integer> = 0x0000000000000000 (0)
00:00:01.204917   pConsole              <integer> = 0x0000000002f07f20 (49 315 616)
00:00:01.204918   papLeds               <integer> = 0x0000000002f08258 (49 316 440)
00:00:01.204919   pmapMediumAttachments <integer> = 0x0000000002f08540 (49 317 184)
00:00:01.204920 
00:00:01.204920 [/Devices/apic/] (level 2)
00:00:01.204921 
00:00:01.204921 [/Devices/apic/0/] (level 3)
00:00:01.204922   Trusted <integer> = 0x0000000000000001 (1)
00:00:01.204923 
00:00:01.204923 [/Devices/apic/0/Config/] (level 4)
00:00:01.204924   IOAPIC  <integer> = 0x0000000000000001 (1)
00:00:01.204925   NumCPUs <integer> = 0x0000000000000001 (1)
00:00:01.204926 
00:00:01.204926 [/Devices/e1000/] (level 2)
00:00:01.204927 
00:00:01.204927 [/Devices/e1000/0/] (level 3)
00:00:01.204928   PCIBusNo      <integer> = 0x0000000000000000 (0)
00:00:01.204929   PCIDeviceNo   <integer> = 0x0000000000000003 (3)
00:00:01.204930   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:01.204930   Trusted       <integer> = 0x0000000000000001 (1)
00:00:01.204931 
00:00:01.204931 [/Devices/e1000/0/Config/] (level 4)
00:00:01.204932   AdapterType    <integer> = 0x0000000000000000 (0)
00:00:01.204933   CableConnected <integer> = 0x0000000000000001 (1)
00:00:01.204934   LineSpeed      <integer> = 0x0000000000000000 (0)
00:00:01.204934   MAC            <bytes>   = "08 00 27 6d 56 a8" (cb=6)
00:00:01.204936 
00:00:01.204936 [/Devices/e1000/0/LUN#0/] (level 4)
00:00:01.204937   Driver <string>  = "IntNet" (cb=7)
00:00:01.204938 
00:00:01.204938 [/Devices/e1000/0/LUN#0/Config/] (level 5)
00:00:01.204939   IfPolicyPromisc      <string>  = "deny" (cb=5)
00:00:01.204940   IgnoreConnectFailure <integer> = 0x0000000000000000 (0)
00:00:01.204941   Network              <string>  = "HostInterfaceNetworking-Realtek RTL8723AE Wireless LAN 802.11n PCI-E NIC" (cb=73)
00:00:01.204941   SharedMacOnWire      <integer> = 0x0000000000000001 (1)
00:00:01.204942   Trunk                <string>  = "\DEVICE\{0F61251E-E045-4354-BA0E-4BE22183A062}" (cb=47)
00:00:01.204943   TrunkType            <integer> = 0x0000000000000003 (3)
00:00:01.204944 
00:00:01.204944 [/Devices/e1000/0/LUN#999/] (level 4)
00:00:01.204945   Driver <string>  = "MainStatus" (cb=11)
00:00:01.204946 
00:00:01.204946 [/Devices/e1000/0/LUN#999/Config/] (level 5)
00:00:01.204947   First   <integer> = 0x0000000000000000 (0)
00:00:01.204948   Last    <integer> = 0x0000000000000000 (0)
00:00:01.204949   papLeds <integer> = 0x0000000002f08408 (49 316 872)
00:00:01.204950 
00:00:01.204950 [/Devices/i8254/] (level 2)
00:00:01.204951 
00:00:01.204951 [/Devices/i8254/0/] (level 3)
00:00:01.204952 
00:00:01.204952 [/Devices/i8254/0/Config/] (level 4)
00:00:01.204953 
00:00:01.204953 [/Devices/i8259/] (level 2)
00:00:01.204954 
00:00:01.204954 [/Devices/i8259/0/] (level 3)
00:00:01.204955   Trusted <integer> = 0x0000000000000001 (1)
00:00:01.204956 
00:00:01.204956 [/Devices/i8259/0/Config/] (level 4)
00:00:01.204957 
00:00:01.204957 [/Devices/ichac97/] (level 2)
00:00:01.204958 
00:00:01.204958 [/Devices/ichac97/0/] (level 3)
00:00:01.204959   PCIBusNo      <integer> = 0x0000000000000000 (0)
00:00:01.204960   PCIDeviceNo   <integer> = 0x0000000000000005 (5)
00:00:01.204960   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:01.204961   Trusted       <integer> = 0x0000000000000001 (1)
00:00:01.204962 
00:00:01.204962 [/Devices/ichac97/0/Config/] (level 4)
00:00:01.204963 
00:00:01.204963 [/Devices/ichac97/0/LUN#0/] (level 4)
00:00:01.204964   Driver <string>  = "AUDIO" (cb=6)
00:00:01.204965 
00:00:01.204965 [/Devices/ichac97/0/LUN#0/Config/] (level 5)
00:00:01.204966   AudioDriver <string>  = "dsound" (cb=7)
00:00:01.204967   StreamName  <string>  = "Rarity" (cb=7)
00:00:01.204967 
00:00:01.204968 [/Devices/ioapic/] (level 2)
00:00:01.204968 
00:00:01.204969 [/Devices/ioapic/0/] (level 3)
00:00:01.204969   Trusted <integer> = 0x0000000000000001 (1)
00:00:01.204970 
00:00:01.204970 [/Devices/ioapic/0/Config/] (level 4)
00:00:01.204971   NumCPUs <integer> = 0x0000000000000001 (1)
00:00:01.204972 
00:00:01.204972 [/Devices/mc146818/] (level 2)
00:00:01.204973 
00:00:01.204973 [/Devices/mc146818/0/] (level 3)
00:00:01.204974 
00:00:01.204974 [/Devices/mc146818/0/Config/] (level 4)
00:00:01.204975   UseUTC <integer> = 0x0000000000000001 (1)
00:00:01.204976 
00:00:01.204976 [/Devices/parallel/] (level 2)
00:00:01.204977 
00:00:01.204977 [/Devices/pcarch/] (level 2)
00:00:01.204978 
00:00:01.204978 [/Devices/pcarch/0/] (level 3)
00:00:01.204979   Trusted <integer> = 0x0000000000000001 (1)
00:00:01.204980 
00:00:01.204980 [/Devices/pcarch/0/Config/] (level 4)
00:00:01.204981 
00:00:01.204981 [/Devices/pcbios/] (level 2)
00:00:01.204982 
00:00:01.204982 [/Devices/pcbios/0/] (level 3)
00:00:01.204983   Trusted <integer> = 0x0000000000000001 (1)
00:00:01.204984 
00:00:01.204984 [/Devices/pcbios/0/Config/] (level 4)
00:00:01.204986   BootDevice0        <string>  = "FLOPPY" (cb=7)
00:00:01.204986   BootDevice1        <string>  = "DVD" (cb=4)
00:00:01.204987   BootDevice2        <string>  = "IDE" (cb=4)
00:00:01.204988   BootDevice3        <string>  = "NONE" (cb=5)
00:00:01.204988   FloppyDevice       <string>  = "i82078" (cb=7)
00:00:01.204989   HardDiskDevice     <string>  = "piix3ide" (cb=9)
00:00:01.204990   IOAPIC             <integer> = 0x0000000000000001 (1)
00:00:01.204991   LanBootRom         <string>  = "C:\Program Files\Oracle\VirtualBox/ExtensionPacks/Oracle_VM_VirtualBox_Extension_Pack/PXE-Intel.rom" (cb=100)
00:00:01.204992   McfgBase           <integer> = 0x0000000000000000 (0)
00:00:01.204992   McfgLength         <integer> = 0x0000000000000000 (0)
00:00:01.204993   NumCPUs            <integer> = 0x0000000000000001 (1)
00:00:01.204994   PXEDebug           <integer> = 0x0000000000000000 (0)
00:00:01.204995   RamHoleSize        <integer> = 0x0000000020000000 (536 870 912, 512 MB)
00:00:01.204996   RamSize            <integer> = 0x00000000c0000000 (3 221 225 472, 3 GB)
00:00:01.204998   SataHardDiskDevice <string>  = "ahci" (cb=5)
00:00:01.204998   UUID               <bytes>   = "fb ff bd 31 38 fb c3 4e a1 e2 be 60 59 a7 2f 75" (cb=16)
00:00:01.205000 
00:00:01.205001 [/Devices/pcbios/0/Config/NetBoot/] (level 5)
00:00:01.205002 
00:00:01.205002 [/Devices/pcbios/0/Config/NetBoot/0/] (level 6)
00:00:01.205003   NIC           <integer> = 0x0000000000000000 (0)
00:00:01.205004   PCIBusNo      <integer> = 0x0000000000000000 (0)
00:00:01.205005   PCIDeviceNo   <integer> = 0x0000000000000003 (3)
00:00:01.205006   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:01.205006 
00:00:01.205007 [/Devices/pci/] (level 2)
00:00:01.205007 
00:00:01.205008 [/Devices/pci/0/] (level 3)
00:00:01.205009   Trusted <integer> = 0x0000000000000001 (1)
00:00:01.205009 
00:00:01.205009 [/Devices/pci/0/Config/] (level 4)
00:00:01.205010   IOAPIC <integer> = 0x0000000000000001 (1)
00:00:01.205011 
00:00:01.205011 [/Devices/pckbd/] (level 2)
00:00:01.205012 
00:00:01.205012 [/Devices/pckbd/0/] (level 3)
00:00:01.205013   Trusted <integer> = 0x0000000000000001 (1)
00:00:01.205014 
00:00:01.205014 [/Devices/pckbd/0/Config/] (level 4)
00:00:01.205015 
00:00:01.205015 [/Devices/pckbd/0/LUN#0/] (level 4)
00:00:01.205016   Driver <string>  = "KeyboardQueue" (cb=14)
00:00:01.205017 
00:00:01.205017 [/Devices/pckbd/0/LUN#0/AttachedDriver/] (level 5)
00:00:01.205018   Driver <string>  = "MainKeyboard" (cb=13)
00:00:01.205019 
00:00:01.205019 [/Devices/pckbd/0/LUN#0/AttachedDriver/Config/] (level 6)
00:00:01.205020   Object <integer> = 0x0000000002ec4250 (49 037 904)
00:00:01.205021 
00:00:01.205021 [/Devices/pckbd/0/LUN#0/Config/] (level 5)
00:00:01.205022   QueueSize <integer> = 0x0000000000000040 (64)
00:00:01.205023 
00:00:01.205024 [/Devices/pckbd/0/LUN#1/] (level 4)
00:00:01.205024   Driver <string>  = "MouseQueue" (cb=11)
00:00:01.205025 
00:00:01.205025 [/Devices/pckbd/0/LUN#1/AttachedDriver/] (level 5)
00:00:01.205026   Driver <string>  = "MainMouse" (cb=10)
00:00:01.205027 
00:00:01.205027 [/Devices/pckbd/0/LUN#1/AttachedDriver/Config/] (level 6)
00:00:01.205028   Object <integer> = 0x0000000002f00f50 (49 286 992)
00:00:01.205029 
00:00:01.205030 [/Devices/pckbd/0/LUN#1/Config/] (level 5)
00:00:01.205031   QueueSize <integer> = 0x0000000000000080 (128)
00:00:01.205031 
00:00:01.205032 [/Devices/pcnet/] (level 2)
00:00:01.205033 
00:00:01.205033 [/Devices/piix3ide/] (level 2)
00:00:01.205034 
00:00:01.205034 [/Devices/piix3ide/0/] (level 3)
00:00:01.205035   PCIBusNo      <integer> = 0x0000000000000000 (0)
00:00:01.205036   PCIDeviceNo   <integer> = 0x0000000000000001 (1)
00:00:01.205037   PCIFunctionNo <integer> = 0x0000000000000001 (1)
00:00:01.205037   Trusted       <integer> = 0x0000000000000001 (1)
00:00:01.205038 
00:00:01.205038 [/Devices/piix3ide/0/Config/] (level 4)
00:00:01.205039   Type <string>  = "PIIX4" (cb=6)
00:00:01.205040 
00:00:01.205040 [/Devices/piix3ide/0/Config/SecondaryMaster/] (level 5)
00:00:01.205041   NonRotationalMedium <integer> = 0x0000000000000000 (0)
00:00:01.205042 
00:00:01.205042 [/Devices/piix3ide/0/LUN#2/] (level 4)
00:00:01.205043   Driver <string>  = "Block" (cb=6)
00:00:01.205044 
00:00:01.205044 [/Devices/piix3ide/0/LUN#2/Config/] (level 5)
00:00:01.205045   Mountable <integer> = 0x0000000000000001 (1)
00:00:01.205046   Type      <string>  = "DVD" (cb=4)
00:00:01.205046 
00:00:01.205046 [/Devices/piix3ide/0/LUN#999/] (level 4)
00:00:01.205047   Driver <string>  = "MainStatus" (cb=11)
00:00:01.205048 
00:00:01.205048 [/Devices/piix3ide/0/LUN#999/Config/] (level 5)
00:00:01.205049   DeviceInstance        <string>  = "piix3ide/0" (cb=11)
00:00:01.205050   First                 <integer> = 0x0000000000000000 (0)
00:00:01.205051   Last                  <integer> = 0x0000000000000003 (3)
00:00:01.205052   pConsole              <integer> = 0x0000000002f07f20 (49 315 616)
00:00:01.205053   papLeds               <integer> = 0x0000000002f08238 (49 316 408)
00:00:01.205054   pmapMediumAttachments <integer> = 0x0000000002f08540 (49 317 184)
00:00:01.205055 
00:00:01.205055 [/Devices/serial/] (level 2)
00:00:01.205056 
00:00:01.205056 [/Devices/usb-ehci/] (level 2)
00:00:01.205057 
00:00:01.205057 [/Devices/usb-ehci/0/] (level 3)
00:00:01.205058   PCIBusNo      <integer> = 0x0000000000000000 (0)
00:00:01.205059   PCIDeviceNo   <integer> = 0x000000000000000b (11)
00:00:01.205060   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:01.205060   Trusted       <integer> = 0x0000000000000001 (1)
00:00:01.205061 
00:00:01.205061 [/Devices/usb-ehci/0/Config/] (level 4)
00:00:01.205062 
00:00:01.205063 [/Devices/usb-ehci/0/LUN#0/] (level 4)
00:00:01.205064   Driver <string>  = "VUSBRootHub" (cb=12)
00:00:01.205064 
00:00:01.205064 [/Devices/usb-ehci/0/LUN#0/Config/] (level 5)
00:00:01.205065 
00:00:01.205066 [/Devices/usb-ehci/0/LUN#999/] (level 4)
00:00:01.205067   Driver <string>  = "MainStatus" (cb=11)
00:00:01.205067 
00:00:01.205068 [/Devices/usb-ehci/0/LUN#999/Config/] (level 5)
00:00:01.205069   First   <integer> = 0x0000000000000000 (0)
00:00:01.205069   Last    <integer> = 0x0000000000000000 (0)
00:00:01.205070   papLeds <integer> = 0x0000000002f08538 (49 317 176)
00:00:01.205071 
00:00:01.205071 [/Devices/usb-ohci/] (level 2)
00:00:01.205072 
00:00:01.205072 [/Devices/usb-ohci/0/] (level 3)
00:00:01.205073   PCIBusNo      <integer> = 0x0000000000000000 (0)
00:00:01.205074   PCIDeviceNo   <integer> = 0x0000000000000006 (6)
00:00:01.205074   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:01.205075   Trusted       <integer> = 0x0000000000000001 (1)
00:00:01.205076 
00:00:01.205076 [/Devices/usb-ohci/0/Config/] (level 4)
00:00:01.205077 
00:00:01.205077 [/Devices/usb-ohci/0/LUN#0/] (level 4)
00:00:01.205078   Driver <string>  = "VUSBRootHub" (cb=12)
00:00:01.205079 
00:00:01.205079 [/Devices/usb-ohci/0/LUN#0/Config/] (level 5)
00:00:01.205080 
00:00:01.205080 [/Devices/usb-ohci/0/LUN#999/] (level 4)
00:00:01.205081   Driver <string>  = "MainStatus" (cb=11)
00:00:01.205082 
00:00:01.205082 [/Devices/usb-ohci/0/LUN#999/Config/] (level 5)
00:00:01.205083   First   <integer> = 0x0000000000000000 (0)
00:00:01.205084   Last    <integer> = 0x0000000000000000 (0)
00:00:01.205084   papLeds <integer> = 0x0000000002f08530 (49 317 168)
00:00:01.205085 
00:00:01.205086 [/Devices/vga/] (level 2)
00:00:01.205086 
00:00:01.205087 [/Devices/vga/0/] (level 3)
00:00:01.205087   PCIBusNo      <integer> = 0x0000000000000000 (0)
00:00:01.205088   PCIDeviceNo   <integer> = 0x0000000000000002 (2)
00:00:01.205089   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:01.205089   Trusted       <integer> = 0x0000000000000001 (1)
00:00:01.205090 
00:00:01.205090 [/Devices/vga/0/Config/] (level 4)
00:00:01.205092   CustomVideoModes <integer> = 0x0000000000000000 (0)
00:00:01.205092   FadeIn           <integer> = 0x0000000000000001 (1)
00:00:01.205093   FadeOut          <integer> = 0x0000000000000001 (1)
00:00:01.205094   HeightReduction  <integer> = 0x0000000000000000 (0)
00:00:01.205095   LogoFile         <string>  = "" (cb=1)
00:00:01.205095   LogoTime         <integer> = 0x0000000000000000 (0)
00:00:01.205096   MonitorCount     <integer> = 0x0000000000000001 (1)
00:00:01.205097   ShowBootMenu     <integer> = 0x0000000000000002 (2)
00:00:01.205097   VRamSize         <integer> = 0x0000000000c00000 (12 582 912, 12 MB)
00:00:01.205099 
00:00:01.205099 [/Devices/vga/0/LUN#0/] (level 4)
00:00:01.205100   Driver <string>  = "MainDisplay" (cb=12)
00:00:01.205101 
00:00:01.205101 [/Devices/vga/0/LUN#0/Config/] (level 5)
00:00:01.205128   Object <integer> = 0x0000000002f0dc90 (49 339 536)
00:00:01.205130 
00:00:01.205131 [/Devices/virtio-net/] (level 2)
00:00:01.205133 
00:00:01.205134 [/HWVirtExt/] (level 1)
00:00:01.205135   64bitEnabled       <integer> = 0x0000000000000001 (1)
00:00:01.205137   EnableLargePages   <integer> = 0x0000000000000001 (1)
00:00:01.205139   EnableNestedPaging <integer> = 0x0000000000000001 (1)
00:00:01.205140   EnableVPID         <integer> = 0x0000000000000001 (1)
00:00:01.205142   Enabled            <integer> = 0x0000000000000001 (1)
00:00:01.205143   Exclusive          <integer> = 0x0000000000000000 (0)
00:00:01.205144 
00:00:01.205145 [/MM/] (level 1)
00:00:01.205146   CanUseLargerHeap <integer> = 0x0000000000000000 (0)
00:00:01.205147 
00:00:01.205148 [/PDM/] (level 1)
00:00:01.205149 
00:00:01.205150 [/PDM/AsyncCompletion/] (level 2)
00:00:01.205151 
00:00:01.205151 [/PDM/AsyncCompletion/File/] (level 3)
00:00:01.205153 
00:00:01.205153 [/PDM/AsyncCompletion/File/BwGroups/] (level 4)
00:00:01.205155 
00:00:01.205155 [/PDM/BlkCache/] (level 2)
00:00:01.205156   CacheSize <integer> = 0x0000000000500000 (5 242 880, 5 MB)
00:00:01.205158 
00:00:01.205159 [/PDM/Devices/] (level 2)
00:00:01.205160 
00:00:01.205160 [/PDM/Devices/VBoxEhci/] (level 3)
00:00:01.205162   Path         <string>  = "C:\Program Files\Oracle\VirtualBox/ExtensionPacks/Oracle_VM_VirtualBox_Extension_Pack/win.amd64/VBoxEhciR3.DLL" (cb=111)
00:00:01.205164   R0SearchPath <string>  = "C:\Program Files\Oracle\VirtualBox/ExtensionPacks/Oracle_VM_VirtualBox_Extension_Pack/win.amd64" (cb=96)
00:00:01.205165   RCSearchPath <string>  = "C:\Program Files\Oracle\VirtualBox/ExtensionPacks/Oracle_VM_VirtualBox_Extension_Pack/win.amd64" (cb=96)
00:00:01.205166 
00:00:01.205167 [/PDM/Drivers/] (level 2)
00:00:01.205168 
00:00:01.205168 [/PDM/Drivers/VBoxC/] (level 3)
00:00:01.205170   Path <string>  = "VBoxC" (cb=6)
00:00:01.205171 
00:00:01.205171 [/PDM/NetworkShaper/] (level 2)
00:00:01.205173 
00:00:01.205173 [/PDM/NetworkShaper/BwGroups/] (level 3)
00:00:01.205175 
00:00:01.205175 [/PDM/USB/] (level 2)
00:00:01.205176 
00:00:01.205176 [/PDM/USB/VBoxUsbCardReader/] (level 3)
00:00:01.205178   Path <string>  = "C:\Program Files\Oracle\VirtualBox/ExtensionPacks/Oracle_VM_VirtualBox_Extension_Pack/win.amd64/VBoxUsbCardReaderR3.DLL" (cb=120)
00:00:01.205179 
00:00:01.205180 [/PDM/USB/VBoxUsbWebcam/] (level 3)
00:00:01.205181   Path <string>  = "C:\Program Files\Oracle\VirtualBox/ExtensionPacks/Oracle_VM_VirtualBox_Extension_Pack/win.amd64/VBoxUsbWebcamR3.DLL" (cb=116)
00:00:01.205182 
00:00:01.205182 [/TM/] (level 1)
00:00:01.205184   UTCOffset <integer> = 0x0000000000000000 (0)
00:00:01.205185 
00:00:01.205185 [/USB/] (level 1)
00:00:01.205186 
00:00:01.205187 [/USB/HidMouse/] (level 2)
00:00:01.205188 
00:00:01.205189 [/USB/HidMouse/0/] (level 3)
00:00:01.205190 
00:00:01.205190 [/USB/HidMouse/0/Config/] (level 4)
00:00:01.205192   Absolute <integer> = 0x0000000000000001 (1)
00:00:01.205193 
00:00:01.205193 [/USB/HidMouse/0/LUN#0/] (level 4)
00:00:01.205195   Driver <string>  = "MouseQueue" (cb=11)
00:00:01.205196 
00:00:01.205196 [/USB/HidMouse/0/LUN#0/AttachedDriver/] (level 5)
00:00:01.205198   Driver <string>  = "MainMouse" (cb=10)
00:00:01.205199 
00:00:01.205199 [/USB/HidMouse/0/LUN#0/AttachedDriver/Config/] (level 6)
00:00:01.205201   Object <integer> = 0x0000000002f00f50 (49 286 992)
00:00:01.205203 
00:00:01.205204 [/USB/HidMouse/0/LUN#0/Config/] (level 5)
00:00:01.205205   QueueSize <integer> = 0x0000000000000080 (128)
00:00:01.205207 
00:00:01.205207 [/USB/USBProxy/] (level 2)
00:00:01.205209 
00:00:01.205209 [/USB/USBProxy/GlobalConfig/] (level 3)
00:00:01.205210 
00:00:01.205211 ********************* End of CFGM dump **********************
00:00:01.205251 MM: cbHyperHeap=0x140000 (1310720)
00:00:01.206717 Debug: HCPhysInterPD=00000000af250000 HCPhysInterPaePDPT=00000000af24d000 HCPhysInterPaePML4=00000000af24b000
00:00:01.206732 Debug: apInterPTs={00000000af24f000,00000000af24e000} apInterPaePTs={0000000236a49000,00000002359ca000} apInterPaePDs={000000023584b000,00000002359cc000,000000023604d000,00000002358ce000} pInterPaePDPT64=00000000af24c000
00:00:01.206739 Host paging mode: AMD64+PGE+NX
00:00:01.206746 PGMPool: cMaxPages=1584 (u64MaxPages=1571)
00:00:01.206750 pgmR3PoolInit: cMaxPages=0x630 cMaxUsers=0xc60 cMaxPhysExts=0xc60 fCacheEnable=true 
00:00:01.223815 TM: GIP - u32Mode=1 (SyncTSC) u32UpdateHz=66
00:00:01.255622 TM: cTSCTicksPerSecond=0x87656a90 (2 271 570 576) fTSCVirtualized=true  fTSCUseRealTSC=false
00:00:01.255632 TM: fMaybeUseOffsettedHostTSC=true  TSCTiedToExecution=false TSCNotTiedToHalt=false
00:00:01.256239 CoreCode: R3=0000000000600000 R0=fffff8800bf54000 RC=a0db9000 Phys=00000000ae818000 cb=0x1000
00:00:01.258012 AIOMgr: Default manager type is "Async"
00:00:01.258021 AIOMgr: Default file backend is "NonBuffered"
00:00:01.258309 BlkCache: Cache successfully initialised. Cache size is 5242880 bytes
00:00:01.258318 BlkCache: Cache commit interval is 10000 ms
00:00:01.258323 BlkCache: Cache commit threshold is 2621440 bytes
00:00:01.261452 [SMP] BIOS with 1 CPUs
00:00:01.262318 DevPcBios: Using LAN ROM 'C:\Program Files\Oracle\VirtualBox/ExtensionPacks/Oracle_VM_VirtualBox_Extension_Pack/PXE-Intel.rom' with a size of 0xc000 bytes
00:00:01.262743 SUP: Opened VBoxDDR0.r0 (C:\Program Files\Oracle\VirtualBox\VBoxDDR0.r0) at 0xfffff8800de96000.
00:00:01.262751 SUP: windbg> .reload /f C:\Program Files\Oracle\VirtualBox\VBoxDDR0.r0=0xfffff8800de96000
00:00:01.263065 SUP: Opened VBoxDD2R0.r0 (C:\Program Files\Oracle\VirtualBox\VBoxDD2R0.r0) at 0xfffff8800deb9000.
00:00:01.263110 SUP: windbg> .reload /f C:\Program Files\Oracle\VirtualBox\VBoxDD2R0.r0=0xfffff8800deb9000
00:00:01.263146 Activating Local APIC
00:00:01.263152 CPUMSetGuestCpuIdFeature: Enabled APIC
00:00:01.263156 CPUMClearGuestCpuIdFeature: Disabled x2APIC
00:00:01.263298 PIT: mode=3 count=0x10000 (65536) - 18.20 Hz (ch=0)
00:00:01.265890 Shared Folders service loaded.
00:00:01.268716 Chipset cannot do MSI: VERR_NOT_IMPLEMENTED
00:00:01.268988 DrvBlock: Flushes will be ignored
00:00:01.268994 DrvBlock: Async flushes will be passed to the disk
00:00:01.269143 VDInit finished
00:00:01.269564 AIOMgr: Endpoint for file 'D:\Rarity.vdi' (flags 000c0781) created successfully
00:00:01.296881 AIOMgr: Endpoint for file 'C:\Users\BlackWidower\VirtualBox VMs\Rarity\Snapshots\{1aa35fb1-1e4e-4c3f-bd03-aa8f4e4005c1}.vdi' (flags 000c0723) created successfully
00:00:01.319365 VD: Opening the disk took 50349528 ns
00:00:01.319425 AHCI: LUN#0: disk, PCHS=16383/16/63, total number of sectors 209715200
00:00:01.319436 AHCI: LUN#0: using async I/O
00:00:01.319462 AHCI#0: Reset the HBA
00:00:01.319768 PIIX3 ATA: LUN#0: no unit
00:00:01.319810 PIIX3 ATA: LUN#1: no unit
00:00:01.319967 DrvBlock: Flushes will be ignored
00:00:01.319980 DrvBlock: Async flushes will be passed to the disk
00:00:01.320144 PIIX3 ATA: LUN#2: CD/DVD, total number of sectors 0, passthrough disabled
00:00:01.320155 PIIX3 ATA: LUN#3: no unit
00:00:01.320211 PIIX3 ATA: Ctl#0: finished processing RESET
00:00:01.320269 PIIX3 ATA: Ctl#1: finished processing RESET
00:00:01.320433 IntNet#0: szNetwork={HostInterfaceNetworking-Realtek RTL8723AE Wireless LAN 802.11n PCI-E NIC} enmTrunkType=3 szTrunk={\DEVICE\{0F61251E-E045-4354-BA0E-4BE22183A062}} fFlags=0x8001 cbRecv=325632 cbSend=196608 fIgnoreConnectFailure=false
00:00:01.321064 Audio: Trying driver 'dsound'.
00:00:01.346128 Audio: set_record_source ars=0 als=0 (not implemented)
00:00:01.362295 VUSB: attached 'HidMouse' to port 1
00:00:01.362940 SUP: Opened VBoxEhciR0.r0 (C:\Program Files\Oracle\VirtualBox\ExtensionPacks\Oracle_VM_VirtualBox_Extension_Pack\win.amd64\VBoxEhciR0.r0) at 0xfffff8800dec2000.
00:00:01.362948 SUP: windbg> .reload /f C:\Program Files\Oracle\VirtualBox\ExtensionPacks\Oracle_VM_VirtualBox_Extension_Pack\win.amd64\VBoxEhciR0.r0=0xfffff8800dec2000
00:00:01.363012 DevPcBios: SATA LUN#0 LCHS=1024/255/63
00:00:01.363237 PGM: The CPU physical address width is 36 bits
00:00:01.363246 PGMR3InitFinalize: 4 MB PSE mask 0000000fffffffff
00:00:01.366821 VMM: fUsePeriodicPreemptionTimers=false
00:00:01.366838 Logical host processors: 8 present, 8 max, 8 online, online mask: 00000000000000ff
00:00:01.366840 ************************* CPUID dump ************************
00:00:01.366845          RAW Standard CPUIDs
00:00:01.366846      Function  eax      ebx      ecx      edx
00:00:01.366846 Gst: 00000000  00000005 756e6547 6c65746e 49656e69
00:00:01.366848 Hst:           0000000d 756e6547 6c65746e 49656e69
00:00:01.366849 Gst: 00000001  000306a9 00000800 00000209 078bf3bf
00:00:01.366850 Hst:           000306a9 07100800 7fbae3bf bfebfbff
00:00:01.366851 Gst: 00000002  76035a01 00f0b2ff 00000000 00ca0000
00:00:01.366852 Hst:           76035a01 00f0b2ff 00000000 00ca0000
00:00:01.366853 Gst: 00000003  00000000 00000000 00000000 00000000
00:00:01.366854 Hst:           00000000 00000000 00000000 00000000
00:00:01.366854 Gst: 00000004  00000000 00000000 00000000 00000000
00:00:01.366855 Hst:           1c004121 01c0003f 0000003f 00000000
00:00:01.366856 Gst: 00000005  00000040 00000040 00000000 00000000
00:00:01.366857 Hst:           00000040 00000040 00000003 00021120
00:00:01.366858 Name:                            GenuineIntel
00:00:01.366858 Supports:                        0-5
00:00:01.366859 Family:                          6  	Extended: 0 	Effective: 6
00:00:01.366860 Model:                           10  	Extended: 3 	Effective: 58
00:00:01.366860 Stepping:                        9
00:00:01.366861 Type:                            0 (primary)
00:00:01.366861 APIC ID:                         0x00
00:00:01.366862 Logical CPUs:                    0
00:00:01.366862 CLFLUSH Size:                    8
00:00:01.366862 Brand ID:                        0x00
00:00:01.366864 Mnemonic - Description                 = guest (host)
00:00:01.366865 FPU - x87 FPU on Chip                  = 1 (1)
00:00:01.366865 VME - Virtual 8086 Mode Enhancements   = 1 (1)
00:00:01.366866 DE - Debugging extensions              = 1 (1)
00:00:01.366866 PSE - Page Size Extension              = 1 (1)
00:00:01.366867 TSC - Time Stamp Counter               = 1 (1)
00:00:01.366867 MSR - Model Specific Registers         = 1 (1)
00:00:01.366868 PAE - Physical Address Extension       = 0 (1)
00:00:01.366868 MCE - Machine Check Exception          = 1 (1)
00:00:01.366868 CX8 - CMPXCHG8B instruction            = 1 (1)
00:00:01.366869 APIC - APIC On-Chip                    = 1 (1)
00:00:01.366869 10 - Reserved                          = 0 (0)
00:00:01.366870 SEP - SYSENTER and SYSEXIT             = 0 (1)
00:00:01.366870 MTRR - Memory Type Range Registers     = 1 (1)
00:00:01.366871 PGE - PTE Global Bit                   = 1 (1)
00:00:01.366871 MCA - Machine Check Architecture       = 1 (1)
00:00:01.366872 CMOV - Conditional Move Instructions   = 1 (1)
00:00:01.366872 PAT - Page Attribute Table             = 1 (1)
00:00:01.366873 PSE-36 - 36-bit Page Size Extention    = 1 (1)
00:00:01.366873 PSN - Processor Serial Number          = 0 (0)
00:00:01.366873 CLFSH - CLFLUSH Instruction.           = 1 (1)
00:00:01.366874 20 - Reserved                          = 0 (0)
00:00:01.366874 DS - Debug Store                       = 0 (1)
00:00:01.366875 ACPI - Thermal Mon. & Soft. Clock Ctrl.= 0 (1)
00:00:01.366875 MMX - Intel MMX Technology             = 1 (1)
00:00:01.366876 FXSR - FXSAVE and FXRSTOR Instructions = 1 (1)
00:00:01.366876 SSE - SSE Support                      = 1 (1)
00:00:01.366877 SSE2 - SSE2 Support                    = 1 (1)
00:00:01.366877 SS - Self Snoop                        = 0 (1)
00:00:01.366878 HTT - Hyper-Threading Technology       = 0 (1)
00:00:01.366878 TM - Thermal Monitor                   = 0 (1)
00:00:01.366878 30 - Reserved                          = 0 (0)
00:00:01.366879 PBE - Pending Break Enable             = 0 (1)
00:00:01.366879 Supports SSE3                          = 1 (1)
00:00:01.366880 PCLMULQDQ                              = 0 (1)
00:00:01.366880 DS Area 64-bit layout                  = 0 (1)
00:00:01.366881 Supports MONITOR/MWAIT                 = 1 (1)
00:00:01.366881 CPL-DS - CPL Qualified Debug Store     = 0 (1)
00:00:01.366882 VMX - Virtual Machine Technology       = 0 (1)
00:00:01.366882 SMX - Safer Mode Extensions            = 0 (0)
00:00:01.366883 Enhanced SpeedStep Technology          = 0 (1)
00:00:01.366883 Terminal Monitor 2                     = 0 (1)
00:00:01.366884 Supplemental SSE3 instructions         = 1 (1)
00:00:01.366885 L1 Context ID                          = 0 (0)
00:00:01.366885 11 - Reserved                          = 0 (0)
00:00:01.366886 FMA extensions using YMM state         = 0 (0)
00:00:01.366886 CMPXCHG16B instruction                 = 0 (1)
00:00:01.366887 xTPR Update Control                    = 0 (1)
00:00:01.366887 Perf/Debug Capability MSR              = 0 (1)
00:00:01.366888 16 - Reserved                          = 0 (0)
00:00:01.366888 PCID - Process-context identifiers     = 0 (1)
00:00:01.366889 DCA - Direct Cache Access              = 0 (0)
00:00:01.366889 SSE4.1 instruction extensions          = 0 (1)
00:00:01.366890 SSE4.2 instruction extensions          = 0 (1)
00:00:01.366890 Supports the x2APIC extensions         = 0 (1)
00:00:01.366890 MOVBE instruction                      = 0 (0)
00:00:01.366891 POPCNT instruction                     = 0 (1)
00:00:01.366891 TSC-Deadline LAPIC timer mode          = 0 (1)
00:00:01.366892 AESNI instruction extensions           = 0 (1)
00:00:01.366892 XSAVE/XRSTOR extended state feature    = 0 (1)
00:00:01.366893 Supports OSXSAVE                       = 0 (1)
00:00:01.366893 AVX instruction extensions             = 0 (1)
00:00:01.366894 29/30 - Reserved                       = 0x0 (0x3)
00:00:01.366894 Hypervisor Present (we're a guest)     = 0 (0)
00:00:01.366895 
00:00:01.366895          RAW Extended CPUIDs
00:00:01.366895      Function  eax      ebx      ecx      edx
00:00:01.366896 Gst: 80000000  80000008 00000000 00000000 00000000
00:00:01.366897 Hst:           80000008 00000000 00000000 00000000
00:00:01.366898 Gst: 80000001  00000000 00000000 00000000 08000000
00:00:01.366898 Hst:           00000000 00000000 00000001 28100800
00:00:01.366899 Gst: 80000002  20202020 6e492020 286c6574 43202952
00:00:01.366901 Hst:           20202020 6e492020 286c6574 43202952
00:00:01.366902 Gst: 80000003  2865726f 20294d54 332d3769 51303136
00:00:01.366903 Hst:           2865726f 20294d54 332d3769 51303136
00:00:01.366904 Gst: 80000004  5043204d 20402055 30332e32 007a4847
00:00:01.366905 Hst:           5043204d 20402055 30332e32 007a4847
00:00:01.366906 Gst: 80000005  00000000 00000000 00000000 00000000
00:00:01.366906 Hst:           00000000 00000000 00000000 00000000
00:00:01.366907 Gst: 80000006  00000000 00000000 01006040 00000000
00:00:01.366908 Hst:           00000000 00000000 01006040 00000000
00:00:01.366909 Gst: 80000007  00000000 00000000 00000000 00000000
00:00:01.366909 Hst:           00000000 00000000 00000000 00000100
00:00:01.366910 Gst: 80000008  00003024 00000000 00000000 00000000
00:00:01.366911 Hst:           00003024 00000000 00000000 00000000
00:00:01.366911 Gst: 80000009  00000007 00000340 00000340 00000000*
00:00:01.366912 Hst:           00000007 00000340 00000340 00000000
00:00:01.366913 Ext Name:                        
00:00:01.366914 Ext Supports:                    0x80000000-0x80000008
00:00:01.366914 Family:                          0  	Extended: 0 	Effective: 0
00:00:01.366915 Model:                           0  	Extended: 0 	Effective: 0
00:00:01.366915 Stepping:                        0
00:00:01.366916 Brand ID:                        0x000
00:00:01.366916 Mnemonic - Description                 = guest (host)
00:00:01.366918 FPU - x87 FPU on Chip                  = 0 (0)
00:00:01.366918 VME - Virtual 8086 Mode Enhancements   = 0 (0)
00:00:01.366919 DE - Debugging extensions              = 0 (0)
00:00:01.366919 PSE - Page Size Extension              = 0 (0)
00:00:01.366920 TSC - Time Stamp Counter               = 0 (0)
00:00:01.366920 MSR - K86 Model Specific Registers     = 0 (0)
00:00:01.366921 PAE - Physical Address Extension       = 0 (0)
00:00:01.366921 MCE - Machine Check Exception          = 0 (0)
00:00:01.366922 CX8 - CMPXCHG8B instruction            = 0 (0)
00:00:01.366922 APIC - APIC On-Chip                    = 0 (0)
00:00:01.366922 10 - Reserved                          = 0 (0)
00:00:01.366923 SEP - SYSCALL and SYSRET               = 0 (1)
00:00:01.366923 MTRR - Memory Type Range Registers     = 0 (0)
00:00:01.366924 PGE - PTE Global Bit                   = 0 (0)
00:00:01.366924 MCA - Machine Check Architecture       = 0 (0)
00:00:01.366925 CMOV - Conditional Move Instructions   = 0 (0)
00:00:01.366925 PAT - Page Attribute Table             = 0 (0)
00:00:01.366926 PSE-36 - 36-bit Page Size Extention    = 0 (0)
00:00:01.366926 18 - Reserved                          = 0 (0)
00:00:01.366926 19 - Reserved                          = 0 (0)
00:00:01.366927 NX - No-Execute Page Protection        = 0 (1)
00:00:01.366927 DS - Debug Store                       = 0 (0)
00:00:01.366928 AXMMX - AMD Extensions to MMX Instr.   = 0 (0)
00:00:01.366928 MMX - Intel MMX Technology             = 0 (0)
00:00:01.366929 FXSR - FXSAVE and FXRSTOR Instructions = 0 (0)
00:00:01.366929 25 - AMD fast FXSAVE and FXRSTOR Instr.= 0 (0)
00:00:01.366930 26 - 1 GB large page support           = 0 (0)
00:00:01.366930 27 - RDTSCP instruction                = 1 (1)
00:00:01.366931 28 - Reserved                          = 0 (0)
00:00:01.366931 29 - AMD Long Mode                     = 0 (1)
00:00:01.366931 30 - AMD Extensions to 3DNow!          = 0 (0)
00:00:01.366932 31 - AMD 3DNow!                        = 0 (0)
00:00:01.366932 LahfSahf - LAHF/SAHF in 64-bit mode    = 0 (1)
00:00:01.366933 CmpLegacy - Core MP legacy mode (depr) = 0 (0)
00:00:01.366933 SVM - AMD VM Extensions                = 0 (0)
00:00:01.366934 APIC registers starting at 0x400       = 0 (0)
00:00:01.366934 AltMovCR8 - LOCK MOV CR0 means MOV CR8 = 0 (0)
00:00:01.366935 5  - Advanced bit manipulation         = 0 (0)
00:00:01.366935 6  - SSE4A instruction support         = 0 (0)
00:00:01.366935 7  - Misaligned SSE mode               = 0 (0)
00:00:01.366936 8  - PREFETCH and PREFETCHW instruction= 0 (0)
00:00:01.366936 9  - OS visible workaround             = 0 (0)
00:00:01.366937 10 - Instruction based sampling        = 0 (0)
00:00:01.366937 11 - SSE5 support                      = 0 (0)
00:00:01.366938 12 - SKINIT, STGI, and DEV support     = 0 (0)
00:00:01.366938 13 - Watchdog timer support.           = 0 (0)
00:00:01.366939 31:14 - Reserved                       = 0x0 (0x0)
00:00:01.366939 Full Name:                             Intel(R) Core(TM) i7-3610QM CPU @ 2.30GHz
00:00:01.366940 TLB 2/4M Instr/Uni:              res0     0 entries
00:00:01.366941 TLB 2/4M Data:                   res0     0 entries
00:00:01.366941 TLB 4K Instr/Uni:                res0     0 entries
00:00:01.366942 TLB 4K Data:                     res0     0 entries
00:00:01.366942 L1 Instr Cache Line Size:        0 bytes
00:00:01.366943 L1 Instr Cache Lines Per Tag:    0
00:00:01.366943 L1 Instr Cache Associativity:    res0  
00:00:01.366943 L1 Instr Cache Size:             0 KB
00:00:01.366944 L1 Data Cache Line Size:         0 bytes
00:00:01.366944 L1 Data Cache Lines Per Tag:     0
00:00:01.366945 L1 Data Cache Associativity:     res0  
00:00:01.366945 L1 Data Cache Size:              0 KB
00:00:01.366945 L2 TLB 2/4M Instr/Uni:           off       0 entries
00:00:01.366946 L2 TLB 2/4M Data:                off       0 entries
00:00:01.366947 L2 TLB 4K Instr/Uni:             off       0 entries
00:00:01.366947 L2 TLB 4K Data:                  off       0 entries
00:00:01.366948 L2 Cache Line Size:              0 bytes
00:00:01.366948 L2 Cache Lines Per Tag:          0
00:00:01.366948 L2 Cache Associativity:          off   
00:00:01.366949 L2 Cache Size:                   0 KB
00:00:01.366949 APM Features:                   
00:00:01.366950 Physical Address Width:          36 bits
00:00:01.366950 Virtual Address Width:           48 bits
00:00:01.366951 Guest Physical Address Width:    0 bits
00:00:01.366951 Physical Core Count:             0
00:00:01.366952 
00:00:01.366952          RAW Centaur CPUIDs
00:00:01.366952      Function  eax      ebx      ecx      edx
00:00:01.366952 Gst: c0000000  00000007 00000340 00000340 00000000
00:00:01.366953 Hst:           00000007 00000340 00000340 00000000
00:00:01.366954 Gst: c0000001  00000007 00000340 00000340 00000000
00:00:01.366955 Hst:           00000007 00000340 00000340 00000000
00:00:01.366956 Gst: c0000002  00000007 00000340 00000340 00000000
00:00:01.366956 Hst:           00000007 00000340 00000340 00000000
00:00:01.366957 Gst: c0000003  00000007 00000340 00000340 00000000
00:00:01.366958 Hst:           00000007 00000340 00000340 00000000
00:00:01.366958 Centaur Supports:                0xc0000000-0x00000007
00:00:01.366959 Mnemonic - Description                 = guest (host)
00:00:01.366959 AIS - Alternate Instruction Set        = 0 (0)
00:00:01.366960 AIS-E - AIS enabled                    = 0 (0)
00:00:01.366961 RNG - Random Number Generator          = 0 (0)
00:00:01.366961 RNG-E - RNG enabled                    = 0 (0)
00:00:01.366961 LH - LongHaul MSR 0000_110Ah           = 0 (0)
00:00:01.366962 FEMMS - FEMMS                          = 0 (0)
00:00:01.366962 ACE - Advanced Cryptography Engine     = 0 (0)
00:00:01.366963 ACE-E - ACE enabled                    = 0 (0)
00:00:01.366963 ACE2 - Advanced Cryptography Engine 2  = 0 (0)
00:00:01.366964 ACE2-E - ACE enabled                   = 0 (0)
00:00:01.366964 PHE - Padlock Hash Engine              = 0 (0)
00:00:01.366965 PHE-E - PHE enabled                    = 0 (0)
00:00:01.366965 PMM - Montgomery Multiplier            = 0 (0)
00:00:01.366966 PMM-E - PMM enabled                    = 0 (0)
00:00:01.366966 14 - Reserved                          = 0 (0)
00:00:01.366966 15 - Reserved                          = 0 (0)
00:00:01.366967 Parallax                               = 0 (0)
00:00:01.366967 Parallax enabled                       = 0 (0)
00:00:01.366968 Overstress                             = 0 (0)
00:00:01.366968 Overstress enabled                     = 0 (0)
00:00:01.366969 TM3 - Temperature Monitoring 3         = 0 (0)
00:00:01.366969 TM3-E - TM3 enabled                    = 0 (0)
00:00:01.366970 RNG2 - Random Number Generator 2       = 0 (0)
00:00:01.366970 RNG2-E - RNG2 enabled                  = 0 (0)
00:00:01.366971 24 - Reserved                          = 0 (0)
00:00:01.366971 PHE2 - Padlock Hash Engine 2           = 0 (0)
00:00:01.366971 PHE2-E - PHE2 enabled                  = 0 (0)
00:00:01.366972 Bit 27                                 = 1 (0)
00:00:01.366973 
00:00:01.366973 
00:00:01.366973 ******************** End of CPUID dump **********************
00:00:01.367027 HWACCM: Host CR4=000406F8
00:00:01.367028 HWACCM: MSR_IA32_FEATURE_CONTROL      = 5
00:00:01.367029 HWACCM: MSR_IA32_VMX_BASIC_INFO       = da040000000010
00:00:01.367030 HWACCM: VMCS id                       = 10
00:00:01.367031 HWACCM: VMCS size                     = 400
00:00:01.367031 HWACCM: VMCS physical address limit   = None
00:00:01.367032 HWACCM: VMCS memory type              = 6
00:00:01.367032 HWACCM: Dual monitor treatment        = 1
00:00:01.367033 HWACCM: MSR_IA32_VMX_PINBASED_CTLS    = 7f00000016
00:00:01.367034 HWACCM:    VMX_VMCS_CTRL_PIN_EXEC_CONTROLS_EXT_INT_EXIT
00:00:01.367034 HWACCM:    VMX_VMCS_CTRL_PIN_EXEC_CONTROLS_NMI_EXIT
00:00:01.367034 HWACCM:    VMX_VMCS_CTRL_PIN_EXEC_CONTROLS_VIRTUAL_NMI
00:00:01.367035 HWACCM:    VMX_VMCS_CTRL_PIN_EXEC_CONTROLS_PREEMPT_TIMER
00:00:01.367035 HWACCM: MSR_IA32_VMX_PROCBASED_CTLS   = fff9fffe0401e172
00:00:01.367036 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_IRQ_WINDOW_EXIT
00:00:01.367037 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_TSC_OFFSET
00:00:01.367037 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_HLT_EXIT
00:00:01.367037 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_INVLPG_EXIT
00:00:01.367038 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_MWAIT_EXIT
00:00:01.367038 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_RDPMC_EXIT
00:00:01.367039 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_RDTSC_EXIT
00:00:01.367039 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_CR3_LOAD_EXIT
00:00:01.367039 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_CR3_STORE_EXIT
00:00:01.367040 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_CR8_LOAD_EXIT
00:00:01.367040 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_CR8_STORE_EXIT
00:00:01.367040 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_USE_TPR_SHADOW
00:00:01.367041 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_NMI_WINDOW_EXIT
00:00:01.367041 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_MOV_DR_EXIT
00:00:01.367042 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_UNCOND_IO_EXIT
00:00:01.367042 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_USE_IO_BITMAPS
00:00:01.367042 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_MONITOR_TRAP_FLAG
00:00:01.367043 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_USE_MSR_BITMAPS
00:00:01.367043 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_MONITOR_EXIT
00:00:01.367044 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_PAUSE_EXIT
00:00:01.367044 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_USE_SECONDARY_EXEC_CTRL
00:00:01.367045 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_CR3_LOAD_EXIT *must* be set
00:00:01.367046 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_CR3_STORE_EXIT *must* be set
00:00:01.367046 HWACCM: MSR_IA32_VMX_PROCBASED_CTLS2  = 8ff00000000
00:00:01.367047 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC2_VIRT_APIC
00:00:01.367048 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC2_EPT
00:00:01.367048 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC2_DESCRIPTOR_INSTR_EXIT
00:00:01.367048 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC2_RDTSCP
00:00:01.367049 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC2_X2APIC
00:00:01.367049 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC2_VPID
00:00:01.367049 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC2_WBINVD_EXIT
00:00:01.367050 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC2_REAL_MODE
00:00:01.367051 HWACCM: MSR_IA32_VMX_ENTRY_CTLS       = ffff000011ff
00:00:01.367052 HWACCM:    VMX_VMCS_CTRL_ENTRY_CONTROLS_LOAD_DEBUG
00:00:01.367053 HWACCM:    VMX_VMCS_CTRL_ENTRY_CONTROLS_IA64_MODE
00:00:01.367053 HWACCM:    VMX_VMCS_CTRL_ENTRY_CONTROLS_ENTRY_SMM
00:00:01.367053 HWACCM:    VMX_VMCS_CTRL_ENTRY_CONTROLS_DEACTIVATE_DUALMON
00:00:01.367054 HWACCM:    VMX_VMCS_CTRL_ENTRY_CONTROLS_LOAD_GUEST_PERF_MSR
00:00:01.367054 HWACCM:    VMX_VMCS_CTRL_ENTRY_CONTROLS_LOAD_GUEST_PAT_MSR
00:00:01.367055 HWACCM:    VMX_VMCS_CTRL_ENTRY_CONTROLS_LOAD_GUEST_EFER_MSR
00:00:01.367055 HWACCM:    VMX_VMCS_CTRL_ENTRY_CONTROLS_LOAD_DEBUG *must* be set
00:00:01.367055 HWACCM: MSR_IA32_VMX_EXIT_CTLS        = 7fffff00036dff
00:00:01.367056 HWACCM:    VMX_VMCS_CTRL_EXIT_CONTROLS_SAVE_DEBUG
00:00:01.367057 HWACCM:    VMX_VMCS_CTRL_EXIT_CONTROLS_HOST_AMD64
00:00:01.367057 HWACCM:    VMX_VMCS_CTRL_EXIT_CONTROLS_ACK_EXTERNAL_IRQ
00:00:01.367057 HWACCM:    VMX_VMCS_CTRL_EXIT_CONTROLS_SAVE_GUEST_PAT_MSR
00:00:01.367058 HWACCM:    VMX_VMCS_CTRL_EXIT_CONTROLS_LOAD_HOST_PAT_MSR
00:00:01.367058 HWACCM:    VMX_VMCS_CTRL_EXIT_CONTROLS_SAVE_GUEST_EFER_MSR
00:00:01.367059 HWACCM:    VMX_VMCS_CTRL_EXIT_CONTROLS_LOAD_HOST_EFER_MSR
00:00:01.367060 HWACCM:    VMX_VMCS_CTRL_EXIT_CONTROLS_SAVE_VMX_PREEMPT_TIMER
00:00:01.367060 HWACCM:    VMX_VMCS_CTRL_EXIT_CONTROLS_SAVE_DEBUG *must* be set
00:00:01.367061 HWACCM: MSR_IA32_VMX_EPT_VPID_CAPS    = f0106114141
00:00:01.367062 HWACCM:    MSR_IA32_VMX_EPT_CAPS_RWX_X_ONLY
00:00:01.367062 HWACCM:    MSR_IA32_VMX_EPT_CAPS_GAW_48_BITS
00:00:01.367062 HWACCM:    MSR_IA32_VMX_EPT_CAPS_EMT_UC
00:00:01.367063 HWACCM:    MSR_IA32_VMX_EPT_CAPS_EMT_WB
00:00:01.367063 HWACCM:    MSR_IA32_VMX_EPT_CAPS_SP_21_BITS
00:00:01.367064 HWACCM:    MSR_IA32_VMX_EPT_CAPS_INVEPT
00:00:01.367064 HWACCM:    MSR_IA32_VMX_EPT_CAPS_INVEPT_CAPS_SINGLE_CONTEXT
00:00:01.367064 HWACCM:    MSR_IA32_VMX_EPT_CAPS_INVEPT_CAPS_ALL_CONTEXTS
00:00:01.367065 HWACCM:    MSR_IA32_VMX_EPT_CAPS_INVVPID
00:00:01.367065 HWACCM:    MSR_IA32_VMX_EPT_CAPS_INVVPID_CAPS_INDIV_ADDR
00:00:01.367066 HWACCM:    MSR_IA32_VMX_EPT_CAPS_INVVPID_CAPS_SINGLE_CONTEXT
00:00:01.367066 HWACCM:    MSR_IA32_VMX_EPT_CAPS_INVVPID_CAPS_ALL_CONTEXTS
00:00:01.367066 HWACCM:    MSR_IA32_VMX_EPT_CAPS_INVVPID_CAPS_SINGLE_CONTEXT_RETAIN_GLOBALS
00:00:01.367067 HWACCM: MSR_IA32_VMX_MISC             = 100401e5
00:00:01.367067 HWACCM:    MSR_IA32_VMX_MISC_PREEMPT_TSC_BIT 5
00:00:01.367068 HWACCM:    MSR_IA32_VMX_MISC_ACTIVITY_STATES 7
00:00:01.367068 HWACCM:    MSR_IA32_VMX_MISC_CR3_TARGET      4
00:00:01.367069 HWACCM:    MSR_IA32_VMX_MISC_MAX_MSR         200
00:00:01.367069 HWACCM:    MSR_IA32_VMX_MISC_MSEG_ID         0
00:00:01.367070 HWACCM: MSR_IA32_VMX_CR0_FIXED0       = 80000021
00:00:01.367070 HWACCM: MSR_IA32_VMX_CR0_FIXED1       = ffffffff
00:00:01.367071 HWACCM: MSR_IA32_VMX_CR4_FIXED0       = 2000
00:00:01.367072 HWACCM: MSR_IA32_VMX_CR4_FIXED1       = 1727ff
00:00:01.367072 HWACCM: MSR_IA32_VMX_VMCS_ENUM        = 2a
00:00:01.367073 HWACCM: TPR shadow physaddr           = 00000000ae817000
00:00:01.367074 HWACCM: VCPU0: MSR bitmap physaddr    = 00000000ae814000
00:00:01.367075 HWACCM: VCPU0: VMCS physaddr          = 00000000ae816000
00:00:01.367092 CPUMSetGuestCpuIdFeature: Enabled sysenter/exit
00:00:01.367093 CPUMSetGuestCpuIdFeature: Enabled PAE
00:00:01.367094 CPUMSetGuestCpuIdFeature: Enabled LONG MODE
00:00:01.367094 CPUMSetGuestCpuIdFeature: Enabled syscall/ret
00:00:01.367095 CPUMSetGuestCpuIdFeature: Enabled LAHF/SAHF
00:00:01.367095 CPUMSetGuestCpuIdFeature: Enabled NX
00:00:01.367095 HWACCM: 32-bit and 64-bit guests supported.
00:00:01.367096 HWACCM: VMX enabled!
00:00:01.367096 HWACCM: Enabled nested paging
00:00:01.367097 HWACCM: EPT root page                 = 00000000af20d000
00:00:01.367098 HWACCM: enmFlushEPT                   = VMX_FLUSH_EPT_SINGLE_CONTEXT
00:00:01.367098 HWACCM: Unrestricted guest execution enabled!
00:00:01.367098 HWACCM: Large page support enabled!
00:00:01.367099 HWACCM: Enabled VPID
00:00:01.367099 HWACCM: enmFlushVPID                  = VMX_FLUSH_VPID_SINGLE_CONTEXT
00:00:01.367100 HWACCM: TPR Patching disabled.
00:00:01.367101 HWACCM: Using the VMX-preemption timer (cPreemptTimerShift=5)
00:00:01.367102 HWACCM:    VT-x/AMD-V init method: LOCAL
00:00:01.369332 VM: Halt method global1 (5)
00:00:01.369350 HaltedGlobal1 config: cNsSpinBlockThresholdCfg=125000
00:00:01.369356 Changing the VM state from 'CREATING' to 'CREATED'.
00:00:01.369567 Changing the VM state from 'CREATED' to 'POWERING_ON'.
00:00:01.369599 AIOMgr: Endpoints without assigned bandwidth groups:
00:00:01.369607 AIOMgr:     C:\Users\BlackWidower\VirtualBox VMs\Rarity\Snapshots\{1aa35fb1-1e4e-4c3f-bd03-aa8f4e4005c1}.vdi
00:00:01.369612 AIOMgr:     D:\Rarity.vdi
00:00:01.369743 Changing the VM state from 'POWERING_ON' to 'RUNNING'.
00:00:01.372698 Guest Log: BIOS: VirtualBox 4.2.12
00:00:01.372796 PIT: mode=2 count=0x10000 (65536) - 18.20 Hz (ch=0)
00:00:01.386407 PIIX3 ATA: Ctl#1: RESET, DevSel=0 AIOIf=0 CmdIf0=0x00 (-1 usec ago) CmdIf1=0x00 (-1 usec ago)
00:00:01.386453 PIIX3 ATA: Ctl#1: finished processing RESET
00:00:01.390694 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=0000000000000000 w=720 h=400 bpp=0 cbLine=0x0, flags=0x1
00:00:01.397846 AHCI#0: Reset the HBA
00:00:01.397957 AHCI#0: Port 0 reset
00:00:01.398531 Guest Log: BIOS: AHCI 0-P#0: PCHS=16383/16/63 LCHS=1024/255/63 209715200 sectors
00:00:01.398596 PIT: mode=2 count=0x48d3 (18643) - 64.00 Hz (ch=0)
00:00:01.411221 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=0000000009ef0000 w=640 h=480 bpp=32 cbLine=0xA00, flags=0x1
00:00:01.649718 2D video acceleration is disabled.
00:00:03.875983 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=0000000000000000 w=720 h=400 bpp=0 cbLine=0x0, flags=0x1
00:00:03.876238 PIT: mode=2 count=0x10000 (65536) - 18.20 Hz (ch=0)
00:00:03.876522 Guest Log: BIOS: Boot : bseqnr=1, bootseq=0231
00:00:03.876747 Guest Log: BIOS: Boot from Floppy 0 failed
00:00:03.877006 Guest Log: BIOS: Boot : bseqnr=2, bootseq=0023
00:00:03.877655 Guest Log: BIOS: CDROM boot failure code : 0003
00:00:03.877857 Guest Log: BIOS: Boot from CD-ROM failed
00:00:03.878199 Guest Log: BIOS: Boot : bseqnr=3, bootseq=0002
00:00:03.895163 Guest Log: BIOS: Booting from Hard Disk...
00:00:04.317002 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=0000000009ef0000 w=640 h=480 bpp=32 cbLine=0xA00, flags=0x1
00:00:05.364110 PIT: mode=2 count=0x12a5 (4773) - 249.98 Hz (ch=0)
00:00:05.680229 PIT: mode=0 count=0x10000 (65536) - 18.20 Hz (ch=0)
00:00:05.768160 OHCI: Software reset
00:00:06.003753 EHCI: Hardware reset
00:00:06.003947 EHCI: USB Operational
00:00:06.004226 PIIX3 ATA: Ctl#0: RESET, DevSel=0 AIOIf=0 CmdIf0=0x00 (-1 usec ago) CmdIf1=0x00 (-1 usec ago)
00:00:06.004290 PIIX3 ATA: Ctl#0: finished processing RESET
00:00:06.004595 PIIX3 ATA: Ctl#1: RESET, DevSel=0 AIOIf=0 CmdIf0=0xa0 (-1 usec ago) CmdIf1=0x00 (-1 usec ago)
00:00:06.004655 PIIX3 ATA: Ctl#1: finished processing RESET
00:00:06.013464 OHCI: USB Reset
00:00:06.068414 OHCI: Software reset
00:00:06.068504 OHCI: USB Operational
00:00:06.605881 EHCI: USB Suspended
00:00:07.139329 AHCI#0: Reset the HBA
00:00:07.140546 AHCI#0: Port 0 reset
00:00:07.197445 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=0000000009ef0000 w=640 h=480 bpp=32 cbLine=0xA00, flags=0x1
00:00:07.197539 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=0000000009ef0000 w=640 h=480 bpp=32 cbLine=0xA00, flags=0x1
00:00:07.214547 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=0000000009ef0000 w=640 h=480 bpp=32 cbLine=0xA00, flags=0x1
00:00:11.236148 AIOMgr: Preparing flush failed with VERR_NOT_SUPPORTED, disabling async flushes
00:00:13.528507 Audio: set_record_source ars=0 als=0 (not implemented)
00:00:13.528911 Audio: set_record_source ars=0 als=0 (not implemented)
00:00:13.534584 Audio: set_record_source ars=0 als=0 (not implemented)
00:00:25.045347 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=0000000009ef0000 w=1024 h=768 bpp=32 cbLine=0x1000, flags=0x1
00:07:06.681124 PGM: Failed to procure handy pages; rc=VERR_NO_MEMORY rcAlloc=VINF_SUCCESS rcSeed=VINF_SUCCESS cHandyPages=0x8
00:07:06.681135      cAllPages=0xc1048 cPrivatePages=0x50368 cSharedPages=0x0 cZeroPages=0x70cba
00:07:06.681169 GMM: Statistics:
00:07:06.681170      Allocated pages: 4f36c
00:07:06.681171      Maximum   pages: c009e
00:07:06.681171      Ballooned pages: 0
00:07:06.681302 PGM: Failed to procure handy pages; rc=VERR_NO_MEMORY rcAlloc=VINF_SUCCESS rcSeed=VINF_SUCCESS cHandyPages=0x7
00:07:06.681303      cAllPages=0xc1048 cPrivatePages=0x50369 cSharedPages=0x0 cZeroPages=0x70cb9
00:07:06.681312 GMM: Statistics:
00:07:06.681313      Allocated pages: 4f36c
00:07:06.681313      Maximum   pages: c009e
00:07:06.681314      Ballooned pages: 0
00:07:06.681323 VM: Raising runtime error 'HostMemoryLow' (fFlags=0x2)
00:07:06.681330 AssertLogRel D:\tinderbox\win-4.2\src\VBox\VMM\VMMR3\VMM.cpp(1703) int __cdecl VMMR3EmtRendezvous(struct VM *,unsigned int,int (__cdecl *)(struct VM *,struct VMCPU *,void *),void *): !pVCpu->vmm.s.fInRendezvous
00:07:06.681344 Console: VM runtime error: fatal=false, errorID=HostMemoryLow message="Unable to allocate and lock memory. The virtual machine will be paused. Please close applications to free up memory or close the VM"
00:07:06.719328 Changing the VM state from 'RUNNING' to 'GURU_MEDITATION'.
00:07:58.635812 Console::powerDown(): A request to power off the VM has been issued (mMachineState=Stopping, InUninit=0)
00:07:58.636847 Changing the VM state from 'GURU_MEDITATION' to 'POWERING_OFF'.
00:07:58.636864 ****************** Guest state at power off ******************
00:07:58.636874 Guest CPUM (VCPU 0) state: 
00:07:58.636882 rax=000000000064a3c0 rbx=0000000000001000 rcx=0000000000000200 rdx=0000000000000000
00:07:58.636885 rsi=000000000064a3c0 rdi=ffff880074a00000 r8 =ffff880074a00000 r9 =00000000fffff000
00:07:58.636888 r10=ffffea0001d28000 r11=0000000000000d29 r12=0000000000001000 r13=0000000000001000
00:07:58.636889 r14=ffff880075f88000 r15=0000000000000000
00:07:58.636890 rip=ffffffff81352e40 rsp=ffff880075f89bc0 rbp=ffff880075f89bd0 iopl=0      rf nv up ei pl nz na po nc
00:07:58.636894 cs={0010 base=0000000000000000 limit=ffffffff flags=0000a09b}
00:07:58.636896 ds={0000 base=0000000000000000 limit=000fffff flags=00010000}
00:07:58.636897 es={0000 base=0000000000000000 limit=000fffff flags=00010000}
00:07:58.636897 fs={0000 base=00007f4f7bbf9740 limit=ffffffff flags=0001c000}
00:07:58.636899 gs={0000 base=ffff8800bfc00000 limit=000fffff flags=00010000}
00:07:58.636900 ss={0018 base=0000000000000000 limit=ffffffff flags=0000c093}
00:07:58.636901 cr0=0000000080050033 cr2=00007f557cd3b000 cr3=00000000759ef000 cr4=00000000000006f0
00:07:58.636903 dr0=0000000000000000 dr1=0000000000000000 dr2=0000000000000000 dr3=0000000000000000
00:07:58.636904 dr4=0000000000000000 dr5=0000000000000000 dr6=00000000ffff0ff0 dr7=0000000000000400
00:07:58.636905 gdtr=ffff8800bfc04000:007f  idtr=ffffffff81df4000:0fff  eflags=00010246
00:07:58.636907 ldtr={0000 base=00000000 limit=00000000 flags=00000082}
00:07:58.636908 tr  ={0040 base=ffff8800bfc11b40 limit=00002087 flags=0000008b}
00:07:58.636909 SysEnter={cs=0010 eip=ffffffff816d4de0 esp=0000000000000000}
00:07:58.636911 FCW=037f FSW=0000 FTW=0000 FOP=0000 MXCSR=00001f80 MXCSR_MASK=0000ffff
00:07:58.636913 FPUIP=00000000 CS=0000 Rsrvd1=0000  FPUDP=00000000 DS=0000 Rsvrd2=0000
00:07:58.636914 ST(0)=FPR0={0000'00000000'00000000} t0 +0.0000000000000000000000 ^ 0
00:07:58.636916 ST(1)=FPR1={0000'00000000'00000000} t0 +0.0000000000000000000000 ^ 0
00:07:58.636918 ST(2)=FPR2={0000'00000000'00000000} t0 +0.0000000000000000000000 ^ 0
00:07:58.636919 ST(3)=FPR3={0000'00000000'00000000} t0 +0.0000000000000000000000 ^ 0
00:07:58.636921 ST(4)=FPR4={0000'00000000'00000000} t0 +0.0000000000000000000000 ^ 0
00:07:58.636922 ST(5)=FPR5={0000'00000000'00000000} t0 +0.0000000000000000000000 ^ 0
00:07:58.636923 ST(6)=FPR6={0000'00000000'00000000} t0 +0.0000000000000000000000 ^ 0
00:07:58.636924 ST(7)=FPR7={0000'00000000'00000000} t0 +0.0000000000000000000000 ^ 0
00:07:58.636926 XMM0 =3c06eee7'805e3ab2'bfecd33f'dfde97be  XMM1 =55c7cff3'cff236f1'922ff97f'33ff709b
00:07:58.636928 XMM2 =cc1fcb1f'7fdfcf6f'a1119f7c'6f247c02  XMM3 =ffef983e'b565df3e'91a85b66'8eab7c51
00:07:58.636931 XMM4 =1646bdfd'2e29dd34'bc793130'c747b316  XMM5 =ebb0bcde'e4fc160d'e5c5890d'e206f294
00:07:58.636933 XMM6 =dedd153d'4c7a78c9'2bfc1365'f5204fce  XMM7 =26ffb17e'b4567bea'5a3c0691'1c9bd79f
00:07:58.636935 XMM8 =00000000'00000000'00000000'00000000  XMM9 =00000000'00000000'00000000'00000000
00:07:58.636936 XMM10=00000000'00000000'00000000'00000000  XMM11=00000000'00000000'00000000'00000000
00:07:58.636938 XMM12=00000000'00000000'00000000'00000000  XMM13=00000000'00000000'00000000'00000000
00:07:58.636940 XMM14=00000000'00000000'00000000'00000000  XMM15=00000000'00000000'00000000'00000000
00:07:58.636942 EFER         =0000000000000d01
00:07:58.636942 PAT          =0007010600070106
00:07:58.636943 STAR         =0023001000000000
00:07:58.636944 CSTAR        =ffffffff816d5010
00:07:58.636945 LSTAR        =ffffffff816d3720
00:07:58.636946 SFMASK       =0000000000043700
00:07:58.636946 KERNELGSBASE =0000000000000000
00:07:58.636947 ***
00:07:58.636952 Guest paging mode:  AMD64+NX (changed 3356 times), A20 enabled (changed 2 times)
00:07:58.636953 Shadow paging mode: EPT
00:07:58.636955 Host paging mode:   AMD64+G+NX
00:07:58.636955 ***
00:07:58.636960 Active Timers (pVM=00000000002c0000)
00:07:58.636961 pTimerR3         offNext  offPrev  offSched Clock               Time             Expire HzHint State                     Description
00:07:58.636964 000000000631cd70 fffeb720 00000000 00000000 Real             3839434            3787487      0 2-ACTIVE                  EMT Yielder
00:07:58.636969 0000000006308490 00014860 000148e0 00000000 Real             3839434            3787496      0 2-ACTIVE                  VGA Refresh Timer
00:07:58.636972 000000000631ccf0 00000000 fffeb7a0 00000000 Real             3839434            3788264      0 2-ACTIVE                  CPU Load Timer
00:07:58.636975 0000000006316bd0 00002f60 00000000 00000000 Virt        425311309291       425310150379      0 2-ACTIVE                  Audio timer
00:07:58.636980 0000000006319b30 00000000 ffffd0a0 00000000 Virt        425311309291       425326786090      0 2-ACTIVE                  USB Frame Timer
00:07:58.636984 00000000062f2b40 00001460 00000000 00000000 VrSy        425310055329       425313326554    255 2-ACTIVE                  APIC Timer #0
00:07:58.636987 00000000062f3fa0 00027800 ffffeba0 00000000 VrSy        425310055329       425990000000      0 2-ACTIVE                  MC146818 RTC/CMOS - Second
00:07:58.636990 000000000631b7a0 00000000 fffd8800 00000000 VrSy        425310055329      1199864031601      0 2-ACTIVE                  ACPI PM Timer
00:07:58.636994 ***
00:07:58.637000 Shadow GDT (GCAddr=ff5bb000):
00:07:58.637012 ffd8 - 81980087 fe008980 - base=fe808198 limit=00000087 dpl=0 TSS32Avail Present 16-bit  HyperTSSTrap08
00:07:58.637014 ffe0 - 81100087 fe008980 - base=fe808110 limit=00000087 dpl=0 TSS32Avail Present 16-bit  HyperTSS
00:07:58.637015 ffe8 - 0000ffff 00af9b00 - base=00000000 limit=ffffffff dpl=0 CodeER Accessed Present Page 16-bit  HyperCS64
00:07:58.637017 fff0 - 0000ffff 00cf9300 - base=00000000 limit=ffffffff dpl=0 DataRW Accessed Present Page 32-bit  HyperDS
00:07:58.637019 fff8 - 0000ffff 00cf9b00 - base=00000000 limit=ffffffff dpl=0 CodeER Accessed Present Page 32-bit  HyperCS
00:07:58.637019 ***
00:07:58.637020 ************** End of Guest state at power off ***************
00:07:58.638294 PDMR3PowerOff: 1 262 703 ns run time
00:07:58.638317 Changing the VM state from 'POWERING_OFF' to 'OFF'.
00:07:58.639407 Changing the VM state from 'OFF' to 'DESTROYING'.
00:07:58.639471 ************************* Statistics *************************
00:07:58.639633 /Devices/E1k0/ReceiveBytes       78463994 bytes
00:07:58.639640 /Devices/E1k0/TransmitBytes       1516612 bytes
00:07:58.639645 /Devices/IDE0/ATA0/Unit0/AtapiDMA        0 times
00:07:58.639648 /Devices/IDE0/ATA0/Unit0/AtapiPIO        0 times
00:07:58.639652 /Devices/IDE0/ATA0/Unit0/DMA            0 times
00:07:58.639655 /Devices/IDE0/ATA0/Unit0/PIO            0 times
00:07:58.639659 /Devices/IDE0/ATA0/Unit0/ReadBytes        0 bytes
00:07:58.639673 /Devices/IDE0/ATA0/Unit0/WrittenBytes        0 bytes
00:07:58.639678 /Devices/IDE0/ATA0/Unit1/AtapiDMA        0 times
00:07:58.639681 /Devices/IDE0/ATA0/Unit1/AtapiPIO        0 times
00:07:58.639685 /Devices/IDE0/ATA0/Unit1/DMA            0 times
00:07:58.639688 /Devices/IDE0/ATA0/Unit1/PIO            0 times
00:07:58.639713 /Devices/IDE0/ATA0/Unit1/ReadBytes        0 bytes
00:07:58.639716 /Devices/IDE0/ATA0/Unit1/WrittenBytes        0 bytes
00:07:58.639720 /Devices/IDE0/ATA1/Unit0/AtapiDMA        1 times
00:07:58.639723 /Devices/IDE0/ATA1/Unit0/AtapiPIO      235 times
00:07:58.639727 /Devices/IDE0/ATA1/Unit0/DMA            0 times
00:07:58.639730 /Devices/IDE0/ATA1/Unit0/PIO            0 times
00:07:58.639734 /Devices/IDE0/ATA1/Unit0/ReadBytes        0 bytes
00:07:58.639737 /Devices/IDE0/ATA1/Unit0/WrittenBytes        0 bytes
00:07:58.639740 /Devices/IDE0/ATA1/Unit1/AtapiDMA        0 times
00:07:58.639744 /Devices/IDE0/ATA1/Unit1/AtapiPIO        0 times
00:07:58.639747 /Devices/IDE0/ATA1/Unit1/DMA            0 times
00:07:58.639750 /Devices/IDE0/ATA1/Unit1/PIO            0 times
00:07:58.639754 /Devices/IDE0/ATA1/Unit1/ReadBytes        0 bytes
00:07:58.639757 /Devices/IDE0/ATA1/Unit1/WrittenBytes        0 bytes
00:07:58.639760 /Devices/SATA0/Port0/DMA            40744 times
00:07:58.639766 /Devices/SATA0/Port0/ReadBytes   385396224 bytes
00:07:58.639770 /Devices/SATA0/Port0/WrittenBytes 1214063616 bytes
00:07:58.639776 /Devices/VMMDev/BalloonChunks           0 count
00:07:58.639780 /Drivers/IntNet-0/BadFrames             0 count
00:07:58.639783 /Drivers/IntNet-0/Bytes/Received 78319328 bytes
00:07:58.639787 /Drivers/IntNet-0/Bytes/Sent      1516612 bytes
00:07:58.639790 /Drivers/IntNet-0/Overflows/Recv        0 count
00:07:58.639794 /Drivers/IntNet-0/Overflows/Sent        0 count
00:07:58.639797 /Drivers/IntNet-0/Packets/Lost          0 count
00:07:58.639800 /Drivers/IntNet-0/Packets/Received    52267 count
00:07:58.639804 /Drivers/IntNet-0/Packets/Received-Gso        0 count
00:07:58.639807 /Drivers/IntNet-0/Packets/Sent      21995 count
00:07:58.639811 /Drivers/IntNet-0/Packets/Sent-Gso        0 count
00:07:58.639814 /Drivers/IntNet-0/Packets/Sent-R0    21824 count
00:07:58.639817 /Drivers/IntNet-0/Recv1                 0 ticks/call (           0 ticks,       0 times, max         0, min      -1)
00:07:58.639822 /Drivers/IntNet-0/Recv2                 0 ticks/call (           0 ticks,       0 times, max         0, min      -1)
00:07:58.639826 /Drivers/IntNet-0/Reserved              0 ticks/call (           0 ticks,       0 times, max         0, min      -1)
00:07:58.639830 /Drivers/IntNet-0/Send1             21043 ticks/call (   921638057 ticks,   43796 times, max    600358, min      92)
00:07:58.639835 /Drivers/IntNet-0/Send2             38406 ticks/call (   845173386 ticks,   22006 times, max    598012, min   11520)
00:07:58.639840 /Drivers/IntNet-0/XmitProcessRing    21801 count
00:07:58.639843 /Drivers/IntNet-0/XmitWakeup-R0     21995 count
00:07:58.639847 /Drivers/IntNet-0/XmitWakeup-R3         0 count
00:07:58.639850 /Drivers/IntNet-0/YieldNok              0 count
00:07:58.639853 /Drivers/IntNet-0/YieldOk               0 count
00:07:58.639856 /FT/Checkpoint/Network                  0 times
00:07:58.639860 /FT/Checkpoint/Storage                  0 times
00:07:58.639867 /FT/Received/Mem                        0 bytes
00:07:58.639872 /FT/Received/State                      0 bytes
00:07:58.639876 /FT/Sent/Mem                            0 bytes
00:07:58.639879 /FT/Sent/State                          0 bytes
00:07:58.639883 /FT/Sync/DeltaMem                       0 times
00:07:58.639886 /FT/Sync/DeltaVM                        0 times
00:07:58.639890 /FT/Sync/Full                           0 times
00:07:58.639893 /GMM/VM/Allocated/cBasePages       324460 pages
00:07:58.639897 /GMM/VM/Allocated/cFixedPages           0 pages
00:07:58.639900 /GMM/VM/Allocated/cShadowPages          0 pages
00:07:58.639904 /GMM/VM/Reserved/cBasePages        786590 pages
00:07:58.639907 /GMM/VM/Reserved/cFixedPages         4100 pages
00:07:58.639911 /GMM/VM/Reserved/cShadowPages           1 pages
00:07:58.639914 /GMM/VM/cBalloonedPages                 0 pages
00:07:58.639917 /GMM/VM/cMaxBalloonedPages              0 pages
00:07:58.639921 /GMM/VM/cPrivatePages              324460 pages
00:07:58.639924 /GMM/VM/cReqActuallyBalloonedPages        0 pages
00:07:58.639928 /GMM/VM/cReqBalloonedPages              0 pages
00:07:58.639931 /GMM/VM/cReqDeflatePages                0 pages
00:07:58.639934 /GMM/VM/cShareableModules               0 count
00:07:58.639938 /GMM/VM/cSharedPages                    0 pages
00:07:58.639941 /GMM/VM/enmPolicy                       1 
00:07:58.639945 /GMM/VM/enmPriority                     2 
00:07:58.639948 /GMM/VM/fBallooningEnabled       false    
00:07:58.639952 /GMM/VM/fMayAllocate             false    
00:07:58.639955 /GMM/VM/fSharedPagingEnabled     false    
00:07:58.639958 /GMM/cAllocatedPages               844768 pages
00:07:58.639962 /GMM/cBalloonedPages                    0 pages
00:07:58.639965 /GMM/cChunks                         1650 count
00:07:58.639969 /GMM/cDuplicatePages                    0 pages
00:07:58.639972 /GMM/cFreedChunks                     591 count
00:07:58.639976 /GMM/cLeftBehindSharedPages             0 pages
00:07:58.639979 /GMM/cMaxPages                   4294967295 pages
00:07:58.639983 /GMM/cOverCommittedPages                0 pages
00:07:58.639986 /GMM/cReservedPages               1320262 pages
00:07:58.639990 /GMM/cShareableModules                  0 count
00:07:58.639993 /GMM/cSharedPages                       0 pages
00:07:58.639997 /GVMM/EMTs                              4 calls
00:07:58.640000 /GVMM/HostCPUs                          8 calls
00:07:58.640004 /GVMM/HostCpus/0                        0 
00:07:58.640007 /GVMM/HostCpus/0/CurTimerHz             0 Hz
00:07:58.640011 /GVMM/HostCpus/0/DesiredHz              0 Hz
00:07:58.640014 /GVMM/HostCpus/0/PPTChanges             0 times
00:07:58.640018 /GVMM/HostCpus/0/PPTStarts              0 times
00:07:58.640021 /GVMM/HostCpus/0/idxCpuSet              0 
00:07:58.640024 /GVMM/HostCpus/1                        1 
00:07:58.640028 /GVMM/HostCpus/1/CurTimerHz             0 Hz
00:07:58.640031 /GVMM/HostCpus/1/DesiredHz              0 Hz
00:07:58.640034 /GVMM/HostCpus/1/PPTChanges             0 times
00:07:58.640038 /GVMM/HostCpus/1/PPTStarts              0 times
00:07:58.640041 /GVMM/HostCpus/1/idxCpuSet              1 
00:07:58.640044 /GVMM/HostCpus/2                        2 
00:07:58.640048 /GVMM/HostCpus/2/CurTimerHz             0 Hz
00:07:58.640051 /GVMM/HostCpus/2/DesiredHz              0 Hz
00:07:58.640055 /GVMM/HostCpus/2/PPTChanges             0 times
00:07:58.640058 /GVMM/HostCpus/2/PPTStarts              0 times
00:07:58.640062 /GVMM/HostCpus/2/idxCpuSet              2 
00:07:58.640065 /GVMM/HostCpus/3                        3 
00:07:58.640069 /GVMM/HostCpus/3/CurTimerHz             0 Hz
00:07:58.640072 /GVMM/HostCpus/3/DesiredHz              0 Hz
00:07:58.640075 /GVMM/HostCpus/3/PPTChanges             0 times
00:07:58.640079 /GVMM/HostCpus/3/PPTStarts              0 times
00:07:58.640082 /GVMM/HostCpus/3/idxCpuSet              3 
00:07:58.640085 /GVMM/HostCpus/4                        4 
00:07:58.640089 /GVMM/HostCpus/4/CurTimerHz             0 Hz
00:07:58.640094 /GVMM/HostCpus/4/DesiredHz              0 Hz
00:07:58.640098 /GVMM/HostCpus/4/PPTChanges             0 times
00:07:58.640102 /GVMM/HostCpus/4/PPTStarts              0 times
00:07:58.640105 /GVMM/HostCpus/4/idxCpuSet              4 
00:07:58.640109 /GVMM/HostCpus/5                        5 
00:07:58.640112 /GVMM/HostCpus/5/CurTimerHz             0 Hz
00:07:58.640115 /GVMM/HostCpus/5/DesiredHz              0 Hz
00:07:58.640119 /GVMM/HostCpus/5/PPTChanges             0 times
00:07:58.640122 /GVMM/HostCpus/5/PPTStarts              0 times
00:07:58.640126 /GVMM/HostCpus/5/idxCpuSet              5 
00:07:58.640129 /GVMM/HostCpus/6                        6 
00:07:58.640132 /GVMM/HostCpus/6/CurTimerHz             0 Hz
00:07:58.640136 /GVMM/HostCpus/6/DesiredHz              0 Hz
00:07:58.640139 /GVMM/HostCpus/6/PPTChanges             0 times
00:07:58.640143 /GVMM/HostCpus/6/PPTStarts              0 times
00:07:58.640146 /GVMM/HostCpus/6/idxCpuSet              6 
00:07:58.640149 /GVMM/HostCpus/7                        7 
00:07:58.640153 /GVMM/HostCpus/7/CurTimerHz             0 Hz
00:07:58.640156 /GVMM/HostCpus/7/DesiredHz              0 Hz
00:07:58.640159 /GVMM/HostCpus/7/PPTChanges             0 times
00:07:58.640162 /GVMM/HostCpus/7/PPTStarts              0 times
00:07:58.640166 /GVMM/HostCpus/7/idxCpuSet              7 
00:07:58.640169 /GVMM/Sum/HaltBlocking            2339007 calls
00:07:58.640173 /GVMM/Sum/HaltCalls               2338947 calls
00:07:58.640176 /GVMM/Sum/HaltNotBlocking               3 calls
00:07:58.640179 /GVMM/Sum/HaltTimeouts             781516 calls
00:07:58.640183 /GVMM/Sum/HaltWakeUps                   0 calls
00:07:58.640186 /GVMM/Sum/PokeCalls                254867 calls
00:07:58.640190 /GVMM/Sum/PokeNotBusy               10512 calls
00:07:58.640193 /GVMM/Sum/PollCalls                 30485 calls
00:07:58.640197 /GVMM/Sum/PollHalts                     0 calls
00:07:58.640200 /GVMM/Sum/PollWakeUps                   0 calls
00:07:58.640203 /GVMM/Sum/WakeUpCalls             1579083 calls
00:07:58.640207 /GVMM/Sum/WakeUpNotHalted          154768 calls
00:07:58.640210 /GVMM/Sum/WakeUpWakeUps                 0 calls
00:07:58.640214 /GVMM/VM/HaltBlocking              209153 calls
00:07:58.640218 /GVMM/VM/HaltCalls                 209154 calls
00:07:58.640221 /GVMM/VM/HaltNotBlocking                1 calls
00:07:58.640224 /GVMM/VM/HaltTimeouts              108631 calls
00:07:58.640228 /GVMM/VM/HaltWakeUps                    0 calls
00:07:58.640231 /GVMM/VM/PokeCalls                  30306 calls
00:07:58.640235 /GVMM/VM/PokeNotBusy                 1961 calls
00:07:58.640238 /GVMM/VM/PollCalls                   4966 calls
00:07:58.640242 /GVMM/VM/PollHalts                      0 calls
00:07:58.640245 /GVMM/VM/PollWakeUps                    0 calls
00:07:58.640248 /GVMM/VM/WakeUpCalls               101913 calls
00:07:58.640252 /GVMM/VM/WakeUpNotHalted            24836 calls
00:07:58.640255 /GVMM/VM/WakeUpWakeUps                  0 calls
00:07:58.640259 /GVMM/VMs                               2 calls
00:07:58.640263 /IEM/CPU0/cInstructions                 0 count
00:07:58.640266 /IEM/CPU0/cPotentialExits               0 count
00:07:58.640270 /IEM/CPU0/cRetAspectNotImplemented        0 count
00:07:58.640273 /IEM/CPU0/cRetErrStatuses               0 count
00:07:58.640276 /IEM/CPU0/cRetInfStatuses               0 count
00:07:58.640280 /IEM/CPU0/cRetInstrNotImplemented        0 count
00:07:58.640283 /IEM/CPU0/cbWritten                     0 bytes
00:07:58.640286 /MM/HyperHeap/cbFree              1030224 bytes
00:07:58.640290 /MM/HyperHeap/cbHeap              1310400 bytes
00:07:58.640293 /PDM/BlkCache/cbCached            4984832 bytes
00:07:58.640297 /PDM/BlkCache/cbCachedFru               0 bytes
00:07:58.640300 /PDM/BlkCache/cbCachedMruIn       4984832 bytes
00:07:58.640304 /PDM/BlkCache/cbCachedMruOut      2097152 bytes
00:07:58.640307 /PDM/BlkCache/cbMax               5242880 bytes
00:07:58.640311 /PDM/CritSects/8237A#0 Auto/ContentionR3        0 times
00:07:58.640316 /PDM/CritSects/8237A#0 Auto/ContentionRZLock        0 times
00:07:58.640320 /PDM/CritSects/8237A#0 Auto/ContentionRZUnlock        0 times
00:07:58.640324 /PDM/CritSects/AHCI#0/ContentionR3        0 times
00:07:58.640328 /PDM/CritSects/AHCI#0/ContentionRZLock        9 times
00:07:58.640331 /PDM/CritSects/AHCI#0/ContentionRZUnlock        0 times
00:07:58.640334 /PDM/CritSects/ATA#0/ContentionR3        0 times
00:07:58.640338 /PDM/CritSects/ATA#0/ContentionRZLock        0 times
00:07:58.640341 /PDM/CritSects/ATA#0/ContentionRZUnlock        0 times
00:07:58.640345 /PDM/CritSects/ATA#1/ContentionR3        0 times
00:07:58.640348 /PDM/CritSects/ATA#1/ContentionRZLock       17 times
00:07:58.640351 /PDM/CritSects/ATA#1/ContentionRZUnlock        0 times
00:07:58.640355 /PDM/CritSects/AudioSniffer#0 Auto/ContentionR3        0 times
00:07:58.640358 /PDM/CritSects/AudioSniffer#0 Auto/ContentionRZLock        0 times
00:07:58.640361 /PDM/CritSects/AudioSniffer#0 Auto/ContentionRZUnlock        0 times
00:07:58.640365 /PDM/CritSects/E1000#0/ContentionR3        0 times
00:07:58.640368 /PDM/CritSects/E1000#0/ContentionRZLock       20 times
00:07:58.640372 /PDM/CritSects/E1000#0/ContentionRZUnlock        0 times
00:07:58.640375 /PDM/CritSects/E1000#0RX/ContentionR3        0 times
00:07:58.640378 /PDM/CritSects/E1000#0RX/ContentionRZLock        6 times
00:07:58.640382 /PDM/CritSects/E1000#0RX/ContentionRZUnlock        0 times
00:07:58.640385 /PDM/CritSects/E1000#0TX/ContentionR3        0 times
00:07:58.640388 /PDM/CritSects/E1000#0TX/ContentionRZLock        0 times
00:07:58.640391 /PDM/CritSects/E1000#0TX/ContentionRZUnlock        0 times
00:07:58.640395 /PDM/CritSects/EM-REM/ContentionR3        0 times
00:07:58.640398 /PDM/CritSects/EM-REM/ContentionRZLock        0 times
00:07:58.640402 /PDM/CritSects/EM-REM/ContentionRZUnlock        0 times
00:07:58.640405 /PDM/CritSects/FTM/ContentionR3         0 times
00:07:58.640408 /PDM/CritSects/FTM/ContentionRZLock        0 times
00:07:58.640411 /PDM/CritSects/FTM/ContentionRZUnlock        0 times
00:07:58.640415 /PDM/CritSects/IOM Lock/ContentionR3        0 times
00:07:58.640418 /PDM/CritSects/IOM Lock/ContentionRZLock        0 times
00:07:58.640421 /PDM/CritSects/IOM Lock/ContentionRZUnlock        0 times
00:07:58.640425 /PDM/CritSects/IntNetXmit_0/ContentionR3        2 times
00:07:58.640428 /PDM/CritSects/IntNetXmit_0/ContentionRZLock      171 times
00:07:58.640431 /PDM/CritSects/IntNetXmit_0/ContentionRZUnlock        0 times
00:07:58.640435 /PDM/CritSects/MM-HYPER/ContentionR3        0 times
00:07:58.640438 /PDM/CritSects/MM-HYPER/ContentionRZLock        0 times
00:07:58.640451 /PDM/CritSects/MM-HYPER/ContentionRZUnlock        0 times
00:07:58.640454 /PDM/CritSects/NOP/ContentionR3         0 times
00:07:58.640458 /PDM/CritSects/NOP/ContentionRZLock        0 times
00:07:58.640461 /PDM/CritSects/NOP/ContentionRZUnlock        0 times
00:07:58.640464 /PDM/CritSects/PDM/ContentionR3         0 times
00:07:58.640468 /PDM/CritSects/PDM/ContentionRZLock      859 times
00:07:58.640471 /PDM/CritSects/PDM/ContentionRZUnlock        6 times
00:07:58.640475 /PDM/CritSects/PGM/ContentionR3         0 times
00:07:58.640478 /PDM/CritSects/PGM/ContentionRZLock      267 times
00:07:58.640481 /PDM/CritSects/PGM/ContentionRZUnlock        0 times
00:07:58.640485 /PDM/CritSects/PS2K#0/ContentionR3        0 times
00:07:58.640488 /PDM/CritSects/PS2K#0/ContentionRZLock        0 times
00:07:58.640491 /PDM/CritSects/PS2K#0/ContentionRZUnlock        0 times
00:07:58.640495 /PDM/CritSects/PS2KM#0/ContentionR3        0 times
00:07:58.640498 /PDM/CritSects/PS2KM#0/ContentionRZLock        0 times
00:07:58.640501 /PDM/CritSects/PS2KM#0/ContentionRZUnlock        0 times
00:07:58.640505 /PDM/CritSects/REM-Register/ContentionR3        0 times
00:07:58.640508 /PDM/CritSects/REM-Register/ContentionRZLock        0 times
00:07:58.640511 /PDM/CritSects/REM-Register/ContentionRZUnlock        0 times
00:07:58.640515 /PDM/CritSects/TM Timer Lock/ContentionR3        0 times
00:07:58.640558 /PDM/CritSects/TM Timer Lock/ContentionRZLock        0 times
00:07:58.640564 /PDM/CritSects/TM Timer Lock/ContentionRZUnlock        0 times
00:07:58.640568 /PDM/CritSects/TM VirtualSync Lock/ContentionR3        0 times
00:07:58.640571 /PDM/CritSects/TM VirtualSync Lock/ContentionRZLock        0 times
00:07:58.640575 /PDM/CritSects/TM VirtualSync Lock/ContentionRZUnlock        0 times
00:07:58.640578 /PDM/CritSects/VGA#u/ContentionR3        0 times
00:07:58.640582 /PDM/CritSects/VGA#u/ContentionRZLock        0 times
00:07:58.640585 /PDM/CritSects/VGA#u/ContentionRZUnlock        0 times
00:07:58.640588 /PDM/CritSects/VMMDev#0 Auto/ContentionR3        0 times
00:07:58.640592 /PDM/CritSects/VMMDev#0 Auto/ContentionRZLock        0 times
00:07:58.640595 /PDM/CritSects/VMMDev#0 Auto/ContentionRZUnlock        0 times
00:07:58.640599 /PDM/CritSects/VMMDev#u/ContentionR3        0 times
00:07:58.640602 /PDM/CritSects/VMMDev#u/ContentionRZLock        0 times
00:07:58.640605 /PDM/CritSects/VMMDev#u/ContentionRZUnlock        0 times
00:07:58.640609 /PDM/CritSects/acpi0/ContentionR3        0 times
00:07:58.640612 /PDM/CritSects/acpi0/ContentionRZLock        0 times
00:07:58.640615 /PDM/CritSects/acpi0/ContentionRZUnlock        0 times
00:07:58.640619 /PDM/CritSects/ahci#0 Auto/ContentionR3        0 times
00:07:58.640622 /PDM/CritSects/ahci#0 Auto/ContentionRZLock        0 times
00:07:58.640626 /PDM/CritSects/ahci#0 Auto/ContentionRZUnlock        0 times
00:07:58.640629 /PDM/CritSects/e1000#0 Auto/ContentionR3        0 times
00:07:58.640632 /PDM/CritSects/e1000#0 Auto/ContentionRZLock        0 times
00:07:58.640636 /PDM/CritSects/e1000#0 Auto/ContentionRZUnlock        0 times
00:07:58.640639 /PDM/CritSects/ichac97#0 Auto/ContentionR3        0 times
00:07:58.640642 /PDM/CritSects/ichac97#0 Auto/ContentionRZLock        0 times
00:07:58.640646 /PDM/CritSects/ichac97#0 Auto/ContentionRZUnlock        0 times
00:07:58.640649 /PDM/CritSects/mc146818#0 Auto/ContentionR3        0 times
00:07:58.640653 /PDM/CritSects/mc146818#0 Auto/ContentionRZLock        0 times
00:07:58.640656 /PDM/CritSects/mc146818#0 Auto/ContentionRZUnlock        0 times
00:07:58.640659 /PDM/CritSects/pcarch#0 Auto/ContentionR3        0 times
00:07:58.640663 /PDM/CritSects/pcarch#0 Auto/ContentionRZLock        0 times
00:07:58.640666 /PDM/CritSects/pcarch#0 Auto/ContentionRZUnlock        0 times
00:07:58.640669 /PDM/CritSects/pcbios#0 Auto/ContentionR3        0 times
00:07:58.640673 /PDM/CritSects/pcbios#0 Auto/ContentionRZLock        0 times
00:07:58.640676 /PDM/CritSects/pcbios#0 Auto/ContentionRZUnlock        0 times
00:07:58.640679 /PDM/CritSects/pckbd#0 Auto/ContentionR3        0 times
00:07:58.640683 /PDM/CritSects/pckbd#0 Auto/ContentionRZLock        0 times
00:07:58.640686 /PDM/CritSects/pckbd#0 Auto/ContentionRZUnlock        0 times
00:07:58.640689 /PDM/CritSects/piix3ide#0 Auto/ContentionR3        0 times
00:07:58.640693 /PDM/CritSects/piix3ide#0 Auto/ContentionRZLock        0 times
00:07:58.640696 /PDM/CritSects/piix3ide#0 Auto/ContentionRZUnlock        0 times
00:07:58.640699 /PDM/CritSects/pit/ContentionR3         0 times
00:07:58.640702 /PDM/CritSects/pit/ContentionRZLock        0 times
00:07:58.640706 /PDM/CritSects/pit/ContentionRZUnlock        0 times
00:07:58.640717 /PDM/CritSects/usb-ehci#0 Auto/ContentionR3        0 times
00:07:58.640721 /PDM/CritSects/usb-ehci#0 Auto/ContentionRZLock        0 times
00:07:58.640725 /PDM/CritSects/usb-ehci#0 Auto/ContentionRZUnlock        0 times
00:07:58.640728 /PDM/CritSects/usb-ohci#0 Auto/ContentionR3        0 times
00:07:58.640731 /PDM/CritSects/usb-ohci#0 Auto/ContentionRZLock        0 times
00:07:58.640735 /PDM/CritSects/usb-ohci#0 Auto/ContentionRZUnlock        0 times
00:07:58.640738 /PDM/CritSects/vga#0 Auto/ContentionR3        0 times
00:07:58.640741 /PDM/CritSects/vga#0 Auto/ContentionRZLock        0 times
00:07:58.640745 /PDM/CritSects/vga#0 Auto/ContentionRZUnlock        0 times
00:07:58.640750 /PDM/Queue/AHCI-Xmit/AllocFailures        0 times
00:07:58.640754 /PDM/Queue/AHCI-Xmit/Flush              0 calls
00:07:58.640758 /PDM/Queue/AHCI-Xmit/FlushLeftovers        0 times
00:07:58.640762 /PDM/Queue/AHCI-Xmit/Insert         65981 calls
00:07:58.640765 /PDM/Queue/AHCI-Xmit/cItems            60 count
00:07:58.640769 /PDM/Queue/AHCI-Xmit/cbItem            32 bytes
00:07:58.640772 /PDM/Queue/DevHlp/AllocFailures         0 times
00:07:58.640776 /PDM/Queue/DevHlp/Flush                 0 calls
00:07:58.640779 /PDM/Queue/DevHlp/FlushLeftovers        0 times
00:07:58.640782 /PDM/Queue/DevHlp/Insert                0 calls
00:07:58.640786 /PDM/Queue/DevHlp/cItems                8 count
00:07:58.640789 /PDM/Queue/DevHlp/cbItem               56 bytes
00:07:58.640793 /PDM/Queue/E1000-Rcv/AllocFailures        0 times
00:07:58.640796 /PDM/Queue/E1000-Rcv/Flush              0 calls
00:07:58.640800 /PDM/Queue/E1000-Rcv/FlushLeftovers        0 times
00:07:58.640803 /PDM/Queue/E1000-Rcv/Insert         37544 calls
00:07:58.640807 /PDM/Queue/E1000-Rcv/cItems             1 count
00:07:58.640811 /PDM/Queue/E1000-Rcv/cbItem            24 bytes
00:07:58.640814 /PDM/Queue/E1000-Xmit/AllocFailures        0 times
00:07:58.640818 /PDM/Queue/E1000-Xmit/Flush             0 calls
00:07:58.640821 /PDM/Queue/E1000-Xmit/FlushLeftovers        0 times
00:07:58.640824 /PDM/Queue/E1000-Xmit/Insert            0 calls
00:07:58.640828 /PDM/Queue/E1000-Xmit/cItems            1 count
00:07:58.640831 /PDM/Queue/E1000-Xmit/cbItem           24 bytes
00:07:58.640835 /PDM/Queue/Keyboard/AllocFailures        0 times
00:07:58.640838 /PDM/Queue/Keyboard/Flush               0 calls
00:07:58.640842 /PDM/Queue/Keyboard/FlushLeftovers        0 times
00:07:58.640845 /PDM/Queue/Keyboard/Insert             86 calls
00:07:58.640848 /PDM/Queue/Keyboard/cItems             64 count
00:07:58.640852 /PDM/Queue/Keyboard/cbItem             32 bytes
00:07:58.640855 /PDM/Queue/Mouse/AllocFailures          0 times
00:07:58.640859 /PDM/Queue/Mouse/Flush                  0 calls
00:07:58.640862 /PDM/Queue/Mouse/FlushLeftovers         0 times
00:07:58.640865 /PDM/Queue/Mouse/Insert                 0 calls
00:07:58.640869 /PDM/Queue/Mouse/cItems               128 count
00:07:58.640872 /PDM/Queue/Mouse/cbItem                56 bytes
00:07:58.640876 /PDM/Queue/Mouse_1/AllocFailures        0 times
00:07:58.640879 /PDM/Queue/Mouse_1/Flush                0 calls
00:07:58.640883 /PDM/Queue/Mouse_1/FlushLeftovers        0 times
00:07:58.640886 /PDM/Queue/Mouse_1/Insert            4261 calls
00:07:58.640889 /PDM/Queue/Mouse_1/cItems             128 count
00:07:58.640893 /PDM/Queue/Mouse_1/cbItem              56 bytes
00:07:58.640896 /PGM/CPU0/cA20Changes                   2 times
00:07:58.640900 /PGM/CPU0/cGuestModeChanges          3356 times
00:07:58.640903 /PGM/ChunkR3Map/Mapped                634 count
00:07:58.640907 /PGM/ChunkR3Map/Unmapped                0 count
00:07:58.640910 /PGM/ChunkR3Map/c                     634 count
00:07:58.640914 /PGM/ChunkR3Map/cMax             4294967295 count
00:07:58.640918 /PGM/LargePage/Recheck                  0 times
00:07:58.640921 /PGM/LargePage/Refused                  2 times
00:07:58.640924 /PGM/LargePage/Reused                 498 times
00:07:58.640929 /PGM/Page/cAllPages                790600 count
00:07:58.640933 /PGM/Page/cBalloonedPages               0 count
00:07:58.640936 /PGM/Page/cHandyPages                   7 count
00:07:58.640939 /PGM/Page/cLargePages                 300 count
00:07:58.640943 /PGM/Page/cLargePagesDisabled           0 count
00:07:58.640946 /PGM/Page/cMonitoredPages               0 count
00:07:58.640950 /PGM/Page/cPrivatePages            328553 count
00:07:58.640953 /PGM/Page/cPureMmioPages               38 count
00:07:58.640956 /PGM/Page/cReadLockedPages              0 count
00:07:58.640960 /PGM/Page/cReusedSharedPages            0 count
00:07:58.640963 /PGM/Page/cSharedPages                  0 count
00:07:58.640966 /PGM/Page/cWriteLockedPages             0 count
00:07:58.640973 /PGM/Page/cWrittenToPages               0 count
00:07:58.640979 /PGM/Page/cZeroPages               462009 count
00:07:58.640982 /PGM/ShMod/Check                        0 ticks/call (           0 ticks,       0 times, max         0, min      -1)
00:07:58.640987 /PGM/cRelocations                       0 times
00:07:58.640990 /PROF/CPU0/EM/Capped                    0 ticks/call (           0 ticks,       0 times, max         0, min      -1)
00:07:58.640994 /PROF/CPU0/EM/ForcedActions        643752 times
00:07:58.640998 /PROF/CPU0/EM/Halted               100728 times
00:07:58.641002 /PROF/CPU0/EM/RAWTotal                  0 times
00:07:58.641005 /PROF/CPU0/EM/REMTotal                  0 times
00:07:58.641008 /PROF/CPU0/EM/Total              975998941828 ticks/call (975998941828 ticks,       1 times, max 975998941828, min 975998941828)
00:07:58.641014 /PROF/VM/CPU0/Halt/Block          1476344 ns/call (308702126603 ticks,  209099 times, max   8354145, min       1)
00:07:58.641019 /PROF/VM/CPU0/Halt/BlockInsomnia        0 ns/call (           0 ticks,       0 times, max         0, min      -1)
00:07:58.641023 /PROF/VM/CPU0/Halt/BlockOnTime          0 ns/call (           0 ticks,       0 times, max         0, min      -1)
00:07:58.641027 /PROF/VM/CPU0/Halt/BlockOverslept        0 ns/call (           0 ticks,       0 times, max         0, min      -1)
00:07:58.641031 /PROF/VM/CPU0/Halt/Timers            1384 ns/call (  2556696992 ticks, 1846535 times, max 106592532, min       2)
00:07:58.641036 /PROF/VM/CPU0/Halt/Yield             2905 ns/call (    14430261 ticks,    4966 times, max     77484, min    1082)
00:07:58.641041 /REM/TbFlushCount                       0 times
00:07:58.641045 /REM/TbPhysInvldCount                7776 times
00:07:58.641048 /REM/TlbFlushCount                   7547 times
00:07:58.641052 /SELM/HyperSels/Changed                 0 times
00:07:58.641056 /SELM/HyperSels/Scan                    0 times
00:07:58.641059 /SELM/LoadHidSel/GstReadErrors          0 times
00:07:58.641062 /SELM/LoadHidSel/NoGoodGuest            0 times
00:07:58.641066 /SELM/UpdateFromCPUM/AlreadyStaleCS        0 times
00:07:58.641069 /SELM/UpdateFromCPUM/AlreadyStaleDS        0 times
00:07:58.641073 /SELM/UpdateFromCPUM/AlreadyStaleES        0 times
00:07:58.641076 /SELM/UpdateFromCPUM/AlreadyStaleFS        0 times
00:07:58.641079 /SELM/UpdateFromCPUM/AlreadyStaleGS        0 times
00:07:58.641082 /SELM/UpdateFromCPUM/AlreadyStaleSS        0 times
00:07:58.641085 /SELM/UpdateFromCPUM/DetectedStaleCS        0 times
00:07:58.641089 /SELM/UpdateFromCPUM/DetectedStaleDS        0 times
00:07:58.641092 /SELM/UpdateFromCPUM/DetectedStaleES        0 times
00:07:58.641095 /SELM/UpdateFromCPUM/DetectedStaleFS        0 times
00:07:58.641099 /SELM/UpdateFromCPUM/DetectedStaleGS        0 times
00:07:58.641102 /SELM/UpdateFromCPUM/DetectedStaleSS        0 times
00:07:58.641105 /SELM/UpdateFromCPUM/StaleToUnstale        0 times
00:07:58.641109 /TM/CPU/00/cNsExecuting          97301737203 ns
00:07:58.641113 /TM/CPU/00/cNsHalted             311661271322 ns
00:07:58.641116 /TM/CPU/00/cNsOther              16348301866 ns
00:07:58.641120 /TM/CPU/00/cNsTotal              425311310391 ns
00:07:58.641124 /TM/CPU/00/cPeriodsExecuting      4375141 count
00:07:58.641127 /TM/CPU/00/cPeriodsHalted           99848 count
00:07:58.641131 /TM/CPU/00/pctExecuting                96 %
00:07:58.641134 /TM/CPU/00/pctHalted                    0 %
00:07:58.641137 /TM/CPU/00/pctOther                     3 %
00:07:58.641141 /TM/CPU/pctExecuting                   96 %
00:07:58.641144 /TM/CPU/pctHalted                       0 %
00:07:58.641148 /TM/CPU/pctOther                        3 %
00:07:58.641151 /TM/MaxHzHint                           0 Hz
00:07:58.641155 /TM/R0/1nsSteps                      2091 times
00:07:58.641158 /TM/R3/1nsSteps                      2449 times
00:07:58.641162 /TM/TSC/offCPU0                         0 ticks
00:07:58.641166 /TM/VirtualSync/CurrentOffset       78221 ns
00:07:58.641171 /VUSB/0/cUrbsInPool                     0 count
00:07:58.641175 /VUSB/1/cUrbsInPool                     1 count
00:07:58.641179 ********************* End of statistics **********************
00:07:58.702886 Changing the VM state from 'DESTROYING' to 'TERMINATED'.
```

---

### Post by yeswetran on 2013-05-19
Wait, I think I'm going a bit head-first with this, but maybe you should uninstall Lubuntu from VirtualBox and reinstall a new version's .iso; or you could use Peppermint OS, a lighter, more compact version. I have a live CD with this. Download Peppermint at peppermintos.com

---

