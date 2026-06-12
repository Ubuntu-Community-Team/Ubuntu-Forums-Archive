---
title: "Quick question about internal &amp; external IP"
date: 2011-05-22
forum: Server Platforms
---

### Post by wolfgang89 on 2011-05-22
I am working on a web, DNS, and mail server(and possibly proxy server) all in one box. I believe I've found the solution to my first problem of my DNS server not responding being it was using an internal IP and not an external one. So my main question concerns my server and a mythtv box I have. I would like to be able to access my server using my domain i.e. [www.example.com]("http://www.example.com") and click a link to bring me to my mythtv box for web control/programming. My issue would be linking from my server with an external IP to mythtv with an internal IP. 
 
Also on a side note, I would like to know if there is a quick & simple way to setup the server as a DHCP server using two network interfaces and the configuration   
 
Internet <-> Modem <-> Server <-> Wireless Router
 
Any help would be greatly appreciated. Thanks.
P.S. I'm using Webmin to configure my server.
 
Thanks. 
WolfGang

---

### Post by Lars Noodén on 2011-05-22
> **wolfgang89 said:**
> ... I would like to know if there is a quick & simple way to setup the server as a DHCP server...


For that, I would recommend looking at [dnsmasq](http://www.thekelleys.org.uk/dnsmasq/doc.html).  It's in the Ubuntu package repository.  It's fast to set up and very easy to use.

---

### Post by CharlesA on 2011-05-22
+1 to dnsmasq. I don't think you need a full blown BIND server to do local DNS lookups.

---

### Post by wolfgang89 on 2011-05-22
Ok, I'll look into it. But local DNS lookups aren't the problem. I want to be able to access my server from external networks. I can get it to work internally with it being setup 

Internet <-> Modem <-> Router <-> Server

But for example if my domain was registered as example.com with nameservers ns1.example.com and ns2.example.com and both had a glue record to my public external IP of 174.x.x.x, when I try to perform a DNS trace or navigate to [www.example.com](www.example.com) or check.example.com(both of which are setup on bind) it runs into a wall at my server's internal IP or says page can not be found/displayed.

Again, thanks for any help.
WolfGang

---

### Post by CharlesA on 2011-05-22
You'd have to forward the port for whatever service you want on your router.

If you are on a dynamic IP, look into using something like Dynamic DNS.

---

### Post by wolfgang89 on 2011-05-22
I've tried forwarding port 53 to my server for DNS and I've even tried using Linksys' DMZ setting and forwarding ALL traffic to my server but it still would not resolve properly. Kept hitting a wall on my DNS trace saying it was unable to query the server b/c it was on a private network/IP. Do you know how I would need to setup the server to "host" my internet connection. For example, hook eth0 to the modem and eth1 to the router and have the server act as my router and the router act as a switch(if possible?) or would I need to replace my wireless router with a wireless switch/AP?

---

### Post by CharlesA on 2011-05-22
How did you set DNS up? It should be pointing to your public IP address.

There are a few howtos around, you can start here: [https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router)

---

### Post by wolfgang89 on 2011-05-22
I can get it working internally with private IP addresses but I wasn't able to get it working externally whether using private or public IP addresses. Think I'll try setting it up as a router and using my current router as an AP only. Thanks for the help. Any other ideas are still welcome.

Thanks
WolfGang

---

### Post by CharlesA on 2011-05-22
If you can't get to it from the public ip, then make sure you have port forwarding on your router set up correctly.

You can use something like [http://www.canyouseeme.org/](http://www.canyouseeme.org/) to see if your machine can be seen from the internet. :)

---

