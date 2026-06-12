---
title: "how to connect the service site to client site"
date: 2013-05-26
forum: Server Platforms
---

### Post by lipxian988 on 2013-05-26
hi everyone i have some questions want to ask here
i using ubuntu to become my os and my service site is asterisk client site is sflphone 
the problem that i facing now is i cant connect my client to my server 
below is the printscreen about the server confriguration 
[IMG]Screenshot from 2013-05-10 11:34:50.png[/IMG]
[IMG]Screenshot from 2013-05-10 12:28:38.png[/IMG]
[IMG]Screenshot from 2013-05-10 12:03:55.png[/IMG]
the kingsley and wiliam should be 111 and 112
[IMG]Screenshot from 2013-05-16 22:11:53.png[/IMG]
below s my client site sflphone 
[IMG]Screenshot from 2013-05-26 21:51:24.png[/IMG]
some time it trying for long time and host unreachable 
[IMG]Screenshot from 2013-05-26 21:53:30.png[/IMG]

---

### Post by darkod on 2013-05-27
If the phone and the Asterisk PBX are on different locations it's best to use VPN. SIP traffic doesn't travel well through NAT.

Also, in the last screenshot I noticed you are trying to use 120.0.0.1 as server address. I guess that should be 127.0.0.1 but only if you are trying this on the Asterisk machine. Otherwise, it should be the IP of the Asterisk machine.

To make sure you have connectivity, try pinging the server IP from the client first and see if it responds. Of course, if you have a firewall in between it might reject the ping reply.

---

