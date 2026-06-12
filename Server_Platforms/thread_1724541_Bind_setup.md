---
title: "Bind setup"
date: 2011-04-08
forum: Server Platforms
---

### Post by systemshq on 2011-04-08
I'm trying to get bind9 working and I'm just wondering what's wrong with the following configuration file:-
```
$TTL 3D; Forward zone DNS->IP
@	IN	SOA	example.org.	hostmaster.example.org. (
			2011040801	;
			8H		;
			2H		;
			1W		;
			1D )		;
	IN	NS	dns1.example.org.
www.	IN	A	192.168.1.200
mail.	IN	A	192.168.1.200
	IN	MX	10	mail.example.org.
;
dns1.	IN	A	192.168.1.200
```

If I do a dns lookup, e.g.:-

dig @localhost dns1.example.org

I get:-

```
; <<>> DiG 9.7.1-P2 <<>> @localhost dns1.example.org
; (2 servers found)
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 12568
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;dns1.example.org.		IN	A

;; Query time: 2 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Fri Apr  8 18:17:49 2011
;; MSG SIZE  rcvd: 34

```

and not the ip address 192.168.1.200 as defined in the above file?

Many thanks in advance

---

### Post by falko on 2011-04-08
You use too many dots:

```
www[COLOR="Red"].[/COLOR]	IN	A	192.168.1.200
mail[COLOR="Red"].[/COLOR]	IN	A	192.168.1.200
dns1[COLOR="Red"].[/COLOR]	IN	A	192.168.1.200
```

Either use
```
www	IN	A	192.168.1.200
mail	IN	A	192.168.1.200
dns1	IN	A	192.168.1.200
```
or
```
www.example.org[COLOR="Red"].[/COLOR]	IN	A	192.168.1.200
mail.example.org[COLOR="Red"].[/COLOR]	IN	A	192.168.1.200
dns1.example.org[COLOR="Red"].[/COLOR]	IN	A	192.168.1.200
```

This is also explained in this guide: [http://www.howtoforge.com/traditional_dns_howto](http://www.howtoforge.com/traditional_dns_howto)

---

### Post by systemshq on 2011-04-11
Many thanks that did the trick!

---

