---
title: "Setting up some DNS and MX records"
date: 2008-10-13
forum: Server Platforms
---

### Post by Vegan on 2008-10-13
OK I installed BIND9 on my server, so now I would like to install A records and MX records so that postfix will have DNS services available.

I have 5 URLs I want to add to the DNS.

I created my db files:

;
; BIND data file for local loopback interface
;
$TTL	604800
@	IN	SOA	contract-developer.dyndns.biz. root.localhost. (
			      2		; Serial
			 604800		; Refresh
			  86400		; Retry
			2419200		; Expire
			 604800 )	; Negative Cache TTL
;
@	IN	NS	localhost.
@	IN	A	192.168.7.250
@	IN	AAAA	::1


This is my resolv.conf

search gv.shawcable.net
nameserver 4.2.2.2
nameserver 64.59.160.13
nameserver 64.59.160.15
nameserver 64.125.134.133
nameserver 64.125.134.132
nameserver 204.11.126.131
nameserver 208.185.179.218



When I use dig -x ......
I get a parse error.

---

### Post by Vegan on 2008-10-14
Nobody know to fix the problems?

---

