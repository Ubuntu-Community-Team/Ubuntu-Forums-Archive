---
title: "Bind9 Configuration"
date: 2016-05-24
forum: Server Platforms
---

### Post by hiostreas on 2016-05-24
Hello, I installed bind9 in my ubuntu server computer

mydomain is in the IP 192.168.1.10

in Ubuntu when  do $ ping mydomain and $ ping [www.mydomain]("http://www.mydomain")
it works

but in only works when I type $ ping [www.mydomain]("http://www.mydomain") it works but when I type $ ping mydomain it doesn't

 and I did the following:

In the [COLOR=#333333][FONT=monospace]/etc/bind/named.conf.local 

I wrote:
[/FONT][/COLOR]```
[I]zone "mydomain"{
        type master;
        file "/etc/bind/db.mydomain";
};[/I]

```
I created a file db.mydomain and i Typed the following:

```
[I]$TTL    604800
@       IN      SOA     ns.mydomain. root.mydomain. (
                              2         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns.mydomain.


ns      IN      A       192.168.1.10


@       IN      A       192.168.1.10
www     IN      A       192.168.1.10[/I]
```

for the reverse file, I must use another domain

Thanks




[COLOR=#333333][FONT=monospace]
[/FONT][/COLOR]

---

### Post by QDR06VV9 on 2016-05-24
Moved to Server Platforms.

---

### Post by darkod on 2016-05-24
This line should be:
```
@       IN      SOA mydomain. root.mydomain. (
```

You need to put only the domain, not the nameserver like you did.

Also, you need to use 192.168.1.10 as DNS server on any client when testing... Otherwise it won't work because instead of querying your dns server it will be querying another one that doesn't contain info about your zone.

---

