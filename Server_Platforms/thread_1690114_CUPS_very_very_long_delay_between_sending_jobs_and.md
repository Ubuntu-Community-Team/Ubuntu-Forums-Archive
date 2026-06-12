---
title: "CUPS very very long delay between sending jobs and printing"
date: 2011-02-17
forum: Server Platforms
---

### Post by gtkrab on 2011-02-17
Hi,

I've set up a cups printing server using ubuntu 10.04.1 LTS. The printer's a HP Laser Jet 1018

I can connect to it over vpn using openvpn from my netbook which is also running ubuntu 10.04.1. I can connect to the printer all right and test page prints without a problem. 

But if I try to print anything else, it take at least 5 minutes before the job is successfully send and printed out. 

Also, on the client side, for example, the file size would like 500k, and when it finally prints out, the file size on the server side is less than 10k. 
The file is a black and white document, and from what I can tell, the printed page is not missing any information. 

Wonder what's the problem?

Thanks in advance.

---

### Post by elico on 2011-02-18
over VPN ? why?
the cups print server takes more then any windows print server for my usb printer but it' not 5 minutes.

you should try to copy the file to the server and on the server to print it.

how did you setup the cups server and client?

---

### Post by gtkrab on 2011-02-19
well, the server's running unbuntu 10.04, and I just plugged in the printer using usb and use the cups web interface to install driver, oh yea, I use the hplib provided by hp to install the driver.
for the client, I just use the gnome interface to connect to the printer using ipp protocol. 
I'm sure there is a way, but I haven't figure out how to have user control for cups, since anyone can just connect to the printer. So I hided it behind a router and use vpn to connect to it. kind of a cheap way out. 
it worked smoothly before, ever since I tried to connect my windows machine to the printer using samba, the cups stopped working correctly. 

Hope this answers your question. 
thank you for ur time.

---

### Post by crogers on 2011-06-23
I found this thread while researching a problem of my own.  I'm here to add more info about the possible problem, not to offer a solution:

I have installed Ubuntu 10 and now have 11.04.  When I upgraded to Ubuntu 10, my HP 1200 LaserJet began working very slowly.  The HPLIP Printer Test Page takes 50 seconds to start printing.  JPG files and  PDF files sometimes print eventually.  This printer used to work fine with Ubuntu 9.10.  It still works fine with Windows XP.  

I think something was lost in the upgrade from previous Ubuntu / CUPS/ HPLIP versions.  I have un-installed and re-installed HPLIP.  I have removed and re-installed the printer.  No changes in the performance.    At least two of us need help on this issue. :confused:

---

### Post by walterbyrd on 2012-05-02
I am having the same problem with my HP-3015. 

Everything worked fine with Ubuntu 10.4. 

I wonder if it would help to go back? Or, is this a problem with the new CUPS?

---

