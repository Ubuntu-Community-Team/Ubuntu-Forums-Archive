---
title: "Window's 7 Home Premium not reading ethernet cable"
date: 2013-10-17
forum: Windows
---

### Post by aaronschillings on 2013-10-17
I just set up my Lenovo G505 to dual boot Ubuntu 13.04 and Windows 7 Home Premium.  My wireless adapter works perfectly fine in Ubuntu, but will not I need driver updates to be able to get it to work in 7.  When I try connecting to my network via ethernet cable, 7 won't even read that.  Ubuntu reads the ethernet cable just fine.  I have no idea what the problem is, or how to fix it.  Any one have any suggestions?

---

### Post by oldos2er on 2013-10-17
Since this is a Windows support question I've moved it to Other OS/Distro Support.

---

### Post by Bibek on 2013-10-18
Looks like you are missing the drivers for the Ethernet card as well as the wireless card. check if you have the drives installed. since i have not used windows for a bit, i dont exactly remember the details of where you can see it but as far as i remember, if you right click on Computer and click on Manage, something will open up and there you can click hardware or something. if you dont have the drivers installed, the items are there with yellow question marks or a yellow exclamation sign if your drivers are not functioning properly. if you are missing drivers, go to lenovo support and download the missing drivers for your particular model and install it. 

ubuntu works out of the box because ubuntu contains most of the drivers built into the operating system. since you have working internet on the ubuntu system, you can download drivers there and use a flashdrive or something to install it on windows. 

Best of luck.

---

### Post by danielr2 on 2013-10-19
Looks like your stuck with getting your network to work with Win7 on that Laptop. I checked the Lenovo driver page for your model and it seems that only Windows8 driver are available for your model. Is this a fairly new model? It seems to be a consumer model and not a business model. Most manufacturers only offer the driver for the latest "home version" Windows for their consumer product line. Presently, that is Windows 8. So you can either install Windows 8 and get the manufacturers drivers or try to find some 3rd party driver for Win7 on the net.

Alternatively, go for a laptop from the business line. Here you usually get all Windows driver back to WinXP for many of the current models. Since even here the lower end models tend to be shipped without legacy Windows driver support, it's best to check with the drivers pages of your preferred manufacturer before your purchase.

---

### Post by coffeecat on 2013-10-19
@aaronschillings, it might be that the Windows 8 drivers on the Lenovo website that danielr2 mentions will work in Windows 7. Or, if you google the exact chipset names for the ethernet and wireless devices, you might be able to find Windows 7 drivers from the chipset manufacturers themselves. Running lspci from the terminal in Ubuntu should give you enough information on the two network devices to get google results.

---

