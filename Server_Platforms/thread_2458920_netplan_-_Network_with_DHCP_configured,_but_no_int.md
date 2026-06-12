---
title: "netplan - Network with DHCP configured, but no internet"
date: 2021-03-06
forum: Server Platforms
---

### Post by eduardolucioac on 2021-03-06
I am trying to configure my Ubuntu Server 20.04 LTS to use DHCP in its network configuration.


Many tutorials on the internet recommend that I create the following file with the following settings...


```
root@sinj:/home/brlight# cat /etc/netplan/99_config.yaml
network:
  version: 2
  renderer: networkd
  ethernets:
    ens3:
      dhcp4: true

```

... and run the following commands...


```
root@sinj:/home/brlight# netplan --debug generate
root@sinj:/home/brlight# netplan apply

```

PROBLEM: The server is obtaining its settings via DHCP, but is unable to access the internet.


-----------


**PLUS:**


Unlike other servers on the same network, it appears that the server is unable to obtain the gateway settings.


No problem server...


```
[root@ssh_brl ~]# ip route show
default via 10.0.0.1 dev eth0 proto dhcp metric 100 
10.0.0.0/24 dev eth0 proto kernel scope link src 10.0.0.6 metric 100 
10.2.0.0/24 via 10.0.0.7 dev eth0 proto dhcp metric 100

```

Server with problem ...


```
root@sinj:/home/brlight# ip route show
10.0.0.0/24 dev ens3 proto kernel scope link src 10.0.0.17 
10.2.0.0/24 via 10.0.0.7 dev ens3 proto dhcp src 10.0.0.17 metric 100 

```

-----------


**OTHER INFORMATION:**


**I**


```
root@sinj:/home/brlight# ip route show
10.0.0.0/24 dev ens3 proto kernel scope link src 10.0.0.17 
10.2.0.0/24 via 10.0.0.7 dev ens3 proto dhcp src 10.0.0.17 metric 100

``` 


**II**


```
root@sinj:/home/brlight# lshw -C network
  *-network                 
       description: Ethernet controller
       product: Virtio network device
       vendor: Red Hat, Inc.
       physical id: 3
       bus info: pci@0000:00:03.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: msix bus_master cap_list rom
       configuration: driver=virtio-pci latency=0
       resources: irq:11 ioport:c060(size=32) memory:fc056000-fc056fff memory:fc000000-fc03ffff
     *-virtio0
          description: Ethernet interface
          physical id: 0
          bus info: virtio@0
          logical name: ens3
          serial: 52:54:00:6c:ec:1f
          capabilities: ethernet physical
          configuration: autonegotiation=off broadcast=yes driver=virtio_net driverversion=1.0.0 ip=10.0.0.17 link=yes multicast=yes

```

**III**


```
root@sinj:/home/brlight# networkctl status ens3
&#9679; 2: ens3                                                              
             Link File: /usr/lib/systemd/network/99-default.link       
          Network File: /run/systemd/network/10-netplan-ens3.network   
                  Type: ether                                          
                 State: routable (configured)
                  Path: pci-0000:00:03.0                               
                Driver: virtio_net                                     
                Vendor: Red Hat, Inc.                                  
                 Model: Virtio network device                          
            HW Address: 52:54:00:6c:ec:1f                              
                   MTU: 1500 (min: 68, max: 65535)                     
  Queue Length (Tx/Rx): 1/1                                            
      Auto negotiation: no                                             
                 Speed: n/a                                            
               Address: 10.0.0.17 (DHCP4)                              
                        fe80::5054:ff:fe6c:ec1f                        
                   DNS: 10.0.0.1                                       


Mar 06 01:47:12 sinj systemd-networkd[641]: ens3: IPv6 successfully enabled
Mar 06 01:47:12 sinj systemd-networkd[641]: ens3: Link UP
Mar 06 01:47:12 sinj systemd-networkd[641]: ens3: Gained carrier
Mar 06 01:47:12 sinj systemd-networkd[641]: ens3: DHCPv4 address 10.0.0.17/24 via 10.0.0.1
Mar 06 01:47:13 sinj systemd-networkd[641]: ens3: Gained IPv6LL

```

**IV**


```
root@sinj:/home/brlight# dig www.google.com


; <<>> DiG 9.16.1-Ubuntu <<>> www.google.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 10647
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1


;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 65494
;; QUESTION SECTION:
;www.google.com.                        IN      A


;; ANSWER SECTION:
www.google.com.         41      IN      A       172.217.30.36


;; Query time: 48 msec
;; SERVER: 127.0.0.53#53(127.0.0.53)
;; WHEN: Sat Mar 06 04:37:04 UTC 2021
;; MSG SIZE  rcvd: 59

```

