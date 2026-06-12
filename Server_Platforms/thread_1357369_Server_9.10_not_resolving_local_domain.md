---
title: "Server 9.10 not resolving local domain"
date: 2009-12-17
forum: Server Platforms
---

### Post by ejay563 on 2009-12-17
Hello everyone,

I've attempted to setup a Bind9 DNS server, but it will not resolve the local domain name fateb.local. When it is set as the DNS server for the network, it will resolve external domain names just fine. Below are my configuration files. 

resolv.conf
```

domain fateb.local
search fateb.local
nameserver 127.0.0.1

```

/etc/bind/named.conf.local
```
//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

zone "fateb.local" IN {
        type master;
        file "/etc/bind/zones/fateb.local.db";
};

# This is the zone definition for reverse DNS.
zone "110.115.10.in-addr.arpa" {
type master;
file "/etc/bind/zones/rev.110.115.10.in-addr.arpa";
};

```

/etc/bind/zones/fateb.local.db
```
; Use semicolons to add comments.
; Host-to-IP Address DNS Pointers for fateb.local
; Note: The extra ... at the end of addresses are important.
; The following parameters set when DNS records will expire, etc.
; Importantly, the serial number must always be iterated upward to prevent
; undesirable consequences. A good format to use is YYYYMMDDI where
; the I index is in case you make more that one change in the same day.
fateb.local. IN SOA ns1.fateb.local. hostmaster.fateb.local. (
    200912101 ; serial
    8H ; refresh
    4H ; retry
    4W ; expire
    1D ; minimum
)
; NS indicates that ns1 is the name server on fateb.local
; MX indicates that ns1 is (also) the mail server on fateb.local, but it is not set up
fateb.local. IN NS ns1.fateb.local.
fateb.local. IN MX 10 ns1.fateb.local.
; Set an alias (canonical name) for webserver
www IN CNAME genesis.fateb.local.
; Set the address for localhost.fateb.local
localhost    IN A 127.0.0.1
; Set the hostnames in alphabetical order
fateb        IN A 10.115.110.10
genesis      IN A 10.115.110.12
ns1          IN A 10.115.110.13
router       IN A 10.115.110.1

```

/etc/bind/zones/rev.110.115.10.in-addr.arpa
```
; IP Address-to-Host DNS Pointers for 10.115.110.0 subnet
@ IN SOA ns1.fateb.local. hostmaster.fateb.local. (
    200912101 ; serial
    8H ; refresh
    4H ; retry
    4W ; expire
    1D ; minimum
)
; define the authoritative name server
IN NS ns1.fateb.local.
; our hosts, in numeric order
13        IN PTR ns1.fateb.local.
12        IN PTR genesis.fateb.local.
10        IN PTR fateb.fateb.local.


```

I read in another thread that the /etc/nsswitch.conf file had a line that needed to be changed to get it to work properly, but that line was already the way it was supposed to be changed to:
> 
    * Open /etc/nsswitch.conf in your favorite text editor (I like nano, vim works, if you are an emacs user.......well I guess you can keep reading).
    * find the following line:
      hosts: file mdns4_minimal [NOTFOUND=return] dns mdns4
    * Change it to:
      hosts: files dns
    * Thats it!!

... yeah, so that was done already, and it still doesn't resolve. Just in case here is /etc/nsswitch.conf:
```
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files dns
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

```

Thanks in advance for the help!

~ejay563

---

### Post by codfather on 2009-12-21
This link may help you. It appears you need to turn avahi off to get it to work.

[https://bugs.launchpad.net/ubuntu/+source/nss-mdns/+bug/94940](https://bugs.launchpad.net/ubuntu/+source/nss-mdns/+bug/94940)

I have a slightly different issue I'm trying to get an answer to , and came across your post in the process. I hope this sorts your issue.

Nick

---

### Post by ejay563 on 2009-12-29
Thanks for your reply Nick. For some reason I didn't get e-mail notification that a reply was made. I finally did figure out how to get it working. I re-did the BIND9 setup with this tutorial: [http://ulyssesonline.com/2007/11/07/how-to-setup-a-dns-server-in-ubuntu/]("http://ulyssesonline.com/2007/11/07/how-to-setup-a-dns-server-in-ubuntu/"). I then figured out that you can't just type fateb.local (in my case) you have to type [www.fateb.local](www.fateb.local). I tried getting it to work with only fateb.local, but I couldn't figure it out, and it't not that big of a deal. Thanks again!

---

