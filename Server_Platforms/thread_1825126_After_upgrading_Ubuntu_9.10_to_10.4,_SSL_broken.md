---
title: "After upgrading Ubuntu 9.10 to 10.4, SSL broken"
date: 2011-08-14
forum: Server Platforms
---

### Post by isthisyournacho on 2011-08-14
For some reason SSL sites no longer load from a server I upgraded today from Ubuntu 9.10 to 10.4.  

The domain name points to a hardware load balancer that has three servers behind it for the one website.  Only one of these three servers handles the SSL requests.

Since I did the upgrade all SSL requests to the machine are timing out.  There's nothing in the logs.  I have restarted the hardware load balancer and the main firewall.

Any ideas on where I could start to look to solve this?  Also telnet:

```
snoochbox:~ thedoug$ telnet IP 443
Trying IP...
telnet: connect to address IP: Operation timed out
telnet: Unable to connect to remote host

```

p.s. Seconds after posting this I realized it should've gone in the Installations and Upgrades section...

---

### Post by isthisyournacho on 2011-08-14
Doh - a 2nd reboot did the trick.  It's serving SSL now.

---

