---
title: "Ubuntu As A Small Office Router+VPN Server?"
date: 2014-10-25
forum: Server Platforms
---

### Post by Brendan_Farr-Gayno on 2014-10-25
Hi Everyone,

I'm rolling out a an office for my small business (web development) and have a rack mount server with two network ports that I would like to explore turning into our router, firewall, DHCP, DNS and IPSEC VPN. Basically the 'gatekeeper' to the internet and our central network server.

In the past I've used off the shelf SMB router appliances like the Linksys RV082 which I loved, but that appliance hasn't been updated in years by Cisco and I'm thinking I might have a better performing system in the longer term if I just rolled my own. The RV082 was great since it not only had the standard DHCP and routing capabilities but had dual wan with load balancing and had pretty solid L2TP tunnels and a decent firewall system. I don't need dual wan, but having a router that also acts as my VPN server seems to make sense to me? In any case, money is tight in the small business, so I want to stretch this machine for as much as I can get out of it.

My question is, is there a good how to you know of that covers this kind of thing with respect to all of the services on the same box at once? I know there are a few talking about each one of these services specifically but I'm somewhat worried about how they will play together. It seems like this setup has got to be common?

I installed Ubuntu Server 14 LTS

Thanks!

---

### Post by koenn on 2014-10-25
This should be fairly easy, and I'm sure there are howtos and blog posts out there that describe this sort of setup, but then you'll just be copying whatever some random blogger considered "the perfect setup" for his particular situation.

There's no problem with just installing all components you need separately, they'll work together just fine, unless you configure them to do things that contradict each other.

pointers:
  * routing is available in the linux kernel but needs to be enabled
  * use iptables for firewall and NAT. you most likely need NAT. check out ufw - it's an 'uncomplicated' frontend to itables
  * when using a machine with 2 NIC's, check for each service that you install  what interface you want it to listen on. You preferably don't want to serve DHCP or your LAN's DNS to the internet
  * for dhcp and dns, consider dnsmasq in stead of separate dhcpd and named setups - dnsmasq is way simpler yet (usually) powerfull enough for SOHO and SMB LANs
  * consider openvpn in stead of ipsec, it's more than adequate and less troublesome to get right.

---

### Post by nerdtron on 2014-10-25
Mikrotik devices are good application for this, If you are familiar with networking, ip address, nat and tunnels, you will be familiar with it.
[http://routerboard.com/RB951-2n](http://routerboard.com/RB951-2n)

---

