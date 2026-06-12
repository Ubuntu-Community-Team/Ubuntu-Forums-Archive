---
title: "ubuntu 12.04 unqualified dns lookups???"
date: 2012-07-12
forum: Server Platforms
---

### Post by oliwei on 2012-07-12
Hi,
 
I have a problem with a fresh install of Ubuntu 12.04. The problem is that the system hangs a lot from time to time and running tcpdump I can see that it is trying to resolve unqualified hostnames. /etc/resolv.conf has the search option set. The client is setup by DHCP.
 
Any ideas?

---

### Post by oliwei on 2012-07-13
Ok, I solved the problem by changing some of my bind dns server settings according to the following article on howto setup a bind forwarding only server:
 
[http://www.daemonforums.org/showthread.php?t=4471](http://www.daemonforums.org/showthread.php?t=4471)

---