**V**

```
root@sinj:/home/brlight# dhclient -v ens3
Internet Systems Consortium DHCP Client 4.4.1
Copyright 2004-2018 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/


Listening on LPF/ens3/52:54:00:6c:ec:1f
Sending on   LPF/ens3/52:54:00:6c:ec:1f
Sending on   Socket/fallback
DHCPREQUEST for 10.0.0.17 on ens3 to 255.255.255.255 port 67 (xid=0x601d9dc1)
DHCPACK of 10.0.0.17 from 10.0.0.5 (xid=0xc19d1d60)
RTNETLINK answers: File exists
bound to 10.0.0.17 -- renewal in 933 seconds.

```


**VI**


```
root@sinj:/home/brlight# cat /var/lib/dhcp/dhclient.leases
lease {
  interface "ens3";
  fixed-address 10.0.0.17;
  option subnet-mask 255.255.255.0;
  option dhcp-lease-time 4000;
  option routers 10.0.0.1;
  option dhcp-message-type 5;
  option dhcp-server-identifier 10.0.0.5;
  option domain-name-servers 10.0.0.1;
  option dhcp-renewal-time 1000;
  option rfc3442-classless-static-routes 24,10,2,0,10,0,0,7;
  option dhcp-rebinding-time 2000;
  option host-name "sinj";
  renew 6 2021/03/06 05:20:33;
  rebind 6 2021/03/06 05:38:40;
  expire 6 2021/03/06 06:12:00;
}
lease {
  interface "ens3";
  fixed-address 10.0.0.17;
  option subnet-mask 255.255.255.0;
  option dhcp-lease-time 4000;
  option routers 10.0.0.1;
  option dhcp-message-type 5;
  option dhcp-server-identifier 10.0.0.5;
  option domain-name-servers 10.0.0.1;
  option dhcp-renewal-time 1000;
  option rfc3442-classless-static-routes 24,10,2,0,10,0,0,7;
  option dhcp-rebinding-time 2000;
  option host-name "sinj";
  renew 6 2021/03/06 18:50:24;
  rebind 6 2021/03/06 19:10:57;
  expire 6 2021/03/06 19:44:17;
}

```

**VII**

```
[FONT=monospace][COLOR=#000000]root@sinj:/home/brlight# ip route[/COLOR]
10.0.0.0/24 dev ens3 proto kernel scope link src 10.0.0.17  
10.2.0.0/24 via 10.0.0.7 dev ens3  
10.2.0.0/24 via 10.0.0.7 dev ens3 proto dhcp src 10.0.0.17 metric 100
[/FONT]
```[FONT=monospace]
[/FONT]
[**Refs.:** [https://ubuntu.com/server/docs/network-configuration](https://ubuntu.com/server/docs/network-configuration) , 
[http://manpages.ubuntu.com/manpages/cosmic/man5/netplan.5.html](http://manpages.ubuntu.com/manpages/cosmic/man5/netplan.5.html) , [https://www.krizna.com/ubuntu/setup-network-ubuntu-18-04/](https://www.krizna.com/ubuntu/setup-network-ubuntu-18-04/) , 
[https://websiteforstudents.com/configure-static-ip-addresses-on-ubuntu-18-04-beta/](https://websiteforstudents.com/configure-static-ip-addresses-on-ubuntu-18-04-beta/) , 
[https://www.linuxtechi.com/assign-static-ip-address-ubuntu-20-04-lts/](https://www.linuxtechi.com/assign-static-ip-address-ubuntu-20-04-lts/) ]

---

### Post by TheFu on 2021-03-06
Appears that you "buried the lead" by not mentioning virtualisation and how the host connection is setup for each.
Perhaps one uses host-only or NAT networking and the other uses a bridge?  Just a guess.

---

### Post by eduardolucioac on 2021-03-06
> **TheFu said:**
> Appears that you "buried the lead" by not mentioning virtualisation and how the host connection is setup for each.
Perhaps one uses host-only or NAT networking and the other uses a bridge?  Just a guess.

They all use brigde and are configured in the same way in the Hypervisor. We even have an Ubuntu Server 14.04 LTS and it works perfectly. The other distros are CentOS 7 and they works perfectly too.


We have already raised a lot of information about the problem and **we are starting to suspect that this is a bug or limitation of the "netplan"**.

Thanks! =D

---

### Post by LHammonds on 2021-03-08
If you add a gateway4 address, does that solve the issue?

Reference: [DHCP Overrides](https://netplan.io/reference/#dhcp-overrides)

LHammonds

---

