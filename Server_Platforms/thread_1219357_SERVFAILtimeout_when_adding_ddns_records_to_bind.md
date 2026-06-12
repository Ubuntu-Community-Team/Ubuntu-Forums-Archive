---
title: "SERVFAIL/timeout when adding ddns records to bind"
date: 2009-07-21
forum: Server Platforms
---

### Post by Zebranky on 2009-07-21
I'm having trouble getting ddns to work. DHCP works perfectly, but when a client gets a lease, syslog looks like so:
```
Jul 21 16:32:18 odin named[17566]: client: client 127.0.0.1#37060: UDP request
Jul 21 16:32:18 odin named[17566]: security: client 127.0.0.1#37060: request has valid signature
Jul 21 16:32:18 odin named[17566]: security: client 127.0.0.1#37060: recursion available
Jul 21 16:32:18 odin named[17566]: client: client 127.0.0.1#37060: update
Jul 21 16:32:18 odin named[17566]: client: client 127.0.0.1#37060: send
Jul 21 16:32:18 odin named[17566]: client: client 127.0.0.1#37060: sendto
**Jul 21 16:32:18 odin dhcpd: Unable to add forward map from testvm.mydomain.net. to 192.168.10.100: timed out**
Jul 21 16:32:18 odin named[17566]: client: client 127.0.0.1#37060: senddone
Jul 21 16:32:18 odin named[17566]: client: client 127.0.0.1#37060: next
Jul 21 16:32:18 odin named[17566]: client: client 127.0.0.1#37060: endrequest
Jul 21 16:32:18 odin named[17566]: client: client @0xb5cc4008: udprecv
Jul 21 16:32:18 odin dhcpd: DHCPREQUEST for 192.168.10.100 from 00:0c:29:df:60:72 (testvm) via eth2
Jul 21 16:32:18 odin dhcpd: DHCPACK on 192.168.10.100 to 00:0c:29:df:60:72 (testvm) via eth2
```

tcpdump of dhcpd<->named exchange:
```
16:29:22.427577 IP localhost.53316 > localhost.domain: 8091 update [1a] [2n] [1au] SOA? mydomain.net. (211)
16:29:22.428762 IP localhost.domain > localhost.53316: 8091 update ServFail [0q] 0/0/1 (98)
```

relevant parts of named.conf.local:
```
include "/etc/bind/rndc.key";
controls {
        inet 127.0.0.1 port 953 allow { 127.0.0.1; } keys { rndc-key-mydomain; };
        };

// create the forward master zone
zone "mydomain.net" IN {
        type master;
        file "/var/lib/bind/mydomain.net.hosts";
        allow-update { key rndc-key-mydomain; };
        notify yes;
        };
// create the reverse master zone
zone "168.192.in-addr.arpa" {
        type master;
        file "/var/lib/bind/192.168.rev";
        allow-update { key rndc-key-mydomain; };
        notify yes;
        };
```

relevant parts of dhcpd.conf:
```
authoritative;
ddns-update-style interim;
ignore client-updates;
ddns-domainname "mydomain.net.";
ddns-rev-domainname "in-addr.arpa.";

key "rndc-key-mydomain" {
        algorithm hmac-md5;
        secret "supersecretkey==";
}

zone mydomain.net. {
        primary 127.0.0.1;
        key rndc-key-mydomain;
}

zone 168.192.in-addr.arpa. {
        primary 127.0.0.1;
        key rndc-key-mydomain;
}
```

Thanks in advance for any help.

---

