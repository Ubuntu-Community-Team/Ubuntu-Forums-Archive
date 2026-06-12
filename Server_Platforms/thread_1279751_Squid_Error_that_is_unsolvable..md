---
title: "Squid Error that is unsolvable."
date: 2009-10-01
forum: Server Platforms
---

### Post by blindmist on 2009-10-01
I have had this problem for a few years now and I just cannot figure out how to solve this.

The page that I get is this page
[http://jslaydesign.net/squiderror.html](http://jslaydesign.net/squiderror.html)

Open to any suggestions.

---

### Post by shizzy-t on 2009-10-01
If you log into the box that squids running on and run a 

*# dig [www.google.com](www.google.com) *

What happens?  Maybe /etc/resolv.conf isn't setup correctly.

---

### Post by blindmist on 2009-10-01
I changed the cache_mem for 8M to 64M and I have been waiting for it to fail and crash again.

I don't think this is a DNS problem because I can still access the web server and I can still get the server to download torrents.

Although, there are times where I lose connectivity on the "Main" ethernet card and have to gain access to the server through the backup card. When I do ifdown eth3 and let it sit for about 5 minutes and then ifup it comes back on line. I think it is a dupluxing issue which I will never get worked out because I don't think the problem is with my hardware, I think it is with the ISP

```

justin@sfhs:~$ dig google.com

; <<>> DiG 9.4.2-P2 <<>> google.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 49615
;; flags: qr rd ra; QUERY: 1, ANSWER: 3, AUTHORITY: 4, ADDITIONAL: 4

;; QUESTION SECTION:
;google.com.                    IN      A

;; ANSWER SECTION:
google.com.             292     IN      A       74.125.67.100
google.com.             292     IN      A       74.125.127.100
google.com.             292     IN      A       74.125.45.100

;; AUTHORITY SECTION:
google.com.             91240   IN      NS      ns3.google.com.
google.com.             91240   IN      NS      ns2.google.com.
google.com.             91240   IN      NS      ns4.google.com.
google.com.             91240   IN      NS      ns1.google.com.

;; ADDITIONAL SECTION:
ns1.google.com.         85269   IN      A       216.239.32.10
ns2.google.com.         85270   IN      A       216.239.34.10
ns3.google.com.         85269   IN      A       216.239.36.10
ns4.google.com.         85269   IN      A       216.239.38.10

;; Query time: 34 msec
;; SERVER: 216.167.161.35#53(216.167.161.35)
;; WHEN: Thu Oct  1 15:01:06 2009
;; MSG SIZE  rcvd: 212

```

resolv.conf
```

justin@sfhs:~$ sudo vim /etc/resolv.conf
nameserver  216.167.161.35
nameserver  216.167.161.36

```

EDIT:

Just got it to crash and got this.

```

dig google.com

; <<>> DiG 9.4.2-P2 <<>> google.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: REFUSED, id: 33938
;; flags: qr rd; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0
;; WARNING: recursion requested but not available

;; QUESTION SECTION:
;google.com.                    IN      A

;; Query time: 243 msec
;; SERVER: 216.167.161.35#53(216.167.161.35)
;; WHEN: Thu Oct  1 15:30:16 2009
;; MSG SIZE  rcvd: 28

```

---

### Post by blindmist on 2009-10-02
bump it up

---

### Post by blindmist on 2009-10-06
bump bump

---

### Post by dragos2 on 2009-10-06
That is a DNS erorr.

Maybe the dns server refused to solve the domains for you, maybe squid
asks solving too many domains at a time and it gets blocked.

Who own's the dns servers ?

---

