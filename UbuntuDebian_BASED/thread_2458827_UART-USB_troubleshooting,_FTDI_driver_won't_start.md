---
title: "UART-USB troubleshooting, FTDI driver won't start"
date: 2021-03-04
forum: Ubuntu/Debian BASED
---

### Post by alfredoraymundo on 2021-03-04
Hello,

I am trying to get the system to recognize the FTD2XX driver for an FT232 UART-USB interface to work (Linux has the FTDI_SIO driver built in kernel, but is not compatible). I followed the instructions to install the driver and to use
```
sudo rmmod ftdi_sio

sudo rmmod usbserial
```

But right after I unload the drivers nothing happens. I don't know how to tell the system to use the FT2XX driver or if it should be automatic and I messed up the installation.

Help is very much appreciated.

---

