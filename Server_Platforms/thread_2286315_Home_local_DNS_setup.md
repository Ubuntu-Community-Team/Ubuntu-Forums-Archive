---
title: "Home local DNS setup"
date: 2015-07-11
forum: Server Platforms
---

### Post by denis35 on 2015-07-11
I have about 10 VMs and a few other devices in my home and would really love to work with hostnames / fqdn's.  
DNS/BIND is pretty intimidating for me.  All I want is to have a local domain name / host name that my computers/devices can resolve.

Is there a cookbook for simple home DNS setup with Ubuntu 14.04? 
DNS and DHCP is being handled by my home router now.  I don't have have a physical host to run DNS was hoping to put in a VM.

I have a public domain name that would be cool to use as my home domain if that would be ok.

Thanks

---

### Post by volkswagner on 2015-07-11
What model router do you have? In my opinion the easier solution for home use is to have the router handle DNS. If your router is capable of running OpenWRT or DD-WRT, they both use DNSmasq as the service for both DHCP and DNS.

---

### Post by Doug S on 2015-07-11
> **denis35 said:**
> Is there a cookbook for simple home DNS setup with Ubuntu 14.04?You try using the [Ubuntu Server guide]("https://help.ubuntu.com/lts/serverguide/dns.html").
> **denis35 said:**
> I have a public domain name that would be cool to use as my home domain if that would be ok. That is what I do. Externally, my ISP nameservers handle my domain. Internally, I handle it with my DNS server. That way if some portable device (i.e. a laptop) is taken from internal to external, at least the externally facing stuff (i.e. web page links) still work.

---

### Post by denis35 on 2015-07-13
My router is a Netgear R700.  Looks like DD-WRT can be loaded on it..
[http://dd-wrt.com/wiki/index.php/DD-WRT_on_R7000](http://dd-wrt.com/wiki/index.php/DD-WRT_on_R7000)

I'm not sure what's the best approach, dd-wrt or run dns in a vm.  I've been through dozens of routers and don't like the idea of losing my local dns if I change routers.  However if dnsmasq is simple to setup than maybe that's my best option. 

I think I'll follow the above guide and see how I make out.  I'm sure I'll have more questions.

Thanks for the replies.

---

### Post by CharlesA on 2015-07-13
I tried it both ways, but it was easier for me to just run DNS off the router via dnsmasq. With that said, I do have a dns server on the network but it's set up for my development/test environment, so I can test stuff without screwing with production.

---

