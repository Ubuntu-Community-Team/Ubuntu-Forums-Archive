---
title: "Apache - Allow Certbot Renewal on IP Limited Subdomain?"
date: 2019-11-01
forum: Server Platforms
---

### Post by Kirk Schnable on 2019-11-01
Hello,

Maybe a simple question but I haven't had any luck getting it working so far...

I have a subdomain on an Apache 2.4 server that I am limiting to an IP whitelist:
```
<Directory "/home/secure/www">
        Options Indexes FollowSymLinks
        AllowOverride All


        # Allowed IPs
        Require ip a.b.c.d
        Require ip a.b.c.e
        Require all denied
</Directory>
```

I want to allow Certbot \ Let's Encrypt to generate an SSL for this domain, so it needs to complete the ACME challenge.

Therefore I need to exempt a path from this IP limitation:  /home/secure/www/.well-known/acme-challenge

I tried creating another directory declaration, but I am still getting a 403 response:

```
<Directory "/home/secure/www/.well-known/acme-challenge">
        Options Indexes FollowSymLinks
        AllowOverride All

        Require all granted
</Directory>
```

Anybody have any ideas how I can get this working?

---

### Post by LHammonds on 2019-11-02
There are several ways to skin that cat.

You could find out the IPs used by Certbot and add them to the exception list.
You could instead use DNS validation instead of HTTP.
You could setup another apache config using the same domain/port but points to a different folder...then disable your real site, enable the temp site that is not IP-restricted, run the certbot against that, then disable that site, re-enable your real site and modify your real site to use SSL and the certs that were created while the other site was active.

There are probably a few other ways as well but that is what came to mind without any research.

LHammonds

---

### Post by Kirk Schnable on 2019-11-03
> **LHammonds said:**
> There are several ways to skin that cat.

You could find out the IPs used by Certbot and add them to the exception list.
You could instead use DNS validation instead of HTTP.
You could setup another apache config using the same domain/port but points to a different folder...then disable your real site, enable the temp site that is not IP-restricted, run the certbot against that, then disable that site, re-enable your real site and modify your real site to use SSL and the certs that were created while the other site was active.

There are probably a few other ways as well but that is what came to mind without any research.

LHammonds
Thanks, but I was really hoping for something more permanent.  Certbot's IPs could change and those other solutions require manual intervention to perform renewal.  I would think it should be possible with the authz module to apply a less restrictive access list to a subdirectory of a more restricted one, or is that just simply not possible?

---

### Post by LHammonds on 2019-11-05
Everything I mentioned could be automated.

However, the DNS method would probably require hosting your own DNS server.

LHammonds

---

