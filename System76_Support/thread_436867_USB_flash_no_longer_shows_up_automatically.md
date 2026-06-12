---
title: "USB flash no longer shows up automatically"
date: 2007-05-08
forum: System76 Support
---

### Post by ajlewis2 on 2007-05-08
Two days ago prior to an upgrade of the System76 drivers, I could plug in my usb flash and it opened a nautilus window automatically.  Now I can see that the drive is found using 'tail -f /var/log/syslog' but it is not opening up in nautilus.  Also, I cannot figure out how to mount it manually.

Any idea what happened to change the behavior?

My sd card from my camera does open up as expected.

Thanks,
Anita

---

### Post by thomasaaron on 2007-05-08
Most likely, the format of your card is not vfat, fat16, fat32 (I'm not sure what other formats are acceptable).

We've encountered some mounting problems with cards formatted by Palm devices.

For some reason, this seems to be a problem under Fiesty, and I've heard reports that it was not a problem under Edgy.

From a terminal, type:
sudo apt-get install gparted

Gparted should show up in your Application's menu.
From Gparted, you can see what format your cards are in (and change the format).

Or you can try a new card and see what it does. They come from the factory with vfat formatting.

Best,
Tom

---

### Post by ajlewis2 on 2007-05-08
Thanks for the reply, Tom.  It wasn't quite that simple, but I did figure it out.  I got a clue when I noticed that with the usb device in, my .jpg on my desktop did not show the usual icon thumbnail.  I clicked on it and it said that it did not exist.  That clued me that this was a conflict in mounting.

I had /dev/sda1 for the device for my root partition, because originally /dev/hda1 no longer worked after the Feisty upgrade.  The usb device was taking /dev/sda1 now.  It had not been doing that for the couple weeks that I had used Feisty, but after my last upgrade, the problem began.

The solution was to use UUID=... instead of /dev/sda1.  I got the UUID from /boot/grub/menu.lst.  Now the mount works fine.  In fact, the usb device is showing up mounted on /dev/sda1.  

Anita

---

