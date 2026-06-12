---
title: "vlan dhcp-server netplan - not listening"
date: 2020-05-19
forum: Server Platforms
---

### Post by Tr1p on 2020-05-19
i'm having isseus with my dhcp server listening on vlans:

this is my config: (netplan/isc-dhcp/status/ip a)

What am i doing wrong? i searched fora's and my config looks ok ...

 ```


           steven@test:~$ cat /etc/netplan/00-installer-config.yaml
        network:
            version: 2
            ethernets:
                enp0s7:
                    addresses:
                    - 192.168.178.3/24
                    gateway4: 192.168.178.1
                    nameservers:
                        addresses:
                        - 192.168.178.1
        
                enp1s7:
                    addresses:
                    - 192.168.99.1/24
                    nameservers:
                        addresses:
                        - 8.8.8.8
                        - 8.8.4.4
        
                enp1s7: {}
        
            vlans:
                vlan.101:
                    id: 101
                    link: enp1s7
                    addresses: [192.168.101.1/24]
                    nameservers:
                        addresses:
                        - 8.8.8.8
                        - 8.8.4.4
                vlan.102:
                    id: 102
                    link: enp1s7
                    addresses: [192.168.102.1/24]
                    nameservers:
                        addresses:
                        - 8.8.8.8
                        - 8.8.4.4
        
        #############################################################################
        
            steven@test:~$ cat /etc/dhcp/dhcpd.conf
        subnet 192.168.99.0 netmask 255.255.255.0 {
        option domain-name-servers 8.8.8.8, 8.8.4.4;
        option subnet-mask 255.255.255.0;
        option broadcast-address 192.168.99.255;
        range 192.168.99.20 192.168.99.50;
        option routers 192.168.99.1;
        default-lease-time 600;
        max-lease-time 7200;
        }
        
        subnet 192.168.101.0 netmask 255.255.255.0 {
        option domain-name-servers 8.8.8.8, 8.8.4.4;
        option subnet-mask 255.255.255.0;
        option broadcast-address 192.168.101.255;
        range 192.168.101.20 192.168.101.50;
        option routers 192.168.101.1;
        default-lease-time 600;
        max-lease-time 7200;
        }
        
        subnet 192.168.102.0 netmask 255.255.255.0 {
        option domain-name-servers 8.8.8.8, 8.8.4.4;
        option subnet-mask 255.255.255.0;
        option broadcast-address 192.168.102.255;
        range 192.168.102.20 192.168.102.50;
        option routers 192.168.102.1;
        default-lease-time 600;
        max-lease-time 7200;

        #############################################################################

            steven@test:~$ sudo service isc-dhcp-server stop
        steven@test:~$ sudo service isc-dhcp-server start
        steven@test:~$ sudo service isc-dhcp-server status
        &#9679; isc-dhcp-server.service - ISC DHCP IPv4 server
             Loaded: loaded (/lib/systemd/system/isc-dhcp-server.service; enabled; vendor preset: enabled)
             Active: active (running) since Tue 2020-05-19 20:30:34 UTC; 2s ago
               Docs: man:dhcpd(8)
           Main PID: 1678 (dhcpd)
              Tasks: 4 (limit: 2205)
             Memory: 4.7M
             CGroup: /system.slice/isc-dhcp-server.service
                     &#9492;&#9472;1678 dhcpd -user dhcpd -group dhcpd -f -4 -pf /run/dhcp-server/dhcpd.pid -cf /etc/dhcp/dhcpd.conf
        
        May 19 20:30:35 test sh[1678]: Listening on LPF/enp1s7/00:0c:f6:45:27:7f/192.168.99.0/24
        May 19 20:30:35 test sh[1678]: Sending on   LPF/enp1s7/00:0c:f6:45:27:7f/192.168.99.0/24
        May 19 20:30:35 test dhcpd[1678]:    in your dhcpd.conf file for the network segment
        May 19 20:30:35 test dhcpd[1678]:    to which interface enp0s7 is attached. **
        May 19 20:30:35 test dhcpd[1678]:
        May 19 20:30:35 test dhcpd[1678]: Listening on LPF/enp1s7/00:0c:f6:45:27:7f/192.168.99.0/24
        May 19 20:30:35 test dhcpd[1678]: Sending on   LPF/enp1s7/00:0c:f6:45:27:7f/192.168.99.0/24
        May 19 20:30:35 test dhcpd[1678]: Sending on   Socket/fallback/fallback-net
        May 19 20:30:35 test sh[1678]: Sending on   Socket/fallback/fallback-net
        May 19 20:30:35 test dhcpd[1678]: Server starting service.
        steven@test:~$

    ######################################################################

    steven@test:~$ ip a
    1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
        link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
        inet 127.0.0.1/8 scope host lo
           valid_lft forever preferred_lft forever
        inet6 ::1/128 scope host
           valid_lft forever preferred_lft forever
    2: enp1s7: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
        link/ether 00:0c:f6:45:27:7f brd ff:ff:ff:ff:ff:ff
        inet 192.168.99.1/24 brd 192.168.99.255 scope global enp1s7
           valid_lft forever preferred_lft forever
        inet6 fe80::20c:f6ff:fe45:277f/64 scope link
           valid_lft forever preferred_lft forever
    3: enp0s7: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
        link/ether 00:24:1d:a5:55:a9 brd ff:ff:ff:ff:ff:ff
        inet 192.168.178.3/24 brd 192.168.178.255 scope global enp0s7
           valid_lft forever preferred_lft forever
        inet6 fe80::224:1dff:fea5:55a9/64 scope link
           valid_lft forever preferred_lft forever
    4: vlan.101@enp1s7: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
        link/ether 00:0c:f6:45:27:7f brd ff:ff:ff:ff:ff:ff
        inet 192.168.101.1/24 brd 192.168.101.255 scope global vlan.101
           valid_lft forever preferred_lft forever
        inet6 fe80::20c:f6ff:fe45:277f/64 scope link
           valid_lft forever preferred_lft forever
    5: vlan.102@enp1s7: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
        link/ether 00:0c:f6:45:27:7f brd ff:ff:ff:ff:ff:ff
        inet 192.168.102.1/24 brd 192.168.102.255 scope global vlan.102
           valid_lft forever preferred_lft forever
        inet6 fe80::20c:f6ff:fe45:277f/64 scope link
           valid_lft forever preferred_lft forever
    steven@test:~$
```

---

### Post by Tr1p on 2020-05-20
Wrong subgroup. Moved to networks. Please close

---

