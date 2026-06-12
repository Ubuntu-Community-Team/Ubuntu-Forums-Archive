---
title: "[BIND9] help please!"
date: 2009-01-25
forum: Server Platforms
---

### Post by robgr85 on 2009-01-25
I've read some manuals available in the network, tried few times... and bind ain't working for me :-|

What I want to do, is to set simple DNS server for my local network. I've got hard time with it... could You help me?

That I've done:

1. install the bind9
sudo apt-get update
sudo apt-get install bind9

2. edit on 
/etc/bind/named.conf.local
3. added file
/etc/bind/my.zone
4. added reversed zone file
/etc/bind/zone.my

It just does not want to work :/

when tried to check zone-files by
```

named-checkzone my.zone zone.my

```
I got the following output
```

zone.my:2: ignoring out-of-zone data (1.168.192.in-addr.arpa)
zone my.zone/IN: has 0 SOA records
zone my.zone/IN: has no NS records

```
after trying
```

named-checkzone . my.zone

```
i got:
```

my.zone:2: SOA record not at top of zone (my.zone)
zone ./IN: loading from master file my.zone failed: not at top of zone

```


what can be the cause of that problem? Any solutions?

---

### Post by robgr85 on 2009-01-26
noone knows how to help?

here are mine named.conf.local:
```

zone "my.zone" IN{
	type master;
	file  "my.zone";
};

zone "1.168.192.IN-ADDR.ARPA" IN {
    type master;
    file "zone.my";
};


```

zone.my:
```

$TTL	86400
1.168.192.in-addr.arpa.	IN	SOA	ns.my.zone.	robgr85.my.zone. (
	2009012501; serial
	12h; refresh
	1h; retry
	1w; expire
	1h; default_ttl
	)
10	IN	NS	ns1.my.zone.
11	IN	PTR	jerzy.my.zone.
20	IN	PTR	artur.my.zone.
10	IN	PTR	robert.my.zone.   

```
my.zone:
```

$TTL 86400
my.zone.	IN	SOA	ns.my.zone.	robgr85.my.zone. (
2009012501
12h
1h
1w
1h
)
my.zone. IN NS ns.my.zone.
jerzy.my.zone. IN A 192.168.1.11
artur.my.zone. IN A 192.168.1.20
robert.my.zone. IN A 192.168.1.10
ns.my.zone.	IN A 192.168.1.10
www IN A 192.168.1.10

```


hope, that You will be able to find some errors now...

---

### Post by netztier on 2009-01-26
> **robgr85 said:**
> n
```

zone "my.zone" **[COLOR="Red"]IN[/COLOR]**{
	type master;
	file  "my.zone";
};

zone "1.168.192.IN-ADDR.ARPA" **[COLOR="Red"]IN [/COLOR]**{
    type master;
    file "zone.my";
};


```


I don't think that "IN" belongs right there. That should just be a space after the " and the opening bracket.

regards

Marc

---

### Post by robgr85 on 2009-01-26
> **netztier said:**
> I don't think that "IN" belongs right there. That should just be a space after the " and the opening bracket.

regards

Marc

thanks for suggestion, but removing "IN" from there didn't helped :(

What can it be?

edit:

I've copied my named.conf.local and zone files to /var/cache/bind/ directory, and it finaly started to work :)

---

### Post by netztier on 2009-01-27
> **robgr85 said:**
> 
I've copied my named.conf.local and zone files to /var/cache/bind/ directory, and it finaly started to work :)

That strikes me as odd.

IMHO, these files do not belong there. named.conf should be somewhere in /etc/bind/ or /etc.

zonefiles can be anywhere you like them, be that /etc/named/... or /etc/bind/... or /var/named/..., just as long as you indicate their exact location in named.conf.

... which probably was the mistake in the first place; in named.conf.local, you might've tried to specifiy the zone file's location with an absolute path.

I suggest leaving the files in their original locations. Should you ever consider installing Webmin or e-Box as a web based admin GUI for your server, their ubuntu-packaged versions will expect the files in their default locations - you'll have quite a bit of work to do to make them work.

regards

Marc

---

