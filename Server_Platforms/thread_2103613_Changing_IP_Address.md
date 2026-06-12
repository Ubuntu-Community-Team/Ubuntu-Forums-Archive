---
title: "Changing IP Address"
date: 2013-01-10
forum: Server Platforms
---

### Post by pgp_protector on 2013-01-10
We've got an inhouse server that's configured to 192.169.1.50

This server acts as an Internal Web server, DNS, host a few pages (Internal & external), Database, SOAP/WSDL & Meteor server (For some push services)

Well our ISP once in a while drops the DSL Connection for a few seconds, not a major issue, problem is the Netgear router then decides that it doesn't like the 192.168.1.x network & changes the IP subnet to the 10.0.0.x range.  

This "Feature" can't be disabled that I know of and is a pain in the )#$*%&

So It's looking like I'll have to convert the server from 192.168.1.50 to something in the 10.10.x.x range

1) is their a simple way to search all the configuration files in a Ubuntu server so I can change everything 
2) if no what hickups am I looking forward to?

---

### Post by spynappels on 2013-01-11
Let me just check that you are thinking of changing the IP addressing for your entire LAN? Unless the server is the only item with a static IP and everything is configured by DHCP, that is a serious undertaking.

Is the problem that your Netgear router essentially does a factory reset every time the DSL drops, or is it the case that most of your network is on the 10.x.x.x subnet anyway, and you are using the 192.168.x.x as a DMZ subnet? Could you give the model no of the Netgear router?

To actually start answering your question, it depends on how services are configured. If the server has only one interface and all services listen to that interface on their respective ports, it could be as simple as changing the IP address and the DNS records relating to any internal resources. Otherwise, you need to manually check the config of each service and see if there is a specific setting binding it to a specific IP/interface, and changing this as required.

---

### Post by lisati on 2013-01-11
I'm guessing that someone has configured the static IP address on the server rather than on the router. If so, and assuming that the router isn't doing a full factory reset, it is possible that using the router's options to reserve IP addresses for particular machines might suit your needs better.

---

### Post by Grenage on 2013-01-11
Why not simply replace the router?  It's obviously defective.

---

### Post by spynappels on 2013-01-11
> **Grenage said:**
> Why not simply replace the router?  It's obviously defective.

That would have been my next move....

---

### Post by Toriku on 2013-01-11
> **Grenage said:**
> Why not simply replace the router?  It's obviously defective.

that's what I was thinking

---

### Post by pgp_protector on 2013-01-11
> **spynappels said:**
> Let me just check that you are thinking of changing the IP addressing for your entire LAN? 
Unless the server is the only item with a static IP and everything is configured by DHCP, that is a serious undertaking.

Only fixed IP addresses are the Linux Server a Windows Home server, and 2 Printers.

> **spynappels said:**
> Is the problem that your Netgear router essentially does a factory reset every time the DSL drops, or is it the case that most of your network is on the 10.x.x.x subnet anyway, and you are using the 192.168.x.x as a DMZ subnet? Could you give the model no of the Netgear router?

When originally setup the whole network was configured for the 192.168.1.x range, but if the DSL Drops this wonderful Netgear (WNR3500L) router (Know issue with lots of netgear routers apparently) sees it as a "Double NAT" and takes it upon itself to Reassign the network to the 10.x.x.x range.


> **spynappels said:**
> To actually start answering your question, it depends on how services are configured. If the server has only one interface and all services listen to that interface on their respective ports, it could be as simple as changing the IP address and the DNS records relating to any internal resources. Otherwise, you need to manually check the config of each service and see if there is a specific setting binding it to a specific IP/interface, and changing this as required.
the Router assigns the IP Numbers, with the only Fixed IPs being the 2 Servers (For external access), and the Printers.
All other computers just use whatever IP Address is assigned.

We were hoping to not have to change the IP Address, as some testing hardware was coded to talk to Fixed IP Address (Custom software, but can be rewritten) 

When me or one of our other engineers in in shop this isn't an issue as we both know how to reset it, but when we're both off site, it prevents others from using the testing equipment or internet.

The other option I'm looking at is re-wiring the network so that the troublesome Netgear router is just pulled from the network fully, and get a second network card for the Linux server & have that handle everything (DNS, Assigning IP Address, Firewall, ect)

---

### Post by pgp_protector on 2013-01-11
> **Grenage said:**
> Why not simply replace the router?  It's obviously defective.

Did that twice.  Yes it's defective(Though Netgear wouldn't agree) , but it's the firmware that's defective.

---

### Post by spynappels on 2013-01-11
> **pgp_protector said:**
> The other option I'm looking at is re-wiring the network so that the troublesome Netgear router is just pulled from the network fully, and get a second network card for the Linux server & have that handle everything (DNS, Assigning IP Address, Firewall, ect)

This would be the best option in my opinion, if replacing the router with another model is not an option....

---

### Post by volkswagner on 2013-01-11
> **pgp_protector said:**
> Did that twice.  Yes it's defective(Though Netgear wouldn't agree) , but it's the firmware that's defective.

If you can pull the Netgear from service, why not get a different model that does not have this bug?

If you move DHCP and Gateway to the server, you now have a single point of failure.

Perhaps get two new routers that can be configured the same.  If one goes down, a non-techie can swap out the few wires and be up and running if you are not on site.  Plus having a backup unit is just nice to have :)

---

### Post by chadk5utc on 2013-01-11
just a suggestion in the event its an issue with the firmware( I know its a stretch)
[http://www.dd-wrt.com/wiki/index.php/Netgear_WNR3500L](http://www.dd-wrt.com/wiki/index.php/Netgear_WNR3500L)

---

### Post by pgp_protector on 2013-01-12
> **chadk5utc said:**
> just a suggestion in the event its an issue with the firmware( I know its a stretch)
[http://www.dd-wrt.com/wiki/index.php/Netgear_WNR3500L](http://www.dd-wrt.com/wiki/index.php/Netgear_WNR3500L)

Yes, I stumbled across that also, saw that the router I've got if fully compatible with the Full version of dd-wrt to boot.

---

