---
title: "AR9285 Not showing but wired connection working without being plugged in"
date: 2016-10-08
forum: Virtualisation
---

### Post by msriptide on 2016-10-08
Hi,
I've got a really strange problem with my Ath AR9285. I'm really new to linux and Ubuntu (using a VMware) so you may have to give me a few prompts
Current its showing that i have a wired connection via ubuntu but i've only got my computer setup wirelessly.
the internet works within ubuntu but it currently won't find anything to do with wireless.
my lspci output doesn't even show the wireless card within it.
```
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 01)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 01)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 08)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 08)
00:07.7 System peripheral: VMware Virtual Machine Communication Interface (rev 10)
00:0f.0 VGA compatible controller: VMware SVGA II Adapter
00:10.0 SCSI storage controller: LSI Logic / Symbios Logic 53c1030 PCI-X Fusion-MPT Dual Ultra320 SCSI (rev 01)
00:11.0 PCI bridge: VMware PCI bridge (rev 02)
00:15.0 PCI bridge: VMware PCI Express Root Port (rev 01)
00:15.1 PCI bridge: VMware PCI Express Root Port (rev 01)
00:15.2 PCI bridge: VMware PCI Express Root Port (rev 01)
00:15.3 PCI bridge: VMware PCI Express Root Port (rev 01)
00:15.4 PCI bridge: VMware PCI Express Root Port (rev 01)
00:15.5 PCI bridge: VMware PCI Express Root Port (rev 01)
00:15.6 PCI bridge: VMware PCI Express Root Port (rev 01)
00:15.7 PCI bridge: VMware PCI Express Root Port (rev 01)
00:16.0 PCI bridge: VMware PCI Express Root Port (rev 01)
00:16.1 PCI bridge: VMware PCI Express Root Port (rev 01)
00:16.2 PCI bridge: VMware PCI Express Root Port (rev 01)
00:16.3 PCI bridge: VMware PCI Express Root Port (rev 01)
00:16.4 PCI bridge: VMware PCI Express Root Port (rev 01)
00:16.5 PCI bridge: VMware PCI Express Root Port (rev 01)
00:16.6 PCI bridge: VMware PCI Express Root Port (rev 01)
00:16.7 PCI bridge: VMware PCI Express Root Port (rev 01)
00:17.0 PCI bridge: VMware PCI Express Root Port (rev 01)
00:17.1 PCI bridge: VMware PCI Express Root Port (rev 01)
00:17.2 PCI bridge: VMware PCI Express Root Port (rev 01)
00:17.3 PCI bridge: VMware PCI Express Root Port (rev 01)
00:17.4 PCI bridge: VMware PCI Express Root Port (rev 01)
00:17.5 PCI bridge: VMware PCI Express Root Port (rev 01)
00:17.6 PCI bridge: VMware PCI Express Root Port (rev 01)
00:17.7 PCI bridge: VMware PCI Express Root Port (rev 01)
00:18.0 PCI bridge: VMware PCI Express Root Port (rev 01)
00:18.1 PCI bridge: VMware PCI Express Root Port (rev 01)
00:18.2 PCI bridge: VMware PCI Express Root Port (rev 01)
00:18.3 PCI bridge: VMware PCI Express Root Port (rev 01)
00:18.4 PCI bridge: VMware PCI Express Root Port (rev 01)
00:18.5 PCI bridge: VMware PCI Express Root Port (rev 01)
00:18.6 PCI bridge: VMware PCI Express Root Port (rev 01)
00:18.7 PCI bridge: VMware PCI Express Root Port (rev 01)
02:00.0 USB controller: VMware USB1.1 UHCI Controller
02:01.0 Ethernet controller: Advanced Micro Devices, Inc. [AMD] 79c970 [PCnet32 LANCE] (rev 10)
02:02.0 Multimedia audio controller: Ensoniq ES1371 / Creative Labs CT2518/ES1373 (rev 02)
02:03.0 USB controller: VMware USB2 EHCI Controller
02:05.0 SATA controller: VMware SATA AHCI controller
```

I've been searching for two days to get this working and have tried a few different things, someone said about updating the drivers. i thought i had but if someone can give me the path to the apt as all the others i tried couldn't be found (lots of old posts) 
if anyone can help me as im about to pull my hair out!

Thanks
ms

---

### Post by jeremy31 on 2016-10-08
With VMWare, I don't think you can control PCI wireless from the guest OS and the VM creates some virtual bridge to the guest OS as an ethernet and that is why you have an ethernet connection in the guest without a cable connected

---

### Post by msriptide on 2016-10-08
Thanks for the quick reply, 
Is there anyway i can get my wireless connection up then? Even if i need to download a different VM as i really wanted to be able to put it into monitor mode, at the moment i don't even get a WLAN to change

---

### Post by jeremy31 on 2016-10-08
That I do not know as I only tried VMWare but a USB wifi card will work in the guest OS.
I will also move this to the Virtualization sub forum

---

### Post by wildmanne39 on 2016-10-08
Yes you can use a usb wifi adapter in the guest of a vm but make sure you buy the right adapter and for the record discussing topics like monitor mode is not allowed on this forum so if you need help with that once you get a usb adapter please ask at the Kali forum.
Thanks

---

### Post by msriptide on 2016-10-08
Hi, thanks for the response, i've bought a usb wireless adpater now and i've set my VM to use it instead of host.
I'm still not finding it. is there a guide or something i can be pointed to to set up my wireless adpater on this?
sorry for saying anything about monitoring.

---

### Post by jeremy31 on 2016-10-08
with the guest OS having control of the usb adapter, post results for ```
lsusb
```

---

### Post by msriptide on 2016-10-08
```

Bus 001 Device 002: ID 0846:9053 NetGear, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 0e0f:0002 VMware, Inc. Virtual USB Hub
Bus 002 Device 002: ID 0e0f:0003 VMware, Inc. Virtual Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```
Should have said its a netgear A6210 as well, sorry

---

### Post by jeremy31 on 2016-10-08
This poster had the same ID [https://ubuntuforums.org/showthread.php?t=2265150&p=13234180#post13234180](https://ubuntuforums.org/showthread.php?t=2265150&p=13234180#post13234180)

---

### Post by msriptide on 2016-10-08
Thanks guys, there goes another adapter back to the shop! should do my homework next time, this can be marked as solved, thanks

---

