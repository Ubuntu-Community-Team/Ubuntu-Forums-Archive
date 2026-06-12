---
title: "Bind 9 Slave zone records not being transferred"
date: 2020-11-23
forum: Server Platforms
---

### Post by modsbyus on 2020-11-23
I have a Master Bind 9 server setup and am trying to get it to transfer its records to the slave. The zones are transferred but not the records. I get notify messages but the slave says no serial. When the master is sending the notifies it shows a serial. The serials are being incremented on the master when changes are made. Both master and slave are on public IPs and I am using the UFW, allowing port 53 in and out and have allowed all to and from master and slave on both master and slave. I am and have to use webmin for management. If I have missed giving any information please just ask.

Master RNDC Status:
```
version: BIND 9.16.1-Ubuntu (Stable Release) <id:d497c32>
running on ns0.telpage.net: Linux x86_64 5.4.0-52-generic #57-Ubuntu SMP Thu Oct 15 10:57:00 UTC 2020
boot time: Thu, 19 Nov 2020 21:36:18 GMT
last configured: Thu, 19 Nov 2020 21:36:18 GMT
configuration file: /etc/bind/named.conf
CPUs found: 2
worker threads: 2
UDP listeners per interface: 2
number of zones: 148 (97 automatic)
debug level: 0
xfers running: 0
xfers deferred: 0
soa queries in progress: 0
query logging is OFF
recursive clients: 0/900/1000
tcp clients: 6/150
TCP high-water: 23
server is up and running
```

Slave RNDC Status:
```
version: BIND 9.16.1-Ubuntu (Stable Release) <id:d497c32>
running on ns2.telpage.net: Linux x86_64 5.4.0-54-generic #60-Ubuntu SMP Fri Nov 6 10:37:59 UTC 2020
boot time: Thu, 19 Nov 2020 18:59:43 GMT
last configured: Thu, 19 Nov 2020 18:59:43 GMT
configuration file: /etc/bind/named.conf
CPUs found: 4
worker threads: 4
UDP listeners per interface: 4
number of zones: 146 (99 automatic)
debug level: 0
xfers running: 0
xfers deferred: 0
soa queries in progress: 0
query logging is OFF
recursive clients: 53/900/1000
tcp clients: 0/150
TCP high-water: 0
server is up and running
```

```
Master:
ns0 named[4082195]: zone jlwalston.com/IN: sending notifies (serial 1603727618)

Slave:
notify: info: client @0x7f51f0043980 192.40.120.9#33347/key 1: received notify for zone 'jlwalston.com': TSIG '1'
general: info: zone jlwalston.com/IN: notify from 192.40.120.9#33347: no serial
```

