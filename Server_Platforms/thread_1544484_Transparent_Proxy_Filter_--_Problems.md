---
title: "Transparent Proxy Filter -- Problems"
date: 2010-08-02
forum: Server Platforms
---

### Post by greenwom on 2010-08-02
I took a fresh server 10.04 install on a desk top with two nic's
and installed the following 

```
LAMP
SSH Server
Shorewall 
DNS setup (dnsmasq)
DHCP Server
Squid proxy
Dansguardian
webmin w/ dansguardian module
```

I am trying to set up this filter, it's not working and I don't know where to start the trouble shooting.

I have a speedstream dsl modem (I've tried PPPOE on the modem and on the server... can't get either to work)

I've configured both NICs to static address.
Setup a dnsmasq for DNS and DHCP  (not sure if I need DHCP3-server, when I tried I had conflicts)

So I'm a lont time ubuntu user (since warty) but new to server / networking.   I've followed this guy's how-to with the exception of DHCP3.  [http://taksuyama.com/?p=16]("http://taksuyama.com/?p=16")

I'll post what ever logs or config files you need.  Please someone help!

I tried setting my external nic to 192.168.0.2 with a gateway of 192.168.0.1 (the dsl modem)
and I've set the internal NIC to 192.168.1.2 (my router is still 192.168.1.1).
I've turned off the DHCP function on the router and changed the internet connection type to DHCP.
I can't ping the modem from the server.  I can ping the router from the server.

Tell me what you need to help me :)

---

