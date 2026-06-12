---
title: "DDNS not updating"
date: 2009-04-09
forum: Server Platforms
---

### Post by helpme-buntu on 2009-04-09
I am a green newbie, still wet behind the ears.

I tried to setup bind9 and dhcp3 tonight. Everything is working great except DDNS. I do not seem to be updating my db file with my dhcp clients.

My db file is located in /etc/bind/zones/domainname.db. Could the fact that I added a folder zones be causing the problem?

Again, DNS works, DHCP works. The only issue I have in DDNS is not working. Any suggestions or tutorials that I should look at? I have attached all relevant files.

Thanks.


named.conf-->
// This is the primary configuration file for the BIND DNS server named.
//
// Please read /usr/share/doc/bind9/README.Debian.gz for information on the 
// structure of BIND configuration files in Debian, *BEFORE* you customize 
// this configuration file.
//
// If you are just adding zones, please do that in /etc/bind/named.conf.local

include "/etc/bind/named.conf.options";

acl homenet {
        10.0.0.0/24;
        127.0.0.1;
        };


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

include "/etc/bind/named.conf.local";
-----------------------------------------
named.conf.local-->
key SecDNS {
      algorithm hmac-md5;
      secret "SuperSecretKeyDNSUpdates";
      } ;

server 10.0.0.13 {
      keys { SecDNS ;};
      };

zone "homenetworks.com" {
        type master;
        file "/etc/bind/zones/homenetworks.com.db";
        allow-update {
                key SecDNS;
                };
        allow-query {
                homenet;
                }; 
        };

zone "0.0.10.in-addr.arpa" {
        type master;
        file "/etc/bind/zones/rev.0.0.10.in-addr.arpa";
        allow-update {
                key SecDNS;
                };
        allow-query {
                homenet;
                };
        };
---------------------------------------------------------
named.conf.options-->
cat named.conf.options
options {
        directory "/var/cache/bind";

        forwarders {
                x.x.x.x; y.y.y.y;
        };

        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
};
----------------------------------------------------
homenetworks.com.db-->$TTL 28800
homenetworks.com.      IN      SOA     ns1.homenetworks.com. none.none.com. (
                                                        2009040801; serial 
                                                        28800; refresh
                                                        3600; retry
                                                        60480; expiry - max
                                                        38400; don't try more than every
 )

homenetworks.com.      IN      NS              ns1.homenetworks.com.

ns1             IN      A       10.0.0.13
server          IN      A       10.0.0.2
sw1             IN      A       10.0.0.3
sw2             IN      A       10.0.0.4
ap1             IN      A       10.0.0.6
ap2             IN      A       10.0.0.7
ap3             IN      A       10.0.0.8
--------------------------------------------------
dhcpd.conf-->
ddns-updates on;
#
# Sample configuration file for ISC dhcpd for Debian
#
# Attention: If /etc/ltsp/dhcpd.conf exists, that will be used as
# configuration file instead of this file.
#
# $Id: dhcpd.conf,v 1.1.1.1 2002/05/21 00:07:44 peloy Exp $
#

# The ddns-updates-style parameter controls whether or not the server will
# attempt to do a DNS update when a lease is confirmed. We default to the
# behavior of the version 2 packages ('none', since DHCP v2 didn't
# have support for DDNS.)
ddns-update-style interim;
ddns-domainname "homenetworks.com";
deny client-updates;
ddns-rev-domainname "in-addr.arpa.";
allow unknown-clients;
ignore client-updates;


# option definitions common to all supported networks...
option dhcp-server-identifier 10.0.0.13;

authoritative;


log-facility local7;

key SecDNS {
  algorithm hmac-md5;
  secret "SuperSecretKeyDNSUpdates";
  }

# Forward DNS lookup zone
zone homenetworks.com. {
  primary 127.0.0.1;
  key SecDNS;
  }

# Reverse DNS lookup zone
zone 0.0.10.in-addr.arpa. {
  primary 127.0.0.1;
  key SecDNS;
  }

# HOME LAN
subnet 10.0.0.0 netmask 255.255.255.0 {
  range 10.0.0.140 10.0.0.180;
  option domain-name "homenetworks.com"; 
  option broadcast-address 10.0.0.255;
  option subnet-mask 255.255.255.0;
  option routers 10.0.0.1;
  option domain-name-servers 10.0.0.13;
  authoritative; 
  max-lease-time 14400;
  default-lease-time 7200;
  ignore client-updates;
  ddns-updates on;
  }

---

### Post by helpme-buntu on 2009-04-09
Everything is working. My config was good.

When I created the folder zones, I needed to modify the permissions to include write.

---

