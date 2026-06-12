---
title: "Booting of ltsp get hang on old thin client"
date: 2011-04-21
forum: Server Platforms
---

### Post by pravindra.kumar on 2011-04-21
Hi,
I have configured ltsp on edubuntu10.04, but when i boot my Siemens P-III with 128Mb RAM machine from server then it get hang after assigning IP address from DHCP. But on edubuntu9.04 it's working fine.
My dhcp.conf file is below:-

#
# Default LTSP dhcpd.conf config file.
#

authoritative;

subnet 192.168.9.0 netmask 255.255.255.0 {
    range 192.168.9.20 192.168.9.250;
    option domain-name "ltsp-era";
    option domain-name-servers 192.168.9.1;
    option broadcast-address 192.168.9.255;
    option routers 192.168.9.1;
#    next-server 192.168.9.1;
#    get-lease-hostnames true;
    option subnet-mask 255.255.255.0;
    option root-path "/opt/ltsp/i386";
    if substring( option vendor-class-identifier, 0, 9 ) = "PXEClient" {
        filename "/ltsp/i386/pxelinux.0";
    } else {
        filename "/ltsp/i386/nbi.img";
    }
}
group   {
    use-host-decl-names       on;
    option log-servers        192.168.9.6;

#############################################################
#Testing
host ws202 {
        hardware ethernet   00:80:48:59:74:1A;
        fixed-address       192.168.9.202;
}



}

deny unknown-clients;

---

