---
title: "Cannot access FTP Server externally"
date: 2009-10-23
forum: Server Platforms
---

### Post by djliamtate on 2009-10-23
I have followed the instructions to setup ProFTPD to work behind a NAT and have so far only managed to connect from local machines with the servers private IP Address. I am currently using a local file server with Ubuntu Server installed so I can access all my music locally but I also need to be able to FTP to the server when I am away from the home network.

Now currently, I have PassivePorts directive set to 60000 60100 and the Port directive to 1980. I have my Masquerade address set to xxxxxxxxxx.homeftp.net and am using a Netgear WRN2000 Router for my home network. I have a static IP assigned to the server although all other devices have their IP addresses assigned Dynamically by the router. When I try to connect using the DynDNS hostname in CrossFTP or from a Finder folder on my Mac I get no joy but if I connect using FTP with the 192.xxx.xxx.xxx private address it seems to be fine. From the router I have port forwarding set up which routes traffic for port 1980 to the FTP server.

I have flushed iptables to ensure it's not a firewall issue and that doesn't resolve anything either. I am running ProFTPD in standalone mode. I find it strange that by typing in a private address it works but then won't if I access it with the DynDNS address.

Any clues anyone, I have been reading the net for the last few days.

This is the error I get from Cross FTP

[R1] Reconnect #1 to House in 30 seconds.
[R1] Connect to House
[R1] Connection refused
[R1] Connection lost.
[R1] Reconnect #2 to House in 30 seconds.


Thanks in advance.

Liam

---

