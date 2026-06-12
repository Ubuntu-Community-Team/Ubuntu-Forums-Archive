---
title: "Recommend Network Security Appliance?"
date: 2012-08-13
forum: Security
---

### Post by ericmachine on 2012-08-13
Hi everyone,

I have couple of boxes of Ubuntu 10.04 servers in my  office environment. At the same time I have 10 Apple Macs for end users  usage.

I am considering to buy Network Security Appliance  (firewall for internal office environment), reviewed SonicWall NSA2400  and PaloAlto PA-500 (entry level but super expensive). Sonicwall is more  affordable to my environment.

However Sonicwall's reporting  module only works on Windows Server 2008. Without that reporting module,  I can't check historic data. 

I need to have a network security appliace for this:-
a) works well with linux and apple, probably can link up with Linux OpenLDAP or something instead of tracking by IP address?
b) appmonitor - blocks facebook, facebook chat, block urls
c) anti-virus and anti-spyware
d) QOS - used for outbound SIP calls, priority port 5060
e) SSL VPN
f) IPSec VPN
g) basic wan acceleration

Any recommendations? Thank you.

---

### Post by uRock on 2012-08-13
A decent Cisco router can handle most, if not all, of those tasks.

---

### Post by ericmachine on 2012-08-13
any specific cisco model? 

router can do firewall? hmm?

---

### Post by lisati on 2012-08-13
> **ericmachine said:**
> router can do firewall? hmm?
Both my all-in-one modem/routers offer firewall functions. I gather you'd like something that offers a bit more peace of mind, and with the gadgets I have, reporting might be a bit of a challenge.

---

### Post by samiux on 2012-08-13
> **ericmachine said:**
> Hi everyone,

I have couple of boxes of Ubuntu 10.04 servers in my  office environment. At the same time I have 10 Apple Macs for end users  usage.

I am considering to buy Network Security Appliance  (firewall for internal office environment), reviewed SonicWall NSA2400  and PaloAlto PA-500 (entry level but super expensive). Sonicwall is more  affordable to my environment.

However Sonicwall's reporting  module only works on Windows Server 2008. Without that reporting module,  I can't check historic data. 

I need to have a network security appliace for this:-
a) works well with linux and apple, probably can link up with Linux OpenLDAP or something instead of tracking by IP address?
b) appmonitor - blocks facebook, facebook chat, block urls
c) anti-virus and anti-spyware
d) QOS - used for outbound SIP calls, priority port 5060
e) SSL VPN
f) IPSec VPN
g) basic wan acceleration

Any recommendations? Thank you.

I would like to recommend [Untangle]("http://www.untangle.com/").

Samiux

---

### Post by Cheesemill on 2012-08-13
If you have hardware that you can use or are willing to purchase then you could take a look at [Untangle]("http://www.untangle.com/"), [Smoothwall]("http://www.smoothwall.com/"), [Zentyal]("http://www.zentyal.com/") and [Vyatta]("http://www.vyatta.com/"), all of which offer software only subscriptions as well as bespoke hardware appliances.

---

### Post by Hungry Man on 2012-08-13
Or you can have a look at pfsense, which should be able to be expanded to do IDS/IPS as well as perform as a basic Firewall.

[https://en.wikipedia.org/wiki/PfSense](https://en.wikipedia.org/wiki/PfSense)

Features

Stateful firewall
Network Address Translation
Redundancy through CARP and pfsync
Outbound and inbound load balancing
Virtual Private Networks using IPsec, L2TP, OpenVPN, or PPTP
PPPoE server
RRD graphs reporting
Real-time information using Ajax
Dynamic DNS
Captive portal
uPnP
VLAN (802.1q)
DHCP server and relay
Live CD version available
Support for software extensions, including the Squid proxy server, the Snort intrusion prevention/detection system, and the FreeSWITCH[7] telephony platform

---

### Post by uRock on 2012-08-13
> **ericmachine said:**
> any specific cisco model? 

router can do firewall? hmm?

Cisco offers multiple types of firewalls, if you purchase the models with the proper version of IOS. You would need to search their site for the proper hardware for your set up.
Routers [http://www.cisco.com/en/US/products/ps10906/Products_Sub_Category_Home.html](http://www.cisco.com/en/US/products/ps10906/Products_Sub_Category_Home.html)

Security hardware [http://www.cisco.com/en/US/products/hw/vpndevc/index.html](http://www.cisco.com/en/US/products/hw/vpndevc/index.html) They do offer network based equipment that can scan machines and traffic for a wide range of malware signatures. This equipment, with service plans, can get expensive an may not be an option for a small business.

With a few ACLs, Facebook and other sites can be blocked. QoS is easy to set up and adjust. Cisco offers quite a few ways of managing VPNs. These are all done on the router or switch.

Juniper offers equivelant hardware, but I have not had the pleasure of working with their systems, yet. [https://www.juniper.net/us/en/products-services/](https://www.juniper.net/us/en/products-services/)

---

### Post by uRock on 2012-08-13
> **samiux said:**
> I would like to recommend [Untangle]("http://www.untangle.com/").

Samiux

That looks like a great product. I will have to look into that in the near future. Thanx!

---

### Post by ericmachine on 2012-08-13
Thanks everyone, will take a look on this one :) untangle looks good

---

