---
title: "UBUNTU UDEV RULES for USB ports question..."
date: 2012-07-08
forum: Ubuntu Application Development
---

### Post by tester100 on 2012-07-08
Hi guys

i have some questions abou the UDEV functions on ubuntu.

currently i am running a server machine ubuntu-server 10.04LTS x64 environment.

here is the deal

currently using

1 usb keyboard
1 usb mouse 
3 pcsc card readers USB

problema happens sometimes i end up loosing conection in some reader os usb device and my applications show me the information that my USB card reader or device is off, and when i run pcsc_scan it also shows that the card is unknown or not responsive , so i eventually have to restart PCSCD via init.d.

problem is that most of the times after restarting pcscd everything comes up mixed up with different USB device ID numbers.

that is a pain in the BUT once my software is detecting cards via DEVICE ID configured manually due to different ATR structures on the cards , and some extra unique information from each card.

not to mention sometimes my usb keyboard or mouse stop working also due to mixup of device id.


So my general question now, how can i solve this buzzup/cockup using UDEV rules, to make each USB device fix id , so even if i restart the PCSCD aplication this won´t mess up with my USB devices configuration?

any ideas or hints???

PS-Same thing happens if i restart my machine, after restarting all events sometimes my USB keyboard or mouse or reader come up with different devices iD usb...

hints or ideas are welcome.

thanks
Tester100

---

