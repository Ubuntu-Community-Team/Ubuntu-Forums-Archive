---
title: "Ubuntu on USB stick - running under Linux, Windows, allows saving my stuff"
date: 2012-10-19
forum: The Cafe
---

### Post by moribashi on 2012-10-19
Hi

So my problem description: I have USB stick and I wan't to  carry a copy of Ubuntu on it with me. I want to use this Ubuntu on Windows or in Linux, it depends what kind of device I have in hand at the moment. I also want to save my files inside this Ubuntu, listen to my music from it etc. I do not want to reboot and boot from USB stick. Basically what I wan't to do is run operating system inside operating system.

I have tried LinuxLive USB creator which offers some kind of virtualbox solution and allows do something like that, but with limitations:
1. It only runs on Windows
2. I can use only 4 GB space for my files (restriction of FAT32).

If anyone knows some kind of solution, don't hesitate to answer. :)

Thanks!

---

### Post by C.S.Cameron on 2012-10-19
If the host computers have VBox on them you can put an Ubuntu virtual machine on the USB stick.

---

### Post by layers on 2012-10-23
Well, first off, why Ubuntu on a USB? You have a problem you want to solve? Do not jump to a solution.

Objectives> Save files (like text documents)
Listenning to mp3's
Constraints> not to reboot every time
to run on different computers from USB

The best thing my brain tells me is portable apps:
to run on Windows: [http://portableapps.com/](http://portableapps.com/)
to run on Linux: [http://portablelinuxapps.org/](http://portablelinuxapps.org/)
You just download them to a computer and install them into the USB you will be using. And then just carry the USB around

Maybe you can get them to use the same data somehow.

---

### Post by leclerc65 on 2012-10-23
There is a program named YUMI (Windows 7, not so sure about XP) that can put several distros on a USB stick

[http://www.pendrivelinux.com/yumi-multiboot-usb-creator/](http://www.pendrivelinux.com/yumi-multiboot-usb-creator/)

Have fun with it and let us know.
I have Parted Magic, System Rescue CD, Puppy on my 64G stick that I carry with me all the time. Yumi put everything in a 'multiboot' folder, you can use the empty space for file storage.

---

### Post by doorknob60 on 2012-10-24
I would say Portable Apps would be worth looking into, but you could do a Virtualbox setup. I would try to get portable copies of both the Windows and Linux versions of Virtualbox, and then format your USB as exFAT or NTFS to get around the 4 GB filesize limitation.

I found a zip file of a portable version of Virtuabox for Windows here: [http://www.linuxliveusb.com/en/other-versions](http://www.linuxliveusb.com/en/other-versions)
And for Linux, you could probably just download the official .run installer and choose the flash drive as the save point, not sure if that's the best solution though, but seems like it should work: [http://download.virtualbox.org/virtualbox/4.2.2/VirtualBox-4.2.2-81494-Linux_x86.run](http://download.virtualbox.org/virtualbox/4.2.2/VirtualBox-4.2.2-81494-Linux_x86.run)

---

