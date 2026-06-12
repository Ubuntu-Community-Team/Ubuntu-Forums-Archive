---
title: "CUPS add printer"
date: 2009-11-12
forum: Server Platforms
---

### Post by Fenix1 on 2009-11-12
**CUPS - add printer**             
                                                                I have HP Laser Jet 1320 printer connected to my usb, and im operating ubuntu server 9.04 or 9.10 not sure. As you probably allready know, this version of ubuntu does not have a GUI so I cant access the web interfacee for CUPS. I,ve tried to add the printer via lpadmin with little success. heres what I get

lpinfo -v

...
direct usb://HP/LaserJet%201320%20series
...

lpinfo -m

...
Foomatic: HP-LaserJet_1320-Postscript.ppd HP Laser Jet 1320 foomatic/Postscript
...


Ok? So then I try to add the printer.

lpadmin -p printer1 -v //HP/LaserJet%201320%20series -m HP-LaserJet_1320-Postscript.ppd
lpadmin: Unable to copy PPD file

I am baffled, what is the problem. I apologize for lack of information. please help.

---

### Post by dgoosens on 2009-11-12
Hi Cups is accessible through
[http://localhost:631/](http://localhost:631/)

and it is much easier to install your printer through 
System > Administration > Printing

Just select new printer and select to correct model in the GUI.

---

### Post by Fenix1 on 2009-11-12
> **dgoosens said:**
> Hi Cups is accessible through
[http://localhost:631/](http://localhost:631/)

and it is much easier to install your printer through 
System > Administration > Printing

Just select new printer and select to correct model in the GUI.

I cant cause i have only command line, no GUI

---

### Post by dgoosens on 2009-11-12
server edition right ?
well then, [http://serverName:631](http://serverName:631) should still work... or not ?

[EDIT]
--> just checked this and it doesn't...
sorry

---

### Post by silvernewt on 2009-11-12
[http://ubuntuforums.org/showthread.php?t=1323942](http://ubuntuforums.org/showthread.php?t=1323942)

---

### Post by lykwydchykyn on 2009-11-12
Sorry if this is a dumb question, but are you attempting this from a root shell?  I ask because the commands you listed don't use sudo, and probably wouldn't work if run as a non-root user or without sudo.

---

