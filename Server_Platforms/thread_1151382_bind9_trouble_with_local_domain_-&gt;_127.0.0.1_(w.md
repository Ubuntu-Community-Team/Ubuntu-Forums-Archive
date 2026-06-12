---
title: "bind9: trouble with local domain -&gt; 127.0.0.1 (wildcard subdomain)"
date: 2009-05-06
forum: Server Platforms
---

### Post by skiquel on 2009-05-06
Ubuntu server 9.04. Trouble with local domain -> 127.0.0.1 (wildcard subdomain)

I want to get ldnm.lan to forward to 127.0.0.1

/etc/hosts won't cut it because I need all subdomains to fall through.

I have my /etc/bind/named.conf:

```
zone "ldnm.lan" { type master; file "/etc/bind/ldnm.lan.db"; };
```

What I have set in /etc/bind/ldnm.lan.db:
```
;
; BIND data file for local loopback interface
;
$TTL 14400
@ IN  SOA localhost. root.localhost. (
      2009050651   ; Serial
       86400   ; Refresh
        7200   ; Retry
      3600000   ; Expire
       86400 ) ; Negative Cache TTL
;
@ IN  NS  localhost.
@ IN  A 127.0.0.1
* IN  A 127.0.0.1
@ IN  AAAA  ::1
```


It's not working... However.

```
$ ping www.ldnm.lan
ping: unknown host www.ldnm.lan
```


```
$ named-checkzone ldnm.lan ldnm.lan.db
zone ldnm.lan/IN: loaded serial 2009050651
OK
```

Here is what works on OS X:

```
$TTL 24h

@ IN SOA localhost. root.localhost. (
2009050400 86400 300 604800 3600 )

@ IN NS localhost.
@ IN A 127.0.0.1
* IN A 127.0.0.1
```h

---

### Post by skiquel on 2009-05-07
Bump. If you have bind9 experience this may be something you're familiar with.

Edit: The bind data was actually OK (If you run into this, remember to make your serial higher). I had to edit /etc/resolv.conf to my local IP. It clicked.

---

