---
title: "Bind9 won't resolve internal addresses"
date: 2008-07-27
forum: Server Platforms
---

### Post by bond00 on 2008-07-27
I've been trying to setup Bind9 for my internal network. I've followed every tutorial I've found on the internet, but apparently am still doing something wrong. The DNS server is in virtual machine, but I don't think that should matter as I'm using bridged networking. The VMs name is dnsvm and my network address is 192.168.2.0. 

On the PCs I've tested this on, I manually change the DNS entry to IP address of my bind server (192.168.2.225). After doing that, the problem is that when I type in mydomain.lan, [www.mydomain.lan](www.mydomain.lan), or dnsvm.mydomain.lan, IE or Firefox cannot find the page...it's like they are attempting to find the page on the Internet instead of my intranet. I've even gone into the router and change it's DNS settings to run from dnsvm...but no luck. 

When I try to ping by the DNS entry, it promptly replies 'unknown host'. 


Can anyone help me out?

Here are my conf files. 

File: /etc/bind/named.conf.local
```
zone "mydomain.lan" {
	type master;
	file "/etc/bind/zones/mydomain.lan.db";
};

zone "2.168.192.in-addr.arpa" {
	type master;
	file "/etc/bind/zones/rev.2.168.192.in-addr.arpa";
};

```


File: /etc/bind/zones/rev.2.168.192.in-addr.arpa
```
; IP Address-to-Host DNS Pointers for 192.168.1.0 subnet
@ IN SOA dnsvm.mydomain.lan. hostmaster.mydomain.lan. (
    200709131 ; serial
    8H ; refresh
    4H ; retry
    4W ; expire
    1D ; minimum
)
; define the authoritative name server
 IN NS dnsvm.mydomain.lan.
; our hosts, in numeric order
225        IN PTR dnsvm.mydomain.lan.

```

File: /etc/bind/zones/mydomain.lan.db
```
; Use semicolons to add comments.
; Host-to-IP Address DNS Pointers for mydomain.lan
; Note: The extra “.” at the end of addresses are important.
; The following parameters set when DNS records will expire, etc.
; Importantly, the serial number must always be iterated upward to prevent
; undesirable consequences. A good format to use is YYYYMMDDI where
; the I index is in case you make more that one change in the same day.
mydomain.lan. IN SOA dnsvm.mydomain.lan. hostmaster.mydomain.lan. (
    200709131 ; serial
    8H ; refresh
    4H ; retry
    4W ; expire
    1D ; minimum
)
; NS indicates that john is the name server on mydomain.lan
; MX indicates that john is (also) the mail server on mydomain.lan
mydomain.lan. IN NS dnsvm.mydomain.lan.
mydomain.lan. IN MX 10 dnsvm.mydomain.lan.
; Set an alias (canonical name) for paul
www IN CNAME dnsvm.mydomain.lan.
; Set the address for localhost.mydomain.lan
localhost    IN A 127.0.0.1
; Set the hostnames in alphabetical order
;hack   IN A 192.168.2.7

```

---

