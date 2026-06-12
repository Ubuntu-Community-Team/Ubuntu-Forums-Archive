---
title: "Ubuntu 9.10 bind9, problems"
date: 2010-09-08
forum: Server Platforms
---

### Post by LarsEriksson on 2010-09-08
Im using bind9 as DNS server on my LAN, but it does not seem to translate its own hostname correctly for some reason.
Other hosts is translated correctly, the problem only seems to apply to the DNS host itself.

if i "ping <server_hostname>" from the server, it translates correctly. But if i "ping <server_hostname>" from the client it only says "unknown host"

The client has the correct DNS-server assigned.


How can i start troubleshooting this?

Update:
I tried  this:   (real host name replaced with "dnshost")

```
brasse@brasse-laptop:~$ nslookup
> dnshost
Server:		192.168.1.22
Address:	192.168.1.22#53

*** Can't find dnshost: No answer
>
```

The IP-address seems correct, but what is this #53 thing?


I get the same result if i do "nslookup dnshost" directly from the host itself..

---

### Post by LarsEriksson on 2010-09-14
Ok i have progress.

From my ubuntu workstation:
```
brasse@brasse-laptop:~$ nslookup hostname
Server:		192.168.1.22
Address:	192.168.1.22#53

Name:	hostname.domain
Address: 192.168.1.22

brasse@brasse-laptop:~$ host hostname
hostname.domain has address 192.168.1.22
```

Seems correct enough.
But from WinXP:
```
C:\Documents and Settings\dfgdfg>nslookup hostname
*** Can't find server name for address 192.168.1.22: Server failed
Server:  resolver1-u-fo.skanova.com
Address:  195.67.199.12

*** resolver1-u-fo.skanova.com can't find hostname: Non-existent domain

C:\Documents and Settings\dfgdfg>ping hostname

Skickar signaler till hostname.DOMAIN [192.168.1.22] med 32 byte data:

Svar från 192.168.1.22: byte=32 tid=3ms TTL=64
Svar från 192.168.1.22: byte=32 tid=1ms TTL=64
Svar från 192.168.1.22: byte=32 tid=1ms TTL=64
Svar från 192.168.1.22: byte=32 tid=2ms TTL=64

Ping-statistik för 192.168.1.22:
    Paket: Skickade = 4, mottagna = 4, Förlorade = 0 (0 %),
Ungefärligt överföringstid i millisekunder:
    Lägsta = 1 ms, Högsta = 3 ms, Medel = 1 ms

```
It falls back on secondary DNS, and that is from my ISP.

Windows 2008R2:
```
C:\Users\TEMP.REMOTEDESK>nslookup hostname
Server:  UnKnown
Address:  192.168.1.22

Name:    hostname.DOMAIN
Address:  192.168.1.22

C:\Users\TEMP.REMOTEDESK>nslookup 192.168.1.22
Server:  UnKnown
Address:  192.168.1.22

*** UnKnown can't find 192.168.1.22: Server failed
```


Here are my bind9 configs:
```
root@hostname:/etc/bind# cat named.conf.local 
//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

zone "domain" {
        type master;
        file "/etc/bind/zones/domain.db";
};

zone "1.168.192.in-addr.arpa" {
        type master;
        file "/etc/bind/zones/rev.1.168.192.in-addr.arpa";
};
```

```
root@hostname:/etc/bind/zones# cat domain.db 
domain. IN SOA ns1.domain. admin.domain. (

2006081401
28800
3600
604800
38400 )

domain. 		IN 	NS 		ns1.domain.
 			IN 	A 		192.168.1.22
mail.domain. IN 	MX 	10 	mail.domain.
domain. 		IN 	MX 	10 	mail.domain.
hostname		IN	A		192.168.1.22
www 			IN 	A 		192.168.1.22
mail 			IN 	A 		192.168.1.22
ns1 			IN 	A 		192.168.1.22

```

```
root@hostname:/etc/bind/zones# cat rev.1.168.192.in-addr.arpa 
@ IN SOA domain. admin.domain. (
2006081401;
28800;
604800;
604800;
86400 );

IN NS ns1.domain.
22 IN PTR domain.
22 IN PTR hostname.domain.
```

---

### Post by terazen on 2010-09-14
Why do you have 2 PTR records for .22?  I'd delete the first one and leave the hostname one.  Also, you may want to change ns1 to be a cname pointing to hostname instead of having 2 a records.  It may not be the problem, but it could cause less confusion reading your file.

Edit:
Meant to say change www,ns1, and www to all be cnames.

---

### Post by kalyp on 2011-01-07
@LarsEriksson: how did you go from "*** Can't find dnshost: No answer" to actually resolving it in nslookup? 

I think I have exactly the same problem. More precisely:
- nslookup can't find my machine ("*** Can't find <mymachine>: No answer")
- ping and ssh towards my machine won't work (unknown host) when using the machine name, but work when using the IP address (as obtained from ifconfig)

It's driving me crazy... any help appreciated :)

(oh and I have another machine for which the hostname is resolved but points towards the wrong IP... ie nslookup and ifconfig give 2 different answers. Interested in inputs on that too...)

thanks a lot!

---

