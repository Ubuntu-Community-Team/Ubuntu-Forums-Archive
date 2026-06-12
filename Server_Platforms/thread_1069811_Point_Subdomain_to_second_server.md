---
title: "Point Subdomain to second server?"
date: 2009-02-14
forum: Server Platforms
---

### Post by jamieh on 2009-02-14
I have two web servers on the same network, behind the same router (a Linksys BEFSX41), and I have several subomains for my domain set up with VirtualHost entries.

How would I go about pointing a subdomain to the OTHER server, while still using Port 80?
With my router, (AFAIK) you can only forward a port to one server...

mydomain.com > Server A
sub.mydomain.com > Server A
othersub.mydomain.com > Server B

Server A is 192.168.6.107
Server B is 192.168.6.108.

How would I go about doing this?

Thanks

---

### Post by HermanAB on 2009-02-14
That should be done with DNS.  BIND connects hostnames to IP addresses, TCP/IP does the rest.

Cheers,

Herman

---

### Post by hyper_ch on 2009-02-14
his problem is that he's behind a router...

---

### Post by volkswagner on 2009-02-14
Can't this be accomplished with ip directive in vhost file.

I was wondering this myself as I a trying to upgrade my server to new hardware.  I have the email working on new server, but I need to transfer apache hosts.  It would be nice if I could move one at a time and verify each was working with minimal downtime.

Can we use the following directive?

```
<VirtualHost ip.add.ress.otherserver>
```

Then the router won't need to forward to two servers on port 80 as this will be done inside LAN?

Obviously the second server would need a proper vhost running.

Or will this need to be done with a network share as the root directory?

---

### Post by volkswagner on 2009-02-14
duh, I just realized that directive is for listening on multiple IP's.  I can only think of a messy redirect.

---

### Post by JeppeM on 2009-02-15
Hey,

What you're looking for is the an transparent apache proxy... You need to enable mod_proxy and mod_rewrite for this, and then do the following on ServerA:

```
<VirtualHost *:80>
  <IfModule mod_proxy.c>
    <IfModule mod_rewrite.c>
      RewriteEngine On

      rewriteCond %{HTTP_HOST} ^othersub\.mydomain\.com
      rewriteRule (.*) http://192.168.6.108/$1 [P,L]
    </IfModule>
  </IfModule>
</VirtualHost>
```

This is untested, so i can't say that it will work 100%, but it's close... Have a look at Dynamic Mirror in the [URL Rewriting Guide]("http://httpd.apache.org/docs/2.0/misc/rewriteguide.html") (it's about half way down).

hope this leads you in the right direction..

---

