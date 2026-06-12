---
title: "DHCP - Not getting IP Assigned."
date: 2008-07-16
forum: Server Platforms
---

### Post by T.Louis on 2008-07-16
Hello,

I just installed Ubuntu 8.04 Server on a very old computer. However I can not connect to the net, basically I do not get an IP assigned through my switch and broadband router. The same port on the switch works with Windows Server 2003.

My /etc/network/interfaces is setup for just simply DHCP. I have tried several boards and solution with no luck. From trying to edit nameserver in resolv.conf to settings in dhclient.conf to send my mac address and computer ID before requesting anything.

Has anyone stumbled upon the problem of not getting an IP assigned through DHCP with 8.04?

I have also forced it to static e.g. 10.0.0.10 and I get the IP assigned by viewing ifconfig but I can't even ping my own broadband router at IP 10.0.0.138 or gateway.2shire.net.

Thanks for any tips or help that could lead to an IP address and an internet connection with DHCP!

T. Louis

---

### Post by windependence on 2008-07-16
You need to specify the gateway in your network config.

```
sudo nano /etc/network/interfaces

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.3.90
gateway 192.168.3.1
netmask 255.255.255.0
network 192.168.3.0
broadcast 192.168.3.255
```

Of course, you need to change the addresses to your addresses.

Then restart the network.

```
sudo /etc/init.d/networking restart
```

-Tim

---

### Post by T.Louis on 2008-07-16
Thank you for the reply Tim.

I have tried this already though and many other configurations. (e.g. dns). Not sure if it has something to do with my network card or something else. I have seen a few people with a similar problem on the boards however it did not solve my situation.

I might try to find a copy of 7.xx Server and run it and if it works I know for a fact that there is something with either the set up and not my hardware or network configuration. Will jot down a reply after testing the 7.xx.

Ty again,
T.Louis

---

### Post by T.Louis on 2008-07-17
My apologize, I have solved the problem. It was actually the length of the Ethernet cable vs the old Network card. For some reason it could not establish a connection through a 10 m Ethernet cable + the length of the actually cabling in the walls.

---

