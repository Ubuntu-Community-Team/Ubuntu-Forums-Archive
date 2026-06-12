---
title: "DHCPD and DNS Dynamic Update HELP!I have ubuntu 9.04 installations.  2 Name servers a"
date: 2009-08-18
forum: Server Platforms
---

### Post by krisarmstrong on 2009-08-18
I have ubuntu 9.04 installations.  2 Name servers and one that is a DHCP server along with some other roles.  The DHCP server will not automatically update the DNS names on the DNS servers.   Dose the DNS and DHCP have to be on the same box.  here is the configs.  Any help would be greatly appreciated.

NS1.homelinux.com
Bind9 DNS
rmstrong@ns1:/etc/bind$ cat named.conf
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
include "/etc/bind/named.conf.local";
karmstrong@ns1:/etc/bind$ cat named.conf.local
# The secret key used for DHCP updates.
key DHCP_UPDATER {
    algorithm HMAC-MD5.SIG-ALG.REG.INT;

    # Important: Replace this key with your generated key.
    # Also note that the key should be surrounded by quotes.
    secret "OjsK2b9HWc99z21Y0CwHsA==";
};
//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

# Our domain zone
zone "homelinux.com" {
   type master;
   file "/var/lib/bind/homelinux.com.db";
    # Tell this zone that we will allow it to be updated from anyone
    # that knows the secret specified in the DHCP_UPDATER key.
    allow-update { key DHCP_UPDATER; };
};
 
# For reverse DNS 
zone "2.16.172.in-addr.arpa" {
   type master;
   file "/var/lib/bind/rev.0.2.16.172.in-addr.arpa";
    # Tell this zone that we will allow it to be updated from anyone
    # that knows the secret specified in the DHCP_UPDATER key.
    allow-update { key DHCP_UPDATER; };
};
karmstrong@ns1:/etc/bind$ cat named.conf.options
options {
      directory "/var/cache/bind";

      // If there is a firewall between you and nameservers you want
      // to talk to, you may need to fix the firewall to allow multiple
      // ports to talk.  See [http://www.kb.cert.org/vuls/id/800113](http://www.kb.cert.org/vuls/id/800113)

      // If your ISP provided one or more IP addresses for stable 
      // nameservers, you probably want to use them as forwarders.  
      // Uncomment the following block, and insert the addresses replacing 
      // the all-0's placeholder.

       forwarders {
             208.67.222.220;
            208.67.220.220;
       };

      auth-nxdomain no;    # conform to RFC1035
      listen-on-v6 { any; };
};
karmstrong@ns1:/etc/bind$ 


cortex.homelinux.com
DHCP

karmstrong@cortex:/etc/dhcp3$ cat dhcpd.conf
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
ignore client-updates;      # Overwrite client configured FQHNs
ddns-domainname "homelinux.com.";
ddns-rev-domainname "rev-0.2.16.172.in-addr.arpa.";


# option definitions common to all supported networks...
# option domain-name "homelinux.com";
# option domain-name-servers 172.16.2.30, 172.16.2.35;

# default-lease-time 600;
# max-lease-time 7200;

# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.
authoritative;

# Use this to send dhcp log messages to a different log file (you also
# have to hack syslog.conf to complete the redirection).
log-facility local7;

# No service will be given on this subnet, but declaring it helps the 
# DHCP server to understand the network topology.

#subnet 10.152.187.0 netmask 255.255.255.0 {
#}

key DHCP_UPDATER {
    algorithm HMAC-MD5.SIG-ALG.REG.INT;

    # Important: Replace this key with your generated key.
    # Also note that the key should be surrounded by quotes.
      secret "OjsK2b9HWc99z21Y0CwHsA==";
       };
       zone homelinux.com. {
       primary 127.0.0.1;
       key DHCP_UPDATER;
       }
    
       zone rev.0.2.16.172.in-addr.arpa. {
       primary 127.0.0.1;
       key DHCP_UPDATER;
       }
    
    

