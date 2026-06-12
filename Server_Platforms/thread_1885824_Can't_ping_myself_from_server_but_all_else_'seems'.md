---
title: "Can't ping myself from server but all else 'seems' to work fine (BIND9)"
date: 2011-11-23
forum: Server Platforms
---

### Post by yt_l9 on 2011-11-23
*Running 11.10 64-bit Ubuntu-Server*

I've been tasked with setting up an email server for a school project and have hit a snag, after searching for about a week and not being able to figure it out on my own... I've decided to come here for help.

The issue is simply that I can't resolve to my domain via ping from the server it's self whereas it works from other stations on the network- that and dig doesn't seem to recognize anything beyond my router but I'll save that for a late date.  

I'm sure I'm just overlooking something really stupid but here goes:
/etc/bind/named.conf.local
```
        zone "UHMS.us" {
             type master;
             file "/etc/bind/db.UHMS.us";
        };

	zone "1.168.192.in-addr.arpa" {
	        type master;
	        notify no;
	        file "/etc/bind/db.192";
	};
```
dig -x 127.0.0.1
```
; <<>> DiG 9.7.3 <<>> -x 127.0.0.1
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 16386
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 2

;; QUESTION SECTION:
;1.0.0.127.in-addr.arpa.		IN	PTR

;; ANSWER SECTION:
1.0.0.127.in-addr.arpa.	604800	IN	PTR	localhost.

;; AUTHORITY SECTION:
127.in-addr.arpa.	604800	IN	NS	localhost.

;; ADDITIONAL SECTION:
localhost.		604800	IN	A	127.0.0.1
localhost.		604800	IN	AAAA	::1

;; Query time: 0 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Wed Nov 23 23:00:09 2011
;; MSG SIZE  rcvd: 121
```
db.UHMS.us
```
; BIND data file for local loopback interface
;
$TTL	604800
@	IN	SOA	server1.UHMS.us. root.UHMS.us. (
			      4		; Serial
			 604800		; Refresh
			  86400		; Retry
			2419200		; Expire
			 604800 )	; Negative Cache TTL
;
@	IN	NS	ns.UHMS.us.
ns	IN	A	192.168.1.100
mail	IN	A	192.168.1.100
@	IN	AAAA	::1
;
; MX Records
UHMS.us.	IN	MX	10	mail.UHMS.us.
```
db.192
```
; BIND reverse data file for local loopback interface
;
$TTL	604800
@	IN	SOA	localhost. root.localhost. (
			      3		; Serial
			 604800		; Refresh
			  86400		; Retry
			2419200		; Expire
			 604800 )	; Negative Cache TTL
;
@	IN	NS	ns.
100	IN	PTR	ns.UHMS.us.
100	IN	PTR	mail.UHMS.us.
```

and of course...
ping -c 3 google.com
```
64 bytes from yi-in-f99.1e100.net (74.125.159.99): icmp_req=1 ttl=51 time=38.7 ms
64 bytes from yi-in-f99.1e100.net (74.125.159.99): icmp_req=2 ttl=51 time=36.2 ms
64 bytes from yi-in-f99.1e100.net (74.125.159.99): icmp_req=3 ttl=51 time=37.3 ms

--- google.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 36.248/37.434/38.719/1.011 ms
```

but, from the server, if I try to...
ping -c 3 UHMS.us, it leads to:
```
ping: unknown host UHMS.us
```
I don't think this should prevent me from setting up POSTFIX but just in case I'd like to get it all working properly.  I'll be checking back frequently should anyone have a quick solution or be in need of more info.

If this helps any (dig from the server):
```
; <<>> DiG 9.7.3 <<>> uhms.us
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 292
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;uhms.us.			IN	A

;; AUTHORITY SECTION:
uhms.us.		604800	IN	SOA	server1.uhms.us. root.uhms.us. 4 604800 86400 2419200 604800

;; Query time: 0 msec
;; SERVER: 192.168.1.100#53(192.168.1.100)
;; WHEN: Wed Nov 23 23:22:53 2011
;; MSG SIZE  rcvd: 74
```


Thank you in advance! :)

---

### Post by Doug S on 2011-11-24
I will try to help, while also trying to respect forum policy to not to do one's school work for them. Your "ping UHMS.us" issue I think could be solved by a change to your db.UHMS.us file. I would try this for the SOA part:
```

@    IN    SOA    UHMS.us. root.UHMS.us. (
             4        ; Serial
             604800        ; Refresh
             86400        ; Retry
            2419200        ; Expire
             604800 )    ; Negative Cache TTL
       IN    A    192.168.1.100

```
and then declare server1.UHMS.us seperately as another "A" record.
I think your MX record is incorrect. See the example in the [Ubuntu 11.10 server guide]("https://help.ubuntu.com/11.10/serverguide/C/index.html") ([I prefer the PDF version]("https://help.ubuntu.com/11.10/serverguide/C/serverguide.pdf")) (there are some good references in the DNS section of the server guide also).
 
Edit: I forgot to mention your db.192 file needs some work. There should only be 1 reverse entry per IP address. And I think the SOA should be something.UHMS.us related and not localhost related.

---

### Post by yt_l9 on 2011-11-28
Thank you! I'll try to change those shortly.  

Not that it matters much but I wasn't looking for a "do my homework" as much as "what did I screw up this time" which you hopefully pointed out.  =D


Just as a follow up, I followed your suggestions and re-read the guide... but it's still not resolving it's self.  I swapped localhost to UHMS.us.   root.UHMS.us within db.192 as well swapping out your suggestion for what I had in db.UHMS.us.  I got the email server to work regardless of this, and class has finished, but it's kind of bothering me that it's not working as I had hoped.  I want to teach myself about virtual machines, web hosting and a few other aspects of servers but I'm kind of hung up on this. - yes I increased the serial # and restarted BIND to no avail.  

Any other ideas on what I might be messing up?

---

### Post by yt_l9 on 2012-12-19
Very much a late update here, but the problem was fixed by properly configuring the hosts file if I recall correctly.  This was remedied quite some time ago but I forgot my login information (before I started using last-pass).

---

