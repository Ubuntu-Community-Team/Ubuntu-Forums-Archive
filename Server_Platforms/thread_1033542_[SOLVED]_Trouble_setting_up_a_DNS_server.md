---
title: "[SOLVED] Trouble setting up a DNS server"
date: 2009-01-07
forum: Server Platforms
---

### Post by harrybazeegar on 2009-01-07
Hi

I am using Ubuntu 7.10 Desktop Edition, but I pretty much use it as a server too (apache, mysql, memcached). Now I tried to install DNS on my computer, and I just can't understand what's going wrong.

First things first: My computer lives in a 10.8.40.0/9 subnet. My own IP is 10.8.41.1

I tried to set up the "example.com" zone on my computer EXACTLY as demonstrated in [http://doc.ubuntu.com/ubuntu/serverguide/C/dns-configuration.html](http://doc.ubuntu.com/ubuntu/serverguide/C/dns-configuration.html) , except that I replaced 192.168.1.10 with 10.8.41.1, and replaced "1.168.192.in-addr.arpa" with "40.8.10.in-addr.arpa".

so ns.example.com. became 10.8.41.1



After editing the zone files I removed all other nameservers from /etc/resolv.conf so it just read "nameserver 10.8.41.1".

now I did this:
1. "ping localhost" -> success
2. "ping 10.8.41.1" -> success
3. "dig -x 10.8.41.1" -> output here:

```

; <<>> DiG 9.4.2-P2 <<>> -x 10.8.41.1
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 12919
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;1.41.8.10.in-addr.arpa.                IN      PTR

;; ANSWER SECTION:
1.41.8.10.in-addr.arpa. 604800  IN      PTR     ns.exapmle.com.

;; AUTHORITY SECTION:
41.8.10.in-addr.arpa.   604800  IN      NS      ns.

;; Query time: 0 msec
;; SERVER: 10.8.41.1#53(10.8.41.1)
;; WHEN: Wed Jan  7 23:48:00 2009
;; MSG SIZE  rcvd: 84

```

4. "dig @10.8.41.1 ns.example.com A" -> output here: (!)

```

; <<>> DiG 9.4.2-P2 <<>> @10.8.41.1 ns.example.com A
; (1 server found)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 14520
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;ns.example.com.                        IN      A

```

why did this happen? the zone file specifically contains A records for ns.example.com. in the example.com. zone:
contents of db.example.com:
```

$TTL    604800
@       IN      SOA     ns.example.com. root.example.com. (
                              1         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                          86400 )       ; Negative Cache TTL
;
@       IN      NS      ns.example.com.
@       IN      A       10.8.41.1
ns      IN      A       10.8.41.1

``` 

could somebody please explain what is happenning? how do I make my dns server work?

---

### Post by harrybazeegar on 2009-01-08
Okay, I solved this somehow.

I don't really know how though.

---

