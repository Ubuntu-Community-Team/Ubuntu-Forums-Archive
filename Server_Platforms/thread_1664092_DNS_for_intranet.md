---
title: "DNS for intranet"
date: 2011-01-10
forum: Server Platforms
---

### Post by Ed_Ziffel on 2011-01-10
Objective:  Set up local website where local users can enter xyz.com into their browsers and get to the index of that site on a local server.

The server manual indicates the the /etc/hosts file can be used to do this as it will override the DNS.  What is not clear is whether this is in reference to just the local DNS from the server or from the LAN's router.  Currently the LAN's DNS is handled by the router and the server DNS is disabled (I think).  

Does someone know the correct DNS configuration for a LAN with a router internet connection to enable the use of the hosts file and why?  "Guess a setting" might work but it is always better to know what ur a doin.

The LAN is set up stacic and have tested getting to the index page in var/www by using the local server ip in a browser.

---

### Post by rubylaser on 2011-01-10
The /etc/hosts file will override the settings provided by the DNS server, but you would have to manually edit each users host file, and every time after that if something changes.  It's much preferred to use your router or DNS server to properly match the hostname with the ip providing the service.

For instance
```
10.1.1.15    intranet.yourcompany.net
```

---

### Post by stlsaint on 2011-01-10
> Objective: Set up local website where local users can enter xyz.com into their browsers and get to the index of that site on a local server.

You are wanting a domain without getting a FQDN. That is not going to happen. Google: [FQDN]("http://en.wikipedia.org/wiki/FQDN"). This assuming you dont already have one.

Then i know you will need to edit the /etc/hosts file but you may also need to edit the /etc/resolv.conf. 
Try looking up in terminal:
man HOSTS
man RESOLVER

Also if its on a local server and you want to keep it intranet, you will have to edit every client that connects to that server manually. Instead you should let the router do all the heavy lifting. Or as i just noticed a little too late from the other person who replied, go with a in house DNS server.

---

### Post by NIT006.5 on 2011-01-10
Is xyz.com your local domain or something totally different? The setups I do generally have an Ubuntu server running as firewall/router/dhcp/ddns, where public DNS for the domain is hosted by the ISP and internal DNS is handled by the local server (mostly applicable to small/medium businesses). If it's your local domain which is already being handled internally, then it's just a matter of adding a host record for 'www' on your domain. If that domain is not already being handled internally, then you need to create a zone for it, plus a host record. If this is not the same as your lan domain, I'm not sure if your router will allow you to configure a second domain or not, as a lot of routers will only provide dhcp and ddns for the one local domain. And if that's the case, you might be better off running DNS on the server where you can set up multiple zones.

As stated by rubylaser above, the hosts file only applies to the local machine and not the rest of the LAN, so I wouldn't see that as an option (unless you have a very small LAN).

---

### Post by Ed_Ziffel on 2011-01-10
> You are wanting a domain without getting a FQDN. That is not going to happen. Google: FQDN. This assuming you dont already have one.

As long as the domain is local only it could be what ever.  The xyz.com is just a generic think xyz as variables, and the .com as arbitrary. Already have 6 domains on a commerical server although I don't remember the exact requirements for a fully qualified domain name.  will glance at that again.
> 
 The setups I do generally have an Ubuntu server running as firewall/router/dhcp/ddns, where public DNS for the domain is hosted by the ISP and internal DNS is handled by the local server (mostly applicable to small/medium businesses)

Yeah, now that's where I want to be!  You mentioned zones and possibly setting up different domains on my router.  Point me the right direction with the zones and I'm downloading the manual for my router as I'm typing this.  

Also how do I set up the server as a firewall/router/dhcp/ddns?  This is exactly what I would like to learn!

Thanks

---

### Post by elico on 2011-01-10
leave the FQDN stuff!!!
he wants to make his users get it done so let it be...
in the DHCP server\router put the inside DNS as the primary DNS and make the DNS forward everything you want to your router DNS or your ISP DNS.
and then every DNS request that wont be found on the local DNS will be forwarded to the DNS ISP server.


