---
title: "Problem in setting wireless acess point"
date: 2012-08-16
forum: Server Platforms
---

### Post by rushikesh988 on 2012-08-16
Hello ,

I am trying to setup a wireless acess point with the ubuntu server but Not getting the WIFI of my laptop turned on ..

WHEN I type 
> ifconfig -a 
I get my wireless card as 
> wlan0


THIS ARE THE FEW STEPS THAT I HAVE DONE for it

INSTALLED UBUNTU 12.04 SERVER ON MY LAPTOP
with
> 
[*] DNS server

[*] OpenSSH server 


updated and upgraded it 

tried to bridge the networks
using
> sudo apt-get install bridge-utils

and Then edit the network config

> 
sudo nano /etc/network/interfaces


> 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

#Gateway -
auto eth0
iface eth0 inet dhcp
pre-up iptables-restore < /etc/iptables.rules
post-down iptables-save > /etc/iptables.rules

#Wireless Setup
auto wlan0
iface wlan0 inet manual
wireless-mode master
wireless-essid pivotpoint

#Bridge interface
auto br0
iface br0 inet static
    address 10.1.1.1
    network 10.1.1.0
    netmask 255.255.255.0
    broadcast 10.1.1.255
    bridge-ports eth1 wlan0

Installed IPTABLES FIREWALL
> 
sudo iptables -t nat -A POSTROUTING -s 10.1.1.0/24 -o eth0 -j MASQUERADE

sudo iptables -A FORWARD -s 10.1.1.0/24 -o eth0 -j ACCEPT

sudo iptables -A FORWARD -d 10.1.1.0/24 -m conntrack --ctstate ESTABLISHED,RELATED -i eth0 -j ACCEPT

sudo iptables -A INPUT -m conntrack --ctstate NEW -p tcp --dport 80 -j LOG --log-prefix "NEW_HTTP_CONN: "

sudo sh -c "iptables-save > /etc/iptables.rules"


FOR PORT FORWARDING I HAVE DONE
> 
sudo nano /etc/sysctl.conf

net.ipv4.ip_forward = 1

echo 1 | sudo tee /proc/sys/net/ipv4/ip_forward

cat /proc/sys/net/ipv4/ip_forward






FOR DOING THE DHCP SERVER I HAVE DONE

> 
sudo apt-get install dhcp3-server
sudo nano /etc/dhcp3/dhcpd.conf


THEN EDITED
> 
# Subnet for DHCP Clients
subnet 10.1.1.0 netmask 255.255.255.0 {
        option domain-name-servers 10.1.1.1;
        max-lease-time 7200;
        default-lease-time 600;
        range 10.1.1.50 10.1.1.60;
        option subnet-mask 255.255.255.0;
        option broadcast-address 10.1.1.255;
        option routers 10.1.1.1;
        }


then

> sudo nano /etc/default/dhcp3-server

added the
> INTERFACES="br0"

and restarted my laptop ...

but this thing is not working for me.... 
HELP ME

---

### Post by bakegoodz on 2012-08-17
I heard of people getting ad-hoc mode working by just putting the wifi adapter in master mode, but you really need a daemon to authenticate the connecting clients to have an access point. I setup my Ubuntu Server AP with hostapd.
First are you sure the hardware and driver supports AP Mode?
Check with:
```
sudo apt-get install iw
iw list | grep modes: -A 10
```
I like this guide for setting up Hostapd:
[http://www.danbishop.org/2011/12/11/using-hostapd-to-add-wireless-access-point-capabilities-to-an-ubuntu-server/](http://www.danbishop.org/2011/12/11/using-hostapd-to-add-wireless-access-point-capabilities-to-an-ubuntu-server/)

---

### Post by rushikesh988 on 2012-08-19
> **bakegoodz said:**
> I heard of people getting ad-hoc mode working by just putting the wifi adapter in monitor mode, but you really need a daemon to authenticate the connecting clients to have an access point. I setup my Ubuntu Server AP with hostapd.
First are you sure the hardware and driver supports AP Mode?
Check with:
```
sudo apt-get install iw
iw list | grep modes: -A 10
```
I like this guide for setting up Hostapd:
[http://www.danbishop.org/2011/12/11/using-hostapd-to-add-wireless-access-point-capabilities-to-an-ubuntu-server/](http://www.danbishop.org/2011/12/11/using-hostapd-to-add-wireless-access-point-capabilities-to-an-ubuntu-server/)
Thank You ..

---

