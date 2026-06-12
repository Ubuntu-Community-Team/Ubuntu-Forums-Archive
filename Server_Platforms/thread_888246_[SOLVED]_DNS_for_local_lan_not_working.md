---
title: "[SOLVED] DNS for local lan not working"
date: 2008-08-12
forum: Server Platforms
---

### Post by jerome1232 on 2008-08-12
I installed bind9 and followed [this]("http://www.zaphu.com/2007/09/14/ubuntu-dns-server-guide-bind-master-server-setup/") and [this]("http://lani78.wordpress.com/2008/08/09/setting-up-a-dns-for-the-local-network/") guide for setting up a DNS server for resolving local ips (and caching others) They are essientally the same. After having gone through it all DNS for the local machines doesn't work, while it does work for getting out to the internet. Any help would be great, thanks in advance.

edit: revers dns does work
```
dig -x 192.168.1.3

; <<>> DiG 9.4.2-P1 <<>> -x 192.168.1.3
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 11628
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;3.1.168.192.in-addr.arpa.	IN	PTR

;; ANSWER SECTION:
3.1.168.192.in-addr.arpa. 86400	IN	PTR	server.home.lan.

;; AUTHORITY SECTION:
1.168.192.in-addr.arpa.	86400	IN	NS	server.home.lan.1.168.192.in-addr.arpa.

;; Query time: 9 msec
;; SERVER: 192.168.1.3#53(192.168.1.3)
;; WHEN: Tue Aug 12 20:58:02 2008
;; MSG SIZE  rcvd: 101

```
```
jeremy@desktop:~$ dig google.com

; <<>> DiG 9.4.2-P1 <<>> google.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 41922
;; flags: qr rd ra; QUERY: 1, ANSWER: 3, AUTHORITY: 13, ADDITIONAL: 0

;; QUESTION SECTION:
;google.com.			IN	A

;; ANSWER SECTION:
google.com.		70	IN	A	72.14.207.99
google.com.		70	IN	A	64.233.187.99
google.com.		70	IN	A	64.233.167.99

;; AUTHORITY SECTION:
.			449071	IN	NS	A.ROOT-SERVERS.NET.
.			449071	IN	NS	F.ROOT-SERVERS.NET.
.			449071	IN	NS	H.ROOT-SERVERS.NET.
.			449071	IN	NS	E.ROOT-SERVERS.NET.
.			449071	IN	NS	C.ROOT-SERVERS.NET.
.			449071	IN	NS	G.ROOT-SERVERS.NET.
.			449071	IN	NS	L.ROOT-SERVERS.NET.
.			449071	IN	NS	B.ROOT-SERVERS.NET.
.			449071	IN	NS	M.ROOT-SERVERS.NET.
.			449071	IN	NS	J.ROOT-SERVERS.NET.
.			449071	IN	NS	I.ROOT-SERVERS.NET.
.			449071	IN	NS	K.ROOT-SERVERS.NET.
.			449071	IN	NS	D.ROOT-SERVERS.NET.

;; Query time: 6 msec
;; SERVER: 192.168.1.3#53(192.168.1.3)
;; WHEN: Tue Aug 12 20:15:57 2008
;; MSG SIZE  rcvd: 287

```
```
jeremy@desktop:~$ dig server.home.lan

; <<>> DiG 9.4.2-P1 <<>> server.home.lan
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 34604
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;server.home.lan.		IN	A

;; Query time: 3 msec
;; SERVER: 192.168.1.3#53(192.168.1.3)
;; WHEN: Tue Aug 12 20:17:28 2008
;; MSG SIZE  rcvd: 33

```
here are my config files: /etc/bind/named.conf.local
```
//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";
zone "home.lan" IN {
        type master;
        file "/etc/bind/zones/home.lan.db";
};
zone "1.168.192.in-addr.arpa" {
        type master;
        file "/etc/bind/zones/rev.1.168.192.in-addr.arpa";
};

```
/etc/bind/zones/home.lan.db
```
; Use semicolons to add comments.
; NO EMPTY lines.
; Host-to-IP Address DNS Pointers for home.lan
; Impotant serial number must always be iterated upward to prevent
; undesirable consequences. here I use YYYYMMDDII
home.lan. IN SOA server.home.lan. hostmaster.home.lan. (
        2008081203 ; serial
        8H ; refresh
        4H ; retry
        4W ; expire
        1D ; minimum
)
home.lan. IN NS server.home.lan.
home.lan. IN MX server.home.lan.
localhost IN A 127.0.0.1
; Set the hostnames in alphabetical order
desktop IN A 192.168.1.4
inlaws IN A 192.168.1.5
laptop IN A 192.168.1.2
router IN A 192.168.1.1
server IN A 192.168.1.3

```
and /etc/bind/zones/rev.1.168.192.in-addr.arpa
```
; IP Address-to-Host DNS Pointers for the 192.168.1.0 subnet
@ IN SOA server.home.lan. hostmaster.home.lan. (
        2008081202 ; serial
        8H ; refresh
        4H ; retry
        4W ; expire
        1D ; minimum
)
; define the authoritive name server
 IN NS server.home.lan
; our hosts, in numeric order
1 IN PTR router.home.lan.
2 IN PTR laptop.home.lan.
3 IN PTR server.home.lan.
4 IN PTR desktop.home.lan.
5 IN PTR inlaws.home.lan.

```

