---
title: "Dynamic DNS"
date: 2006-07-04
forum: Server Platforms
---

### Post by systemdown on 2006-07-04
Hi all,
Bit of a linux newbie, and have been using ubuntu as a desktop and also the server distro. Plan is to setup a web server in order to learn more and get some experience. I have done a bit of reading and research....
I want to setup a web server and my own DNS server, now since my ISP gives me a dynamic IP then i require a DDNS. I have mostly been reading about people just using services from dyndns and no-ip.com etc etc
My question is... how does one setup their own DDNS without having to outsource the service of companys like dyndns & no-ip?

---

### Post by reacocard on 2006-07-04
i don't think you can. Services like DynDns simply keep track of what your IP is, and redirect trafic for your domain into that IP. without an external server to keep track, there is no way to tell the domain where to go.

---

### Post by Krieg on 2006-09-11
[www.afraid.org](www.afraid.org)

---

### Post by az on 2006-09-11
> **systemdown said:**
> Hi all,
Bit of a linux newbie, and have been using ubuntu as a desktop and also the server distro. Plan is to setup a web server in order to learn more and get some experience. I have done a bit of reading and research....
I want to setup a web server and my own DNS server, now since my ISP gives me a dynamic IP then i require a DDNS. I have mostly been reading about people just using services from dyndns and no-ip.com etc etc
My question is... how does one setup their own DDNS without having to outsource the service of companys like dyndns & no-ip?

You need someone to host your DNS.

[https://help.ubuntu.com/community/WebServerHosting](https://help.ubuntu.com/community/WebServerHosting)

And most companies offer a free dyndns service:

[https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS)

---

### Post by chrisfay on 2006-09-11
I beleive you can use nsupdate to dynamically update your own DNS server with your new IP if its dynamic. Usually, nsupdate is used to update dynamic clients using your static dns server but if you treat your setup as both the client and the server I think its possible. 

I am in the same boat as I run Bind9 on a cable/dynamic IP. Even though it only changes roughly once a year it still causes an inconvenience having to update all the zones when that happens. Not only that, but even using nsupdate you would still have to update your name servers IP's at the registrar that point to the old IP after it changes; I'm pretty sure that no dymanic dns client could update those records at the registrar.

[http://linux.yyz.us/nsupdate/](http://linux.yyz.us/nsupdate/)
[http://freelock.com/kb/BIND_nsupdate](http://freelock.com/kb/BIND_nsupdate)

---

