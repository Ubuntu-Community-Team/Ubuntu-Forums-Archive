---
title: "Some network setup help"
date: 2012-07-27
forum: Server Platforms
---

### Post by lloydwood on 2012-07-27
Hello,

I have Ubuntu Server 12.04 installed on an HP Microserver. Attached to this server is an unmanaged HP switch. Attached to the switch is a wireless internet router and various computers.

A DHCP server is installed on the Ubuntu server. The DHCP server has been turned off on the router so it is acting as a wireless access point.

This all works fine. All the computers connect to the server and the internet through the switch or the wireless access point and get assigned their IPs from the Ubuntu server. The problem is that the Ubuntu server itself can't see the internet. I this because it is the DHCP server? Is there a way to fix this?

Any help appreciated.

---

### Post by papibe on 2012-07-27
Hi lloydwood.

For the server you need a fix configuration. That means that all parameters need to be explicitly set on the config files.

Could you post the content of this files?
```
/etc/network/interfaces

/etc/resolv.conf
```
Regards.

---

### Post by brent1975 on 2012-07-27
> **lloydwood said:**
> Hello,

I have Ubuntu Server 12.04 installed on an HP Microserver. Attached to this server is an unmanaged HP switch. Attached to the switch is a wireless internet router and various computers.

A DHCP server is installed on the Ubuntu server. The DHCP server has been turned off on the router so it is acting as a wireless access point.

This all works fine. All the computers connect to the server and the internet through the switch or the wireless access point and get assigned their IPs from the Ubuntu server. The problem is that the Ubuntu server itself can't see the internet. I this because it is the DHCP server? Is there a way to fix this?

Any help appreciated.

Sounds like you are just missing a little finish touch with dns resolution.

Take a look at:
```
 sudo nano /etc/network/interfaces
```You should have at the bottom your dns
```

/ iface eth0 inet static  
 address 192.168.2.106
 netmask 255.255.255.0  
gateway 192.168.2.1
network 192.168.2.0
broadcast 192.168.2.255

dns-nameservers 192.168.2.1 8.8.8.8  [192.168.2.1 is my router use your ISP DNS or router] 
dns-search google.com
```

---

### Post by lloydwood on 2012-07-29
That's got it. I had my gateways set wrong in my interfaces file. All working now :D

Thank you very much.

---

