---
title: "Connection Sharing"
date: 2011-02-14
forum: Server Platforms
---

### Post by viperce on 2011-02-14
Hi,
I need help sharing my pppoe connection with eth0 & eth1 can someone please help me with this
 
eth0 192.168.1.254
eth1 192.168.0.254
ppp0 
I am not sure how to get this working.
I want to be able to set all my Gateways on the workstations that need internet access to those 2 ip addresses

---

### Post by elico on 2011-02-14
what have done until now?

did you setup a DHCP server?

on the machine itself you should just set iptables to masquerade any request and also allow forwarding in sysctl.conf by adding in the end of the file or uncommenting the line 
> net.ipv4.ip_forward=1

to masquerade use :
iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE

---

### Post by viperce on 2011-02-14
I was using windows xp connection sharing worked but was a little slow...
 
I tried adding 
net.ipv4.ip_forward=1 to /etc/ufw/sysctl.conf
an iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE
then /etc/init.d/networking restart
 
but it did not work..

---

### Post by elico on 2011-02-14
no no..
you should do more than just that.

you need to make sure that all these settings are working.
use the command

iptables-save |grep ppp0
to see if you have a line like that
-A POSTROUTING -o ppp0 -j MASQUERADE
and use 
sysctl net.ipv4.ip_forward
to see if it's 1 (enables) or 0 (disabled)

if you want it to be enabled on boot you will need to make some changes in your system.

if you are not using a DHCP server:
on the other machines setup the ip address as 192.168.0.200 and mask 255.255.255.0
default gateway 192.168.0.254
and dns use 8.8.8.8
just to make sure you are getting any internet connection.

to save iptables rules you will need to change your iptables rules and save it to a file using:
iptables-save > /etc/iptables-rules.up
and add the following line to the file 
/etc/network/interfaces

you should have  
iface eth1 inet static
 ....
.... 
add after this line as in the next lines:
iface eth1 inet static
 pre-up /sbin/iptables-restore < /etc/iptables-rules.up

this will load on networking restart the saved rules of iptables.

if you need a more detailed help i will be glad to help.

---

### Post by viperce on 2011-02-18
thanks elico got it working :D

---

