---
title: "PSTN/FXO PCIe Passthru error...other passthrough still works fine :-("
date: 2015-10-21
forum: Virtualisation
---

### Post by KillerKelvUK on 2015-10-21
Okay so I've already successfully passed through an nVidia GTX 650 to a windows guest, although I don't use this now.  I also pass through a DVBSky S2 card to a linux guest for my sat stuff.  Today arrived my new OpenVox PCIe with 1x FXO card...basically so I can connect to my phone line and run a small PBX/SIP telephony switch.  However I'm getting something I've not seen before when attempting to passthrough the card and would appreciate any pointers...

Host:  ASRock z97 || Ubuntu 15.04 || Kernel 3.19.30 (acs patched) || Intel IGP which isn't used || nVidia GTX 650 for host gfx || DVB-S2 Sat card for vm guest

Without acs patching my kernel iommu is impossible aka lots of devices combined in groups.  Post patching my group separation is good and allows my DVB card (currently the only device in passthrough) shown in IOMMU group 19 below so all is good.  The new card however shows in group 20 along with 1 other device...I've swapped the PCIe slots the DVB card and the OpenVox card use, the DVB always remains the only device in a group but the OpenVox card is always combined with the ASMedia device.  The error message I get when starting the guest isn't what I would expect if this was an IOMMU separation problem, the key bit of the error I'm homing in on is "vfio: Error: Failed to setup INTx fd: Device or resource busy".


[LIST=1]
[*]Can anyone help me understand the purpose of the other device in the IOMMU group along with the OpenVox card?
[*]What does the error message mean?
[*]Any suggestions for how I might work through this problem to pass the OpenVox through to my VM?
[/LIST]

Thanks

K

The error message I get when starting the guest is...

```

Error starting domain: internal error: early end of file from monitor: possible problem:
2015-10-21T19:40:58.092552Z qemu-system-x86_64: -device vfio-pci,host=09:00.0,id=hostdev0,bus=pci.0,addr=0x9: vfio: Error: Failed to setup INTx fd: Device or resource busy
2015-10-21T19:40:58.092892Z qemu-system-x86_64: -device vfio-pci,host=09:00.0,id=hostdev0,bus=pci.0,addr=0x9: Device initialization failed
2015-10-21T19:40:58.092943Z qemu-system-x86_64: -device vfio-pci,host=09:00.0,id=hostdev0,bus=pci.0,addr=0x9: Device 'vfio-pci' could not be initialized




Traceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/asyncjob.py", line 89, in cb_wrapper
    callback(asyncjob, *args, **kwargs)
  File "/usr/share/virt-manager/virtManager/asyncjob.py", line 125, in tmpcb
    callback(*args, **kwargs)
  File "/usr/share/virt-manager/virtManager/libvirtobject.py", line 83, in newfn
    ret = fn(self, *args, **kwargs)
  File "/usr/share/virt-manager/virtManager/domain.py", line 1433, in startup
    self._backend.create()
  File "/usr/lib/python2.7/dist-packages/libvirt.py", line 1029, in create
    if ret == -1: raise libvirtError ('virDomainCreate() failed', dom=self)
libvirtError: internal error: early end of file from monitor: possible problem:
2015-10-21T19:40:58.092552Z qemu-system-x86_64: -device vfio-pci,host=09:00.0,id=hostdev0,bus=pci.0,addr=0x9: vfio: Error: Failed to setup INTx fd: Device or resource busy
2015-10-21T19:40:58.092892Z qemu-system-x86_64: -device vfio-pci,host=09:00.0,id=hostdev0,bus=pci.0,addr=0x9: Device initialization failed
2015-10-21T19:40:58.092943Z qemu-system-x86_64: -device vfio-pci,host=09:00.0,id=hostdev0,bus=pci.0,addr=0x9: Device 'vfio-pci' could not be initialized

```

New card is...

```

09:00.0 Network controller: Tiger Jet Network Inc. Tiger3XX Modem/ISDN interface
    Subsystem: OpenVox Communication Co. Ltd. Device 0001
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin A routed to IRQ 16
    Region 0: I/O ports at c000 [disabled] [size=256]
    Region 1: Memory at ef100000 (32-bit, non-prefetchable) [disabled] [size=4K]
    Capabilities: [40] Power Management version 2
        Flags: PMEClk- DSI+ D1- D2+ AuxCurrent=55mA PME(D0+,D1-,D2+,D3hot+,D3cold+)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Kernel driver in use: pci-stub

```

IOMMU groups are...

