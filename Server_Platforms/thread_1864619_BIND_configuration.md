---
title: "BIND configuration"
date: 2011-10-19
forum: Server Platforms
---

### Post by pasadia on 2011-10-19
I have problems with a simple BIND  configuration in CentOS. I have a static public IP 1.1.1.1 and I  recently bought a domain name gigi.com. I just want that gigi.com points  to 1.1.1.1 (Apache Web Server).

This is how my named.conf file looks:
> 
options {
        directory "/var/named";
};

zone "." IN {
        type hint;
        file "named.ca";
};

zone "gigi.com" IN {
      type master;
      file "named.gigi.com";

};


 This is how zone file named.gigi.com looks:

> 
$TTL 14400

; Specify the primary nameserver ns1.example.com in SOA
@ 14400 IN SOA ns1.gigi.com. hostmaster.gigi.com. (
                                2008092902 ; Serial in YYYYMMDDXX (XX is increment)
                                10800; refresh seconds
                                3600; retry
                                604800; expire
                                38400; minimum
                                );
; Website IP Address specified in A record

       IN A 1.1.1.1

; TWO nameserver names

       IN NS ns1.gigi.com.
       IN NS ns2.gigi.com.

; Nameservers and their corresponding IPs

ns1  IN A 1.1.1.1
ns2  IN A 1.1.1.2

; Specify here any Aliases using CNAME record

www IN CNAME 1.1.1.1

  
 Named daemon runs with no errors, but when the DNS doesn't work. nslookup gigi.com doesn't give me the dns server ip.

---

### Post by nyu2007 on 2011-10-20
look at /etc/resolve.conf it must be point to dns server

PS: This is Ubuntu forum. Your distro is CentOS, it have some different when config

---

