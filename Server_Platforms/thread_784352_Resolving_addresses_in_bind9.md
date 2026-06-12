---
title: "Resolving addresses in bind9"
date: 2008-05-06
forum: Server Platforms
---

### Post by spark01 on 2008-05-06
I'm working on setting up a DNS server with Bind9 on an ubuntu 7.10 machine.  Right now, I can resolve all of my virtual hostnames with a dig, and can ping them, but only from the localhost.  Also, I get an error when using nslookup.  

root@test:/home/susy# nslookup mvrsouthernalberta.ca
Server:         127.0.0.1
Address:        127.0.0.1#53

*** Can't find mvrsouthernalberta.ca: No answer

I can't resolve or ping any of my hostnames from other computers in my local network either.

Any suggestions?

---

### Post by yogensha on 2008-05-06
In order for your changes to be visible to other systems, either those systems must be configured to use your name server, or your name server must be listed globally as the authoritative server for that domain.  Currently:

```

jcole@relleno:~$ dig mvrsouthernalberta.ca ns @ca01.cira.ca.

; <<>> DiG 9.4.2 <<>> mvrsouthernalberta.ca ns @ca01.cira.ca.
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 11664
;; flags: qr rd; QUERY: 1, ANSWER: 0, AUTHORITY: 2, ADDITIONAL: 0
;; WARNING: recursion requested but not available

;; QUESTION SECTION:
;mvrsouthernalberta.ca.		IN	NS

;; AUTHORITY SECTION:
mvrsouthernalberta.ca.	86400	IN	NS	ns2.lcncap.com.
mvrsouthernalberta.ca.	86400	IN	NS	ns1.lcncap.com.

```

So unless the machine you're working on is ns1.lcncap.com or ns2.lcncap.com, your changes won't have global effect.

Here's a good overview of DNS:

[http://www.faqs.org/docs/linux_network/x-087-2-resolv.howdnsworks.html](http://www.faqs.org/docs/linux_network/x-087-2-resolv.howdnsworks.html)

---

