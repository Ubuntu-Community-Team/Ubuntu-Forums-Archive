---
title: "Dell PowerEdge R310 Integrated NIC"
date: 2012-02-01
forum: Server Platforms
---

### Post by Jefferythewind on 2012-02-01
Hi Everyone,

  I just have installed a Dell PowerEdge R310 with a fresh 11.10 installation.  It has 2 Ethernet jacks for integrated NICs.  We have set the server to have a fixed IP address, but the other Ethernet card is getting another IP from the DHCP server.  

  How do I have the two ports share the fixed IP and the traffic load?

---

### Post by ruffEdgz on 2012-02-01
If you want to have one IP address with two NICs, you will probably have to 'bond' the NICs together:

[https://help.ubuntu.com/community/UbuntuBonding](https://help.ubuntu.com/community/UbuntuBonding)

Quote from the site about what 'bonding' is:
> 
Bonding is also called port trunking or link aggregation and it will let you combine several network ports to make a single group. This combines the the bandwidth from several interfaces as a single connection.


Hope this helps.

---

### Post by Jefferythewind on 2012-02-01
Thanks ruffEdgz,
  I think that is exactly what I am looking for.  I have installed the ifenslave package, but still have not been able to configure it correctly in /etc/network/interfaces

  I have 2 interfaces that I want to share one IP address.  They are eth0 and eth1.  Does anyone have know how to set this up for these two interfaces to share one static IP?

---

### Post by Jefferythewind on 2012-02-01
OK i used the following codes and i accomplished the 2 ethernet ports sharing one IP from the man page for ifenslave -> [http://manpages.ubuntu.com/manpages/oneiric/man8/ifenslave-2.6.8.html](http://manpages.ubuntu.com/manpages/oneiric/man8/ifenslave-2.6.8.html).
```
modprobe bonding
ifconfig bond0 192.168.0.1 netmask 255.255.0.0
ifenslave bond0 eth0 eth1
```

---

