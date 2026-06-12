---
title: "2 connections at the same time ...Help Help"
date: 2009-07-06
forum: Server Platforms
---

### Post by tropin on 2009-07-06
Hello Please Help

I have a server with two nic cards running with jaunty .
both nics have public pppoe static address's from my ISP. i have managed to get both nics activated with the appropriate ip . 
The default interface is eth0 .My issue is when i try to ping my eth1 nic it comes back unsuccessful , however i can see that the  eth1 nic is getting the packets ok but just not sending them back . 

When I disable eth0 , all connections drop . I have tried taking down both nics and setting them up one by one and everything works perfert until I try and use them at the same time .

My goal is get have both interfaces to be able to send and receive ok .

 Please let me know if you need more info 

Here is a copy of my ineterfaces file 

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

auto eth0
iface eth0 inet ppp
provider dsleth0

auto eth1
iface eth1 inet ppp
provider dsleth1

pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
pre-up /sbin/ifconfig eth1 up

---

### Post by Iowan on 2009-07-06
What are addresses of the two NIC's? 
Also - results of **route -n**?

---

### Post by tropin on 2009-07-07
Hello ,thanks for the reply

eth0
206.45.95.156

eth1
206.45.95.174

Here are the results

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
142.161.133.209 0.0.0.0         255.255.255.255 UH    0      0        0 ppp1
142.161.133.202 0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
206.45.95.156   0.0.0.0         255.255.255.255 UH    0      0        0 ppp1
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp1
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0

---

### Post by Iowan on 2009-07-07
Guess I need more experience with ppp(oe) to be of much help... I'm not sure how ppp0 and ppp1 relate to eth0 and eth1 (and each other).  I still have a hard time understanding two interfaces in the same subnet (bridged?), and it seems strange that eth0 routes to ppp1.

---

### Post by tropin on 2009-07-07
I know  , its really fustrating

---

