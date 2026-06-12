---
title: "Attempting to SSH to Server Opens Session to localhost Instead"
date: 2011-03-12
forum: Server Platforms
---

### Post by RAdams on 2011-03-12
This is a rather interesting problem, almost certainly caused by my butchering my DNS setup.

I have a DynDNS name pointing to my dynamic IP at home. Let's call that **myname.dyndns.org**. On a public-facing web server outside my network, I have a domain name. Let's call that **mysite.com**. The web server running mysite.com also hosts the DNS zone for mysite.com. I have a CNAME in there resolving myname.dyndns.org to **myhouse.mysite.com**. Why? Because I want to. It works.

So, at home I have a server. Let's call that **myserver**. myserver is also a DNS server. It uses views, with the goal of essentially overriding myhouse.mysite.com. From the outside, of course, this would resolve to my public (dynamic) IP address, via:
**myhouse.mysite.com (CNAME on mysite.com server) --> myname.dyndns.org (DynDNS service) --> My public IP.**

From the inside, I want:
**myhouse.mysite.com (A record on myserver) --> Local IP of myserver**

So, I setup my named.conf to not include named.conf.default-zones. Then I setup my named.conf.local like so:
```
acl "lan_hosts" {
	10.254.7.0/24;	//My local subnet
	127.0.0.1;
};

view "inside" {
	match-clients { lan_hosts; };
	recursion yes;
	notify no;

	include "/etc/bind/named.conf.default-zones";
	include "/etc/bind/zones.rfc1918-modified";	//just a copy of the normal zones.rfc1918 with my private subnet (10.in-addr.arpa) commented out.

	zone "7.254.10.in-addr.arpa" {
		type master;
		notify no;
		file "etc/bind/db.10";
	};

	zone "myhouse.mysite.com" {
		type master;
		file "/etc/bind/inside/db.myhouse.mysite.com";
	};
};

view "outside" {
	match-clients { !localnets; any; };
	recursion no;
};
```

And here's my zone file for myhouse.mysite.com:
```
$TTL	86400
@       IN      SOA     ns.myhouse.mysite.com myemail.mysite.com. (
                        2011031808      ; Serial
                        86400           ; Refresh
                        7200            ; Retry
                        1209600         ; Expire
                        86400 )         ; Negative Cache TTL
;
@	IN	NS	ns.myhouse.mysite.com.
@       IN      A       10.254.7.5
@       IN      AAAA    ::1
ns	IN	A	10.254.7.5
www     IN      CNAME   myhouse.mysite.com.
```

And my reverse lookup zone:
```
$TTL	604800
@	IN	SOA	ns.myhouse.mysite.com. myemail.mysite.com. (
			2011031803	; Serial
			604800		; Refresh
			86400		; Retry
			2419200		; Expire
			604800 )	; Negative Cache TTL
;

@	IN	NS	ns.
5	IN	PTR	ns.myhouse.mysite.com.

```

So here's the problem: if I ping 10.254.7.5 from the inside, it responds, and the ping times are fine, but there's a very long delay between responses (5-15 seconds). If I ssh to myhouse.mysite.com from inside, it instead opens a session to whatever I machine I am on! It's like myhouse.mysite.com is being routed to locahost, but I don't see why.

My only hunch so far is that I've flummoxed the reverse zone file, because:
```
me@mylaptop:~$ nslookup
> set type=ptr
> 5.7.254.10.in-addr.arpa
Server:		10.254.7.5
Address:	10.254.7.5#53

** server can't find 5.7.254.10.in-addr.arpa: NXDOMAIN
```

However:
```
; <<>> DiG 9.7.3 <<>> myhouse.mysite.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 29230
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 1

;; QUESTION SECTION:
;myhouse.mysite.com.		IN	A

;; ANSWER SECTION:
myhouse.mysite.com.	86400	IN	A	10.254.7.5

;; AUTHORITY SECTION:
myhouse.mysite.com.	86400	IN	NS	ns.myhouse.mysite.com.

;; ADDITIONAL SECTION:
ns.myhouse.mysite.com.	86400	IN	A	10.254.7.5

;; Query time: 0 msec
;; SERVER: 10.254.7.5#53(10.254.7.5)
;; WHEN: Sat Mar 12 06:49:47 2011
;; MSG SIZE  rcvd: 83

```

Any ideas? Let me know if there's any other information I can provide.

---

### Post by RAdams on 2011-03-12
I corrected two errors, one in named.conf.local (the file for the rdns was improperly set to "etc/bind/db.10" instead of "/etc/bind/db.10" and I corrected the missing . at the end of "ns.myhouse.mysite.com" in the reverse zone file. nslookup now appears correct ("5.7.254.10.in-addr.arpa	name = myhouse.mysite.com."), but ssh myhouse.mysite.com still dumps me in localhost... I'm at an utter loss here. :confused:

---

### Post by RAdams on 2011-03-12
So, I'm a dolt and forgot to remove that AAAA record pointing to ::1 in the forward zone file.

Oops.

It works now that I'm not instructing IPv4 it's at 10.254.7.5 and IPv6 it's at localhost... :rolleyes:

---

