---
title: "VirtualBox: Guest internet suddenly not working"
date: 2008-02-04
forum: Virtualisation
---

### Post by jjsonp on 2008-02-04
Ubuntu 7.10 wired internet connection was working fine. XP Pro virtual machine running running in VirtualBox was working fine.

Then yesterday I played around with getting a wireless USB adapter to work...it worked for a while, then suddenly stopped, so I switched back to my wired connection and deleted the non-working wireless one.

Ubuntu's internet connection is working fine...but now my XP Pro VM can't connect to the internet. I've tried pinging and that also doesn't work, so it's not just DNS. The VirtualBox adapter shows 'cable connected'...I've tried turning this off and on, tried rebooting Ubuntu with the wired internet connection off and on - no luck.

Any ideas?

---

### Post by W A L E E D on 2009-02-08
I am facing same problem right now!!
suddenly the internet is not working in win xp virtual box!!

anybody can help?

---

### Post by Ng Oon-Ee on 2009-02-08
Some details you should provide...

What's the network adapter's set to in you VM? And what interface are they bound to? Any bridging things that you did to get networking working?

The latest VBox is actually very simple, just create an adapter, set it to host-only networking, and bind it to the adapter on your Linux that connects you to the internet. if you have a wireless and a LAN, create two adapters and whichever works will be used....

---

### Post by W A L E E D on 2009-02-08
I have the last VBox.
the proble is that it is connected in winXP, but there no internet!
it was working but suddenly my computer shut down, then there is no internet in Vbox!

---

### Post by Ng Oon-Ee on 2009-02-08
> **W A L E E D said:**
> I have the last VBox.
the proble is that it is connected in winXP, but there no internet!
it was working but suddenly my computer shut down, then there is no internet in Vbox!

I'm not sure you read my post properly. If you wish to ask for help, you need to provide the information I requested (as well as anything else you think may be useful).

With your VM shut down, go to VirtualBox, right-click on your VM, and choose 'settings'. Select 'Network' on the left-hand tab, then select each Adaptor tab (Adaptor 1, Adaptor 2 etc.) and tell us what exactly your current settings are.

Alternatively, a faster way to do the above would be to run the following command in a terminal:-
```
VBoxManage showvminfo WinXP | grep NIC
```
and copy-pasting the result here. If you jus tell us 'my network is not working', its like calling the doctor and saying 'I don't feel well', he's not going to be able to tell you what medication to take. You've said what you tried to do, but there's not enough detail, so you need to give more detail as mentioned above.

---

### Post by W A L E E D on 2009-02-08
Thanks.
I didn't understand what did mean at first post, so sorry. :)

Adapter 1
Adapter type PCnet-FAST III (Am79C973)
Attached to NAT

caple connected

---

### Post by Ng Oon-Ee on 2009-02-08
It's okay. Not all of us have English as a first language.

Anyway, try setting it to 'Host Interface' and choosing the interface that you use to connect to the internet. eth0 is normally for your LAN connection. If you don't understand the interfaces shown ask here.

---

### Post by W A L E E D on 2009-02-08
Thank you so much.
I tried it before but wasn't successful.
But now I did it twice and it works.
Thank you.

---

### Post by Ng Oon-Ee on 2009-02-08
You're welcome. Enjoy your VBox

---