---

### Post by jerome1232 on 2008-08-13
Ok well I'm not sure what change did it, but it's fixed lol.

I think it may have been my spacing in /etc/bind/zones/home.lan.db
this is the working copy:
```
; Use semicolons to add comments.
; NO EMPTY lines.
; Host-to-IP Address DNS Pointers for home.lan
; Impotant serial number must always be iterated upward to prevent
; undesirable consequences. here I use YYYYMMDDII
home.lan. IN SOA server.home.lan. hostmaster.home.lan. (
        2008081209 ; serial
        8H ; refresh
        4H ; retry
        4W ; expire
        1D ; minimum
)
home.lan. IN NS server.home.lan.
home.lan. IN MX 10 server.home.lan.
localhost    IN A 127.0.0.1
; Set the hostnames in alphabetical order
desktop      IN A 192.168.1.4
inlaws       IN A 192.168.1.5
laptop       IN A 192.168.1.2
router       IN A 192.168.1.1
server       IN A 192.168.1.3

```

---

### Post by gonesolo on 2008-09-06
Hi I wonder could you help me. I'm having the same problem you were. I'm new to Ubuntu server but been using desktop for years. i've spent years as a windows IT admin so understand about dns and stuff. 

I read your problem I have the same I can ping/connect to external sites with no issues but can not ping my server by name.

here is my /etc/bind/db.home.local

```


;
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     server.home.local. root.home.local. (
                              5         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      server.home.local.
@       IN      A       10.10.10.10
ns      IN      A       10.10.10.10


```


Also can someone tell me how to configure ubuntu to do name server for systems that get their IP address by dhcp. in windows I'd use WINS but I've read the Ubuntu documentation and can not find how to do it on linux.

Thanks in advance.

EDIT: on review I'm pretty sure my named.conf file is wrong but the layout/etc is different from whats recommended in the documentation.

```


// This is the primary configuration file for the BIND DNS server named.
//
// Please read /usr/share/doc/bind9/README.Debian.gz for information on the
// structure of BIND configuration files in Debian, *BEFORE* you customize
// this configuration file.
//
// If you are just adding zones, please do that in /etc/bind/named.conf.local

include "/etc/bind/named.conf.options";

// prime the server with knowledge of the root servers
zone "." {
        type hint;
        file "/etc/bind/db.root";
};

// be authoritative for the localhost forward and reverse zones, and for
// broadcast zones as per RFC 1912

zone "localhost" {
        type master;
        file "/etc/bind/db.home.local";
};

zone "127.in-addr.arpa" {
        type master;
        file "/etc/bind/db.10";
};

zone "0.in-addr.arpa" {
        type master;
        file "/etc/bind/db.0";
};

zone "255.in-addr.arpa" {
        type master;
        file "/etc/bind/db.255";
};

include "/etc/bind/named.conf.local";
 
```

Any advice?

---

### Post by kevinthecomputerguy on 2010-02-11
Jerome1232-
 
Thanks for your help getting this working, it had me stumped.
I gave you some props in my linux how-to
 
[http://t3.woodel.com/my-linux-how-to/debian_howto_start_to_finish_using_webmin.pdf](http://t3.woodel.com/my-linux-how-to/debian_howto_start_to_finish_using_webmin.pdf)
 
thanks again!
-Kevinthecomputerguy

---

