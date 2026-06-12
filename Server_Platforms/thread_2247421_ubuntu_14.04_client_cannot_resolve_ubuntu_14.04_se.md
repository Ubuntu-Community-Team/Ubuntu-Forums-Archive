---
title: "ubuntu 14.04 client cannot resolve ubuntu 14.04 server localname (domainname)"
date: 2014-10-07
forum: Server Platforms
---

### Post by qkitchen on 2014-10-07
what i am trying to accomplish is running the isc-dhcp-server alongside dnsmasq for dns only locally. from the client i can ping the server address of 192.168.145.137 but cannot ping the servers name of qkserver.research.local. i get "ping: unknown host". i have configured dnsmasq, but no sure what i am doing wrong. i am new to ubuntu server and could use some guidance on getting successful results. i can provide any config details upon request.

---

### Post by papibe on 2014-10-07
Hi qkitchen. Welcome to the forum ):P

That combo is very unusual. I don't know if it is even possible to update leases from isc-dhcp-server to dnsmasq.

The usual (and proven) combo is isc-dhcp-server with proper bind.

Having said that, dnsmasq can do both: DHCP and DNS. I'd recommend using dnsmasq as DHCP server and the DNS.

Just a thought.
Regards.

---

### Post by qkitchen on 2014-10-07
That has actually come across my mind that, that combo wasn't possible but I wasn't sure. So after switching to dnsmasq is there a way to test my client-server link for dns interaction?

---

### Post by papibe on 2014-10-07
> **qkitchen said:**
> ... is there a way to test my client-server link for dns interaction?
dnsmasq should update the DHCP leases to its DNS database.

You should be able to ping and ssh from client to server and the other way around, using their short hostnames.

Let us know if you need more help with that.
Regards,

---

