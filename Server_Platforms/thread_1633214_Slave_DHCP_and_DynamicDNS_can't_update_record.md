---
title: "Slave DHCP and DynamicDNS can't update record"
date: 2010-11-29
forum: Server Platforms
---

### Post by onlyu on 2010-11-29
Hi all,

I setup 2 servers for DHCP and DDNS failover. But I see only Master DNS can update to db. file. When I disconnect Master, the Slave can release new IP to client but can't update record to db. file.
Error:
```
[B]bdc named[878]: client 192.168.100.2#36203: signer "rndc-key" denied
Nov 28 22:42:22 bdc named[878]: client 192.168.100.2#36203: update forwarding 'systeminteg.com/IN' denied[/B]

```Help me!!!. 
Many thanks for any advance!!


I edit apparmor already for all DHCP and Bind
```

usr.sbin.dhcpd3
/etc/bind/ rw,
/etc/bind/** rw,

``````

usr.sbin.named
/etc/bind/ rw,
/etc/bind/** rw,

```This is my conf file


[SIZE=3]**DHCP**[/SIZE]
**Master**:
```

include "/etc/dhcp3/dhcpd.failover";
include "/etc/dhcp3/dhcpd.ltspboot";
include "/etc/dhcp3/dhcpd.reserved";
include "/etc/dhcp3/dhcpd.subnet";
include "/etc/bind/rndc.key";


default-lease-time              521600;
max-lease-time                  521600;
ddns-update-style               interim;
ddns-domainname                 "systeminteg.com.";
ddns-rev-domainname             "in-addr.arpa.";
allow                           booting;
allow                           bootp;
ignore                          client-updates;
authoritative;

zone systeminteg.com. {
        primary 127.0.0.1;
        key rndc-key;
}


option subnet-mask              255.255.255.0;
option broadcast-address        192.168.100.255;
option routers                  192.168.100.14;
option domain-name-servers      192.168.100.1, 192.168.100.2;
option domain-name              "systeminteg.com";
option ip-forwarding            off;
option option-128 code 128 =    string;
option option-129 code 129 =    text;
option option-221 code 221 =    text;
use-host-decl-names             on;
#option log-servers             192.168.100.x;
log-facility                    local7;

zone systeminteg.com. {
        primary 192.168.100.1;
        key rndc-key;
}

zone 100.168.192.in-addr.arpa. {
        primary 192.168.100.1;
        key rndc-key;
}

```**Slave**:
```

include "/etc/dhcp3/dhcpd.failover";
include "/etc/dhcp3/dhcpd.ltspboot";
include "/etc/dhcp3/dhcpd.reserved";
include "/etc/dhcp3/dhcpd.subnet";
include "/etc/bind/rndc.key";


default-lease-time              521600;
max-lease-time                  521600;
ddns-update-style               interim;
ddns-domainname                 "systeminteg.com.";
ddns-rev-domainname             "in-addr.arpa.";
allow                           booting;
allow                           bootp;
ignore                          client-updates;
authoritative;

zone systeminteg.com. {
        primary 127.0.0.1;
        key rndc-key;
}


option subnet-mask              255.255.255.0;
option broadcast-address        192.168.100.255;
option routers                  192.168.100.14;
option domain-name-servers      192.168.100.1, 192.168.100.2;
option domain-name              "systeminteg.com";
option ip-forwarding            off;
option option-128 code 128 =    string;
option option-129 code 129 =    text;
option option-221 code 221 =    text;
use-host-decl-names             on;
#option log-servers             192.168.100.x;
log-facility                    local7;

zone systeminteg.com. {
        primary 192.168.100.2;
        key rndc-key;
}

zone 100.168.192.in-addr.arpa. {
        primary 192.168.100.2;
        key rndc-key;
}

```[SIZE=3]**Bind9**[/SIZE]
**Master:**
named.conf.options
```

options {
        directory "/var/cache/bind";
        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
        forwarders {
                8.8.8.8;
                8.8.2.2;
        };

        recursion yes;

        version "REFUSED";

        allow-recursion {
                127.0.0.1;
                192.168.100.0/24;
        };

        allow-query {
                127.0.0.1;
                192.168.100.0/24;
        };

};

controls {
        inet 127.0.0.1 allow { localhost; 192.168.100.1; 192.168.100.2; } keys { "rndc-key";};
};

```named.conf.local
```

include "/etc/bind/rndc.key";

zone "systeminteg.com" in {
        type master;
        file "/etc/bind/db.systeminteg.com";
        allow-update { key "rndc-key";};
        allow-transfer { 192.168.100.2;};
        notify yes;
};

zone "100.168.192.in-addr.arpa" in {
        type master;
        file "/etc/bind/db.100.168.192";
        allow-update { key "rndc-key";};
        allow-transfer { 192.168.100.2;};
        notify yes;
};

```**Slave**
named.conf.options
```

options {
        directory "/var/cache/bind";
        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
        forwarders {
                8.8.8.8;
                8.8.2.2;
        };

        recursion yes;

        version "REFUSED";

        allow-recursion {
                127.0.0.1;
                192.168.100.0/24;
        };

        allow-query {
                127.0.0.1;
                192.168.100.0/24;
        };

};

controls {
        inet 127.0.0.1 allow { localhost; 192.168.100.1; 192.168.100.2; } keys { "rndc-key";};
};
```named.conf.local
```
include "/etc/bind/rndc.key";

zone "systeminteg.com" in {
        type slave;
        masters { 192.168.100.1; };
        file "/etc/bind/db.systeminteg.com";
};

zone "100.168.192.in-addr.arpa" in {
        type slave;
        masters { 192.168.100.1; };
        file "/etc/bind/db.100.168.192";
};

```

---

### Post by onlyu on 2010-11-29
Anyone help???

Regards,

---

### Post by zrin on 2011-07-20
one possible solution, for the record:
include rndc.key in named.conf.options
not in named.conf.local

---

### Post by nyu2007 on 2011-09-06
I still in this issues. Anyone help!!

Thanks so much

---