### Post by baditaflorin on 2009-06-07
The internet it`s working fine in Ubuntu, but in VirtualBox i have Windows XP and no Network adapter. What can i do ?

> 00:00:00.800 VirtualBox 2.1.4_OSE r42893 linux.x86 (Mar 30 2009 00:56:07) release log
00:00:00.800 Log opened 2009-06-07T12:21:10.838684000Z
00:00:00.800 OS Product: Linux
00:00:00.800 OS Release: 2.6.28-11-generic
00:00:00.800 OS Version: #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009
00:00:00.800 Package type: LINUX_32BITS_GENERIC (OSE)
00:00:00.830 SUP: Loaded VMMR0.r0 (/usr/lib/virtualbox/VMMR0.r0) at 0xf8369060 - ModuleInit at 00000000f837a1f0 and ModuleTerm at 00000000f837a1b0
00:00:00.831 SUP: VMMR0EntryEx located at 00000000f837a0b0, VMMR0EntryFast at 00000000f837a260 and VMMR0EntryInt at 00000000f83794a0
00:00:00.861 Initializing host clipboard service
00:00:00.898 VBoxSharedClipboard mode: Bidirectional
00:00:00.898 Shared clipboard: starting host clipboard thread
00:00:00.953 ************************* CFGM dump *************************
00:00:00.953 pRoot=0a02ada0:{/}
00:00:00.953 [/] (level 0)
00:00:00.953   Name               <string>  = "Windows xp" (cch=11)
00:00:00.953   UUID               <bytes>   = "3b 0b 5b 40 f1 d3 23 49 b6 24 d7 9d ae 02 a3 36" (cb=16)
00:00:00.953   RamSize            <integer> = 0x0000000020000000 (536870912)
00:00:00.953   NumCPUs            <integer> = 0x0000000000000001 (1)
00:00:00.953   TimerMillies       <integer> = 0x000000000000000a (10)
00:00:00.953   RawR3Enabled       <integer> = 0x0000000000000001 (1)
00:00:00.953   RawR0Enabled       <integer> = 0x0000000000000001 (1)
00:00:00.953   PATMEnabled        <integer> = 0x0000000000000001 (1)
00:00:00.953   CSAMEnabled        <integer> = 0x0000000000000001 (1)
00:00:00.953   HwVirtExtForced    <integer> = 0x0000000000000000 (0)
00:00:00.953   EnableNestedPaging <integer> = 0x0000000000000000 (0)
00:00:00.953   EnableVPID         <integer> = 0x0000000000000000 (0)
00:00:00.953   EnablePAE          <integer> = 0x0000000000000000 (0)
00:00:00.953 
00:00:00.953 [/HWVirtExt/] (level 1)
00:00:00.953 
00:00:00.953 [/PDM/] (level 1)
00:00:00.953 
00:00:00.953 [/PDM/Drivers/] (level 2)
00:00:00.953 
00:00:00.953 [/PDM/Drivers/VBoxC/] (level 3)
00:00:00.953   Path <string>  = "/usr/lib/virtualbox/components/VBoxC" (cch=37)
00:00:00.953 
00:00:00.953 [/Devices/] (level 1)
00:00:00.953 
00:00:00.953 [/Devices/pcarch/] (level 2)
00:00:00.953 
00:00:00.953 [/Devices/pcarch/0/] (level 3)
00:00:00.953   Trusted <integer> = 0x0000000000000001 (1)
00:00:00.953 
00:00:00.953 [/Devices/pcarch/0/Config/] (level 4)
00:00:00.953 
00:00:00.953 [/Devices/pcbios/] (level 2)
00:00:00.953 
00:00:00.953 [/Devices/pcbios/0/] (level 3)
00:00:00.953   Trusted <integer> = 0x0000000000000001 (1)
00:00:00.953 
00:00:00.953 [/Devices/pcbios/0/Config/] (level 4)
00:00:00.953   RamSize        <integer> = 0x0000000020000000 (536870912)
00:00:00.953   NumCPUs        <integer> = 0x0000000000000001 (1)
00:00:00.953   HardDiskDevice <string>  = "piix3ide" (cch=9)
00:00:00.953   FloppyDevice   <string>  = "i82078" (cch=7)
00:00:00.953   IOAPIC         <integer> = 0x0000000000000000 (0)
00:00:00.953   PXEDebug       <integer> = 0x0000000000000000 (0)
00:00:00.953   UUID           <bytes>   = "3b 0b 5b 40 f1 d3 23 49 b6 24 d7 9d ae 02 a3 36" (cb=16)
00:00:00.953   BootDevice0    <string>  = "FLOPPY" (cch=7)
00:00:00.953   BootDevice1    <string>  = "DVD" (cch=4)
00:00:00.953   BootDevice2    <string>  = "IDE" (cch=4)
00:00:00.953   BootDevice3    <string>  = "NONE" (cch=5)
00:00:00.953 
00:00:00.953 [/Devices/8237A/] (level 2)
00:00:00.953 
00:00:00.953 [/Devices/8237A/0/] (level 3)
00:00:00.953   Trusted <integer> = 0x0000000000000001 (1)
00:00:00.953 
00:00:00.953 [/Devices/pci/] (level 2)
00:00:00.953 
00:00:00.953 [/Devices/pci/0/] (level 3)
00:00:00.953   Trusted <integer> = 0x0000000000000001 (1)
00:00:00.953 
00:00:00.953 [/Devices/pci/0/Config/] (level 4)
00:00:00.954   IOAPIC <integer> = 0x0000000000000000 (0)
00:00:00.954 
00:00:00.954 [/Devices/pckbd/] (level 2)
00:00:00.954 
00:00:00.954 [/Devices/pckbd/0/] (level 3)
00:00:00.954   Trusted <integer> = 0x0000000000000001 (1)
00:00:00.954 
00:00:00.954 [/Devices/pckbd/0/Config/] (level 4)
00:00:00.954 
00:00:00.954 [/Devices/pckbd/0/LUN#0/] (level 4)
00:00:00.954   Driver <string>  = "KeyboardQueue" (cch=14)
00:00:00.954 
00:00:00.954 [/Devices/pckbd/0/LUN#0/Config/] (level 5)
00:00:00.954   QueueSize <integer> = 0x0000000000000040 (64)
00:00:00.954 
00:00:00.954 [/Devices/pckbd/0/LUN#0/AttachedDriver/] (level 5)
00:00:00.954   Driver <string>  = "MainKeyboard" (cch=13)
00:00:00.954 
00:00:00.954 [/Devices/pckbd/0/LUN#0/AttachedDriver/Config/] (level 6)
00:00:00.954   Object <integer> = 0x000000000a0004c0 (167773376)
00:00:00.954 
00:00:00.954 [/Devices/pckbd/0/LUN#1/] (level 4)
00:00:00.954   Driver <string>  = "MouseQueue" (cch=11)
00:00:00.954 
00:00:00.954 [/Devices/pckbd/0/LUN#1/Config/] (level 5)
00:00:00.954   QueueSize <integer> = 0x0000000000000080 (128)
00:00:00.954 
00:00:00.954 [/Devices/pckbd/0/LUN#1/AttachedDriver/] (level 5)
00:00:00.954   Driver <string>  = "MainMouse" (cch=10)
00:00:00.954 
00:00:00.954 [/Devices/pckbd/0/LUN#1/AttachedDriver/Config/] (level 6)
00:00:00.954   Object <integer> = 0x000000000a000598 (167773592)
00:00:00.954 
00:00:00.954 [/Devices/i82078/] (level 2)
00:00:00.954 
00:00:00.954 [/Devices/i82078/0/] (level 3)
00:00:00.954   Trusted <integer> = 0x0000000000000001 (1)
00:00:00.954 
00:00:00.954 [/Devices/i82078/0/Config/] (level 4)
00:00:00.954   IRQ       <integer> = 0x0000000000000006 (6)
00:00:00.954   DMA       <integer> = 0x0000000000000002 (2)
00:00:00.954   MemMapped <integer> = 0x0000000000000000 (0)
00:00:00.954   IOBase    <integer> = 0x00000000000003f0 (1008)
00:00:00.954 
00:00:00.954 [/Devices/i82078/0/LUN#999/] (level 4)
00:00:00.954   Driver <string>  = "MainStatus" (cch=11)
00:00:00.954 
00:00:00.954 [/Devices/i82078/0/LUN#999/Config/] (level 5)
00:00:00.954   papLeds <integer> = 0x0000000009ffff54 (167771988)
00:00:00.954   First   <integer> = 0x0000000000000000 (0)
00:00:00.954   Last    <integer> = 0x0000000000000000 (0)
00:00:00.954 
00:00:00.954 [/Devices/i82078/0/LUN#0/] (level 4)
00:00:00.954   Driver <string>  = "Block" (cch=6)
00:00:00.954 
00:00:00.954 [/Devices/i82078/0/LUN#0/Config/] (level 5)
00:00:00.954   Type      <string>  = "Floppy 1.44" (cch=12)
00:00:00.954   Mountable <integer> = 0x0000000000000001 (1)
00:00:00.954 
00:00:00.954 [/Devices/acpi/] (level 2)
00:00:00.954 
00:00:00.954 [/Devices/acpi/0/] (level 3)
00:00:00.954   Trusted       <integer> = 0x0000000000000001 (1)
00:00:00.954   PCIDeviceNo   <integer> = 0x0000000000000007 (7)
00:00:00.954   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:00.954 
00:00:00.954 [/Devices/acpi/0/Config/] (level 4)
00:00:00.954   RamSize    <integer> = 0x0000000020000000 (536870912)
00:00:00.954   NumCPUs    <integer> = 0x0000000000000001 (1)
00:00:00.954   IOAPIC     <integer> = 0x0000000000000000 (0)
00:00:00.954   FdcEnabled <integer> = 0x0000000000000001 (1)
00:00:00.954 
00:00:00.954 [/Devices/acpi/0/LUN#0/] (level 4)
00:00:00.954   Driver <string>  = "ACPIHost" (cch=9)
00:00:00.954 
00:00:00.954 [/Devices/acpi/0/LUN#0/Config/] (level 5)
00:00:00.954 
00:00:00.954 [/Devices/i8254/] (level 2)
00:00:00.954 
00:00:00.954 [/Devices/i8254/0/] (level 3)
00:00:00.954 
00:00:00.954 [/Devices/i8254/0/Config/] (level 4)
00:00:00.954 
00:00:00.954 [/Devices/i8259/] (level 2)
00:00:00.954 
00:00:00.954 [/Devices/i8259/0/] (level 3)
00:00:00.954   Trusted <integer> = 0x0000000000000001 (1)
00:00:00.954 
00:00:00.954 [/Devices/i8259/0/Config/] (level 4)
00:00:00.954 
00:00:00.954 [/Devices/apic/] (level 2)
00:00:00.954 
00:00:00.954 [/Devices/apic/0/] (level 3)
00:00:00.954   Trusted <integer> = 0x0000000000000001 (1)
00:00:00.954 
00:00:00.954 [/Devices/apic/0/Config/] (level 4)
00:00:00.954   IOAPIC  <integer> = 0x0000000000000000 (0)
00:00:00.954   NumCPUs <integer> = 0x0000000000000001 (1)
00:00:00.954 
00:00:00.954 [/Devices/mc146818/] (level 2)
00:00:00.954 
00:00:00.954 [/Devices/mc146818/0/] (level 3)
00:00:00.954 
00:00:00.954 [/Devices/mc146818/0/Config/] (level 4)
00:00:00.954 
00:00:00.954 [/Devices/vga/] (level 2)
00:00:00.954 
00:00:00.954 [/Devices/vga/0/] (level 3)
00:00:00.954   Trusted       <integer> = 0x0000000000000001 (1)
00:00:00.955   PCIDeviceNo   <integer> = 0x0000000000000002 (2)
00:00:00.955   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:00.955 
00:00:00.955 [/Devices/vga/0/Config/] (level 4)
00:00:00.955   VRamSize         <integer> = 0x0000000000c00000 (12582912)
00:00:00.955   FadeIn           <integer> = 0x0000000000000001 (1)
00:00:00.955   FadeOut          <integer> = 0x0000000000000001 (1)
00:00:00.955   LogoTime         <integer> = 0x0000000000000000 (0)
00:00:00.955   LogoFile         <string>  = "" (cch=1)
00:00:00.955   ShowBootMenu     <integer> = 0x0000000000000002 (2)
00:00:00.955   CustomVideoModes <integer> = 0x0000000000000000 (0)
00:00:00.955   HeightReduction  <integer> = 0x0000000000000000 (0)
00:00:00.955 
00:00:00.955 [/Devices/vga/0/LUN#0/] (level 4)
00:00:00.955   Driver <string>  = "MainDisplay" (cch=12)
00:00:00.955 
00:00:00.955 [/Devices/vga/0/LUN#0/Config/] (level 5)
00:00:00.955   Object <integer> = 0x000000000a000670 (167773808)
00:00:00.955 
00:00:00.955 [/Devices/piix3ide/] (level 2)
00:00:00.955 
00:00:00.955 [/Devices/piix3ide/0/] (level 3)
00:00:00.955   Trusted       <integer> = 0x0000000000000001 (1)
00:00:00.955   PCIDeviceNo   <integer> = 0x0000000000000001 (1)
00:00:00.955   PCIFunctionNo <integer> = 0x0000000000000001 (1)
00:00:00.955 
00:00:00.955 [/Devices/piix3ide/0/Config/] (level 4)
00:00:00.955   PIIX4 <integer> = 0x0000000000000001 (1)
00:00:00.955 
00:00:00.955 [/Devices/piix3ide/0/LUN#999/] (level 4)
00:00:00.955   Driver <string>  = "MainStatus" (cch=11)
00:00:00.955 
00:00:00.955 [/Devices/piix3ide/0/LUN#999/Config/] (level 5)
00:00:00.955   papLeds <integer> = 0x0000000009ffff5c (167771996)
00:00:00.955   First   <integer> = 0x0000000000000000 (0)
00:00:00.955   Last    <integer> = 0x0000000000000003 (3)
00:00:00.955 
00:00:00.955 [/Devices/piix3ide/0/LUN#0/] (level 4)
00:00:00.955   Driver <string>  = "Block" (cch=6)
00:00:00.955 
00:00:00.955 [/Devices/piix3ide/0/LUN#0/Config/] (level 5)
00:00:00.955   Type      <string>  = "HardDisk" (cch=9)
00:00:00.955   Mountable <integer> = 0x0000000000000000 (0)
00:00:00.955 
00:00:00.955 [/Devices/piix3ide/0/LUN#0/AttachedDriver/] (level 5)
00:00:00.955   Driver <string>  = "VD" (cch=3)
00:00:00.955 
00:00:00.955 [/Devices/piix3ide/0/LUN#0/AttachedDriver/Config/] (level 6)
00:00:00.955   Path   <string>  = "/home/vietnam/.VirtualBox/HardDisks/Windows xp.vdi" (cch=51)
00:00:00.955   Format <string>  = "VDI" (cch=4)
00:00:00.955 
00:00:00.955 [/Devices/piix3ide/0/LUN#2/] (level 4)
00:00:00.955   Driver <string>  = "Block" (cch=6)
00:00:00.955 
00:00:00.955 [/Devices/piix3ide/0/LUN#2/Config/] (level 5)
00:00:00.955   Type      <string>  = "DVD" (cch=4)
00:00:00.955   Mountable <integer> = 0x0000000000000001 (1)
00:00:00.955 
00:00:00.955 [/Devices/piix3ide/0/LUN#2/AttachedDriver/] (level 5)
00:00:00.955   Driver <string>  = "MediaISO" (cch=9)
00:00:00.955 
00:00:00.955 [/Devices/piix3ide/0/LUN#2/AttachedDriver/Config/] (level 6)
00:00:00.955   Path <string>  = "/home/vietnam/.VirtualBox/VBoxGuestAdditions_2.1.4.iso" (cch=55)
00:00:00.955 
00:00:00.955 [/Devices/pcnet/] (level 2)
00:00:00.955 
00:00:00.955 [/Devices/pcnet/0/] (level 3)
00:00:00.955   Trusted       <integer> = 0x0000000000000001 (1)
00:00:00.955   PCIDeviceNo   <integer> = 0x0000000000000003 (3)
00:00:00.955   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:00.955 
00:00:00.955 [/Devices/pcnet/0/Config/] (level 4)
00:00:00.955   Am79C973       <integer> = 0x0000000000000001 (1)
00:00:00.955   MAC            <bytes>   = "08 00 27 c3 c6 fb" (cb=6)
00:00:00.955   CableConnected <integer> = 0x0000000000000001 (1)
00:00:00.955   LineSpeed      <integer> = 0x0000000000000000 (0)
00:00:00.955 
00:00:00.955 [/Devices/pcnet/0/LUN#999/] (level 4)
00:00:00.955   Driver <string>  = "MainStatus" (cch=11)
00:00:00.955 
00:00:00.955 [/Devices/pcnet/0/LUN#999/Config/] (level 5)
00:00:00.955   papLeds <integer> = 0x0000000009ffffe4 (167772132)
00:00:00.955 
00:00:00.955 [/Devices/pcnet/0/LUN#0/] (level 4)
00:00:00.955   Driver <string>  = "NAT" (cch=4)
00:00:00.955 
00:00:00.955 [/Devices/pcnet/0/LUN#0/Config/] (level 5)
00:00:00.955   TFTPPrefix <string>  = "/home/vietnam/.VirtualBox/TFTP" (cch=31)
00:00:00.955   BootFile   <string>  = "Windows xp.pxe" (cch=15)
00:00:00.955 
00:00:00.955 [/Devices/e1000/] (level 2)
00:00:00.955 
00:00:00.955 [/Devices/serial/] (level 2)
00:00:00.955 
00:00:00.955 [/Devices/parallel/] (level 2)
00:00:00.955 
00:00:00.955 [/Devices/VMMDev/] (level 2)
00:00:00.955 
00:00:00.955 [/Devices/VMMDev/0/] (level 3)
00:00:00.955   Trusted       <integer> = 0x0000000000000001 (1)
00:00:00.955   PCIDeviceNo   <integer> = 0x0000000000000004 (4)
00:00:00.955   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:00.955 
00:00:00.955 [/Devices/VMMDev/0/Config/] (level 4)
00:00:00.955 
00:00:00.955 [/Devices/VMMDev/0/LUN#0/] (level 4)
00:00:00.955   Driver <string>  = "MainVMMDev" (cch=11)
00:00:00.955 
00:00:00.955 [/Devices/VMMDev/0/LUN#0/Config/] (level 5)
00:00:00.955   Object <integer> = 0x000000000a000c98 (167775384)
00:00:00.955 
00:00:00.955 [/Devices/VMMDev/0/LUN#999/] (level 4)
00:00:00.955   Driver <string>  = "MainStatus" (cch=11)
00:00:00.955 
00:00:00.955 [/Devices/VMMDev/0/LUN#999/Config/] (level 5)
00:00:00.955   papLeds <integer> = 0x000000000a000004 (167772164)
00:00:00.956   First   <integer> = 0x0000000000000000 (0)
00:00:00.956   Last    <integer> = 0x0000000000000000 (0)
00:00:00.956 
00:00:00.956 [/Devices/AudioSniffer/] (level 2)
00:00:00.956 
00:00:00.956 [/Devices/AudioSniffer/0/] (level 3)
00:00:00.956 
00:00:00.956 [/Devices/AudioSniffer/0/Config/] (level 4)
00:00:00.956 
00:00:00.956 [/Devices/AudioSniffer/0/LUN#0/] (level 4)
00:00:00.956   Driver <string>  = "MainAudioSniffer" (cch=17)
00:00:00.956 
00:00:00.956 [/Devices/AudioSniffer/0/LUN#0/Config/] (level 5)
00:00:00.956   Object <integer> = 0x000000000a000118 (167772440)
00:00:00.956 
00:00:00.956 [/TM/] (level 1)
00:00:00.956   UTCOffset <integer> = 0x0000000000000000 (0)
00:00:00.956 
00:00:00.956 ********************* End of CFGM dump **********************
00:00:00.956 Logical host processors: 2, processor active mask: 0000000000000003
00:00:00.956 ************************* CPUID dump ************************
00:00:00.957          RAW Standard CPUIDs
00:00:00.957      Function  eax      ebx      ecx      edx
00:00:00.957 Gst: 00000000  00000002 756e6547 6c65746e 49656e69
00:00:00.957 Hst:           0000000a 756e6547 6c65746e 49656e69
00:00:00.957 Gst: 00000001  000006fb 00000800 00000009 078bf1bf
00:00:00.957 Hst:           000006fb 00020800 0000e3bd bfebfbff
00:00:00.957 Gst: 00000002  05b0b101 005657f0 00000000 2cb43049
00:00:00.957 Hst:           05b0b101 005657f0 00000000 2cb43049
00:00:00.957 Gst: 00000003  07280202 00000000 00000000 00000503*
00:00:00.957 Hst:           00000000 00000000 00000000 00000000
00:00:00.957 Gst: 00000004  00000000 00000000 00000000 00000503*
00:00:00.957 Hst:           04000121 01c0003f 0000003f 00000001
00:00:00.957 Gst: 00000005  07280202 00000000 00000000 00000503*
00:00:00.957 Hst:           00000040 00000040 00000003 00022220
00:00:00.957 Name:                            GenuineIntel
00:00:00.957 Supports:                        0-2
00:00:00.957 Family:                          6  	Extended: 0 	Effective: 6
00:00:00.957 Model:                           15  	Extended: 0 	Effective: 15
00:00:00.957 Stepping:                        11
00:00:00.957 APIC ID:                         0x00
00:00:00.957 Logical CPUs:                    0
00:00:00.957 CLFLUSH Size:                    8
00:00:00.957 Brand ID:                        0x00
00:00:00.957 Mnemonic - Description                 = guest (host)
00:00:00.957 FPU - x87 FPU on Chip                  = 1 (1)
00:00:00.957 VME - Virtual 8086 Mode Enhancements   = 1 (1)
00:00:00.957 DE - Debugging extensions              = 1 (1)
00:00:00.957 PSE - Page Size Extension              = 1 (1)
00:00:00.957 TSC - Time Stamp Counter               = 1 (1)
00:00:00.957 MSR - Model Specific Registers         = 1 (1)
00:00:00.957 PAE - Physical Address Extension       = 0 (1)
00:00:00.957 MCE - Machine Check Exception          = 1 (1)
00:00:00.957 CX8 - CMPXCHG8B instruction            = 1 (1)
00:00:00.957 APIC - APIC On-Chip                    = 0 (1)
00:00:00.957 Reserved                               = 0 (0)
00:00:00.957 SEP - SYSENTER and SYSEXIT             = 0 (1)
00:00:00.957 MTRR - Memory Type Range Registers     = 1 (1)
00:00:00.957 PGE - PTE Global Bit                   = 1 (1)
00:00:00.957 MCA - Machine Check Architecture       = 1 (1)
00:00:00.957 CMOV - Conditional Move Instructions   = 1 (1)
00:00:00.957 PAT - Page Attribute Table             = 1 (1)
00:00:00.957 PSE-36 - 36-bit Page Size Extention    = 1 (1)
00:00:00.957 PSN - Processor Serial Number          = 0 (0)
00:00:00.957 CLFSH - CLFLUSH Instruction.           = 1 (1)
00:00:00.957 Reserved                               = 0 (0)
00:00:00.957 DS - Debug Store                       = 0 (1)
00:00:00.957 ACPI - Thermal Mon. & Soft. Clock Ctrl.= 0 (1)
00:00:00.957 MMX - Intel MMX Technology             = 1 (1)
00:00:00.957 FXSR - FXSAVE and FXRSTOR Instructions = 1 (1)
00:00:00.957 SSE - SSE Support                      = 1 (1)
00:00:00.957 SSE2 - SSE2 Support                    = 1 (1)
00:00:00.957 SS - Self Snoop                        = 0 (1)
00:00:00.957 HTT - Hyper-Threading Technolog        = 0 (1)
00:00:00.957 TM - Thermal Monitor                   = 0 (1)
00:00:00.957 30 - Reserved                          = 0 (0)
00:00:00.957 PBE - Pending Break Enable             = 0 (1)
00:00:00.957 Supports SSE3 or not                   = 1 (1)
00:00:00.957 Reserved                               = 0 (2)
00:00:00.957 Supports MONITOR/MWAIT                 = 1 (1)
00:00:00.957 CPL-DS - CPL Qualified Debug Store     = 0 (1)
00:00:00.957 VMX - Virtual Machine Technology       = 0 (1)
00:00:00.957 Reserved                               = 0 (0)
00:00:00.957 Enhanced SpeedStep Technology          = 0 (1)
00:00:00.957 Terminal Monitor 2                     = 0 (1)
00:00:00.957 Supports Supplemental SSE3 or not      = 0 (1)
00:00:00.957 L1 Context ID                          = 0 (0)
00:00:00.957 Reserved                               = 0x0 (0x0)
00:00:00.957 CMPXCHG16B                             = 0 (1)
00:00:00.957 xTPR Update Control                    = 0 (1)
00:00:00.957 Reserved                               = 0x0 (0x1)
00:00:00.957 
00:00:00.957          RAW Extended CPUIDs
00:00:00.957      Function  eax      ebx      ecx      edx
00:00:00.957 Gst: 80000000  80000008 00000000 00000000 00000000
00:00:00.957 Hst:           80000008 00000000 00000000 00000000
00:00:00.957 Gst: 80000001  00000000 00000000 00000000 00000000
00:00:00.957 Hst:           00000000 00000000 00000001 20100000
00:00:00.957 Gst: 80000002  65746e49 2952286c 726f4320 4d542865
00:00:00.957 Hst:           65746e49 2952286c 726f4320 4d542865
00:00:00.957 Gst: 80000003  44203229 43206f75 20205550 54202020
00:00:00.957 Hst:           44203229 43206f75 20205550 54202020
00:00:00.957 Gst: 80000004  30303537 20402020 30322e32 007a4847
00:00:00.957 Hst:           30303537 20402020 30322e32 007a4847
00:00:00.957 Gst: 80000005  00000000 00000000 00000000 00000000
00:00:00.957 Hst:           00000000 00000000 00000000 00000000
00:00:00.957 Gst: 80000006  00000000 00000000 10008040 00000000
00:00:00.957 Hst:           00000000 00000000 10008040 00000000
00:00:00.957 Gst: 80000007  00000000 00000000 00000000 00000000
00:00:00.957 Hst:           00000000 00000000 00000000 00000000
00:00:00.957 Gst: 80000008  00003024 00000000 00000000 00000000
00:00:00.957 Hst:           00003024 00000000 00000000 00000000
00:00:00.957 Gst: 80000009  07280202 00000000 00000000 00000503*
00:00:00.957 Hst:           07280202 00000000 00000000 00000503
00:00:00.957 Ext Name:                        
00:00:00.957 Ext Supports:                    0x80000000-0x80000008
00:00:00.957 Family:                          0  	Extended: 0 	Effective: 0
00:00:00.957 Model:                           0  	Extended: 0 	Effective: 0
00:00:00.957 Stepping:                        0
00:00:00.957 Brand ID:                        0x000
00:00:00.957 Mnemonic - Description                 = guest (host)
00:00:00.957 FPU - x87 FPU on Chip                  = 0 (0)
00:00:00.957 VME - Virtual 8086 Mode Enhancements   = 0 (0)
00:00:00.957 DE - Debugging extensions              = 0 (0)
00:00:00.957 PSE - Page Size Extension              = 0 (0)
00:00:00.957 TSC - Time Stamp Counter               = 0 (0)
00:00:00.957 MSR - K86 Model Specific Registers     = 0 (0)
00:00:00.957 PAE - Physical Address Extension       = 0 (0)
00:00:00.957 MCE - Machine Check Exception          = 0 (0)
00:00:00.957 CX8 - CMPXCHG8B instruction            = 0 (0)
00:00:00.957 APIC - APIC On-Chip                    = 0 (0)
00:00:00.957 10 - Reserved                          = 0 (0)
00:00:00.957 SEP - SYSCALL and SYSRET               = 0 (0)
00:00:00.957 MTRR - Memory Type Range Registers     = 0 (0)
00:00:00.957 PGE - PTE Global Bit                   = 0 (0)
00:00:00.957 MCA - Machine Check Architecture       = 0 (0)
00:00:00.957 CMOV - Conditional Move Instructions   = 0 (0)
00:00:00.957 PAT - Page Attribute Table             = 0 (0)
00:00:00.957 PSE-36 - 36-bit Page Size Extention    = 0 (0)
00:00:00.957 18 - Reserved                          = 0 (0)
00:00:00.957 19 - Reserved                          = 0 (0)
00:00:00.957 NX - No-Execute Page Protection        = 0 (1)
00:00:00.957 DS - Debug Store                       = 0 (0)
00:00:00.957 AXMMX - AMD Extensions to MMX Instr.   = 0 (0)
00:00:00.957 MMX - Intel MMX Technology             = 0 (0)
00:00:00.957 FXSR - FXSAVE and FXRSTOR Instructions = 0 (0)
00:00:00.957 25 - AMD fast FXSAVE and FXRSTOR Instr.= 0 (0)
00:00:00.957 26 - 1 GB large page support           = 0 (0)
00:00:00.957 27 - RDTSCP instruction                = 0 (0)
00:00:00.957 28 - Reserved                          = 0 (0)
00:00:00.957 29 - AMD Long Mode                     = 0 (1)
00:00:00.957 30 - AMD Extensions to 3DNow           = 0 (0)
00:00:00.957 31 - AMD 3DNow                         = 0 (0)
00:00:00.957 LahfSahf - LAHF/SAHF in 64-bit mode    = 0 (1)
00:00:00.957 CmpLegacy - Core MP legacy mode (depr) = 0 (0)
00:00:00.957 SVM - AMD VM Extensions                = 0 (0)
00:00:00.957 APIC registers starting at 0x400       = 0 (0)
00:00:00.957 AltMovCR8 - LOCK MOV CR0 means MOV CR8 = 0 (0)
00:00:00.957 Advanced bit manipulation              = 0 (0)
00:00:00.957 SSE4A instruction support              = 0 (0)
00:00:00.957 Misaligned SSE mode                    = 0 (0)
00:00:00.957 PREFETCH and PREFETCHW instruction     = 0 (0)
00:00:00.957 OS visible workaround                  = 0 (0)
00:00:00.957 Instruction based sampling             = 0 (0)
00:00:00.957 SSE5 support                           = 0 (0)
00:00:00.957 SKINIT, STGI, and DEV support          = 0 (0)
00:00:00.957 Watchdog timer support.                = 0 (0)
00:00:00.957 31:14 - Reserved                       = 0x0 (0x0)
00:00:00.957 Full Name:                       Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz
00:00:00.957 TLB 2/4M Instr/Uni:              res0     0 entries
00:00:00.957 TLB 2/4M Data:                   res0     0 entries
00:00:00.957 TLB 4K Instr/Uni:                res0     0 entries
00:00:00.957 TLB 4K Data:                     res0     0 entries
00:00:00.957 L1 Instr Cache Line Size:        0 bytes
00:00:00.957 L1 Instr Cache Lines Per Tag:    0
00:00:00.957 L1 Instr Cache Associativity:    res0  
00:00:00.957 L1 Instr Cache Size:             0 KB
00:00:00.957 L1 Data Cache Line Size:         0 bytes
00:00:00.957 L1 Data Cache Lines Per Tag:     0
00:00:00.957 L1 Data Cache Associativity:     res0  
00:00:00.957 L1 Data Cache Size:              0 KB
00:00:00.957 L2 TLB 2/4M Instr/Uni:           off       0 entries
00:00:00.957 L2 TLB 2/4M Data:                off       0 entries
00:00:00.957 L2 TLB 4K Instr/Uni:             off       0 entries
00:00:00.957 L2 TLB 4K Data:                  off       0 entries
00:00:00.957 L2 Cache Line Size:              0 bytes
00:00:00.957 L2 Cache Lines Per Tag:          0
00:00:00.957 L2 Cache Associativity:          off   
00:00:00.957 L2 Cache Size:                   0 KB
00:00:00.957 APM Features:                   
00:00:00.957 Physical Address Width:          36 bits
00:00:00.957 Virtual Address Width:           48 bits
00:00:00.957 Physical Core Count:             0
00:00:00.957 
00:00:00.957          RAW Centaur CPUIDs
00:00:00.957      Function  eax      ebx      ecx      edx
00:00:00.957 Gst: c0000000  07280202 00000000 00000000 00000503
00:00:00.957 Hst:           07280202 00000000 00000000 00000503
00:00:00.957 Gst: c0000001  07280202 00000000 00000000 00000503
00:00:00.957 Hst:           07280202 00000000 00000000 00000503
00:00:00.957 Gst: c0000002  07280202 00000000 00000000 00000503
00:00:00.957 Hst:           07280202 00000000 00000000 00000503
00:00:00.957 Gst: c0000003  07280202 00000000 00000000 00000503
00:00:00.957 Hst:           07280202 00000000 00000000 00000503
00:00:00.957 Centaur Supports:                0xc0000000-0x07280202
00:00:00.957 Mnemonic - Description                 = guest (host)
00:00:00.957 AIS - Alternate Instruction Set        = 0 (1)
00:00:00.957 AIS-E - AIS enabled                    = 0 (1)
00:00:00.957 RNG - Random Number Generator          = 0 (0)
00:00:00.957 RNG-E - RNG enabled                    = 0 (0)
00:00:00.957 LH - LongHaul MSR 0000_110Ah           = 0 (0)
00:00:00.957 FEMMS - FEMMS                          = 0 (0)
00:00:00.957 ACE - Advanced Cryptography Engine     = 0 (0)
00:00:00.957 ACE-E - ACE enabled                    = 0 (0)
00:00:00.957 ACE2 - Advanced Cryptography Engine 2  = 0 (1)
00:00:00.957 ACE2-E - ACE enabled                   = 0 (0)
00:00:00.957 PHE - Hash Engine                      = 0 (1)
00:00:00.957 PHE-E - PHE enabled                    = 0 (0)
00:00:00.957 PMM - Montgomery Multiplier            = 0 (0)
00:00:00.957 PMM-E - PMM enabled                    = 0 (0)
00:00:00.957 
00:00:00.957 
00:00:00.957 ******************** End of CPUID dump **********************
00:00:00.977 REM: VBoxREM32
00:00:00.985 TM: GIP - u32Mode=1 (SyncTSC) u32UpdateHz=83
00:00:01.020 TM: cTSCTicksPerSecond=0xb8ea787 (193898375) fTSCVirtualized=true  fTSCUseRealTSC=false
00:00:01.020 TM: fMaybeUseOffsettedHostTSC=true  TSCTiedToExecution=false TSCNotTiedToHalt=false
00:00:01.020 CoreCode: R3=b3e7d000 R0=f84ae000 RC=a03ac000 Phys=00000000083f2000 cb=0x2000
00:00:01.108 SUP: Loaded VBoxDDR0.r0 (/usr/lib/virtualbox/VBoxDDR0.r0) at 0xf84b6060 - ModuleInit at 0000000000000000 and ModuleTerm at 0000000000000000
00:00:01.124 SUP: Loaded VBoxDD2R0.r0 (/usr/lib/virtualbox/VBoxDD2R0.r0) at 0xf84d4060 - ModuleInit at 0000000000000000 and ModuleTerm at 0000000000000000
00:00:01.124 Activating Local APIC
00:00:01.124 CPUMSetGuestCpuIdFeature: Enabled APIC
00:00:01.124 CPUMSetGuestCpuIdFeature: Disabled x2APIC
00:00:01.125 PIT: mode=3 count=0x10000 (65536) - 18.20 Hz (ch=0)
00:00:01.145 Shared Folders service loaded.
00:00:01.164 VDInit finished
00:00:01.164 PIIX3 ATA: LUN#0: disk, PCHS=12570/16/63, total number of sectors 12670976
00:00:01.164 PIIX3 ATA: LUN#1: no unit
00:00:01.164 PIIX3 ATA: LUN#2: CD/DVD, total number of sectors 9466, passthrough disabled
00:00:01.164 PIIX3 ATA: LUN#3: no unit
00:00:01.164 PIIX3 ATA: Ctl#0: finished processing RESET
00:00:01.263 PIIX3 ATA: Ctl#1: finished processing RESET
00:00:01.358 NAT: DNS address: 193.19.192.15
00:00:01.358 NAT: ignored DNS address: 193.19.192.16
00:00:01.371 DevPcBios: ATA LUN#0 LCHS=788/255/63
00:00:01.372 PGMR3InitFinalize: 4 MB PSE mask 0000000fffffffff
00:00:01.463 VM: Halt method global1 (5)
00:00:01.464 Changing the VM state from 'CREATING' to 'CREATED'.
00:00:01.464 Changing the VM state from 'CREATED' to 'RUNNING'.
00:00:01.485 Guest Log: BIOS: VirtualBox 2.1.4_OSE
00:00:01.487 PIT: mode=2 count=0x10000 (65536) - 18.20 Hz (ch=0)
00:00:01.578 PIIX3 ATA: Ctl#0: RESET, DevSel=0 AIOIf=0 CmdIf0=0x00 (-1 usec ago) CmdIf1=0x00 (-1 usec ago)
00:00:01.579 PIIX3 ATA: Ctl#0: finished processing RESET
00:00:01.584 Guest Log: BIOS: ata0-0: PCHS=12570/16/63 LCHS=788/255/63
00:00:01.587 PIIX3 ATA: Ctl#1: RESET, DevSel=0 AIOIf=0 CmdIf0=0x00 (-1 usec ago) CmdIf1=0x00 (-1 usec ago)
00:00:01.587 PIIX3 ATA: Ctl#1: finished processing RESET
00:00:01.589 PIT: mode=2 count=0x48d3 (18643) - 64.00 Hz (ch=0)
00:00:01.596 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=b2a3f000 w=640 h=480 bpp=32 cbLine=0xA00
00:00:04.093 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=00000000 w=720 h=400 bpp=0 cbLine=0x0
00:00:04.094 PIT: mode=2 count=0x10000 (65536) - 18.20 Hz (ch=0)
00:00:04.100 Guest Log: BIOS: Boot from Floppy 0 failed
00:00:04.116 Guest Log: BIOS: CDROM boot failure code : 0004
00:00:04.116 Guest Log: BIOS: Boot from CD-ROM failed
00:00:04.119 Guest Log: BIOS: Booting from Hard Disk...
00:00:04.558 Guest Log: BIOS: int13_harddisk: function 15, unmapped device for ELDL=81
00:00:08.441 PIT: mode=2 count=0x2ead (11949) - 99.85 Hz (ch=0)
00:00:08.640 CPUMSetGuestCpuIdFeature: Disabled x2APIC
00:00:08.673 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=b2a3f000 w=640 h=480 bpp=0 cbLine=0x140
00:00:10.093 PIIX3 ATA: LUN#0: IDLE IMMEDIATE, CmdIf=0xef (-1 usec ago)
00:00:10.093 PIIX3 ATA: LUN#0: aborting current command
00:00:11.205 Guest Additions information report: additionsVersion = 0x00010004  osType = 0x00033000
00:00:11.316 Guest reported fixed hypervisor window at 0xf7400000 (size = 0x800000, rc = VINF_SUCCESS)
00:00:12.079 Guest requests mouse pointer integration
00:00:13.506 Guest adapter information contains unsupported type 5. The block has been skipped.
00:00:14.099 SharedFolders host service: connected, u32ClientID = 1
00:00:14.277 PATM: Disable block at 81ecbb5c - write 81ecbccf-81ecbcd3
00:00:17.117 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=b2a3f000 w=640 h=480 bpp=32 cbLine=0xA00
00:00:17.118 VBVA: Enabled.
00:00:22.249 Guest Log: VBoxService: Started.
00:00:36.079 Guest Log: VBoxTray: Started.
00:00:36.436 Guest Additions capability report: (0x5) seamless: yes, hostWindowMapping: no, graphics: yes
00:01:06.877 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=b2a3f000 w=800 h=600 bpp=32 cbLine=0xC80
00:01:06.878 VBVA: Disabled.
00:01:06.882 VBVA: Enabled.
00:01:30.970 Guest Log: VBOXNP: DLL loaded.
00:02:57.105 Changing the VM state from 'RUNNING' to 'SUSPENDED'.
00:02:57.110 Changing the VM state from 'SUSPENDED' to 'RUNNING'.
00:03:06.421 NAT: link down
00:03:08.437 NAT: link up
00:04:18.784 Guest Log: VBOXNP: DLL loaded.
00:04:26.821 Changing the VM state from 'RUNNING' to 'SUSPENDED'.
00:04:26.821 PIIX3 ATA: LUN#2: CD/DVD, total number of sectors 2182528, passthrough disabled
00:04:26.821 Changing the VM state from 'SUSPENDED' to 'RUNNING'.
00:18:43.456 PIT: mode=2 count=0x4ad (1197) - 996.81 Hz (ch=0)
00:18:53.569 PIT: mode=2 count=0x2ead (11949) - 99.85 Hz (ch=0)


---

