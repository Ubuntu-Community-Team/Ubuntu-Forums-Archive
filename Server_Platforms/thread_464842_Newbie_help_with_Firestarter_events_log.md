---
title: "Newbie help with Firestarter events log"
date: 2007-06-05
forum: Server Platforms
---

### Post by ubuntuben on 2007-06-05
I'm using Firestarter to configure my personal firewall even though my PC is connected to a Linksys router. I've set up the policy to be restrictive allowing only http, https, AOL IM, and DHCP both in and out. Firestarter shows the following events blocked.

Time:Jun  5 01:12:07 Direction: Unknown In:eth0 Out: Port:46316 Source: prat.canonical.com Destination: xxx.xxx.x.xxx Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jun  5 01:14:04 Direction: Unknown In:eth0 Out: Port:57461 Source: leningradskaya.canonical.com Destination: xxx.xxx.x.xxx  Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jun  5 01:16:04 Direction: Unknown In:eth0 Out: Port:57692 Source: forster.canonical.com Destination: xxx.xxx.x.xxx Length:44 TOS:0x00 Protocol:TCP Service:Unknown

The above continually repeats as the above sources appear to be scanning different ports. How concerned should I be?

---

### Post by turinglabs on 2007-06-05
Those are probably replies to an update requests or popularity-contest data being sent from your box.  Check system->administration->software sources and click on the 'Statistics' tab to read about this. You should only be concerned about this as it probably indicates your firewall is mis-configured. Keep in mind that with firestarter will automatically allow replies to connections initiated from your box, but will by default block all inbound connection attempts. 

What works for most home-based, host firewalls of this sort is to allow all outbound traffic (permissive outbound mode in firestarter), and block all inbound traffic, except for whatever servers you want to run. For you, if you have the default firestarter policy in place, I don't see any need to allow any inbound connections. You don't need to allow DHCP inbound, as your box's DHCP requests at boot will be allowed out by the permissive policy, and the replies will be allowed back in automatically. Same for AOL IM, your online presence is initiated by a connection from your box out to their IM server(s), so the replies will also be allowed automatically.

Caveat - I don't know your home network setup - if you do actually have a DHCP server on your box, serving other clients on your home LAN, then yes, you will need to allow DHCP inbound.

---

