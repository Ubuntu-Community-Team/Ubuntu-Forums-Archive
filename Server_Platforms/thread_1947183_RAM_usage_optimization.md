---
title: "RAM usage optimization"
date: 2012-03-26
forum: Server Platforms
---

### Post by AndrejsLi on 2012-03-26
Hello,

my system is working on Ubuntu server 64 bit v. 10.04. Free RAM is 300 MB.

Homepage when used always get: PHP Fatal error:  Out of memory (error 500 on browser)

I have a default Ubuntu settings, nothing is changing after install.

Current settings httpd:

StartServers       1
MinSpareServers    0
MaxSpareServers    0
ServerLimit        20000
MaxClients       256
MaxRequestsPerChild  20000

PHP memory limit 128

What settings can solve this problem?

Thank you and sorry about my english.

---

### Post by sanderj on 2012-03-26
Wouldn't a PHP forum give better help? It looks like a PHP error, not a Ubuntu/Linux error.

---

### Post by AndrejsLi on 2012-03-26
> **sanderj said:**
> Wouldn't a PHP forum give better help? It looks like a PHP error, not a Ubuntu/Linux error.

I think, it's is in Ubuntu server configuration. Last I had 1 GB RAM system (now 512) and this problem did'nt exist.

Maybe I'm wrong, just a Ubuntu newbie..Can it be in mysql?

---

### Post by AndrejsLi on 2012-03-26
Is it really Mysql configuration? Please, give any suggests.

---

### Post by d4m1r on 2012-03-26
> **AndrejsLi said:**
> Hello,

my system is working on Ubuntu server 64 bit v. 10.04. Free RAM is 300 MB.

Homepage when used always get: PHP Fatal error:  Out of memory (error 500 on browser)

I have a default Ubuntu settings, nothing is changing after install.

Current settings httpd:

StartServers       1
MinSpareServers    0
MaxSpareServers    0
ServerLimit        20000
MaxClients       256
MaxRequestsPerChild  20000

PHP memory limit 128

What settings can solve this problem?

Thank you and sorry about my english.

Those are really high numbers...try lowering them to:


StartServers       1
MinSpareServers    0
MaxSpareServers    0
ServerLimit        1000
MaxClients       100
MaxRequestsPerChild 100

And see if it makes a difference. I am sure it will fix your problem.

---

### Post by AndrejsLi on 2012-03-26
> **d4m1r said:**
> Those are really high numbers...try lowering them to:


StartServers       1
MinSpareServers    0
MaxSpareServers    0
ServerLimit        1000
MaxClients       100
MaxRequestsPerChild 100

And see if it makes a difference. I am sure it will fix your problem.

Thank you. Not absolutely, but it make perfomance much better.

---

