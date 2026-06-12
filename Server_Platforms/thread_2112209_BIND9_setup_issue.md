---
title: "BIND9 setup issue"
date: 2013-02-04
forum: Server Platforms
---

### Post by Yizi on 2013-02-04
Having issue configuring BIND, I've registered a domain at namecheap and created NS names e.g. ns1.mydomain.com and ns2.mydomain.com and pointed my domain to it.

I installed BIND on the server and this is my current setting:

**named.conf.local**

```
//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

zone "mydomain.com" {
	type master;
	file "/etc/bind/db.mydomain.com";
};

# This is the zone definition for reverse DNS. replace 0.168.192 with your network address in reverse notation - e.g my network address is 192.168.0
zone "201.168.192.in-addr.arpa" {
    	type master;
     	file "/etc/bind/rev.201.168.192.in-addr.arpa";
};
```

**db.mydomain.com**

```
;
; BIND data file for mydomain.com
;
$TTL	604800
mydomain.com.	IN	SOA	ns1.mydomain.com. admin.mydomain.com. (
	84739	; Serial
	604800	; Refresh
	86400	; Retry
	2419200	; Expire
	604800 ); Negative Cache TTL
;
mydomain.com.			IN	NS	ns1.mydomain.com.
mydomain.com.	86400	IN	NS	ns2.mydomain.com.
localhost		14400	IN	A	127.0.0.1
ns1				14400	IN	A	<external server IP>
ns2				14400	IN	A	<external server IP>
@	IN	A	127.0.0.1
@	IN	AAAA	::1
```

This is the first time I'm configuring the BIND so I would appreciate any help given.

---

### Post by Doug S on 2013-02-04
Others may have different opinions, however it has been many hours now so I will give a reply.
 
I wouldn't recommend that you implement an externally facing DNS. You should let your domain name registrar or ISP handle it. Many of us on these forums do run bind, but only for our own local area network.
 
That being said, if you do want to run an externally facing DNS for your domain name, then you are supposed to have at least two, not just have ns1 and ns2 point to the same static IP address.
 
Your db.mydomain.com syntax looks odd to me and it not the way I would do it, but it seems to pass the named-checkzone program. Your reverse file must be for local use only. I think only your ISP can implement a reverse lookup for your external IP.

---

### Post by hawkmage on 2013-02-04
If you are truly trying to setup an external DNS the @ entries in your db.mydomain.com should not resolve to the IPv4 and IPv6 loopback addresses.  Any name resolution you do on an externally accessible DNS should resolve to an internet routable address.  

Also you wil have to work with your ISP to setup DNS Glue records for your name server entries.  Without DNS Glue entries no one will know to use your DNS.  If your DNS is authoritative for mydomain.com and someone is trying to lookup [www.mydomain.com](www.mydomain.com) the .com TLD DNS needs to not only refer the query to ns1.mydomain.com and ns1.mydomain.com but it needs to be able to give them the IP address as well.  

As for reverse DNS it can be handled a couple of ways depending on how your ISP/Hosting is being done.  If you are allocated a block of IP addresses by your ISP you may be able to get them to allow you to be the authoritative reverse zone for those addresses but unles it is a large address range it is not likely.  So you will probably have to work with your ISP to set up the reverse DNS entries.

---

### Post by SeijiSensei on 2013-02-04
> **Doug S said:**
> I wouldn't recommend that you implement an externally facing DNS. You should let your domain name registrar or ISP handle it. Many of us on these forums do run bind, but only for our own local area network.
 
That being said, if you do want to run an externally facing DNS for your domain name, then you are supposed to have at least two, not just have ns1 and ns2 point to the same static IP address.

I endorse both of Doug's points.  Don't reinvent the wheel; just let your registrar host your DNS records.  And you must have two servers to conform to Internet standards.  That insures that your DNS records are available in the event of an outage.  

I've run public DNS servers for years, but mine sit on two virtual machines out in the cloud that I pay for each month.  Unless you have a static IP address from your provider, and a secondary DNS server, you shouldn't be in the business of hosting your own DNS.

---

### Post by Habitual on 2013-02-05
self-hosted DNS (personally) is NOT something to be taken lightly.

[https://help.ubuntu.com/community/BIND9ServerHowto](https://help.ubuntu.com/community/BIND9ServerHowto)

---

### Post by Yizi on 2013-02-06
Advice taken, I'm using the DNS provided by the domain provider, thank you guys.

---

