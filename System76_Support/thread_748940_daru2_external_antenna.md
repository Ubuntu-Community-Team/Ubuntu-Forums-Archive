---
title: "daru2 external antenna?"
date: 2008-04-07
forum: System76 Support
---

### Post by 6174 on 2008-04-07
I've got a daru2 and at work I've got poor wireless connectivity.  I've noticed that next to the HDMI port there appears to be a hookup for an external antenna. Am I correct that this is for the wireless? If so, what type of connector is it?

---

### Post by tedrampart on 2008-04-08
believe its for a tv tuner thats built in, but not supported

---

### Post by 6174 on 2008-04-08
> **tedrampart said:**
> believe its for a tv tuner thats built in, but not supported

I don't know about that, neither MSI's page ([http://www.msicomputer.com/NB/product_spec.asp?model=MS-1221](http://www.msicomputer.com/NB/product_spec.asp?model=MS-1221)) nor the System76 Knowledge base ([http://knowledge76.com/index.php/Daru2](http://knowledge76.com/index.php/Daru2)) say anything about a TV tuner that I can see.

---

### Post by tedrampart on 2008-04-08
there was a thread on here a few months back when that model was introduced that said it was a tv tuner.

[here's the post]("http://ubuntuforums.org/showpost.php?p=3080066&postcount=12") from thomasaaron about it

---

### Post by thomasaaron on 2008-04-08
That's correct. Unsupported tv tuner.

How close are you to the wireless router?
Also, could you post the output of lspci so that I can see which card you are using?
How do you have the router configured? Might want to try WEP 64-bit hex unless you have some serious security issues.

---

### Post by 6174 on 2008-04-08
6174@gauss:~$ lspci
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
6174@gauss:~$ 

I'm not sure where the router is, but it is an old building with lots of brick walls and interfering things (it is a physics building at a University with lots of labs running who knows what). 

The wireless is done is a pretty silly way. The wireless is completely unencrypted, but you can't get anywhere without authenticating with their Cisco VPN service.

I can connect to the wireless router at my home with no issues at all (signal or otherwise). I really just think that the router is in a bad location for where I want to use it. I've also seen private routers of various professors when looking via kismet and some of those signals are full strength (I just don't have authorization to use them).

edit: To be clear I can connect, it is just low signal strength making things slow and laggy.

---

