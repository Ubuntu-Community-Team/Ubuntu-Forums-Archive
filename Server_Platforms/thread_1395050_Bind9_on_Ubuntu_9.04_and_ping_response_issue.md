---
title: "Bind9 on Ubuntu 9.04 and ping response issue"
date: 2010-01-31
forum: Server Platforms
---

### Post by shoaibi on 2010-01-31
[SIZE="5"]**Configurations**[/SIZE]

named.conf.local
```

//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

zone "example.com" {
             type master;
             file "/etc/bind/db.example.com";
        };

zone "50.168.192.in-addr.arpa" {
		type master;
 		notify no;
	        file "/etc/bind/db.192";

	};


```

named.conf.acl  (manually included at the end of named.conf)
```

acl "trusted" {
    192.168.50.0/24;
    localhost;
    localnets;
};

```

named.conf.options
```

 
options {
	directory "/var/cache/bind";

	// If there is a firewall between you and nameservers you want
	// to talk to, you may need to fix the firewall to allow multiple
	// ports to talk.  See http://www.kb.cert.org/vuls/id/800113

	// If your ISP provided one or more IP addresses for stable 
	// nameservers, you probably want to use them as forwarders.  
	// Uncomment the following block, and insert the addresses replacing 
	// the all-0's placeholder.

	forwarders {
	 	208.67.220.220;
		208.67.222.222;
	 };

	auth-nxdomain no;    # conform to RFC1035
	listen-on-v6 { none; };
	listen-on { 192.168.50.1; };
	dump-file               "data/cache_dump.db";
        statistics-file         "data/named_stats.txt";
        memstatistics-file      "data/named_mem_stats.txt";
        allow-query { trusted; };
        allow-recursion { trusted; };
        allow-query-cache { trusted; };
        version "go away";

};


```

db.example.com
```

;
; BIND data file for example.com
;
$TTL	604800
@	IN	SOA	example.com. sysadmin.example.com. (
	   	   310120101400 	; Serial
			 604800		; Refresh
			  86400		; Retry
			2419200		; Expire
			 604800 )	; Negative Cache TTL
;
@	IN	NS	example.com.
;@	IN	A	192.168.50.1
@	IN	A	72.13.95.107
@	IN	AAAA	::1

; Public records
;www	IN	A	72.13.95.107
;



; Private records
phpmyadmin	IN	A	192.168.50.1
nagios		IN	A	192.168.50.1
redmine		IN	A	192.168.50.1
status		IN	A	192.168.50.1

pma		IN	CNAME	phpmyadmin
cacti		IN	CNAME	nagios
projects	IN	CNAME	redmine
git		IN	CNAME	redmine
vpn		IN	CNAME	status
vps		IN	CNAME	status

```



db.192
```

;
; BIND reverse data file for example.com
;
$TTL	604800
@	IN	SOA	example.com. sysadmin.example.com. (
	    	   300120101400 	; Serial
			 604800		; Refresh
			  86400		; Retry
			2419200		; Expire
			 604800 )	; Negative Cache TTL
;
@	IN	NS	example.com.
;1	IN	PTR	example.com.
1	IN	PTR	phpmyadmin
1	IN	PTR	nagios
1	IN	PTR	redmine
1	IN	PTR	status

```

[SIZE="5"]**Problem**[/SIZE]


If i ping, it keeps rotating between all hosts instead of just response from that subdomain, why?
```

PING phpmyadmin.example.com (192.168.50.1) 56(84) bytes of data.
64 bytes from phpmyadmin.50.168.192.in-addr.arpa (192.168.50.1): icmp_seq=1 ttl=64 time=362 ms
64 bytes from redmine.50.168.192.in-addr.arpa (192.168.50.1): icmp_seq=2 ttl=64 time=365 ms
64 bytes from status.50.168.192.in-addr.arpa (192.168.50.1): icmp_seq=3 ttl=64 time=368 ms
64 bytes from nagios.50.168.192.in-addr.arpa (192.168.50.1): icmp_seq=4 ttl=64 time=364 ms
64 bytes from phpmyadmin.50.168.192.in-addr.arpa (192.168.50.1): icmp_seq=5 ttl=64 time=371 ms
64 bytes from redmine.50.168.192.in-addr.arpa (192.168.50.1): icmp_seq=6 ttl=64 time=367 ms
64 bytes from status.50.168.192.in-addr.arpa (192.168.50.1): icmp_seq=7 ttl=64 time=368 ms
^C64 bytes from nagios.50.168.192.in-addr.arpa (192.168.50.1): icmp_seq=8 ttl=64 time=363 ms

--- phpmyadmin.example.com ping statistics ---
8 packets transmitted, 8 received, 0% packet loss, time 7007ms
rtt min/avg/max/mdev = 362.089/366.251/371.054/2.959 ms

```

Further more i can't browse to some urls like [https://pip.verisignlabs.com/login.do](https://pip.verisignlabs.com/login.do) but i can browse it if i remove the pip part.

---

