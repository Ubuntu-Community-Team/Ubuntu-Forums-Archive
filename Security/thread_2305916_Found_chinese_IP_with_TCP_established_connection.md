---
title: "Found chinese IP with TCP established connection"
date: 2015-12-10
forum: Security
---

### Post by y-george-b on 2015-12-10
I have an Ubuntu 14.04 instance on a digitalocean droplet.
The firewall is enabled with only the following ports available externally :

PORT    STATE SERVICE
22/tcp  open  ssh
80/tcp  open  http
443/tcp open  https

Xrdp is running which I can access by a firewall rule to allow access from my work.
Yesterday the  rdp connection didi not work, I was getting connection refused.
When I ssh'd in to the server and ran "netstat | grep 3389" to see of the xrdp server was listening I saw an ESTABLISHED TCP connection from a chinese ip address. 
I have run a root kit checker and  Commodo anti virus and they have detected nothing.

Very strange, and wondering if I should delete the droplet and start again !

George

---

### Post by Doug S on 2015-12-10
An ESTABLISHED TCP connection does not mean for sure that access was gained, it only means that there was an ESTABLISHED network connection while they tried.
I would think "trying" would be very common. For example there were 20 attempts on port 3389 on my system yesterday, not including blacklisted huge sub-nets from China that are DROPPED and not even logged.

Examine your log files for any further details, towards answering the question: Did they gain access, or did they just try to?

---

