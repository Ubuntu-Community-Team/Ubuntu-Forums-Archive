---
title: "Virtual box and intrepid unable to open VM"
date: 2008-12-21
forum: Virtualisation
---

### Post by Robbyx on 2008-12-21
I had been advised to reinstall Intrepid by taking a new user name. My home directory was on a separate drive. 

Since the reinstall I have not been able to access the VB drive.

After doing a fair amount of fidling around I have progressed to  clicking on the available snapshot of win2k and instead of windows loading getting an error message:

FATAL: could not read from the boot medium! System halted.

I have tried to discard the current snapshot and the current state of the VM but I can see the following error messages when I attempt it:
> 
Could not open the hard disk storage unit '/home/robin/.VirtualBox/Win2knew.vdi'.
VD: error opening image file '/home/robin/.VirtualBox/Win2knew.vdi' (VERR_FILE_NOT_FOUND).


Result Code: 
NS_ERROR_FAILURE (0x80004005)
Component: 
HardDisk2
Interface: 
IHardDisk2 {ed6e2525-c2fd-42a4-917a-7a9045ac9e15}


Robin is no longer the user. It is rob. I should be seeing /home/rob/.virtualbox. How do I do that?

---

### Post by bodhi.zazen on 2008-12-21
```
sudo cp -R /home/robin/.VirtualBox/ /home/rob
sudo chown -R rob.rob /home/rob/.VirtualBox/
```

If that fails

```
sudo chown -R rob.rob /home/robin/.VirtualBox/
```

---

### Post by Robbyx on 2008-12-22
Thank you for trying to help me. I had moved the .virtualbox from robin to rob prior to your advice. I therefore ran 
sudo chown -R rob.rob /home/rob/.VirtualBox/

It made no difference. Of course the second idea did not work because of the original move.

These are the files in .virtualbox. I wonder if they will us find a solution?

> /home/rob/.VirtualBox/xpti.dat
/home/rob/.VirtualBox/Win2knew.vdi
/home/rob/.VirtualBox/VirtualBox.xml.1.3-linux.bak
/home/rob/.VirtualBox/VirtualBox.xml
/home/rob/.VirtualBox/compreg.dat
/home/rob/.VirtualBox/Machines


In machines/win2k
> /home/rob/.VirtualBox/Machines/Win2k/Win2k.xml.1.3-linux.bak
/home/rob/.VirtualBox/Machines/Win2k/Win2k.xml
/home/rob/.VirtualBox/Machines/Win2k/Snapshots
/home/rob/.VirtualBox/Machines/Win2k/Logs


In snapshots

> /home/rob/.VirtualBox/Machines/Win2k/Snapshots/{b5df4910-cc93-436c-5685-70926befcef7}.sav
/home/rob/.VirtualBox/Machines/Win2k/Snapshots/{7127e9fd-0755-4d86-f8b0-b42d2cbb37b1}.vdi


This is the content of the vbox.log.1, the latest of the logs

