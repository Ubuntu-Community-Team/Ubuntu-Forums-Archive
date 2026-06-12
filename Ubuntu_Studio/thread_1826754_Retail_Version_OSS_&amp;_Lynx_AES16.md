---
title: "Retail Version OSS &amp; Lynx AES16 ?"
date: 2011-08-17
forum: Ubuntu Studio
---

### Post by JuanPabloCuervo on 2011-08-17
Hi, 
any owners ?
comments?

[http://manuals.opensound.com/devlists/lynxtwo.html](http://manuals.opensound.com/devlists/lynxtwo.html)
**Limitations of the LynxTWO/L22/AES16 driver of OSS**

   The OSS driver for the LynxTWO/L22/AES16 audio cards by Lynx Studio Technology is based on the same driver core (HAL) that is used also by the Windows and Mac drivers for these devices. So in general the OSS driver has the same  functionality than the Windows and Mac drivers. The control panel (ossxmix) screens are rather similar than the Windows and Mac ones. There is no OSS specific user documentation available for these devices but the Windows/Mac documentation is valid for OSS too. 
   However the OSS driver doesn't implement all the features of these devices. More features can be added to the driver on contract. Please check that the features you will need are available before purchasing the driver. The current OSS driver has the following limitations: 
     Unlike other parts of OSS the LynxTWO/AES16 driver is not in open source. The driver will only be included in the precompiled binary packages distributed by 4Front Technologies.  However we will give the source code to the customers who have signed NDA with Lynx Studio Technology. 
   Only of a subset of the control panel settings are supported. The "adapter" page lacks half of the settings. The "outputs" page provides only 2 sources (the Win/Mac version has 4 of them). 
   The AES16e (PCI-E) model is not supported. At least not yet. 
   The Aurora16 converter is not supported in 64 bit systems. It may work under 32 bits but this has not been verified. 
   The HAL library used by OSS may be older version. In general we update to the latest HAL every 1 to 3 years. This means that latest firmware versions may not necessarily be compatible with OSS. 
   At this moment the LynxTWO/AES16 driver is only available for Linux (x86 and x86_64) and Solaris/OpenSolaris (x86). 
   There are known issues with PC chipsets that are not properly supported by the Linux kernel. Interrupts may fail to work in systems that don't have native APIC driver in the kernel. This has been a problem with the intel 945 chipset (may have been fixed in the latest Linux kernels). 
   There have been unsolvable problems with some Linux distributions while the same OSS/lynxtwo version works just fine under some other distributions. 
  


is it worth the $50usd. ?
[http://www.opensound.com/ossorder.html](http://www.opensound.com/ossorder.html)

if it had Digi HD core support would buy it in a sec.

Thanks.

---

