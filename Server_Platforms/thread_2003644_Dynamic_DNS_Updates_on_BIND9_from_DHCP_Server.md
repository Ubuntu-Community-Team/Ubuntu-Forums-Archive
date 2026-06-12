---
title: "Dynamic DNS Updates on BIND9 from DHCP Server"
date: 2012-06-14
forum: Server Platforms
---

### Post by anonymouschief on 2012-06-14
Hello All,

I am running Ubuntu Server 12.04. The same server is the master DNS caching and authoritative server for my internal domain using BIND9. The same server is now also the DHCP Server for my home network using isc-dhcp-server.

While installing the DNS Services (based on the tutorials linked below), I had to manually add DNS entries for the rest of the computers in my home network (See the conf files below).

Now that the server is now a DHCP Server, I would like the DNS Server to dynamically receive my other computer's ip information from the DHCP Server instead of using the hardcoded ones, because they will change.

Please note: After hardcoding the ip addresses in my DNS settings, my Windows machines could now ping the Ubuntu server by hostname, instead of only by ip. There is nothing wrong with the DHCP services. I just need BIND9 to automatically update host information (based on info from DHCP).

The References/Guides I used for DNS:

[http://www.youtube.com/user/cgermany77/videos?query=bind](http://www.youtube.com/user/cgermany77/videos?query=bind)
[https://help.ubuntu.com/community/BIND9ServerHowto](https://help.ubuntu.com/community/BIND9ServerHowto)

FYI: I have renamed my local domain in the code below to example.local. That is not my real username or server name either :)

```

Zone file for example.local

;
; BIND data file for example.local
;
$TTL    604800
@       IN      SOA     example.local. root.example.local. (
                             34         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
                IN      A       192.168.1.120
;
@               IN      NS      ubuntu.example.local.
@               IN      A       192.168.1.120
@               IN      AAAA    ::1
ns.example.local.    IN      CNAME   ubuntu.example.local.
;ns             IN      A       192.168.1.120
ubuntu       	IN      A       192.168.1.120
desktop         IN      A       192.168.1.100
laptop          IN      A       192.168.1.102
router     	IN      A       192.168.1.1
www             IN      CNAME   ubuntu
crmapp          IN      CNAME   ubuntu

```

```

Reverse Zone File

;
; BIND reverse data file for local 192.168.1.x network
;
$TTL    604800
@       IN      SOA     example.local. root.example.local. (
                             30         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns.
1       IN      PTR     router.example.local.
10      IN      PTR     example.local.
100     IN      PTR     desktop.example.local.
102     IN      PTR     laptop.example.local.
120     IN      PTR     ubuntu.example.local.

```

```

DIG example.local

user@server:/etc/bind# dig example.local

; <<>> DiG 9.8.1-P1 <<>> example.local
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 23740
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 1

;; QUESTION SECTION:
;example.local.              IN      A

;; ANSWER SECTION:
example.local.       604800  IN      A       192.168.1.120

;; AUTHORITY SECTION:
example.local.       604800  IN      NS      ubuntu.example.local.

;; ADDITIONAL SECTION:
ubuntu.example.local. 604800 IN   A       192.168.1.120

;; Query time: 1 msec
;; SERVER: 192.168.1.120#53(192.168.1.120)
;; WHEN: Thu Jun 14 09:59:59 2012
;; MSG SIZE  rcvd: 90

```

```

DIG localhost


; <<>> DiG 9.8.1-P1 <<>> localhost
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 56833
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 1

;; QUESTION SECTION:
;localhost.                     IN      A

;; ANSWER SECTION:
localhost.              604800  IN      A       127.0.0.1

;; AUTHORITY SECTION:
localhost.              604800  IN      NS      localhost.

;; ADDITIONAL SECTION:
localhost.              604800  IN      AAAA    ::1

;; Query time: 1 msec
;; SERVER: 192.168.1.120#53(192.168.1.120)
;; WHEN: Thu Jun 14 09:59:46 2012
;; MSG SIZE  rcvd: 85

```

```

Testing Configuration

user@server:~# named-checkzone example.local /etc/bind/db.example.local
zone example.local/IN: loaded serial 34
OK

user@server:~# named-checkzone example.local /etc/bind/db.192
zone example.local/IN: loaded serial 30
OK


; <<>> DiG 9.8.1-P1 <<>> 1.168.192.in-addr.arpa AXFR
;; global options: +cmd
1.168.192.in-addr.arpa. 604800  IN      SOA     example.local. root.example.local. 30 604800 86400 2419200 604800
1.168.192.in-addr.arpa. 604800  IN      NS      ns.
1.1.168.192.in-addr.arpa. 604800 IN     PTR     router.example.local.
10.1.168.192.in-addr.arpa. 604800 IN    PTR     example.local.
100.1.168.192.in-addr.arpa. 604800 IN   PTR     desktop.example.local.
102.1.168.192.in-addr.arpa. 604800 IN   PTR     laptop.example.local.
120.1.168.192.in-addr.arpa. 604800 IN   PTR     ubuntu.example.local.
1.168.192.in-addr.arpa. 604800  IN      SOA     example.local. root.example.local. 30 604800 86400 2419200 604800
;; Query time: 1 msec
;; SERVER: 192.168.1.120#53(192.168.1.120)
;; WHEN: Thu Jun 14 10:13:24 2012
;; XFR size: 8 records (messages 1, bytes 268)

```

Thanks.

---

### Post by Cheesemill on 2012-06-14
There's a good how-to here:
[http://www.semicomplete.com/articles/dynamic-dns-with-dhcp/](http://www.semicomplete.com/articles/dynamic-dns-with-dhcp/)

I used to use this method until I discovered dnsmasq.

Dnsmasq is a combined DHCP and DNS server which will do what you want without the complexity of running BIND. There is just one simple configuration files that usually doesn't need much editing at all.

---

### Post by anonymouschief on 2012-06-14
> **Cheesemill said:**
> There's a good how-to here:

Dnsmasq is a combined DHCP and DNS server which will do what you want without the complexity of running BIND. There is just one simple configuration files that usually doesn't need much editing at all.

The instructions for installing DNSMasq keep making reference to the dhcp3 folder, yet there is no mention about installing dhcp3-server, while at the same time DNSMasq is said to have built in DHCP.

```
/etc/dhcp3/dhclient.conf
```

---

### Post by Cheesemill on 2012-06-14
> **anonymouschief said:**
> Can DNAMasq be used to set IP address reservations?
Yep.

Fore more info:
[http://wiki.debian.org/HowTo/dnsmasq](http://wiki.debian.org/HowTo/dnsmasq)
[http://www.thekelleys.org.uk/dnsmasq/docs/dnsmasq.conf.example](http://www.thekelleys.org.uk/dnsmasq/docs/dnsmasq.conf.example)

---

### Post by anonymouschief on 2012-06-14
The instructions for installing DNSMasq keep making reference to the dhcp3 folder, yet there is no mention about installing dhcp3-server, while at the same time DNSMasq is said to have built in DHCP.

```
/etc/dhcp3/dhclient.conf
```

---

### Post by anonymouschief on 2012-06-14
I have decided not to go with the dynamic DNS updates option. This issue is resolved.

---

