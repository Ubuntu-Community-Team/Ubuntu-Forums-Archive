---
title: "Postfix sending mail problem"
date: 2013-02-19
forum: Server Platforms
---

### Post by Elnison on 2013-02-19
hey guys pls help I can't send email I get this error in /var/log/mail.log
```
Feb 19 15:56:30 mail postfix/smtp[26674]: 3F557B802A3: to=<elnison@gmail.com>,
 relay=smtpdsl4.pldtdsl.net[210.213.253.193]:587, delay=1.6, delays=1.2/0.01/0.27/0.07, dsn=5.0.0, 
status=bounced (host smtpdsl4.pldtdsl.net[210.213.253.193] said: 553 #5.1.8 Domain of sender address <elnison@domain.com> 
does not exist (in reply to MAIL FROM command))

``` 
I've read some guide saying that it has DNS problem but when I check this with dig mx domain.com I've already have a mx record but i still get this error.
```
; <<>> DiG 9.8.1-P1 <<>> mx domain.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 60108
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 2, ADDITIONAL: 2

;; QUESTION SECTION:
;domain.com.                     IN      MX

;; ANSWER SECTION:
domain.com.              3600    IN      MX      10 mail.domain.com.

;; AUTHORITY SECTION:
domain.com.              3600    IN      NS      ns04.domaincontrol.com.
domain.com.              3600    IN      NS      ns03.domaincontrol.com.

;; ADDITIONAL SECTION:
ns03.domaincontrol.com. 85741   IN      A       216.69.185.2
ns04.domaincontrol.com. 85741   IN      A       208.109.255.2

;; Query time: 3614 msec
;; SERVER: 192.168.0.1#53(192.168.0.1)
;; WHEN: Tue Feb 19 15:53:21 2013
;; MSG SIZE  rcvd: 132


```

---

### Post by linuxtechguy on 2013-02-19
Is the domain actually real? Posting fake information doesnt help anyone.

---

### Post by Elnison on 2013-02-19
yes it is real i just edited the domain name. I bought the domain at godaddy.com

---

### Post by Elnison on 2013-02-19
here's the real dig mx
```
; <<>> DiG 9.8.1-P1 <<>> mx hmd-c.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 4441
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 2, ADDITIONAL: 4

;; QUESTION SECTION:
;hmd-c.com.                     IN      MX

;; ANSWER SECTION:
hmd-c.com.              3599    IN      MX      10 mail.hmd-c.com.

;; AUTHORITY SECTION:
hmd-c.com.              3599    IN      NS      ns04.domaincontrol.com.
hmd-c.com.              3599    IN      NS      ns03.domaincontrol.com.

;; ADDITIONAL SECTION:
mail.hmd-c.com.         172798  IN      A       112.202.181.190
ns03.domaincontrol.com. 134897  IN      A       216.69.185.2
ns04.domaincontrol.com. 6559    IN      A       208.109.255.2
ns04.domaincontrol.com. 66973   IN      AAAA    2607:f208:302::2

;; Query time: 50 msec
;; SERVER: 192.168.0.1#53(192.168.0.1)
;; WHEN: Wed Feb 20 08:32:56 2013
;; MSG SIZE  rcvd: 176

```

---

### Post by Elnison on 2013-02-22
up!

---

### Post by lisati on 2013-02-22
You might need to define an "A" record for mail.hmd-c.com that points to the proper server.

---

### Post by Elnison on 2013-02-24
hi thanks for the reply

where will I point the A record for mail.hmd-c.com? In my own IP address or in the godaddy?

---

### Post by d4m1r on 2013-02-25
> **Elnison said:**
> hi thanks for the reply

where will I point the A record for mail.hmd-c.com? In my own IP address or in the godaddy?


You create the A record where ever your DNS is hosted.

---

