---
title: "Ubuntu Update Servers IP Addresses"
date: 2010-03-22
forum: Security
---

### Post by debianfan on 2010-03-22
Hi,

  Does anyone know the ubuntu update servers ip addresses.  I am trying to fine tune my firewall rules and was unsure of what ip addresses to use for the update servers.

  I believe they are us.archive.ubuntu.com and security.ubuntu.com.  However, I could be wrong.

  Thanks for any help you can provide.

---

### Post by l.billon on 2010-03-22
Hi!
Maybe
```
cat /etc/apt/sources.list
```
can help

---

### Post by cdenley on 2010-03-22
You cannot assume that the IP address those domains resolve to will always be the same.

---

### Post by doas777 on 2010-03-22
not really a great plan as the dns will likely change based on time and locality, but you can find the info you need by looking at your sources, and then performing a nslookup or dig on the server

hree is a dig
```
karmic:~/Downloads/skipfish$ dig www.ubuntuforums.org

; <<>> DiG 9.6.1-P2 <<>> www.ubuntuforums.org
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 56766
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 3, ADDITIONAL: 3

;; QUESTION SECTION:
;www.ubuntuforums.org.        IN    A

;; ANSWER SECTION:
www.ubuntuforums.org.    600    IN    A    91.189.94.12

;; AUTHORITY SECTION:
ubuntuforums.org.    52988    IN    NS    ns2.canonical.com.
ubuntuforums.org.    52988    IN    NS    ns3.canonical.com.
ubuntuforums.org.    52988    IN    NS    ns1.canonical.com.

;; ADDITIONAL SECTION:
ns1.canonical.com.    82215    IN    A    91.189.94.173
ns2.canonical.com.    82215    IN    A    91.189.94.219
ns3.canonical.com.    82215    IN    A    209.6.3.210

;; Query time: 36 msec
;; SERVER: 10.88.2.10#53(10.88.2.10)
;; WHEN: Mon Mar 22 16:54:09 2010
;; MSG SIZE  rcvd: 169


```

or an nslookup
```

karmic:~/Downloads/skipfish$ nslookup www.ubuntuforums.org
Server:        10.88.2.10
Address:    10.88.2.10#53

Non-authoritative answer:
Name:    www.ubuntuforums.org
Address: 91.189.94.12

```

---

