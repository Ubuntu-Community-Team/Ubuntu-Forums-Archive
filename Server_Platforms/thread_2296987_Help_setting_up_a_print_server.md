---
title: "Help setting up a print server"
date: 2015-09-30
forum: Server Platforms
---

### Post by Robert Finley on 2015-09-30
My home network is 2 Windows PC's and an Ubuntu server (14.04).  I have connected a printer USB to the server and I want the Windows PC's to be able to print.

Installing Ubuntu Server I selected 'print server, samba server, and openSSH server'.  I am now SSH'd in from the PC and it is all updated.

I need to set up the printer. I nano /etc/cups/cupsd.conf and add 'Listen 10.0.0.5:631, save, restart. Hop over to PC go to [http://10.0.0.5:631](http://10.0.0.5:631) and I get 'Forbidden'

---

### Post by Robert Finley on 2015-09-30
Here is what I did.

typed 'sensible-browser [http://localhost:631'](http://localhost:631') into the server. This opened CUPS admin panel.  I selected 'allow remote administration',  now I can access CUPS remotely via browser.  After that, easy street.  Printer installed, made it available, found it from Windows, done&#65279;

---

