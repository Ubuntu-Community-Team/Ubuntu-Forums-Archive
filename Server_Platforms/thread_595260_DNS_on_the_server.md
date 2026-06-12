---
title: "DNS on the server?"
date: 2007-10-28
forum: Server Platforms
---

### Post by bone2006 on 2007-10-28
I'm trying to run a server at of my house for awhile.  I don't have a static IP address and I've registered with godaddy.  I'm really not 100% sure what the DNS server if I install it will do for me?

What would I need it for?

I don't have a static IP address, so I put a router on that I flashed it with third party software and I've been pointing it to no-ip.org and I'm not sure how to configure it for the IP I'm now paying at godaddy to be honest, so that if my IP changes that it will send the info to godaddy and it will update it.  Would the DNS server do that or should I continue trying to figure out how to configure the DDNS (Not DNS) on my router?

Sorry maybe I'm just a little confused
Thanks in advance.

---

### Post by conjur3r on 2007-10-28
You don't need a DNS server on such a small scale as yours.  Take a look at the scenarios in which you would employ a DNS server from here [https://help.ubuntu.com/community/BIND9ServerHowto](https://help.ubuntu.com/community/BIND9ServerHowto) (near the top).

Alot of routers these days can automatically update a DDNS service such as no-ip.com or dyndns.com.  In these routers, it is built in and you do not have to pay for this service.  These DDNS services allow users with dynamic IP addresses to map back to their IP address using the simple URL provided to you.  If this is your only intention, then there is no need for a DNS server.

---

