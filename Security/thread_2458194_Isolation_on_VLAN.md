---
title: "Isolation on VLAN"
date: 2021-02-18
forum: Security
---

### Post by Geoff_Lane on 2021-02-18
Just started experimenting with VLAN and understand the basic principles.

On my router I have an option when setting a VLAN to isolate; why would someone choose to create a vlan and then **not** isolate?  

Seems to defeat the object unless I am missing some other useful function although I do appreciate it would effectively give you 506 addresses on one network if not isolated.

Geoff

---

### Post by kevdog on 2021-02-19
VLAN provides isolation but intercommunication between VLANs requires routing.  At the router level there is typically a firewall that can control communication (one way/two way/various ports) between VLANs.  Sometimes services like uPnP don't work very well between vlans or anything that requires automatic discovery.  Oftentimes you don't want to isolate when testing various firewall rules.

---

### Post by Geoff_Lane on 2021-03-15
> **kevdog said:**
> VLAN provides isolation but intercommunication between VLANs requires routing.  At the router level there is typically a firewall that can control communication (one way/two way/various ports) between VLANs.  Sometimes services like uPnP don't work very well between vlans or anything that requires automatic discovery.  Oftentimes you don't want to isolate when testing various firewall rules.

Sorry for delayed response, missed notification.

On my router, a TP-Link TD-W9970 there doesn't seem an option to alter isolation once created, you either have it or not.  Easy enough to delete and recreate.

My router firewall seems to be able to only control traffic between WAN and LAN, does not appear to be able to control traffic within LAN unless I am missing something blatantly obvious.

Geoff

---

### Post by kevdog on 2021-03-17
@Geoff_Lane

I've only really worked with interVLAN routing with pfSense router software.  On pfSense you define your VLANs and then use a firewall to control communication or isolation between them.  I'm not sure of other router software since I've never used other software.  Some VLANs like guest -- I totally isolate.  Other VLANs like ioT - I need to allow for UPnP and MDS.  It just depends.  If you can not control communication between VLANs than perhaps you are going to have to design your network a little bit differently.

---

### Post by Geoff_Lane on 2021-03-19
> **kevdog said:**
> VLAN provides isolation but intercommunication between VLANs requires routing.  At the router level there is typically a firewall that can control communication (one way/two way/various ports) between VLANs.  Sometimes services like uPnP don't work very well between vlans or anything that requires automatic discovery.  Oftentimes you don't want to isolate when testing various firewall rules.

Thank you for reply.

Created the vlan via my router and the firewall only seems capable of LAN > WAN or visa versa but not LAN > LAN

Geoff

---

### Post by DuckHook on 2021-03-20
I'm lousy with most things network, but the usual method to route/firewall traffic on the interlan side is through arcane iptables rules. There are no easy GUI controls, even on DD-WRT or OpenWRT. Does your router http interface allow the option of manual commands? If not, can you ssh or telnet into it? Yes, some commercial routers are so poorly secured that they allow telnet. Really. At any rate, if you can get into it in any fashion, you should be able to manually set up iptable rules. Care is needed. You can lock yourself out or, worst case, soft brick your router, though recovery is not usually a problem.

I end up using iptable rules that I find through websearching and kinda&#8209;sorta understand, but not really. It isn't the most secure way to go about things, as I am in knows&#8209;just&#8209;enough&#8209;to&#8209;be&#8209;dangerous territory.

---

### Post by Geoff_Lane on 2021-04-24
> **DuckHook said:**
> I'm lousy with most things network, but the usual method to route/firewall traffic on the interlan side is through arcane iptables rules. There are no easy GUI controls, even on DD-WRT or OpenWRT. Does your router http interface allow the option of manual commands? If not, can you ssh or telnet into it? Yes, some commercial routers are so poorly secured that they allow telnet. Really. At any rate, if you can get into it in any fashion, you should be able to manually set up iptable rules. Care is needed. You can lock yourself out or, worst case, soft brick your router, though recovery is not usually a problem.

I end up using iptable rules that I find through websearching and kinda&#8209;sorta understand, but not really. It isn't the most secure way to go about things, as I am in knows&#8209;just&#8209;enough&#8209;to&#8209;be&#8209;dangerous territory.

Currently experimenting with open-wrt on a Raspeberry-Pi, works OK but probably not practical.

Geoff

---

