---
title: "Zimbra 3322.org dynamic IP DNS woes."
date: 2009-06-08
forum: Server Platforms
---

### Post by ronin_baka on 2009-06-08
I'm having a bit of trouble getting Zimbra up and running on my computer at home. Unforgivably I am in China and the only dynamicIP address system I can use is 3322.org.

I really hope someone can spot the numerous mistakes I'm making.

/etc/hosts:
```
127.0.0.1	localhost.localdomain		localhost
homeserver.9966.org	mail.homeserver.9966.org 	mail

```

/etc/hostname
```
homeserver.9966.org
```

/etc/bind/named.conf.local
```
zone "homeserver.9966.org" {
	type master;
	file "/etc/bind/db.homeserver.9966.org";
};
```

/etc/bind/named.conf.options 
	```
forwarders {
	 	61.177.95.106; 60.191.83.242;
	};
	auth-nxdomain no;
```

/etc/bind/db.homeserver.9966.org
```
;
; Bind data file for homeserver.9966.org
;
$TTL	604800
@	IN	SOA	mail.homeserver.9966.org. admin.homeserver.9966.org. (
			 070725		; Serial
			 604800		; Refresh
			  86400		; Retry
			2419200		; Expire
			 604800	)	; Negitive Cache TTL
;
@	IN	NS	mail
	IN	MX	10 mail
	IN 	A	192.168.1.198
	IN	A	192.168.1.198
```

/etc/resolver.conf
```
nameserver 192.168.1.1
```

Output from some commands
host homeserver.9966.org
```
homeserver.9966.org has address 220.163.34.223
```

host mail.homeserver.9966.org
```
mail.homeserver.9966.org has address 220.165.8.174
Host mail.homeserver.9966.org not found: 3(NXDOMAIN)
Host mail.homeserver.9966.org not found: 3(NXDOMAIN)
```


nslookup homeserver.9966.org
```
Server:		192.168.1.1
Address:	192.168.1.1#53

Non-authoritative answer:
Name:	homeserver.9966.org
Address: 220.163.34.223

```

nslookup mail.homeserver.9966.org
```
Server:		192.168.1.1
Address:	192.168.1.1#53

Non-authoritative answer:
Name:	mail.homeserver.9966.org
Address: 220.165.8.174
```
I have no idea where that IP comes from

dig homeserver.9966.org

```
; <<>> DiG 9.5.0-P2 <<>> homeserver.9966.org
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 59586
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 2, ADDITIONAL: 2

;; QUESTION SECTION:
;homeserver.9966.org.		IN	A

;; ANSWER SECTION:
homeserver.9966.org.	60	IN	A	220.163.34.223

;; AUTHORITY SECTION:
9966.org.		1442	IN	NS	ns1.3322.net.
9966.org.		1442	IN	NS	ns2.3322.net.

;; ADDITIONAL SECTION:
ns1.3322.net.		1505	IN	A	61.177.95.106
ns2.3322.net.		1428	IN	A	60.191.83.242

;; Query time: 70 msec
;; SERVER: 192.168.1.1#53(192.168.1.1)
;; WHEN: Mon Jun  8 15:41:43 2009
;; MSG SIZE  rcvd: 129
```


 dig mail.homeserver.9966.org mx

```
; <<>> DiG 9.5.0-P2 <<>> mail.homeserver.9966.org mx
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 63689
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;mail.homeserver.9966.org.	IN	MX

;; AUTHORITY SECTION:
9966.org.		429	IN	SOA	ns1.3322.net. ppyy.bentium.com. 4587289 600 300 604800 600

;; Query time: 12 msec
;; SERVER: 192.168.1.1#53(192.168.1.1)
;; WHEN: Mon Jun  8 15:47:45 2009
;; MSG SIZE  rcvd: 106

```

---

### Post by cdenley on 2009-06-08
> **ronin_baka said:**
> 
/etc/hosts:
```
127.0.0.1	localhost.localdomain		localhost
**[COLOR="Red"]homeserver.9966.org[/COLOR]**	mail.homeserver.9966.org 	mail

```


This is the first thing that stands out to me. The format is supposed to be
```

[IP address]    [FQDN]       [name]
xxx.xxx.xxx.xxx mydomain.com mydomain

```
```

man hosts

```

---

### Post by ronin_baka on 2009-06-08
Yeah I'm gusing that is part of the problem. 
I think i should change it to 192.168.1.198 mail.homeserver.9966.org using the local ip.
Is that right? most other examples apear to have the external IP there though thats why I tried to use the DynDNS service url.

---

