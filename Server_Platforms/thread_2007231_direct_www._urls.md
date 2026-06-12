---
title: "direct www. urls"
date: 2012-06-20
forum: Server Platforms
---

### Post by Varemenos on 2012-06-20
I have setup a LAMP VPS (pointed the hostname to the nameservers etc) and its almost ready to use but i have 1 problem:
When using the www. urls it returns Server not found so should i make another A record and point it to the [www.subdomain.domain.tld]("http://www.subdomain.domain.tld") or is there a better way of fixing this problem?

---

### Post by spynappels on 2012-06-20
you could just make a cname record for the www subdomain and point it to the A record.

---

