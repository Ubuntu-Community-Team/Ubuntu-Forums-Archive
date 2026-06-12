---
title: "Help configuring network with differente Host IPs in Virtualbox 4.3.1"
date: 2014-04-02
forum: Virtualisation
---

### Post by gabriel16 on 2014-04-02
I have read many reviews on intenet but I could not solve the problem that I describe bellow. I need some help please
 
 
I have a notebook with ubuntu 12.04 virtual box running as a guest in a Windows 7 64bits host.
 
I use bridge connection under virtual box.
 
Everything was ok at home, that is, both guest and host sees each other and guest could connect to internet. 
My guest has a static IP and my host dhcp.
 
But when I moved to work where I have different gateway and had to put a static ip to my host, it wont access the guest anymore and guest has no internet connection.
 
---------------------------------------------------------------
Host at home:
 
DNS: 192.168.1.1
Subnet: 255.255.255.0
Ip: 192.168.1.xxxx (get dinamycally)
 
Guest:
Set as static ip.
The /etc/network/interfaces file:
 
auto lo
iface lo inet loopback
 
auto eth0
iface eth0 inet static
address 192.168.1.25
netmask: 255.255.255.0
gateway 192.168.1.1
dns-nameservers 8.8.8.8 192.168.1.1
 
----------------------------------------------------------------
 
Host at work:
Ip: 192.168.0.125
Subnet: 255.255.255.0
Default gateway: 192.168.0.1
Preferred DNS: 192.168.0.1
 
Guest:
Set as static IP
 
auto lo
iface lo inet loopback
 
auto eth0
iface eth0 inet static
address 192.168.1.25
netmask: 255.255.255.0
gateway 192.168.1.1
dns-nameservers 8.8.8.8 192.168.1.1
-----------------------------------------------------------------
 
How to solve this so I can use virtual box both at home and at work ?? What is the correct way of doing this ?
 
Thank you all in advanced !!

---

### Post by TheFu on 2014-04-03
Your work subnet is different from your home subnet.  That is the issue.  Don't have the guestOS with a static IP. Make it DHCP too. That will fix it.

If you don't run the work network, then setting a static IP there can be dangerous to others. Ask the network admin which static IP you should use, if any.

Or  you could re-IP your home network to match the work one.

---

