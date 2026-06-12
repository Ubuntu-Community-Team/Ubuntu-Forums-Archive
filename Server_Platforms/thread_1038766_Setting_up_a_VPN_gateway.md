---
title: "Setting up a VPN gateway"
date: 2009-01-13
forum: Server Platforms
---

### Post by sparkles on 2009-01-13
At work we connect to another company's VPN which until recently was setup on our ADSL router. We have recently got a new router and we can't get its PPTP client to work (and there's no built in log which makes it really frustrating to debug). I have Ubuntu server 8.10 running in vmware player on our file server so I figured it should be easy to setup a PPTP connection and gateway for other computers to access the other network via.

So far I have:
- setup the PPTP connection
- setup a DNS server

What I can't figure out is how to set it up as a gateway (in my head I imagine setting ubuntu up as the default gateway on our XP boxes). I read a post on these forums about setting up a gateway and got as far as making changes to /etc/sysctl.conf. It then continues on setting up iptables but I have no idea what to do there because the file server only has 1 network card (and I'm not interested in filtering outside traffic because that happens on our router).

Does anyone know how to set up a gateway with only 1 network card?

TIA

---

### Post by Iowan on 2009-01-14
With only one network card, the server seems more like a side door than a gateway.  Or maybe my interpretation that traffic goes "through" a gateway is in error.

---

### Post by hvc123 on 2009-01-16
you can give your 1 nic more than 1 ip.
eth0
eth0:1
eth0:2
eth0:3 
and so on..... i have tried to get this to work too as i wanted my imac to be the router of my network.. i had a few issues then gave up as the missus was threatening me with the eyes :D

---

### Post by windependence on 2009-01-16
Easiest way to do this would be to set up a pfsense box. VPN is built in. GUI web config. VMware image is already provided. More info:

[http://pfsense.org/](http://pfsense.org/)

[http://doc.pfsense.org/index.php/PfSense](http://doc.pfsense.org/index.php/PfSense)

[http://blog.pfsense.org/?p=293](http://blog.pfsense.org/?p=293)

Download link for appliance: [http://files.pfsense.org/vmware/pfSense-1.2.2-VM.zip](http://files.pfsense.org/vmware/pfSense-1.2.2-VM.zip)

HTH

-Tim

---

