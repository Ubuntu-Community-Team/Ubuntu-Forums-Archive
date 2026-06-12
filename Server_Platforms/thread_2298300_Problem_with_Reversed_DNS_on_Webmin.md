---
title: "Problem with Reversed DNS on Webmin"
date: 2015-10-09
forum: Server Platforms
---

### Post by hunterlove22 on 2015-10-09
Hello,

I created Reversed DNS for my domains.

The main domain is myfirstdomain.com with Name server ns1.myfirstdomain.com and ns2.myfirstdomain.com

I configure some subdomains from: mail01.domain1 to mail10.domain1.com.

Then I add the new virtual Machine, with domain name: domain2.com.

I create the subdomains again from mail01.domain2.com to mail10.domain2.com with reversed ip.

I have each ip for each sub domains.

By the way, when dig the subdomains of the domain2.com, they are all resolved to first domain.
> 
$ dig -x xxx.xx.xx.xx +short 
mail01.domain2.com. 

(xxx.xx.xx.xx is the ip reversed for mail01.myseconddomain.com)

I really don't understand why. I tried to delete all and created again but still the same result.

How can i fix it?

Thanks

---

### Post by darkod on 2015-10-10
I don't understand much of what you are trying to do... If dig domain2.com is resolved to domain1.com then that looks like your forward dns is not configured correctly, not the reverse dns.

And for the subdomains you mention, are they "real" subdomains or just host A records in domain1.com and domain2.com?

---

### Post by hunterlove22 on 2015-10-10
I created the A Records for them. 

Here is the record for domain2.


>  @    IN    SOA    ns1.domain1.com root.domain1.com (            2015101020
            10800
            3600
            604800
            38400 )
domain2.com.    IN    NS    ns1.domain1.com
domain2.com.    IN    A    xxx.xx.xx.32
[www.domain2.com]("http://www.domain2.com").    IN    A    xxx.xx.xx.32
ftp.domain2.com.    IN    A    xxx.xx.xx.32
m.domain2.com.    IN    A    xxx.xx.xx.32
localhost.domain2.com.    IN    A    127.0.0.1
webmail.domain2.com.    IN    A    xxx.xx.xx.32
admin.domain2.com.    IN    A    xxx.xx.xx.32
mail.domain2.com.    IN    A    xxx.xx.xx.32
domain2.com.    IN    MX    5 mail.domain2.com.
domain2.com.    IN    TXT    "v=spf1 a mx a:domain1.com ip4:xxx.xx.xx.32 ip6:2xxx.xx.xx::36 ?all"
domain2.com.    IN    AAAA    2xxx.xx.xx::36
[www.domain2.com]("http://www.domain2.com").    IN    AAAA    2xxx.xx.xx::36
ftp.domain2.com.    IN    AAAA    2xxx.xx.xx::36
m.domain2.com.    IN    AAAA    2xxx.xx.xx::36
webmail.domain2.com.    IN    AAAA    2xxx.xx.xx::36
admin.domain2.com.    IN    AAAA    2xxx.xx.xx::36
mail.domain2.com.    IN    AAAA    2xxx.xx.xx::36
domain2.com.    IN    NS    ns2.domain1.com
mta12.domain2.com.    IN    A    xxx.xx.xx.44
mta13.domain2.com.    IN    A    xxx.xx.xx.45
mta14.domain2.com.    IN    A    xxx.xx.xx.46
mta15.domain2.com.    IN    A    xxx.xx.xx.47
mta16.domain2.com.    IN    A    xxx.xx.xx.48
mta17.domain2.com.    IN    A    xxx.xx.xx.49
mta18.domain2.com.    IN    A    xxx.xx.xx.50
mta19.domain2.com.    IN    A    xxx.xx.xx.51
mta20.domain2.com.    IN    A    xxx.xx.xx.52
mta21.domain2.com.    IN    A    xxx.xx.xx.53


Here is the reversed records:

