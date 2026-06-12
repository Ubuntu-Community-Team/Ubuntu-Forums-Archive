---
title: "VPM Client to Client Routing Question"
date: 2008-11-12
forum: Security
---

### Post by scott_ttocs46 on 2008-11-12
Hi All,

I have a server that sends data for client to client file transfers. The data does not pass through the server.

I would like to setup a box and run the server on a private virtual network using VPN. So, the clients would get their own [virtual] IPs, etc.

The goal is to have the traffic completely encrypted.

My question is would my client to client data have to pass through the VPN box or would the VPN actually route it over the internet?

Scott

---

### Post by koenn on 2008-11-12
> **scott_ttocs46 said:**
> Hi All,

I have a server that sends data for client to client file transfers. The data does not pass through the server.

I would like to setup a box and run the server on a private virtual network using VPN. So, the clients would get their own [virtual] IPs, etc.

The goal is to have the traffic completely encrypted.

My question is would my client to client data have to pass through the VPN box or would the VPN actually route it over the internet?

Scott
I'd say it has to go through your box because that will be the only way to establish a route between two (or more) vpn ip addresses. 
Unless you can think of a way to set up a tunnel between the clients


setting up a p2p operation and trying to hide the content ?

---

### Post by scott_ttocs46 on 2008-11-12
It is p2p but not the illegal kind. I was considering BT for corporate stuff. However, we are very big on privacy. It does not seem like what I want is possible with VPN.

---

### Post by koenn on 2008-11-13
> **scott_ttocs46 said:**
> It is p2p but not the illegal kind. I was considering BT for corporate stuff. However, we are very big on privacy. It does not seem like what I want is possible with VPN.

maybe ssh tunnels ?
[http://users.telenet.be/mydotcom/howto/linux/tunnel.htm](http://users.telenet.be/mydotcom/howto/linux/tunnel.htm)

---

