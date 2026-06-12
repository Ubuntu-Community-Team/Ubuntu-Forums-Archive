---
title: "DHCP &amp; DNS Issues with Webmin"
date: 2013-02-08
forum: Server Platforms
---

### Post by jingo_man on 2013-02-08
Added a new computer to the network, a Raspberry Pi.

I have installed a Webmin on my Ubuntu server, which is the BIND and ISC DHCP server.

The computer initially picked up a DHCP address, and was also registered in DNS.

I then went into Webmin, and added a new host in the DHCP module to fix the IP (but still keeps the client machine at DHCP).

The client machine is now using this IP as expected.

But the DNS did not update. So I returned to Webmin, found the existing entry in the DNS Address Records for the zone, and manually edited the entry to point to the new fixed IP.

I have then tried numerous clients on the network to ping and nslookup this entry, and all entries point to the old IP address.

I have run "rndc reload", "rndc flush", even rebooted the server. Flushed the local DNS caches on all machines.

Double checked the underlying dynamic BIND files in /var/cache/bind/.... and it all looks correct.

Can anyone help push this further to resolution.

jingo_man

---

