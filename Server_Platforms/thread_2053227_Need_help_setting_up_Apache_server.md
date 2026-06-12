---
title: "Need help setting up Apache server"
date: 2012-09-04
forum: Server Platforms
---

### Post by Rakeda on 2012-09-04
Hello Ubuntu I've been looking over this forum for about a week now but recently on my ubuntu server I finally decided to put it online.

Since I'm using verizon FiOS I needed to access port 80 so I DMZ'd my main router and connected my laptop to the upstairs router and port forwarded my port's on my laptop through the router's firewall. And opened the port on my laptop and both routers to access my laptop. So my port's are opened now but whenever I type in my WAN it takes me directly to my downstairs router page instead of the /ect/www/ folder like 127.0.0.1 and 192.168.x.xxx do.As mentioned in the sentence before I already did try 127.0.0.1 and my LAN ip and they both work, but the WAN isn't connecting to my laptop, it is connecting to my router downstairs.

Specs-
Root user,
10.04 LTS

---

### Post by Bachstelze on 2012-09-04
Some routers disallow connecting to yourself via your public IP. Ask someone outside your LAN to try it for you.

---

### Post by Rakeda on 2012-09-04
> **Bachstelze said:**
> Some routers disallow connecting to yourself via your public IP. Ask someone outside your LAN to try it for you.

Thank you, that worked! but now my forum page is based on my ip but any links are instantly taken to my 192.168.x.xxx
How do I fix?

---

### Post by Bachstelze on 2012-09-04
The "base" URL should be configurable in your forum engine's configuration panel.

---

### Post by LHammonds on 2012-09-04
If at all possible, use a domain name instead of an IP address when configuring your forum.

Why?  Because on the outside, DNS records can resolve your domain to the external IP which everyone will use to access your forum but internally on your own LAN, you can setup the resolution to the domain name as the internal IP address.  This will allow your forum to work inside or outside your router.

For example, on a Windows PC, you can edit C:\Windows\System32\Drivers\etc\hosts and point forum.mydomain.com to 192.168.1.10 and when you type [http://forum.mydomain.com](http://forum.mydomain.com) in your web browser, it will access the forum via the internal IP address and your forum will continue to operate because it is referencing the domain name...which is resolved to an IP elsewhere and not at the forum level.

LHammonds

---

