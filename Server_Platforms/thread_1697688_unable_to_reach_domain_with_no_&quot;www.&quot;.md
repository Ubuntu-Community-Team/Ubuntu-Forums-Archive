---
title: "unable to reach domain with no &quot;www.&quot;"
date: 2011-03-01
forum: Server Platforms
---

### Post by envis on 2011-03-01
Hi how is it going, I was just wondering if anyone could help me figure why I cant get my domain name to resolve with no "www." in Bind9

Ive tried a few different way to define my zone file, last one I tried was like this:

```
$TTL    604800
@       IN      SOA     ns.mydomain777.com. info.mydomain777.com. (
                             17         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns.mydomain777.com.
ns      IN      A       66.111.x.x

```

it resolves to my server (66.111.x.x) when I ping [www.mydomain777.com](www.mydomain777.com) or test123.mydomain777.com but when I try to ping just mydomain777.com with no subdomains it does not work:
[INDENT][COLOR="DarkRed"]ping: unknown host mydomain777.com[/COLOR][/INDENT]

if I try dig ns [www.mydomain777.com](www.mydomain777.com) and dig ns mydomain777.com it gives me different results too:

```
dig ns mydomain777.com
```
[INDENT][COLOR="DarkRed"]; <<>> DiG 9.7.1-P2 <<>> ns mydomain777.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 3325
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; QUESTION SECTION:
;mydomain777.com.                      IN      NS

;; ANSWER SECTION:
mydomain777.com.               6400    IN      NS      ns.mydomain777.com.

;; ADDITIONAL SECTION:
ns.mydomain777.com.            9653    IN      A       66.111.x.x

;; Query time: 11 msec
;; SERVER: 192.168.0.1#53(192.168.0.1)
;; WHEN: Mon Feb 28 21:05:21 2011
;; MSG SIZE  rcvd: 59[/COLOR][/INDENT]

```
dig ns www.mydomain777.com
```
[INDENT][COLOR="DarkRed"]; <<>> DiG 9.7.1-P2 <<>> ns [www.mydomain777.com](www.mydomain777.com)
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 18808
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;[www.mydomain777.com](www.mydomain777.com).                  IN      NS

;; AUTHORITY SECTION:
mydomain777.com.               2446    IN      SOA     ns.mydomain777.com. info.mydomain777.com. 4 604800 86400 2419200 604800

;; Query time: 13 msec
;; SERVER: 192.168.0.1#53(192.168.0.1)
;; WHEN: Mon Feb 28 21:06:40 2011
;; MSG SIZE  rcvd: 74[/COLOR][/INDENT]


*the domain "mydomain777.com" is just an example, not the actual domain*

---

### Post by HermanAB on 2011-03-01
Use a wildcard:
*.example.com

---

### Post by envis on 2011-03-01
> **HermanAB said:**
> Use a wildcard:
*.example.com


hey whatsup! thanks a lot for your answer, though Im not sure if you read the question right, like my case is: [www.example.com](www.example.com) pings, testwhatever.example.com pings, but example.com does not ping...

I have another domain which im trying to setup too and I set this one a bit different using a wildcard on that one:

```
$TTL    604800
@       IN      SOA     ns.domain2.com. info.domain2.com. (
                              4         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns.domain2.com.
ns      IN      A       123.123.123.123
www     IN      A       123.123.123.123
*       IN      A       123.123.123.123

```

but even there the result mysteriously is exactly the same [www.domain2.com](www.domain2.com) pings to my server testtesttest.domain2.com pings to my server too, but for some reason domain2.com with no subdomain just doesnt ping, it says unknown host..

its really strange!!

---

### Post by envis on 2011-03-01
Im just really trying to understand this its so damn complicated...

I mean what does it mean that when I dig mydomain777.com I get an authority and no answer:
```
QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0
```
and when I dig justatest.mydomain777.com I get an answer but no authority:
```
QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1
```

anyone knows what that means? is that normal?

---

### Post by envis on 2011-03-01
im also quite unsure about my reverse DNS zone...

I have multiple domains and they all need to point to one of my 2 IP addresses which are right next to each other, so i end up having just 1 reverse zone file (db.66) that looks like that:

```
$TTL    604800
@       IN      SOA     ns.mynameservers.ca. info.mynameservers.ca. (
                              7         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns.

10      IN      PTR     ns.domain1.com.
20      IN      PTR     ns.domain2.com.
30      IN      PTR     ns.domain2.com.
40      IN      PTR     ns.domain4.com.

```

Im not too sure about this but it seems to work, except for the problem where no domain resolves without a subdomain for the moment

ns.mynameservers.ca is a domain that I want to use as my nameservers and it uses the godaddy free DNS to point to my servers

---

### Post by envis on 2011-03-01
hey you know what its working now!! :D

I did this:

```
$TTL    604800
@       IN      SOA     ns.mydomain777.com. info.mydomain777.com. (
                             19         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns.mydomain777.com.
ns      IN      A       x.x.x.x
@       IN      A       x.x.x.x
*       IN      A       x.x.x.x

```

im almost sure I tried that before not sure why it didnt work before maybe I was doing something wrong....

---

### Post by envis on 2011-03-01
and now it stopped working again... still subdomains work but domain with no subdomain goes nowhere.. Im not sure maybe its just long to update or something...

---

### Post by envis on 2011-03-01
anyways now it started working again a bit after I set it to this

```
$TTL    604800
@       IN      SOA     ns.mydomain777.com. info.mydomain777.com.$
                              13         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns.mydomain777.com.
mydomain777.com.       IN      A       123.123.123.123
*.mydomain777.com.  IN      A       123.123.123.123


```

yea thats holding now... its the next day and its still working finally :P

---

### Post by envis on 2011-03-01
now im actually gonna change this to this instead:

```
$TTL    604800
@       IN      SOA     ns.mydomain777.com. info.mydomain777.com.$
                              13         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns.mydomain777.com.
ns  IN      A       123.123.123.123
www  IN      A       123.123.123.123
mydomain777.com.       IN      A       123.123.123.123

```

(getting rid of the wildcard, and because of that i need to specify all the subdomains i want manually, must include "ns" and you probably want "www")

because i decided wildcards are not good. What if someone posted links to ilovehitler.mydomain777.com that would be bad for me cos some ppl would think that this is my site... better that this does not ping or anything else "unplanned". anyways i doubt youll get any traffic from unexisting subdomains so theres no point...

---

