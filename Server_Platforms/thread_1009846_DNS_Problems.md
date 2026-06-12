---
title: "DNS Problems"
date: 2008-12-13
forum: Server Platforms
---

### Post by Counter on 2008-12-13
I have a Server hosting a website that the ip has recently change and I had to go resetup my Dns server. Now before this I could simply type my address like mysite.com and it would find it ok , now it will simply not. I have to type [www.mysite](www.mysite) in order for it to find it . Im sure it something simple , but ive messed with is alot and could use some help.Also wonder if maybe because my ISP has control of my reverse lookups if this could be a factor? Thanks


$ttl 38400
mysite.com.	IN  SOA  server1.mysite.com. jesse.mysite.com. 
(
			1219374769
			10800
			3600
			604800
			38400 )
mysite.com.	IN	NS	server1.mysite.com.
ftp.mysite.com.	IN	CNAME	mysite.com.
mysite.com.	IN	MX	10 mysite.com.
mysite.com.	IN	A	111.11.11.111
[www.mysite.com](www.mysite.com).	IN	CNAME	mysite.com.
mail.mysite.com.	IN	CNAME	mysite.com.
173.20.32.201.mysite.com.	IN	PTR	mysite.com.
server1.mysite.com.	IN	CNAME	mysite.com.

---

### Post by MJN on 2008-12-13
Tell us your real domain, and post your unaltered configuration, otherwise it makes fault diagnosis of this type of problem infinitely more difficult.

Assuming it is wartactics.net your fault description does not fit the current configuration.

Resolving wartactics.net we get:

```
$ dig wartactics.net a

; <<>> DiG 9.3.2-P2.1 <<>> wartactics.net a
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 35281
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;wartactics.net.                        IN      A

;; ANSWER SECTION:
wartactics.net.         38216   IN      A       173.20.32.201

;; Query time: 21 msec
;; SERVER: 208.67.222.222#53(208.67.222.222)
;; WHEN: Sat Dec 13 11:00:16 2008
;; MSG SIZE  rcvd: 48
``` Whereas attempting to resolve [www.wartactics.net]("http://www.wartactics.net") we get:

```
$ dig www.wartactics.net a

; <<>> DiG 9.3.2-P2.1 <<>> www.wartactics.net a
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 44179
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;www.wartactics.net.            IN      A

;; Query time: 401 msec
;; SERVER: 208.67.222.222#53(208.67.222.222)
;; WHEN: Sat Dec 13 11:00:52 2008
;; MSG SIZE  rcvd: 36
```Hence it is www. which is not working - the opposite of what you described.

Your PTR record is also wrong, but won't have any bearing on this problem.

Mathew

---

### Post by bluefrog on 2008-12-13
www IN A IP ## [www.example.com](www.example.com) will respond
@   IN A IP ## example.com will respond
*   IN A IP ## anything.example.com will respond (including www)

takes time also for the DNS to propagate

---

### Post by martien on 2008-12-13
You have to set the new ip to your nameservers (or create new nameservers) and point your domain to them. As I see from your zone file i'm wondering how can you run your domain with only one NS, when the registrant would not let you do that. I think if its a top level domain (com,net,org,biz...) it must have at least 2 nameservers.

---

