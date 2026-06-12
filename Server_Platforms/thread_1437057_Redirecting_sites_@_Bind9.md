---
title: "Redirecting sites @ Bind9"
date: 2010-03-23
forum: Server Platforms
---

### Post by robertoneto123 on 2010-03-23
Hello,

I have a Bind9 as a DNS server and I need to redirect some sites to different IP's (ex: when one access [www.bla.com](www.bla.com) it will access the IP 192.168.0.123).

I believe that I'm missing some steps on the BIND config. Can anyone give me a clue of what is wrong?

For now, I have:

named.conf:
```
include "/etc/bind/named.conf.options";

// prime the server with knowledge of the root servers
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

include "/etc/bind/named.conf.local";
```

My named.conf.local:
```
zone "myserver.mydomain.com" {
    type master;
    file "/etc/bind/zones/mydomain.com.db";
};
```

My mydomain.com.db:

```

$TTL 3D
@ IN SOA ns.myserver.mydomain.com. admin.myserver.mydomain.com. (
   2007062001
      28800
         3600
            604800
               38400
               );
               myserver.mydomain.com.  IN      NS       
               computername  IN      A          200.136.227.200
               www            IN      CNAME      computername
               www.bla.com  IN      CNAME      192.168.0.123

```

---

### Post by jrssystemsnet on 2010-03-23
> zone "**myserver.mydomain.com**" {
    type master;
    file "/etc/bind/zones/mydomain.com.db";
};Zone must be named "bla.com", not "myserver.mydomain.com", for what you are trying to do.

Also, this zone file is AFU:

> $TTL 3D
@ IN SOA ns.myserver.mydomain.com. admin.myserver.mydomain.com. (
   2007062001
      28800
         3600
            604800
               38400
               );
               myserver.mydomain.com.  IN      NS       
               computername  IN      A          200.136.227.200
               www            IN      CNAME      computername
               [www.bla.com](www.bla.com)  IN      CNAME      192.168.0.123 This whole thing is screwed up.  The zone should only be referencing bla.com and subdomains thereof.  Like this:

```
$ORIGIN com.
bla  IN      SOA     www.bla.com. postmaster.www.bla.com. (
                                16               ;
                                300           ;
                                3600            ;
                                3600000         ;
                                300)         ;
                IN      NS      ns1.bla.com.
                IN      A       192.168.0.123

$ORIGIN bla.com.
www             IN      A       192.168.0.123
ns1             IN      A       192.168.0.123

```

Note that the "ns1" should actually point to your bind server, which might or might not be the same box as whatever you're actually trying to redirect the host to.

Also note that you probably really SHOULDN'T be trying to hijack a real public FQDN, and should instead be using "bla.local" or "bla.lan" or some crap like that, if what you're trying to do is set up an intranet-only site.

---

### Post by robertoneto123 on 2010-03-26
Hello,

I did the changes you suggest, and I try

```
nslookup www.bla.com myBindServerIP
```

The result was:

```
;; Got SERVFAIL reply from <bindServerIP>, trying next server
```

When I try to get IP from another site (ex nslookup [www.ubuntu.com](www.ubuntu.com) ...) all works.

My conf files are listed bellow:

```

cat /etc/bind/named.conf.local
zone "bla.com" {
    type master;
    file "/etc/bind/zones/mydomain.com.db";
};

```

```

cat /etc/bind/zones/mydomain.com.db
$ORIGIN com.
orkut	IN	SOA	www.bla.com. postmaster.www.bla.com. (
    16	;
    300	;
    3600	;
    3600000	;
    300)	;
    IN	NS	ns1.bla.com.
    IN	A	IP OF WEB SERVER

$ORIGIN	bla.com.
    www	IN	A	IP OF WEB SERVER
    ns1	IN	A	192.168.0.123

```

Any ideas?

Thanks!

---

### Post by jrssystemsnet on 2010-03-26
Where did "orkut" come from:

```
$ORIGIN com.
orkut	IN	SOA	www.bla.com. postmaster.www.bla.com. (
```


That should be "bla".

---

### Post by robertoneto123 on 2010-03-26
ops, corrected, and the error is still there...

---

### Post by jrssystemsnet on 2010-03-26
Update the serial (the "16" at the top), restart BIND, and try again.

---

### Post by robertoneto123 on 2010-03-26
Sorry for what I believe it's a dummy question but... what do you mean by "update"? Chance the value?

---

### Post by jrssystemsnet on 2010-03-26
Yes, increase the value.

It's a little easier to see what's going on if you comment the values in the top section, like this example from one of my sites:

```
$ORIGIN net.
$TTL 5m

ubuntuwiki	IN	SOA	www.jrssystems.net. postmaster.www.jrssystems.net. (
				4		; serial
	                        4h              ; refresh
        	                15m             ; retry
                	        8h              ; expire
                        	4m)             ; negative caching TTL
       		IN	NS	ns1.jrssystems.net.
		IN	NS	ns2.jrssystems.net.
		MX	10	mail.jrssystems.net.
		IN      A	72.55.156.138

```

---

### Post by robertoneto123 on 2010-03-29
I'm getting an error when Bind starts... 

```
Mar 29 07:24:51 automacao1-desktop named[2281]: /etc/bind/zones/mydomain.com.db:12: unknown RR type 'www'
Mar 29 07:24:51 automacao1-desktop named[2281]: zone orkut.com/IN: loading from master file /etc/bind/zones/mydomain.com.db failed: unknown class/type
Mar 29 07:24:51 automacao1-desktop named[2281]: zone localhost/IN: loaded serial 2
```

My mydomain.com.br is:

```

$ORIGIN com.
bla	IN	SOA	www.bla.com. postmaster.www.bla.com. (
    16	;
    300	;
    3600	;
    3600000	;
    300)	;
    IN	NS	ns1.bla.com.
    IN	A	<target www server IP>

$ORIGIN	bla.com.
    www	IN	A	<target www server IP>
    ns1	IN	A	<my bind9 box IP>

```

---

