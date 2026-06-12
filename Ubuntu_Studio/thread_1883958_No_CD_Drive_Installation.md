---
title: "No CD Drive Installation"
date: 2011-11-20
forum: Ubuntu Studio
---

### Post by southpointingchariot on 2011-11-20
This is my first linux install of any kind - I am attempting to install ubuntu studio on a computer where the cd/dvd drive has broken. Obviously I can't host the iso in Windows - is there another installer, or can I install from a usb drive?

---

### Post by WasMeHere on 2011-11-20
Welcome to the Ubuntu Forums, southpointingchariot,

Yes you can install from a live USB drive (flash).

[[COLOR="RoyalBlue"]_https://help.ubuntu.com/community/Installation/FromUSBStick_[/COLOR]]("https://help.ubuntu.com/community/Installation/FromUSBStick")

Please post some details about your computer (cpu, graphics, os, partitions, etc) and how you plan to use it! That makes it easier to give detailed help.

Have fun finding out about Ubuntu :-)
Olle

---

### Post by Kelvari on 2011-11-20
I would like to add as details that you should have at least 750MB free on the flash drive you intend to use (1GB+ preferred). 

One of the more effective tools that I've found for setting up a USB drive to boot a Linux distro (including Ubuntu) is [UNetbootin]("http://unetbootin.sourceforge.net/"). It's probably not the fastest or the flashiest, but it gets the job done, and it works in Windows, Mac OSX, and Linux.

Edit: As far as installing the UbuntuStudio OS goes, you should be able to use WUBI (Windows Ubuntu Installer), if you want to maintain an 'easy' dual-boot system, or you can use the actual installer through the UbuntuStudio and install it onto the raw hardware. If you need help with either of those, please feel free to ask.

---

### Post by jejeman on 2011-11-20
For ubuntu studio you need 2GB empty usb flash.

---

### Post by southpointingchariot on 2011-11-20
Thanks for the quick responses! I am installing this on a Sony VAIO VGN FW139E - not a netbook by any means, just an old warrior being retired ;) . It has Vista (a fresh install), a Core 2 Duo P8400, and a ATI Mobility Radeon 3400 series graphics card. As I said, it's a totally fresh computer software wise (except for chrome), so there's over 200gbs available. I am planning on using a usb external HDD with 80gbs of space to install if necessary, so space is not the issue. 

I'm not looking for anything extravagant - the most simple install possible. I chose studio because I do use some of the tools for video processing/graphic design. My plan is to eventually install MythTV and use it as a home theater hub primarily. Thoughts?

---

### Post by WasMeHere on 2011-11-20
> I'm not looking for anything extravagant - the most simple install possible. I chose studio because I do use some of the tools for video processing/graphic design. My plan is to eventually install MythTV and use it as a home theater hub primarily.

The simplest install might be to use a flavour of Ubuntu, that can run as a live system, so you can test it before you install it. Unfortunately Studio must be installed directly, you cannot test it live. (I run it as well as vanilla Ubuntu, so I know.) But all the software tools can be easily installed into any Ubuntu or Linux Mint system except the real-time kernel, that might be good if you want immediate response (low latency).

Since your hardware is not new, I think you have the best chance to get good co-operation between hardware and software with Ubuntu 10.04 Long Time Support. If you want something newer, try Ubuntu 11.04 or the currently newest version 11.10. If you notice delay in the graphics you may need to install a proprietary graphics driver and/or change from 'vanilla' Ubuntu to Xubuntu or Lubuntu.

---

