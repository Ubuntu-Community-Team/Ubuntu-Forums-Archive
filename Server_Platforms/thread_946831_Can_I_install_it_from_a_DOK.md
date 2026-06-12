---
title: "Can I install it from a DOK?"
date: 2008-10-13
forum: Server Platforms
---

### Post by tehshay on 2008-10-13
Hi there
I have on my home server windows server 2003 for the last 3 years, but now I want to move to Linux-Ubuntu, server edition.
Problem is, that I don't have any CD-ROM drives on that server, all I have is the windows server 2003 installed currently (which I want to uninstall, completely move to linux), and I also have a decent disk on key, 8 GB U3 support etc... 

Can I fully install it on my hard-disk from using the DOK?

Thanks

---

### Post by lykwydchykyn on 2008-10-13
Yep, check this out:

[http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/](http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/)

You can also use PXE boot if you have another box around to run dhcp/tftpd

also, check this out:

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by tehshay on 2008-10-13
>  without installing to a fixed internal system disk.
but that's what i want... i don't want it to stay on the DOK....
I want to install ubuntu on my internal hard-disk, i can't do it normally because i don't have any CD-ROM installed.

---

### Post by lykwydchykyn on 2008-10-13
Once you create a bootable USB device, it's like booting to the liveCD; you can install it from there just like the CD.  Probably unetbootin is the one you want.  It allows you to make any USB drive into a bootable "live CD" device.

---

