---
title: "CUPS conversion"
date: 2009-10-28
forum: Server Platforms
---

### Post by baggus on 2009-10-28
Dear Community,

At the office we have this usb laser printer, it's working great, it's just the windows drivers that are doing my head in.
The Windows drivers support no form of networking whatsoever, so I can't share them from one Windows PC to the other. Other than that they are also conflicting with other software.

The Linux drivers are a different story. 
After installing those on our Ubuntu server, CUPS detects the printer and I can print test pages and pdf files from the commandline.

This printer will have to be used by lots of people from lots of locations, so a CUPS print server would be the obvious choice for me, and this would've worked out fine if it wasn't for the dodgy Windows drivers that won't let me use a port connected to CUPS.

What I am trying to accomplish here:
Create a virtual printer in CUPS that works with standard Windows drivers, and have that virtual printer forward it's jobs to the printer with the troublesome Windows drivers.

What I have set up so far:
A virtual pdf printer in CUPS that acts as a HP Laserjet 1200 and prints all jobs to /opt/pdf/
A commandline script that checks /opt/pdf/ every second for a new .pdf and then prints it to the usb printer.

This however, as you may understand, is a very dirty workaround, and there must be a better way to accomplish the same.

Any and all help is greatly appreciated!

Thanks in advance for looking into this.

---