# This is a very basic subnet declaration.

#subnet 10.254.239.0 netmask 255.255.255.224 {
#  range 10.254.239.10 10.254.239.20;
#  option routers rtr-239-0-1.example.org, rtr-239-0-2.example.org;
#}

# This declaration allows BOOTP clients to get dynamic addresses,
# which we don't really recommend.

#subnet 10.254.239.32 netmask 255.255.255.224 {
#  range dynamic-bootp 10.254.239.40 10.254.239.60;
#  option broadcast-address 10.254.239.31;
#  option routers rtr-239-32-1.example.org;
#}

# A slightly different configuration for an internal subnet.
subnet 172.16.2.0 netmask 255.255.255.0 {
  range 172.16.2.100  172.16.2.125;
  option domain-name-servers 172.16.2.30, 172.16.2.35;
  option domain-name "homelinux.com";
  option routers 172.16.2.254;
  option broadcast-address 10.5.5.31;
  default-lease-time 600;
  max-lease-time 7200;
}

# Hosts which require special configuration options can be listed in
# host statements.   If no address is specified, the address will be
# allocated dynamically (if possible), but the host-specific information
# will still come from the host declaration.

#host passacaglia {
#  hardware ethernet 0:0:c0:5d:bd:95;
#  filename "vmunix.passacaglia";
#  server-name "toccata.fugue.com";
#}

# Fixed IP addresses can also be specified for hosts.   These addresses
# should not also be listed as being available for dynamic assignment.
# Hosts for which fixed IP addresses have been specified can boot using
# BOOTP or DHCP.   Hosts for which no fixed address is specified can only
# be booted with DHCP, unless there is an address range on the subnet
# to which a BOOTP client is connected which has the dynamic-bootp flag
# set.
#host fantasia {
#  hardware ethernet 08:00:07:26:c0:a5;
#  fixed-address fantasia.fugue.com;
#}

# You can declare a class of clients and then do address allocation
# based on that.   The example below shows a case where all clients
# in a certain class get addresses on the 10.17.224/24 subnet, and all
# other clients get addresses on the 10.0.29/24 subnet.

#class "foo" {
#  match if substring (option vendor-class-identifier, 0, 4) = "SUNW";
#}

#shared-network 224-29 {
#  subnet 10.17.224.0 netmask 255.255.255.0 {
#    option routers rtr-224.example.org;
#  }
#  subnet 10.0.29.0 netmask 255.255.255.0 {
#    option routers rtr-29.example.org;
#  }
#  pool {
#    allow members of "foo";
#    range 10.17.224.10 10.17.224.250;
#  }
#  pool {
#    deny members of "foo";
#    range 10.0.29.10 10.0.29.230;
#  }
#}
karmstrong@cortex:/etc/dhcp3$ 

