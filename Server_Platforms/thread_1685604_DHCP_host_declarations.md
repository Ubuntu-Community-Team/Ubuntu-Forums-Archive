---
title: "DHCP host declarations"
date: 2011-02-10
forum: Server Platforms
---

### Post by diablo2nd on 2011-02-10
So, ive got my dhcp server working fine, using the ltsp config file.

I'm trying to setup static assignments for reporting purposes.

i have in my dhcpd.conf 3 entrys for hosts as follows

 ```
host abc { 
hardware address xx:xx:xx:xx:xx:xx;
fixed-address 192.168.0.4;
} 
```but only the first one ever works. if i change the order still only the first declaration works. What am i missing please?

---

### Post by elico on 2011-02-11
i think it's the scope thing.
you should declare the host on the specific network scope.
give us the full dhcpd.conf so we can tell you a thing or two.

---

### Post by diablo2nd on 2011-02-11
DHCPD.conf follows.
Note I have tried many combinations of putting the host inside and outside the subnet declaration and with or without the group (In both places) but the problem remains that .....................

Im an idiot. although it took 24 hours for the other pcs to renew their leases the one the i was getting hung up on not working had a typo.

```
#
# Default LTSP dhcpd.conf config file.
#

authoritative;
default-lease-time 3600;
max-lease-time 7200;


subnet 192.168.0.0 netmask 255.255.255.0 {
    range 192.168.0.20 192.168.0.250;
    option domain-name "office.netmatters.co.nz";
    option domain-name-servers 192.168.1.100;
    option broadcast-address 192.168.0.255;
    option routers 192.168.0.1;
#    next-server 192.168.0.1;
#    get-lease-hostnames true;
    option subnet-mask 255.255.255.0;
    option root-path "/opt/ltsp/i386";
    if substring( option vendor-class-identifier, 0, 9 ) = "PXEClient" {
        filename "/ltsp/i386/pxelinux.0";
    } else {
        filename "/ltsp/i386/nbi.img";
    }
    
}
group{
host banana {
    hardware ethernet 00:0c:f1:65:f3:cf;
    fixed-address 192.169.0.5;
}
host bellatrix {
    hardware ethernet 00:1a:4d:f2:94:cf;
    fixed-address 192.168.0.6;
}

host Wing-Cole-PC {
    hardware ethernet 00:16:6f:4f:c4:a3;
    fixed-address 192.168.0.7;
}

host UNDERSCORE{
    hardware ethernet 00:1f:e1:5b:b5:18;
    fixed-address 192.168.0.20;
}
}
```

---

### Post by elico on 2011-02-12
i will give you a working settings file that based on the one that i am working with:[PHP]
# Sample /etc/dhcpd.conf
# (add your comments here)
default-lease-time 3600;
max-lease-time 7200;
option subnet-mask 255.255.255.0;
option broadcast-address 192.168.0.255;
option routers 192.168.0.1;
option domain-name-servers 192.168.0.100;
#option local-pac-server code 252 = text;
#option local-pac-server "http://wpad.lan:80/wpad.dat";

#your options
authoritative;
option root-path "/opt/ltsp/i386";
    if substring( option vendor-class-identifier, 0, 9 ) = "PXEClient" {
        filename "/ltsp/i386/pxelinux.0";
    } else {
        filename "/ltsp/i386/nbi.img";
    }




# inside_lan
subnet 192.168.0.0 netmask 255.255.255.0 {
        option domain-name "lan";
        range 192.168.0.10 192.168.0.50;
        host banana {
        hardware ethernet 00:0c:f1:65:f3:cf;
        fixed-address 192.169.0.5;
        }
        host bellatrix {
            hardware ethernet 00:1a:4d:f2:94:cf;
            fixed-address 192.168.0.6;
        }
#changed the "-" to "_" underscor cause i didnt used them
        host Wing_Cole_PC {
            hardware ethernet 00:16:6f:4f:c4:a3;
            fixed-address 192.168.0.7;
        }

        host UNDERSCORE{
            hardware ethernet 00:1f:e1:5b:b5:18;
            fixed-address 192.168.0.20;
        }
 }[/PHP]

---

