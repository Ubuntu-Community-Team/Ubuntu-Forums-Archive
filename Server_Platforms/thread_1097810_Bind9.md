---
title: "Bind9"
date: 2009-03-16
forum: Server Platforms
---

### Post by Bengaul on 2009-03-16
Hi All,

I am trying to set up a basic DNS server for a wireless LAN (10.1.0.0/16). It just needs to resolve to a few IP's on a wired LAN (192.168.0.0/16), like our mail server. It does not need to forward any requests anywhere, and cannot access the internet. 

I have tried a few articles on the net, but none of them have worked for me using Ubuntu Server 8.10. I'm sure I am making more of meal of this than I need to. I keep getting DNS timeout errors.

Many thanks,

Bengaul.

I have included the following files. Perhaps some bright spark can tell me why it aint working. 

**_named.conf.local (This is where I name my zones?)_**

//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

# This is the zone definition. replace example.com with your domain name
zone "wireless.network" {
        type master;
        file "/etc/bind/zones/wireless.network.db";
        };

# This is the zone definition for reverse DNS. replace 0.168.192 with your netw$
zone "1.10.in-addr.arpa" {
     type master;
     file "/etc/bind/zones/rev.1.10.in-addr.arpa";
};

**_named.conf_**

// This is the primary configuration file for the BIND DNS server named.
//
// Please read /usr/share/doc/bind9/README.Debian.gz for information on the
// structure of BIND configuration files in Debian, *BEFORE* you customize
// this configuration file.
//
// If you are just adding zones, please do that in /etc/bind/named.conf.local

include "/etc/bind/named.conf.options";

// prime the server with knowledge of the root servers
zone "wireless.network." {
        type hint;
        file "/etc/bind/zones/wireless.network.db";
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

include "/etc/bind/named.conf.local";

**_named.conf.options_**

options {
        directory "/var/cache/bind";

        // If there is a firewall between you and nameservers you want
        // to talk to, you may need to fix the firewall to allow multiple
        // ports to talk.  See [http://www.kb.cert.org/vuls/id/800113](http://www.kb.cert.org/vuls/id/800113)

        // If your ISP provided one or more IP addresses for stable
        // nameservers, you probably want to use them as forwarders.
        // Uncomment the following block, and insert the addresses replacing
        // the all-0's placeholder.

        // forwarders {
        //      0.0.0.0;
        // };

        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
};

---

