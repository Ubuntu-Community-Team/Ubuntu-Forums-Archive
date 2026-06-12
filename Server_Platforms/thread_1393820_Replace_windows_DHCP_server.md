---
title: "Replace windows DHCP server"
date: 2010-01-29
forum: Server Platforms
---

### Post by ntimperio on 2010-01-29
I am trying to replace a windows DHCP server with Ubuntu.  Is there any way to set the Domain Suffix Search Order via DHCP?  I didn't set up the windows server, but windows client PCs used to get multiple domains to resolve unqualified hosts.  Can this be done with Linux?

I've googled and found the the option domain-name only supports one domain name.  I also read that option dns-domain-search-list code 119 was supposed to give you a dns suffix search order.  However, it's not working for me with the windows clients.  This is what I have currently:

ddns-update-style none;

option domain-name "Domain1.local";
option domain-name-servers 10.100.1.15;
option dns-domain-search-list code 119 = string;
option dns-domain-search-list "domain2.local domain1.local domain2.org domain1.org";

default-lease-time 600;
max-lease-time 7200;

subnet 10.100.1.0 netmask 255.255.255.0 {
   authoritative;
   range 10.100.1.60 10.100.1.99;
   option routers 10.100.1.254;
   }

---