Configs:
```
Slave:

Named.conf
include "/etc/bind/named.conf.options";
include "/etc/bind/named.conf.local";
include "/etc/bind/named.conf.default-zones";
key rndc-key {
	algorithm hmac-sha256;
	secret "Changed";
	};
controls {
	inet 192.40.120.10 port 953 allow { 192.40.120.10; 192.40.120.9; } keys { rndc-key; 1; };
	};
server 192.40.120.9 {
	keys {
		1;
		};
	};
key 1 {
	algorithm hmac-md5;
	secret "Changed";
	};
logging{
  channel xfer_in {
    file "/var/log/bind/xfer-in.log" versions 3 size 5m;
    severity debug;
    print-time yes;
    print-severity yes;
    print-category yes;
  };
  channel simple_log {
    file "/var/log/bind/bind.log" versions 3 size 5m;
    severity info;
    print-time yes;
    print-severity yes;
    print-category yes;
  };
  category default{
    simple_log;
  };  
  category xfer-in{
    xfer_in;
  };
  category lame-servers { null; };

};
named.conf.options
options {
	directory "/var/cache/bind";

	// If there is a firewall between you and nameservers you want
	// to talk to, you may need to fix the firewall to allow multiple
	// ports to talk.  See http://www.kb.cert.org/vuls/id/800113

	// If your ISP provided one or more IP addresses for stable 
	// nameservers, you probably want to use them as forwarders.  
	// Uncomment the following block, and insert the addresses replacing 
	// the all-0's placeholder.

	// forwarders {
	// 	0.0.0.0;
	// };

	//========================================================================
	// If BIND logs error messages about the root key being expired,
	// you will need to update your keys.  See https://www.isc.org/bind-keys
	//========================================================================
	dnssec-validation auto;
	listen-on port 53 {
		192.40.120.10;
		};
	listen-on-v6 { any; };
    querylog yes;
	transfer-source 192.40.120.9;
	allow-query {
		any;
		};
	forwarders {
		192.40.120.9;
		208.74.83.90;
		208.74.83.70;
		};
    allow-notify { 192.40.120.9; };
	allow-transfer {
		192.40.120.9;
		};
};
named.conf.local
//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";
zone "amandajoneslaw.com" {
	type slave;
	masters {
		192.40.120.9;
		};
	file "/var/lib/bind/amandajoneslaw.com.hosts";
	allow-transfer {
		192.40.120.9;
		};
	};
zone "brunswickco.com" {
	type slave;
	masters {
		192.40.120.9;
		};
	file "/var/lib/bind/brunswickco.com.hosts";
	allow-transfer {
		192.40.120.9;
		};
	};
zone "buckwaterplantation.com" {
	type slave;
	masters {
		192.40.120.9;
		};
	file "/var/lib/bind/buckwaterplantation.com.hosts";
	allow-transfer {
		192.40.120.9;
		};
	};
zone "chapmanlumber.com" {
	type slave;
	masters {
		192.40.120.9;
		};
	file "/var/lib/bind/chapmanlumber.com.hosts";
	allow-transfer {
		192.40.120.9;
		};
	};
zone "consciencestream.com" {
	type slave;
	masters {
		192.40.120.9;
		};
	file "/var/lib/bind/consciencestream.com.hosts";
	allow-transfer {
		192.40.120.9;
		};
	};
zone "dickensconstruction.com" {
	type slave;
	masters {
		192.40.120.9;
		};
	file "/var/lib/bind/dickensconstruction.com.hosts";
	allow-transfer {
		192.40.120.9;
		};
	};
zone "elliottsadler.com" {
	type slave;
	masters {
		192.40.120.9;
		};
	file "/var/lib/bind/elliottsadler.com.hosts";
	allow-transfer {
		192.40.120.9;
		};
	};
zone "emporiaciviccenter.org" {
	type slave;
	masters {
		192.40.120.9;
		};
	file "/var/lib/bind/emporiaciviccenter.org.hosts";
	allow-transfer {
		192.40.120.9;
		};
	};
zone "emporiamedical.com" {
	type slave;
	masters {
		192.40.120.9;
		};
	file "/var/lib/bind/emporiamedical.com.hosts";
	allow-transfer {
		192.40.120.9;
		};
	};
zone "emporianews.com" {
	type slave;
	masters {
		192.40.120.9;
		};
	file "/var/lib/bind/emporianews.com.hosts";
	allow-transfer {
		192.40.120.9;
		};
	};
zone "flyemv.com" {
	type slave;
	masters {
		192.40.120.9;
		};
	file "/var/lib/bind/flyemv.com.hosts";
	allow-transfer {
		192.40.120.9;
		};
	};
zone "flyemv.org" {
	type slave;
	masters {
		192.40.120.9;
		};
	file "/var/lib/bind/flyemv.org.hosts";
	allow-transfer {
		192.40.120.9;
		};
	};
zone "franklinbraid.com" {
	type slave;
	masters {
		192.40.120.9;
		};
	file "/var/lib/bind/franklinbraid.com.hosts";
	allow-transfer {
		192.40.120.9;
		};
	};
zone "goodearthpeanuts.com" {
	type slave;
	masters {
		192.40.120.9;
		};
	file "/var/lib/bind/goodearthpeanuts.com.hosts";
	allow-transfer {
		192.40.120.9;
		};
	};
zone "greensvillecountyva.gov" {
	type slave;
	masters {
		192.40.120.9;
		};
	file "/var/lib/bind/greensvillecountyva.gov.hosts";
	allow-transfer {
		192.40.120.9;
		};
	};
zone "jarrattfire.org" {
	type slave;
	masters {
		192.40.120.9;
		};
	file "/var/lib/bind/jarrattfire.org.hosts";
	allow-transfer {
		192.40.120.9;
		};
	};
zone "jlwalston.com" {
	type slave;
	masters {
		192.40.120.9;
		};
	file "/var/lib/bind/jlwalston.com.hosts";
	allow-transfer {
		192.40.120.9;
		};
	};
zone "jrallpc.com" {
	type slave;
	masters {
		192.40.120.9;
		};
	file "/var/lib/bind/jrallpc.com.hosts";
	allow-transfer {
		192.40.120.9;
		};
	};
zone "lakegastonassoc.com" {
	type slave;
	masters {
		192.40.120.9;
		};
	file "/var/lib/bind/lakegastonassoc.com.hosts";
	allow-transfer {
		192.40.120.9;
		};
	};
zone "lastday.net" {
	type slave;
	masters {
		192.40.120.9;
		};
	file "/var/lib/bind/lastday.net.hosts";
	allow-transfer {
		192.40.120.9;
		};
	};
zone "lgaston.org" {
	type slave;
	masters {
		192.40.120.9;
		};
	file "/var/lib/bind/lgaston.org.hosts";
	allow-transfer {
		192.40.120.9;
		};
	};
zone "midatlanticinfosec.com" {
	type slave;
	masters {
		192.40.120.9;
		};
	file "/var/lib/bind/midatlanticinfosec.com.hosts";
	allow-transfer {
		192.40.120.9;
		};
	};
zone "midatlantictower.com" {
	type slave;
	masters {
		192.40.120.9;
		};
	file "/var/lib/bind/midatlantictower.com.hosts";
	allow-transfer {
		192.40.120.9;
		};
	};
zone "modsbyus.com" {
	type slave;
	masters {
		192.40.120.9;
		};
	file "/var/lib/bind/modsbyus.com.hosts";
	allow-transfer {
		192.40.120.9;
		};
	};
zone "motorolaradio.com" {
	type slave;
	masters {
		192.40.120.9;
		};
	file "/var/lib/bind/motorolaradio.com.hosts";
	allow-transfer {
		192.40.120.9;
		};
	};
zone "naynaysartbox.com" {
	type slave;
	masters {
		192.40.120.9;
		};
	file "/var/lib/bind/naynaysartbox.com.hosts";
	allow-transfer {
		192.40.120.9;
		};
	};
zone "omnitowers.com" {
	type slave;
	masters {
		192.40.120.9;
		};
	file "/var/lib/bind/omnitowers.com.hosts";
	allow-transfer {
		192.40.120.9;
		};
	};
zone "osg-armor.com" {
	type slave;
	masters {
		192.40.120.9;
		};
	file "/var/lib/bind/osg-armor.com.hosts";
	allow-transfer {
		192.40.120.9;
		};
	};
zone "sadlerbrosoil.com" {
	type slave;
	masters {
		192.40.120.9;
		};
	file "/var/lib/bind/sadlerbrosoil.com.hosts";
	allow-transfer {
		192.40.120.9;
		};
	};
zone "sadlerfanclub.com" {
	type slave;
	masters {
		192.40.120.9;
		};
	file "/var/lib/bind/sadlerfanclub.com.hosts";
	allow-transfer {
		192.40.120.9;
		};
	};
zone "southsideccjb.com" {
	type slave;
	masters {
		192.40.120.9;
		};
	file "/var/lib/bind/southsideccjb.com.hosts";
	allow-transfer {
		192.40.120.9;
		};
	};
zone "telpage.com" {
	type slave;
	masters {
		192.40.120.9;
		};
	file "/var/lib/bind/telpage.com.hosts";
	allow-transfer {
		192.40.120.9;
		};
	};
zone "telpage.net" {
	type slave;
	masters {
		192.40.120.9;
		};
	file "/var/lib/bind/telpage.net.hosts";
	allow-transfer {
		192.40.120.9;
		};
	};
zone "thevirginiapeanutfestival.com" {
	type slave;
	masters {
		192.40.120.9;
		};
	file "/var/lib/bind/thevirginiapeanutfestival.com.hosts";
	allow-transfer {
		192.40.120.9;
		};
	};
zone "virginiacarolina.com" {
	type slave;
	masters {
		192.40.120.9;
		};
	file "/var/lib/bind/virginiacarolina.com.hosts";
	allow-transfer {
		192.40.120.9;
		};
	};
zone "whitman-properties.com" {
	type slave;
	masters {
		192.40.120.9;
		};
	file "/var/lib/bind/whitman-properties.com.hosts";
	allow-transfer {
		192.40.120.9;
		};
	};
zone "wrobinsonlaw.com" {
	type slave;
	masters {
		192.40.120.9;
		};
	file "/var/lib/bind/wrobinsonlaw.com.hosts";
	allow-transfer {
		192.40.120.9;
		};
	};
zone "ymcaofeg.org" {
	type slave;
	masters {
		192.40.120.9;
		};
	file "/var/lib/bind/ymcaofeg.org.hosts";
	allow-transfer {
		192.40.120.9;
		};
	};
zone "120.40.192.in-addr.arpa" {
	type slave;
	masters {
		192.40.120.9;
		};
	allow-transfer {
		192.40.120.9;
		};
	file "/var/lib/bind/192.40.120.rev";
	};
zone "121.40.192.in-addr.arpa" {
	type slave;
	masters {
		192.40.120.9;
		};
	allow-transfer {
		192.40.120.9;
		};
	file "/var/lib/bind/192.40.121.rev";
	};
zone "122.40.192.in-addr.arpa" {
	type slave;
	masters {
		192.40.120.9;
		};
	allow-transfer {
		192.40.120.9;
		};
	file "/var/lib/bind/192.40.122.rev";
	};
zone "123.40.192.in-addr.arpa" {
	type slave;
	masters {
		192.40.120.9;
		};
	allow-transfer {
		192.40.120.9;
		};
	file "/var/lib/bind/192.40.123.rev";
	};
zone "124.40.192.in-addr.arpa" {
	type slave;
	masters {
		192.40.120.9;
		};
	allow-transfer {
		192.40.120.9;
		};
	file "/var/lib/bind/192.40.124.rev";
	};
zone "125.40.192.in-addr.arpa" {
	type slave;
	masters {
		192.40.120.9;
		};
	allow-transfer {
		192.40.120.9;
		};
	file "/var/lib/bind/192.40.125.rev";
	};
zone "126.40.192.in-addr.arpa" {
	type slave;
	masters {
		192.40.120.9;
		};
	allow-transfer {
		192.40.120.9;
		};
	file "/var/lib/bind/192.40.126.rev";
	};
zone "127.40.192.in-addr.arpa" {
	type slave;
	masters {
		192.40.120.9;
		};
	allow-transfer {
		192.40.120.9;
		};
	file "/var/lib/bind/192.40.127.rev";
	};
Master:

named.conf
include "/etc/bind/named.conf.options";
include "/etc/bind/named.conf.local";
include "/etc/bind/named.conf.default-zones";
key 1 {
	algorithm hmac-md5;
	secret "Changed";
	};
server 192.40.120.10 {
	keys {
		1;
		};
	};
controls {
	inet 192.40.120.9 port 953 allow { 192.40.120.9; 192.40.120.10; } keys { rndc-key; 1; };
	};
key rndc-key {
	algorithm hmac-sha256;
	secret "Changed";
	};
named.conf.options
options {
	directory "/var/cache/bind";

	// If there is a firewall between you and nameservers you want
	// to talk to, you may need to fix the firewall to allow multiple
	// ports to talk.  See http://www.kb.cert.org/vuls/id/800113

	// If your ISP provided one or more IP addresses for stable 
	// nameservers, you probably want to use them as forwarders.  
	// Uncomment the following block, and insert the addresses replacing 
	// the all-0's placeholder.

	// forwarders {
	// 	0.0.0.0;
	// };

	//========================================================================
	// If BIND logs error messages about the root key being expired,
	// you will need to update your keys.  See https://www.isc.org/bind-keys
	//========================================================================
	dnssec-validation auto;

	listen-on-v6 { any; };
	forwarders {
		208.74.83.90;
		208.74.83.70;
		};
	forward first;
	allow-recursion {
		192.40.120.0/24;
		192.40.121.0/24;
		192.40.122.0/24;
		192.40.123.0/24;
		192.40.124.0/24;
		192.40.125.0/24;
		192.40.126.0/24;
		192.40.127.0/24;
		};
	allow-query {
		any;
		};
	dnssec-enable yes;
	also-notify {
		192.40.120.10;
		};
    allow-transfer {
    	192.40.120.10;
        };
	notify yes;
	auth-nxdomain no;
};
named.conf.local
//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

zone "telpage.net" {
	type master;
	file "/var/lib/bind/telpage.net.hosts";
	also-notify {
		192.40.120.10;
		};
    allow-transfer {
		192.40.120.10;
		};
	notify yes;
	};
zone "amandajoneslaw.com" {
	type master;
	file "/var/lib/bind/amandajoneslaw.com.hosts";
	also-notify {
		192.40.120.10;
		};
	notify yes;
	};
zone "brunswickco.com" {
	type master;
	file "/var/lib/bind/brunswickco.com.hosts";
	allow-transfer {
		192.40.120.10;
		};
    also-notify {
		192.40.120.10;
		};
	notify yes;
	};
zone "buckwaterplantation.com" {
	type master;
	file "/var/lib/bind/buckwaterplantation.com.hosts";
	allow-transfer {
		192.40.120.10;
		};
    also-notify {
		192.40.120.10;
		};
	notify yes;
	};
zone "chapmanlumber.com" {
	type master;
	file "/var/lib/bind/chapmanlumber.com.hosts";
	allow-transfer {
		192.40.120.10;
		};
    also-notify {
		192.40.120.10;
		};
	notify yes;
	};
zone "consciencestream.com" {
	type master;
	file "/var/lib/bind/consciencestream.com.hosts";
	allow-transfer {
		192.40.120.10;
		};
    also-notify {
		192.40.120.10;
		};
	notify yes;
	};
zone "dickensconstruction.com" {
	type master;
	file "/var/lib/bind/dickensconstruction.com.hosts";
	allow-transfer {
		192.40.120.10;
		};
    also-notify {
		192.40.120.10;
		};
	notify yes;
	};
zone "elliottsadler.com" {
	type master;
	file "/var/lib/bind/elliottsadler.com.hosts";
	allow-transfer {
		192.40.120.10;
		};
    also-notify {
		192.40.120.10;
		};
	notify yes;
	};
zone "emporiaciviccenter.org" {
	type master;
	file "/var/lib/bind/emporiaciviccenter.org.hosts";
	allow-transfer {
		192.40.120.10;
		};
    also-notify {
		192.40.120.10;
		};
	notify yes;
	};
zone "emporiamedical.com" {
	type master;
	file "/var/lib/bind/emporiamedical.com.hosts";
	allow-transfer {
		192.40.120.10;
		};
    also-notify {
		192.40.120.10;
		};
	notify yes;
	};
zone "emporianews.com" {
	type master;
	file "/var/lib/bind/emporianews.com.hosts";
	allow-transfer {
		192.40.120.10;
		};
    also-notify {
		192.40.120.10;
		};
	notify yes;
	};
zone "flyemv.com" {
	type master;
	file "/var/lib/bind/flyemv.com.hosts";
	allow-transfer {
		192.40.120.10;
		};
    also-notify {
		192.40.120.10;
		};
	notify yes;
	};
zone "flyemv.org" {
	type master;
	file "/var/lib/bind/flyemv.org.hosts";
	allow-transfer {
		192.40.120.10;
		};
    also-notify {
		192.40.120.10;
		};
	notify yes;
	};
zone "franklinbraid.com" {
	type master;
	file "/var/lib/bind/franklinbraid.com.hosts";
	allow-transfer {
		192.40.120.10;
		};
    also-notify {
		192.40.120.10;
		};
	notify yes;
	};
zone "goodearthpeanuts.com" {
	type master;
	file "/var/lib/bind/goodearthpeanuts.com.hosts";
	allow-transfer {
		192.40.120.10;
		};
    also-notify {
		192.40.120.10;
		};
	notify yes;
	};
zone "greensvillecountyva.gov" {
	type master;
	file "/var/lib/bind/greensvillecountyva.gov.hosts";
	allow-transfer {
		192.40.120.10;
		};
    also-notify {
		192.40.120.10;
		};
	notify yes;
	};
zone "jarrattfire.org" {
	type master;
	file "/var/lib/bind/jarrattfire.org.hosts";
	allow-transfer {
		192.40.120.10;
		};
    also-notify {
		192.40.120.10;
		};
	notify yes;
	};
zone "jlwalston.com" {
	type master;
	file "/var/lib/bind/jlwalston.com.hosts";
	allow-transfer {
		192.40.120.10;
		};
    also-notify {
		192.40.120.10;
		};
	notify yes;
	};
zone "jrallpc.com" {
	type master;
	file "/var/lib/bind/jrallpc.com.hosts";
	allow-transfer {
		192.40.120.10;
		};
    also-notify {
		192.40.120.10;
		};
	notify yes;
	};
zone "lakegastonassoc.com" {
	type master;
	file "/var/lib/bind/lakegastonassoc.com.hosts";
	allow-transfer {
		192.40.120.10;
		};
    also-notify {
		192.40.120.10;
		};
	notify yes;
	};
zone "lastday.net" {
	type master;
	file "/var/lib/bind/lastday.net.hosts";
	allow-transfer {
		192.40.120.10;
		};
    also-notify {
		192.40.120.10;
		};
	notify yes;
	};
zone "lgaston.org" {
	type master;
	file "/var/lib/bind/lgaston.org.hosts";
	allow-transfer {
		192.40.120.10;
		};
    also-notify {
		192.40.120.10;
		};
	notify yes;
	};
zone "midatlanticinfosec.com" {
	type master;
	file "/var/lib/bind/midatlanticinfosec.com.hosts";
	allow-transfer {
		192.40.120.10;
		};
    also-notify {
		192.40.120.10;
		};
	notify yes;
	};
zone "midatlantictower.com" {
	type master;
	file "/var/lib/bind/midatlantictower.com.hosts";
	allow-transfer {
		192.40.120.10;
		};
    also-notify {
		192.40.120.10;
		};
	notify yes;
	};
zone "modsbyus.com" {
	type master;
	file "/var/lib/bind/modsbyus.com.hosts";
	allow-transfer {
		192.40.120.10;
		};
    also-notify {
		192.40.120.10;
		};
	notify yes;
	};
zone "motorolaradio.com" {
	type master;
	file "/var/lib/bind/motorolaradio.com.hosts";
	allow-transfer {
		192.40.120.10;
		};
    also-notify {
		192.40.120.10;
		};
	notify yes;
	};
zone "naynaysartbox.com" {
	type master;
	file "/var/lib/bind/naynaysartbox.com.hosts";
	allow-transfer {
		192.40.120.10;
		};
    also-notify {
		192.40.120.10;
		};
	notify yes;
	};
zone "omnitowers.com" {
	type master;
	file "/var/lib/bind/omnitowers.com.hosts";
	allow-transfer {
		192.40.120.10;
		};
    also-notify {
		192.40.120.10;
		};
	notify yes;
	};
zone "osg-armor.com" {
	type master;
	file "/var/lib/bind/osg-armor.com.hosts";
	allow-transfer {
		192.40.120.10;
		};
    also-notify {
		192.40.120.10;
		};
	notify yes;
	};
zone "sadlerbrosoil.com" {
	type master;
	file "/var/lib/bind/sadlerbrosoil.com.hosts";
	allow-transfer {
		192.40.120.10;
		};
    also-notify {
		192.40.120.10;
		};
	notify yes;
	};
zone "sadlerfanclub.com" {
	type master;
	file "/var/lib/bind/sadlerfanclub.com.hosts";
	allow-transfer {
		192.40.120.10;
		};
    also-notify {
		192.40.120.10;
		};
	notify yes;
	};
zone "southsideccjb.com" {
	type master;
	file "/var/lib/bind/southsideccjb.com.hosts";
	allow-transfer {
		192.40.120.10;
		};
    also-notify {
		192.40.120.10;
		};
	notify yes;
	};
zone "telpage.com" {
	type master;
	file "/var/lib/bind/telpage.com.hosts";
	allow-transfer {
		192.40.120.10;
		};
    also-notify {
		192.40.120.10;
		};
	notify yes;
	};
zone "thevirginiapeanutfestival.com" {
	type master;
	file "/var/lib/bind/thevirginiapeanutfestival.com.hosts";
	allow-transfer {
		192.40.120.10;
		};
    also-notify {
		192.40.120.10;
		};
	notify yes;
	};
zone "virginiacarolina.com" {
	type master;
	file "/var/lib/bind/virginiacarolina.com.hosts";
	allow-transfer {
		192.40.120.10;
		};
    also-notify {
		192.40.120.10;
		};
	notify yes;
	};
zone "whitman-properties.com" {
	type master;
	file "/var/lib/bind/whitman-properties.com.hosts";
	allow-transfer {
		192.40.120.10;
		};
    also-notify {
		192.40.120.10;
		};
	notify yes;
	};
zone "wrobinsonlaw.com" {
	type master;
	file "/var/lib/bind/wrobinsonlaw.com.hosts";
	allow-transfer {
		192.40.120.10;
		};
    also-notify {
		192.40.120.10;
		};
	notify yes;
	};
zone "ymcaofeg.org" {
	type master;
	file "/var/lib/bind/ymcaofeg.org.hosts";
	allow-transfer {
		192.40.120.10;
		};
    also-notify {
		192.40.120.10;
		};
	notify yes;
	};
zone "120.40.192.in-addr.arpa" {
	type master;
	file "/var/lib/bind/192.40.120.rev";
	also-notify {
		192.40.120.10;
		};
	allow-transfer {
		192.40.120.10;
		};
	notify yes;
	};
zone "121.40.192.in-addr.arpa" {
	type master;
	file "/var/lib/bind/192.40.121.rev";
	also-notify {
		192.40.120.10;
		};
	allow-transfer {
		192.40.120.10;
		};
	notify yes;
	};
zone "122.40.192.in-addr.arpa" {
	type master;
	file "/var/lib/bind/192.40.122.rev";
	also-notify {
		192.40.120.10;
		};
	allow-transfer {
		192.40.120.10;
		};
	notify yes;
	};
zone "123.40.192.in-addr.arpa" {
	type master;
	file "/var/lib/bind/192.40.123.rev";
	also-notify {
		192.40.120.10;
		};
	allow-transfer {
		192.40.120.10;
		};
	notify yes;
	};
zone "124.40.192.in-addr.arpa" {
	type master;
	file "/var/lib/bind/192.40.124.rev";
	also-notify {
		192.40.120.10;
		};
	allow-transfer {
		192.40.120.10;
		};
	notify yes;
	};
zone "125.40.192.in-addr.arpa" {
	type master;
	file "/var/lib/bind/192.40.125.rev";
	also-notify {
		192.40.120.10;
		};
	allow-transfer {
		192.40.120.10;
		};
	notify yes;
	};
zone "126.40.192.in-addr.arpa" {
	type master;
	file "/var/lib/bind/192.40.126.rev";
	also-notify {
		192.40.120.10;
		};
	allow-transfer {
		192.40.120.10;
		};
	notify yes;
	};
zone "127.40.192.in-addr.arpa" {
	type master;
	file "/var/lib/bind/192.40.127.rev";
	also-notify {
		192.40.120.10;
		};
	allow-transfer {
		192.40.120.10;
		};
	notify yes;
	};
```

