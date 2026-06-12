---
title: "BIND/DHCPD Dynamic DNS issues"
date: 2008-04-15
forum: Server Platforms
---

### Post by tcpankon on 2008-04-15
I am in the process of setting up a DHCP/DNS server that will feed a cable modem system.  Both DHCP and BIND start up correctly, I am simply unable to do any lookups.  The cable modems will reside on a 10.0.0.x network, while the server itself is at 192.168.4.3.  The cable modems are ranging properly and being handed the appropriate config files/IP address/etc.  I am now stuck on getting BIND to update the reverse lookup file.  The goal is to be able to verify a modem is online by pinging the modem based off of hostname without having to worry about what IP address it has been assigned.  I would think that because of this, the reverse zone is all I really need to focus on.

here are all the relevant configs (dhcpd.conf, named.conf, named.conf.local, reverse and forward lookup files)

```
cat /etc/dhcp3/dhcpd.conf
# The ddns-updates-style parameter controls whether or not the server will
# attempt to do a DNS update when a lease is confirmed. We default to the
# behavior of the version 2 packages ('none', since DHCP v2 didn't
# have support for DDNS.)
ddns-update-style interim;

default-lease-time 600;
max-lease-time 7200;

# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.
authoritative;

# Use this to send dhcp log messages to a different log file (you also
# have to hack syslog.conf to complete the redirection).
log-facility local7;

# Modem
shared-network Modem {
        next-server 192.168.4.3;
        filename "deny.cm";
        authoritative;
        option log-servers 192.168.4.3;
        option time-servers 192.168.4.3;
        option domain-name-servers 192.168.4.3;
        option domain-name "cci.lab";
        # Modem
        subnet 10.0.0.0 netmask 255.255.255.0 {
                allow unknown-clients;
                ddns-rev-domainname "0.0.10.in-addr.arpa.";
                ddns-domainname "cci.lab.";
                deny client-updates;
                next-server 192.168.4.3;
                authoritative;
                option routers 10.0.0.1;
                range 10.0.0.2 10.0.0.254;
                }
        }
# 1Mx1M
group {
        next-server 192.168.4.3;
        filename "1Mx1M.cm";
        use-host-decl-names on;
        host 001b.d709.def8 {
                hardware ethernet 00:1b:d7:09:de:f8;
                }
        host 0004.bdee.3322 {
                hardware ethernet 00:04:bd:ee:33:22;
                }
        host 0012.2503.5b06 {
                hardware ethernet 00:12:25:03:5b:06;
                }
        host 000a.739a.56ca {
                hardware ethernet 00:0a:73:9a:56:ca;
                }
        }
# 192.168.4.x
subnet 192.168.4.0 netmask 255.255.255.0 {
        filename "deny.cm";
        }
shared-network CPE {
        option domain-name-servers 206.141.192.60 , 206.141.193.55;
        option domain-name "cci.lab";
        # TestCPE
        subnet 172.16.20.0 netmask 255.255.255.0 {
                option routers 172.16.20.1;
                range 172.16.20.2 172.16.20.2;
                }
        # testCPE2
        subnet 172.16.21.0 netmask 255.255.255.0 {
                option routers 172.16.21.1;
                range 172.16.21.2 172.16.21.2;
                }
        # Static
        subnet 172.16.22.0 netmask 255.255.255.0 {
                option routers 172.16.22.1;
                }
        }
# rev
key rndc-key {
        secret "DDr63qO1J9OUzfrSfRoiTg==";
        algorithm hmac-md5;
        }
# 0.0.10.in-addr.arpa
zone 0.0.10.in-addr.arpa. {
        primary 127.0.0.1;
        key rndc-key;
        }
# cci.lab
zone cci.lab. {
        primary 127.0.0.1;
        key rndc-key;
        }






cat named.conf
acl test {
        127.0.0.1;
        };
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
//logging {
//      category default {
//              default_syslog;
//              };
//      category update {
//              default_syslog;
//              };
//      };
include "/etc/bind/rndc.key";
controls {
inet 127.0.0.1 port 953 allow { 127.0.0.1; } keys { rndc-key; };
};



cat named.conf.local
//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";
zone "0.0.10.in-addr.arpa" {
        type master;
        file "/etc/bind/10.0.0.rev";
        allow-update { key rndc-key; };
        notify yes;
        };
zone "cci.lab" {
        type master;
        file "/etc/bind/cci.lab.hosts";
        allow-update { key rndc-key; };
        notify yes;
        };
logging {
        channel update_debug {
                file "/var/log/update-debug.log";
                severity  debug 3;
                print-category yes;
                print-severity yes;
                print-time     yes;
        };
        channel security_info    {
                file "/var/log/named-auth.info";
                severity  info;
                print-category yes;
                print-severity yes;
                print-time     yes;
        };
category update { update_debug; };
category security { security_info; };
};




cat 10.0.0.rev
$ttl 38400
0.0.10.in-addr.arpa.    IN      SOA     zenoss-server.cci.lab. cci.cci.lab. (
                        1208284628
                        10800
                        3600
                        604800
                        38400 )
0.0.10.in-addr.arpa.    IN      NS      zenoss-server.cci.lab.



cat cci.lab.hosts
$ttl 38400
cci.lab.        IN      SOA     zenoss-server.cci.lab. cci.cci.lab. (
                        1208285744
                        10800
                        3600
                        604800
                        38400 )
cci.lab.        IN      NS      zenoss-server.cci.lab.
zenoss-server   IN      A       192.168.4.3

```

