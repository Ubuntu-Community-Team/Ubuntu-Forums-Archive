---
title: "VirtualBox won't detect USB modem."
date: 2013-08-16
forum: Virtualisation
---

### Post by emptycoder on 2013-08-16
Hi eveyone, here's my problem
I have a WiMax USB Stick which I use to connect to Internet, it works well on Windows but unfortunately it doesn't work on Ubuntu, so I though of using VirtualBox with Windows as a Guest and use WiMax from there then share the connection with the Host (Ubuntu)
I installed Windows with no problem,but for some unknown reason the WiMax USB refuses to work on VirtualBox, the list of USB devices are shown except the WiMax, it shows as greyed text with state: unavailable.
I searched around the Internet and tried every trick and yet nothing works.
Here's what I have done so far:
I installed VirtualBox [COLOR=#444444][FONT=arial]PUEL[/FONT][/COLOR], not OSE (Because OSE Edition doesn't support USB Devices)
I installed VirtualBox Extention Pack
I Installed Guest Additions
I enabled USB Controller, USB 2.0 (EHCI) Controler and adding USB filter
I added username to vboxusers
I changed windows xp with windows 7 but same problem occurred
I even tried to run VirtualBox as root, I found the USB but when I enable it the whole VirtualBox freezes and nothing happens, I waited like forever! I tried to click and enable it again and message shows up (Another USB is been installed an need to wait)
What am I doing wrong? I'm no expert so I don't know that much, could someone please provide any help.

Here's my liusb

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 0c45:641d Microdia 1.3 MPixel Integrated Webcam
Bus 002 Device 003: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 002 Device 004: ID 413c:8161 Dell Computer Corp. Integrated Keyboard
Bus 002 Device 005: ID 413c:8162 Dell Computer Corp. Integrated Touchpad [Synaptics]
Bus 001 Device 004: ID 2188:0ae1  
Bus 002 Device 007: ID 198f:0220 Beceem Communications Inc. BCSM250 WiMAX Adapte

Thanks a lot

---

### Post by emptycoder on 2013-08-16
Anyone?

---

