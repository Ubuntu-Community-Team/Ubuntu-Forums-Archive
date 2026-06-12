---
title: "Adding USB Drivers"
date: 2010-07-24
forum: Ubuntu Dev Link Forum
---

### Post by w2vy on 2010-07-24
I have a i.MX51 (arm) based system. Sharp PC-Z1 and I am
trying to get a USB Dongle WIFI working.
(The internal one died)

The usb stick is a RT2870 device and the system does have
/lib/firmware/rt2870.bin

It also has /usr/src/linux-headers-2.6.28-15-araneo/drivers/staging/rt2870

Makefile and Kconfig

but that is all. no rt2870sta.ko etc

Is it possible I have enough on the system to complete the generation of the needed file to enable this device?

It's Ubuntu 9.04

tom
---

Well it turns out the syste, had gcc/ld and full kernel headers
I followed directions that came with the driver source from the vendor (rtlink)
and it builds fine but the driver does to activate when I plug the device in.
--
The Driver did not have my USB ID in it; found the table in the source and now the device is seen (in my case a macro USB_DEVICE)

Now to get the network manager to see it...
---
My device US was 148f:3070 and I found a 3070 driver on the RAlink site.
I also switched to WICD

---

