---
title: "SSL without users having to confirm certification"
date: 2011-06-11
forum: Security
---

### Post by wsonar on 2011-06-11
I am looking for the best method to implement SSL for my sites but without users having to accept the CERT and I'm small so I'd want to use the cheapest method like signing my own certs. Is there an automatic way of doing it or best practice?

---

### Post by bodhi.zazen on 2011-06-12
There is not a way to easily avoid this with self signed certs.

---

### Post by Thewhistlingwind on 2011-06-12
If there was a way for you to avoid it, anyone could avoid it. (AKA, phishing sites.)

---

### Post by BkkBonanza on 2011-06-13
The closest to this is to have your users visit a page and click a link to install your (self-signed) CA cert into their browser, before visiting your site requiring client cert access. You might do this if you have a fairly limited user base who somewhat trust your site (friends maybe). But for the general public this doesn't work so well because more astute users are going to balk at the idea of installing your CA cert into their browser (and they should feel uneasy!). 

The page to install your CA cert is easy to setup if that idea works for you. It's just not very satisfactory for general public visitors. You might have visitors go there upon sign-up via an email link or something, with an explanation of why.

The next best thing I think is to use free certificates from startssl.com. They work well enough and are recognized in browsers without warnings. I've always just been a bit suspicious of them being based in Israel - but I haven't read about any evidence of suspicious behaviour, so who knows.

---

### Post by Lloyd_mcse on 2011-06-14
COMODO do a free 90 day SSL, no strings!
 
[http://www.instantssl.com/ssl-certificate-products/free-ssl-certificate.html](http://www.instantssl.com/ssl-certificate-products/free-ssl-certificate.html) 
 
I got a cheap SSL cert from a host I know.. uh-hosting.co.uk IIRC for £45.

---

### Post by Het@l99 on 2011-06-15
Well as all said there is no way to avoid it otherwise every one can do like that and get the SSL certificate.

---

### Post by i.r.id10t on 2011-06-15
StartSSL gives a free 1 year cert ...

---

### Post by Lloyd_mcse on 2011-06-15
> **i.r.id10t said:**
> StartSSL gives a free 1 year cert ...
 
Good to know :D

---