> $ttl 38400xxx.xx.xx.in-addr.arpa.    IN    SOA    ns1.domain1.com. root.domain1.com. (
            2015101028
            10800
            3600
            604800
            38400 )
xxx.xx.xx.in-addr.arpa.    IN    NS    ns1.domain1.com.
32.xxx.xx.xx.in-addr.arpa.    IN    PTR    ns1.domain1.com.
33.xxx.xx.xx.in-addr.arpa.    IN    PTR    ns2.domain1.com.
44.xxx.xx.xx.in-addr.arpa.    IN    PTR    mta12.domain2.com.
45.xxx.xx.xx.in-addr.arpa.    IN    PTR    mta13.domain2.com.
46.xxx.xx.xx.in-addr.arpa.    IN    PTR    mta14.domain2.com.
47.xxx.xx.xx.in-addr.arpa.    IN    PTR    mta15.domain2.com.
49.xxx.xx.xx.in-addr.arpa.    IN    PTR    mta17.domain2.com.
51.xxx.xx.xx.in-addr.arpa.    IN    PTR    mta19.domain2.com.
50.xxx.xx.xx.in-addr.arpa.    IN    PTR    mta18.domain2.com.
48.xxx.xx.xx.in-addr.arpa.    IN    PTR    mta16.domain2.com.
52.xxx.xx.xx.in-addr.arpa.    IN    PTR    mta20.domain2.com.
53.xxx.xx.xx.in-addr.arpa.    IN    PTR    mta21.domain2.com.
34.xxx.xx.xx.in-addr.arpa.    IN    PTR    mta2.domain1.com.
35.xxx.xx.xx.in-addr.arpa.    IN    PTR    mta3.domain1.com.
36.xxx.xx.xx.in-addr.arpa.    IN    PTR    mta4.domain1.com.
37.xxx.xx.xx.in-addr.arpa.    IN    PTR    mta5.domain1.com.
38.xxx.xx.xx.in-addr.arpa.    IN    PTR    mta6.domain1.com.
39.xxx.xx.xx.in-addr.arpa.    IN    PTR    mta7.domain1.com.
40.xxx.xx.xx.in-addr.arpa.    IN    PTR    mta8.domain1.com.
41.xxx.xx.xx.in-addr.arpa.    IN    PTR    mta9.domain1.com.
42.xxx.xx.xx.in-addr.arpa.    IN    PTR    mta10.domain1.com.
43.xxx.xx.xx.in-addr.arpa.    IN    PTR    mta11.domain1.com.




My first domain:

> $ttl 38400@	IN	SOA	domain1.com. root.domain1.com. (
			2015101021
			10800
			3600
			604800
			38400 )
domain1.com.	IN	NS	ns1.domain1.com.
domain1.com.	IN	A	xxx.xx.xx.32
[www.domain1.com](www.domain1.com).	IN	A	xxx.xx.xx.32
ftp.domain1.com.	IN	A	xxx.xx.xx.32
m.domain1.com.	IN	A	xxx.xx.xx.32
localhost.domain1.com.	IN	A	127.0.0.1
webmail.domain1.com.	IN	A	xxx.xx.xx.32
admin.domain1.com.	IN	A	xxx.xx.xx.32
mail.domain1.com.	IN	A	xxx.xx.xx.32
domain1.com.	IN	MX	5 mail.domain1.com.
domain1.com.	IN	TXT	"v=spf1 a mx ptr ip4:xxx.xx.xx.32/24 ip6:xxx.xx.xx::36 include:google.com all"
domain1.com.	IN	AAAA	xxx.xx.xx::36
[www.domain1.com](www.domain1.com).	IN	AAAA	xxx.xx.xx::36
ftp.domain1.com.	IN	AAAA	xxx.xx.xx::36
m.domain1.com.	IN	AAAA	xxx.xx.xx::36
webmail.domain1.com.	IN	AAAA	xxx.xx.xx::36
admin.domain1.com.	IN	AAAA	xxx.xx.xx::36
mail.domain1.com.	IN	AAAA	xxx.xx.xx::36
domain1.com.	IN	NS	ns2.domain1.com.
ns1.domain1.com.	IN	A	xxx.xx.xx.32
ns2.domain1.com.	IN	A	xxx.xx.xx.33
mta1.domain1.com.	IN	A	xxx.xx.xx.33
mta2.domain1.com.	IN	A	xxx.xx.xx.34
mta3.domain1.com.	IN	A	xxx.xx.xx.35
mta4.domain1.com.	IN	A	xxx.xx.xx.36
mta5.domain1.com.	IN	A	xxx.xx.xx.37
mta6.domain1.com.	IN	A	xxx.xx.xx.38
mta7.domain1.com.	IN	A	xxx.xx.xx.39
mta8.domain1.com.	IN	A	xxx.xx.xx.40
mta9.domain1.com.	IN	A	xxx.xx.xx.41
mta10.domain1.com.	IN	A	xxx.xx.xx.42
mta11.domain1.com.	IN	A	xxx.xx.xx.43




