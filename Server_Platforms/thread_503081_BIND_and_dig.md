---
title: "BIND and dig"
date: 2007-07-17
forum: Server Platforms
---

### Post by WeyOh on 2007-07-17
Hi,

I'm trying to set up bind on a local server but I'm having trouble interpreting the results that dig gives me.
```
admin@server:~$ dig casa.rm

; <<>> DiG 9.3.2 <<>> casa.rm
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 14806
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;casa.rm.                       IN      A

;; AUTHORITY SECTION:
.                       10799   IN      SOA     a.root-servers.net. nstld.verisign-grs.com. 2007071601 1800 900 604800 86400

;; Query time: 57 msec
;; SERVER: 212.76.224.172#53(212.76.224.172)
;; WHEN: Tue Jul 17 18:28:27 2007
;; MSG SIZE  rcvd: 100

```

Especially concerning the server line, is that the ip address of the dns server that provided these results?

---

### Post by koenn on 2007-07-17
> **WeyOh said:**
> Especially concerning the server line, is that the ip address of the dns server that provided these results? yes.

And the rest looks to me that casa.rm could not be resolved so you get a reference to a root.server

---

### Post by Mr. C. on 2007-07-17
Understanding dig's output requires a bit of understanding the resolver process.

Applications ask the resolver to perform a lookup.  That query is shown in the QUESTION section of dig's output.  dig will then provide you with as much information as it can in the ANSWER section; in this case, the domain was unresolvable, and the root server's were the last server's queried that could give an authoritative answer for the query.  Since there is no ".rm"  domain under the root, you get no authoritative response.

The data at the end of the dig output is diagnostic, indicating how long the query took, and which server's were used.

If you are setting up your own bind server, query it by specifying that server to your dig queries:

dig @mybindserver casa.rm

MrC

---

