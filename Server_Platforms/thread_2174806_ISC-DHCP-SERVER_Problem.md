---
title: "ISC-DHCP-SERVER Problem"
date: 2013-09-16
forum: Server Platforms
---

### Post by Toxic64 on 2013-09-16
Hi all, 

Found a nice problem today.One I can't understand.


I installed a DHCP (isc-dhcp-sever) yesterday on my Samba4 server.

my DHCP server address is 192.168.0.16.

Here is the dhcpd.conf

```
ddns-updates on;
ddns-update-style interim;
authoritative;
log-facility local7;
option domain-name "irisit.fr";
option domain-name-servers 192.168.0.16, 8.8.8.8, irissrv.irisit.fr;
default-lease-time 600;
max-lease-time 7200;
option broadcast-address 192.168.0.255;
option routers 192.168.0.1;
option subnet-mask 255.255.255.0;
option ntp-servers 0.fr.pool.ntp.org;
allow unknown-clients;
allow client-updates;

subnet 192.168.0.0 netmask 255.255.255.0 { 
        range dynamic-bootp 192.168.0.101 192.168.0.253;
}
```


It's all installed on a proxmox virtual environnement server and before I installed the DHCP server everything worked flawlessly.
[B]
the problems I'm facing now:[/B]

When I try to install a new Ubuntu server on my environnement (same network), the DHCP config during install fails (which is a major issue)
Then I go for static config and try to turn dhcp after install ->> static = OK, DHCP = FAIL
When I do the same with a Windows machine (same environnement, same network), the dhcp config during install is OK.

For the already installed linux servers with static IP, when I turn them to DHCP, nothing happens DHCPDISCOVER fails everytime and no dhcp address is assigned to the machine.
for the already installe windows machines, going from static to dhcp = no problem.

It seems the server works as all my windows machines get dhcp leases from the server
there is no other DHCP server conflicting on my network, the DHCP server from my router has been disabled.
more than that, no machine (windows or linux) that has been given a lease by my DHCP server can ping my DHCP server or any other machine that is on the same network.

```
 ipconfig /release 
and
 ipconfig /renew 

```
for windows machines will work

PLEASE HELP

---

### Post by Toxic64 on 2013-09-20
ok seems to be a DHCP over bridge /bond issue on my proxmox server.still no solution though....

---

