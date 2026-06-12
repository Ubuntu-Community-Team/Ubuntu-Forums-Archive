---
title: "Bind9 DNS with multidomain issues"
date: 2010-04-09
forum: Server Platforms
---

### Post by nyu2007 on 2010-04-09
Dear All,



I have an issues with my DNS Server (Bind9)

I have 03 domain, I want to host on one DNS server



1. A.COM

2. B.COM

3. C.COM



Hostname of DNS Server: ns.example.com

IP: 192.168.0.1



This is my config file

I add 3 zone on named.conf.local





```
......

zone "a.com" {

   type master;

   file "/etc/bind/db.a.com";

};



zone "b.com" {

   type master;

   file "/etc/bind/db.b.com";

};



zone "c.com" {

   type master;

   file "/etc/bind/db.c.com";

};

.....
```



db.a.com

```
$TTL 604800

@       IN      SOA     ns.example.com.        admin.example.com. (

                        070725  ;

                        604800  ;

                        86400   ;

                        2419200 ;

                        604800 )

;

@           IN      NS      ns.example.com.

            IN      MX      10      mail.a.com.

ns          IN      A       192.168.0.1



mail.a.com  IN      A       192.168.0.1
```







db.b.com

```
$TTL 604800

@       IN      SOA     ns.example.com.        admin.example.com. (

                        070725  ;

                        604800  ;

                        86400   ;

                        2419200 ;

                        604800 )

;

@           IN      NS      ns.example.com.

            IN      MX      10      mail.b.com.

ns          IN      A       192.168.0.1



mail.b.com  IN      A       192.168.0.1
```





db.c.com

```
$TTL 604800

@       IN      SOA     ns.example.com.        admin.example.com. (

                        070725  ;

                        604800  ;

                        86400   ;

                        2419200 ;

                        604800 )

;

@           IN      NS      ns.example.com.

            IN      MX      10      mail.c.com.

ns          IN      A       192.168.0.1



mail.c.com  IN      A       192.168.0.1
```



Edit resolv.conf 

nameserver 192.168.0.1

Now I can dig mx to 3 domain 

```


; <<>> DiG 9.4.2-P2.1 <<>> mx a.com

;; global options:  printcmd

;; Got answer:

;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 27687

;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 0



;; QUESTION SECTION:

;a.com.		IN	MX



;; ANSWER SECTION:

a.com.	604800	IN	MX	10 mail.a.com.



;; AUTHORITY SECTION:

a.com.	604800	IN	NS	ns.example.com.



;; Query time: 1 msec

;; SERVER: 192.168.0.1#53(192.168.0.1)

;; WHEN: Wed Apr  7 12:46:15 2010

;; MSG SIZE  rcvd: 82


```





```


; <<>> DiG 9.4.2-P2.1 <<>> mx b.com

;; global options:  printcmd

;; Got answer:

;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 27687

;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 0



;; QUESTION SECTION:

;b.com.		IN	MX



;; ANSWER SECTION:

b.com.	604800	IN	MX	10 mail.b.com.



;; AUTHORITY SECTION:

b.com.	604800	IN	NS	ns.example.com.



;; Query time: 1 msec

;; SERVER: 192.168.0.1#53(192.168.0.1)

;; WHEN: Wed Apr  7 12:46:15 2010

;; MSG SIZE  rcvd: 82


```







```
; <<>> DiG 9.4.2-P2.1 <<>> mx c.com

;; global options:  printcmd

;; Got answer:

;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 27687

;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 0



;; QUESTION SECTION:

;c.com.		IN	MX



;; ANSWER SECTION:

c.com.	604800	IN	MX	10 mail.c.com.



;; AUTHORITY SECTION:

c.com.	604800	IN	NS	ns.example.com.



;; Query time: 1 msec

;; SERVER: 192.168.0.1#53(192.168.0.1)

;; WHEN: Wed Apr  7 12:46:15 2010

;; MSG SIZE  rcvd: 82
```





BUT I can ping to any alias of 3 domain mail

mail.a.com

mail.b.com

mail.c.com



Help me!!!!



Regards,

NyU

---

### Post by Bachstelze on 2010-04-09
It's better to explicitly define the $ORIGIN of your zones, for example:

```
$ORIGIN .
$TTL 604800

a.com.       IN      SOA     ns.example.com.        admin.example.com. (
                        070725  ;
                        604800  ;
                        86400   ;
                        2419200 ;
                        604800 )
;

            IN      NS      ns.example.com.

            IN      MX      10      mail.a.com.

$ORIGIN a.com.
ns          IN      A       192.168.0.1
mail        IN      A       192.168.0.1
```

With this zone file, it should work. The problem you have with your current one is that [font=monospace]mail.a.com[/font] is not dot-terminated, and is therefore interpreted relative to the ORIGIN. Since you didn't specify an ORIGIN, it defaults to the zone name (i.e. [font=monospace]a.com[/font]), and [font=monospace]mail.a.com[/font] is interpreted as [font=monospace]mail.a.com.a.com.[/font].

---

### Post by nyu2007 on 2010-04-09
Many many thanks Bachstelze
Now my issues was SOLVED

---

