---
title: "BIND9 and DIG timeouts"
date: 2009-04-15
forum: Server Platforms
---

### Post by almogaver on 2009-04-15
I am having some problems with a BIND9 server.
I have Ubuntu 8.10 server in a VmWare machine, bridged network.
I have installed Bind9 and it is up to date.
I have a simple configuration with a local domain. I have run all tests on my DNS config and eveyting seems fine.
I have disabled the forwarders {} option.
My concern is that when I use Dig to query some external name, it times out very often. At some point it seems to get the full record and future queries are answered very fast (I assume they are cached).
My question is: could it be because Root servers are too busy to be queried directly?

Here is a typical request and the responses I get:

```
root@svr3:~# dig ubuntu.com

; <<>> DiG 9.5.0-P2 <<>> ubuntu.com
;; global options:  printcmd
;; connection timed out; no servers could be reached
root@svr3:~# dig ubuntu.com

; <<>> DiG 9.5.0-P2 <<>> ubuntu.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 24684
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;ubuntu.com.                    IN      A

;; Query time: 245 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Wed Apr 15 15:05:28 2009
;; MSG SIZE  rcvd: 28

root@svr3:~# dig ubuntu.com

; <<>> DiG 9.5.0-P2 <<>> ubuntu.com
;; global options:  printcmd
;; connection timed out; no servers could be reached
root@svr3:~# dig ubuntu.com

; <<>> DiG 9.5.0-P2 <<>> ubuntu.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 26530
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 3, ADDITIONAL: 0

;; QUESTION SECTION:
;ubuntu.com.                    IN      A

;; ANSWER SECTION:
ubuntu.com.             600     IN      A       91.189.94.156

;; AUTHORITY SECTION:
ubuntu.com.             170410  IN      NS      ns1.canonical.com.
ubuntu.com.             170410  IN      NS      ns3.canonical.com.
ubuntu.com.             170410  IN      NS      ns2.canonical.com.

;; Query time: 56 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Wed Apr 15 15:06:54 2009
;; MSG SIZE  rcvd: 108

```

---