Here are the error messages from the syslog
Aug 18 05:12:49 cortex dhcpd: DHCPACK on 172.16.2.111 to 00:08:89:62:f4:f4 via eth0
Aug 18 05:17:49 cortex dhcpd: DHCPREQUEST for 172.16.2.111 from 00:08:89:62:f4:f4 via eth0
Aug 18 05:17:49 cortex dhcpd: DHCPACK on 172.16.2.111 to 00:08:89:62:f4:f4 via eth0
Aug 18 05:22:02 cortex dhcpd: Unable to add forward map from iPhone.homelinux.com. to 172.16.2.105: connection refused
Aug 18 05:22:02 cortex dhcpd: DHCPREQUEST for 172.16.2.105 from 00:26:4a:41:13:e9 (iPhone) via eth0
Aug 18 05:22:02 cortex dhcpd: DHCPACK on 172.16.2.105 to 00:26:4a:41:13:e9 (iPhone) via eth0
Aug 18 05:22:49 cortex dhcpd: DHCPREQUEST for 172.16.2.111 from 00:08:89:62:f4:f4 via eth0
Aug 18 05:22:49 cortex dhcpd: DHCPACK on 172.16.2.111 to 00:08:89:62:f4:f4 via eth0
Aug 18 05:27:49 cortex dhcpd: DHCPREQUEST for 172.16.2.111 from 00:08:89:62:f4:f4 via eth0
Aug 18 05:27:49 cortex dhcpd: DHCPACK on 172.16.2.111 to 00:08:89:62:f4:f4 via eth0
Aug 18 05:32:49 cortex dhcpd: DHCPREQUEST for 172.16.2.111 from 00:08:89:62:f4:f4 via eth0
Aug 18 05:32:49 cortex dhcpd: DHCPACK on 172.16.2.111 to 00:08:89:62:f4:f4 via eth0
Aug 18 05:37:49 cortex dhcpd: DHCPREQUEST for 172.16.2.111 from 00:08:89:62:f4:f4 via eth0
Aug 18 05:37:49 cortex dhcpd: DHCPACK on 172.16.2.111 to 00:08:89:62:f4:f4 via eth0
Aug 18 05:42:49 cortex dhcpd: DHCPREQUEST for 172.16.2.111 from 00:08:89:62:f4:f4 via eth0
Aug 18 05:42:49 cortex dhcpd: DHCPACK on 172.16.2.111 to 00:08:89:62:f4:f4 via eth0
Aug 18 05:47:50 cortex dhcpd: DHCPREQUEST for 172.16.2.111 from 00:08:89:62:f4:f4 via eth0
Aug 18 05:47:50 cortex dhcpd: DHCPACK on 172.16.2.111 to 00:08:89:62:f4:f4 via eth0
Aug 18 05:51:46 cortex dhcpd: Unable to add forward map from iPhone.homelinux.com. to 172.16.2.105: connection refused
Aug 18 05:51:46 cortex dhcpd: DHCPREQUEST for 172.16.2.105 from 00:26:4a:41:13:e9 (iPhone) via eth0
Aug 18 05:51:46 cortex dhcpd: DHCPACK on 172.16.2.105 to 00:26:4a:41:13:e9 (iPhone) via eth0
Aug 18 05:52:07 cortex dhcpd: Unable to add forward map from iPhone.homelinux.com. to 172.16.2.105: connection refused
Aug 18 05:52:07 cortex dhcpd: DHCPREQUEST for 172.16.2.105 from 00:26:4a:41:13:e9 (iPhone) via eth0
Aug 18 05:52:07 cortex dhcpd: DHCPACK on 172.16.2.105 to 00:26:4a:41:13:e9 (iPhone) via eth0
Aug 18 05:52:49 cortex dhcpd: DHCPREQUEST for 172.16.2.111 from 00:08:89:62:f4:f4 via eth0
Aug 18 05:52:49 cortex dhcpd: DHCPACK on 172.16.2.111 to 00:08:89:62:f4:f4 via eth0
Aug 18 05:57:49 cortex dhcpd: Wrote 11 leases to leases file.
Aug 18 05:57:49 cortex dhcpd: DHCPREQUEST for 172.16.2.111 from 00:08:89:62:f4:f4 via eth0
Aug 18 05:57:49 cortex dhcpd: DHCPACK on 172.16.2.111 to 00:08:89:62:f4:f4 via eth0
Aug 18 05:58:08 cortex dhcpd: DHCPREQUEST for 172.16.2.101 from 00:25:00:88:05:d8 via eth0
Aug 18 05:58:08 cortex dhcpd: DHCPACK on 172.16.2.101 to 00:25:00:88:05:d8 via eth0
Aug 18 06:02:49 cortex dhcpd: DHCPREQUEST for 172.16.2.111 from 00:08:89:62:f4:f4 via eth0
Aug 18 06:02:49 cortex dhcpd: DHCPACK on 172.16.2.111 to 00:08:89:62:f4:f4 via eth0
Aug 18 06:03:28 cortex dhcpd: DHCPREQUEST for 172.16.2.103 from 00:17:f2:d4:f1:d1 via eth0
Aug 18 06:03:28 cortex dhcpd: DHCPACK on 172.16.2.103 to 00:17:f2:d4:f1:d1 via eth0
Aug 18 06:06:20 cortex dhcpd: Unable to add forward map from AppleTV.homelinux.com. to 172.16.2.100: connection refused
Aug 18 06:06:20 cortex dhcpd: DHCPREQUEST for 172.16.2.100 from 00:17:f2:f7:e1:5a (AppleTV) via eth0
Aug 18 06:06:20 cortex dhcpd: DHCPACK on 172.16.2.100 to 00:17:f2:f7:e1:5a (AppleTV) via eth0
Aug 18 06:07:49 cortex dhcpd: DHCPREQUEST for 172.16.2.111 from 00:08:89:62:f4:f4 via eth0
Aug 18 06:07:49 cortex dhcpd: DHCPACK on 172.16.2.111 to 00:08:89:62:f4:f4 via eth0
Aug 18 06:12:50 cortex dhcpd: DHCPREQUEST for 172.16.2.111 from 00:08:89:62:f4:f4 via eth0
Aug 18 06:12:50 cortex dhcpd: DHCPACK on 172.16.2.111 to 00:08:89:62:f4:f4 via eth0
Aug 18 06:17:49 cortex dhcpd: DHCPREQUEST for 172.16.2.111 from 00:08:89:62:f4:f4 via eth0
Aug 18 06:17:49 cortex dhcpd: DHCPACK on 172.16.2.111 to 00:08:89:62:f4:f4 via eth0
Aug 18 06:21:47 cortex dhcpd: Unable to add forward map from iPhone.homelinux.com. to 172.16.2.105: connection refused
Aug 18 06:21:47 cortex dhcpd: DHCPREQUEST for 172.16.2.105 from 00:26:4a:41:13:e9 (iPhone) via eth0
Aug 18 06:21:47 cortex dhcpd: DHCPACK on 172.16.2.105 to 00:26:4a:41:13:e9 (iPhone) via eth0
Aug 18 06:22:17 cortex dhcpd: Unable to add forward map from iPhone.homelinux.com. to 172.16.2.105: connection refused
Aug 18 06:22:17 cortex dhcpd: DHCPREQUEST for 172.16.2.105 from 00:26:4a:41:13:e9 (iPhone) via eth0
Aug 18 06:22:17 cortex dhcpd: DHCPACK on 172.16.2.105 to 00:26:4a:41:13:e9 (iPhone) via eth0
Aug 18 06:22:49 cortex dhcpd: DHCPREQUEST for 172.16.2.111 from 00:08:89:62:f4:f4 via eth0
Aug 18 06:22:49 cortex dhcpd: DHCPACK on 172.16.2.111 to 00:08:89:62:f4:f4 via eth0
Aug 18 06:27:49 cortex dhcpd: DHCPREQUEST for 172.16.2.111 from 00:08:89:62:f4:f4 via eth0
Aug 18 06:27:49 cortex dhcpd: DHCPACK on 172.16.2.111 to 00:08:89:62:f4:f4 via eth0
Aug 18 06:32:50 cortex dhcpd: DHCPREQUEST for 172.16.2.111 from 00:08:89:62:f4:f4 via eth0


