---
title: "Problem with zones in DHCP server"
date: 2012-11-11
forum: Ubuntu Studio
---

### Post by normis on 2012-11-11
Hi... I'm traying to configure an DHCP server. i have this code in named.config.local : 

zone "." {
	type hint;
	file "/etc/bind/db.root";
};

// be authoritative for the localhost forward and reverse zones, and for
// broadcast zones as per RFC 1912

zone "localhost" {
	type master;
	file "/etc/bind/db.local";
};

zone "127.in-addr.arpa" {
	type master;
	file "/etc/bind/db.127";
};

zone "0.in-addr.arpa" {
	type master;
	file "/etc/bind/db.0";
};

zone "255.in-addr.arpa" {
	type master;
	file "/etc/bind/db.255";
};


In the reverse:

$TTL 86400 	;	1 dia
0.50.10.in-addr.arpa.	IN	SOA	servidor 	postmaster(
		1  ; serie
		12h; refresh(12 hour)
		1h ; retry (1 hour)
		2w ; expire(2 week)
		1w ; minimum(1 week)
);
0.50.10.in-addr.arpa.	IN	NS	servidor
1			IN	PTR	servidor


but when i use named-checkzone 0.10.50.in-ddr.arpa /var/cache/bind/db.10.50.0 says:

zone has 0 soa Redords
zone has no ns records

how can i solve it?

---

