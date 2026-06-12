---
title: "Ubuntu Server - Ports are forwarded but still can't play..."
date: 2013-02-04
forum: Server Platforms
---

### Post by ksbd on 2013-02-04
Hi guys,

I've set up an Ubuntu server for Minecraft, and I'm having a little trouble. I can access the server and play via local connection, but all my efforts so far have not allowed friends outside my home network to join.
Yes, I've given them the correct external IP address, and I've checked both port forwarding and firewall rules on my router are set up correctly multiple times (For port 25565). I've also checked via multiple websites that the port is forwarded, which it is.
I've used ufw disable and rebooted the server also, but still no luck.

Anyone have any suggestions? I'm completely stumped.

---

### Post by Doug S on 2013-02-04
Well, from reading your posting, I'm stumped also. So time to get some more information...
I don't use ufw, and it is merely a front end for iptables, so check that indeed the iptables rule set is empty. Do:```
sudo iptables -v -x -n -L
```Then use tcpdump, or wireshark (tshark) if you prefer, to examine things at the packet level. Example:```
sudo tcpdump -n -nn -tttt -i eth0 port 25565
```(your interface name might be different) Do you see the packets arriving at and leaving from your server?

---

### Post by ksbd on 2013-02-04
> **Doug S said:**
> Well, from reading your posting, I'm stumped also. So time to get some more information...
I don't use ufw, and it is merely a front end for iptables, so check that indeed the iptables rule set is empty. Do:```
sudo iptables -v -x -n -L
```Then use tcpdump, or wireshark (tshark) if you prefer, to examine things at the packet level. Example:```
sudo tcpdump -n -nn -tttt -i eth0 port 25565
```(your interface name might be different) Do you see the packets arriving at and leaving from your server?

Well, I was just about to post additional info and a screenshot of the port being forwarded when I find that it's no longer forwarded, despite nothing changing... I'm going to blame this on my router for the time being, and I'll try the setup again in 3 weeks, as we shall then have fiber-optics installed and an actual up-to-date router. 
Until then, thanks for your reply.

---

