---
title: "DNS Server Question"
date: 2010-08-30
forum: Server Platforms
---

### Post by amorphism on 2010-08-30
Hey all,

I'm a real rookie when it comes to DNS, but i'm wondering if it is possible to setup a DNS server to resolve a host on a dynamic DNS domain name? 
For example:
If my domain is "example.dyndns.org" and someone from outside my network goes to "server1.example.dyndns.org" it resolves to one web server in my network, but if someone goes to "server2.example.dyndns.org" it resolves to a different web server in my network. 

:confused:
Thanks for any help,

---

### Post by anchise on 2010-08-30
Dyndns will resolve your domain to the external IP of your internet router. From there you will have to use NAT.

So let's say you NAT all incoming connections for port 80 to Server A, then on server A you have to take care to redirect the http requests to the correct web server in your LAN.

---

### Post by Bachstelze on 2010-08-30
Or you can use IPv6, if available. But either way, you probably can't have subdomains on a dyndns domain.

---

### Post by amorphism on 2010-08-30
Well that answers that one. No sub-domains kinda sucks for my application. i guess i will have to stick with port forwarding and redirects.

Thanks for the help and quick responses.

---

### Post by anchise on 2010-09-02
If you use redirects then all traffic will go via your only externally visible web server.

Why don't you try this:
Server A (the one to which port 80 is natted) does not redirect (and thusly relaying) the incoming requests for the different subdomains, but sends http 301 moved permanently.

Let's say you NAT port 80 to server A, port 81 to server B and port 82 to server C.

Then server A should answer each incoming request for B.yourdomain.tld with a 301 moved permanently Location=yourdomain.tld:81.

Server A should answer each incoming request for C.yourdomain.tld with a 301 moved permanently Location=yourdomain.tld:82.

---

