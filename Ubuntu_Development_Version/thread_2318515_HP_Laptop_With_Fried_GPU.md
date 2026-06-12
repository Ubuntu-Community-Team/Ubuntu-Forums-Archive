---
title: "HP Laptop With Fried GPU"
date: 2016-03-26
forum: Ubuntu Development Version
---

### Post by Crimple on 2016-03-26
Hi.

I have a HP G62 with an Intel P6100 and a dedicated GPU (HD 5430/5450/5470 according with my Xubuntu's [I]lspci | grep VGA).
[/I]
This machine came with Windows7 pre-installed and everything worked fine until the GPU stopped working. Then I had a Hell of a time just having it booted because Windows would insist on installing the driver for a piece of hardware that wasn't working any more and the monitor would show black (eventually the driver failed to install).

Now I'm having the same issue with Linux. I managed to install Xubuntu 16.04 (beta1) and after a couple of reboots it just went using Intel's integrated graphics. But now, trying to install flavours of beta2 (Ubuntu, Ubuntu Mate) on partitions of the same disk they won't even manage the live USB part. Somewhere along error messages I see *Radeon* written on both tries.

Is there a way of telling the new installs to not see, or ignore, a piece of hardware?

Thanks.

---

### Post by Bucky Ball on 2016-03-26
*Thread moved to **Ubuntu Development Version**.*

Anything to do with 16.04 goes here.

There is a bug with the USB install on 16.04, 16.04 is not yet released.

This is a known bug, expect more breakage in 16.04 before it comes out in late April. I advise you try a supported release. 14.04 or 15.10.

---

### Post by T.J. on 2016-03-26
Hi!

> **Crimple said:**
> 

Is there a way of telling the new installs to not see, or ignore, a piece of hardware?

Thanks.

Absolutely.

When the bootmenu is presented, you can edit the parameters to blacklist any drivers that you do not want loading automatically.  For example, blacklist=nouveau or blacklist=radeon if you want to stop Linux from loading drivers for Nvidia or AMD Radeon. In order to make it permanent, you will need to edit the bootloader file or add a blacklist file under /etc/modules.d after the machine is started.

If you need help figuring it out, please post back. I'd be happy to assist you as much as i can.

---

### Post by Crimple on 2016-03-27
@Bucky Ball
Thanks for the info.


@T.J.
Thanks.
When 16.04 is final I'll create a new thread.

---

### Post by grahammechanical on 2016-03-27
Is there not a setting in the BIOS to disable the dedicated graphic adapter?

---

### Post by Crimple on 2016-03-27
> **grahammechanical said:**
> Is there not a setting in the BIOS to disable the dedicated graphic adapter?
Nope, just checked.

---

### Post by ventrical on 2016-03-28
Can you send us a list of your hardware using /lspci/ in terminal?

thanks..

---

### Post by Crimple on 2016-03-29
here

```
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation HM55 Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Park [Mobility Radeon HD 5430/5450/5470] (rev ff)
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Cedar HDMI Audio [Radeon HD 5400/6300 Series] (rev ff)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller (rev 02)
03:00.0 Network controller: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter (rev 01)
7f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
7f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
7f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
7f:02.1 Host bridge: Intel Corporation 1st Generation Core i3/5/7 Processor QPI Physical 0 (rev 05)
7f:02.2 Host bridge: Intel Corporation 1st Generation Core i3/5/7 Processor Reserved (rev 05)
7f:02.3 Host bridge: Intel Corporation 1st Generation Core i3/5/7 Processor Reserved (rev 05)
```

On  this distro (Xubuntu 16.04 which I'm using as my daily OS) the AMD driver was showing (in additional drivers) as being used. Then, after a couple of reboots, it stopped showing and I activated Intel's proprietary driver. This particular distro has always worked well on this machine.
Ubuntu Mate 15.10 and Lubuntu 15.10 are working fine on their partitions.
Distros that, one way or another, didn't work:
Kubuntu 14.04, USB live worked, installed to disk, first reboot fine, second reboot (after updates) failed
Ubuntu Gnome 15.10, USB live didn't work
Ubuntu 16.04 beta2, USB live didn't work
Ubuntu Mate 16.04 beta2, USB live worked, installation went on but failed first reboot

Maybe it's not the bleeding AMD, maybe it's distros that demand 3d acceleration and beta2 bugs... (I'm guessing)

---

### Post by ventrical on 2016-03-29
> **Crimple said:**
> here

```
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation HM55 Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Park [Mobility Radeon HD 5430/5450/5470] (rev ff)
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Cedar HDMI Audio [Radeon HD 5400/6300 Series] (rev ff)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller (rev 02)
03:00.0 Network controller: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter (rev 01)
7f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
7f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
7f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
7f:02.1 Host bridge: Intel Corporation 1st Generation Core i3/5/7 Processor QPI Physical 0 (rev 05)
7f:02.2 Host bridge: Intel Corporation 1st Generation Core i3/5/7 Processor Reserved (rev 05)
7f:02.3 Host bridge: Intel Corporation 1st Generation Core i3/5/7 Processor Reserved (rev 05)
```

On  this distro (Xubuntu 16.04 which I'm using as my daily OS) the AMD driver was showing (in additional drivers) as being used. Then, after a couple of reboots, it stopped showing and I activated Intel's proprietary driver. This particular distro has always worked well on this machine.
Ubuntu Mate 15.10 and Lubuntu 15.10 are working fine on their partitions.
Distros that, one way or another, didn't work:
Kubuntu 14.04, USB live worked, installed to disk, first reboot fine, second reboot (after updates) failed
Ubuntu Gnome 15.10, USB live didn't work
Ubuntu 16.04 beta2, USB live didn't work
Ubuntu Mate 16.04 beta2, USB live worked, installation went on but failed first reboot

Maybe it's not the bleeding AMD, maybe it's distros that demand 3d acceleration and beta2 bugs... (I'm guessing)


I have the same AMD card. it is not bleeding edge.  It will run on llvmpipe .. but .. othewise it is pretty well obsoleted. Also I would not use that graphics adapter with that processor. There is bound to be problems.

regards..

---

### Post by grahammechanical on 2016-03-29
You said that you had a "fried" dedicated GPU and that you could not deactivate it in the BIOS. A dedicated GPU that randomly switches on & off will cause complications when installing and again when rebooting.

Furthermore, a busted GPU that is being used for booting Ubuntu will prevent Linux from accessing the monitor's (EDID) and getting the optimum screen resolutions. I speak from experience in having an overheated GPU.

This matter is further complicated by the fact that AMD proprietary video drivers are not compatible with the version of the X server in 16.04. So, there will not be (or are not) any AMD proprietary video drivers in 16.04. If we install & tick the box "Install third party software" we will get (or the installer will attempt to get) a proprietary video driver.

You say this

> Then, after a couple of reboots, it stopped showing and I activated Intel's proprietary driver.

If the AMD adapter is fried why are you still trying to use it? You also say this

> This particular distro has always worked well on this machine.

Is that before or after the AMD GPU got fried?

You need to get that machine repaired. Or, open up the case and unplug the AMD video adapter so that the fried GPU does not keep causing complications.

Regards.

---

### Post by Crimple on 2016-03-29
> **grahammechanical said:**
> If the AMD adapter is fried why are you still trying to use it? 
I'm not, the distro will "see" the GPU and will activate the driver.


> **grahammechanical said:**
> Is that before or after the AMD GPU got fried?
After.

I think I have a mix of 3 issues here: the fried GPU,16.04 beta bugs and graphical demanding environments (KDE, Gnome)
At the moment I have 3 working distros on this machine, 1x 16.04 and 2x 15.10 all lightweight (Xfce, Lxde, Mate).
I'll wait for final Xenial and stick with Xfce or Mate.

Thanks to all.

---

### Post by Bucky Ball on 2016-03-29
All good. Please mark thread as solved. See first link in my signature for how.

---

### Post by Crimple on 2016-03-29
done

---

