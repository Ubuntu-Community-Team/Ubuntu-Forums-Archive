---
title: "DHCP server won 't start, i need help"
date: 2017-05-15
forum: Server Platforms
---

### Post by mulbzh2 on 2017-05-15
Hello and sorry for my English :-)

I have install Ubuntu server 16.04 on Hyper-V server.
The VM have got one trunk network card on it

In /etc/network/interfaces, i have got this :
```

# The primary network interface
auto eth0.4
#Interface d'administration sur vlan 4
iface eth0.4 inet static
        address 10.4.0.44
        netmask 255.255.0.0
        network 10.4.0.0
        broadcast 10.4.255.255
        gateway 10.4.255.254
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 10.4.0.2 10.4.0.1
        dns-search domain.toto

```

so i can ping 10.4.0.44, it is ok ! 

I installed DHCP server, in /etc/default/isc-dhcp-server, i have got :
```
INTERFACES=eth0.4
```

In /etc/DHCP/dhcpd.conf, i have just :
```
# OrganisationPEN
subnet 10.94.0.0 netmask 255.255.0.0 {
        range 10.94.200.1 10.94.205.254;
        }
```

if i start the DHCP server, it won t start :(
 ```
isc-dhcp-server.service - ISC DHCP IPv4 server
   Loaded: loaded (/lib/systemd/system/isc-dhcp-server.service; enabled; vendor preset: enabled)
   Active:[COLOR=#ff0000]failed (Result: exit-code)[/COLOR] since lun. 2017-05-15 12:23:04 CEST; 14min ago
     Docs: man:dhcpd(8)
  Process: 2116 ExecStart=/bin/sh -ec      CONFIG_FILE=/etc/dhcp/dhcpd.conf;      if [ -f /etc/ltsp/dhcpd.conf ]; then CO
 Main PID: 2116 (code=exited, status=1/FAILURE)
mai 15 12:23:04 SSGVDHCP sh[2116]: Not configured to listen on any interfaces!
mai 15 12:23:04 SSGVDHCP sh[2116]: If you think you have received this message due to a bug rather
mai 15 12:23:04 SSGVDHCP sh[2116]: than a configuration issue please read the section on submitting
mai 15 12:23:04 SSGVDHCP sh[2116]: bugs on either our web page at [www.isc.org]("http://www.isc.org") or in the README file
mai 15 12:23:04 SSGVDHCP sh[2116]: before submitting a bug.  These pages explain the proper
mai 15 12:23:04 SSGVDHCP sh[2116]: process and the information we find helpful for debugging..
mai 15 12:23:04 SSGVDHCP sh[2116]: exiting.
mai 15 12:23:04 SSGVDHCP systemd[1]: isc-dhcp-server.service: Main process exited, code=exited, status=1/FAILURE
mai 15 12:23:04 SSGVDHCP systemd[1]: isc-dhcp-server.service: Unit entered failed state.
mai 15 12:23:04 SSGVDHCP systemd[1]: isc-dhcp-server.service: Failed with result 'exit-code'.

```



What is the problem ?
thanks

---

### Post by mulbzh2 on 2017-05-15
ok, i found it is one bug :

[https://bugs.launchpad.net/ubuntu/+source/isc-dhcp/+bug/1543794](https://bugs.launchpad.net/ubuntu/+source/isc-dhcp/+bug/1543794)

---

### Post by darkod on 2017-05-15
Have you checked online if you can use eth0.4 like that, without starting eth0 first? I noticed in your interfaces file, you don't have 'auto eth0'.

Also, your eth0.4 is in the 10.4.0.0/16 subnet and you are trying to issue dhcp leases on 10.94.0.0/16 subnet. I am also not sure if it can work like that when the dhcp server has no interface and IP in the subnet it is trying to serve.

When you have only one interface, why do you need to use vlan? Can't you simply use the standard eth0 interface and untagged traffic?

---

### Post by mulbzh2 on 2017-05-15
thank you
ok, i need help. Just some explications before. (sorry for my English)

What i 'd like :

Just set one IP adress to the Ubuntu (10.4.0.44)
Configure DHCP server for offer DHCP for multiple VLAN

What i understand, i have to create one network interface in /etc/network/interface for each subnet create in /etc/DHCP/dhcpd.conf
not possible to have only one interface, only 10.4.0.44 for all subnet ? i want DHCP listen on 10.4.0.44 for all subnet

In Windows server, that 's we do, there is not necessary create interface for each subnet

do you understand to me ? how i can do that ?

because in my firewall, i can only set one IP for DHCP server for all VLAN.

---

### Post by darkod on 2017-05-15
Leave alone windows, things don't always work the same... I find it better creating more interfaces... In fact, if you really want multiple VLANs you need more than one interface, because otherwise it won't connect properly to the VLANs.

You do understand difference between a VLAN and a subnet, right? If you want multiple subnets that's one thing, and multiple VLANs is another.

I would configure the primary interface, eth0, with 10.4.0.44.

Then create as many additional interfaces for each VLAN you need. Assigning address for each subnet you want, for example 10.94.0.1 / 255.255.255.0. You need gateway only on the primary interface, not on the additional ones.

Then configure multiple dhcp subnets listening on the correct virtual interface.

That should be it... For more help about exact commands there should be plenty tutorials online.

---

### Post by mulbzh2 on 2017-05-16
i can t configure eth0 with IP 10.4.0.44 because this IP is in specific VLAN (vlan 4) and  i have set the network card as trunk. Do you think i have to set the network as access mode in VLAN 4 (not trunk), set the IP 10.4.0.44 and configure DHCP with subnet. it will work ?

---

### Post by darkod on 2017-05-16
Why do you need to use vlan for connection to the server? The primary connection I usually use without any vlan.

Then if you have additional connections that you need in specific vlans, you use them as tagged vlans (because only one can be untagged).

---

### Post by mulbzh2 on 2017-05-17
so i resolve my problem

I set my Ubuntu VM as access mode (not trunk) in VLAN 4 (it is my administration VLAN)
I set IP 10.4.0.44 to eth0 with mask 255.255.0.0, Gateway....
For ISC DHCP server, i listen eth0 only
In ISC DHCP server configuration file, i have to set range for VLAN 4 with no attribution. I found this solution in internet. Without that, ISC won t start ! ISC don't wan't to start is there is no range in the same network as network card !

> 
# VLAN4 
subnet 10.4.0.0 netmask 255.255.0.0 {}


after this i create range for others VLAN : (exemple)
> 
 Direct83
subnet 10.83.0.0 netmask 255.255.0.0 {
        option routers 10.83.255.254;
        option domain-name-servers 8.8.8.8, 8.8.4.4;
range 10.83.200.1 10.3.205.254;
        }



Now, the clients in VLAN 83 can get IP

---

