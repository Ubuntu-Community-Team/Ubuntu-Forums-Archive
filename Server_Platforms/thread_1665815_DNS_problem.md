---
title: "DNS problem"
date: 2011-01-12
forum: Server Platforms
---

### Post by Mosabama on 2011-01-12
Hello every one.

I installed bind and configured it and its working fine. but the weird thing is that if the server doesn't have an answer for a client query it will get the answer from some where from the internet!!!

I removed the "." root zone and everything else, I only made one zone.
I want the server to give no answer if it doesn't have it.

please take a look at the conf files and the zone file:

named.conf file:
```

// This is the primary configuration file for the BIND DNS server named.
//
// Please read /usr/share/doc/bind9/README.Debian.gz for information on the 
// structure of BIND configuration files in Debian, *BEFORE* you customize 
// this configuration file.
//
// If you are just adding zones, please do that in /etc/bind/named.conf.local

include "/etc/bind/named.conf.options";
include "/etc/bind/named.conf.local";
include "/etc/bind/named.conf.default-zones";


```


named.conf.options file:
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

	// forwarders {
	// 	0.0.0.0;
	// };

	auth-nxdomain no;    # conform to RFC1035
	listen-on-v6 { any; };
};

```

named.conf. local file:
```
//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

zone "linux.local" {
	type master;
	file "/var/lib/bind/linux.local.hosts";
	};

```

linux.local. hosts zone file:
```
$ttl 38400
linux.local.	IN	SOA	ns1.linux.local. myemail.gmail.com. (
			1293568964
			10800
			3600
			604800
			38400 )
linux.local.	IN	NS	ns1.linux.local.
linux.local.	IN	A	192.168.1.2
www.linux.local.	IN	CNAME	linux.local.
ns1.linux.local.	IN	A	192.168.1.2
mosab-lap		IN	A	192.168.1.2
neda-pc			IN	A	192.168.1.3

```

Thank you for your time...

---

### Post by bsntech on 2011-01-12
First of all, to set it so that the DNS server does not do any external queries, you need to disable recursion.  Do this in the named.conf.options file:

allow-recursion { none; }

Second - in your named.conf.local file, you are saying that your file is "linux.local.hosts".  Ensure the name of the file in the and the path is fully correct and that the file is in the /var/lib/bind/linux.local.hosts.

Third - in your file that has the DNS contents, you list 'www.linux.local' and 'ns1.linux.local'.  Change these to only 'www' and 'ns1' instead of listing the full domain name.

Brian S.

---

### Post by bsntech on 2011-01-12
As an additional note - this may not be correct - but I have my DNS entries setup in this fashion below.

Your line says:

> linux.local.	IN	NS	ns1.linux.local.
linux.local.	IN	A	192.168.1.2


Change that to:

> @	IN	NS	ns1.linux.local.
@	IN	A	192.168.1.2


---

### Post by Mosabama on 2011-01-13
> **bsntech said:**
> 
allow-recursion { none; };

.

Thanks for your reply..
adding this statement actually worked thanks..

but what I would like to know is : where it used to redirect the requests? to what DNS server ? you saw all the conf files!!

---

### Post by chrislynch8 on 2011-01-13
What entries have you got in the /etc/resolv.conf file, when using a your own local DNS server, you should have something like

```

search your.domain
nameserver 127.0.0.1

```

You may have the DNS IP of your ISP in here, by default when configuring the server if it is connected directly to the Internet.

---

### Post by Mosabama on 2011-01-13
> **chrislynch8 said:**
> What entries have you got in the /etc/resolv.conf file, when using a your own local DNS server, you should have something like

```

search your.domain
nameserver 127.0.0.1

```

You may have the DNS IP of your ISP in here, by default when configuring the server if it is connected directly to the Internet.
```

search linux.local
nameserver 192.168.1.2

```

This is mylan ip for the DNS.. I am sure its the same DNS.

---

### Post by bsntech on 2011-01-13
When your DNS server does recursive queries, it typically will start at the root DNS servers.  The root DNS servers will then provide the next level up - then that server provides the next level up.  It is a hierarchical system and so when doing recursive queries, servers always start at the very root of the DNS servers - unless you have specifically put in a zone - such as your linux.local above.

Then your server is authoritative for that 'zone' and doesn't have to go anywhere - hence no recursion is needed.

Brian S.
[BsnTech Networks]("http://www.bsntech.com")

---

### Post by Mosabama on 2011-01-13
Yes, but what I understand that the DNS server will get the IPs of the ROOT SERVERS from the root zone ".". Which I removed ... and Even deleted the root.db file in bind directory. I believe bind needs the root.db file to contact the root servers!

---

