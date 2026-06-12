---
title: "dnsmasq only works for part of my subnet"
date: 2007-08-03
forum: Server Platforms
---

### Post by chris.zeman on 2007-08-03
My Ubuntu server has an IP address of 172.16.100.200, netmask 255.255.0.0. I have dnsmasq installed, and the server is configured to use OpenDNS's nameservers.

This server is also the DHCP server for our wired network. All of our wireless APs assign addresses to their clients. All address pools are configured to assign my server as the default gateway and nameserver.

The wired clients work great, but the wireless clients have been accessing the internet on an intermittent basis. Sometimes it works; sometimes it doesn't. Everything worked great before!

I figured out this morning that the clients aren't able to resolve any domain names. They work great if I configure the clients to use OpenDNS's nameservers. That won't work for our situation here, though.

Any ideas? :confused:

Thank you in advance,
Chris

---

### Post by koenn on 2007-08-03
the title of your thread is misleading - if you're using the AP as dhcp servers, the wireless hosts are probaby on a **different** (sub) net from the wired hosts. 

I suggest you start with looking in dnsmasq.conf - iirc there are some keywords there that limit the use of the server to certain subnets.

---

### Post by chris.zeman on 2007-08-03
I'm sorry, you're right. I meant to type "one of my subnets". I also neglected to mention what my subnets are. The wired subnet is 172.16.1.xxx with a netmask of 255.255.0.0, while the APs assign addresses of 172.16.90.xxx, 172.16.91.xxx, and 172.16.92.xxx,  with a netmask of 255.255.0.0 as well. 

I had checked dnsmasq.conf but couldn't find anything that would cause this problem. I'm going to continue looking through it in case I missed something, which is likely. :)

Thank you,
Chris

---

### Post by koenn on 2007-08-03
> **chris.zeman said:**
> Everything worked great before!

Did you change anything recently ? 

Also, youre subnetting looks weird. you have
172.16.100.xxx
172.16.90.xxx,
172.16.91.xxx
172.16.92.xxx

all with a subnet of 255.255.0.0 - so they *are* all in the same subnet. 

Are you quite sure the LAN interface of your router also has 255.255.0.0 subnet mask ? If it has 255.255.255.0, it can only see the 172.16.100.xxx hosts (assuming it itself has a 172.16.100.xxx address)

---

### Post by chris.zeman on 2007-08-03
Yeah, you're right. They are all in the same subnet. Choices of words are lacking for me right now. (3 hours of sleep, lol)

I verified that the netmask on the server's ethernet card is set to 255.255.0.0.  Remember, though:

Server: 172.16.100.200.
Wired Clients: 172.16.1.xxx
Wireless Clients (AP1): 172.16.90.xxx
Wireless Clients (AP1): 172.16.91.xxx
Wireless Clients (AP1): 172.16.92.xxx

Everything on 172.16.1.xxx works great. The other groups can access everything on the LAN fine. They just can't resolve domain names using 172.16.100.200 as their DNS. They can only resolve domain names is I specify an external nameserver.

---

### Post by koenn on 2007-08-03
can the wireless hosts ping 172.16.100.200 ?

---

### Post by chris.zeman on 2007-08-03
Yes. In fact, they can even access the web site I have on the server.

---

### Post by koenn on 2007-08-03
> **chris.zeman said:**
> Yes. In fact, they can even access the web site I have on the server.
by name ?

---

### Post by chris.zeman on 2007-08-06
Well, I was given two brand new computers today to replace my current servers. I'm going to just go ahead and replace them with a clean Ubuntu installation. I'll see if this behavior continues on the new servers. 

Thank you for your help,
Chris

---

