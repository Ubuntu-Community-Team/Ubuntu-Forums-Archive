---
title: "Internet Drops Randomly"
date: 2011-01-26
forum: Server Platforms
---

### Post by expatCM on 2011-01-26
I do not understand this problem .....   I have a server with two nics, one lan and the other facing the wan.  The problem is that at random the Internet connection will drop.   I cannot figure out what is the cause.

I am using an adsl connection.  I use bridge mode.  The server manages the rest.   I have changed the nic facing the wan.  I have swapped the router.  No change.  I can restart the connection every time it drops by using PuTTY to the server and then issuing the command "pon dsl-provider" which then negotiates a connection and brings up the public IP.

I have only one clue but I do not understand the significance.  In trying to figure this out I put the lan directly onto an adsl modem in pppoe-llc so the ISP managed the traffic directly. With this there was no interruption at all, it was a stable connection for a day or more (it was there until I shut down).  So that says to me that the problem is on the server.

This can happen every hour or so but it can also change to say every 6 - 8 hours. 

Any suggestions at all how to diagnose this since it does not appear to be a hardware issue and so what could have gone wrong and why is this apparently random?

---

