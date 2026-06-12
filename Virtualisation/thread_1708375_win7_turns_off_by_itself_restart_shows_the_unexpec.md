---
title: "win7 turns off by itself? restart shows the unexpected shut down page"
date: 2011-03-16
forum: Virtualisation
---

### Post by sdowney717 on 2011-03-16
If I stop interacting with the VM, looking at the log it wants to enter a sleep but it powers off?
by itself?

I did find this, [http://forums.virtualbox.org/viewtopic.php?f=2&t=38232](http://forums.virtualbox.org/viewtopic.php?f=2&t=38232)
so maybe I need to update vbox

vbox.log file snipet

```
00:02:01.313 PIT: mode=2 count=0x4ad (1197) - 996.81 Hz (ch=0)
00:02:29.981 NAT: DHCP offered IP address 10.0.2.15
00:19:22.383 Stopping the host clipboard service
00:19:22.403 ClipStopX11: stopping the shared clipboard X11 backend
00:19:22.403 Shared clipboard: shared clipboard thread terminated successfully
00:19:45.316 OHCI: USB Operational
00:19:45.316 EHCI: USB Operational
00:19:45.345 OHCI: USB Suspended
00:19:45.346 EHCI: USB Suspended
00:19:45.451 Changing the VM state from 'RUNNING' to 'RESETTING'.
00:19:45.477 CPUMSetGuestCpuIdFeature: Enabled APIC
00:19:45.477 CPUMSetGuestCpuIdFeature: Disabled x2APIC
00:19:45.477 PIT: mode=3 count=0x10000 (65536) - 18.20 Hz (ch=0)
00:19:45.483 PIIX3 ATA: Ctl#0: finished processing RESET
00:19:45.483 PIIX3 ATA: Ctl#1: finished processing RESET
00:19:45.597 AHCI ATA: Ctl: finished processing RESET
00:19:45.597 AHCI ATA: Ctl: finished processing RESET
00:19:45.597 Changing the VM state from 'RESETTING' to 'RUNNING'.
00:19:45.610 Guest Log: BIOS: VirtualBox 4.0.2
00:19:45.610 PIT: mode=2 count=0x10000 (65536) - 18.20 Hz (ch=0)
00:19:45.691 PIIX3 ATA: Ctl#1: RESET, DevSel=0 AIOIf=0 CmdIf0=0xa0 (-1 usec ago) CmdIf1=0x00 (-1 usec ago)
00:19:45.693 PIIX3 ATA: Ctl#1: finished processing RESET
00:19:45.693 AHCI ATA: Ctl: RESET, DevSel=0 AIOIf=0 CmdIf0=0x30 (-1 usec ago) CmdIf1=0x00 (-1 usec ago)
00:19:45.693 AHCI ATA: Ctl: finished processing RESET
00:19:45.693 Guest Log: BIOS: ata2-0: PCHS=16383/16/63 LCHS=1024/255/63
00:19:45.693 PIT: mode=2 count=0x48d3 (18643) - 64.00 Hz (ch=0)
00:19:45.711 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=afa00000 w=640 h=480 bpp=32 cbLine=0xA00, flags=0x1
00:19:48.165 PIT: mode=2 count=0x10000 (65536) - 18.20 Hz (ch=0)
00:19:48.166 Guest Log: BIOS: Boot from Floppy 0 failed
00:19:48.166 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=00000000 w=720 h=400 bpp=0 cbLine=0x0, flags=0x1
00:19:48.167 Guest Log: BIOS: CDROM boot failure code : 0003
00:19:48.168 Guest Log: BIOS: Boot from CD-ROM failed
00:19:48.168 Guest Log: BIOS: Booting from Hard Disk...
00:19:48.206 AHCI ATA: Ctl: RESET, DevSel=0 AIOIf=0 CmdIf0=0xc4 (-1 usec ago) CmdIf1=0x00 (-1 usec ago)
00:19:48.206 AHCI ATA: Ctl: finished processing RESET
00:19:48.860 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=afa00000 w=1024 h=768 bpp=24 cbLine=0xC00, flags=0x1
00:19:53.278 PIT: mode=2 count=0x2ead (11949) - 99.85 Hz (ch=0)
00:19:56.048 Guest Additions information report: Version 4.0.2 r69518 '4.0.2'
00:19:56.049 Guest Additions information report: Interface = 0x00010004 osType = 0x00037000
00:19:56.049 Guest Additions capability report: (0x0) seamless: no, hostWindowMapping: no, graphics: no
00:19:56.049 Guest reported fixed hypervisor window at 0x8cc00000 (size = 0xc00000, rc = VINF_SUCCESS)
00:20:03.853 Guest Log: VBoxVideo: using HGSMI
00:20:04.052 OHCI: Software reset
00:20:04.052 OHCI: USB Reset
00:20:04.107 OHCI: USB Operational
00:20:04.146 EHCI: Hardware reset
00:20:04.146 EHCI: USB Operational
00:20:09.817 EHCI: USB Suspended
00:20:09.817 OHCI: USB Suspended
00:20:15.970 Guest Log: VBoxDisp[0]: VBVA enabled
00:20:15.970 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=afa00000 w=723 h=522 bpp=32 cbLine=0xB4C, flags=0x1
00:20:15.983 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=afa00000 w=723 h=522 bpp=32 cbLine=0xB4C, flags=0x1
00:20:25.475 NAT: DHCP offered IP address 10.0.2.15
00:20:30.047 NAT: DHCP offered IP address 10.0.2.15
00:20:37.055 NAT: DHCP offered IP address 10.0.2.15
00:20:42.737 NAT: DHCP offered IP address 10.0.2.15
00:21:00.981 Guest Additions capability report: (0x4) seamless: no, hostWindowMapping: no, graphics: yes
00:21:00.999 Starting host clipboard service
00:21:01.000 Initializing X11 clipboard backend
00:21:01.603 Shared clipboard: starting shared clipboard thread
00:21:01.740 Guest Additions capability report: (0x5) seamless: yes, hostWindowMapping: no, graphics: yes
00:21:02.862 PIT: mode=2 count=0x4ad (1197) - 996.81 Hz (ch=0)
00:21:03.212 PIT: mode=2 count=0x2ead (11949) - 99.85 Hz (ch=0)
00:21:03.513 PIT: mode=2 count=0x4ad (1197) - 996.81 Hz (ch=0)
00:21:03.534 PIT: mode=2 count=0x2ead (11949) - 99.85 Hz (ch=0)
00:21:03.935 PIT: mode=2 count=0x4ad (1197) - 996.81 Hz (ch=0)
00:21:04.184 PIT: mode=2 count=0x2ead (11949) - 99.85 Hz (ch=0)
00:21:04.244 PIT: mode=2 count=0x4ad (1197) - 996.81 Hz (ch=0)
00:21:04.266 PIT: mode=2 count=0x2ead (11949) - 99.85 Hz (ch=0)
00:21:04.526 PIT: mode=2 count=0x4ad (1197) - 996.81 Hz (ch=0)
00:21:04.548 PIT: mode=2 count=0x2ead (11949) - 99.85 Hz (ch=0)
00:21:05.009 PIT: mode=2 count=0x4ad (1197) - 996.81 Hz (ch=0)
00:21:05.030 PIT: mode=2 count=0x2ead (11949) - 99.85 Hz (ch=0)
00:21:05.091 PIT: mode=2 count=0x4ad (1197) - 996.81 Hz (ch=0)
00:21:05.112 PIT: mode=2 count=0x2ead (11949) - 99.85 Hz (ch=0)
00:21:05.173 PIT: mode=2 count=0x4ad (1197) - 996.81 Hz (ch=0)
00:21:05.245 PIT: mode=2 count=0x2ead (11949) - 99.85 Hz (ch=0)
00:21:05.285 PIT: mode=2 count=0x4ad (1197) - 996.81 Hz (ch=0)
00:21:05.336 PIT: mode=2 count=0x2ead (11949) - 99.85 Hz (ch=0)
00:21:06.008 PIT: mode=2 count=0x4ad (1197) - 996.81 Hz (ch=0)
00:21:07.791 PIT: mode=2 count=0x2ead (11949) - 99.85 Hz (ch=0)
00:22:27.054 NAT: DHCP offered IP address 10.0.2.15
00:22:36.148 PIT: mode=2 count=0x4ad (1197) - 996.81 Hz (ch=0)
00:22:36.199 PIT: mode=2 count=0x2ead (11949) - 99.85 Hz (ch=0)
00:28:37.642 NAT: DHCP offered IP address 10.0.2.15
00:53:14.281 OHCI: USB Operational
00:53:14.282 EHCI: USB Operational
00:53:14.292 OHCI: USB Suspended
00:53:14.303 EHCI: USB Suspended
00:53:14.601 Ignoring guest attempt to enter S1 power state (powered-on suspend)!
00:53:14.601 Entering S4 power state (suspend to disk)
00:53:14.601 Changing the VM state from 'RUNNING' to 'POWERING_OFF'.
00:53:14.601 ****************** Guest state at power off ******************
00:53:14.617 Guest CPUM (VCPU 0) state: se
00:53:14.619 eax=00002401 ebx=00000000 ecx=00002400 edx=00004004 esi=00000511 edi=00000000
00:53:14.619 eip=8281d51
```

```
00:00:05.465 VirtualBox 4.0.2 r69518 linux.x86 (Jan 18 2011 19:58:28) release log
00:00:05.465 Log opened 2011-03-16T18:25:01.258436000Z
00:00:05.465 OS Product: Linux
00:00:05.465 OS Release: 2.6.35-27-generic
00:00:05.465 OS Version: #48-Ubuntu SMP Tue Feb 22 20:25:29 UTC 2011
00:00:05.465 DMI Product Name: P5QC
00:00:05.465 DMI Product Version: System Version
00:00:05.465 Host RAM: 3275MB RAM, available: 2375MB
00:00:05.465 Executable: /usr/lib/virtualbox/VirtualBox
00:00:05.465 Process ID: 7361
00:00:05.465 Package type: LINUX_32BITS_UBUNTU_10_10
00:00:05.613 SUP: Loaded VMMR0.r0 (/usr/lib/virtualbox/VMMR0.r0) at 0xf8486020 - ModuleInit at 00000000f849bd40 and ModuleTerm at 00000000f849bd10
00:00:05.613 SUP: VMMR0EntryEx located at 00000000f849bbf0, VMMR0EntryFast at 00000000f849acc0 and VMMR0EntryInt at 00000000f849ab10
00:00:05.625 File system of '/home/tom/VirtualBox VMs/win7/Snapshots' (snapshots) is unknown
00:00:05.667 File system of '/home/tom/VirtualBox VMs/win7/win7.vdi' is ext4
00:00:05.667 Console: VM runtime error: fatal=false, errorID=Ext4PartitionDetected message="The host I/O cache for at least one controller is disabled and the medium '/home/tom/VirtualBox VMs/win7/win7.vdi' for this VM is located on an ext4 partition. There is a known Linux kernel bug which can lead to the corruption of the virtual disk image under these conditions.
00:00:05.667 Either enable the host I/O cache permanently in the VM settings or put the disk image and the snapshot folder onto a different file system.
00:00:05.667 The host I/O cache will now be enabled for this medium"
00:00:05.674 VBoxSharedClipboard mode: Bidirectional
00:00:05.714 ************************* CFGM dump *************************
00:00:05.722 [/] (level 0)
00:00:05.722   CSAMEnabled     <integer> = 0x0000000000000001 (1)
00:00:05.722   CpuExecutionCap <integer> = 0x0000000000000064 (100)
00:00:05.722   EnablePAE       <integer> = 0x0000000000000000 (0)
00:00:05.722   HwVirtExtForced <integer> = 0x0000000000000000 (0)
00:00:05.722   MemBalloonSize  <integer> = 0x0000000000000000 (0)
00:00:05.722   Name            <string>  = "win7" (cb=5)
00:00:05.722   NumCPUs         <integer> = 0x0000000000000001 (1)
00:00:05.722   PATMEnabled     <integer> = 0x0000000000000001 (1)
00:00:05.722   PageFusion      <integer> = 0x0000000000000000 (0)
00:00:05.722   RamHoleSize     <integer> = 0x0000000020000000 (536870912)
00:00:05.722   RamSize         <integer> = 0x0000000035200000 (891289600)
00:00:05.722   RawR0Enabled    <integer> = 0x0000000000000001 (1)
00:00:05.722   RawR3Enabled    <integer> = 0x0000000000000001 (1)
00:00:05.722   SyntheticCpu    <integer> = 0x0000000000000000 (0)
00:00:05.722   TimerMillies    <integer> = 0x000000000000000a (10)
00:00:05.722   UUID            <bytes>   = "a3 d2 20 30 34 d6 b7 44 87 4c 01 ba fd b1 8c 39" (cb=16)
00:00:05.722 
00:00:05.722 [/CPUM/] (level 1)
00:00:05.722 
00:00:05.722 [/Devices/] (level 1)
00:00:05.722 
00:00:05.722 [/Devices/8237A/] (level 2)
00:00:05.722 
00:00:05.722 [/Devices/8237A/0/] (level 3)
00:00:05.722   Trusted <integer> = 0x0000000000000001 (1)
00:00:05.722 
00:00:05.722 [/Devices/AudioSniffer/] (level 2)
00:00:05.722 
00:00:05.722 [/Devices/AudioSniffer/0/] (level 3)
00:00:05.722 
00:00:05.722 [/Devices/AudioSniffer/0/Config/] (level 4)
00:00:05.722 
00:00:05.722 [/Devices/AudioSniffer/0/LUN#0/] (level 4)
00:00:05.722   Driver <string>  = "MainAudioSniffer" (cb=17)
00:00:05.722 
00:00:05.722 [/Devices/AudioSniffer/0/LUN#0/Config/] (level 5)
00:00:05.722   Object <integer> = 0x00000000093ee218 (155116056)
00:00:05.722 
00:00:05.722 [/Devices/VMMDev/] (level 2)
00:00:05.722 
00:00:05.722 [/Devices/VMMDev/0/] (level 3)
00:00:05.722   PCIBusNo      <integer> = 0x0000000000000000 (0)
00:00:05.722   PCIDeviceNo   <integer> = 0x0000000000000004 (4)
00:00:05.722   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:05.722   Trusted       <integer> = 0x0000000000000001 (1)
00:00:05.722 
00:00:05.722 [/Devices/VMMDev/0/Config/] (level 4)
00:00:05.722   GuestCoreDumpDir <string>  = "/home/tom/VirtualBox VMs/win7/Snapshots" (cb=40)
00:00:05.722   RamSize          <integer> = 0x0000000035200000 (891289600)
00:00:05.722 
00:00:05.722 [/Devices/VMMDev/0/LUN#0/] (level 4)
00:00:05.722   Driver <string>  = "HGCM" (cb=5)
00:00:05.722 
00:00:05.722 [/Devices/VMMDev/0/LUN#0/Config/] (level 5)
00:00:05.722   Object <integer> = 0x00000000094fd350 (156226384)
00:00:05.722 
00:00:05.722 [/Devices/VMMDev/0/LUN#999/] (level 4)
00:00:05.722   Driver <string>  = "MainStatus" (cb=11)
00:00:05.722 
00:00:05.722 [/Devices/VMMDev/0/LUN#999/Config/] (level 5)
00:00:05.722   First   <integer> = 0x0000000000000000 (0)
00:00:05.722   Last    <integer> = 0x0000000000000000 (0)
00:00:05.722   papLeds <integer> = 0x00000000093e28f0 (155068656)
00:00:05.722 
00:00:05.722 [/Devices/acpi/] (level 2)
00:00:05.722 
00:00:05.722 [/Devices/acpi/0/] (level 3)
00:00:05.722   PCIBusNo      <integer> = 0x0000000000000000 (0)
00:00:05.722   PCIDeviceNo   <integer> = 0x0000000000000007 (7)
00:00:05.722   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:05.722   Trusted       <integer> = 0x0000000000000001 (1)
00:00:05.722 
00:00:05.722 [/Devices/acpi/0/Config/] (level 4)
00:00:05.722   CpuHotPlug        <integer> = 0x0000000000000000 (0)
00:00:05.722   FdcEnabled        <integer> = 0x0000000000000000 (0)
00:00:05.722   HostBusPciAddress <integer> = 0x0000000000000000 (0)
00:00:05.722   HpetEnabled       <integer> = 0x0000000000000000 (0)
00:00:05.722   IOAPIC            <integer> = 0x0000000000000000 (0)
00:00:05.722   IocPciAddress     <integer> = 0x0000000000010000 (65536)
00:00:05.722   NumCPUs           <integer> = 0x0000000000000001 (1)
00:00:05.722   RamHoleSize       <integer> = 0x0000000020000000 (536870912)
00:00:05.722   RamSize           <integer> = 0x0000000035200000 (891289600)
00:00:05.722   ShowCpu           <integer> = 0x0000000000000000 (0)
00:00:05.722   ShowRtc           <integer> = 0x0000000000000000 (0)
00:00:05.722   SmcEnabled        <integer> = 0x0000000000000000 (0)
00:00:05.722 
00:00:05.722 [/Devices/acpi/0/LUN#0/] (level 4)
00:00:05.722   Driver <string>  = "ACPIHost" (cb=9)
00:00:05.722 
00:00:05.722 [/Devices/acpi/0/LUN#0/Config/] (level 5)
00:00:05.722 
00:00:05.722 [/Devices/ahci/] (level 2)
00:00:05.722 
00:00:05.722 [/Devices/ahci/0/] (level 3)
00:00:05.722   PCIBusNo      <integer> = 0x0000000000000000 (0)
00:00:05.722   PCIDeviceNo   <integer> = 0x000000000000000d (13)
00:00:05.722   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:05.722   Trusted       <integer> = 0x0000000000000001 (1)
00:00:05.722 
00:00:05.722 [/Devices/ahci/0/Config/] (level 4)
00:00:05.722   Bootable        <integer> = 0x0000000000000001 (1)
00:00:05.722   PortCount       <integer> = 0x0000000000000001 (1)
00:00:05.722   PrimaryMaster   <integer> = 0x0000000000000000 (0)
00:00:05.722   PrimarySlave    <integer> = 0x0000000000000001 (1)
00:00:05.722   SecondaryMaster <integer> = 0x0000000000000002 (2)
00:00:05.722   SecondarySlave  <integer> = 0x0000000000000003 (3)
00:00:05.722 
00:00:05.722 [/Devices/ahci/0/LUN#0/] (level 4)
00:00:05.722   Driver <string>  = "Block" (cb=6)
00:00:05.722 
00:00:05.722 [/Devices/ahci/0/LUN#0/AttachedDriver/] (level 5)
00:00:05.722   Driver <string>  = "VD" (cb=3)
00:00:05.722 
00:00:05.722 [/Devices/ahci/0/LUN#0/AttachedDriver/Config/] (level 6)
00:00:05.722   Format <string>  = "VDI" (cb=4)
00:00:05.722   Path   <string>  = "/home/tom/VirtualBox VMs/win7/win7.vdi" (cb=39)
00:00:05.722   Type   <string>  = "HardDisk" (cb=9)
00:00:05.722 
00:00:05.722 [/Devices/ahci/0/LUN#0/Config/] (level 5)
00:00:05.722   Mountable <integer> = 0x0000000000000000 (0)
00:00:05.722   Type      <string>  = "HardDisk" (cb=9)
00:00:05.722 
00:00:05.722 [/Devices/ahci/0/LUN#999/] (level 4)
00:00:05.722   Driver <string>  = "MainStatus" (cb=11)
00:00:05.722 
00:00:05.722 [/Devices/ahci/0/LUN#999/Config/] (level 5)
00:00:05.722   First   <integer> = 0x0000000000000000 (0)
00:00:05.722   Last    <integer> = 0x0000000000000000 (0)
00:00:05.722   papLeds <integer> = 0x00000000093e27f8 (155068408)
00:00:05.722 
00:00:05.722 [/Devices/apic/] (level 2)
00:00:05.722 
00:00:05.722 [/Devices/apic/0/] (level 3)
00:00:05.722   Trusted <integer> = 0x0000000000000001 (1)
00:00:05.722 
00:00:05.722 [/Devices/apic/0/Config/] (level 4)
00:00:05.722   IOAPIC  <integer> = 0x0000000000000000 (0)
00:00:05.722   NumCPUs <integer> = 0x0000000000000001 (1)
00:00:05.722 
00:00:05.722 [/Devices/e1000/] (level 2)
00:00:05.722 
00:00:05.722 [/Devices/e1000/0/] (level 3)
00:00:05.722   PCIBusNo      <integer> = 0x0000000000000000 (0)
00:00:05.722   PCIDeviceNo   <integer> = 0x0000000000000003 (3)
00:00:05.722   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:05.722   Trusted       <integer> = 0x0000000000000001 (1)
00:00:05.722 
00:00:05.722 [/Devices/e1000/0/Config/] (level 4)
00:00:05.722   AdapterType    <integer> = 0x0000000000000000 (0)
00:00:05.722   CableConnected <integer> = 0x0000000000000001 (1)
00:00:05.722   LineSpeed      <integer> = 0x0000000000000000 (0)
00:00:05.722   MAC            <bytes>   = "08 00 27 48 2d 5b" (cb=6)
00:00:05.722 
00:00:05.722 [/Devices/e1000/0/LUN#0/] (level 4)
00:00:05.722   Driver <string>  = "NAT" (cb=4)
00:00:05.722 
00:00:05.722 [/Devices/e1000/0/LUN#0/Config/] (level 5)
00:00:05.722   AliasMode       <integer> = 0x0000000000000000 (0)
00:00:05.722   BootFile        <string>  = "win7.pxe" (cb=9)
00:00:05.722   DNSProxy        <integer> = 0x0000000000000000 (0)
00:00:05.722   Network         <string>  = "10.0.2.0/24" (cb=12)
00:00:05.722   PassDomain      <integer> = 0x0000000000000001 (1)
00:00:05.722   TFTPPrefix      <string>  = "/home/tom/.VirtualBox/TFTP" (cb=27)
00:00:05.722   UseHostResolver <integer> = 0x0000000000000000 (0)
00:00:05.722 
00:00:05.722 [/Devices/e1000/0/LUN#999/] (level 4)
00:00:05.722   Driver <string>  = "MainStatus" (cb=11)
00:00:05.722 
00:00:05.722 [/Devices/e1000/0/LUN#999/Config/] (level 5)
00:00:05.722   papLeds <integer> = 0x00000000093e28d0 (155068624)
00:00:05.722 
00:00:05.722 [/Devices/hda/] (level 2)
00:00:05.722 
00:00:05.722 [/Devices/hda/0/] (level 3)
00:00:05.722   PCIBusNo      <integer> = 0x0000000000000000 (0)
00:00:05.722   PCIDeviceNo   <integer> = 0x0000000000000005 (5)
00:00:05.722   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:05.722   Trusted       <integer> = 0x0000000000000001 (1)
00:00:05.722 
00:00:05.722 [/Devices/hda/0/Config/] (level 4)
00:00:05.722 
00:00:05.722 [/Devices/hda/0/LUN#0/] (level 4)
00:00:05.722   Driver <string>  = "AUDIO" (cb=6)
00:00:05.722 
00:00:05.722 [/Devices/hda/0/LUN#0/Config/] (level 5)
00:00:05.722   AudioDriver <string>  = "pulse" (cb=6)
00:00:05.722   StreamName  <string>  = "win7" (cb=5)
00:00:05.722 
00:00:05.722 [/Devices/i8254/] (level 2)
00:00:05.722 
00:00:05.722 [/Devices/i8254/0/] (level 3)
00:00:05.722 
00:00:05.722 [/Devices/i8254/0/Config/] (level 4)
00:00:05.722 
00:00:05.722 [/Devices/i8259/] (level 2)
00:00:05.722 
00:00:05.722 [/Devices/i8259/0/] (level 3)
00:00:05.722   Trusted <integer> = 0x0000000000000001 (1)
00:00:05.722 
00:00:05.722 [/Devices/i8259/0/Config/] (level 4)
00:00:05.722 
00:00:05.722 [/Devices/mc146818/] (level 2)
00:00:05.722 
00:00:05.722 [/Devices/mc146818/0/] (level 3)
00:00:05.722 
00:00:05.722 [/Devices/mc146818/0/Config/] (level 4)
00:00:05.722   UseUTC <integer> = 0x0000000000000000 (0)
00:00:05.722 
00:00:05.722 [/Devices/parallel/] (level 2)
00:00:05.722 
00:00:05.722 [/Devices/pcarch/] (level 2)
00:00:05.722 
00:00:05.722 [/Devices/pcarch/0/] (level 3)
00:00:05.722   Trusted <integer> = 0x0000000000000001 (1)
00:00:05.722 
00:00:05.722 [/Devices/pcarch/0/Config/] (level 4)
00:00:05.722 
00:00:05.722 [/Devices/pcbios/] (level 2)
00:00:05.722 
00:00:05.722 [/Devices/pcbios/0/] (level 3)
00:00:05.722   Trusted <integer> = 0x0000000000000001 (1)
00:00:05.722 
00:00:05.722 [/Devices/pcbios/0/Config/] (level 4)
00:00:05.722   BootDevice0            <string>  = "FLOPPY" (cb=7)
00:00:05.722   BootDevice1            <string>  = "DVD" (cb=4)
00:00:05.722   BootDevice2            <string>  = "IDE" (cb=4)
00:00:05.722   BootDevice3            <string>  = "NONE" (cb=5)
00:00:05.722   FloppyDevice           <string>  = "i82078" (cb=7)
00:00:05.722   HardDiskDevice         <string>  = "piix3ide" (cb=9)
00:00:05.722   IOAPIC                 <integer> = 0x0000000000000000 (0)
00:00:05.722   LanBootRom             <string>  = "/usr/lib/virtualbox/ExtensionPacks/Oracle_VM_VirtualBox_Extension_Pack/PXE-Intel.rom" (cb=85)
00:00:05.722   McfgBase               <integer> = 0x0000000000000000 (0)
00:00:05.722   McfgLength             <integer> = 0x0000000000000000 (0)
00:00:05.722   NumCPUs                <integer> = 0x0000000000000001 (1)
00:00:05.722   PXEDebug               <integer> = 0x0000000000000000 (0)
00:00:05.722   RamHoleSize            <integer> = 0x0000000020000000 (536870912)
00:00:05.722   RamSize                <integer> = 0x0000000035200000 (891289600)
00:00:05.722   SataHardDiskDevice     <string>  = "ahci" (cb=5)
00:00:05.722   SataPrimaryMasterLUN   <integer> = 0x0000000000000000 (0)
00:00:05.722   SataPrimarySlaveLUN    <integer> = 0x0000000000000001 (1)
00:00:05.722   SataSecondaryMasterLUN <integer> = 0x0000000000000002 (2)
00:00:05.722   SataSecondarySlaveLUN  <integer> = 0x0000000000000003 (3)
00:00:05.722   UUID                   <bytes>   = "a3 d2 20 30 34 d6 b7 44 87 4c 01 ba fd b1 8c 39" (cb=16)
00:00:05.722 
00:00:05.722 [/Devices/pcbios/0/Config/NetBoot/] (level 5)
00:00:05.722 
00:00:05.722 [/Devices/pcbios/0/Config/NetBoot/0/] (level 6)
00:00:05.722   NIC           <integer> = 0x0000000000000000 (0)
00:00:05.722   PCIBusNo      <integer> = 0x0000000000000000 (0)
00:00:05.722   PCIDeviceNo   <integer> = 0x0000000000000003 (3)
00:00:05.722   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:05.722 
00:00:05.722 [/Devices/pci/] (level 2)
00:00:05.722 
00:00:05.722 [/Devices/pci/0/] (level 3)
00:00:05.722   Trusted <integer> = 0x0000000000000001 (1)
00:00:05.722 
00:00:05.722 [/Devices/pci/0/Config/] (level 4)
00:00:05.722   IOAPIC <integer> = 0x0000000000000000 (0)
00:00:05.722 
00:00:05.722 [/Devices/pckbd/] (level 2)
00:00:05.722 
00:00:05.722 [/Devices/pckbd/0/] (level 3)
00:00:05.722   Trusted <integer> = 0x0000000000000001 (1)
00:00:05.722 
00:00:05.722 [/Devices/pckbd/0/Config/] (level 4)
00:00:05.722 
00:00:05.722 [/Devices/pckbd/0/LUN#0/] (level 4)
00:00:05.722   Driver <string>  = "KeyboardQueue" (cb=14)
00:00:05.722 
00:00:05.722 [/Devices/pckbd/0/LUN#0/AttachedDriver/] (level 5)
00:00:05.722   Driver <string>  = "MainKeyboard" (cb=13)
00:00:05.722 
00:00:05.722 [/Devices/pckbd/0/LUN#0/AttachedDriver/Config/] (level 6)
00:00:05.722   Object <integer> = 0x0000000009380900 (154667264)
00:00:05.722 
00:00:05.722 [/Devices/pckbd/0/LUN#0/Config/] (level 5)
00:00:05.722   QueueSize <integer> = 0x0000000000000040 (64)
00:00:05.722 
00:00:05.722 [/Devices/pckbd/0/LUN#1/] (level 4)
00:00:05.722   Driver <string>  = "MouseQueue" (cb=11)
00:00:05.722 
00:00:05.722 [/Devices/pckbd/0/LUN#1/AttachedDriver/] (level 5)
00:00:05.722   Driver <string>  = "MainMouse" (cb=10)
00:00:05.722 
00:00:05.722 [/Devices/pckbd/0/LUN#1/AttachedDriver/Config/] (level 6)
00:00:05.722   Object <integer> = 0x0000000009380398 (154665880)
00:00:05.722 
00:00:05.722 [/Devices/pckbd/0/LUN#1/Config/] (level 5)
00:00:05.722   QueueSize <integer> = 0x0000000000000080 (128)
00:00:05.722 
00:00:05.722 [/Devices/pcnet/] (level 2)
00:00:05.722 
00:00:05.722 [/Devices/piix3ide/] (level 2)
00:00:05.722 
00:00:05.722 [/Devices/piix3ide/0/] (level 3)
00:00:05.722   PCIBusNo      <integer> = 0x0000000000000000 (0)
00:00:05.722   PCIDeviceNo   <integer> = 0x0000000000000001 (1)
00:00:05.722   PCIFunctionNo <integer> = 0x0000000000000001 (1)
00:00:05.722   Trusted       <integer> = 0x0000000000000001 (1)
00:00:05.722 
00:00:05.722 [/Devices/piix3ide/0/Config/] (level 4)
00:00:05.722   Type <string>  = "PIIX4" (cb=6)
00:00:05.722 
00:00:05.722 [/Devices/piix3ide/0/LUN#2/] (level 4)
00:00:05.722   Driver <string>  = "HostDVD" (cb=8)
00:00:05.722 
00:00:05.722 [/Devices/piix3ide/0/LUN#2/Config/] (level 5)
00:00:05.722   Passthrough <integer> = 0x0000000000000000 (0)
00:00:05.722   Path        <string>  = "/dev/sr0" (cb=9)
00:00:05.722 
00:00:05.722 [/Devices/piix3ide/0/LUN#999/] (level 4)
00:00:05.722   Driver <string>  = "MainStatus" (cb=11)
00:00:05.722 
00:00:05.722 [/Devices/piix3ide/0/LUN#999/Config/] (level 5)
00:00:05.722   First   <integer> = 0x0000000000000000 (0)
00:00:05.722   Last    <integer> = 0x0000000000000003 (3)
00:00:05.722   papLeds <integer> = 0x00000000093e27e8 (155068392)
00:00:05.722 
00:00:05.722 [/Devices/serial/] (level 2)
00:00:05.722 
00:00:05.722 [/Devices/usb-ehci/] (level 2)
00:00:05.722 
00:00:05.722 [/Devices/usb-ehci/0/] (level 3)
00:00:05.722   PCIBusNo      <integer> = 0x0000000000000000 (0)
00:00:05.722   PCIDeviceNo   <integer> = 0x000000000000000b (11)
00:00:05.722   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:05.722   Trusted       <integer> = 0x0000000000000001 (1)
00:00:05.722 
00:00:05.722 [/Devices/usb-ehci/0/Config/] (level 4)
00:00:05.722 
00:00:05.722 [/Devices/usb-ehci/0/LUN#0/] (level 4)
00:00:05.722   Driver <string>  = "VUSBRootHub" (cb=12)
00:00:05.722 
00:00:05.722 [/Devices/usb-ehci/0/LUN#0/Config/] (level 5)
00:00:05.722 
00:00:05.722 [/Devices/usb-ehci/0/LUN#999/] (level 4)
00:00:05.722   Driver <string>  = "MainStatus" (cb=11)
00:00:05.722 
00:00:05.722 [/Devices/usb-ehci/0/LUN#999/Config/] (level 5)
00:00:05.722   First   <integer> = 0x0000000000000000 (0)
00:00:05.722   Last    <integer> = 0x0000000000000000 (0)
00:00:05.722   papLeds <integer> = 0x00000000093e28f8 (155068664)
00:00:05.722 
00:00:05.722 [/Devices/usb-ohci/] (level 2)
00:00:05.722 
00:00:05.722 [/Devices/usb-ohci/0/] (level 3)
00:00:05.722   PCIBusNo      <integer> = 0x0000000000000000 (0)
00:00:05.722   PCIDeviceNo   <integer> = 0x0000000000000006 (6)
00:00:05.722   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:05.722   Trusted       <integer> = 0x0000000000000001 (1)
00:00:05.722 
00:00:05.722 [/Devices/usb-ohci/0/Config/] (level 4)
00:00:05.722 
00:00:05.722 [/Devices/usb-ohci/0/LUN#0/] (level 4)
00:00:05.722   Driver <string>  = "VUSBRootHub" (cb=12)
00:00:05.722 
00:00:05.722 [/Devices/usb-ohci/0/LUN#0/Config/] (level 5)
00:00:05.722 
00:00:05.722 [/Devices/usb-ohci/0/LUN#999/] (level 4)
00:00:05.722   Driver <string>  = "MainStatus" (cb=11)
00:00:05.722 
00:00:05.722 [/Devices/usb-ohci/0/LUN#999/Config/] (level 5)
00:00:05.722   First   <integer> = 0x0000000000000000 (0)
00:00:05.722   Last    <integer> = 0x0000000000000000 (0)
00:00:05.722   papLeds <integer> = 0x00000000093e28f4 (155068660)
00:00:05.722 
00:00:05.722 [/Devices/vga/] (level 2)
00:00:05.722 
00:00:05.722 [/Devices/vga/0/] (level 3)
00:00:05.722   PCIBusNo      <integer> = 0x0000000000000000 (0)
00:00:05.722   PCIDeviceNo   <integer> = 0x0000000000000002 (2)
00:00:05.722   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:05.722   Trusted       <integer> = 0x0000000000000001 (1)
00:00:05.722 
00:00:05.722 [/Devices/vga/0/Config/] (level 4)
00:00:05.722   CustomVideoModes <integer> = 0x0000000000000000 (0)
00:00:05.722   FadeIn           <integer> = 0x0000000000000001 (1)
00:00:05.722   FadeOut          <integer> = 0x0000000000000001 (1)
00:00:05.722   HeightReduction  <integer> = 0x0000000000000000 (0)
00:00:05.722   LogoFile         <string>  = "" (cb=1)
00:00:05.722   LogoTime         <integer> = 0x0000000000000000 (0)
00:00:05.722   MonitorCount     <integer> = 0x0000000000000001 (1)
00:00:05.722   ShowBootMenu     <integer> = 0x0000000000000002 (2)
00:00:05.722   VRamSize         <integer> = 0x0000000002000000 (33554432)
00:00:05.722 
00:00:05.722 [/Devices/vga/0/LUN#0/] (level 4)
00:00:05.722   Driver <string>  = "MainDisplay" (cb=12)
00:00:05.722 
00:00:05.722 [/Devices/vga/0/LUN#0/Config/] (level 5)
00:00:05.722   Object <integer> = 0x00000000093e50b0 (155078832)
00:00:05.722 
00:00:05.722 [/Devices/virtio-net/] (level 2)
00:00:05.722 
00:00:05.722 [/HWVirtExt/] (level 1)
00:00:05.722   64bitEnabled       <integer> = 0x0000000000000000 (0)
00:00:05.722   EnableLargePages   <integer> = 0x0000000000000000 (0)
00:00:05.722   EnableNestedPaging <integer> = 0x0000000000000001 (1)
00:00:05.722   EnableVPID         <integer> = 0x0000000000000001 (1)
00:00:05.722   Enabled            <integer> = 0x0000000000000001 (1)
00:00:05.722   Exclusive          <integer> = 0x0000000000000001 (1)
00:00:05.722 
00:00:05.722 [/MM/] (level 1)
00:00:05.722   CanUseLargerHeap <integer> = 0x0000000000000000 (0)
00:00:05.722 
00:00:05.722 [/PDM/] (level 1)
00:00:05.722 
00:00:05.722 [/PDM/AsyncCompletion/] (level 2)
00:00:05.722 
00:00:05.722 [/PDM/AsyncCompletion/File/] (level 3)
00:00:05.722 
00:00:05.722 [/PDM/AsyncCompletion/File/BwGroups/] (level 4)
00:00:05.722 
00:00:05.722 [/PDM/BlkCache/] (level 2)
00:00:05.722   CacheSize <integer> = 0x0000000000500000 (5242880)
00:00:05.722 
00:00:05.722 [/PDM/Devices/] (level 2)
00:00:05.722 
00:00:05.722 [/PDM/Devices/VBoxEhci/] (level 3)
00:00:05.722   Path         <string>  = "/usr/lib/virtualbox/ExtensionPacks/Oracle_VM_VirtualBox_Extension_Pack/linux.x86/VBoxEhciR3.so" (cb=95)
00:00:05.722   R0SearchPath <string>  = "/usr/lib/virtualbox/ExtensionPacks/Oracle_VM_VirtualBox_Extension_Pack/linux.x86" (cb=81)
00:00:05.722   RCSearchPath <string>  = "/usr/lib/virtualbox/ExtensionPacks/Oracle_VM_VirtualBox_Extension_Pack/linux.x86" (cb=81)
00:00:05.722 
00:00:05.722 [/PDM/Drivers/] (level 2)
00:00:05.722 
00:00:05.722 [/PDM/Drivers/VBoxC/] (level 3)
00:00:05.722   Path <string>  = "/usr/lib/virtualbox/components/VBoxC" (cb=37)
00:00:05.722 
00:00:05.722 [/TM/] (level 1)
00:00:05.722   UTCOffset <integer> = 0x0000000000000000 (0)
00:00:05.722 
00:00:05.722 [/USB/] (level 1)
00:00:05.722 
00:00:05.722 [/USB/USBProxy/] (level 2)
00:00:05.722 
00:00:05.722 [/USB/USBProxy/GlobalConfig/] (level 3)
00:00:05.722 
00:00:05.722 ********************* End of CFGM dump **********************
00:00:05.722 MM: cbHyperHeap=0x140000 (1310720)
00:00:05.724 Logical host processors: 2 present, 2 max, 2 online, online mask: 0000000000000003
00:00:05.724 ************************* CPUID dump ************************
00:00:05.724          RAW Standard CPUIDs
00:00:05.724      Function  eax      ebx      ecx      edx
00:00:05.724 Gst: 00000000  00000005 756e6547 6c65746e 49656e69
00:00:05.724 Hst:           0000000a 756e6547 6c65746e 49656e69
00:00:05.724 Gst: 00000001  000006fb 00000800 00000209 078bf1bf
00:00:05.724 Hst:           000006fb 01020800 0000e3fd bfebfbff
00:00:05.724 Gst: 00000002  05b0b101 005657f0 00000000 2cb43049
00:00:05.724 Hst:           05b0b101 005657f0 00000000 2cb43049
00:00:05.724 Gst: 00000003  00000000 00000000 00000000 00000000
00:00:05.724 Hst:           00000000 00000000 00000000 00000000
00:00:05.724 Gst: 00000004  00000000 00000000 00000000 00000000
00:00:05.724 Hst:           04000121 01c0003f 0000003f 00000001
00:00:05.724 Gst: 00000005  00000040 00000040 00000000 00000000
00:00:05.724 Hst:           00000040 00000040 00000003 00000220
00:00:05.724 Name:                            GenuineIntel
00:00:05.724 Supports:                        0-5
00:00:05.724 Family:                          6  	Extended: 0 	Effective: 6
00:00:05.724 Model:                           15  	Extended: 0 	Effective: 15
00:00:05.724 Stepping:                        11
00:00:05.724 Type:                            0 (primary)
00:00:05.724 APIC ID:                         0x00
00:00:05.724 Logical CPUs:                    0
00:00:05.724 CLFLUSH Size:                    8
00:00:05.724 Brand ID:                        0x00
00:00:05.724 Mnemonic - Description                 = guest (host)
00:00:05.724 FPU - x87 FPU on Chip                  = 1 (1)
00:00:05.724 VME - Virtual 8086 Mode Enhancements   = 1 (1)
00:00:05.724 DE - Debugging extensions              = 1 (1)
00:00:05.724 PSE - Page Size Extension              = 1 (1)
00:00:05.724 TSC - Time Stamp Counter               = 1 (1)
00:00:05.724 MSR - Model Specific Registers         = 1 (1)
00:00:05.724 PAE - Physical Address Extension       = 0 (1)
00:00:05.724 MCE - Machine Check Exception          = 1 (1)
00:00:05.724 CX8 - CMPXCHG8B instruction            = 1 (1)
00:00:05.724 APIC - APIC On-Chip                    = 0 (1)
00:00:05.724 10 - Reserved                          = 0 (0)
00:00:05.724 SEP - SYSENTER and SYSEXIT             = 0 (1)
00:00:05.724 MTRR - Memory Type Range Registers     = 1 (1)
00:00:05.724 PGE - PTE Global Bit                   = 1 (1)
00:00:05.724 MCA - Machine Check Architecture       = 1 (1)
00:00:05.724 CMOV - Conditional Move Instructions   = 1 (1)
00:00:05.724 PAT - Page Attribute Table             = 1 (1)
00:00:05.724 PSE-36 - 36-bit Page Size Extention    = 1 (1)
00:00:05.724 PSN - Processor Serial Number          = 0 (0)
00:00:05.724 CLFSH - CLFLUSH Instruction.           = 1 (1)
00:00:05.724 20 - Reserved                          = 0 (0)
00:00:05.724 DS - Debug Store                       = 0 (1)
00:00:05.724 ACPI - Thermal Mon. & Soft. Clock Ctrl.= 0 (1)
00:00:05.724 MMX - Intel MMX Technology             = 1 (1)
00:00:05.724 FXSR - FXSAVE and FXRSTOR Instructions = 1 (1)
00:00:05.724 SSE - SSE Support                      = 1 (1)
00:00:05.724 SSE2 - SSE2 Support                    = 1 (1)
00:00:05.724 SS - Self Snoop                        = 0 (1)
00:00:05.724 HTT - Hyper-Threading Technology       = 0 (1)
00:00:05.724 TM - Thermal Monitor                   = 0 (1)
00:00:05.724 30 - Reserved                          = 0 (0)
00:00:05.724 PBE - Pending Break Enable             = 0 (1)
00:00:05.724 Supports SSE3                          = 1 (1)
00:00:05.724 PCLMULQDQ                              = 0 (0)
00:00:05.724 DS Area 64-bit layout                  = 0 (1)
00:00:05.724 Supports MONITOR/MWAIT                 = 1 (1)
00:00:05.724 CPL-DS - CPL Qualified Debug Store     = 0 (1)
00:00:05.724 VMX - Virtual Machine Technology       = 0 (1)
00:00:05.724 SMX - Safer Mode Extensions            = 0 (1)
00:00:05.724 Enhanced SpeedStep Technology          = 0 (1)
00:00:05.724 Terminal Monitor 2                     = 0 (1)
00:00:05.724 Supplemental SSE3 instructions         = 1 (1)
00:00:05.724 L1 Context ID                          = 0 (0)
00:00:05.724 11 - Reserved                          = 0 (0)
00:00:05.724 FMA extensions using YMM state         = 0 (0)
00:00:05.724 CMPXCHG16B instruction                 = 0 (1)
00:00:05.724 xTPR Update Control                    = 0 (1)
00:00:05.724 Perf/Debug Capability MSR              = 0 (1)
00:00:05.724 16 - Reserved                          = 0 (0)
00:00:05.724 PCID - Process-context identifiers     = 0 (0)
00:00:05.724 DCA - Direct Cache Access              = 0 (0)
00:00:05.724 SSE4.1 instruction extensions          = 0 (0)
00:00:05.724 SSE4.2 instruction extensions          = 0 (0)
00:00:05.724 Supports the x2APIC extensions         = 0 (0)
00:00:05.724 MOVBE instruction                      = 0 (0)
00:00:05.724 POPCNT instruction                     = 0 (0)
00:00:05.724 TSC-Deadline LAPIC timer mode          = 0 (0)
00:00:05.724 AESNI instruction extensions           = 0 (0)
00:00:05.724 XSAVE/XRSTOR extended state feature    = 0 (0)
00:00:05.724 Supports OSXSAVE                       = 0 (0)
00:00:05.724 AVX instruction extensions             = 0 (0)
00:00:05.724 29/30 - Reserved                       = 0x0 (0x0)
00:00:05.724 31 - Reserved (always 0)               = 0 (0)
00:00:05.724 
00:00:05.724          RAW Extended CPUIDs
00:00:05.724      Function  eax      ebx      ecx      edx
00:00:05.724 Gst: 80000000  80000008 00000000 00000000 00000000
00:00:05.724 Hst:           80000008 00000000 00000000 00000000
00:00:05.724 Gst: 80000001  00000000 00000000 00000000 00000000
00:00:05.724 Hst:           00000000 00000000 00000001 20100000
00:00:05.724 Gst: 80000002  65746e49 2952286c 726f4320 4d542865
00:00:05.724 Hst:           65746e49 2952286c 726f4320 4d542865
00:00:05.724 Gst: 80000003  44203229 43206f75 20205550 45202020
00:00:05.724 Hst:           44203229 43206f75 20205550 45202020
00:00:05.724 Gst: 80000004  30353536 20402020 33332e32 007a4847
00:00:05.724 Hst:           30353536 20402020 33332e32 007a4847
00:00:05.724 Gst: 80000005  00000000 00000000 00000000 00000000
00:00:05.724 Hst:           00000000 00000000 00000000 00000000
00:00:05.724 Gst: 80000006  00000000 00000000 10008040 00000000
00:00:05.724 Hst:           00000000 00000000 10008040 00000000
00:00:05.724 Gst: 80000007  00000000 00000000 00000000 00000000
00:00:05.724 Hst:           00000000 00000000 00000000 00000000
00:00:05.724 Gst: 80000008  00003024 00000000 00000000 00000000
00:00:05.724 Hst:           00003024 00000000 00000000 00000000
00:00:05.724 Gst: 80000009  07280202 00000000 00000000 00000503*
00:00:05.724 Hst:           07280202 00000000 00000000 00000503
00:00:05.724 Ext Name:                        
00:00:05.724 Ext Supports:                    0x80000000-0x80000008
00:00:05.724 Family:                          0  	Extended: 0 	Effective: 0
00:00:05.724 Model:                           0  	Extended: 0 	Effective: 0
00:00:05.724 Stepping:                        0
00:00:05.724 Brand ID:                        0x000
00:00:05.724 Mnemonic - Description                 = guest (host)
00:00:05.724 FPU - x87 FPU on Chip                  = 0 (0)
00:00:05.724 VME - Virtual 8086 Mode Enhancements   = 0 (0)
00:00:05.724 DE - Debugging extensions              = 0 (0)
00:00:05.724 PSE - Page Size Extension              = 0 (0)
00:00:05.724 TSC - Time Stamp Counter               = 0 (0)
00:00:05.724 MSR - K86 Model Specific Registers     = 0 (0)
00:00:05.724 PAE - Physical Address Extension       = 0 (0)
00:00:05.724 MCE - Machine Check Exception          = 0 (0)
00:00:05.724 CX8 - CMPXCHG8B instruction            = 0 (0)
00:00:05.724 APIC - APIC On-Chip                    = 0 (0)
00:00:05.724 10 - Reserved                          = 0 (0)
00:00:05.724 SEP - SYSCALL and SYSRET               = 0 (0)
00:00:05.724 MTRR - Memory Type Range Registers     = 0 (0)
00:00:05.724 PGE - PTE Global Bit                   = 0 (0)
00:00:05.724 MCA - Machine Check Architecture       = 0 (0)
00:00:05.724 CMOV - Conditional Move Instructions   = 0 (0)
00:00:05.724 PAT - Page Attribute Table             = 0 (0)
00:00:05.724 PSE-36 - 36-bit Page Size Extention    = 0 (0)
00:00:05.724 18 - Reserved                          = 0 (0)
00:00:05.724 19 - Reserved                          = 0 (0)
00:00:05.724 NX - No-Execute Page Protection        = 0 (1)
00:00:05.724 DS - Debug Store                       = 0 (0)
00:00:05.724 AXMMX - AMD Extensions to MMX Instr.   = 0 (0)
00:00:05.724 MMX - Intel MMX Technology             = 0 (0)
00:00:05.724 FXSR - FXSAVE and FXRSTOR Instructions = 0 (0)
00:00:05.724 25 - AMD fast FXSAVE and FXRSTOR Instr.= 0 (0)
00:00:05.724 26 - 1 GB large page support           = 0 (0)
00:00:05.724 27 - RDTSCP instruction                = 0 (0)
00:00:05.724 28 - Reserved                          = 0 (0)
00:00:05.724 29 - AMD Long Mode                     = 0 (1)
00:00:05.724 30 - AMD Extensions to 3DNow           = 0 (0)
00:00:05.724 31 - AMD 3DNow                         = 0 (0)
00:00:05.724 LahfSahf - LAHF/SAHF in 64-bit mode    = 0 (1)
00:00:05.724 CmpLegacy - Core MP legacy mode (depr) = 0 (0)
00:00:05.724 SVM - AMD VM Extensions                = 0 (0)
00:00:05.724 APIC registers starting at 0x400       = 0 (0)
00:00:05.724 AltMovCR8 - LOCK MOV CR0 means MOV CR8 = 0 (0)
00:00:05.724 Advanced bit manipulation              = 0 (0)
00:00:05.724 SSE4A instruction support              = 0 (0)
00:00:05.724 Misaligned SSE mode                    = 0 (0)
00:00:05.724 PREFETCH and PREFETCHW instruction     = 0 (0)
00:00:05.724 OS visible workaround                  = 0 (0)
00:00:05.724 Instruction based sampling             = 0 (0)
00:00:05.724 SSE5 support                           = 0 (0)
00:00:05.724 SKINIT, STGI, and DEV support          = 0 (0)
00:00:05.724 Watchdog timer support.                = 0 (0)
00:00:05.724 31:14 - Reserved                       = 0x0 (0x0)
00:00:05.724 Full Name:                       Intel(R) Core(TM)2 Duo CPU     E6550  @ 2.33GHz
00:00:05.724 TLB 2/4M Instr/Uni:              res0     0 entries
00:00:05.724 TLB 2/4M Data:                   res0     0 entries
00:00:05.724 TLB 4K Instr/Uni:                res0     0 entries
00:00:05.724 TLB 4K Data:                     res0     0 entries
00:00:05.724 L1 Instr Cache Line Size:        0 bytes
00:00:05.724 L1 Instr Cache Lines Per Tag:    0
00:00:05.724 L1 Instr Cache Associativity:    res0  
00:00:05.724 L1 Instr Cache Size:             0 KB
00:00:05.724 L1 Data Cache Line Size:         0 bytes
00:00:05.724 L1 Data Cache Lines Per Tag:     0
00:00:05.724 L1 Data Cache Associativity:     res0  
00:00:05.724 L1 Data Cache Size:              0 KB
00:00:05.724 L2 TLB 2/4M Instr/Uni:           off       0 entries
00:00:05.724 L2 TLB 2/4M Data:                off       0 entries
00:00:05.724 L2 TLB 4K Instr/Uni:             off       0 entries
00:00:05.724 L2 TLB 4K Data:                  off       0 entries
00:00:05.724 L2 Cache Line Size:              0 bytes
00:00:05.724 L2 Cache Lines Per Tag:          0
00:00:05.724 L2 Cache Associativity:          off   
00:00:05.724 L2 Cache Size:                   0 KB
00:00:05.724 APM Features:                   
00:00:05.724 Physical Address Width:          36 bits
00:00:05.724 Virtual Address Width:           48 bits
00:00:05.724 Guest Physical Address Width:    0 bits
00:00:05.724 Physical Core Count:             0
00:00:05.724 
00:00:05.724          RAW Centaur CPUIDs
00:00:05.724      Function  eax      ebx      ecx      edx
00:00:05.724 Gst: c0000000  07280202 00000000 00000000 00000503
00:00:05.724 Hst:           07280202 00000000 00000000 00000503
00:00:05.724 Gst: c0000001  07280202 00000000 00000000 00000503
00:00:05.724 Hst:           07280202 00000000 00000000 00000503
00:00:05.724 Gst: c0000002  07280202 00000000 00000000 00000503
00:00:05.724 Hst:           07280202 00000000 00000000 00000503
00:00:05.724 Gst: c0000003  07280202 00000000 00000000 00000503
00:00:05.724 Hst:           07280202 00000000 00000000 00000503
00:00:05.724 Centaur Supports:                0xc0000000-0x07280202
00:00:05.724 Mnemonic - Description                 = guest (host)
00:00:05.724 AIS - Alternate Instruction Set        = 0 (1)
00:00:05.724 AIS-E - AIS enabled                    = 0 (1)
00:00:05.724 RNG - Random Number Generator          = 0 (0)
00:00:05.724 RNG-E - RNG enabled                    = 0 (0)
00:00:05.724 LH - LongHaul MSR 0000_110Ah           = 0 (0)
00:00:05.724 FEMMS - FEMMS                          = 0 (0)
00:00:05.724 ACE - Advanced Cryptography Engine     = 0 (0)
00:00:05.724 ACE-E - ACE enabled                    = 0 (0)
00:00:05.724 ACE2 - Advanced Cryptography Engine 2  = 0 (1)
00:00:05.724 ACE2-E - ACE enabled                   = 0 (0)
00:00:05.724 PHE - Hash Engine                      = 0 (1)
00:00:05.724 PHE-E - PHE enabled                    = 0 (0)
00:00:05.724 PMM - Montgomery Multiplier            = 0 (0)
00:00:05.724 PMM-E - PMM enabled                    = 0 (0)
00:00:05.724 
00:00:05.724 
00:00:05.724 ******************** End of CPUID dump **********************
00:00:05.724 pgmR3PoolInit: cMaxPages=0x400 cMaxUsers=0x800 cMaxPhysExts=0x800 fCacheEnable=true 
00:00:05.779 REM: VBoxREM32
00:00:05.786 TM: GIP - u32Mode=1 (SyncTSC) u32UpdateHz=83
00:00:05.818 TM: cTSCTicksPerSecond=0xd85253a3 (3 629 274 019) fTSCVirtualized=true  fTSCUseRealTSC=false
00:00:05.818 TM: fMaybeUseOffsettedHostTSC=true  TSCTiedToExecution=false TSCNotTiedToHalt=false
00:00:05.818 CoreCode: R3=00fa9000 R0=f8250000 RC=a04f8000 Phys=000000000b778000 cb=0x3000
00:00:05.835 AIOMgr: Default manager type is "Async"
00:00:05.835 AIOMgr: Default file backend is "NonBuffered"
00:00:05.836 BlkCache: Cache successfully initialised. Cache size is 5242880 bytes
00:00:05.836 BlkCache: Cache commit interval is 10000 ms
00:00:05.836 BlkCache: Cache commit threshold is 2621440 bytes
00:00:05.916 [SMP] BIOS with 1 CPUs
00:00:05.959 SUP: Loaded VBoxDDR0.r0 (/usr/lib/virtualbox/VBoxDDR0.r0) at 0xf841f020 - ModuleInit at 0000000000000000 and ModuleTerm at 0000000000000000
00:00:05.969 SUP: Loaded VBoxDD2R0.r0 (/usr/lib/virtualbox/VBoxDD2R0.r0) at 0xf82e7020 - ModuleInit at 0000000000000000 and ModuleTerm at 0000000000000000
00:00:05.969 Activating Local APIC
00:00:05.969 CPUMSetGuestCpuIdFeature: Enabled APIC
00:00:05.969 CPUMSetGuestCpuIdFeature: Disabled x2APIC
00:00:05.969 PIT: mode=3 count=0x10000 (65536) - 18.20 Hz (ch=0)
00:00:05.971 Shared Folders service loaded.
00:00:06.000 Chipset cannot do MSI: VERR_NOT_IMPLEMENTED
00:00:06.000 DrvBlock: Flushes will be ignored
00:00:06.000 DrvBlock: Async flushes will be passed to the disk
00:00:06.000 VDInit finished
00:00:06.000 AHCI: LUN#0: disk, PCHS=16383/16/63, total number of sectors 41943040
00:00:06.000 AHCI: LUN#0: using normal I/O
00:00:06.001 AHCI ATA: LUN#0: disk, PCHS=16383/16/63, total number of sectors 41943040
00:00:06.001 AHCI ATA: LUN#1: no unit
00:00:06.001 AHCI ATA: Ctl: finished processing RESET
00:00:06.001 AHCI ATA: LUN#2: no unit
00:00:06.001 AHCI ATA: LUN#3: no unit
00:00:06.001 AHCI ATA: Ctl: finished processing RESET
00:00:06.001 AHCI ATA: Ctl: finished processing RESET
00:00:06.001 AHCI ATA: Ctl: finished processing RESET
00:00:06.001 PIIX3 ATA: LUN#0: no unit
00:00:06.001 PIIX3 ATA: LUN#1: no unit
00:00:06.007 PIIX3 ATA: LUN#2: CD/DVD, total number of sectors 0, passthrough disabled
00:00:06.007 PIIX3 ATA: LUN#3: no unit
00:00:06.007 PIIX3 ATA: Ctl#0: finished processing RESET
00:00:06.007 PIIX3 ATA: Ctl#1: finished processing RESET
00:00:06.022 NAT: value of BindIP has been ignored
00:00:06.022 Chipset cannot do MSI: VERR_NOT_IMPLEMENTED
00:00:06.022 Audio: Trying driver 'pulse'.
00:00:06.038 Pulse: open PCM_IN rate=44100Hz channels=2 format=s16le
00:00:06.038 Pulse: Requested record buffer attributes: maxlength=26460 fragsize=17640
00:00:06.152 Pulse:  Obtained record buffer attributes: maxlength=26460 fragsize=8820
00:00:06.152 HDAcodec: can't open in fmt(freq: 44100)
00:00:06.152 Pulse: open PCM_OUT rate=44100Hz channels=2 format=s16le
00:00:06.152 Pulse: Requested playback buffer attributes: maxlength=26460 tlength=17640 prebuf=-1 minreq=-1
00:00:06.249 Pulse:  Obtained playback buffer attributes: maxlength=26460 tlength=12348 prebuf=8824 minreq=3528
00:00:06.249 HDAcodec: can't open out fmt(freq: 44100)
00:00:06.260 SUP: Loaded VBoxEhciR0.r0 (/usr/lib/virtualbox/ExtensionPacks/Oracle_VM_VirtualBox_Extension_Pack/linux.x86/VBoxEhciR0.r0) at 0xf8209020 - ModuleInit at 0000000000000000 and ModuleTerm at 0000000000000000
00:00:06.260 DevPcBios: SATA LUN#0 LCHS=1024/255/63
00:00:06.260 PGM: The CPU physical address width is 36 bits
00:00:06.260 PGMR3InitFinalize: 4 MB PSE mask 0000000fffffffff
00:00:06.270 VMM: fUsePeriodicPreemptionTimers=true 
00:00:06.270 HWACCM: Host CR4=000006D0
00:00:06.270 HWACCM: MSR_IA32_FEATURE_CONTROL      = 5
00:00:06.270 HWACCM: MSR_IA32_VMX_BASIC_INFO       = 5a08000000000b
00:00:06.270 HWACCM: VMCS id                       = b
00:00:06.270 HWACCM: VMCS size                     = 800
00:00:06.270 HWACCM: VMCS physical address limit   = None
00:00:06.270 HWACCM: VMCS memory type              = 6
00:00:06.270 HWACCM: Dual monitor treatment        = 1
00:00:06.270 HWACCM: MSR_IA32_VMX_PINBASED_CTLS    = 3f00000016
00:00:06.270 HWACCM:    VMX_VMCS_CTRL_PIN_EXEC_CONTROLS_EXT_INT_EXIT
00:00:06.270 HWACCM:    VMX_VMCS_CTRL_PIN_EXEC_CONTROLS_NMI_EXIT
00:00:06.270 HWACCM:    VMX_VMCS_CTRL_PIN_EXEC_CONTROLS_VIRTUAL_NMI
00:00:06.270 HWACCM: MSR_IA32_VMX_PROCBASED_CTLS   = f7f9fffe0401e172
00:00:06.270 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_IRQ_WINDOW_EXIT
00:00:06.270 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_TSC_OFFSET
00:00:06.270 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_HLT_EXIT
00:00:06.270 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_INVLPG_EXIT
00:00:06.270 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_MWAIT_EXIT
00:00:06.270 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_RDPMC_EXIT
00:00:06.270 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_RDTSC_EXIT
00:00:06.270 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_CR3_LOAD_EXIT
00:00:06.270 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_CR3_STORE_EXIT
00:00:06.270 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_CR8_LOAD_EXIT
00:00:06.270 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_CR8_STORE_EXIT
00:00:06.270 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_USE_TPR_SHADOW
00:00:06.270 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_NMI_WINDOW_EXIT
00:00:06.270 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_MOV_DR_EXIT
00:00:06.270 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_UNCOND_IO_EXIT
00:00:06.270 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_USE_IO_BITMAPS
00:00:06.270 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_USE_MSR_BITMAPS
00:00:06.270 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_MONITOR_EXIT
00:00:06.270 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_PAUSE_EXIT
00:00:06.270 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_USE_SECONDARY_EXEC_CTRL
00:00:06.270 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_CR3_LOAD_EXIT *must* be set
00:00:06.270 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_CR3_STORE_EXIT *must* be set
00:00:06.270 HWACCM: MSR_IA32_VMX_PROCBASED_CTLS2  = 100000000
00:00:06.270 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC2_VIRT_APIC
00:00:06.270 HWACCM: MSR_IA32_VMX_ENTRY_CTLS       = 1fff000011ff
00:00:06.270 HWACCM:    VMX_VMCS_CTRL_ENTRY_CONTROLS_LOAD_DEBUG
00:00:06.270 HWACCM:    VMX_VMCS_CTRL_ENTRY_CONTROLS_IA64_MODE
00:00:06.270 HWACCM:    VMX_VMCS_CTRL_ENTRY_CONTROLS_ENTRY_SMM
00:00:06.270 HWACCM:    VMX_VMCS_CTRL_ENTRY_CONTROLS_DEACTIVATE_DUALMON
00:00:06.270 HWACCM:    VMX_VMCS_CTRL_ENTRY_CONTROLS_LOAD_DEBUG *must* be set
00:00:06.270 HWACCM: MSR_IA32_VMX_EXIT_CTLS        = 3efff00036dff
00:00:06.270 HWACCM:    VMX_VMCS_CTRL_EXIT_CONTROLS_SAVE_DEBUG
00:00:06.270 HWACCM:    VMX_VMCS_CTRL_EXIT_CONTROLS_HOST_AMD64
00:00:06.270 HWACCM:    VMX_VMCS_CTRL_EXIT_CONTROLS_ACK_EXTERNAL_IRQ
00:00:06.270 HWACCM:    VMX_VMCS_CTRL_EXIT_CONTROLS_SAVE_DEBUG *must* be set
00:00:06.270 HWACCM: MSR_IA32_VMX_MISC             = 403c0
00:00:06.270 HWACCM:    MSR_IA32_VMX_MISC_PREEMPT_TSC_BIT 0
00:00:06.270 HWACCM:    MSR_IA32_VMX_MISC_ACTIVITY_STATES 7
00:00:06.270 HWACCM:    MSR_IA32_VMX_MISC_CR3_TARGET      4
00:00:06.270 HWACCM:    MSR_IA32_VMX_MISC_MAX_MSR         200
00:00:06.270 HWACCM:    MSR_IA32_VMX_MISC_MSEG_ID         0
00:00:06.270 HWACCM: MSR_IA32_VMX_CR0_FIXED0       = 80000021
00:00:06.270 HWACCM: MSR_IA32_VMX_CR0_FIXED1       = ffffffff
00:00:06.270 HWACCM: MSR_IA32_VMX_CR4_FIXED0       = 2000
00:00:06.270 HWACCM: MSR_IA32_VMX_CR4_FIXED1       = 67ff
00:00:06.270 HWACCM: MSR_IA32_VMX_VMCS_ENUM        = 2c
00:00:06.270 HWACCM: TPR shadow physaddr           = 000000002d140000
00:00:06.270 HWACCM: VCPU0: MSR bitmap physaddr      = 000000000b72d000
00:00:06.270 HWACCM: VCPU0: VMCS physaddr            = 000000002d038000
00:00:06.270 HWACCM: Real Mode TSS guest physaddr  = 00000000f0800000
00:00:06.270 HWACCM: Non-Paging Mode EPT CR3       = 00000000f0803000
00:00:06.270 CPUMSetGuestCpuIdFeature: Enabled sysenter/exit
00:00:06.270 HWACCM: 32-bit guests supported.
00:00:06.270 HWACCM: VMX enabled!
00:00:06.270 HWACCM: TPR Patching disabled.
00:00:06.270 HWACCM:    VT-x/AMD-V init method: GLOBAL
00:00:06.279 VM: Halt method global1 (5)
00:00:06.279 HaltedGlobal1 config: cNsSpinBlockThresholdCfg=2000
00:00:06.279 Changing the VM state from 'CREATING' to 'CREATED'.
00:00:06.279 Changing the VM state from 'CREATED' to 'POWERING_ON'.
00:00:06.279 Changing the VM state from 'POWERING_ON' to 'RUNNING'.
00:00:06.287 ERROR [COM]: aRC=VBOX_E_IPRT_ERROR (0x80bb0005) aIID={09eed313-cd56-4d06-bd56-fac0f716b5dd} aComponent={Display} aText={Could not take a screenshot (VERR_NOT_SUPPORTED)}, preserve=false
00:00:06.287 Guest Log: BIOS: VirtualBox 4.0.2
00:00:06.287 PIT: mode=2 count=0x10000 (65536) - 18.20 Hz (ch=0)
00:00:06.299 ERROR [COM]: aRC=VBOX_E_IPRT_ERROR (0x80bb0005) aIID={09eed313-cd56-4d06-bd56-fac0f716b5dd} aComponent={Display} aText={Could not take a screenshot (VERR_NOT_SUPPORTED)}, preserve=false
00:00:06.345 PIIX3 ATA: Ctl#1: RESET, DevSel=0 AIOIf=0 CmdIf0=0x00 (-1 usec ago) CmdIf1=0x00 (-1 usec ago)
00:00:06.345 PIIX3 ATA: Ctl#1: finished processing RESET
00:00:06.345 AHCI ATA: Ctl: RESET, DevSel=0 AIOIf=0 CmdIf0=0x00 (-1 usec ago) CmdIf1=0x00 (-1 usec ago)
00:00:06.345 AHCI ATA: Ctl: finished processing RESET
00:00:06.346 Guest Log: BIOS: ata2-0: PCHS=16383/16/63 LCHS=1024/255/63
00:00:06.346 PIT: mode=2 count=0x48d3 (18643) - 64.00 Hz (ch=0)
00:00:06.348 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=afa00000 w=640 h=480 bpp=32 cbLine=0xA00, flags=0x1
00:00:07.823 2D video acceleration is disabled.
00:00:08.823 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=00000000 w=720 h=400 bpp=0 cbLine=0x0, flags=0x1
00:00:08.823 PIT: mode=2 count=0x10000 (65536) - 18.20 Hz (ch=0)
00:00:08.823 Guest Log: BIOS: Boot from Floppy 0 failed
00:00:08.824 Guest Log: BIOS: CDROM boot failure code : 0003
00:00:08.824 Guest Log: BIOS: Boot from CD-ROM failed
00:00:08.824 Guest Log: BIOS: Booting from Hard Disk...
00:00:08.883 AHCI ATA: Ctl: RESET, DevSel=0 AIOIf=0 CmdIf0=0xc4 (-1 usec ago) CmdIf1=0x00 (-1 usec ago)
00:00:08.883 AHCI ATA: Ctl: finished processing RESET
00:00:09.508 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=afa00000 w=1024 h=768 bpp=24 cbLine=0xC00, flags=0x1
00:00:17.273 PIT: mode=2 count=0x2ead (11949) - 99.85 Hz (ch=0)
00:00:20.146 Guest Additions information report: Version 4.0.2 r69518 '4.0.2'
00:00:20.146 Guest Additions information report: Interface = 0x00010004 osType = 0x00037000
00:00:20.146 Guest Additions capability report: (0x0) seamless: no, hostWindowMapping: no, graphics: no
00:00:20.147 Guest reported fixed hypervisor window at 0x8cc00000 (size = 0xc00000, rc = VINF_SUCCESS)
00:00:24.259 Guest Log: VBoxVideo: using HGSMI
00:00:24.487 OHCI: Software reset
00:00:24.487 OHCI: USB Reset
00:00:24.541 OHCI: USB Operational
00:00:24.579 EHCI: Hardware reset
00:00:24.579 EHCI: USB Operational
00:00:25.738 NAT: IPv6 not supported
00:00:27.158 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=afa00000 w=1600 h=1076 bpp=32 cbLine=0x1900, flags=0x1
00:00:27.166 Guest Log: VBoxDisp[0]: VBVA enabled
00:00:27.166 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=afa00000 w=1600 h=1076 bpp=32 cbLine=0x1900, flags=0x1
00:00:27.166 Display::handleDisplayResize(): Warning: resize postponed.
00:00:27.178 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=afa00000 w=1600 h=1076 bpp=32 cbLine=0x1900, flags=0x1
00:00:30.851 EHCI: USB Suspended
00:00:30.851 OHCI: USB Suspended
00:00:38.744 NAT: DHCP offered IP address 10.0.2.15
00:00:40.671 Guest Additions capability report: (0x4) seamless: no, hostWindowMapping: no, graphics: yes
00:00:40.684 Starting host clipboard service
00:00:40.725 Initializing X11 clipboard backend
00:00:40.840 Shared clipboard: starting shared clipboard thread
00:00:40.888 Guest Additions capability report: (0x5) seamless: yes, hostWindowMapping: no, graphics: yes
00:00:41.826 PIT: mode=2 count=0x4ad (1197) - 996.81 Hz (ch=0)
00:00:42.500 PIT: mode=2 count=0x2ead (11949) - 99.85 Hz (ch=0)
00:00:43.341 PIT: mode=2 count=0x4ad (1197) - 996.81 Hz (ch=0)
00:00:43.362 PIT: mode=2 count=0x2ead (11949) - 99.85 Hz (ch=0)
00:00:43.542 PIT: mode=2 count=0x4ad (1197) - 996.81 Hz (ch=0)
00:00:43.624 PIT: mode=2 count=0x2ead (11949) - 99.85 Hz (ch=0)
00:00:43.706 NAT: DHCP offered IP address 10.0.2.15
00:00:43.823 PIT: mode=2 count=0x4ad (1197) - 996.81 Hz (ch=0)
00:00:43.845 PIT: mode=2 count=0x2ead (11949) - 99.85 Hz (ch=0)
00:00:44.367 PIT: mode=2 count=0x4ad (1197) - 996.81 Hz (ch=0)
00:00:44.388 PIT: mode=2 count=0x2ead (11949) - 99.85 Hz (ch=0)
00:00:44.889 PIT: mode=2 count=0x4ad (1197) - 996.81 Hz (ch=0)
00:00:45.141 PIT: mode=2 count=0x2ead (11949) - 99.85 Hz (ch=0)
00:00:45.581 PIT: mode=2 count=0x4ad (1197) - 996.81 Hz (ch=0)
00:00:45.645 PIT: mode=2 count=0x2ead (11949) - 99.85 Hz (ch=0)
00:00:45.826 PIT: mode=2 count=0x4ad (1197) - 996.81 Hz (ch=0)
00:00:46.449 PIT: mode=2 count=0x2ead (11949) - 99.85 Hz (ch=0)
00:00:46.531 PIT: mode=2 count=0x4ad (1197) - 996.81 Hz (ch=0)
00:00:46.818 PIT: mode=2 count=0x2ead (11949) - 99.85 Hz (ch=0)
00:00:50.515 NAT: DHCP offered IP address 10.0.2.15
00:00:55.607 NAT: DHCP offered IP address 10.0.2.15
00:01:19.173 VMMDev::SetVideoModeHint: got a video mode hint (640x480x0) at 0
00:01:19.186 Guest Log: VBoxDisp[0]: VBVA enabled
00:01:19.186 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=afa00000 w=640 h=480 bpp=32 cbLine=0xA00, flags=0x1
00:01:19.196 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=afa00000 w=640 h=480 bpp=32 cbLine=0xA00, flags=0x1
00:01:25.271 VMMDev::SetVideoModeHint: got a video mode hint (723x480x0) at 0
00:01:25.283 Guest Log: VBoxDisp[0]: VBVA enabled
00:01:25.283 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=afa00000 w=723 h=480 bpp=32 cbLine=0xB4C, flags=0x1
00:01:25.293 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=afa00000 w=723 h=480 bpp=32 cbLine=0xB4C, flags=0x1
00:01:35.033 VMMDev::SetVideoModeHint: got a video mode hint (723x522x0) at 0
00:01:35.046 Guest Log: VBoxDisp[0]: VBVA enabled
00:01:35.046 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=afa00000 w=723 h=522 bpp=32 cbLine=0xB4C, flags=0x1
00:01:35.058 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=afa00000 w=723 h=522 bpp=32 cbLine=0xB4C, flags=0x1
00:01:45.533 PIT: mode=2 count=0x4ad (1197) - 996.81 Hz (ch=0)
00:01:45.602 PIT: mode=2 count=0x2ead (11949) - 99.85 Hz (ch=0)
00:01:45.913 PIT: mode=2 count=0x4ad (1197) - 996.81 Hz (ch=0)
00:01:45.997 PIT: mode=2 count=0x2ead (11949) - 99.85 Hz (ch=0)
00:01:49.433 PIT: mode=2 count=0x4ad (1197) - 996.81 Hz (ch=0)
00:01:49.495 PIT: mode=2 count=0x2ead (11949) - 99.85 Hz (ch=0)
00:01:55.344 PIT: mode=2 count=0x4ad (1197) - 996.81 Hz (ch=0)
00:01:55.393 PIT: mode=2 count=0x2ead (11949) - 99.85 Hz (ch=0)
00:02:01.313 PIT: mode=2 count=0x4ad (1197) - 996.81 Hz (ch=0)
00:02:29.981 NAT: DHCP offered IP address 10.0.2.15
00:19:22.383 Stopping the host clipboard service
00:19:22.403 ClipStopX11: stopping the shared clipboard X11 backend
00:19:22.403 Shared clipboard: shared clipboard thread terminated successfully
00:19:45.316 OHCI: USB Operational
00:19:45.316 EHCI: USB Operational
00:19:45.345 OHCI: USB Suspended
00:19:45.346 EHCI: USB Suspended
00:19:45.451 Changing the VM state from 'RUNNING' to 'RESETTING'.
00:19:45.477 CPUMSetGuestCpuIdFeature: Enabled APIC
00:19:45.477 CPUMSetGuestCpuIdFeature: Disabled x2APIC
00:19:45.477 PIT: mode=3 count=0x10000 (65536) - 18.20 Hz (ch=0)
00:19:45.483 PIIX3 ATA: Ctl#0: finished processing RESET
00:19:45.483 PIIX3 ATA: Ctl#1: finished processing RESET
00:19:45.597 AHCI ATA: Ctl: finished processing RESET
00:19:45.597 AHCI ATA: Ctl: finished processing RESET
00:19:45.597 Changing the VM state from 'RESETTING' to 'RUNNING'.
00:19:45.610 Guest Log: BIOS: VirtualBox 4.0.2
00:19:45.610 PIT: mode=2 count=0x10000 (65536) - 18.20 Hz (ch=0)
00:19:45.691 PIIX3 ATA: Ctl#1: RESET, DevSel=0 AIOIf=0 CmdIf0=0xa0 (-1 usec ago) CmdIf1=0x00 (-1 usec ago)
00:19:45.693 PIIX3 ATA: Ctl#1: finished processing RESET
00:19:45.693 AHCI ATA: Ctl: RESET, DevSel=0 AIOIf=0 CmdIf0=0x30 (-1 usec ago) CmdIf1=0x00 (-1 usec ago)
00:19:45.693 AHCI ATA: Ctl: finished processing RESET
00:19:45.693 Guest Log: BIOS: ata2-0: PCHS=16383/16/63 LCHS=1024/255/63
00:19:45.693 PIT: mode=2 count=0x48d3 (18643) - 64.00 Hz (ch=0)
00:19:45.711 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=afa00000 w=640 h=480 bpp=32 cbLine=0xA00, flags=0x1
00:19:48.165 PIT: mode=2 count=0x10000 (65536) - 18.20 Hz (ch=0)
00:19:48.166 Guest Log: BIOS: Boot from Floppy 0 failed
00:19:48.166 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=00000000 w=720 h=400 bpp=0 cbLine=0x0, flags=0x1
00:19:48.167 Guest Log: BIOS: CDROM boot failure code : 0003
00:19:48.168 Guest Log: BIOS: Boot from CD-ROM failed
00:19:48.168 Guest Log: BIOS: Booting from Hard Disk...
00:19:48.206 AHCI ATA: Ctl: RESET, DevSel=0 AIOIf=0 CmdIf0=0xc4 (-1 usec ago) CmdIf1=0x00 (-1 usec ago)
00:19:48.206 AHCI ATA: Ctl: finished processing RESET
00:19:48.860 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=afa00000 w=1024 h=768 bpp=24 cbLine=0xC00, flags=0x1
00:19:53.278 PIT: mode=2 count=0x2ead (11949) - 99.85 Hz (ch=0)
00:19:56.048 Guest Additions information report: Version 4.0.2 r69518 '4.0.2'
00:19:56.049 Guest Additions information report: Interface = 0x00010004 osType = 0x00037000
00:19:56.049 Guest Additions capability report: (0x0) seamless: no, hostWindowMapping: no, graphics: no
00:19:56.049 Guest reported fixed hypervisor window at 0x8cc00000 (size = 0xc00000, rc = VINF_SUCCESS)
00:20:03.853 Guest Log: VBoxVideo: using HGSMI
00:20:04.052 OHCI: Software reset
00:20:04.052 OHCI: USB Reset
00:20:04.107 OHCI: USB Operational
00:20:04.146 EHCI: Hardware reset
00:20:04.146 EHCI: USB Operational
00:20:09.817 EHCI: USB Suspended
00:20:09.817 OHCI: USB Suspended
00:20:15.970 Guest Log: VBoxDisp[0]: VBVA enabled
00:20:15.970 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=afa00000 w=723 h=522 bpp=32 cbLine=0xB4C, flags=0x1
00:20:15.983 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=afa00000 w=723 h=522 bpp=32 cbLine=0xB4C, flags=0x1
00:20:25.475 NAT: DHCP offered IP address 10.0.2.15
00:20:30.047 NAT: DHCP offered IP address 10.0.2.15
00:20:37.055 NAT: DHCP offered IP address 10.0.2.15
00:20:42.737 NAT: DHCP offered IP address 10.0.2.15
00:21:00.981 Guest Additions capability report: (0x4) seamless: no, hostWindowMapping: no, graphics: yes
00:21:00.999 Starting host clipboard service
00:21:01.000 Initializing X11 clipboard backend
00:21:01.603 Shared clipboard: starting shared clipboard thread
00:21:01.740 Guest Additions capability report: (0x5) seamless: yes, hostWindowMapping: no, graphics: yes
00:21:02.862 PIT: mode=2 count=0x4ad (1197) - 996.81 Hz (ch=0)
00:21:03.212 PIT: mode=2 count=0x2ead (11949) - 99.85 Hz (ch=0)
00:21:03.513 PIT: mode=2 count=0x4ad (1197) - 996.81 Hz (ch=0)
00:21:03.534 PIT: mode=2 count=0x2ead (11949) - 99.85 Hz (ch=0)
00:21:03.935 PIT: mode=2 count=0x4ad (1197) - 996.81 Hz (ch=0)
00:21:04.184 PIT: mode=2 count=0x2ead (11949) - 99.85 Hz (ch=0)
00:21:04.244 PIT: mode=2 count=0x4ad (1197) - 996.81 Hz (ch=0)
00:21:04.266 PIT: mode=2 count=0x2ead (11949) - 99.85 Hz (ch=0)
00:21:04.526 PIT: mode=2 count=0x4ad (1197) - 996.81 Hz (ch=0)
00:21:04.548 PIT: mode=2 count=0x2ead (11949) - 99.85 Hz (ch=0)
00:21:05.009 PIT: mode=2 count=0x4ad (1197) - 996.81 Hz (ch=0)
00:21:05.030 PIT: mode=2 count=0x2ead (11949) - 99.85 Hz (ch=0)
00:21:05.091 PIT: mode=2 count=0x4ad (1197) - 996.81 Hz (ch=0)
00:21:05.112 PIT: mode=2 count=0x2ead (11949) - 99.85 Hz (ch=0)
00:21:05.173 PIT: mode=2 count=0x4ad (1197) - 996.81 Hz (ch=0)
00:21:05.245 PIT: mode=2 count=0x2ead (11949) - 99.85 Hz (ch=0)
00:21:05.285 PIT: mode=2 count=0x4ad (1197) - 996.81 Hz (ch=0)
00:21:05.336 PIT: mode=2 count=0x2ead (11949) - 99.85 Hz (ch=0)
00:21:06.008 PIT: mode=2 count=0x4ad (1197) - 996.81 Hz (ch=0)
00:21:07.791 PIT: mode=2 count=0x2ead (11949) - 99.85 Hz (ch=0)
00:22:27.054 NAT: DHCP offered IP address 10.0.2.15
00:22:36.148 PIT: mode=2 count=0x4ad (1197) - 996.81 Hz (ch=0)
00:22:36.199 PIT: mode=2 count=0x2ead (11949) - 99.85 Hz (ch=0)
00:28:37.642 NAT: DHCP offered IP address 10.0.2.15
00:53:14.281 OHCI: USB Operational
00:53:14.282 EHCI: USB Operational
00:53:14.292 OHCI: USB Suspended
00:53:14.303 EHCI: USB Suspended
00:53:14.601 Ignoring guest attempt to enter S1 power state (powered-on suspend)!
00:53:14.601 Entering S4 power state (suspend to disk)
00:53:14.601 Changing the VM state from 'RUNNING' to 'POWERING_OFF'.
00:53:14.601 ****************** Guest state at power off ******************
00:53:14.617 Guest CPUM (VCPU 0) state: se
00:53:14.619 eax=00002401 ebx=00000000 ecx=00002400 edx=00004004 esi=00000511 edi=00000000
00:53:14.619 eip=8281d512 esp=8a705b90 ebp=8a705bbc iopl=0         nv up di pl zr na pe nc
00:53:14.619 cs={0008 base=0000000000000000 limit=ffffffff flags=0000c09b} dr0=00000000 dr1=00000000
00:53:14.619 ds={0023 base=0000000000000000 limit=ffffffff flags=0000c0f3} dr2=00000000 dr3=00000000
00:53:14.619 es={0023 base=0000000000000000 limit=ffffffff flags=0000c0f3} dr4=00000000 dr5=00000000
00:53:14.619 fs={0030 base=000000008294fc00 limit=00003748 flags=00004093} dr6=ffff4ff0 dr7=00000400
00:53:14.619 gs={0000 base=0000000000000000 limit=ffffffff flags=0001c000} cr0=e0010031 cr2=0064ecc4
00:53:14.619 ss={0010 base=0000000000000000 limit=ffffffff flags=0000c093} cr3=00185000 cr4=00000699
00:53:14.619 gdtr=0000000080b95000:03ff  idtr=0000000080b95400:07ff  eflags=00000002
00:53:14.619 ldtr={0000 base=00000000 limit=00000000 flags=00000082}
00:53:14.619 tr  ={0028 base=801c6000 limit=000020ab flags=0000008b}
00:53:14.619 SysEnter={cs=0008 eip=82863630 esp=80d8b000}
00:53:14.619 FCW=027f FSW=0000 FTW=0000 FOP=0000 MXCSR=00001f80 MXCSR_MASK=0000ffff
00:53:14.619 FPUIP=00000000 CS=0000 Rsvrd1=0000  FPUDP=00000000 DS=0000 Rsvrd2=0000
00:53:14.619 ST(0)=FPR0={0000'00000000'00000000} t0 +0.0000000000000000000000 ^ 0
00:53:14.619 ST(1)=FPR1={0000'00000000'00000000} t0 +0.0000000000000000000000 ^ 0
00:53:14.619 ST(2)=FPR2={0000'00000000'00000000} t0 +0.0000000000000000000000 ^ 0
00:53:14.619 ST(3)=FPR3={0000'00000000'00000000} t0 +0.0000000000000000000000 ^ 0
00:53:14.619 ST(4)=FPR4={0000'00000000'00000000} t0 +0.0000000000000000000000 ^ 0
00:53:14.619 ST(5)=FPR5={0000'00000000'00000000} t0 +0.0000000000000000000000 ^ 0
00:53:14.619 ST(6)=FPR6={0000'00000000'00000000} t0 +0.0000000000000000000000 ^ 0
00:53:14.619 ST(7)=FPR7={0000'00000000'00000000} t0 +0.0000000000000000000000 ^ 0
00:53:14.619 XMM0 =00000000'00000000'00000000'00000000  XMM1 =00000000'00000000'00000000'00000000
00:53:14.619 XMM2 =00000000'00000000'00000000'00000000  XMM3 =00000000'00000000'00000000'00000000
00:53:14.619 XMM4 =00000000'00000000'00000000'00000000  XMM5 =00000000'00000000'00000000'00000000
00:53:14.619 XMM6 =00000000'00000000'00000000'00000000  XMM7 =00000000'00000000'00000000'00000000
00:53:14.619 XMM8 =00000000'00000000'00000000'00000000  XMM9 =00000000'00000000'00000000'00000000
00:53:14.619 XMM10=00000000'00000000'00000000'00000000  XMM11=00000000'00000000'00000000'00000000
00:53:14.619 XMM12=00000000'00000000'00000000'00000000  XMM13=00000000'00000000'00000000'00000000
00:53:14.619 XMM14=00000000'00000000'00000000'00000000  XMM15=00000000'00000000'00000000'00000000
00:53:14.619 EFER         =0000000000000000
00:53:14.619 PAT          =0007010600070106
00:53:14.619 STAR         =0000000000000000
00:53:14.619 CSTAR        =0000000000000000
00:53:14.619 LSTAR        =0000000000000000
00:53:14.619 SFMASK       =0000000000000000
00:53:14.619 KERNELGSBASE =0000000000000000
00:53:14.619 ***
00:53:14.619 Guest paging mode:  32-bit, changed 35274 times, A20 enabled
00:53:14.619 Shadow paging mode: 32-bit
00:53:14.619 Host paging mode:   32-bit+G
00:53:14.619 ***
00:53:14.619 Active Timers (pVM=b2c5b000)
00:53:14.619 pTimerR3 offNext  offPrev  offSched Clock               Time             Expire HzHint State                     Description
00:53:14.619 047b6a60 fffefcb0 00000000 00000000 Real           718787470          718787455      0 2-ACTIVE                  EMT Yielder
00:53:14.619 047a6710 000102f0 00010350 00000000 Real           718787470          718787469      0 2-ACTIVE                  VGA Refresh Timer
00:53:14.619 047b6a00 00000000 fffefd10 00000000 Real           718787470          718787679      0 2-ACTIVE                  CPU Load Timer
00:53:14.619 047b2620 00000000 00000000 00000000 Virt       3188338710303      3188322944494      0 2-ACTIVE                  Audio timer
00:53:14.619 0479e770 00000430 00000000 00000000 VrSy       3188322299330      3188322299330     99 2-ACTIVE                  i8254 Programmable Interval Timer
00:53:14.619 0479eba0 00016e00 fffffbd0 00000000 VrSy       3188322299330      3188990000000      0 2-ACTIVE                  MC146818 RTC/CMOS - Second
00:53:14.619 047b59a0 00000000 fffe9200 00000000 VrSy       3188322299330      3578902831100      0 2-ACTIVE                  ACPI Timer
00:53:14.619 ***
00:53:14.619 Shadow GDT (GCAddr=ff4fc000):
00:53:14.619 ffd8 - 80d80087 ff008900 - base=ff0080d8 limit=00000087 dpl=0 TSS32Avail Present 16-bit  HyperTSSTrap08
00:53:14.619 ffe0 - 80500087 ff008900 - base=ff008050 limit=00000087 dpl=0 TSS32Avail Present 16-bit  HyperTSS
00:53:14.619 ffe8 - 0000ffff 00af9b00 - base=00000000 limit=ffffffff dpl=0 CodeER Accessed Present Page 16-bit  HyperCS64
00:53:14.619 fff0 - 0000ffff 00cf9300 - base=00000000 limit=ffffffff dpl=0 DataRW Accessed Present Page 32-bit  HyperDS
00:53:14.619 fff8 - 0000ffff 00cf9b00 - base=00000000 limit=ffffffff dpl=0 CodeER Accessed Present Page 32-bit  HyperCS
00:53:14.619 ***
00:53:14.619 ************** End of Guest state at power off ***************
00:53:14.619 Changing the VM state from 'POWERING_OFF' to 'OFF'.
00:53:14.746 Console::powerDown(): A request to power off the VM has been issued (mMachineState=Stopping, InUninit=0)
00:53:14.747 Stopping the host clipboard service
00:53:14.747 ClipStopX11: stopping the shared clipboard X11 backend
00:53:14.747 Shared clipboard: shared clipboard thread terminated successfully
00:53:14.910 Changing the VM state from 'OFF' to 'DESTROYING'.
00:53:14.910 ************************* Statistics *************************
00:53:14.910 /Devices/E1k0/ReceiveBytes        5312633 bytes
00:53:14.910 /Devices/E1k0/TransmitBytes        797964 bytes
00:53:14.910 /Devices/IDE0/ATA0/Unit0/AtapiDMA        0 times
00:53:14.910 /Devices/IDE0/ATA0/Unit0/AtapiPIO        0 times
00:53:14.910 /Devices/IDE0/ATA0/Unit0/DMA            0 times
00:53:14.910 /Devices/IDE0/ATA0/Unit0/PIO            0 times
00:53:14.910 /Devices/IDE0/ATA0/Unit0/ReadBytes        0 bytes
00:53:14.910 /Devices/IDE0/ATA0/Unit0/WrittenBytes        0 bytes
00:53:14.910 /Devices/IDE0/ATA0/Unit1/AtapiDMA        0 times
00:53:14.910 /Devices/IDE0/ATA0/Unit1/AtapiPIO        0 times
00:53:14.910 /Devices/IDE0/ATA0/Unit1/DMA            0 times
00:53:14.910 /Devices/IDE0/ATA0/Unit1/PIO            0 times
00:53:14.910 /Devices/IDE0/ATA0/Unit1/ReadBytes        0 bytes
00:53:14.910 /Devices/IDE0/ATA0/Unit1/WrittenBytes        0 bytes
00:53:14.910 /Devices/IDE0/ATA1/Unit0/AtapiDMA        0 times
00:53:14.910 /Devices/IDE0/ATA1/Unit0/AtapiPIO     3352 times
00:53:14.910 /Devices/IDE0/ATA1/Unit0/DMA            0 times
00:53:14.910 /Devices/IDE0/ATA1/Unit0/PIO            0 times
00:53:14.910 /Devices/IDE0/ATA1/Unit0/ReadBytes        0 bytes
00:53:14.910 /Devices/IDE0/ATA1/Unit0/WrittenBytes        0 bytes
00:53:14.910 /Devices/IDE0/ATA1/Unit1/AtapiDMA        0 times
00:53:14.910 /Devices/IDE0/ATA1/Unit1/AtapiPIO        0 times
00:53:14.910 /Devices/IDE0/ATA1/Unit1/DMA            0 times
00:53:14.910 /Devices/IDE0/ATA1/Unit1/PIO            0 times
00:53:14.910 /Devices/IDE0/ATA1/Unit1/ReadBytes        0 bytes
00:53:14.910 /Devices/IDE0/ATA1/Unit1/WrittenBytes        0 bytes
00:53:14.910 /Devices/SATA0/Port0/DMA           255637 times
00:53:14.910 /Devices/SATA0/Port0/IORequestsPerSecond      187 times
00:53:14.910 /Devices/SATA0/Port0/ReadBytes   4209046528 bytes
00:53:14.910 /Devices/SATA0/Port0/WrittenBytes 3046350336 bytes
00:53:14.910 /Devices/VMMDev/BalloonChunks           0 count
00:53:14.910 /FT/Checkpoint/Network                  0 times
00:53:14.910 /FT/Checkpoint/Storage                  0 times
00:53:14.910 /FT/Received/Mem                        0 bytes
00:53:14.910 /FT/Received/State                      0 bytes
00:53:14.910 /FT/Sent/Mem                            0 bytes
00:53:14.910 /FT/Sent/State                          0 bytes
00:53:14.910 /FT/Sync/DeltaMem                       0 times
00:53:14.910 /FT/Sync/DeltaVM                        0 times
00:53:14.910 /FT/Sync/Full                           0 times
00:53:14.910 /GVMM/EMTs                              1 calls
00:53:14.910 /GVMM/HostCPUs                          4 calls
00:53:14.910 /GVMM/HostCpus/0                        0 
00:53:14.910 /GVMM/HostCpus/0/CurTimerHz             0 Hz
00:53:14.910 /GVMM/HostCpus/0/DesiredHz              0 Hz
00:53:14.910 /GVMM/HostCpus/0/PPTChanges          7756 times
00:53:14.910 /GVMM/HostCpus/0/PPTStarts           1670 times
00:53:14.910 /GVMM/HostCpus/0/idxCpuSet              0 
00:53:14.910 /GVMM/HostCpus/1                        1 
00:53:14.910 /GVMM/HostCpus/1/CurTimerHz             0 Hz
00:53:14.910 /GVMM/HostCpus/1/DesiredHz              0 Hz
00:53:14.910 /GVMM/HostCpus/1/PPTChanges          7819 times
00:53:14.910 /GVMM/HostCpus/1/PPTStarts           1574 times
00:53:14.910 /GVMM/HostCpus/1/idxCpuSet              1 
00:53:14.910 /GVMM/HostCpus/2                        2 
00:53:14.910 /GVMM/HostCpus/2/CurTimerHz             0 Hz
00:53:14.910 /GVMM/HostCpus/2/DesiredHz              0 Hz
00:53:14.910 /GVMM/HostCpus/2/PPTChanges             0 times
00:53:14.910 /GVMM/HostCpus/2/PPTStarts              0 times
00:53:14.910 /GVMM/HostCpus/2/idxCpuSet              2 
00:53:14.910 /GVMM/HostCpus/3                        3 
00:53:14.910 /GVMM/HostCpus/3/CurTimerHz             0 Hz
00:53:14.910 /GVMM/HostCpus/3/DesiredHz              0 Hz
00:53:14.910 /GVMM/HostCpus/3/PPTChanges             0 times
00:53:14.910 /GVMM/HostCpus/3/PPTStarts              0 times
00:53:14.910 /GVMM/HostCpus/3/idxCpuSet              3 
00:53:14.910 /GVMM/Sum/HaltBlocking            1006371 calls
00:53:14.910 /GVMM/Sum/HaltCalls               1015766 calls
00:53:14.910 /GVMM/Sum/HaltNotBlocking            9395 calls
00:53:14.910 /GVMM/Sum/HaltTimeouts             736983 calls
00:53:14.910 /GVMM/Sum/HaltWakeUps                   0 calls
00:53:14.910 /GVMM/Sum/PokeCalls                120848 calls
00:53:14.910 /GVMM/Sum/PokeNotBusy               25312 calls
00:53:14.910 /GVMM/Sum/PollCalls                   119 calls
00:53:14.910 /GVMM/Sum/PollHalts                     0 calls
00:53:14.910 /GVMM/Sum/PollWakeUps                   0 calls
00:53:14.910 /GVMM/Sum/WakeUpCalls              270540 calls
00:53:14.910 /GVMM/Sum/WakeUpNotHalted          188884 calls
00:53:14.910 /GVMM/Sum/WakeUpWakeUps                 0 calls
00:53:14.910 /GVMM/VM/HaltBlocking             1006371 calls
00:53:14.910 /GVMM/VM/HaltCalls                1015766 calls
00:53:14.910 /GVMM/VM/HaltNotBlocking             9395 calls
00:53:14.910 /GVMM/VM/HaltTimeouts              736983 calls
00:53:14.910 /GVMM/VM/HaltWakeUps                    0 calls
00:53:14.910 /GVMM/VM/PokeCalls                 120848 calls
00:53:14.910 /GVMM/VM/PokeNotBusy                25312 calls
00:53:14.910 /GVMM/VM/PollCalls                    119 calls
00:53:14.910 /GVMM/VM/PollHalts                      0 calls
00:53:14.910 /GVMM/VM/PollWakeUps                    0 calls
00:53:14.910 /GVMM/VM/WakeUpCalls               270540 calls
00:53:14.910 /GVMM/VM/WakeUpNotHalted           188884 calls
00:53:14.910 /GVMM/VM/WakeUpWakeUps                  0 calls
00:53:14.910 /GVMM/VMs                               1 calls
00:53:14.910 /MM/HyperHeap/cbFree               985888 bytes
00:53:14.910 /MM/HyperHeap/cbHeap              1310528 bytes
00:53:14.910 /PDM/BlkCache/cbCached                  0 bytes
00:53:14.910 /PDM/BlkCache/cbCachedFru               0 bytes
00:53:14.910 /PDM/BlkCache/cbCachedMruIn             0 bytes
00:53:14.910 /PDM/BlkCache/cbCachedMruOut            0 bytes
00:53:14.910 /PDM/BlkCache/cbMax               5242880 bytes
00:53:14.910 /PDM/CritSects/AHCI0/ContentionR3        0 times
00:53:14.910 /PDM/CritSects/AHCI0/ContentionRZLock        4 times
00:53:14.910 /PDM/CritSects/AHCI0/ContentionRZUnlock        0 times
00:53:14.910 /PDM/CritSects/ATA0/ContentionR3        0 times
00:53:14.910 /PDM/CritSects/ATA0/ContentionRZLock        0 times
00:53:14.910 /PDM/CritSects/ATA0/ContentionRZUnlock        0 times
00:53:14.910 /PDM/CritSects/ATA1/ContentionR3        0 times
00:53:14.910 /PDM/CritSects/ATA1/ContentionRZLock        1 times
00:53:14.910 /PDM/CritSects/ATA1/ContentionRZUnlock        0 times
00:53:14.910 /PDM/CritSects/E1000#0/ContentionR3        0 times
00:53:14.910 /PDM/CritSects/E1000#0/ContentionRZLock        0 times
00:53:14.910 /PDM/CritSects/E1000#0/ContentionRZUnlock        0 times
00:53:14.910 /PDM/CritSects/E1000#0RX/ContentionR3        0 times
00:53:14.910 /PDM/CritSects/E1000#0RX/ContentionRZLock        0 times
00:53:14.910 /PDM/CritSects/E1000#0RX/ContentionRZUnlock        0 times
00:53:14.910 /PDM/CritSects/EM-REM/ContentionR3        0 times
00:53:14.910 /PDM/CritSects/EM-REM/ContentionRZLock        0 times
00:53:14.910 /PDM/CritSects/EM-REM/ContentionRZUnlock        0 times
00:53:14.910 /PDM/CritSects/EmulatedATA0/ContentionR3        0 times
00:53:14.910 /PDM/CritSects/EmulatedATA0/ContentionRZLock        4 times
00:53:14.910 /PDM/CritSects/EmulatedATA0/ContentionRZUnlock        0 times
00:53:14.910 /PDM/CritSects/EmulatedATA1/ContentionR3        0 times
00:53:14.910 /PDM/CritSects/EmulatedATA1/ContentionRZLock        0 times
00:53:14.910 /PDM/CritSects/EmulatedATA1/ContentionRZUnlock        0 times
00:53:14.910 /PDM/CritSects/FTM/ContentionR3         0 times
00:53:14.910 /PDM/CritSects/FTM/ContentionRZLock        0 times
00:53:14.910 /PDM/CritSects/FTM/ContentionRZUnlock        0 times
00:53:14.910 /PDM/CritSects/IOM EMT Lock/ContentionR3        0 times
00:53:14.910 /PDM/CritSects/IOM EMT Lock/ContentionRZLock        0 times
00:53:14.910 /PDM/CritSects/IOM EMT Lock/ContentionRZUnlock        0 times
00:53:14.910 /PDM/CritSects/MM-HYPER/ContentionR3        0 times
00:53:14.910 /PDM/CritSects/MM-HYPER/ContentionRZLock        0 times
00:53:14.910 /PDM/CritSects/MM-HYPER/ContentionRZUnlock        0 times
00:53:14.910 /PDM/CritSects/PDM/ContentionR3         0 times
00:53:14.910 /PDM/CritSects/PDM/ContentionRZLock     1720 times
00:53:14.910 /PDM/CritSects/PDM/ContentionRZUnlock        3 times
00:53:14.910 /PDM/CritSects/PGM/ContentionR3         0 times
00:53:14.910 /PDM/CritSects/PGM/ContentionRZLock    73084 times
00:53:14.910 /PDM/CritSects/PGM/ContentionRZUnlock        0 times
00:53:14.910 /PDM/CritSects/PS2KM#0/ContentionR3        0 times
00:53:14.910 /PDM/CritSects/PS2KM#0/ContentionRZLock        0 times
00:53:14.910 /PDM/CritSects/PS2KM#0/ContentionRZUnlock        0 times
00:53:14.910 /PDM/CritSects/REM-Register/ContentionR3        0 times
00:53:14.910 /PDM/CritSects/REM-Register/ContentionRZLock        0 times
00:53:14.910 /PDM/CritSects/REM-Register/ContentionRZUnlock        0 times
00:53:14.910 /PDM/CritSects/TM Timer Lock/ContentionR3        0 times
00:53:14.910 /PDM/CritSects/TM Timer Lock/ContentionRZLock        0 times
00:53:14.910 /PDM/CritSects/TM Timer Lock/ContentionRZUnlock        0 times
00:53:14.910 /PDM/CritSects/TM VirtualSync Lock/ContentionR3        0 times
00:53:14.910 /PDM/CritSects/TM VirtualSync Lock/ContentionRZLock        0 times
00:53:14.910 /PDM/CritSects/TM VirtualSync Lock/ContentionRZUnlock        0 times
00:53:14.910 /PDM/CritSects/VGA/ContentionR3         0 times
00:53:14.910 /PDM/CritSects/VGA/ContentionRZLock        0 times
00:53:14.910 /PDM/CritSects/VGA/ContentionRZUnlock        0 times
00:53:14.910 /PDM/CritSects/VMMDev/ContentionR3        0 times
00:53:14.910 /PDM/CritSects/VMMDev/ContentionRZLock        0 times
00:53:14.910 /PDM/CritSects/VMMDev/ContentionRZUnlock        0 times
00:53:14.910 /PDM/Queue/AHCI-Xmit/AllocFailures        0 times
00:53:14.910 /PDM/Queue/AHCI-Xmit/Flush              0 calls
00:53:14.910 /PDM/Queue/AHCI-Xmit/FlushLeftovers        0 times
00:53:14.910 /PDM/Queue/AHCI-Xmit/Insert        242545 calls
00:53:14.910 /PDM/Queue/AHCI-Xmit/cItems            60 count
00:53:14.910 /PDM/Queue/AHCI-Xmit/cbItem            16 bytes
00:53:14.910 /PDM/Queue/DevHlp/AllocFailures         0 times
00:53:14.910 /PDM/Queue/DevHlp/Flush                 0 calls
00:53:14.910 /PDM/Queue/DevHlp/FlushLeftovers        0 times
00:53:14.910 /PDM/Queue/DevHlp/Insert                0 calls
00:53:14.910 /PDM/Queue/DevHlp/cItems                8 count
00:53:14.910 /PDM/Queue/DevHlp/cbItem               32 bytes
00:53:14.910 /PDM/Queue/E1000-Rcv/AllocFailures        0 times
00:53:14.910 /PDM/Queue/E1000-Rcv/Flush              0 calls
00:53:14.910 /PDM/Queue/E1000-Rcv/FlushLeftovers        0 times
00:53:14.910 /PDM/Queue/E1000-Rcv/Insert           536 calls
00:53:14.910 /PDM/Queue/E1000-Rcv/cItems             1 count
00:53:14.910 /PDM/Queue/E1000-Rcv/cbItem            16 bytes
00:53:14.910 /PDM/Queue/E1000-Xmit/AllocFailures        0 times
00:53:14.910 /PDM/Queue/E1000-Xmit/Flush             0 calls
00:53:14.910 /PDM/Queue/E1000-Xmit/FlushLeftovers        0 times
00:53:14.910 /PDM/Queue/E1000-Xmit/Insert         5908 calls
00:53:14.910 /PDM/Queue/E1000-Xmit/cItems            1 count
00:53:14.910 /PDM/Queue/E1000-Xmit/cbItem           16 bytes
00:53:14.910 /PDM/Queue/Keyboard/AllocFailures        0 times
00:53:14.910 /PDM/Queue/Keyboard/Flush               0 calls
00:53:14.910 /PDM/Queue/Keyboard/FlushLeftovers        0 times
00:53:14.910 /PDM/Queue/Keyboard/Insert              6 calls
00:53:14.910 /PDM/Queue/Keyboard/cItems             64 count
00:53:14.910 /PDM/Queue/Keyboard/cbItem             16 bytes
00:53:14.910 /PDM/Queue/Mouse/AllocFailures          0 times
00:53:14.910 /PDM/Queue/Mouse/Flush                  0 calls
00:53:14.910 /PDM/Queue/Mouse/FlushLeftovers         0 times
00:53:14.910 /PDM/Queue/Mouse/Insert              8561 calls
00:53:14.910 /PDM/Queue/Mouse/cItems               128 count
00:53:14.910 /PDM/Queue/Mouse/cbItem                48 bytes
00:53:14.910 /PGM/CPU0/cGuestModeChanges         35274 times
00:53:14.910 /PGM/ChunkR3Map/Mapped                426 count
00:53:14.910 /PGM/ChunkR3Map/Unmapped                0 count
00:53:14.910 /PGM/ChunkR3Map/c                     426 count
00:53:14.910 /PGM/ChunkR3Map/cMax                  512 count
00:53:14.910 /PGM/LargePage/Alloc                    0 times
00:53:14.910 /PGM/LargePage/Recheck                  0 times
00:53:14.910 /PGM/LargePage/Refused                  0 times
00:53:14.910 /PGM/LargePage/Reused                   0 times
00:53:14.910 /PGM/Page/cAllPages                226851 count
00:53:14.910 /PGM/Page/cBalloonedPages               0 count
00:53:14.910 /PGM/Page/cHandyPages                  69 count
00:53:14.910 /PGM/Page/cMonitoredPages               0 count
00:53:14.910 /PGM/Page/cPrivatePages            226570 count
00:53:14.910 /PGM/Page/cPureMmioPages                1 count
00:53:14.910 /PGM/Page/cReadLockedPages              0 count
00:53:14.910 /PGM/Page/cReusedSharedPages            0 count
00:53:14.910 /PGM/Page/cSharedPages                  0 count
00:53:14.910 /PGM/Page/cWriteLockedPages             0 count
00:53:14.910 /PGM/Page/cWrittenToPages               0 count
00:53:14.910 /PGM/Page/cZeroPages                  280 count
00:53:14.910 /PGM/cRelocations                       0 times
00:53:14.910 /PROF/CPU0/EM/Capped                    0 ticks/call (           0 ticks,       0 times, max         0, min      -1)
00:53:14.910 /PROF/CPU0/EM/ForcedActions       1306262 times
00:53:14.910 /PROF/CPU0/EM/Halted               238422 times
00:53:14.910 /PROF/CPU0/EM/RAWTotal                  0 times
00:53:14.910 /PROF/CPU0/EM/REMTotal              90044 times
00:53:14.910 /PROF/CPU0/EM/Total              11159254512483 ticks/call (11159254512483 ticks,       1 times, max 11159254512483, min 11159254512483)
00:53:14.910 /PROF/VM/CPU0/Halt/Block          1796313 ns/call (1824628915790 ticks, 1015763 times, max  15053798, min       1)
00:53:14.910 /PROF/VM/CPU0/Halt/BlockInsomnia        0 ns/call (           0 ticks,       0 times, max         0, min      -1)
00:53:14.910 /PROF/VM/CPU0/Halt/BlockOnTime          0 ns/call (           0 ticks,       0 times, max         0, min      -1)
00:53:14.910 /PROF/VM/CPU0/Halt/BlockOverslept        0 ns/call (           0 ticks,       0 times, max         0, min      -1)
00:53:14.910 /PROF/VM/CPU0/Halt/Timers            2120 ns/call (  2738836907 ticks, 1291620 times, max   4430508, min       2)
00:53:14.910 /PROF/VM/CPU0/Halt/Yield             1926 ns/call (      229195 ticks,     119 times, max      5510, min    1400)
00:53:14.910 /REM/TbFlushCount                   53580 times
00:53:14.910 /REM/TbPhysInvldCount              136698 times
00:53:14.910 /REM/TlbFlushCount                5283103 times
00:53:14.910 /TM/CPU/00/cNsExecuting          1009387157230 ns
00:53:14.910 /TM/CPU/00/cNsHalted             1828068243650 ns
00:53:14.910 /TM/CPU/00/cNsOther              350995547172 ns
00:53:14.910 /TM/CPU/00/cNsTotal              3188450948052 ns
00:53:14.910 /TM/CPU/00/cPeriodsExecuting     159530178 count
00:53:14.910 /TM/CPU/00/cPeriodsHalted          237741 count
00:53:14.910 /TM/CPU/00/pctExecuting                42 %
00:53:14.910 /TM/CPU/00/pctHalted                   30 %
00:53:14.910 /TM/CPU/00/pctOther                    26 %
00:53:14.910 /TM/CPU/pctExecuting                   42 %
00:53:14.910 /TM/CPU/pctHalted                      30 %
00:53:14.910 /TM/CPU/pctOther                       26 %
00:53:14.910 /TM/MaxHzHint                          99 Hz
00:53:14.910 /TM/R0/1nsSteps                    859948 times
00:53:14.910 /TM/R3/1nsSteps                    891077 times
00:53:14.910 /TM/TSC/offCPU0                  4301170505247 ticks
00:53:14.910 /TM/VirtualSync/CurrentOffset      349371 ns
00:53:14.910 /VUSB/0/cUrbsInPool                     0 count
00:53:14.910 /VUSB/1/cUrbsInPool                     0 count
00:53:14.910 ********************* End of statistics **********************
00:53:15.131 NAT: zone(nm:mbuf, used:3)
00:53:15.131 NAT: zone(nm:mbuf_cluster, used:0)
00:53:15.131 NAT: zone(nm:mbuf_packet, used:0)
00:53:15.131 NAT: zone(nm:mbuf_jumbo_pagesize, used:0)
00:53:15.131 NAT: zone(nm:mbuf_jumbo_9k, used:0)
00:53:15.131 NAT: zone(nm:mbuf_jumbo_16k, used:0)
00:53:15.184 Changing the VM state from 'DESTROYING' to 'TERMINATED'.
```

---

