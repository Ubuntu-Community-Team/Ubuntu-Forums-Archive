---
title: "Booting ubuntu-server from SSD doesn't work on Raspberry Pi 3B+"
date: 2020-03-05
forum: Server Platforms
---

### Post by mikex72 on 2020-03-05
Hello,

i installed ubuntu server for the RPI on a microSD card, put it into my Pi 3B+ and it booted and worked without any problems at all.

But since running a server from an sd card isn't ideal, I decided to upgrade to SSD.

So I:
- removed the sd card from the Pi
- flashed ubuntu-server onto the SSD 
- in cmdline.txt on the boot partition I changed the root=/dev/mmdpart2 to root=/dev/sda2 (since that is where the rootfs is on the SSD)
- plugged the SSD into the PI via usb

When I turned the PI on, I saw the rainbow screen and then the bootloader (uboot)  printed a bunch of stuff, some errors and such, and then tried to load the OS from network via TFTPGET.  This means that raspberry was able to read the boot partition on the SSD and start the boot process from it, but for some reason, it wasn't able to find the second partition on the SSD where the ubuntu root system resides and boot it from it.

I then took an empty microsd card, flashed another copy of the ubuntu-server on it, then in partition manager i deleted the system partition, so only boot partition was left on the sd card. After that i edited the cmdline.txt on the sd card the same way I mentioned above and then tried to start the RPI with both the microsd and SSD plugged in. 
It booted without any problems. 

So what is going on here, why am I forced to have the boot partition on the microsd for the system to boot, when the boot process is clearly capable of starting directly from the SSD as well?

Thanks!

---

### Post by TheFu on 2020-03-08
Google found this : [https://www.raspberrypi.org/documentation/hardware/raspberrypi/bootmodes/msd.md](https://www.raspberrypi.org/documentation/hardware/raspberrypi/bootmodes/msd.md)

I don't use Ubuntu on my Pi devices. Sorry.

---

### Post by vawaver on 2020-03-19
Try to use Berryboot to install Ubuntu server 18.04.4 - image here [https://berryboot.alexgoldcheidt.com/search-downloads/?dl_cat=0&dl_search=LTS](https://berryboot.alexgoldcheidt.com/search-downloads/?dl_cat=0&dl_search=LTS)

Try to follow up this tutorial - [https://youtu.be/eAkUWAcxrtE](https://youtu.be/eAkUWAcxrtE)

---

### Post by ahbart on 2020-03-25
It looks like you have enabled usb boot on the raspberry have you? [link]("https://www.raspberrypi.org/documentation/hardware/raspberrypi/bootmodes/msd.md")

---

