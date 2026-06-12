---
title: "Set Outbound IP for Single Apache Virtualhost"
date: 2010-07-14
forum: Server Platforms
---

### Post by citricguy on 2010-07-14
I'm not quite sure where to start my Google search for this one, any direction would be greatly appreciated :)

I have a hand full of IP addresses for apache to use for inbound requests, but need a specific site "xyx.com" to make all outbound requests using a specific IP address (that isn't the apache default.)

Current setup: 
[INDENT]xyz.com listens on (lets say) 1.1.1.2
xyz.com sends XML-RPC requests using servers main IP 1.1.1.1 instead of 1.1.1.2.

How can I force any request being sent from xyz.com to be sent from 1.1.1.2 without making changes to my scripts. :)[/INDENT]

If there is an easy way to automatically (or manually) use a domains inbound or A record as the address the server uses to make outbound requests (for XML-RPC queries for example) that would be even better.

---

### Post by citricguy on 2010-07-14
Just in case anyone runs into this same question.  Solution, I think, ended up being SNAT and iptables to redirect outbound traffic.

Warning: fsockopen()+ Connection timeout's seem to be the issue now.

It doesn't seem to be very reliable, but thats for another search I suppose. :)

---

