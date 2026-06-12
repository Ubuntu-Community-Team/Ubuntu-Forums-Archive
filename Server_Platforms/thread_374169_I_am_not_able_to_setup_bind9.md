---
title: "I am not able to setup bind9"
date: 2007-03-02
forum: Server Platforms
---

### Post by dupa on 2007-03-02
The static IP address of the machine on which I run the DNS Server is **XXX.YYY.ZZZ.KKK**

other example IPs of my network are

**XXX.YYY.ZZZ.JJJ**
**XXX.YYY.ZZZ.WWW**

**AAA.BBB.CCC.DDD** is the DNS server of my provider.


These are my configuration files:

```

$ cat /etc/bind/named.conf
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

// zone "com" { type delegation-only; };
// zone "net" { type delegation-only; };

// From the release notes:
//  Because many of our users are uncomfortable receiving undelegated answers
//  from root or top level domains, other than a few for whom that behaviour
//  has been trusted and expected for quite some length of time, we have now
//  introduced the "root-delegations-only" feature which applies delegation-only
//  logic to all top level domains, and to the root domain.  An exception list
//  should be specified, including "MUSEUM" and "DE", and any other top level
//  domains from whom undelegated responses are expected and trusted.
// root-delegation-only exclude { "DE"; "MUSEUM"; };

include "/etc/bind/named.conf.local";


```


```

$ cat /etc/bind/named.conf.options
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
                **AAA.BBB.CCC.DDD**;
        };

        auth-nxdomain no;    # conform to RFC1035

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

```

$ cat /etc/bind/named.conf.local
//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

# This is the zone definition.
zone "my-own-domain.it" {
        type master;
        file "/etc/bind/zones/my-own-domain.it.db";
        };

# This is the zone definition for reverse DNS. 

zone "**ZZZ**.**YYY**.**XXX**.in-addr.arpa" {
     type master;
     file "/etc/bind/zones/rev.**ZZZ**.**YYY**.**XXX**.in-addr.arpa";
};


```

```

$ cat /etc/bind/zones/my-own-domain.it.db
// replace example.com with your domain name. do not forget the . after the domain name!
// Also, replace ns1 with the name of your DNS server
my-own-domain.it.      IN      SOA     test1.my-own-domain.it. test2.my-own-domain.it. (
// Do not modify the following lines!
     2006081401
     28800
     3600
     604800
     38400
 )

// Replace the following line as necessary:
// ns1 = DNS Server name
// mta = mail server name
// example.com = domain name
my-own-domain.it.      IN      NS              test1.my-own-domain.it.
my-own-domain.it.      IN      MX     10       mta.my-own-domain.it.

// Replace the IP address with the right IP addresses.
test1              IN      A       **XXX.YYY.ZZZ.JJJ**
mta              IN      A       **XXX.YYY.ZZZ.WWW**
test2         IN      A       **XXX.YYY.ZZZ.KKK**


```

```

$ cat /etc/bind/zones/rev.**ZZZ**.**YYY**.**XXX**.in-addr.arpa
//replace example.com with yoour domain name, ns1 with your DNS server name.
// The number before IN PTR example.com is the machine address of the DNS server. 

@ IN SOA test1.my-own-domain.it. test2.my-own-domain.it. (
                        2006081401;
                        28800;
                        604800;
                        604800;
                        86400
)

                     IN    NS     test1.my-own-domain.it.
**ZZZ**                    IN    PTR    my-own-domain.it


```

```

$ cat /etc/resolv.conf
nameserver **XXX.YYY.ZZZ.KKK**

```

And after configuration files, here it's what I do:

```

$ sudo /etc/init.d/networking restart

```

```

$ sudo /etc/init.d/bind9 restart

```

```

ping www.google.com
PING www.l.google.com (209.85.129.99) 56(84) bytes of data.
64 bytes from fk-in-f99.google.com (209.85.129.99): icmp_seq=1 ttl=238 time=76.6 ms

```

```

$ ping my-own-domain.it
ping: unknown host my-own-domain.it

```

```

ping test1.my-own-domain.it
ping: unknown host test1.my-own-domain.it

```

```

$ ping test2.my-own-domain.it
ping: unknown host test2.my-own-domain.it


```

---

### Post by jparello on 2007-03-16
Hi,

I just finished setting up bind9 with the exact setup you had  and got the the same problem. I couldn't see anythign wrong with your (or my setup) 

I restarted bind9 while tailing /var/daemons.log and saw that I was getting this error:

Mar 16 15:56:36 server named[28388]: /etc/bind/zones/mydomain.com.db:1: unknown RR type 'replace'
Mar 16 15:56:36 server named[28388]: zone mydomain.com/IN: loading master file /etc/bind/zones/slytly.com.db: unknown class/type

Well the first comment line in the file has the word replace in it so I removed all the // comments 

That was it. For some reason the // comments were not being processed.

I'm not sure if I had some fat finger error in there or not but it may help you if you tail the daemons.log when you restart to look for any errors in your .db files.

HTH
John

---

