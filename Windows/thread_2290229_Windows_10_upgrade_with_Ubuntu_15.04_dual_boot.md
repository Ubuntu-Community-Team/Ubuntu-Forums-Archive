---
title: "Windows 10 upgrade with Ubuntu 15.04 dual boot"
date: 2015-08-10
forum: Windows
---

### Post by andrewpmk on 2015-08-10
I am trying to upgrade a Lenovo T440 laptop from Windows 7 Pro to Windows 10 Pro using the free upgrade. The laptop has Ubuntu 15.04 installed as a dual boot. The upgrade does not work at all, when I try to install Windows 10 it goes to the "Configuring Windows 10 Upgrade" shutdown screen, then the computer just reboots back to the Grub menu and then back into Windows 7 as if I didn't upgrade at all. On my older HP Pavilion dm3 laptop (which does not have Linux installed), the Windows 10 upgrade process works fine and you get an "Upgrading Windows" screen once you boot up again. What am I doing wrong?

---

### Post by vandend278 on 2015-08-10
> **andrewpmk said:**
> I am trying to upgrade a Lenovo T440 laptop from Windows 7 Pro to Windows 10 Pro using the free upgrade. The laptop has Ubuntu 15.04 installed as a dual boot. The upgrade does not work at all, when I try to install Windows 10 it goes to the "Configuring Windows 10 Upgrade" shutdown screen, then the computer just reboots back to the Grub menu and then back into Windows 7 as if I didn't upgrade at all. On my older HP Pavilion dm3 laptop (which does not have Linux installed), the Windows 10 upgrade process works fine and you get an "Upgrading Windows" screen once you boot up again. What am I doing wrong?

In bios, remove the Ubuntu partition while/when you're upgrading Windows 10.

---

### Post by jerrylamos on 2015-08-22
Since whenever I run ubuntu from usb ssd or usb hard drive.  
The usb cases cost about $10 or $20 the leftover laptop 2.5" hard drive was "free", ssd's I look for a bargain on Amazon or Tiger
That way the installed hard drive on the pc remains windows whatever so I can pass the pc on with it installed.

Also, I remove usb ubuntu when booting Windows so I'm sure Windows won't screw up ubuntu

Win 7's upgraded to Win 10 O.K.  I don't like Windows, but for my casual use Win 10 is better than Win 7

Only Win 10 problem is Win 10 screws up boot sequence, so when I want to boot ubuntu next I have to use F1 or F12 or reset bios whatever.

Pain, but since I don't run Win 10 much, just to keep upgraded, I'm usually on ubuntu O.K.

I have used gparted to squeeze down windows partition and created a couple ubuntu partitions on the hard drive.  That was in an Acer netbook which has since died.  I removed its hard drive and have it in a usb case so I've got access to all the files.  The windows won't boot from usb but I wouldn't want to anyway.

---

### Post by nurchi on 2015-11-21
Thanks for the info, everyone.

> **jerrylamos said:**
> ...Only Win 10 problem is Win 10 screws up boot sequence, so when I want to boot ubuntu next I have to use F1 or F12 or reset bios whatever. ...

It doesn't if you disable fast startup, this link shows how to do it: [http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)

In short, **Open Control Panel** -> **Power Options** -> **Choose what the power buttons do** -> **Change settings that are currently unavailable**
Then you untick the "**Turn on fast startup**" box, then click "**Save changes**"

The most important thing is that after this change, you cannot just restart the computer: **YOU HAVE TO SHUT IT DOWN AND TURN ON AGAIN!!!**

After this, Windows 10 will take a bit longer to start/shutdown, but will no longer mess up the boot sequence.

The site offers method 2, which is simply download a .bat file and run it as administrator. While this is ok if you trust the source, generally, you should never trust a file that came from the internet. You are welcome to download it, but before running it as administrator (i.e. with unlimited rights), please just right click and choose edit. Examine the file, see what it does, see if it makes sense.

If you can't make sense of the content, just go with method 1, it's safer that way. Trust me, I'm an engineer... ;)

Cheers.

---

