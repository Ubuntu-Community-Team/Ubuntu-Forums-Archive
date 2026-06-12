---
title: "unable to get ip from DHCP configured for maas"
date: 2013-10-11
forum: Ubuntu Cloud and Juju
---

### Post by narasimha18sv on 2013-10-11
Hi ,

I have installed maas with maas-dhcp and maas-dns on a machine. Updated dhcp.conf(/etc/maas/dhcpd.conf) with the ip range,broadcast address,router ip. when trying to boot from PXE it is not able to fetch Ip from maas-dhcp.

I have tested the dhcp.conf for normal dhcp server. Machine is able to get ip from the range which i have specified.

steps I followed :

1. apt-get install maas maas-dhcp maas-dns
2. vi /etc/maas/dhcpd.conf
  subnet xx.xx.xx.xx netmask 255.255.255.0 {
    filename "pxelinux.0";
    option subnet-mask 255.255.255.0;
    option broadcast-address xx.xx.xx.xx;
    option domain-name-servers xx.xx.xx.xx;
    option routers xx.xx.xx.xx;
    range dynamic-bootp xx.xx.xx.126 xx.xx.xx.130;
}
3. updated eth0 interface with the same above values in cluster configuration.
4. service maas-dhcp-server restart
5. maas-import-pxe-files
6. reboot
7. dpkg-reconfigure maas

Please let me know if i have missed any configuration or did any step wrong in the above procedure.
Need help in resolving this issue as soon as possible

Thanks in advance

Regards,
Narasimha

---