---

### Post by twistedtwig on 2008-04-16
what errors are you getting (if any) in your log files, daemon.log ,messages , etc?

---

### Post by tcpankon on 2008-04-16
Not really seeing any errors in any log files.  

Running BIND with logging on shows the following when the modems range:

```
16-Apr-2008 10:13:00.426 client 192.168.4.3#32773: UDP request
16-Apr-2008 10:13:00.427 client 192.168.4.3#32773: using view '_default'
16-Apr-2008 10:13:00.427 client 192.168.4.3#32773: request is not signed
16-Apr-2008 10:13:00.427 client 192.168.4.3#32773: recursion available
16-Apr-2008 10:13:00.427 client 192.168.4.3#32773: query
16-Apr-2008 10:13:00.427 client 192.168.4.3#32773: ns_client_attach: ref = 1
16-Apr-2008 10:13:00.428 client 192.168.4.3#32773: query '253.0.0.10.in-addr.arpa/PTR/IN' approved
16-Apr-2008 10:13:00.428 client 192.168.4.3#32773: send
16-Apr-2008 10:13:00.428 client 192.168.4.3#32773: sendto
16-Apr-2008 10:13:00.428 client 192.168.4.3#32773: senddone
16-Apr-2008 10:13:00.428 client 192.168.4.3#32773: next
16-Apr-2008 10:13:00.429 client 192.168.4.3#32773: ns_client_detach: ref = 0
16-Apr-2008 10:13:00.429 client 192.168.4.3#32773: endrequest
16-Apr-2008 10:13:00.429 client @0xb60a2008: udprecv
16-Apr-2008 10:13:00.486 client 192.168.4.3#32773: UDP request
16-Apr-2008 10:13:00.486 client 192.168.4.3#32773: using view '_default'
16-Apr-2008 10:13:00.486 client 192.168.4.3#32773: request is not signed
16-Apr-2008 10:13:00.486 client 192.168.4.3#32773: recursion available
16-Apr-2008 10:13:00.487 client 192.168.4.3#32773: query
16-Apr-2008 10:13:00.487 client 192.168.4.3#32773: ns_client_attach: ref = 1
16-Apr-2008 10:13:00.487 client 192.168.4.3#32773: query '254.0.0.10.in-addr.arpa/PTR/IN' approved
16-Apr-2008 10:13:00.487 client 192.168.4.3#32773: send
16-Apr-2008 10:13:00.488 client 192.168.4.3#32773: sendto
16-Apr-2008 10:13:00.488 client 192.168.4.3#32773: senddone
16-Apr-2008 10:13:00.488 client 192.168.4.3#32773: next
16-Apr-2008 10:13:00.488 client 192.168.4.3#32773: ns_client_detach: ref = 0
16-Apr-2008 10:13:00.488 client 192.168.4.3#32773: endrequest
16-Apr-2008 10:13:00.488 client @0xb60a2008: udprecv
16-Apr-2008 10:13:01.569 client 192.168.4.3#32773: UDP request
16-Apr-2008 10:13:01.569 client 192.168.4.3#32773: using view '_default'
16-Apr-2008 10:13:01.569 client 192.168.4.3#32773: request is not signed
16-Apr-2008 10:13:01.569 client 192.168.4.3#32773: recursion available
16-Apr-2008 10:13:01.569 client 192.168.4.3#32773: query
16-Apr-2008 10:13:01.569 client 192.168.4.3#32773: ns_client_attach: ref = 1
16-Apr-2008 10:13:01.570 client 192.168.4.3#32773: query '253.0.0.10.in-addr.arpa/PTR/IN' approved
16-Apr-2008 10:13:01.570 client 192.168.4.3#32773: send
16-Apr-2008 10:13:01.570 client 192.168.4.3#32773: sendto
16-Apr-2008 10:13:01.570 client 192.168.4.3#32773: senddone
16-Apr-2008 10:13:01.570 client 192.168.4.3#32773: next
16-Apr-2008 10:13:01.570 client 192.168.4.3#32773: ns_client_detach: ref = 0
16-Apr-2008 10:13:01.570 client 192.168.4.3#32773: endrequest
16-Apr-2008 10:13:01.570 client @0xb60a2008: udprecv
16-Apr-2008 10:13:03.820 client 192.168.4.3#32773: UDP request
16-Apr-2008 10:13:03.820 client 192.168.4.3#32773: using view '_default'
16-Apr-2008 10:13:03.820 client 192.168.4.3#32773: request is not signed
16-Apr-2008 10:13:03.820 client 192.168.4.3#32773: recursion available
16-Apr-2008 10:13:03.821 client 192.168.4.3#32773: query
16-Apr-2008 10:13:03.821 client 192.168.4.3#32773: ns_client_attach: ref = 1
16-Apr-2008 10:13:03.821 client 192.168.4.3#32773: query '253.0.0.10.in-addr.arpa/PTR/IN' approved
16-Apr-2008 10:13:03.821 client 192.168.4.3#32773: send
16-Apr-2008 10:13:03.821 client 192.168.4.3#32773: sendto
16-Apr-2008 10:13:03.821 client 192.168.4.3#32773: senddone
16-Apr-2008 10:13:03.821 client 192.168.4.3#32773: next
16-Apr-2008 10:13:03.821 client 192.168.4.3#32773: ns_client_detach: ref = 0
16-Apr-2008 10:13:03.821 client 192.168.4.3#32773: endrequest
16-Apr-2008 10:13:03.821 client @0xb60a2008: udprecv
16-Apr-2008 10:13:04.672 client 192.168.4.3#32773: UDP request
16-Apr-2008 10:13:04.672 client 192.168.4.3#32773: using view '_default'
16-Apr-2008 10:13:04.672 client 192.168.4.3#32773: request is not signed
16-Apr-2008 10:13:04.673 client 192.168.4.3#32773: recursion available
16-Apr-2008 10:13:04.673 client 192.168.4.3#32773: query
16-Apr-2008 10:13:04.673 client 192.168.4.3#32773: ns_client_attach: ref = 1
16-Apr-2008 10:13:04.673 client 192.168.4.3#32773: query '252.0.0.10.in-addr.arpa/PTR/IN' approved
16-Apr-2008 10:13:04.673 client 192.168.4.3#32773: send
16-Apr-2008 10:13:04.673 client 192.168.4.3#32773: sendto
16-Apr-2008 10:13:04.674 client 192.168.4.3#32773: senddone
16-Apr-2008 10:13:04.674 client 192.168.4.3#32773: next
16-Apr-2008 10:13:04.674 client 192.168.4.3#32773: ns_client_detach: ref = 0
16-Apr-2008 10:13:04.674 client 192.168.4.3#32773: endrequest
16-Apr-2008 10:13:04.674 client @0xb60a2008: udprecv
16-Apr-2008 10:13:06.697 client 192.168.4.3#32773: UDP request
16-Apr-2008 10:13:06.698 client 192.168.4.3#32773: using view '_default'
16-Apr-2008 10:13:06.698 client 192.168.4.3#32773: request is not signed
16-Apr-2008 10:13:06.698 client 192.168.4.3#32773: recursion available
16-Apr-2008 10:13:06.698 client 192.168.4.3#32773: query
16-Apr-2008 10:13:06.698 client 192.168.4.3#32773: ns_client_attach: ref = 1
16-Apr-2008 10:13:06.698 client 192.168.4.3#32773: query '252.0.0.10.in-addr.arpa/PTR/IN' approved
16-Apr-2008 10:13:06.698 client 192.168.4.3#32773: send
16-Apr-2008 10:13:06.698 client 192.168.4.3#32773: sendto
16-Apr-2008 10:13:06.698 client 192.168.4.3#32773: senddone
16-Apr-2008 10:13:06.698 client 192.168.4.3#32773: next
16-Apr-2008 10:13:06.698 client 192.168.4.3#32773: ns_client_detach: ref = 0
16-Apr-2008 10:13:06.699 client 192.168.4.3#32773: endrequest
16-Apr-2008 10:13:06.699 client @0xb60a2008: udprecv
16-Apr-2008 10:13:08.941 client 192.168.4.3#32773: UDP request
16-Apr-2008 10:13:08.941 client 192.168.4.3#32773: using view '_default'
16-Apr-2008 10:13:08.941 client 192.168.4.3#32773: request is not signed
16-Apr-2008 10:13:08.941 client 192.168.4.3#32773: recursion available
16-Apr-2008 10:13:08.941 client 192.168.4.3#32773: query
16-Apr-2008 10:13:08.941 client 192.168.4.3#32773: ns_client_attach: ref = 1
16-Apr-2008 10:13:08.942 client 192.168.4.3#32773: query '252.0.0.10.in-addr.arpa/PTR/IN' approved
16-Apr-2008 10:13:08.942 client 192.168.4.3#32773: send
16-Apr-2008 10:13:08.942 client 192.168.4.3#32773: sendto
16-Apr-2008 10:13:08.942 client 192.168.4.3#32773: senddone
16-Apr-2008 10:13:08.942 client 192.168.4.3#32773: next
16-Apr-2008 10:13:08.942 client 192.168.4.3#32773: ns_client_detach: ref = 0
16-Apr-2008 10:13:08.942 client 192.168.4.3#32773: endrequest
16-Apr-2008 10:13:08.942 client @0xb60a2008: udprecv

```

