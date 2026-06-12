---
title: "Virtualbox windows 10 guest does not see UDB DVD"
date: 2022-08-16
forum: Virtualisation
---

### Post by nocom2 on 2022-08-16
I have an Ubuntu 22 host running Virtualbox (6.1.34) and Windows 10 home as guest. In the USB section I enabled USB 3.0 and created an empty filter. When I connect a DVD to my laptop the DVD is seen by Ubuntu but not by windows. What am I doing wrong?

---

### Post by SeijiSensei on 2022-08-16
Are you sure it's a USB 3.0 device? Is it connected to a 3.0 port? What if you use a 2.0 filter instead?

---

### Post by nocom2 on 2022-08-17
Good point. I am sure it is connected to a 3.0 port. As an extra check I connected a usb-stick as well and I tried all connections (usb 1.1, 2.0 and 3.0). In all cases no devices were detected.   I forgot to mention in my first message, but I have the guestadditions installed.

---

