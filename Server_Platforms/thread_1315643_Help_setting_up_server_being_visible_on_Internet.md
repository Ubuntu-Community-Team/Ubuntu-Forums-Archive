---
title: "Help setting up server being visible on Internet"
date: 2009-11-05
forum: Server Platforms
---

### Post by alex_log on 2009-11-05
Hi all,

First of all, I'm not an admin, nor a Linux guru by any means, just a developer in a startup being in a position where I have to do everything myself, so be gentle :)

I've set up an Ubuntu Server 9.04, following this quite excellent [guide]("http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/"), and the only thing I can't figure out is how to make the Apache server visible on the network.

When I access the IP on local network, I get the "It works!" page. The IP is static, I know that for sure (we got 5 static IP's package from the ISP). Also, port 80 is open... I have Shorewall firewall setup, but it's configured to accept HTTP connections. Unfortunately, the server is not visible (and IP is not pingable) from the outside world.

What am I missing? I have a feeling it's some network settings on the server I have to configured. 

Any help will be greatly appreciated.

Thanks!!!

---

### Post by koenn on 2009-11-05
> **alex_log said:**
> 
What am I missing? I have a feeling it's some network settings on the server I have to configured. 

Does the web server actually have 1 of those 5 addresses your ISP gave you ?

---

### Post by zzzBrett on 2009-11-05
Try testing it without the firewall.

---

### Post by karlson on 2009-11-05
> **alex_log said:**
> 
When I access the IP on local network, I get the "It works!" page. The IP is static, I know that for sure (we got 5 static IP's package from the ISP). Also, port 80 is open... I have Shorewall firewall setup, but it's configured to accept HTTP connections. Unfortunately, the server is not visible (and IP is not pingable) from the outside world.


I have to assume that the Firewall also does NAT.  In which case your IP address inside is probably something like 192.168.x.x or 10.x.x.x.

In which case the internal addresses are not visible and you need to have the firewall be the outside IP address and also do port forwarding to the internal network.

---

### Post by koenn on 2009-11-05
> **karlson said:**
> I have to assume that the Firewall also does NAT.  In which case your IP address inside is probably something like 192.168.x.x or 10.x.x.x.

In which case the internal addresses are not visible and you need to have the firewall be the outside IP address and also do port forwarding to the internal network.
or assign a public, routeable address to the server ...

let's first see what the problem is, and  then see how it can be fixed. The other way usually doesn't work so well.

---

### Post by baltadt on 2009-11-05
i am having the same problem. From server site works fine but can not connect from other computers.

---

### Post by ZALinuxDude on 2009-11-06
I apologise before hand if i end up putting my foot in my mouth by saying this but... doesn't this release of Ubuntu server have VPN ? It should do as all of them from 8.04 have had VPN, why don't you use that to log on remotely... again appologies for putting my foot in my mouth if that is the case as from what i hear it should be relatively easy to set up (i stand corrected of course, as i haven't done it yet myself)

---

### Post by kevin11951 on 2009-11-06
to the OP,

please post the output of 
```
ifconfig
```

---

