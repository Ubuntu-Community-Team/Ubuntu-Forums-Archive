---
title: "Apache HTTPS"
date: 2012-02-03
forum: Server Platforms
---

### Post by DanHorniblow on 2012-02-03
Hi, I have a server that multiple sites are hosted on using virtual hosts.

I want one of these sites to be served over https. It is a webmail interface and I would prefer it to be accessed securly.

I am not going to buy a SSL. So I want to use an unsigned one.

How would I force a virtual to only be served via https.

Thanks Dan

---

### Post by Lars Noodén on 2012-02-03
It's a good question.  It's been ages since I've done that and the material on the net is a bit dated, too, and doesn't match so well with Apache2.  

If I recall correctly, it will be some combination of the [SSLRequireSSL](http://httpd.apache.org/docs/2.2/mod/mod_ssl.html#sslrequiressl) directive and a rewrite rule.

---

