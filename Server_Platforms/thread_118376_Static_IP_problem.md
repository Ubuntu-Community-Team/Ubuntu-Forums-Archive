---
title: "Static IP problem"
date: 2006-01-16
forum: Server Platforms
---

### Post by Tux_Phoenix on 2006-01-16
Ok I set up my server I have apache php and mysql running great.  I set the the static IP and now it cann't connect to the internet.  I know I have some thing set wrong but I am not sure.  So here is my set up...

I have a dsl modem connected to a router then to a switch.  
modems IP: 10.0.0.2
router : 10.0.0.5

and here is my interfaces file 
```
# The primary network interface
iface eth0 inet static
        address 192.168.1.30
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 10.0.0.2
        dns-nameservers 192.107.41.34 192.107.41.21

auto eth0
```

the dns servers are the ones I got from my isp.  

I have tryed setting my gateway to 10.0.0.5 and the same thing.  I can acces my server from with in the network but it will not connect out.  So no ping yahoo.com etc...

---

### Post by Iowan on 2006-01-16
Forgive me if I only confuse the issue:

If the router is between the server and the modem, do you need the router address for the gateway?

---

### Post by sphinx on 2006-01-16
Well, I'm not 100% sure but there may be more than one problem. 

First up, your networking equipment seems to be on a 10.0.0.* subnet but your server is on a 192.168.1.* subnet. Try making your computers static ip address 10.0.0.6 or something in the 10.0.0.1-255 range thats not in use (of course changing the network and broadcast addresses to match).

Otherwise you need to add a route into your router directing traffic from the 192.168.1 subnet to the 10.0.0 one, And make the computer use the router as the gateway. I think I may have used incorrect terminology there as I'm a bit hazy on non-trivial routing.

Although I also suspect your modem might be acting as a router too if it has an IP address. But that may no have anything to do with the problem.

---

### Post by papayiya on 2006-01-16
[QUOTE=Tux_Phoenix]Ok I set up my server I have apache php and mysql running great.  I set the the static IP and now it cann't connect to the internet.  I know I have some thing set wrong but I am not sure.  So here is my set up...

I have a dsl modem connected to a router then to a switch.  
modems IP: 10.0.0.2
router : 10.0.0.5

and here is my interfaces file 
```
# The primary network interface
iface eth0 inet static
        address 192.168.1.30
        netmask 255.255.255.0
        gateway 192.168.1.0
         

auto eth0
```

the dns servers are the ones I got from my isp.  

I have tryed setting my gateway to 10.0.0.5 and the same thing.  I can acces my server from with in the network but it will not connect out.  So no ping yahoo.com etc...[/QUOTE]


Ok.. try this:

```
# The primary network interface
iface eth0 inet static
        address 192.168.1.30
        netmask 255.255.255.0
        gateway 192.168.1.0
         

auto eth0
```

if that doesn't work, set the gateway to 192.168.1.1

Good luck,
George

---

### Post by Tux_Phoenix on 2006-01-16
Awsome I got it working thanks guys.

The working setup was 

```
# The primary network interface
iface eth0 inet static
        address 192.168.1.30
        netmask 255.255.255.0
        gateway 192.168.1.1

auto eth0

```

---

