---
title: "Having lots of problems"
date: 2008-04-29
forum: System76 Support
---

### Post by MyraMains on 2008-04-29
Last christmas I bought my wife a darter ultra. When we booted up for the first time it went to the login prompt rather than the initial setup. To keep this long story short. Not realizing that it came with the 64-bit version I reinstalled with the 32-bit version and updated the drivers. Since then she has been having the following issues. Some I have found work around to on this board but no fixes yet. 

**Power Management:**
[LIST]
[*]I have power management completely turned off otherwise the screen flickers back and forth between bright and dark. I thought this was fixed in recent driver update but her's still does it.
[*]It has the damnedest time going back and forth between AC power and battery. The hardware may be fine but the power status icon hasn't got a clue if it is charging or what. Only if I plug or unplug and reboot then it works everything out and is happy.
[/LIST]

**Wireless Connection:**
[LIST]
[*]It will not automatically connect to my home network after boot. Well sometimes it does but most of the time it does not. You have to click wireless connection icon and choose the network. 
[*]  It will often disconnect several times a day for no apparent reason and you have to manually reconnect. Sometimes after 2 or 3 reconnects it will not be able to acquire an address till the system is rebooted.
[/LIST]
FYI The signal strength at my wife's desk is between 75% and 90% and none of the other wireless devices in my house have these issues. 
  

I am wondering if these problems are related to me installing the 32bit version instead of the 64bit? I have never had this much trouble out of a Linux box. I am thinking about rebuilding the whole thing and using 64bit 8.04 when she finishes this semester of school but I am wondering if it will help. Thanks in advance for any help or advice you can offer.

---

### Post by thomasaaron on 2008-04-30
If you install 64-bit gutsy and install/run the system76 driver most of your problems will be gone.

This will enable hibernate and both s1 and s3 suspend. It will also fix the power management and screen flickering problems.

Some of these problems have resurfaced in Hardy, and we are working right now on a fix.

As for your wireless, problem, I need to know more about your wireless configurations: wep/wpa/wpa2? What kind of router? How old is it? etc...

---

### Post by MyraMains on 2008-04-30
Thank you for the reply! I am happy to hear that most of these are easily fixed. I will get her switched to the 64-bit as soon as schools is out. Maybe you guys will have everything in Hardy fixed by then :)

My router is a Linksys but I don't know the model number off the top of my head. It will be 3 years old this summer. I am using WEP and it is running in mixed mode for both b and g because my notebook is 802.11b only.

---

### Post by thomasaaron on 2008-04-30
Which wireless card does your computer have?
Is it the 3945 or the 4965.
That info should be available if your run this command from a terminal:
lspci

---

### Post by ctsdownloads on 2008-04-30
> **MyraMains said:**
> Last christmas I bought my wife a darter ultra. When we booted up for the first time it went to the login prompt rather than the initial setup. To keep this long story short. Not realizing that it came with the 64-bit version I reinstalled with the 32-bit version and updated the drivers. Since then she has been having the following issues. Some I have found work around to on this board but no fixes yet. 

**Power Management:**
[LIST]
[*]I have power management completely turned off otherwise the screen flickers back and forth between bright and dark. I thought this was fixed in recent driver update but her's still does it.
[*]It has the damnedest time going back and forth between AC power and battery. The hardware may be fine but the power status icon hasn't got a clue if it is charging or what. Only if I plug or unplug and reboot then it works everything out and is happy.
[/LIST]

**Wireless Connection:**
[LIST]
[*]It will not automatically connect to my home network after boot. Well sometimes it does but most of the time it does not. You have to click wireless connection icon and choose the network. 
[*]  It will often disconnect several times a day for no apparent reason and you have to manually reconnect. Sometimes after 2 or 3 reconnects it will not be able to acquire an address till the system is rebooted.
[/LIST]
FYI The signal strength at my wife's desk is between 75% and 90% and none of the other wireless devices in my house have these issues. 
  

I am wondering if these problems are related to me installing the 32bit version instead of the 64bit? I have never had this much trouble out of a Linux box. I am thinking about rebuilding the whole thing and using 64bit 8.04 when she finishes this semester of school but I am wondering if it will help. Thanks in advance for any help or advice you can offer.

I would definitely go ahead and provide Tom with your lspci output. That said, I have actually found zero advantage to using 32bit any longer and because System76 provides fixes for the 64bit release, this might be the fastest approach, be it me making no promises.

If it was me, I would install Heron 64bit, then ensure that I reinstalled the latest System76 package with the patches provided. This will greatly help everyone along I suspect. Just my thinking...

---

### Post by MyraMains on 2008-05-01
> **thomasaaron said:**
> Which wireless card does your computer have?
Is it the 3945 or the 4965.
That info should be available if your run this command from a terminal:
lspci

**wireless card**
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

**rest of lspic output**
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
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)

---

### Post by thomasaaron on 2008-05-02
OK. I think if you install 64-bit Gutsy, you will be impressed. We're still working on getting Hardy up to speed. It has some regressions for the DarU2.

We should have that worked out pretty quickly, though. It is a major priority around here.

---

