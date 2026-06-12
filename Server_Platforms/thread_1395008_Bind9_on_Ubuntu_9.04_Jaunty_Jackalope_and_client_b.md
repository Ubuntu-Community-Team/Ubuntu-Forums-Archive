---
title: "Bind9 on Ubuntu 9.04 Jaunty Jackalope and client being denied"
date: 2010-01-31
forum: Server Platforms
---

### Post by shoaibi on 2010-01-31
**_Resolved: Changed configuration to what its at [http://ubuntuforums.org/showthread.php?t=1395050](http://ubuntuforums.org/showthread.php?t=1395050) and works_**

I have setup bind9 on ubuntu 9.04 jaunty and here are the details:

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
        recursion no;
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

/var/log/syslog on server
```

Jan 31 15:19:20 server named[17540]: client 192.168.50.6#50054: query (cache) 'pop.gmail.com.lan/A/IN' denied
Jan 31 15:19:20 server named[17540]: client 192.168.50.6#52852: query (cache) 'download850.avast.com/A/IN' denied
Jan 31 15:19:21 server named[17540]: client 192.168.50.6#38634: query (cache) 'pop.gmail.com/A/IN' denied
Jan 31 15:19:22 server named[17540]: client 192.168.50.6#53249: query (cache) 'download850.avast.com.lan/A/IN' denied
Jan 31 15:19:23 server named[17540]: client 192.168.50.6#50158: query (cache) 'pop.gmail.com/A/IN' denied
Jan 31 15:19:24 server named[17540]: client 192.168.50.6#59028: query (cache) 'pastebin.com/A/IN' denied
Jan 31 15:19:25 server named[17540]: client 192.168.50.6#33061: query (cache) 'pop.gmail.com.lan/A/IN' denied
Jan 31 15:19:25 server named[17540]: client 192.168.50.6#40061: query (cache) 'www.opendns.com/A/IN' denied
Jan 31 15:19:25 server named[17540]: client 192.168.50.6#49904: query (cache) 'pastebin.com/A/IN' denied
Jan 31 15:19:26 server named[17540]: client 192.168.50.6#40748: query (cache) 'pop.gmail.com.lan/A/IN' denied
Jan 31 15:19:26 server named[17540]: client 192.168.50.6#59660: query (cache) 'pastebin.com.lan/A/IN' denied
Jan 31 15:19:28 server named[17540]: client 192.168.50.6#38904: query (cache) 'pastebin.com.lan/A/IN' denied
Jan 31 15:19:29 server named[17540]: client 192.168.50.6#42210: query (cache) 'pastebin.com/A/IN' denied
Jan 31 15:19:29 server named[17540]: client 192.168.50.6#35240: query (cache) 'www.opendns.com/A/IN' denied
Jan 31 15:19:29 server named[17540]: client 192.168.50.6#44690: query (cache) 'pastebin.com/A/IN' denied
Jan 31 15:19:30 server named[17540]: client 192.168.50.6#33826: query (cache) 'pastebin.com.lan/A/IN' denied
Jan 31 15:19:31 server named[17540]: client 192.168.50.6#52377: query (cache) 'pastebin.com.lan/A/IN' denied
Jan 31 15:19:43 server named[17540]: client 192.168.50.6#57971: query (cache) 'twitter.com/A/IN' denied
Jan 31 15:19:43 server named[17540]: client 192.168.50.6#37093: query (cache) 'twitter.com/A/IN' denied
Jan 31 15:19:44 server named[17540]: client 192.168.50.6#46238: query (cache) 'twitter.com.lan/A/IN' denied
Jan 31 15:19:44 server named[17540]: client 192.168.50.6#34111: query (cache) 'twitter.com.lan/A/IN' denied
Jan 31 15:19:46 server named[17540]: client 192.168.50.6#50827: query (cache) 'pop.gmail.com/A/IN' denied
Jan 31 15:19:46 server named[17540]: client 192.168.50.6#52308: query (cache) 'pop.gmail.com/A/IN' denied
Jan 31 15:19:47 server named[17540]: client 192.168.50.6#45317: query (cache) 'mail.google.com/A/IN' denied
Jan 31 15:19:47 server named[17540]: client 192.168.50.6#43735: query (cache) 'pop.gmail.com.lan/A/IN' denied
Jan 31 15:19:47 server named[17540]: client 192.168.50.6#52248: query (cache) 'pop.gmail.com.lan/A/IN' denied
Jan 31 15:19:48 server named[17540]: client 192.168.50.6#48003: query (cache) 'pop.gmail.com/A/IN' denied
Jan 31 15:19:49 server named[17540]: client 192.168.50.6#52280: query (cache) 'pop.gmail.com/A/IN' denied
Jan 31 15:19:49 server named[17540]: client 192.168.50.6#48119: query (cache) 'pop.gmail.com.lan/A/IN' denied
Jan 31 15:19:50 server named[17540]: client 192.168.50.6#40738: query (cache) 'pop.gmail.com.lan/A/IN' denied

```


client digs:
```

[1047][shoaibi@blade:~]$ dig yahoo.com                                                                                                      (31/01/10 20:02:06)

; <<>> DiG 9.6.1-P2 <<>> yahoo.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: REFUSED, id: 24700
;; flags: qr rd; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0
;; WARNING: recursion requested but not available

;; QUESTION SECTION:
;yahoo.com.			IN	A

;; Query time: 689 msec
;; SERVER: 192.168.50.1#53(192.168.50.1)
;; WHEN: Sun Jan 31 20:19:03 2010
;; MSG SIZE  rcvd: 27

[1047][shoaibi@blade:~]$ dig gmail.com                                                                                                      (31/01/10 20:19:03)

; <<>> DiG 9.6.1-P2 <<>> gmail.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: REFUSED, id: 30199
;; flags: qr rd; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0
;; WARNING: recursion requested but not available

;; QUESTION SECTION:
;gmail.com.			IN	A

;; Query time: 795 msec
;; SERVER: 192.168.50.1#53(192.168.50.1)
;; WHEN: Sun Jan 31 20:19:08 2010
;; MSG SIZE  rcvd: 27

```


Client resolv.conf:
```

# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 192.168.50.1
search lan

```

---

### Post by klcom on 2010-02-10
I have the saem problem, can you help me please?

Feb 10 15:10:30 ns1 named[4253]: client 192.9.202.34#55880: query (cache) 'wpad.xxxx.com/A/IN' denied
Feb 10 15:10:56 ns1 named[4253]: client 192.9.202.34#60243: query (cache) 'retail.sp.f-secure.com/A/IN' denied
Feb 10 15:10:56 ns1 named[4253]: client 192.9.202.34#64327: query (cache) 'retail.sp.f-secure.com/AAAA/IN' denied
Feb 10 15:11:04 ns1 named[4253]: client 192.9.202.34#57678: query (cache) 'teredo.ipv6.microsoft.com/A/IN' denied
Feb 10 15:11:38 ns1 named[4253]: client 192.9.202.34#60220: query (cache) 'teredo.ipv6.microsoft.com/A/IN' denied
Feb 10 15:11:56 ns1 named[4253]: client 192.9.202.34#62718: query (cache) 'retail.sp.f-secure.com/A/IN' denied
Feb 10 15:11:56 ns1 named[4253]: client 192.9.202.34#63694: query (cache) 'retail.sp.f-secure.com/AAAA/IN' denied
Feb 10 15:12:21 ns1 named[4253]: client 192.9.202.34#62554: query (cache) 'teredo.ipv6.microsoft.com/A/IN' denied
Feb 10 15:12:56 ns1 named[4253]: client 192.9.202.34#59123: query (cache) 'retail.sp.f-secure.com/A/IN' denied
Feb 10 15:12:56 ns1 named[4253]: client 192.9.202.34#58950: query (cache) 'retail.sp.f-secure.com/AAAA/IN' denied
Feb 10 15:12:58 ns1 named[4253]: client 192.9.202.34#61876: query (cache) 'teredo.ipv6.microsoft.com/A/IN' denied


I have 3 Vlans from the vlan how have the DNS server all work perfect but with the other vlans only resolv the adress of the db.xxxxx.com, put wen i want goo to [www.google.com](www.google.com)

Feb 10 15:01:20 ns1 named[4119]: client 192.9.202.34#50219: query (cache) 'www.google.es/A/IN' denied

Thanks!:guitar:

---

### Post by shoaibi on 2010-02-10
- Do not reply in a "SOLVED" thread. Create a new topic instead, thats what i feel shouldn't be done.
- Google the error and you will find that you are also querying Ipv6, disable that by adding "-4" to /etc/default/bind9 in args to daemon.
There were some other things that i did as well but don't remember much. Google should be your best bet as its very common error.

ALSO
read first post's first line VERY carefully.

---