```

### Group 0 ###
    00:00.0 Host bridge: Intel Corporation 4th Gen Core Processor DRAM Controller (rev 06)
### Group 1 ###
    00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)
### Group 2 ###
    00:01.1 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x8 Controller (rev 06)
### Group 3 ###
    00:14.0 USB controller: Intel Corporation 9 Series Chipset Family USB xHCI Controller
### Group 4 ###
    00:16.0 Communication controller: Intel Corporation 9 Series Chipset Family ME Interface #1
### Group 5 ###
    00:19.0 Ethernet controller: Intel Corporation Ethernet Connection (2) I218-V
### Group 6 ###
    00:1a.0 USB controller: Intel Corporation 9 Series Chipset Family USB EHCI Controller #2
### Group 7 ###
    00:1b.0 Audio device: Intel Corporation 9 Series Chipset Family HD Audio Controller
### Group 8 ###
    00:1c.0 PCI bridge: Intel Corporation 9 Series Chipset Family PCI Express Root Port 1 (rev d0)
### Group 9 ###
    00:1c.2 PCI bridge: Intel Corporation 9 Series Chipset Family PCI Express Root Port 3 (rev d0)
### Group 10 ###
    00:1c.3 PCI bridge: Intel Corporation 9 Series Chipset Family PCI Express Root Port 4 (rev d0)
### Group 11 ###
    00:1c.6 PCI bridge: Intel Corporation 9 Series Chipset Family PCI Express Root Port 7 (rev d0)
### Group 12 ###
    00:1d.0 USB controller: Intel Corporation 9 Series Chipset Family USB EHCI Controller #1
### Group 13 ###
    00:1f.0 ISA bridge: Intel Corporation 9 Series Chipset Family Z97 LPC Controller
    00:1f.2 SATA controller: Intel Corporation 9 Series Chipset Family SATA Controller [AHCI Mode]
    00:1f.3 SMBus: Intel Corporation 9 Series Chipset Family SMBus Controller
### Group 14 ###
    02:00.0 VGA compatible controller: NVIDIA Corporation GK106 [GeForce GTX 650 OEM] (rev a1)
    02:00.1 Audio device: NVIDIA Corporation GK106 HDMI Audio Controller (rev a1)
### Group 15 ###
    04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 11)
### Group 16 ###
    05:00.0 PCI bridge: ASMedia Technology Inc. Device 1184
### Group 17 ###
    06:01.0 PCI bridge: ASMedia Technology Inc. Device 1184
### Group 18 ###
    06:05.0 PCI bridge: ASMedia Technology Inc. Device 1184
### Group 19 ###
    07:00.0 Multimedia video controller: Spin Master Ltd. Device 3038 (rev 01)
### Group 20 ###
    08:00.0 PCI bridge: ASMedia Technology Inc. ASM1083/1085 PCIe to PCI Bridge (rev 03)
    09:00.0 Network controller: Tiger Jet Network Inc. Tiger3XX Modem/ISDN interface
### Group 21 ###
    0a:00.0 USB controller: ASMedia Technology Inc. ASM1042A USB 3.0 Host Controller

```

---

### Post by KillerKelvUK on 2015-10-25
So I managed to solve my own problem after hours of googling...

It looks like my new PCIe device doesn't support PCI2.3 INTx disable, the card was using interrupt 16 but so was a USB 2.0 controller.  From what I understand without the INTx feature the entire interrupt needs dedicating to the passthrough device so I located the usb controller in /sys/bus/usb/... and echo'd a 1 into the 'remove' parameter which detached the device from the driver.  This then allowed my vm to boot with the new PCIe card passed through as intended, early testing shows this is functional...the only downside is that this solution removes 2 usb ports from my host.

New/better compatible hardware required i think.

Links I found useful for the above...

[http://kvm.vger.kernel.narkive.com/th801MQF/genirq-flags-mismatch-irq-17-00000000-vfio-intx-0000-07-04-0-vs-00000000-vfio-intx-0000-01-00-1](http://kvm.vger.kernel.narkive.com/th801MQF/genirq-flags-mismatch-irq-17-00000000-vfio-intx-0000-07-04-0-vs-00000000-vfio-intx-0000-01-00-1)
[https://bbs.archlinux.org/viewtopic.php?id=162768&p=40](https://bbs.archlinux.org/viewtopic.php?id=162768&p=40)

---

### Post by Guilherme_Gentile on 2015-11-18
Hello Kelv, can you please tell me exactly what you've done, I think Im having the same problem!

I look forward hearing from you!

---

### Post by KillerKelvUK on 2015-11-19
Sure.

First I pulled this [ATTACH]265681[/ATTACH] from a mailing list which I think is from one of the main redhat devs coding vfio and other virt services, it basically shows you if the pci device support [COLOR=#000000]PCI2.3 INTx disable or not.  (think you need to run with elevated privs i.e. sudo).[/COLOR]

[COLOR=#000000]For me I confirmed my card was affected using the above, then looked at what devices were using which interrupts by looking at the contents of **/proc/interrupts**, in my case there was a usb port assigned to int 16 which was the point of conflict with my new passthrough card.  What you do here can vary I believe i.e. you could attempt to move the PCI cards around into different slots which could reshuffle the interrupt assignments to free up whichever interrupt your passthrough card was to use exclusively.  Some other posts suggest the UEFI/BIOS may offer an ability to set which interrupts are assigned to devices...unfortunately these didn't work or apply for me so my only remaining recourse was to try and detach the conflicting usb port from the system.

So for me, as root (sudo su) I located the offending usb port device in /sys/devices/pci0000:00/... and echo'd a 1 into remove, so basically this...

[/COLOR]**[COLOR=#000000]echo -n 1 > [/COLOR]"[COLOR=#000000]/sys/devices/pci0000:00/0000:00:1a.0/remove" [/COLOR]**[COLOR=#000000](0000:00:1a.0 being the usb port/device)
[/COLOR][COLOR=#000000]
This effectively detaches the USB port itself which stops it using the interrupt that the passthrough card needs to dedicate to itself.  I located the /sys/device item by grepping the dmesg output for the usb port.

Hope that helps.[/COLOR]

---

