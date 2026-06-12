---
title: "possible to create 2 startup discs on one usb?"
date: 2011-05-05
forum: The Cafe
---

### Post by polardude1983 on 2011-05-05
I am just wondering if there are any possibilities that I can install a startup disc of Ubuntu 10.04.2 and Ubuntu 11.04 on one 8 GB USB.

Are there any pros and cons to this? is it possible?

Should I do it? how to do it?

---

### Post by wilee-nilee on 2011-05-05
> **polardude1983 said:**
> I am just wondering if there are any possibilities that I can install a startup disc of Ubuntu 10.04.2 and Ubuntu 11.04 on one 8 GB USB.

Are there any pros and cons to this? is it possible?

Should I do it? how to do it?

Pendrivelinux has a multiboot install there is a windows version and a linux one for loading here is the page for the Windows one at the bottom of the page is the Linux version. Personally I have used both and find the Linux one easier. But make sure you format the thumb with gparted it seems to only like that formatting.
[http://www.pendrivelinux.com/yumi-multiboot-usb-creator/](http://www.pendrivelinux.com/yumi-multiboot-usb-creator/)

I have a 16 gig thumb that has 3 av programs the W7 install disc, and the last 3 Ubuntu releases, and other OS's, on it and has about 6-8 gigs still free. This is a great way to have your toolset in your pocket.

---

### Post by Retlol on 2011-05-05
You can do it with grub 2 (default in ubuntu).

Fast and easy.

[http://www.panticz.de/MultiBootUSB](http://www.panticz.de/MultiBootUSB)

---

### Post by wilee-nilee on 2011-05-05
> **Retlol said:**
> You can do it with grub 2 (default in ubuntu).

Fast and easy.

[http://www.panticz.de/MultiBootUSB](http://www.panticz.de/MultiBootUSB)
+1 I have used a number of cli base loaders as well, I'm a sucker for a shiny gui though.

---

### Post by ssam on 2011-05-05
I use this script
[http://blog.cyphermox.net/2010/10/booting-to-iso-images-from-usb-key.html](http://blog.cyphermox.net/2010/10/booting-to-iso-images-from-usb-key.html)

there is an iso directory on the USB stick. each time i add or remove an .iso from the folder i rerun the script to update its grub.

---

