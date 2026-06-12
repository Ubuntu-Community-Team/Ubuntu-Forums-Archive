---
title: "Accessing USB serial ports"
date: 2009-11-23
forum: Wine
---

### Post by sjbaugh on 2009-11-23
I have a device which contains a USB serial port (ftdi FT232). Ubuntu sees this and presents it as /dev/ttyUSB0. I can access this through Linux programs (Ubuntu Karmic 64 bit).

I need to access this from a number of existing Win32 programs running under Wine (1.0.0.1 from the repository). These see the hardware COM1 and COM2 ports but I havn't found a way yet of connecting to the USB port.

Is there a ay to do this (even at the expense of re-assigning the COM1 or COM2 ports - /dev/ttyS0 etc)?

Thanks

Steve, England

---

### Post by Sisophon2001 on 2009-11-23
wine does not support USB drivers, but if your device is being recognised as a serial device, and I think it is, then you need a symbolic link between com1 and /dev/usb and it must be in the folder ~/.wine/dosdevices

This will allow windows programs running under wine to see usb serial devices. I use a usb GPS with wine.

This should do it.

ln -s /dev/ttyUSB0 ~/.wine/dosdevices/com1

see
[http://ubuntuforums.org/showthread.php?p=4969966#post4969966]("http://ubuntuforums.org/showthread.php?p=4969966#post4969966")

Garvan

---

### Post by sjbaugh on 2009-11-23
Garvan,

Thanks for that tip! I shall try it this evening.

Steve

---

### Post by sjbaugh on 2009-11-23
Garvan,

Thank you, it worked!

When one tries something different one learns a bit more.


Best wishes,

Steve

---

### Post by isaacalves27 on 2011-01-13
Thank you so much  :) It worked as a charm ;)

---

### Post by orlandocarguy on 2011-10-04
YES! This solved my problem too... trying to get a G-Tech Pro to connect through a USB-to-serial adapter: 

[http://ubuntuforums.org/showthread.php?p=11311366](http://ubuntuforums.org/showthread.php?p=11311366)

It worked! Thanks all for the help!

---

