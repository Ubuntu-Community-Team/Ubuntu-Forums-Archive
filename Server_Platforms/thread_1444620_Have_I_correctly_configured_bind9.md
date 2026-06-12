---
title: "Have I correctly configured bind9?"
date: 2010-04-01
forum: Server Platforms
---

### Post by radubcrisan on 2010-04-01
Hi,

I have configured bind9 on Ubuntu Server 9.10, but I have the feeling that I did something wrong... 

Here is my network configuration:
[IMG]http://img694.imageshack.us/img694/3117/snapshot3rz.png[/IMG]

Here is my bind9 configuration files:
**/etc/bind/named.conf**
```
// This is the primary configuration file for the BIND DNS server named.
//
// Please read /usr/share/doc/bind9/README.Debian.gz for information on the 
// structure of BIND configuration files in Debian, *BEFORE* you customize 
// this configuration file.
//
// If you are just adding zones, please do that in /etc/bind/named.conf.local

include "/etc/bind/named.conf.options";
include "/etc/bind/named.conf.local";
include "/etc/bind/named.conf.default-zones";
```

**/etc/bind/named.conf.options**
```
options {
    directory "/var/cache/bind";

    // If there is a firewall between you and nameservers you want
    // to talk to, you may need to fix the firewall to allow multiple
    // ports to talk.  See http://www.kb.cert.org/vuls/id/800113

    // If your ISP provided one or more IP addresses for stable 
    // nameservers, you probably want to use them as forwarders.  
    // Uncomment the following block, and insert the addresses replacing 
    // the all-0's placeholder.

    forwarders {
         192.168.0.1;
    };

    auth-nxdomain no;    # conform to RFC1035
    listen-on-v6 { any; };
};
```

**/etc/bind/named.conf.local**
```
//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

zone "domain1.com" {
    type master;
    file "/var/lib/bind/domain1.com.hosts";
    };
zone "domain2.com" {
    type master;
    file "/var/lib/bind/domain2.com.hosts";
    };
zone "0.168.192.in-addr.arpa" {
    type master;
    file "/var/lib/bind/192.168.0.rev";
    };
```

**/etc/bind/named.conf.default-zones**
```
// prime the server with knowledge of the root servers
zone "." {
    type hint;
    file "/etc/bind/db.root";
};

// be authoritative for the localhost forward and reverse zones, and for
// broadcast zones as per RFC 1912

zone "localhost" {
    type master;
    file "/etc/bind/db.local";
};

zone "127.in-addr.arpa" {
    type master;
    file "/etc/bind/db.127";
};

zone "0.in-addr.arpa" {
    type master;
    file "/etc/bind/db.0";
};

zone "255.in-addr.arpa" {
    type master;
    file "/etc/bind/db.255";
};
```

**/var/lib/bind/domain1.com.hosts**
```
$ttl 38400
@    IN    SOA    ns1.localdomain. radubcrisan.yahoo.com. (
            1269440202
            10800
            3600
            604800
            38400 )
@    IN    NS    ns1.localdomain.
ns1    IN    A    192.168.0.8
domain1.com.    IN    A    82.77.xxx.xxx
www.domain1.com.    IN    A    82.77.xxx.xxx
new.domain1.com.    IN    A    82.77.xxx.xxx
```

**/var/lib/bind/domain2.com.hosts**
```
$ttl 38400
@    IN    SOA    ns1.localdomain. radubcrisan.yahoo.com. (
            1269440736
            10800
            3600
            604800
            38400 )
@            IN    NS    ns1.localdomain.
ns1            IN    A    192.168.0.8        ; IP Local

domain2.com.    IN    A    82.77.xxx.xxx
www.domain2.com.    IN    A    82.77.xxx.xxx
new.domain2.com.    IN    A    82.77.xxx.xxx
domain2.com.    IN    TXT    "v=spf1 a mx ~all"
```

**/var/lib/bind/192.168.0.rev**
```
$ttl 38400
0.168.192.in-addr.arpa.    IN    SOA    ns1.localdomain. radubcrisan.yahoo.com. (
            1270053514
            10800
            3600
            604800
            38400 )
0.168.192.in-addr.arpa.    IN    NS    ns1.localdomain.
8     IN     PTR    ns1.localdomain.
```

And other configuration that I made:
**/etc/resolv.conf**
```
search domain1.com
search domain2.com
nameserver 192.168.0.8
nameserver 192.168.0.1
```

**/etc/hosts**
```
127.0.0.1       localhost.localdomain   localhost
192.168.0.8     ns1.localdomain         ns1

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

Now, I am not sure if I made well the configuration, specially the name of the server is **ns1.localdomain** should it be **ns1.domain1.com** or **ns1.domain2.com**, because I have two domains on this server?

Thank you for your answer!

---

