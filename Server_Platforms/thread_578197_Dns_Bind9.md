---
title: "Dns Bind9"
date: 2007-10-17
forum: Server Platforms
---

### Post by samona on 2007-10-17
Hi all,
I'm trying to get BIND9 to work at my home using a fake domain name of "math-zone.com".  However, it will not work.  I'm doing this for educational purposes.  My web server is on address 192.168.1.106 and my dns server is on 192.168.1.106 (same computer). 

 The code of the files are below.  I have been working on this for 2 days now and still nothing.  I get a "un-known host math-zone.com".

```


vim math-zone.com.db



math-zone.com. IN SOA ns1.math-zone.com. admin.math-zone.com.(

2007031001
28800
3600
604800
38400
)

math-zone.com. IN NSroot@myServer:/etc/bind/zones# vim math-zone.com.db



math-zone.com. IN SOA ns1.math-zone.com. admin.math-zone.com.(

2007031001
28800
3600
604800
38400
)

math-zone.com. IN NS ns1.math-zone.com.



www IN CNAME math-zone.com
ns1 IN CNAME 192.168.1.106

```

```
cat rev.1.168.192.in-addr.arpa



@ IN SOA ns1.math-zone.com. admin.math-zone.com.(
2007031001
28800
604800
604800
86400
)

IN NS ns1.math-zone.com.
6 IN PTR math-zone.com
```

```
 cat named.conf.local


//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
include "/etc/bind/zones.rfc1918";

#this is the zone definition

zone "math-zone.com" {

type master;
file "/etc/bind/zones/math-zone.com.db";
};

#this is the zone definition for reverse DNS.
zone "1.168.192.in-addr.arpa"{

type master;
file "/etc/bind/zones/rev.1.168.192.in-addr.arpa";
};
```
```

cat named.conf.options




options {
        directory "/var/cache/bind";

        // If there is a firewall between you and nameservers you want
        // to talk to, you might need to uncomment the query-source
        // directive below.  Previous versions of BIND always asked
        // questions using port 53, but BIND 8.1 and later use an unprivileged
        // port by default.

        // query-source address * port 53;

        // If your ISP provided one or more IP addresses for stable
        // nameservers, you probably want to use them as forwarders.
        // Uncomment the following block, and insert the addresses replacing
        // the all-0's placeholder.

         forwarders {
         192.168.1.1;
         };

        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };

        // By default, name servers should only perform recursive domain
        // lookups for their direct clients.  If recursion is left open
        // to the entire Internet, your name server could be used to
        // perform distributed denial of service attacks against other
        // innocent computers.  For more information on DDoS recursion:
        // http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2006-0987

        allow-recursion { localnets; };

        // If you have DNS clients on other subnets outside of your
        // server's "localnets", you can explicitly add their networks
        // without opening up your server to the Internet at large:
        // allow-recursion { localnets; 192.168.0.0/24; };

        // If your name server is only listening on 127.0.0.1, consider:
        // allow-recursion { 127.0.0.1; };
};



```

192.168.1.1 is my router.  If anyone can help me thanks!

---

### Post by MJN on 2007-10-17
A couple of issues in your forward zone (there may be more):
 
1. Your ns1 record cannot be a CNAME to an IP address, but rather an A record e.g. **ns1 IN A 192.168.1.106**
 
2. There is no record for 'math-zone.com', yet *www*.math-zone.com says it's an alias for that record. Hence you need to add this record in with **<SPACE> IN A 192.168.1.106** (where <SPACE> is one, or more, spaces)
 
Mathew

---

### Post by blackjackchik on 2007-10-17
[http://forum.ubuntu.ru/index.php?topic=12746.0](http://forum.ubuntu.ru/index.php?topic=12746.0)
Sorry for russian:(

---

### Post by samona on 2007-10-17
Ok I changed the following file  math-zone.com.db but still doesn't work :(

```
cat math-zone.com.db




@        IN      SOA ns1.math-zone.com. admin.example.com. (
2007031001
28800
3600
604800
38400
)


math-zone.com. IN NS ns1.math-zone.com.

ns1 IN A 192.168.1.105

math-zone.com IN A 192.168.1.102
```

But still doesn't work

---

