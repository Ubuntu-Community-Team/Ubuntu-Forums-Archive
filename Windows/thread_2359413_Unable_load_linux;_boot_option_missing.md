---
title: "Unable load linux; boot option missing"
date: 2017-04-24
forum: Windows
---

### Post by maran-maniam on 2017-04-24
I'm a newbie to Linux. Previously I have installed Linux 16.04 along with Window 10 (preinstalled OS in my computer Acer Aspire). For first few months, it's work fine and I'm able to choose my preferred OS when turn on my PC. 
But suddenly that option went missing, and my PC load Window 10 as default OS. There is no option given for me to choose. Even when I'm trying to change my boot order and insert Live Linux USB to load from USB, my PC still load Window 10 as default OS. 
[IMG]https://drive.google.com/file/d/0B23uFcYa1PSRZ2Mxd2h6RXJPeXM/view?usp=sharing[/IMG]
[https://drive.google.com/file/d/0B23uFcYa1PSRZ2Mxd2h6RXJPeXM/view?usp=sharing](https://drive.google.com/file/d/0B23uFcYa1PSRZ2Mxd2h6RXJPeXM/view?usp=sharing)

When diagnosing my bootloader with easyUEFI and find out that Linux boots order is disabled and hidden.
Please help me solve this. I'm really want to use Linux.
Thank you

---

### Post by yancek on 2017-04-24
If you had been successfully booting both systems for some time and it suddenly stopped working, the most likely problems would be a serious hardware failure or some update or change to the operating system software.  Since your windows system still boots, it is likely that a major windows update might be the problem if you had done that??

Not sure what the problem would be with your inability to change the boot priority in the BIOS to boot a usb.  You might try reviewing your Acer manual to see how to change options.

I'm not familiar with Easy UEFI except to note that it is windows software and you might have better luck posting your problem at a windows forum?  In the image you posted, what do you see when you click to highlight the ubuntu entry in the left panel?  Does any more detail show in the right panel box?

---

### Post by LastDino on 2017-04-24
Probably just shooting in the dark, but it would help if you can show us your Bios settings.

I'm running dual boot too and I update windows with every notification, nothing like this has ever happened. However, I fear that u might have done BIOS update or somehow restored to default undoing your Legacy settings (if you had used that to dual boot).

First priority would be to get that USB booting, if it boots, fixing Grub is 2 min job.

---

