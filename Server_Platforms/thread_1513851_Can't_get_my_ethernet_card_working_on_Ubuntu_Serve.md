---
title: "Can't get my ethernet card working on Ubuntu Server--please help!"
date: 2010-06-20
forum: Server Platforms
---

### Post by TPD on 2010-06-20
Hi guys!

I'm new to Ubuntu Server and I'm not very used to work in a none-GUI  environment.
My Ethernet card works fine with Ubuntu Desktop, it finds it as eth0 and  all I need 
to do is to enter the IP addresses manually to get it working. On Ubuntu Server, I'm 
having trouble setting it up so I can access  Internet. I've tried this:

> 
To configure your Ethernet device with a static IP address and custom configuration, 
some more information will be required. Suppose you want to assign the IP address 
192.168.0.2 to the device eth1, with the typical netmask of 255.255.255.0. Your 
default gateway's IP address is 192.168.0.1. You would enter something like this into 
/etc/network/interfaces:

```

iface eth1 inet static
	address 192.168.0.2
	netmask 255.255.255.0
	gateway 192.168.0.1

```

In this case, you will need to specify your DNS servers manually in /etc/resolv.conf, which should look something like this:

```

search mydomain.example
nameserver 192.168.0.1
nameserver 4.2.2.2

```

[https://help.ubuntu.com/8.04/serverguide/C/network-configuration.html](https://help.ubuntu.com/8.04/serverguide/C/network-configuration.html)


It still doesn't work.

Do I need to do anything more than this?

---

### Post by denarced on 2010-06-20
Run this command and give us the output:
```

ifconfig -a

```
You insert the ip-address manually?
You don't have a router?
Just in case you do then you can just run:
```

sudo dhclient

```

---

### Post by denarced on 2010-06-20
There actually is the possibility that the address 192.168.0.2 is already taken and it's also possible that it's not really taken but the OSI-layer-3 device is getting things mixed up and reserving the address for some machine that once was connected to that address. In my experience and I'm not an expert(half-way there), it's better to bind the ip-address to a MAC-address on your router. Usually you want this on your machines but particularly on your server it's a good thing.

---

### Post by Groodles on 2010-06-20
Just in case you've posted the example into your /etc/network/interfaces file.  Your file should probably reference eth0, not eth1.  Hopefully your output of:
```

sudo config -a

```
will confirm this.

---

