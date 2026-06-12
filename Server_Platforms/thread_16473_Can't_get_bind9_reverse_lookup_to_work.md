---
title: "Can't get bind9 reverse lookup to work"
date: 2005-02-21
forum: Server Platforms
---

### Post by Levander on 2005-02-21
Host name lookup works fine, reverse ip lookup doesn't.  Only three files I've modified from default ubuntu install are listed below.

Trying to get it to work from this reference:

[http://www.linux.com/howtos/DNS-HOWTO-5.shtml](http://www.linux.com/howtos/DNS-HOWTO-5.shtml)

When I run nslookup to do a reverse lookup:
bread:/var/log $ nslookup
> 192.168.254.1
Server:         192.168.254.4
Address:        192.168.254.4#53

** server can't find 1.254.168.192.in-addr.arpa: NXDOMAIN


Any help appreciated.



Follows is /etc/bind/named.conf.local:
```

//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

zone "254.168.192.in-addr.arp" {
	type master;
	file "/etc/bind/highhat.net.rev";
};

zone "highhat.net" {
	type master;
	file "/etc/bind/highhat.net.db";
};

```

Follows is /etc/bind/highhat.net.rev:
```

;
; BIND reverse data file for 192.168.100.0
;
@       IN      SOA     highhat.net. root.highhat.net. (
                              1         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Default TTL
;
        IN      NS      bread.highhat.net.
 
1	IN	PTR	blink.highhat.net.
4	IN	PTR	bread.highhat.net.
254	IN	PTR	router.highhat.net.

```

Follows is /etc/bind/highhat.net.db:
```

;
; BIND data file for yourdomain.com
;
@	IN	SOA	highhat.net. root.highhat.net. (
			      1         ; Serial
			 604800         ; Refresh
			  86400         ; Retry
			2419200         ; Expire
			 604800 )       ; Default TTL
   
	IN	NS	bread.highhat.net.
	IN	MX	10	bread.highhat.net.
     
bread	IN	A	192.168.254.4
blink	IN	A	192.168.254.1
router	IN	A	192.168.254.254

```

---

### Post by Levander on 2005-02-23
Never mind, in named.conf.local, it's supposed to be arpa, not arp.

---

