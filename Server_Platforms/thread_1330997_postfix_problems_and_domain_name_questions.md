---
title: "postfix problems and domain name questions?"
date: 2009-11-18
forum: Server Platforms
---

### Post by ductiletoaster on 2009-11-18
ok so firstly i have my server runing postfix and relayhost is set to my isp's smtp server....

how would i send and email from the server via telnet to and outside source like hotmail.com or gmail.com

Now my isp blocks port 25 so can i still send msgs from the server via there smtp

And lastly is there any way to set up the server to recive msgs from an outside source like hotmail... even with port 25 blocked. maybe using my isp or something.

Lasty once more... what im try to do is make and email with my domain name
my domain name is lostpropaganda.net and i would like to have [email]name@lostpropaganda.net[/email]... if there is any way to do this with out paying my register please let me know. thanks ahead of time


O and i can telnet to my isps server and email that way but i can use my postfix server?...
It turns out i just wasnt telneting quit right.... go figure


but ok so my second question!

---

### Post by kewlrichie on 2009-11-19
As for receiving inbound mail on 25 you need a service like mail reflector from no-ip.com or something just like that here's a link [http://www.no-ip.com/services/managed_mail/inbound_port_25_unblock.html]("http://www.no-ip.com/services/managed_mail/inbound_port_25_unblock.html")

---

