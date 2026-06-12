---
title: "Install printer on Ubuntu server"
date: 2009-07-24
forum: Server Platforms
---

### Post by darwinj on 2009-07-24
I am a new Ubuntu user. I am setting up an Ubuntu server for my wife's office. The office has 5 Windows XP computer. The server will be used as an internet gateway, a DHCP server, file server and print server. The place I need help is with the print server. How do I install a printer on the server? I am using 9.04 with samba, cups, LAMP, SSH and Webmin. I have 3 printers, 1 Epson impact parallel printer and 2 HP all-in-one Deskjet USB printers. I have searched the Ubuntu server guide and came up empty. What do I need to do?
Thanks,
Darwin in Brazil

---

### Post by bacil on 2009-07-24
cups how to 

[http://www.linuxprinting.org/~till/printing-tutorial/tut.html](http://www.linuxprinting.org/~till/printing-tutorial/tut.html)

---

### Post by wojox on 2009-07-24
[http://localhost:631/](http://localhost:631/)

---

### Post by kustomjs on 2009-07-24
[http://youripaddressofbox:631](http://youripaddressofbox:631) and you have to add a super admin rights to access the web gui.  also make sure you go to /etc/cups/ config file and switch it to:

config file:

# Only listen for connections from the local machine.
Listen 192.168.xx.186:631
Listen /var/run/cups/cups.sock

# Show shared printers on the local network.
Browsing On
BrowseOrder allow,deny
BrowseAllow all
BrowseAddress 192.168.xx.186

then restart the print server by: sudo /etc/init.d/cups restart

---

### Post by darwinj on 2009-07-24
> **wojox said:**
> [http://localhost:631/](http://localhost:631/)

I am running my server without a monitor. How do I use this?

---

### Post by darwinj on 2009-07-24
Thanks. This is a real learning experience. I am glad that the community is there to help.

---

### Post by darwinj on 2009-07-24
This I can follow. Thanks

---

### Post by wojox on 2009-07-24
> **darwinj said:**
> I am running my server without a monitor. How do I use this?

You never mentioned headless?

---

### Post by darwinj on 2009-07-24
> **wojox said:**
> You never mentioned headless?

Sorry, as I said, I am new to this and it slipped my mind that I am running headless. All of these new terms are hard to remember sometimes.

---

