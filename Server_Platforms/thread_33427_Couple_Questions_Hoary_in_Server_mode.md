---
title: "Couple Questions Hoary in Server mode"
date: 2005-05-10
forum: Server Platforms
---

### Post by ibda12u on 2005-05-10
Okay, so I just installed Hoary in Server Mode, I'm wanting to configure it to run MySQL.  But what do I need to do to setup a static IP, that way I can Apt-Get Mysql server.

So I guess I don't know what I need to do to get my network connection going (LAN)

---

### Post by Beernut on 2005-05-10
When you installed Ubuntu it should have found your network card unless you have a ISA card then it won't auto detect the card.  To chack and see if you card has an IP address type ifconfig at a command line.  If you are running DHCP on your network and your gateway was automatically configured all you need to do is the following.

Login to the server and type the following.

```
sudo apt-get update
sudo apt-get install mysql-server
```

---

### Post by ibda12u on 2005-05-11
[QUOTE=Beernut]When you installed Ubuntu it should have found your network card unless you have a ISA card then it won't auto detect the card.  To chack and see if you card has an IP address type ifconfig at a command line.  If you are running DHCP on your network and your gateway was automatically configured all you need to do is the following.

Login to the server and type the following.

```
sudo apt-get update
sudo apt-get install mysql-server
```[/QUOTE]
 Well it did find the network card, and I believe it found it with DHCP, but I want to give it a static IP address.  10.1.1.x 
I tried the man pages for interface but didn't get far.
I guess I'm trying to figure out what I need to do to set s static IP address, configure nameservers and the GW.

---

### Post by LordHunter317 on 2005-05-11
You need to change the settings in /etc/network/interfaces then,

Have a look at the interfaces(5) manpage for the details and an example.

---

### Post by bazh on 2005-05-11
```
sudo nano /etc/network/interfaces
``` 

Heres mine
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

# The primary network interface
auto eth0
iface eth0 inet static
    address 10.0.0.3 
    netmask 255.255.255.0
    gateway 10.0.0.100
```

---

### Post by ibda12u on 2005-05-11
[QUOTE=bazh]```
sudo nano /etc/network/interfaces
``` 

Heres mine
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

# The primary network interface
auto eth0
iface eth0 inet static
    address 10.0.0.3 
    netmask 255.255.255.0
    gateway 10.0.0.100
```[/QUOTE]
 Thanks a ton, where would I configure my nameserver settings?

---

### Post by saltydog on 2005-05-11
>  Thanks a ton, where would I configure my nameserver settings?

in /etc/resolv.conf

the format is:

nameserver xxx.yyy.zzz.www

---

### Post by ibda12u on 2005-05-11
Awesome that works great! Thanks for the help folks.

---

