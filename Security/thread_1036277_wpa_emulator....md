---
title: "wpa emulator..."
date: 2009-01-10
forum: Security
---

### Post by zander1013 on 2009-01-10
hi,

i have an older laptop (circa 2003) that does not have wpa on the wifi card. are there any wpa emulators available?

please advise.

-zander

---

### Post by wirelessmonkey on 2009-01-10
wpa needs to be supported by the wireless card driver/firmware, I don't believe that it is possible to emulate.

---

### Post by hyper_ch on 2009-01-11
you could buy a usb wifi device that supports wpa...

---

### Post by brian_p on 2009-01-11
> **hyper_ch said:**
> you could buy a usb wifi device that supports wpa...

Or even a PCMCIA card, if there is a slot to use. Both options are not expensive but look for a card/usb device with a supported chipset.

---

### Post by kevdog on 2009-01-11
Atheros chipset are the most versatile in my opinion, and in addition I would suggest a pci/pcmcia card over a USB dongle if possible depending on your hardware. These devices are far better supported than USB devices.

---

### Post by hyper_ch on 2009-01-11
then one usb dongle I got for free has worked in hardy and ibex out of the box :)

---

### Post by brian_p on 2009-01-11
> **hyper_ch said:**
> then one usb dongle I got for free has worked in hardy and ibex out of the box :)

A technical detail or two for posterity?

---

### Post by kevdog on 2009-01-11
You can do monitor mode with the Usb dongle?

---

### Post by hyper_ch on 2009-01-12
no clue about monitor mode... gave it to my mom

The model is a Netopia USB Wireless LAN Card
Model: TER/GUSB-E
P/N: 8960049-00-01

and lsusb returns:
```

Bus 005 Device 003: ID 148f:2570 Ralink Technology, Corp. 802.11g WiFi

```

---

### Post by kevdog on 2009-01-12
hyper_ch

Ra chipset -- Very cool -- I think that can do monitor mode, however since I don't own a Ra chipset, have never tried.

---

