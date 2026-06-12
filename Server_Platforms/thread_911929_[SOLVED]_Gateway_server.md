---
title: "[SOLVED] Gateway server"
date: 2008-09-06
forum: Server Platforms
---

### Post by rickfun101 on 2008-09-06
Hi, 

I have a windows 2003 server that runs a domain-based network with 120 users(using active directory). I need to build an ubuntu server that will handle internet traffic, both web and mail. 

I will have 2 network cards on the server. 1 to the internal network and 1 to ISP's router. Mail is hosted by a different provider for which I have the IP address for. 

The previous server that served this role has had a hdd failure. I tried recreating it with the bits of information I had and what I can see in the DNS on the windows server but I'm getting lost. 

I'm new to Ubuntu and not very strong on networks. 

Can you help with the steps I need to get this server up and running? I am going to start a fresh install with DNS now. 

Thanks

---

### Post by overdrank on 2008-09-06
Moved to Server Platforms :)

---

### Post by windependence on 2008-09-06
Easiest and fastest way would be [www.untangle.com](www.untangle.com).

-Tim

---

### Post by rickfun101 on 2008-09-06
Thanks. I did come across untangle when I started working on this server a few days ago and completely forgot about it. Will start the download now on another box. 

In the meantime, I still would like to work on the Ubuntu box. 

Will post update asap?

---

### Post by rickfun101 on 2008-09-07
Hi, 

Here's an update:
 - Installed Ubuntu on a new PC and will try Untangle on another. We have a few low spec PC's standing around that I want to try out some of the other distro's. 
 - Configured my network cards
 - Enabled IP Forwarding
 - Set iptables to allow all traffic for the established connection. Is this necessary??
 - Installed Squid and temporarily allowing all http traffic. 

What I cannot figure out is how to get email down to Outlook. Get socket error 10065 and I have worked through some of the online troubleshooters. 

Any help?

---

### Post by rickfun101 on 2008-09-10
closing. will list individual issues elsewhere. 

ps: untangle was picking up the network interfaces incorrectly.

---

### Post by windependence on 2008-09-10
FYI, my favorite is actually pfsense, but this is a Linux forum. ;)

-Tim

---

