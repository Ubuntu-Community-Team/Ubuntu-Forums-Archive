---
title: "ISPConfig and Multiple Domains"
date: 2007-11-14
forum: Server Platforms
---

### Post by bradhawk08 on 2007-11-14
Alrighty, I'm having a couple problems.

First I still can't access ISPConfig externally using the commands:
[http://mydomain.com:81](http://mydomain.com:81) or
[https://mydomain.com:81](https://mydomain.com:81) or
[http://www.mydomain.com:81](http://www.mydomain.com:81) or
[https://www.mydomain.com:81](https://www.mydomain.com:81)

I can access it internally using [http://192.168.1.112:81](http://192.168.1.112:81)

I have my domain provider forwarding my domain to my router's IP address and my router is set up to forward port 81 to 192.168.1.112.

Note: The server computer cannot access internet webpages because the wireless card (linksys/broadcom problem) but it still seems to access my apache web server by [www.mydomain.com](www.mydomain.com).

My next question is how do i set up ISPConfig to take care of two completely different domains.

The names would be something like:

[www.thisisdomainone.com](www.thisisdomainone.com)
[www.completelydifdomain.com](www.completelydifdomain.com)

both need to have there own homepage and such, but I only have one IP (static local 192.168.1.112) and one IP for the router (which port forwards port 80 to the static local IP)

Please I'm brand new at setting up servers.  I would be greatly appreciate for some help.  Let me know if you need more info.

I'm using a clean install of Ubuntu Server 7.10 (Gusty Gibbon)

Thanks!

---

### Post by Fullback on 2007-11-15
Hey, I am also having the same problem. I bought a domain from godaddy.com and used zoneedit.com to point it to my ip address. And i have a DDNS in my router set up to, so when i ping my domain i get my ip address. Though after port forwarding I cannot still access ISPconfig through the outside network, I can only access it through my Lan network.

---

