---
title: "Bind9 random error problem for some address"
date: 2023-01-03
forum: Server Platforms
---

### Post by secooonder on 2023-01-03
Hi
 i use bind 9.18.1 on Ubuntu 22.04.1.
But i have a problem. 
Some clients have an error while answering their queries.

in queries.log ;
```
03-Jan-2023 15:40:57.342 query-errors: info: client @0x7f2b90004ea0 212.c.a.b#37848 (hclm.allianz.com.tr): view f: query failed (SERVFAIL) for hclm.allianz.com.tr/IN/TYPE65 at query.c:6182
03-Jan-2023 15:43:52.540 query-errors: info: client @0x7f2b6c9dfd00 176.a.b.c#56469 (platform.twitter.com): view f: query failed (timed out) for platform.twitter.com/IN/TYPE65 at query.c:6883
03-Jan-2023 15:44:02.564 query-errors: info: client @0x7f2b6c9dfd00 176.a.b.c#56469 (platform.twitter.com): view f: query failed (timed out) for platform.twitter.com/IN/TYPE65 at query.c:6883
03-Jan-2023 15:48:28.715 query-errors: info: client @0x7f2b64073ba0 192.168.a.b#61932 (webprovizyon.allianz.com.tr): view intranet: query failed (timed out) for webprovizyon.allianz.com.tr/IN/TYPE65 at query.c:6883
03-Jan-2023 15:48:28.935 query-errors: info: client @0x7f2b680365e0 192.168.c.d#52167 (cas.allianz.com.tr): view intranet: query failed (timed out) for cas.allianz.com.tr/IN/TYPE65 at query.c:6883

```

named.conf


```
include "/etc/bind/named.conf.options";
include "/etc/bind/named.conf.local";
//include "/etc/bind/named.conf.default-zones";




logging {


     channel queries_log {
          file "/var/log/named/queries" versions 10 size 40m;
          print-time yes;
          print-category yes;
          print-severity yes;
          severity dynamic;
     };


    channel default_log {
          file "/var/log/named/default" versions 3 size 20m;
          print-time yes;
          print-category yes;
          print-severity yes;
          severity info;
     };


  channel query-errors_log {
          file "/var/log/named/query-errors" versions 3 size 10m;
          print-time yes;
          print-category yes;
          print-severity yes;
          severity dynamic;
     };


category queries        { queries_log; };
category default        { default_debug; };
category query-errors   {query-errors_log; };


};
```

```
acl "trusted" {
             127.0.0.0/8 ;           
             212.c.a.b ;        
            176.a.b.c ;               


     
};




options {
        directory "/var/cache/bind";




            dnssec-validation auto;


            recursion yes;
        allow-recursion { trusted ; };


 forwarders {
              8.8.8.8 ;
              195.175.39.39 ;
              4.2.2.6 ;
 } ;
                 allow-transfer {"none";};
                  version "nooo";


                 
                       empty-zones-enable yes;


                   auth-nxdomain no;    # conform to RFC1035
                   listen-on port 53 { 127.0.0.1 ; 192.168.a.b ; d.c.e.f; };
                   listen-on-v6 { none; };
```

What is the problem ?


Please help me.
King Regards

---

### Post by secooonder on 2023-01-04
Plase Help Me

---

### Post by secooonder on 2023-01-08
[COLOR=#000000]Please Help Me[/COLOR]

---

### Post by Doug S on 2023-01-08
Disclaimer: I do not know much about TYPE65, and only read a little this morning.

Does bind9 even support TYPE65? Do those addresses have TYPE65 records? I don't think so.

```
doug@s19:~/iptables/misc$ dig -t TYPE65 hclm.allianz.com.tr @192.168.111.1

; <<>> DiG 9.16.1-Ubuntu <<>> -t TYPE65 hclm.allianz.com.tr @192.168.111.1
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: [COLOR="#FF0000"]SERVFAIL[/COLOR], id: 62247
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 1232
; COOKIE: c4c6f9b4711aa1f00100000063baf1190ba6de77c205bd22 (good)
;; QUESTION SECTION:
;hclm.allianz.com.tr.           IN      TYPE65

;; Query time: 4 msec
;; SERVER: 192.168.111.1#53(192.168.111.1)
;; WHEN: Sun Jan 08 08:36:41 PST 2023
;; MSG SIZE  rcvd: 76
```

and 

```
doug@s19:~/iptables/misc$ dig -t TYPE65 webprovizyon.allianz.com.tr @192.168.111.1

; <<>> DiG 9.16.1-Ubuntu <<>> -t TYPE65 webprovizyon.allianz.com.tr @192.168.111.1
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: [COLOR="#FF0000"]SERVFAIL[/COLOR], id: 22850
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 1232
; COOKIE: c481b4e75f41856a0100000063bae6ba2d6d4d0061643aa4 (good)
;; QUESTION SECTION:
;webprovizyon.allianz.com.tr.   IN      TYPE65

;; Query time: 3 msec
;; SERVER: 192.168.111.1#53(192.168.111.1)
;; WHEN: Sun Jan 08 07:52:26 PST 2023
;; MSG SIZE  rcvd: 84
```

But, and for example:

```
doug@s19:~/iptables/misc$ dig -t A hclm.allianz.com.tr @192.168.111.1

; <<>> DiG 9.16.1-Ubuntu <<>> -t A hclm.allianz.com.tr @192.168.111.1
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: [COLOR="#FF0000"]NOERROR[/COLOR], id: 16795
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 1232
; COOKIE: 2694d30436230d1e0100000063baf17b45d71b9ad55fbe46 (good)
;; QUESTION SECTION:
;hclm.allianz.com.tr.           IN      A

;; ANSWER SECTION:
hclm.allianz.com.tr.    249     IN      A       85.159.72.222

;; Query time: 0 msec
;; SERVER: 192.168.111.1#53(192.168.111.1)
;; WHEN: Sun Jan 08 08:38:20 PST 2023
;; MSG SIZE  rcvd: 92
```

Edit: deleted, it was wrong.

---

