---
title: "Server 8.04 - Static IP issues"
date: 2008-06-30
forum: Server Platforms
---

### Post by stizzump on 2008-06-30
Hey everyone,

This my first time setting up Linux server box, and most of it seems to be working out pretty well. However, I am running into a problem getting a static IP assigned.

I have the interfaces file configured for STATIC, and have filled in the appropriate network information. And have also set the DNS servers in the resolv.conf file.

After I set these, and restart the network service the Static IP will hold for a few days. Then, with no warning, it grabs a new address like it is setup for DHCP. 

There is only one network card in the server, although it is a dual port network card. Ubuntu sees this as one card though, not two.

Anyone know of how this can be resolved?

Thank you in advance for any suggestions.

---

### Post by Titan8990 on 2008-06-30
Type $cat /etc/network/interfaces and post the results.

Does your DHCP server acknowledge that system should get a static IP?

---

### Post by mrpeenut24 on 2008-06-30
It shouldn't be happening if your /etc/network/interfaces is set up properly(?), but check and make sure dhcp isn't running.

```

sudo /etc/init.d/dhcdbd stop

```


Just to make sure, can you show what you've got in your interfaces file?

---

### Post by stizzump on 2008-07-01
Hey guys,

The interfaces file is as follows:
___________________________________________________
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 10.10.1.17
netmask 255.255.255.0
network 10.10.1.0
broadcast 10.10.1.255
gateway 10.10.1.254
_________________________________________

Did I miss something obvious?

Here is also the output of ifconfig. Notice the IP of eth0..
_________________________________________
eth0      Link encap:Ethernet  HWaddr 00:0d:56:70:3f:9c
          inet addr:10.10.1.201  Bcast:10.10.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:56ff:fe70:3f9c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:45305929 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27414 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1894393481 (1.7 GB)  TX bytes:9281454 (8.8 MB)
          Interrupt:17

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:511 errors:0 dropped:0 overruns:0 frame:0
          TX packets:511 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:45864 (44.7 KB)  TX bytes:45864 (44.7 KB)
________________________________________

When I run the "sudo /etc/init.d/dhcdbd stop" command I get a command not found message.

---

### Post by Buffalo Soldier on 2008-07-01
> **stizzump said:**
> # The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 10.10.1.17
netmask 255.255.255.0
network 10.10.1.0
broadcast 10.10.1.255
gateway 10.10.1.254


When setting static IP, I never set the network and broadcast. All that i net to set is the IP address, netmask and gateway. Have you tried just using this setting?

```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 10.10.1.17
netmask 255.255.255.0
gateway 10.10.1.254
```

---

### Post by stizzump on 2008-07-01
Buffalo Solier,

I have not tried it without setting the broadcast and network. I have taken those out of the interfaces file, and restarted the networking service.

Right now it is set to the correct IP address, which I defined in the interfaces file. I will check it periodically to see if it holds.

Thanks for the help.

---

