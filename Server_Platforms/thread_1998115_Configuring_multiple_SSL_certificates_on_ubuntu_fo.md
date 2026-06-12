---
title: "Configuring multiple SSL certificates on ubuntu for apache"
date: 2012-06-06
forum: Server Platforms
---

### Post by Nadil2030 on 2012-06-06
Dear all,

I have two domains hosted out of the same IP address. Take them as [www.example1.com](www.example1.com) [www.example2.com](www.example2.com) 

I have purchased two different SSL certificates for individual domains and how do I create virtualhost definitions to include the SSL certificates?

---

### Post by SeijiSensei on 2012-06-06
Short answer is you need two IP addresses, one for each secure host.  Name-based virtual hosting and SSL don't mix.

---

### Post by stmiller on 2012-06-06
It's now possible to do this with one IP:

[http://wiki.apache.org/httpd/NameBasedSSLVHostsWithSNI](http://wiki.apache.org/httpd/NameBasedSSLVHostsWithSNI)

Cheers,

---

