---
title: "DNS Issue with www"
date: 2008-09-12
forum: Server Platforms
---

### Post by slooksterpsv on 2008-09-12
Hey all,

I'm having a problem with DNS right now on my server. I can add different subdomains, no problem, but the www portion isn't working. I'm trying to figure out if it's something on my end, or if I need to wait for the DNS Servers to update.

I tried to setup my server behind a router and doing NAT so I gave the bind and apache info 10.10.0.100, I also setup some things in my modem for that, but since then I've disabled NAT and set my modem in bridge mode and removed all the 10.10.0.100 and replaced it with my IP address. Now I can add new subdomains, but cannot get [www.slookytech.com](www.slookytech.com) to work. <--- I've checked my info it all looks good. So is it on my end or other?

---

### Post by jerome1232 on 2008-09-12
```
nslookup www.slookytech.com
Server:		192.168.1.3
Address:	192.168.1.3#53

Non-authoritative answer:
Name:	www.slookytech.com
Address: 10.10.0.100
```

Looks like it's still saying 10.10.0.100 I just ran that.

---

### Post by slooksterpsv on 2008-09-12
How do I fix that though?

---

### Post by windependence on 2008-09-12
You don't need a DNS server to run your web site. You need to go to your domain registrar's control panel and point your 'A' record at your server's external IP address (or your router in your case). Since you have Apache running and working, make sure port 80 is forwarded back to your server IP on the LAN and then check to see ikf your ISP is blocking port 80 by going to [www.canyouseeme.org](www.canyouseeme.org) and check the port to make sure it's open.

I really think we should take out the BIND part of the perfect server tutorial because it isn't necessary unless you have many many machines on your LAN, and it just seems to confuse everyone.

Let me know how you make out with this.

-Tim

---

### Post by slooksterpsv on 2008-09-12
Sorry, I may have that a little confused, but I am running BIND9 on my server, and my server is getting a public IP of 66.111.118.76, here's my db file:

;
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     dns.slookytech.com. shawn.slookytech.com. (
                     2008091202         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
        IN NS dns.slookytech.com.
        IN MX 0         pop.slookytech.com.

                IN A    66.111.118.76
pop             IN A    66.111.118.76
www             IN A    66.111.118.76
ftp             IN A    66.111.118.76
mail            IN A    66.111.118.76
melicrules      IN A    66.111.118.76
eyeos           IN A    66.111.118.76
psp             IN A    66.111.118.76
dns             IN A    66.111.118.76
www3            IN A    66.111.118.76
shawn@shawn-desktop:/etc/bind/dns$

Not sure if that helps, but that's what it has on it. I'll check on GoDaddy

EDIT:
I can get to my site by going to slookytech.com, but not [www.slookytech.com](www.slookytech.com)

---

### Post by windependence on 2008-09-12
OK then you need to set up a CNAME in your Godaddy panel. Give them a call and tell them what you wanna do. they will walk you right through it. And no, you STILL don't need BIND9 (your DNS server).

-Tim

---

