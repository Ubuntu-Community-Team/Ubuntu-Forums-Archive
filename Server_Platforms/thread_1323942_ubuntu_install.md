---
title: "ubuntu install"
date: 2009-11-12
forum: Server Platforms
---

### Post by Fenix1 on 2009-11-12
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

### Post by silvernewt on 2009-11-12
you can still access the web interface through lynx if it makes things easier for you..?

apt-get install lynx

lynx 127.0.0.1:631

or....

you can open up the admin pages to other machines on the local network by editing /etc/cups/cupsd.conf and changing Allow localhost to Allow @LOCAL and then connect to your server machine on port 631.

# Restrict access to the admin pages...
<Location /admin> 
  Order allow,deny
  Allow localhost
</Location>

just remember to change it back to Allow localhost once you're done. that's how i managed to configure my canon IP2000 as a network printer.

---

### Post by Fenix1 on 2009-11-13
> **silvernewt said:**
> 
or....

you can open up the admin pages to other machines on the local network by editing /etc/cups/cupsd.conf and changing Allow localhost to Allow @LOCAL and then connect to your server machine on port 631.


How do I connect to my server machine? Put the ip address in my web browser? 10.10.10.10:631 for example?

---

### Post by aquavitae on 2009-11-13
> **Fenix1 said:**
> How do I connect to my server machine? Put the ip address in my web browser? 10.10.10.10:631 for example?
That should work - try it!

---