---

### Post by darkod on 2020-11-23
I couldn't read the whole setup because there is much text, but I think your setup on the slave is incorrect. The allow-transfer and allow-notify options go on the master, not the slave.

I haven't done much DNS servers but the basic instructions from ubuntu always worked for me. Read carefully here:
[https://ubuntu.com/server/docs/service-domain-name-service-dns](https://ubuntu.com/server/docs/service-domain-name-service-dns)

And also, I don't have much faith in webmin but if you say you have to use it...

---

### Post by modsbyus on 2020-11-23
Okay, So following the guide at [https://ubuntu.com/server/docs/servi...me-service-dns]("https://ubuntu.com/server/docs/servi...me-service-dns") I still have the same problem. No transfer ever even shows up in the logs and each notify message in the master logs shows a serial number but on the slave the notify messages all end with no serial. Im pretty sure that the slave not getting the serial is the issue but I don't know where else to look for the culprit.

---

### Post by darkod on 2020-11-23
Please post your current named.conf.local from master and slave, but select only one zone and post only its setup. That way it will be easier to follow.

If you get it working for one zone your can replicate the setup to the rest.

---

### Post by modsbyus on 2020-11-23
Master:
```
zone "telpage.net" {
	type master;
	file "/var/lib/bind/telpage.net.hosts";
	also-notify {
		192.40.120.10;
		};
    allow-transfer {
		192.40.120.10;
		};
	notify yes;
	};
```

Slave:
```
zone "telpage.net" {
	type slave;
	masters {
		192.40.120.9;
		};
	file "/var/lib/bind/telpage.net.hosts";
	};
```

---

### Post by darkod on 2020-11-23
It looks OK, but for easier reading I would do it like this (it is allowed):
```
zone "telpage.net" {
    type master;
    file "/var/lib/bind/telpage.net.hosts";
    also-notify { 192.40.120.10; };
    allow-transfer { 192.40.120.10; };
    notify yes;
};
```

Also, check named.conf.options on the slave and remove the allow-transfer and allow-notify lines there. According to your post #1 you have those lines in the general options but they shouldn't be on the slave.

Don't forget to restart the bind9 service each time you do changes.

If it still doesn't work post the current /var/lib/bind/telpage.net.hosts file from both master and slave for comparison.

If after evrything it still doesn't work, I would suggest to purge bind and start from zero. First set up the basics and make sure they work, and after you can tune more specific settings according to your needs. And that way you can also know which setting "broke" it and look for solution. Right now you are unsure why it doesn't work.

---

### Post by modsbyus on 2020-11-24
I removed those statements from named.conf.options when you suggested removing from named.conf.local.
The hosts record for the telpage zone is large. I'm presenting a different zone for that reason. The hosts files have not been created on the slave. I tried manually creating them one time and after restarting bind  I ended up with this in /var/lib/bind
```
db-0diKPIsd  db-4yt5raLz  db-7iEQbJFa  db-AH06ciA1  db-bNsG25hV  db-d20awZwf  db-fbGMGRPQ  db-GikJuHaL  db-imgwEaoY  db-JRNuHuUX  db-mykDBrWA  db-Pkq7vAhG  db-rsdzz9Af  db-uFQ06yti  db-vL0Uo03D  db-x6IUy1Ox  db-Xzo0hYjL
db-0lCorgu2  db-5Vl0EXyu  db-7onioOTb  db-B0EwU1iE  db-bRYGRHlr  db-E10NEA02  db-FIi6covw  db-GxBSNF0w  db-IWSSgoGg  db-LJ3UfHkw  db-N4gckLsM  db-q6aGB2yt  db-SchXrDO4  db-UsytBwqZ  db-w4QxsvOq  db-x8yLXoyN  db-zAT0EEfI
db-0UmHnYrX  db-6iDjJ3LF  db-8AWQrjFN  db-BDrHLPLs  db-BwQEKQgZ  db-e7jEFYza  db-FkqQwqNA  db-gyaAHYVR  db-J54lHHTy  db-lJIvg8f6  db-nKuGCgwB  db-QfPEywQm  db-sjsQCsan  db-UZ9k0x9p  db-wPSH3kQB  db-XczlZnw1  db-ZDQXLruG
db-1o6kryku  db-6uI23Sh5  db-8m3GvHSp  db-BK6wOksW  db-C1tS82rN  db-eNtDBaDL  db-FzMTdfIg  db-H96NXjXE  db-Jb5Q473Y  db-LNmcBQAY  db-OLoJXT93  db-qypYqera  db-TCoMDaGh  db-UZTe2YJQ  db-WTJWBI0Y  db-XKEIk66X  db-zIL9NABd
db-4QRH1zkG  db-6VTaDhD0  db-AFwFSSZ8  db-BldXlM65  db-CZdrMF31  db-EuJVMemi  db-gIiNR3sG  db-IIcXb7oe  db-Ji8MqtEK  db-mEfHPRlB  db-pAgh1A9r  db-rEerRn5L  db-TPzSqTO6  db-V2boqV81  db-WZ8rIH8a  db-XSFSnXpb  db-zMuHl4KS
```

```
$ttl 3600
amandajoneslaw.com.     IN      SOA     ns0.telpage.net. techsupport.telpage.net. (
                        1603454507
                        3600
                        600
                        1209600
                        3600 )
amandajoneslaw.com.     IN      NS      ns0.telpage.net.
amandajoneslaw.com.     IN      NS      ns2.telpage.net.
amandajoneslaw.com.     IN      MX      10 telpage.net.mx1.rcimx.com.
amandajoneslaw.com.     IN      MX      20 telpage.net.mx2.rcimx.com.
amandajoneslaw.com.     IN      MX      30 telpage.net.mx3.rcimx.com.
amandajoneslaw.com.     IN      MX      40 telpage.net.mx4.rcimx.com.
```

---

### Post by modsbyus on 2020-11-24
I tried removing all zones and restarted bind on the slave. Now when I restart bind on the master,  the logs on the slave say
```
notify: notice: client @0x7f6cb0028950 192.40.120.9#57026/key 1: received notify for zone 'goodearthpeanuts.com': TSIG '1': not authoritative
```

---

### Post by modsbyus on 2020-11-24
I realized the reason I got the : not authoritative message was because the slave zones were not created on the slave. after adding the slave zone I am back to the no serial error.
I also went ahead and started over with the slave. I purged the bind install and made sure no directories or files were left over from previous install and then reinstalled and reconfigured.
Still same issue. I just don't get why the master would send the serial and the slave would say that on the notify message that there isn't one. I am going to try to reboot the master server tonight.

---

### Post by darkod on 2020-11-24
I have no ideas at this point. I hate to simply blame webmin but the fact remains that it is not recommended to use it and one can never be sure what it does in the background.

If you want to be sure you are doing everything right you can do quick test in VirtualBox or similar. Create two VMs and install basic ubuntu + bind. Setup one zone as per the Ubuntu Help docs and see if it syncs correctly between the master and the slave.

If that works I think it is safe to assume webmin is making some issues for you.

I don't lke the format of the serial either. But that shouldn't be a problem as long as it is incremented correctly. I prefer the format YYYYMMDDXX which is much easier to read. But again, it depends if you control the format of the serial at all and whether you edit the config files manually in the CLI or not.

Ubuntu server is what it is, linux server with CLI. I would dump webmin the first chance I have...

---

### Post by modsbyus on 2020-11-25
I will do that. Thank you for your help. One more question. My boss manages the DNS records and is fairly non technical.... They require a GUI. Do you have any suggestions for a GUI interface other than webmin?

---

### Post by darkod on 2020-11-25
I wouldn't know of any GUI to recommend. Since many years ago I stopped researching GUIs for ubuntu server and I have no idea what exists currently.

---

### Post by SeijiSensei on 2020-11-25
If you really need a GUI, you might look into whether your domain name provider offers such a service. For most people with just a single domain name, DNS management isn't worth the effort of setting up BIND9 on multiple servers. Let your DNS provider handle it all.

---

