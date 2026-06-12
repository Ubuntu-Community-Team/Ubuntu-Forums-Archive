---
title: "I installed BIND9 right! but ping doesnt work!"
date: 2011-01-01
forum: Server Platforms
---

### Post by ansary on 2011-01-01
hello guys i have a problem with my BIND9 installation please see my output below!

I know that my BIND9 is already working properly! but when i ping the domain name, it doesnt work!


-----------------------------------------------------------------------------
Microsoft Windows [Version 6.1.7600]
Copyright (c) 2009 Microsoft Corporation.  All rights reserved.

C:\Users\mydeskop>nslookup cool-ansary.com
Server:  cool-ansary.com
Address:  192.168.1.50

Name:    cool-ansary.com


C:\Users\mydeskop>

C:\Users\mydeskop>ping cool-ansary.com
Ping request could not find host cool-ansary.com. Please check the name and try
again.

C:\Users\mydeskop>

-------------------------------------------------------------------------------

---

### Post by jgedeon on 2011-01-01
On the windows computer try to flush the dns cache then retry the ping.

ipconfig /flushdns

---

### Post by James78 on 2011-01-02
I get no reply when I query for the domain. So it's likely that one of these is the problem:

DNS isn't setup properly somewhere along the line.
- Your DNS server isn't setup properly.
- is your domain provider pointing properly at you?
If this is a new domain you just made, sometimes you need to wait a few hours or a few days for the DNS to propagate and work before you can do more testing out to make sure everything works.

```
toonarmy@opti-hacker:~$ dig cool-ansary.com

; <<>> DiG 9.7.1-P2 <<>> cool-ansary.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 21428
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;cool-ansary.com.               IN      A

;; AUTHORITY SECTION:
com.                    900     IN      SOA     a.gtld-servers.net. nstld.verisign-grs.com. 1293950054 1800 900 604800 86400

;; Query time: 184 msec
;; SERVER: 192.168.1.120#53(192.168.1.120)
;; WHEN: Sat Jan  1 22:34:54 2011
;; MSG SIZE  rcvd: 106
```

---

### Post by woodman231 on 2011-01-03
Since you set it up as a DNS server for Windows did you specify your DNS Server in your TCP/IP properties for this DNS server that you just setup?

It is possibly that port 53 on your DNS (Ubuntu) server is blocked, perhaps try:

```

sudo ufw 53 allow

```

Thanks,
Sean W.

---