and if you want to setup your server as al lthe above you will need to now\learn:
 IPTABLES, little BIND9 DNS, DHCPD, DDCLIENT or BIND9 nsupdate and the last thing is dial-up\vpn +routing.

---

### Post by NIT006.5 on 2011-01-11
> **Ed_Ziffel said:**
> Yeah, now that's where I want to be!  You mentioned zones and possibly setting up different domains on my router.  Point me the right direction with the zones and I'm downloading the manual for my router as I'm typing this.

You can check the router manual, but chances are you won't be able to do it there because its probably not really designed for that. If by some chance your router does handle multiple zones, configuration will obviously depend on the router and you'd just have to follow the manual.

I would guess though, that you'll probably need to set up the server for this though.

> **Ed_Ziffel said:**
> Also how do I set up the server as a firewall/router/dhcp/ddns?  This is exactly what I would like to learn!

There's no quick and easy way to do this, and you'll need to learn it in stages.

Firewall/router: For starters, you need to be aware of the kernel's IP routing tables (man route), although if you only have two interfaces on the box, most of this is done automatically by Ubuntu server once it knows what your local networks are (see file /etc/networks). The rest will be done with iptables, including the actual firewall and any PAT/NAT that is required. In my opinion, iptables is not something that should be rushed either, because of the security implications. To do it properly will take a lot of research, so prepare yourself ;) There are differing levels of paranoia but generally I would suggest starting with a firewall that blocks absolutely all traffic, and then work on opening up only what is required for your network. You could also look at UFW which is shipped with Ubuntu server, but while this gives you a slightly easier interface to iptables in the beginning, functionality is limited. So I definitely recommend learning iptables.

DHCP/DNS: When I was first learning this, my life was made considerably easier by using webmin to do most of the dhcp/dns config. But once again, it will take considerable research. I would start by configuring dhcp and dns individually, only afterwards (once you've mastered both) look at getting them to work together for dynamic dns (because that can be tricky at first).

As always, my advice is to start with the official Ubuntu Server guide for the version you're working on, rather than using the first how-to that Google spits up, because you never know if its correct or out-of-date, etc. Whatever isn't covered in the server guide you can always research separately, but I think its best to start there.

Even if you do start off using something like webmin to make it easier, its always best to know what's going on in the actual configuration files (especially if you're lazy like me and would want to script the configurations later).

---

### Post by ripat on 2011-01-12
It is quite straight forward. On your server, install the lightweight dnsmasq which is a DNS cache and dhcp server.

In the /etc/dnsmasq.conf add a rule pointing to a file that will redirect (resolve) the FQDN to a local address.

Example, your local dev web server's ip: 1.2.3.4

1 - Create a file dnsmasq.redirect (or whatever) with:
```
address=/sco.com/1.2.3.4
address=/microsoft.com/1.2.3.4
address=/oracle.com/1.2.3.4
```

2 - Add a line in the dnsmasq.conf file:
```
conf-file=/etc/dnsmasq.redirect
```

3- In your lan DHCP server change the DNS server address to 1.2.3.4 so that all the hosts will use your dnsmasq server as DNS server.

4- make sure you have proper upstream servers set in the server's resolv.conf file (i.e. your ISP's upstream servers)

5- restart dnsmasq

You could skip step 1 and 2 and insert directly the *address=* rule in the dnsmasq.conf file but it is easier to keep it separated if you have a lot of domain names to redirect. 

I use that system on my router to block all ads for all the hosts of my lan. It's lightning fast despite the fact that my router only has 16 MB of ram. No need to install a full fledged Bind to achieve this.

---

### Post by chrislynch8 on 2011-01-12
I have something similar - in which I have a web based app running on a local server. Users accessed it via the ip address and path. But I wanted them to access it using a url.

Create a new DNS zone that will point xyn.com to the IP address of the server. Then in the Apache2, create a Virtual Directory that will point all requests for xyn.com to the /var/www/directory

Works a charm for me

---

