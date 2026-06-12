---
title: "Multiple application + one IP"
date: 2011-11-02
forum: Server Platforms
---

### Post by fabianofernandes on 2011-11-02
I have only one IP (without domain) and I want to put multiple applications on my Apache
ex:
xxx.xxx.xxx.xxx/app1
xxx.xxx.xxx.xxx/app2
xxx.xxx.xxx.xxx/app3

How do I configure my virtualhost to work this way

[]`s

---

### Post by koenn on 2011-11-02
you make an apache virtualhost for each app

you're going to need hostnames, though - 1 for each app


what you're going for is
app1.domain.tld
app2.domain.tld
app3.domain.tld

---

