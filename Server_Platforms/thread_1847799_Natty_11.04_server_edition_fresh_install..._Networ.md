---
title: "Natty 11.04 server edition fresh install... Network issues"
date: 2011-09-21
forum: Server Platforms
---

### Post by Church.Cameron on 2011-09-21
Just set up my Linux server running Compliant hardware along with 11.04 Natty. The server during install auto negs a dhcp IP (which I have no issues with) but after completed install I reboot the machine and the server is left in dhcp and gave me no option to add a static route during install... I had to fish around and figured out in order to change the interface I had to do the below

```
$sudo vi /etc/network/interfaces 
```
and change the iface eth0 inet dhcp

to

```
iface eth0 inet static

address(ip i have set from the vlan to use)
netmask so on so forth down this list
broadcast
network
gateway
```
I have also had to make changes to the resolv.conf since it was still showing the dhcp name servers. I did this by using

```
$sudo vi /etc/resolv.conf
```
after editing these I did a restart of the network services. This did nothing and the server still couldn't ping. restarted the server completely and still could not ping.

I cannot think of where else I need to change any information. Ubuntu is not my strong set ( CentOS is more my forte) but any help you can give me on this would help so much!

Thanks!

---

### Post by Entilza on 2011-09-21
Check this guide:

[https://help.ubuntu.com/11.04/serverguide/C/network-configuration.html](https://help.ubuntu.com/11.04/serverguide/C/network-configuration.html)

---

### Post by Church.Cameron on 2011-09-21
problem solved! Now to get this server jamming. Thank you so much for your quick link Entilza!

---

