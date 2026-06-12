---
title: "Squid and SNMP issue"
date: 2006-03-24
forum: Server Platforms
---

### Post by beartamer on 2006-03-24
Hail ubuntians :)

I'm new to ubuntu world and I've decided to install ubuntu onto my home server. Not so long ago I've installed squid proxy server upon my host.

Here is what I've got:

```

% squid -v
Squid Cache: Version 2.5.STABLE10
configure options:  --prefix=/usr --exec_prefix=/usr --bindir=/usr/sbin --sbindir=/usr/sbin --libexecdir=/usr/lib/squid --sysconfdir=/etc/squid --localstatedir=/var/spool/squid --datadir=/usr/share/squid --enable-async-io --with-pthreads --enable-storeio=ufs,aufs,diskd,null --enable-linux-netfilter --enable-arp-acl --enable-removal-policies=lru,heap --enable-snmp --enable-delay-pools --enable-htcp --enable-poll --enable-cache-digests --enable-underscores --enable-referer-log --enable-useragent-log --enable-auth=basic,digest,ntlm --enable-carp --with-large-files i386-debian-linux 
```

I've added these strings to squid.conf:
```

snmp_port 3401
acl  snmppublic      snmp_community  public
snmp_access allow   snmppublic localhost
snmp_access deny    all

```

as a result I have only:
```

% sudo grep /var/log/squid/cache.log | grep SNMP
2006/03/24 23:11:18| Accepting SNMP messages on port 3401, FD 42.

```

... but port 3401 appears to be closed (netstat -nat and  nmap -p 3401 127.0.0.1 told me so) therefore snmpwalk can't connect to host (Timeout) and I cant get my neat rrdtool diagramms in cacti.

Can anybody help me? What could be caveat in these issue?

p.s. that's my first post here and sorry for my english :p

---

### Post by beartamer on 2006-03-24
Sorry, issue solved. That was my fault only.  I didn't realized that SNMP works over UDP. And as for snmpwalk timeout - that was -v 1 (version selection)  problem

---

