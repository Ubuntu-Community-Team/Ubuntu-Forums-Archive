---
title: "Startup Disk Creator crash-no logical exit:"
date: 2012-08-08
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by ventrical on 2012-08-08
SDC does not give me the option to send bug report except (relaunch) ??

---

### Post by ventrical on 2012-08-08
Ok .. I clicked <relaunch> and  SDC popped up along with other notification.

---

### Post by cariboo on 2012-08-08
Can you confirm that the packages mentioned in the error message are the latest versions?

---

### Post by ronacc on 2012-08-08
when I tried to use SDC this morning to see if it would burn a useable stick from this AM's zsync I got something similar  , different warning but same thing ,only choice was relaunch which diddn't work in my case . go ahead and file and I'll me too it . I didn't have time this morning .

---

### Post by GreatDanton on 2012-08-08
I have exactly same problem.

Regards.

---

### Post by ventrical on 2012-08-08
> **cariboo907 said:**
> Can you confirm that the packages mentioned in the error message are the latest versions?


Unfortunately I decided to :

sudo apt-get update
sudo apt-get upgrade

So far .. a successful update, however, there was an error about the new Nvidia driver could only be bound to the 3.5.0-7 kernel and not the new 3.5.0-8.

Also. now, horizontal tearing (I'll leave that in the appropiate forum) between title-bars and windows using compiz wobbly windows.

---

### Post by ventrical on 2012-08-08
> **ronacc said:**
> when I tried to use SDC this morning to see if it would burn a useable stick from this AM's zsync I got something similar  , different warning but same thing ,only choice was relaunch which diddn't work in my case . go ahead and file and I'll me too it . I didn't have time this morning .

 I had just zsynced quantal-alternate-i386.iso and used SDC to make a startup disk. However, even though it crashed again (and I was unable to report) I was able to successfully boot that .ISO (which is currently installing on another machine).

 Also, there did not seem to be any problem while using SDC  to create a USB with quantal-alternate-amd64.iso <which has not been zsynced for some time>. So, before I declare my assumption here I am going to have to back-track on this one because the quantal-alternate-i328.iso may be corrupt? - and subsequently borked the USB created disk.

---

### Post by ventrical on 2012-08-08
> **cariboo907 said:**
> Can you confirm that the packages mentioned in the error message are the latest versions?

 I have a syncronized install before updates so I will see if that report can be emulated.

---

### Post by ventrical on 2012-08-08
> **GreatDanton said:**
> I have exactly same problem.

Regards.

 I'm going to try it now after all the updates.

EDIT-

I tried it with quantal-desktop-i386-iso (alpha3) and it crashed into nowhere. No apport , nothing. So I am not sure whether to file a bug against SDC or apport or both ?

---

### Post by ventrical on 2012-08-08
Whats the code to enter  for SDC when reporting a bug. I tired:

ubuntu-bug sdc
ubuntu-bug startup disk creator

and neither are recognized.

---

### Post by ventrical on 2012-08-08
Here is the link for the assumed apport bug.

[https://bugs.launchpad.net/ubuntu/+source/apport/+bug/1034590](https://bugs.launchpad.net/ubuntu/+source/apport/+bug/1034590)

---

### Post by GreatDanton on 2012-08-08
> **ventrical said:**
> I'm going to try it now after all the updates.

EDIT-

I tried it with quantal-desktop-i386-iso (alpha3) and it crashed into nowhere. No apport , nothing. So I am not sure whether to file a bug against SDC or apport or both ?

I also installed the latest updates and now there is no apport :lolflag:  I will add myself to the bug. Thanks for pointing this out.

---

### Post by cariboo on 2012-08-08
The package you are looking for is usb-creator-gtk.

---

### Post by ventrical on 2012-08-08
@ Cariboo907 :)

Yes .. I finally figured it out:) Thanks

[https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1034601](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1034601)

EDIT

The bug is 'failed to install the bootloader' .. but it does !

---

### Post by cariboo on 2012-08-08
I had startup disk creator crash on me last week trying to create a usb thumb drive with the 12.04 32-bit server iso. I realized my mistake as I wanted the 64-bit version so I never thought anything of it, as the 64-bit version was created without a problem. What version did you have a problem with.

---

