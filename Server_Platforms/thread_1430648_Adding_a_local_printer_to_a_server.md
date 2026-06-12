---
title: "Adding a local printer to a server"
date: 2010-03-15
forum: Server Platforms
---

### Post by poltr1 on 2010-03-15
I'm running Karmic server on a Gateway E-4000 box.  Last week, I plugged in an HP LaserJet 4050n printer to the 25-pin printer port (what the Windows folks would call "LPT1").  I'd like to set this up as a print queue that can be shared on the local network.  

I know I need to make changes to /etc/cups/cupsd.conf to define the print queue, but I can't seem to find what those commands are.  I'm running samba and have already edited /etc/samba/smb.conf accordingly.

Thanks in advance for your help.

---

### Post by johnson.d on 2010-03-16
1) Karmic server configuration.

i) Installing CUPS.

CUPS can be installed in your Karmic server machine using the following command:

$ sudo apt-get install cups

ii) Now to enable the remote administration of cups using web interface, you need to use the following command:

$ sudo cupsctl --remote-admin

You can now use the browser from a remote machine to configure cups through web interface. The link can be accessed using the url http://<ip-address>:631.

iii) Finding the link you need to use for configuring the printer in other operating systems:

You can goto the url http://<ip-address>:631 in a remote machine. Goto Administration in the web page and click Manage printers. It will be showing the printers as links. Right click on the relevant link and click copy link location and note down the URL, because it is needed while configuring this printer in other machines.

2) Configuring a windows machine to print from this CUPS server:

i) Goto start menu -> Printers and faxes -> Add a printer
ii) Select "A network printer, or a printer attached to another computer" and click next
iii) Select "Connect to a printer on the Internet or on a home or office network" 
iv) Enter the URL you have noted down in the windows system and click next
V) It will be showing a window to install the drivers either by selecting in the list or from a disk (you can choose your option)
vi) After installing the drivers you can select between setting this printer as default or not
vii) Click finish

3) Configuring a Ubuntu Desktop to print from this CUPS server:

i) Goto Gnome menu-> System-> Administration-> Printing. A window will open.
ii) Click on 'New', A window will open
iii) At the 'Device url' you can paste the URL that is already noted down.
iv) Now it ask for driver installation.
v) You can install appropriate driver and you can now try printing from the Ubuntu machine

---

### Post by poltr1 on 2010-03-16
It took a little bit of digging to find the printer once I clicked on "Add printer", but I found it and added the print queue to the server.

Thank you for your help!

---

