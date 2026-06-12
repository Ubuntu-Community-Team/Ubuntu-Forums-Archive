---
title: "DHCP with multi default-lease-time in the same subnet"
date: 2012-07-09
forum: Server Platforms
---

### Post by paco699 on 2012-07-09
Hi all,

I configure a DHCP server.

In this configuration i would like, in the same subnet, 2 differents 
default-lease-time & max-lease-time

My goal:

"fixed-address" with 
default-lease-time & max-lease-time 
and "range" with another 
default-lease-time & max-lease-time 
Is it possible?


Thank you very much.


paco

---

### Post by paco699 on 2012-07-11
I think of this solution:
```
ddns-update-style none;

        option routers                  192.168.0.254;
        option subnet-mask              255.255.255.0;
        option broadcast-address        192.168.0.255;
        option domain-name-servers      192.168.0.1;
        option domain-name         "exemple.com";
        default-lease-time         86400;
        max-lease-time             1296000;

    ## Free Pool - 240 at 245 ##
subnet 192.168.0.0 netmask 255.255.255.0 {
    range 192.168.0.240 192.168.0.245;
    option routers 192.168.0.254;
    option broadcast-address 192.168.0.255;
    option domain-name-servers 192.168.0.1;
    option domain-name "exemple.com";
    default-lease-time 86400;
    max-lease-time 172800;
}

    ## Fixed-addresses ##
    
    host pc1 {
        hardware ethernet 02:02:27:11:00:00;
        fixed-address 192.168.0.16;
        }

    host pc2 {
        hardware ethernet 02:02:03:11:00:20;
        fixed-address 192.168.0.17;
        }
```Somebody can say to me if it is a good solution?

Thank you very much.

---

### Post by paco699 on 2012-07-19
Hello all,
 
That config works very well after 1 week of use.

---