Running the following doesn't show anything abnormal either:


```
sudo dhcpd3 -d -f 2>&1 | tee dhcp3.log
Internet Systems Consortium DHCP Server V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/
WARNING: Host declarations are global.  They are not limited to the scope you declared them in.
Wrote 0 deleted host decls to leases file.
Wrote 0 new dynamic host decls to leases file.
Wrote 3 leases to leases file.
Listening on LPF/eth0/00:d0:b7:4a:eb:17/192.168.4/24
Sending on   LPF/eth0/00:d0:b7:4a:eb:17/192.168.4/24
Sending on   Socket/fallback/fallback-net
DHCPDISCOVER from 00:12:25:03:5b:06 via 10.0.0.1
DHCPOFFER on 10.0.0.253 to 00:12:25:03:5b:06 via 10.0.0.1
DHCPDISCOVER from 00:0a:73:9a:56:ca via 10.0.0.1
DHCPOFFER on 10.0.0.254 to 00:0a:73:9a:56:ca via 10.0.0.1
DHCPREQUEST for 10.0.0.253 (192.168.4.3) from 00:12:25:03:5b:06 via 10.0.0.1
DHCPACK on 10.0.0.253 to 00:12:25:03:5b:06 via 10.0.0.1
DHCPREQUEST for 10.0.0.254 (192.168.4.3) from 00:0a:73:9a:56:ca via 10.0.0.1
DHCPACK on 10.0.0.254 to 00:0a:73:9a:56:ca via 10.0.0.1
DHCPDISCOVER from 00:1b:d7:09:de:f8 via 10.0.0.1
DHCPOFFER on 10.0.0.252 to 00:1b:d7:09:de:f8 via 10.0.0.1
DHCPREQUEST for 10.0.0.252 (192.168.4.3) from 00:1b:d7:09:de:f8 via 10.0.0.1
DHCPACK on 10.0.0.252 to 00:1b:d7:09:de:f8 via 10.0.0.1

```

Doing a tail -f on /var/log/messages syslog and daemon.log does not show any errors being reported by either BIND or DHCP.

Also, manually adding A records in the forward lookup file works correctly.

---

### Post by twistedtwig on 2008-04-17
i am at a lose then I am afraid.  I have had some issues where bind was not adding reverse mapping and stuff like that but it always put records into daemon.log (or message) can't remember.  

Hopefully someone more experienced than my self could help.

GL

---

