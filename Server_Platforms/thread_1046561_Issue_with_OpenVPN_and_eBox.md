---
title: "Issue with OpenVPN and eBox"
date: 2009-01-21
forum: Server Platforms
---

### Post by Gr3y on 2009-01-21
I've gotten OpenVPN running (configured through eBox) and am having an issue.

First the scenario, I want the VPN clients to be able to access a handful of windows shares that reside on a computer that is on the same network as the VPN server. Clients can join the network, but are unable to see any offered shares.

Server information:
Single NIC
Static IP (192.168.200.x)
VPN subnet: (192.168.0.0)
Advertised networks (192.168.200.0)

That means that the clients should be hopping on the same subnet as the file server, and should therefore be able to see them. 

I need to know what I have to do to get my clients access to that file server.

---

### Post by koenn on 2009-01-22
I'm not a fan of 'helper' tools because they tend to obfuscate things. Like, I know openvpn a bit, but I have know idea what you (or eBox ?) mean by "Advertised Networks". 

Here's a quickstart guide to openvpn, including access to the network the server is on.
[http://users.telenet.be/mydotcom/howto/linux/openvpn.htm](http://users.telenet.be/mydotcom/howto/linux/openvpn.htm)

---

