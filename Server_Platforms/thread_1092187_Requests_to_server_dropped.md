---
title: "Requests to server dropped"
date: 2009-03-10
forum: Server Platforms
---

### Post by mistrial on 2009-03-10
Hi

We are running a squid proxy server and experiencing poor preformance during business hours. 

After a lot of troubleshooting we have found that slowness is related to dropped requests on the Ubuntu server. We are checking this with netstat -s. When the SYN packets are being dropped on the server, the proxy is slow and when no SYN packets are dropped everything is fine. This is logical and makes sence. 

However we need to allow more connections in order to serve all our clients. We can also see that we never have more then 1000 established TCP connections. The server is powerful enough to handle more than this. 

Is it possible to have more than 1000 connections in Ubuntu? If yes, how to change this? We are stuck and have many angry clients at the moment...


Here is a snapshot from netstat, the whole printout is attached.
[FONT="Courier New"]netstat -s
46960 times the listen queue of a socket overflowed
46960 SYNs to LISTEN sockets dropped
786 connections established[/FONT]

---

### Post by mistrial on 2009-03-11
After some more troubleshooting, we found the solution!:D

It was related to file descriptors and per process limit of 1024. This limit is imposed by the kernel on all processes including Squid.

To resolve it we had to recompile squid with new file descriptor limit that overrides kernel's default value. Below are some links that explain the solution in detail.

[http://www.zazzybob.com/squid_fd.html](http://www.zazzybob.com/squid_fd.html)
[http://www.onlamp.com/pub/a/onlamp/2004/02/12/squid.html](http://www.onlamp.com/pub/a/onlamp/2004/02/12/squid.html)
[http://wiki.squid-cache.org/SquidFaq/TroubleShooting#head-eb3240fe8e61368056af86138a2b5dcbc9781a54](http://wiki.squid-cache.org/SquidFaq/TroubleShooting#head-eb3240fe8e61368056af86138a2b5dcbc9781a54)

Anyone with the same experience?

---

