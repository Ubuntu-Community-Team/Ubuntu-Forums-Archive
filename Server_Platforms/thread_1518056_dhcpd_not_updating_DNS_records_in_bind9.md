---
title: "dhcpd not updating DNS records in bind9"
date: 2010-06-26
forum: Server Platforms
---

### Post by tr333 on 2010-06-26
I'm having trouble getting dhcpd to update DNS records in bind9.  I'm not seeing any journal files created for bind9.  The following appears in syslog when a client machine connects to the network:
```

Jun 26 04:07:22 ubuntu dhcpd: DHCPDISCOVER from 00:23:df:44:78:83 via eth0
Jun 26 04:07:23 ubuntu dhcpd: DHCPOFFER on 10.0.0.112 to 00:23:df:44:78:83 (Computer1) via eth0
Jun 26 04:07:24 ubuntu named[10089]: client 10.0.0.1#56315: update 'mydomain/IN' denied
Jun 26 04:07:24 ubuntu dhcpd: Unable to add forward map from Computer1.mydomain to 10.0.0.112: timed out
Jun 26 04:07:24 ubuntu dhcpd: DHCPREQUEST for 10.0.0.112 (10.0.0.1) from 00:23:df:44:78:83 (Computer1) via eth0
Jun 26 04:07:24 ubuntu dhcpd: DHCPACK on 10.0.0.112 to 00:23:df:44:78:83 (Computer1) via eth0

```

dhcpd.conf:
```
ddns-update-style interim;
ddns-domainname "mydomain";
ddns-rev-domainname "0.0.10.in-addr.arpa";

# option definitions common to all supported networks...
option domain-name "mydomain";
option domain-name-servers 10.0.0.1;
option ntp-servers 10.0.0.5;
option subnet-mask 255.255.255.0;
option broadcast-address 10.0.0.255;
option routers 10.0.0.254;

default-lease-time 600;
max-lease-time 7200;

subnet 10.0.0.0 netmask 255.255.255.0 {
    range 10.0.0.100 10.0.0.199;
}

# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.
authoritative;

# Use this to send dhcp log messages to a different log file (you also
# have to hack syslog.conf to complete the redirection).
log-facility local7;

key DHCP_UPDATER {
    algorithm HMAC-MD5.SIG-ALG.REG.INT;
    secret "<rndc.key-secret>";
};
```

named.conf.local:
```
key DHCP_UPDATER {
    algorithm HMAC-MD5.SIG-ALG.REG.INT;
    secret "<rndc.key-secret>";
};

zone "mydomain" {
    type master;
    file "/var/lib/bind/db.mydomain";
    allow-update { key DHCP_UPDATER; };
};

zone "0.0.10.in-addr.arpa" {
    type master;
    file "/var/lib/bind/db.0.0.10";
    allow-update { key DHCP_UPDATER; };
};
```

rndc.key:
```
key "rndc-key" {
	algorithm hmac-md5;
	secret "<rndc.key-secret>";
};
```

---

### Post by kevinthecomputerguy on 2010-07-20
I put together a how-to on that, using webmin.
You may need to skip to page 5
[http://woodel.com](http://woodel.com)

---

### Post by tr333 on 2010-07-20
Thanks.  I'll take a look and see how it goes.

---

### Post by kevinthecomputerguy on 2010-07-21
Its really picky about spaces and carriage returns. But I included all that in the how-to.
Once its working, leave it alone and run away :- )

---

