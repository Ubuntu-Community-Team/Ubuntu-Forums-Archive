---
title: "CUPS info request"
date: 2013-01-12
forum: Server Platforms
---

### Post by ranger12 on 2013-01-12
Hello gentlemen, I do not have a problem - I just want some information.

Epson Workforce 545
Ubuntu 12.04.1 server
Cups is configured and the printer is going wireless.
I have a client workstation using Ubuntu 12.04.1 Desktop. I have the printer hooked up and running as a remote printer so I can send jobs from the client. I am just simply wondering this. The printers.conf file has the device uri as lpd://xxx.xxx.xxx.xx:515/PASSTHRU but on the client the device uri is ipp://sxxx.xxx.xxx.xx:631/printers/EPSON_WorkForce_545. Everything works fine so I am going to let it be. I was just wondering if someone could shed some light on this - that's all. I do understand basically what ipp and lpd are.

---

### Post by Cheesehead on 2013-01-13
ipp (internet printing protocol) and lpd (line printer daemon) are two different ways to communicate with a printer.

See [http://en.wikipedia.org/wiki/Internet_Printing_Protocol](http://en.wikipedia.org/wiki/Internet_Printing_Protocol)
See [http://en.wikipedia.org/wiki/Line_Printer_Daemon_protocol](http://en.wikipedia.org/wiki/Line_Printer_Daemon_protocol)

---

### Post by ranger12 on 2013-01-13
I appreciate your trying to help and no offence but I already know what the two protocols are.  I am asking is why the server is configured with lpd and the client with ipp and this seems to work.  I do thank you for trying though.

---

### Post by Cheesehead on 2013-01-13
lpd://xxx.xxx.xxx.xx:515/PASSTHRU is the printer the local CUPS backend uses when printing.

ipp://sxxx.xxx.xxx.xx:631/printers/EPSON_WorkForce_545 makes the printer available to other machines on the network.

---

### Post by ranger12 on 2013-01-13
Now that is what I was looking for, thank you very much.

---

