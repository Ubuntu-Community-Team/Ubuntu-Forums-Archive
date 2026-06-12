---
title: "CUPS Print Server - Print from Windows"
date: 2008-05-21
forum: Server Platforms
---

### Post by snuza on 2008-05-21
Hi, i've managed to set up an Ubuntu server (8.04) on my LAN and connect a printer to it (HP DeskJet 990C) and successfully print a test page. I can manage CUPS from any PC within the LAN and I can see the printer on the Ubuntu server from a windows machine... but i cannot seem to configure the windows machine to use the printer. I've followed just about every document i can find on this but to no avail. Under Win, I've tried to use the Have Disk option and chosing the right .inf file when installing the driver but it comes back with an error about it not containing information about my hardware.

Any help or direction to previous articles (although i've probably read it), would be greatly appreciated.

BTW, [https://help.ubuntu.com/community/NetworkPrintingFromWinXP](https://help.ubuntu.com/community/NetworkPrintingFromWinXP) doesn't work for me - anyone had success with 8.04?

Greg

---

### Post by HermanAB on 2008-05-21
Linux makes any printer look like a Postscript printer.  So instead of trying to install the correct driver on Windows, simply tell Windows that it is an Apple Laser Writer II or III and it should be happy.

Cheers,

Herman

---

### Post by snuza on 2008-05-22
Thanks Herman... but it didn't work. Tried the Apple driver but no luck. I downloaded a universal HP postscript printer driver but Windoze still tells me there's a print driver setup error. I'm off to buy a razor blade ;)

Is anyone else printing from Windows to an Ubuntu print server? There seems to be a lack of documentation on how to acheive this. Lots of info, but most of it lacking sufficient explanation, conflicting or pure hacking of the .conf files but nothing that actually works (for me anyway). Most frustrating!

---

