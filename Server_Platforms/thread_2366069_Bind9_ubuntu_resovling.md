---
title: "Bind9 ubuntu resovling"
date: 2017-07-13
forum: Server Platforms
---

### Post by mmancina on 2017-07-13
Hi guys, I installed bind9 on my Ubuntu 16.04 machine.

But I've problems with resolving local domains. Extern like google.com works fine.

Here are my configuraton files and troubleshoots i've made.

Forward:
```

$TTL 2D
@       IN      SOA     localhost.mancina.home. root.mancina.home. (
                        22      ; Serial
                                8H      ; Refresh
                                2H      ; Retry
                                4W      ; Expire
                                3H ) 
@    IN    NS    localhost.mancina.home.
    IN    A    192.168.1.150

lenny    IN    A    192.168.1.150
homer    IN    A    192.168.1.110


```

Reverse

```

root@lenny:/etc/bind# cat db.mancina.home 
$TTL 2D
@       IN      SOA     localhost.mancina.home. root.mancina.home. (
                        22      ; Serial
                                8H      ; Refresh
                                2H      ; Retry
                                4W      ; Expire
                                3H ) 
@    IN    NS    localhost.mancina.home.
    IN    A    192.168.1.150

lenny    IN    A    192.168.1.150
homer    IN    A    192.168.1.110

root@lenny:/etc/bind# cat db.1.168.192 
$TTL 2D
@       IN      SOA     localhost.mancina.home. root.mancina.home. (
                        2      ; Serial
                                8H      ; Refresh
                                2H      ; Retry
                                4W      ; Expire
                                3H )

@       IN      NS      localhost.mancina.home.
150    IN    PTR    lenny.mancina.home.
110    IN    PTR    homer.mancina.home.


```

named.conf,local

```
root@lenny:/etc/bind# cat named.conf.local 
//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";
logging {
    channel query.log {      
        file "/var/log/query.log"; 
        severity info;
    print-time yes;
        print-severity yes;
        print-category yes; 
    }; 
    category queries { query.log; }; 
};


```

named.local.conf

```
zone "mancina.home" {
type master;
file "/etc/bind/db.mancina.home";
};

zone "1.168.192.in-addr.arpa" {
type master;
file "/etc/bind/db.1.168.192";
};


```

named.conf.options

```
root@lenny:/etc/bind# cat named.conf.options 
options {
    directory "/var/cache/bind";
     forwarders {
         8.8.8.8    ;
     };
    dnssec-validation auto;

    auth-nxdomain no;    # conform to RFC1035
    listen-on-v6 { any; };
};


```

```
root@lenny:/etc/bind# named-checkzone db.mancina.home ./db.mancina.home 
zone db.mancina.home/IN: loaded serial 22
OK


```

```
root@lenny:/etc/bind# dig lenny.home.local.

; <<>> DiG 9.10.3-P4-Ubuntu <<>> lenny.home.local.
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 40661
;; flags: qr rd ra ad; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
;; QUESTION SECTION:
;lenny.home.local.        IN    A

;; AUTHORITY SECTION:
.            10800    IN    SOA    a.root-servers.net. nstld.verisign-grs.com. 2017071301 1800 900 604800 86400

;; Query time: 33 msec
;; SERVER: 192.168.1.150#53(192.168.1.150)
;; WHEN: Thu Jul 13 20:12:13 CEST 2017
;; MSG SIZE  rcvd: 120



```

```
root@lenny:/etc/bind# nslookup lenny.home.local
Server:        192.168.1.150
Address:    192.168.1.150#53

** server can't find lenny.home.local: NXDOMAIN



```

```
root@lenny:/etc/bind# nslookup google.com
Server:        192.168.1.150
Address:    192.168.1.150#53

Non-authoritative answer:
Name:    google.com
Address: 216.58.205.110



```


I hope anyone can see an error in the conf or give me an advice what could be wrong.

TIA
Mattia

---

### Post by Doug S on 2017-07-14
Yes, you have several things incorrect in your configuration files. Please have a look at the relevant section of the Ubuntu [Serverguide]("https://help.ubuntu.com/lts/serverguide/dns.html").
I do not know why you are trying to lookup "lenny.home.local" when you have defined (sort of) "mancina.home". You should be trying to lookup "lenny.mancina.home".

It'll take me about an hour to write a proper reply, but I can only do that later today, if nobody else does so first.

EDIT: I see you have not been back here, so no use wasting the time to write a proper reply.

---