---

### Post by darkod on 2015-10-10
If you want domain2.com to be separate zone on its own, you can't use IN SOA ns1.domain1.com... That is the important line that specifies the main domain of the zone. Plus the ns1 part is a mistake.

For domain2.com code you posted, you have few mistakes.
#1 IN SOA ns1.domain1.com. should be domain2.com.
```
@   IN   SOA   domain2.com. root.domain1.com.
```

The root.domain1.com. is the mail address of the admin, so you can use domain1 or domain2, as you choose. But the first part after the SOA must be the domain you are creating the zone for.

#2 The IN NS definition goes like this, and always with a dot at the end. I assume you will be using same ns1.domain1.com and ns2.domain1.com dns servers for both domains.
```
@   IN   NS   ns1.domain1.com.
@   IN   NS   ns2.domain1.com.
```

These ns1 and ns2 A records have to exist in the domain1.com zone.

For all forward zones, you have errors in your A records. You need to specify only the prefix, without the domain name at the end. For example:
```
@   IN   A   x.x.x.32
www   IN   A   x.x.x.32
ftp   IN   A   x.x.x.32
......
```

Here is the basic ubuntu guide for dns and records syntax: [https://help.ubuntu.com/lts/serverguide/dns-configuration.html](https://help.ubuntu.com/lts/serverguide/dns-configuration.html)

Try that...

PS. I forgot to mention, if you want two separate zones for domain1.com and domain2.com of course you need two separate zone definitions in /etc/bind/named.conf.local. You can't create only one zone definition for domain1.com and then expect to control create/manage records also for domain2.com. The two are separate. Your /etc/bind/named.conf.local should have something like:
```
 zone "domain1.com" {
   type master;
   file "/etc/bind/db.domain1.com";
};

zone "domain2.com" {
   type master;
   file "/etc/bind/db.domain2.com";
};
```

Then you put your config in /etc/bind/db.domain1.com and /etc/bind/db.domain2.com for each domain accordingly.

---

### Post by hunterlove22 on 2015-10-10
FYI, I am using webmin to create them. 

1. yep, lemme edit it and see.

2. I am not sure why it used the full domain names.

3.  I have separate zones:

```
options {	listen-on port 53 {
		any;
		};
	listen-on-v6 port 53 {
		any;
		};
	directory 	"/var/named";
	dump-file 	"/var/named/data/cache_dump.db";
        statistics-file "/var/named/data/named_stats.txt";
        memstatistics-file "/var/named/data/named_mem_stats.txt";
	recursion yes;


	dnssec-enable yes;
	dnssec-validation no;


	/* Path to ISC DLV key */
	bindkeys-file "/etc/named.iscdlv.key";


	managed-keys-directory "/var/named/dynamic";
	forwarders {
		xx.xx.xx.x;
		xx.xx.xx.x;
		};
	forward first;
	transfer-format one-answer;
};


logging {
        channel default_debug {
                file "data/named.run";
                severity dynamic;
        };
};


zone "." IN {
	type hint;
	file "named.ca";
};


include "/etc/named.rfc1912.zones";
include "/etc/named.root.key";


trusted-keys {
	};
zone "domain3.com" {
	type master;
	file "/var/named/domain3.com.hosts";
	allow-transfer {
		127.0.0.1;
		localnets;
		};
	};
zone "domain1.com" {
	type master;
	file "/var/named/domain1.com.hosts";
	allow-transfer {
		127.0.0.1;
		localnets;
		};
	};
zone "domain2.com" {
	type master;
	file "/var/named/domain2.com.hosts";
	allow-transfer {
		127.0.0.1;
		localnets;
		};
	};
zone "xx.xx.xxx.in-addr.arpa" {
	type master;
	file "/var/named/xxxx.xx.xx.rev";
	};



```

---

### Post by darkod on 2015-10-10
Yes, webmin might have something to do with it. How it edits the files is not always good. That's why it's not an official tool and not recommended. If you are willing to work over ssh session I would use ssh for all important management. Not webmin.

That way you know for sure what the modified file looks like.

---

### Post by hunterlove22 on 2015-10-10
I edited it and Bind didn't start then. Can you take a look above settings and see what's else I should do?

---

### Post by darkod on 2015-10-10
Is it in /var/named instead of /etc/bind? The documentation shows /etc/bind as default.

Check any error messages in /var/log/syslog.

My installation has /etc/bind and there is no /var/named at all.

---

### Post by hunterlove22 on 2015-10-10
Nothing interesting there

```
Oct 10 17:32:21 rapsaye named[11710]: sizing zone task pool based on 10 zonesOct 10 17:32:21 rapsaye named[11710]: set up managed keys zone for view _default, file '/var/named/dynamic/managed-keys.bind'
Oct 10 17:32:21 rapsaye named[11710]: Warning: 'empty-zones-enable/disable-empty-zone' not set: disabling RFC 1918 empty zones
Oct 10 17:32:21 rapsaye named[11710]: automatic empty zone: 127.IN-ADDR.ARPA
Oct 10 17:32:21 rapsaye named[11710]: automatic empty zone: 254.169.IN-ADDR.ARPA
Oct 10 17:32:21 rapsaye named[11710]: automatic empty zone: 2.0.192.IN-ADDR.ARPA
Oct 10 17:32:21 rapsaye named[11710]: automatic empty zone: 100.51.198.IN-ADDR.ARPA
Oct 10 17:32:21 rapsaye named[11710]: automatic empty zone: 113.0.203.IN-ADDR.ARPA
Oct 10 17:32:21 rapsaye named[11710]: automatic empty zone: 255.255.255.255.IN-ADDR.ARPA
Oct 10 17:32:21 rapsaye named[11710]: automatic empty zone: 0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
Oct 10 17:32:21 rapsaye named[11710]: automatic empty zone: D.F.IP6.ARPA
Oct 10 17:32:21 rapsaye named[11710]: automatic empty zone: 8.E.F.IP6.ARPA
Oct 10 17:32:21 rapsaye named[11710]: automatic empty zone: 9.E.F.IP6.ARPA
Oct 10 17:32:21 rapsaye named[11710]: automatic empty zone: A.E.F.IP6.ARPA
Oct 10 17:32:21 rapsaye named[11710]: automatic empty zone: B.E.F.IP6.ARPA
Oct 10 17:32:21 rapsaye named[11710]: automatic empty zone: 8.B.D.0.1.0.0.2.IP6.ARPA
Oct 10 17:32:21 rapsaye named[11710]: command channel listening on 127.0.0.1#953
Oct 10 17:32:21 rapsaye named[11710]: command channel listening on ::1#953
Oct 10 17:32:21 rapsaye named[11710]: zone 0.in-addr.arpa/IN: loaded serial 0
Oct 10 17:32:21 rapsaye named[11710]: zone 1.0.0.127.in-addr.arpa/IN: loaded serial 0
Oct 10 17:32:21 rapsaye named[11710]: zone xx.xx.xxx.in-addr.arpa/IN: loaded serial 2015101028
Oct 10 17:32:21 rapsaye named[11710]: zone 1.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.ip6.arpa/IN: loaded serial 0
Oct 10 17:32:21 rapsaye named[11710]: zone domain1.com/IN: loaded serial 2015101022
Oct 10 17:32:21 rapsaye named[11710]: zone domain3.com/IN: loaded serial 2015101000
Oct 10 17:32:21 rapsaye named[11710]: zone domain2.com/IN: loaded serial 2015101020
Oct 10 17:32:21 rapsaye named[11710]: zone localhost.localdomain/IN: loaded serial 0
Oct 10 17:32:21 rapsaye named[11710]: zone localhost/IN: loaded serial 0
Oct 10 17:32:21 rapsaye named[11710]: managed-keys-zone ./IN: loaded serial 144
Oct 10 17:32:21 rapsaye named[11710]: running
Oct 10 17:32:21 rapsaye named[11710]: zone domain2.com/IN: sending notifies (serial 2015101020)
Oct 10 17:32:21 rapsaye named[11710]: zone domain1.com/IN: sending notifies (serial 2015101022)
Oct 10 17:34:10 rapsaye clamd[3072]: SelfCheck: Database status OK.
Oct 10 17:49:12 rapsaye clamd[3072]: SelfCheck: Database status OK.
```

---

### Post by darkod on 2015-10-10
Well, it does say the zones for the domains are loaded...
```
[COLOR=#000000]*Oct 10 17:32:21 rapsaye named[11710]: zone domain1.com/IN: loaded serial 2015101022*[/COLOR]
[COLOR=#000000]*Oct 10 17:32:21 rapsaye named[11710]: zone domain3.com/IN: loaded serial 2015101000*[/COLOR]
[COLOR=#000000]*Oct 10 17:32:21 rapsaye named[11710]: zone domain2.com/IN: loaded serial 2015101020*[/COLOR]
```

The service is not running?
```
sudo service bind9 status
```

---

### Post by hunterlove22 on 2015-10-10
CPUs found: 4
worker threads: 4
number of zones: 24
debug level: 0
xfers running: 0
xfers deferred: 0
soa queries in progress: 0
query logging is OFF
recursive clients: 0/0/1000
tcp clients: 0/100
server is up and running
named (pid  31597) is running...

---

### Post by hunterlove22 on 2015-10-10
I dont know why the IP still reversed to the domain1.com instead of domain2.com

For example if I dig mta20.domain2.com's ip, it willl show mta20.domain1.com.

---

### Post by darkod on 2015-10-10
Did you restart the service after modifying the files? You always need to do that.

I am also surprised the service is called named. Mine is called bind9. How did you install bind and which version of ubuntu server you are running? This could have everything to do with webmin too, it might not install bind the same way.

---

### Post by hunterlove22 on 2015-10-10
yep i did. Buut still wrong resolving.

---

### Post by darkod on 2015-10-10
You didn't answer which version of ubuntu server you are running. In your place I would remove and reinstall bind using ssh session, to rule out webmin messing things up, especially if the first time you activated/installed the dns service through webmin.

Something like:
```
sudo apt-get purge bind9
sudo apt-get install bind9
```

After that it should be installed in the folder /etc/bind and the main config files should be there. Before removing it you can copy the zone files you have to another location and use them later.

After it's reinstalled make the zone entries in /etc/bind/named.conf.local. Start with one domain only. Copy the needed zone file to the needed location, for example /etc/bind/db.domain1.com or create a new zone file with the basic entries for a start.

See if that works... If it works for one domain, continue with the rest.

---

### Post by hunterlove22 on 2015-10-12
[COLOR=#000000][FONT=Verdana]I created the DNS zone with that subdomain and ip. However, when i checked it, that ip was reversed to sub1.domain1.com instead of sub1.domain2.com.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]I checked the losf with pid of named, i found these:

> [/FONT][/COLOR][COLOR=#000000][FONT=Verdana]named 14987 named 21u IPv4 2040244 0t0 TCP server.domain1.com:domain (LISTEN)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]named 14987 named 22u IPv4 2040246 0t0 TCP mta1.domain1.com:domain (LISTEN)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]named 14987 named 23u IPv4 2040248 0t0 TCP mta2.domain1.com:domain (LISTEN)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]named 14987 named 24u IPv4 2040250 0t0 TCP mta3.domain1.com:domain (LISTEN)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]named 14987 named 25u IPv4 2040252 0t0 TCP mta4.domain1.com:domain (LISTEN)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]named 14987 named 26u IPv4 2040254 0t0 TCP mta5.domain1.com:domain (LISTEN)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]named 14987 named 27u IPv4 2040256 0t0 TCP mta6.domain1.com:domain (LISTEN)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]named 14987 named 28u IPv4 2040258 0t0 TCP mta7.domain1.com:domain (LISTEN)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]named 14987 named 29u IPv4 2040260 0t0 TCP mta8.domain1.com:domain (LISTEN)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]named 14987 named 30u IPv4 2040262 0t0 TCP mta9.domain1.com:domain (LISTEN)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]named 14987 named 31u IPv4 2040264 0t0 TCP mta10.domain1.com:domain (LISTEN)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]named 14987 named 32u IPv4 2040266 0t0 TCP mta11.domain1.com:domain (LISTEN)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]named 14987 named 33u IPv4 2040268 0t0 TCP mta12.domain1.com:domain (LISTEN)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]named 14987 named 34u IPv4 2040270 0t0 TCP mta13.domain1.com:domain (LISTEN)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]named 14987 named 35u IPv4 2040272 0t0 TCP mta14.domain1.com:domain (LISTEN)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]named 14987 named 36u IPv4 2040274 0t0 TCP mta15.domain1.com:domain (LISTEN)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]named 14987 named 37u IPv4 2040276 0t0 TCP mta16.domain1.com:domain (LISTEN)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]named 14987 named 38u IPv4 2040278 0t0 TCP mta17.domain1.com:domain (LISTEN)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]named 14987 named 39u IPv4 2040280 0t0 TCP mta18.domain1.com:domain (LISTEN)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]named 14987 named 40u IPv4 2040282 0t0 TCP mta19.domain1.com:domain (LISTEN)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]named 14987 named 41u IPv4 2040284 0t0 TCP mta20.domain1.com:domain (LISTEN)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]named 14987 named 42u IPv4 2040286 0t0 TCP mta21.domain1.com:domain (LISTEN)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]named 14987 named 43u IPv4 2040288 0t0 TCP mta22.domain1.com:domain (LISTEN)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]named 14987 named 44u IPv4 2040290 0t0 TCP mta23.domain1.com:domain (LISTEN)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]named 14987 named 45u IPv4 2040292 0t0 TCP mta24.domain1.com:domain (LISTEN)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]named 14987 named 46u IPv4 2040294 0t0 TCP mta25.domain1.com:domain (LISTEN)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]named 14987 named 47u IPv4 2040296 0t0 TCP mta26.domain1.com:domain (LISTEN)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]named 14987 named 48u IPv4 2040298 0t0 TCP mta27.domain1.com:domain (LISTEN)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]named 14987 named 49u IPv4 2040300 0t0 TCP mta28.domain1.com:domain (LISTEN)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]named 14987 named 50u IPv4 2040302 0t0 TCP mta29.domain1.com:domain (LISTEN)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]named 14987 named 51u IPv4 2040304 0t0 TCP mta30.domain1.com:domain (LISTEN)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]named 14987 named 52u IPv4 2040306 0t0 TCP mta31.domain1.com:domain (LISTEN)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]named 14987 named 53u IPv4 2040309 0t0 TCP ns1:rndc (LISTEN)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]named 14987 named 512u IPv4 2040241 0t0 UDP ns1:domain [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]named 14987 named 513u IPv4 2040243 0t0 UDP server.domain1.com:domain [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]named 14987 named 514u IPv4 2040245 0t0 UDP mta1.domain1.com:domain [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]named 14987 named 515u IPv4 2040247 0t0 UDP mta2.domain1.com:domain [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]named 14987 named 516u IPv4 2040249 0t0 UDP mta3.domain1.com:domain [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]named 14987 named 517u IPv4 2040251 0t0 UDP mta4.domain1.com:domain [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]named 14987 named 518u IPv4 2040253 0t0 UDP mta5.domain1.com:domain [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]named 14987 named 519u IPv4 2040255 0t0 UDP mta6.domain1.com:domain [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]named 14987 named 520u IPv4 2040257 0t0 UDP mta7.domain1.com:domain [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]named 14987 named 521u IPv4 2040259 0t0 UDP mta8.domain1.com:domain [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]named 14987 named 522u IPv4 2040261 0t0 UDP mta9.domain1.com:domain [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]named 14987 named 523u IPv4 2040263 0t0 UDP mta10.domain1.com:domain [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]named 14987 named 524u IPv4 2040265 0t0 UDP mta11.domain1.com:domain [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]named 14987 named 525u IPv4 2040267 0t0 UDP mta12.domain1.com:domain [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]named 14987 named 526u IPv4 2040269 0t0 UDP mta13.domain1.com:domain [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]named 14987 named 527u IPv4 2040271 0t0 UDP mta14.domain1.com:domain [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]named 14987 named 528u IPv4 2040273 0t0 UDP mta15.domain1.com:domain [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]named 14987 named 529u IPv4 2040275 0t0 UDP mta16.domain1.com:domain [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]named 14987 named 530u IPv4 2040277 0t0 UDP mta17.domain1.com:domain [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]named 14987 named 531u IPv4 2040279 0t0 UDP mta18.domain1.com:domain [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]named 14987 named 532u IPv4 2040281 0t0 UDP mta19.domain1.com:domain [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]named 14987 named 533u IPv4 2040283 0t0 UDP mta20.domain1.com:domain [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]named 14987 named 534u IPv4 2040285 0t0 UDP mta21.domain1.com:domain [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]named 14987 named 535u IPv4 2040287 0t0 UDP mta22.domain1.com:domain [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]named 14987 named 536u IPv4 2040289 0t0 UDP mta23.domain1.com:domain [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]named 14987 named 537u IPv4 2040291 0t0 UDP mta24.domain1.com:domain [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]named 14987 named 538u IPv4 2040293 0t0 UDP mta25.domain1.com:domain [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]named 14987 named 539u IPv4 2040295 0t0 UDP mta26.domain1.com:domain [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]named 14987 named 540u IPv4 2040297 0t0 UDP mta27.domain1.com:domain [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]named 14987 named 541u IPv4 2040299 0t0 UDP mta28.domain1.com:domain [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]named 14987 named 542u IPv4 2040301 0t0 UDP mta29.domain1.com:domain [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]named 14987 named 543u IPv4 2040303 0t0 UDP mta30.domain1.com:domain [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]named 14987 named 544u IPv4 2040305 0t0 UDP mta31.domain1.com:domain[/FONT][/COLOR][COLOR=#000000][FONT=Verdana][/FONT][/COLOR]

---

### Post by darkod on 2015-10-12
Can you post the new zone files? Something is wrong...

And what do you mean by "that ip was reversed"? You are talking about the forward or reverse zone? Is the forward zone working good? Lets get that out of the way first.

---

### Post by SeijiSensei on 2015-10-12
Unless those are private IP addresses, or your public subnet is "[delegated]("https://www.ietf.org/rfc/rfc2317.txt")" from your ISP which is rare, you have no control over reverse lookups. Only the ISP can manage those.  

Since you have all the IPs obfuscated, I'm guessing they are public?

---

