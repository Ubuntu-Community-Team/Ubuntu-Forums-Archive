---
title: "Ubuntu 7.04 server with 3 NICs on Dell SC440"
date: 2007-05-03
forum: Server Platforms
---

### Post by cbergilo on 2007-05-03
hi all

i've installed 2 NICs (realtek 8139D) in addtion to onboard broadcom (BCM95754).
the problem is: random assignment of ethx to the 3 NICs.

on first boot:

onboard broadcom ---->eth2
realtech on pci slot 3 ---> eth0
realtech on pci slot 5 ---> eth1

on reboot number x:

onboard broadcom ---->eth0
realtech on pci slot 3 ---> eth2
realtech on pci slot 5 ---> eth1

on reboot number y:

onboard broadcom ---->eth1
realtech on pci slot 3 ---> eth2
realtech on pci slot 5 ---> eth0

lspci , dmesg confirmed the above scenario. (sorry no output of these command since the box is on centos 4.4 right now - just to confirm, it's not hardware problem).

i've googled the net but of not much help so far. pls anyone cause i'm at my wits' end right now. 


thanks you in advance.

---

### Post by z33k3r on 2007-05-03
I have also seen this problem, but on 6.06 and 6.10... I would also like to know what the reason behind it is. It appears that with 7.04, the issue has stopped as far as my Tyan K8SE is concerned...

---

### Post by salvimoratalla on 2007-05-04
Hello, try with the "nameif [interface] [mac-address]" in /etc/network/interfaces pre-up

f.e.: 

/etc/network/interfaces

auto eth0
iface eth0 inet static
        pre-up  /sbin/nameif eth0 [macaddress1] || true
        address xxx.yyy.1.1
        netmask 255.255.255.0

auto eth1
iface eth1 inet static
        pre-up  /sbin/nameif eth0 [macaddress1] || true
        address xxx.yyy.2.1
        netmask 255.255.255.0

auto eth2
iface eth2 inet static
        pre-up  /sbin/nameif eth0 [macaddress1] || true
        address xxx.yyy.3.1
        netmask 255.255.255.0

---

### Post by jerrylamos on 2007-05-04
Some of us would think the "random assignment" is the "Network Mangler" in mangling the networks.  Now from the forums there are those who think the "Network Mangler" keeps the "best" network connection running by dynamically choosing among those available; there are others like me who during boot the "Network Mangler" goes out of its way to disable the only connection I've got.  So on every boot I've got to "manually" restart the network, which for my configuration is a step backwards from Edgy and Dapper who just enable the connection and leave it enabled, no user intervention required.

So the developers have a dilemma, help some people by having the "Network Mangler" keep looking for the best connection, and slow some of the rest of us down when the "Network Mangler" closes the only network connection.

So the developers may believe in some cases the "Network Mangler" is automagically keeping the "best" connection going, at the price of some of the rest of us who have to find ways to defeat the "mangling" as in the previous posts.

I'm trying early "Gutsy" now, so I'll be interested if there are any changes.....

Cheers, Jerry:confused:

---

### Post by cbergilo on 2007-05-04
it's not the cleanest solution but what i did was (4 hours ago before reading ur postings);
1. disabled onboard broadcom
2. replaced realtek nic on pci slot 5 with 3com card
the result? even after more than 10 restarts, the assignments are as below:-

realtek (pci slot 3)----->eth0
3com (pci slot 5)------->eth2

i'll give nameif a try tomorrow.

thanks once again.

---

