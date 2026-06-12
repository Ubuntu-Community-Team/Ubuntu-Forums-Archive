---
title: "error in slave bind9"
date: 2018-08-16
forum: Server Platforms
---

### Post by santintin on 2018-08-16
Hi all,

I have three server with BIND version 9.10 over ubuntu server 16.04, I have configured one server like master and two others like slaves, it has working since two years ago with 31 domains with the same config, and the last domain I tried to add are not syncing with the slaves, in two slaves I have the same error (0.0.0.0 master ip - 1.1.1.1 slave ip)

Aug 16 14:56:25 slaveserver named[5073]: transfer of ‘domain.es/IN' from 0.0.0.0#53: connected using 1.1.1.1#59657
Aug 16 14:56:25 slaveserver named[5073]: transfer of 'domain.es/IN' from 0.0.0.0#53: failed while receiving responses: SERVFAIL
Aug 16 14:56:25 slaveserver named[5073]: transfer of 'domain.es/IN' from 0.0.0.0#53: Transfer status: SERVFAIL
Aug 16 14:56:25 slaveserver named[5073]: transfer of 'domain.es/IN' from 0.0.0.0#53: Transfer completed: 0 messages, 0 records, 0 bytes, 0.002 secs (0 bytes/sec)

the other domains still syncing without problems but the new domain remains unsynced, the server logs says (0.0.0.0 master ip - 1.1.1.1 slave ip)

Aug 16 15:30:28 masterserver named[29092]: zone domain.es/IN: sending notifies (serial 1934264406)

my config files in master server are:
**named.conf**
[INDENT]include "/etc/bind/named.conf.options";
include "/etc/bind/named.conf.default-zones";
include "/etc/bind/named.conf.local";
acl "slaves" { 
1.1.1.1;
2.2.2.2; 
}; 
acl recurseallow {
0.0.0.0;
1.1.1.1;
2.2.2.2; 
};[/INDENT]

**named.conf.options**
[INDENT]options {
directory "/var/cache/bind";
dnssec-validation auto;
auth-nxdomain no;    # conform to RFC1035
listen-on-v6 { any; };
allow-query { any; };
recursion no;
};[/INDENT]

**named.conf.default-zones**
[INDENT]zone "." {
	type hint;
	file "/etc/bind/db.root";
};
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
};[/INDENT]

**named.conf.local**
[INDENT]zone "domain.es" {
	type master;
	also-notify {
		1.1.1.1;
		2.2.2.2;
		};
	file "/var/lib/bind/domain.es.hosts";
	allow-query {
		any;
		};
	allow-transfer {
		127.0.0.1;
		};
	notify yes;
	};[/INDENT]
all the zones (working zones and this last no-working zone) have the same config.

and in the slave server the config files are:
**named.conf**
[INDENT]include "/etc/bind/named.conf.options";
include "/etc/bind/named.conf.default-zones";
include "/etc/bind/named.conf.local";
[/INDENT]

**named.conf.options**
[INDENT]options {
directory "/var/cache/bind";
auth-nxdomain no;    # conform to RFC1035
dnssec-validation auto;
listen-on-v6 { any; };
allow-new-zones yes;
};[/INDENT]

**named.conf.local**
[INDENT]zone "domain.es" {
type slave;
masters { 0.0.0.0; };
file "/var/lib/bind/domain.es.hosts";
};[/INDENT]

I checked permissions in al bind directories (/etc/bind /var/cache/bind and /var/lib/bind) to be root:bind an 775

I'm stalled all other slaves are syncing but this domains always have the same error when i try to sync with the master.
Testing transfer of slave zone from 0.0.0.0 ..
.. from 0.0.0.0 : Failed : ; <<>> DiG 9.10.3-P4-Ubuntu <<>> IN AXFR domain.es @0.0.0.0 ;; global options: +cmd ; Transfer failed. 

Please, anyone can help me

---

### Post by santintin on 2018-08-17
It seems that no config problem, I restarted the server, not only the service, and now is syncing. and all works fine again

---

