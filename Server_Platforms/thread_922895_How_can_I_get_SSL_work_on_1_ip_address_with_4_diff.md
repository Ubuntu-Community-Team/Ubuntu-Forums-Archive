---
title: "How can I get SSL work on 1 ip address with 4 different sites"
date: 2008-09-17
forum: Server Platforms
---

### Post by kustomjs on 2008-09-17
Hi Guys
can anybody tell me how would I be able to get SSL to work on my server with 1 ip address and 4 different domain/names.

---

### Post by RealPSL on 2008-09-17
[http://httpd.apache.org/docs/2.2/ssl/ssl_faq.html#vhosts2]("http://httpd.apache.org/docs/2.2/ssl/ssl_faq.html#vhosts2")

The only way that I am aware of is to use different port numbers which is probably not the answer you are looking for. Name based solutions will not work.

---

### Post by kustomjs on 2008-09-17
ok so how would i do that like 443,444,445,446,447 correct?

---

### Post by MJN on 2008-09-18
That's right (although that's five ports... ;-))
 
There are some alternatives which may or may not be suitable for your requirements:
 
- Using a wildcard certificate e.g *.example.com would allow foo.example.com and bar.example.com sites to both use the same certificate on the same IP/port without error. If your virtual hosts are not within the same domain then this won't work for you.
 
- Taking advantage of the TLS Upgrade feature of RFC2817 - this allows HTTPS to be inititiated after a standard HTTP connection hence it occurs after the HOST header request has been served. Unfortunately browser support for this is not very widespread so you would have to rely on it with caution.
 
- Serve all your hosts from the same IP/port using the same certificate and accept the common-name mismatch error on first connection. This is very inelegent but if all you're after is encryption of traffic (and no authentication) then it might be sufficient.
 
- As a slight tweak on using multiple ports, you could establish redirects for your hosts on standard HTTP connections. That is, make [http://foo.example.com](http://foo.example.com) redirect to [https://secure.example.com:443](https://secure.example.com:443), and [http://bar.example.com](http://bar.example.com) redirect to [https://secure.example.com:444](https://secure.example.com:444), etc. This would allow your users to use the 'familiar' names for initial connection without having to specify particular ports. It does take the edge off the authentication benefits of SSL but it still might suffice for your circumstances.
 
Mathew

---

### Post by kustomjs on 2008-09-18
so now I got to make subdomain account to make it secure or how would I configure the different ports?

---

### Post by HermanAB on 2008-09-18
Honestly, your best, easiest and most cost effective solution is to buy more IP addresses from your ISP.  For about $10 per month you can save yourself and your customers from a whole world of hurt by doing it the right way.

Cheers,

Herman

---

### Post by kustomjs on 2008-09-18
this is the reason why I went to hosting my own server because I dont have the money right now to pay 10 or 20 dollars extra a month if comes down to it I will install extra nic card or get extra computer.

---

### Post by HermanAB on 2008-09-18
You can have as many IP addresses as you want on a single NIC.  So it is not a hardware problem.  The problem is that your ISP has to assign you more IP addresses.

---

### Post by kustomjs on 2008-09-18
so can i go and get ip address from like no-ip or similar or do I have to go my ISP and pay other 39.95 a month for other ip address.

---

### Post by kustomjs on 2008-09-18
can somebody please tell me how to install/enabled TLS onto my server.

if this helps anybody I got openssl and mod_ssl installed onto my server

---

