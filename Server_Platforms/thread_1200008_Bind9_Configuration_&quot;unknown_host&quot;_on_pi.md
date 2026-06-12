---
title: "Bind9 Configuration: &quot;unknown host&quot; on ping"
date: 2009-06-29
forum: Server Platforms
---

### Post by lightnb on 2009-06-29
I have two JEOS Virtual Machines, running Ubuntu 9.04:

One is a web-server with MediaWiki, the other is a DNS server running Bind9.

I set-up DNS following the official Ubuntu server documentation.
When I ping "mywiki.com" from the NameServer machine, I get:
```
ping: unknown host mywiki.com
``` Pinging other sites like google.com works just fine. 


dig mywiki.com:
```

; <<>> DiG 9.5.1-P2 <<>> mywiki.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 24809
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;mywiki.com.			IN	A

;; Query time: 0 msec
;; SERVER: 192.168.5.131#53(192.168.5.131)
;; WHEN: Mon Jun 29 15:40:15 2009
;; MSG SIZE  rcvd: 28

```


 /etc/bind/named.conf.local:
```
// A zone for our WikiMedia Server
zone "mywiki.com" {
        type master;
        file "/etc/bind/db.mywiki.com";
        };


// Reverse Lookup Zone
zone "5.168.192.in-addr.arpa" {
        type master;
        notify no;
        file "/etc/bind/db.192";
        };

```

/etc/bind/db.mywiki.com:
```

;
        ; BIND data file for the WikiMedia Wiki at mywiki.com
        ;
        $TTL    604800
        @       IN      SOA     mywiki.com. root.mywiki.com. (
                                      4         ; Serial
                                 604800         ; Refresh
                                  86400         ; Retry
                                2419200         ; Expire
                                 604800 )       ; Negative Cache TTL
        ;
        @       IN      NS      mywiki.com.
        @       IN      A       192.168.5.102
        ns      IN      A       192.168.5.102


```

Any ideas what I'm missing?

Thanks,

Nick

---

### Post by jhannah on 2009-06-30
What exactly is at 192.168.5.131 providing the empty DNS responses? I would recommend you try adding '@127.0.0.1' to your dig command and see if you get the expected responses by running that directly on the bind server.

The results of digging at localhost should tell you if the issue is in bind or if the name server at 192.168.5.131 is giving invalid results for another reason. Anything interesting in your bind logs?

---

### Post by lightnb on 2009-07-01
192.168.5.131 is the IP address of the DNS server in question.

dig mywiki.com@127.0.0.1

```

; <<>> DiG 9.5.1-P2 <<>> mywiki.com@127.0.0.1
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 45480
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;mywiki.com\@127.0.0.1.		IN	A

;; Query time: 111 msec
;; SERVER: 192.168.5.131#53(192.168.5.131)
;; WHEN: Wed Jul  1 08:13:25 2009
;; MSG SIZE  rcvd: 38

```

I looked in /var/log for a Bind9 log file or folder, but couldn't find one...

---

### Post by lightnb on 2009-07-01
Ok, got logging working.

Ping and dig just produce this:

```

client 192.168.5.131#54471: query: mywiki.com IN A +
client 192.168.5.131#41687: query: mywiki.com IN A +
client 192.168.5.131#60652: query: mywiki.com IN A +
client 192.168.5.131#49115: query: mywiki.com IN A +
client 192.168.5.131#39969: query: mywiki.com IN A +

```

---

