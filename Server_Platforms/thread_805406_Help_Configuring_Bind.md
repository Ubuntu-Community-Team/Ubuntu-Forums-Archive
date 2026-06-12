---
title: "Help Configuring Bind"
date: 2008-05-23
forum: Server Platforms
---

### Post by oxsyn on 2008-05-23
Please, please help.  I can't figure out what I'm doing wrong.

My domain is nathanfarrar.com, it's registered with godaddy.  With godaddy, I bound ns1.nathanfarrar.com to my home IP address.  Port 53 is forwarded on my home router to this server.

**named.conf.local**
> 
//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

# Zone definition for nathanfarrar.com
zone "nathanfarrar.com" {
        type master;
        file "/etc/bind/zones/nathanfarrar.com.db";
};

# Zone definition for reverse dns.
# IP is reverse (i.e. 192.168.1.x = 1.168.192.in-addr.arpa)
zone "1.168.192.in-addr.arpa" {
        type master;
        file "/etc/bind/zones/rev.1.168.192.in-addr.arpa";
};

**nathanfarrar.com.db zone file**
> ;
; Zone File for nathanfarrar.com
;

$TTL 3h
nathanfarrar.com.               IN      SOA             ns1.nathanfarrar.com. (

                                                1                       ; Serial
                                                1h                      ; Refres
h
                                                1h                      ; Retry
                                                1w                      ; Expire
                                                1h                      ; Negati
ve Cache TTL

)

;
; Name Servers
;

nathanfarrar.com.               IN      NS              ns1.nathanfarrar.com.

;
; Hosts
;

localhost.nathanfarrar.com.     IN      A               127.0.0.1               ; localhost definition
[www.nathanfarrar.com](www.nathanfarrar.com).           IN      A               192.168.1.20            ; www

**rev.1.168.192.in-addr.arpa**
> 
//replace example.com with yoour domain name, ns1 with your DNS server name.
// The number before IN PTR example.com is the machine address of the DNS server. in my case, it's 1, as my IP address is 192.168.0.1.

$TTL 3h
1.168.192.in-addr.arpa.         IN      SOA             ns1.nathanfarrar.com. (

                                                        1               ; Serial
                                                        1h              ; Refresh
                                                        1h              ; Retry
                                                        1w              ; Expire
                                                        1h              ; Negative Cache TTL
)

;
; Name Servers
;

1.168.192.in-addr.arpa.         IN      NS              ns1.nathanfarrar.com.

;
; Hosts
;

20.1.168.192.in-addr.arpa.      IN      PTR             [www.nathanfarrar.com](www.nathanfarrar.com).

When I try to dig my domain (dig nathanfarrar.com),I get the following result:
> f4rr4r@Hawking:/etc/bind/zones$ dig nathanfarrar.com

; <<>> DiG 9.4.2 <<>> nathanfarrar.com
;; global options:  printcmd
;; Got answer:
**;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 65151**
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;nathanfarrar.com.              IN      A

;; Query time: 0 msec
;; SERVER: 192.168.1.20#53(192.168.1.20)
;; WHEN: Sat May 24 11:18:49 2008
;; MSG SIZE  rcvd: 34

When I try to ping nathanfarrar.com, I see:
> f4rr4r@Hawking:/etc/bind/zones$ ping nathanfarrar.com
ping: unknown host nathanfarrar.com

When I try to ping ns1.nathanfarrar.com, I see:
> f4rr4r@Hawking:/etc/bind/zones$ ping ns1.nathanfarrar.com
ping: unknown host ns1.nathanfarrar.com

Please help!

---

### Post by oxsyn on 2008-05-24
I'm dying, please help!  I've been working on this for nearly a week!

---

