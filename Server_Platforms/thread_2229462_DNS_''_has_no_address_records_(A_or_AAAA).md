---
title: "DNS: '' has no address records (A or AAAA)"
date: 2014-06-13
forum: Server Platforms
---

### Post by Seuseukeu on 2014-06-13
Hello.
I'm trying to set a DNS server using bind9 with one master and slaves on Debian (first time trying)
and I'm meeting with an error.

When I try this : "named-checkzone looker.local db.looker.local", it displays : 
"zone looker.local/ IN: loaded serial 2014...
OK"

but when I try this : "named-checkzone looker.local db.looker.local.inv", its displays this error : "zone looker.local/ IN : NS 'master.looker.local' has no address records (A or AAAA)"

Here's the file (db.looker.local.inv) content :

> $TTL 604800
@ IN SOA looker.local. root.looker.local. (
  2014120642
  604800
  86400
  2419200
  604800)

@ IN NS master.looker.local.

130 IN PTR master.looker.local.
131 IN PTR debian7.looker.local.
132 IN PTR debian7b.looker.local.
133 IN PTR debian7c.looker.local.
134 IN PTR debian7d.looker.local.
135 IN PTR master1.looker.local.


Just in case, the content of db.looker.local :
> 
$TTL 604800
@ IN SOA looker.local. root.looker.local. (
  2014120642
  604800
  86400
  2419200
  604800)

@ IN NS master.looker.local.
master IN A 192.168.171.130
debian7 IN A 192.168.171.131
debian7b IN A 192.168.171.132
debian7c IN A 192.168.171.133
debian7d IN A 192.168.171.134
master1 IN A 192.168.171.135


The server I'm trying this is master (root@master).
I can't see what's the problem and how to solve it.
Thanks for your help.

---

### Post by Doug S on 2014-06-13
Hi and welcome to Ubuntu forums. 

Using named-checkzone to verify a reverse lookup file is different. It would be something like:```
named-checkzone 171.168.192.in-addr.arpa db.looker.local.inv
```[see also]("https://help.ubuntu.com/14.04/serverguide/dns-troubleshooting.html")

---

