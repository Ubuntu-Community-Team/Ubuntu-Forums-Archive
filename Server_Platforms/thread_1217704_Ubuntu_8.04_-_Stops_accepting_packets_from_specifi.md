---
title: "Ubuntu 8.04 - Stops accepting packets from specific hosts"
date: 2009-07-19
forum: Server Platforms
---

### Post by grapz on 2009-07-19
Hi

I currently have the following as my dev enviroment:

Server 1: Ubuntu 8.04 (Running on VMWare Server, not JeOS) with:
  - Apache2
  - PHP5

Server 2: Ubuntu 8.04 (Running on VMWare Server, not JeOS) with:
  - MySQL

Host: Ubuntu 9.04 with VMWare Server. This is also the maching I'm physically at. Got bridged NICs with the two VMs. 

So I log into Server 1 with 4 different SSH sessions and do some php coding (with Zend and Smarty).

I test the stuff in my web browser, and look at the result on Server 2 through phpmyadmin (running on Server 1).

The suddenly Server 1 stops accepting packets on any port from my host. It still accepts packets from Server 2.

If I do nmap -sS 'Server 1', the ports are listed as open, but all my SSHs goes down, and I can't access the Apache server.

If I try to reconnect the SSH sessions from the host, I get 'connection refused', but as I said, it works from Server 2.

After about 5 minutes, Server 1 starts accepting connections from my host again.

This haven't happened to Server 2 yet, so I'm thinking it could be an Apache issue.

Anyone got some suggestions?

Edit:
After doing some more testing, I think the problem was caused by some bad coding with the Zend Framework on my part. I've changed some code, and it looks to be ok so far.

---

