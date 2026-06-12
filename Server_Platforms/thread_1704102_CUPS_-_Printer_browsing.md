---
title: "CUPS - Printer browsing"
date: 2011-03-10
forum: Server Platforms
---

### Post by Herazio on 2011-03-10
Dear all

I seem to be having (another) problem with CUPS. In windows it is possible to setup a central print server which users can connect to and has printers from all over the network on it.

People just type in **\\printsrv **and they can see all the printers on the network, double click on the one that they need and they can print.

I'm trying to find an equivalent to Linux for this. I've tried to access it the regular way via a samba windows share and was hoping I would see all the printers. Instead I saw all the drivers and not the devices.

So I was wondering, IS there even an alternative to this method used in Windows ? It would be handy so users don't have a lot of trouble configuring the printer they need.

Thanks in advance hope to hear from you

---

### Post by mciverza on 2011-03-10
Hi, you got the subject line correct. It is a CUPS browsing feature.

To enable browsing of other printers (and publishing of your own shared printers) via CUPS:

Open the cups admin application via the top menu System -> Administration -> Printing
(you will be asked to put in your login password, because you are about to make system changes)

In the window that opens, select the "Server" menu, and choose "Settings".
Tick "Show printers shared by other systems"
and tick "Publish shared printers connected to this system"
(it shouldn't be neccessary to tick the sub-option relating to "internet")

Click "OK" and you're done. After a while the list of printers will be auto-populated.

---

### Post by Herazio on 2011-03-10
Hi MCIVersa

Thanks so much for the reply that works great ! 

The only problem I still have is that I have no idea how to add the printers from the windows network into the CUPS server. But I guess I could try to create a script that reads a file with the printernames on the network and use a generic printer driver.

Once again, thanks so much for all of your help and have a nice day !

Herazio

---

