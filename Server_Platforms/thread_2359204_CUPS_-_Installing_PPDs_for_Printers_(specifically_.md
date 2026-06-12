---
title: "CUPS - Installing PPDs for Printers (specifically Samsung 332_ Series)"
date: 2017-04-21
forum: Server Platforms
---

### Post by objr.jtree on 2017-04-21
Hi,

First I apologize if this post is in the wrong category, I think I'm in the right place, but if not please move it to the correct category.

I'm using Ubuntu 16.04 LTS Server for a CUPS server. I use the web-interface to add printers using the following steps: Add Printer -> ipp -> socket://PRINTER-NAME -> I select the Make of the printer, in this case Samsung, but it doesn't have the correct model which is a 332_ Series. I found Linux drivers for it from Samsung ( uupd_V3.00.24_00.93.aix.tar.gz ). I transferred it to the server using a USB flash drive and *cp* it to a directory in my home directory. I used *tar -xvzf* to extract it. Once it is extracted I ran the install file it has ( *./install *) and it ran. I tried adding the printer again, but it doesn't list the correct model or any additional models to what was listed before installing the drivers. I went looking for the Samsung .ppd file I was looking for and found all kinds, including the Samsung 332_ model I need, that were apart of the uupd_V3.00.24_00.93.aix.tar.gz file in /usr/share/printnx/model directory. Does it make a difference where I extracted the uupd_V3.00.24_00.93.aix.tar.gz to and ran the ./install from? Does it need to be run for the / directory? I did reboot it, just in case, but it didn't make a difference(I didn't think it would, but it was worth a shot. "Hi, IT. Have you tried turning it off and on again?" -Roy). Any ideas?

Thanks!

---

### Post by objr.jtree on 2017-06-06
Hi,

So here's what I did to work around the fact that I couldn't find where to copy the .ppd files to: Option 1: I used the web interface and logged in and added the printer and when I arrived at the driver screen I clicked the Browse button found the correct .ppd file for the printer I was setting up and chose it, and clicked continue, and then finished installing the printer. Option 2: I copied the .ppd into a directory of a make of printers that I could find where it listed their .ppd files and added the .ppd I needed even thought it was under the wrong make it was the right model and it worked. (i.e. /usr/share/cups/ppd/KONICAMINOLTA/samsung.ppd) Doing it this way you just have to remember which Make you put it under.

---

