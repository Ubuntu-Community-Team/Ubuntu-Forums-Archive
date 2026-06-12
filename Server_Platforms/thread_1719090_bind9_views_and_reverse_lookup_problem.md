---
title: "bind9 views and reverse lookup problem"
date: 2011-04-01
forum: Server Platforms
---

### Post by wconstantine on 2011-04-01
I'm at a loss to why my reverse lookup zone doesn't work for me. Could anybody see what I've done wrong?

I've got two views. One internal and one external. My domain is isp2.datornatverk.se. Public IP: 130.240.133.81. 

dig -x @8.8.8.8 130.240.133.81

gives me:

;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 2917
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

I've set it up so that the internal subnets gets the domains resolved to the internal IP-addresses. When querying from external addresses I will get public IP. 

My named.conf.local file:

```
acl internals {
	127.0.0.0/8;
	10.0.0.0/8;
	192.168.0.0/16;
	172.16.0.0/12;
};

view "internal" {
        match-clients { internals; };
        recursion yes;

	allow-recursion { internals; };

        zone "isp2.datornatverk.se" {
                allow-transfer  { none; };
                type master;
                file "/etc/bind/db.internal.isp2.datornatverk.se";
        };
};

view "external" {
	match-clients { any; };
	recursion no;

	zone "isp2.datornatverk.se" {
		allow-transfer  { none; };
		type master;
	        file "/etc/bind/db.isp2.datornatverk.se";
	};

	zone "133.240.130.in-addr.arpa" {
		type master;
		notify no;
		file "/etc/bind/db.130";
	};
};

```

db.130 file:

```

;
; BIND reverse data file for local loopback interface
;
$TTL	604800
@	IN	SOA	ns1.isp2.datornatverk.se. root.isp2.datornatverk.se. (
			      2		; Serial
			 604800		; Refresh
			  86400		; Retry
			2419200		; Expire
			 604800 )	; Negative Cache TTL
;
	IN	NS	ns1.isp2.datornatverk.se.
81	IN	PTR	ns1.isp2.datornatverk.se.
81	IN	PTR	mail.isp2.datornatverk.se.

```

I don't know whether the views has messed something up. It worked before I added the views.

---

### Post by hawkmage on 2011-04-05
I am not sure why it is not working for you.  In my bind config I have 3 views:
```
view "internal" {
    match-clients { internal_nets; };
    recursion yes;
    include "/etc/bind/named.conf.local";
};
view "external" {
    match-clients { !internal_nets; };
    recursion yes;
    include "/etc/bind/named.conf.external";
};
view "default" {
    match-clients { any; };
    recursion yes;
    include "/etc/bind/named.conf.default";
};
```

---

### Post by wconstantine on 2011-04-06
The problem was the dig command.

I did dig -x @8.8.8.8 <ip>, but it should have been dig -x <ip>. It's working now. Altough someone other than me seems to have control over the reverse DNS PTR. I have to talk to someone about it.

---

### Post by SeijiSensei on 2011-04-06
> **wconstantine said:**
> Altough someone other than me seems to have control over the reverse DNS PTR. I have to talk to someone about it.

Your ISP has control of the in-addr.arpa domain for its block of addresses.  There's a technique called "[delegation]("http://www.ietf.org/rfc/rfc2317.txt")" that ISPs can use to let their subscribers manage their own portions of the address space, but they'll usually only do that if you manage an IP subnet on a business-class IP connection.

If you have a static IP, your ISP may be willing to create a custom PTR record for you.

---

