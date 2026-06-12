---
title: "static ip address doesn't connect to internet on ubuntu 12.04"
date: 2012-06-11
forum: Server Platforms
---

### Post by xihad76 on 2012-06-11
Recently due to high voltage our previous server crashed and we had to setup a new one as server. We have installed ubuntu 12.04 server edition. There are two lan cards where eth1 is primary lan card connected to internet and eth0 is used to share the Internet to other pc in the dept and connected to a router. when eth1 is in dhcp mode it connects to internet fine and through router other computer gets connectivity too. But when i set static ip which was set in the previous server it doesn't connect to Internet anymore. I have tried setting up the static ip using network manager too. but it didn't work either. For review I am copy pasting the etc/network/interfaces files.the same configuration was working fine in the previous server(ubuntu 10.04) befor it crashed. I would be grateful if anyone kindly point me the mistake I am doing. thanks in advance 
```

/etc/network/interfaces file

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#auto eth0
#iface eth0 inet dhcp

# The primary network interface
auto eth1
iface eth1 inet static
    address 203.112.196.119
    netmask 255.255.255.224
    network 203.112.196.96
    broadcast 203.112.196.127
    gateway 203.112.196.97
    # dns-* options are implemented by the resolvconf package, if installed
    dns-nameservers 203.112.196.85
    dns-search bmpt.du.ac.bd


auto eth0
iface eth0 inet static
    address 192.168.1.1
    netmask 255.255.255.0
    network 192.168.1.0
    broadcast 192.168.1.255


connection information when in DHCP Mode (that works)


ip address: 10.10.1.12
Broadcast address: 10.10.1.13
subnet mask: 255.255.255.224
default route: 10.10.1.1
primary dns: 203.112.196.85
```

---

### Post by darkod on 2012-06-11
The 10.10.1.12 address is what it received by dhcp on eth1?

In that case, it seems you have a router with a private interface connected to the server, and you need to use IP in that range, not a public IP like 203.112.x.x

Do you have any idea how and from where you would receive the 10.10.1.12 address when in dhcp mode?

---

### Post by xihad76 on 2012-06-11
> **darkod said:**
> The 10.10.1.12 address is what it received by dhcp on eth1?

In that case, it seems you have a router with a private interface connected to the server, and you need to use IP in that range, not a public IP like 203.112.x.x

Do you have any idea how and from where you would receive the 10.10.1.12 address when in dhcp mode?

The server is actually in my department and the internet connection is provided by the university. If this is the case which you mentioned then I am confused how the same configuration was working just fine before the server got crashed. I have already sent a mail to the IT dept. lets see what they response with. and thank you very much for your answer.

---

### Post by volkswagner on 2012-06-11
If you are running NetworkManager that indicates you have the desktop installed.

You will have conflicts with NM while trying to hand edit /etc/network/interfaces.  You will want to use NM for your static ip, or uninstall NetworkManager.

---

### Post by xihad76 on 2012-06-11
> **volkswagner said:**
> If you are running NetworkManager that indicates you have the desktop installed.

You will have conflicts with NM while trying to hand edit /etc/network/interfaces.  You will want to use NM for your static ip, or uninstall NetworkManager.

I have tried with Network manager too keeping interfaces file in default state. but it didnt work.

---

### Post by darkod on 2012-06-11
> **xihad76 said:**
> The server is actually in my department and the internet connection is provided by the university. If this is the case which you mentioned then I am confused how the same configuration was working just fine before the server got crashed. I have already sent a mail to the IT dept. lets see what they response with. and thank you very much for your answer.

I am also confused how the older server worked with this config. But if dhcp gives you an IP in the 10.x.x.x range it's 100% certain you are in your private network and need to use private IP.

Unless a specific connection (cable) was routed to that desk, you can't simply configure a public IP on a server inside your private LAN.

Lets see what they tell you.

---

### Post by kennethconn on 2012-06-11
1) To which interface are you referring when you say static ip address doesn't connect to internet?
 
2) What exactly does not connecting to internet mean (have you tried a ping to the outside world by IP address and not by DNS name)?
 
3) eth0 has no gateway when it is manually configured.

---