I would prefer to keep DHCP and BIND on different machines.  it seems odd to me that they would have to be on the same machines.  Thanks

---

### Post by krisarmstrong on 2009-08-18
**UPDATED CONF and LOGS**

karmstrong@ns2:/etc/bind$ cat named.conf
// This is the primary configuration file for the BIND DNS server named.
//
// Please read /usr/share/doc/bind9/README.Debian.gz for information on the 
// structure of BIND configuration files in Debian, *BEFORE* you customize 
// this configuration file.
//
// If you are just adding zones, please do that in /etc/bind/named.conf.local

include "/etc/bind/named.conf.options";

// prime the server with knowledge of the root servers

key "rndc-key" {
    algorithm hmac-md5;
    secret "C0BUNay+hlyInBfahyYHQg==";
};

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
karmstrong@ns2:/etc/bind$ cat named.conf.local
# The secret key used for DHCP updates.
key DHCP_UPDATER {
    algorithm HMAC-MD5.SIG-ALG.REG.INT;

    # Important: Replace this key with your generated key.
    # Also note that the key should be surrounded by quotes.
    secret "OjsK2b9HWc99z21Y0CwHsA==";
};
//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

# Our domain zone
zone "homelinux.com" {
   type slave;
   file "/var/lib/bind/homelinux.com.db";
    # Tell this zone that we will allow it to be updated from anyone
    # that knows the secret specified in the DHCP_UPDATER key.
    allow-update { 172.16.2.40; };
    masters { 172.16.2.30; };
};
 
