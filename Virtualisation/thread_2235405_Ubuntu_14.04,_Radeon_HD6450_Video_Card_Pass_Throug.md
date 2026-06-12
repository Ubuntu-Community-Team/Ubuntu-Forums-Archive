---
title: "Ubuntu 14.04, Radeon HD6450 Video Card Pass Through Using ESXi 5.5"
date: 2014-07-20
forum: Virtualisation
---

### Post by kirk2 on 2014-07-20
About to go nuts with this.  I have an Ubuntu 14.04 Desktop VM that I'm trying to pass an Asus HD6450 video card through and get working.  I've tried just about every suggestion I can think of and find on the net and have had to install this system 5-6 this weekend alone.  Use the Ubuntu drivers, the ATI drivers, nothing.   Not sure where else to go with this.

Hardware specs:
[LIST]
[*]AsRock 970 Extreme3 R2.0 mobo 
[*]AMD FX-8320 CPU 
[*]32gb on the host 2gb allocated to this Ubuntu VM. 
[*]Asus HD6450 Silent video card 
[/LIST]

Pass through seems to be working as I have USB controllers and such working fine.  I just can't get this video card to work.

```
[    8.154236] radeon 0000:03:00.0: enabling device (0000 -> 0003)
[    8.158126] [drm] initializing kernel modesetting (CAICOS 0x1002:0x6779 0x1043:0x0483).
[    8.158156] [drm] register mmio base: 0xD3F00000
[    8.158159] [drm] register mmio size: 131072
[    8.158199] radeon 0000:03:00.0: BAR 6: can't assign [??? 0x00000000 flags 0x0] (bogus alignment)
[    8.158214] radeon 0000:03:00.0: BAR 6: can't assign [??? 0x00000000 flags 0x0] (bogus alignment)
[    8.158218] [drm:radeon_get_bios] *ERROR* Unable to locate a BIOS ROM
[    8.158251] radeon 0000:03:00.0: Fatal error during GPU init
[    8.158276] [drm] radeon: finishing device.
[    8.200757] radeon: probe of 0000:03:00.0 failed with error -22

```

In the gpu-manager.log:

```

Vendor/Device Id: 1002:6779
BusID "PCI:3@0:0:0"
Is boot vga? no
Error: can't access /sys/bus/pci/devices/0000:03:00.0/driver
The device is not bound to any driver. Skipping...
I couldn't open /var/lib/ubuntu-drivers-common/last_gfx_boot for reading.
Create /var/lib/ubuntu-drivers-common/last_gfx_boot for the 1st time
last cards number = 1
Has amd? no
Has intel? no
Has nvidia? no
How many cards? 1
Has the system changed? Yes
main_arch_path x86_64-linux-gnu, other_arch_path i386-linux-gnu
Current alternative: /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf
Is nvidia enabled? no
Is fglrx enabled? no
Is mesa enabled? yes
Is pxpress enabled? no
Is prime enabled? no
Is nvidia available? no
Is fglrx available? no
Is mesa available? yes
Is pxpress available? no
Is prime available? no
System configuration has changed
Single card detected
System configuration has changed
Removing xorg.conf. Path: /etc/X11/xorg.conf
Moved /etc/X11/xorg.conf to /etc/X11/xorg.conf.07202014

```

lspci -nn output:

```

00:00.0 Host bridge [0600]: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge [8086:7190] (rev 01)
00:01.0 PCI bridge [0604]: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge [8086:7191] (rev 01)
00:07.0 ISA bridge [0601]: Intel Corporation 82371AB/EB/MB PIIX4 ISA [8086:7110] (rev 08)
00:07.1 IDE interface [0101]: Intel Corporation 82371AB/EB/MB PIIX4 IDE [8086:7111] (rev 01)
00:07.3 Bridge [0680]: Intel Corporation 82371AB/EB/MB PIIX4 ACPI [8086:7113] (rev 08)
00:07.7 System peripheral [0880]: VMware Virtual Machine Communication Interface [15ad:0740] (rev 10)
00:0f.0 VGA compatible controller [0300]: VMware SVGA II Adapter [15ad:0405]
00:10.0 SCSI storage controller [0100]: LSI Logic / Symbios Logic 53c1030 PCI-X Fusion-MPT Dual Ultra320 SCSI [1000:0030] (rev 01)
00:11.0 PCI bridge [0604]: VMware PCI bridge [15ad:0790] (rev 02)
00:15.0 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:15.1 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:15.2 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:15.3 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:15.4 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:15.5 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:15.6 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:15.7 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:16.0 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:16.1 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:16.2 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:16.3 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:16.4 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:16.5 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:16.6 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:16.7 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:17.0 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:17.1 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:17.2 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:17.3 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:17.4 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:17.5 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:17.6 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:17.7 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:18.0 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:18.1 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:18.2 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:18.3 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:18.4 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:18.5 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:18.6 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:18.7 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
02:00.0 USB controller [0c03]: VMware USB1.1 UHCI Controller [15ad:0774]
02:01.0 USB controller [0c03]: VMware USB2 EHCI Controller [15ad:0770]
03:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Caicos [Radeon HD 6450/7450/8450 / R5 230 OEM] [1002:6779]
03:00.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Caicos HDMI Audio [Radeon HD 6400 Series] [1002:aa98]
13:00.0 USB controller [0c03]: VIA Technologies, Inc. VL80x xHCI USB 3.0 Controller [1106:3432] (rev 03)
1b:00.0 Ethernet controller [0200]: VMware VMXNET3 Ethernet Controller [15ad:07b0] (rev 01)

```

