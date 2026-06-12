---
title: "Two kind of taxes to pay"
date: 2007-03-07
forum: Testimonials &amp; Experiences
---

### Post by FreedomOfThought on 2007-03-07
The installation of Ubuntu6.10 Edgy passed smoothly. I had some trouble in installing the wireless hardware, but I could find a solution on the forum. It's a pity that these days one still has to use the commandline for installing and/or configuring your softwarebuild. For lots of people this will be threshold to take and this will not benefit their appreciation for the system. I found even some dinosaurs in the software, such as "vi" (How I hated that program 25 years ago). I thought dinosaurs were extinct. Apparently, not in the Linux-kernel.

Another mayor drawback to me is the lack of drivers for printers and flatbed-scanners. I can't find a suitable workable driver for my old "X75-lexmark". I don't care, as far that oldie is concerned, but when I browse the printer/scanner-producers' website for specs of their newer models, they generally don't provide Linux-drivers either! Is this some kind of sabotage to the disadvantage of Linux? Is Linux so difficult to interface? Are they paid by other OS-suppliers to get out of the way?
Anyhow this lack of acceptance is a second mayor drawback that will impede a wide spread of the open OS. Maybe we can do something to it and send requests to these producers for them to develop their drivers for the products they sell. Or we can publish a list of all devices for which acceptable linuxdrivers are available.

As a conclusion. Ubuntu6.10 works pretty good. My experience with OpenOffice is good too. I'll hope that I can soon get rid of the commandline (It don't like executing weird magic spells)
and that hardwarevendors will ship linuxdrivers together with their products. If that is the case
I will remove the Microsoft-pakkages with pleasure as I don't like their current monopoly. Each time we buy a computer in this country (Belgium), we 'll have to pay 2 kind of taxes : one for the government and another substantial one for Microsoft!

---

### Post by Tuna-Fish on 2007-03-07
> **FreedomOfThought said:**
> The installation of Ubuntu6.10 Edgy passed smoothly. I had some trouble in installing the wireless hardware, but I could find a solution on the forum. It's a pity that these days one still has to use the commandline for installing and/or configuring your softwarebuild. For lots of people this will be threshold to take and this will not benefit their appreciation for the system. I found even some dinosaurs in the software, such as "vi" (How I hated that program 25 years ago). I thought dinosaurs were extinct. Apparently, not in the Linux-kernel.
vi isn't a part of the linux-kernel, it, and emacs, however are very liked by the people writing it. A friend of mine pointed out that it is because once you know to use either of them, not other program in the world can match the speed they give, because everything is very quickly achieved by a keystroke. meh, i just don't want to bother learning them.
> 
Another mayor drawback to me is the lack of drivers for printers and flatbed-scanners. I can't find a suitable workable driver for my old "X75-lexmark". I don't care, as far that oldie is concerned, but when I browse the printer/scanner-producers' website for specs of their newer models, they generally don't provide Linux-drivers either! Is this some kind of sabotage to the disadvantage of Linux? Is Linux so difficult to interface? Are they paid by other OS-suppliers to get out of the way?
Anyhow this lack of acceptance is a second mayor drawback that will impede a wide spread of the open OS. Maybe we can do something to it and send requests to these producers for them to develop their drivers for the products they sell. Or we can publish a list of all devices for which acceptable linuxdrivers are available.

You were looking in the wrong place for the drivers. one of the tenets of linux is that all the work in software should be done by people who are interested to do it. Drivers should, ideally, be written by the makers of the device, but maintained by the community, as after the device has been sold, maintaining good drivers only ever hurts the device-makers bottom line. As such, all the linux printer drivers can be found from the linux printing project's page, [http://www.linux-foundation.org/en/OpenPrinting](http://www.linux-foundation.org/en/OpenPrinting) . When installing the device, however, you should never have to fetch the drivers from somewhere in the net, but it should be provided by distro maker in CUPS.

> 
As a conclusion. Ubuntu6.10 works pretty good. My experience with OpenOffice is good too. I'll hope that I can soon get rid of the commandline (It don't like executing weird magic spells)
and that hardwarevendors will ship linuxdrivers together with their products. If that is the case
I will remove the Microsoft-pakkages with pleasure as I don't like their current monopoly. Each time we buy a computer in this country (Belgium), we 'll have to pay 2 kind of taxes : one for the government and another substantial one for Microsoft!

As said above, a device that you install in linux should never come with linux drivers on disk, as depending on the type of the device the drivers should be found from the kernel, the mesa project, the common usb project (can't remember the name) or cups.

---

