---
title: "Weird SMTP problems."
date: 2008-03-23
forum: Server Platforms
---

### Post by dantheman3212 on 2008-03-23
I've recently set up a Citadel server, and I have everything working, I can receive emails from any outside email server (hotmail, gmail, yahoo) just fine to my user accounts, and can send email to other user accounts on the same domain I'm hosting, but when I try to send an email out to any outside servers, I get either "you must log in to example.com" when sending out an email, and when I enable unauthenticated users to spoof domains, i get "relay denied". Any ideas on how to fix this? Thanks.

---

### Post by HermanAB on 2008-03-23
Check the machine hostname.  If the hostname doesn't match the DNS, then Citadel will refuse to send mail.

The hostname is configured in /etc/sysconfig/network 

Cheers,

Herman

---

### Post by ctyc on 2008-03-23
does the ptr record resolve correctly?

---

### Post by dantheman3212 on 2008-03-24
As far as I can tell everything seems to be correct on my dns side. How do I test if the PTR is resolving? I'm new to setting up DNS and mail servers in general, and I'm just kind of winging it. Everythings working fine, its just this SMTP thing is the last hurdle over a decent server set up.

---

### Post by Mr. C. on 2008-03-25
```
$ host ip_address
$ dig -x ip_address    
```

---

### Post by Tavorisch on 2008-03-26
```

;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 45055
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 2, ADDITIONAL: 2

;; QUESTION SECTION:
;71.5.117.24.in-addr.arpa.      IN      PTR

;; ANSWER SECTION:
71.5.117.24.in-addr.arpa. 84756 IN      PTR     24-117-5-71.cpe.cableone.net.

;; AUTHORITY SECTION:
117.24.in-addr.arpa.    5530    IN      NS      ns2.cableone.net.
117.24.in-addr.arpa.    5530    IN      NS      ns1.cableone.net.

;; ADDITIONAL SECTION:
ns1.cableone.net.       1457    IN      A       24.116.0.201
ns2.cableone.net.       1457    IN      A       24.116.0.202

;; Query time: 24 msec
;; SERVER: 24.116.2.50#53(24.116.2.50)
;; WHEN: Tue Mar 25 23:08:37 2008
;; MSG SIZE  rcvd: 152

```


thats the result of dig -x 24.117.5.71

---

### Post by Mr. C. on 2008-03-26
The PTR is 24-117-5-71.cpe.cableone.net, which can be seen in the ANSWER section:
```

71.5.117.24.in-addr.arpa. 84756 IN      PTR     24-117-5-71.cpe.cableone.net.

```

So the question is, does that PTR match the A record of the mail host?

---

### Post by dantheman3212 on 2008-03-27
Okay here is all my IN A in my ptxsolutions.com.db

```

ptxsolutions.com. IN SOA ptxserver.ptxsolutions.com. admin.ptxsolutions.com. (

2006081401
28800
3600
604800
38400 )

ptxsolutions.com. IN NS ptxserver.ptxsolutions.com.
mail.ptxsolutions.com. IN MX 10 mail.ptxsolutions.com.


ptxsolutions.com IN A 24.117.5.71
www IN A 24.117.5.71
ns1 IN A 24.117.5.71
@ IN A 24.117.5.71
mail IN A 24.117.5.71

```

all of them resolve, ptxsolutions.com, mail, www, all working, did have a jumble with postfix! reinstalled everything backup and running again.

---

