---
title: "apache 2 (99)Cannot assign requested address"
date: 2010-03-20
forum: Server Platforms
---

### Post by JDP91 on 2010-03-20
Hi, my Apache2 was running fine for a while. Bur yeserday when I tried to start it again after a couple of weeks of vacation, I got the message:
 * Starting web server apache2 [Sat Mar 20 10:48:12 2010] [warn] The Alias directive in /etc/phpmyadmin/apache.conf at line 3 will probably never match because it overlaps an earlier Alias.
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
(99)Cannot assign requested address: make_sock: could not bind to address 192.168.0.6:80
no listening sockets available, shutting down
Unable to open logs
                                                                         [fail]
===================
he 1st part of the message was already there when Apache2 worked fine, but the erroe 99 is new.
After several tries yesterday evening, Apache2 started (I do not know how). but this morning again no way to start it. any idea ?
Rgds
JD

---

### Post by Iowan on 2010-03-20
(Stabbing wildly - hoping to connect)
Does server have static  - or DHCP address?

---

### Post by Sef on 2010-03-20
Moved to server forums.

---

### Post by JDP91 on 2010-03-20
> **Iowan said:**
> (Stabbing wildly - hoping to connect)
Does server have static  - or DHCP address?
Hi, my server is using DHCP address.

The problem is partially solved. I found that if I start my router only after the server is started, I can then start Apache2 without problem

This may have occured after an update of my router firmware (NetGear).
I have now to investigate in this direction.
Thank you for helping

---

### Post by JDP91 on 2010-03-21
Concurrently to this problem I had sometimes problem to get an IP address from the same DHCP router (Netgear DG834GT) for a windows Vista desktop on . Looking on a Netgear forum I found that a new firmware was available correcting problem sdealing with DHCP. I applied it and this morning I could start Apache 2 normally. Wait and see....:)

---

### Post by Iowan on 2010-03-21
You may wish to configure your DHCP server to issue a "static lease" to the server(based on MAC address). Then you won't need to set up a static address on the server, but it will always have the same address.

---

### Post by JDP91 on 2010-03-22
Thank you for your answer, but I really feel that my DHCP problem (seen on a windows vista workstation)is corrected by applying the new firmware on the router (DHCP server). The problem appeared when I applied firmware #22 and seems to be corrected after applying firmware #23 (correction of a time out in supplying IP address by DHCP server). This in the mean time corrected my Apache 2 problem on the Ubuntu workstation, I do not understand why, but...
rgds

---

### Post by progone on 2010-10-08
> **Sef said:**
> Moved to server forums.
where did you move it?  Do you have a link for the lost souls that will come to this link first?

---

