---
title: "Problem with DHCP and DDNS"
date: 2011-07-30
forum: Server Platforms
---

### Post by carballinho on 2011-07-30
Hello to all,

I have a problem updating DNS Server with fixed IPs that are configured in dhcpd.conf file. This is the error that appears in syslog:

Jul 30 18:40:54 ubuntuserver named[1039]: client 127.0.0.1#42282: updating zone 'cgestion.com/IN': update unsuccessful: ts.cgestion.com: 'name not in use' prerequisite not satisfied (YXDOMAIN)
Jul 30 18:40:54 ubuntuserver named[1039]: client 127.0.0.1#52577: updating zone 'cgestion.com/IN': update unsuccessful: ts.cgestion.com/TXT: 'RRset exists (value dependent)' prerequisite not satisfied (NXRRSET)

It's an error that only happens on Fixed IPs added on dhcpd.conf. Wiht automated IP address the update of DNS records works fine.

Thanks.

---

### Post by carballinho on 2011-08-01
Nobody knows nothing about this error?

---

### Post by carballinho on 2011-08-01
This is my dhcpd.conf file:

```

server-identifier       ubuntuserver;
ddns-updates            on;
ddns-update-style       interim;
ddns-domainname         "cgestion.com.";
ddns-rev-domainname     "in-addr.arpa.";
ignore                  client-updates;

include                 "/etc/bind/rndc.key";

zone cgestion.com. {
        primary 127.0.0.1;
        key rndc-key;
}

option ip-forwarding            off;
authoritative;
log-facility local7;
option domain-name              "cgestion.com";
option domain-name-servers      10.3.110.55;
default-lease-time              600;
max-lease-time                  7200;

subnet 10.0.0.0 netmask 255.0.0.0 {
        range 10.4.110.10 10.4.110.255;
        option routers 10.4.200.51;
        option broadcast-address 10.255.255.255;
        interfaces=eth0;
        allow unknown-clients;

        zone 10.in-addr.arpa. {
                primary 10.3.110.55;
                key "rndc-key";
        }

        zone localdomain. {
                primary 10.3.110.55;
                key "rndc-key";
        }
}

update-static-leases on;
#SERVIDOR CLIENTE EDI
host ccomunica2{
        DDNS-hostname "ccomunica2";
        option host-name "ccomunica2";
        hardware ethernet 00:0C:29:90:03:66;
        fixed-address 10.0.0.88;
}

#TERMINAL SERVER
host ts{
        DDNS-hostname "ts";
        option host-name "ts";
        hardware ethernet 00:0C:29:36:9D:E8;
        fixed-address 10.0.0.77;
}

```

---

