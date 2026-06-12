---
title: "Qjackctl usb audio freezes the system"
date: 2012-12-14
forum: Ubuntu Studio
---

### Post by jfde on 2012-12-14
Hello everybody,
I have ubuntustudio 12.10 installed on core i7  ASUS U36SD laptop with 4 GB RAM 
When I tried the distribution without installing everything worked fine so I decided 
to install the distribution.
Sadly I had to find that with the standard distribution kernels,  whenever I started Qjackctl with any USB AUDIO device the system just  freezed without any warning and I could read nothing about it from the  logs.
I went searching for an rt kernel so I downloaded and compiled it from  source and installed it (version 3.6.7-rt18). The exact same issue is  happening but I was able to soft reboot and to find that the problem is  related to ehci and irq23 which apparently conflict
and freeze the kernel...
Any of you guys have any clue?

thank you):P

---

### Post by jejeman on 2012-12-14
Try to change USB port.

---

### Post by CrocoDuck on 2012-12-16
Hi. If the changing of the USB port is not effective you could try, carefully, by setting IRQs with your BIOS, if it lets you to do those regulations.

---