### Post by ventrical on 2012-08-08
> **cariboo907 said:**
> I had startup disk creator crash on me last week trying to create a usb thumb drive with the 12.04 32-bit server iso. I realized my mistake as I wanted the 64-bit version so I never thought anything of it, as the 64-bit version was created without a problem. What version did you have a problem with.

As I mentioned previously it was <quantal-alternate-i386.iso>  and <quantal-desktop-i386.iso> on an updated quantal desktop.
```


00:00.0 Host bridge: Advanced Micro Devices [AMD] nee ATI Radeon Xpress 200 Host Bridge (rev 01)
00:02.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS480 PCI-X Root Port
00:06.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS480 PCI Bridge
00:11.0 IDE interface: Advanced Micro Devices [AMD] nee ATI IXP SB400 Serial ATA Controller (rev 80)
00:12.0 IDE interface: Advanced Micro Devices [AMD] nee ATI IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI IXP SB400 USB Host Controller (rev 80)
00:13.1 USB controller: Advanced Micro Devices [AMD] nee ATI IXP SB400 USB Host Controller (rev 80)
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI IXP SB400 PCI-PCI Bridge (rev 80)
01:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce G210] (rev a2)
01:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)
02:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03)
03:03.0 Ethernet controller: VIA Technologies, Inc. VT86C100A [Rhine] (rev 06)
dale@dale-desktop:~$ 

```
but , funny thing .. this is an Intel mobo.

---

### Post by ronacc on 2012-08-08
Ubuntu upgraded it :P

---

### Post by GreatDanton on 2012-08-08
I have made several more live usb, and this is the last result

---

### Post by cariboo on 2012-08-08
> **ventrical said:**
> As I mentioned previously it was <quantal-alternate-i386.iso>  and <quantal-desktop-i386.iso> on an updated quantal desktop.
```


00:00.0 Host bridge: Advanced Micro Devices [AMD] nee ATI Radeon Xpress 200 Host Bridge (rev 01)
00:02.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS480 PCI-X Root Port
00:06.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS480 PCI Bridge
00:11.0 IDE interface: Advanced Micro Devices [AMD] nee ATI IXP SB400 Serial ATA Controller (rev 80)
00:12.0 IDE interface: Advanced Micro Devices [AMD] nee ATI IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI IXP SB400 USB Host Controller (rev 80)
00:13.1 USB controller: Advanced Micro Devices [AMD] nee ATI IXP SB400 USB Host Controller (rev 80)
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI IXP SB400 PCI-PCI Bridge (rev 80)
01:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce G210] (rev a2)
01:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)
02:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03)
03:03.0 Ethernet controller: VIA Technologies, Inc. VT86C100A [Rhine] (rev 06)
dale@dale-desktop:~$ 

```
but , funny thing .. this is an Intel mobo.

Looks to me like the manufacturer used AMD/ATI devices, even though the motherboard uses an Intel processor.

I have an [MSI G31]("http://www.msi.com/product/mb/G31TM-P21.html") in my server, it is all Intel except for the NIC:

```
lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA Controller [IDE mode] (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 RAID bus controller: Silicon Image, Inc. SiI 3114 [SATALink/SATARaid] Serial ATA Controller (rev 02)

```
The Silicon Image Raid controller, is just an add in card to add more SATA ports.

The system uses an Pentium(R) Dual-Core  CPU E5400.

---

### Post by ventrical on 2012-08-08
When I boot this PC up the splash screen comes up  with 'Intel Desktops.." etc.. I'll take a pic of it.

It is an Intel Pentium 4 (R)(D) dual core.

---

### Post by ventrical on 2012-08-08
Here is my Dell Dimension 3100.

```

ventrical@ventrical-Dell-DV051:~$ lspci
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
00:1d.0 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801FR/FRW (ICH6R/ICH6RW) SATA Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
03:02.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem
03:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller (rev 04)
ventrical@ventrical-Dell-DV051:~$ 

```

all Intel, but made by Dell.

---

### Post by ventrical on 2012-08-08
Here is pic of my Intel splash on bootup.

edit: So. Intel Board with AMD/ATI chipset ?

I know .. weird. :)

---

### Post by cariboo on 2012-08-08
> **ventrical said:**
> Here is pic of my Intel splash on bootup.

edit: So. Intel Board with AMD/ATI chipset ?

I know .. weird. :)

It's' not that unusual, I use MSI motherboards exclusively, I see several of their Intel powered motherboards using AMD/ATI chipsets

---

