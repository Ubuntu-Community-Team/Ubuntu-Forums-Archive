---
title: "Is it possible to..."
date: 2009-06-13
forum: The Cafe
---

### Post by heroidi on 2009-06-13
Is it possible to print from virtualbox?

---

### Post by yabbadabbadont on 2009-06-13
Yes.  Assuming that Linux can see the printer that is.

---

### Post by heroidi on 2009-06-13
the printer doesn't work on ubuntu

---

### Post by yabbadabbadont on 2009-06-13
It doesn't have to.  At least, you don't have to have a working linux driver for it.  It just has to be seen at the device level as a printer.  Does it show up in your dmesg output as a printer?  If so, you should be able to print to it from inside of virtualbox or vmware.

---

### Post by cariboo on 2009-06-13
Yes, I've been printing quite a bit in the last couple of weeks. My Epson R340 is connected to a computer running XP. I found that Win 7 doesn't have legacy drivers for my HP 5P, so I can't use my laser printer. :( from Win 7, it works perfectly from Karmic.

---

### Post by heroidi on 2009-06-13
i'll have to wait until caramic maybe until my driver works it's a hp laserjet 1000

---

### Post by cariboo on 2009-06-13
You can get drivers for you printer directly from HP. If you have the guest extensions installed you can use the usb ports to connect your printer. you will even be able to use the Windows drivers if you are running XP, VIsta or Win 7.

---