```
00:00:00.366 VirtualBox 2.1.0 r41146 linux.x86 (Dec 17 2008 10:18:42) release log
00:00:00.366 Log opened 2008-12-21T21:15:51.107327000Z
00:00:00.366 OS Product: Linux
00:00:00.366 OS Release: 2.6.27-9-generic
00:00:00.366 OS Version: #1 SMP Thu Nov 20 21:57:00 UTC 2008
00:00:00.366 Package type: LINUX_32BITS_UBUNTU_8_10
00:00:00.377 SUP: Loaded VMMR0.r0 (/usr/lib/virtualbox/VMMR0.r0) at 0xfb99a060 - ModuleInit at 00000000fb9aaed0 and ModuleTerm at 00000000fb9aae90
00:00:00.377 SUP: VMMR0EntryEx located at 00000000fb9aad90, VMMR0EntryFast at 00000000fb9aaf40 and VMMR0EntryInt at 00000000fb9aa190
00:00:00.405 Initializing host clipboard service
00:00:00.433 Shared clipboard: starting host clipboard thread
00:00:00.433 VBoxSharedClipboard mode: Bidirectional
00:00:00.481 ************************* CFGM dump *************************
00:00:00.481 pRoot=b5d01338:{/}
00:00:00.481 [/] (level 0)
00:00:00.481   Name               <string>  = "Win2k" (cch=6)
00:00:00.481   UUID               <bytes>   = "67 92 f2 e3 6c 5d 84 47 45 b0 27 e1 36 2f 06 af" (cb=16)
00:00:00.481   RamSize            <integer> = 0x000000003b200000 (991952896)
00:00:00.481   NumCPUs            <integer> = 0x0000000000000001 (1)
00:00:00.481   TimerMillies       <integer> = 0x000000000000000a (10)
00:00:00.481   RawR3Enabled       <integer> = 0x0000000000000001 (1)
00:00:00.481   RawR0Enabled       <integer> = 0x0000000000000001 (1)
00:00:00.481   PATMEnabled        <integer> = 0x0000000000000001 (1)
00:00:00.481   CSAMEnabled        <integer> = 0x0000000000000001 (1)
00:00:00.481   HwVirtExtForced    <integer> = 0x0000000000000000 (0)
00:00:00.481   EnableNestedPaging <integer> = 0x0000000000000000 (0)
00:00:00.481   EnableVPID         <integer> = 0x0000000000000000 (0)
00:00:00.481   EnablePAE          <integer> = 0x0000000000000000 (0)
00:00:00.481 
00:00:00.481 [/HWVirtExt/] (level 1)
00:00:00.482   Enabled      <integer> = 0x0000000000000001 (1)
00:00:00.482   64bitEnabled <integer> = 0x0000000000000000 (0)
00:00:00.482 
00:00:00.482 [/PDM/] (level 1)
00:00:00.482 
00:00:00.482 [/PDM/Drivers/] (level 2)
00:00:00.482 
00:00:00.482 [/PDM/Drivers/VBoxC/] (level 3)
00:00:00.482   Path <string>  = "/usr/lib/virtualbox/components/VBoxC" (cch=37)
00:00:00.482 
00:00:00.482 [/Devices/] (level 1)
00:00:00.482 
00:00:00.482 [/Devices/pcarch/] (level 2)
00:00:00.482 
00:00:00.482 [/Devices/pcarch/0/] (level 3)
00:00:00.482   Trusted <integer> = 0x0000000000000001 (1)
00:00:00.482 
00:00:00.482 [/Devices/pcarch/0/Config/] (level 4)
00:00:00.482 
00:00:00.482 [/Devices/pcbios/] (level 2)
00:00:00.482 
00:00:00.482 [/Devices/pcbios/0/] (level 3)
00:00:00.482   Trusted <integer> = 0x0000000000000001 (1)
00:00:00.482 
00:00:00.482 [/Devices/pcbios/0/Config/] (level 4)
00:00:00.482   RamSize        <integer> = 0x000000003b200000 (991952896)
00:00:00.482   NumCPUs        <integer> = 0x0000000000000001 (1)
00:00:00.482   HardDiskDevice <string>  = "piix3ide" (cch=9)
00:00:00.482   FloppyDevice   <string>  = "i82078" (cch=7)
00:00:00.482   IOAPIC         <integer> = 0x0000000000000001 (1)
00:00:00.482   PXEDebug       <integer> = 0x0000000000000000 (0)
00:00:00.482   UUID           <bytes>   = "67 92 f2 e3 6c 5d 84 47 45 b0 27 e1 36 2f 06 af" (cb=16)
00:00:00.482   BootDevice0    <string>  = "IDE" (cch=4)
00:00:00.482   BootDevice1    <string>  = "NONE" (cch=5)
00:00:00.482   BootDevice2    <string>  = "NONE" (cch=5)
00:00:00.482   BootDevice3    <string>  = "NONE" (cch=5)
00:00:00.482 
00:00:00.482 [/Devices/8237A/] (level 2)
00:00:00.482 
00:00:00.482 [/Devices/8237A/0/] (level 3)
00:00:00.482   Trusted <integer> = 0x0000000000000001 (1)
00:00:00.482 
00:00:00.482 [/Devices/pci/] (level 2)
00:00:00.482 
00:00:00.482 [/Devices/pci/0/] (level 3)
00:00:00.482   Trusted <integer> = 0x0000000000000001 (1)
00:00:00.482 
00:00:00.482 [/Devices/pci/0/Config/] (level 4)
00:00:00.482   IOAPIC <integer> = 0x0000000000000001 (1)
00:00:00.482 
00:00:00.482 [/Devices/pckbd/] (level 2)
00:00:00.482 
00:00:00.482 [/Devices/pckbd/0/] (level 3)
00:00:00.482   Trusted <integer> = 0x0000000000000001 (1)
00:00:00.482 
00:00:00.482 [/Devices/pckbd/0/Config/] (level 4)
00:00:00.482 
00:00:00.482 [/Devices/pckbd/0/LUN#0/] (level 4)
00:00:00.482   Driver <string>  = "KeyboardQueue" (cch=14)
00:00:00.482 
00:00:00.482 [/Devices/pckbd/0/LUN#0/Config/] (level 5)
00:00:00.482   QueueSize <integer> = 0x0000000000000040 (64)
00:00:00.482 
00:00:00.482 [/Devices/pckbd/0/LUN#0/AttachedDriver/] (level 5)
00:00:00.482   Driver <string>  = "MainKeyboard" (cch=13)
00:00:00.482 
00:00:00.482 [/Devices/pckbd/0/LUN#0/AttachedDriver/Config/] (level 6)
00:00:00.482   Object <integer> = 0x00000000090d92d0 (151884496)
00:00:00.482 
00:00:00.482 [/Devices/pckbd/0/LUN#1/] (level 4)
00:00:00.482   Driver <string>  = "MouseQueue" (cch=11)
00:00:00.482 
00:00:00.482 [/Devices/pckbd/0/LUN#1/Config/] (level 5)
00:00:00.482   QueueSize <integer> = 0x0000000000000080 (128)
00:00:00.482 
00:00:00.482 [/Devices/pckbd/0/LUN#1/AttachedDriver/] (level 5)
00:00:00.482   Driver <string>  = "MainMouse" (cch=10)
00:00:00.482 
00:00:00.482 [/Devices/pckbd/0/LUN#1/AttachedDriver/Config/] (level 6)
00:00:00.482   Object <integer> = 0x00000000090d93a8 (151884712)
00:00:00.482 
00:00:00.482 [/Devices/i82078/] (level 2)
00:00:00.482 
00:00:00.482 [/Devices/i82078/0/] (level 3)
00:00:00.482   Trusted <integer> = 0x0000000000000001 (1)
00:00:00.482 
00:00:00.482 [/Devices/i82078/0/Config/] (level 4)
00:00:00.482   IRQ       <integer> = 0x0000000000000006 (6)
00:00:00.482   DMA       <integer> = 0x0000000000000002 (2)
00:00:00.482   MemMapped <integer> = 0x0000000000000000 (0)
00:00:00.482   IOBase    <integer> = 0x00000000000003f0 (1008)
00:00:00.482 
00:00:00.482 [/Devices/i82078/0/LUN#999/] (level 4)
00:00:00.482   Driver <string>  = "MainStatus" (cch=11)
00:00:00.482 
00:00:00.482 [/Devices/i82078/0/LUN#999/Config/] (level 5)
00:00:00.482   papLeds <integer> = 0x00000000090d8c3c (151882812)
00:00:00.482   First   <integer> = 0x0000000000000000 (0)
00:00:00.482   Last    <integer> = 0x0000000000000000 (0)
00:00:00.482 
00:00:00.482 [/Devices/i82078/0/LUN#0/] (level 4)
00:00:00.482   Driver <string>  = "Block" (cch=6)
00:00:00.482 
00:00:00.482 [/Devices/i82078/0/LUN#0/Config/] (level 5)
00:00:00.482   Type      <string>  = "Floppy 1.44" (cch=12)
00:00:00.482   Mountable <integer> = 0x0000000000000001 (1)
00:00:00.482 
00:00:00.482 [/Devices/acpi/] (level 2)
00:00:00.482 
00:00:00.482 [/Devices/acpi/0/] (level 3)
00:00:00.482   Trusted       <integer> = 0x0000000000000001 (1)
00:00:00.482   PCIDeviceNo   <integer> = 0x0000000000000007 (7)
00:00:00.482   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:00.482 
00:00:00.482 [/Devices/acpi/0/Config/] (level 4)
00:00:00.482   RamSize    <integer> = 0x000000003b200000 (991952896)
00:00:00.482   NumCPUs    <integer> = 0x0000000000000001 (1)
00:00:00.482   IOAPIC     <integer> = 0x0000000000000001 (1)
00:00:00.482   FdcEnabled <integer> = 0x0000000000000001 (1)
00:00:00.482 
00:00:00.482 [/Devices/acpi/0/LUN#0/] (level 4)
00:00:00.482   Driver <string>  = "ACPIHost" (cch=9)
00:00:00.482 
00:00:00.482 [/Devices/acpi/0/LUN#0/Config/] (level 5)
00:00:00.482 
00:00:00.482 [/Devices/i8254/] (level 2)
00:00:00.482 
00:00:00.482 [/Devices/i8254/0/] (level 3)
00:00:00.482 
00:00:00.482 [/Devices/i8254/0/Config/] (level 4)
00:00:00.482 
00:00:00.482 [/Devices/i8259/] (level 2)
00:00:00.482 
00:00:00.483 [/Devices/i8259/0/] (level 3)
00:00:00.483   Trusted <integer> = 0x0000000000000001 (1)
00:00:00.483 
00:00:00.483 [/Devices/i8259/0/Config/] (level 4)
00:00:00.483 
00:00:00.483 [/Devices/apic/] (level 2)
00:00:00.483 
00:00:00.483 [/Devices/apic/0/] (level 3)
00:00:00.483   Trusted <integer> = 0x0000000000000001 (1)
00:00:00.483 
00:00:00.483 [/Devices/apic/0/Config/] (level 4)
00:00:00.483   IOAPIC  <integer> = 0x0000000000000001 (1)
00:00:00.483   NumCPUs <integer> = 0x0000000000000001 (1)
00:00:00.483 
00:00:00.483 [/Devices/ioapic/] (level 2)
00:00:00.483 
00:00:00.483 [/Devices/ioapic/0/] (level 3)
00:00:00.483   Trusted <integer> = 0x0000000000000001 (1)
00:00:00.483 
00:00:00.483 [/Devices/ioapic/0/Config/] (level 4)
00:00:00.483 
00:00:00.483 [/Devices/mc146818/] (level 2)
00:00:00.483 
00:00:00.483 [/Devices/mc146818/0/] (level 3)
00:00:00.483 
00:00:00.483 [/Devices/mc146818/0/Config/] (level 4)
00:00:00.483 
00:00:00.483 [/Devices/vga/] (level 2)
00:00:00.483 
00:00:00.483 [/Devices/vga/0/] (level 3)
00:00:00.483   Trusted       <integer> = 0x0000000000000001 (1)
00:00:00.483   PCIDeviceNo   <integer> = 0x0000000000000002 (2)
00:00:00.483   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:00.483 
00:00:00.483 [/Devices/vga/0/Config/] (level 4)
00:00:00.483   VRamSize         <integer> = 0x0000000001000000 (16777216)
00:00:00.483   FadeIn           <integer> = 0x0000000000000001 (1)
00:00:00.483   FadeOut          <integer> = 0x0000000000000001 (1)
00:00:00.483   LogoTime         <integer> = 0x0000000000000000 (0)
00:00:00.483   LogoFile         <string>  = "" (cch=1)
00:00:00.483   ShowBootMenu     <integer> = 0x0000000000000002 (2)
00:00:00.483   CustomVideoModes <integer> = 0x0000000000000000 (0)
00:00:00.483   HeightReduction  <integer> = 0x0000000000000000 (0)
00:00:00.483 
00:00:00.483 [/Devices/vga/0/LUN#0/] (level 4)
00:00:00.483   Driver <string>  = "MainDisplay" (cch=12)
00:00:00.483 
00:00:00.483 [/Devices/vga/0/LUN#0/Config/] (level 5)
00:00:00.483   Object <integer> = 0x00000000090d9480 (151884928)
00:00:00.483 
00:00:00.483 [/Devices/piix3ide/] (level 2)
00:00:00.483 
00:00:00.483 [/Devices/piix3ide/0/] (level 3)
00:00:00.483   Trusted       <integer> = 0x0000000000000001 (1)
00:00:00.483   PCIDeviceNo   <integer> = 0x0000000000000001 (1)
00:00:00.483   PCIFunctionNo <integer> = 0x0000000000000001 (1)
00:00:00.483 
00:00:00.483 [/Devices/piix3ide/0/Config/] (level 4)
00:00:00.483   PIIX4 <integer> = 0x0000000000000000 (0)
00:00:00.483 
00:00:00.483 [/Devices/piix3ide/0/LUN#999/] (level 4)
00:00:00.483   Driver <string>  = "MainStatus" (cch=11)
00:00:00.483 
00:00:00.483 [/Devices/piix3ide/0/LUN#999/Config/] (level 5)
00:00:00.483   papLeds <integer> = 0x00000000090d8c44 (151882820)
00:00:00.483   First   <integer> = 0x0000000000000000 (0)
00:00:00.483   Last    <integer> = 0x0000000000000003 (3)
00:00:00.483 
00:00:00.483 [/Devices/piix3ide/0/LUN#2/] (level 4)
00:00:00.483   Driver <string>  = "Block" (cch=6)
00:00:00.483 
00:00:00.483 [/Devices/piix3ide/0/LUN#2/Config/] (level 5)
00:00:00.483   Type      <string>  = "DVD" (cch=4)
00:00:00.483   Mountable <integer> = 0x0000000000000001 (1)
00:00:00.483 
00:00:00.483 [/Devices/piix3ide/0/LUN#2/AttachedDriver/] (level 5)
00:00:00.483   Driver <string>  = "MediaISO" (cch=9)
00:00:00.483 
00:00:00.483 [/Devices/piix3ide/0/LUN#2/AttachedDriver/Config/] (level 6)
00:00:00.483   Path <string>  = "/usr/share/virtualbox/VBoxGuestAdditions.iso" (cch=45)
00:00:00.483 
00:00:00.483 [/Devices/pcnet/] (level 2)
00:00:00.483 
00:00:00.483 [/Devices/pcnet/0/] (level 3)
00:00:00.483   Trusted       <integer> = 0x0000000000000001 (1)
00:00:00.483   PCIDeviceNo   <integer> = 0x0000000000000003 (3)
00:00:00.483   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:00.483 
00:00:00.483 [/Devices/pcnet/0/Config/] (level 4)
00:00:00.483   Am79C973       <integer> = 0x0000000000000001 (1)
00:00:00.483   MAC            <bytes>   = "08 00 27 03 9d 3c" (cb=6)
00:00:00.483   CableConnected <integer> = 0x0000000000000001 (1)
00:00:00.483   LineSpeed      <integer> = 0x00000000000f4240 (1000000)
00:00:00.483 
00:00:00.483 [/Devices/pcnet/0/LUN#999/] (level 4)
00:00:00.483   Driver <string>  = "MainStatus" (cch=11)
00:00:00.483 
00:00:00.483 [/Devices/pcnet/0/LUN#999/Config/] (level 5)
00:00:00.483   papLeds <integer> = 0x00000000090d8ccc (151882956)
00:00:00.483 
00:00:00.483 [/Devices/pcnet/0/LUN#0/] (level 4)
00:00:00.483   Driver <string>  = "NAT" (cch=4)
00:00:00.483 
00:00:00.483 [/Devices/pcnet/0/LUN#0/Config/] (level 5)
00:00:00.483   TFTPPrefix <string>  = "/home/rob/.VirtualBox/TFTP" (cch=27)
00:00:00.483   BootFile   <string>  = "Win2k.pxe" (cch=10)
00:00:00.483 
00:00:00.483 [/Devices/e1000/] (level 2)
00:00:00.483 
00:00:00.483 [/Devices/serial/] (level 2)
00:00:00.483 
00:00:00.483 [/Devices/parallel/] (level 2)
00:00:00.483 
00:00:00.483 [/Devices/VMMDev/] (level 2)
00:00:00.483 
00:00:00.483 [/Devices/VMMDev/0/] (level 3)
00:00:00.483   Trusted       <integer> = 0x0000000000000001 (1)
00:00:00.483   PCIDeviceNo   <integer> = 0x0000000000000004 (4)
00:00:00.483   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:00.483 
00:00:00.483 [/Devices/VMMDev/0/Config/] (level 4)
00:00:00.483 
00:00:00.483 [/Devices/VMMDev/0/LUN#0/] (level 4)
00:00:00.483   Driver <string>  = "MainVMMDev" (cch=11)
00:00:00.483 
00:00:00.483 [/Devices/VMMDev/0/LUN#0/Config/] (level 5)
00:00:00.483   Object <integer> = 0x00000000090d9eb0 (151887536)
00:00:00.483 
00:00:00.483 [/Devices/VMMDev/0/LUN#999/] (level 4)
00:00:00.484   Driver <string>  = "MainStatus" (cch=11)
00:00:00.484 
00:00:00.484 [/Devices/VMMDev/0/LUN#999/Config/] (level 5)
00:00:00.484   papLeds <integer> = 0x00000000090d8cec (151882988)
00:00:00.484   First   <integer> = 0x0000000000000000 (0)
00:00:00.484   Last    <integer> = 0x0000000000000000 (0)
00:00:00.484 
00:00:00.484 [/Devices/AudioSniffer/] (level 2)
00:00:00.484 
00:00:00.484 [/Devices/AudioSniffer/0/] (level 3)
00:00:00.484 
00:00:00.484 [/Devices/AudioSniffer/0/Config/] (level 4)
00:00:00.484 
00:00:00.484 [/Devices/AudioSniffer/0/LUN#0/] (level 4)
00:00:00.484   Driver <string>  = "MainAudioSniffer" (cch=17)
00:00:00.484 
00:00:00.484 [/Devices/AudioSniffer/0/LUN#0/Config/] (level 5)
00:00:00.484   Object <integer> = 0x00000000090d88e0 (151881952)
00:00:00.484 
00:00:00.484 [/Devices/usb-ohci/] (level 2)
00:00:00.484 
00:00:00.484 [/Devices/usb-ohci/0/] (level 3)
00:00:00.484   Trusted       <integer> = 0x0000000000000001 (1)
00:00:00.484   PCIDeviceNo   <integer> = 0x0000000000000006 (6)
00:00:00.484   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:00.484 
00:00:00.484 [/Devices/usb-ohci/0/Config/] (level 4)
00:00:00.484 
00:00:00.484 [/Devices/usb-ohci/0/LUN#0/] (level 4)
00:00:00.484   Driver <string>  = "VUSBRootHub" (cch=12)
00:00:00.484 
00:00:00.484 [/Devices/usb-ohci/0/LUN#0/Config/] (level 5)
00:00:00.484 
00:00:00.484 [/Devices/usb-ohci/0/LUN#999/] (level 4)
00:00:00.484   Driver <string>  = "MainStatus" (cch=11)
00:00:00.484 
00:00:00.484 [/Devices/usb-ohci/0/LUN#999/Config/] (level 5)
00:00:00.484   papLeds <integer> = 0x00000000090d8cf0 (151882992)
00:00:00.484   First   <integer> = 0x0000000000000000 (0)
00:00:00.484   Last    <integer> = 0x0000000000000000 (0)
00:00:00.484 
00:00:00.484 [/Devices/usb-ehci/] (level 2)
00:00:00.484 
00:00:00.484 [/Devices/usb-ehci/0/] (level 3)
00:00:00.484   Trusted       <integer> = 0x0000000000000001 (1)
00:00:00.484   PCIDeviceNo   <integer> = 0x000000000000000b (11)
00:00:00.484   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:00.484 
00:00:00.484 [/Devices/usb-ehci/0/Config/] (level 4)
00:00:00.484 
00:00:00.484 [/Devices/usb-ehci/0/LUN#0/] (level 4)
00:00:00.484   Driver <string>  = "VUSBRootHub" (cch=12)
00:00:00.484 
00:00:00.484 [/Devices/usb-ehci/0/LUN#0/Config/] (level 5)
00:00:00.484 
00:00:00.484 [/Devices/usb-ehci/0/LUN#999/] (level 4)
00:00:00.484   Driver <string>  = "MainStatus" (cch=11)
00:00:00.484 
00:00:00.484 [/Devices/usb-ehci/0/LUN#999/Config/] (level 5)
00:00:00.484   papLeds <integer> = 0x00000000090d8cf4 (151882996)
00:00:00.484   First   <integer> = 0x0000000000000000 (0)
00:00:00.484   Last    <integer> = 0x0000000000000000 (0)
00:00:00.484 
00:00:00.484 [/TM/] (level 1)
00:00:00.484   UTCOffset <integer> = 0x0000000000000000 (0)
00:00:00.484 
00:00:00.484 ********************* End of CFGM dump **********************
00:00:00.485 Logical host processors: 2, processor active mask: 0000000000000003
00:00:00.485 ************************* CPUID dump ************************
00:00:00.485          RAW Standard CPUIDs
00:00:00.485      Function  eax      ebx      ecx      edx
00:00:00.485 Gst: 00000000  00000002 756e6547 6c65746e 49656e69
00:00:00.485 Hst:           0000000a 756e6547 6c65746e 49656e69
00:00:00.485 Gst: 00000001  00010676 00000800 00000009 078bf1bf
00:00:00.485 Hst:           00010676 00020800 0008e3fd bfebfbff
00:00:00.485 Gst: 00000002  05b0b101 005657f0 00000000 2cb4304e
00:00:00.485 Hst:           05b0b101 005657f0 00000000 2cb4304e
00:00:00.485 Gst: 00000003  07280202 00000000 00000000 00000503*
00:00:00.485 Hst:           00000000 00000000 00000000 00000000
00:00:00.485 Gst: 00000004  00000000 00000000 00000000 00000503*
00:00:00.485 Hst:           04000121 01c0003f 0000003f 00000001
00:00:00.485 Gst: 00000005  07280202 00000000 00000000 00000503*
00:00:00.485 Hst:           00000040 00000040 00000003 00022220
00:00:00.485 Name:                            GenuineIntel
00:00:00.485 Supports:                        0-2
00:00:00.485 Family:                          6  	Extended: 0 	Effective: 6
00:00:00.485 Model:                           7  	Extended: 1 	Effective: 23
00:00:00.485 Stepping:                        6
00:00:00.485 APIC ID:                         0x00
00:00:00.485 Logical CPUs:                    0
00:00:00.485 CLFLUSH Size:                    8
00:00:00.485 Brand ID:                        0x00
00:00:00.485 Mnemonic - Description                 = guest (host)
00:00:00.485 FPU - x87 FPU on Chip                  = 1 (1)
00:00:00.485 VME - Virtual 8086 Mode Enhancements   = 1 (1)
00:00:00.485 DE - Debugging extensions              = 1 (1)
00:00:00.485 PSE - Page Size Extension              = 1 (1)
00:00:00.485 TSC - Time Stamp Counter               = 1 (1)
00:00:00.485 MSR - Model Specific Registers         = 1 (1)
00:00:00.485 PAE - Physical Address Extension       = 0 (1)
00:00:00.485 MCE - Machine Check Exception          = 1 (1)
00:00:00.485 CX8 - CMPXCHG8B instruction            = 1 (1)
00:00:00.485 APIC - APIC On-Chip                    = 0 (1)
00:00:00.485 Reserved                               = 0 (0)
00:00:00.485 SEP - SYSENTER and SYSEXIT             = 0 (1)
00:00:00.485 MTRR - Memory Type Range Registers     = 1 (1)
00:00:00.485 PGE - PTE Global Bit                   = 1 (1)
00:00:00.485 MCA - Machine Check Architecture       = 1 (1)
00:00:00.485 CMOV - Conditional Move Instructions   = 1 (1)
00:00:00.485 PAT - Page Attribute Table             = 1 (1)
00:00:00.485 PSE-36 - 36-bit Page Size Extention    = 1 (1)
00:00:00.485 PSN - Processor Serial Number          = 0 (0)
00:00:00.485 CLFSH - CLFLUSH Instruction.           = 1 (1)
00:00:00.485 Reserved                               = 0 (0)
00:00:00.485 DS - Debug Store                       = 0 (1)
00:00:00.485 ACPI - Thermal Mon. & Soft. Clock Ctrl.= 0 (1)
00:00:00.485 MMX - Intel MMX Technology             = 1 (1)
00:00:00.485 FXSR - FXSAVE and FXRSTOR Instructions = 1 (1)
00:00:00.485 SSE - SSE Support                      = 1 (1)
00:00:00.485 SSE2 - SSE2 Support                    = 1 (1)
00:00:00.485 SS - Self Snoop                        = 0 (1)
00:00:00.485 HTT - Hyper-Threading Technolog        = 0 (1)
00:00:00.485 TM - Thermal Monitor                   = 0 (1)
00:00:00.485 30 - Reserved                          = 0 (0)
00:00:00.485 PBE - Pending Break Enable             = 0 (1)
00:00:00.485 Supports SSE3 or not                   = 1 (1)
00:00:00.485 Reserved                               = 0 (2)
00:00:00.485 Supports MONITOR/MWAIT                 = 1 (1)
00:00:00.485 CPL-DS - CPL Qualified Debug Store     = 0 (1)
00:00:00.485 VMX - Virtual Machine Technology       = 0 (1)
00:00:00.485 Reserved                               = 0 (1)
00:00:00.485 Enhanced SpeedStep Technology          = 0 (1)
00:00:00.485 Terminal Monitor 2                     = 0 (1)
00:00:00.485 Supports Supplemental SSE3 or not      = 0 (1)
00:00:00.485 L1 Context ID                          = 0 (0)
00:00:00.485 Reserved                               = 0x0 (0x0)
00:00:00.485 CMPXCHG16B                             = 0 (1)
00:00:00.485 xTPR Update Control                    = 0 (1)
00:00:00.485 Reserved                               = 0x0 (0x11)
00:00:00.485 
00:00:00.485          RAW Extended CPUIDs
00:00:00.485      Function  eax      ebx      ecx      edx
00:00:00.485 Gst: 80000000  80000008 00000000 00000000 00000000
00:00:00.485 Hst:           80000008 00000000 00000000 00000000
00:00:00.485 Gst: 80000001  00000000 00000000 00000000 00000000
00:00:00.485 Hst:           00000000 00000000 00000001 20100000
00:00:00.485 Gst: 80000002  65746e49 2952286c 726f4320 4d542865
00:00:00.485 Hst:           65746e49 2952286c 726f4320 4d542865
00:00:00.485 Gst: 80000003  44203229 43206f75 20205550 45202020
00:00:00.485 Hst:           44203229 43206f75 20205550 45202020
00:00:00.485 Gst: 80000004  30303238 20402020 36362e32 007a4847
00:00:00.485 Hst:           30303238 20402020 36362e32 007a4847
00:00:00.485 Gst: 80000005  00000000 00000000 00000000 00000000
00:00:00.485 Hst:           00000000 00000000 00000000 00000000
00:00:00.485 Gst: 80000006  00000000 00000000 18008040 00000000
00:00:00.485 Hst:           00000000 00000000 18008040 00000000
00:00:00.485 Gst: 80000007  00000000 00000000 00000000 00000000
00:00:00.485 Hst:           00000000 00000000 00000000 00000000
00:00:00.485 Gst: 80000008  00003024 00000000 00000000 00000000
00:00:00.485 Hst:           00003024 00000000 00000000 00000000
00:00:00.485 Gst: 80000009  07280202 00000000 00000000 00000503*
00:00:00.485 Hst:           07280202 00000000 00000000 00000503
00:00:00.485 Ext Name:                        
00:00:00.485 Ext Supports:                    0x80000000-0x80000008
00:00:00.485 Family:                          0  	Extended: 0 	Effective: 0
00:00:00.485 Model:                           0  	Extended: 0 	Effective: 0
00:00:00.485 Stepping:                        0
00:00:00.485 Brand ID:                        0x000
00:00:00.485 Mnemonic - Description                 = guest (host)
00:00:00.485 FPU - x87 FPU on Chip                  = 0 (0)
00:00:00.485 VME - Virtual 8086 Mode Enhancements   = 0 (0)
00:00:00.485 DE - Debugging extensions              = 0 (0)
00:00:00.485 PSE - Page Size Extension              = 0 (0)
00:00:00.485 TSC - Time Stamp Counter               = 0 (0)
00:00:00.485 MSR - K86 Model Specific Registers     = 0 (0)
00:00:00.485 PAE - Physical Address Extension       = 0 (0)
00:00:00.485 MCE - Machine Check Exception          = 0 (0)
00:00:00.485 CX8 - CMPXCHG8B instruction            = 0 (0)
00:00:00.485 APIC - APIC On-Chip                    = 0 (0)
00:00:00.485 10 - Reserved                          = 0 (0)
00:00:00.485 SEP - SYSCALL and SYSRET               = 0 (0)
00:00:00.485 MTRR - Memory Type Range Registers     = 0 (0)
00:00:00.485 PGE - PTE Global Bit                   = 0 (0)
00:00:00.485 MCA - Machine Check Architecture       = 0 (0)
00:00:00.485 CMOV - Conditional Move Instructions   = 0 (0)
00:00:00.485 PAT - Page Attribute Table             = 0 (0)
00:00:00.485 PSE-36 - 36-bit Page Size Extention    = 0 (0)
00:00:00.485 18 - Reserved                          = 0 (0)
00:00:00.485 19 - Reserved                          = 0 (0)
00:00:00.485 NX - No-Execute Page Protection        = 0 (1)
00:00:00.485 DS - Debug Store                       = 0 (0)
00:00:00.485 AXMMX - AMD Extensions to MMX Instr.   = 0 (0)
00:00:00.485 MMX - Intel MMX Technology             = 0 (0)
00:00:00.485 FXSR - FXSAVE and FXRSTOR Instructions = 0 (0)
00:00:00.485 25 - AMD fast FXSAVE and FXRSTOR Instr.= 0 (0)
00:00:00.485 26 - 1 GB large page support           = 0 (0)
00:00:00.485 27 - RDTSCP instruction                = 0 (0)
00:00:00.485 28 - Reserved                          = 0 (0)
00:00:00.485 29 - AMD Long Mode                     = 0 (1)
00:00:00.485 30 - AMD Extensions to 3DNow           = 0 (0)
00:00:00.485 31 - AMD 3DNow                         = 0 (0)
00:00:00.485 LahfSahf - LAHF/SAHF in 64-bit mode    = 0 (1)
00:00:00.485 CmpLegacy - Core MP legacy mode (depr) = 0 (0)
00:00:00.485 SVM - AMD VM Extensions                = 0 (0)
00:00:00.485 APIC registers starting at 0x400       = 0 (0)
00:00:00.485 AltMovCR8 - LOCK MOV CR0 means MOV CR8 = 0 (0)
00:00:00.485 Advanced bit manipulation              = 0 (0)
00:00:00.485 SSE4A instruction support              = 0 (0)
00:00:00.485 Misaligned SSE mode                    = 0 (0)
00:00:00.485 PREFETCH and PREFETCHW instruction     = 0 (0)
00:00:00.485 OS visible workaround                  = 0 (0)
00:00:00.485 Instruction based sampling             = 0 (0)
00:00:00.485 SSE5 support                           = 0 (0)
00:00:00.485 SKINIT, STGI, and DEV support          = 0 (0)
00:00:00.485 Watchdog timer support.                = 0 (0)
00:00:00.485 31:14 - Reserved                       = 0x0 (0x0)
00:00:00.485 Full Name:                       Intel(R) Core(TM)2 Duo CPU     E8200  @ 2.66GHz
00:00:00.485 TLB 2/4M Instr/Uni:              res0     0 entries
00:00:00.485 TLB 2/4M Data:                   res0     0 entries
00:00:00.485 TLB 4K Instr/Uni:                res0     0 entries
00:00:00.485 TLB 4K Data:                     res0     0 entries
00:00:00.485 L1 Instr Cache Line Size:        0 bytes
00:00:00.485 L1 Instr Cache Lines Per Tag:    0
00:00:00.485 L1 Instr Cache Associativity:    res0  
00:00:00.485 L1 Instr Cache Size:             0 KB
00:00:00.485 L1 Data Cache Line Size:         0 bytes
00:00:00.485 L1 Data Cache Lines Per Tag:     0
00:00:00.485 L1 Data Cache Associativity:     res0  
00:00:00.485 L1 Data Cache Size:              0 KB
00:00:00.485 L2 TLB 2/4M Instr/Uni:           off       0 entries
00:00:00.485 L2 TLB 2/4M Data:                off       0 entries
00:00:00.485 L2 TLB 4K Instr/Uni:             off       0 entries
00:00:00.485 L2 TLB 4K Data:                  off       0 entries
00:00:00.485 L2 Cache Line Size:              0 bytes
00:00:00.485 L2 Cache Lines Per Tag:          0
00:00:00.485 L2 Cache Associativity:          off   
00:00:00.485 L2 Cache Size:                   0 KB
00:00:00.485 APM Features:                   
00:00:00.485 Physical Address Width:          36 bits
00:00:00.485 Virtual Address Width:           48 bits
00:00:00.485 Physical Core Count:             0
00:00:00.485 
00:00:00.485          RAW Centaur CPUIDs
00:00:00.485      Function  eax      ebx      ecx      edx
00:00:00.485 Gst: c0000000  07280202 00000000 00000000 00000503
00:00:00.485 Hst:           07280202 00000000 00000000 00000503
00:00:00.485 Gst: c0000001  07280202 00000000 00000000 00000503
00:00:00.485 Hst:           07280202 00000000 00000000 00000503
00:00:00.485 Gst: c0000002  07280202 00000000 00000000 00000503
00:00:00.485 Hst:           07280202 00000000 00000000 00000503
00:00:00.485 Gst: c0000003  07280202 00000000 00000000 00000503
00:00:00.485 Hst:           07280202 00000000 00000000 00000503
00:00:00.485 Centaur Supports:                0xc0000000-0x07280202
00:00:00.485 Mnemonic - Description                 = guest (host)
00:00:00.485 AIS - Alternate Instruction Set        = 0 (1)
00:00:00.485 AIS-E - AIS enabled                    = 0 (1)
00:00:00.485 RNG - Random Number Generator          = 0 (0)
00:00:00.485 RNG-E - RNG enabled                    = 0 (0)
00:00:00.485 LH - LongHaul MSR 0000_110Ah           = 0 (0)
00:00:00.485 FEMMS - FEMMS                          = 0 (0)
00:00:00.485 ACE - Advanced Cryptography Engine     = 0 (0)
00:00:00.485 ACE-E - ACE enabled                    = 0 (0)
00:00:00.485 ACE2 - Advanced Cryptography Engine 2  = 0 (1)
00:00:00.485 ACE2-E - ACE enabled                   = 0 (0)
00:00:00.485 PHE - Hash Engine                      = 0 (1)
00:00:00.485 PHE-E - PHE enabled                    = 0 (0)
00:00:00.485 PMM - Montgomery Multiplier            = 0 (0)
00:00:00.485 PMM-E - PMM enabled                    = 0 (0)
00:00:00.485 
00:00:00.485 
00:00:00.485 ******************** End of CPUID dump **********************
00:00:00.486 REM: VBoxREM32
00:00:00.529 TM: cTSCTicksPerSecond=0xa173dcb8 (2708724920) fTSCVirtualized=true  fTSCUseRealTSC=false
00:00:00.529 TM: fMaybeUseOffsettedHostTSC=true  TSCTiedToExecution=false TSCNotTiedToHalt=false
00:00:00.530 CoreCode: R3=b6463000 R0=fa8e3000 RC=a055e000 Phys=00000000336d0000 cb=0x2000
00:00:00.538 SUP: Loaded VBoxDDR0.r0 (/usr/lib/virtualbox/VBoxDDR0.r0) at 0xfa8e6060 - ModuleInit at 0000000000000000 and ModuleTerm at 0000000000000000
00:00:00.541 SUP: Loaded VBoxDD2R0.r0 (/usr/lib/virtualbox/VBoxDD2R0.r0) at 0xfa8f9060 - ModuleInit at 0000000000000000 and ModuleTerm at 0000000000000000
00:00:00.541 Activating Local APIC
00:00:00.541 CPUMSetGuestCpuIdFeature: Enabled APIC
00:00:00.541 CPUMSetGuestCpuIdFeature: Disabled x2APIC
00:00:00.541 PIT: mode=3 count=0x10000 (65536) - 18.20 Hz (ch=0)
00:00:00.543 Shared Folders service loaded.
00:00:00.550 PIIX3 ATA: LUN#0: no unit
00:00:00.550 PIIX3 ATA: LUN#1: no unit
00:00:00.550 PIIX3 ATA: LUN#2: CD/DVD, total number of sectors 13238, passthrough disabled
00:00:00.550 PIIX3 ATA: LUN#3: no unit
00:00:00.550 PIIX3 ATA: Ctl#0: finished processing RESET
00:00:00.651 PIIX3 ATA: Ctl#1: finished processing RESET
00:00:00.751 NAT: passing domain name config
00:00:00.751 NAT: DNS address: 192.168.1.254
00:00:00.752 PGMR3InitFinalize: 4 MB PSE mask 0000000fffffffff
00:00:00.765 HWACCM: Host CR4=00000690
00:00:00.765 HWACCM: MSR_IA32_FEATURE_CONTROL      = 5
00:00:00.765 HWACCM: MSR_IA32_VMX_BASIC_INFO       = 5a08000000000d
00:00:00.765 HWACCM: VMCS id                       = d
00:00:00.765 HWACCM: VMCS size                     = 800
00:00:00.765 HWACCM: VMCS physical address limit   = None
00:00:00.765 HWACCM: VMCS memory type              = 6
00:00:00.765 HWACCM: Dual monitor treatment        = 1
00:00:00.765 HWACCM: MSR_IA32_VMX_PINBASED_CTLS    = 3f00000016
00:00:00.765 HWACCM:    VMX_VMCS_CTRL_PIN_EXEC_CONTROLS_EXT_INT_EXIT
00:00:00.765 HWACCM:    VMX_VMCS_CTRL_PIN_EXEC_CONTROLS_NMI_EXIT
00:00:00.765 HWACCM: MSR_IA32_VMX_PROCBASED_CTLS   = f7f9fffe0401e172
00:00:00.766 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_IRQ_WINDOW_EXIT
00:00:00.766 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_TSC_OFFSET
00:00:00.766 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_HLT_EXIT
00:00:00.766 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_INVLPG_EXIT
00:00:00.766 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_MWAIT_EXIT
00:00:00.766 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_RDPMC_EXIT
00:00:00.766 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_RDTSC_EXIT
00:00:00.766 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_CR3_LOAD_EXIT
00:00:00.766 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_CR3_STORE_EXIT
00:00:00.766 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_CR8_LOAD_EXIT
00:00:00.766 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_CR8_STORE_EXIT
00:00:00.766 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_USE_TPR_SHADOW
00:00:00.766 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_MOV_DR_EXIT
00:00:00.766 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_UNCOND_IO_EXIT
00:00:00.766 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_USE_IO_BITMAPS
00:00:00.766 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_USE_MSR_BITMAPS
00:00:00.766 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_MONITOR_EXIT
00:00:00.766 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_PAUSE_EXIT
00:00:00.766 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_USE_SECONDARY_EXEC_CTRL
00:00:00.766 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_CR3_LOAD_EXIT *must* be set
00:00:00.766 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC_CONTROLS_CR3_STORE_EXIT *must* be set
00:00:00.766 HWACCM: MSR_IA32_VMX_PROCBASED_CTLS2  = 4100000000
00:00:00.766 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC2_VIRT_APIC
00:00:00.766 HWACCM:    VMX_VMCS_CTRL_PROC_EXEC2_WBINVD_EXIT
00:00:00.766 HWACCM: MSR_IA32_VMX_ENTRY_CTLS       = 3fff000011ff
00:00:00.766 HWACCM:    VMX_VMCS_CTRL_ENTRY_CONTROLS_LOAD_DEBUG
00:00:00.766 HWACCM:    VMX_VMCS_CTRL_ENTRY_CONTROLS_IA64_MODE
00:00:00.766 HWACCM:    VMX_VMCS_CTRL_ENTRY_CONTROLS_ENTRY_SMM
00:00:00.766 HWACCM:    VMX_VMCS_CTRL_ENTRY_CONTROLS_DEACTIVATE_DUALMON
00:00:00.766 HWACCM:    VMX_VMCS_CTRL_ENTRY_CONTROLS_LOAD_GUEST_PERF_MSR
00:00:00.766 HWACCM:    VMX_VMCS_CTRL_ENTRY_CONTROLS_LOAD_DEBUG *must* be set
00:00:00.766 HWACCM: MSR_IA32_VMX_EXIT_CTLS        = 3ffff00036dff
00:00:00.766 HWACCM:    VMX_VMCS_CTRL_EXIT_CONTROLS_SAVE_DEBUG
00:00:00.766 HWACCM:    VMX_VMCS_CTRL_EXIT_CONTROLS_HOST_AMD64
00:00:00.766 HWACCM:    VMX_VMCS_CTRL_EXIT_CONTROLS_ACK_EXTERNAL_IRQ
00:00:00.766 HWACCM:    VMX_VMCS_CTRL_EXIT_CONTROLS_SAVE_DEBUG *must* be set
00:00:00.766 HWACCM: MSR_IA32_VMX_MISC             = 403c0
00:00:00.766 HWACCM:    MSR_IA32_VMX_MISC_ACTIVITY_STATES 7
00:00:00.766 HWACCM:    MSR_IA32_VMX_MISC_CR3_TARGET      4
00:00:00.766 HWACCM:    MSR_IA32_VMX_MISC_MAX_MSR         200
00:00:00.766 HWACCM:    MSR_IA32_VMX_MISC_MSEG_ID         0
00:00:00.766 HWACCM: MSR_IA32_VMX_CR0_FIXED0       = 80000021
00:00:00.766 HWACCM: MSR_IA32_VMX_CR0_FIXED1       = ffffffff
00:00:00.766 HWACCM: MSR_IA32_VMX_CR4_FIXED0       = 2000
00:00:00.766 HWACCM: MSR_IA32_VMX_CR4_FIXED1       = 67ff
00:00:00.766 HWACCM: MSR_IA32_VMX_VMCS_ENUM        = 2c
00:00:00.766 HWACCM: TPR shadow physaddr           = 0000000032de7000
00:00:00.766 HWACCM: MSR bitmap physaddr           = 0000000032de6000
00:00:00.766 HWACCM: VMCS physaddr VCPU0           = 0000000032de5000
00:00:00.766 HWACCM: Real Mode TSS guest physaddr  = 00000000f0800000
00:00:00.766 HWACCM: Non-Paging Mode EPT CR3       = 00000000f0803000
00:00:00.779 CPUMSetGuestCpuIdFeature: Enabled sysenter/exit
00:00:00.779 HWACCM: 32-bit guest supported.
00:00:00.779 HWACCM: VMX enabled!
00:00:00.792 VM: Halt method global1 (5)
00:00:00.792 Changing the VM state from 'CREATING' to 'CREATED'.
00:00:00.792 SharedFolders host service: adding host mapping.
00:00:00.792     Host path /media/mydocs/My Documents/CLIENTS, map name CLIENTS, writable 1
00:00:00.793 SharedFolders host service: add mapping result VINF_SUCCESS
00:00:00.793 SharedFolders host service: adding host mapping.
00:00:00.793     Host path /media/mydocs, map name Docs, writable 1
00:00:00.793 SharedFolders host service: add mapping result VINF_SUCCESS
00:00:00.793 SharedFolders host service: adding host mapping.
00:00:00.793     Host path /media/mydocs/My Documents, map name My Documents, writable 1
00:00:00.793 SharedFolders host service: add mapping result VINF_SUCCESS
00:00:00.793 Changing the VM state from 'CREATED' to 'RUNNING'.
00:00:00.796 Guest Log: BIOS: VirtualBox 2.1.0
00:00:00.796 PIT: mode=2 count=0x10000 (65536) - 18.20 Hz (ch=0)
00:00:00.865 PIIX3 ATA: Ctl#1: RESET, DevSel=0 AIOIf=0 CmdIf0=0x00 (-1 usec ago) CmdIf1=0x00 (-1 usec ago)
00:00:00.865 PIIX3 ATA: Ctl#1: finished processing RESET
00:00:00.866 PIT: mode=2 count=0x48d3 (18643) - 64.00 Hz (ch=0)
00:00:00.868 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=b3305000 w=640 h=480 bpp=32 cbLine=0xA00
00:00:03.346 PIT: mode=2 count=0x10000 (65536) - 18.20 Hz (ch=0)
00:00:03.347 Guest Log: BIOS: int13_harddisk: function 02, parameters out of range 0000/0000/0001!
00:00:03.347 Guest Log: BIOS: Boot from Hard Disk 0 failed
00:00:03.348 Guest Log: Could not read from the boot medium! System halted.
00:00:03.348 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=00000000 w=720 h=400 bpp=0 cbLine=0x0
00:00:12.952 Changing the VM state from 'RUNNING' to 'SUSPENDED'.
00:00:17.585 Console::powerDown(): A request to power off the VM has been issued (mMachineState=8, InUninit=0)
00:00:17.590 vboxClipboardDestroy: shutting down host clipboard
00:00:17.601 Shared clipboard: host clipboard thread terminated successfully
00:00:17.601 ****************** Guest state at power off ******************
00:00:17.601 Guest CPUM state: se
00:00:17.601 eax=0000f001 ebx=0000d7a1 ecx=00000001 edx=00000000 esi=0000bff0 edi=0000ffd8
00:00:17.601 eip=00000a6e esp=0000ffb6 ebp=0000ffca iopl=0      rf nv up di pl zr na pe nc
00:00:17.601 cs={f000 base=00000000000f0000 limit=0000ffff flags=000000f3} dr0=00000000 dr1=00000000
00:00:17.601 ds={0000 base=0000000000000000 limit=0000ffff flags=000000f3} dr2=00000000 dr3=00000000
00:00:17.601 es={07c0 base=0000000000007c00 limit=0000ffff flags=000000f3} dr4=00000000 dr5=00000000
00:00:17.601 fs={0000 base=0000000000000000 limit=0000ffff flags=000000f3} dr6=ffff0ff0 dr7=00000400
00:00:17.601 gs={0000 base=0000000000000000 limit=0000ffff flags=000000f3} cr0=60000010 cr2=00000000
00:00:17.601 ss={0000 base=0000000000000000 limit=0000ffff flags=000000f3} cr3=00000000 cr4=00000000
00:00:17.601 gdtr=0000000000000000:ffff  idtr=0000000000000000:ffff  eflags=00010002
00:00:17.601 ldtr={0000 base=00000000 limit=00000000 flags=00000082}
00:00:17.601 tr  ={0000 base=00000000 limit=0000ffff flags=00000089}
00:00:17.601 SysEnter={cs=0000 eip=00000000 esp=00000000}
00:00:17.601 FPU:
00:00:17.601 FCW=037f FSW=0000 FTW=00
00:00:17.601 res1=00 FOP=0000 FPUIP=00000000 CS=0000 Rsvrd1=0000
00:00:17.601 FPUDP=0000 DS=0000 Rsvrd2=0000 MXCSR=00000000 MXCSR_MASK=00000000
00:00:17.601 MSR:
00:00:17.601 EFER         =0000000000000000
00:00:17.601 PAT          =0007040600070406
00:00:17.601 STAR         =0000000000000000
00:00:17.601 CSTAR        =0000000000000000
00:00:17.601 LSTAR        =0000000000000000
00:00:17.601 SFMASK       =0000000000000000
00:00:17.601 KERNELGSBASE =0000000000000000
00:00:17.601 ***
00:00:17.601 Guest paging mode:  Real, changed 0 times, A20 enabled
00:00:17.601 Shadow paging mode: 32-bit
00:00:17.601 Host paging mode:   32-bit+G
00:00:17.601 ***
00:00:17.601 Active Timers (pVM=b5e4d000)
00:00:17.601 pTimerR3 offNext  offPrev  offSched Clock Time               Expire             State                     Description
00:00:17.601 b570dbb0 00007e50 00000000 00000000 Real  000000000011616561 000000000011611920 ACTIVE                    VGA Refresh Timer
00:00:17.601 b5715a00 00000000 ffff81b0 00000000 Real  000000000011616561 000000000011611935 ACTIVE                    EMT Yielder
00:00:17.601 b5708300 00000380 00000000 00000000 VrSy  000000012105665076 000000012160590478 ACTIVE                    i8254 Programmable Interval Timer
00:00:17.601 b5708680 0000c9c0 fffffc80 00000000 VrSy  000000012105665076 000000012990000000 ACTIVE                    MC146818 RTC/CMOS - Second
00:00:17.601 b5715040 00000000 ffff3640 00000000 VrSy  000000012105665076 000001199864031601 ACTIVE                    ACPI Timer
00:00:17.601 ***
00:00:17.601 Shadow GDT (GCAddr=a0561000):
00:00:17.602 ffd8 - 08f80087 a0008901 - base=a00108f8 limit=00000087 dpl=0 TSS32Avail Present 16-bit  HyperTSSTrap08
00:00:17.602 ffe0 - 08700087 a0008901 - base=a0010870 limit=00000087 dpl=0 TSS32Avail Present 16-bit  HyperTSS
00:00:17.602 ffe8 - 0000ffff 00af9b00 - base=00000000 limit=ffffffff dpl=0 CodeER Accessed Present Page 16-bit  HyperCS64
00:00:17.602 fff0 - 0000ffff 00cf9300 - base=00000000 limit=ffffffff dpl=0 DataRW Accessed Present Page 32-bit  HyperDS
00:00:17.602 fff8 - 0000ffff 00cf9b00 - base=00000000 limit=ffffffff dpl=0 CodeER Accessed Present Page 32-bit  HyperCS
00:00:17.602 ***
00:00:17.602 ***
00:00:17.602 ss:sp=0000:ffb6 0000:ff80 TO 0000:1007f:
00:00:17.602 b5bd2248 0000: 00 00 00 00 02 00 a8 ff-0c 01 d8 ff f0 bf a8 ff ................
00:00:17.602 b5bd2258 0010: 9a ff 00 00 00 00 01 00-0a 0e 00 00 c0 07 46 30 ..............F0
00:00:17.602 b5bd2268 0020: e5 05 00 f0 46 30 a0 d7-ae ff 00 00 a1 d7 ca ff ....F0..........
00:00:17.602 b5bd2278 0030: 57 0a 00 f0 a1 d7 00 00-c0 ff 00 00 00 00 d0 ff W...............
00:00:17.602 b5bd2288 0040: 00 00 d0 ff 00 00 00 00-76 00 d4 ff c7 17 07 00 ........v.......
00:00:17.602 b5bd2298 0050: a1 d7 00 00 f0 ff 5a af-00 00 00 00 80 00 01 00 ......Z.........
00:00:17.602 b5bd22a8 0060: 01 00 00 01 01 00 c0 07-06 00 00 80 02 00 c0 9f ................
00:00:17.602 b5bd22b8 0070: f6 ff 00 b7 01 00 f8 ff-a4 e2 00 f0 82 32 00 00 .............2..
00:00:17.602 b5bd22c8 0080: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:17.602 b5bd22d8 0090: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:17.602 b5bd22e8 00a0: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:17.602 b5bd22f8 00b0: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:17.602 b5bd2308 00c0: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:17.602 b5bd2318 00d0: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:17.602 b5bd2328 00e0: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:17.602 b5bd2338 00f0: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:17.602 2000:0000 TO 2000:01ff:
00:00:17.602 b5bd2248 0000: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:17.602 b5bd2258 0010: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:17.602 b5bd2268 0020: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:17.602 b5bd2278 0030: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:17.602 b5bd2288 0040: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:17.602 b5bd2298 0050: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:17.602 b5bd22a8 0060: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:17.602 b5bd22b8 0070: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:17.602 b5bd22c8 0080: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:17.602 b5bd22d8 0090: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:17.602 b5bd22e8 00a0: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:17.602 b5bd22f8 00b0: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:17.602 b5bd2308 00c0: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:17.602 b5bd2318 00d0: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:17.602 b5bd2328 00e0: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:17.602 b5bd2338 00f0: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:17.602 b5bd2348 0100: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:17.602 b5bd2358 0110: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:17.602 b5bd2368 0120: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:17.602 b5bd2378 0130: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:17.602 b5bd2388 0140: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:17.602 b5bd2398 0150: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:17.602 b5bd23a8 0160: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:17.602 b5bd23b8 0170: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:17.602 b5bd23c8 0180: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:17.602 b5bd23d8 0190: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:17.602 b5bd23e8 01a0: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:17.602 b5bd23f8 01b0: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:17.602 b5bd2408 01c0: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:17.602 b5bd2418 01d0: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:17.602 b5bd2428 01e0: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:17.602 b5bd2438 01f0: 00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00 ................
00:00:17.602 ************** End of Guest state at power off ***************
00:00:17.602 Changing the VM state from 'SUSPENDED' to 'OFF'.
00:00:17.606 Changing the VM state from 'OFF' to 'DESTROYING'.
00:00:17.606 ************************* Statistics *************************
00:00:17.606 /Devices/ATA0/Unit0/AtapiDMA            0 times
00:00:17.606 /Devices/ATA0/Unit0/AtapiPIO            0 times
00:00:17.606 /Devices/ATA0/Unit0/DMA                 0 times
00:00:17.606 /Devices/ATA0/Unit0/PIO                 0 times
00:00:17.606 /Devices/ATA0/Unit0/ReadBytes           0 bytes
00:00:17.606 /Devices/ATA0/Unit0/WrittenBytes        0 bytes
00:00:17.606 /Devices/ATA0/Unit1/AtapiDMA            0 times
00:00:17.606 /Devices/ATA0/Unit1/AtapiPIO            0 times
00:00:17.606 /Devices/ATA0/Unit1/DMA                 0 times
00:00:17.606 /Devices/ATA0/Unit1/PIO                 0 times
00:00:17.606 /Devices/ATA0/Unit1/ReadBytes           0 bytes
00:00:17.606 /Devices/ATA0/Unit1/WrittenBytes        0 bytes
00:00:17.606 /Devices/ATA1/Unit0/AtapiDMA            0 times
00:00:17.606 /Devices/ATA1/Unit0/AtapiPIO            0 times
00:00:17.606 /Devices/ATA1/Unit0/DMA                 0 times
00:00:17.606 /Devices/ATA1/Unit0/PIO                 0 times
00:00:17.606 /Devices/ATA1/Unit0/ReadBytes           0 bytes
00:00:17.606 /Devices/ATA1/Unit0/WrittenBytes        0 bytes
00:00:17.606 /Devices/ATA1/Unit1/AtapiDMA            0 times
00:00:17.606 /Devices/ATA1/Unit1/AtapiPIO            0 times
00:00:17.606 /Devices/ATA1/Unit1/DMA                 0 times
00:00:17.606 /Devices/ATA1/Unit1/PIO                 0 times
00:00:17.606 /Devices/ATA1/Unit1/ReadBytes           0 bytes
00:00:17.606 /Devices/ATA1/Unit1/WrittenBytes        0 bytes
00:00:17.606 /Devices/PCNet0/ReceiveBytes            0 bytes
00:00:17.606 /Devices/PCNet0/TransmitBytes           0 bytes
00:00:17.606 /Drivers/NAT0/Fill                   1368 ticks/call (        1368 ticks,       1 times, max      1368, min    1368)
00:00:17.606 /Drivers/NAT0/Poll                   2040 ticks/call (        2040 ticks,       1 times, max      2040, min    2040)
00:00:17.606 /Drivers/NAT0/SockTCP                   0 count
00:00:17.606 /Drivers/NAT0/SockTCPHot                0 count
00:00:17.606 /Drivers/NAT0/SockUDP                   0 count
00:00:17.606 /Drivers/NAT0/SockUDPHot                0 count
00:00:17.606 /Drivers/NAT0/TimerFast                 0 ticks/call (           0 ticks,       0 times, max         0, min      -1)
00:00:17.606 /Drivers/NAT0/TimerSlow                 0 ticks/call (           0 ticks,       0 times, max         0, min      -1)
00:00:17.606 /GVMM/Sum/HaltBlocking               1188 calls
00:00:17.606 /GVMM/Sum/HaltCalls                 15547 calls
00:00:17.606 /GVMM/Sum/HaltNotBlocking           14359 calls
00:00:17.606 /GVMM/Sum/HaltTimeouts                426 calls
00:00:17.606 /GVMM/Sum/HaltWakeUps                   0 calls
00:00:17.606 /GVMM/Sum/PollCalls                     0 calls
00:00:17.606 /GVMM/Sum/PollHalts                     0 calls
00:00:17.606 /GVMM/Sum/PollWakeUps                   0 calls
00:00:17.606 /GVMM/Sum/WakeUpCalls                1109 calls
00:00:17.606 /GVMM/Sum/WakeUpNotHalted             653 calls
00:00:17.606 /GVMM/Sum/WakeUpWakeUps                 0 calls
00:00:17.606 /GVMM/VM/HaltBlocking                1188 calls
00:00:17.606 /GVMM/VM/HaltCalls                  15547 calls
00:00:17.606 /GVMM/VM/HaltNotBlocking            14359 calls
00:00:17.606 /GVMM/VM/HaltTimeouts                 426 calls
00:00:17.606 /GVMM/VM/HaltWakeUps                    0 calls
00:00:17.606 /GVMM/VM/PollCalls                      0 calls
00:00:17.606 /GVMM/VM/PollHalts                      0 calls
00:00:17.606 /GVMM/VM/PollWakeUps                    0 calls
00:00:17.606 /GVMM/VM/WakeUpCalls                 1109 calls
00:00:17.606 /GVMM/VM/WakeUpNotHalted              653 calls
00:00:17.606 /GVMM/VM/WakeUpWakeUps                  0 calls
00:00:17.606 /GVMM/VMs                               1 calls
00:00:17.606 /MM/HyperHeap/cbFree              1156528 bytes
00:00:17.606 /MM/HyperHeap/cbHeap              1310656 bytes
00:00:17.606 /PDM/VUSB0/cUrbsInPool                  0 count
00:00:17.606 /PDM/VUSB1/cUrbsInPool                  0 count
00:00:17.606 /PGM/cGuestModeChanges                  0 times
00:00:17.606 /PROF/EM/ForcedActions               4646 ticks/call (     2072184 ticks,     446 times, max   1114408, min     216)
00:00:17.606 /PROF/EM/Halted                  180808179 ticks/call ( 32726280400 ticks,     181 times, max 3812703576, min 29066336)
00:00:17.606 /PROF/EM/RAWTotal                       0 ticks/call (           0 ticks,       0 times, max         0, min      -1)
00:00:17.606 /PROF/EM/REMTotal                       0 ticks/call (           0 ticks,       0 times, max         0, min      -1)
00:00:17.606 /PROF/EM/Total                   33071438576 ticks/call ( 33071438576 ticks,       1 times, max 33071438576, min 33071438576)
00:00:17.606 /PROF/VM/Halt/Block               2098231 ticks/call ( 32602318776 ticks,   15538 times, max  82906584, min    2000)
00:00:17.606 /PROF/VM/Halt/Poll                     73 ticks/call (     1390704 ticks,   18875 times, max      1424, min      40)
00:00:17.606 /PROF/VM/Halt/Timers                 5553 ticks/call (   104817056 ticks,   18875 times, max  25801104, min     808)
00:00:17.606 /PROF/VM/Halt/Yield                     0 ticks/call (           0 ticks,       0 times, max         0, min      -1)
00:00:17.606 /TM/R3/1nsSteps                      3764 times
00:00:17.606 /TM/VirtualSync/CurrentOffset          69 ns
00:00:17.606 ********************* End of statistics **********************
00:00:17.608 Changing the VM state from 'DESTROYING' to 'TERMINATED'.
```

---

### Post by Robbyx on 2008-12-23
I would very much appreciate some help, because currently I can not use VB and this is causing me a lot of problems.

---

