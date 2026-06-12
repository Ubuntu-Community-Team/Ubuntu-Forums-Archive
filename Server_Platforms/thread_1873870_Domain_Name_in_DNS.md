---
title: "Domain Name in DNS"
date: 2011-11-02
forum: Server Platforms
---

### Post by stockie on 2011-11-02
Hello guys,

i wont create a DNS Server and i have a question about the config file in /etc/bind/db.myhomenetwork
In the description about the config file they write (see example below) a domain name "ns.example.com"
Is it also possible that i write my own name or must a registered Domainname?
I used this dns server in my homenetwork.

@
604800
IN
SOA
ns.example.com. root.example.com. (
2
604800

---

### Post by vasile002 on 2011-11-02
you  need to put there the primary nameserver of your domain so yes it needs to be a valid hostname

---

