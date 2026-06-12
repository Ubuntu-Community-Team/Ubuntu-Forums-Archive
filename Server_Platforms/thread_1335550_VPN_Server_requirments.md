---
title: "VPN Server requirments"
date: 2009-11-23
forum: Server Platforms
---

### Post by rx_shorty on 2009-11-23
Hello all,
 
I want to set up a server with a VPN connection.
About 20 users are going to be on it at the same time.
 
What do I require if we talk about Hardware for the server.
 
-CPU
-Memory
-10/100 MB
 
And which software is to proven the most stable?
 
Hope to hear from you.
Any help is much appreciated.

---

### Post by Bachstelze on 2009-11-23
Moved to Server Platforms.

---

### Post by rx_shorty on 2009-11-23
Ahh thanks!

---

### Post by JillK on 2009-11-23
what do you mean by '-10/100 MB'?

---

### Post by rx_shorty on 2009-11-23
10 mbit or 100 mbit required for a 20 user vpn :)

---

### Post by JillK on 2009-11-23
what will the users be doing? Are the processes on the client side or server side? Will they all be on at the same time?

---

### Post by gombadi on 2009-11-23
If VPN is the servers main function then you do not need much. To give you an idea we have a vpn server running OpenVPN that connects four remote sites. The main use is MySQL replication.

It is not over worked but it can easily handle 20Mb/sec doing about 15% CPU usage. The system is a 1.2GHz PIII with 512 MB ram(currently using 72MB ram).

Most times you do not need a brand new multi core machine to run a vpn.

If the server is used for other functions then you will have to let us know and work that into the estimate.

---

