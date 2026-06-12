---
title: "Change from Samba server to LAMP"
date: 2008-06-28
forum: Server Platforms
---

### Post by Gnome949 on 2008-06-28
Is it possible to change from a samba server to a LAMP server, because on the Ubuntu Server install i choose Samba file sharing but I would like to change it to a LAMP...
Is this only programs that are pre-installed for you or is it much deeper than that requiring a re-install? I would rather not re-install the OS.
Thank You

---

### Post by stoneybroke on 2008-06-28
There is no need to uninstall samba here is the description of what samba does.

a LanManager-like file and printer server for Unix 
The Samba software suite is a collection of programs that
implements the SMB/CIFS protocol for unix systems, allowing you to serve
files and printers to Windows, NT, OS/2 and DOS clients. This protocol
is sometimes also referred to as the LanManager or NetBIOS protocol.

all you need to do is enter sudo tasksel wait then select the server stuff you want to install or remove from the menu

---

### Post by Lapp-Same on 2008-06-28
> **Gnome949 said:**
> Is it possible to change from a samba server to a LAMP server, because on the Ubuntu Server install i choose Samba file sharing but I would like to change it to a LAMP...
Is this only programs that are pre-installed for you or is it much deeper than that requiring a re-install? I would rather not re-install the OS.
Thank You

No, its LAMP-Server is a kinda "Package"

but just type ```
sudo apt-get install lamp or lamp-server
```
in terminal...

---

### Post by nix4me on 2008-06-28
the 2 have nothing in common.  Samba is mostly used for file server.  LAMP is for webserving.

---

### Post by windependence on 2008-06-28
Agreed. Not to be funny here but what do you want to do with this box? maybe we can suggest an appropriate application for you.


-Tim

---

