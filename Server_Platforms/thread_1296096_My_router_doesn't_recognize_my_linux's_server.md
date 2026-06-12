---
title: "My router doesn't recognize my linux's server"
date: 2009-10-20
forum: Server Platforms
---

### Post by any.linux12 on 2009-10-20
Hi!

I want to finish my email server but my router is driving me crazy. All my servers are behind my router and when I want to configure the NAT from the router it only recognizes my workstation's hostname and my servers are shown as ip's only.

when I did the configuration for my website there was no problem, I just pointed the http to the ip 192.168.1.195 and it was fine, but for the email server I have to give a hostname to the software. in my case zimbra

Additional info: The router is a Motorola 3356 and my servers are all ubuntu 8.04

thanks

---

### Post by Vegan on 2009-10-20
Routers only know IP addresses. Be sure you forward ports so that services get to the server properly.

Also be aware only one kind of server can live behind NAT as there is no way to tell which one to go to.

---

### Post by Lars Noodén on 2009-10-20
People outside your LAN will have to use your external IP address.

You might look at dnsmasq.  You can set it to map a few hostnames to specific ip numbers and then pass all other queries on to the main dns service.

[INDENT][FONT="Courier New"]address=/www.linux12.org/192.168.1.195[/FONT][/INDENT]

---

### Post by mutrax on 2009-10-20
With current hardware you could configure a dhcp & dns server on the linux box.

Anyway, I use to have similar problems until I booted my old router and replaced it with one that handles dns, static dhcp leases, vpn, etc.... linksys [wrt54gl]("http://www.linksysbycisco.com/US/en/products/WRT54GL") + [dd-wrt]("http://www.dd-wrt.com/wiki/index.php/What_is_DD-WRT%3F#Features") firmware was for me the quickest solution.

---

