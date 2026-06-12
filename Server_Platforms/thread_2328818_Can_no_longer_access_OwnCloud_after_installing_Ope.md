---
title: "Can no longer access OwnCloud after installing OpenVPN"
date: 2016-06-24
forum: Server Platforms
---

### Post by ligerman1993 on 2016-06-24
Hi all, sorry if this is the wrong place to post this but I installed owncloud, configured it properly and it worked fine, i could access it from a domain name, download and upload medeia, etc.Then I Installed  and configured OpenVPN and can no longer access the server. Whenever I  try to connect to the server the connection times out.  The server runs  Apache2. This is my network interface file.  

auto lo 
iface lo inet loopback

auto br0
iface br0 inet static
address 192.168.0.19
netmask 255.255.255.0
gateway 192.168.0.1
bridge_ports p3p1

iface p3p1 inet manual
up ifconfig $IFACE 0.0.0.0 up
up ip link set $IFACE promisc on
down ip link set $IFACE promisc off
down ifconfig $IFACE down

  Any idea what might have happened?

---

### Post by volkswagner on 2016-06-26
Did you follow a tutorial for OpenVPN? Can you provide a link?

Please post output of 

```
ifconfig
```

Also the "Network" stanza should also be listed in your /etc/network/interfaces
Like:
```
network 192.168.0.0
```

Can you access Owncloud via your local LAN? Is the webserver available at all?

Is apache2 running? Do you see any info in logs?

---

### Post by nerdtron on 2016-06-26
I think there is also routing issue going on here. For example, when you activate OpenVPN, your server will have an extra IP address and another gateway configured to it, therefore, it won't be able to respond to HTTP server requests. Please also provide the output of the below command before and after you activate OpenVPN
```
 route -n 
```

---

