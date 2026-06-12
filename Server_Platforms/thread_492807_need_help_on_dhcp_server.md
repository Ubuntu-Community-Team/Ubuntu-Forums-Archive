---
title: "need help on dhcp server"
date: 2007-07-05
forum: Server Platforms
---

### Post by virushioyo on 2007-07-05
Hi all,

i am new for ubuntu dhcp server. please help if my configuration are wrong or maybe provide a good step by step HOWto link to me. 

here is my concern.

i have a server with 2 NIC which is eth0 & eth1.
eth0 dial to modem using rp-pppoe 
eth1 - dhcp request from here

my configuration for /etc/network/interfaces
iface eth0 inet dhcp

iface eth1 inet static
address 192.168.2.1
netmask 255.255.255.0
network 192.168.2.0
broadcast 192.168.2.255

setting for rp-pppoe
on demand=no
firewall=NONE
interface="eth0"
dns=202.188.0.133, 202.188.1.5 (malaysia ISP)
and blah blah setup all ok and able to dial to internet

configuration for /etc/dhcp3/dhcpd.conf
# A slightly different configuration for an internal subnet.
subnet 192.168.2.0 netmask 255.255.255.0 {
 range 192.168.2.10 192.168.2.100;
 option domain-name-servers 202.188.0.133, 202.188.1.5, 192.168.2.1;
 option domain-name "tm.net.my";
 option routers 192.168.2.1;
 option broadcast-address 192.168.2.255;
 default-lease-time 600;
 max-lease-time 7200;
}

ok now.
i can dial to internet with command
pppoe-start
...CONNECTED!
can assign ip to clients
no firewall install
but both server and client cant connect to internet.

appreciate your help. thanks

---

### Post by virushioyo on 2007-07-05
already apt-get bind9. thanks

---

### Post by swu on 2007-07-09
I am trying to configure a DHCP server on my ubuntu box. I have looked at various posts and wikis and am not sure which config file I should be modifying. It seems there are DHCP config files in:

/etc/dhcpd.conf
/etc/default/dhcp3-server 

They look pretty identical, but which one should I configure? Which one is the server looking at for DHCP configuration?

Thx!

---

### Post by Mr. C. on 2007-07-10
virushioyo: When you make your dialup connection, what is the output of the commands:

```
netstat -rn
ifconfig -a
```

swu: The file /etc/dhcpd.conf is the DHCP server configuration file.  Files in /etc/default are commonly used for default or distro-specific settings, usually read by the /etc/init.d/* files.  So anything in /etc/default/dhcp3-server would be some default dhcp server settings.  Make your modifications to /etc/dhcpd.conf (save a backup copy in case you want to revert).

MrC

---

