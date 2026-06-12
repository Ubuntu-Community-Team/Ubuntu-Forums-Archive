---
title: "Hosting webserver sithout static ip"
date: 2009-10-02
forum: Server Platforms
---

### Post by bonzi on 2009-10-02
I am planning to host a ubuntu web server (connected to internet). I dont have a static ip. How ever i have the domain names. Can I host a webserver without a static ip??

---

### Post by undecim on 2009-10-02
If you have dynamic IP addresses, it's probably against your ISP's ToS to run a web server for more than personal use (check on this.)

Some DNS services will have a feature that lets you update your IP by visiting a web address. Just add this address to a cron job

---

### Post by gordintoronto on 2009-10-02
Also have a look at no-ip.com.  I believe it has competitors.

---

### Post by jptech on 2009-10-02
If your domain registrar has advanced DNS services you can use a CNAME entry + DynDNS to get something that would work reasonably well.  It works ok for personal use, but isn't a good solution for a production site.

Assuming you are using mydomain.com as your custom domain and have a DynDNS account that always resolves mydyndnsname.dyndns.org to your external IP, add a CNAME record for (ex):

[www.mydomain.com](www.mydomain.com) --(CNAME)--> mydyndnsname.dyndns.org

The interfaces for setting up DynDNS on your router and using advanced DNS from your registrar vary greatly, so YMMV.

---

