---
title: "UEC NC initial network setup"
date: 2010-12-15
forum: Ubuntu Cloud and Juju
---

### Post by s7upify on 2010-12-15
Hi there. I am having problems setting up the network settings for my NC(s). I believe there is a problem with the was the gateway is configured as the NC do not have external connectivity. 

My cloud setup is:
Server A - CLC, CC, W, SC
Server B - NC
Server xx - NC's
Server A eth0 connected to enterprise network, eth1 connected to switch
Server B-xx - eth0 connected to switch

I tried to follow the Euca Beginner's Guide UEC Edition steps as closely as possible. The private network is set up on 192.168.20.xxx. However, once I reach the steps in section 2.2.2 in the guide I run into problems. apt-get cannot connect, therefore I cannot update eucalyptus and cannot install ntp, leaving my clocks non-synced.

I have Server A set up and it seems to be working fine. I can log into the web interface and download images from the ubuntu site and so on. Here is the contents of some config files from Server A:

```
:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address A.B.C.D
        netmask x.x.x.x
        network x.x.x.x
        broadcast x.x.x.x
        gateway x.x.x.x
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers W.X.Y.Z M.N.O.P
        dns-search entdomain

auto eth1
iface eth1 inet static
        address 192.168.20.1
        netmask 255.255.255.0
        network 192.168.20.0
        broadcast 192.168.20.255


cat /etc/resolv.conf
search entdomain
nameserver W.X.Y.Z 
nameserver M.N.O.P


cat /etc/eucalyptus/eucalyptus.conf
...
# Affects: CC, NC
# See: **NOTE** below
ENABLE_WS_SECURITY="Y"
LOGLEVEL="DEBUG"
VNET_PUBINTERFACE="eth0"
VNET_PRIVINTERFACE="eth1"
VNET_MODE="MANAGED-NOVLAN"

# Affects: CC
# See: **NOTE** below
CC_PORT="8774"
SCHEDPOLICY="ROUNDROBIN"
POWER_IDLETHRESH="300"
POWER_WAKETHRESH="300"
NC_SERVICE="axis2/services/EucalyptusNC"
VNET_DHCPDAEMON="/usr/sbin/dhcpd3"
VNET_DHCPUSER="dhcpd"
DISABLE_TUNNELLING="N"
NODES=""
VNET_ADDRSPERNET="32"
#VNET_SUBNET=""
#VNET_NETMASK=""
#VNET_DNS=""
#VNET_PUBLICIPS=""
...
```
As I said, this guy seems to be working. When I went to install the NC, I canceled DHCP setup and did the steps manually. When it got to apt setup it hung so I canceled that part of the installation (I'm guessing that it could not connect to the internet).

Now Server B is up and running. However, I do not think the default gateway is working. I have to SSH into Server A before SSH'ing into Server B on the private network (understandable). From there I can ping both the private and public IP's of Server A successfully, but cannot ping any other enterprise network IP's nor access the internet, which leads me to think that some gateway setting is broken (but then again, I don't know much about networking...)

Here is some of Server B's configuration:


```
cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet manual

auto br0
iface br0 inet static
        address 192.168.20.2
        netmask 255.255.255.0
        network 192.168.20.0
        broadcast 192.168.20.255
        gateway 192.168.20.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers W.X.Y.Z M.N.O.P
        bridge_ports eth0
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off


cat /etc/resolv.conf
nameserver W.X.Y.Z 
nameserver M.N.O.P


cat /etc/eucalyptus/eucalyptus.conf
...
# Affects: CC, NC
# See: **NOTE** below
ENABLE_WS_SECURITY="Y"
LOGLEVEL="DEBUG"
VNET_PUBINTERFACE="br0"
VNET_PRIVINTERFACE="br0"
VNET_MODE="MANAGED-NOVLAN"
...
```
If there is any other information pertinant and useful let me know. Help would be greatly appreciated!

Thank you very much.




TLDR:
My NC cannot connect outside of the private network through the gateway CLC/CC/... node. Help please?

---

### Post by raymdt on 2010-12-15
Hi s7upify,
your CLC Server ist the gateway for your NC and you have to enable the traffic forwarding and masquerade on it.


Try this on your CLC (as root)

```


echo 1 > /proc/sys/net/ipv4/ip_forward

iptables -P FORWARD ACCEPT
 
 iptables --table -nat -A POSTROUTING -o eth0 -j MASQUERADE


```

does it work now?

---

### Post by s7upify on 2010-12-16
Hi raymdt,
Your solution got me on the right track, and I ended up following a more in-depth [solution]("http://www.howtoforge.com/nat_iptables").
It works now! I can use apt-get.

Thanks!

---

### Post by raymdt on 2010-12-16
Thanks for the feedback ;)

---

### Post by ashishrevar on 2011-01-20
At this moment I am totally lost in the network configuration.
At the time of installation, I've avoided to add the proxy settings and now I am not able to perform apt-get or able to add any of the images.

How to deal with this?
Its urgent, please.

---

### Post by s7upify on 2011-02-07
Hello ashishrevar

If you have a setup where the NC's all go through the CC to reach the public net, then you might need to set up the iptables like I did.


Create a file called "/etc/iptables.rules" and paste the following into it:

```
# Generated by iptables-save v1.4.4 on Mon Jan 10 13:51:00 2011
*filter
:INPUT ACCEPT [68139:8946002]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [64129:8622968]
-A FORWARD -m conntrack --ctstate ESTABLISHED -j ACCEPT
-A FORWARD ! -d 172.19.0.0/16 -j ACCEPT
-A FORWARD -i eth1 -j ACCEPT
COMMIT
# Completed on Mon Jan 10 13:51:00 2011
# Generated by iptables-save v1.4.4 on Mon Jan 10 13:51:00 2011
*nat
:PREROUTING ACCEPT [201:31510]
:OUTPUT ACCEPT [2483:150142]
:POSTROUTING ACCEPT [2481:149883]
-A POSTROUTING -o eth0 -j MASQUERADE
COMMIT
# Completed on Mon Jan 10 13:51:00 2011


# COMMAND: sudo iptables-restore < /etc/iptables.rules
```Save the file.

Run "sudo iptables-restore < /etc/iptables.rules"

Now try apt-get on your NC's!

---

