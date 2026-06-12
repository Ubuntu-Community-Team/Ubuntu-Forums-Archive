---
title: "Domain name nomenclature"
date: 2008-09-16
forum: Server Platforms
---

### Post by botfish on 2008-09-16
I am setting up an Ubuntu server which will be connected to my home network. It is not intended to be accessed from outside.

My Ubuntu server will be set up to host a number of different sites I am working on. At a later date I will be adding other servers to my network, some of which will be accessed from outside.

My question is: What is the best nomenclature for generating the domain names?

I am thinking of the following but is it a correct use of the "localhost" top level domain?

Sitename.ComputerName.localhost
e.g.
mywiki.server1.localhost
myblog.server1.localhost

What is considered best practice?

---

### Post by promodus on 2008-09-17
Category: Best Current Practice
Title: Reserved Top Level DNS Names
[ftp://ftp.rfc-editor.org/in-notes/rfc2606.txt](ftp://ftp.rfc-editor.org/in-notes/rfc2606.txt)

More DNS RFC's
[http://www.dns.net/dnsrd/rfc/](http://www.dns.net/dnsrd/rfc/)

---

### Post by botfish on 2008-09-17
rfc2606 indicated to me that .localhost can be used as a top level domain name so I take it that my examples in the original post are valid.

Only problem I have with this is that localhost is usually mapped to the loopback address so to me it dose not make too much sense to use localhost as a TLD.

What do large network admins do? Would they purchase a second level domain name and use that? I will soon purchase a domain name (example.com). Would I then use the name

myblog.computername.example.com

Cheers

---

### Post by lazyart on 2008-09-17
Just use .local as your internal tld.

---

