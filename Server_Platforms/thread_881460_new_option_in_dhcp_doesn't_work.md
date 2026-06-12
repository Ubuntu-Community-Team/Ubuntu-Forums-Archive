---
title: "new option in dhcp doesn't work"
date: 2008-08-06
forum: Server Platforms
---

### Post by ablmf on 2008-08-06
Hi all,

I am trying to publish a server address through dhcp so I add these lines to my dhcpd.conf

```
option ccs-port-number code 192 = unsigned integer 16;
option ccs-server-address code 193 = ip-address;
subnet 192.168.0.0 netmask 255.255.255.0 {
        range 192.168.0.200 192.168.0.230;
        option subnet-mask 255.255.255.0;
        option broadcast-address 192.168.0.255;
        option routers 192.168.0.1;
        option ccs-port-number 5060;
        option ccs-server-address 192.168.0.103;
}

```

The grammar is OK but in the dhcp packages I catched, these new options are not send to client.

Can anyone familiar with DHCP help me?

Thanks a lot!

---

