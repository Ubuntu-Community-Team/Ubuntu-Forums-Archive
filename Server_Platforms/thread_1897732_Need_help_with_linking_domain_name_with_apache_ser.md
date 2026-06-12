---
title: "Need help with linking domain name with apache server"
date: 2011-12-19
forum: Server Platforms
---

### Post by KrisDeniseRiley1 on 2011-12-19
So I downloaded LAMP so that I could do a little bit of website design for fun, and to have others give ideas when viewing. I went through dyndns.com and got a domain name. It does have the right public address linked to it. I was able to have a friend get to my server via the ipaddress:port method. For some reason I can't seem to get the domain name in the url to work instead of using an ip address. I did put my server pc on the DMZ with a ufw firewall allowing only port 80 access. Oh, I also cannot ping the domain name either.....HELP!! Do you also have any suggestions to the way I set it up?

---

### Post by Dangertux on 2011-12-19
> **KrisDeniseRiley1 said:**
> So I downloaded LAMP so that I could do a little bit of website design for fun, and to have others give ideas when viewing. I went through dyndns.com and got a domain name. It does have the right public address linked to it. I was able to have a friend get to my server via the ipaddress:port method. For some reason I can't seem to get the domain name in the url to work instead of using an ip address. I did put my server pc on the DMZ with a ufw firewall allowing only port 80 access. Oh, I also cannot ping the domain name either.....HELP!! Do you also have any suggestions to the way I set it up?

Have you tried to see if your friend can reach the domain externally? 

If you are on the same network as the machine it is likely your router does not support NAT loopback, so you can not connect to the external IP or a hostname that resolves to it from inside the network.

Let me know if the domain is still not accessible externally (note DNS propogation changes with DynDNS can take up to 24 hours, even though it's supposed to be quickly).

---

