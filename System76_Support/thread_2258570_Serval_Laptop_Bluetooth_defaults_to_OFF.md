---
title: "Serval Laptop Bluetooth defaults to OFF"
date: 2014-12-28
forum: System76 Support
---

### Post by mindpoem on 2014-12-28
I'm trying to get bluetooth to default ON when I reboot my System76 Serval Professional laptop using Ubuntu 14.10.  I'm using an external monitor and bluetooth keyboard and currently every time I reboot I must open the lid of the laptop and push Fn-F12 to turn on the bluetooth adaptor...???

My /etc/bluetooth/main.conf file has both of these settings so it seems like the system should default to bluetooth being ON already:
InitiallyPowered = true
RememberPowered = true

Thanks in advance for any help on this,
Mike

---

### Post by jbelmonte on 2014-12-29
From [https://system76.com/support]("https://system76.com/support")

Turn on Bluetooth

Press Fn+F12 to toggle your laptop’s Bluetooth adapter. If you see a Bluetooth icon in the top-right, the adapter is on. If not, the adapter is off.

-------------------------------------------

I believe the Fn+F12 is a hardware switch. if so, then until the Bluetooth adapter is hardware enable by Fn+F12, the kernel can't see the Bluetooth adapter or toggle Bluetooth on/off via a software command. I don't know if there is a BIOS setting for the Bluetooth or if there is a switch on the Bluetooth adapter itself to determine its initial state. I suggest opening a support ticket with System76 so they can answer this question for your specific hardware.

---

