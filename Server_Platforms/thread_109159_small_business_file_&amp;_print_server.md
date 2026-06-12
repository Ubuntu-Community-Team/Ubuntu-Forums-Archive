---
title: "small business file &amp; print server"
date: 2005-12-27
forum: Server Platforms
---

### Post by Zelut on 2005-12-27
I've been comissioned to setup a small business network but I thought I'd get your advice on a few issues.

I need to setup (preferably) a Ubuntu central server for file & print sharing.  This server will need to have four printers connected to it, have a shared documents folder & maintain regular backups (probably via cron).  I understand I'll need to use Samba for the sharing but this is where I'm potentially stuck..

Two of the printers that need setting up do NOT have Linux drivers.  If these are connected to the central server will they be able to be publicly shared despite not having PostScript drivers for Linux?  The clients in the office are all notebooks so connecting to these machines isn't the best option.

Any tips are greatly appreciated.
Cheers

---

### Post by amohanty on 2005-12-28
> Two of the printers that need setting up do NOT have Linux drivers.

If they are PCL printers, you can set them up with generic PCL drivers and they should work via CUPS and generic MS drivers (I think its called MS Publisher ....) on the laptops. As long as your requirements are restricted to basic printing it should work. 

Also look here for some more info on setting up PCL printers.
[http://www.linuxprinting.org/](http://www.linuxprinting.org/)
[http://www.linuxprinting.org/till/printing-tutorial/tut.html#1_1_4](http://www.linuxprinting.org/till/printing-tutorial/tut.html#1_1_4)

HTH
AM

---

### Post by Zelut on 2005-12-28
I've checked out linuxprinting.org searching for drivers for these two and one isn't listed.  The one I can't find on linuxprinting.org is a Sharp AR-M237 (office printer/copy/scanner).  I'll read up on the second link you sent & see if I can find anything to use as far as PPD.

---

### Post by amohanty on 2005-12-28
Have you looked here:

[http://www.sharpusa.com/products/applications/linux_mac_unix/1,2728,2-7,00.html](http://www.sharpusa.com/products/applications/linux_mac_unix/1,2728,2-7,00.html)

[google]("http://www.google.com/search?sourceid=mozclient&ie=utf-8&oe=utf-8&q=Sharp+AR-M237+linux")

---

### Post by nursegirl on 2006-02-14
For some reason, the Sharp Canada site has the driver, although the SharpUSA doesn't.

[http://www.sharp.ca/downloads/](http://www.sharp.ca/downloads/)

Then go to Copiers-> Sharp AR-M237 and the second choice is the Linux one.  When I was installing a Sharp copier at my workplace, the only issues that came up were:
1) The file I downloaded was an exe, and I had to rename it and unzip it to be able to pull out the ppd
2) All of the documentation said that it was a CUPS printer, but I could only get it to work by calling it an LPR printer.

Hope this helps!

---

