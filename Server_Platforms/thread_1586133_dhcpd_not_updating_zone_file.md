---
title: "dhcpd not updating zone file"
date: 2010-10-01
forum: Server Platforms
---

### Post by Jsdey on 2010-10-01
Hi List,

I have been struggling to get dhcpd to update the zone by creating the zone jrl files.  Syslog produces the following:

Oct  1 11:25:19 robo5 dhcpd: Unable to add forward map from robo6.robo.net. to 192.168.0.101: timed out
Oct  1 11:25:19 robo5 dhcpd: server: host unknown.
Oct  1 11:25:19 robo5 dhcpd: dhcp.c(4001): non-null pointer
Oct  1 11:25:19 robo5 dhcpd: DHCPREQUEST for 192.168.0.101 from 00:1e:37:24:0d:a2 (robo6) via eth0
Oct  1 11:25:19 robo5 dhcpd: DHCPACK on 192.168.0.101 to 00:1e:37:24:0d:a2 (robo6) via eth0

Any help would be greatly appreciated.  Thanks

John

---

### Post by Jsdey on 2010-10-04
Went back over conf files and found error in named.conf.

---

### Post by peposimo on 2011-02-09
> **Jsdey said:**
> Went back over conf files and found error in named.conf.

can you tell us what exactly did you found in named.conf? I have the same error and my named.conf looks like:

include "/etc/bind/named.conf.options";
include "/etc/bind/named.conf.local";

controls {
        inet 127.0.0.1 port 953 allow {127.0.0.1; 192.168.1.18; 192.168.1.9; } keys { "rndc-key"; } ;
};

... but I don't see any error in configuration.:confused:

Thank you.

---

