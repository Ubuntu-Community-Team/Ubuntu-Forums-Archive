---
title: "Network Interface Configuration for Internet Sharing"
date: 2011-06-02
forum: Server Platforms
---

### Post by grants on 2011-06-02
I know I have a config file called interfaces. 

Looks something like this. . .


# The primary network interface
    auto eth0
    iface eth0 inet static
    address 192.168.3.100
    gateway 192.168.3.1
    netmask 255.255.255.0
    network 192.168.3.0
    broadcast 192.168.3.255

# Second interface
    auto eth1
    iface eth1 inet static
    address 192.168.3.101
    gateway 192.168.3.1
    netmask 255.255.255.0
    network 192.168.3.0
    broadcast 192.168.3.255

I'm curious if there is a way set up internet connection sharing on my second interface via this file in /etc/network/interfaces. Also my second question is if there is a way to only specify a static ip address and the rest of the information is provided by my router. 

I have my router set up for DHCP and it's ip is 192.168.3.1

eth0 is connected to a LAN port on my router (wrt-54g) and eth1 is connected to my xbox. All other ports on my router are used so I'd like to get sharing set up so I don't need to buy a switch since I have an unused port anyways.

Any help would be great. 

I was able to get this to work with the network manager in ubuntu desktop but the machine I need this to work on is ubuntu server and for some reason my desktop environment of my server doesn't have the same network manager as the default desktop install and it also doesn't seem to work. It lists my interfaces as "not managed" and doesn't let me edit the settings. I then removed one interface from the interface file and was able to edit connections with the GUI manager but it didn't let me connect and if I saved any settings they disappeared. Very odd. I'd rather set it up with the interface file if possible.

GUI Method: (only worked on desktop version of Ubuntu)
[https://help.ubuntu.com/community/Internet/ConnectionSharing#GUI%20Method%20via%20Network%20Manager%20%28Ubuntu%209.10%20and%20up%29](https://help.ubuntu.com/community/Internet/ConnectionSharing#GUI%20Method%20via%20Network%20Manager%20%28Ubuntu%209.10%20and%20up%29)

---

### Post by giggins on 2011-06-02
Take a look at this guide:

[https://help.ubuntu.com/community/Internet/ConnectionSharing#Ubuntu%20Internet%20Gateway%20Method%20(iptables](https://help.ubuntu.com/community/Internet/ConnectionSharing#Ubuntu%20Internet%20Gateway%20Method%20(iptables))

and also consider doing what's under the "Advanced Gateway Configuration" section too. dnsmasq is an excellent recursive DNS server and a good DHCP server.

It boils down to:
[LIST=1]
[*]NAT
[*]Routing / Forwarding
[*]DHCP
[/LIST]

NetworkManager makes it easy to get started with this, but it's not nearly as flexible as a solution like the guide above provides.

---

### Post by ruffEdgz on 2011-06-02
You should be able to add this line to any of the interfaces to enable DHCP:
```

auto ethX
iface ethX inet dhcp

```
Both interface connections look good but if you router can set static IPs for both, that also can work which will have minimal changes on the server.

Also, make sure you pick IPs that aren't in your routers start ip isn't near the 192.168.3.100 range.

Hope that helps.

---

### Post by grants on 2011-06-02
> **ruffEdgz said:**
> You should be able to add this line to any of the interfaces to enable DHCP:
```

auto ethX
iface ethX inet dhcp

```
Both interface connections look good but if you router can set static IPs for both, that also can work which will have minimal changes on the server.

Also, make sure you pick IPs that aren't in your routers start ip isn't near the 192.168.3.100 range.

Hope that helps.

My router's DHCP starts at .100 so are you saying if I set it to be static I should set it not in the DHCP range?

I don't have the ability to do static ip's in my router I need to do it on the host itself. 
```

auto ethX
iface ethX inet dhcp

```
This will assign a random dhcp address. I'd like everything to be auto except for the address. 

I don't have much experience with IP tables so I'd like to stay away from that if possible.

---

### Post by ruffEdgz on 2011-06-02
> **grants said:**
> My router's DHCP starts at .100 so are you saying if I set it to be static I should set it not in the DHCP range?

I don't have the ability to do static ip's in my router I need to do it on the host itself. 
```

auto ethX
iface ethX inet dhcp

```
This will assign a random dhcp address. I'd like everything to be auto except for the address. 

I don't have much experience with IP tables so I'd like to stay away from that if possible.

Answers to your questions:
[LIST=1]
[*]Yes, if the router doesn't know that both 100 and 101 are being used, the router might try and use both IPs if a new connection occurs (wired or wireless). I recommend taking an IP below 100 for the static IPs
[*]From my understanding of a static IP and how I have used them, its one or the other. When I say that is, you can't have the static IP part but auto the rest or auto the IP address but have the static gateway, subnet mask, etc... If you make one DHCP though, it should get all the information it needs to get network access and it might be the same as the static setup you have right now.
[/LIST]

Cheers!

---

