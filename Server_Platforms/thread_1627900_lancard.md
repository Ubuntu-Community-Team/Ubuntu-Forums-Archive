---
title: "lancard"
date: 2010-11-21
forum: Server Platforms
---

### Post by Rakeshvijayan on 2010-11-21
Hi 
 
I installed two lancard in my pc . And I install ubuntu server 10.10..
At install time os ask me for which is the default connection and it show me that 
dhcp not working configure your network manually I give  ip 192.168.1.100
and subnet 255.255.255.0 gateway  and dns 192.168.1.1...
after I installed server i tried to update and install Desktop i got a message that
sudo apt-get install ubuntu-desktop
 
"Reading package list done 
Building dependency tree
Reading state information ....Done 
E: Unable to locate package updates"
 
how can i check the network connections 
 
and I want share the cdrom  with out Desktop 

By using ifconfig i can see my network address
 
help me am stuck here .........

---

### Post by Fafler on 2010-11-22
Have you defined a default gateway?

```
route add default gw 192.168.1.1
```

---

### Post by Rakeshvijayan on 2010-11-23
yes that i mentioned above, i use the command sudo vi /etc/network/interface 
that only show the eth0 ip address it is to difficult to vi in 10 .10 server I cant save nothing .i don't know what is the 
reason may be if I am a new user

---

### Post by Fafler on 2010-11-23
Can you ping the gateway?

---

### Post by cariboo on 2010-11-23
I personally find vim a pain in the you know what. I use nano to edit configuration files. if you want to use both network cards, you need to set them up in /etc/network/interfaces. The file should look something like this:

```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
	address		192.168.1.250
	netmask		255.255.255.0
	broadcast	192.168.1.254
	gateway		192.168.1.1

# the second interface
auto eth1 inet static
       address            192.168.1.125
       netmask           255.255.255.0
       broadcast        192.168.1.254
       gateway            192.168.1.1     
```

The above config file assume you want to set static ip address for both cards. If you want one to get its ip address via DHCP then change the static to dhcp.

---

