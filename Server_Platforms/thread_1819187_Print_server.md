---
title: "Print server"
date: 2011-08-05
forum: Server Platforms
---

### Post by gameguy on 2011-08-05
I was trying to set up a ubuntu 11.04 distribution as a print server. There will be clients running windows 7 home premium and 1 running mac OSX. I was wondering how to set it up to make it accesible by the other computers.

Here's what I've found from googling (all the tutorials seem to be outdated)
The server IP is 192.168.1.2
This is where I see the printer from the server machine:
[http://localhost:631/printers/Deskjet-F300-series](http://localhost:631/printers/Deskjet-F300-series)

So basically, how do I set up the server and what address do I type in to connect to the server?

---

### Post by HermanAB on 2011-08-06
You run system-config-printer.  That's all.


The CUPS system is a print server, you don't need anything else.

[http://www.aeronetworks.ca/howtos/print-howto.html](http://www.aeronetworks.ca/howtos/print-howto.html)

---

### Post by gameguy on 2011-08-07
That looks like it would only work with ubuntu as the client (and maybe mac OSX). The clients will be running windows and mac OSx.

---

### Post by HermanAB on 2011-08-07
From Windows, you just connect to the Linux machine IP address using the IPP protocol and the printer name.  You don't even need a printer driver.  Linux makes all printers look like postscript printers, so you can use a generic Apple Laser Writer III driver (A is at the top of the list in Windows).

So, as I said, you don't need anything else.

---

### Post by SeijiSensei on 2011-08-07
> **HermanAB said:**
> From Windows, you just connect to the Linux machine IP address using the IPP protocol and the printer name.  You don't even need a printer driver.  Linux makes all printers look like postscript printers, so you can use a generic Apple Laser Writer III driver (A is at the top of the list in Windows).

So, as I said, you don't need anything else.

I wish it were that easy.  Last I looked the Apple Laser Writer driver was removed from Windows 7.  Some alternatives I see suggested in other forums include the generic driver from Adobe (now some nine years old), the "MS Publisher Color Printer" driver, or the driver for any HP printer that ends with "PS" in its name.

Why Microsoft doesn't just ship a generic PS driver is beyond me.  It must have to do with licensing or MS's desire to dump as many support issues as possible onto the hardware manufacturers.

---

