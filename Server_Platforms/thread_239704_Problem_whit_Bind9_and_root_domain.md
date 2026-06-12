---
title: "Problem whit Bind9 and root domain"
date: 2006-08-19
forum: Server Platforms
---

### Post by insulae on 2006-08-19
(first sorry for my english, my primary language is spanish)

i have a ubuntu dapper server **for a intranet only**.
i need to create a "root domain(?)" only like: [http://virtual](http://virtual) , i dont want [http://virtual.com](http://virtual.com) or [http://virtual.localdomain](http://virtual.localdomain) , i need only [http://virtual](http://virtual) 

so i create the next configuration:

in file /etc/bind/named.conf 

```
zone "virtual" {
        type master;
        file "/etc/bind/db.virtual";
};

```

in file /etc/bind/db.virtual

```
$TTL    604800
@       IN      SOA     virtual. virtual. (
                              1         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@               IN      NS      localhost.

virtual.        IN      A       1.1.1.253
www             IN      A       1.1.1.253

```

or 

```
$TTL    604800
@       IN      SOA     ns.localhost. root.localhost. (
                              1         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@               IN      NS      ns
virtual.        IN      A       1.1.1.253
```


when i run from linux client:

nslookup virtual

```

Server: 1.1.1.253
Address:  1.1.1.253#53

Name:  virtual
Address:  1.1.1.253[/B]

```

when i run from linux client:

ping virtual

```

PING virtual (1.1.1.253) 56(84) bytes of data.
64 bytes from 1.1.1.253: icmp_seq=1 ttl=64 time=0.213 ms
64 bytes from 1.1.1.253: icmp_seq=2 ttl=64 time=0.315 ms

```

when i try to see the web page in firefox or konqueror with [http://virtual](http://virtual) is everything ok!! i see the web perfectly

**so what is my problem?**

when i try to see the web page from a windows client, with iexplorer or firefox i can't see anything.

if i run from windows client:

nslookup virtual 

```

Server: 1.1.1.253
Address:  1.1.1.253#53

Name:  virtual
Address:  1.1.1.253[/B]

```

the nslookup is ok, but if i try to do a ping to virtual i dont receive any response, but if a execute a ping to [www.virtual](www.virtual) or virtual. i have response!!, and now if i try to go via iexplorer to [http://virtual](http://virtual) i can see the page.

i don't know what to do, i read many pages in google but i dont have any response.

---

### Post by insulae on 2006-08-19
SORRY I MYSTAKE THE FORUM and i don't know how move to another forum =).

---

