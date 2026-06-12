---
title: "firestarter/DHCP server broken on upgrade from 12.04LTS to 13.10"
date: 2014-04-28
forum: Server Platforms
---

### Post by johnzbesko on 2014-04-28
I had a home server running 12.04LTS Kubuntu. (I like having a desktop environment for the server.) The server provides DHCP and firewall services for my home network. I have used firestarter to do so and it was persistent, that is, if the server reboots, all my home devices are able to reconnect to the internet.

In preparation to upgrade to 14.04LTS, I had to upgrade to 13.10. The persistence of firestarter is broken, that is, if the server reboots, I have to log into the desktop and start firestarter in order for the home network to be able to connect to the internet. (The server is beginning to show signs of instability, that is, it has shut down spontaneously a couple of times.)

I understand that dhcp3-server has been upgraded to isc-dhcp, and I made some changes to some config files. I'm at the point where IP addresses are assigned at boot-up, but the firewall is not, i.e. I get an IP address at a client PC (and can mount an NFS share on the server), but cannot browse the internet (even though I installed iptables-persistent.) Only when I sit down at the server machine and log into my desktop and then run firestarter, can the rest of the household play Candy Crush.

Any help, either specific advice or suggestions for googling the problem, is greatly appreciated.

---

### Post by sandyd on 2014-04-29
Firestarter has been discontinued - it may be better for you to use iptables, ufw, or gufw

---

### Post by johnzbesko on 2014-04-29
Thanks, I did discover that firestarter had been discontinued. I installed gufw and realized I had to start from scratch, meaning learning a new program and re-entering all my rules. Is there a way to port all my rules from what I had to ufw?

What changed so that the iptable rules designed with firestarter are not automatically applied upon boot-up? Firestarter is only supposed to be a GUI to design the rules, not be the daemon running them.

---

