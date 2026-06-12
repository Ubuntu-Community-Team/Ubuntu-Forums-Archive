---
title: "darter clone problematic with gutsy"
date: 2007-10-15
forum: System76 Support
---

### Post by muzcuk on 2007-10-15
Hey there!

I've recently installed gutsy on my laptop, It is pretty much the same configuration as the System76 Darter Ultra, or at least I think it is. 

As far as I know from this forum, gutsy should work for most of my hardware right out of the box, whereas it didn't. I also know that system76 has released a special ubuntu version optimized for darter ultra and would like to acquire it. 

I have several problems with my power management drivers and also the card reader isn't working yet some people say that it should work with gutsy. Same thing with webcam. Fingerprint reader seems hopeless for the moment and that is not a problem but I would really really like to make the hdmi work. 

Also there is a strange thing with this laptop, when I plug the ac adapter to the laptop, the external lcd (Samsung SyncMaster 940BW) starts to flicker. When I take the ac power out, it is crystal clear. Has anybody seen anything like this before? This is why i'd like to use the hdmi port. 

This is my lspci out, if someone would be kind enough to submit a lspci out for darter ultra, we could compare. 

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
01:04.0 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller
01:04.1 Generic system peripheral [0805]: ENE Technology Inc ENE PCI SmartMedia / xD Card Reader Controller
01:04.2 FLASH memory: ENE Technology Inc Unknown device 0720
01:04.3 FLASH memory: ENE Technology Inc ENE PCI Secure Digital / MMC Card Reader Controller
02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)

---

### Post by tedrampart on 2007-10-15
I know there was a discussion and a workaround for the screen issue somewhere in this forum, just recently.  mind you from what I remember its not a fix.. atleast til the driver is released.  

I don't think the fingerprint reader, or HDMI out even work on the official darter, atleast not without a lot of work (even then I'm not sure), so you might need to look for a resolution for that elsewhere on this site.  

the card reader should work, if its the same hardware, but there's a good chance its not.

here's the thread about screen issues: [http://ubuntuforums.org/showthread.php?t=565993](http://ubuntuforums.org/showthread.php?t=565993)

I'm sure someone will post more help soon (I don't own a darter, just a different s76)

---

