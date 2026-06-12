---
title: "Domain resolving to two ip adresses based on the availability."
date: 2010-04-17
forum: Server Platforms
---

### Post by cherva on 2010-04-17
I have a server with 2 internet connections from 2 providers. And I want to make my server reachable at all times, no matter if one of the connections go down. I can make a php script on a hosting company to redirect my domain to a certain sub domain ( subdomain1.domain.com and subdomain2.domain.com ) ,but the problem is that I want it to be reachable not only with internet browsers ... I have developed a GPS server and I don't think that if I make the gps devices give their coordinates to domain.com and domain.com redirect them to subdomain1 or subdomain2 they are going to understand that and start sending the data to one of the subdomains automaticly.... All ideas are welcome.

---

### Post by Xipher on 2010-04-17
You will need some form of protocol agnostic service to handle that. Might look into [http://www.linuxvirtualserver.org/](http://www.linuxvirtualserver.org/) to help you out with this.

---

### Post by Bachstelze on 2010-04-17
All you need is a DNS round robin with the two IPs:

[http://www.zytrax.com/books/dns/ch9/rr.html](http://www.zytrax.com/books/dns/ch9/rr.html)

---

### Post by Xipher on 2010-04-17
> **Bachstelze said:**
> All you need is a DNS round robin with the two IPs:

[http://www.zytrax.com/books/dns/ch9/rr.html](http://www.zytrax.com/books/dns/ch9/rr.html)

That won't handle connectivity failure at all.

---

### Post by cherva on 2010-04-17
If the linux virtual server's load balancer is down it will stop working as well.... I was thinking about a managed DNS (that one that has a program that watches your IP and if it change the program updates your DNS) So a script that pings an always available site like google and if google does not respond bring down the current internet connection and bring up the backup one ... then the program will see the change of the IP and update the DNS...

---

