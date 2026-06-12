---
title: "DHCPD with shared-networks"
date: 2013-12-20
forum: Server Platforms
---

### Post by iryna7 on 2013-12-20
Hi, as soon as i tried to set host configurations with mac address in the each subnet, it does not works
without host configurations, it works fine. 

any comment would be nice. thanks in advance.

jason


shared-network local {
  subnet 192.168.10.0 netmask 255.255.255.0 {
    range dynamic-bootp 192.168.10.10 192.168.10.200;
    option routers 192.168.10.1;
    host pc1 {
      hardware ethernet XX:XX:XX:XX:XX:XX;
      fixed-address 192.168.10.10;
    }
  }


  subnet 10.100.10.0 netmask 255.255.255.0 {
    range dynamic-bootp 10.100.10.10 10.100.10.200;
    option routers 10.100.10.1;
    host pc10 {
      hardware ethernet XX:XX:XX:XX:XX:XX;
      fixed-address 10.100.10.10;
    }
  }
}

ubuntu dhcpd: WARNING: Host declarations are global.  They are not limited to the scope you declared them in.

---

### Post by Phrank_Da on 2014-01-23
From the error at the bottom, I'd assume you'd need to declare each host outside the brackets in it's own line. 
Like:

host pc10 {
      hardware ethernet XX:XX:XX:XX:XX:XX;
      subnet: X...
router ...
etc..
fixed-address 10.100.10.10;
    
}

Seems like DHCP looks for each host first, then if it's not declare it goes to one of the subnets.

---

