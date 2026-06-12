---
title: "Server as Router with Squid and DHCP"
date: 2010-07-20
forum: Server Platforms
---

### Post by Nikusha on 2010-07-20
Hi,

[I]**I want to have this set up at home:**
Have a Ubuntu Server, which acts as the DHCP, and monitors the traffic on each computer connected to the LAN using Squid in transparent mode. [/I]

[I]**What I have:**
The laptop I want to use to do this has one network card, ethernet only.
It has Ubuntu on it.

I have a wireless modem/router.
[/I]
---

How can I do this?

---

### Post by Bertus_Nel on 2010-07-20
Hi Nikusha

Quick question - why do you want to run DHCP at home? Personally I will just make them static in the scope I run, unless you have like 10 + pc's at home. Running DHCP on one pc (Your laptop - will always have the same IP address - DHCP will use the first available IP to assign to your Laptop)

Do you have a server box or will you use your laptop to run everything? Did you configure your router and your Ubuntu Server?

THis is a quick setup if you want to do it this way. Configure server, router. Open laptop and connect to your wireless router and of you go.

Details you gave is a bit sketchy - ie: You want to setup a server - but you have a laptop? Run DHCP on laptop or server?  Give more info and Im sure we can help you out as this is not impossible. 

Later then:)
[U]

[/U]

---

