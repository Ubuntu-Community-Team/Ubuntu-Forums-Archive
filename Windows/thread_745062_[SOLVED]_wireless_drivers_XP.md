---
title: "[SOLVED] wireless drivers XP"
date: 2008-04-04
forum: Windows
---

### Post by insane_alien on 2008-04-04
so, i'm trying to fix my neighbours laptop it needed a clean install of XP so i've been driver hunting for a while already. i've got everything bar the wireless card. i have no idea what it is.

the ubuntu livecd uses the rt73usb driver as far as i can tell. how can i find a driver that will work in XP with it?

---

### Post by Battie on 2008-04-04
Someone at work just showed me this trick:

-Open your device manager, and go to the properties of the unknown device.

-Go the details tab and look at the long string that describes the device.

-In this string, there should be a vendor ID (VEN) and a device ID (DEV).  Look them up here: [http://www.pcidatabase.com/](http://www.pcidatabase.com/)

-Now you know which drivers to download!

For example, my network card shows this string: PCI\VEN_14E4&DEV_1677&SUBSYS_01AD1028&REV_01\4&117729E2&0&00E0

So, I look up 14e4 in the vendor search.  This correctly takes me to a Broadcom listing.  Now I look for 1677 in the list.  It says my card is a NetXtreme Gigabit Ethernet PCI Express, which is exactly right!

It's a very handy tool for those frustrating mystery devices.  I hope you find it useful too!

---

### Post by rickyjones on 2008-04-04
What kind of laptop is it? Who makes it? Does it have a service code or anything similar?

For example, my Dell has a nice service tag on it. I go to the website and type in the service tag and it brings up my exact laptop and all the hardware that is in it, along with driver download links.

Have you tried that route?

-Richard

---

### Post by insane_alien on 2008-04-05
okay, i tried this out and there is no 'details' tab, only 'general' and 'driver'

---

### Post by Battie on 2008-04-05
Hmm, that's very odd.  There is a chance you can find the device unders Start-->Accessories-->System Info and get the PnP device ID, but I'm not sure if that one shows unknown devices.

---

### Post by myusername on 2008-04-05
right click my computer> properties>device manager> whatever the device> update driver( or something of the sort) and use this driver (the .inf file) and all should be well

---

### Post by insane_alien on 2008-04-06
okay, i got it working with the statr/acessories... thing. turns out its a ralink usb adaptor(even though it is an internal device)

---

### Post by myusername on 2008-04-06
> **insane_alien said:**
>  turns out its a ralink usb adaptor(even though it is an internal device)

wow thats wierd

---

### Post by insane_alien on 2008-04-06
yeah, no kidding. now i just got to remove the 12+  drivers i installed from false leads.

---

