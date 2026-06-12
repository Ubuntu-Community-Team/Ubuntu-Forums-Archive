---
title: "printing through a firewall"
date: 2008-06-04
forum: Server Platforms
---

### Post by neill on 2008-06-04
hi

i have a printer (hp990) attached to a headless ubuntu HH server which is served to XP LAN clients \\server\hp990c using samba

however ...

there is an internal firewall on the LAN (endian community firewall if that matters) and some XP clients need to access the printer which is 'inside' the firewall from 'outside' the firewall

port 631 is open on the HH server and is correctly forwarded to the firewall external interface

but when i try and run the install printer wizard the XP clients cannot connect to the printer through the firewall

any ideas anyone ??

incidentally //server:631/printers in firefox clients on either side of the firewall generates a 403 forbidden error whihc i don't get either

thanks for any help you can give

/neill

---

### Post by SpaceTeddy on 2008-06-04
631 is the management interface for CUPS. You also need to open the port 445 (tcp) which is the default port for windows shared. This is needed as the printer is accessed like a normal share.

Also, it might be needed that you open 137+139(tcp) which are the old windows share ports. Don't know if you need to do this.... 

hope it helps :)

---

### Post by quelx on 2008-06-04
Your external computers will need to connect to the wan side of the firewall.  Instead of **\\server\printer** they should use **\\firewall\printer**.  Also make sure **UDP** and **TCP** ports are forwarded to **server**

---

### Post by neill on 2008-06-04
thanks for the suggestions

i think this is actually a fault of the XP install printer wizard rather than anything else

when i did:

net use LPT1: \\firewall\printer

i was able to then install the printer via the wizard as if it were on LPT1 - and all is now good !

:)

---

