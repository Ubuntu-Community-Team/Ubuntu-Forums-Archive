---
title: "Setting Up a DHCP and DNS server"
date: 2008-07-13
forum: Server Platforms
---

### Post by azurepancake on 2008-07-13
Currently my network is composed of several computers connecting to a router, which in turn connects to a modem and then finally into the phone line. 

The router is a regular SOHO router with a built in DHCP and DNS server, but I have recently been considering setting up my own DHCP and DNS server just for the sake of getting my feet wet and to have more control over my network.

But before I jump in and start configuring daemons, I need to know how this will work. I am guessing for this kind of setup, I will need the modem plugging directly into the server and then out of the server and into a switch/hub. 

So I guess my question is how one would configure this on Linux? I'd imagine I would need to configure the networking settings on the server to know how to handle the information between its two NICs. 

If anyone can throw me some words of wisdom, I'd greatly appreciate it.

Thanks.

---

### Post by koenn on 2008-07-13
TCP/IP networks are layered : the network stuff (NICs, IP addresses, routing, ...) is separated from the applications (dhcp, dns, ....) so to set up DNS and DHCP you don't need to modify your network and you don't need a server with 2 NIC's, unless you want the server to also act as a router, firewall, gateway, etc, or you have a special network design in mind that requires such modifications. 

For what you describe, you can just
- turn of the dhcp service of your router : you don't want 2 dhcp servers on the same network (unless you manage to make them cooperate)
- run a dhcp service on the server
- run a dns service on the server. To make it capable of resolving external addresses, set it up to forward to a dns server that knows external addresses. This can be your router's dns server, or a public dns such as any ISP's nameservers, OpenDNS.org, ...
- configure the clients to use your DNS as nameserver. This is an option that can be configured through (your) dhcp.

---