# For reverse DNS 
zone "2.16.172.in-addr.arpa" {
   type slave;
   file "/var/lib/bind/rev.0.2.16.172.in-addr.arpa";
    # Tell this zone that we will allow it to be updated from anyone
    # that knows the secret specified in the DHCP_UPDATER key.
    allow-update { 172.16.2.40; };
    masters { 172.16.2.30; };
};
karmstrong@ns2:/etc/bind$ cat named.conf.options
options {
    directory "/var/cache/bind";

    // If there is a firewall between you and nameservers you want
    // to talk to, you may need to fix the firewall to allow multiple
    // ports to talk.  See [http://www.kb.cert.org/vuls/id/800113](http://www.kb.cert.org/vuls/id/800113)

    // If your ISP provided one or more IP addresses for stable 
    // nameservers, you probably want to use them as forwarders.  
    // Uncomment the following block, and insert the addresses replacing 
    // the all-0's placeholder.

     forwarders {
         208.67.222.220;
        208.67.220.220;
     };

    auth-nxdomain no;    # conform to RFC1035
    listen-on-v6 { any; };
};
karmstrong@ns2:/etc/bind$ cat rndc.key
cat: rndc.key: Permission denied
karmstrong@ns2:/etc/bind$ sudo cat rndc.key
[sudo] password for karmstrong: 
Sorry, try again.
[sudo] password for karmstrong: 
key "rndc-key" {
    algorithm hmac-md5;
    secret "C0BUNay+hlyInBfahyYHQg==";
};
karmstrong@ns2:/etc/bind$ tail /var/log/syslog
Aug 18 14:01:25 ns2 named[1725]: client 172.16.2.30#52150: received notify for zone '2.16.172.in-addr.arpa'
Aug 18 14:01:25 ns2 named[1725]: client 172.16.2.30#52150: received notify for zone 'homelinux.com'
Aug 18 14:01:29 ns2 named[1725]: client 172.16.2.30#50262: received notify for zone '2.16.172.in-addr.arpa'
Aug 18 14:01:29 ns2 named[1725]: client 172.16.2.30#50262: received notify for zone 'homelinux.com'
Aug 18 14:02:32 ns2 named[1725]: invalid command from 127.0.0.1#49138: bad auth
Aug 18 14:02:34 ns2 named[1725]: invalid command from 127.0.0.1#54311: bad auth
Aug 18 14:02:35 ns2 named[1725]: invalid command from 127.0.0.1#52728: bad auth
Aug 18 14:02:36 ns2 named[1725]: invalid command from 127.0.0.1#36026: bad auth
Aug 18 14:27:17 ns2 -- MARK --
Aug 18 14:29:38 ns2 named[1725]: invalid command from 127.0.0.1#37660: bad auth
karmstrong@ns2:/etc/bind$

---

