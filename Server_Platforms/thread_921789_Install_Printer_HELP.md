---
title: "Install Printer HELP"
date: 2008-09-16
forum: Server Platforms
---

### Post by vegas588 on 2008-09-16
Newbie here trying to learn Ubuntu. Having a difficult time installing a print server. Windows Domain network. All printers are networked with static ip addresses. I installed CUPS and modified the /etc/cups/cupsd.conf file with the following information based on things I have read so far.

#Listen localhost:631
Listen /var/run/cups/cups.sock
Listen 192.168.110.80:631  (IP ADDRESS OF UBUNTU SERVER)

#Restrict access to the server...
<Location />
  Order Deny,Allow
  Deny from All
  Allow from 127.0.0.1
  Allow from 192.168.110.*
</Location>

What do I do now? I really do not understand the next step. For example, I have a printer in my office that is an HP LaserJet 2300. What are my next steps to install the drivers for that printer?

Thanks.

---