---

### Post by TheFu on 2014-07-22
I wouldn't expect ESXi video passthru to work - probably just my limited imagination, I dunno. It is a server VM hypervisor, not a desktop system.  

Googling "esxi video passthru" showed lots of people trying. It is unclear to me if anyone got it working.

For desktop-on-desktop virtualization, there are other tools.  I think this is a "I have a hammer, everything is a nail" thing, even when there aren't any nails.  I've read here about folks getting Xen working with specific videocard passthru for Windows gaming.  For Linux desktops, I'm inclined to use Spice for remote, low-latency, video needs.

---

### Post by kirk2 on 2014-07-23
> **TheFu said:**
> I wouldn't expect ESXi video passthru to work - probably just my limited imagination, I dunno. It is a server VM hypervisor, not a desktop system.  

Googling "esxi video passthru" showed lots of people trying. It is unclear to me if anyone got it working.

For desktop-on-desktop virtualization, there are other tools.  I think this is a "I have a hammer, everything is a nail" thing, even when there aren't any nails.  I've read here about folks getting Xen working with specific videocard passthru for Windows gaming.  For Linux desktops, I'm inclined to use Spice for remote, low-latency, video needs.

It is very possible to get it to work.  A guy has a site dedicated to doing several of these setups using the same hardware I'm using:  [http://thehomeserverblog.com/](http://thehomeserverblog.com/)

I don't have a "driver" file in the PCI directory for some reason.  It doesn't matter how I try to install software to get it there.
 - Error: can't access /sys/bus/pci/devices/0000:03:00.0/driver
 - The device is not bound to any driver. Skipping...

Anyone else have suggestions?  I'm at my wits end here.

---

### Post by matt133 on 2014-08-13
> **kirk2 said:**
> It is very possible to get it to work.  A guy has a site dedicated to doing several of these setups using the same hardware I'm using:  [http://thehomeserverblog.com/](http://thehomeserverblog.com/)

I don't have a "driver" file in the PCI directory for some reason.  It doesn't matter how I try to install software to get it there.
 - Error: can't access /sys/bus/pci/devices/0000:03:00.0/driver
 - The device is not bound to any driver. Skipping...

Anyone else have suggestions?  I'm at my wits end here.

Did you ever find a solution to your problem? I had the same problem as yourself with the same looking output and logging, but since then I've been too busy at work.

---

### Post by kayrune on 2014-08-24
issue is discussed here [https://communities.vmware.com/thread/297072?start=720&tstart=0](https://communities.vmware.com/thread/297072?start=720&tstart=0) , there is a workaround that involves compiling kernel.

this is probably the bios file you need ? [http://www.techpowerup.com/vgabios/102255/asus-hd6450-1024-110316.html](http://www.techpowerup.com/vgabios/102255/asus-hd6450-1024-110316.html)


If I remember corretly the regression started with ubuntu 13.10, it was working fine before that.

---

### Post by mitt2 on 2015-01-13
> **kayrune said:**
> issue is discussed here [https://communities.vmware.com/thread/297072?start=720&tstart=0](https://communities.vmware.com/thread/297072?start=720&tstart=0) , there is a workaround that involves compiling kernel.

this is probably the bios file you need ? [http://www.techpowerup.com/vgabios/102255/asus-hd6450-1024-110316.html](http://www.techpowerup.com/vgabios/102255/asus-hd6450-1024-110316.html)


If I remember corretly the regression started with ubuntu 13.10, it was working fine before that.


Hi,
unfortunately I'm faceing the same issue.

I already downloaded the (probably) correct bios file and put it in [COLOR=#666666][FONT=arial]/lib/firmware/radeon/vbios.bin

The kernel seems to be already patched, so i decided to not download and compile/install it again. Is this correct?
Nevertheless, also with the correct vbios.bin file and disabled VMWare SVGA Driver my Desktop Screen doesnt show up.

Any advice would be really great :)
[/FONT][/COLOR]

---

### Post by worthlutz on 2015-01-23
Did any one figure this out?  I'm just getting started and having the same error.

---

