---
title: "uping own BIND9 DNS server and setting up subdomain"
date: 2011-08-22
forum: Server Platforms
---

### Post by Farrukhjon on 2011-08-22
Hi guys, I have up my DNS Serevr BIND9. My hostname ns1 in /etc/hosts->mydomain.org. I have three real IP addresses. and i want up sub-domain for each ip: mydomain.org, news.mydomain.org, forum.mydomain.org. My db bind record are: 
$ORIGIN mydomain.org.
$ttl 38400
mydomain.org.       IN      SOA     mydomain.org. root.mydomain.org. (
                        1313235295
                        10800
                        3600
                        604800
                        38400 )

mydomain.org.       IN      NS      ns1.mydomain.org.
mydomain.org.       IN      MX      10 mail.mydomain.org.
mydomain.org.       IN      PTR     news.mydomain.org.
mydomain.org.       IN      PTR     forum.mydomain.org.
mydomain.org.       IN      PTR     tahsil.mydomain.org.
mydomain.org.       IN      A       xxx.xxx.xxx.1
www             IN      CNAME   mydomain.org.
ns1             IN      A       xxx.xxx.xxx.1
mail            IN      A       xxx.xxx.xxx.1
news.mydomain.org.  IN      A   xxx.xxx.xxx.2
forum.mydomain.org. IN      A   xxx.xxx.xxx.3
tahsil          IN      A       xxx.xxx.xxx.1

how these records are correct ???

root@ns1:/var/lib/bind# dig mydomain.org

; <<>> DiG 9.7.0-P1 <<>> mydomain.org
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 626
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 1

;; QUESTION SECTION:
;mydomain.org.                      IN      A

;; ANSWER SECTION:
mydomain.org.               38400   IN      A       xxx.xxx.xxx.1

;; AUTHORITY SECTION:
mydomain.org.               38400   IN      NS      ns1.mydomain.org.

;; ADDITIONAL SECTION:
ns1.mydomain.org.           38400   IN      A       xxx.xxx.xxx.1

;; Query time: 0 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Mon Aug 22 14:38:32 2011
;; MSG SIZE  rcvd: 76

and there is not enough to fully configure DNS servers ???
Thanks an advance?

---

### Post by Sanados on 2011-08-22
www IN CNAME mydomain.org.

always make www an A record, if just for the sake of google :)


you did set up the right mx record. :) most ppl use a ip address there.



mydomain.org. IN PTR news.mydomain.org.
mydomain.org. IN PTR forum.mydomain.org.
mydomain.org. IN PTR tahsil.mydomain.org.
are wrong imo.
Reverse DNS (PTR) resolve an ip to a name

should sound like:
2 IN PTR news.mydomain.org.
3 IN PTR forum.mydomain.org.
1 IN PTR tahsil.mydomain.org.



also ptr should be split from the other records in different files


zone "mydomain.org" in {
        type master;
        file "/etc/bind/mydomain.org.hosts";
        };

#use real first 3 parts from your ip
zone "10.10.10.in-addr.arpa" in {
        type master;
        file "/etc/bind/db.10.10.10";
        };

---

