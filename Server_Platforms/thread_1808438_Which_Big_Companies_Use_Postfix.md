---
title: "Which Big Companies Use Postfix"
date: 2011-07-20
forum: Server Platforms
---

### Post by systemshq on 2011-07-20
I've done a search on the internet to see which big companies use i.e. the googles, yahoos etc use postfix and have come up with a blank. In theory I could do eg -

dig google.com mx

and it would come up with:-

;; ANSWER SECTION:
google.com.		600	IN	MX	50 alt4.aspmx.l.google.com.
google.com.		600	IN	MX	40 alt3.aspmx.l.google.com.
google.com.		600	IN	MX	30 alt2.aspmx.l.google.com.
google.com.		600	IN	MX	10 aspmx.l.google.com.
google.com.		600	IN	MX	20 

and then:-

telnet alt1.aspmx.l.google.com 25

Trying 74.125.47.27...
Connected to alt4.aspmx.l.google.com.
Escape character is '^]'.
220 mx.google.com ESMTP r61si735760yhm.1
ehlo systemshq.net
250-mx.google.com at your service, [89.16.173.238]
250-SIZE 35882577
250-8BITMIME
250-STARTTLS
250 ENHANCEDSTATUSCODES

but the actual name of the mail server software is hidden. I've tried going to netcraft but I guess because of the above problem they can't compile an accurate survey.

Anyone know any big names using postfix please?

Many thanks in advance

---

### Post by efball3 on 2011-07-22
> **systemshq said:**
> I've done a search on the internet to see which big companies use i.e. the googles, yahoos etc use postfix and have come up with a blank. 

Anyone know any big names using postfix

hp
agilent (spun off from hp).

---

